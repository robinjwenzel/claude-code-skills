# claude-code-skills

Versionskontrollierte Sammlung von Claude Code Skills (Custom Slash Commands).

## Skills

| Skill | Befehl | Beschreibung |
|-------|--------|--------------|
| slide | `/slide` | Erstellt professionelle PowerPoint-Folien im mindsquare CI-Design |
| ihk-auszug | `/ihk-auszug` | Erstellt IHK-PDF-Auszuege aus Langzeitlieferantenerklaerungen |

## Setup

Die Skills werden ueber Symlinks in `~/.claude/commands/` global verfuegbar gemacht:

```bash
ln -s "$(pwd)/skills/slide/slide.md" ~/.claude/commands/slide.md
ln -s "$(pwd)/skills/ihk-auszug/ihk-auszug.md" ~/.claude/commands/ihk-auszug.md
```

## Struktur

Jeder Skill hat einen eigenen Ordner unter `skills/` mit der Skill-Definition und optionalen Assets (Templates, Beispiele).
