---
description: Erstellt eine professionelle Management-Praesentationsfolie als PowerPoint-Datei (.pptx) im mindsquare CI-Design
allowed-tools: Write, Read, Edit, Bash
argument-hint: Beschreibung des Folieninhalts (z.B. "Management Summary fuer SAP S/4HANA Migration")
---

Erstelle eine einzelne Praesentationsfolie als PowerPoint-Datei (.pptx) mithilfe der Python-Bibliothek `python-pptx` basierend auf folgender Anforderung:

**Gewuenschter Inhalt:** $ARGUMENTS

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
slide = prs.slides.add_slide(prs.slide_layouts[6])
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

- **Schriftfamilie**: `"Segoe UI"` (Fallback: `"Arial"`)
- **Folientitel**: 28pt, bold, Farbe Dunkelgrau. Einzelne Schluesselwoerter in Orange hervorheben (separater Run im gleichen Paragraph)
- **Untertitel/Sektionsueberschriften**: 18-20pt, semi-bold, Dunkelgrau
- **Fliesstext**: 14-16pt, regular, Dunkelgrau
- **Kleintext/Labels**: 11-12pt, Dunkelgrau oder Mittelgrau

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
run1.font.name = "Segoe UI"

run2 = p.add_run()
run2.text = "Hervorgehobenes Wort"
run2.font.size = Pt(28)
run2.font.bold = True
run2.font.color.rgb = RGBColor(0xEA, 0x5B, 0x0B)  # Orange
run2.font.name = "Segoe UI"
```

---

## Folien-Grundstruktur

Jede Folie muss folgende Elemente enthalten:

### 1. Header-Bereich (oben)

- **Titel**: Links oben, Position `(Inches(0.5), Inches(0.3))`, max. Breite 9 Zoll
- **Logo**: Rechts oben - bestehend aus 4 kleinen Quadraten (2x2 Raster) in Orange/Gold plus dem Text "mindsquare"

Logo-Aufbau:
```python
# Logo-Quadrate (2x2 Raster, oben rechts)
logo_x = Inches(11.5)
logo_y = Inches(0.35)
size = Inches(0.15)
gap = Inches(0.04)

# Oben links - Orange
sq = slide.shapes.add_shape(MSO_SHAPE.RECTANGLE, logo_x, logo_y, size, size)
sq.fill.solid(); sq.fill.fore_color.rgb = RGBColor(0xEA, 0x5B, 0x0B); sq.line.fill.background()

# Oben rechts - Gold
sq = slide.shapes.add_shape(MSO_SHAPE.RECTANGLE, logo_x + size + gap, logo_y, size, size)
sq.fill.solid(); sq.fill.fore_color.rgb = RGBColor(0xFD, 0xC3, 0x00); sq.line.fill.background()

# Unten links - Gold
sq = slide.shapes.add_shape(MSO_SHAPE.RECTANGLE, logo_x, logo_y + size + gap, size, size)
sq.fill.solid(); sq.fill.fore_color.rgb = RGBColor(0xFD, 0xC3, 0x00); sq.line.fill.background()

# Unten rechts - Orange
sq = slide.shapes.add_shape(MSO_SHAPE.RECTANGLE, logo_x + size + gap, logo_y + size + gap, size, size)
sq.fill.solid(); sq.fill.fore_color.rgb = RGBColor(0xEA, 0x5B, 0x0B); sq.line.fill.background()

# Logo-Text
logo_text = slide.shapes.add_textbox(logo_x + 2 * size + 2 * gap + Inches(0.1), logo_y - Inches(0.03), Inches(1.5), Inches(0.4))
tf = logo_text.text_frame
p = tf.paragraphs[0]
p.text = "mindsquare"
p.font.size = Pt(18)
p.font.bold = True
p.font.color.rgb = RGBColor(0x56, 0x56, 0x56)
p.font.name = "Segoe UI"
```

### 2. Gradient-Linie unter dem Titel

Da python-pptx keine echten Farbverlaeufe fuer Linien unterstuetzt, simuliere den Gradient mit mehreren schmalen Rechtecken:

```python
line_y = Inches(1.05)
line_height = Pt(3)
num_segments = 40
total_width = Inches(12.333)
seg_width = total_width / num_segments

for i in range(num_segments):
    ratio = i / (num_segments - 1)
    r = int(0xEA + (0xFD - 0xEA) * ratio)
    g = int(0x5B + (0xC3 - 0x5B) * ratio)
    b = int(0x0B + (0x00 - 0x0B) * ratio)
    seg = slide.shapes.add_shape(
        MSO_SHAPE.RECTANGLE,
        Inches(0.5) + int(seg_width * i), line_y, int(seg_width) + 1, line_height
    )
    seg.fill.solid()
    seg.fill.fore_color.rgb = RGBColor(r, g, b)
    seg.line.fill.background()
```

### 3. Content-Bereich

- **Startposition**: ab `Inches(0.5), Inches(1.4)` (unterhalb der Gradient-Linie)
- **Verfuegbare Breite**: ca. 12.3 Zoll
- **Verfuegbare Hoehe**: ca. 5.5 Zoll (bis zum Footer)
- Hier wird der eigentliche Folieninhalt platziert

### 4. Footer

- **Position**: Rechts unten, `Inches(12.5), Inches(7.05)`
- **Inhalt**: Seitenzahl
- **Schrift**: 11pt, Mittelgrau

```python
footer = slide.shapes.add_textbox(Inches(12.5), Inches(7.05), Inches(0.5), Inches(0.3))
tf = footer.text_frame
p = tf.paragraphs[0]
p.text = "1"
p.font.size = Pt(11)
p.font.color.rgb = RGBColor(0x99, 0x99, 0x99)
p.font.name = "Segoe UI"
p.alignment = PP_ALIGN.RIGHT
```

---

## Design-Prinzipien (Management-Qualitaet)

Halte dich strikt an diese Prinzipien:

1. **Visuelle Hierarchie**: Wichtigstes zuerst, klare Leserichtung von oben links nach unten rechts
2. **Strukturierte Darstellung**: Verwende Spalten-Layouts, Karten-Boxen (Rounded Rectangles), Prozessflows, Vergleichs-Layouts - NIEMALS reine Fliesstextbloecke
3. **Sparsamer Farbeinsatz**: Hauptsaechlich Dunkelgrau (#565656) auf weissem Grund. Orange (#ea5b0b) NUR fuer Akzente, Highlights, wichtige Zahlen. Gold (#fdc300) nur als Sekundaerakzent
4. **Folien-Hintergrund**: Standardmaessig Weiss. Fuer besondere Folien (z.B. Trennfolien) kann ein dunkler Hintergrund verwendet werden
5. **Icons/Piktogramme**: Nutze Unicode-Symbole/Emojis wo passend (z.B. Buch-Emojis, Zahnrad, Rakete, Diagramm etc.)
6. **Professioneller Stil**: Wie von McKinsey/BCG erstellt. Kein visueller Schnickschnack. Klare Linien, geordnete Strukturen
7. **Datenorientiert**: Wo moeglich, konkrete Zahlen, Metriken, KPIs visuell hervorheben
8. **Maximale Raumnutzung**: Der Content-Bereich soll gut gefuellt sein - keine grossen Leerflaechen
9. **Konsistente Abstaende**: Einheitliches Spacing, saubere Ausrichtung
10. **Karten/Boxen-Design**: Verwende `MSO_SHAPE.ROUNDED_RECTANGLE` mit `RGBColor(0xF5, 0xF5, 0xF5)` Hintergrund und `RGBColor(0xE0, 0xE0, 0xE0)` oder Orange Border fuer strukturierte Inhaltsboxen

## Folientypen und Layouts

Waehle je nach Inhalt das passende Layout:

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
p.font.name = "Segoe UI"

p2 = tf.add_paragraph()
p2.text = "Zweite Zeile"
p2.font.size = Pt(12)
p2.font.color.rgb = RGBColor(0x99, 0x99, 0x99)
p2.font.name = "Segoe UI"
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

1. **Dateiname**: Speichere die PowerPoint-Datei im AKTUELLEN Arbeitsverzeichnis als `slide_[kurzer-beschreibender-name].pptx` (z.B. `slide_management_summary.pptx`)
2. **Erzeugung**: Schreibe ein vollstaendiges Python-Script, speichere es temporaer und fuehre es mit `python3` aus, um die .pptx-Datei zu generieren. Loesche das Script nach erfolgreicher Erzeugung.
3. **Qualitaet**: Die Folie muss so aussehen, als waere sie von einer Top-Unternehmensberatung erstellt worden
4. **Inhalt**: Fuelle die Folie mit sinnvollen, plausiblen Inhalten basierend auf der Anforderung. Erfinde realistische Zahlen/Daten wo noetig
5. **Eigenstaendig**: Die .pptx-Datei muss ohne externe Abhaengigkeiten funktionieren
6. **Kompatibilitaet**: Die Datei muss in Microsoft PowerPoint, LibreOffice Impress und Google Slides korrekt dargestellt werden

Generiere JETZT das Python-Script, fuehre es aus und erstelle die PowerPoint-Datei basierend auf der Inhaltsanforderung oben. Gib nach dem Erstellen den Dateipfad aus.
