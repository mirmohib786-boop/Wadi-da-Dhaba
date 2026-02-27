<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Wadi da Dhaba — by Ubaid | 3B2 Mohali</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400;1,600&family=Josefin+Sans:wght@200;300;400;600&family=Lora:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<style>
:root {
  --chinar: #B8390E;       /* deep chinar red */
  --saffron: #E8750A;      /* kashmiri saffron */
  --mustard: #D4A017;      /* punjabi mustard */
  --forest: #2C4A2E;       /* pine forest green */
  --sage: #4A6741;         /* lighter forest */
  --cream: #FAF3E8;        /* warm cream */
  --parchment: #F0E6CE;    /* parchment */
  --dark: #1A1008;         /* rich dark */
  --walnut: #3D2008;       /* walnut brown */
  --mist: #E8F0E9;         /* misty morning */
}

* { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior:smooth; }

body {
  font-family: 'Lora', serif;
  background: var(--cream);
  color: var(--dark);
  overflow-x: hidden;
  cursor: none;
}

/* Custom cursor */
.cursor {
  width: 12px; height: 12px;
  background: var(--chinar);
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
}
.cursor-ring {
  width: 36px; height: 36px;
  border: 1.5px solid rgba(184,57,14,0.5);
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 9998;
  transform: translate(-50%, -50%);
  transition: transform 0.15s ease, width 0.3s, height 0.3s;
}

/* ===================== NAV ===================== */
nav {
  position: fixed; top:0; left:0; right:0; z-index:500;
  padding: 1.4rem 4rem;
  display: flex; align-items:center; justify-content:space-between;
  transition: all 0.4s;
}
nav.scrolled {
  background: rgba(26,16,8,0.96);
  backdrop-filter: blur(12px);
  padding: 0.9rem 4rem;
  box-shadow: 0 2px 30px rgba(0,0,0,0.3);
}
.nav-logo {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.6rem; font-weight: 700;
  color: var(--cream); text-decoration: none;
  letter-spacing: 0.02em;
}
.nav-logo em { color: var(--saffron); font-style:italic; }

.nav-links { display:flex; gap:2.5rem; list-style:none; }
.nav-links a {
  color: rgba(250,243,232,0.75);
  text-decoration: none;
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.72rem; font-weight:300;
  letter-spacing: 0.2em; text-transform:uppercase;
  transition: color 0.25s;
}
.nav-links a:hover { color: var(--mustard); }

/* ===================== HERO ===================== */
.hero {
  min-height: 100vh;
  background: var(--forest);
  position: relative;
  display: flex; flex-direction:column;
  align-items: center; justify-content:center;
  overflow: hidden;
}

/* Layered Kashmir-Punjab background */
.hero-bg {
  position: absolute; inset:0;
  background:
    radial-gradient(ellipse at 0% 0%, rgba(212,160,23,0.15) 0%, transparent 50%),
    radial-gradient(ellipse at 100% 100%, rgba(184,57,14,0.2) 0%, transparent 50%),
    radial-gradient(ellipse at 50% 50%, rgba(44,74,46,0.5) 0%, transparent 80%);
}

/* Chinar leaf pattern via CSS */
.chinar-pattern {
  position: absolute; inset:0;
  background-image: url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.025'%3E%3Cpolygon points='40,5 52,25 72,25 57,38 63,58 40,46 17,58 23,38 8,25 28,25'/%3E%3C/g%3E%3C/svg%3E");
  opacity: 0.6;
}

/* Diagonal accent stripe */
.hero-stripe {
  position: absolute;
  width: 3px; height: 45%;
  background: linear-gradient(to bottom, transparent, var(--mustard), transparent);
  left: 15%; top: 27%;
  opacity: 0.4;
  transform: rotate(15deg);
}
.hero-stripe:nth-child(2) { left: 85%; top: 20%; transform: rotate(-15deg); opacity: 0.3; }

.hero-inner {
  position: relative; z-index: 2;
  text-align: center;
  padding: 2rem;
}

.hero-eyebrow {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.7rem; font-weight: 300;
  letter-spacing: 0.45em; text-transform: uppercase;
  color: var(--mustard);
  margin-bottom: 1.8rem;
  animation: slideDown 1s ease both;
}

.hero-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(5rem, 14vw, 11rem);
  font-weight: 700;
  color: var(--cream);
  line-height: 0.82;
  letter-spacing: -0.03em;
  animation: fadeIn 1.2s 0.2s ease both;
}

.hero-name-sub {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2.5rem, 6vw, 5rem);
  font-weight: 300;
  font-style: italic;
  color: var(--saffron);
  letter-spacing: 0.1em;
  display: block;
  animation: fadeIn 1.2s 0.35s ease both;
}

.hero-dash {
  width: 80px; height: 2px;
  background: linear-gradient(to right, var(--mustard), var(--chinar));
  margin: 1.8rem auto;
  animation: expand 1s 0.6s ease both;
  transform-origin: center;
}

.hero-tagline {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  font-style: italic; font-weight: 300;
  color: rgba(250,243,232,0.7);
  letter-spacing: 0.05em;
  margin-bottom: 0.5rem;
  animation: fadeIn 1s 0.7s ease both;
}

.hero-location {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.72rem; font-weight: 300;
  letter-spacing: 0.3em; text-transform: uppercase;
  color: rgba(212,160,23,0.75);
  margin-bottom: 3rem;
  animation: fadeIn 1s 0.85s ease both;
}

.hero-btns {
  display: flex; gap: 1.2rem; justify-content:center; flex-wrap:wrap;
  animation: fadeIn 1s 1s ease both;
}

.btn {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.72rem; font-weight: 400;
  letter-spacing: 0.22em; text-transform: uppercase;
  padding: 1rem 2.5rem;
  text-decoration: none;
  border: none; cursor: pointer;
  transition: all 0.3s;
  display: inline-block;
}
.btn-filled { background: var(--chinar); color: #fff; }
.btn-filled:hover { background: var(--saffron); transform: translateY(-2px); box-shadow: 0 10px 30px rgba(184,57,14,0.4); }
.btn-ghost { background: transparent; color: var(--cream); border: 1px solid rgba(250,243,232,0.35); }
.btn-ghost:hover { border-color: var(--mustard); color: var(--mustard); transform: translateY(-2px); }

/* Scroll indicator */
.scroll-hint {
  position: absolute; bottom: 2.5rem; left:50%; transform: translateX(-50%);
  z-index: 2; text-align: center;
  animation: bounce 2s infinite;
}
.scroll-hint span {
  display: block;
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
  color: rgba(250,243,232,0.4);
  margin-bottom: 0.5rem;
}
.scroll-hint div {
  width: 1px; height: 40px;
  background: linear-gradient(to bottom, rgba(212,160,23,0.6), transparent);
  margin: 0 auto;
}

/* ===================== MARQUEE ===================== */
.marquee-wrap {
  background: var(--chinar);
  padding: 0.9rem 0;
  overflow: hidden;
  white-space: nowrap;
}
.marquee-track {
  display: inline-block;
  animation: marquee 25s linear infinite;
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.75rem; font-weight: 300;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: rgba(255,255,255,0.9);
}
.marquee-track span { margin: 0 2rem; color: var(--mustard); }

/* ===================== STORY ===================== */
.story-section {
  padding: 8rem 4rem;
  background: var(--parchment);
  display: grid;
  grid-template-columns: 1fr 1.1fr;
  gap: 6rem;
  align-items: center;
  max-width: 1300px;
  margin: 0 auto;
}

.story-visual-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 200px 200px;
  gap: 10px;
}

.vis-box {
  display: flex; align-items:center; justify-content:center;
  font-size: 3.5rem;
  position: relative; overflow:hidden;
}
.vis-box-1 { background: var(--forest); grid-column: 1 / 2; grid-row: 1 / 3; font-size: 6rem; color: var(--mustard); }
.vis-box-2 { background: var(--chinar); font-size: 3rem; }
.vis-box-3 { background: var(--mustard); font-size: 2rem; flex-direction: column; gap: 0.3rem; }
.vis-box-3 p { font-family: 'Cormorant Garamond',serif; font-size: 1.1rem; color: var(--dark); font-weight:700; letter-spacing:0.05em; }

.story-label {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.68rem; font-weight: 300;
  letter-spacing: 0.35em; text-transform: uppercase;
  color: var(--chinar);
  margin-bottom: 1rem;
}

.story-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2.2rem, 4vw, 3.5rem);
  font-weight: 600; line-height: 1.1;
  margin-bottom: 1.8rem;
  color: var(--dark);
}
.story-title em { font-style:italic; color: var(--sage); }

.story-body {
  font-size: 1.05rem; line-height: 1.9;
  color: #4a3820;
  margin-bottom: 1.2rem;
}

.story-owner {
  display: flex; align-items:center; gap:1rem;
  margin-top: 2rem; padding-top: 1.5rem;
  border-top: 1px solid rgba(44,74,46,0.2);
}
.owner-badge {
  width: 55px; height: 55px;
  background: var(--forest);
  border-radius: 50%;
  display: flex; align-items:center; justify-content:center;
  font-size: 1.6rem;
}
.owner-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.2rem; font-weight:600;
}
.owner-title {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.65rem; letter-spacing:0.2em; text-transform:uppercase;
  color: var(--sage);
}

/* ===================== MENU ===================== */
.menu-section {
  background: var(--dark);
  padding: 7rem 2rem;
  position: relative;
  overflow: hidden;
}

/* Chinar leaves bg */
.menu-section::before {
  content: '';
  position: absolute; inset:0;
  background:
    radial-gradient(ellipse at top left, rgba(44,74,46,0.3) 0%, transparent 50%),
    radial-gradient(ellipse at bottom right, rgba(184,57,14,0.2) 0%, transparent 50%);
}

.menu-inner { position: relative; z-index: 1; max-width: 1300px; margin: 0 auto; }

.menu-header { text-align:center; margin-bottom: 4rem; }
.menu-header .section-label {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.68rem; font-weight:300; letter-spacing: 0.4em; text-transform:uppercase;
  color: var(--mustard); margin-bottom: 1rem;
}
.menu-header h2 {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2.5rem, 5vw, 4rem); font-weight: 600;
  color: var(--cream); line-height:1;
}
.menu-header h2 em { font-style:italic; color: var(--saffron); }

/* Tab nav */
.menu-tabs {
  display: flex; gap: 0.5rem;
  justify-content: center; flex-wrap: wrap;
  margin-bottom: 3rem;
}
.tab-btn {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.68rem; font-weight:300; letter-spacing:0.2em; text-transform:uppercase;
  padding: 0.6rem 1.4rem;
  border: 1px solid rgba(250,243,232,0.15);
  color: rgba(250,243,232,0.55);
  background: transparent;
  cursor: pointer;
  transition: all 0.25s;
}
.tab-btn:hover, .tab-btn.active {
  border-color: var(--saffron);
  color: var(--cream);
  background: rgba(232,117,10,0.12);
}

/* Menu grid */
.menu-pane { display: none; }
.menu-pane.active { display: block; }

.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1px;
  background: rgba(255,255,255,0.05);
}

.menu-item-card {
  background: rgba(26,16,8,0.7);
  padding: 1.4rem 1.6rem;
  display: flex; justify-content:space-between; align-items:baseline;
  border-bottom: 1px solid rgba(255,255,255,0.04);
  transition: background 0.2s;
}
.menu-item-card:hover { background: rgba(44,74,46,0.25); }

.item-info { flex:1; }
.item-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.05rem; font-weight: 600;
  color: var(--cream); margin-bottom: 0.15rem;
}
.item-desc {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.65rem; font-weight:300; letter-spacing:0.05em;
  color: rgba(250,243,232,0.45);
}
.item-price {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1rem; font-weight:600;
  color: var(--saffron);
  margin-left: 1.5rem; white-space: nowrap;
}

/* ===================== SPECIALS ===================== */
.specials-section {
  padding: 8rem 4rem;
  background: var(--mist);
  position: relative;
  overflow: hidden;
}
.specials-section::before {
  content: '';
  position: absolute; top:-100px; right:-100px;
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(212,160,23,0.12) 0%, transparent 70%);
}

.specials-inner { max-width: 1200px; margin: 0 auto; }
.specials-header { margin-bottom: 3.5rem; }

.specials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.special-card {
  background: #fff;
  padding: 0;
  overflow: hidden;
  box-shadow: 0 4px 25px rgba(0,0,0,0.06);
  transition: all 0.35s;
  position: relative;
}
.special-card:hover { transform: translateY(-6px); box-shadow: 0 15px 40px rgba(0,0,0,0.12); }

.special-top {
  height: 130px;
  display: flex; align-items:center; justify-content:center;
  font-size: 3.5rem;
  position: relative;
}
.special-top.c1 { background: linear-gradient(135deg, var(--forest), var(--sage)); }
.special-top.c2 { background: linear-gradient(135deg, var(--chinar), #8B1A1A); }
.special-top.c3 { background: linear-gradient(135deg, var(--walnut), var(--chinar)); }
.special-top.c4 { background: linear-gradient(135deg, var(--mustard), #B8860B); }
.special-top.c5 { background: linear-gradient(135deg, var(--sage), var(--forest)); }
.special-top.c6 { background: linear-gradient(135deg, #8B1A1A, var(--walnut)); }

.special-body { padding: 1.5rem 1.8rem 2rem; }
.special-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.25rem; font-weight:700;
  margin-bottom: 0.5rem;
}
.special-desc {
  font-size: 0.9rem; line-height:1.65; color: #666;
}
.special-price {
  margin-top: 1rem;
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.8rem; font-weight:600; letter-spacing:0.1em;
  color: var(--chinar);
}

/* ===================== ABOUT BAND ===================== */
.about-band {
  background: var(--forest);
  padding: 7rem 2rem;
  text-align:center;
  position: relative; overflow:hidden;
}
.about-band::before {
  content: '';
  position: absolute; inset:0;
  background: radial-gradient(ellipse at center, rgba(212,160,23,0.1) 0%, transparent 60%);
}
.about-band-inner { position:relative; z-index:1; max-width:750px; margin:0 auto; }
.about-band-label {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.65rem; font-weight:300;
  letter-spacing: 0.4em; text-transform:uppercase;
  color: var(--mustard); margin-bottom: 1.5rem;
}
.about-band-quote {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(1.5rem, 3vw, 2.3rem);
  font-style: italic; font-weight:300;
  color: var(--cream); line-height: 1.5;
  margin-bottom: 2rem;
}
.about-band-attr {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.75rem; letter-spacing:0.2em; text-transform:uppercase;
  color: rgba(212,160,23,0.8);
}

/* ===================== CONTACT / VISIT ===================== */
.visit-section {
  padding: 7rem 4rem;
  background: var(--parchment);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: center;
  max-width: 1300px;
  margin: 0 auto;
}

.visit-heading { margin-bottom: 3rem; }
.visit-heading .section-label {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.68rem; font-weight:300;
  letter-spacing:0.35em; text-transform:uppercase;
  color: var(--chinar); margin-bottom: 1rem;
}
.visit-heading h2 {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2rem, 4vw, 3rem); font-weight:600; line-height:1.1;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem 2rem;
  margin-bottom: 2.5rem;
}
.contact-item { }
.contact-label {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.6rem; font-weight:300;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 0.3rem;
}
.contact-value {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.15rem; font-weight:600;
  color: var(--dark);
}
.contact-value a { color: var(--chinar); text-decoration:none; }
.contact-value a:hover { text-decoration: underline; }

/* Map card */
.map-card {
  background: var(--forest);
  height: 100%;
  min-height: 400px;
  display: flex; flex-direction:column;
  align-items:center; justify-content:center;
  position: relative; overflow:hidden;
}
.map-card::before {
  content: '';
  position: absolute; inset:0;
  background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Ccircle cx='30' cy='30' r='20'/%3E%3C/g%3E%3C/svg%3E");
}
.map-card-inner { position:relative; z-index:1; text-align:center; }
.map-pin { font-size: 4rem; margin-bottom: 1rem; }
.map-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2rem; font-weight:700; font-style:italic;
  color: var(--cream); line-height:1;
  margin-bottom: 0.5rem;
}
.map-addr {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.72rem; font-weight:300;
  letter-spacing: 0.2em; text-transform:uppercase;
  color: rgba(212,160,23,0.8);
}

/* ===================== FOOTER ===================== */
footer {
  background: var(--dark);
  padding: 4rem 4rem 2rem;
}
.footer-top {
  display: flex; justify-content:space-between; align-items:flex-start;
  padding-bottom: 3rem;
  border-bottom: 1px solid rgba(255,255,255,0.07);
  margin-bottom: 2rem;
  flex-wrap: wrap; gap: 2rem;
}
.footer-brand-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2.5rem; font-weight:700;
  color: var(--cream); line-height:0.9;
  margin-bottom: 0.5rem;
}
.footer-brand-name em { font-style:italic; color: var(--saffron); }
.footer-brand-sub {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.62rem; font-weight:300; letter-spacing:0.25em; text-transform:uppercase;
  color: rgba(250,243,232,0.4);
}
.footer-nav { list-style:none; display:flex; flex-direction:column; gap:0.6rem; }
.footer-nav a {
  color: rgba(250,243,232,0.5);
  text-decoration:none;
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.72rem; letter-spacing:0.1em; text-transform:uppercase;
  transition: color 0.2s;
}
.footer-nav a:hover { color: var(--mustard); }
.footer-bottom {
  display:flex; justify-content:space-between; align-items:center;
  flex-wrap:wrap; gap:1rem;
}
.footer-copy {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.65rem; letter-spacing:0.1em; text-transform:uppercase;
  color: rgba(250,243,232,0.25);
}

/* ===================== FADE-IN ===================== */
.reveal { opacity:0; transform: translateY(24px); transition: opacity 0.75s ease, transform 0.75s ease; }
.reveal.visible { opacity:1; transform: translateY(0); }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }

/* ===================== ANIMATIONS ===================== */
@keyframes slideDown { from { opacity:0; transform: translateY(-20px); } to { opacity:1; transform: translateY(0); } }
@keyframes fadeIn { from { opacity:0; } to { opacity:1; } }
@keyframes expand { from { transform: scaleX(0); opacity:0; } to { transform: scaleX(1); opacity:1; } }
@keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }
@keyframes bounce { 0%,100% { transform: translateX(-50%) translateY(0); } 50% { transform: translateX(-50%) translateY(8px); } }

/* ===================== RESPONSIVE ===================== */
@media (max-width: 900px) {
  nav { padding: 1rem 1.5rem; }
  nav.scrolled { padding: 0.75rem 1.5rem; }
  .nav-links { display: none; }
  .story-section { grid-template-columns:1fr; gap:3rem; padding: 5rem 2rem; }
  .visit-section { grid-template-columns:1fr; gap:3rem; padding: 5rem 2rem; }
  .specials-grid { grid-template-columns: 1fr 1fr; }
  .specials-section { padding: 5rem 2rem; }
  .menu-grid { grid-template-columns: 1fr; }
  .contact-grid { grid-template-columns: 1fr; }
}
@media (max-width: 600px) {
  .specials-grid { grid-template-columns: 1fr; }
  .story-visual-grid { grid-template-columns: 1fr 1fr; grid-template-rows: 150px 150px; }
  .vis-box-1 { grid-column: 1; grid-row: 1; }
}
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ===== NAV ===== -->
<nav id="navbar">
  <a href="#" class="nav-logo">Wadi <em>da Dhaba</em></a>
  <ul class="nav-links">
    <li><a href="#story">Story</a></li>
    <li><a href="#menu">Menu</a></li>
    <li><a href="#specials">Specialties</a></li>
    <li><a href="#visit">Visit</a></li>
  </ul>
</nav>

<!-- ===== HERO ===== -->
<section class="hero" id="home">
  <div class="hero-bg"></div>
  <div class="chinar-pattern"></div>
  <div class="hero-stripe"></div>
  <div class="hero-stripe" style="left:85%;top:20%;transform:rotate(-15deg);opacity:0.3;"></div>

  <div class="hero-inner">
    <p class="hero-eyebrow">Now Open · 3B2, Mohali · Kashmiri &amp; Punjabi Fusion</p>
    <h1 class="hero-name">
      Wadi
      <em class="hero-name-sub">da Dhaba</em>
    </h1>
    <div class="hero-dash"></div>
    <p class="hero-tagline">"Where the Valley Meets the Fields"</p>
    <p class="hero-location">By Ubaid &nbsp;·&nbsp; 3B2 Mohali &nbsp;·&nbsp; +91 6005341675</p>
    <div class="hero-btns">
      <a href="#menu" class="btn btn-filled">Explore Menu</a>
      <a href="#visit" class="btn btn-ghost">Find Us</a>
    </div>
  </div>

  <div class="scroll-hint">
    <span>Scroll</span>
    <div></div>
  </div>
</section>

<!-- ===== MARQUEE ===== -->
<div class="marquee-wrap">
  <div class="marquee-track">
    Kashmiri Pulao <span>✦</span> Rogan Josh <span>✦</span> Noon Chai <span>✦</span> Butter Chicken <span>✦</span> Tandoori Tikka <span>✦</span> Cold Coffee <span>✦</span> Kashmiri Kahwa <span>✦</span> Mango Shake <span>✦</span> Chapli Kabab <span>✦</span> Dal Makhani <span>✦</span> Shawarma <span>✦</span> Desi Burger <span>✦</span> Pink Tea <span>✦</span> Fresh Juices <span>✦</span>
    Kashmiri Pulao <span>✦</span> Rogan Josh <span>✦</span> Noon Chai <span>✦</span> Butter Chicken <span>✦</span> Tandoori Tikka <span>✦</span> Cold Coffee <span>✦</span> Kashmiri Kahwa <span>✦</span> Mango Shake <span>✦</span> Chapli Kabab <span>✦</span> Dal Makhani <span>✦</span> Shawarma <span>✦</span> Desi Burger <span>✦</span> Pink Tea <span>✦</span> Fresh Juices <span>✦</span>
  </div>
</div>

<!-- ===== STORY ===== -->
<div style="background:var(--parchment);">
<div class="story-section" id="story">
  <div class="story-visual-grid reveal">
    <div class="vis-box vis-box-1">🏔️</div>
    <div class="vis-box vis-box-2">🌾</div>
    <div class="vis-box vis-box-3">
      <span>☕</span>
      <p>Est. 2026</p>
    </div>
  </div>
  <div>
    <p class="story-label reveal">Our Story</p>
    <h2 class="story-title reveal reveal-delay-1">Two Cuisines,<br><em>One Soulful Table</em></h2>
    <p class="story-body reveal reveal-delay-2">
      Wadi da Dhaba was born where two great food cultures embrace — the aromatic, slow-cooked richness of Kashmiri mountain kitchens, and the bold, open-hearted flavours of the Punjabi fields. Founder Ubaid brings these worlds together in the heart of 3B2 Mohali.
    </p>
    <p class="story-body reveal reveal-delay-2">
      Come for the food. Stay for the warmth. Every cup of Noon Chai, every plate of Rogan Josh, every sip of cold coffee tells a story of mountains, mustard fields, and home.
    </p>
    <div class="story-owner reveal reveal-delay-3">
      <div class="owner-badge">👨‍🍳</div>
      <div>
        <div class="owner-name">Ubaid</div>
        <div class="owner-title">Founder &amp; Owner</div>
      </div>
    </div>
  </div>
</div>
</div>

<!-- ===== MENU ===== -->
<section id="menu" class="menu-section">
  <div class="menu-inner">
    <div class="menu-header reveal">
      <p class="section-label">What We Serve</p>
      <h2>Our <em>Menu</em></h2>
    </div>

    <div class="menu-tabs" id="menuTabs">
      <button class="tab-btn active" data-tab="kashmiri">🏔️ Kashmiri</button>
      <button class="tab-btn" data-tab="punjabi">🌾 Punjabi</button>
      <button class="tab-btn" data-tab="fastfood">🍔 Fast Food</button>
      <button class="tab-btn" data-tab="coffee">☕ Coffee</button>
      <button class="tab-btn" data-tab="shakes">🥛 Shakes</button>
      <button class="tab-btn" data-tab="tea">🍵 Tea</button>
      <button class="tab-btn" data-tab="drinks">🥤 Drinks</button>
    </div>

    <!-- KASHMIRI -->
    <div class="menu-pane active" id="tab-kashmiri">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kashmiri Pulao</div><div class="item-desc">Fragrant rice with dry fruits, saffron & whole spices</div></div><div class="item-price">₹100</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Rogan Josh</div><div class="item-desc">Slow-cooked lamb in Kashmiri red masala</div></div><div class="item-price">₹160</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Yakhni Chicken</div><div class="item-desc">Tender chicken in yogurt &amp; fennel gravy</div></div><div class="item-price">₹140</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Dum Aloo (Kashmiri)</div><div class="item-desc">Baby potatoes in rich tomato-fennel curry</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kashmiri Naan</div><div class="item-desc">Saffron-brushed, sesame-topped naan</div></div><div class="item-price">₹30</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Haakh Saag</div><div class="item-desc">Kashmiri collard greens slow-cooked with mustard oil</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Tabak Maaz</div><div class="item-desc">Crispy fried ribs marinated in Kashmiri spices</div></div><div class="item-price">₹180</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kashmiri Rajma</div><div class="item-desc">Mountain kidney beans with walnut paste</div></div><div class="item-price">₹85</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Seekh Kabab (Kashmiri)</div><div class="item-desc">Minced meat with Kashmiri spices, grilled on charcoal</div></div><div class="item-price">₹130</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kashmiri Chaman</div><div class="item-desc">Cottage cheese cubes in Kashmiri gravy</div></div><div class="item-price">₹95</div></div>
      </div>
    </div>

    <!-- PUNJABI -->
    <div class="menu-pane" id="tab-punjabi">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Butter Chicken</div><div class="item-desc">Tandoor-grilled chicken in creamy tomato sauce</div></div><div class="item-price">₹130</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Dal Makhani</div><div class="item-desc">Black lentils slow-cooked overnight with cream &amp; butter</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Tandoori Chicken (half)</div><div class="item-desc">Classic marinated chicken from the clay oven</div></div><div class="item-price">₹150</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Amritsari Kulcha</div><div class="item-desc">Stuffed flatbread served with chhole &amp; pickle</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Sarson da Saag + Makki Roti</div><div class="item-desc">Mustard greens with white butter &amp; jaggery</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Paneer Tikka</div><div class="item-desc">Marinated cottage cheese grilled to perfection</div></div><div class="item-price">₹110</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Punjabi Chhole</div><div class="item-desc">Spiced chickpeas with bhatura or rice</div></div><div class="item-price">₹75</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chicken Curry (Punjabi)</div><div class="item-desc">Bold desi chicken curry with onion-tomato masala</div></div><div class="item-price">₹120</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Tandoori Roti</div><div class="item-desc">Whole-wheat from clay oven</div></div><div class="item-price">₹20</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Wadi Combo Thali</div><div class="item-desc">Dal, sabzi, rice, roti, raita &amp; pickle</div></div><div class="item-price">₹120</div></div>
      </div>
    </div>

    <!-- FAST FOOD -->
    <div class="menu-pane" id="tab-fastfood">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Desi Chicken Burger</div><div class="item-desc">Crispy tikka patty, kashmiri chutney, onion rings</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Veggie Burger</div><div class="item-desc">Spiced aloo tikki, cheese slice, coleslaw</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chicken Shawarma</div><div class="item-desc">Grilled chicken, garlic sauce, veggies in bread</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chapli Kabab Wrap</div><div class="item-desc">Spiced beef chapli, mint chutney, in roomali roti</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Crispy Fries (Regular)</div><div class="item-desc">Golden salted fries with ketchup</div></div><div class="item-price">₹40</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Masala Fries</div><div class="item-desc">Chaat masala, lemon, green chilli</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Club Sandwich</div><div class="item-desc">Triple layer with chicken, egg, cheese, veggies</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Grilled Chicken Sandwich</div><div class="item-desc">Tender grilled breast, lettuce, mayo</div></div><div class="item-price">₹75</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Cheese Tikki</div><div class="item-desc">Potato tikki stuffed with cheese &amp; herbs</div></div><div class="item-price">₹55</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Pizza (Personal)</div><div class="item-desc">Desi-spiced chicken or paneer topping</div></div><div class="item-price">₹100</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Noodles (Wok-tossed)</div><div class="item-desc">Spicy desi style hakka noodles</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chicken Roll</div><div class="item-desc">Paratha wrap with juicy chicken tikka &amp; onions</div></div><div class="item-price">₹70</div></div>
      </div>
    </div>

    <!-- COFFEE -->
    <div class="menu-pane" id="tab-coffee">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Espresso</div><div class="item-desc">Strong single shot, dark roast</div></div><div class="item-price">₹40</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Double Espresso</div><div class="item-desc">Two shots, intense &amp; bold</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Americano</div><div class="item-desc">Espresso diluted with hot water</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Cappuccino</div><div class="item-desc">Espresso, steamed milk &amp; thick foam</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Café Latte</div><div class="item-desc">Espresso with creamy steamed milk</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Flat White</div><div class="item-desc">Velvety micro-foam with double ristretto</div></div><div class="item-price">₹85</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mocha</div><div class="item-desc">Espresso, chocolate sauce &amp; steamed milk</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Cold Coffee</div></div><div class="item-price">₹130</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Cold Coffee (Special)</div><div class="item-desc">With ice cream &amp; chocolate drizzle</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Dalgona Coffee</div><div class="item-desc">Whipped coffee over chilled milk</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Vietnamese Iced Coffee</div><div class="item-desc">Sweetened condensed milk &amp; drip coffee</div></div><div class="item-price">₹85</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Hazelnut Latte</div><div class="item-desc">Latte with hazelnut syrup &amp; foam</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Caramel Macchiato</div><div class="item-desc">Vanilla, milk foam &amp; caramel drizzle</div></div><div class="item-price">₹95</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Turkish Coffee</div><div class="item-desc">Unfiltered, cardamom-spiced, rich</div></div><div class="item-price">₹65</div></div>
      </div>
    </div>

    <!-- SHAKES -->
    <div class="menu-pane" id="tab-shakes">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mango Shake</div><div class="item-desc">Fresh Alfonso mango blended with milk</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Banana Shake</div><div class="item-desc">Ripe banana, milk &amp; honey</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Strawberry Shake</div><div class="item-desc">Fresh strawberries blended with cream</div></div><div class="item-price">₹75</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chocolate Shake</div><div class="item-desc">Thick chocolate milkshake with choco chips</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Oreo Shake</div><div class="item-desc">Crushed Oreo cookies &amp; vanilla ice cream</div></div><div class="item-price">₹85</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Dry Fruit Shake</div><div class="item-desc">Almonds, cashews, pista &amp; dates — Kashmiri style</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Rose Shake (Rooh Afza)</div><div class="item-desc">Traditional rose sherbet &amp; chilled milk</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kesar Badam Shake</div><div class="item-desc">Saffron &amp; almond milk — Kashmiri heritage</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Butterscotch Shake</div><div class="item-desc">Butterscotch ice cream &amp; caramel swirl</div></div><div class="item-price">₹80</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mixed Fruit Shake</div><div class="item-desc">Seasonal fruits blended fresh daily</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Pistachio Shake</div><div class="item-desc">Thick pista shake with rose essence</div></div><div class="item-price">₹90</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Sweet Lassi</div><div class="item-desc">Thick Punjabi yogurt shake, sugar &amp; rose water</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Salted Lassi</div><div class="item-desc">Chilled yogurt, roasted cumin, mint</div></div><div class="item-price">₹45</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mango Lassi</div><div class="item-desc">Fresh mango pulp blended in yogurt</div></div><div class="item-price">₹65</div></div>
      </div>
    </div>

    <!-- TEA -->
    <div class="menu-pane" id="tab-tea">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Noon Chai (Pink Tea)</div><div class="item-desc">Authentic Kashmiri pink salt tea with pistachios</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Kashmiri Kahwa</div><div class="item-desc">Green tea, saffron, cardamom, cinnamon &amp; almonds</div></div><div class="item-price">₹55</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Sheer Chai</div><div class="item-desc">Creamy milk tea with Kashmiri spices</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Masala Chai</div><div class="item-desc">Ginger, cardamom, clove &amp; pepper in desi tea</div></div><div class="item-price">₹30</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Karak Chai</div><div class="item-desc">Strong tea brewed with condensed milk</div></div><div class="item-price">₹40</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Green Tea</div><div class="item-desc">Light, refreshing unoxidised leaves</div></div><div class="item-price">₹35</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Lemon Ginger Tea</div><div class="item-desc">Detox tea with honey, lemon &amp; fresh ginger</div></div><div class="item-price">₹40</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mint Tea</div><div class="item-desc">Fresh pudina with green tea</div></div><div class="item-price">₹35</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Black Tea</div><div class="item-desc">Classic plain tea, no milk</div></div><div class="item-price">₹25</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Chamomile Tea</div><div class="item-desc">Calming herbal infusion</div></div><div class="item-price">₹45</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Adrak Wali Chai</div><div class="item-desc">Extra strong ginger tea, desi style</div></div><div class="item-price">₹30</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Saffron Milk Tea</div><div class="item-desc">Warm milk with Kashmiri kesar — luxurious</div></div><div class="item-price">₹60</div></div>
      </div>
    </div>

    <!-- DRINKS -->
    <div class="menu-pane" id="tab-drinks">
      <div class="menu-grid">
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Fresh Lime Soda</div><div class="item-desc">Sweet or salted, with mint &amp; ice</div></div><div class="item-price">₹40</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Rooh Afza Cooler</div><div class="item-desc">Rose sherbet with chilled water &amp; basil seeds</div></div><div class="item-price">₹45</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Mango Panna</div><div class="item-desc">Raw mango summer drink with cumin &amp; mint</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Fresh Orange Juice</div><div class="item-desc">Freshly squeezed, no added sugar</div></div><div class="item-price">₹60</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Watermelon Juice</div><div class="item-desc">Chilled seasonal watermelon</div></div><div class="item-price">₹50</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Apple Juice (Fresh)</div><div class="item-desc">Kashmiri apple — seasonal &amp; sweet</div></div><div class="item-price">₹65</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Pomegranate Juice</div><div class="item-desc">Rich anaar juice, fresh &amp; antioxidant</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Virgin Mojito</div><div class="item-desc">Lime, mint, sugar syrup &amp; sparkling water</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Blue Lagoon</div><div class="item-desc">Blue curacao syrup, lime &amp; soda</div></div><div class="item-price">₹75</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Lychee Cooler</div><div class="item-desc">Fresh lychee juice with rose water</div></div><div class="item-price">₹70</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Iced Jaljeera</div><div class="item-desc">Classic cumin-tamarind chilled drink</div></div><div class="item-price">₹35</div></div>
        <div class="menu-item-card"><div class="item-info"><div class="item-name">Buttermilk (Chaas)</div><div class="item-desc">Chilled spiced curd water with coriander</div></div><div class="item-price">₹30</div></div>
      </div>
    </div>

  </div>
</section>

<!-- ===== SPECIALS ===== -->
<section id="specials" class="specials-section">
  <div class="specials-inner">
    <div class="specials-header">
      <p class="story-label reveal">Signature Dishes</p>
      <h2 class="story-title reveal reveal-delay-1" style="max-width:600px;">Must-Try<br><em>Specialties</em></h2>
    </div>
    <div class="specials-grid">
      <div class="special-card reveal">
        <div class="special-top c1">🏔️</div>
        <div class="special-body">
          <div class="special-name">Noon Chai Experience</div>
          <p class="special-desc">Authentic Kashmiri pink salt tea brewed the traditional way with cardamom, crushed pistachios, and baked milk. A rare and stunning cup you can't find easily in Mohali.</p>
          <div class="special-price">From ₹50</div>
        </div>
      </div>
      <div class="special-card reveal reveal-delay-1">
        <div class="special-top c2">🍛</div>
        <div class="special-body">
          <div class="special-name">Wadi Grand Platter</div>
          <p class="special-desc">Our signature sharing platter — Rogan Josh, Kashmiri Pulao, Yakhni Chicken, Naan & Kashmiri Kahwa. The ultimate Kashmiri feast for two.</p>
          <div class="special-price">₹350 (for 2)</div>
        </div>
      </div>
      <div class="special-card reveal reveal-delay-2">
        <div class="special-top c3">🔥</div>
        <div class="special-body">
          <div class="special-name">Ubaid's Fusion Kabab</div>
          <p class="special-desc">Chapli-Seekh fusion — minced meat with Kashmiri red chilli, pomegranate seeds, and desi ghee. Grilled over coals, served with house chutney.</p>
          <div class="special-price">₹130</div>
        </div>
      </div>
      <div class="special-card reveal">
        <div class="special-top c4">☕</div>
        <div class="special-body">
          <div class="special-name">Kesar Kahwa Cooler</div>
          <p class="special-desc">Chilled Kashmiri Kahwa with rose water, honey ice cubes, and a saffron thread on top. Our most-photographed summer drink.</p>
          <div class="special-price">₹80</div>
        </div>
      </div>
      <div class="special-card reveal reveal-delay-1">
        <div class="special-top c5">🌾</div>
        <div class="special-body">
          <div class="special-name">Sarson Thali</div>
          <p class="special-desc">The pure Punjabi winter soul meal — Sarson da Saag cooked overnight, Makki di Roti, white butter, and gur (jaggery). Warmth on a plate.</p>
          <div class="special-price">₹80</div>
        </div>
      </div>
      <div class="special-card reveal reveal-delay-2">
        <div class="special-top c6">🥛</div>
        <div class="special-body">
          <div class="special-name">Kesar Badam Shake</div>
          <p class="special-desc">Rich almond milk blended with authentic Kashmiri saffron, cardamom, and rose essence. A royal drink inspired by Mughal-era Kashmiri traditions.</p>
          <div class="special-price">₹90</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== ABOUT BAND ===== -->
<div class="about-band">
  <div class="about-band-inner reveal">
    <p class="about-band-label">A Word from the Founder</p>
    <p class="about-band-quote">"I built Wadi da Dhaba because Mohali deserved to taste the mountains. Every dish is a memory — of Kashmiri winters, Punjabi summers, and the warmth that food brings to strangers who soon become friends."</p>
    <p class="about-band-attr">— Ubaid, Founder &nbsp;·&nbsp; +91 6005341675</p>
  </div>
</div>

<!-- ===== VISIT ===== -->
<div style="background:var(--parchment);">
<div class="visit-section" id="visit">
  <div class="reveal">
    <div class="visit-heading">
      <p class="section-label">Come Find Us</p>
      <h2>Visit<br><em style="font-style:italic; color:var(--sage);">Wadi da Dhaba</em></h2>
    </div>
    <div class="contact-grid">
      <div class="contact-item">
        <div class="contact-label">Address</div>
        <div class="contact-value">3B2, Mohali<br>Punjab, India</div>
      </div>
      <div class="contact-item">
        <div class="contact-label">Open Daily</div>
        <div class="contact-value">8:00 AM – 11:00 PM</div>
      </div>
      <div class="contact-item">
        <div class="contact-label">Call / WhatsApp</div>
        <div class="contact-value"><a href="tel:+916005341675">+91 6005341675</a></div>
      </div>
      <div class="contact-item">
        <div class="contact-label">Owner</div>
        <div class="contact-value">Ubaid</div>
      </div>
    </div>
    <a href="tel:+916005341675" class="btn btn-filled">📞 Call Now</a>
    <a href="#menu" class="btn btn-ghost" style="margin-left:1rem;">View Menu</a>
  </div>

  <div class="map-card reveal">
    <div class="map-card-inner">
      <div class="map-pin">📍</div>
      <div class="map-name">Wadi da Dhaba</div>
      <div class="map-addr">3B2, Mohali, Punjab</div>
      <div style="margin-top:1.5rem; font-family:'Lora',serif; font-style:italic; font-size:1rem; color:rgba(250,243,232,0.5);">"Open every day,<br>warm every hour"</div>
    </div>
  </div>
</div>
</div>

<!-- ===== FOOTER ===== -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-brand-name">Wadi <em>da Dhaba</em></div>
      <div class="footer-brand-sub">Kashmiri · Punjabi · 3B2 Mohali</div>
    </div>
    <ul class="footer-nav">
      <li><a href="#story">Our Story</a></li>
      <li><a href="#menu">Menu</a></li>
      <li><a href="#specials">Specialties</a></li>
      <li><a href="#visit">Visit Us</a></li>
    </ul>
    <div>
      <div class="contact-label" style="font-family:'Josefin Sans',sans-serif; font-size:0.6rem; letter-spacing:0.2em; text-transform:uppercase; color:var(--sage); margin-bottom:0.4rem;">Contact</div>
      <div style="font-family:'Cormorant Garamond',serif; font-size:1.1rem; color:var(--cream);">
        <a href="tel:+916005341675" style="color:var(--mustard); text-decoration:none;">+91 6005341675</a>
      </div>
      <div style="font-family:'Lora',serif; font-size:0.9rem; font-style:italic; color:rgba(250,243,232,0.4); margin-top:0.3rem;">Open 8 AM – 11 PM Daily</div>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">© 2026 Wadi da Dhaba by Ubaid · 3B2 Mohali</div>
    <div class="footer-copy">Where the Valley Meets the Fields</div>
  </div>
</footer>

<script>
// Cursor
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx=0, my=0, rx=0, ry=0;
document.addEventListener('mousemove', e => { mx=e.clientX; my=e.clientY; cursor.style.left=mx+'px'; cursor.style.top=my+'px'; });
function animateRing() { rx+=(mx-rx)*0.12; ry+=(my-ry)*0.12; ring.style.left=rx+'px'; ring.style.top=ry+'px'; requestAnimationFrame(animateRing); }
animateRing();

// Navbar scroll
const navbar = document.getElementById('navbar');
window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', window.scrollY > 60);
});

// Menu tabs
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.menu-pane').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('tab-' + btn.dataset.tab).classList.add('active');
  });
});

// Reveal on scroll
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
