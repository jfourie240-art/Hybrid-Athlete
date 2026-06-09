<Index.html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hybrid Athlete — 6 Month Program</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,700;1,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --dark: #111214;
    --card: #18191d;
    --border: #2a2b2f;
    --accent: #e8ff47;
    --accent2: #ff6b35;
    --accent3: #4fc3f7;
    --text: #e8e8e6;
    --muted: #7a7b80;
    --red: #ff4444;
    --green: #52c97a;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 60px;
    position: relative;
    overflow: hidden;
    background: linear-gradient(160deg, #0a0a0a 0%, #111520 50%, #0a0f0a 100%);
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -200px; right: -200px;
    width: 700px; height: 700px;
    background: radial-gradient(circle, rgba(232,255,71,0.06) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: -100px; left: -100px;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(255,107,53,0.05) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .hero h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(72px, 12vw, 160px);
    line-height: 0.9;
    letter-spacing: 0.02em;
    color: var(--text);
    margin-bottom: 30px;
  }

  .hero h1 span { color: var(--accent); }

  .hero-stats {
    display: flex;
    gap: 40px;
    flex-wrap: wrap;
    margin-top: 40px;
  }

  .hero-stat {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .hero-stat .val {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 36px;
    color: var(--accent);
    line-height: 1;
  }

  .hero-stat .label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
  }

  .hero-divider {
    width: 60px;
    height: 2px;
    background: var(--accent);
    margin: 30px 0;
  }

  /* NAV TABS */
  .nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(10,10,10,0.95);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    padding: 0 60px;
    display: flex;
    gap: 0;
    overflow-x: auto;
  }

  .nav-btn {
    padding: 18px 24px;
    background: none;
    border: none;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .nav-btn:hover { color: var(--text); }
  .nav-btn.active { color: var(--accent); border-bottom-color: var(--accent); }

  /* SECTIONS */
  .section { display: none; padding: 60px; }
  .section.active { display: block; }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(36px, 5vw, 64px);
    letter-spacing: 0.03em;
    margin-bottom: 8px;
  }

  .section-sub {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 48px;
  }

  /* PHASE CARDS */
  .phases {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2px;
    margin-bottom: 48px;
  }

  .phase-card {
    background: var(--card);
    padding: 32px;
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s;
  }

  .phase-card:hover { border-color: var(--accent); }
  .phase-card.active-phase { border-color: var(--accent); background: #1a1c14; }

  .phase-card::before {
    content: attr(data-num);
    position: absolute;
    top: -10px; right: 16px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 100px;
    color: rgba(255,255,255,0.03);
    line-height: 1;
    pointer-events: none;
  }

  .phase-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .phase-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 0.05em;
    margin-bottom: 12px;
  }

  .phase-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 20px;
  }

  .phase-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tag {
    padding: 4px 10px;
    border: 1px solid var(--border);
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.1em;
    color: var(--muted);
    border-radius: 2px;
  }

  .tag.lift { border-color: var(--accent); color: var(--accent); }
  .tag.cardio { border-color: var(--accent3); color: var(--accent3); }
  .tag.hybrid { border-color: var(--accent2); color: var(--accent2); }

  /* WEEK SCHEDULE */
  .schedule-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 2px;
    margin-bottom: 48px;
  }

  .day-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 20px 16px;
    min-height: 160px;
  }

  .day-name {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .day-badge {
    display: inline-block;
    padding: 3px 8px;
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.1em;
    border-radius: 2px;
    margin-bottom: 8px;
    font-weight: 500;
  }

  .badge-push { background: rgba(232,255,71,0.15); color: var(--accent); border: 1px solid rgba(232,255,71,0.3); }
  .badge-pull { background: rgba(79,195,247,0.12); color: var(--accent3); border: 1px solid rgba(79,195,247,0.3); }
  .badge-legs { background: rgba(255,107,53,0.12); color: var(--accent2); border: 1px solid rgba(255,107,53,0.3); }
  .badge-cardio { background: rgba(82,201,122,0.12); color: var(--green); border: 1px solid rgba(82,201,122,0.3); }
  .badge-rest { background: rgba(255,255,255,0.04); color: var(--muted); border: 1px solid var(--border); }
  .badge-hybrid { background: rgba(255,68,68,0.1); color: var(--red); border: 1px solid rgba(255,68,68,0.3); }

  .day-detail {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.6;
  }

  /* PHASE DETAIL */
  .phase-detail {
    display: none;
    background: var(--card);
    border: 1px solid var(--border);
    padding: 40px;
    margin-bottom: 48px;
  }

  .phase-detail.visible { display: block; }

  .detail-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 32px;
  }

  @media (max-width: 768px) {
    .detail-grid { grid-template-columns: 1fr; }
    .schedule-grid { grid-template-columns: repeat(4, 1fr); }
    .hero, .section, .nav { padding-left: 24px; padding-right: 24px; }
    .hero-stats { gap: 20px; }
  }

  .detail-block h4 {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
  }

  .detail-list {
    list-style: none;
  }

  .detail-list li {
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 13px;
    display: flex;
    justify-content: space-between;
    gap: 12px;
  }

  .detail-list li:last-child { border-bottom: none; }

  .detail-list .li-label { color: var(--muted); }
  .detail-list .li-val { color: var(--text); text-align: right; font-weight: 500; }

  /* WORKOUTS TABLE */
  .workout-block {
    margin-bottom: 40px;
  }

  .workout-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 16px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--border);
  }

  .workout-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 24px;
    letter-spacing: 0.05em;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }

  th {
    text-align: left;
    padding: 10px 14px;
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    border-bottom: 1px solid var(--border);
  }

  td {
    padding: 12px 14px;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    color: var(--text);
    vertical-align: top;
  }

  tr:last-child td { border-bottom: none; }
  tr:hover td { background: rgba(255,255,255,0.02); }

  td .note { font-size: 11px; color: var(--muted); margin-top: 3px; }

  /* NUTRITION */
  .macro-bar {
    margin-bottom: 32px;
  }

  .macro-row {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 12px;
  }

  .macro-name {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    width: 100px;
    color: var(--muted);
  }

  .macro-track {
    flex: 1;
    height: 6px;
    background: var(--border);
    border-radius: 3px;
    overflow: hidden;
  }

  .macro-fill {
    height: 100%;
    border-radius: 3px;
    transition: width 1s ease;
  }

  .fill-protein { background: var(--accent); width: 38%; }
  .fill-carbs { background: var(--accent3); width: 32%; }
  .fill-fat { background: var(--accent2); width: 30%; }

  .macro-val {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: var(--text);
    width: 80px;
    text-align: right;
  }

  .meal-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 16px;
    margin-bottom: 40px;
  }

  .meal-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 24px;
  }

  .meal-time {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .meal-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20px;
    letter-spacing: 0.05em;
    margin-bottom: 12px;
  }

  .meal-items {
    list-style: none;
    font-size: 13px;
    color: var(--muted);
    line-height: 2;
  }

  .meal-items li::before {
    content: '— ';
    color: var(--border);
  }

  .meal-kcal {
    margin-top: 14px;
    padding-top: 14px;
    border-top: 1px solid var(--border);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    display: flex;
    justify-content: space-between;
  }

  .meal-kcal span { color: var(--text); }

  /* CALLOUT */
  .callout {
    background: rgba(232,255,71,0.05);
    border: 1px solid rgba(232,255,71,0.2);
    border-left: 3px solid var(--accent);
    padding: 20px 24px;
    margin-bottom: 24px;
    font-size: 13px;
    line-height: 1.7;
  }

  .callout strong { color: var(--accent); }

  .callout-red {
    background: rgba(255,68,68,0.05);
    border-color: rgba(255,68,68,0.2);
    border-left-color: var(--red);
  }
  .callout-red strong { color: var(--red); }

  .callout-blue {
    background: rgba(79,195,247,0.05);
    border-color: rgba(79,195,247,0.2);
    border-left-color: var(--accent3);
  }
  .callout-blue strong { color: var(--accent3); }

  /* PROGRESS */
  .timeline {
    position: relative;
    padding-left: 32px;
    margin-bottom: 48px;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 8px; top: 8px; bottom: 0;
    width: 1px;
    background: var(--border);
  }

  .tl-item {
    position: relative;
    margin-bottom: 40px;
  }

  .tl-item::before {
    content: '';
    position: absolute;
    left: -28px; top: 6px;
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--accent);
    border: 2px solid var(--black);
    box-shadow: 0 0 0 2px var(--accent);
  }

  .tl-month {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .tl-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 0.04em;
    margin-bottom: 8px;
  }

  .tl-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.7;
  }

  /* METRIC CHIPS */
  .metric-row {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 40px;
  }

  .metric-chip {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 16px 20px;
    display: flex;
    flex-direction: column;
    gap: 4px;
    min-width: 120px;
  }

  .chip-val {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    color: var(--accent);
    line-height: 1;
  }

  .chip-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* FOOTER */
  footer {
    padding: 40px 60px;
    border-top: 1px solid var(--border);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
  }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow">Personalised 6-Month Protocol · Johan · 2026</div>
  <h1>HYBRID<br><span>ATHLETE</span></h1>
  <div class="hero-divider"></div>
  <div style="font-size:14px; color:var(--muted); max-width:560px; line-height:1.8;">
    Body recomposition focus. Advanced lifter. Cardiovascular base-build. 6 days per week, mornings. Built around red meat, chicken, and your existing eating window.
  </div>
  <div class="hero-stats">
    <div class="hero-stat"><div class="val">120kg</div><div class="label">Start weight</div></div>
    <div class="hero-stat"><div class="val">1.89m</div><div class="label">Height</div></div>
    <div class="hero-stat"><div class="val">6</div><div class="label">Days / week</div></div>
    <div class="hero-stat"><div class="val">6</div><div class="label">Months</div></div>
    <div class="hero-stat"><div class="val">~12kg</div><div class="label">Target fat loss</div></div>
  </div>
</div>

<!-- NAV -->
<nav class="nav">
  <button class="nav-btn active" onclick="showSection('overview')">Overview</button>
  <button class="nav-btn" onclick="showSection('training')">Training</button>
  <button class="nav-btn" onclick="showSection('workouts')">Workouts</button>
  <button class="nav-btn" onclick="showSection('nutrition')">Nutrition</button>
  <button class="nav-btn" onclick="showSection('progression')">Progression</button>
</nav>

<!-- OVERVIEW -->
<section id="overview" class="section active">
  <div class="section-title">PROGRAM OVERVIEW</div>
  <div class="section-sub">6-Phase Periodised Recomposition Protocol</div>

  <div class="callout">
    <strong>Your profile in short:</strong> You have a strong muscular base with centralised abdominal fat — this is primarily driven by cortisol and insulin dynamics, not just calories. The strategy is to <strong>lift heavy to preserve muscle</strong>, build a cardio engine progressively, and <strong>time carbs around training</strong> to force fuel partitioning toward muscle over fat storage. Your existing eating window (11:30–18:30) is your biggest metabolic asset — we keep it.
  </div>

  <div class="metric-row">
    <div class="metric-chip"><div class="chip-val">3,100</div><div class="chip-label">Est. TDEE (kcal)</div></div>
    <div class="metric-chip"><div class="chip-val">2,600</div><div class="chip-label">Target intake</div></div>
    <div class="metric-chip"><div class="chip-val">~500</div><div class="chip-label">Daily deficit</div></div>
    <div class="metric-chip"><div class="chip-val">200g+</div><div class="chip-label">Protein target</div></div>
    <div class="metric-chip"><div class="chip-val">6:00</div><div class="chip-label">Train time</div></div>
    <div class="metric-chip"><div class="chip-val">90min</div><div class="chip-label">Session cap</div></div>
  </div>

  <div class="phases">
    <div class="phase-card" data-num="1" onclick="selectPhase(1)">
      <div class="phase-label">Month 1–2</div>
      <div class="phase-name">FOUNDATION</div>
      <div class="phase-desc">Build the engine. Establish lifting cadence, introduce Zone 2 cardio, fix nutrition timing. Low intensity, high consistency.</div>
      <div class="phase-tags">
        <span class="tag lift">Hypertrophy</span>
        <span class="tag cardio">Zone 2</span>
      </div>
    </div>
    <div class="phase-card" data-num="2" onclick="selectPhase(2)">
      <div class="phase-label">Month 3–4</div>
      <div class="phase-name">DEVELOPMENT</div>
      <div class="phase-desc">Increase cardio modalities. Add rowing and running. Introduce hybrid sessions. Lift intensity climbs.</div>
      <div class="phase-tags">
        <span class="tag lift">Strength</span>
        <span class="tag cardio">Zone 2+3</span>
        <span class="tag hybrid">Hybrid</span>
      </div>
    </div>
    <div class="phase-card" data-num="3" onclick="selectPhase(3)">
      <div class="phase-label">Month 5–6</div>
      <div class="phase-name">PERFORMANCE</div>
      <div class="phase-desc">Full hybrid expression. HIIT, longer runs, strength peaks. Compete with yourself. Push body recomposition to maximum.</div>
      <div class="phase-tags">
        <span class="tag lift">Power</span>
        <span class="tag cardio">HIIT</span>
        <span class="tag hybrid">Hybrid</span>
      </div>
    </div>
  </div>

  <div id="phase-detail" class="phase-detail">
    <!-- populated by JS -->
  </div>

  <div class="callout callout-red">
    <strong>Weekend protocol:</strong> This is your biggest variable. The goal isn't restriction — it's <strong>damage control</strong>. Guidelines: eat a high-protein meal before going out, avoid drinking on an empty stomach, prioritise sleep over extra drinks, and add a 30-min low-intensity cardio session Sunday morning to kickstart recovery. You don't need to be perfect — you need a floor.
  </div>
</section>

<!-- TRAINING -->
<section id="training" class="section">
  <div class="section-title">WEEKLY STRUCTURE</div>
  <div class="section-sub">Phase 1–2 · Foundation Schedule</div>

  <div class="callout callout-blue">
    <strong>Lifting split:</strong> Push / Pull / Legs across 6 days, with cardio embedded into each session (either as a warm-up or a standalone block). Sunday is active recovery — walk, sauna, steam room.
  </div>

  <div class="schedule-grid">
    <div class="day-card">
      <div class="day-name">Mon</div>
      <div class="day-badge badge-push">Push A</div>
      <div class="day-detail">Chest, Shoulders, Triceps<br><br>+ 20min Zone 2<br>(bike warm-up)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Tue</div>
      <div class="day-badge badge-cardio">Cardio</div>
      <div class="day-detail">45min Zone 2<br>(watt-bike or row)<br><br>Core circuit</div>
    </div>
    <div class="day-card">
      <div class="day-name">Wed</div>
      <div class="day-badge badge-pull">Pull A</div>
      <div class="day-detail">Back, Biceps, Rear Delts<br><br>+ 15min Zone 2<br>(ski erg cool-down)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Thu</div>
      <div class="day-badge badge-legs">Legs A</div>
      <div class="day-detail">Quads, Hamstrings, Glutes<br><br>+ 20min Zone 2<br>(treadmill incline walk)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Fri</div>
      <div class="day-badge badge-push">Push B</div>
      <div class="day-detail">Shoulders-led<br>Chest, Tris<br><br>+ 15min rowing<br>technique work</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sat</div>
      <div class="day-badge badge-hybrid">Hybrid</div>
      <div class="day-detail">Pull B + Legs B<br>(condensed)<br><br>+ 20min trail walk<br>or easy run</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sun</div>
      <div class="day-badge badge-rest">Recovery</div>
      <div class="day-detail">30min walk<br>Sauna + steam<br>Mobility / stretch</div>
    </div>
  </div>

  <div class="section-sub" style="margin-top: 48px;">Phase 3–4 · Development Schedule</div>

  <div class="schedule-grid">
    <div class="day-card">
      <div class="day-name">Mon</div>
      <div class="day-badge badge-push">Push A</div>
      <div class="day-detail">Chest, Shoulders, Tris<br><br>+ 25min Zone 2/3<br>(row or ski)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Tue</div>
      <div class="day-badge badge-cardio">Run / Row</div>
      <div class="day-detail">30min easy run<br>(trail or treadmill)<br><br>+ core & KB circuit</div>
    </div>
    <div class="day-card">
      <div class="day-name">Wed</div>
      <div class="day-badge badge-pull">Pull A</div>
      <div class="day-detail">Back, Biceps<br><br>+ 20min swim<br>(technique focus)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Thu</div>
      <div class="day-badge badge-legs">Legs A</div>
      <div class="day-detail">Squat-led<br>Hamstring work<br><br>+ 20min run</div>
    </div>
    <div class="day-card">
      <div class="day-name">Fri</div>
      <div class="day-badge badge-hybrid">Hybrid</div>
      <div class="day-detail">Push B + short run<br>Shoulders + Chest<br><br>15min Zone 3<br>intervals (bike)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sat</div>
      <div class="day-badge badge-hybrid">Long Cardio</div>
      <div class="day-detail">45–60min<br>trail run / row<br><br>Pull B (condensed)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sun</div>
      <div class="day-badge badge-rest">Recovery</div>
      <div class="day-detail">Sauna + steam<br>30min walk<br>Stretch</div>
    </div>
  </div>

  <div class="section-sub" style="margin-top: 48px;">Phase 5–6 · Performance Schedule</div>

  <div class="schedule-grid">
    <div class="day-card">
      <div class="day-name">Mon</div>
      <div class="day-badge badge-push">Push A</div>
      <div class="day-detail">Heavy strength<br>5x5 focus<br><br>+ 20min HIIT<br>(bike or rower)</div>
    </div>
    <div class="day-card">
      <div class="day-name">Tue</div>
      <div class="day-badge badge-cardio">Run</div>
      <div class="day-detail">5km+ trail run<br>Zone 2–3<br><br>KB finisher</div>
    </div>
    <div class="day-card">
      <div class="day-name">Wed</div>
      <div class="day-badge badge-pull">Pull A</div>
      <div class="day-detail">Heavy back<br>Deadlift focus<br><br>+ 20min swim</div>
    </div>
    <div class="day-card">
      <div class="day-name">Thu</div>
      <div class="day-badge badge-legs">Legs A</div>
      <div class="day-detail">Heavy legs<br><br>+ 25min run<br>or ski erg HIIT</div>
    </div>
    <div class="day-card">
      <div class="day-name">Fri</div>
      <div class="day-badge badge-hybrid">Hybrid</div>
      <div class="day-detail">Push B + Cardio<br>Circuit style<br><br>Metabolic finisher<br>10–15min</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sat</div>
      <div class="day-badge badge-hybrid">Long Day</div>
      <div class="day-detail">Long run 7–10km<br>or 60min row<br><br>Pull B condensed</div>
    </div>
    <div class="day-card">
      <div class="day-name">Sun</div>
      <div class="day-badge badge-rest">Recovery</div>
      <div class="day-detail">Sauna + steam<br>Mobility work<br>Walk</div>
    </div>
  </div>
</section>

<!-- WORKOUTS -->
<section id="workouts" class="section">
  <div class="section-title">WORKOUT DETAIL</div>
  <div class="section-sub">Phase 1–2 Exercise Selection · Sets × Reps</div>

  <div class="callout callout-blue">
    <strong>Lifting approach:</strong> All lifting is in the 8–12 rep hypertrophy range for Phase 1–2, progressing to 5–8 strength range in Phase 3–6. Rest 90–120 seconds between working sets. Always have 1–2 reps in reserve (RIR) — you're training 6 days, so no grinding failures.
  </div>

  <div class="workout-block">
    <div class="workout-header">
      <div class="day-badge badge-push" style="font-size:13px; padding:6px 14px;">PUSH A — Monday</div>
      <div class="workout-title">CHEST · SHOULDERS · TRICEPS</div>
    </div>
    <table>
      <thead><tr><th>Exercise</th><th>Sets × Reps</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td>Flat Barbell Bench Press</td><td>4 × 8–10</td><td>Primary chest driver. Keep 1–2 RIR.</td></tr>
        <tr><td>Incline Dumbbell Press</td><td>3 × 10–12</td><td>Upper chest emphasis.</td></tr>
        <tr><td>Cable Lateral Raises</td><td>4 × 15</td><td>Slow eccentric. No swinging.</td></tr>
        <tr><td>Overhead Press (DB or BB)</td><td>3 × 8–10</td><td>Seated or standing.</td></tr>
        <tr><td>Cable Tricep Pushdown</td><td>3 × 12–15</td><td>Full extension at bottom.</td></tr>
        <tr><td>Overhead Tricep Extension</td><td>3 × 12</td><td>Long head emphasis.</td></tr>
        <tr><td colspan="3" style="padding-top:12px;"><em style="color:var(--muted); font-size:12px;">Then: 20 min watt-bike Zone 2 (conversational pace, ~65% max HR)</em></td></tr>
      </tbody>
    </table>
  </div>

  <div class="workout-block">
    <div class="workout-header">
      <div class="day-badge badge-pull" style="font-size:13px; padding:6px 14px;">PULL A — Wednesday</div>
      <div class="workout-title">BACK · BICEPS · REAR DELTS</div>
    </div>
    <table>
      <thead><tr><th>Exercise</th><th>Sets × Reps</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td>Barbell Deadlift (Romanian Phase 1)</td><td>4 × 6–8</td><td>RDL in phase 1. Conventional from month 3.</td></tr>
        <tr><td>Weighted Pull-Ups or Lat Pulldown</td><td>4 × 8–10</td><td>Progress to bodyweight reps first.</td></tr>
        <tr><td>Seated Cable Row (neutral grip)</td><td>3 × 10–12</td><td>Drive elbows back, squeeze at peak.</td></tr>
        <tr><td>Face Pulls</td><td>4 × 15–20</td><td>Rear delt + rotator cuff health.</td></tr>
        <tr><td>Barbell or DB Curl</td><td>3 × 10–12</td><td>Full ROM, no cheating.</td></tr>
        <tr><td>Hammer Curl</td><td>3 × 12</td><td>Brachialis emphasis.</td></tr>
        <tr><td colspan="3" style="padding-top:12px;"><em style="color:var(--muted); font-size:12px;">Then: 15 min ski erg — easy, focus on technique</em></td></tr>
      </tbody>
    </table>
  </div>

  <div class="workout-block">
    <div class="workout-header">
      <div class="day-badge badge-legs" style="font-size:13px; padding:6px 14px;">LEGS A — Thursday</div>
      <div class="workout-title">QUADS · HAMSTRINGS · GLUTES · CALVES</div>
    </div>
    <table>
      <thead><tr><th>Exercise</th><th>Sets × Reps</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td>Barbell Back Squat</td><td>4 × 8–10</td><td>Primary compound. Depth to parallel+.</td></tr>
        <tr><td>Romanian Deadlift</td><td>3 × 10–12</td><td>Hip hinge, feel the hamstring stretch.</td></tr>
        <tr><td>Leg Press</td><td>3 × 12–15</td><td>Foot position controls emphasis.</td></tr>
        <tr><td>Leg Curl (seated or lying)</td><td>3 × 12–15</td><td>Full ROM, slow eccentric.</td></tr>
        <tr><td>Bulgarian Split Squat</td><td>3 × 10 each</td><td>Balance + unilateral strength.</td></tr>
        <tr><td>Standing Calf Raise</td><td>4 × 15–20</td><td>Pause at top and bottom.</td></tr>
        <tr><td colspan="3" style="padding-top:12px;"><em style="color:var(--muted); font-size:12px;">Then: 20 min incline treadmill walk @ 6–8% grade, 5–6 km/h</em></td></tr>
      </tbody>
    </table>
  </div>

  <div class="workout-block">
    <div class="workout-header">
      <div class="day-badge badge-cardio" style="font-size:13px; padding:6px 14px;">CARDIO DAY — Tuesday</div>
      <div class="workout-title">ZONE 2 ENGINE BUILD + CORE</div>
    </div>
    <table>
      <thead><tr><th>Activity</th><th>Duration</th><th>Target</th></tr></thead>
      <tbody>
        <tr><td>Watt-bike or Rower</td><td>40–45 min</td><td>Zone 2 — 60–70% max HR. Conversational pace. Never breathless.</td></tr>
        <tr><td>Plank Hold</td><td>3 × 45–60s</td><td>Brace hard, don't let hips sag.</td></tr>
        <tr><td>Dead Bug</td><td>3 × 10 each side</td><td>Core stability, lower back protection.</td></tr>
        <tr><td>Hanging Knee Raise</td><td>3 × 15</td><td>Progress to leg raises over time.</td></tr>
        <tr><td>McGill Curl-Up</td><td>3 × 8</td><td>Spine-safe ab work.</td></tr>
      </tbody>
    </table>
  </div>

  <div class="workout-block">
    <div class="workout-header">
      <div class="day-badge badge-hybrid" style="font-size:13px; padding:6px 14px;">SATURDAY — Hybrid</div>
      <div class="workout-title">PUSH B + PULL B (CONDENSED) + LIGHT CARDIO</div>
    </div>
    <table>
      <thead><tr><th>Exercise</th><th>Sets × Reps</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td>DB Shoulder Press</td><td>3 × 10–12</td><td>Push B opener.</td></tr>
        <tr><td>Cable Fly or Pec Dec</td><td>3 × 12–15</td><td>Chest isolation, pump focus.</td></tr>
        <tr><td>Tricep Dips (weighted if possible)</td><td>3 × 10–12</td><td></td></tr>
        <tr><td>Single-Arm DB Row</td><td>3 × 10–12 each</td><td>Pull B opener.</td></tr>
        <tr><td>Straight-Arm Lat Pulldown</td><td>3 × 12–15</td><td>Lat isolation.</td></tr>
        <tr><td>Incline DB Curl</td><td>3 × 12</td><td></td></tr>
        <tr><td>Trail Walk or Easy Run</td><td>20–30 min</td><td>Low HR, enjoy it. This is active recovery.</td></tr>
      </tbody>
    </table>
  </div>
</section>

<!-- NUTRITION -->
<section id="nutrition" class="section">
  <div class="section-title">NUTRITION PROTOCOL</div>
  <div class="section-sub">Built around your eating window · Red meat & chicken focused</div>

  <div class="callout">
    <strong>Core principle:</strong> You're already doing compressed eating (11:30–18:30 window = ~7 hours). This naturally lowers insulin for 16+ hours per day, which is your primary fat-burning lever. We don't need to starve you — we need to <strong>raise protein, time carbs around training, and manage weekends</strong>.
  </div>

  <div class="section-sub" style="margin-top:0;">Daily Macro Targets</div>

  <div class="macro-bar">
    <div class="macro-row">
      <div class="macro-name">Protein</div>
      <div class="macro-track"><div class="macro-fill fill-protein"></div></div>
      <div class="macro-val">200–220g</div>
    </div>
    <div class="macro-row">
      <div class="macro-name">Carbs</div>
      <div class="macro-track"><div class="macro-fill fill-carbs"></div></div>
      <div class="macro-val">180–220g</div>
    </div>
    <div class="macro-row">
      <div class="macro-name">Fat</div>
      <div class="macro-track"><div class="macro-fill fill-fat"></div></div>
      <div class="macro-val">70–90g</div>
    </div>
    <div style="margin-top:16px; font-family:'DM Mono',monospace; font-size:11px; color:var(--muted);">
      TOTAL TARGET: 2,500–2,700 kcal/day · DEFICIT: ~400–600 kcal
    </div>
  </div>

  <div class="section-sub">Daily Meal Plan — Training Days</div>

  <div class="meal-grid">
    <div class="meal-card">
      <div class="meal-time">Pre-Training · 05:30</div>
      <div class="meal-name">PRE-WORKOUT PRIMER</div>
      <ul class="meal-items">
        <li>1 banana or 2 dates</li>
        <li>Black coffee (no milk/sugar)</li>
        <li>Optional: 5g creatine</li>
      </ul>
      <div class="meal-kcal"><div>Purpose</div><span>Quick carbs, no digestion issue, doesn't break fat-fasting</span></div>
    </div>
    <div class="meal-card">
      <div class="meal-time">Meal 1 · 11:30</div>
      <div class="meal-name">FIRST BREAK</div>
      <ul class="meal-items">
        <li>200g Greek yoghurt (full fat)</li>
        <li>2 boiled eggs</li>
        <li>Protein shake (30g protein)</li>
        <li>Handful berries or apple</li>
      </ul>
      <div class="meal-kcal"><div>~kcal</div><span>600–650</span></div>
    </div>
    <div class="meal-card">
      <div class="meal-time">Meal 2 · 13:30</div>
      <div class="meal-name">LUNCH — ANCHOR MEAL</div>
      <ul class="meal-items">
        <li>200–250g beef / chicken breast</li>
        <li>1 cup white rice or sweet potato</li>
        <li>Roasted veg or large salad</li>
        <li>Olive oil or butter dressing</li>
      </ul>
      <div class="meal-kcal"><div>~kcal</div><span>750–850</span></div>
    </div>
    <div class="meal-card">
      <div class="meal-time">Meal 3 · 18:00–18:30</div>
      <div class="meal-name">DINNER — PROTEIN HEAVY</div>
      <ul class="meal-items">
        <li>250–300g steak, mince or chicken thighs</li>
        <li>Low-carb veg (broccoli, spinach, zucchini)</li>
        <li>Avocado or olive oil fat source</li>
        <li>No starchy carbs (keep dinner lower carb)</li>
      </ul>
      <div class="meal-kcal"><div>~kcal</div><span>700–800</span></div>
    </div>
  </div>

  <div class="callout callout-blue">
    <strong>Carb timing rule:</strong> Carbs at Meal 1 (post-training, replenish muscle glycogen) and Meal 2 (midday). Dinner is protein + fat + fibre only. This trains your body to use fat as evening fuel and improves overnight fat oxidation — directly targeting that central fat.
  </div>

  <div class="section-sub" style="margin-top:40px;">Weekend Strategy</div>

  <div class="callout callout-red">
    <strong>The non-negotiables:</strong><br><br>
    1. <strong>Eat before you go out</strong> — high protein meal, 300–400 kcal minimum. Don't arrive hungry.<br>
    2. <strong>Alcohol order of preference:</strong> Dry red wine &gt; spirits neat/with soda &gt; beer. Avoid cocktails with mixers.<br>
    3. <strong>Alternate water</strong> between every drink.<br>
    4. <strong>Sunday morning protocol:</strong> Within 1 hour of waking — 40g protein (eggs or shake), 30–40 min sauna/steam, light walk. This resets cortisol and restores insulin sensitivity faster than rest alone.<br>
    5. <strong>Don't restrict hard on Monday to compensate</strong> — it spikes cortisol and drives more central fat storage. Just return to plan.
  </div>

  <div class="section-sub" style="margin-top:40px;">Protein Sources (Your Situation)</div>

  <table>
    <thead><tr><th>Source</th><th>Protein per 100g</th><th>Best use</th><th>Fat content</th></tr></thead>
    <tbody>
      <tr><td>Beef mince (lean, 5–10%)</td><td>~26g</td><td>Lunch / dinner</td><td>Low–Med</td></tr>
      <tr><td>Beef steak (rump/sirloin)</td><td>~28g</td><td>Dinner</td><td>Med</td></tr>
      <tr><td>Chicken breast</td><td>~31g</td><td>Lunch, meal prep</td><td>Very low</td></tr>
      <tr><td>Chicken thighs (skinless)</td><td>~26g</td><td>Dinner, more flavour</td><td>Low–Med</td></tr>
      <tr><td>Eggs (per egg ~6g)</td><td>~13g per 100g</td><td>Meal 1, breakfast</td><td>Med</td></tr>
      <tr><td>Greek yoghurt (full fat)</td><td>~9g per 100g</td><td>Meal 1</td><td>Low</td></tr>
      <tr><td>Whey protein (per scoop)</td><td>~25–30g</td><td>Shake, gap filler</td><td>Very low</td></tr>
    </tbody>
  </table>

  <div class="callout" style="margin-top:32px;">
    <strong>Supplements (keep it simple):</strong> Creatine monohydrate 5g/day (any time), Whey protein as needed to hit 200g target, Magnesium glycinate 400mg at night (improves sleep and cortisol management — key for belly fat), Vitamin D3 + K2 (5,000 IU daily). That's it. Don't overcomplicate.
  </div>
</section>

<!-- PROGRESSION -->
<section id="progression" class="section">
  <div class="section-title">PROGRESSION MAP</div>
  <div class="section-sub">Monthly milestones and what to expect</div>

  <div class="callout">
    <strong>Reality check:</strong> Body recomposition at your size and training level is measurable but not linear. Expect weight to fluctuate ±2–3kg week to week. Track <strong>waist circumference and progress photos</strong> over scale weight. Your goal markers are: smaller waist, stronger lifts, improving cardio benchmarks.
  </div>

  <div class="timeline">
    <div class="tl-item">
      <div class="tl-month">Month 1</div>
      <div class="tl-title">ESTABLISH THE HABIT</div>
      <div class="tl-desc">Focus entirely on showing up. Lift 6 days. Don't miss. Cardio will feel easy — that's correct, you're building the aerobic base slowly. Expect: some initial weight drop (water + glycogen from diet clean-up), energy dip in week 2 as body adapts, sleeping better by week 3-4.</div>
    </div>
    <div class="tl-item">
      <div class="tl-month">Month 2</div>
      <div class="tl-title">FIRST MARKERS SHOW</div>
      <div class="tl-desc">Waist tape should show 2–4cm reduction. Lifts feel strong and consistent. Zone 2 cardio at same heart rate feels easier — you're building mitochondria. Introduce rowing 2× per week. Protein intake should be dialled in by now. Expect: visible reduction in lower chest puffiness, clothes fitting differently.</div>
    </div>
    <div class="tl-item">
      <div class="tl-month">Month 3</div>
      <div class="tl-title">CARDIO AWAKENING</div>
      <div class="tl-desc">Introduce running 2× per week (start with 20 min easy). First swim sessions for technique. Lifting transitions toward heavier strength ranges (5–8 reps on compounds). This is when the engine starts coming online. Expect: cardiovascular fitness improving noticeably, ability to push harder without heart rate spiking.</div>
    </div>
    <div class="tl-item">
      <div class="tl-month">Month 4</div>
      <div class="tl-title">RECOMPOSITION VISIBLE</div>
      <div class="tl-desc">Muscle definition should be increasingly visible in upper body. Running to 30–35 min continuous. Rowing 4km+ efforts. Hybrid sessions now mixing lifting and cardio in same block. Expect: other people noticing, lifts at or above pre-programme levels despite being in deficit — this is the recomp working.</div>
    </div>
    <div class="tl-item">
      <div class="tl-month">Month 5</div>
      <div class="tl-title">PERFORMANCE MODE</div>
      <div class="tl-desc">You're now a different athlete than you were in January. Introduce HIIT on bike and rower (4–6 × 30s hard / 90s easy). Running 5km+ comfortably. Lifts are heavy. Hybrid sessions are challenging but manageable. Expect: significant body composition shift, high energy levels, noticeable improvement in all benchmarks.</div>
    </div>
    <div class="tl-item">
      <div class="tl-month">Month 6</div>
      <div class="tl-title">FULL EXPRESSION</div>
      <div class="tl-desc">Peak the programme. Test: 5km run time, 2km row time, lifting 1RMs on big compounds. Long Saturday sessions (60 min) mixing modalities. Weekend benders are now less damaging because your metabolic rate is higher and insulin sensitivity is dramatically improved. Expect: 8–14kg of fat lost, measurable muscle gain, a fundamentally more capable body.</div>
    </div>
  </div>

  <div class="section-sub">Benchmark Tests — Track These</div>

  <table>
    <thead><tr><th>Test</th><th>Month 1 Baseline</th><th>Month 3 Target</th><th>Month 6 Target</th></tr></thead>
    <tbody>
      <tr><td>Waist circumference</td><td>Measure week 1</td><td>–4 to –6cm</td><td>–8 to –12cm</td></tr>
      <tr><td>Body weight</td><td>120kg</td><td>115–117kg</td><td>108–112kg</td></tr>
      <tr><td>Watt-bike 20min avg power</td><td>Baseline test</td><td>+10–15%</td><td>+25–35%</td></tr>
      <tr><td>2km row time</td><td>Not tested (new)</td><td>Sub 8:30</td><td>Sub 7:30</td></tr>
      <tr><td>5km run</td><td>Not tested (new)</td><td>Continuous 30min</td><td>Sub 28–30 min</td></tr>
      <tr><td>Bench press 1RM</td><td>Baseline week 1</td><td>Maintain / +2.5kg</td><td>+5–10kg</td></tr>
      <tr><td>Deadlift 1RM</td><td>Baseline week 1</td><td>Maintain / +5kg</td><td>+10–20kg</td></tr>
    </tbody>
  </table>

  <div class="callout" style="margin-top:32px;">
    <strong>When to adjust:</strong> If weight hasn't moved in 3 consecutive weeks AND waist hasn't changed, reduce carbs by 30g/day. If energy crashes or lifts drop significantly, add 150–200 kcal via protein or carbs. Never drop below 2,200 kcal — you'll lose muscle and stall. The programme is designed to be sustainable, not aggressive.
  </div>
</section>

<footer>
  Johan · Hybrid Athlete Protocol · 6 Months · Generated June 2026 — Adjust every 4 weeks based on progress
</footer>

<script>
  function showSection(id) {
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    event.target.classList.add('active');
  }

  const phaseData = {
    1: {
      title: 'FOUNDATION — Months 1–2',
      lifting: [
        ['Lifting style', 'Hypertrophy — 8–12 reps'],
        ['Compounds', 'RDL, Squat, Bench, Row'],
        ['Accessory', 'High volume, moderate weight'],
        ['Rest periods', '90–120 seconds'],
      ],
      cardio: [
        ['Primary modality', 'Watt-bike (Zone 2)'],
        ['Secondary', 'Incline treadmill walk'],
        ['Tertiary', 'Ski erg technique'],
        ['Weekly cardio volume', '~90–120 min'],
        ['Target HR', '60–70% max (139–163 bpm est.)'],
      ]
    },
    2: {
      title: 'DEVELOPMENT — Months 3–4',
      lifting: [
        ['Lifting style', 'Strength — 6–8 reps on compounds'],
        ['Compounds', 'Conventional DL, Squat, Bench'],
        ['New elements', 'Heavier loading, fewer reps'],
        ['Rest periods', '2–3 minutes on compounds'],
      ],
      cardio: [
        ['Primary modality', 'Running (trail / treadmill)'],
        ['Secondary', 'Rowing (technique → volume)'],
        ['Tertiary', 'Swimming (2× per week)'],
        ['Weekly cardio volume', '~150–180 min'],
        ['Target HR', 'Zone 2–3 mix (70–80% max)'],
      ]
    },
    3: {
      title: 'PERFORMANCE — Months 5–6',
      lifting: [
        ['Lifting style', 'Power — 5×5 on big lifts'],
        ['Compounds', 'Max effort deadlift, squat, press'],
        ['Hypertrophy', 'Maintained via accessories'],
        ['Rest periods', '3–5 min on heavy compounds'],
      ],
      cardio: [
        ['Primary modality', '5km+ trail runs'],
        ['Secondary', 'HIIT — bike & rower intervals'],
        ['Tertiary', 'Long Saturday sessions 60min+'],
        ['Weekly cardio volume', '~200–240 min'],
        ['Target HR', 'Zone 2–4 mix, HIIT at Zone 5'],
      ]
    }
  };

  function selectPhase(num) {
    document.querySelectorAll('.phase-card').forEach(c => c.classList.remove('active-phase'));
    document.querySelector(`.phase-card[data-num="${num}"]`).classList.add('active-phase');

    const d = phaseData[num];
    const detail = document.getElementById('phase-detail');

    detail.innerHTML = `
      <div style="font-family:'DM Mono',monospace; font-size:11px; letter-spacing:0.15em; text-transform:uppercase; color:var(--accent); margin-bottom:20px;">${d.title}</div>
      <div class="detail-grid">
        <div class="detail-block">
          <h4>Lifting Focus</h4>
          <ul class="detail-list">
            ${d.lifting.map(([l, v]) => `<li><span class="li-label">${l}</span><span class="li-val">${v}</span></li>`).join('')}
          </ul>
        </div>
        <div class="detail-block">
          <h4>Cardio Focus</h4>
          <ul class="detail-list">
            ${d.cardio.map(([l, v]) => `<li><span class="li-label">${l}</span><span class="li-val">${v}</span></li>`).join('')}
          </ul>
        </div>
      </div>
    `;
    detail.classList.add('visible');
  }
</script>
</body>
</html>
