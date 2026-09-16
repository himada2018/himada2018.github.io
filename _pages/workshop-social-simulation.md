---
layout: single
title: "Simulating Social Worlds"
excerpt: "A free two-day workshop on social simulations for early career psychologists on 21–22 October 2026."
permalink: /projects/social-simulation/workshop/
author_profile: true
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Spectral:ital,wght@0,400;0,600;0,700;1,400&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap">

<style>
/* ══════════════════════════════════════════════════════════════
   Workshop page styles.
   Every selector is scoped under .ws so nothing leaks into the
   AcademicPages / Minimal Mistakes theme.
   ══════════════════════════════════════════════════════════════ */
.ws {
  --ws-surface:   #FFFFFF;
  --ws-surface-2: #EBEEF2;
  --ws-text:      #1A2433;
  --ws-muted:     #5C6F85;
  --ws-faint:     #8A9BAE;
  --ws-accent:    #1D6B5C;
  --ws-accent-lt: #E4F2EE;
  --ws-warm:      #C27F33;
  --ws-warm-lt:   #FBF0E4;
  --ws-hero:      #0B3228;
  --ws-border:    #D0D9E4;
  --ws-r:         8px;

  font-family: 'DM Sans', system-ui, -apple-system, sans-serif;
  color: var(--ws-text);
  line-height: 1.6;
  font-size: 16px;
}

.ws *, .ws *::before, .ws *::after { box-sizing: border-box; }
.ws p { margin: 0; }
.ws ul { margin: 0; padding: 0; list-style: none; }
.ws a { color: var(--ws-accent); }
.ws :focus-visible { outline: 2px solid var(--ws-accent); outline-offset: 2px; }

/* Theme headings can be aggressive — reset ours explicitly. */
.ws h2, .ws h3 {
  font-family: 'Spectral', Georgia, serif;
  color: var(--ws-text);
  border: 0;
  padding: 0;
  margin: 0;
}

/* ── Back link ─────────────────────────────────────────────── */
.ws-back {
  display: inline-block;
  font-size: 0.83rem;
  font-weight: 500;
  text-decoration: none;
  margin-bottom: 1rem;
}
.ws-back:hover { text-decoration: underline; }

/* ── Hero ──────────────────────────────────────────────────── */
.ws-hero {
  background: var(--ws-hero);
  border-radius: 12px;
  padding: 2.6rem 2rem 2.3rem;
  position: relative;
  overflow: hidden;
  margin-bottom: 1rem;
}
.ws-hero canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  opacity: 0.2;
}
.ws-hero-inner { position: relative; }

.ws-eyebrow {
  display: inline-block;
  border: 1px solid rgba(255,255,255,0.18);
  border-radius: 3px;
  padding: 0.28rem 0.75rem;
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(226,240,235,0.78);
  margin-bottom: 1.3rem;
}
.ws-hero h2.ws-title {
  font-size: clamp(1.85rem, 4.4vw, 2.7rem);
  font-weight: 700;
  line-height: 1.12;
  letter-spacing: -0.015em;
  color: #EDF7F3;
  margin-bottom: 0.6rem;
  text-wrap: balance;
}
.ws-hero p.ws-subtitle {
  font-family: 'Spectral', Georgia, serif;
  font-size: clamp(1rem, 2.1vw, 1.22rem);
  font-style: italic;
  color: rgba(226,240,235,0.7);
  margin-bottom: 1.3rem;
}
.ws-lede {
  font-size: 0.98rem;
  color: rgba(226,240,235,0.74);
  max-width: 54ch;
  line-height: 1.68;
  margin-bottom: 1.8rem;
}
.ws-facts {
  display: flex;
  flex-wrap: wrap;
  gap: 1.1rem 2.3rem;
  border-top: 1px solid rgba(255,255,255,0.14);
  padding-top: 1.3rem;
}
.ws-fact-key {
  font-size: 0.66rem;
  font-weight: 600;
  letter-spacing: 0.11em;
  text-transform: uppercase;
  color: rgba(226,240,235,0.45);
  margin-bottom: 0.2rem;
}
.ws-fact-val { font-size: 0.92rem; color: rgba(226,240,235,0.94); line-height: 1.4; }

/* ── Stat strip ────────────────────────────────────────────── */
.ws-stats {
  display: flex;
  flex-wrap: wrap;
  gap: 1.7rem;
  background: var(--ws-surface);
  border: 1px solid var(--ws-border);
  border-radius: var(--ws-r);
  padding: 1.1rem 1.4rem;
  margin-bottom: 2.6rem;
}
.ws-stat { display: flex; align-items: center; gap: 0.55rem; }
.ws-stat-num {
  font-family: 'Spectral', Georgia, serif;
  font-size: 1.55rem;
  font-weight: 600;
  color: var(--ws-accent);
  line-height: 1;
  font-variant-numeric: tabular-nums;
  white-space: nowrap;
}
.ws-stat-label { font-size: 0.75rem; color: var(--ws-muted); line-height: 1.3; }

/* ── Sections ──────────────────────────────────────────────── */
.ws-section { margin-bottom: 2.8rem; }
.ws-label {
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--ws-accent);
  margin-bottom: 0.55rem;
}
.ws-section h2 {
  font-size: 1.42rem;
  font-weight: 600;
  line-height: 1.25;
  margin-bottom: 0.8rem;
  text-wrap: balance;
}
.ws-prose { line-height: 1.72; max-width: 64ch; }
.ws-prose + .ws-prose { margin-top: 0.85rem; }

/* ── Focus areas ───────────────────────────────────────────── */
/* Always 2 x 2 — never 3 + 1. Collapses to one column only on narrow phones. */
.ws-areas {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.85rem;
  margin-top: 1.25rem;
}
.ws-area {
  background: var(--ws-surface);
  border: 1px solid var(--ws-border);
  border-top: 2px solid var(--ws-accent);
  border-radius: 0 0 var(--ws-r) var(--ws-r);
  padding: 1rem 1.1rem 1.1rem;
}
.ws-area-when {
  font-size: 0.645rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--ws-faint);
  margin-bottom: 0.5rem;
}
.ws-area h3 {
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: 0.38rem;
}
.ws-area p { font-size: 0.83rem; color: var(--ws-muted); line-height: 1.55; }

/* ── Programme ─────────────────────────────────────────────── */
.ws-days {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.95rem;
  margin-top: 1.25rem;
}
.ws-day {
  background: var(--ws-surface);
  border: 1px solid var(--ws-border);
  border-radius: var(--ws-r);
  overflow: hidden;
}
.ws-day-head {
  background: var(--ws-surface-2);
  padding: 0.65rem 0.95rem;
  border-bottom: 1px solid var(--ws-border);
}
.ws-day-num {
  font-family: 'Spectral', Georgia, serif;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--ws-accent);
}
.ws-day-date { font-size: 0.77rem; color: var(--ws-muted); }

.ws-sessions li {
  display: grid;
  grid-template-columns: 80px 1fr;
  gap: 0.6rem;
  padding: 0.58rem 0.95rem;
  border-bottom: 1px solid var(--ws-border);
  font-size: 0.83rem;
  align-items: baseline;
}
.ws-sessions li:last-child { border-bottom: none; }
.ws-stime {
  color: var(--ws-faint);
  font-variant-numeric: tabular-nums;
  font-size: 0.74rem;
  letter-spacing: -0.01em;
  white-space: nowrap;
}
/* Every row reads the same — breaks are not dimmed. */
.ws-stitle { color: var(--ws-text); line-height: 1.42; }

/* ── Eligibility ───────────────────────────────────────────── */
.ws-elig { margin-top: 1.05rem; border-top: 1px solid var(--ws-border); }
.ws-elig li {
  padding: 0.72rem 0 0.72rem 1.05rem;
  border-bottom: 1px solid var(--ws-border);
  border-left: 2px solid var(--ws-accent-lt);
  font-size: 0.9rem;
  line-height: 1.55;
}

/* ── Register ──────────────────────────────────────────────── */
.ws-register {
  background: var(--ws-accent);
  border-radius: 12px;
  padding: 2.1rem 1.9rem;
  margin-bottom: 2.8rem;
}
.ws-register .ws-label { color: rgba(226,240,235,0.62); }
.ws-register h2 { color: #EDF7F3; font-size: 1.5rem; margin-bottom: 0.45rem; }
.ws-register .ws-prose { color: rgba(226,240,235,0.78); margin-bottom: 1.4rem; }
.ws-cta-row { display: flex; flex-wrap: wrap; align-items: center; gap: 1rem; }
.ws-btn {
  background: #FFFFFF;
  color: #0B3228 !important;
  font-size: 0.93rem;
  font-weight: 600;
  padding: 0.72rem 1.65rem;
  border-radius: 6px;
  text-decoration: none !important;
  display: inline-block;
  transition: transform 0.12s ease, box-shadow 0.12s ease;
}
.ws-btn:hover { transform: translateY(-1px); box-shadow: 0 4px 14px rgba(0,0,0,0.18); }
.ws-deadline { font-size: 0.81rem; color: rgba(226,240,235,0.62); }
.ws-deadline strong { color: rgba(226,240,235,0.92); font-weight: 600; }

/* ── Organisers & funder ───────────────────────────────────── */
.ws-organisers {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.8rem;
  margin-top: 1.1rem;
}
.ws-org {
  background: var(--ws-surface);
  border: 1px solid var(--ws-border);
  border-left: 3px solid var(--ws-accent);
  border-radius: 0 var(--ws-r) var(--ws-r) 0;
  padding: 0.9rem 1.1rem;
}
.ws-org-name {
  font-family: 'Spectral', Georgia, serif;
  font-size: 0.98rem;
  font-weight: 600;
  margin-bottom: 0.15rem;
}
.ws-org-role { font-size: 0.78rem; color: var(--ws-muted); line-height: 1.45; }

.ws-funder {
  background: var(--ws-surface);
  border: 1px solid var(--ws-border);
  border-radius: var(--ws-r);
  padding: 1.35rem 1.5rem;
  margin-top: 1.1rem;
  display: flex;
  align-items: center;
  gap: 1.5rem;
}
/* Logo keeps its own aspect ratio and clear space — never stretch or recolour it. */
.ws-funder-logo {
  height: 56px;
  width: auto;
  flex-shrink: 0;
  display: block;
}
@media (max-width: 520px) {
  .ws-funder { flex-direction: column; align-items: flex-start; gap: 1rem; }
}
.ws-funder-text { font-size: 0.8rem; color: var(--ws-muted); line-height: 1.5; }
.ws-funder-text strong {
  display: block;
  font-size: 0.87rem;
  color: var(--ws-text);
  font-weight: 600;
  margin-bottom: 0.12rem;
}

.ws-contact {
  border-top: 1px solid var(--ws-border);
  padding-top: 1.2rem;
  font-size: 0.85rem;
  color: var(--ws-muted);
  line-height: 1.7;
}

/* ── Responsive ────────────────────────────────────────────── */
@media (max-width: 680px) {
  .ws-hero { padding: 1.9rem 1.25rem 1.75rem; }
  .ws-days { grid-template-columns: 1fr; }
  .ws-organisers { grid-template-columns: 1fr; }
  .ws-register { padding: 1.6rem 1.2rem; }
  .ws-stats { gap: 1rem; }
  .ws-sessions li { grid-template-columns: 72px 1fr; }
}
@media (max-width: 460px) {
  .ws-areas { grid-template-columns: 1fr; }
}
@media (prefers-reduced-motion: reduce) {
  .ws-btn { transition: none; }
}
</style>

<div class="ws" markdown="0">

<a class="ws-back" href="/projects/social-simulation/">&larr; Back to the Social Simulation Project</a>

<div class="ws-hero">
  <canvas id="ws-net" aria-hidden="true"></canvas>
  <div class="ws-hero-inner">
    <p class="ws-eyebrow">Free Workshop &middot; Registration Open</p>
    <h2 class="ws-title">Simulating Social Worlds</h2>
    <p class="ws-subtitle">Social Simulations for Psychologists</p>
    <p class="ws-lede">
      Hands-on training in Python and social simulatiosn &mdash; from everyday decision
      problems to the evolution of human sociality. No prior programming experience
      required.
    </p>
    <div class="ws-facts">
      <div>
        <div class="ws-fact-key">Dates</div>
        <div class="ws-fact-val">21&ndash;22 October 2026<br>Wednesday &amp; Thursday</div>
      </div>
      <div>
        <div class="ws-fact-key">Venue</div>
        <div class="ws-fact-val">Stewart House, Royal Holloway, University of London</div>
      </div>
      <div>
        <div class="ws-fact-key">Cost</div>
        <div class="ws-fact-val">Free to attend<br>Registration required</div>
      </div>
    </div>
  </div>
</div>

<div class="ws-stats">
  <div class="ws-stat">
    <span class="ws-stat-num">2</span>
    <span class="ws-stat-label">Full<br>days</span>
  </div>
  <div class="ws-stat">
    <span class="ws-stat-num">8</span>
    <span class="ws-stat-label">Taught<br>sessions</span>
  </div>
  <div class="ws-stat">
    <span class="ws-stat-num">Free</span>
    <span class="ws-stat-label">No registration<br>fee</span>
  </div>
  <div class="ws-stat">
    <span class="ws-stat-num">9 Oct</span>
    <span class="ws-stat-label">Registration<br>closes</span>
  </div>
</div>

<div class="ws-section">
  <p class="ws-label">About the Workshop</p>
  <h2>Bringing simulations methods into  psychological science</h2>
  <p class="ws-prose">
    Social simulations and programming remain absent from most psychology training
    programmes. This constrains what students are able to ask of their data, and narrows
    their prospects across both academic and industry careers. This workshop, funded by
    The British Academy, is a direct response to that gap.
  </p>
  <p class="ws-prose">
    Over two days we move from the ground up: a Python foundation, then simulation as a
    way of reasoning about familiar real-world problems, then its application in
    psychological science, and finally agent-based models of cooperation and the
    evolution of human sociality. Sessions are practical throughout, and all teaching
    materials will be released openly after the event.
  </p>
</div>

<div class="ws-section">
  <p class="ws-label">Four Areas of Focus</p>
  <h2>What the two days cover</h2>
  <div class="ws-areas">
    <div class="ws-area">
      <p class="ws-area-when">Day 1 &middot; Morning</p>
      <h3>Python crash course</h3>
      <p>An optional crash course for complete beginners, followed by the specific Python
         tooling used across the rest of the workshop.</p>
    </div>
    <div class="ws-area">
      <p class="ws-area-when">Day 1 &middot; Afternoon</p>
      <h3>Simulating real-world problems</h3>
      <p>Simulation as a way of thinking, built through classic everyday puzzles &mdash;
         queueing behaviour, the secretary problem, and related decision scenarios.</p>
    </div>
    <div class="ws-area">
      <p class="ws-area-when">Day 2 &middot; Morning</p>
      <h3>Simulation in psychological science</h3>
      <p>How social simulation complements experimental work, and the theoretical
         questions it can address that experiments alone cannot.</p>
    </div>
    <div class="ws-area">
      <p class="ws-area-when">Day 2 &middot; Afternoon</p>
      <h3>Evolution of human sociality</h3>
      <p>Agent-based models of cooperation, reciprocity, and the conditions under which
         human cooperation emerges and stabilises.</p>
    </div>
  </div>
</div>

<div class="ws-section">
  <p class="ws-label">Programme</p>
  <h2>Two days with hands-on workshops and keynote talks</h2>
  <p class="ws-prose">
    The Python crash course on Day 1 is optional
    &mdash; skip it and join us at 11:00 if you already use Python comfortably. Every
    other session forms the core programme, and we ask that you attend these in full.
  </p>
  <div class="ws-days">

    <div class="ws-day">
      <div class="ws-day-head">
        <div class="ws-day-num">Day 1</div>
        <div class="ws-day-date">Wednesday 21 October</div>
      </div>
      <ul class="ws-sessions">
        <li><span class="ws-stime">09:30&ndash;10:00</span><span class="ws-stitle">Registration</span></li>
        <li><span class="ws-stime">10:00&ndash;11:00</span><span class="ws-stitle">Python crash course (TBA)</span></li>
        <li><span class="ws-stime">11:00&ndash;12:00</span><span class="ws-stitle">TBA</span></li>
        <li><span class="ws-stime">12:00&ndash;13:00</span><span class="ws-stitle">Lunch &amp; late registration</span></li>
        <li><span class="ws-stime">13:00&ndash;14:00</span><span class="ws-stitle">Social simulation workshop 1 (Hiro Imada)</span></li>
        <li><span class="ws-stime">14:00&ndash;14:30</span><span class="ws-stitle">Coffee break</span></li>
        <li><span class="ws-stime">14:30&ndash;15:30</span><span class="ws-stitle">Social simulation workshop 2 (Hiro Imada)</span></li>
      </ul>
    </div>

    <div class="ws-day">
      <div class="ws-day-head">
        <div class="ws-day-num">Day 2</div>
        <div class="ws-day-date">Thursday 22 October</div>
      </div>
      <ul class="ws-sessions">
        <li><span class="ws-stime">10:00&ndash;11:00</span><span class="ws-stitle">Using social simulations in psychological science (Hiro Imada)</span></li>
        <li><span class="ws-stime">11:00&ndash;11:30</span><span class="ws-stitle">Coffee break</span></li>
        <li><span class="ws-stime">11:30&ndash;12:30</span><span class="ws-stitle">Agent-based modelling and the evolution of cooperation 1 (Isamu Okada)</span></li>
        <li><span class="ws-stime">12:30&ndash;13:30</span><span class="ws-stitle">Lunch break</span></li>
        <li><span class="ws-stime">13:30&ndash;14:30</span><span class="ws-stitle">Agent-based modelling and the evolution of cooperation 2 (Isamu Okada)</span></li>
        <li><span class="ws-stime">14:30&ndash;15:00</span><span class="ws-stitle">Coffee break</span></li>
        <li><span class="ws-stime">15:00&ndash;16:00</span><span class="ws-stitle">Keynote lecture (TBA)</span></li>
        <li><span class="ws-stime">16:00</span><span class="ws-stitle">Closing</span></li>
      </ul>
    </div>

  </div>
</div>

<div class="ws-section">
  <p class="ws-label">Who Should Attend</p>
  <h2>Designed for early career psychologists</h2>
  <p class="ws-prose">
    This workshop is aimed at early career researchers in psychology and closely related
    behavioural sciences &mdash; PhD students, postdoctoral researchers, and early career
    PIs.
  </p>
  <p class="ws-prose">
    <strong>No prior experience with Python or social simulation is required.</strong>
    The programme is built from first principles, and we particularly welcome those for
    whom computational methods represent a genuinely new methodological direction.
  </p>
  <ul class="ws-elig">
    <li>PhD students in psychology or a closely related behavioural science</li>
    <li>Postdoctoral researchers and research fellows in psychology or related fields</li>
    <li>Early career principal investigators, lecturers, and new group leaders in psychology or related fields</li>
  </ul>
</div>

<div class="ws-register">
  <p class="ws-label">Registration</p>
  <h2>Register your place</h2>
  <p class="ws-prose">
    Attendance is free, but places are limited and registration is required. Since our capacity is limited, please do NOT regiseter if you do not show up. Registration takes about three minutes.
  </p>
  <div class="ws-cta-row">
    <a class="ws-btn" href="https://rhulpsychology.eu.qualtrics.com/jfe/form/SV_0CiKU7ZwD2UewPY">Register now</a>
    <span class="ws-deadline">Registration closes <strong>September 30, 2026</strong></span>
  </div>
</div>

<div class="ws-section">
  <p class="ws-label">Organisers</p>
  <div class="ws-organisers">
    <div class="ws-org">
      <div class="ws-org-name">Hirotaka Imada</div>
      <div class="ws-org-role">Principal Investigator<br>Royal Holloway, University of London</div>
    </div>
    <div class="ws-org">
      <div class="ws-org-name">Isamu Okada</div>
      <div class="ws-org-role">Collaborator<br>Soka University</div>
    </div>
    <div class="ws-org">
      <div class="ws-org-name">Maryam Saeed</div>
      <div class="ws-org-role">Undergradudate Research Assistant<br>Royal Holloway, University of London</div>
    </div>
  </div>
  <div class="ws-funder">
    <img class="ws-funder-logo"
         src="/images/BritishAcademy.jpg"
         alt="The British Academy">
    <div class="ws-funder-text">
      <strong>Funded by The British Academy</strong>
      Part of the project &ldquo;Advancing Theoretical Understanding and Methodological
      Capacity in Psychology Through Social Simulation&rdquo; (2026&ndash;2027).
    </div>
  </div>
</div>

<p class="ws-contact">
  Questions? Contact <a href="mailto:Hirotaka.Imada@rhul.ac.uk">Hirotaka.Imada@rhul.ac.uk</a><br>
  Part of the <a href="/projects/social-simulation/">Social Simulation Project</a>, CIP Lab.
</p>

</div>

<script>
/* Drifting agent network in the hero — a nod to the models taught inside. */
(function () {
  var canvas = document.getElementById('ws-net');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');
  var reduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  var COLOR = '#6DD5B8';
  var N = 26;

  var nodes = [];
  for (var i = 0; i < N; i++) {
    nodes.push({
      x: Math.random(),
      y: Math.random(),
      vx: (Math.random() - 0.5) * (reduced ? 0 : 0.00020),
      vy: (Math.random() - 0.5) * (reduced ? 0 : 0.00020)
    });
  }

  var edges = [];
  for (var a = 0; a < N; a++) {
    var deg = 1 + Math.floor(Math.random() * 3);
    for (var k = 0; k < deg; k++) {
      var b = Math.floor(Math.random() * N);
      if (a !== b) edges.push([a, b]);
    }
  }

  function frame() {
    var w = canvas.offsetWidth, h = canvas.offsetHeight;
    if (canvas.width !== w) canvas.width = w;
    if (canvas.height !== h) canvas.height = h;
    var W = canvas.width, H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var maxDist = W * 0.34;
    ctx.strokeStyle = COLOR;
    ctx.lineWidth = 0.8;
    for (var e = 0; e < edges.length; e++) {
      var p = nodes[edges[e][0]], q = nodes[edges[e][1]];
      var ax = p.x * W, ay = p.y * H, bx = q.x * W, by = q.y * H;
      var d = Math.sqrt((ax - bx) * (ax - bx) + (ay - by) * (ay - by));
      if (d > maxDist) continue;
      ctx.globalAlpha = 0.55 * (1 - d / maxDist);
      ctx.beginPath();
      ctx.moveTo(ax, ay);
      ctx.lineTo(bx, by);
      ctx.stroke();
    }

    ctx.globalAlpha = 1;
    ctx.fillStyle = COLOR;
    for (var n = 0; n < N; n++) {
      var node = nodes[n];
      ctx.beginPath();
      ctx.arc(node.x * W, node.y * H, 2.3, 0, Math.PI * 2);
      ctx.fill();
      node.x += node.vx;
      node.y += node.vy;
      if (node.x < 0 || node.x > 1) node.vx *= -1;
      if (node.y < 0 || node.y > 1) node.vy *= -1;
    }
    if (!reduced) requestAnimationFrame(frame);
  }

  frame();
  window.addEventListener('resize', frame);
})();
</script>