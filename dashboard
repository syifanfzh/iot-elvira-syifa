<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AIoT SmartEnv — Monitoring & Predictive Analytics</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap');

  :root {
    --white: #ffffff;
    --bg: #faf9fd;
    --surface: #ffffff;
    --surface2: #f5f3fb;
    --lavender-50: #f3f0fd;
    --lavender-100: #e9e4fb;
    --lavender-200: #d4c9f7;
    --lavender-300: #b9a8f1;
    --lavender-400: #9b84e9;
    --lavender-500: #7c5fd9;
    --pink-100: #fce8f3;
    --pink-200: #f9d0e8;
    --pink-300: #f2a8d4;
    --pink-400: #e879b9;
    --pink-500: #d4509e;
    --accent: #8b6fdf;
    --accent2: #c97dd4;
    --text-primary: #1a1626;
    --text-secondary: #5e5472;
    --text-muted: #9088a4;
    --border: #e8e3f5;
    --border-light: #f0ecfa;
    --success: #22c55e;
    --danger: #ef4444;
    --warning: #f59e0b;
    --shadow-sm: 0 1px 3px rgba(139,111,223,0.08), 0 1px 2px rgba(0,0,0,0.04);
    --shadow: 0 4px 16px rgba(139,111,223,0.12), 0 2px 4px rgba(0,0,0,0.04);
    --shadow-lg: 0 12px 40px rgba(139,111,223,0.18), 0 4px 8px rgba(0,0,0,0.06);
    --radius: 16px;
    --radius-sm: 10px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--bg);
    color: var(--text-primary);
    line-height: 1.6;
    min-height: 100vh;
  }

  /* ─── NAV ─── */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(255,255,255,0.88);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border-light);
    padding: 0 32px;
  }
  .nav-inner {
    max-width: 1280px;
    margin: 0 auto;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .nav-logo {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    color: var(--text-primary);
  }
  .logo-icon {
    width: 36px;
    height: 36px;
    background: linear-gradient(135deg, var(--lavender-400), var(--accent2));
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 16px;
  }
  .logo-text {
    font-family: 'Space Grotesk', sans-serif;
    font-weight: 700;
    font-size: 18px;
    letter-spacing: -0.3px;
  }
  .logo-sub {
    font-size: 11px;
    color: var(--text-muted);
    font-weight: 400;
    letter-spacing: 0.5px;
  }
  .nav-tabs {
    display: flex;
    gap: 4px;
    background: var(--lavender-50);
    border-radius: 10px;
    padding: 4px;
  }
  .nav-tab {
    padding: 7px 18px;
    border-radius: 7px;
    border: none;
    background: transparent;
    color: var(--text-secondary);
    font-size: 13.5px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'Inter', sans-serif;
  }
  .nav-tab.active {
    background: var(--white);
    color: var(--accent);
    box-shadow: var(--shadow-sm);
  }
  .nav-right {
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .status-live {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 12.5px;
    color: var(--success);
    font-weight: 500;
  }
  .dot-live {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--success);
    animation: pulse-green 2s infinite;
  }
  @keyframes pulse-green {
    0%,100% { opacity:1; transform:scale(1); }
    50% { opacity:0.5; transform:scale(1.4); }
  }

  /* ─── LAYOUT ─── */
  .page { display: none; }
  .page.active { display: block; }
  .container { max-width: 1280px; margin: 0 auto; padding: 32px; }

  /* ─── HERO ─── */
  .hero {
    background: linear-gradient(135deg, #f8f5ff 0%, #fff0fa 50%, #f5f0ff 100%);
    border-bottom: 1px solid var(--border);
    padding: 48px 32px 40px;
  }
  .hero-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 40px;
    align-items: center;
  }
  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: 11.5px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--accent);
    background: var(--lavender-100);
    padding: 5px 12px;
    border-radius: 100px;
    margin-bottom: 14px;
  }
  .hero h1 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 36px;
    font-weight: 700;
    letter-spacing: -1px;
    color: var(--text-primary);
    line-height: 1.15;
    margin-bottom: 12px;
  }
  .hero h1 span {
    background: linear-gradient(135deg, var(--lavender-500), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-desc {
    font-size: 15px;
    color: var(--text-secondary);
    max-width: 500px;
    line-height: 1.7;
  }
  .hero-meta {
    display: flex;
    gap: 24px;
    margin-top: 20px;
  }
  .hero-meta-item {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 13px;
    color: var(--text-muted);
  }
  .hero-meta-item strong { color: var(--text-secondary); font-weight: 600; }
  .hero-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .hero-stat {
    background: white;
    border-radius: 14px;
    padding: 16px 20px;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    min-width: 120px;
  }
  .hero-stat-val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 28px;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 4px;
  }
  .hero-stat-val.temp { color: var(--lavender-500); }
  .hero-stat-val.humid { color: var(--accent2); }
  .hero-stat-val.alert { color: var(--danger); }
  .hero-stat-val.rec { color: var(--success); }
  .hero-stat-label { font-size: 11.5px; color: var(--text-muted); font-weight: 500; }

  /* ─── SECTION TITLE ─── */
  .section-header { margin-bottom: 20px; }
  .section-title {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: 4px;
    letter-spacing: -0.3px;
  }
  .section-sub { font-size: 13px; color: var(--text-muted); }

  /* ─── CARDS GRID ─── */
  .kpi-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
    margin-bottom: 24px;
  }
  .kpi-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 20px 22px;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    position: relative;
    overflow: hidden;
  }
  .kpi-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
  }
  .kpi-card.t::before { background: linear-gradient(90deg, var(--lavender-400), var(--lavender-300)); }
  .kpi-card.h::before { background: linear-gradient(90deg, var(--accent2), var(--pink-300)); }
  .kpi-card.a::before { background: linear-gradient(90deg, #ef4444, #f97316); }
  .kpi-card.n::before { background: linear-gradient(90deg, var(--success), #86efac); }
  .kpi-icon {
    width: 38px;
    height: 38px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    margin-bottom: 12px;
  }
  .kpi-card.t .kpi-icon { background: var(--lavender-100); }
  .kpi-card.h .kpi-icon { background: var(--pink-100); }
  .kpi-card.a .kpi-icon { background: #fff1f1; }
  .kpi-card.n .kpi-icon { background: #f0fdf4; }
  .kpi-val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 30px;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 5px;
  }
  .kpi-card.t .kpi-val { color: var(--lavender-500); }
  .kpi-card.h .kpi-val { color: var(--accent2); }
  .kpi-card.a .kpi-val { color: #ef4444; }
  .kpi-card.n .kpi-val { color: #16a34a; }
  .kpi-label { font-size: 12px; color: var(--text-muted); font-weight: 500; }
  .kpi-sub { font-size: 11px; color: var(--text-muted); margin-top: 6px; }

  /* ─── CHART CARDS ─── */
  .charts-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 24px;
  }
  .chart-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
  }
  .chart-card.full { grid-column: 1 / -1; }
  .chart-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 20px;
  }
  .chart-title { font-size: 14px; font-weight: 600; color: var(--text-primary); }
  .chart-sub { font-size: 12px; color: var(--text-muted); margin-top: 2px; }
  .chart-badge {
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 100px;
    font-weight: 600;
  }
  .badge-purple { background: var(--lavender-100); color: var(--accent); }
  .badge-pink { background: var(--pink-100); color: var(--pink-500); }
  .badge-green { background: #f0fdf4; color: #16a34a; }
  .badge-red { background: #fff1f1; color: #ef4444; }
  .chart-wrap { position: relative; height: 240px; }
  .chart-wrap.tall { height: 300px; }

  /* ─── TABLE ─── */
  .table-card {
    background: var(--white);
    border-radius: var(--radius);
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    overflow: hidden;
    margin-bottom: 24px;
  }
  .table-header {
    padding: 20px 24px 16px;
    border-bottom: 1px solid var(--border-light);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .table-controls { display: flex; gap: 8px; align-items: center; }
  .search-input {
    padding: 7px 14px;
    border: 1px solid var(--border);
    border-radius: 8px;
    font-size: 13px;
    outline: none;
    background: var(--lavender-50);
    color: var(--text-primary);
    width: 200px;
    transition: border-color 0.2s;
    font-family: 'Inter', sans-serif;
  }
  .search-input:focus { border-color: var(--lavender-300); }
  .filter-btn {
    padding: 7px 14px;
    border: 1px solid var(--border);
    border-radius: 8px;
    font-size: 13px;
    background: var(--lavender-50);
    cursor: pointer;
    color: var(--text-secondary);
    font-weight: 500;
    transition: all 0.15s;
    font-family: 'Inter', sans-serif;
  }
  .filter-btn:hover, .filter-btn.active-filter { background: var(--lavender-100); border-color: var(--lavender-300); color: var(--accent); }
  .table-scroll { overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; font-size: 13px; }
  thead th {
    padding: 11px 20px;
    text-align: left;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    color: var(--text-muted);
    background: var(--lavender-50);
    border-bottom: 1px solid var(--border);
  }
  tbody tr { border-bottom: 1px solid var(--border-light); transition: background 0.12s; }
  tbody tr:hover { background: var(--lavender-50); }
  tbody tr:last-child { border-bottom: none; }
  tbody td { padding: 11px 20px; color: var(--text-primary); }
  tbody td.muted { color: var(--text-muted); }
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    padding: 3px 10px;
    border-radius: 100px;
    font-size: 11.5px;
    font-weight: 600;
  }
  .badge-normal { background: #f0fdf4; color: #16a34a; }
  .badge-panas { background: #fff1f1; color: #ef4444; }
  .table-footer {
    padding: 12px 24px;
    border-top: 1px solid var(--border-light);
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 12.5px;
    color: var(--text-muted);
  }
  .pagination { display: flex; gap: 4px; }
  .page-btn {
    width: 30px; height: 30px;
    border: 1px solid var(--border);
    border-radius: 7px;
    background: white;
    cursor: pointer;
    font-size: 12.5px;
    color: var(--text-secondary);
    transition: all 0.15s;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Inter', sans-serif;
  }
  .page-btn:hover { background: var(--lavender-50); border-color: var(--lavender-300); }
  .page-btn.active-page { background: var(--accent); color: white; border-color: var(--accent); }

  /* ─── ML PAGE ─── */
  .ml-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 24px;
  }
  .info-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
  }
  .info-card.accent-card {
    background: linear-gradient(135deg, var(--lavender-50), var(--pink-100));
    border-color: var(--lavender-200);
  }
  .formula-box {
    background: var(--lavender-50);
    border: 1px solid var(--lavender-200);
    border-radius: 10px;
    padding: 16px 20px;
    margin: 16px 0;
    text-align: center;
    font-family: 'Space Grotesk', sans-serif;
    font-size: 17px;
    font-weight: 600;
    color: var(--accent);
  }
  .metric-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid var(--border-light);
  }
  .metric-row:last-child { border-bottom: none; }
  .metric-name { font-size: 13px; color: var(--text-secondary); font-weight: 500; }
  .metric-val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 16px;
    font-weight: 700;
  }
  .metric-badge { font-size: 11px; color: var(--text-muted); }

  /* ─── PREDICTOR ─── */
  .predictor-card {
    background: linear-gradient(135deg, #faf8ff, #fff5fe);
    border: 1px solid var(--lavender-200);
    border-radius: var(--radius);
    padding: 28px;
    box-shadow: var(--shadow);
    margin-bottom: 24px;
  }
  .predictor-grid {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 24px;
    align-items: center;
    margin-top: 20px;
  }
  .input-group label {
    display: block;
    font-size: 12.5px;
    font-weight: 600;
    color: var(--text-secondary);
    margin-bottom: 8px;
    letter-spacing: 0.3px;
  }
  .range-wrap { position: relative; }
  input[type=range] {
    width: 100%;
    height: 6px;
    border-radius: 3px;
    appearance: none;
    background: linear-gradient(90deg, var(--lavender-300), var(--accent2));
    outline: none;
    cursor: pointer;
  }
  input[type=range]::-webkit-slider-thumb {
    appearance: none;
    width: 20px; height: 20px;
    border-radius: 50%;
    background: white;
    border: 3px solid var(--accent);
    box-shadow: 0 2px 8px rgba(139,111,223,0.3);
  }
  .range-val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: var(--accent);
    margin-top: 8px;
  }
  .range-unit { font-size: 14px; color: var(--text-muted); margin-top: 4px; }
  .predict-arrow {
    font-size: 28px;
    color: var(--lavender-300);
    text-align: center;
  }
  .predict-result {
    text-align: center;
  }
  .predict-temp {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 52px;
    font-weight: 700;
    line-height: 1;
    background: linear-gradient(135deg, var(--lavender-500), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 6px;
  }
  .predict-label { font-size: 13px; color: var(--text-muted); }
  .predict-status {
    margin-top: 10px;
    font-size: 13px;
    font-weight: 600;
    padding: 5px 14px;
    border-radius: 100px;
    display: inline-block;
  }

  /* ─── SCATTER ─── */
  .scatter-meta {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 12px;
    margin-top: 16px;
  }
  .scatter-stat {
    background: var(--lavender-50);
    border-radius: 10px;
    padding: 12px 16px;
    border: 1px solid var(--lavender-100);
  }
  .scatter-stat-val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--accent);
  }
  .scatter-stat-label { font-size: 11.5px; color: var(--text-muted); margin-top: 2px; }

  /* ─── ABOUT PAGE ─── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 24px;
  }
  .about-card {
    background: white;
    border-radius: var(--radius);
    padding: 24px;
    border: 1px solid var(--border-light);
    box-shadow: var(--shadow-sm);
  }
  .tech-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px 0;
    border-bottom: 1px solid var(--border-light);
  }
  .tech-item:last-child { border-bottom: none; }
  .tech-icon {
    width: 34px; height: 34px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }
  .tech-name { font-size: 13.5px; font-weight: 600; color: var(--text-primary); }
  .tech-desc { font-size: 12px; color: var(--text-muted); }
  .step-list { list-style: none; counter-reset: steps; }
  .step-item {
    counter-increment: steps;
    display: flex;
    gap: 14px;
    padding: 12px 0;
    border-bottom: 1px solid var(--border-light);
  }
  .step-item:last-child { border-bottom: none; }
  .step-num {
    width: 28px; height: 28px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--lavender-400), var(--accent2));
    color: white;
    font-size: 13px;
    font-weight: 700;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
    font-family: 'Space Grotesk', sans-serif;
  }
  .step-text { font-size: 13px; color: var(--text-secondary); padding-top: 4px; line-height: 1.6; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-stats { grid-template-columns: repeat(4, 1fr); }
    .kpi-grid { grid-template-columns: 1fr 1fr; }
    .charts-grid { grid-template-columns: 1fr; }
    .ml-grid { grid-template-columns: 1fr; }
    .about-grid { grid-template-columns: 1fr; }
    .predictor-grid { grid-template-columns: 1fr; }
    .predict-arrow { display: none; }
    .nav-tabs { display: none; }
  }
  @media (max-width: 600px) {
    .container, .hero { padding: 20px; }
    .hero h1 { font-size: 26px; }
    .kpi-grid { grid-template-columns: 1fr 1fr; }
    .hero-stats { grid-template-columns: 1fr 1fr; }
  }

  /* ─── ANIMATION ─── */
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .fade-in { animation: fadeIn 0.4s ease both; }
  .fade-in-2 { animation: fadeIn 0.4s 0.1s ease both; }
  .fade-in-3 { animation: fadeIn 0.4s 0.2s ease both; }
  .progress-bar-wrap {
    height: 6px;
    background: var(--lavender-100);
    border-radius: 3px;
    overflow: hidden;
    margin-top: 8px;
  }
  .progress-bar {
    height: 100%;
    border-radius: 3px;
    background: linear-gradient(90deg, var(--lavender-400), var(--accent2));
    transition: width 0.8s ease;
  }
  .tooltip-info {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 16px; height: 16px;
    border-radius: 50%;
    background: var(--lavender-100);
    color: var(--accent);
    font-size: 10px;
    font-weight: 700;
    cursor: default;
    margin-left: 4px;
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <a class="nav-logo" href="#">
      <div class="logo-icon">🌡️</div>
      <div>
        <div class="logo-text">AIoT SmartEnv</div>
        <div class="logo-sub">DHT11 · ESP8266 · ThingSpeak · ML</div>
      </div>
    </a>
    <div class="nav-tabs">
      <button class="nav-tab active" onclick="showPage('monitoring')">📊 Monitoring</button>
      <button class="nav-tab" onclick="showPage('dataset')">🗃️ Dataset</button>
      <button class="nav-tab" onclick="showPage('ml')">🤖 Machine Learning</button>
      <button class="nav-tab" onclick="showPage('about')">📋 Tentang</button>
    </div>
    <div class="nav-right">
      <div class="status-live"><div class="dot-live"></div> Sistem Aktif</div>
    </div>
  </div>
</nav>

<!-- ══════════════════════════════ PAGE: MONITORING ══════════════════════════════ -->
<div id="page-monitoring" class="page active">
  <!-- HERO -->
  <div class="hero">
    <div class="hero-inner">
      <div>
        <div class="hero-eyebrow">🏠 Smart Room Monitoring</div>
        <h1>Monitoring Suhu & Kelembaban<br><span>Real-Time berbasis IoT</span></h1>
        <p class="hero-desc">Pemantauan kondisi lingkungan secara kontinu menggunakan sensor DHT11, mikrokontroler ESP8266, dan platform cloud ThingSpeak. Data dikirim setiap 15 detik secara otomatis.</p>
        <div class="hero-meta">
          <div class="hero-meta-item">🔌 <span><strong>DHT11</strong> Sensor</span></div>
          <div class="hero-meta-item">📡 <span><strong>ESP8266</strong> Wi-Fi</span></div>
          <div class="hero-meta-item">☁️ <span><strong>ThingSpeak</strong> Cloud</span></div>
          <div class="hero-meta-item">⚡ <span>Alert &gt; <strong>32°C</strong></span></div>
        </div>
      </div>
      <div class="hero-stats">
        <div class="hero-stat">
          <div class="hero-stat-val temp" id="hs-avg-temp">29.8°C</div>
          <div class="hero-stat-label">Suhu Rata-rata</div>
        </div>
        <div class="hero-stat">
          <div class="hero-stat-val humid" id="hs-avg-humid">67.3%</div>
          <div class="hero-stat-label">Kelembaban Rata-rata</div>
        </div>
        <div class="hero-stat">
          <div class="hero-stat-val alert" id="hs-alerts">18</div>
          <div class="hero-stat-label">Kejadian PANAS</div>
        </div>
        <div class="hero-stat">
          <div class="hero-stat-val rec">100</div>
          <div class="hero-stat-label">Total Record</div>
        </div>
      </div>
    </div>
  </div>

  <div class="container">
    <!-- KPI -->
    <div class="kpi-grid fade-in">
      <div class="kpi-card t">
        <div class="kpi-icon">🌡️</div>
        <div class="kpi-val">29.47°C</div>
        <div class="kpi-label">Suhu Mean</div>
        <div class="kpi-sub">Min: 25.1°C · Max: 33.8°C</div>
        <div class="progress-bar-wrap"><div class="progress-bar" style="width:72%"></div></div>
      </div>
      <div class="kpi-card h">
        <div class="kpi-icon">💧</div>
        <div class="kpi-val">67.30%</div>
        <div class="kpi-label">Kelembaban Mean</div>
        <div class="kpi-sub">Min: 58.0% · Max: 76.7%</div>
        <div class="progress-bar-wrap"><div class="progress-bar" style="width:67%"></div></div>
      </div>
      <div class="kpi-card a">
        <div class="kpi-icon">🔴</div>
        <div class="kpi-val">18%</div>
        <div class="kpi-label">Status PANAS</div>
        <div class="kpi-sub">18 dari 100 record · Threshold 32°C</div>
        <div class="progress-bar-wrap" style="--lavender-100:#fff1f1"><div class="progress-bar" style="width:18%;background:linear-gradient(90deg,#ef4444,#f97316)"></div></div>
      </div>
      <div class="kpi-card n">
        <div class="kpi-icon">✅</div>
        <div class="kpi-val">82%</div>
        <div class="kpi-label">Status NORMAL</div>
        <div class="kpi-sub">82 dari 100 record · Kondisi aman</div>
        <div class="progress-bar-wrap"><div class="progress-bar" style="width:82%;background:linear-gradient(90deg,#22c55e,#86efac)"></div></div>
      </div>
    </div>

    <!-- CHARTS ROW 1 -->
    <div class="charts-grid fade-in-2">
      <div class="chart-card full">
        <div class="chart-header">
          <div>
            <div class="chart-title">Grafik Monitoring Suhu Real-Time</div>
            <div class="chart-sub">Fluktuasi suhu dari 100 record sensor DHT11</div>
          </div>
          <div style="display:flex;gap:8px;align-items:center;">
            <span class="chart-badge badge-red">⚠ Threshold 32°C</span>
            <span class="chart-badge badge-purple">100 record</span>
          </div>
        </div>
        <div class="chart-wrap tall">
          <canvas id="chartTemp"></canvas>
        </div>
      </div>
    </div>

    <div class="charts-grid fade-in-3">
      <div class="chart-card">
        <div class="chart-header">
          <div>
            <div class="chart-title">Kelembaban (%) vs Waktu</div>
            <div class="chart-sub">Variasi kelembaban relatif</div>
          </div>
          <span class="chart-badge badge-pink">DHT11</span>
        </div>
        <div class="chart-wrap">
          <canvas id="chartHumid"></canvas>
        </div>
      </div>
      <div class="chart-card">
        <div class="chart-header">
          <div>
            <div class="chart-title">Distribusi Status Alert</div>
            <div class="chart-sub">Normal vs Panas per 10 record</div>
          </div>
          <span class="chart-badge badge-green">Overview</span>
        </div>
        <div class="chart-wrap">
          <canvas id="chartStatus"></canvas>
        </div>
      </div>
    </div>

    <!-- STATS CARD -->
    <div class="chart-card" style="margin-bottom:24px;">
      <div class="chart-header">
        <div>
          <div class="chart-title">Statistik Deskriptif</div>
          <div class="chart-sub">Ringkasan statistik dataset DHT11</div>
        </div>
      </div>
      <div style="overflow-x:auto;">
        <table>
          <thead>
            <tr>
              <th>Statistik</th>
              <th>Suhu (°C)</th>
              <th>Kelembaban (%)</th>
            </tr>
          </thead>
          <tbody>
            <tr><td>Jumlah Data</td><td>100</td><td>100</td></tr>
            <tr><td>Rata-rata (Mean)</td><td style="color:var(--accent);font-weight:600">29.47</td><td style="color:var(--accent2);font-weight:600">67.30</td></tr>
            <tr><td>Std. Deviasi</td><td>2.37</td><td>4.47</td></tr>
            <tr><td>Minimum</td><td>25.10</td><td>58.00</td></tr>
            <tr><td>Kuartil 1 (Q1)</td><td>27.50</td><td>63.95</td></tr>
            <tr><td>Median (Q2)</td><td>29.60</td><td>67.05</td></tr>
            <tr><td>Kuartil 3 (Q3)</td><td>31.40</td><td>70.75</td></tr>
            <tr><td>Maksimum</td><td>33.80</td><td>76.70</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════ PAGE: DATASET ══════════════════════════════ -->
<div id="page-dataset" class="page">
  <div class="hero" style="padding-top:36px;padding-bottom:32px;">
    <div class="hero-inner">
      <div>
        <div class="hero-eyebrow">🗃️ Dataset IoT DHT11</div>
        <h1>100 Record <span>Monitoring Sensor</span></h1>
        <p class="hero-desc">Data suhu dan kelembaban dari sensor DHT11 melalui ESP8266 ke ThingSpeak. Setiap record dikirim setiap 15 detik. Status PANAS aktif saat suhu melebihi 32°C.</p>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="table-card fade-in">
      <div class="table-header">
        <div class="section-header" style="margin:0">
          <div class="section-title">Data Sensor DHT11</div>
          <div class="section-sub" id="table-count">Menampilkan 100 dari 100 record</div>
        </div>
        <div class="table-controls">
          <input type="text" class="search-input" placeholder="🔍 Cari data..." oninput="filterTable()" id="searchInput">
          <button class="filter-btn" id="btn-all" onclick="setFilter('ALL')" style="background:var(--lavender-100);border-color:var(--lavender-300);color:var(--accent)">Semua</button>
          <button class="filter-btn" id="btn-normal" onclick="setFilter('NORMAL')">Normal</button>
          <button class="filter-btn" id="btn-panas" onclick="setFilter('PANAS')">Panas</button>
          <input type="file" id="fileUploadInput" accept=".csv,.json" style="display:none" onchange="handleFileUpload(event)">
          <button class="filter-btn" onclick="document.getElementById('fileUploadInput').click()" style="background:var(--lavender-100);border-color:var(--lavender-300);color:var(--accent);display:flex;align-items:center;gap:6px;">📂 Upload Dataset</button>
        </div>
      </div>
      <div class="table-scroll">
        <table>
          <thead>
            <tr>
              <th>No</th>
              <th>Suhu (°C)</th>
              <th>Kelembaban (%)</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody id="tableBody"></tbody>
        </table>
      </div>
      <div class="table-footer">
        <span id="page-info">Halaman 1 dari 5</span>
        <div class="pagination" id="pagination"></div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════ PAGE: ML ══════════════════════════════ -->
<div id="page-ml" class="page">
  <div class="hero" style="padding-top:36px;padding-bottom:32px;">
    <div class="hero-inner">
      <div>
        <div class="hero-eyebrow">🤖 AIoT Predictive Analytics</div>
        <h1>Prediksi Suhu dengan<br><span>Linear Regression</span></h1>
        <p class="hero-desc">Model machine learning yang dilatih dari dataset DHT11 untuk memprediksi suhu ruangan berdasarkan nilai kelembaban. Implementasi menggunakan Python scikit-learn di Google Colab.</p>
      </div>
    </div>
  </div>
  <div class="container">

    <!-- PREDICTOR -->
    <div class="predictor-card fade-in">
      <div class="section-header" style="margin-bottom:4px">
        <div class="section-title">🎯 Prediksi Suhu Interaktif</div>
        <div class="section-sub">Masukkan nilai kelembaban, model akan memprediksi suhu ruangan</div>
      </div>
      <div class="predictor-grid">
        <div class="input-group">
          <label>INPUT — Kelembaban (%)</label>
          <div class="range-wrap">
            <input type="range" min="58" max="77" value="70" id="humidSlider" oninput="updatePrediction()">
          </div>
          <div class="range-val" id="humidDisplay">70</div>
          <div class="range-unit">% Kelembaban Relatif (RH)</div>
          <div style="margin-top:12px;font-size:12px;color:var(--text-muted)">Rentang dataset: 58% – 76.7%</div>
        </div>
        <div class="predict-arrow">→</div>
        <div class="predict-result">
          <div style="font-size:12px;font-weight:600;color:var(--text-muted);letter-spacing:1px;text-transform:uppercase;margin-bottom:8px;">PREDIKSI SUHU</div>
          <div class="predict-temp" id="predictedTemp">29.74°C</div>
          <div class="predict-label">Suhu = 21.3483 + 0.11989 × Kelembaban</div>
          <div class="predict-status" id="predictStatus" style="background:#f0fdf4;color:#16a34a">✅ Kondisi NORMAL</div>
        </div>
      </div>
    </div>

    <!-- MODEL INFO + METRICS -->
    <div class="ml-grid fade-in-2">
      <div class="info-card">
        <div class="section-title" style="margin-bottom:16px">📐 Parameter Model</div>
        <div class="formula-box">Suhu = 21.3483 + 0.11989 × Kelembaban</div>
        <div class="metric-row">
          <span class="metric-name">Algoritma</span>
          <span class="metric-val" style="color:var(--accent)">Linear Regression</span>
        </div>
        <div class="metric-row">
          <span class="metric-name">Koefisien (β₁) <span class="tooltip-info">i</span></span>
          <div>
            <div class="metric-val" style="color:var(--accent)">0.11989</div>
            <div class="metric-badge">Slope garis regresi</div>
          </div>
        </div>
        <div class="metric-row">
          <span class="metric-name">Intercept (β₀)</span>
          <div>
            <div class="metric-val" style="color:var(--accent)">21.3483</div>
            <div class="metric-badge">Nilai y saat X = 0</div>
          </div>
        </div>
        <div class="metric-row">
          <span class="metric-name">Train / Test Split</span>
          <span class="metric-val" style="color:var(--text-secondary);font-size:14px">80 / 20 record</span>
        </div>
        <div class="metric-row">
          <span class="metric-name">Random State</span>
          <span class="metric-val" style="color:var(--text-secondary);font-size:14px">42</span>
        </div>
      </div>

      <div class="info-card">
        <div class="section-title" style="margin-bottom:16px">📏 Evaluasi Model</div>
        <div style="background:var(--lavender-50);border-radius:10px;padding:14px 16px;margin-bottom:16px;border:1px solid var(--lavender-100)">
          <div style="font-size:12px;color:var(--text-muted);margin-bottom:4px">Interpretasi R² Score</div>
          <div style="font-size:13px;color:var(--text-secondary);line-height:1.6">Nilai R² = -0.0005 menunjukkan kelembaban tunggal <strong>tidak cukup</strong> untuk memprediksi suhu secara akurat. Fitur waktu atau variabel lain diperlukan.</div>
        </div>
        <div class="metric-row">
          <span class="metric-name">MAE <span class="tooltip-info">i</span></span>
          <div>
            <div class="metric-val" style="color:#f59e0b">1.7187</div>
            <div class="metric-badge">Mean Absolute Error (°C)</div>
          </div>
        </div>
        <div class="metric-row">
          <span class="metric-name">MSE <span class="tooltip-info">i</span></span>
          <div>
            <div class="metric-val" style="color:#ef4444">4.8607</div>
            <div class="metric-badge">Mean Squared Error</div>
          </div>
        </div>
        <div class="metric-row">
          <span class="metric-name">R² Score <span class="tooltip-info">i</span></span>
          <div>
            <div class="metric-val" style="color:#ef4444">-0.0005</div>
            <div class="metric-badge">Koefisien Determinasi</div>
          </div>
        </div>
        <div class="metric-row">
          <span class="metric-name">Error Relatif</span>
          <div>
            <div class="metric-val" style="color:#f59e0b">~20%</div>
            <div class="metric-badge">Dari total rentang data</div>
          </div>
        </div>
      </div>
    </div>

    <!-- CHARTS ML -->
    <div class="charts-grid fade-in-3">
      <div class="chart-card">
        <div class="chart-header">
          <div>
            <div class="chart-title">Scatter Plot: Kelembaban vs Suhu</div>
            <div class="chart-sub">Sebaran data + garis regresi</div>
          </div>
          <span class="chart-badge badge-purple">R² = -0.0005</span>
        </div>
        <div class="chart-wrap">
          <canvas id="chartScatter"></canvas>
        </div>
        <div class="scatter-meta">
          <div class="scatter-stat">
            <div class="scatter-stat-val">Lemah</div>
            <div class="scatter-stat-label">Korelasi Linear</div>
          </div>
          <div class="scatter-stat">
            <div class="scatter-stat-val">Non-linear</div>
            <div class="scatter-stat-label">Pola Hubungan</div>
          </div>
          <div class="scatter-stat">
            <div class="scatter-stat-val">±0.12°C</div>
            <div class="scatter-stat-label">Pengaruh per 1% RH</div>
          </div>
        </div>
      </div>

      <div class="chart-card">
        <div class="chart-header">
          <div>
            <div class="chart-title">Aktual vs Prediksi (Data Testing)</div>
            <div class="chart-sub">20 data testing — selisih prediksi</div>
          </div>
          <span class="chart-badge badge-pink">20 record</span>
        </div>
        <div class="chart-wrap">
          <canvas id="chartActualPred"></canvas>
        </div>
      </div>
    </div>

    <!-- TESTING RESULTS TABLE -->
    <div class="table-card fade-in">
      <div class="table-header">
        <div>
          <div class="section-title">Hasil Prediksi Data Testing</div>
          <div class="section-sub">Perbandingan suhu aktual dan prediksi model (20 data testing)</div>
        </div>
      </div>
      <div class="table-scroll">
        <table>
          <thead>
            <tr>
              <th>No</th>
              <th>Index Data</th>
              <th>Suhu Aktual (°C)</th>
              <th>Prediksi Suhu (°C)</th>
              <th>Selisih (°C)</th>
              <th>Akurasi</th>
            </tr>
          </thead>
          <tbody id="mlTableBody"></tbody>
        </table>
      </div>
    </div>

  </div>
</div>

<!-- ══════════════════════════════ PAGE: ABOUT ══════════════════════════════ -->
<div id="page-about" class="page">
  <div class="hero" style="padding-top:36px;padding-bottom:32px;">
    <div class="hero-inner">
      <div>
        <div class="hero-eyebrow">📋 Tentang Proyek</div>
        <h1>Implementasi <span>Smart Monitoring</span><br>& AIoT Analytics</h1>
        <p class="hero-desc">Mini riset IoT & AIoT dari Program Studi Sistem dan Teknologi Informasi, Universitas Muhammadiyah Prof. Dr. Hamka (UHAMKA), 2026.</p>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="about-grid fade-in">
      <div class="about-card">
        <div class="section-title" style="margin-bottom:16px">👩‍💻 Tim Pengembang</div>
        <div class="tech-item">
          <div class="tech-icon" style="background:var(--lavender-100);font-size:20px">👩</div>
          <div>
            <div class="tech-name">Elvira Putri Ramadhani</div>
            <div class="tech-desc">NIM 2403045016 · STI FTII UHAMKA</div>
          </div>
        </div>
        <div class="tech-item">
          <div class="tech-icon" style="background:var(--pink-100);font-size:20px">👩</div>
          <div>
            <div class="tech-name">Syifa Nur Fauziah</div>
            <div class="tech-desc">NIM 2403045036 · STI FTII UHAMKA</div>
          </div>
        </div>
        <div class="tech-item">
          <div class="tech-icon" style="background:var(--lavender-50);font-size:20px">🎓</div>
          <div>
            <div class="tech-name">Dr. Ir. Mohammad Givia Efgivia, M.Kom.</div>
            <div class="tech-desc">Dosen Pengampu · UHAMKA 2026</div>
          </div>
        </div>
      </div>

      <div class="about-card">
        <div class="section-title" style="margin-bottom:16px">🛠️ Teknologi yang Digunakan</div>
        <div class="tech-item">
          <div class="tech-icon" style="background:#e8f5e9">🔬</div>
          <div>
            <div class="tech-name">Sensor DHT11</div>
            <div class="tech-desc">Mengukur suhu (0–50°C ±2°C) & kelembaban (20–90% ±5%)</div>
          </div>
        </div>
        <div class="tech-item">
          <div class="tech-icon" style="background:#e3f2fd">📡</div>
          <div>
            <div class="tech-name">ESP8266 NodeMCU</div>
            <div class="tech-desc">Mikrokontroler Wi-Fi · Kirim data via HTTP ke ThingSpeak</div>
          </div>
        </div>
        <div class="tech-item">
          <div class="tech-icon" style="background:#fff8e1">☁️</div>
          <div>
            <div class="tech-name">ThingSpeak IoT Platform</div>
            <div class="tech-desc">Cloud storage & visualisasi real-time · MathWorks</div>
          </div>
        </div>
        <div class="tech-item">
          <div class="tech-icon" style="background:#fce4ec">🐍</div>
          <div>
            <div class="tech-name">Python + scikit-learn</div>
            <div class="tech-desc">Linear Regression · pandas · matplotlib · Google Colab</div>
          </div>
        </div>
      </div>

      <div class="about-card">
        <div class="section-title" style="margin-bottom:16px">⚙️ Alur Kerja Sistem IoT</div>
        <ul class="step-list">
          <li class="step-item"><div class="step-num">1</div><div class="step-text">ESP8266 inisialisasi koneksi Wi-Fi dan sensor DHT11 saat dinyalakan</div></li>
          <li class="step-item"><div class="step-num">2</div><div class="step-text">Setiap 15 detik, DHT11 membaca nilai suhu (°C) dan kelembaban (%)</div></li>
          <li class="step-item"><div class="step-num">3</div><div class="step-text">Data dikirim ke ThingSpeak melalui HTTP GET request secara otomatis</div></li>
          <li class="step-item"><div class="step-num">4</div><div class="step-text">Sistem memeriksa suhu — jika &gt;32°C, alert aktif dan LED menyala</div></li>
          <li class="step-item"><div class="step-num">5</div><div class="step-text">ThingSpeak memperbarui grafik dan dashboard secara real-time</div></li>
        </ul>
      </div>

      <div class="about-card">
        <div class="section-title" style="margin-bottom:16px">🤖 Pipeline AIoT Machine Learning</div>
        <ul class="step-list">
          <li class="step-item"><div class="step-num">1</div><div class="step-text">Import library: pandas, numpy, matplotlib, scikit-learn di Google Colab</div></li>
          <li class="step-item"><div class="step-num">2</div><div class="step-text">Inisialisasi dataset 100 record — eksplorasi & statistik deskriptif</div></li>
          <li class="step-item"><div class="step-num">3</div><div class="step-text">Visualisasi time-series suhu, kelembaban, dan scatter plot</div></li>
          <li class="step-item"><div class="step-num">4</div><div class="step-text">Split data 80:20 (train/test) dengan random_state=42</div></li>
          <li class="step-item"><div class="step-num">5</div><div class="step-text">Training model Linear Regression · evaluasi MAE, MSE, R² Score</div></li>
          <li class="step-item"><div class="step-num">6</div><div class="step-text">Prediksi suhu berdasarkan input kelembaban baru dari sensor</div></li>
        </ul>
      </div>
    </div>

    <div class="about-card fade-in-2" style="margin-bottom:24px;">
      <div class="section-title" style="margin-bottom:16px">💡 Kesimpulan & Saran Pengembangan</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
        <div>
          <div style="font-size:13px;font-weight:600;color:var(--text-secondary);margin-bottom:10px;">✅ Pencapaian</div>
          <ul style="list-style:none;display:flex;flex-direction:column;gap:8px;">
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Sistem monitoring IoT real-time berhasil diimplementasikan dengan DHT11, ESP8266, dan ThingSpeak</li>
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Alert threshold 32°C berfungsi baik — 18 kejadian PANAS terdeteksi dari 100 record</li>
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Pipeline AIoT Linear Regression berhasil dibangun dengan persamaan: Suhu = 21.3483 + 0.11989 × Kelembaban</li>
          </ul>
        </div>
        <div>
          <div style="font-size:13px;font-weight:600;color:var(--text-secondary);margin-bottom:10px;">🚀 Saran Pengembangan</div>
          <ul style="list-style:none;display:flex;flex-direction:column;gap:8px;">
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Tambahkan fitur waktu (jam, hari) sebagai variabel independen untuk meningkatkan akurasi model</li>
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Coba algoritma Random Forest atau LSTM untuk menangkap pola non-linear lebih baik</li>
            <li style="font-size:13px;color:var(--text-secondary);display:flex;gap:8px;"><span>•</span>Integrasikan notifikasi Telegram Bot API saat alert PANAS terdeteksi</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
// ─── DATA ───
const DATA = [
  [28.3,64.9],[29.3,68.1],[29.7,69.4],[30.7,71.2],[32.5,73.2],[33.7,61.7],
  [27.7,61.4],[25.4,66.6],[28.5,63.3],[29.8,67.8],[30.2,70.1],[30.6,70.6],
  [31.5,74.6],[33.2,58.1],[27.5,64.3],[25.5,67.9],[28.8,64.9],[28.9,67.0],
  [30.3,70.7],[30.9,73.1],[31.6,73.0],[32.8,62.0],[27.7,63.5],[25.9,65.7],
  [28.2,66.9],[29.1,67.5],[29.8,71.8],[32.0,70.4],[31.0,73.4],[33.0,61.1],
  [27.0,62.5],[26.8,66.9],[28.1,64.9],[28.6,66.3],[30.5,68.9],[31.6,72.2],
  [31.2,73.6],[33.0,59.6],[27.0,64.0],[25.4,66.6],[27.1,64.1],[28.9,67.9],
  [29.3,71.1],[31.4,70.9],[31.2,75.1],[32.6,59.7],[26.5,62.8],[25.1,68.8],
  [27.5,65.2],[28.3,67.6],[29.9,69.6],[30.9,72.6],[31.0,73.6],[32.2,59.8],
  [27.4,63.5],[26.2,65.4],[27.7,65.9],[29.0,67.7],[30.6,68.7],[31.4,70.3],
  [32.2,76.7],[33.7,61.1],[26.5,62.6],[26.2,65.8],[27.3,63.7],[28.2,67.0],
  [29.3,68.6],[31.6,71.9],[32.4,73.5],[33.3,59.9],[26.6,63.8],[25.7,67.6],
  [27.3,66.0],[29.3,69.7],[30.3,69.1],[31.6,73.9],[31.2,73.4],[33.2,59.6],
  [26.3,62.3],[26.9,65.4],[28.4,63.4],[28.2,67.1],[29.7,71.2],[30.8,70.7],
  [32.3,76.4],[33.8,58.0],[26.9,62.4],[25.1,65.6],[28.3,64.0],[29.5,67.3],
  [29.9,71.1],[30.4,71.1],[32.8,76.3],[32.8,61.9],[26.0,61.8],[25.9,65.9],
  [28.3,65.9],[29.8,66.5],[30.0,69.8],[31.6,72.0]
];

const ML_TEST = [
  {no:1,idx:83,actual:30.8,pred:29.82},
  {no:2,idx:53,actual:32.2,pred:28.52},
  {no:3,idx:70,actual:26.6,pred:29.00},
  {no:4,idx:45,actual:32.6,pred:28.51},
  {no:5,idx:44,actual:31.2,pred:30.35},
  {no:6,idx:39,actual:25.4,pred:29.33},
  {no:7,idx:22,actual:27.7,pred:28.96},
  {no:8,idx:80,actual:28.4,pred:28.95},
  {no:9,idx:10,actual:30.2,pred:29.75},
  {no:10,idx:0,actual:28.3,pred:29.13},
  {no:11,idx:18,actual:30.3,pred:29.82},
  {no:12,idx:30,actual:27.0,pred:28.84},
  {no:13,idx:73,actual:29.3,pred:29.70},
  {no:14,idx:33,actual:28.6,pred:29.30},
  {no:15,idx:90,actual:29.9,pred:29.87},
  {no:16,idx:66,actual:28.2,pred:29.10},
  {no:17,idx:37,actual:33.0,pred:28.65},
  {no:18,idx:99,actual:31.6,pred:29.95},
  {no:19,idx:62,actual:26.5,pred:28.96},
  {no:20,idx:48,actual:27.5,pred:29.13}
];

// ─── CHART DEFAULTS ───
Chart.defaults.font.family = "'Inter', sans-serif";
Chart.defaults.color = '#9088a4';

const PURPLE = '#8b6fdf', PINK = '#c97dd4', LAVL = '#b9a8f1', LAVD = '#7c5fd9';
const GREEN = '#22c55e', RED = '#ef4444';

function gradH(ctx, c1, c2) {
  const g = ctx.createLinearGradient(0, 0, 0, 300);
  g.addColorStop(0, c1); g.addColorStop(1, c2); return g;
}

// ─── MONITORING CHARTS ───
function initMonitoring() {
  const labels = DATA.map((_,i)=>i+1);
  const temps = DATA.map(d=>d[0]);
  const humids = DATA.map(d=>d[1]);

  // Temp chart
  const ctxT = document.getElementById('chartTemp').getContext('2d');
  const gradT = gradH(ctxT, 'rgba(139,111,223,0.3)', 'rgba(139,111,223,0)');
  new Chart(ctxT, {
    type:'line',
    data:{
      labels,
      datasets:[{
        label:'Suhu (°C)',
        data: temps,
        borderColor: PURPLE,
        backgroundColor: gradT,
        borderWidth: 2,
        pointRadius: 0,
        pointHoverRadius: 5,
        pointHoverBackgroundColor: PURPLE,
        fill: true,
        tension: 0.35
      },{
        label:'Threshold 32°C',
        data: new Array(100).fill(32),
        borderColor: RED,
        borderWidth: 1.5,
        borderDash: [6,4],
        pointRadius: 0,
        fill: false
      }]
    },
    options:{
      responsive:true, maintainAspectRatio:false,
      interaction:{mode:'index',intersect:false},
      plugins:{legend:{display:true,position:'top',labels:{usePointStyle:true,pointStyleWidth:10,boxHeight:8}},tooltip:{callbacks:{label:c=>` ${c.dataset.label}: ${c.parsed.y}${c.datasetIndex===0?'°C':''}`}}},
      scales:{
        x:{grid:{color:'rgba(0,0,0,0.03)'},ticks:{maxTicksLimit:10}},
        y:{grid:{color:'rgba(0,0,0,0.04)'},ticks:{callback:v=>v+'°C'},suggestedMin:24,suggestedMax:35}
      }
    }
  });

  // Humid chart
  const ctxH = document.getElementById('chartHumid').getContext('2d');
  const gradPink = gradH(ctxH, 'rgba(201,125,212,0.25)', 'rgba(201,125,212,0)');
  new Chart(ctxH, {
    type:'line',
    data:{
      labels,
      datasets:[{
        label:'Kelembaban (%)',
        data: humids,
        borderColor: PINK,
        backgroundColor: gradPink,
        borderWidth: 2,
        pointRadius: 0,
        fill: true,
        tension: 0.35
      }]
    },
    options:{
      responsive:true, maintainAspectRatio:false,
      plugins:{legend:{display:false}},
      scales:{
        x:{grid:{color:'rgba(0,0,0,0.03)'},ticks:{maxTicksLimit:10}},
        y:{grid:{color:'rgba(0,0,0,0.04)'},ticks:{callback:v=>v+'%'},suggestedMin:55,suggestedMax:80}
      }
    }
  });

  // Status bar chart
  const statusGroups = [];
  const normalArr = [], panasArr = [];
  for(let i=0;i<10;i++){
    const chunk = DATA.slice(i*10,(i+1)*10);
    const n = chunk.filter(d=>d[0]<=32).length;
    const p = chunk.filter(d=>d[0]>32).length;
    statusGroups.push(`${i*10+1}-${i*10+10}`);
    normalArr.push(n); panasArr.push(p);
  }
  const ctxS = document.getElementById('chartStatus').getContext('2d');
  new Chart(ctxS, {
    type:'bar',
    data:{
      labels: statusGroups,
      datasets:[
        {label:'Normal',data:normalArr,backgroundColor:'rgba(34,197,94,0.7)',borderRadius:4},
        {label:'Panas',data:panasArr,backgroundColor:'rgba(239,68,68,0.7)',borderRadius:4}
      ]
    },
    options:{
      responsive:true, maintainAspectRatio:false,
      plugins:{legend:{display:true,position:'top',labels:{usePointStyle:true}}},
      scales:{x:{stacked:true,grid:{display:false}},y:{stacked:true,grid:{color:'rgba(0,0,0,0.04)'},ticks:{stepSize:1}}}
    }
  });
}

// ─── TABLE ───
let currentPage = 1, currentFilter = 'ALL', searchTerm = '';
const ROWS_PER_PAGE = 20;

function getStatus(t){ return t > 32 ? 'PANAS' : 'NORMAL'; }

function getFilteredData() {
  return DATA.map((d,i)=>({no:i+1,suhu:d[0],humid:d[1],status:getStatus(d[0])}))
    .filter(r=>{
      const matchStatus = currentFilter === 'ALL' || r.status === currentFilter;
      const matchSearch = searchTerm === '' || r.suhu.toString().includes(searchTerm) || r.humid.toString().includes(searchTerm) || r.no.toString().includes(searchTerm);
      return matchStatus && matchSearch;
    });
}

function renderTable() {
  const filtered = getFilteredData();
  const total = filtered.length;
  const totalPages = Math.max(1, Math.ceil(total / ROWS_PER_PAGE));
  if(currentPage > totalPages) currentPage = 1;
  const slice = filtered.slice((currentPage-1)*ROWS_PER_PAGE, currentPage*ROWS_PER_PAGE);

  document.getElementById('table-count').textContent = `Menampilkan ${total} dari 100 record`;
  document.getElementById('page-info').textContent = `Halaman ${currentPage} dari ${totalPages}`;

  const tbody = document.getElementById('tableBody');
  tbody.innerHTML = slice.map(r=>`
    <tr>
      <td class="muted">${r.no}</td>
      <td style="font-weight:600;color:${r.suhu>32?'#ef4444':'var(--lavender-500)'}">${r.suhu.toFixed(1)}</td>
      <td style="color:var(--accent2)">${r.humid.toFixed(1)}</td>
      <td><span class="badge ${r.status==='PANAS'?'badge-panas':'badge-normal'}">${r.status==='PANAS'?'🔴':'✅'} ${r.status}</span></td>
    </tr>`).join('');

  const pg = document.getElementById('pagination');
  pg.innerHTML = '';
  const makePgBtn = (lbl, p, isActive) => {
    const btn = document.createElement('button');
    btn.className = 'page-btn' + (isActive?' active-page':'');
    btn.textContent = lbl;
    btn.onclick = () => { currentPage = p; renderTable(); };
    pg.appendChild(btn);
  };
  if(currentPage > 1) makePgBtn('‹', currentPage-1, false);
  for(let i=1;i<=totalPages;i++) makePgBtn(i, i, i===currentPage);
  if(currentPage < totalPages) makePgBtn('›', currentPage+1, false);
}

function handleFileUpload(event) {
  const file = event.target.files[0];
  if (!file) return;
  const ext = file.name.split('.').pop().toLowerCase();
  const reader = new FileReader();
  reader.onload = function(e) {
    try {
      let newData = [];
      if (ext === 'json') {
        const parsed = JSON.parse(e.target.result);
        const arr = Array.isArray(parsed) ? parsed : (parsed.data || parsed.dataset || []);
        newData = arr.map(row => {
          if (Array.isArray(row)) return [parseFloat(row[0]), parseFloat(row[1])];
          const suhu = parseFloat(row.suhu ?? row.temperature ?? row.temp ?? row[Object.keys(row)[0]]);
          const humid = parseFloat(row.kelembaban ?? row.humidity ?? row.humid ?? row[Object.keys(row)[1]]);
          return [suhu, humid];
        }).filter(r => !isNaN(r[0]) && !isNaN(r[1]));
      } else {
        const lines = e.target.result.trim().split('\n');
        const start = isNaN(parseFloat(lines[0].split(',')[0])) ? 1 : 0;
        for (let i = start; i < lines.length; i++) {
          const cols = lines[i].split(',');
          if (cols.length >= 2) {
            const suhu = parseFloat(cols[0]);
            const humid = parseFloat(cols[1]);
            if (!isNaN(suhu) && !isNaN(humid)) newData.push([suhu, humid]);
          }
        }
      }
      if (newData.length === 0) { alert('❌ Data tidak ditemukan atau format tidak valid.'); return; }
      DATA.splice(0, DATA.length, ...newData);
      currentPage = 1;
      renderTable();
      document.getElementById('table-count').textContent = `Menampilkan ${DATA.length} dari ${DATA.length} record`;
      alert(`✅ Dataset berhasil diunggah! ${DATA.length} record dimuat dari "${file.name}".`);
      event.target.value = '';
    } catch(err) {
      alert('❌ Gagal membaca file: ' + err.message);
    }
  };
  reader.readAsText(file);
}

function setFilter(f) {
  currentFilter = f; currentPage = 1;
  ['ALL','NORMAL','PANAS'].forEach(x=>{
    const el = document.getElementById('btn-'+x.toLowerCase());
    if(el) el.className = 'filter-btn' + (x===f?' active-filter':'');
  });
  renderTable();
}
function filterTable() {
  searchTerm = document.getElementById('searchInput').value;
  currentPage = 1;
  renderTable();
}

// ─── ML CHARTS ───
function initML() {
  // Scatter
  const ctxSc = document.getElementById('chartScatter').getContext('2d');
  const scatterData = DATA.map(d=>({x:d[1],y:d[0]}));
  // Regression line
  const b1 = 0.11989, b0 = 21.3483;
  const lineX = [58,77];
  const lineData = lineX.map(x=>({x,y:b0+b1*x}));

  new Chart(ctxSc, {
    type:'scatter',
    data:{
      datasets:[
        {
          label:'Data Aktual',
          data: scatterData,
          backgroundColor: DATA.map(d=> d[0]>32 ? 'rgba(239,68,68,0.55)':'rgba(139,111,223,0.45)'),
          pointRadius:5,pointHoverRadius:7,
        },
        {
          label:'Garis Regresi',
          type:'line',
          data: lineData,
          borderColor: PINK,
          borderWidth:2.5,
          pointRadius:0,
          fill:false,
          borderDash:[5,4]
        }
      ]
    },
    options:{
      responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:true,position:'top',labels:{usePointStyle:true}}},
      scales:{
        x:{title:{display:true,text:'Kelembaban (%)'},grid:{color:'rgba(0,0,0,0.04)'}},
        y:{title:{display:true,text:'Suhu (°C)'},grid:{color:'rgba(0,0,0,0.04)'},suggestedMin:24,suggestedMax:35}
      }
    }
  });

  // Actual vs Predicted
  const ctxAP = document.getElementById('chartActualPred').getContext('2d');
  new Chart(ctxAP, {
    type:'bar',
    data:{
      labels: ML_TEST.map(r=>`#${r.idx+1}`),
      datasets:[
        {label:'Suhu Aktual',data:ML_TEST.map(r=>r.actual),backgroundColor:'rgba(139,111,223,0.65)',borderRadius:4},
        {label:'Prediksi',data:ML_TEST.map(r=>r.pred),backgroundColor:'rgba(201,125,212,0.6)',borderRadius:4}
      ]
    },
    options:{
      responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:true,position:'top',labels:{usePointStyle:true}}},
      scales:{
        x:{grid:{display:false},ticks:{font:{size:10}}},
        y:{grid:{color:'rgba(0,0,0,0.04)'},ticks:{callback:v=>v+'°C'},suggestedMin:24,suggestedMax:35}
      }
    }
  });

  // ML Table
  const tbody = document.getElementById('mlTableBody');
  tbody.innerHTML = ML_TEST.map(r=>{
    const diff = Math.abs(r.actual - r.pred);
    const acc = Math.max(0, 100 - (diff / 8.7 * 100));
    const clr = diff < 1 ? '#16a34a' : diff < 2 ? '#f59e0b' : '#ef4444';
    return `<tr>
      <td class="muted">${r.no}</td>
      <td class="muted">${r.idx + 1}</td>
      <td style="font-weight:600;color:var(--lavender-500)">${r.actual.toFixed(1)}</td>
      <td style="color:var(--accent2)">${r.pred.toFixed(2)}</td>
      <td style="font-weight:600;color:${clr}">${diff.toFixed(2)}</td>
      <td><span class="chart-badge" style="background:${acc>80?'#f0fdf4':acc>60?'#fffbeb':'#fff1f1'};color:${acc>80?'#16a34a':acc>60?'#d97706':'#ef4444'}">${acc.toFixed(1)}%</span></td>
    </tr>`;
  }).join('');
}

// ─── PREDICTOR ───
function updatePrediction() {
  const h = parseFloat(document.getElementById('humidSlider').value);
  document.getElementById('humidDisplay').textContent = h;
  const t = 21.3483 + 0.11989 * h;
  document.getElementById('predictedTemp').textContent = t.toFixed(2)+'°C';
  const st = document.getElementById('predictStatus');
  if(t > 32) {
    st.textContent = '🔴 Potensi PANAS';
    st.style.background = '#fff1f1'; st.style.color = '#ef4444';
  } else {
    st.textContent = '✅ Kondisi NORMAL';
    st.style.background = '#f0fdf4'; st.style.color = '#16a34a';
  }
}

// ─── PAGE NAV ───
let mlInited = false, monInited = false;

function showPage(name) {
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t=>t.classList.remove('active'));
  document.getElementById('page-'+name).classList.add('active');
  const tabs = document.querySelectorAll('.nav-tab');
  const map = {monitoring:0, dataset:1, ml:2, about:3};
  tabs[map[name]]?.classList.add('active');

  if(name==='monitoring' && !monInited) { initMonitoring(); monInited=true; }
  if(name==='dataset') { renderTable(); }
  if(name==='ml' && !mlInited) { initML(); mlInited=true; }
}

// ─── INIT ───
window.addEventListener('DOMContentLoaded', ()=>{
  initMonitoring(); monInited = true;
  renderTable();
  updatePrediction();
});
</script>
</body>
</html>
