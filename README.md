# Portfolio-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Interactive Resume — Abhishek Kushwaha</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0f0f1a;
    --card-bg: #16162a;
    --border: rgba(255,255,255,0.08);
    --accent-blue: #4d96ff;
    --accent-green: #6bcb77;
    --accent-cyan: #00d4aa;
    --accent-purple: #c77dff;
    --accent-amber: #ff9a3c;
    --text: #e8e8f0;
    --muted: #888899;
    --heading-font: 'Nunito', sans-serif;
    --mono-font: 'Space Mono', monospace;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--heading-font);
    line-height: 1.6;
    min-height: 100vh;
    padding: 40px 20px;
  }

  .resume-container {
    max-width: 800px;
    margin: 0 auto;
  }

  /* ── HEADER ── */
  header {
    text-align: center;
    margin-bottom: 40px;
    position: relative;
    padding-bottom: 30px;
    border-bottom: 1px solid var(--border);
  }
  header h1 {
    font-size: 2.8rem;
    font-weight: 900;
    background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 8px;
  }
  header p.subtitle {
    font-size: 1.2rem;
    color: var(--accent-blue);
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 15px;
  }
  .contact-info {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
    font-family: var(--mono-font);
    font-size: 0.85rem;
    color: var(--muted);
  }
  .contact-info span strong { color: var(--text); }

  /* ── ACCORDION STYLE ── */
  .accordion-section {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 12px;
    margin-bottom: 16px;
    overflow: hidden;
    cursor: pointer;
    transition: box-shadow 0.3s, border-color 0.3s;
  }
  .accordion-section:hover {
    border-color: rgba(255,255,255,0.15);
    box-shadow: 0 4px 20px rgba(0,0,0,0.3);
  }

  .accordion-header {
    padding: 20px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    user-select: none;
  }
  
  .header-title-wrapper {
    display: flex;
    align-items: center;
    gap: 15px;
  }
  
  .section-icon {
    width: 32px;
    height: 32px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--mono-font);
    font-weight: 700;
    font-size: 0.9rem;
  }

  .accordion-header h2 {
    font-size: 1.25rem;
    font-weight: 800;
  }

  .icon-arrow {
    font-size: 1.2rem;
    color: var(--muted);
    transition: transform 0.3s ease;
  }

  /* ── CONTENT HIDDEN BY DEFAULT ── */
  .accordion-content {
    max-height: 0;
    overflow: hidden;
    padding: 0 24px;
    background: rgba(0, 0, 0, 0.15);
    transition: max-height 0.4s ease, padding 0.4s ease;
  }

  /* ── WHEN CLICKED (ACTIVE STATE) ── */
  .accordion-section.active .accordion-content {
    max-height: 1200px; /* Bada height takki content cut na ho */
    padding: 20px 24px;
    border-top: 1px solid var(--border);
  }
  .accordion-section.active .icon-arrow {
    transform: rotate(180deg);
    color: var(--text);
  }

  /* ── CONTENT INTERNAL STYLING ── */
  .info-block { margin-bottom: 20px; }
  .info-block:last-child { margin-bottom: 0; }
  .info-title {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    font-weight: 700;
    font-size: 1.05rem;
    color: var(--text);
    margin-bottom: 4px;
  }
  .info-subtitle {
    font-size: 0.9rem;
    color: var(--muted);
    margin-bottom: 8px;
    font-family: var(--mono-font);
  }
  .info-desc {
    font-size: 0.95rem;
    color: #b0b0c8;
    padding-left: 15px;
  }
  .info-desc li { margin-bottom: 6px; }

  /* Skills tags */
  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .skill-tag {
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    padding: 6px 14px;
    border-radius: 8px;
    font-family: var(--mono-font);
    font-size: 0.85rem;
    color: #d0d0e8;
  }

  /* Section Colors */
  .s-summary .section-icon { background: rgba(77,150,255,0.15); color: var(--accent-blue); }
  .s-skills .section-icon { background: rgba(107,203,119,0.15); color: var(--accent-green); }
  .s-projects .section-icon { background: rgba(0,212,170,0.15); color: var(--accent-cyan); }
  .s-experience .section-icon { background: rgba(199,125,255,0.15); color: var(--accent-purple); }
  .s-education .section-icon { background: rgba(255,154,60,0.15); color: var(--accent-amber); }

  .accordion-section.active.s-summary .accordion-header h2 { color: var(--accent-blue); }
  .accordion-section.active.s-skills .accordion-header h2 { color: var(--accent-green); }
  .accordion-section.active.s-projects .accordion-header h2 { color: var(--accent-cyan); }
  .accordion-section.active.s-experience .accordion-header h2 { color: var(--accent-purple); }
  .accordion-section.active.s-education .accordion-header h2 { color: var(--accent-amber); }

  footer {
    text-align: center;
    margin-top: 50px;
    font-family: var(--mono-font);
    font-size: 0.8rem;
    color: var(--muted);
  }
</style>
</head>
<body>

<div class="resume-container">

  <header>
    <h1>Abhishek Kushwaha</h1>
    <p class="subtitle">Aspiring Data Analyst / Business Analytics</p>
    <div class="contact-info">
      <span>📍 <strong>Hyderabad, India</strong></span>
      <span>📞 <strong>+91 9118109149</strong></span>
      <span>📧 <strong>abhi109149@gmail.com</strong></span>
    </div>
  </header>

  <div class="accordion-section s-summary" onclick="this.classList.toggle('active')">
    <div class="accordion-header">
      <div class="header-title-wrapper">
        <div class="section-icon">01</div>
        <h2>Professional Summary</h2>
      </div>
      <div class="icon-arrow">▼</div>
    </div>
    <div class="accordion-content">
      <p style="color: #b0b0c8; font-size: 0.95rem;">
        Detail-oriented Data Analytics learner with hands-on exposure to SQL, Power BI, Tableau, Excel, and Python. Background in healthcare operations (B.Pharm + hospital experience) sharpened precision and process thinking. Actively building real-world projects in dashboarding, data cleaning, and business reporting - targeting entry-level Data/Business Analyst roles.
      </p>
    </div>
  </div>

  <div class="accordion-section s-skills" onclick="this.classList.toggle('active')">
    <div class="accordion-header">
      <div class="header-title-wrapper">
        <div class="section-icon">02</div>
        <h2>Core Skills</h2>
      </div>
      <div class="icon-arrow">▼</div>
    </div>
    <div class="accordion-content">
      <div class="info-block">
        <div class="info-title" style="margin-bottom: 10px;">Technical Skills</div>
        <div class="skills-grid">
          <span class="skill-tag">SQL</span>
          <span class="skill-tag">Power BI</span>
          <span class="skill-tag">Tableau</span>
          <span class="skill-tag">Microsoft Excel</span>
          <span class="skill-tag">Python (Basic)</span>
          <span class="skill-tag">Data Visualization</span>
          <span class="skill-tag">Data Cleaning</span>
          <span class="skill-tag">Dashboard Reporting</span>
          <span class="skill-tag">Statistics</span>
          <span class="skill-tag">AI/ML Fundamentals</span>
        </div>
      </div>
      
      <div class="info-block" style="margin-top: 20px;">
        <div class="info-title" style="margin-bottom: 10px;">Soft Skills</div>
        <div class="skills-grid">
          <span class="skill-tag">Analytical Thinking</span>
          <span class="skill-tag">Problem Solving</span>
          <span class="skill-tag">Attention to Detail</span>
          <span class="skill-tag">Team Collaboration</span>
          <span class="skill-tag">Communication</span>
        </div>
      </div>
      
      <div class="info-block" style="margin-top: 20px;">
        <div class="info-title" style="margin-bottom: 10px;">Languages</div>
        <div class="skills-grid">
          <span class="skill-tag">Hindi (Native)</span>
          <span class="skill-tag">English (Professional Working Proficiency)</span>
        </div>
      </div>
    </div>
  </div>

  <div class="accordion-section s-projects" onclick="this.classList.toggle('active')">
    <div class="accordion-header">
      <div class="header-title-wrapper">
        <div class="section-icon">03</div>
        <h2>Projects</h2>
      </div>
      <div class="icon-arrow">▼</div>
    </div>
    <div class="accordion-content">
      <div class="info-block">
        <div class="info-title">
          <span>Sales Dashboard Analysis | Power BI</span>
          <span style="color: var(--accent-cyan);">2026</span>
        </div>
        <ul class="info-desc">
          <li>Built interactive sales dashboards tracking revenue trends, customer segments, and growth KPIs.</li>
          <li>Identified key business insights through visual data storytelling and drill-down analysis.</li>
        </ul>
      </div>
      
      <div class="info-block" style="margin-top: 15px;">
        <div class="info-title">
          <span>Excel Data Analysis | Microsoft Excel</span>
          <span style="color: var(--accent-cyan);">2026</span>
        </div>
        <ul class="info-desc">
          <li>Cleaned and analyzed raw business datasets using VLOOKUP, pivot tables, and advanced formulas.</li>
          <li>Generated actionable reports with charts and summaries for simulated business scenarios.</li>
        </ul>
      </div>
      
      <div class="info-block" style="margin-top: 15px;">
        <div class="info-title">
          <span>SQL Practice Projects | MySQL/PostgreSQL</span>
          <span style="color: var(--accent-cyan);">2026</span>
        </div>
        <ul class="info-desc">
          <li>Wrote complex queries using JOINS, GROUP BY, subqueries, and window functions for analytical tasks.</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="accordion-section s-experience" onclick="this.classList.toggle('active')">
    <div class="accordion-header">
      <div class="header-title-wrapper">
        <div class="section-icon">04</div>
        <h2>Work Experience</h2>
      </div>
      <div class="icon-arrow">▼</div>
    </div>
    <div class="accordion-content">
      <div class="info-block">
        <div class="info-title">
          <span>Assistant Pharmacist</span>
          <span style="color: var(--accent-purple);">2025</span>
        </div>
        <div class="info-subtitle">Apollo pharmacy,Delhi</div>
        <ul class="info-desc">
          <li>Managed healthcare documentation and patient records with high accuracy across busy Pharmacy workflows.</li>
          <li>Streamlined record-keeping processes, improving reporting efficiency and reducing manual errors.</li>
          <li>Developed strong attention to detail and cross-functional communication in a high-stakes environment.</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="accordion-section s-education" onclick="this.classList.toggle('active')">
    <div class="accordion-header">
      <div class="header-title-wrapper">
        <div class="section-icon">05</div>
        <h2>Education & Training</h2>
      </div>
      <div class="icon-arrow">▼</div>
    </div>
    <div class="accordion-content">
      <div class="info-block">
        <div class="info-title">
          <span>Data Analytics & Business Analytics</span>
          <span style="color: var(--accent-amber);">Feb 2026 - Present</span>
        </div>
        <div class="info-subtitle">Naresh IT, Hyderabad</div>
        <ul class="info-desc">
          <li>Mastering SQL queries, Excel analytics, Power BI dashboards, and Tableau visualizations for business reporting.</li>
          <li>Exploring AI/ML fundamentals and data-driven decision-making frameworks.</li>
          <li>Practicing end-to-end data workflows: data cleaning → analysis → visualization → insight generation.</li>
        </ul>
      </div>

      <div class="info-block" style="margin-top: 15px;">
        <div class="info-title">
          <span>Bachelor of Pharmacy (B.Pharm)</span>
          <span style="color: var(--accent-amber);">2021 - 2025</span>
        </div>
        <div class="info-subtitle">RGPV University</div>
        <ul class="info-desc">
          <li>CGPA: 7.0 | Built strong analytical and documentation skills applicable to data work.</li>
        </ul>
      </div>
    </div>
  </div>

</div>

<footer>
  Interactive Resume Layout &bull; No JS Script Tag Required
</footer>

</body>
</html>
