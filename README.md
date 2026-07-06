<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>J S Harini Devi — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #0a0d14;
    --panel: #10151f;
    --panel-2: #131a26;
    --cyan: #5eead4;
    --pink: #e879c9;
    --gold: #f0b429;
    --text: #e7e9ee;
    --muted: #8b93a7;
    --line: rgba(231,233,238,0.08);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Inter',sans-serif;
    overflow-x:hidden;
    position:relative;
  }

  /* subtle honeycomb texture backdrop */
  .honey-bg{
    position:fixed;
    inset:0;
    z-index:0;
    opacity:0.05;
    background-image:
      repeating-linear-gradient(60deg, transparent, transparent 39px, var(--cyan) 40px),
      repeating-linear-gradient(-60deg, transparent, transparent 39px, var(--pink) 40px);
    pointer-events:none;
  }
  .glow-orb{
    position:fixed;
    border-radius:50%;
    filter:blur(90px);
    z-index:0;
    pointer-events:none;
  }
  .orb1{width:420px;height:420px;background:var(--cyan);opacity:0.10;top:-100px;left:-100px;}
  .orb2{width:380px;height:380px;background:var(--pink);opacity:0.08;bottom:10%;right:-120px;}
  .orb3{width:300px;height:300px;background:var(--gold);opacity:0.06;top:40%;left:50%;}

  section, header, footer{position:relative;z-index:1;}

  .wrap{max-width:1080px;margin:0 auto;padding:0 28px;}

  /* NAV */
  nav{
    position:sticky;top:0;z-index:10;
    backdrop-filter:blur(14px);
    background:rgba(10,13,20,0.72);
    border-bottom:1px solid var(--line);
  }
  nav .wrap{display:flex;align-items:center;justify-content:space-between;height:68px;}
  .logo{
    font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:18px;letter-spacing:0.5px;
    color:var(--text);
  }
  .logo span{color:var(--cyan);}
  .navlinks{display:flex;gap:32px;list-style:none;}
  .navlinks a{
    color:var(--muted);text-decoration:none;font-size:14px;font-weight:500;
    transition:color .25s ease;
  }
  .navlinks a:hover{color:var(--cyan);}

  /* HERO */
  header.hero{
    padding:96px 0 80px;
    display:flex;align-items:center;gap:56px;
    min-height:80vh;
  }
  .hero .wrap{display:flex;align-items:center;gap:56px;flex-wrap:wrap;}
  .hero-text{flex:1 1 380px;}
  .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size:12.5px;color:var(--gold);letter-spacing:2px;text-transform:uppercase;
    display:flex;align-items:center;gap:10px;margin-bottom:20px;
    opacity:0;animation:fadeUp .7s ease forwards;
  }
  .eyebrow::before{
    content:"";width:22px;height:1px;background:var(--gold);display:inline-block;
  }
  h1.name{
    font-family:'Space Grotesk',sans-serif;
    font-weight:700;
    font-size:clamp(36px,6vw,58px);
    line-height:1.05;
    letter-spacing:-0.5px;
    margin-bottom:18px;
    opacity:0;animation:fadeUp .7s ease .1s forwards;
  }
  h1.name .grad{
    background:linear-gradient(90deg,var(--cyan),var(--pink) 60%, var(--gold));
    -webkit-background-clip:text;background-clip:text;color:transparent;
  }
  .tagline{
    font-size:17px;color:var(--muted);max-width:480px;line-height:1.65;margin-bottom:32px;
    opacity:0;animation:fadeUp .7s ease .2s forwards;
  }
  .hero-cta{
    display:flex;gap:14px;flex-wrap:wrap;
    opacity:0;animation:fadeUp .7s ease .3s forwards;
  }
  .btn{
    font-family:'Inter',sans-serif;font-weight:600;font-size:14px;
    padding:13px 26px;border-radius:8px;text-decoration:none;
    transition:transform .25s ease, box-shadow .25s ease;
  }
  .btn-primary{
    background:linear-gradient(90deg,var(--cyan),var(--pink));
    color:#0a0d14;
  }
  .btn-primary:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(94,234,212,0.25);}
  .btn-ghost{
    border:1px solid var(--line);color:var(--text);
  }
  .btn-ghost:hover{border-color:var(--cyan);color:var(--cyan);}

  @keyframes fadeUp{
    from{opacity:0;transform:translateY(16px);}
    to{opacity:1;transform:translateY(0);}
  }

  /* profile hex frame — echoes the honeycomb medal */
  .hex-frame{
    flex:0 0 260px;
    width:260px;height:300px;
    position:relative;
    opacity:0;animation:fadeUp .8s ease .15s forwards;
  }
  .hex-clip{
    width:100%;height:100%;
    clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
    background:var(--panel);
    position:relative;
    overflow:hidden;
    box-shadow:0 0 0 2px rgba(94,234,212,0.35), 0 0 40px rgba(94,234,212,0.15);
  }
  .hex-clip img{
    width:100%;height:100%;object-fit:cover;object-position:top center;
  }
  .hex-ring{
    position:absolute;inset:-14px;
    clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
    border:1px dashed rgba(232,121,201,0.4);
    pointer-events:none;
  }

  /* SECTION HEADERS */
  .section{padding:88px 0;}
  .section-head{
    display:flex;align-items:baseline;gap:16px;margin-bottom:44px;
  }
  .hex-bullet{
    width:11px;height:11px;flex-shrink:0;
    background:var(--gold);
    clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
  }
  .section-title{
    font-family:'Space Grotesk',sans-serif;font-weight:600;font-size:28px;
  }
  .section-sub{
    font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);letter-spacing:1px;
  }

  /* ABOUT */
  .about-grid{
    display:grid;grid-template-columns:1.3fr 1fr;gap:48px;
  }
  .about-text p{
    color:#c7cbd6;line-height:1.8;font-size:15.5px;margin-bottom:16px;
  }
  .about-text strong{color:var(--cyan);font-weight:600;}
  .info-card{
    background:var(--panel);border:1px solid var(--line);border-radius:14px;
    padding:24px 26px;
  }
  .info-row{
    display:flex;justify-content:space-between;padding:11px 0;
    border-bottom:1px solid var(--line);font-size:14px;
  }
  .info-row:last-child{border-bottom:none;}
  .info-row .k{color:var(--muted);font-family:'JetBrains Mono',monospace;font-size:12.5px;}
  .info-row .v{color:var(--text);font-weight:500;text-align:right;}

  /* INSPIRATION */
  .insp-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:24px;
  }
  .insp-card{
    background:var(--panel);border:1px solid var(--line);border-radius:16px;
    padding:30px 28px;position:relative;overflow:hidden;
    transition:border-color .25s ease, transform .25s ease;
  }
  .insp-card:hover{transform:translateY(-4px);}
  .insp-card.tata:hover{border-color:var(--cyan);}
  .insp-card.kalam:hover{border-color:var(--pink);}
  .insp-mark{
    font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:15px;
    letter-spacing:1px;margin-bottom:6px;
  }
  .insp-card.tata .insp-mark{color:var(--cyan);}
  .insp-card.kalam .insp-mark{color:var(--pink);}
  .insp-role{
    font-family:'JetBrains Mono',monospace;font-size:11.5px;color:var(--muted);
    letter-spacing:0.5px;margin-bottom:16px;text-transform:uppercase;
  }
  .insp-text{color:#c7cbd6;font-size:14.5px;line-height:1.75;}

  /* ACHIEVEMENT */
  .achieve-card{
    background:linear-gradient(155deg, var(--panel) 0%, var(--panel-2) 100%);
    border:1px solid var(--line);
    border-radius:20px;
    padding:44px;
    position:relative;
    overflow:hidden;
  }
  .achieve-card::before{
    content:"";position:absolute;top:-40%;right:-15%;width:340px;height:340px;
    background:radial-gradient(circle, rgba(240,180,41,0.18), transparent 70%);
    pointer-events:none;
  }
  .achieve-top{
    display:flex;align-items:center;gap:14px;margin-bottom:10px;position:relative;z-index:1;
  }
  .medal-tag{
    font-family:'JetBrains Mono',monospace;font-size:11.5px;letter-spacing:1.5px;
    color:var(--gold);text-transform:uppercase;
    border:1px solid rgba(240,180,41,0.4);
    padding:5px 12px;border-radius:100px;
  }
  .achieve-title{
    font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:25px;
    margin-bottom:12px;position:relative;z-index:1;
  }
  .achieve-desc{
    color:#c7cbd6;font-size:15px;line-height:1.75;max-width:560px;margin-bottom:32px;position:relative;z-index:1;
  }
  .achieve-media{
    display:grid;grid-template-columns:1fr 1.4fr;gap:28px;position:relative;z-index:1;
  }
  .medal-box{
    background:#000;border-radius:14px;overflow:hidden;
    border:1px solid rgba(240,180,41,0.3);
    display:flex;align-items:center;justify-content:center;
    aspect-ratio:3/4;
  }
  .medal-box img{width:100%;height:100%;object-fit:cover;}
  .cert-box{
    background:#000;border-radius:14px;overflow:hidden;
    border:1px solid var(--line);
    display:flex;align-items:center;justify-content:center;
    aspect-ratio:3/4;
  }
  .cert-box img{width:100%;height:100%;object-fit:cover;object-position:top;}
  .media-cap{
    font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--muted);
    text-align:center;margin-top:10px;letter-spacing:0.5px;
  }

  /* SKILLS */
  .skills-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;
  }
  .skill-chip{
    background:var(--panel);border:1px solid var(--line);border-radius:12px;
    padding:18px 20px;
    transition:border-color .25s ease, transform .25s ease;
  }
  .skill-chip:hover{border-color:var(--pink);transform:translateY(-3px);}
  .skill-name{font-weight:600;font-size:14.5px;margin-bottom:4px;}
  .skill-cat{font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--muted);}

  footer{
    padding:48px 0 64px;text-align:center;border-top:1px solid var(--line);
  }
  footer .foot-name{font-family:'Space Grotesk',sans-serif;font-weight:600;color:var(--text);margin-bottom:6px;}
  footer .foot-sub{font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);}

  .reveal{opacity:0;transform:translateY(24px);transition:opacity .7s ease, transform .7s ease;}
  .reveal.in{opacity:1;transform:translateY(0);}

  @media (max-width:760px){
    .hero .wrap{flex-direction:column-reverse;text-align:center;}
    .hero-text{text-align:center;}
    .tagline{margin-left:auto;margin-right:auto;}
    .eyebrow{justify-content:center;}
    .hero-cta{justify-content:center;}
    .about-grid{grid-template-columns:1fr;}
    .achieve-media{grid-template-columns:1fr;}
    .navlinks{gap:18px;}
    .navlinks a{font-size:12.5px;}
  }
  @media (prefers-reduced-motion: reduce){
    *{animation:none !important;transition:none !important;}
  }
  a:focus-visible, button:focus-visible{outline:2px solid var(--cyan);outline-offset:3px;}
</style>
</head>
<body>

<div class="honey-bg"></div>
<div class="glow-orb orb1"></div>
<div class="glow-orb orb2"></div>
<div class="glow-orb orb3"></div>

<nav>
  <div class="wrap">
    <div class="logo">J.S. <span>Harini</span> Devi</div>
    <ul class="navlinks">
      <li><a href="#about">About</a></li>
      <li><a href="#inspiration">Inspiration</a></li>
      <li><a href="#achievement">Achievement</a></li>
      <li><a href="#skills">Skills</a></li>
    </ul>
  </div>
</nav>

<header class="hero">
  <div class="wrap">
    <div class="hero-text">
      <div class="eyebrow">First Year · AI &amp; Data Science</div>
      <h1 class="name">J S Harini<br><span class="grad">Devi</span></h1>
      <p class="tagline">Calm under pressure, sharp with data. I build thoughtful, well-reasoned solutions — and I'm just getting started in AI &amp; Data Science.</p>
      <div class="hero-cta">
        <a href="#achievement" class="btn btn-primary">View Achievement</a>
        <a href="#about" class="btn btn-ghost">About Me</a>
      </div>
    </div>
    <div class="hex-frame">
      <div class="hex-ring"></div>
      <div class="hex-clip">
        <img src="data:image/png;base64,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
