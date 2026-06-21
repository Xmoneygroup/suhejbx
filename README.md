
<html lang="sq">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<meta name="theme-color" content="#000000"/>
<title>MKDMAP — Web Development, Video Marketing & Social Media</title>
<meta name="description" content="MKDMAP - Zhvillim Web, Video Marketing dhe Menaxhim i Rrjeteve Sociale për biznese në Evropë dhe Ballkan."/>
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ctext y='.9em' font-size='90'%3E%F0%9F%9A%80%3C/text%3E%3C/svg%3E"/>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cormorant+Garamond:wght@300;400;500&family=DM+Serif+Display&family=Playfair+Display:wght@500;600;700&family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#000000;
  --white:#ffffff;
  --off:#f2f2f2;
  --blue:#3B82F6;
  --blue-dark:#2563EB;
  --gray:#8a8a8a;
  --gray-light:#c9c9c9;
  --green:#5E9C3E;
  --radius:18px;
}
html{scroll-behavior:smooth;overflow-x:hidden;width:100%}
body{background:var(--bg);color:var(--white);font-family:'Poppins',sans-serif;font-weight:400;overflow-x:hidden;line-height:1.65}
img,svg{max-width:100%;display:block}
a{color:inherit;text-decoration:none}
ul{list-style:none}
section{position:relative}
.container{max-width:1280px;margin:0 auto;padding:0 2rem}

/* NOISE OVERLAY */
.noise{position:fixed;inset:0;z-index:5;pointer-events:none;opacity:.045;mix-blend-mode:overlay;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E")}

/* ══════════════ NAV ══════════════ */
.nav{position:fixed;top:0;left:0;right:0;z-index:300;display:flex;align-items:center;justify-content:space-between;padding:1.1rem 3rem;background:rgba(0,0,0,.45);backdrop-filter:blur(14px);border-bottom:1px solid rgba(255,255,255,.06);transition:background .3s,border-color .3s}
.nav.scrolled{background:rgba(0,0,0,.85);border-color:rgba(255,255,255,.1)}
.nav-logo{display:flex;align-items:center;gap:.5rem;font-family:'Bebas Neue','Arial Narrow',sans-serif;font-weight:400;font-size:1.6rem;letter-spacing:.12em;color:#fff}
.nav-badge{width:17px;height:17px;flex-shrink:0}
.nav-links{display:flex;align-items:center;gap:2.1rem}
.nav-links a{font-size:.85rem;font-weight:500;color:var(--gray-light);transition:color .25s}
.nav-links a:hover{color:var(--blue)}
.nav-cta{background:var(--blue);color:#fff !important;padding:.6rem 1.4rem;border-radius:999px;font-weight:600;font-size:.82rem;transition:background .25s,transform .25s}
.nav-cta:hover{background:var(--blue-dark);transform:translateY(-2px)}
.nav-toggle{display:none;flex-direction:column;gap:5px;background:none;border:none;cursor:pointer;padding:6px;z-index:310}
.nav-toggle span{width:22px;height:2px;background:#fff;border-radius:2px;transition:transform .25s,opacity .25s}
.nav-toggle.open span:nth-child(1){transform:translateY(7px) rotate(45deg)}
.nav-toggle.open span:nth-child(2){opacity:0}
.nav-toggle.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg)}

/* ══════════════ HERO ══════════════ */
.hero{min-height:100vh;display:flex;align-items:center;padding:7rem 0 3rem;overflow:hidden}
.blob{position:absolute;z-index:1;pointer-events:none;fill:#fff}
.blob-tl{top:-90px;left:-110px;width:380px;display:none}
.blob-br{bottom:-110px;right:-130px;width:420px;transform:rotate(180deg);display:none}

.hero-grid{display:grid;grid-template-columns:1.05fr 1fr;gap:2rem;align-items:start;max-width:1280px;margin:0 auto;padding:0 3rem;width:100%;position:relative;z-index:2}
.hero-text{display:flex;flex-direction:column;gap:2.1rem}
.logo-row{display:flex;align-items:flex-start;gap:.9rem;max-width:100%;min-width:0}
.logo{font-family:'Bebas Neue','Arial Narrow',sans-serif;font-weight:400;font-size:clamp(2.7rem,9.5vw,5.8rem);letter-spacing:.05em;line-height:1;
  background:linear-gradient(120deg,#ffffff 0%,#fbfcfd 22%,#eef1f5 42%,#ffffff 52%,#f1f4f7 70%,#ffffff 100%);
  background-size:220% auto;
  -webkit-background-clip:text;background-clip:text;
  -webkit-text-fill-color:transparent;color:#ffffff;
  filter:drop-shadow(0 3px 18px rgba(255,255,255,.16));
  opacity:0;transform:translateY(24px);
  animation:fadeUp .8s .1s cubic-bezier(.16,1,.3,1) forwards, sheen 7s linear 1s infinite;min-width:0}
@keyframes sheen{to{background-position:220% center}}
.badge{width:clamp(26px,4vw,42px);height:clamp(26px,4vw,42px);margin-top:.35rem;flex-shrink:0;animation:badgePulse 3s ease-in-out infinite,fadeUp .8s .3s cubic-bezier(.16,1,.3,1) forwards;opacity:0}
@keyframes badgePulse{0%,100%{transform:scale(1)}50%{transform:scale(1.12)}}
@keyframes fadeUp{to{opacity:1;transform:translateY(0)}}

.services-list{font-family:'Playfair Display',Georgia,'Times New Roman',serif;font-weight:600;font-size:clamp(1rem,3.6vw,1.7rem);letter-spacing:.01em;color:var(--off);display:flex;flex-direction:column;gap:.3rem}
.services-list p{opacity:0;transform:translateX(-16px);animation:slideIn .7s cubic-bezier(.16,1,.3,1) forwards;max-width:100%}
.services-list p:nth-child(1){animation-delay:.45s}
.services-list p:nth-child(2){animation-delay:.6s}
.services-list p:nth-child(3){animation-delay:.75s}
@keyframes slideIn{to{opacity:1;transform:translateX(0)}}

.tagline{font-family:'DM Serif Display',serif;font-size:clamp(1.05rem,4vw,1.7rem);color:var(--off);max-width:34ch;opacity:0;animation:fadeUp .8s .95s cubic-bezier(.16,1,.3,1) forwards}

/* directory hero copy */
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
.directory-title{font-family:'Cormorant Garamond','Playfair Display',serif;font-weight:300;font-size:clamp(1.45rem,4.6vw,2.7rem);letter-spacing:.02em;line-height:1.16;color:#fff;max-width:20ch;opacity:0;animation:fadeIn 1.1s .5s ease forwards}
.directory-sub{font-weight:400;font-size:clamp(.92rem,2.5vw,1.1rem);color:var(--gray-light);max-width:44ch;line-height:1.6;opacity:0;animation:fadeIn 1.1s .85s ease forwards}
.hero-actions{display:flex;flex-direction:column;align-items:flex-start;gap:1.3rem;margin-top:.5rem;opacity:0;animation:fadeIn 1.1s 1.2s ease forwards}
.hero-contact{display:flex;flex-wrap:wrap;gap:.7rem 1.8rem;align-items:center}
.contact-line{display:inline-flex;align-items:center;gap:.6rem;color:var(--gray-light);font-size:.95rem;font-weight:500;transition:color .2s}
.contact-line:hover{color:#fff}
.contact-line .ci{display:inline-flex;width:34px;height:34px;align-items:center;justify-content:center;border-radius:9px;background:rgba(255,255,255,.06);color:var(--blue);font-size:1rem;flex-shrink:0}

.hero-cta{display:flex;gap:1rem;flex-wrap:wrap;margin-top:.3rem;opacity:0;animation:fadeUp .8s 1.1s cubic-bezier(.16,1,.3,1) forwards}
.btn{padding:.85rem 1.9rem;border-radius:999px;font-weight:600;font-size:.9rem;transition:all .25s;border:2px solid transparent;display:inline-flex;align-items:center;gap:.4rem;cursor:pointer}
.btn-primary{background:var(--blue);color:#fff}
.btn-primary:hover{background:var(--blue-dark);transform:translateY(-3px)}
.btn-outline{border-color:rgba(255,255,255,.25);color:#fff}
.btn-outline:hover{border-color:var(--blue);color:var(--blue)}

/* LIZARD STAGE */
.lizard-stage{position:relative;display:flex;justify-content:center;align-items:center;z-index:2;perspective:1400px}
.lizard-stage::before{content:'';position:absolute;width:75%;height:75%;background:radial-gradient(circle,rgba(59,130,246,.30),transparent 70%);filter:blur(50px);z-index:-1}
.lizard-3d{width:100%;max-width:620px;transform-style:preserve-3d;animation:idleTilt 9s ease-in-out infinite;transition:transform .4s ease-out;will-change:transform}
@keyframes idleTilt{0%,100%{transform:rotateY(-8deg) rotateX(3deg)}50%{transform:rotateY(8deg) rotateX(-3deg)}}
.lizard{display:block;width:100%;height:auto;filter:drop-shadow(0 30px 35px rgba(0,0,0,.55))}

#lizard-group{transform-box:fill-box;animation:bob 3.4s ease-in-out infinite}
@keyframes bob{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}

#tail{transform-box:fill-box;transform-origin:0% 50%;animation:tailSway 2.8s ease-in-out infinite}
@keyframes tailSway{0%,100%{transform:rotate(-7deg)}50%{transform:rotate(7deg)}}

.leg{transform-box:fill-box;transform-origin:50% 0%}
.leg-a{animation:legA 1.3s ease-in-out infinite}
.leg-b{animation:legB 1.3s ease-in-out infinite}
@keyframes legA{0%,100%{transform:rotate(-9deg)}50%{transform:rotate(9deg)}}
@keyframes legB{0%,100%{transform:rotate(9deg)}50%{transform:rotate(-9deg)}}

#spikes{transform-box:fill-box;transform-origin:50% 100%;animation:spikeFlex 3.4s ease-in-out infinite;fill:#E8F5D8}
@keyframes spikeFlex{0%,100%{transform:scaleY(1)}50%{transform:scaleY(1.08)}}

#pupil{transform-box:fill-box;transform-origin:50% 50%;animation:blink 4.5s ease-in-out infinite}
@keyframes blink{0%,90%,100%{transform:scaleY(1)}94%{transform:scaleY(.1)}}

#tongue{transform-box:fill-box;transform-origin:100% 50%;opacity:0;animation:tongue 5s ease-in-out infinite}
@keyframes tongue{0%,85%,100%{opacity:0;transform:scaleX(0)}88%,93%{opacity:1;transform:scaleX(1)}}

.scroll-cue{position:absolute;bottom:1.6rem;left:50%;transform:translateX(-50%);z-index:3;display:flex;flex-direction:column;align-items:center;gap:.4rem;color:var(--gray-light);font-size:.7rem;letter-spacing:.2em;text-transform:uppercase;animation:cueBounce 2.4s ease-in-out infinite}
@keyframes cueBounce{0%,100%{transform:translate(-50%,0)}50%{transform:translate(-50%,8px)}}

/* ══════════════ SHARED SECTION STYLES ══════════════ */
.section-tag{font-size:.78rem;letter-spacing:.22em;text-transform:uppercase;color:var(--blue);font-weight:600;margin-bottom:.7rem}
.section-title{font-weight:800;font-size:clamp(2rem,5vw,3.1rem);margin-bottom:1.2rem}
.brand-mark{color:#fff;font-weight:800;letter-spacing:.04em}
.section-lead{color:var(--gray-light);max-width:60ch;margin-bottom:3rem;font-size:1.02rem}

.reveal{opacity:0;transform:translateY(34px);transition:opacity .8s ease,transform .8s ease}
.reveal.in{opacity:1;transform:none}

/* ══════════════ SERVICES ══════════════ */
.services{padding:6.5rem 0;background:#070707;border-top:1px solid rgba(255,255,255,.05);border-bottom:1px solid rgba(255,255,255,.05)}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1.6rem}
.card{background:linear-gradient(160deg,rgba(255,255,255,.05),rgba(255,255,255,.012));border:1px solid rgba(255,255,255,.08);border-radius:var(--radius);padding:2.3rem;transition:transform .35s,border-color .35s}
.card:hover{transform:translateY(-8px);border-color:var(--blue)}
.card-icon{width:54px;height:54px;border-radius:14px;background:var(--blue);display:flex;align-items:center;justify-content:center;font-size:1.6rem;margin-bottom:1.5rem}
.card h3{font-size:1.25rem;margin-bottom:.8rem;font-weight:700}
.card p{color:var(--gray-light);font-size:.95rem}

/* ══════════════ ABOUT ══════════════ */
.about{padding:6.5rem 0}
.about-grid{display:grid;grid-template-columns:1.1fr 1fr;gap:3.5rem;align-items:center}
.about p{color:var(--gray-light);margin-bottom:1.1rem;max-width:54ch}
.stats{display:grid;grid-template-columns:repeat(2,1fr);gap:1.8rem 1.4rem}
.stat{border-left:2px solid var(--blue);padding-left:1rem}
.stat-num{font-weight:800;font-size:clamp(1.8rem,4vw,2.6rem);color:#fff;display:block}
.stat-label{font-size:.85rem;color:var(--gray-light)}

/* ══════════════ PROCESS ══════════════ */
.process{padding:6.5rem 0;background:#070707;border-top:1px solid rgba(255,255,255,.05);border-bottom:1px solid rgba(255,255,255,.05)}
.steps{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:1.6rem}
.step{position:relative;padding:2.2rem 1.7rem;border:1px solid rgba(255,255,255,.08);border-radius:var(--radius);overflow:hidden;transition:border-color .3s,transform .3s}
.step:hover{border-color:var(--blue);transform:translateY(-6px)}
.step-num{font-weight:800;font-size:2.8rem;color:rgba(255,255,255,.08);position:absolute;top:.6rem;right:1.2rem;line-height:1}
.step h3{font-size:1.1rem;font-weight:700;margin-bottom:.6rem;position:relative;z-index:1}
.step p{color:var(--gray-light);font-size:.92rem;position:relative;z-index:1}

/* ══════════════ CONTACT ══════════════ */
.contact{padding:6.5rem 0}
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem}
.form input,.form textarea{width:100%;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.12);border-radius:12px;padding:.9rem 1.1rem;color:#fff;font-family:inherit;font-size:.92rem;margin-bottom:1rem;transition:border-color .25s}
.form input:focus,.form textarea:focus{outline:none;border-color:var(--blue)}
.form textarea{resize:vertical;min-height:120px}
.contact-info{display:flex;flex-direction:column;justify-content:center}
.contact-info p{color:var(--gray-light);margin-bottom:1.6rem;max-width:46ch}
.contact-info a{display:flex;align-items:center;gap:.7rem;margin-bottom:1rem;color:var(--off);font-weight:500;transition:color .2s}
.contact-info a:hover{color:var(--blue)}
.contact-info .ic{width:38px;height:38px;border-radius:10px;background:rgba(255,255,255,.06);display:flex;align-items:center;justify-content:center;font-size:1.05rem;flex-shrink:0}

/* ══════════════ FOOTER ══════════════ */
footer{padding:3rem 0;border-top:1px solid rgba(255,255,255,.06)}
.footer-grid{display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:1.4rem}
.footer-logo{display:flex;align-items:center;gap:.5rem;font-family:'Bebas Neue','Arial Narrow',sans-serif;font-weight:400;font-size:1.4rem;letter-spacing:.12em;color:#fff}
.footer-badge{width:15px;height:15px}
footer .nav-links a{color:var(--gray)}
.footer-copy{color:var(--gray);font-size:.8rem}

/* ══════════════ RESPONSIVE ══════════════ */
@media (max-width:980px){
  .hero-grid{grid-template-columns:1.2fr .8fr;text-align:left;gap:1rem;align-items:start}
  .hero{padding-top:6.5rem;min-height:auto}
  .logo-row,.services-list,.hero-cta{align-items:flex-start;justify-content:flex-start}
  .logo-row{justify-content:flex-start}
  .tagline{margin:0}
  .lizard-3d{max-width:440px;margin-top:0}
  .about-grid,.contact-grid{grid-template-columns:1fr;gap:2.5rem}
}
@media (max-width:860px){
  .nav{padding:1rem 1.4rem}
  .nav-toggle{display:flex}
  .nav-links{position:fixed;top:64px;left:0;right:0;flex-direction:column;align-items:flex-start;background:#000;padding:1.6rem 2rem;gap:1.2rem;border-bottom:1px solid rgba(255,255,255,.08);transform:translateY(-110%);opacity:0;transition:all .3s;pointer-events:none}
  .nav-links.open{transform:translateY(0);opacity:1;pointer-events:auto}
  .nav-cta{display:inline-block;text-align:center;width:100%}
  .footer-grid{flex-direction:column;text-align:center}
}
@media (max-width:560px){
  .container{padding:0 1.1rem}
  .hero{padding-top:6rem;padding-bottom:2rem}
  .hero-grid{padding:0 1.1rem;gap:1.4rem}
  .hero-text{gap:1.5rem}
  .logo-row{gap:.55rem}
  .logo{font-size:clamp(1.8rem,8.5vw,2.7rem)}
  .badge{margin-top:.2rem;width:clamp(22px,5vw,30px);height:clamp(22px,5vw,30px)}
  .blob-tl{width:220px;top:-70px;left:-90px;opacity:.7}
  .blob-br{width:260px}
  .services-list{font-size:clamp(.9rem,4.2vw,1.15rem);gap:.25rem}
  .tagline{font-size:clamp(.95rem,4.2vw,1.15rem);max-width:30ch}
  .hero-cta{gap:.7rem;margin-top:.1rem}
  .btn{padding:.75rem 1.5rem;font-size:.85rem}
  .section-title{font-size:clamp(1.6rem,7vw,2.2rem)}
  .section-lead{margin-bottom:2.2rem;font-size:.95rem}
  .services,.about,.process,.contact{padding:4.2rem 0}
  .card{padding:1.7rem}
  .stats{grid-template-columns:1fr 1fr;gap:1.4rem 1rem}
  .stat-num{font-size:clamp(1.5rem,6vw,2rem)}
}
@media (max-width:400px){
  .container{padding:0 .9rem}
  .hero-grid{padding:0 .9rem;gap:.7rem}
  .logo{font-size:clamp(1.55rem,8vw,2.2rem)}
  .services-list{font-size:clamp(.78rem,4.2vw,.95rem)}
  .tagline{font-size:.88rem}
  .hero-cta .btn{width:100%;justify-content:center}
  .stats{grid-template-columns:1fr}
}

/* ══════════════ HERO BACKGROUND CANVAS (stars fill whole page) ══════════════ */
.hero{background:#000}
.hero-canvas{position:absolute;inset:0;width:100%;height:100%;z-index:1;display:block;pointer-events:none}
.hero-grid{position:relative;z-index:2}
.hero-spacer{min-height:clamp(300px,44vh,520px)}
@media (max-width:980px){.hero-spacer{min-height:clamp(260px,40vh,380px)}}
@media (max-width:560px){.hero-spacer{min-height:clamp(220px,34vh,300px)}}
</style>
</head>
<body>
<div class="noise"></div>

<header class="nav" id="siteNav">
  <a href="#top" class="nav-logo">MKDMAP
    <svg class="nav-badge" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
      <polygon points="50,0 60.1,12.3 75,6.7 77.6,22.4 93.3,25 87.7,39.9 100,50 87.7,60.1 93.3,75 77.6,77.6 75,93.3 60.1,87.7 50,100 39.9,87.7 25,93.3 22.4,77.6 6.7,75 12.3,60.1 0,50 12.3,39.9 6.7,25 22.4,22.4 25,6.7 39.9,12.3" fill="#3B82F6"/>
      <path d="M28 52 L42 66 L74 32" stroke="#fff" stroke-width="9" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </a>
  <nav class="nav-links" id="navLinks">
    <a href="#sherbimet">Shërbimet</a>
    <a href="#procesi">Procesi</a>
    <a href="#rreth-nesh">Rreth Nesh</a>
    <a href="#kontakt">Kontakt</a>
    <a href="#kontakt" class="nav-cta">Fillo Projektin</a>
  </nav>
  <button class="nav-toggle" id="navToggle" aria-label="Menu"><span></span><span></span><span></span></button>
</header>

<!-- ══════════════ HERO ══════════════ -->
<section class="hero" id="top">
  <canvas id="rocketCanvas" class="hero-canvas"></canvas>

  <div class="hero-grid">
    <div class="hero-text">
      <div class="logo-row">
        <h1 class="logo">MKDMAP</h1>
        <svg class="badge" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <polygon points="50,0 60.1,12.3 75,6.7 77.6,22.4 93.3,25 87.7,39.9 100,50 87.7,60.1 93.3,75 77.6,77.6 75,93.3 60.1,87.7 50,100 39.9,87.7 25,93.3 22.4,77.6 6.7,75 12.3,60.1 0,50 12.3,39.9 6.7,25 22.4,22.4 25,6.7 39.9,12.3" fill="#3B82F6"/>
          <path d="M28 52 L42 66 L74 32" stroke="#fff" stroke-width="9" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>

      <p class="directory-title">Direktoria e Bizneseve në Maqedoni</p>

      <p class="directory-sub">Në ndihmë të Qytetarëve, Bizneseve dhe turistëve të Republikës së Maqedonisë</p>

      <div class="hero-actions">
        <a href="mailto:mkdmapx@gmail.com?subject=Listo%20Biznesin%20tim" class="btn btn-primary">Listo Biznesin tënd</a>
        <div class="hero-contact">
          <a href="mailto:mkdmapx@gmail.com" class="contact-line"><span class="ci">✉</span> mkdmapx@gmail.com</a>
          <a href="tel:+38970878227" class="contact-line"><span class="ci">☎</span> 070 878 227</a>
        </div>
      </div>
    </div>

    <div class="hero-spacer" aria-hidden="true"></div>
  </div>

  <div class="scroll-cue">Zbrit ↓</div>
</section>

<!-- ══════════════ SERVICES ══════════════ -->
<section class="services" id="sherbimet">
  <div class="container reveal">
    <p class="section-tag">Çka Ofrojmë</p>
    <h2 class="section-title">Shërbimet Tona</h2>
    <p class="section-lead">Ndihmojmë bizneset evropiane dhe ballkanike të rrisin praninë e tyre online me zgjidhje digjitale moderne, të shpejta dhe efektive.</p>
    <div class="cards">
      <div class="card">
        <div class="card-icon">🌐</div>
        <h3>Zhvillim Web</h3>
        <p>Krijojmë faqe interneti moderne, të shpejta dhe responsive — nga landing pages deri te platforma e-commerce, të optimizuara për konvertim dhe SEO.</p>
      </div>
      <div class="card">
        <div class="card-icon">🎬</div>
        <h3>Video Marketing</h3>
        <p>Prodhojmë dhe montojmë video profesionale për reklama, social media dhe storytelling që e bëjnë brendin tuaj të dallohet dhe rrit shitjet.</p>
      </div>
      <div class="card">
        <div class="card-icon">📱</div>
        <h3>Menaxhim i Rrjeteve Sociale</h3>
        <p>Strategji content-i, dizajn grafik, postime të rregullta dhe rritje organike për Instagram, Facebook, TikTok dhe LinkedIn.</p>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════ ABOUT ══════════════ -->
<section class="about" id="rreth-nesh">
  <div class="container about-grid reveal">
    <div>
      <p class="section-tag">Rreth Nesh</p>
      <h2 class="section-title">Pse <span class="brand-mark">MKDMAP</span>?</h2>
      <p>Jemi një ekip i vogël, por i fokusuar, që punon ekskluzivisht me biznese nga Evropa dhe Ballkani.</p>
      <p>Kombinojmë dizajn modern, teknologji të fundit dhe strategji marketingu për të sjellë rezultate reale — më shumë klientë, më shumë shitje, brand më i fortë.</p>
    </div>
    <div class="stats">
      <div class="stat"><span class="stat-num">30+</span><span class="stat-label">Projekte të Realizuara</span></div>
      <div class="stat"><span class="stat-num">15+</span><span class="stat-label">Klientë të Kënaqur</span></div>
      <div class="stat"><span class="stat-num">6</span><span class="stat-label">Vende të Mbuluara</span></div>
      <div class="stat"><span class="stat-num">100%</span><span class="stat-label">Përkushtim &amp; Cilësi</span></div>
    </div>
  </div>
</section>

<!-- ══════════════ PROCESS ══════════════ -->
<section class="process" id="procesi">
  <div class="container reveal">
    <p class="section-tag">Si Punojmë</p>
    <h2 class="section-title">Procesi Ynë</h2>
    <p class="section-lead">Një proces i thjeshtë, transparent dhe i fokusuar te rezultatet — nga ideja e parë deri te lançimi dhe rritja vazhduese.</p>
    <div class="steps">
      <div class="step">
        <span class="step-num">01</span>
        <h3>Konsultim &amp; Analizë</h3>
        <p>Mësojmë biznesin tuaj, qëllimet dhe audiencën para se të nisim çdo projekt.</p>
      </div>
      <div class="step">
        <span class="step-num">02</span>
        <h3>Strategji &amp; Dizajn</h3>
        <p>Krijojmë konceptin vizual dhe planin e përmbajtjes së përshtatur për brendin tuaj.</p>
      </div>
      <div class="step">
        <span class="step-num">03</span>
        <h3>Zhvillim &amp; Prodhim</h3>
        <p>Ndërtojmë faqen, prodhojmë videot dhe përgatisim përmbajtjen për rrjetet sociale.</p>
      </div>
      <div class="step">
        <span class="step-num">04</span>
        <h3>Lançim &amp; Rritje</h3>
        <p>Publikojmë, monitorojmë performancën dhe optimizojmë vazhdimisht për rezultate më të mira.</p>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════ CONTACT ══════════════ -->
<section class="contact" id="kontakt">
  <div class="container contact-grid reveal">
    <div>
      <p class="section-tag">Kontakt</p>
      <h2 class="section-title">Le të Fillojmë Projektin</h2>
      <form class="form" id="contactForm">
        <input type="text" name="name" placeholder="Emri" required/>
        <input type="email" name="email" placeholder="Email" required/>
        <textarea name="message" placeholder="Më trego pak për biznesin tuaj..." required></textarea>
        <button type="submit" class="btn btn-primary">Dërgo Mesazhin</button>
      </form>
    </div>
    <div class="contact-info">
      <p>Na shkruani disa fjalë për biznesin tuaj — kthehemi shpejt me një plan të përshtatur për ju.</p>
      <a href="mailto:hello@mkdmap.com"><span class="ic">✉️</span> hello@mkdmap.com</a>
      <a href="#"><span class="ic">📷</span> @mkdmap</a>
      <a href="#"><span class="ic">💼</span> MKDMAP on LinkedIn</a>
    </div>
  </div>
</section>

<!-- ══════════════ FOOTER ══════════════ -->
<footer>
  <div class="container footer-grid">
    <a href="#top" class="footer-logo">MKDMAP
      <svg class="footer-badge" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
        <polygon points="50,0 60.1,12.3 75,6.7 77.6,22.4 93.3,25 87.7,39.9 100,50 87.7,60.1 93.3,75 77.6,77.6 75,93.3 60.1,87.7 50,100 39.9,87.7 25,93.3 22.4,77.6 6.7,75 12.3,60.1 0,50 12.3,39.9 6.7,25 22.4,22.4 25,6.7 39.9,12.3" fill="#3B82F6"/>
        <path d="M28 52 L42 66 L74 32" stroke="#fff" stroke-width="9" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </a>
    <nav class="nav-links">
      <a href="#sherbimet">Shërbimet</a>
      <a href="#procesi">Procesi</a>
      <a href="#rreth-nesh">Rreth Nesh</a>
      <a href="#kontakt">Kontakt</a>
    </nav>
    <p class="footer-copy">© 2026 MKDMAP. Të gjitha të drejtat e rezervuara.</p>
  </div>
</footer>

<script>
// nav background on scroll
const siteNav = document.getElementById('siteNav');
window.addEventListener('scroll', () => {
  siteNav.classList.toggle('scrolled', window.scrollY > 40);
});

// mobile menu toggle
const navToggle = document.getElementById('navToggle');
const navLinks = document.getElementById('navLinks');
navToggle.addEventListener('click', () => {
  navToggle.classList.toggle('open');
  navLinks.classList.toggle('open');
});
navLinks.querySelectorAll('a').forEach(a => a.addEventListener('click', () => {
  navToggle.classList.remove('open');
  navLinks.classList.remove('open');
}));

// scroll reveal
const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => { if (entry.isIntersecting) entry.target.classList.add('in'); });
}, { threshold: .15 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));


// contact form -> mailto
document.getElementById('contactForm').addEventListener('submit', e => {
  e.preventDefault();
  const data = new FormData(e.target);
  const subject = encodeURIComponent('Projekt i ri nga ' + data.get('name'));
  const body = encodeURIComponent(data.get('message') + '\n\nEmail: ' + data.get('email'));
  window.location.href = `mailto:hello@mkdmap.com?subject=${subject}&body=${body}`;
});
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
(function(){
  if(!window.THREE){ return; }
  var canvas = document.getElementById('rocketCanvas');
  if(!canvas) return;
  var stage = canvas.parentElement;
  var mobile = Math.min(window.innerWidth, window.innerHeight) < 760;
  var reduce = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  var renderer = new THREE.WebGLRenderer({ canvas: canvas, antialias: true, alpha: true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.setClearColor(0x000000, 0);

  var scene = new THREE.Scene();
  scene.fog = new THREE.FogExp2(0x000000, 0.02);
  var camera = new THREE.PerspectiveCamera(50, 1, 0.1, 120);
  camera.position.set(0, 0, 6);
  var camBaseY = 0;

  // soft round dot
  function discTexture(){
    var c = document.createElement('canvas'); c.width = c.height = 64;
    var x = c.getContext('2d');
    var g = x.createRadialGradient(32,32,0,32,32,32);
    g.addColorStop(0,'rgba(255,255,255,1)');
    g.addColorStop(0.22,'rgba(255,255,255,0.92)');
    g.addColorStop(0.55,'rgba(255,255,255,0.28)');
    g.addColorStop(1,'rgba(255,255,255,0)');
    x.fillStyle = g; x.fillRect(0,0,64,64);
    return new THREE.CanvasTexture(c);
  }
  var sprite = discTexture();

  function glowSprite(hex, opacity){
    var m = new THREE.SpriteMaterial({ map:sprite, color:new THREE.Color(hex), transparent:true,
            depthWrite:false, blending:THREE.AdditiveBlending, opacity:opacity });
    return new THREE.Sprite(m);
  }

  // ---------- build the rocket from points ----------
  var P = [], C = [];
  // warm "stardust" palette (matches the reference video)
  var paleGold  = new THREE.Color('#ffe9b0');
  var gold      = new THREE.Color('#ffb43a');
  var amber     = new THREE.Color('#ff7a1a');
  var amberDeep = new THREE.Color('#c2400a');
  var win       = new THREE.Color('#48e6ff');   // bright cyan porthole
  var winRing   = new THREE.Color('#1b9dff');
  var nozzleCol = new THREE.Color('#9a5a2a');
  // legacy aliases so the rest of the build keeps working, now warm-toned
  var white     = paleGold;
  var lightBlue = gold;
  var blue      = amber;
  var deepBlue  = amberDeep;
  function push(x,y,z,col){ P.push(x,y,z); C.push(col.r,col.g,col.b); }
  function mix(a,b,t){ return a.clone().lerp(b,t); }

  var R = 0.46, H = 2.0;
  var i, a, y, t, r, col;

  // body shell
  var bodyN = mobile ? 2600 : 4200;
  for(i=0;i<bodyN;i++){
    a = Math.random()*Math.PI*2; y = Math.random()*H;
    col = mix(white, lightBlue, Math.random()*0.55);
    push(Math.cos(a)*R, y, Math.sin(a)*R, col);
  }
  // panel seam rings (crisper, brighter)
  var seams = [0.30,0.66,1.02,1.40,1.76];
  for(var s=0;s<seams.length;s++){
    var ringN = mobile ? 120 : 200;
    for(i=0;i<ringN;i++){
      a = Math.random()*Math.PI*2;
      push(Math.cos(a)*R*1.004, seams[s] + (Math.random()-0.5)*0.012, Math.sin(a)*R*1.004, white);
    }
  }
  // blue accent band
  var bandN = mobile ? 320 : 520;
  for(i=0;i<bandN;i++){
    a = Math.random()*Math.PI*2; y = 1.04 + Math.random()*0.22;
    push(Math.cos(a)*R*1.006, y, Math.sin(a)*R*1.006, blue);
  }

  // smooth elliptical nose
  var noseN = mobile ? 1000 : 1500;
  for(i=0;i<noseN;i++){
    t = Math.pow(Math.random(),0.6); a = Math.random()*Math.PI*2;
    y = H + 0.95*t; r = R*Math.sqrt(Math.max(0,1 - t*t));
    push(Math.cos(a)*r, y, Math.sin(a)*r, mix(blue, deepBlue, t*0.6));
  }
  // nose tip accent
  for(i=0;i<70;i++){
    a = Math.random()*Math.PI*2; r = Math.random()*0.05;
    push(Math.cos(a)*r, H+0.92+Math.random()*0.05, Math.sin(a)*r, white);
  }

  // four swept fins
  function fin(rot){
    var v0x=R, v0y=0.62, v1x=R, v1y=0.0, v2x=R+0.46, v2y=-0.10, k, u, w, px, py, X, Z;
    var fn = mobile ? 330 : 520;
    for(k=0;k<fn;k++){
      u=Math.random(); w=Math.random();
      if(u+w>1){ u=1-u; w=1-w; }
      px = v0x + (v1x-v0x)*u + (v2x-v0x)*w;
      py = v0y + (v1y-v0y)*u + (v2y-v0y)*w;
      X = px*Math.cos(rot); Z = px*Math.sin(rot);
      push(X, py, Z, mix(blue, deepBlue, 0.3));
    }
  }
  fin(0); fin(Math.PI/2); fin(Math.PI); fin(Math.PI*1.5);

  // porthole window (bright cyan core + blue ring)
  for(i=0;i<140;i++){
    var ang = Math.random()*Math.PI*2, rad = Math.sqrt(Math.random())*0.12;
    push(Math.cos(ang)*rad, 1.30 + Math.sin(ang)*rad, R + 0.03, win);
  }
  for(i=0;i<200;i++){
    var ang2 = Math.random()*Math.PI*2;
    push(Math.cos(ang2)*0.16, 1.30 + Math.sin(ang2)*0.16, R + 0.025, winRing);
  }

  // flared nozzle
  var nozN = mobile ? 300 : 440;
  for(i=0;i<nozN;i++){
    t = Math.random(); a = Math.random()*Math.PI*2;
    r = R*0.66*(1 + t*0.6); y = -0.02 - 0.18*t;
    push(Math.cos(a)*r, y, Math.sin(a)*r, nozzleCol);
  }

  // loose stardust halo — sparse glowing motes drifting off the hull
  var dustN = mobile ? 900 : 1500;
  for(i=0;i<dustN;i++){
    a = Math.random()*Math.PI*2;
    y = -0.2 + Math.random()*(H+1.0);
    // distance from surface, biased close but with a long sparse tail outward
    var d = R*1.02 + Math.pow(Math.random(),2.2)*1.5;
    var hcol = mix(gold, amber, Math.random());
    if(Math.random()<0.22) hcol = mix(amber, amberDeep, Math.random());
    if(Math.random()<0.12) hcol = paleGold;
    push(Math.cos(a)*d, y + (Math.random()-0.5)*0.5, Math.sin(a)*d, hcol);
  }

  var rgeo = new THREE.BufferGeometry();
  rgeo.setAttribute('position', new THREE.Float32BufferAttribute(P, 3));
  rgeo.setAttribute('color', new THREE.Float32BufferAttribute(C, 3));
  var rmat = new THREE.PointsMaterial({
    size: mobile ? 0.055 : 0.05, map: sprite, vertexColors: true, transparent: true,
    depthWrite: false, blending: THREE.AdditiveBlending, sizeAttenuation: true, opacity: 0
  });
  var rocketPoints = new THREE.Points(rgeo, rmat);

  // ---------- materialize: every dot starts scattered and converges into the rocket ----------
  var NP = rgeo.attributes.position.count;
  var targetPos = new Float32Array(rgeo.attributes.position.array); // the finished rocket shape
  var scatterPos = new Float32Array(NP*3);
  var pDelay = new Float32Array(NP);
  for(var mp=0; mp<NP; mp++){
    var mth = Math.random()*Math.PI*2;
    var mph = Math.acos(2*Math.random()-1);
    var mdist = reduce ? 0 : (1.6 + Math.pow(Math.random(),1.6)*3.4); // push each dot outward in a random direction
    scatterPos[mp*3]   = targetPos[mp*3]   + Math.sin(mph)*Math.cos(mth)*mdist;
    scatterPos[mp*3+1] = targetPos[mp*3+1] + Math.cos(mph)*mdist;
    scatterPos[mp*3+2] = targetPos[mp*3+2] + Math.sin(mph)*Math.sin(mth)*mdist;
    pDelay[mp] = reduce ? 0 : Math.random()*0.35; // slight stagger so they don't all arrive at once
    rgeo.attributes.position.array[mp*3]   = scatterPos[mp*3];
    rgeo.attributes.position.array[mp*3+1] = scatterPos[mp*3+1];
    rgeo.attributes.position.array[mp*3+2] = scatterPos[mp*3+2];
  }
  rgeo.attributes.position.needsUpdate = true;
  var assembleT = 0, ASSEMBLE_DUR = 3.0, assembled = false;

  var rocket = new THREE.Group();
  rocket.add(rocketPoints);

  // engine flare + ignition flash + soft body bloom (move with the rocket)
  var engineFlare = glowSprite('#ff9540', 0.0); engineFlare.position.set(0,-0.16,0); rocket.add(engineFlare);
  var flash = glowSprite('#ffffff', 0.0); flash.position.set(0,-0.16,0); rocket.add(flash);
  var bodyBloom = glowSprite('#ff9a3c', 0.0); bodyBloom.position.set(0,0.95,0); bodyBloom.scale.set(2.4,3.4,1); rocket.add(bodyBloom);
  var winGlow = glowSprite('#48e6ff', 0.0); winGlow.position.set(0,1.30,R+0.05); winGlow.scale.set(0.8,0.8,1); rocketPoints.add(winGlow);

  scene.add(rocket);
  // diagonal pose, pointing up-and-to-the-right like the reference
  rocket.rotation.z = -0.52;
  rocket.rotation.x = 0.15;
  var baseY = -1.15;
  rocket.position.set(3.0, baseY, 0);

  // ---------- particle pools (world space => leave a trail) ----------
  function Pool(count, size, opacity){
    this.count=count; this.cursor=0;
    this.pos=new Float32Array(count*3); this.col=new Float32Array(count*3);
    this.life=new Float32Array(count); this.max=new Float32Array(count);
    this.vel=new Float32Array(count*3); this.grow=new Float32Array(count);
    for(var i=0;i<count;i++) this.pos[i*3+1]=9999;
    this.geo=new THREE.BufferGeometry();
    this.geo.setAttribute('position', new THREE.BufferAttribute(this.pos,3));
    this.geo.setAttribute('color', new THREE.BufferAttribute(this.col,3));
    this.mat=new THREE.PointsMaterial({ size:size, map:sprite, vertexColors:true, transparent:true,
              depthWrite:false, blending:THREE.AdditiveBlending, sizeAttenuation:true, opacity:opacity });
    this.pts=new THREE.Points(this.geo, this.mat); scene.add(this.pts);
  }
  Pool.prototype.emit=function(n,wx,wy,wz,vmin,vmax,spread,lmin,lmax,grow){
    for(var k=0;k<n;k++){
      var i=this.cursor; this.cursor=(this.cursor+1)%this.count;
      this.max[i]=lmin+Math.random()*(lmax-lmin); this.life[i]=this.max[i];
      this.vel[i*3]=(Math.random()-0.5)*spread;
      this.vel[i*3+1]=-(vmin+Math.random()*(vmax-vmin));
      this.vel[i*3+2]=(Math.random()-0.5)*spread;
      this.grow[i]=grow;
      this.pos[i*3]=wx+(Math.random()-0.5)*0.12;
      this.pos[i*3+1]=wy+(Math.random()-0.5)*0.05;
      this.pos[i*3+2]=wz+(Math.random()-0.5)*0.12;
    }
  };
  Pool.prototype.burst=function(n,wx,wy,wz,speed,lmin,lmax){
    for(var k=0;k<n;k++){
      var i=this.cursor; this.cursor=(this.cursor+1)%this.count;
      this.max[i]=lmin+Math.random()*(lmax-lmin); this.life[i]=this.max[i];
      var th=Math.random()*Math.PI*2, ph=Math.acos(2*Math.random()-1), sp=speed*(0.5+Math.random()*0.7);
      this.vel[i*3]=Math.sin(ph)*Math.cos(th)*sp;
      this.vel[i*3+1]=Math.abs(Math.cos(ph))*-0.3*sp;
      this.vel[i*3+2]=Math.sin(ph)*Math.sin(th)*sp;
      this.grow[i]=0;
      this.pos[i*3]=wx; this.pos[i*3+1]=wy; this.pos[i*3+2]=wz;
    }
  };
  Pool.prototype.update=function(dt, lo, mid, hi){
    for(var i=0;i<this.count;i++){
      if(this.life[i]>0){
        this.life[i]-=dt;
        if(this.grow[i]>0){
          this.vel[i*3]   += (this.vel[i*3]>=0?1:-1)*this.grow[i]*dt;
          this.vel[i*3+2] += (this.vel[i*3+2]>=0?1:-1)*this.grow[i]*dt;
        }
        this.pos[i*3]   += this.vel[i*3]*dt;
        this.pos[i*3+1] += this.vel[i*3+1]*dt;
        this.pos[i*3+2] += this.vel[i*3+2]*dt;
        var f=this.life[i]/this.max[i]; if(f<0)f=0;
        var rr,gg,bb,tt;
        if(f>0.5){ tt=(f-0.5)*2; rr=mid[0]+(hi[0]-mid[0])*tt; gg=mid[1]+(hi[1]-mid[1])*tt; bb=mid[2]+(hi[2]-mid[2])*tt; }
        else { tt=f*2; rr=lo[0]+(mid[0]-lo[0])*tt; gg=lo[1]+(mid[1]-lo[1])*tt; bb=lo[2]+(mid[2]-lo[2])*tt; }
        this.col[i*3]=rr; this.col[i*3+1]=gg; this.col[i*3+2]=bb;
      } else {
        this.col[i*3]=this.col[i*3+1]=this.col[i*3+2]=0;
        this.pos[i*3+1]=9999;
      }
    }
    this.geo.attributes.position.needsUpdate=true;
    this.geo.attributes.color.needsUpdate=true;
  };

  var flame = new Pool(mobile?700:1000, 0.10, 0.95);
  var plume = new Pool(mobile?800:1300, 0.20, 0.7);
  var FLAME_LO=[0.35,0.06,0.0], FLAME_MID=[1.0,0.55,0.16], FLAME_HI=[1.0,0.97,0.80];
  var PLUME_LO=[0.22,0.24,0.28], PLUME_MID=[0.62,0.66,0.74], PLUME_HI=[0.97,0.98,1.0];

  // ---------- sky: two star layers + soft nebula ----------
  function starLayer(count, size, opacity, zmin, zmax, hex){
    var pos=new Float32Array(count*3);
    var col=new Float32Array(count*3);
    var phase=new Float32Array(count);
    var tw=new Float32Array(count);
    var base=new THREE.Color(hex);
    for(var i=0;i<count;i++){
      pos[i*3]=(Math.random()-0.5)*36;
      pos[i*3+1]=(Math.random()-0.5)*30;
      pos[i*3+2]=zmin-Math.random()*(zmax-zmin);
      col[i*3]=base.r; col[i*3+1]=base.g; col[i*3+2]=base.b;
      phase[i]=Math.random()*Math.PI*2;     // each star twinkles on its own clock
      tw[i]=0.5+Math.random()*1.9;           // its own twinkle speed
    }
    var geo=new THREE.BufferGeometry();
    geo.setAttribute('position', new THREE.BufferAttribute(pos,3));
    geo.setAttribute('color', new THREE.BufferAttribute(col,3));
    var mat=new THREE.PointsMaterial({ size:size, map:sprite, vertexColors:true, transparent:true,
            opacity:opacity, depthWrite:false, blending:THREE.AdditiveBlending, sizeAttenuation:true });
    var pts=new THREE.Points(geo,mat); scene.add(pts);
    return { pos:pos, col:col, base:base, phase:phase, tw:tw, geo:geo };
  }
  // denser field so the whole sky — including behind the text — stays lit
  var starsFar    = starLayer(mobile?900:1600, 0.05,  0.6,  9, 22, '#9fbcff');
  var starsNear   = starLayer(mobile?420:780,  0.085, 0.95, 3, 11, '#dfeaff');
  var starsSparkle= starLayer(mobile?70:140,   0.12,  0.95, 1,  7, '#ffffff');

  // keep every star shining, with a soft living twinkle (never fully dark)
  function twinkle(layer, t){
    var c=layer.col, b=layer.base, ph=layer.phase, tw=layer.tw, n=ph.length;
    for(var i=0;i<n;i++){
      var f=0.55+0.45*(0.5+0.5*Math.sin(t*tw[i]+ph[i]));
      c[i*3]=b.r*f; c[i*3+1]=b.g*f; c[i*3+2]=b.b*f;
    }
    layer.geo.attributes.color.needsUpdate=true;
  }

  // (no nebula — keep the background pure black)

  // ---------- responsive framing ----------
  var rocketX = 1.6;
  function resize(){
    var w = stage.clientWidth || canvas.clientWidth || 400;
    var h = stage.clientHeight || canvas.clientHeight || 400;
    renderer.setSize(w, h, false);
    camera.aspect = w / h;
    var fr = camera.fov*Math.PI/180;
    var dH = 1.95/Math.tan(fr/2);
    var dW = 1.30/(camera.aspect*Math.tan(fr/2));
    camera.position.z = Math.max(dH, dW) * 1.45;
    camera.updateProjectionMatrix();
    // how wide is the world at the rocket's depth -> park it on the right
    var halfW = Math.tan(fr/2) * camera.position.z * camera.aspect;
    rocketX = Math.max(0, Math.min(halfW * 0.52, halfW - 2.0));
  }
  resize();
  window.addEventListener('resize', resize);
  if(window.ResizeObserver){ new ResizeObserver(resize).observe(stage); }

  // ---------- calm hover: slow spin, gentle bob, warm dust drift ----------
  var rocketAlpha=0, starSpeed=0.05, thrustVis=0.2;
  var clock = new THREE.Clock();
  var _engineWorld = new THREE.Vector3();

  function update(dt, t){
    rocket.updateMatrixWorld();

    // fade the rocket in once, then keep it present
    rocketAlpha += (1 - rocketAlpha) * Math.min(1, dt*3);
    rmat.opacity = rocketAlpha;

    // hold position on the right — no slide-in — with a gentle floating bob
    rocket.position.x = rocketX;
    rocket.position.y = baseY + 0.10*Math.sin(t*1.2);
    // slow shimmer: particles rotate around the body's long axis
    rocketPoints.rotation.y += (reduce ? 0.10 : 0.22) * dt;

    // materialize: ease the scattered dots in until they form the rocket
    if(!assembled){
      assembleT += dt / ASSEMBLE_DUR;
      if(assembleT >= 1){ assembleT = 1; assembled = true; }
      var pa = rgeo.attributes.position.array;
      for(var qi=0; qi<NP; qi++){
        var loc = (assembleT - pDelay[qi]) / (1 - pDelay[qi]);
        if(loc < 0) loc = 0; else if(loc > 1) loc = 1;
        var ee = loc < 0.5 ? 4*loc*loc*loc : 1 - Math.pow(-2*loc+2, 3)/2; // easeInOutCubic — show the spread, then gather
        var s0 = scatterPos[qi*3], s1 = scatterPos[qi*3+1], s2 = scatterPos[qi*3+2];
        pa[qi*3]   = s0 + (targetPos[qi*3]   - s0)*ee;
        pa[qi*3+1] = s1 + (targetPos[qi*3+1] - s1)*ee;
        pa[qi*3+2] = s2 + (targetPos[qi*3+2] - s2)*ee;
      }
      rgeo.attributes.position.needsUpdate = true;
    }

    // soft, steady thruster level
    thrustVis += (0.55 - thrustVis) * Math.min(1, dt*3);

    // world position of the nozzle (respects the tilt)
    _engineWorld.set(0, -0.18, 0).applyMatrix4(rocket.matrixWorld);
    var wx = _engineWorld.x, wy = _engineWorld.y, wz = _engineWorld.z;

    // warm stardust drifting off the engine + a faint haze (only once the rocket has formed)
    if(assembleT > 0.6){
      flame.emit(reduce?2:4, wx, wy, wz, 0.5, 1.2, 0.18, 0.5, 1.1, 0.25);
      plume.emit(reduce?1:2, wx, wy-0.03, wz, 0.25, 0.6, 0.22, 0.9, 1.6, 0.4);
    }
    starSpeed += (0.06 - starSpeed) * Math.min(1, dt*2);

    // engine flare + window glow + body bloom (always lit now)
    var flick = 0.9 + Math.random()*0.18;
    var es = (0.3 + 0.9*thrustVis) * flick;
    engineFlare.scale.set(es, es*1.15, 1);
    engineFlare.material.opacity = (0.25 + 0.55*thrustVis) * rocketAlpha * assembleT;
    winGlow.material.opacity = (0.55 + 0.4*Math.sin(t*2.6)) * rocketAlpha * assembleT;
    bodyBloom.material.opacity = 0.12 * rocketAlpha * assembleT;
    flash.material.opacity = 0;

    // calm camera (no shake)
    camera.position.x += (0 - camera.position.x)*0.1;
    camera.position.y += (camBaseY - camera.position.y)*0.1;
    camera.lookAt(0, 0, 0);

    // particles
    flame.update(dt, FLAME_LO, FLAME_MID, FLAME_HI);
    plume.update(dt, PLUME_LO, PLUME_MID, PLUME_HI);

    // stars (parallax: nearer layers faster)
    var sp1 = starSpeed, sp2 = starSpeed*1.7, sp3 = starSpeed*2.3;
    for(var i=0;i<starsFar.pos.length;i+=3){
      starsFar.pos[i+1] -= sp1*dt;
      if(starsFar.pos[i+1] < -15){ starsFar.pos[i+1] += 30; starsFar.pos[i] = (Math.random()-0.5)*36; }
    }
    for(var j=0;j<starsNear.pos.length;j+=3){
      starsNear.pos[j+1] -= sp2*dt;
      if(starsNear.pos[j+1] < -15){ starsNear.pos[j+1] += 30; starsNear.pos[j] = (Math.random()-0.5)*36; }
    }
    for(var k=0;k<starsSparkle.pos.length;k+=3){
      starsSparkle.pos[k+1] -= sp3*dt;
      if(starsSparkle.pos[k+1] < -15){ starsSparkle.pos[k+1] += 30; starsSparkle.pos[k] = (Math.random()-0.5)*36; }
    }
    starsFar.geo.attributes.position.needsUpdate = true;
    starsNear.geo.attributes.position.needsUpdate = true;
    starsSparkle.geo.attributes.position.needsUpdate = true;
    // continuous twinkle on every layer
    twinkle(starsFar, t);
    twinkle(starsNear, t);
    twinkle(starsSparkle, t);
  }

  function loop(){
    requestAnimationFrame(loop);
    var dt = Math.min(clock.getDelta(), 0.05);
    update(dt, clock.elapsedTime);
    renderer.render(scene, camera);
  }
  loop();
})();
</script>
</body>
</html>
