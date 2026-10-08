<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>ClassMonitor · Phonics Readers · Session 2</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700;800;900&family=Poppins:wght@500;600;700;800&display=swap" rel="stylesheet">
<style>
:root{--navy:#14264d;--blue:#1565d8;--blue2:#e8f1ff;--yellow:#ffd23f;--pink:#ff3d8b;--green:#20a060;--orange:#ff8a00;--purple:#8a3ffc;--red:#e63946;--ink:#1d2b4f;--muted:#5d6b88;}
*{box-sizing:border-box}
html,body{margin:0;height:100%;overflow:hidden;background:#e9f0fb;font-family:'Poppins','Montserrat','Raleway',system-ui,sans-serif;color:var(--ink);user-select:none}
button{font-family:inherit;cursor:pointer;border:0}
#app{display:flex;flex-direction:column;height:100vh}
#strip{height:8px;flex:none;background:linear-gradient(90deg,#ff9a4a 25%,#1565d8 25% 50%,#5fc08a 50% 75%,#0b4fc4 75%)}
#top{height:72px;flex:none;background:#fff;display:flex;align-items:center;gap:14px;padding:0 22px;box-shadow:0 2px 12px rgba(20,38,77,.08);z-index:5}
#logoBox{display:flex;align-items:center;height:48px;margin-right:6px}
#logoImg{height:44px;display:none;}
#logoSvg{height:44px;display:block}
.sep{width:1px;height:34px;background:#dfe6f2}
#deckTitle{font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;color:var(--blue);font-size:21px;letter-spacing:.3px;white-space:nowrap}
#deckTitle span{color:var(--blue)}
.sp{flex:1}
.pill{height:42px;padding:0 16px;border-radius:14px;background:#f2f6fd;border:2px solid #e1e9f6;font-weight:800;display:flex;align-items:center;gap:7px;font-size:16px;color:var(--navy)}
.ib{width:48px;height:48px;border-radius:14px;background:#fff;border:2px solid #cfdcf0;font-size:22px;font-weight:800;color:var(--blue);transition:.15s}
.ib:hover{background:var(--blue2);transform:translateY(-2px)}
#counter{min-width:76px;height:48px;border-radius:14px;background:#fff1c2;display:flex;align-items:center;justify-content:center;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:22px;color:#7a5600}
#main{flex:1;display:flex;min-height:0}
#side{width:250px;flex:none;background:#f5f8fe;padding:14px 12px;overflow-y:auto;border-right:1px solid #dde6f4}
#side .ttl{background:linear-gradient(135deg,#0b4fc4,#1565d8);color:#fff;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;text-align:center;padding:12px 10px;border-radius:14px;font-size:14px;letter-spacing:.5px;margin-bottom:12px;line-height:1.2}
.nav{display:flex;align-items:center;gap:10px;width:100%;text-align:left;background:#fff;border:2px solid #e3eaf6;border-radius:14px;padding:9px 10px;margin-bottom:9px;font-weight:800;font-size:13.5px;color:var(--navy);line-height:1.15}
.nav i{font-style:normal;width:28px;height:28px;border-radius:9px;background:#eef2f9;display:flex;align-items:center;justify-content:center;font-size:12px;color:var(--muted);flex:none}
.nav.on{border-color:var(--navy);background:var(--blue2)}
.nav.on i{background:var(--blue);color:#fff}
#pane{flex:1;position:relative;min-width:0;display:flex;align-items:center;justify-content:center;padding:14px}
#frame{position:relative;flex:none}
#stage{position:absolute;left:0;top:0;width:1600px;height:900px;transform-origin:0 0}
body.fs #side{display:none}
body.fs #pane{padding:6px}
#bar{height:5px;flex:none;background:#dfe7f5}
#bar div{height:100%;width:0;background:linear-gradient(90deg,#ff9a4a,#1565d8,#5fc08a);transition:width .4s}

/* ===== slides ===== */
.slide{position:absolute;inset:0;display:none;flex-direction:column;gap:14px;padding:46px 60px 38px;border-radius:34px;overflow:hidden;
 background:radial-gradient(circle at 92% 8%,#dcebff 0,transparent 26%),radial-gradient(circle at 4% 96%,#fff0c9 0,transparent 24%),radial-gradient(circle at 96% 96%,#ffe3ee 0,transparent 20%),linear-gradient(135deg,#fffefb,#f4f8ff);
 box-shadow:0 10px 40px rgba(20,38,77,.15)}
.slide.active{display:flex;animation:slin .45s ease}
@keyframes slin{from{opacity:0;transform:translateX(30px)}to{opacity:1;transform:none}}
.tag{align-self:flex-start;background:#dcebff;color:var(--blue);font-weight:800;letter-spacing:1.5px;font-size:19px;padding:7px 20px;border-radius:30px;text-transform:uppercase}
h1{letter-spacing:-.5px;margin:0;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:58px;line-height:1.08;color:var(--navy)}
h1 em{font-style:normal;color:var(--blue)}
.sub{font-size:26px;color:var(--muted);font-weight:700;margin-top:-4px}
.body{flex:1;min-height:0;display:flex;flex-direction:column;gap:18px}
.row{display:flex;gap:18px}
.card{background:#fff;border-radius:28px;box-shadow:0 6px 22px rgba(20,38,77,.1);border:3px solid #eaf0fa}
.teach{flex:none;display:flex;align-items:center;gap:18px;background:#e4f0ff;border:3px solid #cfe2fb;border-radius:60px;padding:12px 30px 12px 14px;min-height:92px}
.teach .av{font-size:44px;width:68px;height:68px;border-radius:50%;background:#fff;display:flex;align-items:center;justify-content:center;flex:none}
.teach .script{flex:1;font-size:26px;font-weight:800;color:var(--navy);line-height:1.25}
.teach .script small{display:block;font-size:20px;color:var(--muted);font-weight:700}
.spk{flex:none;width:62px;height:62px;border-radius:50%;background:var(--blue);color:#fff;font-size:28px;box-shadow:0 5px 0 #0b4fc4;transition:.1s}
.spk:active{transform:translateY(4px);box-shadow:0 1px 0 #0b4fc4}
.btn{background:var(--yellow);color:#4a3600;font-weight:800;font-size:24px;padding:14px 30px;border-radius:50px;box-shadow:0 6px 0 #d9a900;transition:.1s;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif}
.btn:active{transform:translateY(5px);box-shadow:0 1px 0 #d9a900}
.btn.blue{background:var(--blue);color:#fff;box-shadow:0 6px 0 #0b4fc4}
.btn.green{background:#3dcf8b;color:#06391f;box-shadow:0 6px 0 #1f9e63}
.btn.pink{background:#ff6fa5;color:#fff;box-shadow:0 6px 0 #d03d78}
.btn.sm{font-size:19px;padding:9px 22px}
.mascot{width:100%;height:100%;overflow:visible}
.float{animation:bob 3s ease-in-out infinite}
@keyframes bob{50%{transform:translateY(-12px)}}
.hop{animation:hop .6s ease}
@keyframes hop{30%{transform:translateY(-40px) rotate(-6deg)}60%{transform:translateY(0) rotate(4deg)}}
.shake{animation:shk .4s}
@keyframes shk{25%{transform:translateX(-10px)}75%{transform:translateX(10px)}}
.pop{animation:pp .5s}
@keyframes pp{40%{transform:scale(1.18)}}
.clk{cursor:pointer;transition:.15s}
.clk:hover{transform:translateY(-4px) scale(1.03)}
.hidden{visibility:hidden;opacity:0}
.show{visibility:visible;opacity:1;animation:pp .5s}

/* pattern colours */
.p-m{color:var(--pink)}.p-ai{color:var(--blue)}.p-ay{color:var(--purple)}.p-ee{color:var(--green)}.p-oa{color:var(--orange)}.p-ow{color:var(--red)}
.w{border-radius:8px;padding:0 2px;transition:.15s}
.w.now{background:#ffe27a;box-shadow:0 0 0 3px #ffe27a}
.pat .w[class*="p-"]{font-weight:800;text-decoration:underline;text-decoration-thickness:4px;text-underline-offset:6px}
.pat .w:not([class*="p-"]){color:var(--ink)}
.nopat .w{color:var(--ink)!important;text-decoration:none!important}

/* s1 */
.s1g{flex:1;display:grid;grid-template-columns:1fr 600px;gap:20px;min-height:0}
.hero{font-size:84px;line-height:.98}
.hero b{display:block;color:var(--blue);font-size:92px;text-shadow:0 5px 0 #c9dcfa}
.lead{font-size:29px;font-weight:700;color:var(--muted);margin:16px 0 0;max-width:760px;line-height:1.35}
.vrow{display:flex;align-items:flex-end;justify-content:center;height:330px;gap:0}
.vrow .m{width:150px;margin:0 -8px}
.bookbase{height:46px;background:#fff6dd;border:5px solid #ffb43a;border-radius:10px 10px 40px 40px;margin-top:-26px;position:relative;z-index:0}
.go{flex:1;display:flex;align-items:center;gap:16px;padding:14px 22px;cursor:pointer;border-radius:28px}
.go h3{white-space:nowrap;font-size:26px!important;margin:0 0 6px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-size:32px;display:inline-block;padding:0 16px;border-radius:30px}
.go p{margin:0;font-size:20px;font-weight:700;color:var(--muted);line-height:1.25}
.go .mm{width:100px;height:116px;flex:none}
.go .arr{width:56px;height:56px;border-radius:50%;color:#fff;font-size:28px;display:flex;align-items:center;justify-content:center;flex:none}

/* s2 */
.cast{display:flex;gap:16px;justify-content:center;margin-top:8px}
.cast div{text-align:center;font-weight:800;font-size:20px}
.cast span{display:flex;width:112px;height:112px;border-radius:50%;background:#fff;box-shadow:0 5px 14px rgba(20,38,77,.15);align-items:center;justify-content:center;font-size:62px;margin-bottom:4px}
.quote{font-size:30px;font-weight:700;line-height:1.35;margin:10px 0}
.quote b{color:#0b2a8a}.quote u{text-decoration:none;color:var(--blue);font-weight:800}
.askbox{border:3px solid #cfe0f7;border-radius:22px;padding:16px 22px;font-size:29px;font-weight:800;background:#f6faff}

/* s3 */
.wcard{background:#fff;border-radius:30px;box-shadow:0 8px 24px rgba(20,38,77,.15);display:flex;align-items:center;justify-content:center;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;color:var(--navy);letter-spacing:2px;border:4px solid #eaf0fa}
.wcard .a{color:var(--orange)}.wcard .c{color:var(--navy)}.wcard .e{color:var(--blue)}.wcard .e.in{display:inline-block;animation:pp .6s}
.pairs{display:grid;grid-template-columns:repeat(4,1fr);gap:18px;flex:1;min-height:0}
.pair{border-radius:26px;padding:12px 10px;text-align:center;border:3px solid transparent;display:flex;flex-direction:column;align-items:center;justify-content:center}
.pair .em{font-size:70px;line-height:1.1}
.pair .tx{font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:46px;color:var(--navy)}
.pair .tx .e{color:var(--blue)}
.bubble{background:#fff;border:4px solid #cfe0f7;border-radius:32px;padding:20px 26px;font-size:30px;font-weight:700;line-height:1.4;position:relative}
.bubble b{color:var(--blue)}

/* s4 */
.wgrid{display:grid;grid-template-columns:repeat(5,1fr);grid-template-rows:1fr 1fr;gap:16px;flex:1;min-height:0}
.wb{position:relative;height:auto;border-radius:26px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:66px;color:var(--navy);background:#fff;border:4px solid #dbe6f7;box-shadow:0 5px 0 #dbe6f7}
.wb.sel{border-color:var(--blue);background:var(--blue2);transform:translateY(-4px)}
.wb.ok{background:#d9f7e6;border-color:#3dcf8b;box-shadow:0 5px 0 #3dcf8b}
.wb.hint{background:#fff3cf;border-color:#ffc83d;box-shadow:0 5px 0 #ffc83d}
.wb .bd{position:absolute;right:10px;top:4px;font-size:30px}
.big{flex:1;height:112px;border-radius:30px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:38px;color:#fff}

/* s5 */
.team{position:relative;height:100%;display:flex;align-items:center;justify-content:center;gap:0}
.team .m{width:150px;height:175px;transition:transform .8s cubic-bezier(.5,1.6,.5,1)}
.team.joined .l{transform:translateX(52px)}.team.joined .r{transform:translateX(-52px)}
.wc5{display:grid;grid-template-columns:repeat(5,1fr);gap:16px;flex:1;min-height:0}
.wc5 .pair{background:#fff;border:3px solid #dbe6f7;box-shadow:0 5px 0 #dbe6f7}
.chips{display:flex;gap:12px;flex-wrap:wrap}
.chip{font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:30px;padding:2px 18px;border-radius:40px;background:#fff;border:3px solid #dbe6f7}
.chip.ai{color:var(--blue)}.chip.ay{color:var(--purple)}.chip.ee{color:var(--green)}.chip.oa{color:var(--orange)}.chip.ow{color:var(--red)}
.hl{font-weight:800}

/* s6 */
.tg{display:grid;grid-template-columns:repeat(3,1fr);grid-template-rows:1fr 1fr;gap:18px;flex:1;min-height:0}
.tile{border-radius:28px;padding:14px 20px;display:flex;flex-direction:column;gap:8px;border:3px solid transparent}
.tile .hd{display:flex;align-items:center;gap:14px;margin-bottom:6px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:72px;line-height:1}
.tile .hd span{font-size:64px}
.tile .ws{display:flex;gap:10px;flex-wrap:wrap}
.tile .ws b{background:#fff;border-radius:40px;padding:4px 28px;font-size:40px;font-weight:800;box-shadow:0 3px 0 rgba(0,0,0,.08);cursor:pointer}
.cue{background:#fff3cf;border:3px solid #ffd96a;border-radius:24px;padding:14px 20px;font-size:23px;font-weight:700;line-height:1.3}

/* s7 */
.srow{display:flex;align-items:center;gap:18px;background:#fff;border:3px solid #dbe6f7;border-radius:26px;padding:10px 20px;height:112px;box-shadow:0 5px 0 #dbe6f7}
.srow .em{font-size:60px;width:80px;text-align:center}
.srow .tx{flex:1;font-size:46px;font-weight:700}
.play{width:68px;height:68px;border-radius:50%;background:#e3efff;color:var(--blue);font-size:28px;flex:none;box-shadow:0 4px 0 #bcd5f7}

/* s8 */
.pass{font-size:35px;line-height:1.6;font-weight:700;padding:26px 34px;flex:1}
.pass p{margin:0 0 10px}
.legend{display:flex;gap:10px;flex-wrap:wrap}
.lg{font-weight:800;font-size:20px;padding:4px 16px;border-radius:30px;background:#fff;border:3px solid #dbe6f7}
.tip{background:#e6fbf1;border:3px solid #b6ecd2;border-radius:24px;padding:14px 22px;font-size:23px;font-weight:700;line-height:1.3}

/* s9 */
.mp{display:flex;gap:12px}
.mb{flex:1;height:64px;border-radius:20px;background:#fff;border:3px solid #dbe6f7;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:23px;color:var(--navy);box-shadow:0 4px 0 #dbe6f7}
.mb.on{background:var(--blue);color:#fff;border-color:var(--blue);box-shadow:0 4px 0 #0b4fc4}
.mb.done{background:#d9f7e6;border-color:#3dcf8b}
.mb.on.done{background:#1f9e63;color:#fff}
.mission{display:flex;align-items:center;gap:22px;padding:14px 26px;border-radius:26px;background:#f1e8ff;border:3px solid #dccbff}
.mission h2{margin:0;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-size:36px;color:#4b1d99;line-height:1.1}
.mission p{margin:0;font-size:21px;font-weight:700;color:#6a4aa8}
.tgt{display:flex;gap:10px;margin-left:auto;flex-wrap:wrap;justify-content:flex-end}
.tgt b{min-width:104px;text-align:center;font-size:30px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;background:#fff;border:3px dashed #b9a2ee;border-radius:16px;padding:2px 12px;color:#b9a2ee}
.tgt b.f{border-style:solid;border-color:#3dcf8b;color:var(--navy);background:#e8fff2}
.dpass{font-size:33px;line-height:1.55;font-weight:700;padding:18px 32px;flex:1}
.dpass .w{cursor:pointer}
.dpass .w:not(.found){color:var(--ink)!important}
.dpass .w:hover{background:#eaf1ff}
.dpass .w.found{font-weight:800;text-decoration:underline;text-decoration-thickness:4px;text-underline-offset:6px;background:#fff6c9}
.dpass p{margin:0 0 6px}

/* s10 */
.opt{width:100%;text-align:left;font-size:34px;font-weight:800;background:#fff;border:4px solid #dbe6f7;border-radius:24px;padding:18px 28px;box-shadow:0 5px 0 #dbe6f7;color:var(--navy)}
.opt.ok{background:#d9f7e6;border-color:#3dcf8b;box-shadow:0 5px 0 #3dcf8b}
.opt.no{background:#ffe6e6;border-color:#ff9c9c}
.dots{display:flex;gap:10px}.dots i{width:22px;height:22px;border-radius:50%;background:#dbe6f7}.dots i.on{background:var(--blue)}.dots i.dn{background:#3dcf8b}

/* s11 */
.csnd{display:flex;align-items:center;gap:24px;flex:1;min-height:0}
.cw{flex:1;padding:18px;text-align:center;border-radius:30px;background:#fff;border:4px solid #dbe6f7}
.cw .em{font-size:96px;line-height:1}
.cw .tx{font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:78px;color:var(--navy);line-height:1}
.cw .tx b{color:var(--pink)}
.cw .sd{font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:56px;color:var(--blue);height:70px}

/* s12 */
.hw{display:flex;align-items:center;gap:22px;padding:16px 26px;border-radius:26px;cursor:pointer;background:#fff;border:3px solid #dbe6f7}
.hw .n{width:70px;height:70px;border-radius:50%;background:var(--yellow);font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:40px;display:flex;align-items:center;justify-content:center;flex:none}
.hw .t{flex:1;font-size:32px;font-weight:800;line-height:1.25}
.hw .t small{display:block;font-size:22px;color:var(--muted);font-weight:700}
.hw .ck{width:56px;height:56px;border-radius:16px;border:4px solid #cfdcf0;font-size:36px;display:flex;align-items:center;justify-content:center;color:#fff;flex:none}
.hw.done{background:#e8fff2;border-color:#3dcf8b}.hw.done .ck{background:#3dcf8b;border-color:#3dcf8b}

#toast{position:absolute;left:50%;bottom:150px;transform:translateX(-50%) scale(.8);background:var(--navy);color:#fff;font-weight:800;font-size:30px;padding:14px 34px;border-radius:50px;opacity:0;pointer-events:none;transition:.25s;z-index:20;white-space:nowrap}
#toast.on{opacity:1;transform:translateX(-50%) scale(1)}
#fx{position:fixed;inset:0;pointer-events:none;z-index:50}
</style>
</head>
<body>
<div id="app">
 <div id="strip"></div>
 <header id="top">
  <div id="logoBox">
   <!-- Official ClassMonitor logo embedded (transparent background) -->
   <img id="logoImg" src="data:image/png;base64,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" alt="ClassMonitor" onload="this.style.display='block';document.getElementById('logoSvg').style.display='none'" onerror="this.style.display='none'">
   <svg id="logoSvg" viewBox="0 0 270 60" xmlns="http://www.w3.org/2000/svg" aria-label="ClassMonitor">
    <path d="M18 4h26a16 16 0 0 1 16 16v22a16 16 0 0 1-16 16H6a2 2 0 0 1-1.4-3.4L12 47.2 4 40V18A14 14 0 0 1 18 4z" fill="#ef5a5f" transform="translate(-1 0)"/>
    <path d="M30 12 L34.1 22.3 L45.2 23.1 L36.7 30.2 L39.4 41 L30 35 L20.6 41 L23.3 30.2 L14.8 23.1 L25.9 22.3 Z" fill="#fff" stroke="#fff" stroke-width="3" stroke-linejoin="round"/>
    <path d="M9 52 Q14 42 21 37" stroke="#fff" stroke-width="3.5" fill="none" stroke-linecap="round"/>
    <text x="70" y="42" font-family="Poppins,Montserrat,sans-serif" font-weight="600" font-size="32" fill="#0b0b0b" letter-spacing="-.5">ClassMonitor</text>
   </svg>
  </div>
  <div class="sep"></div>
  <div id="deckTitle">PHONICS READERS · SESSION 2</div>
  <div class="sp"></div>
  <div class="pill" title="Stars">⭐ <span id="stars">0</span></div>
  <div class="pill" title="XP">⚡ <span id="xp">0</span> XP</div>
  <button class="ib" id="muteBtn" title="Sound on/off (M)">🔊</button>
  <button class="ib" id="spdBtn" title="Voice speed" style="font-size:19px">1×</button>
  <button class="ib" id="prev" title="Previous (←)">←</button>
  <div id="counter">1/13</div>
  <button class="ib" id="next" title="Next (→)">→</button>
  <button class="ib" id="fsBtn" title="Full screen (F)">⛶</button>
 </header>
 <div id="main">
  <aside id="side"><div class="ttl">SESSION 2 · MAGIC OF LONG VOWELS</div><div id="navList"></div></aside>
  <section id="pane">
   <div id="frame"><div id="stage">

<!-- ============ 1 · TITLE ============ -->
<section class="slide active" id="s1" data-title="Welcome · Long Vowels" data-icon="🌟">
 <div class="s1g">
  <div style="display:flex;flex-direction:column;justify-content:center">
   <span class="tag">Session 2 · Phonics Adventure</span>
   <h1 class="hero" style="margin-top:14px">THE MAGIC OF<b>LONG VOWELS</b></h1>
   <p class="lead">Today we discover how vowels can change their sounds — with Magic e and vowel teams.</p>
  </div>
  <div style="display:flex;flex-direction:column;justify-content:center">
   <div class="vrow" id="vrow"></div><div class="bookbase"></div>
  </div>
 </div>
 <div class="row" style="height:178px;flex:none">
  <div class="go clk card" style="background:#fff0f4;border-color:#ffd6e2" data-go="3"><div class="mm" id="gm1"></div><div style="flex:1"><h3 style="background:#ffd0df;color:#c2185b">Magic e</h3><p>See how a quiet e helps the vowel say its long sound.</p></div><div class="arr" style="background:#ff5d8f">→</div></div>
  <div class="go clk card" style="background:#fff8e1;border-color:#ffe9a8" data-go="5"><div class="mm" id="gm2"></div><div style="flex:1"><h3 style="background:#ffe18a;color:#7a5600">Vowel Teams</h3><p>Discover when two vowels work together.</p></div><div class="arr" style="background:#ffa800">→</div></div>
  <div class="go clk card" style="background:#eafaf2;border-color:#bdeed6" data-go="9"><div class="mm" style="font-size:84px;display:flex;align-items:center;justify-content:center">🔍</div><div style="flex:1"><h3 style="background:#bff0d8;color:#126a43">Phonics Detective</h3><p>Find long-vowel patterns hiding in a story.</p></div><div class="arr" style="background:#2fb67c">→</div></div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">Teacher: “Hello, Reader! Ready to discover the magic?”</div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 2 · CONNECTION ============ -->
<section class="slide" id="s2" data-title="Session 1 Connection" data-icon="🧩">
 <span class="tag">Welcome &amp; Connection to Session 1</span>
 <h1>Remember our last <em>adventure?</em></h1>
 <div class="sub">Let the child answer before you continue.</div>
 <div class="body">
  <div class="row" style="flex:1;min-height:0">
   <div class="card" style="flex:1.05;padding:20px 28px;background:#eef6ff">
    <div style="font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:36px">📖 Think back</div>
    <div class="quote">“We went on an adventure with <b>Sam, Ben,</b> <b>the cat, the dog and the frog.</b>”</div>
    <div class="quote">“We used our <u>short vowel sounds</u> to read the story.”</div>
    <div class="cast">
     <div class="clk" data-say="Sam"><span>👦</span>Sam</div><div class="clk" data-say="Ben"><span>👧</span>Ben</div>
     <div class="clk" data-say="meow"><span>🐱</span>cat</div><div class="clk" data-say="woof woof"><span>🐶</span>dog</div><div class="clk" data-say="ribbit"><span>🐸</span>frog</div>
    </div>
   </div>
   <div class="card" style="flex:.95;padding:20px 28px;background:#fff8e1;border-color:#ffe9a8;display:flex;flex-direction:column;gap:14px">
    <div style="font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:36px">✨ Today’s mystery</div>
    <div style="background:#ffd9e6;border-radius:30px;padding:22px 28px;font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:38px;line-height:1.2;color:var(--navy)">“Today, I’m going to show you something <span style="color:var(--blue)">interesting.</span>”</div>
    <div class="askbox" id="askBox">Ask: “What do you think a long vowel might sound like?”</div>
    <div id="ansBox" class="askbox hidden" style="background:#e6fbf1;border-color:#b6ecd2">💡 A long vowel <u style="text-decoration:none;color:#126a43">says its own name</u> — a · e · i · o · u!</div>
    <div style="display:flex;gap:12px"><button class="btn sm" id="s2ask">❓ Ask the question</button><button class="btn sm green" id="s2ans">💡 Reveal</button></div>
   </div>
  </div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">“Do you remember what we did in our last class?”<small>“Yes! We used our short vowel sounds to read the story. Today, I’m going to show you something interesting.”</small></div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 3 · MAGIC E ============ -->
<section class="slide" id="s3" data-title="Magic e" data-icon="🪄">
 <span class="tag">Magic e · Revision</span>
 <h1>Meet the quiet helper: <em>Magic e</em> ✨</h1>
 <div class="sub">Explain the rule simply, then read the examples together.</div>
 <div class="body">
  <div class="row" style="align-items:center;height:290px;flex:none">
   <div class="wcard clk" id="capL" data-say="cap" style="width:340px;height:210px;font-size:150px"><span class="c">c</span><span class="a">a</span><span class="c">p</span></div>
   <div style="width:210px;height:250px" id="magicE" class="float"></div>
   <div class="wcard clk" id="capR" data-say="cape" style="width:400px;height:210px;font-size:150px;background:#fff8e1;border-color:#ffe9a8"><span class="c">c</span><span class="a">a</span><span class="c">p</span><span class="e" id="capE" style="opacity:.15">e</span></div>
   <div class="bubble" style="flex:1"><b>Magic e</b> usually sits quietly at the end. It doesn’t say /e/. It helps the vowel before it say its <b>long sound.</b></div>
  </div>
  <div class="row" style="justify-content:center;gap:20px;flex:none"><button class="btn pink" id="cast">🪄 Cast the Magic e spell</button><button class="btn sm blue" id="castReset" style="align-self:center">↺ Reset</button></div>
  <div class="pairs" id="pairs"></div>
 </div>
</section>

<!-- ============ 4 · SHORT OR LONG ============ -->
<section class="slide" id="s4" data-title="Short or Long?" data-icon="👏">
 <span class="tag">Quick Game · Short or Long?</span>
 <h1><span style="color:var(--pink)">Clap</span> or <em>High-Five?</em></h1>
 <div class="sub">Teacher says a word. Child gives: <b style="color:var(--pink)">Clap = Long</b> or <b style="color:var(--blue)">High five = Short</b>. Tap a word, then tap the child’s answer.</div>
 <div class="body">
  <div class="wgrid" id="wgrid"></div>
  <div class="row" style="flex:none"><button class="big" id="bClap" style="background:#ff6fa5;box-shadow:0 7px 0 #d03d78">👏 CLAP = LONG</button><button class="big" id="bHigh" style="background:#3b8cff;box-shadow:0 7px 0 #1565d8">✋ HIGH-FIVE = SHORT</button></div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">Don’t overcorrect. The purpose is rapid recognition.<small id="s4score">Score: 0 / 10 — tap a word to begin</small></div><button class="btn sm blue" id="s4reset">↺ Restart</button></div>
</section>

<!-- ============ 5 · VOWEL TEAMS ============ -->
<section class="slide" id="s5" data-title="Vowel Teams" data-icon="🤝">
 <span class="tag">Vowel Team Revision</span>
 <h1>Two vowels can work <em>as a team</em> 🤝</h1>
 <div class="sub">“Magic e isn’t the only way. Sometimes two vowels work together.”</div>
 <div class="body">
  <div class="row" style="height:250px;flex:none">
   <div class="card" style="flex:1.1;display:flex;align-items:center;justify-content:center;gap:24px;background:#eef6ff;padding:0 24px">
    <div class="team" id="team"><div class="m l" id="mA"></div><div class="m r" id="mI"></div></div>
    <div style="text-align:center"><div id="aiBig" class="wcard hidden" style="width:240px;height:130px;font-size:90px;color:var(--blue)">ai</div><button class="btn sm" id="join" style="margin-top:12px">🤝 Make the team</button></div>
   </div>
   <div class="card" style="flex:.9;padding:18px 26px;display:flex;flex-direction:column;gap:12px;justify-content:center">
    <div style="font-size:28px;font-weight:800;line-height:1.3"><b style="color:var(--blue)">ai</b> is a team. Together they say the long <b style="color:var(--blue)">A</b> sound.</div>
    <div style="font-weight:800;color:var(--muted);font-size:21px">Common vowel teams for today’s reading:</div>
    <div class="chips"><span class="chip ai clk" data-say="A I says A">ai</span><span class="chip ay clk" data-say="A Y says A">ay</span><span class="chip ee clk" data-say="E E says E">ee</span><span class="chip oa clk" data-say="O A says O">oa</span><span class="chip ow clk" data-say="O W says ow">ow</span></div>
   </div>
  </div>
  <div class="wc5" id="aiWords"></div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">“We have seen one way to make a vowel long. But Magic e isn’t the only way. Sometimes two vowels work together.”<small>Write: <b>ai</b> — “These two letters are a team.”</small></div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 6 · TOOLKIT ============ -->
<section class="slide" id="s6" data-title="Long-Vowel Toolkit" data-icon="🧰">
 <span class="tag">Common Vowel Teams · Today’s Toolkit</span>
 <h1>Build your long-vowel <em>toolkit</em> 🧰</h1>
 <div class="sub">Tap a team to hear it. Tap a word to hear the word.</div>
 <div class="body">
  <div class="tg" id="tg"></div>
 </div>
 <div class="teach" style="background:#fff3cf;border-color:#ffd96a"><div class="av">📢</div><div class="script"><b>Teacher cue:</b> Point out the vowel pattern before asking the child to read the whole word.</div></div>
</section>

<!-- ============ 7 · SENTENCES ============ -->
<section class="slide" id="s7" data-title="Sentence Reading" data-icon="🗣️">
 <span class="tag">Sentence Reading</span>
 <h1>Read it like you’re <em>talking!</em> 🗣️</h1>
 <div class="sub">Remember: read the sentence as if you’re talking.</div>
 <div class="body">
  <div class="row" style="flex:1;min-height:0">
   <div style="flex:1;display:flex;flex-direction:column;gap:14px" id="sents"></div>
   <div style="width:290px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px"><div style="font-size:190px;line-height:1" class="float">🧒</div><div style="font-size:90px;margin-top:-30px">📗</div><button class="btn sm green" id="readAll">▶ Read all</button></div>
  </div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">“Remember, read the sentence as if you’re talking.”</div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 8 · PASSAGE ============ -->
<section class="slide" id="s8" data-title="Main Reading Passage" data-icon="📖">
 <span class="tag">Main Reading Passage · Teacher-Guided</span>
 <h1>Jake and the <em>Rainy Day</em> 🌈</h1>
 <div class="row" style="flex:1;min-height:0">
  <div style="flex:1;display:flex;flex-direction:column;gap:14px;min-width:0">
   <div class="card pass pat" id="passage"></div>
   <div class="tip">💡 <b>Teacher tip:</b> If the child gets stuck, ask: “Look at the vowel pattern. What sound does it make?”</div>
  </div>
  <div style="width:280px;display:flex;flex-direction:column;gap:12px">
   <div style="font-size:150px;text-align:center;line-height:1" class="float">☔</div>
   <button class="btn green sm" id="pRead">▶ Read to me</button>
   <button class="btn blue sm" id="pStop">⏹ Stop</button>
   <button class="btn sm" id="pPat">👁 Patterns on/off</button>
   <div class="legend" style="flex-direction:column;align-items:stretch;gap:6px;margin-top:4px">
    <span class="lg p-m">Magic e</span><span class="lg p-ai">ai</span><span class="lg p-ay">ay</span><span class="lg p-ee">ee</span><span class="lg p-oa">oa</span><span class="lg p-ow">ow</span>
   </div>
  </div>
 </div>
</section>

<!-- ============ 9 · DETECTIVE ============ -->
<section class="slide" id="s9" data-title="Phonics Detective" data-icon="🔍">
 <span class="tag">Phonics Detective</span>
 <h1>Go back into the story. <em>Find the clues!</em> 🔍</h1>
 <div class="body" style="gap:14px">
  <div class="mp" id="mp"></div>
  <div class="mission" id="mission"></div>
  <div class="card dpass" id="dpass"></div>
 </div>
 <div class="teach"><div class="av">🕵️</div><div class="script">“Now you’re going to become a Phonics Detective. I’m going to give you a mission.”<small>Child taps each hidden word in the story.</small></div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 10 · COMPREHENSION ============ -->
<section class="slide" id="s10" data-title="Comprehension" data-icon="💭">
 <span class="tag">Comprehension · 5 minutes</span>
 <h1>Story <em>Questions</em> 💭</h1>
 <div class="body">
  <div class="row" style="flex:1;min-height:0">
   <div style="flex:1;display:flex;flex-direction:column;gap:14px;min-width:0">
    <div class="card" style="padding:20px 30px;display:flex;align-items:center;gap:20px"><div id="qEm" style="font-size:84px"></div><div id="qTx" style="font-size:44px;font-weight:800;line-height:1.2;flex:1"></div><button class="spk" id="qSay">🔊</button></div>
    <div id="opts" style="display:flex;flex-direction:column;gap:14px"></div>
   </div>
   <div style="width:300px;display:flex;flex-direction:column;align-items:center;gap:16px;justify-content:center">
    <div class="card" style="padding:16px 20px;text-align:center;width:100%"><div style="font-weight:800;color:var(--muted);font-size:20px">⏱ Time left</div><div id="tmr" style="font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:76px;color:var(--navy);line-height:1">5:00</div><button class="btn sm blue" id="tmrBtn" style="margin-top:8px">▶ Start</button></div>
    <div class="dots" id="dots"></div>
    <button class="btn sm green" id="qNext">Next question →</button>
   </div>
  </div>
 </div>
</section>

<!-- ============ 11 · BRIDGE ============ -->
<section class="slide" id="s11" data-title="Bridge to Session 3" data-icon="🌉">
 <span class="tag">Bridge to Session 3</span>
 <h1>A <em>mystery</em> letter 🕵️</h1>
 <div class="sub" id="s11sub">Step 1 — ask the child about the letter c.</div>
 <div class="body">
  <div class="csnd">
   <div class="cw clk" id="cwCat" data-say="cat"><div class="em">🐱</div><div class="tx"><b>c</b>at</div><div class="sd hidden" id="sdK">/k/</div></div>
   <div style="font-size:90px" class="float hidden" id="arrowC">➜</div>
   <div class="cw clk hidden" id="cwCity" data-say="city"><div class="em">🏙️</div><div class="tx"><b>c</b>ity</div><div class="sd hidden" id="sdS">/s/</div></div>
   <div class="hidden" id="mysteryQ" style="width:300px;text-align:center"><div style="font-size:150px;line-height:1" class="float">❓</div><div style="font-family:'Montserrat','Poppins','Raleway',system-ui,sans-serif;font-weight:800;font-size:30px;color:var(--purple)">Next time…</div></div>
  </div>
  <div class="row" style="justify-content:center;flex:none"><button class="btn pink" id="s11next">Next step ▶</button><button class="btn sm blue" id="s11reset" style="align-self:center">↺ Reset</button></div>
 </div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script" id="s11say">“What sound does the c make?”</div><button class="spk" id="s11spk">🔊</button></div>
</section>

<!-- ============ 12 · HOMEWORK ============ -->
<section class="slide" id="s12" data-title="Homework" data-icon="🏠">
 <span class="tag">Session 2 Homework</span>
 <h1>Your reading <em>mission</em> at home 🏠</h1>
 <div class="sub">Sample tasks — teachers can edit them in the HOMEWORK list at the top of the script.</div>
 <div class="body" id="hwList" style="gap:16px;justify-content:center"></div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">“Great work today! Here is your mission for home.”</div><button class="spk" data-script>🔊</button></div>
</section>

<!-- ============ 13 · WRAP UP ============ -->
<section class="slide" id="s13" data-title="Wrap-Up" data-icon="🏆">
 <span class="tag">Session 2 Complete</span>
 <h1>You did it, <em>Reader!</em> 🏆</h1>
 <div class="sub">Tap each goal the child has reached today.</div>
 <div class="body"><div class="row" style="flex:1;min-height:0"><div id="objs" style="flex:1;display:grid;grid-template-columns:1fr 1fr;gap:12px;align-content:center"></div>
  <div style="width:330px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:12px"><div style="width:200px;height:230px" id="gm3" class="float"></div><div class="pill" style="font-size:24px;height:56px">⭐ <span id="stars2">0</span> stars · ⚡ <span id="xp2">0</span> XP</div><button class="btn pink sm" id="celebrate">🎉 Celebrate!</button></div></div></div>
 <div class="teach"><div class="av">👩‍🏫</div><div class="script">“Fantastic! You found phonics rules hiding inside a real story.”</div><button class="spk" data-script>🔊</button></div>
</section>

   <div id="toast"></div>
   </div></div>
  </section>
 </div>
 <div id="bar"><div id="barFill"></div></div>
</div>
<canvas id="fx"></canvas>

<script>
/* ================= EDITABLE CONTENT ================= */
const HOMEWORK=[
 {t:'Read “Jake and the Rainy Day” aloud two times.',s:'Read it like you’re talking!'},
 {t:'Find 5 long-vowel words at home.',s:'Look in books, on food boxes or on signs. Write them down.'},
 {t:'Sort your words: Magic e or vowel team?',s:'Draw two columns and put each word in the right one.'}
];
const QUESTIONS=[
 {e:'🧒',q:'Who is the story about?',o:['Jake','Sam','Ben'],a:0},
 {e:'🪁',q:'What did Jake have?',o:['A game','A kite','A bike'],a:1},
 {e:'🌧️',q:'What came one day?',o:['Snow','Wind','Rain'],a:2},
 {e:'🌈',q:'What did Jake see in the sky?',o:['A rainbow','A plane','A bird'],a:0},
 {e:'😄',q:'How did Jake feel at the end?',o:['Sad','Happy','Cross'],a:1}
];
const OBJECTIVES=['Recognise short and long vowel sounds','Identify when Magic e changes a vowel sound','Recognise common vowel teams','Read words with long vowel patterns','Compare short and long vowel words','Apply the rules while reading a story','Find long-vowel patterns independently','Read the passage with growing fluency'];
const PASSAGE=[
 '{Jake|m} had a {kite|m}. He liked to play a {game|m} outside.',
 'One {day|ay}, the {rain|ai} came. “It {may|ay} rain all {day|ay},” said {Jake|m}.',
 '{Jake|m} looked at the {rainbow|ai} in the sky. “I {like|m} the colors!” he said with a {smile|m}.',
 '{Jake|m} walked {down|ow} the {road|oa}. He saw a {green|ee} tree and stopped to {see|ee} the {rain|ai}.',
 'Soon it was {time|m} to go {home|m}. “What a fun {day|ay}!” {Jake|m} said.'
];
const SENTENCES=[
 {e:'🚲',m:'{Jake|m} {likes|m} to ride a {bike|m}.'},
 {e:'🌈',m:'The {rain|ai} made a {rainbow|ai}.'},
 {e:'🌳',m:'{Green|ee} trees line the {road|oa}.'},
 {e:'☔',m:'We {may|ay} {see|ee} {rain|ai} {down|ow} the {road|oa}.'}
];
const TOOLKIT=[
 {p:'ai',c:'ai',bg:'#e6f0ff',em:'☁️',w:['rain','train','mail'],say:'A I says A, as in rain'},
 {p:'ay',c:'ay',bg:'#f1e8ff',em:'☀️',w:['day','may'],say:'A Y says A, as in day'},
 {p:'ee',c:'ee',bg:'#e6f8ee',em:'🌳',w:['green','see'],say:'E E says E, as in green'},
 {p:'oa',c:'oa',bg:'#fff0dc',em:'🛣️',w:['road'],say:'O A says O, as in road'},
 {p:'ow',c:'ow',bg:'#ffe6e6',em:'⬇️',w:['down'],say:'O W says ow, as in down'}
];
/* ================= STATE & HELPERS ================= */
const $=s=>document.querySelector(s), $$=s=>[...document.querySelectorAll(s)];
let stars=0,xp=0,muted=false,speedMul=1,cur=0,voice=null,kTimer=null;
const awarded=new Set();
function award(key,x,s){ if(awarded.has(key))return; awarded.add(key); xp+=x; stars+=s||0; syncScore(); }
function syncScore(){ ['stars','stars2'].forEach(i=>$('#'+i).textContent=stars); ['xp','xp2'].forEach(i=>$('#'+i).textContent=xp); }
function toast(t){ const el=$('#toast'); el.textContent=t; el.classList.add('on'); clearTimeout(toast.t); toast.t=setTimeout(()=>el.classList.remove('on'),1700); }

/* ---------- speech ---------- */
function pickVoice(){ const v=speechSynthesis.getVoices().filter(x=>/^en/i.test(x.lang)); if(!v.length)return;
 const pref=[/Neerja|Heera|Google UK English Female|Samantha|Zira|Aria|Jenny|Female/i,/en-IN/i,/en-GB/i,/en-US/i];
 for(const p of pref){ const f=v.find(x=>p.test(x.name)||p.test(x.lang)); if(f){voice=f;return} } voice=v[0]; }
if('speechSynthesis' in window){ pickVoice(); speechSynthesis.onvoiceschanged=pickVoice; }
function speak(text,o={}){ if(!('speechSynthesis' in window)||muted){ o.onend&&setTimeout(o.onend,400); return; }
 speechSynthesis.cancel();
 setTimeout(()=>{ const u=new SpeechSynthesisUtterance(text); u.lang='en-US'; if(voice)u.voice=voice; u.rate=(o.rate||0.9)*speedMul; u.pitch=1.1;
  u.onend=o.onend||null; u.onerror=o.onend||null; if(o.onboundary)u.onboundary=o.onboundary; speechSynthesis.speak(u); },40); }
function stopSpeech(){ if('speechSynthesis' in window)speechSynthesis.cancel(); clearInterval(kTimer); $$('.w.now').forEach(e=>e.classList.remove('now')); }
/* karaoke: highlights spans while reading */
function karaoke(spans,onDone){ stopSpeech(); if(!spans.length)return;
 const toks=spans.map(s=>s.dataset.sp||s.textContent), text=toks.join(' '); const off=[]; let p=0; toks.forEach(t=>{off.push(p);p+=t.length+1;});
 const hl=i=>spans.forEach((s,k)=>s.classList.toggle('now',k===i)); let gotB=false;
 const runTimer=()=>{ let i=0; hl(0); clearInterval(kTimer); kTimer=setInterval(()=>{ i++; if(i>=spans.length){clearInterval(kTimer);hl(-1);onDone&&onDone();} else hl(i); },560/speedMul); };
 if(muted){ runTimer(); return; }
 speak(text,{rate:.85,onend:()=>{clearInterval(kTimer);hl(-1);onDone&&onDone();},onboundary:e=>{ if(e.name&&e.name!=='word')return; gotB=true; clearInterval(kTimer); let i=0; off.forEach((o,k)=>{if(o<=e.charIndex)i=k}); hl(i); }});
 setTimeout(()=>{ if(!gotB&&!muted)runTimer(); },900); }

/* ---------- sound effects ---------- */
let AC; function ac(){ if(!AC)AC=new (window.AudioContext||window.webkitAudioContext)(); if(AC.state==='suspended')AC.resume(); return AC; }
function tone(f,d,type='sine',v=.18,t0=0,f2){ if(muted)return; const c=ac(),o=c.createOscillator(),g=c.createGain(),t=c.currentTime+t0; o.type=type; o.frequency.setValueAtTime(f,t); if(f2)o.frequency.exponentialRampToValueAtTime(f2,t+d); g.gain.setValueAtTime(v,t); g.gain.exponentialRampToValueAtTime(.0001,t+d); o.connect(g).connect(c.destination); o.start(t); o.stop(t+d+.02); }
function noise(d,fq=1500,v=.4,t0=0,q=1){ if(muted)return; const c=ac(),n=c.sampleRate*d,b=c.createBuffer(1,n,c.sampleRate),a=b.getChannelData(0); for(let i=0;i<n;i++)a[i]=(Math.random()*2-1)*Math.pow(1-i/n,3); const s=c.createBufferSource(),f=c.createBiquadFilter(),g=c.createGain(); s.buffer=b; f.type='bandpass'; f.frequency.value=fq; f.Q.value=q; g.gain.value=v; s.connect(f).connect(g).connect(c.destination); s.start(c.currentTime+t0); }
const sfx={
 pop:()=>tone(520,.12,'sine',.15,0,900),
 ding:()=>{tone(784,.18,'triangle',.2);tone(1175,.35,'triangle',.2,.12)},
 boop:()=>tone(220,.25,'sawtooth',.08,0,160),
 clap:()=>{noise(.12,1800,.7);noise(.12,2400,.6,.16)},
 five:()=>{noise(.07,3200,.8,0,2);tone(180,.1,'sine',.2,0,90)},
 magic:()=>{[523,659,784,988,1319,1568].forEach((f,i)=>tone(f,.28,'triangle',.14,i*.07))},
 whoosh:()=>noise(.4,900,.35,0,.6),
 win:()=>{[523,659,784,1047].forEach((f,i)=>tone(f,.4,'square',.1,i*.13));tone(1047,.7,'triangle',.18,.55)}
};
/* ---------- confetti ---------- */
const fx=$('#fx'),fc=fx.getContext('2d'); let parts=[];
function sizeFx(){fx.width=innerWidth;fx.height=innerHeight} sizeFx(); addEventListener('resize',sizeFx);
function confetti(n=140){ const cols=['#ff5d8f','#ffd23f','#1565d8','#3dcf8b','#ff8a00','#8a3ffc']; for(let i=0;i<n;i++)parts.push({x:innerWidth/2+(Math.random()-.5)*300,y:innerHeight*.4,vx:(Math.random()-.5)*16,vy:-Math.random()*16-4,r:Math.random()*8+5,c:cols[i%6],a:Math.random()*6,l:130+Math.random()*60}); if(parts.length===n)loopFx(); }
function loopFx(){ fc.clearRect(0,0,fx.width,fx.height); parts.forEach(p=>{p.x+=p.vx;p.y+=p.vy;p.vy+=.45;p.a+=.2;p.l--; fc.save();fc.translate(p.x,p.y);fc.rotate(p.a);fc.fillStyle=p.c;fc.fillRect(-p.r/2,-p.r/4,p.r,p.r/2);fc.restore();}); parts=parts.filter(p=>p.l>0&&p.y<innerHeight+40); if(parts.length)requestAnimationFrame(loopFx); else fc.clearRect(0,0,fx.width,fx.height); }
/* ---------- mascots ---------- */
function mascot(letter,color,cape){
 return `<svg viewBox="0 0 140 160" class="mascot">${cape?'<path d="M30 62 Q4 110 14 152 L72 126Z" fill="#e63946"/><path d="M110 62 Q136 110 126 152 L68 126Z" fill="#c92d3a"/>':''}
 <ellipse cx="70" cy="152" rx="36" ry="7" fill="rgba(0,0,0,.12)"/>
 <path d="M26 90 Q8 98 14 118" stroke="${color}" stroke-width="11" fill="none" stroke-linecap="round"/><path d="M114 90 Q132 98 126 118" stroke="${color}" stroke-width="11" fill="none" stroke-linecap="round"/>
 <rect x="22" y="22" width="96" height="114" rx="46" fill="${color}"/><ellipse cx="46" cy="40" rx="14" ry="7" fill="rgba(255,255,255,.3)"/>
 <circle cx="52" cy="58" r="13" fill="#fff"/><circle cx="90" cy="58" r="13" fill="#fff"/><circle cx="55" cy="60" r="6.5" fill="#1d2b4f"/><circle cx="87" cy="60" r="6.5" fill="#1d2b4f"/><circle cx="57" cy="57" r="2.4" fill="#fff"/><circle cx="89" cy="57" r="2.4" fill="#fff"/>
 <circle cx="36" cy="78" r="6" fill="#ff8fa3" opacity=".75"/><circle cx="104" cy="78" r="6" fill="#ff8fa3" opacity=".75"/>
 <path d="M58 80 Q70 94 82 80" stroke="#1d2b4f" stroke-width="4" fill="none" stroke-linecap="round"/>
 <text x="70" y="126" text-anchor="middle" font-family="Montserrat,Poppins,sans-serif" font-weight="800" font-size="40" fill="#fff">${letter}</text>
 <ellipse cx="52" cy="146" rx="15" ry="8" fill="#fff"/><ellipse cx="88" cy="146" rx="15" ry="8" fill="#fff"/></svg>`; }
/* ---------- markup renderer ---------- */
function render(markup){ return markup.split(' ').map(tok=>{
  const m=tok.match(/^([“"‘(]*)(.+?)([.,!?”"’)]*)$/); const lead=m[1],core=m[2],trail=m[3];
  const mm=core.match(/^\{(.+)\|(\w+)\}$/); const word=mm?mm[1]:core, p=mm?mm[2]:'';
  const sp=word+(trail.match(/[.,!?]/)||[''])[0];
  return `${lead}<span class="w${p?' p-'+p:''}" data-w="${word.toLowerCase()}" data-p="${p}" data-sp="${sp}" data-say="">${word}</span>${trail}`; }).join(' '); }
/* ---------- navigation ---------- */
const slides=$$('.slide'), N=slides.length;
$('#navList').innerHTML=slides.map((s,i)=>`<button class="nav" data-i="${i}"><i>${i+1}</i><span>${s.dataset.icon} ${s.dataset.title}</span></button>`).join('');
function go(i,quiet){ i=Math.max(0,Math.min(N-1,i)); stopSpeech(); slides[cur].classList.remove('active'); cur=i; slides[cur].classList.add('active'); if(!quiet)sfx.whoosh();
 $('#counter').textContent=(cur+1)+'/'+N; $('#barFill').style.width=((cur+1)/N*100)+'%'; $$('.nav').forEach((n,k)=>n.classList.toggle('on',k===cur));
 $$('.nav')[cur].scrollIntoView({block:'nearest'}); if(cur===12)syncScore(); }
$('#navList').addEventListener('click',e=>{const b=e.target.closest('.nav'); if(b)go(+b.dataset.i)});
$('#prev').onclick=()=>go(cur-1); $('#next').onclick=()=>go(cur+1);
$$('[data-go]').forEach(b=>b.addEventListener('click',()=>go(+b.dataset.go-1)));
function fit(){ const pane=$('#pane'),pw=pane.clientWidth-(document.body.classList.contains('fs')?12:28),ph=pane.clientHeight-(document.body.classList.contains('fs')?12:28);
 const s=Math.min(pw/1600,ph/900); const fr=$('#frame'); fr.style.width=1600*s+'px'; fr.style.height=900*s+'px'; $('#stage').style.transform=`scale(${s})`; }
addEventListener('resize',fit);
function toggleFs(){ if(!document.fullscreenElement){document.documentElement.requestFullscreen&&document.documentElement.requestFullscreen()}else document.exitFullscreen(); }
$('#fsBtn').onclick=toggleFs;
document.addEventListener('fullscreenchange',()=>{document.body.classList.toggle('fs',!!document.fullscreenElement);setTimeout(fit,60)});
addEventListener('keydown',e=>{ if(e.key==='ArrowRight'||e.key==='PageDown')go(cur+1); else if(e.key==='ArrowLeft'||e.key==='PageUp')go(cur-1); else if(e.key==='f'||e.key==='F')toggleFs(); else if(e.key==='m'||e.key==='M')$('#muteBtn').click(); });
$('#muteBtn').onclick=()=>{muted=!muted;$('#muteBtn').textContent=muted?'🔇':'🔊';if(muted)stopSpeech()};
$('#spdBtn').onclick=()=>{ const o=[1,.75,1.2]; speedMul=o[(o.indexOf(speedMul)+1)%3]; $('#spdBtn').textContent=speedMul+'×'; speak('This is my voice speed.'); };
/* generic: click any [data-say] to hear it; teacher script buttons */
document.addEventListener('click',e=>{ ac();
 const sb=e.target.closest('[data-script]'); if(sb){ const sc=sb.closest('.teach').querySelector('.script'); speak(sc.textContent.replace(/\s+/g,' ').replace(/Teacher:/,''),{rate:.88}); return; }
 const t=e.target.closest('[data-say]'); if(t&&t.dataset.say){ sfx.pop(); speak(t.dataset.say,{rate:.8}); } });

/* ================= SLIDE 1 ================= */
(function(){ const cols=['#ff5d8f','#ffb300','#2f7df6','#3dcf8b','#8a3ffc'],L=['a','e','i','o','u'],S=['a','ee','eye','oh','you'];
 $('#vrow').innerHTML=L.map((l,i)=>`<div class="m clk float" style="animation-delay:${i*.35}s;height:${[205,230,205,218,198][i]}px" data-say="${l==='a'?'ay':l==='e'?'ee':l==='i'?'eye':l==='o'?'oh':'you'}">${mascot(l,cols[i])}</div>`).join('');
 $('#gm1').innerHTML=mascot('e','#ff5d8f'); $('#gm2').innerHTML=mascot('a','#2f7df6'); $('#gm3').innerHTML=mascot('e','#2f7df6',true); })();

/* ================= SLIDE 2 ================= */
$('#s2ask').onclick=()=>{ speak('What do you think a long vowel might sound like?'); $('#askBox').classList.add('pop'); setTimeout(()=>$('#askBox').classList.remove('pop'),600); };
$('#s2ans').onclick=()=>{ $('#ansBox').className='askbox show'; $('#ansBox').style.cssText='background:#e6fbf1;border-color:#b6ecd2'; sfx.ding(); speak('A long vowel says its own name. A, E, I, O, U.'); award('s2',10,1); };

/* ================= SLIDE 3 ================= */
$('#magicE').innerHTML=mascot('e','#2f7df6',true);
$('#cast').onclick=()=>{ const m=$('#magicE'); m.classList.remove('float'); m.classList.add('hop'); sfx.magic();
 setTimeout(()=>{ const e=$('#capE'); e.style.opacity=1; e.classList.add('in'); $('#capR .a').style.textShadow='0 0 24px #ffb300'; speak('cap... cape!',{rate:.7}); },500);
 setTimeout(()=>{m.classList.remove('hop');m.classList.add('float');},900); award('s3a',15,1); };
$('#castReset').onclick=()=>{ $('#capE').style.opacity=.15; $('#capE').classList.remove('in'); $('#capR .a').style.textShadow='none'; };
const PAIRS=[['cap','cape','🧢','#e6f0ff'],['kit','kite','🪁','#fff4dc'],['hop','hope','🐰','#ffe8ef'],['tub','tube','🧴','#e8f7ec']];
$('#pairs').innerHTML=PAIRS.map((p,i)=>`<div class="pair clk" data-i="${i}" style="background:${p[3]}"><div class="em">${p[2]}</div><div class="tx"><span class="w1">${p[0]}</span> → <span>${p[0]}<span class="e">e</span></span></div></div>`).join('');
$$('#pairs .pair').forEach(el=>el.addEventListener('click',()=>{ const p=PAIRS[+el.dataset.i]; el.classList.remove('pop'); void el.offsetWidth; el.classList.add('pop'); sfx.magic(); speak(p[0]+'... '+p[1],{rate:.7}); award('pair'+el.dataset.i,5,0); }));

/* ================= SLIDE 4 ================= */
const WORDS=[['cat',0],['cape',1],['hop',0],['hope',1],['kit',0],['kite',1],['tub',0],['tube',1],['pet',0],['Pete',1]];
let selW=null,doneW=0,corr=0;
function buildWG(){ selW=null;doneW=0;corr=0; $('#wgrid').innerHTML=WORDS.map((w,i)=>`<button class="wb" data-i="${i}">${w[0]}<span class="bd"></span></button>`).join(''); score4(); }
function score4(){ $('#s4score').textContent=`Score: ${corr} / 10 — ${doneW===10?'All done!':'tap a word to begin'}`; }
$('#wgrid').addEventListener('click',e=>{ const b=e.target.closest('.wb'); if(!b||b.dataset.done)return; $$('.wb').forEach(x=>x.classList.remove('sel')); b.classList.add('sel'); selW=b; speak(WORDS[+b.dataset.i][0],{rate:.75}); sfx.pop(); });
function answer(long){ if(!selW)return toast('Tap a word first 👆'); const w=WORDS[+selW.dataset.i], ok=(w[1]===1)===long; long?sfx.clap():sfx.five();
 selW.dataset.done=1; selW.classList.remove('sel'); doneW++; const bd=selW.querySelector('.bd');
 if(ok){selW.classList.add('ok');bd.textContent=long?'👏':'✋';corr++;setTimeout(sfx.ding,250);award('w'+w[0],5,0);} else {selW.classList.add('hint');bd.textContent=w[1]?'👏':'✋';}
 selW=null; score4(); if(doneW===10){ award('s4',20,1); setTimeout(()=>{confetti();sfx.win();},400);} }
$('#bClap').onclick=()=>answer(true); $('#bHigh').onclick=()=>answer(false); $('#s4reset').onclick=buildWG; buildWG();

/* ================= SLIDE 5 ================= */
$('#mA').innerHTML=mascot('a','#2f7df6'); $('#mI').innerHTML=mascot('i','#ffb300');
$('#join').onclick=()=>{ $('#team').classList.add('joined'); sfx.magic(); setTimeout(()=>{$('#aiBig').className='wcard show';speak('A I. These two letters are a team. They say A, as in rain.',{rate:.85})},700); award('s5a',10,1); };
const AIW=[['rain','🌧️'],['train','🚂'],['mail','✉️'],['tail','🦊'],['rainbow','🌈']];
$('#aiWords').innerHTML=AIW.map(w=>`<div class="pair clk" data-say="${w[0]}"><div class="em">${w[1]}</div><div class="tx">${w[0].replace('ai','<span style="color:var(--blue)">ai</span>')}</div></div>`).join('');

/* ================= SLIDE 6 ================= */
$('#tg').innerHTML=TOOLKIT.map(t=>`<div class="tile" style="background:${t.bg}"><div class="hd p-${t.c} clk" data-say="${t.say}"><b>${t.p.toUpperCase()}</b><span>${t.em}</span></div><div class="ws">${t.w.map(w=>`<b data-say="${w}">${w}</b>`).join('')}</div></div>`).join('')+`<div class="tile" style="background:#fff;border:3px dashed #cfdcf0;align-items:center;justify-content:center;text-align:center"><div style="font-size:70px">🎧</div><div style="font-size:26px;font-weight:800;color:var(--muted)">Hear all five teams</div><button class="btn sm blue" id="hearAll">▶ Play</button></div>`;
$('#hearAll').onclick=()=>{ let i=0; const nx=()=>{ if(i>=TOOLKIT.length)return; const t=TOOLKIT[i++]; speak(t.say,{rate:.85,onend:()=>setTimeout(nx,300)}); }; nx(); award('s6',10,1); };

/* ================= SLIDE 7 ================= */
$('#sents').innerHTML=SENTENCES.map((s,i)=>`<div class="srow" data-i="${i}"><div class="em">${s.e}</div><div class="tx pat">${render(s.m)}</div><button class="play">▶</button></div>`).join('');
function $$$(s,r){return [...r.querySelectorAll(s)]}
$('#sents').addEventListener('click',e=>{ const r=e.target.closest('.srow'); if(r){ karaoke($$$('.w',r)); award('sent'+r.dataset.i,5,0); } });
$('#readAll').onclick=()=>{ const rows=$$('#sents .srow'); let i=0; const next=()=>{ if(i>=rows.length){award('s7',15,1);return;} const r=rows[i++]; karaoke($$$('.w',r),()=>setTimeout(next,400)); }; next(); };

/* ================= SLIDE 8 ================= */
$('#passage').innerHTML=PASSAGE.map(p=>`<p>${render(p)}</p>`).join('');
$('#pRead').onclick=()=>karaoke($$('#passage .w'),()=>award('s8',15,1)); $('#pStop').onclick=stopSpeech;
$('#pPat').onclick=()=>{ $('#passage').classList.toggle('pat'); $('#passage').classList.toggle('nopat'); };
$('#passage').addEventListener('click',e=>{ const w=e.target.closest('.w'); if(w){ sfx.pop(); speak(w.textContent,{rate:.75}); } });

/* ================= SLIDE 9 ================= */
const MIS=[
 {t:'Mission 1 – Find Magic e Words',p:'m',w:['jake','kite','like','time','game','smile'],h:'Look for a silent e at the end of the word!'},
 {t:'Mission 2 – Find AI',p:'ai',w:['rain','rainbow'],h:'Find the team a + i.'},
 {t:'Mission 3 – Find AY',p:'ay',w:['day','may'],h:'Find the team a + y.'},
 {t:'Mission 4 – Find EE',p:'ee',w:['green','see'],h:'Find two e’s together.'},
 {t:'Mission 5 – Find OA',p:'oa',w:['road'],h:'Find the team o + a.'},
 {t:'Mission 6 – Find OW',p:'ow',w:['down'],h:'Find the team o + w.'}];
let mi=0; const found=MIS.map(()=>new Set());
$('#dpass').innerHTML=PASSAGE.map(p=>`<p>${render(p)}</p>`).join('');
$('#mp').innerHTML=MIS.map((m,i)=>`<button class="mb" data-i="${i}">🔍 Mission ${i+1}</button>`).join('');
function drawMission(){ const m=MIS[mi]; $$('#mp .mb').forEach((b,i)=>{ b.classList.toggle('on',i===mi); b.classList.toggle('done',MIS[i].w.every(w=>found[i].has(w))); });
 $('#mission').innerHTML=`<div style="font-size:70px">🕵️</div><div><h2>${m.t}</h2><p>${m.h}</p></div><div class="tgt">${m.w.map(w=>found[mi].has(w)?`<b class="f">${w==='jake'?'Jake':w}</b>`:'<b>?</b>').join('')}</div>`; }
$('#mp').addEventListener('click',e=>{ const b=e.target.closest('.mb'); if(!b)return; mi=+b.dataset.i; drawMission(); speak(MIS[mi].t.replace('–',', '),{rate:.85}); });
$('#dpass').addEventListener('click',e=>{ const s=e.target.closest('.w'); if(!s)return; const m=MIS[mi], w=s.dataset.w, p=s.dataset.p;
 const mark=()=>$$('#dpass .w').filter(x=>x.dataset.w===w).forEach(x=>{x.classList.add('found','p-'+p)});
 if(m.w.includes(w)&&!found[mi].has(w)){ found[mi].add(w); mark(); sfx.ding(); speak(s.textContent,{rate:.75}); award('f'+mi+w,10,0);
   if(m.w.every(x=>found[mi].has(x))){ award('m'+mi,10,1); setTimeout(()=>{confetti(80);sfx.win();toast('⭐ Mission '+(mi+1)+' complete!');},350);
     if(MIS.every((mm,i)=>mm.w.every(x=>found[i].has(x)))){ award('s9',30,2); setTimeout(()=>{speak('Fantastic! You found phonics rules hiding inside a real story.');confetti(220)},1600);} } }
 else if(m.w.includes(w)){ speak(s.textContent,{rate:.75}); }
 else if(p===m.p&&!found[mi].has(w)){ found[mi].add('bonus'+w); mark(); sfx.ding(); toast('⭐ Bonus find: '+s.textContent); award('b'+w,10,1); }
 else { sfx.boop(); s.classList.add('shake'); setTimeout(()=>s.classList.remove('shake'),400); toast('Keep looking, detective! 🔍'); }
 drawMission(); });
drawMission();

/* ================= SLIDE 10 ================= */
let qi=0,qdone=false,tLeft=300,tRun=null;
function drawQ(){ const q=QUESTIONS[qi]; qdone=false; $('#qEm').textContent=q.e; $('#qTx').textContent=q.q;
 $('#opts').innerHTML=q.o.map((o,i)=>`<button class="opt" data-i="${i}">${['A','B','C'][i]}.  ${o}</button>`).join('');
 $('#dots').innerHTML=QUESTIONS.map((_,i)=>`<i class="${i<qi?'dn':i===qi?'on':''}"></i>`).join(''); $('#qNext').textContent=qi===QUESTIONS.length-1?'Finish 🎉':'Next question →'; }
$('#opts').addEventListener('click',e=>{ const b=e.target.closest('.opt'); if(!b)return; const q=QUESTIONS[qi];
 if(+b.dataset.i===q.a){ b.classList.add('ok'); sfx.ding(); qdone=true; award('q'+qi,10,1); speak(q.o[q.a]+'! Well done.',{rate:.9}); }
 else { b.classList.add('no','shake'); sfx.boop(); setTimeout(()=>b.classList.remove('shake'),400); toast('Try again! 💪'); } });
$('#qNext').onclick=()=>{ if(!qdone)return toast('Pick an answer first 😊'); if(qi<QUESTIONS.length-1){qi++;drawQ();speak(QUESTIONS[qi].q)} else { confetti(); sfx.win(); speak('Great job, story detective!'); qi=0; drawQ(); } };
$('#qSay').onclick=()=>speak(QUESTIONS[qi].q);
$('#tmrBtn').onclick=()=>{ if(tRun){clearInterval(tRun);tRun=null;$('#tmrBtn').textContent='▶ Start';return;} $('#tmrBtn').textContent='⏸ Pause';
 tRun=setInterval(()=>{ tLeft--; $('#tmr').textContent=Math.floor(tLeft/60)+':'+String(tLeft%60).padStart(2,'0'); if(tLeft<=0){clearInterval(tRun);tRun=null;sfx.win();toast('⏱ Time’s up!');} },1000); };
drawQ();

/* ================= SLIDE 11 ================= */
let st11=0; const S11=[
 ['Step 1 — ask the child about the letter c.','“What sound does the c make?”'],
 ['Step 2 — reveal the sound.','The c in cat makes the /k/ sound.'],
 ['Step 3 — now look at a new word.','“Now look at… city. What sound does the c make here?”'],
 ['Step 4 — the surprise!','“Whoa! The same letter C can sometimes make different sounds!”'],
 ['Step 5 — the mystery.','“How can we know which sound it will make? That’s our mystery for next time.”']];
function draw11(){ $('#s11sub').textContent=S11[Math.min(st11,4)][0]; $('#s11say').textContent=S11[Math.min(st11,4)][1];
 $('#sdK').className='sd '+(st11>=1?'show':'hidden'); $('#arrowC').className='float '+(st11>=2?'show':'hidden'); $('#cwCity').className='cw clk '+(st11>=2?'show':'hidden');
 $('#sdS').className='sd '+(st11>=3?'show':'hidden'); $('#mysteryQ').className=(st11>=4?'show':'hidden'); $('#s11next').textContent=st11>=4?'✔ Done':'Next step ▶'; }
$('#s11next').onclick=()=>{ if(st11<4){st11++;draw11();sfx.pop();speak($('#s11say').textContent.replace(/[“”]/g,''),{rate:.88}); if(st11===1)setTimeout(()=>speak('kuh'),1800); if(st11===3)setTimeout(()=>speak('sss'),2500);} else {confetti(80);sfx.win();award('s11',15,1);} };
$('#s11reset').onclick=()=>{st11=0;draw11()}; $('#s11spk').onclick=()=>speak($('#s11say').textContent.replace(/[“”]/g,''),{rate:.88}); draw11();

/* ================= SLIDE 12 ================= */
$('#hwList').innerHTML=HOMEWORK.map((h,i)=>`<div class="hw clk" data-i="${i}"><div class="n">${i+1}</div><div class="t">${h.t}<small>${h.s}</small></div><div class="ck">✔</div></div>`).join('');
$('#hwList').addEventListener('click',e=>{ const h=e.target.closest('.hw'); if(!h)return; h.classList.toggle('done'); sfx.ding(); speak(HOMEWORK[+h.dataset.i].t,{rate:.9}); award('hw'+h.dataset.i,5,0); });

/* ================= SLIDE 13 ================= */
$('#objs').innerHTML=OBJECTIVES.map((o,i)=>`<div class="hw clk" data-i="${i}" style="padding:12px 18px"><div class="ck" style="width:44px;height:44px;font-size:28px">✔</div><div class="t" style="font-size:24px">${o}</div></div>`).join('');
$('#objs').addEventListener('click',e=>{ const h=e.target.closest('.hw'); if(!h)return; h.classList.toggle('done'); sfx.ding(); award('ob'+h.dataset.i,5,1); if($$('#objs .hw.done').length===OBJECTIVES.length){confetti(220);sfx.win();speak('Wow! You reached every goal today. Fantastic reading!');} });
$('#celebrate').onclick=()=>{confetti(240);sfx.win();speak('Hooray! Great job, Reader!');};

/* ================= START ================= */
go(0,true); fit(); setTimeout(fit,300);
</script>
</body>
</html>
