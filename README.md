<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  <title>A Little Universe for Fariddayy ♡ 27</title>
  <meta name="description" content="A little indie universe, made just for you. Happy 27th, Fariddayy.">
  <meta name="theme-color" content="#250611">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@500;700&family=Courier+Prime:ital,wght@0,400;0,700;1,400&family=DM+Serif+Display:ital@0;1&family=Special+Elite&display=swap" rel="stylesheet">
  <style>
/* =========================================================
   REALITY CLUB: A LITTLE UNIVERSE FOR YOU
   burgundy · cream · dusty pink · vintage brown
   ========================================================= */

:root {
  --burg-d: #250611;
  --burg: #4a0f1f;
  --burg-m: #6e1b30;
  --cream: #f4e8d2;
  --cream-d: #e6d3b0;
  --pink: #d8a0a4;
  --pink-d: #b9707a;
  --brown: #6a4631;
  --ink: #3a1a18;
  --gold: #e9c47c;

  --serif: 'DM Serif Display', Georgia, 'Times New Roman', serif;
  --type: 'Special Elite', 'Courier New', monospace;
  --mono: 'Courier Prime', 'Courier New', monospace;
  --hand: 'Caveat', 'Segoe Script', 'Comic Sans MS', cursive;

  --nav-h: 76px;
  --top-h: 52px;
  --grain: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='220' height='220'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='2' stitchTiles='stitch'/%3E%3CfeColorMatrix values='0 0 0 0 0  0 0 0 0 0  0 0 0 0 0  0 0 0 .55 0'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html, body {
  height: 100%;
  overflow: hidden;
  background: var(--burg-d);
  color: var(--cream);
  font-family: var(--mono);
  -webkit-text-size-adjust: 100%;
}

body {
  background:
    radial-gradient(1000px 600px at 15% 10%, rgba(110, 27, 48, .75), transparent 60%),
    radial-gradient(900px 600px at 90% 90%, rgba(185, 112, 122, .22), transparent 60%),
    var(--burg-d);
}

button { font: inherit; color: inherit; cursor: pointer; }

/* ---------- global layers ---------- */
.grain {
  position: fixed; inset: 0; z-index: 90; pointer-events: none;
  background-image: var(--grain);
  opacity: .16; mix-blend-mode: overlay;
  animation: grainShift 1.2s steps(6) infinite;
}
@keyframes grainShift {
  0% { transform: translate(0, 0); }
  20% { transform: translate(-3%, 2%); }
  40% { transform: translate(2%, -3%); }
  60% { transform: translate(-2%, -1%); }
  80% { transform: translate(3%, 3%); }
  100% { transform: translate(0, 0); }
}

#bgStars { position: fixed; inset: 0; z-index: 0; pointer-events: none; overflow: hidden; }
.bg-star {
  position: absolute; color: var(--cream); opacity: .25;
  animation: twinkle var(--d, 4s) ease-in-out infinite var(--delay, 0s);
}
@keyframes twinkle { 0%, 100% { opacity: .1; transform: scale(.8); } 50% { opacity: .7; transform: scale(1.15); } }

.topbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 40;
  height: var(--top-h);
  display: flex; align-items: center; justify-content: space-between; gap: 12px;
  padding: 0 18px;
  font-family: var(--type); font-size: .68rem; letter-spacing: .18em; color: var(--pink);
  background: linear-gradient(to bottom, rgba(37, 6, 17, .95), rgba(37, 6, 17, 0));
}
.brand { white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.counter { color: var(--cream); white-space: nowrap; }

.progress { position: fixed; top: 0; left: 0; right: 0; height: 3px; z-index: 41; background: rgba(244, 232, 210, .08); }
.progress-fill { height: 100%; width: 0; background: linear-gradient(90deg, var(--pink), var(--gold)); transition: width .8s cubic-bezier(.6, 0, .2, 1); }

/* ---------- stage + scenes ---------- */
#stage { position: fixed; inset: 0; z-index: 10; }

.scene {
  position: absolute; inset: 0;
  display: flex;
  padding: calc(var(--top-h) + 14px) 22px calc(var(--nav-h) + 22px);
  overflow-x: hidden; overflow-y: auto;
  opacity: 0; visibility: hidden;
  transform: translateY(26px) scale(.985);
  transition: opacity .7s ease, transform .7s ease, visibility 0s linear .7s;
  -webkit-overflow-scrolling: touch;
}
.scene.active {
  opacity: 1; visibility: visible; transform: none;
  transition: opacity .7s ease, transform .7s ease, visibility 0s;
}

.scene-inner {
  position: relative; z-index: 2;
  margin: auto; width: 100%; max-width: 1060px;
  display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 28px;
}
.scene-inner.column { max-width: 720px; }
.scene-inner.split { gap: 44px; }
.center-text { text-align: center; }

@media (min-width: 860px) {
  .scene-inner.split { flex-direction: row; gap: 72px; }
  .scene-inner.split.reverse { flex-direction: row; }
  .scene-inner.split > .copy { flex: 1 1 0; max-width: 480px; }
}

/* reveal animation (re-runs each time a scene becomes active) */
@keyframes rise { from { opacity: 0; transform: translateY(18px); } to { opacity: 1; transform: none; } }
.scene.active .reveal { animation: rise .85s cubic-bezier(.2, .7, .2, 1) both; animation-delay: calc(var(--i, 0) * 110ms + 200ms); }

/* ---------- typography ---------- */
.kicker {
  font-family: var(--type); font-size: .72rem; letter-spacing: .28em; text-transform: uppercase;
  color: var(--pink);
}
.display {
  font-family: var(--serif); font-weight: 400; text-transform: uppercase;
  font-size: clamp(1.8rem, 5.6vw, 3.1rem); line-height: 1.04; letter-spacing: .01em;
  color: var(--cream);
  text-shadow: 3px 3px 0 var(--burg-m);
}
.display.huge { font-size: clamp(2.2rem, 8.4vw, 4.6rem); }
.hand-title { font-family: var(--hand); font-weight: 700; font-size: clamp(2rem, 6vw, 2.8rem); line-height: 1.05; color: var(--burg-m); }
.hand { font-family: var(--hand); font-size: 1.55rem; color: var(--pink); line-height: 1.15; }
.hand.big { font-size: clamp(1.7rem, 5vw, 2.4rem); color: var(--gold); max-width: 600px; }
.lead { font-family: var(--serif); font-style: italic; font-size: clamp(1.15rem, 3.4vw, 1.6rem); line-height: 1.3; color: var(--cream-d); max-width: 600px; }

.copy { display: flex; flex-direction: column; gap: 16px; font-size: 1rem; line-height: 1.72; color: var(--cream); }
.copy .display { margin-bottom: 4px; }
.copy.center-text { align-items: center; max-width: 560px; }
p { font-size: 1rem; line-height: 1.72; }

/* ---------- buttons ---------- */
.btn {
  display: inline-block;
  font-family: var(--type); font-size: .85rem; letter-spacing: .14em; text-transform: uppercase;
  color: var(--burg); background: var(--cream);
  border: 2px solid var(--cream); border-radius: 999px;
  padding: 14px 26px;
  box-shadow: 4px 4px 0 var(--pink-d);
  transition: transform .15s ease, box-shadow .15s ease, background .2s ease;
}
.btn:hover { transform: translate(-1px, -2px); box-shadow: 6px 6px 0 var(--pink-d); background: #fff6e4; }
.btn:active { transform: translate(3px, 3px); box-shadow: 1px 1px 0 var(--pink-d); }
.btn.ghost { background: transparent; color: var(--cream); box-shadow: none; }
.btn.ghost:hover { background: rgba(244, 232, 210, .1); box-shadow: none; }
.btn.small { padding: 10px 18px; font-size: .74rem; }
.btn:focus-visible, .nav-btn:focus-visible, .dot:focus-visible, .hidden-star:focus-visible, .vinyl:focus-visible {
  outline: 3px dashed var(--gold); outline-offset: 4px;
}

/* ---------- bottom nav ---------- */
.bottomnav {
  position: fixed; left: 0; right: 0; bottom: 0; z-index: 50;
  height: var(--nav-h);
  display: flex; align-items: center; justify-content: center; gap: 16px;
  padding: 0 16px env(safe-area-inset-bottom, 0);
  background: linear-gradient(to top, rgba(37, 6, 17, .96) 40%, rgba(37, 6, 17, 0));
}
.nav-btn {
  width: 46px; height: 46px; border-radius: 50%;
  background: rgba(244, 232, 210, .08); border: 1.5px solid rgba(244, 232, 210, .35);
  font-size: 1.15rem; line-height: 1;
  transition: background .2s, opacity .2s, transform .15s;
}
.nav-btn:hover:not(:disabled) { background: rgba(244, 232, 210, .2); }
.nav-btn:disabled { opacity: .25; cursor: not-allowed; }
.nav-btn.hidden { visibility: hidden; }
.nav-btn.nudge { animation: shake .5s; }
@keyframes shake { 0%, 100% { transform: translateX(0); } 20% { transform: translateX(-6px); } 40% { transform: translateX(6px); } 60% { transform: translateX(-4px); } 80% { transform: translateX(4px); } }

.dots { display: flex; gap: 10px; align-items: center; }
.dot {
  width: 11px; height: 11px; border-radius: 50%;
  border: 1.5px solid rgba(244, 232, 210, .5); background: transparent; padding: 0;
  transition: transform .25s, background .25s, opacity .25s;
}
.dot.visited { background: rgba(216, 160, 164, .7); border-color: var(--pink); }
.dot.active { background: var(--gold); border-color: var(--gold); transform: scale(1.35); }
.dot.locked { opacity: .3; cursor: not-allowed; }

/* ---------- sparkles + doodles ---------- */
.sparkles { position: absolute; inset: 0; z-index: 1; pointer-events: none; overflow: hidden; }
.sparkle { position: absolute; color: var(--gold); opacity: .4; animation: drift var(--d, 7s) ease-in-out infinite var(--delay, 0s); }
@keyframes drift {
  0%, 100% { transform: translateY(0) rotate(0deg) scale(.9); opacity: .15; }
  50% { transform: translateY(-16px) rotate(20deg) scale(1.15); opacity: .8; }
}

.ghost-num {
  position: absolute; z-index: 0; right: -2vw; bottom: 4vh; pointer-events: none;
  font-family: var(--serif); font-size: clamp(12rem, 38vw, 30rem); line-height: .8;
  color: transparent; -webkit-text-stroke: 2px rgba(216, 160, 164, .16);
}

/* ---------- SCENE 1 · opening letter ---------- */
.letter-card {
  position: relative; max-width: 520px; width: 100%;
  background: var(--cream); color: var(--ink);
  padding: 44px 34px 34px;
  box-shadow: 0 26px 60px rgba(0, 0, 0, .55);
  display: flex; flex-direction: column; gap: 14px; align-items: flex-start;
  background-image:
    repeating-linear-gradient(to bottom, transparent 0 31px, rgba(185, 112, 122, .22) 31px 32px),
    var(--grain);
  background-blend-mode: normal, multiply;
}
.letter-card.tilt-l { transform: rotate(-1.6deg); }
.letter-card .kicker { color: var(--pink-d); }
.letter-card .btn { margin-top: 8px; }
.seal {
  position: absolute; top: -22px; right: 30px; width: 54px; height: 54px; border-radius: 50%;
  display: grid; place-items: center; font-size: 1.5rem; color: var(--cream);
  background: radial-gradient(circle at 35% 30%, #a42a45, var(--burg));
  box-shadow: 0 5px 12px rgba(0, 0, 0, .5), inset 0 -3px 6px rgba(0, 0, 0, .35);
}

/* ---------- SCENE 2 · age roll ---------- */
.age {
  display: inline-flex; align-items: flex-start;
  font-family: var(--serif); font-size: clamp(7rem, 30vw, 13rem); line-height: 1;
  color: var(--cream); text-shadow: 6px 6px 0 var(--burg-m);
}
.age .roll-window { display: inline-block; height: 1em; overflow: hidden; }
.age .roll-strip { display: flex; flex-direction: column; transition: transform 1.3s cubic-bezier(.7, 0, .2, 1); }
.age .roll-strip span { display: block; height: 1em; line-height: 1; }
.age.rolled .roll-strip { transform: translateY(-50%); }
.age.rolled { animation: pop .8s 1.2s both; }
@keyframes pop { 0% { transform: scale(1); } 40% { transform: scale(1.1) rotate(-2deg); color: var(--gold); } 100% { transform: scale(1); } }

/* ---------- photos: polaroids ---------- */
.polaroid {
  position: relative; flex: none;
  width: min(78vw, 340px);
  padding: 14px 14px 62px;
  background-color: #f8f1e2;
  background-image: var(--grain); background-blend-mode: multiply;
  box-shadow: 0 22px 46px rgba(0, 0, 0, .55), 0 0 0 1px rgba(0, 0, 0, .06);
  transform: rotate(var(--r, -3deg));
  animation: floaty 7s ease-in-out infinite;
}
@keyframes floaty {
  0%, 100% { transform: translateY(0) rotate(var(--r, -3deg)); }
  50% { transform: translateY(-9px) rotate(calc(var(--r, -3deg) + 1.2deg)); }
}
.scene.active .polaroid.reveal { animation: rise .85s cubic-bezier(.2, .7, .2, 1) both, floaty 7s ease-in-out 1.3s infinite; animation-delay: .2s, 1.3s; }

.photo-wrap { position: relative; aspect-ratio: 4 / 5; overflow: hidden; background: var(--burg-d); }
.photo-wrap img.photo {
  position: absolute; inset: 0; width: 100%; height: 100%;
  object-fit: cover; object-position: 50% 30%;
  filter: sepia(.16) contrast(1.05) saturate(.95);
}
.photo-wrap::after {
  content: ""; position: absolute; inset: 0; pointer-events: none;
  background: var(--grain), radial-gradient(circle at 50% 45%, transparent 55%, rgba(37, 6, 17, .45));
  background-blend-mode: overlay, normal; opacity: .5;
}
.placeholder { display: none; }
.photo-wrap.missing img.photo { display: none; }
.photo-wrap.missing .placeholder {
  position: absolute; inset: 0; z-index: 1;
  display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 8px; text-align: center;
  padding: 16px; color: var(--cream);
  background:
    radial-gradient(circle at 30% 25%, rgba(216, 160, 164, .35), transparent 55%),
    linear-gradient(160deg, var(--burg-m), var(--burg-d));
  border: 2px dashed rgba(244, 232, 210, .35);
}
.ph-star { font-size: 2.6rem; color: var(--gold); }
.ph-title { font-family: var(--type); font-size: .85rem; letter-spacing: .12em; }
.ph-sub { font-family: var(--hand); font-size: 1.3rem; color: var(--pink); }
.placeholder.mini .ph-star { font-size: 1.6rem; }

.tape {
  position: absolute; top: -15px; left: 50%; z-index: 3;
  width: 112px; height: 32px; transform: translateX(-50%) rotate(3deg);
  background: rgba(233, 196, 124, .6);
  box-shadow: 0 1px 3px rgba(0, 0, 0, .25);
  clip-path: polygon(0 8%, 4% 0, 8% 10%, 12% 0, 92% 0, 96% 10%, 100% 0, 100% 92%, 96% 100%, 92% 90%, 88% 100%, 8% 100%, 4% 90%, 0 100%);
}
.tape.pink { background: rgba(216, 160, 164, .7); transform: translateX(-50%) rotate(-4deg); }

.caption {
  position: absolute; left: 0; right: 0; bottom: 14px; padding: 0 10px; text-align: center;
  font-family: var(--hand); font-size: 1.6rem; line-height: 1; color: var(--brown);
}
.date-stamp {
  position: absolute; right: 10px; bottom: 10px; z-index: 2;
  font-family: var(--type); font-size: .78rem; letter-spacing: .14em;
  color: #f0a04b; text-shadow: 0 0 6px rgba(240, 160, 75, .7);
}

/* ---------- SCENE 4 · together ---------- */
.scene-together::before {
  content: ""; position: absolute; inset: 0; z-index: 0; pointer-events: none;
  background:
    radial-gradient(700px 500px at 28% 50%, rgba(216, 160, 164, .28), transparent 65%),
    radial-gradient(500px 400px at 85% 15%, rgba(110, 27, 48, .6), transparent 70%);
}
.together-stack { position: relative; padding: 20px 26px 40px; flex: none; }
.polaroid.together { width: min(74vw, 400px); padding: 16px 16px 70px; }
.polaroid.together .photo-wrap { aspect-ratio: 4 / 5; }
.polaroid.together .caption { font-size: 1.7rem; bottom: 18px; }

.filmstrip {
  position: absolute; right: -4px; bottom: -6px; z-index: 4;
  width: 132px; padding: 10px 16px 18px;
  background: #1a0a0c; transform: rotate(9deg);
  box-shadow: 0 12px 26px rgba(0, 0, 0, .55);
  animation: floaty2 8s ease-in-out infinite;
  --r2: 9deg;
}
@keyframes floaty2 { 0%, 100% { transform: translateY(0) rotate(9deg); } 50% { transform: translateY(-7px) rotate(7deg); } }
.filmstrip::before, .filmstrip::after {
  content: ""; position: absolute; top: 0; bottom: 0; width: 8px;
  background: repeating-linear-gradient(to bottom, transparent 0 6px, rgba(244, 232, 210, .85) 6px 12px, transparent 12px 18px);
  -webkit-mask: linear-gradient(#000 0 0); opacity: .8;
}
.filmstrip::before { left: 3px; }
.filmstrip::after { right: 3px; }
.filmstrip .frame { aspect-ratio: 1 / 1; }
.filmstrip .frame img.photo { object-position: 50% 28%; filter: sepia(.35) contrast(1.1); }
.frame-no { display: block; margin-top: 6px; font-family: var(--type); font-size: .62rem; letter-spacing: .2em; color: #f0a04b; text-align: right; }

.doodle { position: absolute; z-index: 5; color: var(--pink); pointer-events: none; }
.d-heart1 { width: 46px; top: -6px; left: 2px; transform: rotate(-14deg); animation: floaty3 5s ease-in-out infinite; }
.d-heart2 { width: 26px; top: 58px; right: 2px; color: var(--pink-d); transform: rotate(12deg); animation: floaty3 6s ease-in-out infinite .6s; }
.d-star1 { top: 16px; right: 38px; font-size: 1.4rem; color: var(--gold); }
.d-star2 { bottom: 128px; left: -2px; font-size: 1.1rem; color: var(--gold); }
@keyframes floaty3 { 0%, 100% { translate: 0 0; } 50% { translate: 0 -8px; } }
.note {
  position: absolute; z-index: 5; font-family: var(--hand); font-size: 1.35rem; color: var(--cream-d);
  text-shadow: 0 1px 4px rgba(0, 0, 0, .6); pointer-events: none;
}
.n-1 { top: -14px; left: 56px; transform: rotate(-6deg); }
.n-2 { bottom: 4px; left: 6px; transform: rotate(-4deg); color: var(--pink); }

/* ---------- SCENE 5 · game ---------- */
.scene-game { overflow: hidden; }
.game-card {
  position: relative; z-index: 3; width: 100%; max-width: 560px;
  display: flex; flex-direction: column; align-items: center; gap: 18px; text-align: center;
  padding: 36px 28px;
  background: rgba(37, 6, 17, .6);
  border: 2px dashed rgba(216, 160, 164, .5); border-radius: 6px;
  backdrop-filter: blur(3px);
}
.game-card .display { font-size: clamp(1.5rem, 4.6vw, 2.3rem); }
.game-card.reward { display: none; }
.scene-game.won #gameIntro { display: none; }
.scene-game.won .game-card.reward { display: flex; animation: rise .8s both; }

.star-counter { display: flex; align-items: center; gap: 8px; font-size: 1.7rem; color: var(--gold); }
.star-counter .slot { transition: transform .4s cubic-bezier(.3, 1.8, .5, 1), color .3s; opacity: .8; }
.star-counter .slot.on { transform: scale(1.25) rotate(360deg); color: var(--gold); text-shadow: 0 0 14px rgba(233, 196, 124, .9); }
.star-counter .count { margin-left: 10px; font-family: var(--type); font-size: .85rem; letter-spacing: .15em; color: var(--cream); }
.hint { opacity: 0; transition: opacity .8s; font-size: 1.4rem; }
.hint.show { opacity: 1; }

.hidden-star {
  position: absolute; z-index: 5; left: var(--x); top: var(--y);
  width: 48px; height: 48px; margin: -24px 0 0 -24px;
  display: grid; place-items: center;
  background: none; border: none; font-size: 1.9rem; color: var(--gold);
  opacity: .5; animation: twinkle 3s ease-in-out infinite;
  transition: opacity .2s;
}
.hidden-star:nth-child(2) { animation-delay: .5s; }
.hidden-star:nth-child(3) { animation-delay: 1s; }
.hidden-star:nth-child(4) { animation-delay: 1.5s; }
.hidden-star:nth-child(5) { animation-delay: 2s; }
.hidden-star:hover { opacity: 1; }
.hidden-star.found { pointer-events: none; animation: collect .8s cubic-bezier(.3, 1.6, .5, 1) forwards; }
@keyframes collect {
  0% { transform: scale(1); opacity: 1; }
  40% { transform: scale(2.4) rotate(120deg); opacity: 1; text-shadow: 0 0 24px var(--gold); }
  100% { transform: scale(0) rotate(300deg); opacity: 0; }
}

/* ---------- SCENE 6 · letter ---------- */
.scene-letter .scene-inner { gap: 32px; }
.paper {
  position: relative; width: 100%;
  background-color: var(--cream); background-image: var(--grain); background-blend-mode: multiply;
  color: var(--ink);
  padding: 44px 34px 40px;
  box-shadow: 0 28px 64px rgba(0, 0, 0, .55);
  display: flex; flex-direction: column; gap: 16px;
}
.paper::before {
  content: ""; position: absolute; top: 0; bottom: 0; left: 18px; width: 2px; background: rgba(185, 112, 122, .35);
}
.paper > * { position: relative; }
.paper-top {
  display: flex; justify-content: space-between; gap: 10px;
  font-family: var(--type); font-size: .7rem; letter-spacing: .2em; text-transform: uppercase; color: var(--pink-d);
  border-bottom: 1px dashed rgba(106, 70, 49, .4); padding-bottom: 10px;
}
.paper p { color: var(--ink); line-height: 1.8; padding-left: 10px; }
.paper .hand-title { padding-left: 10px; }
.paper .sign { font-family: var(--hand); font-size: 1.9rem; color: var(--burg-m); line-height: 1.2; padding-top: 6px; }

.secret-btn { animation: wiggle 3.2s ease-in-out infinite; }
@keyframes wiggle { 0%, 88%, 100% { transform: rotate(0); } 92% { transform: rotate(-3deg); } 96% { transform: rotate(3deg); } }
.secret-btn.seen::after { content: " ✓"; }

/* ---------- SCENE 7 · music ---------- */
.deck-wrap { display: flex; flex-direction: column; align-items: center; gap: 22px; flex: none; }
.deck {
  position: relative;
  width: min(84vw, 360px); aspect-ratio: 1 / 0.92;
  background-color: var(--brown); background-image: var(--grain); background-blend-mode: multiply;
  border-radius: 14px; border: 3px solid #3d2517;
  box-shadow: 0 24px 50px rgba(0, 0, 0, .55), inset 0 0 0 6px rgba(244, 232, 210, .06);
  display: grid; place-items: center;
}
.platter { width: 76%; aspect-ratio: 1; border-radius: 50%; background: #170a0c; padding: 4%; box-shadow: inset 0 0 14px #000; margin-right: 10%; }
.vinyl {
  position: relative; width: 100%; height: 100%; border-radius: 50%; cursor: pointer;
  background:
    conic-gradient(from 20deg, rgba(255, 255, 255, .0), rgba(255, 255, 255, .13) 12%, rgba(255, 255, 255, 0) 25%, rgba(255, 255, 255, .1) 62%, rgba(255, 255, 255, 0) 75%),
    repeating-radial-gradient(circle at 50% 50%, #0d0d0d 0 2px, #1d1d1d 3px 4px);
  box-shadow: 0 0 0 2px #000;
  animation: spin 3.6s linear infinite; animation-play-state: paused;
}
.deck.playing .vinyl { animation-play-state: running; }
@keyframes spin { to { transform: rotate(360deg); } }
.vinyl .label {
  position: absolute; inset: 33%; border-radius: 50%;
  display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center;
  background: radial-gradient(circle at 40% 35%, #e9b9bc, var(--pink-d));
  color: var(--burg); font-family: var(--type); font-size: .6rem; letter-spacing: .12em; line-height: 1.2;
  box-shadow: inset 0 0 0 3px rgba(74, 15, 31, .25);
}
.vinyl .label small { font-size: .5rem; margin-top: 3px; opacity: .8; }
.vinyl .label::after { content: ""; position: absolute; width: 8px; height: 8px; border-radius: 50%; background: var(--burg-d); }

.tonearm { position: absolute; top: 7%; right: 7%; width: 12%; height: 62%; transform-origin: 50% 8%; transform: rotate(-22deg); transition: transform 1s cubic-bezier(.5, 0, .2, 1); }
.deck.playing .tonearm { transform: rotate(10deg); }
.tonearm .arm { position: absolute; top: 0; left: 40%; width: 6px; height: 100%; background: linear-gradient(90deg, #cfc2a8, #8d826d); border-radius: 3px; }
.tonearm .head { position: absolute; bottom: -4px; left: 20%; width: 16px; height: 22px; background: #2b1a14; border-radius: 3px; transform: rotate(-8deg); }
.tonearm::before { content: ""; position: absolute; top: -6px; left: 8%; width: 26px; height: 26px; border-radius: 50%; background: radial-gradient(circle at 35% 30%, #e7dcc4, #8d826d); box-shadow: 0 2px 6px rgba(0, 0, 0, .5); }

.sleeve {
  display: flex; align-items: center; gap: 16px;
  padding: 14px; background: rgba(244, 232, 210, .08); border: 1px solid rgba(244, 232, 210, .25);
}
.sleeve-art {
  flex: none; width: 74px; height: 74px; display: grid; place-items: center;
  background: linear-gradient(145deg, var(--pink-d), var(--burg-m)); color: var(--cream);
  font-family: var(--serif); font-size: 1.7rem; border: 2px solid var(--cream); transform: rotate(-4deg);
}
.sleeve-info { display: flex; flex-direction: column; gap: 3px; }
.sleeve-info strong { font-family: var(--serif); font-weight: 400; font-size: 1.25rem; color: var(--cream); }
.sleeve-info span { font-family: var(--type); font-size: .78rem; letter-spacing: .1em; color: var(--pink); }
.sleeve-info em { font-size: .82rem; color: var(--cream-d); }

.spotify iframe { width: 100%; height: 152px; border: 0; border-radius: 14px; display: block; }
.spotify-fallback {
  display: flex; align-items: center; justify-content: space-between; gap: 14px; flex-wrap: wrap;
  padding: 16px 18px; border-radius: 14px; background: #1d0a10; border: 1px solid rgba(244, 232, 210, .2);
}
.spotify-fallback strong { display: block; font-family: var(--serif); font-weight: 400; font-size: 1.1rem; }
.spotify-fallback span { font-family: var(--type); font-size: .75rem; color: var(--pink); letter-spacing: .1em; }
.spotify-fallback a { text-decoration: none; }

/* ---------- SCENE 8 · final ---------- */
.scene-final::before {
  content: ""; position: absolute; inset: 0; z-index: 0; pointer-events: none;
  background: radial-gradient(800px 560px at 50% 40%, rgba(216, 160, 164, .25), transparent 65%);
}
.scene-final .scene-inner { gap: 22px; }
.scene-final .btn { margin-top: 10px; }

#confetti { position: fixed; inset: 0; width: 100%; height: 100%; z-index: 60; pointer-events: none; }

/* ---------- secret overlay ---------- */
.overlay {
  position: fixed; inset: 0; z-index: 80;
  display: flex; padding: 24px 18px; overflow-y: auto;
  background: rgba(20, 3, 9, .88); backdrop-filter: blur(5px);
  opacity: 0; visibility: hidden; transition: opacity .5s ease, visibility 0s linear .5s;
}
.overlay.open { opacity: 1; visibility: visible; transition: opacity .5s ease, visibility 0s; }
.overlay-inner { margin: auto; width: 100%; max-width: 440px; display: flex; flex-direction: column; align-items: center; gap: 26px; }

.envelope { position: relative; width: min(92vw, 420px); }
.env-back, .env-front, .env-flap { position: absolute; left: 0; width: 100%; }
.env-back { top: 0; height: 150px; background: var(--pink-d); z-index: 0; border-radius: 4px 4px 0 0; }
.env-front {
  top: 0; height: 150px; z-index: 4; background: var(--pink); border-radius: 0 0 4px 4px;
  clip-path: polygon(0 0, 50% 52%, 100% 0, 100% 100%, 0 100%);
}
.env-flap {
  top: 0; height: 100px; z-index: 5; background: #c98a90; transform-origin: top center;
  clip-path: polygon(0 0, 100% 0, 50% 100%);
  transition: transform .9s cubic-bezier(.6, 0, .2, 1), z-index 0s linear .35s;
}
.env-seal {
  position: absolute; z-index: 6; top: 70px; left: 50%; margin-left: -22px;
  width: 44px; height: 44px; border-radius: 50%; display: grid; place-items: center; color: var(--cream);
  background: radial-gradient(circle at 35% 30%, #a42a45, var(--burg));
  box-shadow: 0 3px 8px rgba(0, 0, 0, .5); transition: opacity .3s;
}
.secret-letter {
  position: relative; z-index: 2; margin: 112px 6% 0; padding: 64px 24px 28px;
  background-color: var(--cream); background-image: var(--grain); background-blend-mode: multiply; color: var(--ink);
  display: flex; flex-direction: column; gap: 14px;
  box-shadow: 0 14px 34px rgba(0, 0, 0, .5);
  opacity: 0; transform: translateY(-80px); pointer-events: none;
  transition: opacity .8s ease .5s, transform 1s cubic-bezier(.2, .8, .2, 1) .5s;
}
.secret-letter p { color: var(--ink); font-size: .98rem; line-height: 1.75; }
.secret-letter .sign { font-family: var(--hand); font-size: 1.8rem; color: var(--burg-m); line-height: 1.2; }
.envelope.opened .env-flap { transform: rotateX(180deg); z-index: 1; }
.envelope.opened .env-seal { opacity: 0; }
.envelope.opened .secret-letter { opacity: 1; transform: none; pointer-events: auto; }

/* ---------- small screens ---------- */
@media (max-width: 560px) {
  :root { --nav-h: 70px; }
  .scene { padding-left: 16px; padding-right: 16px; }
  .brand { font-size: .6rem; letter-spacing: .1em; }
  .letter-card { padding: 40px 24px 28px; }
  .paper { padding: 36px 22px 32px; }
  .paper::before { left: 10px; }
  .game-card { padding: 28px 18px; }
  .together-stack { padding: 20px 14px 40px; }
  .filmstrip { width: 104px; right: -2px; }
  .d-heart1 { left: -2px; }
  .dots { gap: 7px; }
  .dot { width: 9px; height: 9px; }
  .bottomnav { gap: 10px; }
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; animation-iteration-count: 1 !important; transition-duration: .01ms !important; }
  .grain { display: none; }
}

</style>
</head>
<body>

  <div class="grain" aria-hidden="true"></div>
  <div id="bgStars" aria-hidden="true"></div>

  <header class="topbar">
    <span class="brand">REALITY CLUB: A LITTLE UNIVERSE FOR YOU</span>
    <span class="counter" id="sceneCounter">01 / 08</span>
  </header>
  <div class="progress" aria-hidden="true"><div class="progress-fill" id="progressFill"></div></div>

  <main id="stage">

    <!-- SCENE 1 · OPENING LETTER -->
    <section class="scene" data-scene="0" id="scene-0" aria-label="Opening letter">
      <div class="scene-inner">
        <article class="letter-card tilt-l reveal">
          <div class="seal" aria-hidden="true">♡</div>
          <p class="kicker">a little note · for fariddayy</p>
          <h1 class="hand-title">Hey, Fariddayy!</h1>
          <p>Okay, so... I made something for you.</p>
          <p>It's basically a tiny corner of the internet, just for your birthday. Nothing too crazy, but there's a little bit of thought, a few memories, and some words I wanted you to have.</p>
          <p>So take your time, click around, and enjoy this little thing.</p>
          <p>Ready? Let's get into it. ♡</p>
          <button class="btn" type="button" data-next>let's go →</button>
        </article>
      </div>
    </section>

    <!-- SCENE 2 · AGE TRANSITION -->
    <section class="scene" data-scene="1" id="scene-1" aria-label="Twenty-six to twenty-seven">
      <div class="scene-inner column">
        <p class="kicker reveal">plot twist</p>
        <h2 class="display reveal">WAIT... YOU'RE 27 ALREADY?</h2>
        <div class="age reveal" id="ageNumber" aria-label="26 turning into 27">
          <span class="digit">2</span><span class="roll-window"><span class="roll-strip"><span>6</span><span>7</span></span></span>
        </div>
        <div class="copy center-text">
          <p class="reveal">Look at you, another year older!</p>
          <p class="reveal">26 was a chapter. 27 is a whole new one.</p>
          <p class="reveal">More chances, more experiences, more lessons, more random plot twists, and hopefully a whole lot of good things.</p>
          <p class="reveal">I hope this year surprises you in the best possible ways.</p>
        </div>
      </div>
    </section>

    <!-- SCENE 3 · SOLO PHOTO -->
    <section class="scene" data-scene="2" id="scene-2" aria-label="Birthday introduction">
      <div class="ghost-num" aria-hidden="true">27</div>
      <div class="sparkles" data-sparkles="16" aria-hidden="true"></div>
      <div class="scene-inner split">
        <figure class="polaroid solo reveal" style="--r:-4deg">
          <span class="tape"></span>
          <div class="photo-wrap">
            <img class="photo" data-embed="solo" src="assets/images/farid-main.jpg" alt="Fariddayy, the birthday boy" loading="eager">
            <div class="placeholder" aria-hidden="true">
              <span class="ph-star">★</span>
              <span class="ph-title">farid-main.jpg</span>
              <span class="ph-sub">solo photo goes here</span>
            </div>
            <span class="date-stamp">CHAPTER 27</span>
          </div>
          <figcaption class="caption">the birthday boy himself ♡</figcaption>
        </figure>
        <div class="copy">
          <p class="kicker reveal">chapter twenty-seven</p>
          <h2 class="display reveal">LOOK WHO'S LEVELING UP.</h2>
          <p class="reveal">27 looks good on you, not gonna lie.</p>
          <p class="reveal">I hope you never forget how much potential you have and how many good things are still waiting for you.</p>
          <p class="reveal">Keep being you, Fariddayy. That's already pretty special.</p>
        </div>
      </div>
    </section>

    <!-- SCENE 4 · TOGETHER PHOTO -->
    <section class="scene scene-together" data-scene="3" id="scene-3" aria-label="A little moment">
      <div class="sparkles" data-sparkles="20" aria-hidden="true"></div>
      <div class="scene-inner split reverse">
        <div class="together-stack reveal">
          <svg class="doodle d-heart1" viewBox="0 0 40 40" aria-hidden="true"><path d="M20 34 C6 24 3 14 10 9 C14 6 19 8 20 13 C21 8 26 6 30 9 C37 14 34 24 20 34Z" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
          <svg class="doodle d-heart2" viewBox="0 0 40 40" aria-hidden="true"><path d="M20 34 C6 24 3 14 10 9 C14 6 19 8 20 13 C21 8 26 6 30 9 C37 14 34 24 20 34Z" fill="currentColor"/></svg>
          <span class="doodle d-star1" aria-hidden="true">✦</span>
          <span class="doodle d-star2" aria-hidden="true">★</span>
          <span class="note n-1" aria-hidden="true">this one ↓</span>
          <span class="note n-2" aria-hidden="true">good company ✦</span>

          <figure class="polaroid together" style="--r:3deg">
            <span class="tape pink"></span>
            <div class="photo-wrap">
              <img class="photo" data-embed="together" alt="A photo of us together" loading="eager">
              <div class="placeholder" aria-hidden="true">
                <span class="ph-star">♡</span>
                <span class="ph-title">us-together.jpg</span>
                <span class="ph-sub">our photo goes here</span>
              </div>
            </div>
            <figcaption class="caption">one of my favorite little memories ♡</figcaption>
          </figure>

          <div class="filmstrip" aria-hidden="true">
            <div class="frame photo-wrap">
              <img class="photo" data-embed="together" alt="" loading="eager">
              <div class="placeholder mini"><span class="ph-star">♡</span></div>
            </div>
            <span class="frame-no">27A</span>
          </div>
        </div>

        <div class="copy">
          <p class="kicker reveal">a small one, but it counts</p>
          <h2 class="display reveal">A LITTLE MOMENT I LIKE.</h2>
          <p class="reveal">Okay, this one's special.</p>
          <p class="reveal">Just a little reminder of one of those moments I'm glad I got to have with you.</p>
          <p class="reveal">It's funny how some memories don't have to be anything extraordinary to mean something. Sometimes it's just being there, laughing about random stuff, or simply enjoying the moment.</p>
          <p class="reveal">And honestly? I'm glad I got to share this one with you.</p>
          <p class="reveal">Here's to more moments like this. No big plans needed, just good company and a little bit of happiness.</p>
        </div>
      </div>
    </section>

    <!-- SCENE 5 · MINI-GAME -->
    <section class="scene scene-game" data-scene="4" id="scene-4" aria-label="Find the five stars">
      <button class="hidden-star" type="button" aria-label="A hidden star" style="--x:9%;--y:22%">★</button>
      <button class="hidden-star" type="button" aria-label="A hidden star" style="--x:91%;--y:27%">★</button>
      <button class="hidden-star" type="button" aria-label="A hidden star" style="--x:14%;--y:76%">★</button>
      <button class="hidden-star" type="button" aria-label="A hidden star" style="--x:87%;--y:72%">★</button>
      <button class="hidden-star" type="button" aria-label="A hidden star" style="--x:52%;--y:79%">★</button>

      <div class="scene-inner column">
        <div class="game-card" id="gameIntro">
          <p class="kicker">tiny side quest</p>
          <h2 class="display">Before I tell you the rest, you gotta do one tiny thing.</h2>
          <p>Find all five stars. They're somewhere around here. No pressure, but I'm rooting for you.</p>
          <div class="star-counter" id="starCounter" aria-live="polite">
            <span class="slot">☆</span><span class="slot">☆</span><span class="slot">☆</span><span class="slot">☆</span><span class="slot">☆</span>
            <span class="count" id="starCount">0 / 5</span>
          </div>
          <p class="hand hint" id="starHint">psst... try the corners ✦</p>
        </div>

        <div class="game-card reward" id="gameReward" aria-live="polite">
          <p class="kicker">side quest complete</p>
          <h2 class="display">AYYY, YOU DID IT!</h2>
          <p>Look at you finding all the stars. Here's a little reward — something I've been wanting to tell you.</p>
          <p class="hand">unlocking the next part... ✦</p>
          <button class="btn" type="button" data-next>open it now →</button>
        </div>
      </div>
    </section>

    <!-- SCENE 6 · MAIN BIRTHDAY LETTER + SECRET -->
    <section class="scene scene-letter" data-scene="5" id="scene-5" aria-label="Birthday letter">
      <div class="scene-inner column">
        <article class="paper">
          <div class="paper-top"><span>for: fariddayy</span><span>chapter 27 ♡</span></div>
          <h2 class="hand-title reveal">Happy 27th birthday, Fariddayy! ♡</h2>

          <p class="reveal">First of all, I hope you're having the loveliest day. You deserve to feel celebrated, appreciated, and surrounded by all the good things today.</p>
          <p class="reveal">Not gonna lie, I'm really glad I got to know you. It's kinda funny how someone can become part of your everyday thoughts without even trying. Sometimes it's just a random conversation, a silly joke, or a little moment that probably seems ordinary to everyone else, but somehow makes my day a little better.</p>
          <p class="reveal">And I think that's something I genuinely appreciate about you.</p>
          <p class="reveal">Now that you're 27, I hope life gives you so many reasons to be excited about what's ahead. I hope the things you've been working so hard for finally start falling into place. I hope you get opportunities that make you grow, meet people who bring out the best in you, and experience things that remind you how beautiful life can be.</p>
          <p class="reveal">But hey, don't forget to enjoy the journey, okay?</p>
          <p class="reveal">You don't have to have everything figured out right now. You don't need to be productive every single day, and you definitely don't need to compare your timeline to anyone else's.</p>
          <p class="reveal">Take your time. Make mistakes. Try new things. Change your mind if you need to. Rest when life gets a little too much.</p>
          <p class="reveal">I hope you always have the courage to chase the things you want, even when they feel a little scary. And when things don't go according to plan, I hope you remember that one bad day doesn't define your whole story.</p>
          <p class="reveal">I wish you good health, a peaceful mind, genuine happiness, exciting opportunities, and the kind of love and friendship that makes life feel a little lighter.</p>
          <p class="reveal">And selfishly? I hope I get to be around for more of your little moments. More random talks, more laughs, more spontaneous plans, and more memories that we'll probably laugh about someday.</p>
          <p class="reveal">I don't know what the next chapters will look like, but I'm genuinely happy that our paths crossed.</p>
          <p class="reveal">Thank you for being you, Fariddayy.</p>
          <p class="reveal">You deserve all the good stuff. Not just on your birthday, but on all the random Tuesdays and ordinary days in between.</p>
          <p class="reveal">Here's to 27. Make it a good one, okay?</p>
          <p class="reveal sign">Happy birthday, favorite person. ♡</p>
        </article>

        <button class="btn secret-btn" type="button" id="secretBtn" aria-haspopup="dialog">psst... one more thing</button>
      </div>
    </section>

    <!-- SCENE 7 · MUSIC -->
    <section class="scene scene-music" data-scene="6" id="scene-6" aria-label="Soundtrack">
      <div class="sparkles" data-sparkles="12" aria-hidden="true"></div>
      <div class="scene-inner split">
        <div class="deck-wrap reveal">
          <div class="deck" id="deck">
            <div class="platter">
              <div class="vinyl" id="vinyl" role="button" tabindex="0" aria-label="Spin the record">
                <div class="label"><span>REALITY<br>CLUB</span><small>A · 08</small></div>
              </div>
            </div>
            <div class="tonearm" aria-hidden="true"><span class="arm"></span><span class="head"></span></div>
          </div>
          <button class="btn ghost small" type="button" id="needleBtn">drop the needle ▶</button>
        </div>

        <div class="copy">
          <p class="kicker reveal">side A · track 08</p>
          <h2 class="display reveal">EVERY LITTLE MOMENT NEEDS A SOUNDTRACK.</h2>
          <p class="reveal">Thought this song would fit the vibe.</p>
          <p class="reveal">A little Reality Club, a little birthday mood, and a little something for you.</p>
          <p class="reveal">Press play, relax, and enjoy your day. You deserve your own little main-character moment.</p>

          <div class="sleeve reveal">
            <div class="sleeve-art" aria-hidden="true"><span>RC</span></div>
            <div class="sleeve-info">
              <strong>Anything You Want</strong>
              <span>Reality Club · 3:56</span>
              <em>from "Reality Club Presents…"</em>
            </div>
          </div>

          <div class="spotify reveal" id="spotifyMount"></div>
        </div>
      </div>
    </section>

    <!-- SCENE 8 · FINAL -->
    <section class="scene scene-final" data-scene="7" id="scene-7" aria-label="Happy birthday">
      <div class="sparkles" data-sparkles="26" aria-hidden="true"></div>
      <div class="scene-inner column center-text">
        <p class="kicker reveal">the end of the tour (not really)</p>
        <h2 class="display huge reveal">HAPPY 27TH, FARIDDAYY!</h2>
        <p class="lead reveal">Another year of you being you. And honestly, the world could use more of that.</p>
        <div class="copy center-text">
          <p class="reveal">Hope this chapter brings you closer to everything you've been wishing for.</p>
          <p class="reveal">Keep growing, keep laughing, keep dreaming big, and don't forget to enjoy the little things along the way.</p>
          <p class="reveal">I'm really glad I met you. Here's to more stories, more memories, and more reasons to smile.</p>
        </div>
        <p class="hand big reveal">you make some ordinary days feel a little less ordinary. ♡</p>
        <button class="btn reveal" type="button" id="replayBtn">REPLAY OUR LITTLE UNIVERSE ↺</button>
      </div>
    </section>

  </main>

  <nav class="bottomnav" aria-label="Scene navigation">
    <button class="nav-btn" type="button" id="prevBtn" aria-label="Previous scene">←</button>
    <div class="dots" id="dots" role="tablist"></div>
    <button class="nav-btn" type="button" id="nextBtn" aria-label="Next scene">→</button>
  </nav>

  <canvas id="confetti" aria-hidden="true"></canvas>

  <!-- SECRET MESSAGE -->
  <div class="overlay" id="secretOverlay" role="dialog" aria-modal="true" aria-label="A secret message" aria-hidden="true">
    <div class="overlay-inner">
      <div class="envelope" id="envelope">
        <div class="env-back"></div>
        <div class="secret-letter">
          <p>Okay, one last thing before you go.</p>
          <p>I just want you to know that I'm happy you're here, and I'm happy that I got the chance to know you.</p>
          <p>I hope we get to make more memories, share more laughs, and have more of those random little moments that somehow turn into good memories.</p>
          <p>No expectations, no big promises. Just a little hope for more good days and good moments ahead.</p>
          <p>So please, take care of yourself, okay?</p>
          <p class="sign">I'm rooting for you, always. ♡</p>
        </div>
        <div class="env-front"></div>
        <div class="env-flap"></div>
        <div class="env-seal" aria-hidden="true">♡</div>
      </div>
      <button class="btn small" type="button" id="secretClose">close ♡</button>
    </div>
  </div>

  <script>
/* ====== FOTO (sudah ditanam di kode). 'solo' dikosongkan: kalau kosong, dipakai file assets/images/farid-main.jpg ====== */
window.EMBEDDED_PHOTOS = {
  together: "data:image/jpeg;base64,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",
  solo: ""
};
</script>
<script>
/* =========================================================
   A LITTLE UNIVERSE FOR FARIDDAYY · script.js
   Scenes (0-indexed):
     0 opening letter   1 age 26→27     2 solo photo     3 together photo
     4 mini-game        5 birthday letter + secret        6 music
     7 final
   ========================================================= */
(() => {
  'use strict';

  /* ---------- config ---------- */
  const CONFIG = {
    // Paste the Spotify track ID for "Anything You Want" (Reality Club) here.
    // Spotify → track → Share → Copy link: open.spotify.com/track/THIS_PART?si=...
    // Leave empty to show a friendly "Play on Spotify" card instead of the embed.
    SPOTIFY_TRACK_ID: '2QB8FwOszur18Ai7t2XnNi',
    SPOTIFY_SEARCH_URL: 'https://open.spotify.com/search/Anything%20You%20Want%20Reality%20Club'
  };

  const GAME_INDEX = 4;
  const STARS_NEEDED = 5;
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  const $ = (sel, root = document) => root.querySelector(sel);
  const $$ = (sel, root = document) => Array.from(root.querySelectorAll(sel));
  const rand = (min, max) => Math.random() * (max - min) + min;
  const pad = n => String(n).padStart(2, '0');

  const scenes = $$('.scene');
  const total = scenes.length;
  const prevBtn = $('#prevBtn');
  const nextBtn = $('#nextBtn');
  const dotsEl = $('#dots');
  const counterEl = $('#sceneCounter');
  const fillEl = $('#progressFill');

  let current = -1;
  let maxReached = 0;
  let gameDone = false;
  let timers = [];
  const foundStars = new Set();

  const later = (fn, ms) => { const id = setTimeout(fn, ms); timers.push(id); return id; };
  const clearTimers = () => { timers.forEach(clearTimeout); timers = []; };

  /* =========================================================
     DECOR: background stars + per-scene sparkles
     ========================================================= */
  (function buildBgStars() {
    const wrap = $('#bgStars');
    const glyphs = ['✦', '★', '·', '✧'];
    for (let i = 0; i < 46; i++) {
      const s = document.createElement('span');
      s.className = 'bg-star';
      s.textContent = glyphs[i % glyphs.length];
      s.style.left = rand(0, 100) + '%';
      s.style.top = rand(0, 100) + '%';
      s.style.fontSize = rand(8, 20) + 'px';
      s.style.setProperty('--d', rand(3, 7) + 's');
      s.style.setProperty('--delay', rand(0, 5) + 's');
      wrap.appendChild(s);
    }
  })();

  $$('[data-sparkles]').forEach(box => {
    const n = parseInt(box.dataset.sparkles, 10) || 10;
    const glyphs = ['✦', '★', '♡', '✧'];
    for (let i = 0; i < n; i++) {
      const s = document.createElement('span');
      s.className = 'sparkle';
      s.textContent = glyphs[i % glyphs.length];
      s.style.left = rand(2, 96) + '%';
      s.style.top = rand(6, 92) + '%';
      s.style.fontSize = rand(10, 24) + 'px';
      s.style.setProperty('--d', rand(5, 10) + 's');
      s.style.setProperty('--delay', rand(0, 6) + 's');
      if (i % 4 === 2) s.style.color = 'var(--pink)';
      box.appendChild(s);
    }
  });

  /* stagger index for reveal animations */
  scenes.forEach(scene => {
    $$('.reveal', scene).forEach((el, i) => el.style.setProperty('--i', Math.min(i, 14)));
  });

  /* =========================================================
     PHOTOS: designed placeholder if an image is missing
     ========================================================= */
  $$('.photo-wrap').forEach(wrap => {
    const img = $('img.photo', wrap);
    if (!img) return;
    const key = img.dataset.embed;
    if (key) {
      const emb = (window.EMBEDDED_PHOTOS || {})[key];
      img.src = emb || (key === 'together' ? 'assets/images/us-together.jpg' : 'assets/images/farid-main.jpg');
    }
    const markMissing = () => wrap.classList.add('missing');
    img.addEventListener('error', markMissing);
    img.addEventListener('load', () => wrap.classList.remove('missing'));
    if (img.complete && img.naturalWidth === 0) markMissing();
  });

  /* =========================================================
     NAVIGATION
     ========================================================= */
  const dots = scenes.map((_, i) => {
    const b = document.createElement('button');
    b.type = 'button';
    b.className = 'dot';
    b.setAttribute('aria-label', `Go to scene ${i + 1}`);
    b.addEventListener('click', () => {
      if (i <= maxReached && !(i > GAME_INDEX && !gameDone)) goTo(i);
    });
    dotsEl.appendChild(b);
    return b;
  });

  function updateUI() {
    counterEl.textContent = `${pad(current + 1)} / ${pad(total)}`;
    fillEl.style.width = (total > 1 ? (current / (total - 1)) * 100 : 100) + '%';

    dots.forEach((d, i) => {
      const locked = i > maxReached || (i > GAME_INDEX && !gameDone);
      d.classList.toggle('active', i === current);
      d.classList.toggle('visited', i < current && !locked);
      d.classList.toggle('locked', locked && i !== current);
      if (i === current) d.setAttribute('aria-current', 'step'); else d.removeAttribute('aria-current');
    });

    prevBtn.disabled = current <= 0;
    const last = current === total - 1;
    nextBtn.classList.toggle('hidden', last);
    const blocked = current === GAME_INDEX && !gameDone;
    nextBtn.disabled = blocked;
    nextBtn.title = blocked ? 'Find all five stars first ✦' : '';
  }

  function nudgeNext() {
    nextBtn.classList.remove('nudge');
    void nextBtn.offsetWidth;
    nextBtn.classList.add('nudge');
    const hint = $('#starHint');
    if (hint) hint.classList.add('show');
  }

  function goTo(n) {
    if (n < 0 || n >= total || n === current) return;
    if (n > GAME_INDEX && !gameDone) {
      n = GAME_INDEX;
      if (n === current) { nudgeNext(); return; }
    }
    const old = current;
    current = n;
    maxReached = Math.max(maxReached, n);

    if (old >= 0) {
      scenes[old].classList.remove('active');
      onLeave(old);
    }
    const scene = scenes[n];
    scene.scrollTop = 0;
    scene.classList.add('active');
    onEnter(n);
    updateUI();
  }

  const next = () => goTo(current + 1);
  const prev = () => goTo(current - 1);

  prevBtn.addEventListener('click', prev);
  nextBtn.addEventListener('click', next);
  $$('[data-next]').forEach(b => b.addEventListener('click', next));

  document.addEventListener('keydown', e => {
    if (e.key === 'Escape' && overlay.classList.contains('open')) { closeSecret(); return; }
    if (overlay.classList.contains('open')) return;
    if (e.key === 'ArrowRight') { if (!nextBtn.disabled && current < total - 1) next(); else if (current === GAME_INDEX && !gameDone) nudgeNext(); }
    if (e.key === 'ArrowLeft') prev();
  });

  /* =========================================================
     SCENE HOOKS
     ========================================================= */
  const ageEl = $('#ageNumber');

  function onEnter(i) {
    if (i === 1) {
      ageEl.classList.remove('rolled');
      later(() => ageEl.classList.add('rolled'), 1300);
      later(() => burst(70, innerWidth / 2, innerHeight * 0.38), 2700);
    }
    if (i === 3) { /* together scene: floating handled in CSS */ }
    if (i === GAME_INDEX) {
      if (!gameDone) {
        later(() => { const h = $('#starHint'); if (h && !gameDone) h.classList.add('show'); }, 12000);
      } else {
        scenes[GAME_INDEX].classList.add('won');
      }
    }
    if (i === 7) {
      emitting = true;
      burst(160, innerWidth * 0.5, innerHeight * 0.3);
      later(() => burst(110, innerWidth * 0.2, innerHeight * 0.45), 500);
      later(() => burst(110, innerWidth * 0.8, innerHeight * 0.45), 900);
      startConfetti();
    }
  }

  function onLeave(i) {
    clearTimers();
    if (i === 1) ageEl.classList.remove('rolled');
    if (i === 6) stopVinyl();
    if (i === 7) { emitting = false; }
    if (i === GAME_INDEX) { const h = $('#starHint'); if (h) h.classList.remove('show'); }
  }

  /* =========================================================
     MINI-GAME: find five stars
     ========================================================= */
  const gameScene = scenes[GAME_INDEX];
  const hiddenStars = $$('.hidden-star');
  const slots = $$('#starCounter .slot');
  const countEl = $('#starCount');

  function renderStarCounter() {
    slots.forEach((s, i) => {
      const on = i < foundStars.size;
      s.textContent = on ? '★' : '☆';
      s.classList.toggle('on', on);
    });
    countEl.textContent = `${foundStars.size} / ${STARS_NEEDED}`;
  }

  hiddenStars.forEach((star, idx) => {
    star.addEventListener('click', () => {
      if (foundStars.has(idx)) return;
      foundStars.add(idx);
      star.classList.add('found');
      renderStarCounter();
      if (foundStars.size >= STARS_NEEDED) completeGame();
    });
  });

  function completeGame() {
    gameDone = true;
    gameScene.classList.add('won');
    burst(150, innerWidth / 2, innerHeight * 0.4);
    updateUI();
    // unlock the next section automatically
    later(() => { if (current === GAME_INDEX) goTo(GAME_INDEX + 1); }, 4200);
  }

  /* =========================================================
     SECRET ENVELOPE
     ========================================================= */
  const overlay = $('#secretOverlay');
  const envelope = $('#envelope');
  const secretBtn = $('#secretBtn');
  const secretClose = $('#secretClose');
  let secretTimer = null;

  function openSecret() {
    overlay.classList.add('open');
    overlay.setAttribute('aria-hidden', 'false');
    envelope.classList.remove('opened');
    clearTimeout(secretTimer);
    secretTimer = setTimeout(() => envelope.classList.add('opened'), 550);
    secretBtn.classList.add('seen');
    secretClose.focus({ preventScroll: true });
  }

  function closeSecret(silent) {
    clearTimeout(secretTimer);
    overlay.classList.remove('open');
    overlay.setAttribute('aria-hidden', 'true');
    if (!silent) secretBtn.focus({ preventScroll: true });
    setTimeout(() => envelope.classList.remove('opened'), 500);
  }

  secretBtn.addEventListener('click', openSecret);
  secretClose.addEventListener('click', () => closeSecret());
  overlay.addEventListener('click', e => { if (e.target === overlay || e.target.classList.contains('overlay-inner')) closeSecret(); });

  /* =========================================================
     MUSIC: vinyl + Spotify embed
     ========================================================= */
  const deck = $('#deck');
  const vinyl = $('#vinyl');
  const needleBtn = $('#needleBtn');

  function setVinyl(on) {
    deck.classList.toggle('playing', on);
    needleBtn.textContent = on ? 'lift the needle ❚❚' : 'drop the needle ▶';
  }
  function stopVinyl() { setVinyl(false); }
  const toggleVinyl = () => setVinyl(!deck.classList.contains('playing'));

  needleBtn.addEventListener('click', toggleVinyl);
  vinyl.addEventListener('click', toggleVinyl);
  vinyl.addEventListener('keydown', e => { if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); toggleVinyl(); } });

  (function mountSpotify() {
    const mount = $('#spotifyMount');
    const id = (CONFIG.SPOTIFY_TRACK_ID || '').trim();
    if (id) {
      const f = document.createElement('iframe');
      f.src = `https://open.spotify.com/embed/track/${encodeURIComponent(id)}?utm_source=generator&theme=0`;
      f.title = 'Anything You Want — Reality Club (Spotify)';
      f.allow = 'autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture';
      f.loading = 'lazy';
      mount.appendChild(f);
      // keep the record in sync with the player as best we can: spin when the player is clicked
      mount.addEventListener('click', () => setVinyl(true));
    } else {
      mount.innerHTML =
        '<div class="spotify-fallback">' +
          '<div><strong>Anything You Want</strong><span>Reality Club · Spotify</span></div>' +
          `<a class="btn small" href="${CONFIG.SPOTIFY_SEARCH_URL}" target="_blank" rel="noopener">play on spotify ↗</a>` +
        '</div>';
      $('a', mount).addEventListener('click', () => setVinyl(true));
      console.info('[birthday site] Add the Spotify track ID in script.js (CONFIG.SPOTIFY_TRACK_ID) to enable the inline player.');
    }
  })();

  /* =========================================================
     CONFETTI
     ========================================================= */
  const cv = $('#confetti');
  const ctx = cv.getContext('2d');
  const colors = ['#f4e8d2', '#d8a0a4', '#e9c47c', '#b9707a', '#6e1b30', '#f0a04b'];
  let parts = [];
  let raf = null;
  let emitting = false;

  function resizeCanvas() {
    const dpr = Math.min(window.devicePixelRatio || 1, 2);
    cv.width = innerWidth * dpr;
    cv.height = innerHeight * dpr;
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
  }
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);

  function burst(n, x, y) {
    if (reduceMotion) n = Math.floor(n / 6);
    for (let i = 0; i < n; i++) {
      parts.push({
        x, y,
        vx: rand(-7, 7), vy: rand(-13, -3),
        g: rand(.2, .32), drag: .992,
        w: rand(6, 12), h: rand(4, 8),
        rot: rand(0, Math.PI * 2), vr: rand(-.25, .25),
        color: colors[(Math.random() * colors.length) | 0],
        shape: ['rect', 'circle', 'star'][(Math.random() * 3) | 0]
      });
    }
    startConfetti();
  }

  function startConfetti() {
    if (raf == null) raf = requestAnimationFrame(tick);
  }

  function tick() {
    ctx.clearRect(0, 0, innerWidth, innerHeight);

    if (emitting && !reduceMotion && parts.length < 220 && Math.random() < .5) {
      parts.push({
        x: rand(0, innerWidth), y: -12,
        vx: rand(-1, 1), vy: rand(1.5, 3.5),
        g: .02, drag: 1,
        w: rand(6, 11), h: rand(4, 8),
        rot: rand(0, Math.PI * 2), vr: rand(-.1, .1),
        color: colors[(Math.random() * colors.length) | 0],
        shape: ['rect', 'circle', 'star'][(Math.random() * 3) | 0]
      });
    }

    parts = parts.filter(p => p.y < innerHeight + 30);
    for (const p of parts) {
      p.vx *= p.drag; p.vy = p.vy * p.drag + p.g;
      p.x += p.vx; p.y += p.vy; p.rot += p.vr;
      ctx.save();
      ctx.translate(p.x, p.y);
      ctx.rotate(p.rot);
      ctx.fillStyle = p.color;
      if (p.shape === 'rect') ctx.fillRect(-p.w / 2, -p.h / 2, p.w, p.h);
      else if (p.shape === 'circle') { ctx.beginPath(); ctx.arc(0, 0, p.h / 1.6, 0, Math.PI * 2); ctx.fill(); }
      else { ctx.font = `${p.w * 1.6}px serif`; ctx.textAlign = 'center'; ctx.textBaseline = 'middle'; ctx.fillText('★', 0, 0); }
      ctx.restore();
    }

    if (parts.length || emitting) raf = requestAnimationFrame(tick);
    else { raf = null; ctx.clearRect(0, 0, innerWidth, innerHeight); }
  }

  /* =========================================================
     REPLAY: reset every scene + game state
     ========================================================= */
  $('#replayBtn').addEventListener('click', replay);

  function replay() {
    clearTimers();
    closeSecret(true);
    secretBtn.classList.remove('seen');

    // game
    foundStars.clear();
    gameDone = false;
    hiddenStars.forEach(s => s.classList.remove('found'));
    gameScene.classList.remove('won');
    const hint = $('#starHint'); if (hint) hint.classList.remove('show');
    renderStarCounter();

    // music + age + confetti
    stopVinyl();
    ageEl.classList.remove('rolled');
    emitting = false;
    parts = [];

    // scenes
    const old = current;
    if (old >= 0) scenes[old].classList.remove('active');
    scenes.forEach(s => { s.scrollTop = 0; });
    current = -1;
    maxReached = 0;
    goTo(0);
  }

  /* =========================================================
     INIT
     ========================================================= */
  renderStarCounter();
  goTo(0);
})();

</script>
</body>
</html>
