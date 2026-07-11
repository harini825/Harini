<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Harinidevi — AI &amp; Data Science | Portfolio</title>
<style>
  :root{
    --bg: #05070c;
    --panel: #0b101a;
    --panel-2: #0f1626;
    --cyan: #00eaff;
    --magenta: #ff2bd6;
    --amber: #ffb347;
    --text: #eaf6ff;
    --muted: #7f93ab;
    --line: rgba(255,255,255,0.08);
  }

  *{box-sizing:border-box; margin:0; padding:0;}

  @font-face{
    font-family:'Orbitron';
    src: local('Orbitron');
  }

  html{scroll-behavior:smooth;}

  body{
    background: var(--bg);
    color: var(--text);
    font-family: 'Sora', 'Segoe UI', system-ui, sans-serif;
    overflow-x:hidden;
    position:relative;
    min-height:100vh;
  }

  /* ---------- Neon ambient background ---------- */
  .bg-neon{
    position:fixed;
    inset:0;
    z-index:-2;
    background:
      radial-gradient(ellipse 60% 40% at 15% 10%, rgba(0,234,255,0.16), transparent 60%),
      radial-gradient(ellipse 50% 35% at 85% 20%, rgba(255,43,214,0.14), transparent 60%),
      radial-gradient(ellipse 55% 45% at 50% 90%, rgba(255,179,71,0.08), transparent 60%),
      linear-gradient(180deg, #05070c 0%, #060a13 40%, #05070c 100%);
    animation: drift 22s ease-in-out infinite alternate;
  }
  @keyframes drift{
    0%{ filter:brightness(1); }
    100%{ filter:brightness(1.05); }
  }
  .bg-grid{
    position:fixed;
    inset:0;
    z-index:-1;
    background-image:
      linear-gradient(rgba(0,234,255,0.045) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,234,255,0.045) 1px, transparent 1px);
    background-size: 48px 48px;
    mask-image: radial-gradient(ellipse 80% 60% at 50% 20%, black 40%, transparent 90%);
  }

  /* ---------- Layout shell ---------- */
  header, main, footer{ position:relative; z-index:2; }

  .wrap{
    max-width: 1080px;
    margin: 0 auto;
    padding: 0 28px;
  }

  nav{
    position: sticky;
    top:0;
    z-index: 20;
    backdrop-filter: blur(14px);
    background: rgba(5,7,12,0.55);
    border-bottom: 1px solid var(--line);
  }
  nav .wrap{
    display:flex;
    align-items:center;
    justify-content:space-between;
    height:64px;
  }
  .brand{
    font-family:'Orbitron', sans-serif;
    letter-spacing:2px;
    font-size:15px;
    color: var(--cyan);
    text-shadow: 0 0 12px rgba(0,234,255,0.6);
  }
  .navlinks{
    display:flex;
    gap:26px;
    list-style:none;
  }
  .navlinks a{
    color: var(--muted);
    text-decoration:none;
    font-size:13px;
    letter-spacing:0.5px;
    text-transform:uppercase;
    transition: color .25s ease;
  }
  .navlinks a:hover{ color: var(--cyan); }

  /* ---------- Hero ---------- */
  .hero{
    min-height: 92vh;
    display:flex;
    align-items:center;
    padding-top: 40px;
  }
  .hero .wrap{
    display:grid;
    grid-template-columns: 1.1fr 0.9fr;
    gap: 48px;
    align-items:center;
  }
  .eyebrow{
    font-size:12px;
    letter-spacing:3px;
    text-transform:uppercase;
    color: var(--cyan);
    margin-bottom:18px;
    display:flex;
    align-items:center;
    gap:10px;
  }
  .eyebrow::before{
    content:'';
    width:26px; height:1px;
    background: var(--cyan);
    box-shadow: 0 0 8px var(--cyan);
  }
  h1.name{
    font-family:'Orbitron', sans-serif;
    font-size: clamp(2.6rem, 6vw, 4.4rem);
    line-height:1.05;
    font-weight:700;
    background: linear-gradient(120deg, #ffffff 0%, var(--cyan) 55%, var(--magenta) 100%);
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
    filter: drop-shadow(0 0 22px rgba(0,234,255,0.25));
    margin-bottom: 18px;
  }
  .role{
    font-size: 1.05rem;
    color: var(--text);
    opacity:0.9;
    margin-bottom: 10px;
  }
  .role b{ color: var(--amber); font-weight:600; }
  .tagline{
    color: var(--muted);
    max-width: 46ch;
    line-height:1.7;
    margin-bottom: 30px;
    font-size:0.98rem;
  }
  .cta-row{ display:flex; gap:14px; flex-wrap:wrap; }
  .btn{
    display:inline-flex;
    align-items:center;
    gap:8px;
    padding: 13px 24px;
    border-radius: 999px;
    font-size:13px;
    letter-spacing:0.6px;
    text-transform:uppercase;
    text-decoration:none;
    cursor:pointer;
    border:1px solid transparent;
    transition: transform .25s ease, box-shadow .25s ease;
  }
  .btn-primary{
    background: linear-gradient(90deg, var(--cyan), var(--magenta));
    color:#04060a;
    font-weight:700;
    box-shadow: 0 0 24px rgba(0,234,255,0.35);
  }
  .btn-primary:hover{ transform: translateY(-2px); box-shadow: 0 0 32px rgba(255,43,214,0.5); }
  .btn-ghost{
    border-color: var(--line);
    color: var(--text);
    background: rgba(255,255,255,0.02);
  }
  .btn-ghost:hover{ border-color: var(--cyan); color: var(--cyan); transform: translateY(-2px); }

  .portrait{
    position:relative;
    justify-self:center;
  }
  .portrait-frame{
    width: min(300px, 76vw);
    aspect-ratio: 401/940;
    max-height: 78vh;
    border-radius: 22px;
    position:relative;
    padding:5px;
    background: linear-gradient(160deg, var(--cyan), var(--magenta) 60%, var(--amber));
    box-shadow: 0 0 50px rgba(0,234,255,0.22), 0 0 90px rgba(255,43,214,0.1);
  }
  .portrait-frame img{
    width:100%; height:100%;
    object-fit:contain;
    object-position: center;
    background: #05070c;
    border-radius: 18px;
    display:block;
    image-rendering: -webkit-optimize-contrast;
  }
  .portrait-ring{
    position:absolute;
    inset:-16px;
    border-radius: 30px;
    border: 1px solid rgba(0,234,255,0.25);
  }

  /* ---------- Section shared ---------- */
  section{ padding: 110px 0; border-top: 1px solid var(--line); }
  .sec-head{ margin-bottom: 48px; }
  .sec-num{
    font-family:'Orbitron', sans-serif;
    font-size:12px;
    color: var(--magenta);
    letter-spacing:3px;
    margin-bottom:10px;
    text-shadow: 0 0 10px rgba(255,43,214,0.5);
  }
  .sec-title{
    font-family:'Orbitron', sans-serif;
    font-size: clamp(1.6rem, 3.4vw, 2.3rem);
    font-weight:700;
  }
  .sec-sub{ color: var(--muted); max-width:62ch; margin-top:12px; line-height:1.7; font-size:0.96rem;}

  /* ---------- About / skills ---------- */
  .about-grid{
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
  }
  .about-text p{ color: var(--muted); line-height:1.85; margin-bottom:16px; font-size:0.98rem; }
  .about-text strong{ color: var(--text); }
  .skill-list{ list-style:none; display:flex; flex-direction:column; gap:14px; }
  .skill-list li{
    display:flex; align-items:center; justify-content:space-between;
    padding:14px 18px;
    background: var(--panel);
    border:1px solid var(--line);
    border-radius:12px;
    font-size:0.92rem;
    transition: border-color .3s ease, transform .3s ease;
  }
  .skill-list li:hover{ border-color: var(--cyan); transform: translateX(4px); }
  .skill-list span.tag{
    font-size:10px;
    letter-spacing:1px;
    color: var(--cyan);
    border:1px solid rgba(0,234,255,0.35);
    padding:4px 9px;
    border-radius:999px;
  }

  /* ---------- Achievements ---------- */
  .achieve-grid{
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 28px;
  }
  .achieve-card{
    background: var(--panel);
    border:1px solid var(--line);
    border-radius: 18px;
    overflow:hidden;
    transition: transform .35s ease, box-shadow .35s ease, border-color .35s ease;
    position:relative;
  }
  .achieve-card:hover{
    transform: translateY(-6px);
    border-color: rgba(0,234,255,0.4);
    box-shadow: 0 18px 40px rgba(0,0,0,0.5), 0 0 30px rgba(0,234,255,0.12);
  }
  .achieve-media{
    width:100%;
    aspect-ratio: 4/3;
    overflow:hidden;
    background:#000;
    display:flex; align-items:center; justify-content:center;
  }
  .achieve-media img{
    width:100%; height:100%; object-fit:cover;
    transition: transform .5s ease;
  }
  .achieve-card:hover .achieve-media img{ transform: scale(1.05); }
  .achieve-body{ padding: 20px 22px 24px; }
  .achieve-kicker{
    font-size:10px; letter-spacing:2px; text-transform:uppercase;
    color: var(--amber); margin-bottom:8px;
  }
  .achieve-title{ font-size:1.05rem; font-weight:700; margin-bottom:8px; }
  .achieve-desc{ color: var(--muted); font-size:0.9rem; line-height:1.7; }

  /* ---------- Inspiration ---------- */
  .insp-grid{
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 28px;
  }
  .insp-card{
    padding: 30px 26px;
    border-radius: 18px;
    background: linear-gradient(180deg, var(--panel), var(--panel-2));
    border:1px solid var(--line);
    position:relative;
    overflow:hidden;
  }
  .insp-card::after{
    content:'';
    position:absolute; right:-40px; top:-40px;
    width:140px; height:140px;
    border-radius:50%;
    background: radial-gradient(circle, rgba(0,234,255,0.16), transparent 70%);
  }
  .insp-name{ font-family:'Orbitron', sans-serif; font-size:1.05rem; color: var(--cyan); margin-bottom:6px; }
  .insp-role{ font-size:0.8rem; color: var(--muted); margin-bottom:16px; letter-spacing:0.5px; }
  .insp-quote{ font-size:0.95rem; line-height:1.75; color: var(--text); font-style:italic; }
  .insp-quote::before{ content:'“'; color: var(--magenta); font-size:1.4rem; }
  .insp-quote::after{ content:'”'; color: var(--magenta); font-size:1.4rem; }

  /* ---------- Italian quote / liquid signature panel ---------- */
  .quote-panel{
    border-radius: 22px;
    padding: 54px 40px;
    text-align:center;
    background: var(--panel);
    border:1px solid var(--line);
    position:relative;
    overflow:hidden;
  }
  .quote-panel .glow-orb{
    position:absolute;
    width:320px; height:320px;
    border-radius:50%;
    background: radial-gradient(circle, rgba(255,43,214,0.22), transparent 70%);
    top:-120px; left:-80px;
    pointer-events:none;
  }
  .quote-flag{
    font-size:11px; letter-spacing:3px; text-transform:uppercase;
    color: var(--amber); margin-bottom:20px;
  }
  .quote-it{
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(1.3rem, 3vw, 1.9rem);
    line-height:1.5;
    color: var(--text);
    max-width: 40ch;
    margin: 0 auto 16px;
    text-shadow: 0 0 18px rgba(0,234,255,0.25);
  }
  .quote-en{
    color: var(--muted);
    font-size:0.95rem;
    max-width: 42ch;
    margin: 0 auto;
    font-style:italic;
  }
  .quote-hint{
    margin-top:26px;
    font-size:11px;
    letter-spacing:1.5px;
    text-transform:uppercase;
    color: rgba(255,255,255,0.35);
  }

  /* ---------- Footer ---------- */
  footer{
    padding: 50px 0 60px;
    text-align:center;
    color: var(--muted);
    font-size:0.85rem;
    border-top: 1px solid var(--line);
  }
  footer .brand{ display:block; margin-bottom:10px; }

  @media (max-width: 760px){
    .hero .wrap{ grid-template-columns:1fr; text-align:center; }
    .eyebrow{ justify-content:center; }
    .cta-row{ justify-content:center; }
    .about-grid, .achieve-grid, .insp-grid{ grid-template-columns:1fr; }
    .navlinks{ display:none; }
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation:none !important; transition:none !important; }
  }
</style>
</head>
<body>

<div class="bg-neon"></div>
<div class="bg-grid"></div>

<nav>
  <div class="wrap">
    <div class="brand">HARINIDEVI.DEV</div>
    <ul class="navlinks">
      <li><a href="#about">About</a></li>
      <li><a href="#achievements">Achievements</a></li>
      <li><a href="#inspiration">Inspiration</a></li>
      <li><a href="#quote">Quote</a></li>
    </ul>
  </div>
</nav>

<main>
  <!-- HERO -->
  <section class="hero" style="border-top:none;">
    <div class="wrap">
      <div>
        <div class="eyebrow">First Year · AI &amp; Data Science</div>
        <h1 class="name">Harinidevi</h1>
        <div class="role">Aspiring <b>AI &amp; Data Science Engineer</b> — RD National College of Arts &amp; Science, Erode</div>
        <p class="tagline">I build with curiosity and calm — turning data into decisions and ideas into interfaces. Currently learning Italian alongside code, one language for machines, one for the world.</p>
        <div class="cta-row">
          <a href="#achievements" class="btn btn-primary">View Achievements</a>
          <a href="#quote" class="btn btn-ghost">Motivation ✦</a>
        </div>
      </div>
      <div class="portrait">
        <div class="portrait-ring"></div>
        <div class="portrait-frame">
          <img src="data:image/jpeg;base64,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
