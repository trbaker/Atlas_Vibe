<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Atlas Vibe Coding 🦄</title>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@400;700;900&display=swap" rel="stylesheet" />
  <style>
    :root {
      --pink:    #FF6EB4;
      --yellow:  #FFE44D;
      --purple:  #C97EFF;
      --blue:    #5EC8F5;
      --green:   #5EE8A0;
      --orange:  #FFB347;
      --red:     #FF6B6B;
      --bg:      #FFF8F0;
      --white:   #FFFFFF;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background-color: var(--bg);
      font-family: 'Nunito', sans-serif;
      overflow-x: hidden;
      cursor: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='32' height='32' viewBox='0 0 32 32'><text y='28' font-size='28'>⭐</text></svg>") 16 16, auto;
    }

    /* ── ANIMATED RAINBOW BANNER ── */
    .rainbow-bar {
      height: 12px;
      background: linear-gradient(90deg,
        #FF6B6B, #FFB347, #FFE44D, #5EE8A0,
        #5EC8F5, #C97EFF, #FF6EB4, #FF6B6B);
      background-size: 300% 100%;
      animation: rainbowSlide 3s linear infinite;
    }
    @keyframes rainbowSlide {
      0%   { background-position: 0% 50%; }
      100% { background-position: 300% 50%; }
    }

    /* ── FLOATING EMOJIS (background layer) ── */
    .floaties {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    .floatie {
      position: absolute;
      font-size: 2rem;
      animation: floatUp linear infinite;
      opacity: 0.18;
    }
    @keyframes floatUp {
      0%   { transform: translateY(110vh) rotate(0deg); opacity: 0; }
      10%  { opacity: 0.22; }
      90%  { opacity: 0.18; }
      100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
    }

    /* ── MAIN CONTAINER ── */
    main {
      position: relative;
      z-index: 1;
      max-width: 860px;
      margin: 0 auto;
      padding: 2rem 1.5rem 4rem;
    }

    /* ── HERO SECTION ── */
    .hero {
      text-align: center;
      padding: 3rem 1rem 2rem;
      background: linear-gradient(135deg, #fff0fb 0%, #f0f8ff 50%, #fff8e0 100%);
      border-radius: 32px;
      border: 4px dashed var(--pink);
      margin-bottom: 2.5rem;
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: "🌈";
      position: absolute;
      font-size: 6rem;
      top: -20px;
      left: -10px;
      opacity: 0.25;
      animation: spin 8s linear infinite;
    }
    .hero::after {
      content: "🌈";
      position: absolute;
      font-size: 6rem;
      bottom: -20px;
      right: -10px;
      opacity: 0.25;
      animation: spin 8s linear infinite reverse;
    }
    @keyframes spin {
      from { transform: rotate(0deg); }
      to   { transform: rotate(360deg); }
    }

    .hero-emoji {
      font-size: 5rem;
      display: block;
      animation: bounce 1.2s ease-in-out infinite alternate;
      line-height: 1;
      margin-bottom: 0.5rem;
    }
    @keyframes bounce {
      from { transform: translateY(0); }
      to   { transform: translateY(-18px); }
    }

    .hero h1 {
      font-family: 'Fredoka One', cursive;
      font-size: clamp(2.8rem, 7vw, 5rem);
      line-height: 1.1;
      background: linear-gradient(135deg, var(--pink), var(--purple), var(--blue));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 0.75rem;
      letter-spacing: 1px;
    }

    .hero-tagline {
      font-size: 1.4rem;
      font-weight: 900;
      color: var(--orange);
      animation: wiggle 2s ease-in-out infinite;
    }
    @keyframes wiggle {
      0%, 100% { transform: rotate(-2deg); }
      50%       { transform: rotate(2deg); }
    }

    .stars-row {
      margin-top: 1.2rem;
      font-size: 1.8rem;
      letter-spacing: 0.3rem;
      animation: twinkle 1.5s ease-in-out infinite alternate;
    }
    @keyframes twinkle {
      from { opacity: 1; }
      to   { opacity: 0.4; }
    }

    /* ── SECTION CARDS ── */
    .cards-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
      margin-bottom: 2.5rem;
      max-width: 720px;
      margin-left: auto;
      margin-right: auto;
    }

    .proj-btn {
      display: block;
      text-align: center;
      padding: 0.6rem 1rem;
      border-radius: 12px;
      font-weight: 900;
      font-size: 0.95rem;
      text-decoration: none;
      transition: transform 0.15s, box-shadow 0.15s;
    }
    .proj-btn:hover { transform: translateY(-2px); }
    .proj-launch {
      background: linear-gradient(135deg, var(--pink), var(--purple));
      color: white;
      box-shadow: 0 4px 12px rgba(200,100,255,0.35);
    }
    .proj-launch:hover { box-shadow: 0 6px 18px rgba(200,100,255,0.5); }
    .proj-code {
      background: #FFF8F0;
      color: #666;
      border: 2px solid #ddd;
    }
    .proj-code:hover { border-color: var(--purple); color: var(--purple); }

    .card {
      background: var(--white);
      border-radius: 24px;
      padding: 1.75rem 1.5rem;
      box-shadow: 6px 6px 0px var(--pink);
      border: 3px solid var(--pink);
      transition: transform 0.2s, box-shadow 0.2s;
      position: relative;
      overflow: hidden;
    }
    .card:hover {
      transform: translate(-4px, -4px);
      box-shadow: 10px 10px 0px var(--purple);
    }
    .card:nth-child(2) { border-color: var(--purple); box-shadow: 6px 6px 0px var(--purple); }
    .card:nth-child(2):hover { box-shadow: 10px 10px 0px var(--blue); }

    .card-icon { font-size: 3rem; display: block; margin-bottom: 0.6rem; }
    .card h2 {
      font-family: 'Fredoka One', cursive;
      font-size: 1.5rem;
      color: #333;
      margin-bottom: 0.4rem;
    }
    .card p {
      font-size: 1rem;
      color: #555;
      line-height: 1.6;
    }

    /* ── UNICORN SECTION ── */
    .unicorn-section {
      background: linear-gradient(135deg, #ffe0f7, #e8d5ff, #d0f0ff);
      border-radius: 32px;
      border: 4px solid var(--purple);
      padding: 2.5rem 2rem;
      text-align: center;
      margin-bottom: 2.5rem;
      position: relative;
    }
    .unicorn-big {
      font-size: 6rem;
      animation: unicornPrance 3s ease-in-out infinite;
      display: inline-block;
    }
    @keyframes unicornPrance {
      0%   { transform: translateX(0) rotate(-5deg); }
      25%  { transform: translateX(20px) rotate(5deg) scale(1.05); }
      50%  { transform: translateX(0) rotate(-5deg); }
      75%  { transform: translateX(-20px) rotate(5deg) scale(1.05); }
      100% { transform: translateX(0) rotate(-5deg); }
    }
    .unicorn-section h2 {
      font-family: 'Fredoka One', cursive;
      font-size: 2.2rem;
      color: var(--purple);
      margin: 0.8rem 0 0.5rem;
    }
    .unicorn-section p {
      font-size: 1.1rem;
      color: #555;
      max-width: 500px;
      margin: 0 auto;
    }

    /* ── RAINBOW SVG ── */
    .rainbow-wrapper {
      text-align: center;
      margin-bottom: 2.5rem;
    }
    .rainbow-wrapper svg {
      max-width: 100%;
      filter: drop-shadow(0 6px 14px rgba(200,100,255,0.25));
      animation: floatSlow 4s ease-in-out infinite alternate;
    }
    @keyframes floatSlow {
      from { transform: translateY(0); }
      to   { transform: translateY(-12px); }
    }

    /* ── TREASURE MAP ── */
    .treasure-section {
      background: #fdf4e3;
      border-radius: 28px;
      border: 4px dashed var(--orange);
      padding: 2rem;
      margin-bottom: 2.5rem;
      position: relative;
    }
    .treasure-section::before {
      content: "";
      position: absolute;
      inset: 6px;
      border-radius: 22px;
      border: 2px dashed #e0c070;
      pointer-events: none;
    }
    .treasure-section h2 {
      font-family: 'Fredoka One', cursive;
      font-size: 2rem;
      color: #a05a00;
      margin-bottom: 1rem;
      text-align: center;
    }
    .map-svg-wrap { text-align: center; margin-bottom: 1.2rem; }
    .map-svg-wrap svg {
      max-width: 100%;
      animation: floatSlow 5s ease-in-out infinite alternate-reverse;
    }
    .treasure-steps {
      list-style: none;
      display: grid;
      gap: 0.7rem;
    }
    .treasure-steps li {
      background: #fff8e8;
      border-left: 5px solid var(--orange);
      padding: 0.7rem 1rem;
      border-radius: 12px;
      font-size: 1.05rem;
      font-weight: 700;
      color: #7a4a00;
    }
    .treasure-steps li span { margin-right: 0.5rem; }

    /* ── FLOWERS ROW ── */
    .flowers-section {
      background: linear-gradient(135deg, #e8ffee, #fffbe8, #fff0fb);
      border-radius: 28px;
      border: 4px solid var(--green);
      padding: 2rem;
      margin-bottom: 2.5rem;
      text-align: center;
    }
    .flowers-section h2 {
      font-family: 'Fredoka One', cursive;
      font-size: 2rem;
      color: #2d8a4e;
      margin-bottom: 1rem;
    }
    .flower-row { font-size: 3rem; letter-spacing: 0.5rem; }
    .flower-row span {
      display: inline-block;
      animation: flowerBob 2s ease-in-out infinite;
    }
    .flower-row span:nth-child(2) { animation-delay: 0.2s; }
    .flower-row span:nth-child(3) { animation-delay: 0.4s; }
    .flower-row span:nth-child(4) { animation-delay: 0.6s; }
    .flower-row span:nth-child(5) { animation-delay: 0.8s; }
    .flower-row span:nth-child(6) { animation-delay: 1.0s; }
    .flower-row span:nth-child(7) { animation-delay: 1.2s; }
    .flower-row span:nth-child(8) { animation-delay: 1.4s; }
    @keyframes flowerBob {
      0%, 100% { transform: translateY(0) rotate(-5deg); }
      50%       { transform: translateY(-10px) rotate(5deg); }
    }
    .flowers-section p {
      margin-top: 1rem;
      font-size: 1.1rem;
      color: #3a7a50;
      font-weight: 700;
    }

    /* ── FOOTER ── */
    footer {
      text-align: center;
      font-family: 'Fredoka One', cursive;
      font-size: 1.3rem;
      color: var(--purple);
      padding: 1.5rem;
    }
    footer .footer-emoji { font-size: 2rem; animation: bounce 1s infinite alternate; display: inline-block; }

    /* ── SPARKLE CURSOR TRAIL (canvas) ── */
    #sparkle-canvas {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 9999;
    }
  </style>
</head>
<body>

<!-- Sparkle trail canvas -->
<canvas id="sparkle-canvas"></canvas>

<!-- Animated floating background emojis -->
<div class="floaties" id="floaties"></div>

<!-- Rainbow top bar -->
<div class="rainbow-bar"></div>

<main>

  <!-- ── HERO ── -->
  <section class="hero">
    <span class="hero-emoji">🦄✨</span>
    <h1>Atlas Vibe Coding</h1>
    <p class="hero-tagline">🌟 Where Code Becomes Magic! 🌟</p>
    <p class="stars-row">⭐🌸⭐🌸⭐🌸⭐</p>
  </section>

  <!-- ── PROJECT CARDS ── -->
  <div class="cards-grid">
    <div class="card">
      <span class="card-icon">🌍</span>
      <h2>Schools Living Atlas Explorer</h2>
      <p>Browse and launch amazing real-world maps and data layers from the Schools Living Atlas — oceans, earthquakes, wildlife, and more!</p>
      <div style="margin-top:1rem;display:flex;flex-direction:column;gap:0.5rem;">
        <a href="https://trbaker.github.io/Atlas_Vibe/mapmaker-gallery.html" target="_blank" class="proj-btn proj-launch">🚀 Open Live App</a>

      </div>
    </div>
    <div class="card">
      <span class="card-icon">🏷️</span>
      <h2>MapMaker Tagger</h2>
      <p>A handy tool for adding and managing tags on ArcGIS MapMaker items — making maps easier to find and organize!</p>
      <div style="margin-top:1rem;display:flex;flex-direction:column;gap:0.5rem;">
        <a href="https://trbaker.github.io/Atlas_Vibe/mapmaker-tagger.html" target="_blank" class="proj-btn proj-launch">🚀 Open Live App</a>

      </div>
    </div>
  </div>

  <!-- ── RAINBOW SVG ── -->
  <div class="rainbow-wrapper">
    <svg viewBox="0 0 500 220" xmlns="http://www.w3.org/2000/svg" width="500" height="220">
      <!-- Clouds -->
      <ellipse cx="60" cy="175" rx="55" ry="35" fill="white" opacity="0.9"/>
      <ellipse cx="95" cy="160" rx="45" ry="35" fill="white" opacity="0.9"/>
      <ellipse cx="30" cy="165" rx="40" ry="28" fill="white" opacity="0.9"/>
      <ellipse cx="440" cy="175" rx="55" ry="35" fill="white" opacity="0.9"/>
      <ellipse cx="465" cy="160" rx="45" ry="35" fill="white" opacity="0.9"/>
      <ellipse cx="410" cy="165" rx="40" ry="28" fill="white" opacity="0.9"/>
      <!-- Rainbow arcs -->
      <path d="M60,175 Q250,-60 440,175" fill="none" stroke="#FF6B6B" stroke-width="18" stroke-linecap="round"/>
      <path d="M70,175 Q250,-40 430,175" fill="none" stroke="#FFB347" stroke-width="18" stroke-linecap="round"/>
      <path d="M82,175 Q250,-20 418,175" fill="none" stroke="#FFE44D" stroke-width="18" stroke-linecap="round"/>
      <path d="M94,175 Q250,-2 406,175" fill="none" stroke="#5EE8A0" stroke-width="18" stroke-linecap="round"/>
      <path d="M106,175 Q250,14 394,175" fill="none" stroke="#5EC8F5" stroke-width="18" stroke-linecap="round"/>
      <path d="M118,175 Q250,30 382,175" fill="none" stroke="#C97EFF" stroke-width="18" stroke-linecap="round"/>
      <path d="M130,175 Q250,44 370,175" fill="none" stroke="#FF6EB4" stroke-width="18" stroke-linecap="round"/>
      <!-- Stars on rainbow -->
      <text x="240" y="60" font-size="28" text-anchor="middle">⭐</text>
      <text x="170" y="110" font-size="22">✨</text>
      <text x="310" y="108" font-size="22">✨</text>
    </svg>
  </div>

  <!-- ── UNICORN SECTION ── -->
  <section class="unicorn-section">
    <span class="unicorn-big">🦄</span>
    <h2>You Are a Coding Unicorn!</h2>
    <p>Every coder is unique and magical — just like a unicorn! Your ideas are one-of-a-kind. Never stop dreaming big! 💜</p>
    <p style="margin-top:1rem;font-size:2rem;letter-spacing:0.4rem;">🌟🦄🌟🦄🌟🦄🌟</p>
  </section>


</main>

<footer>
  <span class="footer-emoji">🦄</span>
  Made with 💖 &amp; lots of sparkles by Atlas Vibe Coding
  <span class="footer-emoji" style="animation-delay:0.5s">🌈</span>
</footer>

<div class="rainbow-bar" style="margin-top:0;"></div>

<script>
  /* ── FLOATING BACKGROUND EMOJIS ── */
  const emojis = ['🌸','🌺','🌻','🌈','⭐','✨','💫','🦄','🎀','🍀','🌟','💎','🎉','🎊'];
  const container = document.getElementById('floaties');
  for (let i = 0; i < 28; i++) {
    const el = document.createElement('span');
    el.className = 'floatie';
    el.textContent = emojis[Math.floor(Math.random() * emojis.length)];
    el.style.left = Math.random() * 100 + 'vw';
    el.style.fontSize = (1.5 + Math.random() * 2) + 'rem';
    el.style.animationDuration = (8 + Math.random() * 14) + 's';
    el.style.animationDelay = (Math.random() * 12) + 's';
    container.appendChild(el);
  }

  /* ── SPARKLE CURSOR TRAIL ── */
  const canvas = document.getElementById('sparkle-canvas');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });

  const sparkles = [];
  const colors = ['#FF6EB4','#FFE44D','#C97EFF','#5EC8F5','#5EE8A0','#FFB347','#FF6B6B'];

  window.addEventListener('mousemove', e => {
    for (let i = 0; i < 4; i++) {
      sparkles.push({
        x: e.clientX + (Math.random()-0.5)*20,
        y: e.clientY + (Math.random()-0.5)*20,
        r: 3 + Math.random() * 5,
        vx: (Math.random()-0.5)*3,
        vy: (Math.random()-0.5)*3 - 1.5,
        color: colors[Math.floor(Math.random()*colors.length)],
        life: 1
      });
    }
  });

  function animateSparkles() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    for (let i = sparkles.length - 1; i >= 0; i--) {
      const s = sparkles[i];
      s.x += s.vx;
      s.y += s.vy;
      s.vy += 0.08;
      s.life -= 0.03;
      if (s.life <= 0) { sparkles.splice(i, 1); continue; }
      ctx.globalAlpha = s.life;
      ctx.fillStyle = s.color;
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.r * s.life, 0, Math.PI * 2);
      ctx.fill();
      // tiny star
      ctx.fillStyle = '#fff';
      ctx.beginPath();
      ctx.arc(s.x - 1, s.y - 1, s.r * s.life * 0.35, 0, Math.PI * 2);
      ctx.fill();
    }
    ctx.globalAlpha = 1;
    requestAnimationFrame(animateSparkles);
  }
  animateSparkles();
</script>
</body>
</html>
