---
description: Erstellt eine professionelle Management-Praesentation als PowerPoint-Datei (.pptx) im mindsquare CI-Design
allowed-tools: Write, Read, Edit, Bash
argument-hint: Thema der Praesentation (z.B. 'SAP S/4HANA Migrationsstrategie fuer das Management')
---

Erstelle eine professionelle Management-Praesentation mit mehreren Folien als PowerPoint-Datei (.pptx). Die Praesentation richtet sich an das Management und soll aussehen, als waere sie von einer renommierten Unternehmensberatung (McKinsey, BCG) erstellt worden.

**Thema der Praesentation:** $ARGUMENTS

---

## Technische Grundlagen

### Python-Bibliothek

Verwende `python-pptx` zur Erzeugung der PowerPoint-Datei. Falls nicht installiert, installiere sie mit `pip3 install python-pptx`.

### Folienformat

- **Breite**: 13.333 Zoll (Widescreen 16:9)
- **Hoehe**: 7.5 Zoll
- **Layout**: Blank-Layout (`slide_layouts[6]`)

### Hilfsfunktionen

Verwende im Python-Script folgende Imports und Hilfsfunktionen als Grundgeruest:

```python
from pptx import Presentation
from pptx.util import Inches, Pt, Emu
from pptx.dml.color import RGBColor
from pptx.enum.text import PP_ALIGN, MSO_ANCHOR
from pptx.enum.shapes import MSO_SHAPE

prs = Presentation()
prs.slide_width = Inches(13.333)
prs.slide_height = Inches(7.5)

# Mehrere Folien erzeugen — jede Folie ueber add_slide
# slide = prs.slides.add_slide(prs.slide_layouts[6])
```

---

## mindsquare Corporate Identity

### Farbpalette

| Farbe | RGB-Wert | Verwendung |
|-------|----------|------------|
| Orange | `RGBColor(0xEA, 0x5B, 0x0B)` | Primaerfarbe, Highlights, Akzente, Hervorhebungen im Titel |
| Gelb/Gold | `RGBColor(0xFD, 0xC3, 0x00)` | Sekundaerfarbe, Icons, Badges |
| Dunkelgrau | `RGBColor(0x56, 0x56, 0x56)` | Fliesstext, Ueberschriften, Standardtextfarbe |
| Hellgrau | `RGBColor(0xCC, 0xCC, 0xCC)` | Trennlinien, dezente Strukturen |
| Hintergrund Hellgrau | `RGBColor(0xF5, 0xF5, 0xF5)` | Hintergrundelemente, Karten-Hintergrund |
| Weiss | `RGBColor(0xFF, 0xFF, 0xFF)` | Folien-Hintergrund |
| Mittelgrau | `RGBColor(0x99, 0x99, 0x99)` | Kleintext, Labels, Footer |

### Typografie

- **Titel-Schriftart**: `"Poppins"` (Bold) — fuer Folientitel, Sektionsueberschriften und grosse Labels
- **Body-Schriftart**: `"Calibri"` (Fallback: `"Arial"`) — fuer Fliesstext, Labels, Footer und alle sonstigen Texte
- **Folientitel**: 28pt, bold, Farbe Dunkelgrau, Poppins. Einzelne Schluesselwoerter in Orange hervorheben (separater Run im gleichen Paragraph)
- **Sektionsueberschriften**: 16-20pt, Bold, Dunkelgrau, Poppins
- **Timeline-Marker/grosse Labels**: 28pt, Bold, Poppins
- **Fliesstext**: 14-16pt, regular, Dunkelgrau, Calibri
- **Kleintext/Labels/Footer**: 11-12pt, Dunkelgrau oder Mittelgrau, Calibri

### Hervorhebungen im Titel

Um einzelne Woerter im Titel orange hervorzuheben, verwende separate Runs innerhalb eines Paragraphen:

```python
tf = title_shape.text_frame
p = tf.paragraphs[0]

run1 = p.add_run()
run1.text = "Normaler Text "
run1.font.size = Pt(28)
run1.font.bold = True
run1.font.color.rgb = RGBColor(0x56, 0x56, 0x56)
run1.font.name = "Poppins"

run2 = p.add_run()
run2.text = "Hervorgehobenes Wort"
run2.font.size = Pt(28)
run2.font.bold = True
run2.font.color.rgb = RGBColor(0xEA, 0x5B, 0x0B)  # Orange
run2.font.name = "Poppins"
```

---

## Praesentationsstruktur (Multi-Slide)

Erstelle eine **mehrseitige Praesentation** (typischerweise 5-10 Folien). Empfohlene Struktur:

1. **Titelfolie** — Thema, Datum, Anlass (minimalistisch, grosser Titel, Logo)
2. **Management Summary** — Executive Overview mit den wichtigsten Kernaussagen
3. **Ausgangssituation / Problemstellung** — Kontext und Hintergrund
4. **Zielsetzung & Scope** — Was soll erreicht werden?
5. **Loesungsansatz / Vorgehen** — Wie wird das Ziel erreicht?
6. **Roadmap / Timeline** — Wann passiert was? Phasen und Meilensteine
7. **Pakete / Deliverables** — Konkrete Arbeitspakete und Ergebnisse
8. **Budget / Investition** — Kosten, Nutzen, ROI
9. **Naechste Schritte** — Call to Action, konkrete To-Dos

**Hinweis**: Passe die Struktur an das Thema an — nicht jedes Thema braucht alle Folientypen. Waehle die relevanten Folien aus und ergaenze bei Bedarf themenspezifische Folien.

**Seitenzahlen**: Zaehle die Seitenzahlen automatisch hoch (1, 2, 3, ...) ueber alle Folien.

---

## Folien-Grundstruktur

### Standardfolie

Jede Standardfolie muss folgende Elemente enthalten:

#### 1. Header-Bereich (oben)

- **Titel**: Links oben, Position `(Inches(0.5), Inches(0.3))`, max. Breite 9 Zoll
- **Logo**: Rechts oben als Bilddatei (echtes mindsquare-Logo)

Logo einfuegen:
```python
# Logo als Bild einfuegen
import os
logo_path = "/Users/robinwenzel/AI Playground/Claude Code/claude-code-skills/skills/slide/templates/logo_mindsquare.png"
logo = slide.shapes.add_picture(logo_path, Inches(11.0), Inches(0.15), height=Inches(0.5))
```

Fuer dunkle Hintergruende (z.B. Trennfolien) die weisse Logo-Variante verwenden:
```python
logo_path_white = "/Users/robinwenzel/AI Playground/Claude Code/claude-code-skills/skills/slide/templates/logo_mindsquare_white.png"
logo = slide.shapes.add_picture(logo_path_white, Inches(11.0), Inches(0.15), height=Inches(0.5))
```

#### 2. Gradient-Linie unter dem Titel

Die Gradient-Linie wird als Bilddatei eingefuegt (Orange-zu-Gold-Verlauf):

```python
# Gradient-Linie als Bild einfuegen
line_path = "/Users/robinwenzel/AI Playground/Claude Code/claude-code-skills/skills/slide/templates/gradient_line.png"
line_pic = slide.shapes.add_picture(line_path, Inches(0.2), Inches(0.84), Inches(12.87), Pt(3))
```

#### 3. Content-Bereich

- **Startposition**: ab `Inches(0.5), Inches(1.4)` (unterhalb der Gradient-Linie)
- **Verfuegbare Breite**: ca. 12.3 Zoll
- **Verfuegbare Hoehe**: ca. 5.5 Zoll (bis zum Footer)
- Hier wird der eigentliche Folieninhalt platziert

#### 4. Footer

- **Position**: Rechts unten, `Inches(12.5), Inches(7.05)`
- **Inhalt**: Seitenzahl (automatisch hochzaehlend)
- **Schrift**: 11pt, Mittelgrau

```python
# Seitenzahl-Counter — page_num fuer jede Folie hochzaehlen
footer = slide.shapes.add_textbox(Inches(12.5), Inches(7.05), Inches(0.5), Inches(0.3))
tf = footer.text_frame
p = tf.paragraphs[0]
p.text = str(page_num)
p.font.size = Pt(11)
p.font.color.rgb = RGBColor(0x99, 0x99, 0x99)
p.font.name = "Calibri"
p.alignment = PP_ALIGN.RIGHT
```

### Titelfolie

Die erste Folie der Praesentation ist eine **Titelfolie** mit besonderem Layout:

- **Grosser zentrierter Titel**: Poppins, 36-40pt, Bold, Dunkelgrau — mittig auf der Folie
- **Untertitel** (optional): Datum, Anlass oder Kurzbeschreibung — 18-20pt, Regular, Mittelgrau
- **mindsquare-Logo**: Rechts oben wie gewohnt
- **Gradient-Linie**: Unter dem Titel oder als gestalterisches Element
- **Minimalistisches Design**: Viel Weissraum, keine Inhaltselemente
- **Seitenzahl**: "1"

```python
# Beispiel Titelfolie
slide = prs.slides.add_slide(prs.slide_layouts[6])

# Grosser zentrierter Titel
title_box = slide.shapes.add_textbox(Inches(1.5), Inches(2.5), Inches(10.3), Inches(1.5))
tf = title_box.text_frame
tf.word_wrap = True
p = tf.paragraphs[0]
p.alignment = PP_ALIGN.CENTER
run = p.add_run()
run.text = "Praesentationstitel"
run.font.size = Pt(38)
run.font.bold = True
run.font.color.rgb = RGBColor(0x56, 0x56, 0x56)
run.font.name = "Poppins"

# Untertitel
subtitle_box = slide.shapes.add_textbox(Inches(1.5), Inches(4.0), Inches(10.3), Inches(0.8))
tf2 = subtitle_box.text_frame
tf2.word_wrap = True
p2 = tf2.paragraphs[0]
p2.alignment = PP_ALIGN.CENTER
run2 = p2.add_run()
run2.text = "Untertitel | Datum | Anlass"
run2.font.size = Pt(18)
run2.font.color.rgb = RGBColor(0x99, 0x99, 0x99)
run2.font.name = "Poppins"
```

---

## Design-Prinzipien (Management-Qualitaet)

### Zielgruppe

Die Praesentation richtet sich an **Management und C-Level**. Jede Folie muss auf diesem Niveau kommunizieren: klar, praegnant, entscheidungsorientiert.

### Consulting-Qualitaet

Die Praesentation soll aussehen, als waere sie von **McKinsey oder BCG** erstellt worden. Professionell, strukturiert, visuell ansprechend — keine Amateur-Slides.

### Storyline-Prinzipien

1. **Storyline-Denken**: Die gesamte Praesentation erzaehlt eine zusammenhaengende Geschichte. Jede Folie ist ein Kapitel dieser Story.
2. **"So What?"**: Jede Folie braucht eine klare Kernaussage. Was soll der Leser mitnehmen? Was ist die Schlussfolgerung?
3. **Pyramidales Prinzip**: Wichtigstes zuerst, Details darunter. Die Kernbotschaft steht im Titel oder ganz oben auf der Folie.

### Visuelle Prinzipien

1. **Visuelle Hierarchie**: Wichtigstes zuerst, klare Leserichtung von oben links nach unten rechts
2. **Strukturierte Darstellung**: Verwende Spalten-Layouts, Karten-Boxen (Rounded Rectangles), Prozessflows, Vergleichs-Layouts — NIEMALS reine Fliesstextbloecke
3. **Sparsamer Farbeinsatz**: Hauptsaechlich Dunkelgrau (#565656) auf weissem Grund. Orange (#ea5b0b) NUR fuer Akzente, Highlights, wichtige Zahlen. Gold (#fdc300) nur als Sekundaerakzent
4. **Folien-Hintergrund**: Standardmaessig Weiss. Fuer besondere Folien (z.B. Trennfolien) kann ein dunkler Hintergrund verwendet werden
5. **Icons/Piktogramme**: Nutze Unicode-Symbole/Emojis wo passend (z.B. Buch-Emojis, Zahnrad, Rakete, Diagramm etc.)
6. **Datenorientiert**: Wo moeglich, konkrete Zahlen, Metriken, KPIs visuell hervorheben
7. **Maximale Raumnutzung**: Der Content-Bereich soll gut gefuellt sein — keine grossen Leerflaechen
8. **Konsistente Abstaende**: Einheitliches Spacing, saubere Ausrichtung
9. **Karten/Boxen-Design**: Verwende `MSO_SHAPE.ROUNDED_RECTANGLE` mit `RGBColor(0xF5, 0xF5, 0xF5)` Hintergrund und `RGBColor(0xE0, 0xE0, 0xE0)` oder Orange Border fuer strukturierte Inhaltsboxen

## Folientypen und Layouts

Waehle je nach Inhalt das passende Layout:

- **Titelfolie**: Grosser zentrierter Titel, Untertitel, Logo, Gradient-Linie, minimalistisch
- **Management Summary**: 2-3 Spalten mit Sektionskarten (Rounded Rectangles), jede mit Icon, Titel und Bullet-Points
- **Roadmap/Timeline**: Horizontale Phasen-Pfeile (Chevron-Shapes oder Pfeil-Shapes), darunter Detail-Punkte
- **Paket-/Moduluebersicht**: Karten-Layout mit Rounded Rectangles
- **Prozess-Flow**: Nummerierte Schritte mit Pfeil-Shapes (`MSO_SHAPE.RIGHT_ARROW` oder `MSO_SHAPE.CHEVRON`), optional mit Beschreibungen
- **KPI-Dashboard**: Grosse Zahlen in Karten mit farblichen Akzenten
- **Vergleich/Matrix**: Nebeneinander angeordnete Boxen mit Vergleichskategorien
- **Trennfolie**: Zentrierter grosser Titel, minimalistisch

## Wichtige python-pptx Techniken

### Textbox mit mehreren Absaetzen
```python
txBox = slide.shapes.add_textbox(left, top, width, height)
tf = txBox.text_frame
tf.word_wrap = True

p = tf.paragraphs[0]
p.text = "Erste Zeile"
p.font.size = Pt(14)
p.font.color.rgb = RGBColor(0x56, 0x56, 0x56)
p.font.name = "Calibri"

p2 = tf.add_paragraph()
p2.text = "Zweite Zeile"
p2.font.size = Pt(12)
p2.font.color.rgb = RGBColor(0x99, 0x99, 0x99)
p2.font.name = "Calibri"
```

### Rounded Rectangle mit Text
```python
shape = slide.shapes.add_shape(
    MSO_SHAPE.ROUNDED_RECTANGLE, left, top, width, height
)
shape.fill.solid()
shape.fill.fore_color.rgb = RGBColor(0xF5, 0xF5, 0xF5)
shape.line.color.rgb = RGBColor(0xE0, 0xE0, 0xE0)
shape.line.width = Pt(1)

tf = shape.text_frame
tf.word_wrap = True
tf.margin_left = Inches(0.15)
tf.margin_right = Inches(0.15)
tf.margin_top = Inches(0.1)
tf.margin_bottom = Inches(0.1)
```

### Pfeil-Shape
```python
arrow = slide.shapes.add_shape(
    MSO_SHAPE.RIGHT_ARROW, left, top, width, height
)
arrow.fill.solid()
arrow.fill.fore_color.rgb = RGBColor(0xEA, 0x5B, 0x0B)
arrow.line.fill.background()
```

### Linie / Trennlinie
```python
line = slide.shapes.add_shape(
    MSO_SHAPE.RECTANGLE, left, top, width, Pt(1)
)
line.fill.solid()
line.fill.fore_color.rgb = RGBColor(0xCC, 0xCC, 0xCC)
line.line.fill.background()
```

---

## Ausgabe-Anweisungen

1. **Dateiname**: Speichere die PowerPoint-Datei im AKTUELLEN Arbeitsverzeichnis als `presentation_[kurzer-beschreibender-name].pptx` (z.B. `presentation_sap_migration.pptx`)
2. **Erzeugung**: Schreibe ein vollstaendiges Python-Script, speichere es temporaer und fuehre es mit `python3` aus, um die .pptx-Datei zu generieren. Loesche das Script nach erfolgreicher Erzeugung.
3. **Qualitaet**: Die Praesentation muss so aussehen, als waere sie von einer Top-Unternehmensberatung (McKinsey/BCG) erstellt worden
4. **Inhalt**: Fuelle die Folien mit sinnvollen, plausiblen Inhalten basierend auf dem Thema. Erfinde realistische Zahlen/Daten wo noetig
5. **Eigenstaendig**: Die .pptx-Datei muss ohne externe Abhaengigkeiten funktionieren
6. **Kompatibilitaet**: Die Datei muss in Microsoft PowerPoint, LibreOffice Impress und Google Slides korrekt dargestellt werden
7. **Storyline**: Stelle sicher, dass die Folien eine zusammenhaengende Geschichte erzaehlen — von der Problemstellung ueber den Loesungsansatz bis zum Call to Action

Generiere JETZT das Python-Script, fuehre es aus und erstelle die PowerPoint-Praesentation basierend auf dem Thema oben. Gib nach dem Erstellen den Dateipfad aus.
