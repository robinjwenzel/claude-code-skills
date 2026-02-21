---
name: slide
description: Management-Praesentation (.pptx) im mindsquare CI-Design
allowed-tools: Write, Read, Edit, Bash
---

Praesentation zu: **$ARGUMENTS**

Skill-Verzeichnis: `/Users/robinwenzel/AI Playground/Claude Code/claude-code-skills/skills/slide/`

Lies vor dem Start:
- `references/ci.md` — Farbpalette, HTML-CSS-Skelett, Icon-System
- `references/snippets.md` — Folientypen-Vorlagen, Praesentationsstruktur, Design-Regeln
- `scripts/converter.py` — Python-Converter (Ausführungslogik ist bereits am Ende enthalten)

## Workflow

1. **HTML-Foliendeck** (5–10 Folien) mit echtem, themenspezifischem Inhalt erstellen — Consulting-Qualitaet, keine generischen Platzhalter
2. **Python-Script** schreiben: `TOPIC = "..."` oben → `HTML_CONTENT = """..."""` → Inhalt von `converter.py` **vollstaendig und unveraendert** einfuegen
3. Script **ausfuehren** → erzeugt `presentation_[slug].html` und `.pptx` im CWD → HTML-Datei behalten, Script loeschen
