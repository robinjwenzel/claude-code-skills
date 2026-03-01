# claude-code-skills

Versionskontrollierte Sammlung von Claude Code Skills (Custom Slash Commands).

## Skills

| Skill | Befehl | Beschreibung |
|-------|--------|--------------|
| slide | `/slide` | Erstellt professionelle PowerPoint-Folien im mindsquare CI-Design |
| slide2 | `/slide2` | Erweiterte Version des slide-Skills |
| ihk-auszug | `/ihk-auszug` | Erstellt IHK-PDF-Auszuege aus Langzeitlieferantenerklaerungen |
| reflect | `/reflect` | Diktat-Braindump bereinigen und in die Obsidian Daily Note einfuegen |
| diamant | `/diamant` | Buchkapitel-Diamanten interaktiv formulieren und in Obsidian einfuegen |
| key-message-delivered | `/key-message-delivered` | Strukturierte Verkaufsstorys nach Pyramiden-Prinzip erstellen |

## Setup

Die Skills werden ueber Symlinks in `~/.claude/commands/` global verfuegbar gemacht:

```bash
ln -s "$(pwd)/skills/slide/slide.md" ~/.claude/commands/slide.md
ln -s "$(pwd)/skills/slide2/slide2.md" ~/.claude/commands/slide2.md
ln -s "$(pwd)/skills/ihk-auszug/ihk-auszug.md" ~/.claude/commands/ihk-auszug.md
ln -s "$(pwd)/skills/reflect/reflect.md" ~/.claude/commands/reflect.md
ln -s "$(pwd)/skills/diamant/diamant.md" ~/.claude/commands/diamant.md
ln -s "$(pwd)/skills/key-message-delivered/key-message-delivered.md" ~/.claude/commands/key-message-delivered.md
```

> **Hinweis zu Pfaden:** Einige Skills (insbesondere `reflect` und `diamant`) enthalten hardcodierte
> absolute Pfade zum Obsidian-Vault und lokalen Verzeichnissen. Diese Pfade sind persoenlich und
> muessen vor der Nutzung in den jeweiligen Skill-Dateien angepasst werden. Suche dazu nach
> `/Users/` in den `.md`-Dateien unter `skills/`.

## Struktur

Jeder Skill hat einen eigenen Ordner unter `skills/` mit der Skill-Definition und optionalen Assets (Templates, Beispiele).
