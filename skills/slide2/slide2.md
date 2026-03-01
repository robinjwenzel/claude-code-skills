---
name: slide2
description: Management-Praesentation (.pptx) aus fertigem Konzept im mindsquare CI-Design
allowed-tools: Write, Read, Edit, Bash
---

Präsentationskonzept: **$ARGUMENTS**

Skill-Verzeichnis: `/Users/robinwenzel/AI Playground/Claude Code/claude-code-skills/skills/slide2/`
Template: `templates/mindsquare_Folienmaster.pptx`

## Aufgabe

Wandle das gelieferte Konzept in eine fertige `.pptx` um.
Jede Folie bekommt das Layout, das ihre Kernaussage am besten trägt.
Jeder Folientitel ist eine Aussage – kein neutrales Topic-Label.

## Workflow

1. **Konzept analysieren** → Folienanzahl + Kernaussage je Folie extrahieren
   - Lies dazu: `references/ci.md` (Farben, Schriften – immer benötigt)
   - Bei Layoutfragen: `references/layouts.md` (welches Layout für welchen Aussagetyp)

2. **Je Folie HTML bauen** → passendes Layout wählen, konkreten Inhalt einfüllen
   - Bei Folientyp-Umsetzung: `references/snippets.md` (HTML-Vorlagen)

3. **Python-Script schreiben und ausführen**
   - `TOPIC = "..."` oben setzen
   - `HTML_CONTENT = """..."""` mit dem vollständigen HTML-Deck
   - Inhalt von `scripts/converter2.py` **vollständig und unverändert** anhängen
   - Script ausführen → erzeugt `presentation_[slug].html` und `.pptx` im CWD
   - HTML-Datei behalten, Script löschen
