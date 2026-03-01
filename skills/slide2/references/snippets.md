# Folientypen-Vorlagen

## Titelfolie

```html
<div class="slide slide-cover">
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="cover-center">
    <h1 class="cover-title">Haupttitel mit <span class="accent">Keyword</span></h1>
    <div class="cover-bar"></div>
    <p class="cover-subtitle">Untertitel | Datum | Anlass</p>
  </div>
  <div class="slide-footer">1</div>
</div>
```

## Standardfolie mit 3 Spalten (Management Summary, Pakete, etc.)

```html
<div class="slide">
  <span class="slide-title">Folientitel mit <span class="accent">Highlight</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content columns-3">

    <div class="card" data-accent="orange">
      <i class="bi bi-bullseye card-icon" data-icon="target"></i>
      <h3>Themenbereich 1</h3>
      <ul>
        <li>Wichtiger Punkt mit konkretem Inhalt</li>
        <li>Zweiter Punkt mit Mehrwert</li>
        <li>Dritter Punkt mit Ergebnis</li>
      </ul>
    </div>

    <div class="card" data-accent="gold">
      <i class="bi bi-gear-fill card-icon gold" data-icon="gear"></i>
      <h3>Themenbereich 2</h3>
      <ul>
        <li>Punkt mit Kontext</li>
        <li>Punkt mit Massnahme</li>
        <li>Punkt mit Auswirkung</li>
      </ul>
    </div>

    <div class="card" data-accent="dark">
      <i class="bi bi-graph-up-arrow card-icon dark" data-icon="chart"></i>
      <h3>Themenbereich 3</h3>
      <ul>
        <li>Ergebnis oder Kennzahl</li>
        <li>Weiterer Punkt</li>
        <li>Abschlussgedanke</li>
      </ul>
    </div>

  </div>
  <div class="slide-footer">2</div>
</div>
```

## Standardfolie mit 2 Spalten

```html
<div class="slide">
  <span class="slide-title">Folientitel</span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content columns-2">

    <div class="card" data-accent="orange">
      <i class="bi bi-exclamation-diamond-fill card-icon" data-icon="warning"></i>
      <h3>Problemstellung</h3>
      <ul>
        <li>Herausforderung 1</li>
        <li>Herausforderung 2</li>
        <li>Herausforderung 3</li>
        <li>Herausforderung 4</li>
      </ul>
    </div>

    <div class="card" data-accent="gold">
      <i class="bi bi-compass-fill card-icon gold" data-icon="compass"></i>
      <h3>Loesungsansatz</h3>
      <ul>
        <li>Massnahme 1</li>
        <li>Massnahme 2</li>
        <li>Massnahme 3</li>
        <li>Massnahme 4</li>
      </ul>
    </div>

  </div>
  <div class="slide-footer">3</div>
</div>
```

## Roadmap / Timeline

```html
<div class="slide">
  <span class="slide-title">Roadmap: <span class="accent">Projektphasen</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content roadmap">

    <div class="phase-row">
      <div class="phase" data-color="orange">Phase 1<br>Jan – Mrz</div>
      <div class="phase" data-color="gold">Phase 2<br>Apr – Jun</div>
      <div class="phase" data-color="dark">Phase 3<br>Jul – Sep</div>
    </div>

    <div class="phase-details">
      <div class="phase-detail">
        <ul>
          <li>Analyse der Ist-Situation</li>
          <li>Stakeholder-Interviews</li>
          <li>Anforderungsaufnahme</li>
          <li>Kick-off Workshop</li>
        </ul>
      </div>
      <div class="phase-detail">
        <ul>
          <li>Konzeptentwicklung</li>
          <li>Prototyp-Erstellung</li>
          <li>Review-Workshops</li>
          <li>Freigabe Fachbereich</li>
        </ul>
      </div>
      <div class="phase-detail">
        <ul>
          <li>Technische Umsetzung</li>
          <li>Testing & QS</li>
          <li>Go-Live Vorbereitung</li>
          <li>Schulung & Rollout</li>
        </ul>
      </div>
    </div>

  </div>
  <div class="slide-footer">4</div>
</div>
```

## KPI-Dashboard

```html
<div class="slide">
  <span class="slide-title">Kennzahlen & <span class="accent">Ergebnisse</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content columns-4">

    <div class="kpi-card">
      <i class="bi bi-graph-up-arrow card-icon" data-icon="chart" style="font-size:24px"></i>
      <div class="kpi-value" data-accent="orange">87%</div>
      <div class="kpi-label">Effizienzsteigerung</div>
      <div class="kpi-desc">vs. Vorjahr</div>
    </div>

    <div class="kpi-card">
      <i class="bi bi-currency-euro card-icon" data-icon="euro" style="font-size:24px"></i>
      <div class="kpi-value" data-accent="gold">2,4 Mio.</div>
      <div class="kpi-label">Kosteneinsparung</div>
      <div class="kpi-desc">p.a. ab Jahr 2</div>
    </div>

    <div class="kpi-card">
      <i class="bi bi-people-fill card-icon" data-icon="people" style="font-size:24px"></i>
      <div class="kpi-value" data-accent="orange">340</div>
      <div class="kpi-label">Betroffene Nutzer</div>
      <div class="kpi-desc">in 12 Standorten</div>
    </div>

    <div class="kpi-card">
      <i class="bi bi-calendar-check card-icon" data-icon="calendar" style="font-size:24px"></i>
      <div class="kpi-value" data-accent="dark">9 Mo.</div>
      <div class="kpi-label">Projektlaufzeit</div>
      <div class="kpi-desc">Jan – Sep 2025</div>
    </div>

  </div>
  <div class="slide-footer">5</div>
</div>
```

## Prozess-Flow

```html
<div class="slide">
  <span class="slide-title">Vorgehensmodell: <span class="accent">5 Schritte</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content process-flow">

    <div class="process-steps">
      <div class="step" data-num="1">
        <div class="step-num">1</div>
        <div class="step-content">
          <h3>Analyse</h3>
          <p>Ist-Aufnahme und Bewertung</p>
        </div>
      </div>
      <div class="step-arrow">›</div>
      <div class="step" data-num="2">
        <div class="step-num">2</div>
        <div class="step-content">
          <h3>Konzept</h3>
          <p>Zielarchitektur definieren</p>
        </div>
      </div>
      <div class="step-arrow">›</div>
      <div class="step" data-num="3">
        <div class="step-num">3</div>
        <div class="step-content">
          <h3>Umsetzung</h3>
          <p>Implementierung & Testing</p>
        </div>
      </div>
      <div class="step-arrow">›</div>
      <div class="step" data-num="4">
        <div class="step-num">4</div>
        <div class="step-content">
          <h3>Rollout</h3>
          <p>Go-Live und Schulung</p>
        </div>
      </div>
      <div class="step-arrow">›</div>
      <div class="step" data-num="5">
        <div class="step-num">5</div>
        <div class="step-content">
          <h3>Betrieb</h3>
          <p>Support und Optimierung</p>
        </div>
      </div>
    </div>

    <div class="step-details-row">
      <div class="step-detail"><ul><li>Workshops</li><li>Interviews</li><li>Gap-Analyse</li></ul></div>
      <div class="step-detail"><ul><li>Prototyp</li><li>Reviews</li><li>Freigabe</li></ul></div>
      <div class="step-detail"><ul><li>Sprint 1-4</li><li>Unit Tests</li><li>UAT</li></ul></div>
      <div class="step-detail"><ul><li>Cutover</li><li>Go-Live</li><li>Hypercare</li></ul></div>
      <div class="step-detail"><ul><li>Ticket-System</li><li>KPI-Reviews</li><li>Optimierung</li></ul></div>
    </div>

  </div>
  <div class="slide-footer">6</div>
</div>
```

## Vergleichs-Layout (Ist vs. Soll, Option A vs. B)

```html
<div class="slide">
  <span class="slide-title">Vergleich: <span class="accent">Optionen im Ueberblick</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content columns-2">

    <div class="vs-box" data-accent="orange">
      <h3>Option A: Eigenentwicklung</h3>
      <ul>
        <li>Maximale Flexibilitaet</li>
        <li>Hoehere Initialkosten (~500k €)</li>
        <li>Laengere Laufzeit (18 Monate)</li>
        <li>Interne Ressourcen erforderlich</li>
        <li>Vollstaendige Kontrolle</li>
      </ul>
    </div>

    <div class="vs-box" data-accent="gold">
      <h3>Option B: Standard-Software</h3>
      <ul>
        <li>Schnelle Einfuehrung (6 Monate)</li>
        <li>Geringere Kosten (~180k €)</li>
        <li>Abhaengigkeit vom Anbieter</li>
        <li>Bewaehrte Best Practices</li>
        <li>Regelmaessige Updates inklusive</li>
      </ul>
    </div>

  </div>
  <div class="slide-footer">7</div>
</div>
```

## Naechste Schritte / Call to Action

```html
<div class="slide">
  <span class="slide-title">Naechste <span class="accent">Schritte</span></span>
  <img class="slide-logo" src="LOGO_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="slide-content next-steps">

    <div class="next-step" data-accent="orange">
      <div class="next-step-date">15. Feb</div>
      <div class="next-step-content">
        <h3>Kick-off Meeting organisieren</h3>
        <p>Alle Stakeholder einladen, Agenda abstimmen, Ressourcen bestaetigen</p>
      </div>
    </div>

    <div class="next-step" data-accent="gold">
      <div class="next-step-date">28. Feb</div>
      <div class="next-step-content">
        <h3>Budgetfreigabe einholen</h3>
        <p>Business Case final abstimmen, CFO-Approval, Projektauftrag unterzeichnen</p>
      </div>
    </div>

    <div class="next-step" data-accent="dark">
      <div class="next-step-date">15. Mrz</div>
      <div class="next-step-content">
        <h3>Projektteam aufstellen</h3>
        <p>Projektleiter benennen, externe Berater beauftragen, Kick-off durchfuehren</p>
      </div>
    </div>

    <div class="next-step" data-accent="orange">
      <div class="next-step-date">01. Apr</div>
      <div class="next-step-content">
        <h3>Analysephase starten</h3>
        <p>Ersten Meilenstein setzen, Ist-Analyse beginnen, Reporting aufsetzen</p>
      </div>
    </div>

  </div>
  <div class="slide-footer">8</div>
</div>
```

## Trennfolie

```html
<div class="slide slide-divider">
  <img class="slide-logo" src="LOGO_WHITE_SRC" alt="mindsquare">
  <div class="gradient-line"></div>
  <div class="divider-center">
    <div class="divider-title">Abschnittstitel mit <span class="accent">Highlight</span></div>
    <div class="divider-subtitle">Kurzer erklaerenden Untertitel</div>
  </div>
  <div class="slide-footer" style="color: #999">3</div>
</div>
```

---

## Praesentationsstruktur (5–10 Folien)

Management und C-Level. McKinsey/BCG Standard. Jede Folie braucht eine klare Kernaussage ("So What?"). Pyramidales Prinzip: Wichtigstes zuerst.

1. **Titelfolie** (`.slide-cover`) — Titel, Datum, Anlass
2. **Management Summary** — 2-3 Spalten, Kernaussagen
3. **Ausgangssituation / Problem** — 2 Spalten: Problem vs. Kontext
4. **Zielsetzung & Scope** — 3 Spalten: Was, Warum, Wie
5. **Loesungsansatz** — Prozess-Flow oder 3-Spalten
6. **Roadmap / Timeline** — Phasen-Pfeile mit Details
7. **Pakete / Deliverables** — Karten-Layout
8. **Budget / Investition** — KPI-Dashboard + Vergleich
9. **Naechste Schritte** — Timeline-Liste
10. **Trennfolie** (`.slide-divider`) — zwischen Hauptbloecken

## Visuelle Regeln

1. **Keine Textbloecke** — immer Karten, Spalten, Prozess-Flows, Vergleiche
2. **Farbdisziplin** — Orange sparsam (Highlights, Akzente). Gold sekundaer. Nie Gruen/Blau ohne Grund
3. **Seitenzahlen** — immer hochzaehlen, 1 bis N
4. **Inhalt** — Fuelle Folien mit sinnvollen, plausiblen Inhalten. Erfinde realistische Zahlen wo noetig
5. **Storyline** — alle Folien erzaehlen eine zusammenhaengende Geschichte: Problem → Loesung → CTA
