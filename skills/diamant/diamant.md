---
name: diamant
description: Diamant-Gedanken aus Buchkapiteln interaktiv formulieren und in die Obsidian Buchnotiz einfügen
allowed-tools: Bash, Read, Edit
argument-hint: "<Buchtitel> | Kapitel <N> — <Kapitelname> | <roher Gedanke>"
---

Input: **$ARGUMENTS**

Vault: `/Users/robinwenzel/Library/Mobile Documents/iCloud~md~obsidian/Documents/2nd Brain`

## Was ist ein Diamant?

Ein Diamant ist ein komprimierter Kerngedanke aus einem Buchkapitel:
- Er muss so kompakt sein, dass beim späteren Lesen sofort die volle Kernaussage erfasst wird
- Er ist kein Summary, sondern ein pointierter Gedanke, der beim User resoniert hat
- Er darf das Wissen von Claude über das Buch einbeziehen, um den Gedanken zu schärfen

## Phase 1: Interaktion vor dem Schreiben

**Führe Phase 1 immer durch — schreibe niemals direkt in die Note.**

1. **Input parsen** — Buchtitel, Kapitel-Nummer/-Name und rohen Gedanken aus $ARGUMENTS extrahieren
2. **Buchnotiz finden** — `obsidian search query="<Buchtitel>"` → Pfad ermitteln
3. **Buchnotiz lesen** — bestehende Diamanten-Struktur und Kapitel prüfen
4. **Wissen aktivieren** — eigenes Wissen über das Buch und den Autor einbeziehen
5. **Zwei Varianten formulieren** — deutlich unterschiedlich in Tonalität oder Fokus:
   - Variante A: z.B. konkretes Bild zuerst, Pointe am Ende
   - Variante B: z.B. These zuerst, Beweis/Beispiel danach
6. **Challenge stellen** — 1–2 gezielte Rückfragen:
   - Was hat stärker resoniert: das Konzept oder die Konsequenz?
   - Was ist die eine Zeile, die in 2 Jahren den ganzen Gedanken zurückbringt?
   - Gibt es eine wissenschaftliche Gegenperspektive, die den Diamanten bereichert?
7. **Warten** — User wählt Variante, kombiniert, oder gibt neue Richtung vor

## Phase 2: Schreiben

Erst nach User-Bestätigung:

1. **Endformulierung festlegen** — aus User-Feedback finale Version bauen
2. **Einfügeposition bestimmen:**
   - Abschnitt `## Diamanten` in der Buchnotiz
   - Kapitel **chronologisch** (Kapitel 1 vor Kapitel 2 etc.)
   - Neues Kapitel: nach dem letzten bestehenden `### Kapitel X`-Block einfügen, getrennt mit `---`
   - Weiterer Diamant im selben Kapitel: **am Ende** des Kapitel-Blocks anhängen, getrennt mit `---`
   - Neue Diamanten immer **unten** einfügen — niemals oben oder in der Mitte
3. **Schreiben** — `Edit` auf Vault-Pfad
4. **Bestätigen** — User den finalen Text anzeigen

## Struktur-Regeln für die Buchnotiz

```markdown
## Diamanten

### Kapitel 1 — <Name>

<Diamant-Text>

---

<Zweiter Diamant im selben Kapitel falls vorhanden>

---

### Kapitel 2 — <Name>

<Diamant-Text>
```

- Kapitel immer in aufsteigender Reihenfolge (1, 2, 3 ...)
- Neue Diamanten immer **am Ende** des jeweiligen Blocks einfügen — niemals oben oder in der Mitte
- Mehrere Diamanten im selben Kapitel: jeden einzelnen mit `---` davor und danach visuell abgrenzen
- Zwischen Kapiteln ebenfalls `---`
- Callouts (`> [!note]`) für Gegenthesen oder Synthesen nutzen, wenn sinnvoll
- Tabellen für Pro/Contra-Gegenüberstellungen nutzen, wenn sinnvoll
