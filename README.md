<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Од Золбоогоос Энэрэл рүү</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,400&family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<style>
/* ===== COLORS & FONTS (taken from the reference design) ===== */
:root{
  --bg:#02040a; --burgundy:#31000f; --crimson:#e11d48; --crimson-d:#be123c;
  --rose:#fecdd3; --violet:#9333ea; --text:#f1f5f9; --muted:#94a3b8;
  --serif:'Playfair Display',Georgia,serif; --corm:'Cormorant Garamond',Georgia,serif;
  --sans:'Inter',system-ui,sans-serif;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;scroll-padding-top:90px}
body{background:var(--bg);color:var(--text);font-family:var(--sans);overflow-x:hidden;line-height:1.6}
::selection{background:var(--crimson-d)}
::-webkit-scrollbar{width:6px}::-webkit-scrollbar-track{background:var(--bg)}::-webkit-scrollbar-thumb{background:var(--burgundy);border-radius:3px}
a{color:inherit;text-decoration:none}
button{font-family:inherit;cursor:pointer;color:inherit}
:focus-visible{outline:2px solid var(--rose);outline-offset:3px}

/* ===== BACKGROUND: particles, glow lights, mouse glow ===== */
#stars{position:fixed;inset:0;z-index:0;pointer-events:none}
.orb{position:fixed;border-radius:50%;pointer-events:none;z-index:0;filter:blur(140px)}
.orb.a{top:-10%;left:-10%;width:50vw;height:50vw;background:rgba(49,0,15,.45);animation:pulse 3s infinite ease-in-out}
.orb.b{bottom:-10%;right:-10%;width:60vw;height:60vw;background:rgba(59,7,100,.3)}
@keyframes pulse{0%,100%{opacity:.5;transform:scale(1)}50%{opacity:1;transform:scale(1.05)}}
#mouseGlow{position:fixed;width:420px;height:420px;margin:-210px 0 0 -210px;border-radius:50%;z-index:0;pointer-events:none;
  background:radial-gradient(circle,rgba(225,29,72,.16),transparent 65%);transition:transform .15s ease-out}

/* ===== GLASS STYLES ===== */
.glass{background:linear-gradient(135deg,rgba(255,255,255,.05),rgba(255,255,255,.01));backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);
  border:1px solid rgba(255,255,255,.1);box-shadow:0 15px 35px rgba(0,0,0,.5),0 0 20px rgba(190,18,60,.15)}
.wrap{position:relative;z-index:1;max-width:1300px;margin:0 auto;padding:0 clamp(16px,4vw,48px)}

/* ===== NAVIGATION ===== */
header{position:fixed;top:0;left:0;right:0;z-index:20;padding:14px clamp(12px,3vw,40px)}
nav{max-width:1300px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;padding:12px 24px;border-radius:16px;
  background:rgba(6,9,20,.65);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);border:1px solid rgba(255,255,255,.1);box-shadow:0 20px 50px rgba(0,0,0,.5)}
.brand{display:flex;align-items:center;gap:12px}
.mono{width:40px;height:40px;border-radius:50%;padding:1px;background:linear-gradient(45deg,var(--burgundy),var(--crimson-d),var(--violet))}
.mono span{display:flex;width:100%;height:100%;border-radius:50%;background:var(--bg);align-items:center;justify-content:center;font:600 17px var(--corm);color:#fecdd3;letter-spacing:.05em}
.brand b{font:300 20px var(--corm);letter-spacing:.25em;text-transform:uppercase}
.links{display:flex;gap:clamp(14px,2.2vw,32px)}
.links a{position:relative;font-size:12px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);padding:4px 0;transition:color .3s}
.links a::after{content:"";position:absolute;left:0;bottom:0;height:2px;width:0;border-radius:2px;background:linear-gradient(90deg,var(--crimson),var(--violet));transition:width .3s}
.links a:hover,.links a.active{color:#fff}
.links a:hover::after,.links a.active::after{width:100%}
.nav-right{display:flex;align-items:center;gap:14px}
.date{text-align:right;padding-right:14px;border-right:1px solid rgba(255,255,255,.1);font:italic 12px var(--serif);color:#fecdd3}
.date small{display:block;font:10px var(--sans);letter-spacing:.2em;text-transform:uppercase;color:var(--muted)}
.chip{padding:8px 12px;border-radius:12px;font-size:11px;letter-spacing:.1em;display:flex;gap:8px;align-items:center;color:#cbd5e1;transition:.3s}
.chip:hover{color:#fff;border-color:rgba(255,255,255,.25)}
.burger{display:none;width:40px;height:40px;border-radius:12px;font-size:18px}

/* ===== SECTIONS (all share one continuous background) ===== */
section{position:relative;z-index:1;padding:110px 0}
.hero{min-height:100vh;display:flex;align-items:center;padding-top:120px}
.hero .wrap{display:grid;grid-template-columns:7fr 5fr;gap:40px;align-items:center;width:100%}
.tag{display:inline-flex;align-items:center;gap:12px;padding:6px 16px;border-radius:99px;font-size:11px;letter-spacing:.25em;text-transform:uppercase;color:rgba(254,205,211,.9);border-color:rgba(244,63,94,.25)}
.tag i{width:8px;height:8px;border-radius:50%;background:var(--crimson);animation:ping 1.6s infinite}
@keyframes ping{0%{box-shadow:0 0 0 0 rgba(225,29,72,.7)}100%{box-shadow:0 0 0 10px transparent}}
h1{font:400 clamp(40px,6.4vw,76px)/1.1 var(--serif);letter-spacing:-.01em;margin:28px 0 16px;max-width:680px;
  background:linear-gradient(135deg,#fff,#f3e8ff 40%,#e2e8f0);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
h1 em{font:italic 300 1.05em var(--corm);-webkit-text-fill-color:rgba(254,205,211,.9)}
.sub{font:italic 300 clamp(18px,2.2vw,26px) var(--serif);color:rgba(203,213,225,.8);border-left:2px solid rgba(190,18,60,.5);padding-left:16px}
.lead{max-width:470px;color:var(--muted);font-weight:300;margin:26px 0 34px}
.btn-row{display:flex;flex-wrap:wrap;gap:20px;align-items:center}
.cta{position:relative;border:0;background:none;border-radius:99px;padding:1px;overflow:visible}
.cta::before{content:"";position:absolute;inset:0;border-radius:99px;background:linear-gradient(90deg,var(--crimson-d),var(--violet),#f43f5e);filter:blur(10px);opacity:.7;transition:.5s}
.cta:hover::before{opacity:1;filter:blur(16px)}
.cta span{position:relative;display:flex;align-items:center;gap:16px;padding:15px 30px;border-radius:99px;background:rgba(2,4,10,.9);border:1px solid rgba(255,255,255,.2);
  font-size:13px;font-weight:600;letter-spacing:.2em;text-transform:uppercase;transition:.3s}
.cta:hover span{transform:scale(1.03)}
.cta i{font-style:normal;width:32px;height:32px;border-radius:50%;background:rgba(190,18,60,.85);display:grid;place-items:center;transition:transform .3s}
.cta:hover i{transform:translateX(5px)}
.ghost{padding:15px 24px;border-radius:99px;font-size:12px;letter-spacing:.2em;text-transform:uppercase;color:#cbd5e1;background:rgba(15,10,25,.45);border:1px solid rgba(255,255,255,.1);transition:.3s}
.ghost:hover{color:#fff;border-color:rgba(255,255,255,.3);transform:translateY(-2px)}
.eq{display:flex;align-items:center;gap:14px;margin-top:34px;font-size:11px;letter-spacing:.2em;text-transform:uppercase;color:var(--muted)}
.bars{display:flex;align-items:flex-end;gap:4px;height:26px;padding:4px 8px;border-radius:6px}
.bars b{width:4px;border-radius:4px;animation:bar 1.2s ease-in-out infinite alternate;height:4px}
.bars b:nth-child(1){background:#f43f5e;animation-delay:.1s}.bars b:nth-child(2){background:#a855f7;animation-delay:.3s}
.bars b:nth-child(3){background:var(--crimson);animation-delay:.5s}.bars b:nth-child(4){background:#f472b6;animation-delay:.2s}
@keyframes bar{to{height:18px}}
.paused .bars b{animation-play-state:paused}

/* ===== PHOTO FRAMES (hero + gallery use the same .photo box) ===== */
.stack{position:relative;height:500px;max-width:430px;margin:auto;width:100%}
.frame{position:absolute;padding:12px;border-radius:20px;cursor:pointer;transition:all .6s cubic-bezier(.16,1,.3,1);border-color:rgba(255,255,255,.15)}
.frame:hover{transform:translateY(-8px) scale(1.02) rotate(0)!important;box-shadow:0 25px 50px -12px rgba(225,29,72,.4),0 0 30px rgba(168,85,247,.2)}
.f1{top:0;left:0;width:250px;height:340px;transform:rotate(-6deg);z-index:1}
.f2{bottom:0;right:0;width:270px;height:380px;transform:rotate(3deg);z-index:2}
.photo{position:relative;width:100%;height:100%;border-radius:12px;overflow:hidden;background:#030712 center/cover no-repeat;display:flex;flex-direction:column;justify-content:space-between;padding:16px}
.photo::before{content:"";position:absolute;inset:0;background:linear-gradient(to top,#02040a,rgba(74,4,25,.25),transparent);z-index:1}
.photo .sil{position:absolute;inset:0;background:radial-gradient(circle at 50% 38%,var(--glow,rgba(225,29,72,.45)),transparent 55%)}
.photo .sil::after{content:"";position:absolute;left:32%;right:32%;top:20%;bottom:0;border-radius:50% 50% 0 0/35% 35% 0 0;background:rgba(255,255,255,.06)}
.photo.has-img .sil{display:none}
.photo>*{position:relative;z-index:2}.photo::before{z-index:1}
.photo .top{display:flex;justify-content:space-between;font-size:10px;letter-spacing:.2em;color:rgba(254,205,211,.75)}
.photo .cap{font:italic 13px var(--serif);color:#e2e8f0}
.photo .cap small{display:block;font:10px var(--sans);letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin-top:2px}

/* ===== SHARED SECTION HEADINGS ===== */
.head{text-align:center;margin-bottom:56px}
.head p{font-size:11px;letter-spacing:.3em;text-transform:uppercase;color:#fb7185;margin-bottom:12px}
h2{font:400 clamp(30px,4.4vw,52px)/1.15 var(--serif);background:linear-gradient(135deg,#fff,#fecdd3 50%,#fda4af);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.thread{position:absolute;left:50%;top:0;bottom:0;width:1px;background:linear-gradient(transparent,rgba(225,29,72,.35),transparent);z-index:0}

/* ===== OUR STORY (timeline) ===== */
.timeline{max-width:760px;margin:auto;position:relative}
.timeline::before{content:"";position:absolute;left:14px;top:8px;bottom:8px;width:1px;background:linear-gradient(var(--crimson),var(--violet),transparent)}
.chapter{position:relative;padding:0 0 44px 52px}
.chapter::before{content:"";position:absolute;left:8px;top:8px;width:13px;height:13px;border-radius:50%;background:var(--bg);border:2px solid var(--crimson);box-shadow:0 0 14px var(--crimson)}
.chapter time{font:italic 15px var(--serif);color:#fda4af}
.chapter h3{font:400 26px var(--serif);margin:4px 0 8px}
.chapter p{color:var(--muted);font-weight:300;max-width:60ch}

/* ===== REASONS ===== */
.grid3{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
.reason{position:relative;overflow:hidden;padding:30px;border-radius:20px;transition:.5s cubic-bezier(.16,1,.3,1)}
.reason::before{content:"";position:absolute;top:0;left:-120%;width:60%;height:100%;background:linear-gradient(100deg,transparent,rgba(255,255,255,.08),transparent);transition:left .9s}
.reason:hover::before{left:130%}
.reason:hover{transform:translateY(-8px);border-color:rgba(244,63,94,.35)}
.reason h3{font:italic 400 22px var(--serif);color:var(--rose);margin-bottom:10px}
.reason p{color:var(--muted);font-weight:300;font-size:15px}

/* ===== MEMORIES (gallery) ===== */
.gallery{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
.gallery .frame{position:relative;height:340px;transform:none}
.gallery .frame:nth-child(2){margin-top:34px}
.gallery .frame:nth-child(4){margin-top:-34px}

/* ===== LETTER (animated envelope) ===== */
.env-wrap{display:flex;flex-direction:column;align-items:center;gap:22px}
.envelope{position:relative;width:min(420px,88vw);height:270px;margin-top:150px;cursor:pointer;border:0;background:none;transition:transform .5s,margin .8s}
.envelope:hover{transform:translateY(-6px)}
.env-back,.env-front,.flap{position:absolute;left:0;right:0}
.env-back{inset:0;background:#4a0419;border-radius:6px 6px 12px 12px;box-shadow:0 30px 60px rgba(0,0,0,.6),0 0 50px -10px rgba(225,29,72,.35)}
.env-front{bottom:0;height:100%;border-radius:6px 6px 12px 12px;z-index:3;pointer-events:none;
  background:linear-gradient(to top right,#5c0620 50%,transparent 50%) left/50% 100% no-repeat,linear-gradient(to top left,#6b0a26 50%,transparent 50%) right/50% 100% no-repeat}
.env-front::after{content:"";position:absolute;left:0;right:0;bottom:0;height:60%;background:linear-gradient(#7a0f2e,#4a0419);clip-path:polygon(0 100%,50% 0,100% 100%);opacity:0}
.flap{top:0;height:55%;background:#7a0f2e;clip-path:polygon(0 0,100% 0,50% 100%);transform-origin:top;transition:transform .8s ease,z-index 0s .4s;z-index:4;border-radius:6px 6px 0 0}
.seal{position:absolute;left:50%;top:40%;transform:translate(-50%,-50%);width:46px;height:46px;border-radius:50%;z-index:5;background:radial-gradient(circle at 35% 30%,#fb7185,#be123c 60%,#7f1238);
  display:grid;place-items:center;font:600 15px var(--corm);box-shadow:0 4px 14px rgba(0,0,0,.5);transition:opacity .4s}
.paper{position:absolute;left:6%;right:6%;bottom:10px;top:10px;padding:26px 28px;border-radius:6px;z-index:2;overflow:hidden;
  background:linear-gradient(#f8f0e6,#efe3d3);color:#3a1620;transition:transform 1s ease .35s,z-index 0s .5s;box-shadow:0 6px 20px rgba(0,0,0,.35)}
.paper h4{font:italic 400 22px var(--corm);margin-bottom:8px}
.paper p{font:400 17px/1.5 var(--corm)}
.envelope.open{margin-top:290px}
.envelope.open .flap{transform:rotateX(180deg);z-index:1}
.envelope.open .seal{opacity:0}
.envelope.open .paper{z-index:3;transform:translateY(-330px);height:390px;bottom:auto;overflow:auto}
.envelope.open .env-front{z-index:4}
.env-hint{font:italic 15px var(--serif);color:var(--muted)}
.letter-overlay{position:fixed;inset:0;z-index:20;background:rgba(2,4,10,.32);backdrop-filter:blur(0);-webkit-backdrop-filter:blur(0);opacity:0;pointer-events:none;transition:opacity .7s ease,backdrop-filter .7s ease,-webkit-backdrop-filter .7s ease}
.letter-overlay.show{opacity:1;backdrop-filter:blur(9px);-webkit-backdrop-filter:blur(9px)}
.envelope.open{z-index:21}
.paper{border:1px solid rgba(255,255,255,.35);box-shadow:0 10px 35px rgba(0,0,0,.45),0 0 28px rgba(251,113,133,.16);opacity:0;transition:transform 1s ease .35s,z-index 0s .5s,opacity .8s ease .45s}
.envelope.open .paper{opacity:1}

/* ===== MUSIC PLAYER ===== */
.player{max-width:560px;margin:auto;padding:30px;border-radius:26px}
.now{display:flex;gap:22px;align-items:center}
.disc{width:104px;height:104px;border-radius:50%;flex:none;background:conic-gradient(from 0deg,#31000f,#be123c,#4c1d95,#31000f);border:1px solid rgba(255,255,255,.15);position:relative;animation:spin 8s linear infinite;animation-play-state:paused}
.disc::after{content:"";position:absolute;inset:38%;border-radius:50%;background:var(--bg)}
.playing .disc{animation-play-state:running}
@keyframes spin{to{transform:rotate(360deg)}}
.now h3{font:italic 400 24px var(--serif)}
.now p{color:var(--muted);font-size:13px}
.progress{margin:26px 0 8px;height:6px;border-radius:6px;background:rgba(255,255,255,.1);cursor:pointer;position:relative}
.progress div{height:100%;width:0;border-radius:6px;background:linear-gradient(90deg,var(--crimson),var(--violet))}
.times{display:flex;justify-content:space-between;font-size:11px;color:var(--muted);letter-spacing:.1em}
.ctrl{display:flex;justify-content:center;align-items:center;gap:22px;margin:16px 0 22px}
.ctrl button{width:46px;height:46px;border-radius:50%;font-size:16px;transition:.3s}
.ctrl button:hover{transform:scale(1.1);color:#fff}
.ctrl .play{width:64px;height:64px;background:rgba(190,18,60,.85);border:0;font-size:20px;box-shadow:0 0 30px rgba(225,29,72,.4)}
.tracks button{display:flex;width:100%;justify-content:space-between;padding:12px 14px;border:0;border-radius:12px;background:none;color:var(--muted);font-size:14px;transition:.3s;text-align:left}
.tracks button:hover,.tracks button.on{background:rgba(255,255,255,.06);color:#fff}
.tracks button.on span:first-child{color:#fda4af}
.volume-row{display:flex;align-items:center;gap:12px;margin-top:18px;color:var(--muted);font-size:12px}
.volume-row input{flex:1;accent-color:#be123c;cursor:pointer}
#volumeText{min-width:38px;text-align:right;font-variant-numeric:tabular-nums}
.audio-tools{display:flex;justify-content:center;align-items:center;gap:12px;margin-top:16px;flex-wrap:wrap}
.file-btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:10px 15px;border-radius:12px;border:1px solid rgba(255,255,255,.12);background:rgba(255,255,255,.04);color:#cbd5e1;font-size:12px;cursor:pointer;transition:.3s}
.file-btn:hover{color:#fff;border-color:rgba(255,255,255,.3);transform:translateY(-1px)}
#fileName{max-width:100%;font-size:11px;color:var(--muted);text-align:center;word-break:break-word}
.audio-status{min-height:20px;margin-top:10px;text-align:center;font-size:12px;color:#fda4af}

/* ===== FINAL MESSAGE ===== */
.final{text-align:center;padding-bottom:140px}
.sign{font:italic 300 clamp(20px,3vw,30px) var(--corm);color:var(--rose)}
.final h2{font-size:clamp(28px,4.6vw,56px);max-width:760px;margin:0 auto 40px}
.final h2 em{display:block;font:italic 300 1em var(--corm);-webkit-text-fill-color:rgba(254,205,211,.9)}
footer{position:relative;z-index:1;text-align:center;padding:30px 20px;border-top:1px solid rgba(255,255,255,.05);font:italic 14px var(--serif);color:rgba(148,163,184,.8)}

/* ===== FULLSCREEN VIEWER ===== */
.viewer{position:fixed;inset:0;z-index:50;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:16px;padding:20px;background:rgba(2,4,10,.92);backdrop-filter:blur(20px);opacity:0;pointer-events:none;transition:opacity .4s}
.viewer.show{opacity:1;pointer-events:auto}
.viewer .big{width:min(90vw,520px);height:min(70vh,660px);border-radius:16px;transform:scale(.94);transition:transform .4s}
.viewer.show .big{transform:scale(1)}
.viewer .photo{padding:0}.viewer .photo .top,.viewer .photo .cap{display:none}
.vcap{font:italic 18px var(--serif);text-align:center}
.vbtn{position:absolute;width:44px;height:44px;border-radius:50%;font-size:18px;color:#cbd5e1}
.vbtn:hover{color:#fff}
.vclose{top:22px;right:22px}.vprev{left:22px;top:50%}.vnext{right:22px;top:50%}

/* ===== SCROLL REVEAL ===== */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .9s ease,transform .9s cubic-bezier(.16,1,.3,1)}
.reveal.in{opacity:1;transform:none}

/* ===== MOBILE ===== */
@media(max-width:900px){
  .hero .wrap{grid-template-columns:1fr}
  .grid3,.gallery{grid-template-columns:1fr 1fr}
  .date{display:none}
  .links{position:absolute;top:78px;left:14px;right:14px;flex-direction:column;gap:18px;padding:22px;border-radius:16px;background:rgba(6,9,20,.95);border:1px solid rgba(255,255,255,.1);
    opacity:0;pointer-events:none;transform:translateY(-8px);transition:.3s}
  .links.open{opacity:1;pointer-events:auto;transform:none}
  .burger{display:block}
}
@media(max-width:560px){
  .grid3,.gallery{grid-template-columns:1fr}
  .gallery .frame{margin:0!important}
  .brand b,.chip span{display:none}
  .stack{height:440px}.f1{width:210px;height:290px}.f2{width:230px;height:330px}
  .now{flex-direction:column;text-align:center}
  .vprev,.vnext{top:auto;bottom:24px}
}
@media(prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}html{scroll-behavior:auto}.reveal{opacity:1;transform:none}}
</style>
</head>
<body>

<!-- Background layers -->
<canvas id="stars"></canvas>
<div class="orb a"></div><div class="orb b"></div>
<div id="mouseGlow"></div>

<!-- ===== NAVIGATION ===== -->
<header>
  <nav>
    <a href="#home" class="brand">
      <div class="mono"><span>О &amp; Э</span></div><b>Энэрэл рүү</b>
    </a>
    <div class="links" id="links">
      <a href="#home" class="active">Нүүр</a>
      <a href="#story">Түүх</a>
      <a href="#reasons">Үг</a>
      <a href="#memories">Дурсамж</a>
      <a href="#letter">Захиа</a>
      <a href="#music">Хөгжим</a>
      <a href="#final">Төгсгөл</a>
    </div>
    <div class="nav-right">
      <div class="date"><small>Хувийн захиа</small>Од Золбоогоос</div>
      <button class="chip glass" id="soundChip" aria-label="Хөгжим тоглуулагч руу очих"><span>♪</span><span id="chipName">АНХНЫ ДУУ</span></button>
      <button class="burger glass" id="burger" aria-label="Цэс нээх">☰</button>
    </div>
  </nav>
</header>

<!-- ===== HERO ===== -->
<section class="hero" id="home">
  <div class="wrap">
    <div>
      <div class="tag glass reveal"><i></i>Од Золбоогоос Энэрэл рүү</div>
      <h1 class="reveal">Чамд хэлэх зүйл <em>надад байна.</em></h1>
      <p class="sub reveal">“Энэ бол Од Золбоогоос Энэрэлд зориулсан жижигхэн түүх.”</p>
      <p class="lead reveal">Зөвхөн чамд зориулж бичсэн, хэн ч мэдэхгүй жижигхэн орон зай.</p>
      <div class="btn-row reveal">
        <button class="cta" id="enterBtn"><span>Эхлүүлэх <i>→</i></span></button>
        <button class="ghost" id="archiveBtn">Дурсамжийг үзэх</button>
      </div>
      <div class="eq reveal" id="eq"><div class="bars glass"><b></b><b></b><b></b><b></b></div><span id="eqText">Хөгжим зогссон</span></div>
    </div>

    <div class="stack reveal">
      <!-- HERO PHOTO 1: to use your own image, set data-img="images/her.jpg" (path to your file) -->
      <div class="frame glass f1" data-photo data-img="" data-title="Чиний зураг" data-sub="Энд тайлбар бич">
        <div class="photo" style="--glow:rgba(225,29,72,.45)"><div class="sil"></div>
          <div class="top"><span>№ 01</span><span>♡</span></div>
          <div class="cap">Чиний зураг<small>Энд тайлбар бич</small></div></div>
      </div>
      <!-- HERO PHOTO 2: to use your own image, set data-img="images/together.jpg" -->
      <div class="frame glass f2" data-photo data-img="" data-title="Бидний зураг" data-sub="Энд тайлбар бич">
        <div class="photo" style="--glow:rgba(147,51,234,.5)"><div class="sil"></div>
          <div class="top"><span>№ 02</span><span>♡</span></div>
          <div class="cap">Бидний зураг<small>Энд тайлбар бич</small></div></div>
      </div>
    </div>
  </div>
</section>

<!-- ===== 1. OUR STORY ===== -->
<section id="story">
  <div class="wrap">
    <div class="head reveal"><p>Нэгдүгээр бүлэг</p><h2>Бидний түүх</h2></div>
    <div class="timeline">
      <!-- EDIT: replace these short texts with your real memories and dates -->
      <div class="chapter reveal"><time>Эхлэл</time><h3>Анх танилцсан үе</h3><p>Тэр өдрийг би өөрөөр санаж байна. Ердөө л нэг энгийн өдөр байсан ч чамайг харсан агшнаас хойш бүх зүйл жаахан өөр болсон.</p></div>
      <div class="chapter reveal"><time>Дараа нь</time><h3>Анхны яриа</h3><p>Юу ярьснаа бүр нарийн санахгүй ч, ярьж дуусахад цаг хэр өнгөрснийг анзаараагүй байсныг санаж байна.</p></div>
      <div class="chapter reveal"><time>Цаг хугацаа өнгөрөх тусам</time><h3>Дурсамжууд</h3><p>Том зүйл биш, жижиг зүйлс. Хамт идсэн хоол, хамт инээсэн явдал, хоорондоо ойлголцсон чимээгүй мөчүүд.</p></div>
      <div class="chapter reveal"><time>Одоо</time><h3>Онцгой мөчүүд</h3><p>Заримыг нь зурагт авч үлдсэн, заримыг нь зөвхөн зүрхэндээ. Хоёулаа адилхан үнэтэй.</p></div>
    </div>
  </div>
</section>

<!-- ===== 2. REASONS ===== -->
<section id="reasons">
  <div class="wrap">
    <div class="head reveal"><p>Хоёрдугаар бүлэг</p><h2>Чамд хэлэх үг</h2></div>
    <!-- EDIT: change these reasons -->
    <div class="grid3">
      <!-- EDIT: change these short messages -->
      <div class="reason glass reveal"><h3>Цаг</h3><p>Чамтай ярихад цаг хурдан өнгөрдөг.</p></div>
      <div class="reason glass reveal"><h3>Би</h3><p>Чи намайг өөрөөр нь байлгадаг.</p></div>
      <div class="reason glass reveal"><h3>Энгийн өдөр</h3><p>Хамгийн энгийн өдрийг ч чи онцгой болгодог.</p></div>
      <div class="reason glass reveal"><h3>Инээд</h3><p>Чиний инээд миний өдрийг өөрчилдөг.</p></div>
      <div class="reason glass reveal"><h3>Баярлалаа</h3><p>Надтай хамт байсанд баярлалаа.</p></div>
      <div class="reason glass reveal"><h3>Үнэлдэг</h3><p>Би чамайг үнэлдэг. Үргэлж.</p></div>
    </div>
  </div>
</section>

<!-- ===== 3. MEMORIES ===== -->
<section id="memories">
  <div class="wrap">
    <div class="head reveal"><p>Гуравдугаар бүлэг</p><h2>Дурсамжууд</h2></div>
    <!--
      HOW TO ADD YOUR PHOTOS:
      For each frame below, put your image path inside data-img="" (for example data-img="images/photo1.jpg").
      Change data-title and data-sub to set the caption. Click any photo to open it fullscreen.
      Add more photos by copying one whole <div class="frame ..."> block.
    -->
    <div class="gallery">
      <!-- PHOTO 1: put your image path in data-img="" (e.g. data-img="images/photo1.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 1" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(225,29,72,.4)"><div class="sil"></div><div class="top"><span>№ 01</span></div><div class="cap">Дурсамж 1<small>Энд тайлбар бич</small></div></div></div>
      <!-- PHOTO 2: put your image path in data-img="" (e.g. data-img="images/photo2.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 2" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(147,51,234,.45)"><div class="sil"></div><div class="top"><span>№ 02</span></div><div class="cap">Дурсамж 2<small>Энд тайлбар бич</small></div></div></div>
      <!-- PHOTO 3: put your image path in data-img="" (e.g. data-img="images/photo3.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 3" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(244,63,94,.4)"><div class="sil"></div><div class="top"><span>№ 03</span></div><div class="cap">Дурсамж 3<small>Энд тайлбар бич</small></div></div></div>
      <!-- PHOTO 4: put your image path in data-img="" (e.g. data-img="images/photo4.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 4" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(190,18,60,.5)"><div class="sil"></div><div class="top"><span>№ 04</span></div><div class="cap">Дурсамж 4<small>Энд тайлбар бич</small></div></div></div>
      <!-- PHOTO 5: put your image path in data-img="" (e.g. data-img="images/photo5.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 5" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(168,85,247,.45)"><div class="sil"></div><div class="top"><span>№ 05</span></div><div class="cap">Дурсамж 5<small>Энд тайлбар бич</small></div></div></div>
      <!-- PHOTO 6: put your image path in data-img="" (e.g. data-img="images/photo6.jpg") -->
      <div class="frame glass reveal" data-photo data-img="" data-title="Дурсамж 6" data-sub="Энд тайлбар бич" tabindex="0">
        <div class="photo" style="--glow:rgba(225,29,72,.45)"><div class="sil"></div><div class="top"><span>№ 06</span></div><div class="cap">Дурсамж 6<small>Энд тайлбар бич</small></div></div></div>
    </div>
  </div>
</section>

<!-- ===== 4. LETTER ===== -->
<section id="letter">
  <div class="wrap">
    <div class="head reveal"><p>Дөрөвдүгээр бүлэг</p><h2>Захиа</h2></div>
    <div class="env-wrap reveal">
      <button class="envelope" id="envelope" aria-expanded="false" aria-label="Захидлыг нээх">
        <div class="env-back"></div>
        <!-- Захианы текстийг эндээс өөрчилж болно. -->
        <div class="paper">
          <h4>Сайн уу, Энэрэл.</h4>
          <p>Энэ бүхнийг шууд хэлэхээс жаахан санаа зовдог болохоор энд бичлээ.</p>
          <p style="margin-top:10px">Чамтай өнгөрүүлсэн жижигхэн мөчүүд хүртэл надад сайхан дурсамж болж үлдсэн. Заримдаа юу хэлэхээ мэдэхгүй байсан ч чамтай ярилцах бүрд өдөр арай өөр болдог.</p>
          <p style="margin-top:10px">Би чамаас ямар нэгэн хариу шаардахгүй. Зүгээр л чамд энэ бүхнийг мэдээсэй гэж хүссэн юм.</p>
          <p style="margin-top:10px">Чи миний хувьд онцгой хүн.</p>
          <p style="margin-top:10px;text-align:right;font-style:italic">— Од Золбоогоос</p>
        </div>
        <div class="env-front"></div>
        <div class="flap"></div>
        <div class="seal">О</div>
      </button>
      <p class="env-hint" id="envHint">Дугтуйг товшиж нээгээрэй</p>
    </div>
  </div>
</section>

<!-- Захиа нээгдэхэд арын хэсгийг зөөлөн бүдгэрүүлэх backdrop -->
<div class="letter-overlay" id="letterOverlay" aria-hidden="true"></div>

<!-- ===== 5. MUSIC ===== -->
<section id="music">
  <div class="wrap">
    <div class="head reveal"><p>Тавдугаар бүлэг</p><h2>Бидний хөгжим</h2></div>
    <div class="player glass reveal" id="player">
      <div class="now">
        <div class="disc"></div>
        <div>
          <h3 id="tTitle">One Wish</h3>
          <p id="tArtist">Sweet Love</p>
        </div>
      </div>

      <div class="progress" id="progress" role="slider" aria-label="Дууны явц" tabindex="0">
        <div id="bar"></div>
      </div>
      <div class="times">
        <span id="cur">0:00</span>
        <span id="dur">0:00</span>
      </div>

      <div class="ctrl">
        <button class="play" id="playBtn" aria-label="Тоглуулах">▶</button>
      </div>

      <div class="volume-row">
        <span aria-hidden="true">🔊</span>
        <input id="volume" type="range" min="0" max="1" step="0.01" value="0.8" aria-label="Дууны чанга сул">
        <span id="volumeText">80%</span>
      </div>

      <div class="audio-tools">
        <label class="file-btn" for="audioFile">🎵 MP3 сонгох</label>
        <input id="audioFile" type="file" accept="audio/*,.mp3" hidden>
        <span id="fileName">Анхдагч файл: audio/song.mp3</span>
      </div>
      <div class="audio-status" id="audioStatus" role="status" aria-live="polite"></div>

      <!--
        ӨӨРИЙН MP3 ФАЙЛАА ХОЙНО НЬ СОЛИХ: website-ийн folder дотор audio/song.mp3 байрлуул.
        Өөр нэртэй бол доорх JavaScript-ийн track.src утгыг өөрийн файлын нэрээр солино.
        Мөн дээрх “MP3 сонгох” товчоор компьютерээсээ шууд MP3 сонгож болно.
      -->
    </div>
  </div>
</section>

<!-- ===== 6. FINAL MESSAGE ===== -->
<section class="final" id="final">
  <div class="wrap">
    <h2 class="reveal">Энэ бол төгсгөл биш.<em>Зүгээр л бидний түүхийн нэг хэсэг.</em></h2>
    <p class="sign reveal">Энэрэлд — Од Золбоогоос ❤️</p>
  </div>
</section>

<footer>Од Золбоогоос Энэрэл рүү</footer>

<!-- ===== FULLSCREEN IMAGE VIEWER ===== -->
<div class="viewer" id="viewer" role="dialog" aria-modal="true" aria-label="Зураг үзэгч">
  <button class="vbtn glass vclose" id="vclose" aria-label="Хаах">✕</button>
  <button class="vbtn glass vprev" id="vprev" aria-label="Өмнөх зураг">‹</button>
  <button class="vbtn glass vnext" id="vnext" aria-label="Дараах зураг">›</button>
  <div class="big glass" style="padding:10px"><div class="photo" id="vphoto"><div class="sil"></div></div></div>
  <div class="vcap" id="vcap"></div>
</div>

<script>
/* ===== HELPERS ===== */
const $ = (s, el = document) => el.querySelector(s);
const $$ = (s, el = document) => [...el.querySelectorAll(s)];
const reduceMotion = matchMedia('(prefers-reduced-motion: reduce)').matches;

/* ===== 1. FLOATING PARTICLES ===== */
const canvas = $('#stars'), ctx = canvas.getContext('2d');
let W, H, dots = [];
const colors = ['225,29,72', '244,114,182', '255,255,255', '192,132,252'];
function resize() { W = canvas.width = innerWidth; H = canvas.height = innerHeight; }
addEventListener('resize', resize); resize();
function makeDot(burst) {
  return { x: Math.random() * W, y: Math.random() * H, r: Math.random() * 1.8 + .3,
    vx: (Math.random() - .5) * .2, vy: -Math.random() * .3 - .05,
    a: Math.random() * .7 + .1, c: colors[Math.floor(Math.random() * 4)], life: burst ? 80 : Infinity };
}
for (let i = 0; i < 110; i++) dots.push(makeDot());
// Just a few tiny, faint hearts drifting upward
for (let i = 0; i < 8; i++) {
  const h = makeDot(); h.heart = true; h.c = '225,29,72';
  h.r = Math.random() * 2 + 2.5; h.a = Math.random() * .25 + .15; h.vy = -Math.random() * .25 - .1;
  dots.push(h);
}
function loop() {
  ctx.clearRect(0, 0, W, H);
  dots = dots.filter(d => d.life > 0);
  dots.forEach(d => {
    d.x += d.vx; d.y += d.vy; d.life--;
    if (d.life === Infinity && (d.y < 0 || d.x < 0 || d.x > W)) { d.y = H + 10; d.x = Math.random() * W; }
    ctx.fillStyle = `rgba(${d.c},${d.life < 30 ? d.a * d.life / 30 : d.a})`;
    ctx.shadowBlur = d.r > 1 ? 8 : 0; ctx.shadowColor = `rgba(${d.c},.8)`;
    if (d.heart) { ctx.font = `${d.r * 5}px serif`; ctx.fillText('♥', d.x, d.y); }
    else { ctx.beginPath(); ctx.arc(d.x, d.y, d.r, 0, 6.283); ctx.fill(); }
  });
  requestAnimationFrame(loop);
}
if (!reduceMotion) loop();
function burst(x, y) {
  for (let i = 0; i < 40; i++) {
    const d = makeDot(true); d.x = x; d.y = y; d.r = Math.random() * 3 + 1; d.a = 1;
    d.vx = (Math.random() - .5) * 5; d.vy = (Math.random() - .5) * 5; dots.push(d);
  }
}

/* ===== 2. MOUSE-FOLLOWING GLOW ===== */
const glow = $('#mouseGlow');
addEventListener('mousemove', e => { glow.style.transform = `translate(${e.clientX}px,${e.clientY}px)`; });

/* ===== 3. NAVIGATION (active link + mobile menu) ===== */
const links = $('#links');
$('#burger').onclick = () => links.classList.toggle('open');
$$('a', links).forEach(a => a.onclick = () => links.classList.remove('open'));
const navMap = {};
$$('a', links).forEach(a => navMap[a.getAttribute('href').slice(1)] = a);
const navObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      $$('a', links).forEach(a => a.classList.remove('active'));
      navMap[e.target.id]?.classList.add('active');
    }
  });
}, { rootMargin: '-45% 0px -50% 0px' });
$$('section[id]').forEach(s => navObs.observe(s));

/* Hero buttons */
$('#enterBtn').onclick = e => {
  const r = e.currentTarget.getBoundingClientRect();
  burst(r.left + r.width / 2, r.top + r.height / 2);
  setTimeout(() => $('#story').scrollIntoView({ behavior: 'smooth' }), 350);
};
$('#archiveBtn').onclick = () => $('#memories').scrollIntoView({ behavior: 'smooth' });
$('#soundChip').onclick = () => $('#music').scrollIntoView({ behavior: 'smooth' });

/* ===== 4. SCROLL REVEAL ===== */
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); revObs.unobserve(e.target); } });
}, { threshold: .12 });
$$('.reveal').forEach((el, i) => { el.style.transitionDelay = (i % 3) * 90 + 'ms'; revObs.observe(el); });

/* ===== 5. PHOTOS: apply your images + fullscreen viewer ===== */
const photos = $$('[data-photo]');
photos.forEach(p => {
  const src = p.dataset.img;               // <-- your image path from data-img=""
  if (src) { const box = $('.photo', p); box.style.backgroundImage = `url("${src}")`; box.classList.add('has-img'); }
});
const viewer = $('#viewer'), vphoto = $('#vphoto');
let vIndex = 0;
function showPhoto(i) {
  vIndex = (i + photos.length) % photos.length;
  const p = photos[vIndex], src = p.dataset.img;
  vphoto.style.backgroundImage = src ? `url("${src}")` : 'none';
  vphoto.classList.toggle('has-img', !!src);
  vphoto.style.setProperty('--glow', $('.photo', p).style.getPropertyValue('--glow'));
  $('#vcap').textContent = `${p.dataset.title} — ${p.dataset.sub}`;
}
function openViewer(i) { showPhoto(i); viewer.classList.add('show'); $('#vclose').focus(); }
function closeViewer() { viewer.classList.remove('show'); }
photos.forEach((p, i) => {
  p.onclick = () => openViewer(i);
  p.onkeydown = e => { if (e.key === 'Enter') openViewer(i); };
});
$('#vclose').onclick = closeViewer;
$('#vprev').onclick = () => showPhoto(vIndex - 1);
$('#vnext').onclick = () => showPhoto(vIndex + 1);
viewer.onclick = e => { if (e.target === viewer) closeViewer(); };
addEventListener('keydown', e => {
  if (!viewer.classList.contains('show')) return;
  if (e.key === 'Escape') closeViewer();
  if (e.key === 'ArrowLeft') showPhoto(vIndex - 1);
  if (e.key === 'ArrowRight') showPhoto(vIndex + 1);
});

/* ===== 6. ENVELOPE ===== */
const env = $('#envelope');
const letterOverlay = $('#letterOverlay');

env.onclick = () => {
  const open = env.classList.toggle('open');
  env.setAttribute('aria-expanded', open);
  letterOverlay.classList.toggle('show', open);
  letterOverlay.setAttribute('aria-hidden', String(!open));
  $('#envHint').textContent = open ? 'Дахин товшиж хаагаарай' : 'Дугтуйг товшиж нээгээрэй';

  if (open) {
    setTimeout(() => env.scrollIntoView({ behavior: 'smooth', block: 'center' }), 500);
  }
};

/* ===== 7. MUSIC PLAYER =====
   ӨӨРИЙН MP3-Г ЭНД ОРУУЛАХ:
   1. Website-ийн folder дотор "audio" нэртэй folder үүсгэ.
   2. Өөрийн MP3 файлаа "song.mp3" гэж нэрлээд audio folder дотор хий.
   3. Доорх src: 'audio/song.mp3' гэсэн замыг өөрийн файлын нэрээр солино.
*/
const track = {
  title: 'One Wish',
  artist: 'Sweet Love',
  src: 'audio/song.mp3'
};

const audio = new Audio();
audio.preload = 'metadata';
audio.volume = 0.8;

let playing = false;
let objectUrl = null;

const fmt = s => {
  if (!Number.isFinite(s) || s < 0) return '0:00';
  return Math.floor(s / 60) + ':' + String(Math.floor(s % 60)).padStart(2, '0');
};

function total() {
  return Number.isFinite(audio.duration) ? audio.duration : 0;
}

function paint() {
  const duration = total();
  const current = audio.currentTime || 0;
  $('#cur').textContent = fmt(current);
  $('#dur').textContent = fmt(duration);
  $('#bar').style.width = duration ? Math.min(100, current / duration * 100) + '%' : '0%';
}

function status(msg='') {
  $('#audioStatus').textContent = msg;
}

function render() {
  $('#tTitle').textContent = track.title;
  $('#tArtist').textContent = track.artist;
  $('#chipName').textContent = track.title.toUpperCase();
  $('#playBtn').textContent = playing ? '❚❚' : '▶';
  $('#playBtn').setAttribute('aria-label', playing ? 'Түр зогсоох' : 'Тоглуулах');
  $('#player').classList.toggle('playing', playing);
  $('#eq').classList.toggle('paused', !playing);
  $('#eqText').textContent = playing ? 'Тоглож байна: ' + track.title : 'Хөгжим зогссон';
  paint();
}

async function setPlaying(on) {
  if (on) {
    try {
      // Хэрэглэгч Play дарсны дараа л play() дуудагдана. Autoplay хийхгүй.
      await audio.play();
      playing = true;
      status('');
    } catch (error) {
      playing = false;
      const msg = error?.name === 'NotSupportedError'
        ? 'MP3 файл олдсонгүй эсвэл browser энэ аудиог тоглуулж чадсангүй.'
        : 'Дууг тоглуулж чадсангүй. Доорх “MP3 сонгох” товчоор файлаа сонгоорой.';
      status(msg);
    }
  } else {
    audio.pause();
    playing = false;
  }
  render();
}

// Анхдагч замыг ачаална. Файл байхгүй бол status дээр ойлгомжтой мэдээлэл гаргана.
audio.src = track.src;
audio.load();

audio.ontimeupdate = paint;
audio.onloadedmetadata = () => { status(''); paint(); };
audio.oncanplay = () => { if (!playing) paint(); };
audio.onerror = () => {
  playing = false;
  render();
  status('audio/song.mp3 олдсонгүй. “MP3 сонгох” дээр дарж өөрийн дуугаа сонгоно уу.');
};
audio.onplay = () => { playing = true; render(); };
audio.onpause = () => { playing = false; render(); };
audio.onended = () => { playing = false; audio.currentTime = 0; render(); };

$('#playBtn').onclick = () => setPlaying(!playing);

$('#progress').onclick = e => {
  const duration = total();
  if (!duration) return;
  const r = e.currentTarget.getBoundingClientRect();
  const percent = Math.max(0, Math.min(1, (e.clientX - r.left) / r.width));
  audio.currentTime = percent * duration;
  paint();
};

$('#progress').onkeydown = e => {
  const duration = total();
  if (!duration) return;
  if (e.key === 'ArrowLeft' || e.key === 'ArrowRight') {
    e.preventDefault();
    const step = 5;
    audio.currentTime = Math.max(0, Math.min(duration, audio.currentTime + (e.key === 'ArrowRight' ? step : -step)));
    paint();
  }
};

$('#volume').oninput = e => {
  audio.volume = Number(e.target.value);
  $('#volumeText').textContent = Math.round(audio.volume * 100) + '%';
};

$('#audioFile').onchange = e => {
  const file = e.target.files?.[0];
  if (!file) return;
  if (!file.type.startsWith('audio/') && !file.name.toLowerCase().endsWith('.mp3')) {
    status('Аудио файл сонгоно уу.');
    return;
  }

  if (objectUrl) URL.revokeObjectURL(objectUrl);
  objectUrl = URL.createObjectURL(file);
  audio.src = objectUrl;
  audio.load();
  playing = false;
  $('#fileName').textContent = 'Сонгосон файл: ' + file.name;
  status('Файл бэлэн. ▶ Play дарна уу.');
  render();
};

render();
paint();</script>
</body>
</html>
