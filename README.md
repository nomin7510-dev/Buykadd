<!doctype html>
<html lang="mn">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Happy 17th Birthday, Buyka! 💗</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@300;600;800&display=swap" rel="stylesheet">

<style>
:root{
  --fg:#5b3a4b;
  --accent-1:#ff9cc1;
  --accent-2:#cdb4ff;
  --glass-bg: rgba(255,255,255,0.20);
  --glass-border: rgba(255,255,255,0.35);
  --card-radius:28px;
  --ease: cubic-bezier(.2,.9,.25,1);
}

*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  margin:0;
  font-family:"Montserrat",system-ui,-apple-system,Segoe UI,Roboto,Arial;
  color:var(--fg);
  background: linear-gradient(145deg,#fff5fb 0%, #fff0f7 50%, #fffaf8 100%);
  -webkit-font-smoothing:antialiased;
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:24px;
}

/* common card */
.card{
  width:100%;
  max-width:820px;
  border-radius:var(--card-radius);
  background: linear-gradient(180deg, rgba(255,255,255,0.18), rgba(255,250,255,0.08));
  border:1px solid var(--glass-border);
  box-shadow: 0 18px 50px rgba(107,59,91,0.06);
  padding:32px;
  backdrop-filter: blur(12px) saturate(120%);
  -webkit-backdrop-filter: blur(12px) saturate(120%);
  position:relative;
  overflow:hidden;
}

/* sheen */
.card::before{
  content:"";
  position:absolute; left:-40%; top:-40%;
  width:60%; height:200%;
  background: linear-gradient(120deg, rgba(255,255,255,0.26), rgba(255,255,255,0.04), rgba(255,255,255,0));
  transform: rotate(-25deg);
  pointer-events:none;
  mix-blend-mode: overlay;
  animation: sheen 6s linear infinite;
  opacity:.95;
}
@keyframes sheen{ 0%{transform:translateX(-100%) rotate(-25deg)} 100%{transform:translateX(250%) rotate(-25deg)} }

/* Intro fullscreen */
#intro{
  width:100%;
  max-width:980px;
  text-align:center;
  padding:48px;
}
.title{
  font-family:"Great Vibes", cursive;
  font-size:clamp(40px,8vw,86px);
  color:var(--accent-1);
  line-height:0.9;
  text-shadow: 4px 6px rgba(255,220,235,0.5);
}
.subtitle{
  color:#b86a99;
  margin-top:6px;
  font-weight:700;
  letter-spacing:2px;
}
.intro-decor{ margin:18px 0 22px; height:120px; position:relative; }

/* floating hearts */
.heart{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
  font-size:26px;
  opacity:0;
  animation: heartPop .9s ease forwards;
}
@keyframes heartPop{
  0%{ transform: translateY(20px) scale(.8); opacity:0 }
  60%{ transform: translateY(-6px) scale(1.06); opacity:1 }
  100%{ transform: translateY(0) scale(1); opacity:1 }
}

/* feminine flourishes */
.flower-row{ display:flex; gap:10px; justify-content:center; margin-top:8px; }
.flower-dot{ width:10px; height:10px; border-radius:50%; background:var(--accent-2); box-shadow: 0 6px 14px rgba(197,91,143,0.08); }

/* buttons */
.controls{ margin-top:22px; display:flex; justify-content:center; gap:12px; align-items:center; }
.btn{
  background: linear-gradient(90deg,var(--accent-1),var(--accent-2));
  color:#fff; border:0; border-radius:999px; padding:12px 20px; font-weight:800; cursor:pointer;
  box-shadow: 0 10px 30px rgba(201,114,160,0.12);
}
#audioToggle{ background:transparent; border:1px solid rgba(255,220,235,0.6); color:#d4548c; padding:8px 10px; border-radius:10px; }

/* Sections hidden by default */
.section { display:none; width:100%; max-width:980px; }
.section.active{ display:block; }

/* letter */
.letter{
  margin-top:12px;
  background: linear-gradient(180deg, rgba(255,247,251,0.75), rgba(255,247,251,0.5));
  border:1px solid rgba(255,218,234,0.6);
  padding:20px;
  border-radius:16px;
  font-size:16px;
  line-height:1.9;
  color:#5d3a4b;
  box-shadow: 0 8px 22px rgba(107,59,91,0.04);
}

/* gallery */
.gallery{
  margin-top:18px;
  display:flex;
  gap:14px;
  justify-content:center;
  align-items:center;
  flex-wrap:wrap;
}
.gallery img{
  width:calc(50% - 14px);
  max-width:420px;
  border-radius:14px;
  box-shadow: 0 10px 30px rgba(107,59,91,0.06);
}

/* final screen */
#finalScreen{ text-align:center; padding:36px; position:relative; }
.final-title{ font-family:"Great Vibes", cursive; font-size:clamp(36px,7vw,72px); color:var(--accent-1); margin-bottom:8px; }
.small{ color:#8b4a66; }

/* fireworks canvas covers */
#fireworksCanvas{
  position:fixed; inset:0; pointer-events:none; z-index:9999; display:none;
}

/* responsive */
@media (max-width:720px){
  .title{ font-size:44px }
  .gallery img{ width:100% }
  .card{ padding:20px }
}

/* accessibility: prefers reduced motion */
@media (prefers-reduced-motion: reduce){
  *{ animation-duration: .001ms !important; animation-iteration-count: 1 !important; transition-duration: .001ms !important; }
  .card::before{ display:none; }
}
</style>
</head>
<body>

<!-- AUDIO -->
<audio id="birthdayMusic" loop preload="auto">
  <source src="birthday.mp3" type="audio/mpeg">
</audio>

<!-- fireworks canvas -->
<canvas id="fireworksCanvas"></canvas>

<!-- Main card container -->
<div class="card" role="main" aria-live="polite">

  <!-- INTRO (shows immediately) -->
  <div id="intro" class="section active" aria-label="Welcome">
    <div class="title">Төрсөн өдрийн мэнд, Buyka! 💗</div>
    <div class="subtitle">Хөөрхөн, Бяцхан, Сэтгэлтэй охинд</div>

    <div class="intro-decor" aria-hidden="true">
      <span class="heart" style="left:10%; animation-delay:.05s">💗</span>
      <span class="heart" style="left:28%; animation-delay:.12s">🌸</span>
      <span class="heart" style="left:46%; animation-delay:.20s">✨</span>
      <span class="heart" style="left:64%; animation-delay:.28s">🎀</span>
      <span class="heart" style="left:82%; animation-delay:.35s">💕</span>
    </div>

    <div class="flower-row" aria-hidden="true">
      <div class="flower-dot" style="background:#ffd6e8"></div>
      <div class="flower-dot" style="background:#cdb4ff"></div>
      <div class="flower-dot" style="background:#ffb7da"></div>
    </div>

    <div class="controls">
      <button id="startBtn" class="btn" aria-label="Start surprise">✨ Нээх</button>
      <button id="audioToggle" title="Play / Pause music" aria-pressed="false">🎵</button>
    </div>
  </div>

  <!-- LETTER SCREEN -->
  <div id="letterScreen" class="section" aria-label="Letter">
    <div style="display:flex; align-items:center; justify-content:space-between; gap:12px; flex-wrap:wrap">
      <div>
        <div style="font-weight:800; color:#d46f9a; letter-spacing:1px">💌 A LETTER FOR MY BESTIE</div>
        <div style="margin-top:8px; font-weight:700; color:#c35b8a">10.13 · 17 & BLOOMING 🌷</div>
      </div>
      <div style="display:flex; gap:10px; align-items:center">
        <div style="font-weight:800; color:#b86a99">Буяндэлгэрт Эрхэсээс</div>
      </div>
    </div>

    <div class="letter" id="letterContent" tabindex="0" aria-label="Letter content" style="margin-top:18px; display:none;">
      <h3 style="font-family:'Great Vibes', cursive; text-align:center; color:#d4548c; margin-top:0">
        Эрхэм хүндэт үзэгслэн Гоо Найз минь ээ 💗
      </h3>

      Эрхэм хүндэт үзэгслэн Гоо Найз минь ээ,

      Бие биенийгээ мэддэг болоод, таньдаг болоод 12 жилийн хугацаа өнгөрчээ. Хэрвээ 80 наслах юм бол амьдралынхаа 15% ийг хамтдаа өнгрөөжээ. Цаашдаа ч 20,30 давраад 70,80 жил хөгшин буурал болтлоо андууд байя.

      Хэдий өдөр болгон хамт нэг ангид байдаггүй ч хөндийрөлгүй найз минь байдагт баярлалаа. Холбогч гүүргүй үргэлжилдэг цөөхөн харилцааны минь нэг шүү.

      Гэхдээ 진짜 тэр өдөр 너무 너무 баярласаан.

      Бид 3 ийг гээд зориод бэлэг өгдөг найзтай байна гэдэг надад үнэхээр гоё байсаан тэр үед бүр үнэхээр баярласан шүү уйлах аа шахсан.

      Одоо бичиж байхдаа баярлаад нулимс урсаж байна ㅋㅋㅋ.

      Бид нарын биесийн зай холдож ирээдүйд бүр илүү холдох ч хэдүүлээ сэтгэлээрээ дандаа цуг байцгаая. Яаанаа баахан алдаатай бичээд онигоо болох вий дээ хха.

      Заа ингээд хөөрхөн найздаа төрсөн өдрийн баярын мэнд хүргэе найздаа хайртай шүү.

      <div class="signature" style="margin-top:12px; font-weight:800">Ному ному саранхэёа, чингүяа 🫶🏻❤️❤️❤️</div>
    </div>

    <div style="margin-top:18px; display:flex; gap:12px; justify-content:center">
      <button id="readBtn" class="btn" style="display:inline-block">💌 Захиа унших</button>
      <button id="showPhotosBtn" class="btn" style="display:none">📸 </button>
    </div>
  </div>

  <!-- MEMORIES -->
  <div id="memories" class="section" aria-label="Memories">
    <div style="display:flex; justify-content:space-between; align-items:center; gap:12px; flex-wrap:wrap">
      <div>
        <div style="font-weight:800; color:#d46f9a">OUR LITTLE MEMORIES ♡</div>
        <div style="margin-top:6px; font-weight:700; color:#c35b8a">Бидний дурсамж 💞</div>
      </div>
      <div>
        <button id="finishBtn" class="btn">🎉 Дуусгах</button>
      </div>
    </div>

    <div class="gallery" style="margin-top:18px; justify-content:center">
      <img id="photoA" src="https://mp3tourl.com/images/1791827146817-2ee52077-78f1-4bee-a5ee-034924f00520.jpeg" alt="photo A" loading="lazy">
      <img id="photoB" src="https://mp3tourl.com/images/1791827748819-5b422512-c0d1-4df7-9127-f54bc55de52d.jpeg" alt="photo B" loading="lazy">
    </div>
  </div>

  <!-- FINAL -->
  <div id="final" class="section" aria-label="Final" style="text-align:center; padding:28px;">
    <div class="final-title">Төрсөн өдрийн мэнд хүргэе, Buyka! 🎉</div>
    <div class="small">Найздаа хамгийн сайн сайхан бүхнийг хүсэе</div>
    <div style="margin-top:18px">
      <button id="replayBtn" class="btn">🎈 дахин</button>
    </div>
  </div>

</div>

<script>
/* Simple sequence controller */
const intro = document.getElementById('intro');
const startBtn = document.getElementById('startBtn');
const audioToggle = document.getElementById('audioToggle');
const music = document.getElementById('birthdayMusic');

const letterScreen = document.getElementById('letterScreen');
const readBtn = document.getElementById('readBtn');
const letterContent = document.getElementById('letterContent');
const showPhotosBtn = document.getElementById('showPhotosBtn');

const memories = document.getElementById('memories');
const finishBtn = document.getElementById('finishBtn');

const final = document.getElementById('final');
const replayBtn = document.getElementById('replayBtn');

const fireworksCanvas = document.getElementById('fireworksCanvas');
let musicPlaying = false;

/* play/pause music */
function toggleMusic(){
  if(!music) return;
  if(musicPlaying){
    music.pause();
    musicPlaying = false;
    audioToggle.textContent = '🎵';
    audioToggle.setAttribute('aria-pressed','false');
  } else {
    music.play().then(()=> {
      musicPlaying = true;
      audioToggle.textContent = '🔊';
      audioToggle.setAttribute('aria-pressed','true');
    }).catch(()=> {
      // some browsers block autoplay, still flip UI for manual control
      musicPlaying = true;
      audioToggle.textContent = '🔊';
      audioToggle.setAttribute('aria-pressed','true');
    });
  }
}
audioToggle.addEventListener('click', toggleMusic);

/* helper to show only one section */
function showOnly(sectionEl){
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  sectionEl.classList.add('active');
  // ensure page scroll to top (card is centered)
  window.scrollTo({top:0, behavior:'smooth'});
}

/* small entrance bloom animation for intro hearts */
function animateIntroHearts(){
  document.querySelectorAll('.heart').forEach((h,i)=>{
    h.style.animationDelay = (i*0.08)+'s';
    // set opacity after small delay
    setTimeout(()=> h.style.opacity = 1, i*120);
  });
}

/* start -> reveal letter screen */
function startSequence(){
  // try to play music (user gesture)
  try { music.play(); musicPlaying = true; audioToggle.textContent = '🔊'; audioToggle.setAttribute('aria-pressed','true'); }
  catch(e){ /* ignore */ }

  showOnly(letterScreen);
  // show typed sender then reveal read button
  playSender();
}

/* typed sender */
function playSender(){
  const senderBox = document.getElementById('sender');
  if(!senderBox) return;
  const text = "Буяндэлгэрт Эрхэсээс 💌";
  senderBox.textContent = "";
  let i = 0;
  const t = setInterval(()=>{
    senderBox.textContent += text[i++] || "";
    if(i > text.length){ clearInterval(t);
      setTimeout(()=> {
        readBtn.style.display = 'inline-block';
        readBtn.focus();
      }, 600);
    }
  }, 50);
}

/* read letter -> show letter content and reveal photos button */
function onReadLetter(){
  letterContent.style.display = 'block';
  // animate reveal by briefly adding class to children (simple)
  letterContent.querySelectorAll('p, h3, .signature').forEach((el,i) => {
    el.style.opacity = 0;
    setTimeout(()=> el.style.transition = 'opacity .45s ease', 20);
    setTimeout(()=> el.style.opacity = 1, 120 + i*120);
  });
  // reveal photos button after small delay
  setTimeout(()=> {
    showPhotosBtn.style.display = 'inline-block';
    showPhotosBtn.focus();
  }, 700);
}

/* show photos */
function onShowPhotos(){
  showOnly(memories);
  // small confetti
  confetti(20);
}

/* finish -> final and fireworks */
function onFinish(){
  showOnly(final);
  // ensure music playing
  if(music && !musicPlaying) { music.play().catch(()=>{}); musicPlaying = true; audioToggle.textContent='🔊'; }
  startFireworks();
}

/* replay: go back to intro */
function onReplay(){
  // stop fireworks
  stopFireworks();
  // pause music
  if(music){ music.pause(); music.currentTime = 0; musicPlaying = false; audioToggle.textContent='🎵'; audioToggle.setAttribute('aria-pressed','false'); }
  // hide letter and photos UI
  letterContent.style.display = 'none';
  readBtn.style.display = 'none';
  showPhotosBtn.style.display = 'none';
  // go back
  showOnly(intro);
  animateIntroHearts();
}

/* confetti hearts simple */
function confetti(count=18){
  const symbols = ["💗","✨","🌸","💕","🎀"];
  for(let i=0;i<count;i++){
    const s = document.createElement('span');
    s.textContent = symbols[Math.floor(Math.random()*symbols.length)];
    s.style.position = 'fixed';
    s.style.left = (Math.random()*100)+'vw';
    s.style.top = '-20px';
    s.style.zIndex = 10000;
    s.style.fontSize = (12 + Math.random()*22)+'px';
    s.style.pointerEvents = 'none';
    s.style.transition = 'transform 4.5s linear, opacity 4.5s linear';
    document.body.appendChild(s);
    requestAnimationFrame(()=> {
      s.style.transform = `translateY(${110 + Math.random()*20}vh) rotate(${Math.random()*720}deg)`;
      s.style.opacity = '0';
    });
    setTimeout(()=> s.remove(), 4800);
  }
}

/* FIREWORKS (simple canvas particle fireworks) */
let fwCtx, fwW, fwH, fwRAF, fwParticles = [], fwExplosions = [], fwRunning=false;
function setupFireworks(){
  if(!fireworksCanvas) return;
  fireworksCanvas.style.display = 'block';
  fwCtx = fireworksCanvas.getContext('2d');
  function resize(){ fwW = fireworksCanvas.width = innerWidth; fwH = fireworksCanvas.height = innerHeight; }
  resize();
  addEventListener('resize', resize);
}
function startFireworks(){
  if(fwRunning) return;
  setupFireworks();
  fwRunning = true;
  // create periodic explosions
  fwRAF = requestAnimationFrame(fwLoop);
  fwExplosions.push(createExplosion());
  // add more periodically
  fwInterval = setInterval(()=> fwExplosions.push(createExplosion()), 600);
}
function stopFireworks(){
  fwRunning = false;
  cancelAnimationFrame(fwRAF);
  clearInterval(typeof fwInterval !== 'undefined' ? fwInterval : 0);
  if(fireworksCanvas) fireworksCanvas.style.display = 'none';
  fwParticles = []; fwExplosions = [];
}
function createExplosion(){
  // random position near top-middle
  const x = Math.random()*fwW*0.8 + fwW*0.1;
  const y = Math.random()*fwH*0.45 + fwH*0.05;
  const hue = Math.random()*360;
  const count = 18 + Math.floor(Math.random()*30);
  const particles = [];
  for(let i=0;i<count;i++){
    const angle = Math.random()*Math.PI*2;
    const speed = 2 + Math.random()*6;
    particles.push({
      x,y,
      vx: Math.cos(angle)*speed,
      vy: Math.sin(angle)*speed,
      life: 60 + Math.random()*40,
      age:0,
      color:`hsl(${hue + Math.random()*40-20}deg, 85%, 65%)`,
      size: 2 + Math.random()*3
    });
  }
  return {particles};
}
function fwLoop(){
  fwCtx.clearRect(0,0,fwW,fwH);
  // spawn explosions
  if(fwExplosions.length){
    fwExplosions.forEach((expl, idx) => {
      expl.particles.forEach(p => fwParticles.push(Object.assign({}, p)));
    });
    fwExplosions = [];
  }
  // update particles
  for(let i = fwParticles.length-1; i>=0; i--){
    const p = fwParticles[i];
    p.vy += 0.06; // gravity
    p.vx *= 0.995;
    p.vy *= 0.995;
    p.x += p.vx;
    p.y += p.vy;
    p.age++;
    const alpha = 1 - (p.age / p.life);
    fwCtx.beginPath();
    fwCtx.fillStyle = p.color;
    fwCtx.globalAlpha = Math.max(0, alpha);
    fwCtx.arc(p.x, p.y, p.size, 0, Math.PI*2);
    fwCtx.fill();
    fwCtx.globalAlpha = 1;
    if(p.age >= p.life) fwParticles.splice(i,1);
  }
  if(fwRunning) fwRAF = requestAnimationFrame(fwLoop);
}

/* wiring */
startBtn.addEventListener('click', startSequence);
readBtn.addEventListener('click', onReadLetter);
showPhotosBtn.addEventListener('click', onShowPhotos);
finishBtn.addEventListener('click', onFinish);
replayBtn.addEventListener('click', onReplay);

/* initial intro anim */
document.addEventListener('DOMContentLoaded', ()=> {
  animateIntroHearts();
  // reveal start button focusable
  startBtn.focus();
});
</script>

</body>
