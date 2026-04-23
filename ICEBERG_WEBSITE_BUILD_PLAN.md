# Iceberg AI Solutions — Website Expansion Build Plan
**Version 2.0 · Full-Stack Single-Page Rebuild**  
**Stack: Pure HTML / CSS / Vanilla JS · No framework · GSAP via CDN for new sections**

---

## 0. Executive Summary

The current site is a well-crafted single HTML file (~952 lines) using vanilla JS scroll tracking, Inter + Fraunces + JetBrains Mono fonts, and a custom iceberg-dive animation. The design language is strong and must be fully preserved.

**What changes:**
- Iceberg dive extended from 4 → 8 services
- 7 new content sections added after the iceberg
- Lando Norris-style scroll-driven animations on new sections
- GSAP + ScrollTrigger added via CDN (for new sections only — iceberg stays vanilla)
- Full 3-co-founder team section
- ILMU sovereign callout with depth
- Industries served (6 sectors)
- Problems We Solve (6 pain points)
- Competitor comparison table
- All copy written and ready below

---

## 1. What Must NOT Change

These are locked. Do not modify visuals, structure, or JS logic.

| Element | Status |
|---|---|
| `body` background gradient (navy depth) | LOCKED |
| `.stage` iceberg hero + pinned scroll | LOCKED |
| CSS variables (--navy, --ice, --glacier etc.) | LOCKED |
| Font stack (Inter + Fraunces + JetBrains Mono) | LOCKED |
| Nav layout + Book discovery CTA | LOCKED |
| Section 01 · Malaysian AI Imperative (stats) | LOCKED |
| Section 02 · YTL AI Labs partnership block | LOCKED |
| Section 03 · Engagements / Case Studies | LOCKED |
| Section 04 · Engagement Methodology (4 stages) | LOCKED |
| Section 05 · Why Us / 6 Principles | LOCKED |
| Footer | LOCKED |

---

## 2. Iceberg Dive Extension: 4 → 8 Services

### 2a. Stage Height Change
```css
/* CURRENT */
.stage { height: 520vh; }

/* NEW — double to fit 8 services */
.stage { height: 920vh; }
```

### 2b. Band Positions for 8 Services
The scroll progress `pp` runs from 0 to 1. Services fade in/out within their bands.
Each band: `[fadeIn_start, fadeIn_end]` — the service peaks at midpoint and fades out by end.

```js
// CURRENT (4 services)
const bands = [
  [0.14, 0.32],
  [0.30, 0.50],
  [0.48, 0.68],
  [0.66, 0.92],
];

// NEW (8 services) — evenly distributed
const bands = [
  [0.07, 0.20],   // svc1: AI Voice Receptionist
  [0.18, 0.32],   // svc2: Multi-Channel AI Chatbot
  [0.30, 0.44],   // svc3: AI Outbound Caller
  [0.42, 0.56],   // svc4: Data & Decision Intelligence
  [0.54, 0.68],   // svc5: Enterprise Workflow Automation
  [0.66, 0.80],   // svc6: Interactive AI Personas & Avatars
  [0.78, 0.90],   // svc7: Multimodal Voice + Vision
  [0.88, 1.00],   // svc8: Sovereign Governance Layer
];
```

### 2c. svcs Array — Update the querySelector
```js
// CURRENT
const svcs = [
  document.getElementById('svc1'),
  document.getElementById('svc2'),
  document.getElementById('svc3'),
  document.getElementById('svc4')
];

// NEW
const svcs = [
  document.getElementById('svc1'),
  document.getElementById('svc2'),
  document.getElementById('svc3'),
  document.getElementById('svc4'),
  document.getElementById('svc5'),
  document.getElementById('svc6'),
  document.getElementById('svc7'),
  document.getElementById('svc8'),
];
```

### 2d. Depth HUD — Update marks
```html
<!-- CURRENT marks: Waterline, Receptionist, Chatbot, Outbound, Data -->

<!-- NEW marks: -->
<div class="mark" data-m="0">Waterline</div>
<div class="mark" data-m="1">Voice</div>
<div class="mark" data-m="2">Chatbot</div>
<div class="mark" data-m="3">Outbound</div>
<div class="mark" data-m="4">Data</div>
<div class="mark" data-m="5">Workflow</div>
<div class="mark" data-m="6">Persona</div>
<div class="mark" data-m="7">Vision</div>
<div class="mark" data-m="8">Governance</div>
```

### 2e. marks[0] logic — extend for 8 bands
```js
// CURRENT
marks[0].classList.toggle('active', pp < bands[0][0]);

// NEW — same logic, but also update marks check
bands.forEach((b, i) => {
  const mid = (b[0] + b[1]) / 2;
  const t = smooth(b[0], mid, pp) * (1 - smooth(mid, b[1], pp));
  svcs[i].style.opacity = t;
  svcs[i].style.transform = `translateY(calc(-50% + ${(1 - t) * 16}px))`;
  marks[i + 1].classList.toggle('active', pp >= b[0] && pp <= b[1]);
});
marks[0].classList.toggle('active', pp < bands[0][0]);
```

### 2f. Image pan — extend range for deeper dive
```js
// CURRENT — pans from 25% to 95%
const yPos = 25 + pp * 70;

// NEW — same range is fine, or extend slightly
const yPos = 20 + pp * 75;
```

### 2g. Depth labels — updated for 8 services
| Service | Depth label | Anchor |
|---|---|---|
| AI Voice Receptionist | Depth · 5m · Surface layer | anchor-right |
| Multi-Channel AI Chatbot | Depth · 40m · Mid layer | anchor-left |
| AI Outbound Caller | Depth · 120m · Deeper layer | anchor-right |
| Data & Decision Intelligence | Depth · 240m · Base layer | anchor-left |
| Enterprise Workflow Automation | Depth · 400m · Abyss layer | anchor-right |
| Interactive AI Personas & Avatars | Depth · 600m · Deep layer | anchor-left |
| Multimodal Voice + Vision | Depth · 800m · Hadal layer | anchor-right |
| Sovereign Governance Layer | Depth · 1000m · Foundational layer | anchor-left |

---

## 3. New Service HTML Blocks (svc5–svc8)

Add these immediately after `#svc4` inside `.stage-pin`:

```html
<!-- SVC 5: Enterprise Workflow Automation -->
<div class="svc anchor-right" id="svc5">
  <div class="lead"><span class="ln"></span>Depth · 400m · Abyss layer</div>
  <h3>Enterprise Workflow Automation</h3>
  <p>Multi-agent pipelines that qualify, route, process, and escalate cases end-to-end. Human involvement triggered only at moments of genuine value.</p>
  <div class="stat"><span>Multi-agent orchestration</span><span>CRM + ERP native</span><span>Full audit trail</span></div>
</div>

<!-- SVC 6: Interactive AI Personas & Avatars -->
<div class="svc anchor-left" id="svc6">
  <div class="lead"><span class="ln"></span>Depth · 600m · Deep layer</div>
  <h3>Interactive AI Personas &amp; Avatars</h3>
  <p>Custom AI personas with bespoke voice, personality, and domain knowledge. Deployed on kiosks, hologram displays, and exhibition installations.</p>
  <div class="stat"><span>Custom voice + persona</span><span>Kiosk · Hologram · Web</span><span>BM + EN + dialects</span></div>
</div>

<!-- SVC 7: Multimodal Voice + Vision -->
<div class="svc anchor-right" id="svc7">
  <div class="lead"><span class="ln"></span>Depth · 800m · Hadal layer</div>
  <h3>Multimodal Voice + Vision</h3>
  <p>Process text, voice, and image input within a single conversation thread. Facility check-in by document photo. Claim submission by receipt image. Built on ILMU's native multimodal architecture.</p>
  <div class="stat"><span>Text · Voice · Image</span><span>ILMU multimodal</span><span>Single thread</span></div>
</div>

<!-- SVC 8: Sovereign Governance Layer -->
<div class="svc anchor-left" id="svc8">
  <div class="lead"><span class="ln"></span>Depth · 1000m · Foundational layer</div>
  <h3>Sovereign Governance Layer</h3>
  <p>AIGE seven-principle alignment built into every deployment. Per-decision audit logs. Bias monitoring. Human-in-the-loop checkpoints. Quarterly governance review for your compliance officer.</p>
  <div class="stat"><span>AIGE-aligned</span><span>Per-decision audit log</span><span>Human-in-the-loop</span></div>
</div>
```

---

## 4. Responsive CSS for svc5–svc8

```css
/* Add to the mobile media query @media (max-width:980px) */
#svc5, #svc6, #svc7, #svc8 { left: 6vw; right: 6vw; max-width: none; }
```

---

## 5. New Sections After the Iceberg Dive

After section `<!-- 05 · WHY US / PRINCIPLES -->`, insert these new sections in this order:

```
[existing] 01 · Malaysian AI Imperative
[existing] 02 · YTL AI Labs
[NEW]      02b · ILMU Sovereign Advantage
[existing] 03 · Engagements / Case Studies
[NEW]      03b · Problems We Solve
[NEW]      03c · Industries Served
[existing] 04 · Engagement Methodology
[NEW]      04b · Competitor Comparison
[existing] 05 · Why Us / Principles
[MODIFIED] 06 · The Team (expand to 3 co-founders)
[existing] 07 · Closing CTA
[existing] Footer
```

---

## 6. New Section HTML + Copy

### Section 02b · ILMU Sovereign Advantage

```html
<!-- ============ 02b · ILMU SOVEREIGN ADVANTAGE ============ -->
<section id="ilmu" class="section-ilmu">
  <div class="section-inner-wide">
    <div class="section-lead reveal">
      <div class="num mono">02b · Powered by ILMU</div>
      <h2>Malaysia's AI. Not rented. <span class="emph">Sovereign.</span></h2>
    </div>
    <p class="section-body reveal">
      Most AI vendors in Malaysia route your data through foreign infrastructure — US, Singapore, EU. Their compliance is borrowed. Their Bahasa Melayu is approximate.
      Iceberg operates differently. Through our strategic collaboration with YTL AI Labs, every system we deploy can run on ILMU — Malaysia's first homegrown multimodal LLM, recognised by the Prime Minister and Ministry of Digital as a national capability.
    </p>

    <div class="ilmu-stats reveal">
      <div class="ilmu-stat">
        <div class="ilmu-n">#1</div>
        <div class="ilmu-label">on MalayMMLU benchmark — outperforms all frontier models in Bahasa Melayu</div>
      </div>
      <div class="ilmu-stat">
        <div class="ilmu-n">GPT-4o</div>
        <div class="ilmu-label">performance matched on global benchmarks, hosted entirely within Malaysia</div>
      </div>
      <div class="ilmu-stat">
        <div class="ilmu-n">5</div>
        <div class="ilmu-label">languages fluent — English, Bahasa Melayu, Manglish, Kelantanese, Bahasa Istana</div>
      </div>
    </div>

    <div class="ilmu-grid reveal">
      <div class="ilmu-card">
        <div class="ilmu-card-icon">🏛️</div>
        <div class="ilmu-card-title">Data never leaves Malaysia</div>
        <div class="ilmu-card-body">Hosted on YTL AI Cloud. Your citizen data, your institutional records — on Malaysian soil.</div>
      </div>
      <div class="ilmu-card">
        <div class="ilmu-card-icon">⚖️</div>
        <div class="ilmu-card-title">AIGE-aligned by default</div>
        <div class="ilmu-card-body">Seven-principle National AI Governance and Ethics framework built into every deployment, not retrofitted.</div>
      </div>
      <div class="ilmu-card">
        <div class="ilmu-card-icon">🗣️</div>
        <div class="ilmu-card-title">Bilingual + dialect native</div>
        <div class="ilmu-card-body">No translation approximation. ILMU speaks Malaysian — including Manglish and Kelantanese — natively.</div>
      </div>
      <div class="ilmu-card">
        <div class="ilmu-card-icon">📋</div>
        <div class="ilmu-card-title">Procurement compliant</div>
        <div class="ilmu-card-body">For GLCs, government agencies, and regulated industries — sovereign AI is a procurement requirement, not a preference.</div>
      </div>
    </div>
  </div>
</section>
```

---

### Section 03b · Problems We Solve

```html
<!-- ============ 03b · PROBLEMS WE SOLVE ============ -->
<section id="problems" class="section-problems">
  <div class="section-inner-wide">
    <div class="section-lead reveal">
      <div class="num mono">03b · The operational reality</div>
      <h2>The issue is not effort. It is <span class="emph">infrastructure.</span></h2>
    </div>
    <p class="section-body reveal">
      The volume, timing, and channel diversity of citizen and customer communication today has outpaced what any team can consistently manage without automated infrastructure underneath.
    </p>

    <div class="problems-grid">
      <div class="problem-card reveal">
        <div class="problem-num mono">01</div>
        <h4>The Speed Gap</h4>
        <p>A citizen or customer who enquires is in a decision window that closes in minutes. The average organisation responds in over 42 hours. By then, the moment has passed.</p>
      </div>
      <div class="problem-card reveal">
        <div class="problem-num mono">02</div>
        <h4>After-Hours Demand</h4>
        <p>WhatsApp messages arrive at 11PM. Citizen enquiries come on weekends. Organisations that only respond during staffed hours are unavailable for the majority of hours their stakeholders are active.</p>
      </div>
      <div class="problem-card reveal">
        <div class="problem-num mono">03</div>
        <h4>Leads Never Followed Up</h4>
        <p>Nearly a third of all leads that express interest receive no follow-up. The marketing spend to generate them has been paid. The return is zero.</p>
      </div>
      <div class="problem-card reveal">
        <div class="problem-num mono">04</div>
        <h4>Service That Doesn't Scale</h4>
        <p>The same question asked by 200 customers gets 200 different answers from different staff, at different times, with different quality. Volume grows. Consistency does not.</p>
      </div>
      <div class="problem-card reveal">
        <div class="problem-num mono">05</div>
        <h4>Fragmented Channels</h4>
        <p>WhatsApp, website forms, Instagram DMs, Facebook Messenger, phone, email — each managed by a different person on a different platform. No unified view of the citizen or customer.</p>
      </div>
      <div class="problem-card reveal">
        <div class="problem-num mono">06</div>
        <h4>Data Without Decision</h4>
        <p>Operations generate enormous quantities of data — call logs, enquiry patterns, conversion ratios, service gaps. Most of it is never structured, never reviewed, and never converted into a decision.</p>
      </div>
    </div>
  </div>
</section>
```

---

### Section 03c · Industries Served

```html
<!-- ============ 03c · INDUSTRIES SERVED ============ -->
<section id="industries" class="section-industries">
  <div class="section-inner-wide">
    <div class="section-lead reveal">
      <div class="num mono">03c · Industries served</div>
      <h2>Deployed across six sectors. <span class="emph">Real operations.</span></h2>
    </div>

    <div class="industries-scroll-track" id="industriesTrack">
      <div class="industry-card reveal">
        <div class="industry-num mono">01</div>
        <h4>Government &amp; Public Sector</h4>
        <p>Active engagements with MOHE on AI competition pre-screening; Majlis Bandaraya Johor Bahru (MBJB) on citizen voice agent CRM; federal foundation operational automation.</p>
        <div class="industry-tag mono">MOHE · MBJB · MyKasih</div>
      </div>
      <div class="industry-card reveal">
        <div class="industry-num mono">02</div>
        <h4>Federal Foundations &amp; NGOs</h4>
        <p>MyKasih Foundation and Wassiyah process automation, beneficiary engagement workflows, and structured data acquisition supporting national-scale programmes.</p>
        <div class="industry-tag mono">MyKasih · Wassiyah</div>
      </div>
      <div class="industry-card reveal">
        <div class="industry-num mono">03</div>
        <h4>Healthcare</h4>
        <p>AI Receptionist and Chatbot for appointment booking, patient enquiry handling, and post-visit follow-up. Available 24/7 across WhatsApp and web with full clinical-language calibration.</p>
        <div class="industry-tag mono">24/7 · WhatsApp · Web</div>
      </div>
      <div class="industry-card reveal">
        <div class="industry-num mono">04</div>
        <h4>Financial Services</h4>
        <p>AI Outbound Caller for life insurance and renewal campaigns — hundreds of simultaneous calls without additional headcount. Bilingual qualification with full audit trail for compliance.</p>
        <div class="industry-tag mono">Outbound · Bilingual · Audit</div>
      </div>
      <div class="industry-card reveal">
        <div class="industry-num mono">05</div>
        <h4>Hospitality &amp; Property</h4>
        <p>Bahasa Melayu and Bahasa Indonesia localisation for international AI voice partners serving hotel clients. Property developer deployments for sales qualification and post-handover service.</p>
        <div class="industry-tag mono">BM · BI · Sales qualification</div>
      </div>
      <div class="industry-card reveal">
        <div class="industry-num mono">06</div>
        <h4>Fitness &amp; Wellness</h4>
        <p>MetaXFitness deployment — AI Outbound Caller re-engaging previous clients at subscription end, collecting feedback, and offering renewal without manual follow-up from trainers.</p>
        <div class="industry-tag mono">MetaXFitness · Re-engagement</div>
      </div>
    </div>
  </div>
</section>
```

---

### Section 04b · Competitor Comparison

```html
<!-- ============ 04b · COMPETITOR COMPARISON ============ -->
<section id="compare" class="section-compare">
  <div class="section-inner-wide">
    <div class="section-lead reveal">
      <div class="num mono">04b · How we compare</div>
      <h2>Most vendors are building <span class="emph">on the surface.</span></h2>
    </div>

    <div class="compare-table reveal">
      <div class="compare-header">
        <div class="compare-col-label">Capability</div>
        <div class="compare-col-them">Typical Malaysian AI Vendor</div>
        <div class="compare-col-us">Iceberg AI Solutions</div>
      </div>

      <div class="compare-row">
        <div class="compare-feature">LLM Backbone</div>
        <div class="compare-them">Foreign model (GPT, Gemini, Claude) via API</div>
        <div class="compare-us">ILMU sovereign LLM via YTL AI Labs collaboration</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">Data Hosting</div>
        <div class="compare-them">US, Singapore, or EU data centres</div>
        <div class="compare-us">YTL AI Cloud, Malaysia — data does not leave the country</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">Bahasa Melayu Performance</div>
        <div class="compare-them">Approximate; trained on translated data</div>
        <div class="compare-us">Best-in-class — ILMU is #1 on MalayMMLU; fluent in Manglish, Kelantanese, Bahasa Istana</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">AIGE Compliance</div>
        <div class="compare-them">Not addressed</div>
        <div class="compare-us">AIGE seven-principle alignment built into every deployment by design</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">Engagement Model</div>
        <div class="compare-them">Project handover, then on your own</div>
        <div class="compare-us">Managed end-to-end with monthly KPI review for life of contract</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">Deployment Time</div>
        <div class="compare-them">3 to 6 months typical</div>
        <div class="compare-us">Under 14 days from discovery to live operation for standard configurations</div>
      </div>
      <div class="compare-row">
        <div class="compare-feature">Voice + Chat + Workflow</div>
        <div class="compare-them">Single channel typically</div>
        <div class="compare-us">Unified multi-agent architecture across voice, chat, automation, and data</div>
      </div>
    </div>
  </div>
</section>
```

---

### Section 06 · Team (Replace single-founder with 3 co-founders)

```html
<!-- ============ 06 · THE TEAM (UPDATED) ============ -->
<section id="team">
  <div class="section-lead reveal">
    <div class="num mono">06 · The team</div>
    <h2>A focused founding team. <span class="emph">No intermediaries.</span></h2>
  </div>
  <p class="section-body reveal">Every client engagement is handled directly by the people who built the system. Enterprise business strategy, full-stack technical architecture, and hands-on AI engineering — in one team.</p>

  <div class="team" style="grid-template-columns: repeat(3, 1fr);">

    <div class="person reveal">
      <div class="portrait">
        <div class="ph-bg"></div>
        <div class="ph-ring"></div>
        <div class="ph-shoulders"></div>
        <div class="ph-chip mono">CEO · Business</div>
      </div>
      <div class="name">Firdhaus Othman</div>
      <div class="role mono" style="margin-bottom:8px;">Co-Founder &amp; CEO</div>
      <div class="role">Enterprise engagement, commercial structuring, and government relations. Lead on partnership development including the YTL AI Labs collaboration.</div>
    </div>

    <div class="person reveal">
      <div class="portrait">
        <div class="ph-bg"></div>
        <div class="ph-ring"></div>
        <div class="ph-shoulders"></div>
        <div class="ph-chip mono">COO · Infrastructure</div>
      </div>
      <div class="name">Avvienash Yogaprash</div>
      <div class="role mono" style="margin-bottom:8px;">Co-Founder &amp; COO</div>
      <div class="role">Technology and Operations. Full-stack architecture, infrastructure deployment, and integration engineering across CRM, ERP, telephony, and cloud environments.</div>
    </div>

    <div class="person reveal">
      <div class="portrait">
        <div class="ph-bg"></div>
        <div class="ph-ring"></div>
        <div class="ph-shoulders"></div>
        <div class="ph-chip mono">CTO · AI Engineering</div>
      </div>
      <div class="name">Navientharan</div>
      <div class="role mono" style="margin-bottom:8px;">Co-Founder &amp; CTO</div>
      <div class="role">Lead AI Engineer. Multi-agent system design, ILMU and frontier model integration, voice agent engineering, and AIGE-aligned governance implementation.</div>
    </div>

  </div>
</section>
```

---

## 7. New CSS to Add

Add this block after the existing `/* ---------- footer ---------- */` styles:

```css
/* ---------- SECTION SHARED LAYOUT ---------- */
.section-inner-wide { max-width: 1280px; margin: 0 auto; }
.section-body {
  font-size: clamp(15px, 1.1vw, 17px);
  line-height: 1.65;
  color: var(--muted);
  max-width: 760px;
  margin: 0 0 64px;
}

/* ---------- 02b · ILMU ---------- */
.section-ilmu { padding: 120px 40px; }
.ilmu-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  margin: 64px 0;
  border: 1px solid var(--rule);
}
.ilmu-stat {
  padding: 40px 36px;
  border-right: 1px solid var(--rule);
  background: var(--panel);
}
.ilmu-stat:last-child { border-right: none; }
.ilmu-n {
  font-size: clamp(36px, 3.5vw, 56px);
  font-weight: 300;
  letter-spacing: -.025em;
  color: #fff;
  margin-bottom: 12px;
  font-family: 'Fraunces', Georgia, serif;
  font-style: italic;
}
.ilmu-label {
  font-size: 13.5px;
  color: var(--muted);
  line-height: 1.5;
  max-width: 240px;
}
.ilmu-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2px;
}
.ilmu-card {
  padding: 32px 28px;
  border: 1px solid var(--rule);
  background: var(--panel);
  transition: background .3s;
}
.ilmu-card:hover { background: var(--panel-strong); }
.ilmu-card-icon { font-size: 20px; margin-bottom: 16px; }
.ilmu-card-title {
  font-size: 15px;
  font-weight: 500;
  color: var(--ice);
  margin-bottom: 10px;
  letter-spacing: -.01em;
}
.ilmu-card-body {
  font-size: 13.5px;
  color: var(--muted);
  line-height: 1.55;
}

/* ---------- 03b · PROBLEMS ---------- */
.section-problems { padding: 120px 40px; border-top: 1px solid var(--rule); }
.problems-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  margin-top: 64px;
}
.problem-card {
  padding: 40px 32px;
  border: 1px solid var(--rule);
  background: var(--panel);
  transition: background .3s, transform .3s;
}
.problem-card:hover { background: var(--panel-strong); transform: translateY(-2px); }
.problem-num {
  color: var(--glacier-2);
  margin-bottom: 20px;
  font-size: 11px;
}
.problem-card h4 {
  font-size: 18px;
  font-weight: 500;
  letter-spacing: -.012em;
  color: #fff;
  margin: 0 0 14px;
}
.problem-card p {
  font-size: 13.5px;
  color: var(--muted);
  line-height: 1.6;
  margin: 0;
}

/* ---------- 03c · INDUSTRIES ---------- */
.section-industries { padding: 120px 40px; border-top: 1px solid var(--rule); }
.industries-scroll-track {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  margin-top: 64px;
}
.industry-card {
  padding: 40px 32px;
  border: 1px solid var(--rule);
  background: var(--panel);
  transition: background .3s;
}
.industry-card:hover { background: var(--panel-strong); }
.industry-num {
  color: var(--glacier-2);
  margin-bottom: 20px;
  font-size: 11px;
}
.industry-card h4 {
  font-size: 17px;
  font-weight: 500;
  letter-spacing: -.01em;
  color: #fff;
  margin: 0 0 12px;
}
.industry-card p {
  font-size: 13.5px;
  color: var(--muted);
  line-height: 1.6;
  margin: 0 0 20px;
}
.industry-tag {
  font-size: 10px;
  color: var(--glacier);
  letter-spacing: .12em;
}

/* ---------- 04b · COMPARISON TABLE ---------- */
.section-compare { padding: 120px 40px; border-top: 1px solid var(--rule); }
.compare-table {
  margin-top: 64px;
  border: 1px solid var(--rule);
  border-radius: 4px;
  overflow: hidden;
}
.compare-header, .compare-row {
  display: grid;
  grid-template-columns: 1.2fr 1.8fr 2fr;
}
.compare-header {
  background: var(--panel-strong);
  border-bottom: 1px solid var(--rule);
}
.compare-col-label, .compare-col-them, .compare-col-us {
  padding: 18px 24px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 10.5px;
  letter-spacing: .16em;
  text-transform: uppercase;
  color: var(--muted-2);
}
.compare-col-us { color: var(--glacier); }
.compare-row {
  border-bottom: 1px solid var(--rule);
  transition: background .25s;
}
.compare-row:last-child { border-bottom: none; }
.compare-row:hover { background: var(--panel); }
.compare-feature, .compare-them, .compare-us {
  padding: 22px 24px;
  font-size: 14px;
  line-height: 1.5;
  color: var(--muted);
}
.compare-feature {
  color: var(--ice);
  font-weight: 500;
  border-right: 1px solid var(--rule);
}
.compare-them {
  border-right: 1px solid var(--rule);
  color: rgba(244,246,248,.45);
}
.compare-us {
  color: var(--ice);
  position: relative;
}
.compare-us::before {
  content: "";
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 2px;
  height: 60%;
  background: var(--glacier);
  opacity: .5;
}

/* ---------- RESPONSIVE for new sections ---------- */
@media (max-width: 980px) {
  .ilmu-stats { grid-template-columns: 1fr; }
  .ilmu-grid { grid-template-columns: 1fr 1fr; }
  .problems-grid { grid-template-columns: 1fr; }
  .industries-scroll-track { grid-template-columns: 1fr; }
  .compare-header { display: none; }
  .compare-row { grid-template-columns: 1fr; gap: 0; }
  .compare-feature { border-right: none; border-bottom: 1px solid var(--rule); }
  .compare-them { border-right: none; border-bottom: 1px solid var(--rule); }
  .compare-us::before { display: none; }
  .section-ilmu, .section-problems, .section-industries, .section-compare { padding: 80px 24px; }
}
```

---

## 8. GSAP Animation Layer (Lando-Inspired)

Add GSAP via CDN just before `</body>`. This powers the enhanced scroll animations on new sections without touching the iceberg:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script>
gsap.registerPlugin(ScrollTrigger);

// Staggered reveal for grid cards (problems, industries, ilmu)
gsap.utils.toArray('.problem-card, .industry-card, .ilmu-card').forEach((card, i) => {
  gsap.fromTo(card,
    { opacity: 0, y: 30 },
    {
      opacity: 1,
      y: 0,
      duration: 0.7,
      ease: 'power2.out',
      delay: (i % 3) * 0.12,
      scrollTrigger: {
        trigger: card,
        start: 'top 88%',
        toggleActions: 'play none none none',
      }
    }
  );
});

// Comparison table rows — staggered slide-in
gsap.utils.toArray('.compare-row').forEach((row, i) => {
  gsap.fromTo(row,
    { opacity: 0, x: -20 },
    {
      opacity: 1,
      x: 0,
      duration: 0.5,
      ease: 'power2.out',
      delay: i * 0.08,
      scrollTrigger: {
        trigger: row,
        start: 'top 90%',
        toggleActions: 'play none none none',
      }
    }
  );
});

// ILMU stats — count-up animation
gsap.utils.toArray('.ilmu-stat').forEach((stat, i) => {
  gsap.fromTo(stat,
    { opacity: 0, y: 20 },
    {
      opacity: 1,
      y: 0,
      duration: 0.6,
      ease: 'power2.out',
      delay: i * 0.15,
      scrollTrigger: {
        trigger: stat,
        start: 'top 85%',
        toggleActions: 'play none none none',
      }
    }
  );
});

// Section headings — word split reveal (Lando-style)
gsap.utils.toArray('.section-lead h2').forEach(h2 => {
  gsap.fromTo(h2,
    { opacity: 0, y: 24 },
    {
      opacity: 1,
      y: 0,
      duration: 0.9,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: h2,
        start: 'top 85%',
        toggleActions: 'play none none none',
      }
    }
  );
});
</script>
```

---

## 9. Footer Service Links Update

Update the Services column in the footer:

```html
<div class="foot-col">
  <h5>Services</h5>
  <a href="#services">AI Voice Receptionist</a>
  <a href="#services">Multi-Channel AI Chatbot</a>
  <a href="#services">AI Outbound Caller</a>
  <a href="#services">Data &amp; Intelligence</a>
  <a href="#services">Enterprise Workflow</a>
  <a href="#services">AI Personas &amp; Avatars</a>
  <a href="#services">Multimodal Voice + Vision</a>
  <a href="#services">Sovereign Governance</a>
</div>
```

Update Company column:
```html
<div class="foot-col">
  <h5>Company</h5>
  <a href="#ilmu">ILMU &amp; Sovereignty</a>
  <a href="#work">Engagements</a>
  <a href="#compare">Why Iceberg</a>
  <a href="#industries">Industries</a>
  <a href="#team">Team</a>
  <a href="https://wa.me/601128542591" target="_blank">Careers</a>
</div>
```

---

## 10. Nav Update — Add new links

```html
<div class="nav-center">
  <a href="#services">Services</a>
  <a href="#work">Work</a>
  <a href="#industries">Industries</a>
  <a href="#engage">Engagement</a>
  <a href="#team">Team</a>
</div>
```

---

## 11. Build Execution Order for Claude Code

Follow this exact sequence to avoid breaking the site:

| Step | Action | Risk |
|---|---|---|
| 1 | Change `.stage { height: 920vh }` | Low |
| 2 | Add svc5–svc8 HTML inside `.stage-pin` | Low |
| 3 | Update `bands` array to 8 entries | Medium — test scroll |
| 4 | Update `svcs` array to include svc5–8 | Medium — test scroll |
| 5 | Add 4 more `.mark` entries to HUD | Low |
| 6 | Update `marks[0]` logic in JS | Low |
| 7 | Add responsive CSS for svc5–8 | Low |
| 8 | Insert Section 02b (ILMU) HTML after Section 02 | Low |
| 9 | Insert Section 03b (Problems) HTML after Case Studies | Low |
| 10 | Insert Section 03c (Industries) HTML after Problems | Low |
| 11 | Insert Section 04b (Compare) HTML before Principles | Low |
| 12 | Replace Section 06 Team with 3-founder version | Low |
| 13 | Add all new CSS to style block | Low |
| 14 | Add GSAP CDN + animations before `</body>` | Low |
| 15 | Update footer service links | Low |
| 16 | Update nav links | Low |
| 17 | Full scroll test — all 8 service bands | Critical |

---

## 12. Prompt for Claude Code

Copy this to Claude Code as your starting instruction:

```
I have a single HTML file for icebergaisolutions.com. I want to expand it according to a build plan.

DO NOT change:
- The iceberg scroll mechanic (.stage, .stage-pin, bands system, iceberg image, underwater atmosphere)
- Any existing section content (Malaysian AI stats, YTL section, case studies, engagement methodology, principles)  
- The design system (CSS variables, fonts, color palette)
- The nav visual style

DO:
1. Extend .stage height from 520vh to 920vh
2. Add svc5, svc6, svc7, svc8 HTML blocks inside .stage-pin (after svc4)
3. Update the bands array from 4 to 8 entries with the provided positions
4. Update the svcs array and marks to reference all 8 service elements
5. Add responsive CSS rules for svc5–svc8
6. Insert 4 new sections (ILMU sovereign advantage, Problems We Solve, Industries Served, Competitor Comparison) using the provided HTML + copy
7. Replace the single-founder team section with the 3-co-founder version
8. Add all new CSS to the existing <style> block
9. Add GSAP 3.12.5 + ScrollTrigger via cdnjs before </body>
10. Add the GSAP scroll animations for new sections
11. Update footer service links to include all 8 services
12. Update nav to include Industries link

Here is the build plan with all HTML, CSS, and JS: [paste this document]
```

---

## 13. Notes on Future Enhancements (Post V2)

These are not in this build but recommended for V3:

- **Horizontal scroll strip** (Lando-style) for case study images — use `overflow-x: scroll; scroll-snap-type: x mandatory`
- **Custom cursor** with depth meter that tracks scroll position
- **BotBase product teaser** section — waitlist or coming soon panel
- **Bahasa Malaysia content** — the `BM` lang toggle currently does nothing; hook it to `data-en` / `data-bm` attributes for bilingual toggle
- **Photo uploads** for team portraits — replace placeholder silhouettes when ready
- **Particle canvas** — replace the CSS `<i>` particles with a canvas-based WebGL particle field that responds to mouse movement for the underwater section
