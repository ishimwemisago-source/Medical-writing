Code

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SHO Clinical Note Writing Programme</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0d1f3c;
    --navy-mid: #162d54;
    --teal: #00b4a0;
    --teal-light: #00d4bc;
    --amber: #f5a623;
    --red: #e05252;
    --cream: #f7f4ef;
    --cream-dark: #ede9e1;
    --text: #1a1a2e;
    --muted: #6b7280;
    --white: #ffffff;
    --radius: 12px;
    --shadow: 0 4px 24px rgba(13,31,60,0.10);
    --shadow-lg: 0 8px 40px rgba(13,31,60,0.16);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--text);
    line-height: 1.6;
    min-height: 100vh;
  }

  /* HEADER */
  header {
    background: var(--navy);
    color: var(--white);
    padding: 48px 32px 40px;
    position: relative;
    overflow: hidden;
  }

  header::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 260px; height: 260px;
    background: radial-gradient(circle, rgba(0,180,160,0.18) 0%, transparent 70%);
    border-radius: 50%;
  }

  header::after {
    content: '';
    position: absolute;
    bottom: -80px; left: 10%;
    width: 180px; height: 180px;
    background: radial-gradient(circle, rgba(245,166,35,0.10) 0%, transparent 70%);
    border-radius: 50%;
  }

  .header-badge {
    display: inline-block;
    background: rgba(0,180,160,0.18);
    color: var(--teal-light);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 6px 14px;
    border-radius: 20px;
    border: 1px solid rgba(0,212,188,0.25);
    margin-bottom: 16px;
  }

  header h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(26px, 5vw, 40px);
    font-weight: 400;
    line-height: 1.2;
    margin-bottom: 12px;
    position: relative;
    z-index: 1;
  }

  header h1 em {
    color: var(--teal-light);
    font-style: italic;
  }

  header p {
    color: rgba(255,255,255,0.65);
    font-size: 15px;
    max-width: 560px;
    position: relative;
    z-index: 1;
  }

  .header-meta {
    display: flex;
    gap: 24px;
    margin-top: 24px;
    flex-wrap: wrap;
  }

  .meta-pill {
    display: flex;
    align-items: center;
    gap: 8px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 8px;
    padding: 8px 16px;
    font-size: 13px;
    color: rgba(255,255,255,0.8);
  }

  .meta-pill span.dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--teal);
    display: inline-block;
    flex-shrink: 0;
  }

  /* MAIN */
  main {
    max-width: 900px;
    margin: 0 auto;
    padding: 32px 20px 60px;
  }

  /* PROGRAMME OVERVIEW */
  .overview-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 12px;
    margin-bottom: 36px;
  }

  .overview-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 20px 16px;
    text-align: center;
    box-shadow: var(--shadow);
    border-top: 3px solid transparent;
  }

  .overview-card.teal { border-top-color: var(--teal); }
  .overview-card.amber { border-top-color: var(--amber); }
  .overview-card.navy { border-top-color: var(--navy); }
  .overview-card.red { border-top-color: var(--red); }

  .overview-card .num {
    font-family: 'DM Serif Display', serif;
    font-size: 32px;
    color: var(--navy);
    display: block;
  }

  .overview-card .label {
    font-size: 12px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.8px;
    font-weight: 500;
    margin-top: 4px;
  }

  /* SECTION TITLES */
  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    color: var(--navy);
    margin-bottom: 16px;
    padding-bottom: 8px;
    border-bottom: 2px solid var(--cream-dark);
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-title .icon {
    width: 32px; height: 32px;
    background: var(--navy);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
    flex-shrink: 0;
  }

  /* WEEK CARDS */
  .week-card {
    background: var(--white);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    margin-bottom: 20px;
    overflow: hidden;
    transition: box-shadow 0.2s;
  }

  .week-card:hover { box-shadow: var(--shadow-lg); }

  .week-header {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px 24px;
    cursor: pointer;
    user-select: none;
    position: relative;
  }

  .week-num {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--white);
    background: var(--navy);
    padding: 4px 10px;
    border-radius: 6px;
    white-space: nowrap;
    flex-shrink: 0;
  }

  .week-title {
    font-family: 'DM Serif Display', serif;
    font-size: 18px;
    color: var(--navy);
    flex: 1;
  }

  .week-tag {
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.8px;
    padding: 4px 10px;
    border-radius: 20px;
    flex-shrink: 0;
  }

  .tag-foundation { background: rgba(0,180,160,0.12); color: #007a6e; }
  .tag-clinical { background: rgba(13,31,60,0.10); color: var(--navy); }
  .tag-advanced { background: rgba(245,166,35,0.15); color: #b57c00; }
  .tag-mastery { background: rgba(224,82,82,0.12); color: #b03030; }

  .week-toggle {
    color: var(--muted);
    font-size: 18px;
    transition: transform 0.2s;
    flex-shrink: 0;
  }

  .week-card.open .week-toggle { transform: rotate(180deg); }

  .week-body {
    display: none;
    padding: 0 24px 24px;
    border-top: 1px solid var(--cream-dark);
  }

  .week-card.open .week-body { display: block; }

  .week-goal {
    background: linear-gradient(135deg, rgba(13,31,60,0.04), rgba(0,180,160,0.06));
    border-left: 3px solid var(--teal);
    border-radius: 0 8px 8px 0;
    padding: 12px 16px;
    margin: 16px 0;
    font-size: 14px;
    color: var(--navy);
  }

  .week-goal strong { color: var(--teal); }

  /* TASKS */
  .task-section {
    margin-top: 16px;
  }

  .task-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 1.2px;
    color: var(--muted);
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .task-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--cream-dark);
  }

  .task-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .task-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 14px;
    color: #374151;
    line-height: 1.5;
  }

  .task-item::before {
    content: '';
    width: 18px; height: 18px;
    border: 2px solid var(--cream-dark);
    border-radius: 4px;
    flex-shrink: 0;
    margin-top: 1px;
    background: var(--white);
  }

  /* RESOURCES */
  .resource-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 10px;
    margin-top: 10px;
  }

  .resource-link {
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--cream);
    border: 1px solid var(--cream-dark);
    border-radius: 8px;
    padding: 10px 14px;
    text-decoration: none;
    color: var(--navy);
    font-size: 13px;
    font-weight: 500;
    transition: all 0.15s;
  }

  .resource-link:hover {
    background: var(--navy);
    color: var(--white);
    border-color: var(--navy);
  }

  .resource-link .res-icon {
    width: 28px; height: 28px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 13px;
    flex-shrink: 0;
  }

  .res-free { background: rgba(0,180,160,0.15); }
  .resource-link:hover .res-icon { background: rgba(255,255,255,0.15); }

  .free-badge {
    display: inline-block;
    font-size: 9px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    background: rgba(0,180,160,0.15);
    color: #007a6e;
    padding: 2px 6px;
    border-radius: 4px;
    margin-left: auto;
    flex-shrink: 0;
  }

  .resource-link:hover .free-badge {
    background: rgba(255,255,255,0.2);
    color: var(--white);
  }

  /* SELF AUDIT */
  .audit-box {
    background: var(--navy);
    border-radius: var(--radius);
    padding: 24px;
    color: var(--white);
    margin-top: 36px;
  }

  .audit-box h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 20px;
    margin-bottom: 8px;
    color: var(--teal-light);
  }

  .audit-box p {
    font-size: 14px;
    color: rgba(255,255,255,0.7);
    margin-bottom: 16px;
  }

  .audit-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
  }

  .audit-item {
    background: rgba(255,255,255,0.07);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 8px;
    padding: 12px 14px;
    font-size: 13px;
    color: rgba(255,255,255,0.85);
    display: flex;
    gap: 8px;
    align-items: flex-start;
  }

  .audit-item::before {
    content: '→';
    color: var(--teal);
    flex-shrink: 0;
    font-weight: 600;
  }

  /* TIMELINE BAR */
  .timeline-bar {
    display: flex;
    gap: 4px;
    margin-bottom: 28px;
    align-items: center;
  }

  .tl-seg {
    flex: 1;
    height: 6px;
    border-radius: 3px;
    background: var(--cream-dark);
    position: relative;
    cursor: default;
  }

  .tl-seg.active { background: var(--teal); }
  .tl-seg.amber-bar { background: var(--amber); }
  .tl-seg.red-bar { background: var(--red); }

  .tl-label {
    font-size: 10px;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
    white-space: nowrap;
  }

  footer {
    text-align: center;
    padding: 24px;
    font-size: 12px;
    color: var(--muted);
    border-top: 1px solid var(--cream-dark);
    margin-top: 20px;
  }
</style>
</head>
<body>

<header>
  <div class="header-badge">SHO Development Programme</div>
  <h1>Clinical Note Writing<br><em>From History to Discharge</em></h1>
  <p>An 8-week structured self-study programme using free, internationally recognised resources. Designed for Senior House Officers working in hospital settings.</p>
  <div class="header-meta">
    <div class="meta-pill"><span class="dot"></span> 8 Weeks · ~2 hrs/week</div>
    <div class="meta-pill"><span class="dot"></span> 100% Free Resources</div>
    <div class="meta-pill"><span class="dot"></span> GMC-aligned Standards</div>
    <div class="meta-pill"><span class="dot"></span> Self-paced</div>
  </div>
</header>

<main>

  <!-- OVERVIEW -->
  <div class="overview-grid" style="margin-top: 32px;">
    <div class="overview-card teal">
      <span class="num">8</span>
      <div class="label">Weeks</div>
    </div>
    <div class="overview-card amber">
      <span class="num">5</span>
      <div class="label">Note Types</div>
    </div>
    <div class="overview-card navy">
      <span class="num">12+</span>
      <div class="label">Free Resources</div>
    </div>
    <div class="overview-card red">
      <span class="num">1</span>
      <div class="label">Self-Audit/Week</div>
    </div>
  </div>

  <!-- PROGRESS BAR -->
  <div style="margin-bottom: 8px; font-size: 12px; color: var(--muted); font-family: 'DM Mono', monospace; letter-spacing: 0.5px;">PROGRAMME PHASES</div>
  <div class="timeline-bar">
    <span class="tl-label">Foundation</span>
    <div class="tl-seg active"></div>
    <div class="tl-seg active"></div>
    <span class="tl-label" style="margin: 0 4px;">Clinical Skills</span>
    <div class="tl-seg amber-bar"></div>
    <div class="tl-seg amber-bar"></div>
    <div class="tl-seg amber-bar"></div>
    <span class="tl-label" style="margin: 0 4px;">Advanced</span>
    <div class="tl-seg red-bar"></div>
    <div class="tl-seg red-bar"></div>
    <span class="tl-label">Mastery</span>
    <div class="tl-seg" style="background: var(--navy);"></div>
  </div>

  <h2 class="section-title">
    <span class="icon">📋</span>
    Weekly Programme
  </h2>

  <!-- WEEK 1 -->
  <div class="week-card open">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 01</span>
      <span class="week-title">Foundations — Standards & Principles</span>
      <span class="week-tag tag-foundation">Foundation</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Understand what makes a legally sound, GMC-compliant clinical record and internalise the core principles before touching note types.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Read GMC Good Medical Practice — Section on Records (gmc-uk.org). Note the 5 mandatory elements every entry must contain.</li>
          <li class="task-item">Read GMC guidance on Recording Decisions & Consent (gmc-uk.org/professional-standards). Focus on documenting reasoning, not just actions.</li>
          <li class="task-item">Complete the GMC online learning scenario tool — test yourself on 3 real-world documentation scenarios.</li>
          <li class="task-item">Read the NHS Junior Doctors documentation guide (juniordoctors.sth.nhs.uk) — retrospective note best practice and SOAP structure overview.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Self-Audit Task</div>
        <ul class="task-list">
          <li class="task-item">Pull 3 of your own notes from this week. Check each one against the GMC's 5 mandatory elements. Flag any gaps in a notebook you keep throughout this programme.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.gmc-uk.org/professional-standards" class="resource-link" target="_blank">
            <span class="res-icon res-free">📖</span> GMC Good Medical Practice
            <span class="free-badge">Free</span>
          </a>
          <a href="https://www.gmc-uk.org/professional-standards/learning-materials" class="resource-link" target="_blank">
            <span class="res-icon res-free">🎮</span> GMC Learning Scenarios
            <span class="free-badge">Free</span>
          </a>
          <a href="https://juniordoctors.sth.nhs.uk/daily-activities.html" class="resource-link" target="_blank">
            <span class="res-icon res-free">🏥</span> NHS Junior Doctors Guide
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 2 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 02</span>
      <span class="week-title">History Taking — Documenting the Patient Story</span>
      <span class="week-tag tag-foundation">Foundation</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Write a complete, structured history that captures the patient's voice while meeting clinical and legal standards.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Complete Elevify Medical Documentation Course — Lesson 2 & 3 (elevify.com): SOAP format + documenting chief complaint, HPI, past medical and social history, medication reconciliation.</li>
          <li class="task-item">Review the StatPearls SOAP Notes article (ncbi.nlm.nih.gov/books/NBK482263) — free, peer-reviewed, covers the Subjective component in detail.</li>
          <li class="task-item">Practice writing a Subjective section for 3 patients admitted this week. Aim to capture symptoms in the patient's own words alongside clinical context.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Key Principles to Apply</div>
        <ul class="task-list">
          <li class="task-item">Use direct patient quotes for key symptoms ("crushing chest pain since 2am") — these carry medico-legal weight.</li>
          <li class="task-item">Always document: PC, HPC, PMH, Drug history + allergies, Family history, Social history, Systems review.</li>
          <li class="task-item">Note what the patient denies as well as reports — pertinent negatives matter.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.elevify.com/en-us/courses/health-and-medicine/healthcare/medical-documentation-course-ac63a" class="resource-link" target="_blank">
            <span class="res-icon res-free">💻</span> Elevify Documentation Course
            <span class="free-badge">Free</span>
          </a>
          <a href="https://www.ncbi.nlm.nih.gov/books/NBK482263/" class="resource-link" target="_blank">
            <span class="res-icon res-free">🔬</span> StatPearls: SOAP Notes (NIH)
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 3 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 03</span>
      <span class="week-title">Clinical Findings — Examination & Investigations</span>
      <span class="week-tag tag-clinical">Clinical Skills</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Document examination findings with clinical precision — capturing meaningful positives and negatives without bloat.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Complete Elevify Course — Lesson 4: Focused physical exam documentation, pertinent negatives, standard wording and approved abbreviations.</li>
          <li class="task-item">Read the NHS CARAT principles guide (via heidihealth.com/blog/nhs-letter-template) — Clear, Accurate, Relevant, Appropriate, Timely. Apply these to your Objective section.</li>
          <li class="task-item">Write the Objective section for 5 patients this week. Practice a consistent system-by-system format and record vitals, exam findings, and results reviewed.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Key Principles to Apply</div>
        <ul class="task-list">
          <li class="task-item">Always document who reviewed results and the clinical significance — not just "bloods done."</li>
          <li class="task-item">Avoid copy-paste from previous entries. Each day's findings should reflect today's examination.</li>
          <li class="task-item">Use approved abbreviations only — unapproved ones are a common audit failure point.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.elevify.com/en-us/courses/health-and-medicine/healthcare/medical-documentation-course-ac63a" class="resource-link" target="_blank">
            <span class="res-icon res-free">💻</span> Elevify Course — Lesson 4
            <span class="free-badge">Free</span>
          </a>
          <a href="https://heidihealth.com/blog/nhs-letter-template" class="resource-link" target="_blank">
            <span class="res-icon res-free">📝</span> NHS CARAT Principles
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 4 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 04</span>
      <span class="week-title">Assessment & Plan — Clinical Reasoning on Paper</span>
      <span class="week-tag tag-clinical">Clinical Skills</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Write an Assessment and Plan that makes your clinical reasoning visible, defensible, and useful to the next doctor.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Complete Elevify Course — Lesson 5: Assessment and Plan documentation, including differentials and decision-making transparency.</li>
          <li class="task-item">Read StatPearls SOAP Notes — Assessment section. Practice listing problems in order of clinical priority.</li>
          <li class="task-item">Review GMC guidance on Recording Decisions — note requirements for documenting decisions to take no action (often missed by SHOs).</li>
          <li class="task-item">Write A&P sections for 5 patients. Ensure each plan is time-specific: "repeat U&Es in AM, discuss with consultant at ward round" — not "monitor."</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Key Principles to Apply</div>
        <ul class="task-list">
          <li class="task-item">State your differential diagnoses explicitly when uncertain — this protects you and guides colleagues.</li>
          <li class="task-item">Every plan item should answer: What? When? Who is responsible?</li>
          <li class="task-item">Document senior input explicitly: "Discussed with Dr [Registrar], plan agreed."</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.ncbi.nlm.nih.gov/books/NBK482263/" class="resource-link" target="_blank">
            <span class="res-icon res-free">🔬</span> StatPearls: SOAP Notes
            <span class="free-badge">Free</span>
          </a>
          <a href="https://www.gmc-uk.org/professional-standards/the-professional-standards/decision-making-and-consent/recording-decisions" class="resource-link" target="_blank">
            <span class="res-icon res-free">⚖️</span> GMC: Recording Decisions
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 5 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 05</span>
      <span class="week-title">Daily Progress Notes & Ward Round Documentation</span>
      <span class="week-tag tag-clinical">Clinical Skills</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Write ward round notes that are concise but complete — capturing trajectory, decisions, and plans without copying yesterday's entry.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Re-read NHS Junior Doctors guide on daily review structure — apply I-SOAP (Identification, Subjective, Objective, Assessment, Plan) to every ward round note this week.</li>
          <li class="task-item">Register for NHS e-Learning for Healthcare (e-lfh.org.uk) using your NHS OpenAthens account. Enrol on the Electronic Record Keeping & SNOMED CT programme — covers structured data entry and NHS digital systems.</li>
          <li class="task-item">Audit 5 of your own progress notes. Are they documenting trajectory (better/stable/deteriorating)? Is senior input recorded? Is the plan time-specific?</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Key Principles to Apply</div>
        <ul class="task-list">
          <li class="task-item">Always begin with a one-line summary: "Day 3 of admission for community-acquired pneumonia. Clinically improving."</li>
          <li class="task-item">If documenting retrospectively, note: "Written in retrospect — reviewed at [time]."</li>
          <li class="task-item">Record all active problems — not just the admitting diagnosis.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://juniordoctors.sth.nhs.uk/daily-activities.html" class="resource-link" target="_blank">
            <span class="res-icon res-free">🏥</span> NHS Junior Doctors Guide
            <span class="free-badge">Free</span>
          </a>
          <a href="https://www.e-lfh.org.uk/programmes/" class="resource-link" target="_blank">
            <span class="res-icon res-free">🎓</span> NHS e-LfH Platform
            <span class="free-badge">Free</span>
          </a>
          <a href="https://learninghub.nhs.uk/catalogue/ERK-snomed" class="resource-link" target="_blank">
            <span class="res-icon res-free">💾</span> Electronic Record Keeping (NHS)
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 6 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 06</span>
      <span class="week-title">Referrals — SBAR & Inter-specialty Communication</span>
      <span class="week-tag tag-advanced">Advanced</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Structure verbal and written referrals using SBAR so your communication is clear, safe, and respected by receiving teams.</div>

      <div class="task-section">
        <div class="task-label">Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Read the NHS IMG documentation guide on SBAR (community.trewlink.com) — covers Situation, Background, Assessment, Recommendation with worked examples.</li>
          <li class="task-item">Practice writing a formal referral letter using the NHS clinician letter template. Include: reason for referral, relevant history, examination findings, investigations, current management, and specific question for the receiving team.</li>
          <li class="task-item">Review the Heidi Health NHS letter template (heidihealth.com/blog/nhs-letter-template) for structure guidance on inter-specialty letters — free and UK-specific.</li>
          <li class="task-item">Write SBAR notes for 3 real referrals you make this week. Review them afterwards — did you include all 4 elements?</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">SBAR Quick Reference</div>
        <ul class="task-list">
          <li class="task-item"><strong>S</strong>ituation: Who you are, where you are, why you're calling — in one sentence.</li>
          <li class="task-item"><strong>B</strong>ackground: Brief admission history, key diagnoses, current treatment.</li>
          <li class="task-item"><strong>A</strong>ssessment: Your clinical impression and what you're concerned about.</li>
          <li class="task-item"><strong>R</strong>ecommendation: What you need from the receiving team — be specific.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://community.trewlink.com/articles-hdmgi0x8/post/how-nhs-clinical-notes-are-written-soap-sbar-and-documentation-tips-NAbN7CloNjlZPAE" class="resource-link" target="_blank">
            <span class="res-icon res-free">📡</span> SBAR for NHS Doctors
            <span class="free-badge">Free</span>
          </a>
          <a href="https://heidihealth.com/blog/nhs-letter-template" class="resource-link" target="_blank">
            <span class="res-icon res-free">✉️</span> NHS Referral Letter Template
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 7 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 07</span>
      <span class="week-title">Discharge Summaries & Escalation Notes</span>
      <span class="week-tag tag-advanced">Advanced</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Write discharge summaries that fully equip the GP or receiving team, and escalation notes that are watertight medico-legally.</div>

      <div class="task-section">
        <div class="task-label">Discharge Summary — Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">Complete Elevify Course — Lesson 6 onwards, covering follow-up documentation and discharge planning.</li>
          <li class="task-item">Write a discharge summary for a complex patient this week. Ensure it includes: admitting diagnosis, investigations and results, treatment given, pending results, follow-up plan, and GP actions required.</li>
          <li class="task-item">Have a registrar or consultant review your discharge summary and give you one specific piece of written feedback.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Escalation Notes — Learning Tasks</div>
        <ul class="task-list">
          <li class="task-item">For every deteriorating patient this week, write a dedicated escalation note: time of concern, clinical observations, your assessment, who you escalated to, at what time, what was advised, and what action was taken.</li>
          <li class="task-item">Review GMC Good Medical Practice on duty of candour — essential for cases where escalation is delayed or adverse events occur.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.elevify.com/en-us/courses/health-and-medicine/healthcare/medical-documentation-course-ac63a" class="resource-link" target="_blank">
            <span class="res-icon res-free">💻</span> Elevify Course — Discharge
            <span class="free-badge">Free</span>
          </a>
          <a href="https://www.gmc-uk.org/professional-standards" class="resource-link" target="_blank">
            <span class="res-icon res-free">⚖️</span> GMC Duty of Candour
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- WEEK 8 -->
  <div class="week-card">
    <div class="week-header" onclick="toggleWeek(this)">
      <span class="week-num">Week 08</span>
      <span class="week-title">Full Audit, Reflection & Ongoing Maintenance</span>
      <span class="week-tag tag-mastery">Mastery</span>
      <span class="week-toggle">▾</span>
    </div>
    <div class="week-body">
      <div class="week-goal"><strong>Goal:</strong> Consolidate everything through structured self-audit, peer review, and set up a sustainable habit going forward.</div>

      <div class="task-section">
        <div class="task-label">Full Audit Tasks</div>
        <ul class="task-list">
          <li class="task-item">Pull 10 of your own notes from across the 8 weeks — include at least one of each type: admission, daily progress, referral, discharge summary, and escalation.</li>
          <li class="task-item">Score each note against the GMC's 5 mandatory elements AND the NHS CARAT framework. Record your scores.</li>
          <li class="task-item">Identify your 2 most consistent weaknesses and write a specific action plan for each.</li>
          <li class="task-item">Ask a registrar or consultant to review one full set of notes (admission to discharge) for one patient and give structured feedback.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Ongoing Maintenance (Monthly)</div>
        <ul class="task-list">
          <li class="task-item">Return to e-LfH monthly — enrol in 1 new module relevant to your current rotation.</li>
          <li class="task-item">Audit 3 of your own notes every fortnight — use the same GMC/CARAT checklist.</li>
          <li class="task-item">Use MedAll (medall.co) to find free webinars on clinical documentation — new sessions added regularly.</li>
          <li class="task-item">Consider using your note-writing improvement as a reflection or audit for your ARCP/ePortfolio.</li>
        </ul>
      </div>

      <div class="task-section" style="margin-top: 16px;">
        <div class="task-label">Free Resources</div>
        <div class="resource-grid">
          <a href="https://www.e-lfh.org.uk/programmes/" class="resource-link" target="_blank">
            <span class="res-icon res-free">🎓</span> NHS e-LfH — Browse Catalogue
            <span class="free-badge">Free</span>
          </a>
          <a href="https://medall.co" class="resource-link" target="_blank">
            <span class="res-icon res-free">🌐</span> MedAll — Free Webinars
            <span class="free-badge">Free</span>
          </a>
          <a href="https://foundationprogramme.nhs.uk/curriculum/elearning-for-healthcare/" class="resource-link" target="_blank">
            <span class="res-icon res-free">📚</span> Foundation e-Learning (AoMRC)
            <span class="free-badge">Free</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- SELF AUDIT BOX -->
  <div class="audit-box">
    <h3>Weekly Self-Audit Checklist</h3>
    <p>Apply this to 3 of your own notes every week throughout the programme. Keep a running log in a notebook or your ePortfolio.</p>
    <div class="audit-grid">
      <div class="audit-item">Date, time and signature on every entry</div>
      <div class="audit-item">Clinical findings documented (not just tasks)</div>
      <div class="audit-item">Decision-making reasoning is visible</div>
      <div class="audit-item">Senior input named and documented</div>
      <div class="audit-item">Plan is specific — What, When, Who</div>
      <div class="audit-item">Pending results flagged explicitly</div>
      <div class="audit-item">No unapproved abbreviations used</div>
      <div class="audit-item">Each entry independent — no copy-paste</div>
      <div class="audit-item">Patient capacity/consent noted if relevant</div>
      <div class="audit-item">Legible to a colleague who doesn't know patient</div>
    </div>
  </div>

</main>

<footer>
  All resources linked in this programme are free to access. NHS e-LfH requires an NHS OpenAthens account (register free at openathens.nice.org.uk). GMC resources are publicly available. Programme aligned to GMC Good Medical Practice 2024.
</footer>

<script>
  function toggleWeek(header) {
    const card = header.parentElement;
    card.classList.toggle('open');
  }
</script>

</body>
</html>be 
