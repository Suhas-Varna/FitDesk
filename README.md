<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Gym Management System – README</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;700&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg:        #0a0a0a;
      --surface:   #111111;
      --card:      #161616;
      --border:    #222222;
      --accent:    #e8ff47;
      --accent2:   #ff5c3a;
      --accent3:   #3affce;
      --text:      #f0f0f0;
      --muted:     #777777;
      --heading:   'Bebas Neue', sans-serif;
      --body:      'DM Sans', sans-serif;
      --mono:      'JetBrains Mono', monospace;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--body);
      font-size: 15px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ── NOISE TEXTURE OVERLAY ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 0 32px 80px;
      position: relative;
      z-index: 1;
    }

    /* ── HERO ── */
    .hero {
      padding: 80px 0 60px;
      border-bottom: 1px solid var(--border);
      position: relative;
      overflow: hidden;
    }

    .hero-bg-text {
      position: absolute;
      top: -10px;
      right: -20px;
      font-family: var(--heading);
      font-size: 180px;
      color: rgba(232,255,71,0.04);
      user-select: none;
      white-space: nowrap;
      pointer-events: none;
    }

    .hero-label {
      display: inline-block;
      font-family: var(--mono);
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--accent);
      border: 1px solid var(--accent);
      padding: 4px 12px;
      border-radius: 2px;
      margin-bottom: 24px;
      animation: fadeUp 0.6s ease both;
    }

    .hero h1 {
      font-family: var(--heading);
      font-size: clamp(56px, 10vw, 96px);
      line-height: 0.95;
      letter-spacing: 1px;
      color: var(--text);
      animation: fadeUp 0.7s 0.1s ease both;
    }

    .hero h1 span { color: var(--accent); }

    .hero-sub {
      margin-top: 20px;
      font-size: 16px;
      color: var(--muted);
      max-width: 540px;
      animation: fadeUp 0.7s 0.2s ease both;
    }

    .badges {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 28px;
      animation: fadeUp 0.7s 0.3s ease both;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-family: var(--mono);
      font-size: 11px;
      padding: 5px 12px;
      border-radius: 3px;
      font-weight: 600;
      letter-spacing: 0.5px;
    }

    .badge-py   { background: #1e3a5f; color: #4eaaff; border: 1px solid #2a5080; }
    .badge-st   { background: #3a1414; color: #ff5c3a; border: 1px solid #5a2020; }
    .badge-sql  { background: #1a2e1a; color: #3affce; border: 1px solid #2a4e2a; }
    .badge-ok   { background: #1e2b10; color: var(--accent); border: 1px solid #3a5020; }

    /* ── SECTION ── */
    section {
      padding: 56px 0 0;
    }

    .section-label {
      font-family: var(--mono);
      font-size: 10px;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 6px;
    }

    h2 {
      font-family: var(--heading);
      font-size: 42px;
      letter-spacing: 0.5px;
      color: var(--text);
      margin-bottom: 24px;
      line-height: 1;
    }

    h2 .accent { color: var(--accent); }

    .divider {
      height: 1px;
      background: linear-gradient(90deg, var(--accent) 0%, transparent 60%);
      margin-bottom: 32px;
    }

    p { color: #aaa; margin-bottom: 14px; }
    p strong { color: var(--text); }

    /* ── FEATURE GRID ── */
    .feature-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 16px;
      margin-top: 8px;
    }

    .feature-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 22px 20px;
      transition: border-color 0.2s, transform 0.2s;
      position: relative;
      overflow: hidden;
    }

    .feature-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: var(--accent);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s ease;
    }

    .feature-card:hover { border-color: #333; transform: translateY(-2px); }
    .feature-card:hover::before { transform: scaleX(1); }

    .feature-icon { font-size: 22px; margin-bottom: 10px; }
    .feature-title { font-weight: 700; color: var(--text); font-size: 14px; margin-bottom: 6px; }
    .feature-desc { font-size: 13px; color: var(--muted); line-height: 1.5; }

    /* ── TECH TABLE ── */
    .tech-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 8px;
    }

    .tech-table th {
      font-family: var(--mono);
      font-size: 10px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--muted);
      text-align: left;
      padding: 10px 16px;
      border-bottom: 1px solid var(--border);
    }

    .tech-table td {
      padding: 14px 16px;
      border-bottom: 1px solid #1a1a1a;
      font-size: 14px;
      color: #bbb;
    }

    .tech-table tr:hover td { background: #111; color: var(--text); }

    .tech-table td:first-child {
      font-family: var(--mono);
      font-size: 12px;
      color: var(--accent3);
      font-weight: 600;
      white-space: nowrap;
    }

    /* ── DB SECTION ── */
    .entity-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 14px;
      margin-bottom: 32px;
    }

    .entity-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 18px;
    }

    .entity-icon { font-size: 20px; margin-bottom: 8px; }
    .entity-name { font-weight: 700; font-size: 13px; color: var(--text); margin-bottom: 4px; }
    .entity-desc { font-size: 12px; color: var(--muted); line-height: 1.5; }

    .rel-block {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 20px 24px;
    }

    .rel-block .rel-title {
      font-family: var(--mono);
      font-size: 10px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 14px;
    }

    .rel-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 10px 0;
      border-bottom: 1px solid #1a1a1a;
      font-size: 14px;
      color: #bbb;
    }

    .rel-item:last-child { border-bottom: none; }

    .rel-badge {
      font-family: var(--mono);
      font-size: 10px;
      font-weight: 700;
      padding: 3px 8px;
      border-radius: 2px;
      background: #1e2b10;
      color: var(--accent);
      border: 1px solid #3a5020;
      white-space: nowrap;
    }

    /* ── ARCHITECTURE ── */
    .arch-box {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 32px 28px;
      margin-top: 8px;
    }

    .arch-row {
      display: flex;
      align-items: stretch;
      gap: 0;
      margin-bottom: 0;
    }

    .arch-node {
      background: #111;
      border: 1px solid #2a2a2a;
      border-radius: 5px;
      padding: 16px 18px;
      flex: 1;
      text-align: center;
      position: relative;
    }

    .arch-node .node-label {
      font-family: var(--mono);
      font-size: 10px;
      letter-spacing: 2px;
      color: var(--muted);
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .arch-node .node-title {
      font-weight: 700;
      font-size: 13px;
      color: var(--text);
    }

    .arch-node .node-tech {
      font-size: 11px;
      color: var(--accent);
      font-family: var(--mono);
      margin-top: 4px;
    }

    .arch-arrow {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 0 12px;
      color: var(--muted);
      font-size: 18px;
    }

    .arch-divider {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 12px 0;
      color: var(--muted);
      font-size: 20px;
    }

    /* ── CODE BLOCK ── */
    .code-block {
      background: #0d0d0d;
      border: 1px solid var(--border);
      border-radius: 6px;
      overflow: hidden;
      margin-top: 8px;
    }

    .code-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px 16px;
      background: #111;
      border-bottom: 1px solid var(--border);
    }

    .code-dots { display: flex; gap: 6px; }
    .dot { width: 10px; height: 10px; border-radius: 50%; }
    .dot-r { background: #ff5f57; }
    .dot-y { background: #febc2e; }
    .dot-g { background: #28c840; }

    .code-lang {
      font-family: var(--mono);
      font-size: 10px;
      color: var(--muted);
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .code-body {
      padding: 20px 22px;
      font-family: var(--mono);
      font-size: 13px;
      line-height: 1.8;
      color: #aaa;
      overflow-x: auto;
    }

    .code-body .cm { color: #555; }
    .code-body .kw { color: var(--accent3); }
    .code-body .st { color: #e8a87c; }
    .code-body .num { color: var(--accent); }
    .code-body .cmd { color: #aaa; }
    .code-body .prompt { color: var(--accent2); user-select: none; }

    /* ── TEAM ── */
    .team-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 16px;
    }

    .team-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 24px 20px;
      text-align: center;
      transition: border-color 0.2s;
    }

    .team-card:hover { border-color: #333; }

    .team-avatar {
      width: 52px; height: 52px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
      display: flex; align-items: center; justify-content: center;
      font-family: var(--heading);
      font-size: 22px;
      color: #000;
      margin: 0 auto 12px;
    }

    .team-name { font-weight: 700; font-size: 14px; color: var(--text); margin-bottom: 10px; }

    .team-links { display: flex; gap: 8px; justify-content: center; }

    .team-link {
      font-family: var(--mono);
      font-size: 10px;
      padding: 4px 10px;
      border-radius: 3px;
      text-decoration: none;
      border: 1px solid var(--border);
      color: var(--muted);
      transition: color 0.2s, border-color 0.2s;
    }

    .team-link:hover { color: var(--accent); border-color: var(--accent); }

    /* ── FOOTER ── */
    footer {
      margin-top: 80px;
      padding-top: 32px;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: gap;
      gap: 12px;
    }

    footer .foot-brand {
      font-family: var(--heading);
      font-size: 24px;
      color: var(--text);
    }

    footer .foot-brand span { color: var(--accent); }

    footer .foot-note {
      font-family: var(--mono);
      font-size: 11px;
      color: var(--muted);
    }

    /* ── TOC ── */
    .toc {
      background: var(--card);
      border: 1px solid var(--border);
      border-left: 3px solid var(--accent);
      border-radius: 0 6px 6px 0;
      padding: 20px 24px;
      margin-bottom: 48px;
    }

    .toc-title {
      font-family: var(--mono);
      font-size: 10px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 12px;
    }

    .toc-list {
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      gap: 8px 20px;
    }

    .toc-list a {
      font-size: 13px;
      color: #888;
      text-decoration: none;
      transition: color 0.2s;
    }

    .toc-list a:hover { color: var(--accent); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* ── SCROLLBAR ── */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: #333; border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: #555; }
  </style>
</head>
<body>

<div class="container">

  <!-- ── HERO ── -->
  <div class="hero">
    <div class="hero-bg-text">GYM</div>
    <div class="hero-label">● Project README</div>
    <h1>Gym<br/><span>Management</span><br/>System</h1>
    <p class="hero-sub">
      Manage gym members, trainers, memberships, and workout classes —
      all in one place with <strong>Python</strong>, <strong>Streamlit</strong> &amp; <strong>MySQL</strong>.
    </p>
    <div class="badges">
      <span class="badge badge-py">🐍 Python 3.x</span>
      <span class="badge badge-st">⚡ Streamlit</span>
      <span class="badge badge-sql">🗄️ MySQL</span>
      <span class="badge badge-ok">✔ Status: Active</span>
    </div>
  </div>

  <!-- ── TABLE OF CONTENTS ── -->
  <section>
    <div class="toc">
      <div class="toc-title">Table of Contents</div>
      <ul class="toc-list">
        <li><a href="#overview">Overview</a></li>
        <li><a href="#features">Features</a></li>
        <li><a href="#techstack">Tech Stack</a></li>
        <li><a href="#database">Database Design</a></li>
        <li><a href="#architecture">Architecture</a></li>
        <li><a href="#setup">Setup &amp; Installation</a></li>
        <li><a href="#team">Team</a></li>
      </ul>
    </div>
  </section>

  <!-- ── OVERVIEW ── -->
  <section id="overview">
    <div class="section-label">01 — Overview</div>
    <h2>What is <span class="accent">GMS?</span></h2>
    <div class="divider"></div>
    <p>
      The <strong>Gym Management System</strong> is a lightweight, full-stack web application
      built with <strong>Python</strong> and <strong>Streamlit</strong>, powered by a <strong>MySQL</strong> relational database.
    </p>
    <p>
      It provides gym administrators with a clean, intuitive interface to manage members,
      memberships, trainers, and workout classes — complete with secure login authentication,
      duplicate prevention logic, and real-time database synchronization.
    </p>
    <p>
      Designed as a <strong>DBMS mini-project</strong>, it demonstrates full CRUD operations,
      relational constraints, and a clean UI layer built entirely on Python.
    </p>
  </section>

  <!-- ── FEATURES ── -->
  <section id="features">
    <div class="section-label">02 — Features</div>
    <h2>What it <span class="accent">Does</span></h2>
    <div class="divider"></div>
    <div class="feature-grid">
      <div class="feature-card">
        <div class="feature-icon">🔐</div>
        <div class="feature-title">Secure Login</div>
        <div class="feature-desc">Username &amp; password authentication before accessing any management module.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">👤</div>
        <div class="feature-title">Member Management</div>
        <div class="feature-desc">Add, view, update, and delete member records including name, age, gender, phone, and address.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💳</div>
        <div class="feature-title">Membership Management</div>
        <div class="feature-desc">One-to-one memberships per member with price, start date, end date, and gym branch tracking.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🏋️</div>
        <div class="feature-title">Trainer Management</div>
        <div class="feature-desc">Full CRUD for trainer records covering name, age, and contact number.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🧘</div>
        <div class="feature-title">Workout Classes</div>
        <div class="feature-desc">Add and manage workout programs and class listings offered at the gym.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🏢</div>
        <div class="feature-title">Gym Branch Info</div>
        <div class="feature-desc">View gym details and branch-level information from the database.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">⚠️</div>
        <div class="feature-title">Duplicate Prevention</div>
        <div class="feature-desc">Prevents assigning more than one membership per member with validation checks.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💾</div>
        <div class="feature-title">Real-time DB Updates</div>
        <div class="feature-desc">All CRUD operations commit instantly to MySQL with error handling and success feedback.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🗑️</div>
        <div class="feature-title">Cascaded Deletion</div>
        <div class="feature-desc">Deleting a member auto-removes linked membership records to maintain referential integrity.</div>
      </div>
    </div>
  </section>

  <!-- ── TECH STACK ── -->
  <section id="techstack">
    <div class="section-label">03 — Technology</div>
    <h2>Tech <span class="accent">Stack</span></h2>
    <div class="divider"></div>
    <table class="tech-table">
      <thead>
        <tr>
          <th>Layer</th>
          <th>Technology</th>
          <th>Role</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>UI / Frontend</td>
          <td>Streamlit</td>
          <td>Interactive web interface — forms, tables, sidebar menu</td>
        </tr>
        <tr>
          <td>Backend</td>
          <td>Python 3.x</td>
          <td>Core application logic, query construction, validation</td>
        </tr>
        <tr>
          <td>Database</td>
          <td>MySQL</td>
          <td>Relational data storage — members, memberships, trainers, gyms</td>
        </tr>
        <tr>
          <td>DB Connector</td>
          <td>mysql-connector-python</td>
          <td>Connects Python app to MySQL server</td>
        </tr>
        <tr>
          <td>Data Layer</td>
          <td>pandas</td>
          <td>Converts query results to DataFrames for Streamlit display</td>
        </tr>
      </tbody>
    </table>
  </section>

  <!-- ── DATABASE ── -->
  <section id="database">
    <div class="section-label">04 — Data Model</div>
    <h2>Database <span class="accent">Design</span></h2>
    <div class="divider"></div>

    <p style="margin-bottom:24px;">Five core entities with defined relational constraints power the backend.</p>

    <div class="entity-grid">
      <div class="entity-card">
        <div class="entity-icon">🧍</div>
        <div class="entity-name">Member</div>
        <div class="entity-desc">member_id, name, gender, age, phone_no, address</div>
      </div>
      <div class="entity-card">
        <div class="entity-icon">💳</div>
        <div class="entity-name">Gym_Membership</div>
        <div class="entity-desc">membership_id, member_id (FK), price, start_date, end_date, gym_name</div>
      </div>
      <div class="entity-card">
        <div class="entity-icon">🏢</div>
        <div class="entity-name">Gym</div>
        <div class="entity-desc">gym_id, gym_name, location, capacity</div>
      </div>
      <div class="entity-card">
        <div class="entity-icon">🏋️</div>
        <div class="entity-name">Trainer</div>
        <div class="entity-desc">trainer_id, name, age, phone_no</div>
      </div>
      <div class="entity-card">
        <div class="entity-icon">🧘</div>
        <div class="entity-name">Workout_Class</div>
        <div class="entity-desc">workout_id, workout_name</div>
      </div>
    </div>

    <div class="rel-block">
      <div class="rel-title">Entity Relationships</div>
      <div class="rel-item">
        <span>🧍 Member</span>
        <span style="color:#444">──</span>
        <span class="rel-badge">1 : 1</span>
        <span style="color:#444">──</span>
        <span>💳 Gym_Membership</span>
        <span style="color:var(--muted);font-size:12px;margin-left:auto;">One member, one membership</span>
      </div>
      <div class="rel-item">
        <span>🏢 Gym</span>
        <span style="color:#444">──</span>
        <span class="rel-badge">1 : N</span>
        <span style="color:#444">──</span>
        <span>💳 Gym_Membership</span>
        <span style="color:var(--muted);font-size:12px;margin-left:auto;">One gym, many memberships</span>
      </div>
      <div class="rel-item">
        <span>🏋️ Trainer</span>
        <span style="color:#444">──</span>
        <span class="rel-badge">1 : N</span>
        <span style="color:#444">──</span>
        <span>🧘 Workout_Class</span>
        <span style="color:var(--muted);font-size:12px;margin-left:auto;">One trainer, many classes</span>
      </div>
    </div>
  </section>

  <!-- ── ARCHITECTURE ── -->
  <section id="architecture">
    <div class="section-label">05 — Architecture</div>
    <h2>System <span class="accent">Architecture</span></h2>
    <div class="divider"></div>
    <div class="arch-box">
      <div class="arch-row">
        <div class="arch-node">
          <div class="node-label">Layer 1</div>
          <div class="node-title">Web Browser</div>
          <div class="node-tech">Streamlit UI</div>
        </div>
        <div class="arch-arrow">↓</div>
        <div class="arch-node">
          <div class="node-label">Layer 2</div>
          <div class="node-title">Python Backend</div>
          <div class="node-tech">app.py · Logic · Validation</div>
        </div>
        <div class="arch-arrow">↓</div>
        <div class="arch-node">
          <div class="node-label">Layer 3</div>
          <div class="node-title">MySQL Database</div>
          <div class="node-tech">mysql-connector-python</div>
        </div>
      </div>
      <div style="margin-top:24px; padding-top:24px; border-top:1px solid #1a1a1a;">
        <div style="font-family:var(--mono);font-size:10px;letter-spacing:3px;color:var(--muted);text-transform:uppercase;margin-bottom:14px;">Data Flow</div>
        <div style="font-family:var(--mono);font-size:12px;line-height:2.2;color:#666;">
          User Action (UI)
          <span style="color:#333;padding:0 8px;">→</span>
          <span style="color:var(--accent3)">execute_read_query() / execute_write_query()</span>
          <span style="color:#333;padding:0 8px;">→</span>
          <span style="color:#888">create_connection()</span>
          <span style="color:#333;padding:0 8px;">→</span>
          <span style="color:var(--accent)">MySQL Server</span>
          <span style="color:#333;padding:0 8px;">→</span>
          <span style="color:#888">pd.DataFrame</span>
          <span style="color:#333;padding:0 8px;">→</span>
          <span style="color:var(--accent2)">st.dataframe() / st.success()</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ── SETUP ── -->
  <section id="setup">
    <div class="section-label">06 — Getting Started</div>
    <h2>Setup &amp; <span class="accent">Installation</span></h2>
    <div class="divider"></div>

    <p style="margin-bottom:6px;"><strong>Prerequisites:</strong> Python 3.x · MySQL Server · pip</p>
    <p style="margin-bottom:24px;">Default login credentials: <code style="font-family:var(--mono);font-size:12px;background:#1a1a1a;padding:2px 8px;border-radius:3px;color:var(--accent)">username: dbms</code> &nbsp; <code style="font-family:var(--mono);font-size:12px;background:#1a1a1a;padding:2px 8px;border-radius:3px;color:var(--accent)">password: 1234</code></p>

    <div class="code-block">
      <div class="code-header">
        <div class="code-dots">
          <div class="dot dot-r"></div>
          <div class="dot dot-y"></div>
          <div class="dot dot-g"></div>
        </div>
        <div class="code-lang">bash · setup steps</div>
      </div>
      <div class="code-body">
<span class="cm"># 1️⃣  Clone the repository</span>
<span class="prompt">$</span> <span class="kw">git clone</span> https://github.com/&lt;your-username&gt;/gym-management-system.git
<span class="prompt">$</span> <span class="kw">cd</span> gym-management-system
&nbsp;
<span class="cm"># 2️⃣  Create and activate a virtual environment</span>
<span class="prompt">$</span> <span class="kw">python</span> -m venv venv
<span class="prompt">$</span> <span class="kw">source</span> venv/bin/activate        <span class="cm"># Windows: venv\Scripts\activate</span>
&nbsp;
<span class="cm"># 3️⃣  Install dependencies</span>
<span class="prompt">$</span> <span class="kw">pip install</span> -r requirements.txt
&nbsp;
<span class="cm"># 4️⃣  Configure MySQL credentials inside app.py</span>
host     = <span class="st">'localhost'</span>
user     = <span class="st">'root'</span>
password = <span class="st">'your_password'</span>
database = <span class="st">'suhasvarna'</span>
&nbsp;
<span class="cm"># 5️⃣  Launch the Streamlit app</span>
<span class="prompt">$</span> <span class="kw">streamlit run</span> app.py
      </div>
    </div>

    <div style="margin-top:24px;background:var(--card);border:1px solid var(--border);border-left:3px solid var(--accent2);border-radius:0 6px 6px 0;padding:16px 20px;">
      <div style="font-family:var(--mono);font-size:10px;letter-spacing:3px;color:var(--accent2);text-transform:uppercase;margin-bottom:8px;">requirements.txt</div>
      <div style="font-family:var(--mono);font-size:13px;color:#888;line-height:2;">
        streamlit<br/>
        mysql-connector-python<br/>
        pandas
      </div>
    </div>
  </section>

  <!-- ── TEAM ── -->
  <section id="team">
    <div class="section-label">07 — Contributors</div>
    <h2>The <span class="accent">Team</span></h2>
    <div class="divider"></div>
    <div class="team-grid">
      <div class="team-card">
        <div class="team-avatar">SV</div>
        <div class="team-name">Suhas Varna</div>
        <div class="team-links">
          <a class="team-link" href="https://github.com/Suhas-Varna" target="_blank">GitHub</a>
          <a class="team-link" href="https://www.linkedin.com/in/suhas-varna2003/" target="_blank">LinkedIn</a>
        </div>
      </div>
      <div class="team-card">
        <div class="team-avatar">GK</div>
        <div class="team-name">Seeripi Ganesh Kumar</div>
        <div class="team-links">
          <a class="team-link" href="#">GitHub</a>
          <a class="team-link" href="#">LinkedIn</a>
        </div>
      </div>
      <div class="team-card">
        <div class="team-avatar">VD</div>
        <div class="team-name">Vikas D H</div>
        <div class="team-links">
          <a class="team-link" href="#">GitHub</a>
          <a class="team-link" href="#">LinkedIn</a>
        </div>
      </div>
      <div class="team-card">
        <div class="team-avatar">SJ</div>
        <div class="team-name">Sanjay J</div>
        <div class="team-links">
          <a class="team-link" href="#">GitHub</a>
          <a class="team-link" href="#">LinkedIn</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ── FOOTER ── -->
  <footer>
    <div class="foot-brand">Gym<span>MS</span></div>
    <div class="foot-note">Built with Python · Streamlit · MySQL</div>
  </footer>

</div>
</body>
</html>
