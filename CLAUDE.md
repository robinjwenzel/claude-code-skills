# Claude Code Skills Repository

Dieses Repository verwaltet alle Claude Code Skills (Custom Slash Commands) unter Versionskontrolle.

## Struktur

```
skills/
├── slide/          # PowerPoint-Folien im mindsquare CI-Design
│   ├── slide.md
│   └── templates/  # PPTX-Vorlagen
└── ihk-auszug/     # IHK-Auszug aus Langzeitlieferantenerklaerungen
    └── ihk-auszug.md
```

## Wie Skills funktionieren

- Skill-Definitionen liegen als `.md`-Dateien unter `skills/<name>/`
- Symlinks in `~/.claude/commands/` machen sie global verfuegbar
- Zugehoerige Assets (Templates, Beispiele) liegen im jeweiligen Skill-Ordner

## Neuen Skill hinzufuegen

1. `mkdir skills/<name>/`
2. Skill-Datei erstellen: `skills/<name>/<name>.md`
3. Symlink: `ln -s "$(pwd)/skills/<name>/<name>.md" ~/.claude/commands/`
4. Committen und pushen

## Commit-Konvention

- `slide: <Beschreibung>` -- Slide-Skill
- `ihk: <Beschreibung>` -- IHK-Skill
- `docs: <Beschreibung>` -- Dokumentation
- `repo: <Beschreibung>` -- Repository-Struktur/Config

## Branching

- **main** = stabiler Stand
- **feature/<skill>-<feature>** = groessere Aenderungen
