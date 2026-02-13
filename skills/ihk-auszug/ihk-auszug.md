---
description: Erstellt einen IHK-PDF-Auszug aus einer Langzeitlieferantenerklaerung (LLE) mit markierten Materialzeilen
allowed-tools: Read, Bash, Glob, Grep
argument-hint: <Materialnummer(n)> (z.B. "467000" oder "467000 153920 478510")
---

# IHK-Auszug aus Langzeitlieferantenerklaerung erstellen

Du erstellst einen PDF-Auszug aus einer Langzeitlieferantenerklaerung (LLE) fuer die IHK. Der Auszug enthaelt die Erklaerungsseite (Seite 1) plus alle Seiten, auf denen die gesuchten Materialien vorkommen – mit gelber Markierung der Materialzeilen.

## Schritt 1: PDF identifizieren

Identifiziere die LLE-PDF aus dem aktuellen Konversationskontext (z.B. per @-Referenz, vorheriger Erwaehnung, oder Dateien im aktuellen Verzeichnis). Falls keine PDF eindeutig erkennbar ist, frage den Nutzer.

## Schritt 2: Materialnummern parsen

Extrahiere aus `$ARGUMENTS` eine oder mehrere Materialnummern (Leerzeichen-getrennt). Falls keine Argumente uebergeben wurden, frage den Nutzer nach den Materialnummern.

## Schritt 3: Python-Script ausfuehren

Fuehre via Bash ein Python-Script mit PyMuPDF (`fitz`) aus. Falls `fitz` nicht verfuegbar ist, installiere es zuerst mit `pip3 install PyMuPDF`.

Nutze exakt dieses Script (ersetze `<PDF_PATH>` und die Materialnummern-Liste):

```bash
python3 << 'PYTHON_SCRIPT'
import fitz
import os, sys

pdf_path = "<PDF_PATH>"
material_numbers = [<MATERIALNUMMERN_ALS_STRINGS>]  # z.B. ["467000", "153920"]
output_dir = os.path.dirname(pdf_path) or "."

doc = fitz.open(pdf_path)
pages_to_include = set()
found_materials = {}
not_found = []

for mat_nr in material_numbers:
    found = False
    for i in range(len(doc)):
        page = doc[i]
        results = page.search_for(mat_nr)
        if results:
            found = True
            pages_to_include.add(i)
            # Highlight: Zeile ueber gesamte Seitenbreite
            for rect in results:
                y_top = rect.y0 - 1.5
                y_bottom = rect.y1 + 1.5
                highlight_rect = fitz.Rect(10, y_top, page.rect.width - 10, y_bottom)
                annot = page.add_highlight_annot(highlight_rect)
                annot.set_colors(stroke=(1, 1, 0))
                annot.update()
            if mat_nr not in found_materials:
                found_materials[mat_nr] = []
            found_materials[mat_nr].append(i + 1)  # 1-basierte Seitenzahl
    if not found:
        not_found.append(mat_nr)
        # Aehnliche Nummern suchen
        print(f"WARNUNG: Material '{mat_nr}' nicht gefunden.")
        for i in range(len(doc)):
            page = doc[i]
            text = page.get_text()
            for line in text.split("\n"):
                if mat_nr[:4] in line and any(c.isdigit() for c in line):
                    print(f"  Aehnlich auf Seite {i+1}: {line.strip()[:100]}")

# Neue PDF: Seite 1 (Erklaerung) + alle Seiten mit markierten Materialien
new_doc = fitz.open()
new_doc.insert_pdf(doc, from_page=0, to_page=0)  # Erklaerungsseite immer dabei
for page_idx in sorted(pages_to_include):
    if page_idx != 0:  # Seite 1 nicht doppelt einfuegen
        new_doc.insert_pdf(doc, from_page=page_idx, to_page=page_idx)

# Dateiname generieren
mat_suffix = "_".join(material_numbers[:5])  # Max 5 Nummern im Dateinamen
output_path = os.path.join(output_dir, f"LLE_Auszug_{mat_suffix}.pdf")
new_doc.save(output_path)
new_doc.close()
doc.close()

print(f"\nERGEBNIS:")
print(f"Ausgabedatei: {output_path}")
print(f"Seiten im Auszug: {new_doc.page_count if hasattr(new_doc, 'page_count') else 'gespeichert'}")
for mat, pages in found_materials.items():
    print(f"  Material {mat}: gefunden auf Seite(n) {', '.join(map(str, pages))}")
for mat in not_found:
    print(f"  Material {mat}: NICHT GEFUNDEN")
PYTHON_SCRIPT
```

**Wichtig bei der Script-Anpassung:**
- Ersetze `<PDF_PATH>` mit dem vollstaendigen Pfad zur Quell-PDF (korrekt escaped)
- Ersetze `<MATERIALNUMMERN_ALS_STRINGS>` mit den extrahierten Materialnummern als Python-String-Liste
- Die Highlight-Markierung geht ueber die **gesamte Zeilenbreite** (x=10 bis page.width-10)
- Bei Duplikaten auf einer Seite: Seite nur einmal einfuegen, aber alle Treffer markieren

## Schritt 4: Ergebnis pruefen

Oeffne die erzeugte PDF mit dem Read-Tool und zeige sie dem Nutzer an, damit er das Ergebnis visuell pruefen kann.

## Schritt 5: Zusammenfassung ausgeben

Gib eine uebersichtliche Zusammenfassung aus:
- Welche Materialien gefunden wurden (mit Seitenzahlen)
- Welche Materialien NICHT gefunden wurden (mit Hinweis auf aehnliche Nummern falls vorhanden)
- Vollstaendiger Pfad zur erzeugten Auszugs-PDF
