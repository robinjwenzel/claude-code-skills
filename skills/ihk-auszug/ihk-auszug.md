---
description: Erstellt einen IHK-PDF-Auszug aus einer Langzeitlieferantenerklaerung (LLE) mit markierten Materialzeilen
allowed-tools: Read, Bash, Glob, Grep
argument-hint: <Materialnummer(n)> (z.B. "467000" oder "467000 153920 478510")
---

# IHK-Auszug aus Langzeitlieferantenerklaerung erstellen

Du erstellst einen PDF-Auszug aus einer Langzeitlieferantenerklaerung (LLE) fuer die IHK. Der Auszug enthaelt die Erklaerungsseite (Seite 1) plus alle Seiten, auf denen die gesuchten Materialien vorkommen – mit gelber Markierung der Materialzeilen.

## Schritt 1: PDF identifizieren

Identifiziere die LLE-PDF aus dem aktuellen Konversationskontext (z.B. per @-Referenz, vorheriger Erwaehnung, oder Dateien im aktuellen Verzeichnis). Falls keine PDF eindeutig erkennbar ist, frage den Nutzer nach der Datei.

## Schritt 2: Materialnummern parsen

Extrahiere aus `$ARGUMENTS` eine oder mehrere Materialnummern (Leerzeichen-getrennt). Falls keine Argumente uebergeben wurden, frage den Nutzer nach den gesuchten Materialnummern.

## Schritt 3: Python-Script ausfuehren

Lies `skills/ihk-auszug/scripts/extract_lle.py` und fuehre es via Bash aus. Falls `fitz` nicht verfuegbar ist, installiere es zuerst mit `pip3 install PyMuPDF`.

Passe vor der Ausfuehrung an:
- `<PDF_PATH>` → vollstaendiger Pfad zur Quell-PDF (korrekt escaped)
- `<MATERIALNUMMERN_ALS_STRINGS>` → extrahierte Materialnummern als Python-String-Liste

## Schritt 4: Ergebnis pruefen

Oeffne die erzeugte PDF mit dem Read-Tool und zeige sie dem Nutzer an, damit er das Ergebnis visuell pruefen kann.

## Schritt 5: Zusammenfassung ausgeben

Gib eine uebersichtliche Zusammenfassung aus:
- Welche Materialien gefunden wurden (mit Seitenzahlen)
- Welche Materialien NICHT gefunden wurden (mit Hinweis auf aehnliche Nummern falls vorhanden)
- Vollstaendiger Pfad zur erzeugten Auszugs-PDF
