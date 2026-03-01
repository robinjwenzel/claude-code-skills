---
name: reflect
description: Diktat-Braindump bereinigen und oben in die Notes-Section der heutigen Obsidian Daily Note einfügen
allowed-tools: Bash, Read, Edit
---

Diktat-Text: **$ARGUMENTS**

Vault-Pfad: `/Users/robinwenzel/Library/Mobile Documents/iCloud~md~obsidian/Documents/2nd Brain`
Daily Note Format: `Calendar/Journal/DD.MM.YYYY.md`

## Workflow

1. **Datum ermitteln** — heutiges Datum via `date "+%d.%m.%Y"` abrufen → Dateipfad zusammensetzen
2. **Text bereinigen** — Diktat-Fehler korrigieren, Satzstruktur glätten, auf Deutsch bleiben
3. **Komprimieren** — strukturierter, prägnanter Markdown-Text; bei Reflexionsinhalt mit `**Reflexion:**`-Block, sonst Freitext mit passendem Datum-Header
4. **Daily Note lesen** — `Read` auf den ermittelten Dateipfad
5. **Eintrag prependen** — `Edit` nutzen, um den bereinigten Text direkt unterhalb von `## Notes` einzufügen (neueste Einträge oben)
6. **Bestätigen** — bereinigten Endtext dem User anzeigen

## Eintrag-Format

```markdown
**28.02.2026** — <bereinigter Text>
```

oder bei längerer Reflexion:

```markdown
**Reflexion (28.02.2026):**
<bereinigter, strukturierter Text>
```

## Regeln
- Sprache: immer Deutsch
- Keine neuen Abschnitte oder Überschriften in der Daily Note anlegen
- Bestehende Struktur der Daily Note nicht verändern
- Nur unter `## Notes` einfügen
