# mindsquare CI-Design Referenz

## Farbpalette

| Farbe | RGB-Wert | CSS-Variable | Verwendung |
|-------|----------|--------------|------------|
| Orange | `RGBColor(0xEA, 0x5B, 0x0B)` | `--orange: #EA5B0B` | Primaerfarbe, Highlights, Akzente |
| Gelb/Gold | `RGBColor(0xFD, 0xC3, 0x00)` | `--gold: #FDC300` | Sekundaerfarbe, Akzente |
| Dunkelgrau | `RGBColor(0x56, 0x56, 0x56)` | `--dark: #565656` | Fliesstext, Ueberschriften |
| Hellgrau | `RGBColor(0xCC, 0xCC, 0xCC)` | `--lgray: #CCCCCC` | Trennlinien, dezente Strukturen |
| Hintergrund Hellgrau | `RGBColor(0xF5, 0xF5, 0xF5)` | `--bgray: #F5F5F5` | Karten-Hintergrund |
| Weiss | `RGBColor(0xFF, 0xFF, 0xFF)` | `--white: #FFFFFF` | Folien-Hintergrund, Text auf Dunkel |
| Mittelgrau | `RGBColor(0x99, 0x99, 0x99)` | `--mgray: #999999` | Kleintext, Labels, Footer |

**CI-Regel**: Hauptsaechlich Dunkelgrau auf Weiss. Orange NUR fuer Akzente/Highlights. Gold als Sekundaerakzent. Andere Farben (Gruen, Blau) nur in Ausnahmefaellen.

## Typografie

- **Titel-Schriftart**: `"Poppins"` Bold — Folientitel, Sektionsueberschriften, grosse Labels
- **Body-Schriftart**: `"Calibri"` — Fliesstext, Labels, Footer
- **Folientitel**: 20pt Bold Poppins Dunkelgrau, einzelne Woerter mit `.accent` in Orange hervorheben
- **Sektionsueberschriften**: 14-16pt Bold Poppins Dunkelgrau
- **Grosse KPI-Zahlen**: 36-48pt Bold Poppins Orange
- **Fliesstext/Bullets**: 11-13pt Calibri Dunkelgrau
- **Footer**: 11pt Calibri Mittelgrau

## HTML-Grundgeruest

```html
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
<style>
/* ===== CI-Variablen ===== */
:root {
  --orange: #EA5B0B; --gold: #FDC300;
  --dark:   #565656; --lgray: #CCCCCC;
  --bgray:  #F5F5F5; --mgray: #999999;
  --white:  #FFFFFF;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body { background: #C8C8C8; padding: 40px; font-family: 'Calibri','Segoe UI',sans-serif; }

/* ===== Folie (exakt 1333×750 px = 13.333"×7.5" bei 100px/Zoll) ===== */
.slide {
  width: 1333px; height: 750px; background: var(--white);
  position: relative; overflow: hidden;
  margin: 32px auto;
  box-shadow: 0 8px 40px rgba(0,0,0,0.25);
}

/* ===== Header ===== */
.slide-logo {
  position: absolute; right: 24px; top: 15px; height: 50px;
}
.slide-title {
  position: absolute; left: 50px; top: 28px;
  font-family: 'Poppins', sans-serif; font-size: 20px; font-weight: 700;
  color: var(--dark); white-space: nowrap; line-height: 1.2;
}
.slide-title .accent { color: var(--orange); }
.gradient-line {
  position: absolute; left: 20px; top: 84px;
  width: calc(100% - 40px); height: 3px;
  background: linear-gradient(to right, var(--orange), var(--gold));
  border-radius: 2px;
}

/* ===== Content-Bereich (ab Y=104px, bis Y=714px) ===== */
.slide-content {
  position: absolute;
  top: 104px; left: 50px; right: 50px; bottom: 36px;
}

/* ===== Spalten-Layouts ===== */
.columns-2, .columns-3, .columns-4 {
  display: grid; gap: 16px; height: 100%;
}
.columns-2 { grid-template-columns: 1fr 1fr; }
.columns-3 { grid-template-columns: 1fr 1fr 1fr; }
.columns-4 { grid-template-columns: 1fr 1fr 1fr 1fr; }

/* ===== Karten ===== */
.card {
  background: var(--bgray); border-radius: 10px; padding: 20px 20px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.08);
  border-top: 3px solid var(--orange);
  display: flex; flex-direction: column; gap: 10px;
}
.card[data-accent="gold"]  { border-top-color: var(--gold); }
.card[data-accent="dark"]  { border-top-color: var(--dark); }

.card-icon {
  font-size: 28px; color: var(--orange); line-height: 1;
}
.card-icon.gold  { color: var(--gold); }
.card-icon.dark  { color: var(--dark); }

.card h3 {
  font-family: 'Poppins', sans-serif; font-size: 15px; font-weight: 700;
  color: var(--dark); margin: 0;
}
.card ul { list-style: none; padding: 0; margin: 0; }
.card ul li {
  font-size: 12.5px; color: var(--dark);
  padding: 3px 0 3px 16px; position: relative; line-height: 1.4;
}
.card ul li::before {
  content: ''; position: absolute; left: 0; top: 9px;
  width: 6px; height: 6px; border-radius: 50%; background: var(--orange);
}
.card[data-accent="gold"] ul li::before  { background: var(--gold); }
.card[data-accent="dark"]  ul li::before { background: var(--dark); }

/* ===== KPI-Karte ===== */
.kpi-card {
  background: var(--bgray); border-radius: 10px; padding: 20px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.08);
  border-top: 3px solid var(--orange);
  display: flex; flex-direction: column; align-items: center;
  justify-content: center; gap: 6px; text-align: center;
}
.kpi-value {
  font-family: 'Poppins', sans-serif; font-size: 48px; font-weight: 700;
  color: var(--orange); line-height: 1;
}
.kpi-value[data-accent="gold"] { color: var(--gold); }
.kpi-value[data-accent="dark"] { color: var(--dark); }
.kpi-label {
  font-family: 'Poppins', sans-serif; font-size: 13px; font-weight: 700;
  color: var(--dark);
}
.kpi-desc { font-size: 11px; color: var(--mgray); }

/* ===== Roadmap / Phasen-Pfeile ===== */
.roadmap { display: flex; flex-direction: column; gap: 14px; height: 100%; }
.phase-row { display: flex; gap: 6px; height: 90px; flex-shrink: 0; }
.phase {
  flex: 1; background: var(--orange); color: var(--white);
  font-family: 'Poppins', sans-serif; font-size: 12px; font-weight: 700;
  display: flex; align-items: center; justify-content: center;
  text-align: center; padding: 0 28px; line-height: 1.3;
  clip-path: polygon(0 0, calc(100% - 18px) 0, 100% 50%, calc(100% - 18px) 100%, 0 100%, 18px 50%);
}
.phase:first-child {
  clip-path: polygon(0 0, calc(100% - 18px) 0, 100% 50%, calc(100% - 18px) 100%, 0 100%);
}
.phase:last-child {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%, 18px 50%);
}
.phase[data-color="gold"] { background: var(--gold); color: var(--dark); }
.phase[data-color="dark"] { background: var(--dark); color: var(--white); }

.phase-details { display: flex; gap: 6px; flex: 1; }
.phase-detail {
  flex: 1; background: var(--bgray); border-radius: 8px;
  padding: 12px 14px; overflow: hidden;
}
.phase-detail ul { list-style: none; padding: 0; }
.phase-detail ul li {
  font-size: 11.5px; color: var(--dark); padding: 2px 0 2px 14px; position: relative;
}
.phase-detail ul li::before {
  content: ''; position: absolute; left: 0; top: 8px;
  width: 5px; height: 5px; border-radius: 50%; background: var(--orange);
}

/* ===== Prozess-Flow ===== */
.process-flow { display: flex; flex-direction: column; gap: 12px; height: 100%; }
.process-steps { display: flex; gap: 0; align-items: flex-start; height: 110px; }
.step {
  flex: 1; background: var(--orange); border-radius: 8px;
  padding: 14px 14px 14px 14px; color: var(--white);
  display: flex; gap: 10px; align-items: flex-start;
  position: relative;
}
.step-num {
  font-family: 'Poppins', sans-serif; font-size: 26px; font-weight: 700;
  color: rgba(255,255,255,0.9); flex-shrink: 0; line-height: 1;
}
.step-content h3 {
  font-family: 'Poppins', sans-serif; font-size: 13px; font-weight: 700;
  color: var(--white); margin-bottom: 4px;
}
.step-content p { font-size: 11px; color: rgba(255,255,255,0.85); line-height: 1.4; }
.step-arrow {
  width: 28px; flex-shrink: 0; height: 110px;
  display: flex; align-items: center; justify-content: center;
  font-size: 20px; color: var(--dark);
}
.step-details-row { display: flex; gap: 6px; flex: 1; }
.step-detail { flex: 1; padding: 0 4px; }
.step-detail ul { list-style: none; padding: 0; }
.step-detail ul li {
  font-size: 11.5px; color: var(--dark); padding: 2px 0 2px 14px; position: relative;
}
.step-detail ul li::before {
  content: ''; position: absolute; left: 0; top: 8px;
  width: 5px; height: 5px; border-radius: 50%; background: var(--orange);
}

/* ===== Vergleichs-Layout ===== */
.vs-box {
  background: var(--bgray); border-radius: 10px; padding: 20px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.08);
  display: flex; flex-direction: column; gap: 8px;
}
.vs-box h3 {
  font-family: 'Poppins', sans-serif; font-size: 15px; font-weight: 700;
  color: var(--orange); padding-bottom: 8px;
  border-bottom: 2px solid var(--lgray); margin-bottom: 4px;
}
.vs-box[data-accent="gold"] h3 { color: var(--gold); }
.vs-box[data-accent="dark"]  h3 { color: var(--dark); }
.vs-box ul { list-style: none; padding: 0; }
.vs-box ul li {
  font-size: 12px; color: var(--dark); padding: 3px 0 3px 16px; position: relative;
}
.vs-box ul li::before {
  content: ''; position: absolute; left: 0; top: 9px;
  width: 6px; height: 6px; border-radius: 50%; background: var(--orange);
}

/* ===== Titelfolie ===== */
.slide-cover .cover-center {
  position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
  text-align: center; width: 900px;
}
.slide-cover .cover-title {
  font-family: 'Poppins', sans-serif; font-size: 44px; font-weight: 700;
  color: var(--dark); line-height: 1.2; margin-bottom: 0;
}
.slide-cover .cover-title .accent { color: var(--orange); }
.slide-cover .cover-bar {
  width: 200px; height: 4px; margin: 22px auto;
  background: linear-gradient(to right, var(--orange), var(--gold));
  border-radius: 2px;
}
.slide-cover .cover-subtitle {
  font-family: 'Poppins', sans-serif; font-size: 18px;
  color: var(--mgray); line-height: 1.4;
}

/* ===== Trennfolie ===== */
.slide-divider { background: var(--dark); }
.slide-divider .gradient-line {
  background: linear-gradient(to right, var(--orange), var(--gold));
}
.divider-center {
  position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
  text-align: center; width: 900px;
}
.divider-title {
  font-family: 'Poppins', sans-serif; font-size: 38px; font-weight: 700;
  color: var(--white); line-height: 1.3;
}
.divider-title .accent { color: var(--orange); }
.divider-subtitle {
  font-size: 18px; color: var(--lgray); margin-top: 14px;
}

/* ===== Footer ===== */
.slide-footer {
  position: absolute; bottom: 10px; right: 24px;
  font-size: 11px; color: var(--mgray);
}

/* ===== Highlight-Box / Callout ===== */
.highlight-box {
  background: var(--orange); border-radius: 10px; padding: 16px 20px;
  color: var(--white);
}
.highlight-box h3 {
  font-family: 'Poppins', sans-serif; font-size: 14px; font-weight: 700;
  color: var(--white); margin-bottom: 6px;
}
.highlight-box p { font-size: 12px; color: rgba(255,255,255,0.9); }

/* ===== Naechste-Schritte / Timeline-Liste ===== */
.next-steps { display: flex; flex-direction: column; gap: 10px; height: 100%; }
.next-step {
  display: flex; gap: 16px; align-items: flex-start; padding: 12px 16px;
  background: var(--bgray); border-radius: 8px; flex: 1;
  border-left: 4px solid var(--orange);
}
.next-step[data-accent="gold"] { border-left-color: var(--gold); }
.next-step[data-accent="dark"] { border-left-color: var(--dark); }
.next-step-date {
  font-family: 'Poppins', sans-serif; font-size: 13px; font-weight: 700;
  color: var(--orange); flex-shrink: 0; min-width: 90px;
}
.next-step[data-accent="gold"] .next-step-date { color: var(--gold); }
.next-step-content h3 {
  font-family: 'Poppins', sans-serif; font-size: 13px; font-weight: 700;
  color: var(--dark); margin-bottom: 2px;
}
.next-step-content p { font-size: 11.5px; color: var(--mgray); }
</style>
</head>
<body>

<!-- =============================== -->
<!-- ALLE FOLIEN HIER EINFUEGEN      -->
<!-- =============================== -->

</body>
</html>
```

## Icon-System (HTML → PPTX)

Im HTML: Bootstrap Icons via CDN — `<i class="bi bi-NAME" data-icon="KEY"></i>`
Im PPTX: Der Converter liest `data-icon` und ruft die passende Hilfsfunktion auf.

| Konzept | Bootstrap Icon | `data-icon` Wert | PPTX-Shape |
|---------|---------------|------------------|------------|
| Ziel/Fokus | `bi-bullseye` | `target` | Konzentrische Kreise |
| Prozess/Technik | `bi-gear-fill` | `gear` | `GEAR_6` |
| Geschwindigkeit | `bi-lightning-fill` | `lightning` | `LIGHTNING_BOLT` |
| Person | `bi-person-fill` | `person` | Kopf + Trapez |
| Team | `bi-people-fill` | `people` | 3-Personen-Gruppe |
| Wachstum/Chart | `bi-graph-up-arrow` | `chart` | 3 Balken |
| Warnung | `bi-exclamation-diamond-fill` | `warning` | `DIAMOND` |
| Dokument | `bi-file-earmark-text-fill` | `document` | `FLOWCHART_DOCUMENT` |
| Richtung | `bi-compass-fill` | `compass` | `PENTAGON` |
| Kreislauf | `bi-arrow-repeat` | `cycle` | `CIRCULAR_ARROW` |
| Trichter | `bi-funnel-fill` | `funnel` | `FUNNEL` |
| Baustein | `bi-boxes` | `cube` | `CUBE` |
| Haekchen | `bi-check-circle-fill` | `check` | `FLOWCHART_PROCESS` |
| Budget/Euro | `bi-currency-euro` | `euro` | `OVAL` |
| Kalender | `bi-calendar-check` | `calendar` | `FLOWCHART_DOCUMENT` |
