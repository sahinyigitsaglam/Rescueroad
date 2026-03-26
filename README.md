<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RescueRoad — UK Vehicle Recovery</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Barlow:ital,wght@0,300;0,400;0,600;0,700;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #f0f4ff;
    --deep: #e8eeff;
    --card: #ffffff;
    --border: #c8d4f0;
    --amber: #2563eb;
    --amber-bright: #3b82f6;
    --amber-dim: #1e3a8a;
    --white: #0f172a;
    --muted: #4b5a7a;
    --danger: #ef4444;
  }

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
background: var(–black);
color: var(–white);
font-family: ‘Barlow’, sans-serif;
font-weight: 300;
overflow-x: hidden;
}

/* ── NAV ── */
nav {
position: fixed;
top: 0; left: 0; right: 0;
z-index: 100;
display: flex;
align-items: center;
justify-content: space-between;
padding: 1.2rem 4rem;
background: rgba(240,244,255,0.92);
backdrop-filter: blur(12px);
border-bottom: 1px solid var(–border);
}

.logo {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.8rem;
letter-spacing: 0.08em;
color: var(–white);
}

.logo span { color: #2563eb; }

nav ul {
list-style: none;
display: flex;
gap: 2.5rem;
}

nav ul a {
color: var(–muted);
text-decoration: none;
font-size: 0.85rem;
font-weight: 600;
letter-spacing: 0.12em;
text-transform: uppercase;
transition: color 0.2s;
}

nav ul a:hover { color: #2563eb; }

.nav-cta {
background: #2563eb;
color: #ffffff !important;
padding: 0.55rem 1.4rem;
border-radius: 2px;
font-weight: 700 !important;
transition: background 0.2s !important;
}

.nav-cta:hover { background: #3b82f6 !important; color: #ffffff !important; }

/* ── HERO ── */
.hero {
min-height: 100vh;
display: grid;
grid-template-columns: 1fr 1fr;
position: relative;
overflow: hidden;
}

.hero-left {
display: flex;
flex-direction: column;
justify-content: center;
padding: 10rem 4rem 6rem;
position: relative;
z-index: 2;
}

.hero-badge {
display: inline-flex;
align-items: center;
gap: 0.5rem;
background: rgba(37,99,235,0.08);
border: 1px solid rgba(37,99,235,0.25);
color: var(–amber);
font-size: 0.75rem;
font-weight: 700;
letter-spacing: 0.15em;
text-transform: uppercase;
padding: 0.4rem 1rem;
border-radius: 2px;
margin-bottom: 2rem;
width: fit-content;
animation: fadeUp 0.6s ease both;
}

.pulse-dot {
width: 7px; height: 7px;
background: #2563eb;
border-radius: 50%;
animation: pulse 1.8s infinite;
}

@keyframes pulse {
0%, 100% { opacity: 1; transform: scale(1); }
50% { opacity: 0.4; transform: scale(0.7); }
}

h1 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(4rem, 7vw, 7.5rem);
line-height: 0.92;
letter-spacing: 0.02em;
animation: fadeUp 0.7s 0.1s ease both;
}

h1 .accent { color: #2563eb; }

h1 .stroke {
-webkit-text-stroke: 1px var(–white);
color: transparent;
}

.hero-sub {
margin-top: 1.8rem;
font-size: 1.05rem;
line-height: 1.7;
color: var(–muted);
max-width: 440px;
animation: fadeUp 0.7s 0.2s ease both;
}

.hero-sub strong { color: var(–white); font-weight: 600; }

.hero-actions {
margin-top: 2.5rem;
display: flex;
gap: 1rem;
flex-wrap: wrap;
animation: fadeUp 0.7s 0.3s ease both;
}

.btn-primary {
background: #2563eb;
color: #ffffff;
font-family: ‘Barlow’, sans-serif;
font-weight: 700;
font-size: 0.9rem;
letter-spacing: 0.08em;
text-transform: uppercase;
padding: 1rem 2.2rem;
border: none;
border-radius: 2px;
cursor: pointer;
text-decoration: none;
display: inline-block;
transition: background 0.2s, transform 0.15s;
}

.btn-primary:hover { background: #3b82f6; transform: translateY(-2px); }

.btn-outline {
background: transparent;
color: var(–white);
font-family: ‘Barlow’, sans-serif;
font-weight: 600;
font-size: 0.9rem;
letter-spacing: 0.08em;
text-transform: uppercase;
padding: 1rem 2.2rem;
border: 1px solid var(–border);
border-radius: 2px;
cursor: pointer;
text-decoration: none;
display: inline-block;
transition: border-color 0.2s, color 0.2s;
}

.btn-outline:hover { border-color: #2563eb; color: #2563eb; }

.hero-stats {
margin-top: 4rem;
display: flex;
gap: 3rem;
animation: fadeUp 0.7s 0.4s ease both;
}

.stat-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 2.8rem;
color: #2563eb;
line-height: 1;
}

.stat-label {
font-size: 0.75rem;
color: var(–muted);
text-transform: uppercase;
letter-spacing: 0.1em;
margin-top: 0.2rem;
}

/* Hero right — truck visual */
.hero-right {
position: relative;
overflow: hidden;
}

.hero-img-overlay {
position: absolute;
inset: 0;
background: linear-gradient(90deg, var(–black) 0%, transparent 40%),
linear-gradient(180deg, transparent 60%, var(–black) 100%);
}

.hero-bg {
width: 100%;
height: 100%;
object-fit: cover;
opacity: 0.55;
filter: saturate(0.3) contrast(1.1);
}

/* Animated road lines */
.road-lines {
position: absolute;
bottom: 0; left: 0; right: 0;
height: 6px;
background: repeating-linear-gradient(90deg, #2563eb 0, #2563eb 40px, transparent 40px, transparent 80px);
z-index: 2;
animation: roadScroll 1.2s linear infinite;
}

@keyframes roadScroll {
from { background-position: 0 0; }
to { background-position: 80px 0; }
}

/* Grid texture overlay on hero */
.hero::before {
content: ‘’;
position: absolute;
inset: 0;
background-image: linear-gradient(#c8d4f0 1px, transparent 1px),
linear-gradient(90deg, #c8d4f0 1px, transparent 1px);
background-size: 60px 60px;
opacity: 0.12;
z-index: 0;
}

@keyframes fadeUp {
from { opacity: 0; transform: translateY(24px); }
to { opacity: 1; transform: translateY(0); }
}

/* ── MARQUEE ── */
.marquee-section {
border-top: 1px solid var(–border);
border-bottom: 1px solid var(–border);
background: var(–deep);
overflow: hidden;
padding: 1rem 0;
}

.marquee-track {
display: flex;
gap: 4rem;
animation: marquee 20s linear infinite;
white-space: nowrap;
width: max-content;
}

.marquee-item {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1rem;
letter-spacing: 0.2em;
color: var(–muted);
text-transform: uppercase;
display: flex;
align-items: center;
gap: 1.5rem;
}

.marquee-item::after {
content: ‘◆’;
color: #2563eb;
font-size: 0.5rem;
}

@keyframes marquee {
from { transform: translateX(0); }
to { transform: translateX(-50%); }
}

/* ── SECTIONS ── */
section { padding: 6rem 4rem; }

.section-label {
font-size: 0.72rem;
font-weight: 700;
letter-spacing: 0.2em;
text-transform: uppercase;
color: #2563eb;
margin-bottom: 1rem;
}

.section-title {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(2.8rem, 4vw, 4.5rem);
line-height: 0.95;
margin-bottom: 1.5rem;
}

.section-body {
color: var(–muted);
font-size: 1rem;
line-height: 1.8;
max-width: 560px;
}

/* ── FEATURES ── */
.features {
background: var(–deep);
}

.features-inner {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 5rem;
align-items: center;
max-width: 1200px;
margin: 0 auto;
}

.feature-cards {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1px;
background: var(–border);
border: 1px solid var(–border);
}

.feature-card {
background: var(–card);
padding: 2rem;
transition: background 0.2s;
}

.feature-card:hover { background: #1c1f25; }

.feature-icon {
font-size: 1.8rem;
margin-bottom: 1rem;
}

.feature-card h3 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.3rem;
letter-spacing: 0.05em;
margin-bottom: 0.5rem;
}

.feature-card p {
font-size: 0.85rem;
color: var(–muted);
line-height: 1.6;
}

/* ── FLEET ── */
.fleet-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1.5rem;
margin-top: 3rem;
max-width: 1200px;
margin-left: auto;
margin-right: auto;
}

.fleet-card {
background: var(–card);
border: 1px solid var(–border);
padding: 2.5rem 2rem;
position: relative;
overflow: hidden;
transition: border-color 0.3s, transform 0.2s;
}

.fleet-card:hover {
border-color: #2563eb;
transform: translateY(-4px);
}

.fleet-card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 3px;
background: #2563eb;
transform: scaleX(0);
transform-origin: left;
transition: transform 0.3s;
}

.fleet-card:hover::before { transform: scaleX(1); }

.fleet-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 4rem;
color: rgba(37,99,235,0.12);
position: absolute;
top: 1rem; right: 1.5rem;
line-height: 1;
}

.fleet-icon { font-size: 2.5rem; margin-bottom: 1rem; }

.fleet-card h3 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.6rem;
letter-spacing: 0.04em;
margin-bottom: 0.8rem;
color: var(–white);
}

.fleet-card p {
font-size: 0.88rem;
color: var(–muted);
line-height: 1.7;
}

.fleet-tag {
display: inline-block;
margin-top: 1.2rem;
font-size: 0.7rem;
font-weight: 700;
letter-spacing: 0.15em;
text-transform: uppercase;
color: #2563eb;
border: 1px solid rgba(37,99,235,0.3);
padding: 0.3rem 0.8rem;
border-radius: 2px;
}

/* ── HOW IT WORKS ── */
.how {
background: var(–deep);
}

.steps {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 0;
margin-top: 3.5rem;
max-width: 1100px;
position: relative;
}

.steps::before {
content: ‘’;
position: absolute;
top: 2.2rem;
left: 2rem;
right: 2rem;
height: 1px;
background: var(–border);
z-index: 0;
}

.step {
padding: 0 1.5rem;
position: relative;
z-index: 1;
}

.step-num {
width: 44px; height: 44px;
background: #2563eb;
color: #ffffff;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.3rem;
display: flex;
align-items: center;
justify-content: center;
border-radius: 2px;
margin-bottom: 1.5rem;
}

.step h4 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.2rem;
letter-spacing: 0.04em;
margin-bottom: 0.5rem;
}

.step p {
font-size: 0.85rem;
color: var(–muted);
line-height: 1.6;
}

/* ── COVERAGE ── */
.coverage {
background: var(–black);
}

.coverage-inner {
max-width: 800px;
margin: 0 auto;
}

.coverage-map {
position: relative;
height: 420px;
background: var(–card);
border: 1px solid var(–border);
display: flex;
align-items: center;
justify-content: center;
overflow: hidden;
}

/* UK map silhouette SVG */
.coverage-map svg {
height: 85%;
opacity: 0.85;
}

.ping {
position: absolute;
width: 12px; height: 12px;
border-radius: 50%;
background: #2563eb;
}

.ping::after {
content: ‘’;
position: absolute;
inset: -6px;
border-radius: 50%;
border: 1px solid #2563eb;
animation: pingRing 2s ease infinite;
}

@keyframes pingRing {
from { transform: scale(0.6); opacity: 1; }
to { transform: scale(2.2); opacity: 0; }
}

.coverage-points {
display: flex;
flex-direction: column;
gap: 1.2rem;
margin-top: 2rem;
}

.cov-point {
display: flex;
align-items: flex-start;
gap: 1rem;
}

.cov-icon {
width: 36px; height: 36px;
background: rgba(37,99,235,0.08);
border: 1px solid rgba(37,99,235,0.25);
border-radius: 2px;
display: flex;
align-items: center;
justify-content: center;
font-size: 1rem;
flex-shrink: 0;
margin-top: 2px;
}

.cov-point h4 {
font-weight: 600;
font-size: 0.95rem;
margin-bottom: 0.2rem;
}

.cov-point p {
font-size: 0.83rem;
color: var(–muted);
line-height: 1.5;
}

/* ── TESTIMONIALS ── */
.testimonials { background: var(–deep); }

.testi-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1.5rem;
margin-top: 3rem;
max-width: 1200px;
}

.testi-card {
background: #ffffff;
border: 1px solid #dbe4f0;
border-top: 4px solid #2563eb;
padding: 2rem;
position: relative;
box-shadow: 0 4px 20px rgba(37,99,235,0.08);
}

.testi-card::before {
content: ‘”’;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 5rem;
color: #2563eb;
opacity: 0.15;
line-height: 1;
position: absolute;
top: 0.5rem; left: 1.2rem;
}

.stars { color: #f59e0b; font-size: 1rem; margin-bottom: 1rem; letter-spacing: 0.1em; }

.testi-text {
font-size: 0.95rem;
line-height: 1.8;
color: #1e293b;
margin-bottom: 1.5rem;
font-weight: 400;
}

.testi-author {
font-weight: 700;
font-size: 0.9rem;
color: #0f172a;
}

.testi-loc {
font-size: 0.78rem;
color: #64748b;
margin-top: 0.2rem;
}

/* ── CTA STRIP ── */
.cta-strip {
background: linear-gradient(135deg, #1e40af 0%, #2563eb 60%, #3b82f6 100%);
color: #ffffff;
padding: 5rem 4rem;
text-align: center;
}

.cta-strip h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 5.5rem);
line-height: 0.95;
margin-bottom: 1.2rem;
}

.cta-strip p {
font-size: 1.05rem;
max-width: 520px;
margin: 0 auto 2.5rem;
opacity: 0.75;
}

.btn-dark {
background: #ffffff;
color: #2563eb;
font-family: ‘Barlow’, sans-serif;
font-weight: 700;
font-size: 0.9rem;
letter-spacing: 0.1em;
text-transform: uppercase;
padding: 1.1rem 2.8rem;
border: none;
border-radius: 2px;
cursor: pointer;
text-decoration: none;
display: inline-block;
transition: opacity 0.2s;
}

.btn-dark:hover { opacity: 0.85; }

.phone-big {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(2rem, 4vw, 4rem);
margin-top: 1.5rem;
display: block;
letter-spacing: 0.05em;
}

/* ── FOOTER ── */
footer {
background: var(–deep);
border-top: 1px solid var(–border);
padding: 3rem 4rem;
display: flex;
justify-content: space-between;
align-items: center;
flex-wrap: wrap;
gap: 1rem;
}

.footer-logo {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.6rem;
letter-spacing: 0.06em;
}

.footer-logo span { color: #2563eb; }

.footer-links {
display: flex;
gap: 2rem;
list-style: none;
}

.footer-links a {
color: var(–muted);
text-decoration: none;
font-size: 0.82rem;
letter-spacing: 0.08em;
text-transform: uppercase;
transition: color 0.2s;
}

.footer-links a:hover { color: #2563eb; }

.footer-copy {
font-size: 0.78rem;
color: var(–muted);
}

/* ── MOBILE ── */
@media (max-width: 900px) {
nav { padding: 1rem 1.5rem; }
nav ul { display: none; }
section { padding: 4rem 1.5rem; }
.hero { grid-template-columns: 1fr; }
.hero-right { display: none; }
.hero-left { padding: 8rem 1.5rem 4rem; }
.features-inner { grid-template-columns: 1fr; }
.fleet-grid { grid-template-columns: 1fr; }
.steps { grid-template-columns: 1fr 1fr; gap: 2rem; }
.steps::before { display: none; }
.coverage-inner { grid-template-columns: 1fr; }
.testi-grid { grid-template-columns: 1fr; }
footer { flex-direction: column; text-align: center; }
.hero-stats { gap: 1.5rem; }
}
</style>

</head>
<body>

<!-- NAV -->

<nav>
  <div class="logo">Rescue<span>Road</span></div>
  <ul>
    <li><a href="#fleet">Fleet</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#coverage">Coverage</a></li>
    <li><a href="tel:07557813511" class="nav-cta">Get Help Now</a></li>
  </ul>
</nav>

<!-- HERO -->

<section class="hero">
  <div class="hero-left">
    <div class="hero-badge">
      <div class="pulse-dot"></div>
      Live — 24/7 UK Coverage
    </div>
    <h1>
      BROKEN<br>
      <span class="stroke">DOWN?</span><br>
      <span class="accent">WE'RE</span><br>
      COMING.
    </h1>
    <p class="hero-sub">
      RescueRoad operates the UK's largest independent recovery network. With <strong>over 700 operators</strong> across the country, we'll reach you wherever you are — fast.
    </p>
    <div class="hero-actions">
      <a href="tel:07557813511" class="btn-primary">Get Recovered Now</a>
      <a href="#how" class="btn-outline">How It Works</a>
    </div>
    <div class="hero-stats">
      <div>
        <div class="stat-num">700+</div>
        <div class="stat-label">Operators Ready</div>
      </div>
      <div>
        <div class="stat-num">24/7</div>
        <div class="stat-label">Always Available</div>
      </div>
      <div>
        <div class="stat-num">UK</div>
        <div class="stat-label">Wide Coverage</div>
      </div>
    </div>
  </div>
  <div class="hero-right">
    <!-- Truck visual using CSS/SVG -->
    <div class="hero-img-overlay"></div>
    <svg viewBox="0 0 800 600" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:100%;position:absolute;top:0;left:0;">
      <defs>
        <radialGradient id="glow" cx="50%" cy="50%" r="50%">
          <stop offset="0%" stop-color="#2563eb" stop-opacity="0.15"/>
          <stop offset="100%" stop-color="#2563eb" stop-opacity="0"/>
        </radialGradient>
      </defs>
      <!-- Road -->
      <rect x="0" y="480" width="800" height="120" fill="#c8d4f0"/>
      <rect x="0" y="478" width="800" height="4" fill="#2563eb" opacity="0.5"/>
      <!-- Road markings -->
      <rect x="80" y="530" width="60" height="6" fill="#2563eb" opacity="0.3" rx="2"/>
      <rect x="220" y="530" width="60" height="6" fill="#2563eb" opacity="0.3" rx="2"/>
      <rect x="360" y="530" width="60" height="6" fill="#2563eb" opacity="0.3" rx="2"/>
      <rect x="500" y="530" width="60" height="6" fill="#2563eb" opacity="0.3" rx="2"/>
      <rect x="640" y="530" width="60" height="6" fill="#2563eb" opacity="0.3" rx="2"/>
      <!-- Glow -->
      <ellipse cx="400" cy="450" rx="300" ry="200" fill="url(#glow)"/>
      <!-- Recovery Truck Body -->
      <rect x="80" y="350" width="420" height="130" fill="#1e40af" rx="4"/>
      <rect x="80" y="350" width="420" height="8" fill="#2563eb" opacity="0.9"/>
      <!-- Cab -->
      <rect x="430" y="300" width="160" height="180" fill="#1d4ed8" rx="4 4 0 0"/>
      <!-- Cab window -->
      <rect x="445" y="315" width="130" height="80" fill="#bfdbfe" rx="3"/>
      <rect x="445" y="315" width="130" height="80" fill="#2563eb" opacity="0.08" rx="3"/>
      <!-- Window shine -->
      <line x1="450" y1="318" x2="470" y2="392" stroke="white" stroke-width="1" opacity="0.3"/>
      <!-- Blue lights -->
      <circle cx="590" cy="380" r="10" fill="#2563eb" opacity="0.9"/>
      <circle cx="590" cy="380" r="18" fill="#2563eb" opacity="0.15"/>
      <circle cx="590" cy="380" r="26" fill="#2563eb" opacity="0.07"/>
      <circle cx="83" cy="450" r="10" fill="#ef4444" opacity="0.8"/>
      <!-- Crane arm -->
      <rect x="200" y="260" width="12" height="100" fill="#1e3a8a" rx="2"/>
      <rect x="200" y="258" width="180" height="10" fill="#1e3a8a" rx="2"/>
      <rect x="370" y="258" width="8" height="60" fill="#1e3a8a" rx="2"/>
      <!-- Hook chain -->
      <line x1="374" y1="318" x2="374" y2="360" stroke="#2563eb" stroke-width="2" opacity="0.6" stroke-dasharray="4,3"/>
      <!-- Wheels -->
      <circle cx="160" cy="480" r="46" fill="#1e3a8a" stroke="#3b82f6" stroke-width="3"/>
      <circle cx="160" cy="480" r="28" fill="#1d4ed8"/>
      <circle cx="160" cy="480" r="10" fill="#93c5fd" opacity="0.8"/>
      <circle cx="340" cy="480" r="46" fill="#1e3a8a" stroke="#3b82f6" stroke-width="3"/>
      <circle cx="340" cy="480" r="28" fill="#1d4ed8"/>
      <circle cx="340" cy="480" r="10" fill="#93c5fd" opacity="0.8"/>
      <circle cx="500" cy="480" r="46" fill="#1e3a8a" stroke="#3b82f6" stroke-width="3"/>
      <circle cx="500" cy="480" r="28" fill="#1d4ed8"/>
      <circle cx="500" cy="480" r="10" fill="#93c5fd" opacity="0.8"/>
      <circle cx="570" cy="480" r="36" fill="#1e3a8a" stroke="#3b82f6" stroke-width="3"/>
      <circle cx="570" cy="480" r="22" fill="#1d4ed8"/>
      <circle cx="570" cy="480" r="8" fill="#93c5fd" opacity="0.8"/>
      <!-- Stranded car -->
      <rect x="620" y="430" width="120" height="50" fill="#e8eeff" rx="3" stroke="#c8d4f0" stroke-width="1"/>
      <rect x="635" y="415" width="90" height="30" fill="#e8eeff" rx="3" stroke="#c8d4f0" stroke-width="1"/>
      <circle cx="645" cy="482" r="16" fill="#c8d4f0" stroke="#a0b4d8" stroke-width="2"/>
      <circle cx="715" cy="482" r="16" fill="#c8d4f0" stroke="#a0b4d8" stroke-width="2"/>
      <!-- Hazard triangle on stranded car -->
      <polygon points="680,405 670,422 690,422" fill="none" stroke="#2563eb" stroke-width="2" opacity="0.8"/>
      <text x="679" y="419" fill="#2563eb" font-size="10" text-anchor="middle" opacity="0.8">!</text>
    </svg>
    <div class="road-lines"></div>
  </div>
</section>

<!-- MARQUEE -->

<div class="marquee-section">
  <div class="marquee-track">
    <span class="marquee-item">700+ Operators Nationwide</span>
    <span class="marquee-item">3.5 Ton Trucks Available</span>
    <span class="marquee-item">Low Loaders Across England</span>
    <span class="marquee-item">24/7 Emergency Recovery</span>
    <span class="marquee-item">Motorway Breakdowns</span>
    <span class="marquee-item">Accident Recovery</span>
    <span class="marquee-item">No Fix No Fee</span>
    <span class="marquee-item">700+ Operators Nationwide</span>
    <span class="marquee-item">3.5 Ton Trucks Available</span>
    <span class="marquee-item">Low Loaders Across England</span>
    <span class="marquee-item">24/7 Emergency Recovery</span>
    <span class="marquee-item">Accident Recovery</span>
    <span class="marquee-item">No Fix No Fee</span>
  </div>
</div>

<!-- FEATURES -->

<section class="features" id="about">
  <div class="features-inner">
    <div>
      <div class="section-label">Why RescueRoad</div>
      <h2 class="section-title">RECOVERY<br>DONE RIGHT</h2>
      <p class="section-body">We've built the UK's most connected vehicle recovery network — 700+ independent operators, professional equipment, and a dispatch system that gets someone to you fast. No call centres. No waiting on hold. Just help.</p>
    </div>
    <div class="feature-cards">
      <div class="feature-card">
        <div class="feature-icon">⚡</div>
        <h3>Rapid Response</h3>
        <p>With operators spread across every region of the UK, we minimise your wait time wherever you are.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🗺️</div>
        <h3>UK-Wide Network</h3>
        <p>From the North East to Cornwall, our 700+ operator network covers every corner of England.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🚛</div>
        <h3>Right Equipment</h3>
        <p>3.5 tonne trucks and heavy-duty low loaders available — we can handle any vehicle, any situation.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🕐</div>
        <h3>Always On</h3>
        <p>Breakdowns don't keep office hours. Our dispatch team and operators are available 24 hours a day, 7 days a week.</p>
      </div>
    </div>
  </div>
</section>

<!-- FLEET -->

<section id="fleet" style="background: var(--black);">
  <div style="max-width:1200px;margin:0 auto;">
    <div class="section-label">Our Fleet</div>
    <h2 class="section-title">THE RIGHT TRUCK<br>FOR EVERY JOB</h2>
    <div class="fleet-grid">
      <div class="fleet-card">
        <div class="fleet-num">01</div>
        <div class="fleet-icon">🚛</div>
        <h3>3.5 Tonne Recovery Truck</h3>
        <p>Our workhorse. Fitted with a tilt-and-slide deck, capable of safely loading and transporting cars, vans, and light commercials anywhere in the UK.</p>
        <div class="fleet-tag">Cars · Vans · Light Commercial</div>
      </div>
      <div class="fleet-card">
        <div class="fleet-num">02</div>
        <div class="fleet-icon">🏗️</div>
        <h3>Low Loader</h3>
        <p>For larger vehicles, specialist machinery, or cars that can't be driven or winched onto a standard deck. The low loader handles it safely and securely.</p>
        <div class="fleet-tag">Large Vehicles · Specialist Equipment</div>
      </div>
      <div class="fleet-card">
        <div class="fleet-num">03</div>
        <div class="fleet-icon">🔧</div>
        <h3>Roadside Assist</h3>
        <p>Sometimes you just need a jump start, tyre change, or fuel top-up. Our operators arrive equipped to fix the simple stuff on the spot.</p>
        <div class="fleet-tag">Jump Start · Tyres · Fuel</div>
      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->

<section class="how" id="how">
  <div style="max-width:1100px;margin:0 auto;">
    <div class="section-label">The Process</div>
    <h2 class="section-title">HELP IN<br>4 STEPS</h2>
    <div class="steps">
      <div class="step">
        <div class="step-num">1</div>
        <h4>Call or Book Online</h4>
        <p>Tell us where you are and what's happened. Takes less than 2 minutes.</p>
      </div>
      <div class="step">
        <div class="step-num">2</div>
        <h4>We Dispatch Fast</h4>
        <p>We match you to the nearest available operator in our 700+ network immediately.</p>
      </div>
      <div class="step">
        <div class="step-num">3</div>
        <h4>Operator En Route</h4>
        <p>Your assigned operator heads straight to you with the right equipment for the job.</p>
      </div>
      <div class="step">
        <div class="step-num">4</div>
        <h4>You're Moving Again</h4>
        <p>Whether it's a roadside fix or a full recovery to your destination, consider it handled.</p>
      </div>
    </div>
  </div>
</section>

<!-- COVERAGE -->

<section class="coverage" id="coverage">
  <div class="coverage-inner">
    <div>
      <div class="section-label">Coverage</div>
      <h2 class="section-title">ACROSS<br>ENGLAND</h2>
      <p class="section-body">It doesn't matter if you're on the M25 at rush hour, a busy city street, or a rural road in the countryside — one of our 700+ operators is never far away.</p>
      <div class="coverage-points">
        <div class="cov-point">
          <div class="cov-icon">🏴󠁧󠁢󠁥󠁮󠁧󠁿</div>
          <div>
            <h4>England — Full Coverage</h4>
            <p>North to South, East to West. Motorways, A-roads, and rural routes covered.</p>
          </div>
        </div>
        <div class="cov-point">
          <div class="cov-icon">🛣️</div>
          <div>
            <h4>Motorways & Major Roads</h4>
            <p>M25, M1, M6, M62 and all major routes — we're ready to reach you fast.</p>
          </div>
        </div>
        <div class="cov-point">
          <div class="cov-icon">🏘️</div>
          <div>
            <h4>Cities & Rural Areas</h4>
            <p>From city centres to country lanes, our network leaves no driver stranded.</p>
          </div>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- TESTIMONIALS -->

<section class="testimonials">
  <div style="max-width:1200px;margin:0 auto;">
    <div class="section-label">Reviews</div>
    <h2 class="section-title">WHAT<br>CUSTOMERS SAY</h2>
    <div class="testi-grid">
      <div class="testi-card">
        <div class="stars">★★★★★</div>
        <p class="testi-text">Broke down on the M6 at 11pm. RescueRoad had someone to me in 40 minutes. The driver was brilliant — had my car loaded and on the way to a garage before I even knew what was happening.</p>
        <div class="testi-author">James T.</div>
        <div class="testi-loc">Manchester</div>
      </div>
      <div class="testi-card">
        <div class="stars">★★★★★</div>
        <p class="testi-text">Broke down on the A1 at 2am with no idea what to do. RescueRoad answered straight away, had a driver to me within the hour and got my car to a garage nearby. Absolute lifesavers.</p>
        <div class="testi-author">Liam K.</div>
        <div class="testi-loc">Leeds</div>
      </div>
      <div class="testi-card">
        <div class="stars">★★★★★</div>
        <p class="testi-text">Used them for a low loader to collect my Transit van from a farm out in Lincolnshire. Couldn't believe how fast they covered the area — turned up on time, handled it perfectly. Will definitely use again.</p>
        <div class="testi-author">Dave R.</div>
        <div class="testi-loc">Sheffield</div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->

<section class="cta-strip" id="contact">
  <h2>STRANDED?<br>WE'LL BE THERE.</h2>
  <p>Don't wait on the side of the road. Call now and we'll dispatch the nearest operator to your location immediately.</p>
  <a href="tel:07557813511" class="btn-dark">📞 Call Now</a>
  <span class="phone-big">07557 813 511</span>
</section>

<!-- FOOTER -->

<footer>
  <div class="footer-logo">Rescue<span>Road</span></div>
  <ul class="footer-links">
    <li><a href="#fleet">Fleet</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#coverage">Coverage</a></li>
    <li><a href="#">Privacy Policy</a></li>
  </ul>
  <div class="footer-copy">© 2025 RescueRoad. All rights reserved.</div>
</footer>

</body>
</html>