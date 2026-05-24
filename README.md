<html lang="sq">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>MKDMAP — Zbulo Maqedoninë</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,600;1,300&family=Space+Grotesk:wght@300;400;500;700&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --g:#C9A84C;--g2:#F0D070;--g3:rgba(201,168,76,0.12);--gb:rgba(201,168,76,0.3);
  --ink:#02030A;--ink2:#060810;--ink3:#0A0D1C;
  --t1:#F2EED8;--t2:rgba(242,238,216,0.55);--t3:rgba(242,238,216,0.25);--t4:rgba(242,238,216,0.1);
  --b1:rgba(255,255,255,0.07);--b2:rgba(255,255,255,0.03);
}
html{scroll-behavior:smooth}
@media(pointer:fine){html{cursor:none}}
body{background:var(--ink);color:var(--t1);font-family:'Space Grotesk',sans-serif;font-weight:300;overflow-x:hidden}

/* ── CURSOR ── */
#cur{position:fixed;width:7px;height:7px;background:var(--g);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:transform .15s,width .2s,height .2s}
#cur2{position:fixed;width:28px;height:28px;border:1px solid rgba(201,168,76,.45);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%)}
body.hov #cur{transform:translate(-50%,-50%) scale(2.5)}
body.hov #cur2{width:46px;height:46px;border-color:rgba(201,168,76,.8)}
@media(pointer:coarse){#cur,#cur2{display:none}}

/* ── LIVE 3D BACKGROUND (always on) ── */
#bg3d{position:fixed;inset:0;z-index:0;pointer-events:none}

/* ── NAV ── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:200;
  height:66px;padding:0 3rem;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(2,3,10,.85);backdrop-filter:blur(28px);
  border-bottom:1px solid var(--b1);
}
.logo-nav{font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:1.3rem;letter-spacing:.18em;color:#fff;text-decoration:none;text-transform:uppercase}
.logo-nav span{color:var(--g)}
.nav-r{display:flex;align-items:center;gap:2rem}
.na{font-size:.6rem;font-weight:400;letter-spacing:.16em;text-transform:uppercase;color:var(--t3);text-decoration:none;transition:color .2s}
.na:hover{color:var(--g)}
.lw{position:relative}
.lb{display:flex;align-items:center;gap:6px;background:var(--b2);border:1px solid var(--b1);padding:6px 14px;cursor:none;font-family:'Space Grotesk',sans-serif;font-size:.6rem;letter-spacing:.1em;color:var(--t2);transition:all .2s}
.lb:hover,.lb.open{border-color:var(--gb);color:var(--g)}
.lb svg{width:10px;transition:transform .2s}
.lb.open svg{transform:rotate(180deg)}
.ld{position:absolute;top:calc(100%+8px);right:0;background:var(--ink2);border:1px solid var(--b1);min-width:180px;display:none;flex-direction:column;z-index:50;max-height:270px;overflow-y:auto;box-shadow:0 20px 50px rgba(0,0,0,.7)}
.ld.open{display:flex}
.li{padding:8px 14px;font-size:.68rem;color:var(--t3);cursor:none;transition:all .15s;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid var(--b2)}
.li:hover{background:var(--g3);color:var(--t1)}
.li.active{color:var(--g)}

/* ══════════════════════════════
   HERO
══════════════════════════════ */
.hero{
  position:relative;z-index:1;
  min-height:100vh;display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  padding:9rem 2rem 5rem;overflow:hidden;
}

/* ── MKDMAP LOGO ANIMATION ── */
.logo-wrap{
  position:relative;margin-bottom:2.5rem;
  display:flex;flex-direction:column;align-items:center;
}
.logo-main{
  font-family:'Space Grotesk',sans-serif;
  font-weight:700;
  font-size:clamp(3.5rem,10vw,9rem);
  letter-spacing:.18em;
  line-height:1;
  position:relative;
  text-transform:uppercase;
  /* clip-path reveal animation */
  animation:logoReveal 1.2s cubic-bezier(.16,1,.3,1) .2s both;
}
@keyframes logoReveal{
  0%{clip-path:inset(0 100% 0 0);opacity:0}
  30%{opacity:1}
  100%{clip-path:inset(0 0% 0 0);opacity:1}
}

/* Each letter has layered glow effect */
.logo-main .l{
  display:inline-block;
  position:relative;
  animation:letterFloat 3s ease-in-out infinite;
  color:#fff;
  text-shadow:
    0 0 30px rgba(201,168,76,0),
    0 0 60px rgba(201,168,76,0);
  transition:text-shadow .3s;
}
.logo-main .l:nth-child(1){animation-delay:0s}
.logo-main .l:nth-child(2){animation-delay:.15s}
.logo-main .l:nth-child(3){animation-delay:.3s}
.logo-main .l:nth-child(4){animation-delay:.45s}
.logo-main .l:nth-child(5){animation-delay:.6s}
.logo-main .l:nth-child(6){animation-delay:.75s}

@keyframes letterFloat{
  0%,100%{transform:translateY(0) scale(1)}
  50%{transform:translateY(-6px) scale(1.04)}
}

/* Gold shimmer sweep on the word */
.logo-main::after{
  content:'MKDMAP';
  position:absolute;inset:0;
  font-family:inherit;font-weight:inherit;font-size:inherit;
  letter-spacing:inherit;line-height:inherit;
  background:linear-gradient(90deg,
    transparent 0%,
    transparent 30%,
    rgba(201,168,76,.9) 48%,
    rgba(240,208,112,1) 50%,
    rgba(201,168,76,.9) 52%,
    transparent 70%,
    transparent 100%
  );
  background-size:200% 100%;
  -webkit-background-clip:text;
  background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:shimmerSweep 3.5s ease-in-out infinite;
  pointer-events:none;
}
@keyframes shimmerSweep{
  0%{background-position:200% 0}
  60%,100%{background-position:-200% 0}
}

/* Orbiting ring around logo */
.logo-ring{
  position:absolute;
  width:calc(100% + 80px);
  height:calc(100% + 40px);
  left:-40px;top:-20px;
  border:1px solid rgba(201,168,76,.15);
  pointer-events:none;
  animation:ringRotate 12s linear infinite;
}
@keyframes ringRotate{from{transform:rotateX(70deg) rotateZ(0)}to{transform:rotateX(70deg) rotateZ(360deg)}}

.logo-ring2{
  position:absolute;
  width:calc(100% + 120px);
  height:calc(100% + 60px);
  left:-60px;top:-30px;
  border:1px solid rgba(201,168,76,.07);
  pointer-events:none;
  animation:ringRotate2 20s linear infinite;
}
@keyframes ringRotate2{from{transform:rotateX(70deg) rotateZ(360deg)}to{transform:rotateX(70deg) rotateZ(0)}}

/* Dot scanner */
.logo-scan{
  position:absolute;
  top:0;bottom:0;width:2px;
  background:linear-gradient(180deg,transparent,var(--g),transparent);
  filter:blur(1px);
  animation:scanLine 3.5s ease-in-out infinite;
  pointer-events:none;
}
@keyframes scanLine{
  0%{left:-10px;opacity:0}
  10%{opacity:1}
  90%{opacity:1}
  100%{left:calc(100% + 10px);opacity:0}
}

/* Tagline */
.logo-tagline{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(.85rem,1.8vw,1.25rem);
  font-style:italic;font-weight:300;
  color:var(--t2);letter-spacing:.12em;
  text-align:center;
  animation:fadeUp .8s 1.4s both;
}
.logo-tagline b{color:var(--g);font-style:normal;font-weight:400}

.hero-eyebrow{
  display:inline-flex;align-items:center;gap:12px;
  font-size:.58rem;letter-spacing:.28em;text-transform:uppercase;
  color:var(--g);margin-bottom:2rem;font-weight:400;
  animation:fadeUp .7s .1s both;
}
.hero-eyebrow::before,.hero-eyebrow::after{content:'';width:22px;height:1px;background:var(--g);opacity:.5}
.hero-desc{
  font-size:.88rem;color:var(--t2);line-height:1.9;
  max-width:480px;margin:2rem auto;font-weight:300;
  animation:fadeUp .8s 1.6s both;
  text-align:center;
}
.hero-btns{display:flex;gap:.9rem;justify-content:center;flex-wrap:wrap;animation:fadeUp .8s 1.8s both}
.bp{background:linear-gradient(135deg,var(--g) 0%,var(--g2) 50%,var(--g) 100%);background-size:200%;color:var(--ink);border:none;padding:14px 38px;font-family:'Space Grotesk',sans-serif;font-size:.7rem;letter-spacing:.16em;text-transform:uppercase;font-weight:600;cursor:pointer;transition:all .3s}
@media(pointer:fine){.bp{cursor:none}}
.bp:hover{background-position:100%;transform:translateY(-2px);box-shadow:0 14px 35px rgba(201,168,76,.3)}
.bg{background:transparent;color:var(--t2);border:1px solid var(--b1);padding:14px 38px;font-family:'Space Grotesk',sans-serif;font-size:.7rem;letter-spacing:.16em;text-transform:uppercase;cursor:none;transition:all .25s}
.bg:hover{border-color:var(--gb);color:var(--g)}

@keyframes fadeUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}

/* ── STATS ── */
.statsbar{
  position:relative;z-index:1;
  background:rgba(6,8,16,.85);backdrop-filter:blur(20px);
  border-top:1px solid var(--b1);border-bottom:1px solid var(--b1);
  padding:2.5rem 3rem;display:flex;justify-content:center;gap:0;
}
.si{flex:1;max-width:170px;text-align:center;padding:0 1.5rem;position:relative}
.si+.si::before{content:'';position:absolute;left:0;top:50%;transform:translateY(-50%);width:1px;height:40%;background:var(--b1)}
.sn{font-family:'Cormorant Garamond',serif;font-size:2.8rem;font-weight:300;color:#fff;display:block;line-height:1}
.sn em{font-style:normal;color:var(--g)}
.sl{font-size:.55rem;letter-spacing:.18em;text-transform:uppercase;color:var(--t4);margin-top:6px;display:block}

/* ══════════════════════════════
   SECTIONS
══════════════════════════════ */
.sec{position:relative;z-index:1;padding:7rem 3rem}
.si2{max-width:1200px;margin:0 auto}
.sey{font-size:.57rem;letter-spacing:.24em;text-transform:uppercase;color:var(--g);margin-bottom:.5rem}
.sh{font-family:'Cormorant Garamond',serif;font-size:clamp(1.8rem,3.5vw,3rem);font-weight:300;color:#fff;line-height:1.1;margin-bottom:.6rem}
.sh em{font-style:italic;color:var(--g)}
.sr{width:30px;height:1px;background:var(--g);opacity:.4;margin-bottom:3.5rem}

/* WHY */
.why{background:rgba(6,8,16,.7);backdrop-filter:blur(12px)}
.wgrid{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--b1);border:1px solid var(--b1)}
.wc{background:rgba(6,8,16,.9);padding:3rem 2.5rem;position:relative;overflow:hidden;transition:all .4s cubic-bezier(.16,1,.3,1)}
.wc::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,var(--g3),transparent 55%);opacity:0;transition:opacity .4s}
.wc::after{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--g),transparent);transform:scaleX(0);transition:transform .5s}
.wc:hover{transform:translateY(-4px)}
.wc:hover::before{opacity:1}
.wc:hover::after{transform:scaleX(1)}
.wc:hover .wi{transform:scale(1.1) rotate(-8deg)}
.wn{position:absolute;top:1.5rem;right:2rem;font-family:'Cormorant Garamond',serif;font-size:4.5rem;font-weight:300;color:var(--t4);line-height:1;user-select:none;transition:color .4s}
.wc:hover .wn{color:rgba(201,168,76,.1)}
.wi{font-size:2rem;display:block;margin-bottom:1.25rem;transition:transform .4s}
.wt{font-family:'Space Grotesk',sans-serif;font-size:1rem;font-weight:500;color:var(--t1);margin-bottom:.5rem;letter-spacing:.03em}
.wd{font-size:.78rem;color:var(--t2);line-height:1.9}

/* CATEGORIES */
.catsec{background:rgba(2,3,10,.6);backdrop-filter:blur(8px)}
.csrch{display:flex;border:1px solid var(--b1);background:rgba(6,8,16,.8)}
.csrch input{flex:1;background:transparent;border:none;outline:none;padding:.9rem 1.25rem;font-family:'Space Grotesk',sans-serif;font-size:.85rem;color:var(--t1);font-weight:300}
.csrch input::placeholder{color:var(--t4)}
.csrch span{padding:0 1rem;display:flex;align-items:center;color:var(--t4)}
.cgrid{display:grid;grid-template-columns:repeat(6,1fr);gap:1px;background:var(--b1);border:1px solid var(--b1);margin-top:1.5rem}
.ct{background:rgba(6,8,16,.85);padding:1.75rem 1rem 1.5rem;cursor:none;position:relative;overflow:hidden;transition:all .4s cubic-bezier(.16,1,.3,1);text-decoration:none;display:flex;flex-direction:column;align-items:center;text-align:center;border:1px solid transparent}
.ct::after{content:'';position:absolute;bottom:0;left:0;right:0;height:1.5px;background:linear-gradient(90deg,transparent,var(--g),transparent);transform:scaleX(0);transition:transform .4s}
.ct:hover{background:rgba(13,16,32,.95);border-color:var(--gb);transform:translateY(-5px) perspective(400px) rotateX(4deg);box-shadow:0 18px 45px rgba(0,0,0,.6);z-index:2}
.ct:hover::after{transform:scaleX(1)}
.ct:hover .cti{transform:scale(1.2) translateY(-3px);filter:drop-shadow(0 0 10px rgba(201,168,76,.5))}
.cti{font-size:1.6rem;margin-bottom:.75rem;display:block;transition:all .4s}
.ctn{font-size:.67rem;font-weight:500;color:var(--t1);letter-spacing:.03em;line-height:1.3}
.cts{font-size:.5rem;letter-spacing:.1em;text-transform:uppercase;color:var(--t4);margin-top:.4rem;display:block}

/* HOW */
.howsec{background:rgba(6,8,16,.7);backdrop-filter:blur(12px)}
.hgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.5rem}
.hc{background:rgba(2,3,10,.9);border:1px solid var(--b1);padding:2.75rem 2.25rem;position:relative;transition:all .4s cubic-bezier(.16,1,.3,1)}
.hc::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--g),transparent);transform:scaleX(0);transition:transform .5s}
.hc:hover{transform:translateY(-5px);border-color:var(--gb);box-shadow:0 22px 50px rgba(0,0,0,.5)}
.hc:hover::before{transform:scaleX(1)}
.hn{position:absolute;top:1.5rem;right:1.75rem;font-family:'Cormorant Garamond',serif;font-size:4rem;font-weight:300;color:rgba(201,168,76,.07);line-height:1;transition:color .4s}
.hc:hover .hn{color:rgba(201,168,76,.14)}
.hi{font-size:2rem;display:block;margin-bottom:1.25rem}
.ht{font-size:1rem;font-weight:500;color:var(--t1);margin-bottom:.5rem;letter-spacing:.03em}
.hd{font-size:.77rem;color:var(--t2);line-height:1.9}

/* PROMO */
.promo{position:relative;z-index:1;padding:6rem 3rem;overflow:hidden}
.promo::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse 70% 50% at 50% 100%,rgba(201,168,76,.06),transparent)}
.pi{max-width:800px;margin:0 auto;text-align:center;position:relative;z-index:2}
.pq{font-family:'Cormorant Garamond',serif;font-size:clamp(1.3rem,2.5vw,2rem);font-weight:300;font-style:italic;color:var(--t1);line-height:1.7;margin-bottom:1.5rem;padding:0 1.5rem;position:relative}
.pq::before,.pq::after{font-size:4rem;color:var(--g);opacity:.2;position:absolute;font-family:'Cormorant Garamond',serif;line-height:1}
.pq::before{content:'"';top:-.5rem;left:0}
.pq::after{content:'"';bottom:-2rem;right:0}
.pn{font-size:.63rem;letter-spacing:.15em;color:var(--g);display:inline-flex;align-items:center;gap:10px;margin-top:1.5rem}
.pn::before,.pn::after{content:'';width:22px;height:1px;background:var(--g);opacity:.4}

/* CITIES */
.citsec{position:relative;z-index:1;padding:5rem 3rem;backdrop-filter:blur(12px);background:rgba(6,8,16,.65);border-top:1px solid var(--b1);border-bottom:1px solid var(--b1)}
.crow{display:flex;gap:1px;background:var(--b1);margin-top:2.5rem}
.cc{flex:1;padding:2rem 1.25rem;background:rgba(6,8,16,.85);text-align:center;cursor:none;transition:all .3s;border:1px solid transparent}
.cc:hover{background:rgba(13,16,32,.95);border-color:var(--gb)}
.cc:hover .ccn{color:var(--g)}
.ccn{font-family:'Cormorant Garamond',serif;font-size:1.15rem;font-weight:300;color:var(--t1);transition:color .3s;margin-bottom:.2rem}
.ccr{font-size:.53rem;letter-spacing:.1em;text-transform:uppercase;color:var(--t4)}

/* CONTACT */
.cosec{position:relative;z-index:1;padding:8rem 3rem;background:rgba(2,3,10,.7);backdrop-filter:blur(16px)}
.cogrid{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:6rem;align-items:start}
.cod{font-size:.82rem;color:var(--t2);line-height:1.9;margin-bottom:2.5rem}
.cor{display:flex;align-items:center;gap:12px;margin-bottom:1.25rem;font-size:.8rem;color:var(--t2)}
.cor a{color:var(--t2);text-decoration:none;transition:color .2s}
.cor a:hover{color:var(--g)}
.coic{width:34px;height:34px;border:1px solid var(--b1);display:flex;align-items:center;justify-content:center;font-size:.9rem;flex-shrink:0;color:var(--g)}
.cf{display:flex;flex-direction:column;gap:.7rem}
.cf input,.cf textarea{background:rgba(6,8,16,.9);border:1px solid var(--b1);padding:13px 16px;font-family:'Space Grotesk',sans-serif;font-size:.83rem;color:var(--t1);font-weight:300;outline:none;transition:border .25s;width:100%}
.cf input::placeholder,.cf textarea::placeholder{color:var(--t4)}
.cf input:focus,.cf textarea:focus{border-color:var(--gb)}
.cf textarea{resize:vertical;min-height:110px;font-family:'Space Grotesk',sans-serif}
.cfb{background:linear-gradient(135deg,var(--g),var(--g2));color:var(--ink);border:none;padding:14px;font-family:'Space Grotesk',sans-serif;font-size:.7rem;letter-spacing:.14em;text-transform:uppercase;font-weight:600;cursor:none;transition:all .3s;margin-top:.4rem}
.cfb:hover{opacity:.9;transform:translateY(-1px);box-shadow:0 10px 25px rgba(201,168,76,.25)}
.cfn{font-size:.58rem;color:var(--t4);margin-top:.4rem}

/* WHATSAPP BUTTON */
.wa-btn{
  display:inline-flex;align-items:center;gap:14px;
  background:linear-gradient(135deg,#1DB954,#25D366);
  color:#fff;text-decoration:none;
  padding:18px 48px;
  font-family:'Space Grotesk',sans-serif;
  font-size:1.4rem;font-weight:700;letter-spacing:.04em;
  transition:all .3s;position:relative;overflow:hidden;
  box-shadow:0 12px 40px rgba(37,211,102,.3);
  border:none;cursor:none;
}
.wa-btn::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(255,255,255,.15),transparent);
  opacity:0;transition:opacity .3s;
}
.wa-btn:hover{transform:translateY(-3px);box-shadow:0 20px 50px rgba(37,211,102,.4)}
.wa-btn:hover::before{opacity:1}
.wa-btn svg{flex-shrink:0}
.wa-sub{
  font-size:.65rem;letter-spacing:.18em;text-transform:uppercase;
  color:rgba(255,255,255,.75);display:block;font-weight:400;
  margin-top:1px;
}
.wa-btn span:nth-child(2){display:flex;flex-direction:column;align-items:flex-start}
footer{position:relative;z-index:1;background:rgba(2,3,10,.95);border-top:1px solid var(--b1);padding:5rem 3rem 2.5rem}
.ft{max-width:1200px;margin:0 auto}
.ftop{display:grid;grid-template-columns:2.5fr 1fr 1fr 1fr;gap:4rem;padding-bottom:4rem;border-bottom:1px solid var(--b1)}
.flogo{font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:1.7rem;letter-spacing:.14em;color:#fff}
.flogo span{color:var(--g)}
.fdesc{font-size:.72rem;color:var(--t4);margin-top:.5rem;line-height:1.8;max-width:220px;font-style:italic}
.fct{font-size:.55rem;letter-spacing:.2em;text-transform:uppercase;color:var(--g);margin-bottom:1.2rem}
.fcol a{display:block;font-size:.72rem;color:var(--t4);text-decoration:none;margin-bottom:.6rem;transition:color .2s}
.fcol a:hover{color:var(--t1)}
.fbot{display:flex;justify-content:space-between;padding-top:2.5rem;font-size:.58rem;color:var(--t4);flex-wrap:wrap;gap:.5rem}

/* MODAL */
.mbg{position:fixed;inset:0;background:rgba(2,3,10,.92);backdrop-filter:blur(22px);z-index:600;display:none;align-items:center;justify-content:center;padding:1.5rem}
.mbg.open{display:flex}
.mbox{background:var(--ink2);border:1px solid var(--b1);width:100%;max-width:500px;animation:mIn .35s cubic-bezier(.16,1,.3,1);position:relative;overflow:hidden}
.mbox::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--g),transparent)}
@keyframes mIn{from{opacity:0;transform:scale(.95) translateY(18px)}to{opacity:1;transform:none}}
.mh{padding:1.75rem 2rem;border-bottom:1px solid var(--b1);display:flex;justify-content:space-between;align-items:flex-start}
.mico{font-size:2.5rem;display:block;margin-bottom:.5rem}
.mtit{font-family:'Cormorant Garamond',serif;font-size:1.5rem;font-weight:300;color:#fff}
.msub{font-size:.58rem;letter-spacing:.14em;text-transform:uppercase;color:var(--g);margin-top:3px}
.mcl{background:none;border:1px solid var(--b1);width:32px;height:32px;cursor:none;color:var(--t3);display:flex;align-items:center;justify-content:center;font-size:.9rem;transition:all .2s;flex-shrink:0}
.mcl:hover{border-color:var(--gb);color:var(--g)}
.mb{padding:2rem}
.me{text-align:center;padding:1rem 0}
.meico{font-size:3rem;display:block;margin-bottom:1rem;opacity:.35}
.met{font-family:'Cormorant Garamond',serif;font-size:1.2rem;color:var(--t2);margin-bottom:.6rem}
.med{font-size:.75rem;color:var(--t3);line-height:1.9;margin-bottom:1.5rem}
.mebadge{display:inline-block;border:1px solid var(--gb);background:var(--g3);padding:7px 18px;font-size:.58rem;letter-spacing:.14em;text-transform:uppercase;color:var(--g)}
.mec{margin-top:1.25rem;padding-top:1.25rem;border-top:1px solid var(--b1);font-size:.7rem;color:var(--t3);display:flex;align-items:center;gap:8px;justify-content:center}
.mec a{color:var(--g);text-decoration:none}

/* ══ RESPONSIVE ══ */
@media(max-width:1024px){
  .cgrid{grid-template-columns:repeat(4,1fr)}
  .ftop{grid-template-columns:1fr 1fr;gap:2.5rem}
}

@media(max-width:768px){
  nav{padding:0 1rem}
  .nav-r .na{display:none}
  .logo-nav{font-size:1.1rem}

  .hero{padding:7rem 1.25rem 4rem;min-height:auto}
  .logo-main{font-size:clamp(2.8rem,14vw,5rem) !important}
  .logo-tagline{font-size:.85rem}
  .hero-desc{font-size:.82rem;max-width:100%}
  .hero-btns{flex-direction:column;align-items:center;width:100%}
  .hero-btns .bp,.hero-btns .bg{width:100%;max-width:320px;text-align:center}

  .statsbar{flex-wrap:wrap;padding:1.5rem 1rem}
  .si{min-width:50%;padding:1.25rem .75rem}
  .sn{font-size:2.2rem}

  .sec{padding:3.5rem 1.25rem}
  .wgrid{grid-template-columns:1fr}
  .wc{padding:2rem 1.5rem}
  .wn{font-size:3rem}

  .cgrid{grid-template-columns:repeat(3,1fr)}
  .ct{padding:1.25rem .75rem 1rem}
  .cti{font-size:1.4rem}
  .ctn{font-size:.62rem}

  .hgrid{grid-template-columns:1fr}
  .hc{padding:2rem 1.5rem}

  .promo{padding:3.5rem 1.25rem}
  .pq{font-size:1.1rem;padding:0 .5rem}

  .cosec{padding:4rem 1.25rem}
  .cogrid{grid-template-columns:1fr;gap:2.5rem}

  .wa-btn{padding:14px 28px;font-size:1.1rem;width:100%;max-width:340px;justify-content:center}

  footer{padding:3.5rem 1.25rem 2rem}
  .ftop{grid-template-columns:1fr 1fr;gap:2rem}
  .fbot{flex-direction:column;align-items:center;text-align:center;gap:.5rem}

  .sh{font-size:clamp(1.5rem,5vw,2.2rem)}
  .mbox{max-width:95vw}
  .mb{padding:1.25rem}
  .mh{padding:1.25rem 1.25rem}
}

@media(max-width:480px){
  nav{padding:0 .9rem}
  .logo-nav{font-size:1rem;letter-spacing:.1em}
  .lb{padding:5px 10px;font-size:.55rem}

  .logo-main{font-size:clamp(2.4rem,13vw,3.5rem) !important}
  .logo-tagline{font-size:.75rem;letter-spacing:.06em}
  .hero-eyebrow{font-size:.5rem;letter-spacing:.15em}
  .hero-desc{font-size:.78rem}

  .statsbar{padding:1rem .5rem}
  .si{min-width:50%;padding:1rem .5rem}
  .sn{font-size:1.9rem}
  .sl{font-size:.48rem}

  .sec{padding:2.5rem 1rem}
  .sey{font-size:.5rem;letter-spacing:.18em}
  .sh{font-size:clamp(1.4rem,7vw,2rem)}
  .sr{margin-bottom:2rem}

  .cgrid{grid-template-columns:repeat(2,1fr)}
  .ct{padding:1.1rem .6rem .9rem}
  .cti{font-size:1.3rem;margin-bottom:.5rem}
  .ctn{font-size:.6rem}
  .cts{font-size:.45rem}
  .csrch input{font-size:.78rem;padding:.75rem 1rem}

  .wc{padding:1.75rem 1.25rem}
  .wt{font-size:.9rem}
  .wd{font-size:.74rem}

  .hc{padding:1.75rem 1.25rem}
  .ht{font-size:.9rem}
  .hd{font-size:.74rem}
  .hn{font-size:3rem}

  .pq{font-size:1rem}
  .pn{font-size:.58rem}

  .cosec{padding:3rem .9rem}
  .cod{font-size:.78rem}
  .cf input,.cf textarea{font-size:.8rem;padding:11px 13px}
  .cfb{font-size:.65rem}
  .cfn{font-size:.54rem}
  .cor{font-size:.74rem}
  .coic{width:28px;height:28px;font-size:.8rem}

  .wa-btn{padding:13px 20px;font-size:1rem}
  .wa-btn svg{width:22px;height:22px}
  .wa-sub{font-size:.58rem}

  footer{padding:2.5rem .9rem 1.5rem}
  .ftop{grid-template-columns:1fr;gap:1.5rem}
  .flogo{font-size:1.3rem}
  .fdesc{font-size:.68rem}
  .fct{font-size:.5rem}
  .fcol a{font-size:.68rem}
  .fbot{font-size:.54rem}

  .mbox{max-width:98vw}
  .mh{padding:1rem}
  .mtit{font-size:1.2rem}
  .mb{padding:1rem}
  .meico{font-size:2.2rem}
  .met{font-size:1rem}
  .med{font-size:.7rem}
  .mebadge{font-size:.54rem;padding:6px 14px}
}
</style>
</head>
<body>
<div id="cur"></div>
<div id="cur2"></div>
<canvas id="bg3d"></canvas>

<!-- NAV -->
<nav>
  <a href="#" class="logo-nav">MKD<span>MAP</span></a>
  <div class="nav-r">
    <a href="#cats" class="na" data-t="n1">Kategoritë</a>
    <a href="#how" class="na" data-t="n2">Si Punon</a>
    <a href="#contact" class="na" data-t="n3">Kontakt</a>
    <div class="lw">
      <button class="lb" id="lBtn" onclick="tgL()">
        <span id="lLbl">🇦🇱 SQ</span>
        <svg viewBox="0 0 10 10" fill="none"><path d="M2 3.5l3 3 3-3" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
      </button>
      <div class="ld" id="lDd"></div>
    </div>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-eyebrow">mkdmap.com · Republika e Maqedonisë së Veriut</div>

  <div class="logo-wrap">
    <div class="logo-ring"></div>
    <div class="logo-ring2"></div>
    <div class="logo-scan"></div>
    <div class="logo-main">
      <span class="l">M</span><span class="l">K</span><span class="l">D</span><span class="l">M</span><span class="l">A</span><span class="l">P</span>
    </div>
    <div class="logo-tagline">Në ndihmë të <b>banorëve</b>, <b>turistëve</b> dhe <b>bizneseve</b> të Maqedonisë</div>
  </div>

  <p class="hero-desc" data-t="hdesc">Direktoria premium e bizneseve të Maqedonisë së Veriut — hotele, restorante, shërbime shtëpie, profesionistë dhe shumë tepër, falas.</p>
  <div class="hero-btns">
    <button class="bp" onclick="document.getElementById('cats').scrollIntoView({behavior:'smooth'})" data-t="cta1">Eksploro Tani</button>
    <button class="bg" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})" data-t="cta2">Regjistro Biznesin</button>
  </div>
</section>

<!-- STATS -->
<div class="statsbar">
  <div class="si"><span class="sn">12<em>+</em></span><span class="sl" data-t="s1">Qytete</span></div>
  <div class="si"><span class="sn">32<em>+</em></span><span class="sl" data-t="s2">Kategori</span></div>
  <div class="si"><span class="sn">100<em>%</em></span><span class="sl" data-t="s3">Falas</span></div>
  <div class="si"><span class="sn">24<em>/7</em></span><span class="sl" data-t="s4">Online</span></div>
</div>

<!-- WHY -->
<section class="sec why">
  <div class="si2">
    <p class="sey" data-t="we">Pse MKDMAP?</p>
    <h2 class="sh"><em data-t="wh1">Premium</em> <span data-t="wh2">· Pa Kompromis</span></h2>
    <div class="sr"></div>
    <div class="wgrid">
      <div class="wc"><span class="wn">01</span><span class="wi">🎯</span><div class="wt" data-t="w1t">Direktori e Verifikuar</div><p class="wd" data-t="w1d">Çdo biznes kalon verifikimin tonë. Informacion i saktë dhe i besueshëm.</p></div>
      <div class="wc"><span class="wn">02</span><span class="wi">⚡</span><div class="wt" data-t="w2t">Kontakt Direkt</div><p class="wd" data-t="w2d">Pa ndërmjetës, pa komisione. Telefono drejtpërdrejt me biznesin.</p></div>
      <div class="wc"><span class="wn">03</span><span class="wi">🌍</span><div class="wt" data-t="w3t">12 Gjuhë</div><p class="wd" data-t="w3d">Dizajnuar për banorë dhe turistë. 12 gjuhë të botës.</p></div>

    </div>
  </div>
</section>

<!-- CATEGORIES -->
<section class="sec catsec" id="cats">
  <div class="si2">
    <p class="sey" data-t="cte">Shërbime & Biznese</p>
    <h2 class="sh"><em data-t="cth1">Gjej</em> <span data-t="cth2">çfarë të duhet</span></h2>
    <div class="sr"></div>
    <div class="csrch"><span>🔍</span><input type="text" id="cSr" placeholder="Kërko kategori..." oninput="fC()" data-ph="ctph"/></div>
    <div class="cgrid" id="cGrid"></div>
  </div>
</section>

<!-- HOW -->
<section class="sec howsec" id="how">
  <div class="si2">
    <p class="sey" data-t="hwe">Si funksionon</p>
    <h2 class="sh"><span data-t="hwh1">Thjesht</span> <em data-t="hwh2">& Falas</em></h2>
    <div class="sr"></div>
    <div class="hgrid">
      <div class="hc"><span class="hn">01</span><span class="hi">🔍</span><div class="ht" data-t="h1t">Kërko Kategorinë</div><p class="hd" data-t="h1d">Zgjidh nga 32+ kategori — restorante, hidraulikë, farmaci dhe të tjera.</p></div>
      <div class="hc"><span class="hn">02</span><span class="hi">📍</span><div class="ht" data-t="h2t">Shiko Lokacionin</div><p class="hd" data-t="h2d">Adresë e saktë dhe lidhje direkte me Google Maps.</p></div>
      <div class="hc"><span class="hn">03</span><span class="hi">📞</span><div class="ht" data-t="h3t">Kontakto Direkt</div><p class="hd" data-t="h3d">Telefono me një klik. Pa ndërmjetës, pa komisione.</p></div>
    </div>
  </div>
</section>

<!-- PROMO -->
<section class="promo">
  <div class="pi">
    <div class="pq" data-t="pq">Bizneset e verifikuara ofrojnë kushte speciale dhe zbritje ekskluzive. Kur kontaktoni, përmendni mkdmap.com!</div>
    <div class="pn" data-t="pn">★ Zbritje ekskluzive për klientët e MKDMAP</div>
  </div>
</section>



<!-- CONTACT -->
<section class="cosec" id="contact">
  <div class="si2" style="max-width:900px;margin:0 auto;text-align:center;">
    <p class="sey" data-t="coe">Na Kontakto</p>
    <h2 class="sh" style="text-align:center"><em data-t="coh1">Regjistro</em> <span data-t="coh2">Biznesin Tënd</span></h2>
    <div class="sr" style="margin:0 auto 2rem"></div>
    <p class="cod" style="max-width:560px;margin:0 auto 3rem;text-align:center" data-t="codd">A ke biznes në Maqedoninë e Veriut? Na shkruaj në WhatsApp dhe do ta listojmë falas. Mijëra banorë dhe turistë do ta shohin çdo ditë.</p>

    <!-- WhatsApp BIG BUTTON -->
    <a href="https://wa.me/38970878227?text=Pershendetje%2C%20dua%20te%20regjistroj%20biznesin%20tim%20ne%20MKDMAP" target="_blank" class="wa-btn">
      <svg width="28" height="28" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      <span>070 878 227</span>
      <span class="wa-sub">Shkruaj në WhatsApp</span>
    </a>

    <div style="margin-top:2.5rem;display:flex;flex-direction:column;align-items:center;gap:1rem">
      <div class="cor" style="justify-content:center"><div class="coic">🌐</div><a href="https://mkdmap.com">mkdmap.com</a></div>
      <div class="cor" style="justify-content:center"><div class="coic">📍</div><span>Maqedoni e Veriut</span></div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="ft">
    <div class="ftop">
      <div><div class="flogo">MKD<span>MAP</span></div><div class="fdesc" data-t="ftd">Direktoria premium e bizneseve të Maqedonisë — falas, gjithmonë.</div></div>
      <div class="fcol"><div class="fct" data-t="fc1">Navigim</div><a href="#cats" data-t="fl1">Kategoritë</a><a href="#how" data-t="fl2">Si punon</a><a href="#contact" data-t="fl3">Kontakt</a></div>
      <div class="fcol"><div class="fct" data-t="fc2">Bizneset</div><a href="#contact" data-t="fl4">Regjistro</a><a href="#" data-t="fl5">Rreth nesh</a></div>
      <div class="fcol"><div class="fct">WhatsApp</div><a href="https://wa.me/38970878227" target="_blank">070 878 227</a><a href="https://mkdmap.com">mkdmap.com</a></div>
    </div>
    <div class="fbot"><span data-t="fcp">© 2025 mkdmap.com — Të gjitha të drejtat e rezervuara</span><span>🇲🇰 Bërë me dashuri për Maqedoninë e Veriut</span></div>
  </div>
</footer>

<!-- MODAL -->
<div class="mbg" id="mBg" onclick="cMBg(event)">
  <div class="mbox">
    <div class="mh">
      <div><span class="mico" id="mIco"></span><div class="mtit" id="mTit"></div><div class="msub" data-t="ms">Bizneset po regjistrohen · Coming Soon</div></div>
      <button class="mcl" onclick="cM()">✕</button>
    </div>
    <div class="mb">
      <div class="me">
        <span class="meico" id="mIco2"></span>
        <div class="met" data-t="mt">Kjo kategori hapet së shpejti</div>
        <p class="med" data-t="md">Jemi duke mbledhur bizneset. Nëse keni biznes, na kontaktoni.</p>
        <span class="mebadge" data-t="mb2">Listim Falas · Free Listing</span>
        <div class="mec">📱 <a href="https://wa.me/38970878227" target="_blank">WhatsApp: 070 878 227</a></div>
      </div>
    </div>
  </div>
</div>

<script>
/* ════════════════════════════════════════
   LIVE 3D BACKGROUND — WebGL particle system
════════════════════════════════════════ */
(function(){
  const canvas = document.getElementById('bg3d');
  const gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
  if(!gl) return;

  let W = window.innerWidth, H = window.innerHeight;
  canvas.width = W; canvas.height = H;
  window.addEventListener('resize', ()=>{
    W = window.innerWidth; H = window.innerHeight;
    canvas.width = W; canvas.height = H;
    gl.viewport(0,0,W,H);
  });

  const vsrc = `
    attribute vec3 aPos;
    attribute float aSize;
    attribute float aAlpha;
    uniform float uTime;
    uniform mat4 uMVP;
    varying float vAlpha;
    void main(){
      vec3 p = aPos;
      p.z += mod(uTime * 0.08 + aAlpha * 10.0, 4.0) - 2.0;
      gl_Position = uMVP * vec4(p, 1.0);
      gl_PointSize = aSize * (1.5 / gl_Position.w);
      vAlpha = aAlpha * (1.0 - abs(p.z) * 0.3);
    }
  `;
  const fsrc = `
    precision mediump float;
    varying float vAlpha;
    void main(){
      vec2 uv = gl_PointCoord - 0.5;
      float d = length(uv);
      if(d > 0.5) discard;
      float alpha = vAlpha * (1.0 - d * 2.0);
      gl_FragColor = vec4(0.78, 0.66, 0.30, alpha * 0.6);
    }
  `;

  function mkShader(t,src){const s=gl.createShader(t);gl.shaderSource(s,src);gl.compileShader(s);return s}
  const prog = gl.createProgram();
  gl.attachShader(prog, mkShader(gl.VERTEX_SHADER,vsrc));
  gl.attachShader(prog, mkShader(gl.FRAGMENT_SHADER,fsrc));
  gl.linkProgram(prog);
  gl.useProgram(prog);

  const N = 1800;
  const pos = new Float32Array(N*3);
  const sizes = new Float32Array(N);
  const alphas = new Float32Array(N);

  for(let i=0;i<N;i++){
    pos[i*3]   = (Math.random()-0.5)*6;
    pos[i*3+1] = (Math.random()-0.5)*6;
    pos[i*3+2] = (Math.random()-0.5)*4;
    sizes[i]   = Math.random()*3+1;
    alphas[i]  = Math.random();
  }

  const posBuf = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, posBuf);
  gl.bufferData(gl.ARRAY_BUFFER, pos, gl.STATIC_DRAW);
  const aPos = gl.getAttribLocation(prog,'aPos');
  gl.enableVertexAttribArray(aPos);
  gl.vertexAttribPointer(aPos,3,gl.FLOAT,false,0,0);

  const sizeBuf = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, sizeBuf);
  gl.bufferData(gl.ARRAY_BUFFER, sizes, gl.STATIC_DRAW);
  const aSz = gl.getAttribLocation(prog,'aSize');
  gl.enableVertexAttribArray(aSz);
  gl.vertexAttribPointer(aSz,1,gl.FLOAT,false,0,0);

  const alphaBuf = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, alphaBuf);
  gl.bufferData(gl.ARRAY_BUFFER, alphas, gl.STATIC_DRAW);
  const aAl = gl.getAttribLocation(prog,'aAlpha');
  gl.enableVertexAttribArray(aAl);
  gl.vertexAttribPointer(aAl,1,gl.FLOAT,false,0,0);

  const uTime = gl.getUniformLocation(prog,'uTime');
  const uMVP  = gl.getUniformLocation(prog,'uMVP');

  let mx=0,my=0;
  document.addEventListener('mousemove',e=>{mx=(e.clientX/W-.5)*2;my=(e.clientY/H-.5)*2});

  function mat4(){return new Float32Array(16)}
  function identity(m){m[0]=m[5]=m[10]=m[15]=1;m[1]=m[2]=m[3]=m[4]=m[6]=m[7]=m[8]=m[9]=m[11]=m[12]=m[13]=m[14]=0;return m}
  function perspective(m,fov,ar,near,far){
    const f=1/Math.tan(fov/2),nf=1/(near-far);
    m[0]=f/ar;m[1]=0;m[2]=0;m[3]=0;
    m[4]=0;m[5]=f;m[6]=0;m[7]=0;
    m[8]=0;m[9]=0;m[10]=(far+near)*nf;m[11]=-1;
    m[12]=0;m[13]=0;m[14]=2*far*near*nf;m[15]=0;
    return m;
  }
  function rotateY(m,ang){
    const c=Math.cos(ang),s=Math.sin(ang);
    const a0=m[0],a1=m[1],a2=m[2],a3=m[3];
    const a8=m[8],a9=m[9],a10=m[10],a11=m[11];
    m[0]=a0*c+a8*s;m[1]=a1*c+a9*s;m[2]=a2*c+a10*s;m[3]=a3*c+a11*s;
    m[8]=a8*c-a0*s;m[9]=a9*c-a1*s;m[10]=a10*c-a2*s;m[11]=a11*c-a3*s;
    return m;
  }
  function rotateX(m,ang){
    const c=Math.cos(ang),s=Math.sin(ang);
    const a4=m[4],a5=m[5],a6=m[6],a7=m[7];
    const a8=m[8],a9=m[9],a10=m[10],a11=m[11];
    m[4]=a4*c+a8*s;m[5]=a5*c+a9*s;m[6]=a6*c+a10*s;m[7]=a7*c+a11*s;
    m[8]=a8*c-a4*s;m[9]=a9*c-a5*s;m[10]=a10*c-a6*s;m[11]=a11*c-a7*s;
    return m;
  }
  function translate(m,x,y,z){m[12]+=m[0]*x+m[4]*y+m[8]*z;m[13]+=m[1]*x+m[5]*y+m[9]*z;m[14]+=m[2]*x+m[6]*y+m[10]*z;m[15]+=m[3]*x+m[7]*y+m[11]*z;return m}
  function mul(a,b){
    const o=mat4();
    for(let i=0;i<4;i++)for(let j=0;j<4;j++){let v=0;for(let k=0;k<4;k++)v+=a[i+k*4]*b[k+j*4];o[i+j*4]=v}
    return o;
  }

  let t0=null;
  function frame(ts){
    if(!t0)t0=ts;
    const t=(ts-t0)/1000;

    gl.viewport(0,0,W,H);
    gl.clear(gl.COLOR_BUFFER_BIT|gl.DEPTH_BUFFER_BIT);
    gl.enable(gl.BLEND);
    gl.blendFunc(gl.SRC_ALPHA,gl.ONE);

    const proj=perspective(mat4(),0.9,W/H,0.1,20);
    const view=identity(mat4());
    translate(view,0,0,-4);
    rotateY(view,t*0.04+mx*0.12);
    rotateX(view,-0.35+my*0.08);

    const mvp=mul(proj,view);
    gl.uniformMatrix4fv(uMVP,false,mvp);
    gl.uniform1f(uTime,t);

    // rebind all attribs each frame (for size/alpha)
    gl.bindBuffer(gl.ARRAY_BUFFER,posBuf);
    gl.vertexAttribPointer(aPos,3,gl.FLOAT,false,0,0);
    gl.bindBuffer(gl.ARRAY_BUFFER,sizeBuf);
    gl.vertexAttribPointer(aSz,1,gl.FLOAT,false,0,0);
    gl.bindBuffer(gl.ARRAY_BUFFER,alphaBuf);
    gl.vertexAttribPointer(aAl,1,gl.FLOAT,false,0,0);

    gl.drawArrays(gl.POINTS,0,N);
    requestAnimationFrame(frame);
  }

  // Also draw grid lines layer on 2D canvas overlay
  const oc = document.createElement('canvas');
  oc.style.cssText='position:fixed;inset:0;z-index:0;pointer-events:none;opacity:1';
  oc.width=W;oc.height=H;
  const bg3d = document.getElementById('bg3d');
  if(bg3d && bg3d.parentNode === document.body && bg3d.nextSibling){
    document.body.insertBefore(oc, bg3d.nextSibling);
  } else {
    document.body.appendChild(oc);
  }
  const ctx=oc.getContext('2d');

  function drawGrid(ts){
    if(!t0)return;
    const t2=(ts-t0)/1000;
    oc.width=W;oc.height=H;
    ctx.clearRect(0,0,W,H);

    /* Animated perspective grid on floor */
    const oy = H*0.62 + Math.sin(t2*.3)*20;
    const vp = {x:W/2 + Math.sin(t2*.2)*60, y:oy};
    const cols=24,rows=14;
    const spread=W*1.6, depth=H*0.8;

    ctx.save();
    // Vertical lines
    for(let i=0;i<=cols;i++){
      const px=W/2-spread/2+spread*(i/cols);
      const fade=Math.abs(i-cols/2)/(cols/2);
      const alpha=(0.06-fade*0.05)*(0.7+0.3*Math.sin(t2+i*.3));
      ctx.strokeStyle=`rgba(201,168,76,${Math.max(0,alpha)})`;
      ctx.lineWidth=.5;
      ctx.beginPath();
      ctx.moveTo(vp.x+(px-vp.x)*0,vp.y);
      ctx.lineTo(px,vp.y+depth);
      ctx.stroke();
    }
    // Horizontal lines
    for(let j=0;j<=rows;j++){
      const t=j/rows;
      const et=t*t;
      const y=vp.y+depth*et;
      const xLeft=vp.x+(W/2-spread/2-vp.x)*et;
      const xRight=vp.x+(W/2+spread/2-vp.x)*et;
      const alpha=(0.07*(1-t*.5))*(0.7+0.3*Math.sin(t2*.7+j*.5));
      ctx.strokeStyle=`rgba(201,168,76,${Math.max(0,alpha)})`;
      ctx.lineWidth=.5;
      ctx.beginPath();ctx.moveTo(xLeft,y);ctx.lineTo(xRight,y);ctx.stroke();
    }

    /* Floating glowing orbs */
    const orbs=[
      {x:.15,y:.3,r:180,sp:.4},{x:.8,y:.6,r:220,sp:.25},
      {x:.5,y:.15,r:150,sp:.55},{x:.35,y:.75,r:200,sp:.32},
    ];
    orbs.forEach((o,i)=>{
      const ox=o.x*W+Math.sin(t2*o.sp+i)*80;
      const oy2=o.y*H+Math.cos(t2*o.sp*1.3+i)*60;
      const g=ctx.createRadialGradient(ox,oy2,0,ox,oy2,o.r);
      g.addColorStop(0,`rgba(201,168,76,${0.055+Math.sin(t2+i)*.015})`);
      g.addColorStop(.5,`rgba(100,80,200,${0.025+Math.cos(t2*.7+i)*.01})`);
      g.addColorStop(1,'transparent');
      ctx.fillStyle=g;
      ctx.fillRect(ox-o.r,oy2-o.r,o.r*2,o.r*2);
    });

    ctx.restore();
    requestAnimationFrame(drawGrid);
  }

  window.addEventListener('resize',()=>{oc.width=W;oc.height=H});
  requestAnimationFrame(frame);
  requestAnimationFrame(drawGrid);
})();

/* ════════════════════════════════════════
   TRANSLATIONS
════════════════════════════════════════ */
const TR={
  sq:{flag:'🇦🇱',lbl:'Shqip',n1:'Kategoritë',n2:'Si Punon',n3:'Kontakt',hdesc:'Direktoria premium e bizneseve të Maqedonisë — hotele, restorante, shërbime shtëpie, profesionistë, falas.',cta1:'Eksploro Tani',cta2:'Regjistro Biznesin',s1:'Qytete',s2:'Kategori',s3:'Falas',s4:'Online',we:'Pse MKDMAP?',wh1:'Premium',wh2:'· Pa Kompromis',w1t:'Direktori e Verifikuar',w1d:'Çdo biznes kalon verifikimin tonë.',w2t:'Kontakt Direkt',w2d:'Pa ndërmjetës, pa komisione.',w3t:'12 Gjuhë',w3d:'Dizajnuar për banorë dhe turistë.',w4t:'Ekspozim Premium',w4d:'Mijëra njerëz çdo ditë. Falas.',cte:'Shërbime & Biznese',cth1:'Gjej',cth2:'çfarë të duhet',ctph:'Kërko kategori...',hwe:'Si funksionon',hwh1:'Thjesht',hwh2:'& Falas',h1t:'Kërko Kategorinë',h1d:'32+ kategori — restorante, hidraulikë, farmaci...',h2t:'Shiko Lokacionin',h2d:'Adresë e saktë + Google Maps.',h3t:'Kontakto Direkt',h3d:'Telefono me një klik, pa ndërmjetës.',pq:'Bizneset e verifikuara ofrojnë kushte speciale. Kur kontaktoni, përmendni mkdmap.com!',pn:'★ Zbritje ekskluzive për klientët e MKDMAP',cie:'Qytetet tona',cih1:'Mbulojmë',cih2:'të gjithë vendin',coe:'Regjistro Biznesin',coh1:'Bashkohu',coh2:'me ne',codd:'A ke biznes? Na kontakto dhe ta listojmë falas.',cf1:'Emri i biznesit *',cf2:'Kategoria *',cf3:'Qyteti *',cf4:'Telefoni *',cf5:'Email *',cf6:'Adresa dhe info...',cfsub:'Dërgo Kërkesën',cfn:'★ Listimi 100% falas. Kontaktojmë brenda 24h.',ftd:'Direktoria premium — falas, gjithmonë.',fc1:'Navigim',fl1:'Kategoritë',fl2:'Si punon',fl3:'Kontakt',fc2:'Bizneset',fl4:'Regjistro',fl5:'Rreth nesh',fcp:'© 2025 mkdmap.com',ms:'Coming Soon',mt:'Kjo kategori hapet së shpejti',md:'Na kontakto: info@mkdmap.com',mb2:'Listim Falas · Free Listing',
    cats:{Restorant:'Restorante',Hotel:'Hotele',RentCar:'Rent a Car',Kafene:'Kafene',Farmaci:'Farmaci',Elektricist:'Elektricistë',Hidraulik:'Hidraulikë',Shepi:'Shërbime Shtëpie',Pllaka:'Pllaka & Montues',Mobileri:'Mobileri',MobilShop:'Mobil & Aksesorë',IT:'IT & Kompjuterë',Klinik:'Klinika',Dentist:'Dentistë',Okullist:'Okulistë',Berber:'Berber & Parukeri',Kozmetik:'Kozmetikë',Fitness:'Fitness & Spa',Arsim:'Arsim & Kurse',Banke:'Banka & Financa',Noter:'Noter',Avokat:'Avokat',Inxhinjer:'Inxhinjer',Agjenci:'Agjenci Turistike',Ujsjelles:'Ujësjellës',Lavazh:'Lavazhe',AutoPjes:'Auto Pjesë',Dyqan:'Dyqane',Shitje:'Shitje Online',Events:'Organizim Eventesh',Fotograf:'Fotografi',Tregti:'Tregti & Import'}},
  mk:{flag:'🇲🇰',lbl:'Македонски',cta1:'Истражи Сега',cta2:'Регистрирај Бизнис',ms:'Наскоро',mt:'Категоријата отвора наскоро',md:'info@mkdmap.com',mb2:'Бесплатно Листирање',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Ресторани',Hotel:'Хотели',RentCar:'Рент а кар',Kafene:'Кафеани',Farmaci:'Аптеки',Elektricist:'Електричари',Hidraulik:'Водоинсталатери',Shepi:'Домашни Услуги',Pllaka:'Плочки',Mobileri:'Мебел',MobilShop:'Мобилни',IT:'ИТ',Klinik:'Клиники',Dentist:'Стоматолози',Okullist:'Оптичари',Berber:'Берберници',Kozmetik:'Козметика',Fitness:'Фитнес',Arsim:'Образование',Banke:'Банки',Noter:'Нотари',Avokat:'Адвокати',Inxhinjer:'Инженери',Agjenci:'Туристички',Ujsjelles:'Водовод',Lavazh:'Автоперални',AutoPjes:'Авто Делови',Dyqan:'Продавници',Shitje:'Онлајн',Events:'Настани',Fotograf:'Фотографи',Tregti:'Трговија'}},
  en:{flag:'🇬🇧',lbl:'English',cta1:'Explore Now',cta2:'Register Business',ms:'Coming Soon',mt:'This category opens soon',md:'info@mkdmap.com',mb2:'Free Listing',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restaurants',Hotel:'Hotels',RentCar:'Car Rental',Kafene:'Cafés',Farmaci:'Pharmacies',Elektricist:'Electricians',Hidraulik:'Plumbers',Shepi:'Home Services',Pllaka:'Tiles & Install',Mobileri:'Furniture',MobilShop:'Mobile & Acc',IT:'IT & Computers',Klinik:'Clinics',Dentist:'Dentists',Okullist:'Opticians',Berber:'Barbershops',Kozmetik:'Cosmetics',Fitness:'Fitness & Spa',Arsim:'Education',Banke:'Banking',Noter:'Notary',Avokat:'Lawyers',Inxhinjer:'Engineers',Agjenci:'Travel Agencies',Ujsjelles:'Waterworks',Lavazh:'Car Wash',AutoPjes:'Auto Parts',Dyqan:'Shops',Shitje:'Online Sales',Events:'Event Planning',Fotograf:'Photography',Tregti:'Trade & Import'}},
  de:{flag:'🇩🇪',lbl:'Deutsch',cta1:'Jetzt Erkunden',cta2:'Registrieren',ms:'Demnächst',mt:'Diese Kategorie öffnet bald',md:'info@mkdmap.com',mb2:'Kostenlos',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restaurants',Hotel:'Hotels',RentCar:'Mietwagen',Kafene:'Cafés',Farmaci:'Apotheken',Elektricist:'Elektriker',Hidraulik:'Klempner',Shepi:'Haushalt',Pllaka:'Fliesen',Mobileri:'Möbel',MobilShop:'Handys',IT:'IT',Klinik:'Kliniken',Dentist:'Zahnärzte',Okullist:'Optiker',Berber:'Barbiere',Kozmetik:'Kosmetik',Fitness:'Fitness',Arsim:'Bildung',Banke:'Banken',Noter:'Notar',Avokat:'Anwälte',Inxhinjer:'Ingenieure',Agjenci:'Reisebüros',Ujsjelles:'Wasser',Lavazh:'Autowäsche',AutoPjes:'Autoteile',Dyqan:'Geschäfte',Shitje:'Online',Events:'Events',Fotograf:'Fotografie',Tregti:'Handel'}},
  tr:{flag:'🇹🇷',lbl:'Türkçe',cta1:'Keşfet',cta2:'Kayıt Ol',ms:'Yakında',mt:'Bu kategori yakında',md:'info@mkdmap.com',mb2:'Ücretsiz',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restoranlar',Hotel:'Oteller',RentCar:'Araç Kiralama',Kafene:'Kafeler',Farmaci:'Eczaneler',Elektricist:'Elektrikçiler',Hidraulik:'Tesisatçılar',Shepi:'Ev Hizmetleri',Pllaka:'Fayans',Mobileri:'Mobilya',MobilShop:'Telefon',IT:'IT',Klinik:'Klinikler',Dentist:'Dişçiler',Okullist:'Optisyen',Berber:'Berberler',Kozmetik:'Kozmetik',Fitness:'Fitness',Arsim:'Eğitim',Banke:'Bankalar',Noter:'Noter',Avokat:'Avukatlar',Inxhinjer:'Mühendisler',Agjenci:'Seyahat',Ujsjelles:'Su',Lavazh:'Oto Yıkama',AutoPjes:'Oto Parça',Dyqan:'Dükkanlar',Shitje:'Online',Events:'Etkinlikler',Fotograf:'Fotoğraf',Tregti:'Ticaret'}},
  sr:{flag:'🇷🇸',lbl:'Srpski',cta1:'Istraži',cta2:'Registruj',ms:'Uskoro',mt:'Uskoro se otvara',md:'info@mkdmap.com',mb2:'Besplatno',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restorani',Hotel:'Hoteli',RentCar:'Rent-a-Car',Kafene:'Kafići',Farmaci:'Apoteke',Elektricist:'Električari',Hidraulik:'Vodoinstalateri',Shepi:'Kućne Usluge',Pllaka:'Pločice',Mobileri:'Nameštaj',MobilShop:'Telefoni',IT:'IT',Klinik:'Klinike',Dentist:'Stomatolozi',Okullist:'Optičari',Berber:'Berberi',Kozmetik:'Kozmetika',Fitness:'Fitnes',Arsim:'Obrazovanje',Banke:'Banke',Noter:'Notari',Avokat:'Advokati',Inxhinjer:'Inženjeri',Agjenci:'Turizam',Ujsjelles:'Vodovod',Lavazh:'Autopraonica',AutoPjes:'Auto Delovi',Dyqan:'Prodavnice',Shitje:'Online',Events:'Organizacija',Fotograf:'Fotografija',Tregti:'Trgovina'}},
  it:{flag:'🇮🇹',lbl:'Italiano',cta1:'Esplora',cta2:'Registra',ms:'Presto',mt:'Presto disponibile',md:'info@mkdmap.com',mb2:'Gratuito',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Ristoranti',Hotel:'Hotel',RentCar:'Autonoleggio',Kafene:'Bar',Farmaci:'Farmacie',Elektricist:'Elettricisti',Hidraulik:'Idraulici',Shepi:'Servizi Casa',Pllaka:'Piastrelle',Mobileri:'Mobili',MobilShop:'Telefonia',IT:'IT',Klinik:'Cliniche',Dentist:'Dentisti',Okullist:'Ottici',Berber:'Barbieri',Kozmetik:'Cosmetica',Fitness:'Fitness',Arsim:'Istruzione',Banke:'Banche',Noter:'Notai',Avokat:'Avvocati',Inxhinjer:'Ingegneri',Agjenci:'Agenzie',Ujsjelles:'Acqua',Lavazh:'Autolavaggio',AutoPjes:'Ricambi',Dyqan:'Negozi',Shitje:'Online',Events:'Eventi',Fotograf:'Fotografia',Tregti:'Commercio'}},
  fr:{flag:'🇫🇷',lbl:'Français',cta1:'Explorer',cta2:'S\'inscrire',ms:'Bientôt',mt:'Bientôt disponible',md:'info@mkdmap.com',mb2:'Gratuit',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restaurants',Hotel:'Hôtels',RentCar:'Location Voiture',Kafene:'Cafés',Farmaci:'Pharmacies',Elektricist:'Électriciens',Hidraulik:'Plombiers',Shepi:'Services Maison',Pllaka:'Carrelage',Mobileri:'Meubles',MobilShop:'Téléphones',IT:'Informatique',Klinik:'Cliniques',Dentist:'Dentistes',Okullist:'Opticiens',Berber:'Barbiers',Kozmetik:'Cosmétique',Fitness:'Fitness',Arsim:'Éducation',Banke:'Banques',Noter:'Notaires',Avokat:'Avocats',Inxhinjer:'Ingénieurs',Agjenci:'Agences',Ujsjelles:'Eau',Lavazh:'Lavage Auto',AutoPjes:'Pièces Auto',Dyqan:'Magasins',Shitje:'Online',Events:'Événements',Fotograf:'Photographie',Tregti:'Commerce'}},
  ar:{flag:'🇸🇦',lbl:'العربية',cta1:'استكشف',cta2:'سجّل',ms:'قريباً',mt:'قريباً',md:'info@mkdmap.com',mb2:'مجاني',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'مطاعم',Hotel:'فنادق',RentCar:'تأجير',Kafene:'مقاهي',Farmaci:'صيدليات',Elektricist:'كهربائيون',Hidraulik:'سباكون',Shepi:'خدمات منزلية',Pllaka:'بلاط',Mobileri:'أثاث',MobilShop:'هواتف',IT:'تقنية',Klinik:'عيادات',Dentist:'أسنان',Okullist:'بصريات',Berber:'حلاقون',Kozmetik:'تجميل',Fitness:'لياقة',Arsim:'تعليم',Banke:'بنوك',Noter:'عدل',Avokat:'محامون',Inxhinjer:'مهندسون',Agjenci:'سياحة',Ujsjelles:'مياه',Lavazh:'غسيل',AutoPjes:'قطع',Dyqan:'متاجر',Shitje:'أونلاين',Events:'فعاليات',Fotograf:'تصوير',Tregti:'تجارة'}},
  ru:{flag:'🇷🇺',lbl:'Русский',cta1:'Исследовать',cta2:'Зарегистрировать',ms:'Скоро',mt:'Скоро открывается',md:'info@mkdmap.com',mb2:'Бесплатно',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Рестораны',Hotel:'Отели',RentCar:'Аренда авто',Kafene:'Кафе',Farmaci:'Аптеки',Elektricist:'Электрики',Hidraulik:'Сантехники',Shepi:'Дом. услуги',Pllaka:'Плитка',Mobileri:'Мебель',MobilShop:'Телефоны',IT:'ИТ',Klinik:'Клиники',Dentist:'Стоматологи',Okullist:'Оптики',Berber:'Барбершопы',Kozmetik:'Косметика',Fitness:'Фитнес',Arsim:'Образование',Banke:'Банки',Noter:'Нотариусы',Avokat:'Адвокаты',Inxhinjer:'Инженеры',Agjenci:'Туризм',Ujsjelles:'Вода',Lavazh:'Автомойка',AutoPjes:'Автозапчасти',Dyqan:'Магазины',Shitje:'Онлайн',Events:'Мероприятия',Fotograf:'Фотография',Tregti:'Торговля'}},
  ro:{flag:'🇷🇴',lbl:'Română',cta1:'Explorează',cta2:'Înregistrează',ms:'În curând',mt:'În curând',md:'info@mkdmap.com',mb2:'Gratuit',fcp:'© 2025 mkdmap.com',
    cats:{Restorant:'Restaurante',Hotel:'Hoteluri',RentCar:'Închirieri',Kafene:'Cafenele',Farmaci:'Farmacii',Elektricist:'Electricieni',Hidraulik:'Instalatori',Shepi:'Servicii Casnice',Pllaka:'Gresie',Mobileri:'Mobilă',MobilShop:'Telefoane',IT:'IT',Klinik:'Clinici',Dentist:'Stomatologi',Okullist:'Optici',Berber:'Frizerii',Kozmetik:'Cosmetică',Fitness:'Fitness',Arsim:'Educație',Banke:'Bănci',Noter:'Notari',Avokat:'Avocați',Inxhinjer:'Ingineri',Agjenci:'Agenții',Ujsjelles:'Apă',Lavazh:'Spălătorie',AutoPjes:'Piese Auto',Dyqan:'Magazine',Shitje:'Online',Events:'Evenimente',Fotograf:'Fotografie',Tregti:'Comerț'}}
};
const CATS=[
  {k:'Restorant',i:'🍽'},{k:'Hotel',i:'🏨'},{k:'RentCar',i:'🚗'},{k:'Kafene',i:'☕'},
  {k:'Farmaci',i:'💊'},{k:'Elektricist',i:'⚡'},{k:'Hidraulik',i:'🔧'},{k:'Shepi',i:'🏠'},
  {k:'Pllaka',i:'🪟'},{k:'Mobileri',i:'🛋'},{k:'MobilShop',i:'📱'},{k:'IT',i:'🖥'},
  {k:'Klinik',i:'🏥'},{k:'Dentist',i:'🦷'},{k:'Okullist',i:'👁'},{k:'Berber',i:'💇'},
  {k:'Kozmetik',i:'💅'},{k:'Fitness',i:'🏋'},{k:'Arsim',i:'🎓'},{k:'Banke',i:'🏦'},
  {k:'Noter',i:'⚖'},{k:'Avokat',i:'👔'},{k:'Inxhinjer',i:'🏗'},{k:'Agjenci',i:'🌐'},
  {k:'Ujsjelles',i:'🚿'},{k:'Lavazh',i:'🚘'},{k:'AutoPjes',i:'🔩'},{k:'Dyqan',i:'🛒'},
  {k:'Shitje',i:'🛍'},{k:'Events',i:'🎪'},{k:'Fotograf',i:'📸'},{k:'Tregti',i:'🏪'},
];
let lang='sq';
const t=k=>TR[lang]?.[k]??TR.sq[k]??'';
const cn=k=>(TR[lang]?.cats??TR.sq.cats)[k]??k;

/* LANG */
let lO=false;
const bLD=()=>document.getElementById('lDd').innerHTML=Object.entries(TR).map(([k,v])=>`<div class="li ${k===lang?'active':''}" onclick="sL('${k}')">${v.flag} ${v.lbl}<span style="font-size:.55rem;color:var(--t4)">${k.toUpperCase()}</span></div>`).join('');
function tgL(){lO=!lO;document.getElementById('lDd').classList.toggle('open',lO);document.getElementById('lBtn').classList.toggle('open',lO);bLD()}
function sL(l){lang=l;lO=false;document.getElementById('lDd').classList.remove('open');document.getElementById('lBtn').classList.remove('open');document.getElementById('lLbl').textContent=TR[l].flag+' '+l.toUpperCase();document.body.dir=l==='ar'?'rtl':'ltr';document.querySelectorAll('[data-t]').forEach(el=>{const v=t(el.dataset.t);if(v)el.textContent=v});document.querySelectorAll('[data-ph]').forEach(el=>{const v=t(el.dataset.ph);if(v)el.placeholder=v});bC(document.getElementById('cSr').value)}
document.addEventListener('click',e=>{if(lO&&!e.target.closest('.lw')){lO=false;document.getElementById('lDd').classList.remove('open');document.getElementById('lBtn').classList.remove('open')}});

/* CATEGORIES */
function bC(f=''){
  const list=f?CATS.filter(c=>cn(c.k).toLowerCase().includes(f.toLowerCase())):CATS;
  document.getElementById('cGrid').innerHTML=list.map(c=>`<a class="ct" href="#" onclick="oM('${c.k}','${c.i}');return false;"><span class="cti">${c.i}</span><span class="ctn">${cn(c.k)}</span><span class="cts">Coming Soon</span></a>`).join('');
}
function fC(){bC(document.getElementById('cSr').value)}

/* MODAL */
function oM(k,i){document.getElementById('mIco').textContent=i;document.getElementById('mIco2').textContent=i;document.getElementById('mTit').textContent=cn(k);document.querySelectorAll('#mBg [data-t]').forEach(el=>{const v=t(el.dataset.t);if(v)el.textContent=v});document.getElementById('mBg').classList.add('open');document.body.style.overflow='hidden'}
function cM(){document.getElementById('mBg').classList.remove('open');document.body.style.overflow=''}
function cMBg(e){if(e.target===document.getElementById('mBg'))cM()}
document.addEventListener('keydown',e=>{if(e.key==='Escape')cM()});

/* NAV */
window.addEventListener('scroll',()=>document.querySelector('nav').style.background=scrollY>40?'rgba(2,3,10,.9)':'rgba(2,3,10,.85)');

/* CURSOR */
const c1=document.getElementById('cur'),c2=document.getElementById('cur2');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;c1.style.left=mx+'px';c1.style.top=my+'px'});
(function a(){rx+=(mx-rx)*.1;ry+=(my-ry)*.1;c2.style.left=rx+'px';c2.style.top=ry+'px';requestAnimationFrame(a)})();
document.querySelectorAll('a,button,.ct,.wc,.hc,.cc').forEach(el=>{
  el.addEventListener('mouseenter',()=>document.body.classList.add('hov'));
  el.addEventListener('mouseleave',()=>document.body.classList.remove('hov'));
});

/* 3D TILT */
document.addEventListener('mousemove',e=>{
  document.querySelectorAll('.ct,.wc').forEach(el=>{
    const r=el.getBoundingClientRect();
    if(e.clientX>r.left-30&&e.clientX<r.right+30&&e.clientY>r.top-30&&e.clientY<r.bottom+30){
      const x=(e.clientX-r.left-r.width/2)/(r.width/2),y=(e.clientY-r.top-r.height/2)/(r.height/2);
      el.style.transform=`perspective(500px) rotateX(${-y*5}deg) rotateY(${x*5}deg) translateY(-5px)`;
    } else el.style.transform='';
  });
});

/* FORM */
function onSb(e){e.preventDefault();const b=e.target.querySelector('.cfb');b.textContent='✓ Dërguar!';b.style.background='#2a7a50';setTimeout(()=>{b.textContent=t('cfsub');b.style.background='';e.target.reset()},3000)}

bC();
</script>
</body>
</html>
