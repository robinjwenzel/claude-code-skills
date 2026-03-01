# Layoutwahl nach Aussagetyp

Für jede Folie: Welche Kernaussage hat sie? → Passendes Layout wählen.

| Aussagetyp | Layout | Snippet-Klasse |
|-----------|--------|----------------|
| 3 parallele Punkte / Pakete / Themenbereiche | 3-Spalten-Karten | `columns-3` mit `.card` |
| 4 parallele Punkte / Kennzahlen | 4-Spalten | `columns-4` mit `.card` oder `.kpi-card` |
| 2 Optionen / Vergleich / Ist vs. Soll | Vergleichs-Layout | `columns-2` mit `.vs-box` |
| Zeitlicher Ablauf / Projektphasen | Roadmap | `.roadmap` mit `.phase-row` + `.phase-details` |
| Messergebnis / Zahlen / KPIs | KPI-Dashboard | `columns-4` mit `.kpi-card` |
| Schritt-für-Schritt / Prozess | Prozess-Flow | `.process-flow` mit `.process-steps` |
| Handlungsaufforderung / Nächste Schritte | Nächste-Schritte-Liste | `.next-steps` mit `.next-step` |
| Abschnittstrennung / Kapitelübergang | Trennfolie | `.slide.slide-divider` |
| Einstieg / Titel | Titelfolie | `.slide.slide-cover` |
| Problem + Lösung (2-teilig) | 2-Spalten-Karten | `columns-2` mit `.card` |

## Entscheidungsregeln

- **Zahl von Elementen bestimmt Spalten**: 2 Elemente → `columns-2`, 3 → `columns-3`, 4 → `columns-4`
- **Vergleich immer mit `.vs-box`**, nicht mit `.card` — `.vs-box` hat farbigen Titel statt Icon
- **Zahlen/KPIs immer mit `.kpi-card`** — große Zahl, Label, Beschreibung
- **Zeitliche Abfolge → Roadmap**, logische Abfolge → Prozess-Flow
- **Jede Folie hat exakt eine Kernaussage** im Titel (Verb + Ergebnis, kein neutrales Label)

## Beispiele für Aussage-Titel

| Schlecht (Topic) | Gut (Aussage) |
|-----------------|---------------|
| Projektstatus | Projekt liegt im Plan – alle 3 Meilensteine erreicht |
| Kosten | Investition von 400k € amortisiert sich in 18 Monaten |
| Nächste Schritte | Drei Maßnahmen bis Ende Q1 sichern den Projekterfolg |
| Ausgangssituation | Manuelle Prozesse kosten 2.400 Stunden pro Jahr |
