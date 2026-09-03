<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Mehreen Riaz — Frontend Web </title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,500;0,9..144,600;1,9..144,500&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0e1a16;
    --paper:#eef2ea;
    --paper-dim:#c9d2c2;
    --spring:#8BC34A;
    --summer:#FFB300;
    --autumn:#C1560C;
    --winter:#4FC3F7;
    --accent: var(--spring);
    --sky-a:#bfe3f0;
    --sky-b:#eaf7d9;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--ink);
    color:var(--paper);
    font-family:'Inter', sans-serif;
    overflow-x:hidden;
  }
  h1,h2,h3,.display{
    font-family:'Fraunces', serif;
    font-weight:500;
    letter-spacing:-0.01em;
  }
  a{color:inherit; text-decoration:none;}

  /* ---------- HERO ---------- */
  .hero{
    position:relative;
    height:100svh;
    min-height:640px;
    width:100%;
    overflow:hidden;
    background:linear-gradient(180deg, var(--sky-a), var(--sky-b));
    transition:background 2.2s ease;
  }
  #scene-canvas{
    position:absolute; inset:0;
    width:100%; height:100%;
    display:block;
  }
  .hero-nav{
    position:absolute; top:0; left:0; right:0;
    display:flex; align-items:center; justify-content:space-between;
    padding:26px 6vw;
    z-index:5;
    font-size:13px;
    letter-spacing:0.08em;
    text-transform:uppercase;
    color:var(--ink);
    mix-blend-mode:normal;
  }
  .hero-nav .mark{
    font-family:'Fraunces', serif;
    font-size:18px;
    font-weight:600;
    letter-spacing:0;
    text-transform:none;
  }
  .hero-nav .links{display:flex; gap:22px;}
  .hero-nav .links a{opacity:0.75; transition:opacity .2s;}
  .hero-nav .links a:hover{opacity:1;}

  .hero-copy{
    position:absolute;
    left:6vw; bottom:14vh;
    z-index:5;
    max-width:560px;
    color:var(--ink);
  }
  .hero-eyebrow{
    font-size:12px;
    letter-spacing:0.18em;
    text-transform:uppercase;
    opacity:0.7;
    margin-bottom:14px;
    display:flex; align-items:center; gap:10px;
  }
  .hero-eyebrow::before{
    content:"";
    width:26px; height:1px;
    background:currentColor;
    display:inline-block;
  }
  .hero-copy h1{
    font-size:clamp(2.4rem, 6vw, 4.4rem);
    line-height:1.02;
  }
  .hero-copy .season-word{
    font-style:italic;
    transition:color .8s ease;
  }
  .hero-copy p{
    margin-top:18px;
    font-size:16px;
    max-width:420px;
    opacity:0.82;
    line-height:1.55;
  }

  .season-switch{
    position:absolute;
    right:6vw; bottom:14vh;
    z-index:6;
    display:flex; flex-direction:column; gap:10px;
  }
  .season-btn{
    width:52px; height:52px;
    border-radius:50%;
    border:1px solid rgba(14,26,22,0.25);
    background:rgba(255,255,255,0.35);
    backdrop-filter:blur(6px);
    display:flex; align-items:center; justify-content:center;
    font-size:20px;
    cursor:pointer;
    transition:transform .25s ease, background .25s ease, border-color .25s ease;
    color:var(--ink);
  }
  .season-btn:hover{transform:scale(1.08);}
  .season-btn.active{
    background:var(--accent);
    border-color:var(--accent);
    transform:scale(1.1);
  }

  .scroll-cue{
    position:absolute; left:6vw; bottom:36px; z-index:5;
    font-size:11px; letter-spacing:0.14em; text-transform:uppercase;
    color:var(--ink); opacity:0.6;
    display:flex; align-items:center; gap:8px;
  }
  .scroll-cue .line{width:1px; height:26px; background:currentColor; animation:pulse-line 2s infinite;}
  @keyframes pulse-line{0%,100%{opacity:.3;}50%{opacity:1;}}

  /* ---------- SECTIONS ---------- */
  section{
    padding:100px 6vw;
    max-width:1180px;
    margin:0 auto;
  }
  .kicker{
    font-size:12px;
    letter-spacing:0.18em;
    text-transform:uppercase;
    color:var(--accent);
    transition:color .8s ease;
    margin-bottom:16px;
    display:flex; align-items:center; gap:10px;
  }
  .kicker::before{content:""; width:26px; height:1px; background:currentColor;}
  .reveal{opacity:0; transform:translateY(28px); transition:opacity .8s ease, transform .8s ease;}
  .reveal.in{opacity:1; transform:translateY(0);}

  /* About */
  .about-grid{
    display:grid;
    grid-template-columns:1.1fr 1fr;
    gap:60px;
    align-items:start;
  }
  .about-grid h2{font-size:clamp(1.8rem,3.4vw,2.6rem); line-height:1.15; margin-bottom:22px;}
  .about-grid p{color:var(--paper-dim); line-height:1.7; font-size:15.5px;}
  .stat-row{
    display:flex; gap:36px; margin-top:36px; flex-wrap:wrap;
  }
  .stat-row .stat b{
    display:block; font-family:'Fraunces', serif; font-size:2rem; color:var(--paper);
  }
  .stat-row .stat span{font-size:12px; text-transform:uppercase; letter-spacing:0.08em; color:var(--paper-dim);}

  .edu-card{
    border:1px solid rgba(238,242,234,0.14);
    border-radius:18px;
    padding:28px;
    background:rgba(238,242,234,0.03);
  }
  .edu-card .badge{
    display:inline-block; padding:4px 12px; border-radius:100px;
    font-size:11px; letter-spacing:0.06em; text-transform:uppercase;
    background:var(--accent); color:var(--ink); font-weight:600;
    transition:background .8s ease;
    margin-bottom:14px;
  }
  .edu-card h3{font-size:1.25rem; margin-bottom:4px;}
  .edu-card .yrs{color:var(--paper-dim); font-size:13px; margin-bottom:16px;}
  .edu-card ul{list-style:none; display:flex; flex-direction:column; gap:10px;}
  .edu-card li{font-size:14px; color:var(--paper-dim); line-height:1.55; padding-left:18px; position:relative;}
  .edu-card li::before{content:"—"; position:absolute; left:0; color:var(--accent); transition:color .8s ease;}

  /* Skills */
  .skills-head{margin-bottom:48px;}
  .skills-head h2{font-size:clamp(1.8rem,3.4vw,2.6rem); max-width:640px; line-height:1.15;}
  .skill-cols{display:grid; grid-template-columns:repeat(2, 1fr); gap:28px;}
  .skill-card{
    border:1px solid rgba(238,242,234,0.14);
    border-radius:18px;
    padding:30px;
    transition:border-color .3s;
  }
  .skill-card:hover{border-color:var(--accent);}
  .skill-card .num{font-family:'Fraunces', serif; font-size:13px; color:var(--accent); transition:color .8s ease;}
  .skill-card h3{font-size:1.3rem; margin:12px 0 12px;}
  .skill-card p{color:var(--paper-dim); font-size:14.5px; line-height:1.65;}
  .tag-row{display:flex; flex-wrap:wrap; gap:8px; margin-top:18px;}
  .tag-row span{
    font-size:11.5px; padding:5px 11px; border-radius:100px;
    border:1px solid rgba(238,242,234,0.22); color:var(--paper-dim);
  }

  /* Projects */
  .proj-head{display:flex; justify-content:space-between; align-items:flex-end; margin-bottom:48px; gap:20px; flex-wrap:wrap;}
  .proj-head h2{font-size:clamp(1.8rem,3.4vw,2.6rem);}
  .proj-grid{display:grid; grid-template-columns:repeat(2,1fr); gap:24px;}
  .proj-card{
    border:1px solid rgba(238,242,234,0.14);
    border-radius:18px;
    padding:30px;
    position:relative;
    overflow:hidden;
    transition:transform .3s ease, border-color .3s ease;
  }
  .proj-card:hover{transform:translateY(-4px); border-color:rgba(238,242,234,0.34);}
  .proj-card .season-tag{
    position:absolute; top:22px; right:22px;
    font-size:10.5px; letter-spacing:0.08em; text-transform:uppercase;
    padding:5px 11px; border-radius:100px; font-weight:600; color:var(--ink);
  }
  .season-tag.spring{background:var(--spring);}
  .season-tag.summer{background:var(--summer);}
  .season-tag.autumn{background:var(--autumn); color:var(--paper);}
  .season-tag.winter{background:var(--winter); color:var(--ink);}
  .proj-card h3{font-size:1.2rem; margin:6px 0 10px; max-width:80%;}
  .proj-card p{color:var(--paper-dim); font-size:14px; line-height:1.6; margin-bottom:16px;}
  .proj-card .meta{font-size:12px; color:var(--paper-dim); opacity:0.7;}

  /* Timeline */
  .timeline{position:relative; margin-top:10px;}
  .timeline::before{
    content:""; position:absolute; left:9px; top:6px; bottom:6px; width:1px;
    background:rgba(238,242,234,0.18);
  }
  .tl-item{position:relative; padding-left:44px; margin-bottom:38px;}
  .tl-item:last-child{margin-bottom:0;}
  .tl-dot{
    position:absolute; left:0; top:2px; width:19px; height:19px; border-radius:50%;
    background:var(--ink); border:2px solid var(--accent); transition:border-color .8s ease;
  }
  .tl-item h3{font-size:1.05rem;}
  .tl-item .co{font-size:12.5px; color:var(--accent); transition:color .8s ease; margin:3px 0 2px;}
  .tl-item .dates{font-size:12px; color:var(--paper-dim); margin-bottom:8px;}
  .tl-item p{font-size:14px; color:var(--paper-dim); line-height:1.6; max-width:560px;}

  /* Contact */
  .contact-wrap{
    text-align:center;
    padding:110px 6vw 130px;
  }
  .contact-wrap .kicker{justify-content:center;}
  .contact-wrap .kicker::before{display:none;}
  .contact-wrap h2{font-size:clamp(2rem,5vw,3.4rem); max-width:720px; margin:0 auto 26px; line-height:1.1;}
  .contact-wrap p{color:var(--paper-dim); max-width:460px; margin:0 auto 34px; line-height:1.6;}
  .contact-btn{
    display:inline-block; padding:16px 34px; border-radius:100px;
    background:var(--accent); color:var(--ink); font-weight:600; font-size:14px;
    transition:background .8s ease, transform .2s ease;
  }
  .contact-btn:hover{transform:translateY(-2px);}
  .socials{display:flex; gap:16px; justify-content:center; margin-top:34px;}
  .socials a{
    width:44px; height:44px; border-radius:50%; border:1px solid rgba(238,242,234,0.2);
    display:flex; align-items:center; justify-content:center; font-size:14px;
    transition:border-color .2s, transform .2s;
  }
  .socials a:hover{border-color:var(--accent); transform:translateY(-2px);}

  footer{
    padding:26px 6vw; display:flex; justify-content:space-between;
    font-size:12px; color:var(--paper-dim); border-top:1px solid rgba(238,242,234,0.1);
  }

  @media (max-width:820px){
    .about-grid, .skill-cols, .proj-grid{grid-template-columns:1fr;}
    .hero-copy, .season-switch{position:relative; left:auto; right:auto; bottom:auto; margin:0 6vw;}
    .hero{display:flex; flex-direction:column; justify-content:flex-end; padding-bottom:40px;}
    .season-switch{flex-direction:row; margin-top:20px;}
    .scroll-cue{display:none;}
  }
</style>
</head>
<body>

<section class="hero">
  <canvas id="scene-canvas"></canvas>

  <div class="hero-nav">
    <span class="mark">Mehreen Riaz✦</span>
    <div class="links">
      <a href="#about">About</a>
      <a href="#skills">Skills</a>
      <a href="#work">Work</a>
      <a href="#contact">Contact</a>
    </div>
  </div>

  <div class="hero-copy">
    <div class="hero-eyebrow">Frontend Web &amp; Mobile Developer</div>
    <h1>One developer,<br><span class="season-word" id="season-word">four seasons</span><br>of growth.</h1>
    <p>I build responsive, user-friendly apps with React, React Native and JavaScript — and like any good garden, my work keeps growing, one season at a time.</p>
  </div>

  <div class="season-switch" id="season-switch">
    <button class="season-btn active" data-season="spring" title="Spring">🌱</button>
    <button class="season-btn" data-season="summer" title="Summer">🌞</button>
    <button class="season-btn" data-season="autumn" title="Autumn">🍂</button>
    <button class="season-btn" data-season="winter" title="Winter">❄️</button>
  </div>

  <div class="scroll-cue"><span class="line"></span> Scroll</div>
</section>

<section id="about">
  <div class="kicker">Work &amp; Experience</div>
  <div class="about-grid reveal">
    <div>
      <h2>I'm a frontend web &amp; mobile developer, building interfaces that hold up under real use.</h2>
      <p>I have experience building responsive and user-friendly applications using React, React Native, and JavaScript — cross-platform mobile apps and dynamic web interfaces for startups and established companies. My focus is on performance, clean architecture, and delivering intuitive experiences across devices. I also actively contribute to open-source communities.</p>
      <div class="stat-row">
        <div class="stat"><b>2019–23</b><span>BS Computer Science</span></div>
        <div class="stat"><b>6+</b><span>Shipped Projects</span></div>
        <div class="stat"><b>4</b><span>Core Stacks</span></div>
      </div>
    </div>
    <div class="edu-card">
      <span class="badge">Education</span>
      <h3>The Islamia University of Bahawalpur</h3>
      <div class="yrs">BS Computer Science · 2019 – 2023</div>
      <ul>
        <li>Studied core computer science subjects such as Data Structures, Operating Systems, Computer Networks and Database Systems.</li>
        <li>Gained experience in Artificial Intelligence, Machine Learning, Web and Mobile App Development, and Cloud Computing through coursework and self-directed learning.</li>
      </ul>
    </div>
  </div>
</section>

<section id="skills">
  <div class="kicker">What I Do</div>
  <div class="skills-head reveal">
    <h2>Two disciplines, one goal — interfaces that feel effortless.</h2>
  </div>
  <div class="skill-cols reveal">
    <div class="skill-card">
      <div class="num">01</div>
      <h3>Website Development</h3>
      <p>Building responsive website front ends using React, JavaScript, Redux and Tailwind CSS. Strong UI/UX focus — pixel-perfect, mobile-first interfaces that are fast and accessible, with clean API integration and efficient state management.</p>
      <div class="tag-row"><span>React</span><span>JavaScript</span><span>Redux</span><span>Tailwind CSS</span></div>
    </div>
    <div class="skill-card">
      <div class="num">02</div>
      <h3>Mobile Development</h3>
      <p>Cross-platform mobile apps built with React Native — from productivity tools to media players — with a focus on smooth interaction, reliable data handling, and interfaces that feel native on every device.</p>
      <div class="tag-row"><span>React Native</span><span>JavaScript</span><span>Cloud Computing</span></div>
    </div>
  </div>
</section>

<section id="work">
  <div class="proj-head reveal">
    <div>
      <div class="kicker">My Projects</div>
      <h2>Selected work, tagged by the season it was built in.</h2>
    </div>
  </div>
  <div class="proj-grid reveal">
    <div class="proj-card">
      <span class="season-tag autumn">Autumn</span>
      <h3>E-commerce Website</h3>
      <p>A fully responsive fruit-selling website with product listings, cart functionality, and a user-friendly interface using HTML, CSS and JavaScript.</p>
      <div class="meta">Created Nov 2024</div>
    </div>
    <div class="proj-card">
      <span class="season-tag autumn">Autumn</span>
      <h3>Overtime Mobile App</h3>
      <p>A React Native productivity tool for calculating employee overtime hours, with accurate reporting, salary adjustment support and employee records.</p>
      <div class="meta">Created Aug 2022</div>
    </div>
    <div class="proj-card">
      <span class="season-tag spring">Spring</span>
      <h3>Office Management System</h3>
      <p>Automated payroll processing that reduced manual intervention and streamlined financial operations, plus employee attendance and salary management.</p>
      <div class="meta">Created Apr 2020</div>
    </div>
    <div class="proj-card">
      <span class="season-tag spring">Spring</span>
      <h3>Resume Builder</h3>
      <p>An online resume maker built with React where users create, customize and download professional CVs — with real-time preview, multiple templates and PDF export.</p>
      <div class="meta">Created Jul 2023</div>
    </div>
  </div>
</section>

<section id="journey">
  <div class="kicker">My Work</div>
  <div class="timeline reveal">
    <div class="tl-item">
      <div class="tl-dot"></div>
      <h3>Saigon Music App</h3>
      <div class="co">TuneVerse Pvt Ltd.</div>
      <div class="dates">February 2025 – April 2025</div>
      <p>A sleek React Native mobile music player where users can search, stream and play songs — dynamic search, curated playlists and seamless audio playback.</p>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <h3>CarTag Mobile App</h3>
      <div class="co">AutoSync Solutions Pvt Ltd.</div>
      <div class="dates">January 2025 – March 2025</div>
      <p>A React Native app that lets users keep records using QR code scanning — ideal for inventory or cart management with real-time updates and secure tracking.</p>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <h3>E-commerce Website</h3>
      <div class="co">FreshCart Pvt Ltd.</div>
      <div class="dates">October 2024 – December 2024</div>
      <p>A fully responsive fruit-selling website with product listings, cart functionality and a user-friendly interface built with HTML, CSS and JavaScript.</p>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <h3>Resume Builder</h3>
      <div class="co">SmartHire Technologies Pvt Ltd.</div>
      <div class="dates">March 2024 – May 2024</div>
      <p>An online resume maker built with React, with multiple templates and real-time preview so users can build and export a polished CV in minutes.</p>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <h3>Office Management System</h3>
      <div class="co">Enigmatix Pvt Ltd.</div>
      <div class="dates">January 2023 – April 2023</div>
      <p>Designed and developed a system giving real-time insight into employee attendance patterns, improving workforce management.</p>
    </div>
  </div>
</section>

<section id="contact" class="contact-wrap">
  <div class="kicker">Contact</div>
  <h2>Available for React, Microservices, or full-stack web work.</h2>
  <p>I'm active across a few platforms and typically respond within 24 hours. Reach out whenever a season feels right.</p>
  <a href="#" class="contact-btn">See My Resume</a>
  <div class="socials">
    <a href="#" title="LinkedIn">in</a>
    <a href="#" title="GitHub">gh</a>
    <a href="#" title="Email">✉</a>
    <a href="#" title="Instagram">ig</a>
  </div>
</section>

<footer>
  <span>© 2026 Rimsha</span>
  <span id="season-footer-label">Spring in the garden</span>
</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
/* ---------------- reveal on scroll ---------------- */
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('in'); });
},{threshold:0.15});
revealEls.forEach(el=>io.observe(el));

/* ---------------- SEASON CONFIG ---------------- */
const SEASONS = {
  spring:{
    sky:['#bfe3f0','#eaf7d9'], accent:'#8BC34A',
    ground:0x9ccc65, dress:0xF48FB1, particle:0xffc1e3,
    word:'four seasons', footer:'Spring in the garden',
    fall:0.35, sway:0.55, size:0.09
  },
  summer:{
    sky:['#5fb8e0','#ffe29a'], accent:'#FFB300',
    ground:0xb7c95a, dress:0xFFC107, particle:0xfff2b0,
    word:'full bloom', footer:'Summer, full bloom',
    fall:0.1, sway:0.25, size:0.06
  },
  autumn:{
    sky:['#f2b774','#c96b3f'], accent:'#C1560C',
    ground:0xb5651d, dress:0xBF5B2E, particle:0xd2691e,
    word:'letting go', footer:'Autumn, letting go',
    fall:0.55, sway:0.9, size:0.1
  },
  winter:{
    sky:['#c9dbea','#eef3f7'], accent:'#4FC3F7',
    ground:0xf2f6fa, dress:0x81D4E3, particle:0xffffff,
    word:'quiet focus', footer:'Winter, quiet focus',
    fall:0.4, sway:0.2, size:0.07
  }
};
const order = ['spring','summer','autumn','winter'];
let seasonIndex = 0;
let current = SEASONS.spring;
let target = { ground:new THREE.Color(current.ground), dress:new THREE.Color(current.dress), particle:new THREE.Color(current.particle) };

function applySeasonUI(name){
  const s = SEASONS[name];
  document.documentElement.style.setProperty('--accent', s.accent);
  document.querySelector('.hero').style.setProperty('--sky-a', s.sky[0]);
  document.body.style.setProperty('background', '#0e1a16');
  document.querySelector('.hero').style.background = `linear-gradient(180deg, ${s.sky[0]}, ${s.sky[1]})`;
  document.getElementById('season-word').textContent = s.word;
  document.getElementById('season-footer-label').textContent = s.footer;
  document.querySelectorAll('.season-btn').forEach(b=>b.classList.toggle('active', b.dataset.season===name));
  target.ground.set(s.ground);
  target.dress.set(s.dress);
  target.particle.set(s.particle);
  fallSpeedTarget = s.fall; swayTarget = s.sway;
}

document.getElementById('season-switch').addEventListener('click', (e)=>{
  const btn = e.target.closest('.season-btn');
  if(!btn) return;
  const name = btn.dataset.season;
  seasonIndex = order.indexOf(name);
  applySeasonUI(name);
  resetAutoplay();
});

let autoplayTimer;
function resetAutoplay(){
  clearInterval(autoplayTimer);
  autoplayTimer = setInterval(()=>{
    seasonIndex = (seasonIndex+1) % order.length;
    applySeasonUI(order[seasonIndex]);
  }, 7000);
}
resetAutoplay();
applySeasonUI('spring');

/* ---------------- THREE.JS SCENE ---------------- */
const canvas = document.getElementById('scene-canvas');
const hero = document.querySelector('.hero');
const renderer = new THREE.WebGLRenderer({canvas, antialias:true, alpha:true});
renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(42, hero.clientWidth/hero.clientHeight, 0.1, 100);
camera.position.set(0, 2.1, 6.4);
camera.lookAt(0,1.5,0);

function resize(){
  const w = hero.clientWidth, h = hero.clientHeight;
  renderer.setSize(w,h);
  camera.aspect = w/h;
  camera.updateProjectionMatrix();
}
resize();
window.addEventListener('resize', resize);

/* lights */
const hemi = new THREE.HemisphereLight(0xffffff, 0x445544, 0.9);
scene.add(hemi);
const sun = new THREE.DirectionalLight(0xffffff, 1.0);
sun.position.set(3,5,4);
scene.add(sun);

/* ground */
const groundGeo = new THREE.CircleGeometry(6, 48);
const groundMat = new THREE.MeshStandardMaterial({color:0x9ccc65, roughness:1});
const ground = new THREE.Mesh(groundGeo, groundMat);
ground.rotation.x = -Math.PI/2;
scene.add(ground);

/* ---- low-poly woman figure (full body) ---- */
const girl = new THREE.Group();
const skinMat = new THREE.MeshStandardMaterial({color:0xE7B692, roughness:0.7});
const hairMat = new THREE.MeshStandardMaterial({color:0x3B2A20, roughness:0.6});
const dressMat = new THREE.MeshStandardMaterial({color:0xF48FB1, roughness:0.55});
const shoeMat = new THREE.MeshStandardMaterial({color:0x2b2b2b, roughness:0.5});

// legs
[-0.14, 0.14].forEach(x=>{
  const leg = new THREE.Mesh(new THREE.CylinderGeometry(0.09,0.08,0.95,10), skinMat);
  leg.position.set(x, 0.47, 0);
  girl.add(leg);
  const shoe = new THREE.Mesh(new THREE.SphereGeometry(0.12,10,8), shoeMat);
  shoe.position.set(x, 0.06, 0.05);
  shoe.scale.set(1,0.5,1.3);
  girl.add(shoe);
});

// dress (torso + skirt, tapered cylinder)
const dress = new THREE.Mesh(new THREE.CylinderGeometry(0.27,0.58,1.15,12), dressMat);
dress.position.set(0, 1.5, 0);
girl.add(dress);

// neck
const neck = new THREE.Mesh(new THREE.CylinderGeometry(0.08,0.09,0.16,8), skinMat);
neck.position.set(0,2.14,0);
girl.add(neck);

// head
const head = new THREE.Mesh(new THREE.SphereGeometry(0.27,16,14), skinMat);
head.position.set(0,2.42,0);
girl.add(head);

// hair (cap + flowing back piece)
const hairCap = new THREE.Mesh(new THREE.SphereGeometry(0.29,16,14, 0, Math.PI*2, 0, Math.PI*0.62), hairMat);
hairCap.position.set(0,2.47,0);
girl.add(hairCap);
const hairBack = new THREE.Mesh(new THREE.SphereGeometry(0.24,12,10), hairMat);
hairBack.scale.set(0.9,1.9,0.7);
hairBack.position.set(0,2.02,-0.14);
girl.add(hairBack);

// arms
[-1,1].forEach(sign=>{
  const arm = new THREE.Mesh(new THREE.CylinderGeometry(0.065,0.06,0.85,8), skinMat);
  arm.position.set(sign*0.42, 1.78, 0);
  arm.rotation.z = sign * 0.26;
  girl.add(arm);
  const hand = new THREE.Mesh(new THREE.SphereGeometry(0.08,8,8), skinMat);
  hand.position.set(sign*0.55, 1.37, 0);
  girl.add(hand);
});

girl.position.y = 0;
scene.add(girl);

/* ---- particles (petals / fireflies / leaves / snow) ---- */
const PCOUNT = 260;
const pGeo = new THREE.BufferGeometry();
const positions = new Float32Array(PCOUNT*3);
const speeds = new Float32Array(PCOUNT);
const phases = new Float32Array(PCOUNT);
for(let i=0;i<PCOUNT;i++){
  positions[i*3+0] = (Math.random()-0.5) * 10;
  positions[i*3+1] = Math.random() * 8;
  positions[i*3+2] = (Math.random()-0.5) * 8 - 1;
  speeds[i] = 0.4 + Math.random()*0.8;
  phases[i] = Math.random()*Math.PI*2;
}
pGeo.setAttribute('position', new THREE.BufferAttribute(positions,3));
const pMat = new THREE.PointsMaterial({color:0xffc1e3, size:0.09, transparent:true, opacity:0.9, depthWrite:false});
const particles = new THREE.Points(pGeo, pMat);
scene.add(particles);

let fallSpeedTarget = 0.35, swayTarget = 0.55;
let fallSpeed = 0.35, sway = 0.55;
const currentGround = new THREE.Color(0x9ccc65);
const currentDress = new THREE.Color(0xF48FB1);
const currentParticle = new THREE.Color(0xffc1e3);

/* mouse parallax */
let mouseX=0, mouseY=0;
hero.addEventListener('mousemove', (e)=>{
  const r = hero.getBoundingClientRect();
  mouseX = ((e.clientX-r.left)/r.width - 0.5);
  mouseY = ((e.clientY-r.top)/r.height - 0.5);
});

const clock = new THREE.Clock();
function animate(){
  requestAnimationFrame(animate);
  const dt = Math.min(clock.getDelta(), 0.05);
  const t = clock.elapsedTime;

  // color lerps
  currentGround.lerp(target.ground, 0.01);
  currentDress.lerp(target.dress, 0.01);
  currentParticle.lerp(target.particle, 0.01);
  groundMat.color.copy(currentGround);
  dressMat.color.copy(currentDress);
  pMat.color.copy(currentParticle);
  fallSpeed += (fallSpeedTarget-fallSpeed)*0.02;
  sway += (swayTarget-sway)*0.02;

  // rotate girl slowly to show full body from every angle
  girl.rotation.y += dt * 0.18;

  // camera parallax
  camera.position.x += ((mouseX*0.8) - camera.position.x) * 0.03;
  camera.position.y += ((2.1 - mouseY*0.4) - camera.position.y) * 0.03;
  camera.lookAt(0,1.5,0);

  // particles
  const pos = pGeo.attributes.position.array;
  for(let i=0;i<PCOUNT;i++){
    pos[i*3+1] -= fallSpeed * dt * speeds[i];
    pos[i*3+0] += Math.sin(t*0.6 + phases[i]) * sway * dt * 0.3;
    if(pos[i*3+1] < 0){
      pos[i*3+1] = 7 + Math.random()*2;
      pos[i*3+0] = (Math.random()-0.5)*10;
      pos[i*3+2] = (Math.random()-0.5)*8 - 1;
    }
  }
  pGeo.attributes.position.needsUpdate = true;

  renderer.render(scene, camera);
}
animate();
</script>
</body>
</html>
