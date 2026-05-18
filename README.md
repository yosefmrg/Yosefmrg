<html lang="en" dir="ltr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Yousef Marghalani — Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Bebas+Neue&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --black: #0a0a0a; --off-white: #f5f0e8; --cream: #ede8dc;
      --gold: #c9a84c; --gold-light: #e8c97a; --warm-gray: #6b6460;
    }
    html { scroll-behavior: smooth; }
    body { background: var(--black); color: var(--off-white); font-family: 'DM Sans', sans-serif; font-weight: 300; overflow-x: hidden; cursor: none; }

    /* ── CURSOR ── */
    .cursor {
      position: fixed;
      top: 0; left: 0;
      width: 10px; height: 10px;
      background: var(--gold);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9999;
      will-change: transform;
      mix-blend-mode: difference;
    }
    .cursor-ring {
      position: fixed;
      top: 0; left: 0;
      width: 36px; height: 36px;
      border: 1px solid var(--gold);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9998;
      will-change: transform;
      opacity: 0.6;
      transition: width 0.2s ease, height 0.2s ease, border-color 0.2s ease, opacity 0.2s ease;
    }

    body::before { content:''; position:fixed; inset:0; background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E"); pointer-events:none; z-index:1000; opacity:0.35; }

    /* IMAGE SLOTS */
    .img-slot { position:relative; overflow:hidden; background:rgba(201,168,76,0.03); border:1px solid rgba(201,168,76,0.1); }
    .img-slot img { width:100%; height:100%; object-fit:cover; display:block; transition: transform 0.6s ease; }

    /* HERO */
    .hero { min-height:100vh; display:grid; grid-template-columns:1fr 1fr; position:relative; overflow:hidden; }
    .hero-left { display:flex; flex-direction:column; justify-content:flex-end; padding:80px 60px 80px 80px; position:relative; z-index:2; }
    .hero-right { position:relative; overflow:hidden; }
    .hero-right-overlay { position:absolute; inset:0; background:linear-gradient(to right, var(--black) 0%, transparent 40%); z-index:1; pointer-events:none; }
    .hero-bg-text { position:absolute; top:50%; right:-20px; transform:translateY(-50%) rotate(90deg); font-family:'Bebas Neue',sans-serif; font-size:clamp(120px,18vw,260px); color:transparent; -webkit-text-stroke:1px rgba(201,168,76,0.07); letter-spacing:0.05em; white-space:nowrap; pointer-events:none; z-index:0; user-select:none; }
    .hero-tag { font-size:11px; font-weight:500; letter-spacing:0.3em; text-transform:uppercase; color:var(--gold); margin-bottom:32px; opacity:0; animation:fadeUp 0.8s ease 0.2s forwards; }
    .hero-name { font-family:'Cormorant Garamond',serif; font-size:clamp(52px,7vw,96px); font-weight:300; line-height:0.95; letter-spacing:-0.02em; margin-bottom:8px; opacity:0; animation:fadeUp 0.9s ease 0.4s forwards; }
    .hero-name em { font-style:italic; color:var(--gold); }
    .hero-role { font-family:'Bebas Neue',sans-serif; font-size:clamp(13px,2vw,20px); letter-spacing:0.25em; color:var(--warm-gray); margin-bottom:56px; opacity:0; animation:fadeUp 0.9s ease 0.55s forwards; }
    .hero-divider { width:60px; height:1px; background:linear-gradient(to right,var(--gold),transparent); margin-bottom:36px; opacity:0; animation:fadeUp 0.8s ease 0.65s forwards; }
    .hero-intro { font-family:'Cormorant Garamond',serif; font-size:clamp(18px,2vw,24px); font-weight:300; line-height:1.65; color:var(--cream); max-width:480px; opacity:0; animation:fadeUp 1s ease 0.75s forwards; }
    .hero-intro strong { font-weight:600; color:var(--off-white); }
    .stage-light { position:absolute; top:-100px; left:50%; transform:translateX(-50%); width:2px; height:120vh; background:linear-gradient(to bottom,rgba(201,168,76,0.4) 0%,rgba(201,168,76,0.04) 60%,transparent 100%); filter:blur(8px); animation:flicker 4s ease-in-out infinite; z-index:0; }
    @keyframes flicker { 0%,100%{opacity:1} 50%{opacity:0.65} }
    .scroll-hint { position:absolute; bottom:40px; left:80px; display:flex; align-items:center; gap:12px; font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--warm-gray); opacity:0; animation:fadeUp 1s ease 1.2s forwards; z-index:3; }
    .scroll-line { width:40px; height:1px; background:var(--warm-gray); position:relative; overflow:hidden; }
    .scroll-line::after { content:''; position:absolute; top:0; left:-100%; width:100%; height:100%; background:var(--gold); animation:scanLine 2s ease-in-out 1.5s infinite; }
    @keyframes scanLine { to{left:200%} }

    /* STATS */
    .stats-strip { display:grid; grid-template-columns:repeat(4,1fr); border-top:1px solid rgba(201,168,76,0.15); border-bottom:1px solid rgba(201,168,76,0.15); }
    .stat-item { padding:48px 40px; border-right:1px solid rgba(201,168,76,0.1); position:relative; overflow:hidden; transition:background 0.4s; }
    .stat-item:last-child { border-right:none; }
    .stat-item::before { content:''; position:absolute; bottom:0; left:0; width:0; height:2px; background:var(--gold); transition:width 0.5s; }
    .stat-item:hover::before { width:100%; }
    .stat-item:hover { background:rgba(201,168,76,0.04); }
    .stat-number { font-family:'Bebas Neue',sans-serif; font-size:56px; color:var(--gold); line-height:1; margin-bottom:8px; }
    .stat-label { font-size:11px; letter-spacing:0.2em; text-transform:uppercase; color:var(--warm-gray); }

    /* IDENTITY */
    .identity-section { display:grid; grid-template-columns:1fr 1fr; }
    .identity-left { padding:100px 60px 100px 80px; display:flex; flex-direction:column; justify-content:center; border-right:1px solid rgba(201,168,76,0.1); }
    .identity-right { display:flex; flex-direction:column; }
    .section-label { font-size:10px; letter-spacing:0.35em; text-transform:uppercase; color:var(--gold); margin-bottom:24px; display:flex; align-items:center; gap:16px; }
    .section-label::before { content:''; display:inline-block; width:24px; height:1px; background:var(--gold); }
    .section-heading { font-family:'Cormorant Garamond',serif; font-size:clamp(36px,4.5vw,64px); font-weight:300; line-height:1.1; margin-bottom:36px; letter-spacing:-0.02em; }
    .section-heading em { font-style:italic; color:var(--gold); }
    .body-text { font-family:'Cormorant Garamond',serif; font-size:19px; font-weight:300; line-height:1.75; color:rgba(245,240,232,0.8); margin-bottom:20px; }
    .portrait-slot { flex:1; min-height:420px; }

    /* FIX 1: صورة البورتريه تظهر كاملة */
    .portrait-slot img { filter: grayscale(10%); object-fit: contain !important; object-position: center center; background: #0a0a0a; }

    .trait-cards { padding:32px 40px; display:flex; flex-direction:column; gap:14px; border-top:1px solid rgba(201,168,76,0.08); }
    .trait-card { padding:18px 22px; border:1px solid rgba(201,168,76,0.12); position:relative; overflow:hidden; transition:border-color 0.3s,transform 0.3s; }
    .trait-card::before { content:''; position:absolute; top:0; left:0; width:3px; height:0; background:var(--gold); transition:height 0.4s; }
    .trait-card:hover { border-color:rgba(201,168,76,0.4); transform:translateX(4px); }
    .trait-card:hover::before { height:100%; }
    .trait-icon { font-size:16px; margin-bottom:6px; display:block; }
    .trait-title { font-family:'Bebas Neue',sans-serif; font-size:15px; letter-spacing:0.15em; color:var(--off-white); margin-bottom:5px; }
    .trait-desc { font-size:12px; line-height:1.65; color:var(--warm-gray); }

    /* OFFER */
    .offer-section { padding:100px 80px; border-top:1px solid rgba(201,168,76,0.1); }
    .offer-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:2px; margin-top:60px; background:rgba(201,168,76,0.08); }
    .offer-item { background:var(--black); padding:48px 40px; position:relative; overflow:hidden; transition:background 0.3s; }
    .offer-item:hover { background:#0f0d08; }
    .offer-number { font-family:'Bebas Neue',sans-serif; font-size:72px; color:rgba(201,168,76,0.07); line-height:1; margin-bottom:16px; transition:color 0.3s; }
    .offer-item:hover .offer-number { color:rgba(201,168,76,0.14); }
    .offer-title { font-family:'Cormorant Garamond',serif; font-size:26px; font-weight:400; margin-bottom:16px; }
    .offer-desc { font-size:13px; line-height:1.7; color:var(--warm-gray); }

    /* BOXING */
    .boxing-section { padding:0 80px 80px; }
    .boxing-card { padding:48px; border:1px solid rgba(201,168,76,0.2); background:linear-gradient(135deg,#0f0d08 0%,#0a0a0a 100%); display:grid; grid-template-columns:1fr 1fr; gap:40px; align-items:start; position:relative; overflow:hidden; }
    .boxing-card::before { content:''; position:absolute; top:0; right:0; width:300px; height:300px; background:radial-gradient(circle,rgba(201,168,76,0.05) 0%,transparent 70%); pointer-events:none; }
    .boxing-photos { display:grid; grid-template-columns:1fr 1fr; gap:2px; background:rgba(201,168,76,0.1); }
    .boxing-photo { aspect-ratio:3/4; }

    /* QUOTE */
    .quote-section { padding:100px 80px; text-align:center; position:relative; overflow:hidden; }
    .quote-section::before { content:'\201C'; position:absolute; top:-20px; left:50%; transform:translateX(-50%); font-family:'Cormorant Garamond',serif; font-size:400px; color:rgba(201,168,76,0.04); line-height:1; pointer-events:none; }
    .quote-text { font-family:'Cormorant Garamond',serif; font-size:clamp(24px,3.5vw,48px); font-weight:300; font-style:italic; line-height:1.4; max-width:800px; margin:0 auto 32px; position:relative; z-index:1; }
    .quote-source { font-size:11px; letter-spacing:0.3em; text-transform:uppercase; color:var(--gold); }

    /* GALLERY */
    .gallery-section { padding:80px; padding-bottom:80px; }
    .gallery-grid-2x2 { display:grid; grid-template-columns:1fr 1fr; gap:2px; margin-top:40px; background:rgba(201,168,76,0.06); }
    .gallery-cell { aspect-ratio:3/4; overflow:hidden; }
    .gallery-cell img { transition:transform 0.5s ease; }
    .gallery-cell:hover img { transform:scale(1.04); }
    .wide-strip { display:grid; grid-template-columns:1fr 1fr; gap:2px; margin-top:2px; background:rgba(201,168,76,0.06); }
    .wide-cell { aspect-ratio:16/9; overflow:hidden; }
    .wide-cell img { transition:transform 0.5s ease; }
    .wide-cell:hover img { transform:scale(1.04); }

    /* PARTNERS */
    .partners-section { padding:100px 80px; background:#0c0b08; border-top:1px solid rgba(201,168,76,0.1); }
    .partners-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(150px,1fr)); gap:50px 30px; align-items:center; margin-top:60px; }
    .partner-item { display:flex; flex-direction:column; align-items:center; gap:15px; opacity:0.75; transition:0.4s ease; }
    .partner-item:hover { opacity:1; transform:translateY(-5px); }

    /* FIX 2: اللوغوهات تظهر بشكل طبيعي بدون تحويل للأبيض */
    .partner-item img { width:100%; max-width:130px; height:75px; object-fit:contain; }
    .partner-item span { font-size:9px; letter-spacing:1px; text-transform:uppercase; color:var(--warm-gray); text-align:center; }

    /* BOTTOM */
    .bottom-section { display:grid; grid-template-columns:1fr 1fr; border-top:1px solid rgba(201,168,76,0.1); }
    .lang-section { padding:80px; border-right:1px solid rgba(201,168,76,0.1); display:flex; flex-direction:column; justify-content:center; }
    .lang-item { display:flex; align-items:center; justify-content:space-between; padding:20px 0; border-bottom:1px solid rgba(201,168,76,0.08); }
    .lang-name { font-family:'Cormorant Garamond',serif; font-size:22px; font-weight:300; }
    .lang-level { font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--gold); margin-top:4px; }
    .lang-bar { width:120px; height:1px; background:rgba(201,168,76,0.15); position:relative; }
    .lang-bar-fill { position:absolute; top:0; left:0; height:100%; background:var(--gold); }
    .cta-section { padding:80px; display:flex; flex-direction:column; justify-content:center; position:relative; overflow:hidden; }
    .cta-heading { font-family:'Cormorant Garamond',serif; font-size:clamp(28px,3vw,44px); font-weight:300; line-height:1.2; margin-bottom:32px; position:relative; z-index:2; }
    .cta-heading em { font-style:italic; color:var(--gold); }
    .cta-btn { display:inline-flex; align-items:center; gap:16px; padding:16px 36px; background:transparent; border:1px solid var(--gold); color:var(--gold); font-family:'DM Sans',sans-serif; font-size:11px; letter-spacing:0.25em; text-transform:uppercase; cursor:none; transition:all 0.3s; width:fit-content; text-decoration:none; margin-bottom:12px; position:relative; z-index:2; }
    .cta-btn:hover { background:var(--gold); color:var(--black); }

    footer { padding:32px 80px; border-top:1px solid rgba(201,168,76,0.1); display:flex; align-items:center; justify-content:space-between; }
    .footer-name { font-family:'Bebas Neue',sans-serif; font-size:20px; letter-spacing:0.2em; color:rgba(245,240,232,0.3); }
    .footer-nav { display:flex; gap:40px; }
    .footer-nav a { font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--warm-gray); text-decoration:none; transition:color 0.2s; }
    .footer-nav a:hover { color:var(--gold); }

    @keyframes fadeUp { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }
    .reveal { opacity:0; transform:translateY(30px); transition:opacity 0.8s ease,transform 0.8s ease; }
    .reveal.visible { opacity:1; transform:translateY(0); }

    @media(max-width:900px){
      .hero,.identity-section,.bottom-section{grid-template-columns:1fr}
      .hero-right{height:55vw}
      .hero-left{padding:80px 32px}
      .stats-strip{grid-template-columns:repeat(2,1fr)}
      .offer-grid,.boxing-card,.gallery-grid-2x2,.wide-strip{grid-template-columns:1fr}
      .identity-left{padding:60px 32px}
      .offer-section,.quote-section,.gallery-section,.boxing-section,.partners-section{padding:60px 32px}
      .lang-section,.cta-section{padding:60px 32px}
      .lang-section{border-right:none;border-bottom:1px solid rgba(201,168,76,0.1)}
      .partners-grid{grid-template-columns:repeat(3,1fr);gap:30px 15px}
      footer{padding:32px;flex-direction:column;gap:20px}
      .scroll-hint{left:32px}
    }
  </style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- HERO -->
<section class="hero">
  <div class="hero-left">
    <p class="hero-tag">Media Professional · Event Host · Stage Director</p>
    <h1 class="hero-name">Yousef<br><em>Marghalani</em></h1>
    <p class="hero-role">Radio Presenter & MC · Jeddah, Saudi Arabia</p>
    <div class="hero-divider"></div>
    <p class="hero-intro">
      Seven years commanding airwaves and live stages. I don't just fill silence,
      I <strong>shape atmosphere</strong>, <strong>move audiences</strong>, and
      deliver moments that become memories.
    </p>
  </div>
  <div class="hero-right">
    <div class="img-slot" style="width:100%;height:100%">
      <img src="MicPic.png" alt="Yousef Marghalani on Microphone">
    </div>
    <div class="hero-right-overlay"></div>
    <div class="stage-light"></div>
  </div>
  <div class="hero-bg-text">PRESENCE</div>
  <div class="scroll-hint"><div class="scroll-line"></div>Scroll to explore</div>
</section>

<!-- STATS -->
<div class="stats-strip reveal">
  <div class="stat-item"><div class="stat-number" id="cnt1">7+</div><div class="stat-label">Years on Air</div></div>
  <div class="stat-item"><div class="stat-number" id="cnt2">14</div><div class="stat-label">Team Members Led</div></div>
  <div class="stat-item"><div class="stat-number" id="cnt3">3</div><div class="stat-label">Flagship Shows</div></div>
  <div class="stat-item"><div class="stat-number">2026</div><div class="stat-label">Latest Live Event</div></div>
</div>

<!-- IDENTITY -->
<section class="identity-section">
  <div class="identity-left reveal">
    <p class="section-label">Who I Am</p>
    <h2 class="section-heading">More than a voice —<br>a <em>stage presence</em></h2>
    <p class="body-text">
      I'm a Senior Radio Presenter and Media Manager with over seven years 
      crafting the energy that keeps audiences tuned in and showing up.
    </p>
    <p class="body-text">
      From managing daily live broadcasting at Mix FM across Jeddah and Riyadh, 
      to hosting the Jeddah Shopping Festival, City Walk Opening Ceremony, 
      Swiss Tourism Authority events, and the Saudi Boxing Federation Championship.
      I've learned that great hosting means reading the room and owning the moment.
    </p>
    <p class="body-text">
      Bilingual in Arabic and English, I move fluently between formal ceremony, 
      high-energy entertainment, and intimate audience engagement.
    </p>
  </div>
  <div class="identity-right">
    <div class="portrait-slot">
      <div class="img-slot" style="width:100%;height:100%;min-height:420px">
        <img src="Armedhand.png" alt="Yousef Action Shot">
      </div>
    </div>
    <div class="trait-cards">
      <div class="trait-card"><span class="trait-icon">🎙</span><div class="trait-title">Commanding Communicator</div><div class="trait-desc">Daily live broadcasting trained my instincts — I handle the unexpected without breaking stride.</div></div>
      <div class="trait-card"><span class="trait-icon">🎭</span><div class="trait-title">Stage Intelligence</div><div class="trait-desc">I read the room and adapt — pacing, tone, humor, and gravitas in service of the moment.</div></div>
      <div class="trait-card"><span class="trait-icon">🌐</span><div class="trait-title">Bilingual Fluency</div><div class="trait-desc">Native Arabic, professional English — ready for international conferences and national ceremonies.</div></div>
    </div>
  </div>
</section>

<!-- OFFER -->
<section id="experience" class="offer-section reveal">
  <p class="section-label">What I Bring to Your Event</p>
  <h2 class="section-heading" style="max-width:600px">From brief to <em>brilliance</em></h2>
  <div class="offer-grid">
    <div class="offer-item"><div class="offer-number">01</div><div class="offer-title">Master of Ceremonies</div><div class="offer-desc">Conference openings, award ceremonies, product launches, national events. I anchor the program with authority and warmth, keeping energy alive from start to finish.</div></div>
    <div class="offer-item"><div class="offer-number">02</div><div class="offer-title">Stage & Show Direction</div><div class="offer-desc">Coordinating production, technical, and talent teams is second nature. I ensure the vision translates seamlessly from rehearsal to the live moment.</div></div>
    <div class="offer-item"><div class="offer-number">03</div><div class="offer-title">Live Audience Engagement</div><div class="offer-desc">I turn passive audiences into active participants, creating shared energy that defines memorable events and leaves lasting impressions.</div></div>
    <div class="offer-item"><div class="offer-number">04</div><div class="offer-title">Content & Script Development</div><div class="offer-desc">I collaborate on run-of-show scripting, segment flow, and on-stage messaging that serves the event's purpose and brand identity.</div></div>
    <div class="offer-item"><div class="offer-number">05</div><div class="offer-title">Media & Brand Activation</div><div class="offer-desc">Deep roots in music programming and artist relations, I help brands connect to cultural moments through curated content and strategic partnerships.</div></div>
    <div class="offer-item"><div class="offer-number">06</div><div class="offer-title">Crisis-Calm Leadership</div><div class="offer-desc">Live broadcasting teaches that nothing goes exactly to plan. I stay composed, pivot gracefully, and protect the audience experience no matter what.</div></div>
  </div>
</section>

<!-- BOXING -->
<section class="boxing-section reveal" style="margin-top:80px">
  <div class="boxing-card">
    <div>
      <p class="section-label" style="margin-bottom:20px">Featured Event · April 18, 2026</p>
      <div style="display:flex;align-items:center;gap:15px;margin-bottom:24px">
        <img src="SaudiBoxing.png" alt="Saudi Boxing Federation Logo" style="width:50px;mix-blend-mode:screen">
        <div style="padding:6px 16px;border:1px solid rgba(201,168,76,0.3);font-size:10px;letter-spacing:0.2em;text-transform:uppercase;color:var(--gold)">Saudi Boxing Federation</div>
      </div>
      <h3 style="font-family:'Cormorant Garamond',serif;font-size:clamp(24px,3vw,40px);font-weight:300;line-height:1.15;margin-bottom:20px">
        Western & Southern Region<br><em style="color:var(--gold)">Boxing Championship</em>
      </h3>
      <p style="font-size:14px;color:var(--warm-gray);line-height:1.85;margin-bottom:20px">
        Official MC for the <strong style="color:var(--off-white)">Saudi Boxing Federation Championship</strong> — 
        Western & Southern Region, Men's and Women's age-group categories. 
        Organized under the Saudi Ministry of Sport, Jeddah 2026.
      </p>
      <div style="display:flex;flex-wrap:wrap;gap:10px;margin-top:8px">
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🥊 Men's Categories</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🥊 Women's Categories</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🇸🇦 Ministry of Sport</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">📍 Jeddah</span>
      </div>
    </div>
    <div class="boxing-photos">
      <div class="boxing-photo"><div class="img-slot" style="width:100%;height:100%"><img src="Boxing1.jpg" alt="Boxing Event"></div></div>
      <div class="boxing-photo"><div class="img-slot" style="width:100%;height:100%"><img src="Boxing2.jpg" alt="Boxing Event"></div></div>
    </div>
  </div>
</section>

<!-- QUOTE -->
<section class="quote-section reveal">
  <p class="quote-text">"The stage doesn't make the host. The host makes the stage."</p>
  <p class="quote-source">A guiding principle</p>
</section>

<!-- GALLERY -->
<section id="projects" class="gallery-section reveal">
  <p class="section-label">Behind the Mic</p>
  <h2 class="section-heading" style="max-width:500px">Moments that <em>define the craft</em></h2>
  <p style="font-size:10px;letter-spacing:0.3em;text-transform:uppercase;color:var(--warm-gray);margin-top:48px;margin-bottom:12px">Mix FM Radio مكس إف إم</p>
  <div class="gallery-grid-2x2">
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="Indieshow1.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="MIXPM.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="SahSeh.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="KickOFF.jpg" alt="Mix FM Radio"></div></div>
  </div>
  <p style="font-size:10px;letter-spacing:0.3em;text-transform:uppercase;color:var(--warm-gray);margin-top:32px;margin-bottom:12px">Radio Studio & Live Events</p>
  <div class="wide-strip">
    <div class="wide-cell"><div class="img-slot" style="width:100%;height:100%"><img src="Studio.jpg" alt="Radio Studio Mix FM"></div></div>
    <div class="wide-cell"><div class="img-slot" style="width:100%;height:100%"><img src="SwissMC.jpg" alt="Live Event Stage"></div></div>
  </div>
</section>

<!-- PARTNERS -->
<section class="partners-section reveal">
  <p class="section-label">Success Partners</p>
  <h2 class="section-heading">Brands I've <em>Collaborated</em> With</h2>
  <div class="partners-grid">
    <div class="partner-item"><img src="Mix Logo.png" alt="Mix FM"><span>Mix FM مكس</span></div>
    <div class="partner-item"><img src="GCAM.png" alt="GCAM"><span>GCAM الهيئة العامة لتنظيم الإعلام</span></div>
    <div class="partner-item"><img src="ABC.png" alt="ABC NEWS"><span>ABC NEWS Washington DC - Jeddah</span></div>
    <div class="partner-item"><img src="TheWhiteHouse.png" alt="The White House 2022"><span>The White House - PRESS CORPS JULY 2022</span></div>
    <div class="partner-item"><img src="MDLbeast.png" alt="MDL Beast"><span>MDL Beast SS21 & SS22</span></div>
    <div class="partner-item"><img src="Sela.png" alt="Sela"><span>Sela صلة</span></div>
    <div class="partner-item"><img src="RiyadhSeason 2022.png" alt="Riyadh Season 2022"><span>Riyadh Season 2022 موسم الرياض</span></div>
    <div class="partner-item"><img src="RUH BLVD Ramadan.png" alt="RUH BLVD"><span>Boulevard Riyadh City - Ramadan 2025</span></div>
    <div class="partner-item"><img src="CITYWALK.png" alt="City Walk Jeddah 2022"><span>City Walk Jeddah 2022</span></div>
    <div class="partner-item"><img src="JeddahPromenade.png" alt="Jeddah Promenade"><span>Jeddah Promenade 2025 يوم التأسيس</span></div>
    <div class="partner-item"><img src="F1JED22.png" alt="F1 Jeddah 2022"><span>FORMULA 1 STC SAUDI ARABIAN GRAND PRIX 2022</span></div>
    <div class="partner-item"><img src="Aroya.png" alt="Aroya Cruise"><span>Aroya Cruise أرويا كروز</span></div>
    <div class="partner-item"><img src="Emirates.png" alt="Emirates"><span>Emirates طيران الإمارات</span></div>
    <div class="partner-item"><img src="DUBAI.png" alt="Dubai Tourism"><span>Department of Economy & Tourism - DUBAI</span></div>
    <div class="partner-item"><img src="Geneva.png" alt="Geneva Tourism"><span>Geneva all season campaign 2026</span></div>
    <div class="partner-item"><img src="McDonaldKSA.png" alt="McDonald's KSA"><span>McDonald's KSA</span></div>
    <div class="partner-item"><img src="DunkingAR.png" alt="Dunkin Saudi"><span>Dunkin Saudi</span></div>
    <div class="partner-item"><img src="McCafeKSA.jpg" alt="McCafe KSA"><span>McCafe KSA</span></div>
    <div class="partner-item"><img src="AlmaneHSP.png" alt="Almane Hospital"><span>Almane Hospital مجموعة مستشفيات المانع</span></div>
    <div class="partner-item"><img src="Boost Jeddah.png" alt="Boost Jeddah"><span>Boost Jeddah بووست</span></div>
    <div class="partner-item"><img src="diriyah season.png" alt="Diriyah Season 2022"><span>Basketball 3X3 2022 موسم الدرعية</span></div>
    <div class="partner-item"><img src="SaudiInfra.png" alt="Saudi Infrastructure"><span>Saudi Infrastructure Expo 2025</span></div>
    <div class="partner-item"><img src="SaudiMaritime.png" alt="Saudi Maritime"><span>Saudi Maritime & Logistics Congress 2024</span></div>
    <div class="partner-item"><img src="big5.png" alt="The Big 5"><span>The Big 5 Construct Saudi 2025</span></div>
    <div class="partner-item"><img src="IHF.png" alt="IHF"><span>IHF - International Hardware Fair Saudi</span></div>
    <div class="partner-item"><img src="FSB.png" alt="FSB Sports"><span>FSB Sports Show Riyadh 2025</span></div>
    <div class="partner-item"><img src="OSN.png" alt="OSN PLUS"><span>OSN+ 2023</span></div>
    <div class="partner-item"><img src="disneyplus.png" alt="Disney+"><span>Disney+ 1 year Anniversary campaign 2023</span></div>
    <div class="partner-item"><img src="FIFAJED.png" alt="FIFA Club World Cup Saudi 2023"><span>FIFA Club World Cup Saudi Arabia 2023™</span></div>
    <div class="partner-item"><img src="AFC.png" alt="AFC Jeddah 2026"><span>The AFC Champions League Elite Finals Jeddah 2026</span></div>
    <div class="partner-item"><img src="Supercopa de Espana.png" alt="Supercopa de Espana 2026"><span>Supercopa de Espana 2026 - Jeddah</span></div>
    <div class="partner-item"><img src="SaudiBoxing.png" alt="Saudi Boxing"><span>بطولة المنطقة الغربية والجنوبية نخبة رجال وسيدات 2026</span></div>
    <div class="partner-item"><img src="SaudiBoxing.png" alt="Saudi Boxing"><span>بطولة المنطقة الغربية والجنوبية فئات سنية رجال وسيدات 2026</span></div>
  </div>
</section>

<!-- BOTTOM -->
<div class="bottom-section">
  <div class="lang-section reveal">
    <p class="section-label">Languages</p>
    <h3 class="section-heading" style="font-size:36px;margin-bottom:40px">I speak to <em>every room</em></h3>
    <div class="lang-item">
      <div><div class="lang-name">Arabic</div><div class="lang-level">Native</div></div>
      <div class="lang-bar"><div class="lang-bar-fill" style="width:100%"></div></div>
    </div>
    <div class="lang-item">
      <div><div class="lang-name">English</div><div class="lang-level">Professional</div></div>
      <div class="lang-bar"><div class="lang-bar-fill" style="width:85%"></div></div>
    </div>
  </div>
  <div class="cta-section reveal">
    <p class="section-label">Let's Work Together</p>
    <h3 class="cta-heading">Your next event deserves a host who <em>owns the stage</em>.</h3>
    <p style="font-size:14px;color:var(--warm-gray);margin-bottom:36px;font-weight:300;line-height:1.7">Corporate conferences, national ceremonies, live entertainment. I'm ready to be the voice that makes it unforgettable.</p>
    <a href="tel:+966565624247" class="cta-btn">
      +966 5656 24247
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
    </a>
    <a href="mailto:yosif_saber@yahoo.com" class="cta-btn" style="border-color:rgba(201,168,76,0.5);color:var(--warm-gray)">yosif_saber@yahoo.com</a>
    <a href="https://www.linkedin.com/in/yousef-marghalani-94442742" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">LinkedIn</a>
    <a href="https://www.instagram.com/yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">Instagram</a>
    <a href="https://www.tiktok.com/@yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">TikTok</a>
    <a href="https://x.com/yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">X</a>
  </div>
</div>

<footer>
  <div class="footer-name">Yousef Saber A. Marghalani · Portfolio</div>
  <nav class="footer-nav">
    <a href="#experience">Experience</a>
    <a href="#projects">Projects</a>
  </nav>
</footer>

<script>
  const cursor = document.getElementById('cursor');
  const ring   = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX;
    my = e.clientY;
    cursor.style.transform = `translate(${mx - 5}px, ${my - 5}px)`;
  }, { passive: true });

  (function animRing() {
    rx += (mx - rx - 18) * 0.18;
    ry += (my - ry - 18) * 0.18;
    ring.style.transform = `translate(${rx}px, ${ry}px)`;
    requestAnimationFrame(animRing);
  })();

  document.querySelectorAll('a, button, .trait-card, .offer-item, .stat-item, .img-slot, .partner-item').forEach(el => {
    el.addEventListener('mouseenter', () => {
      ring.style.width  = '52px';
      ring.style.height = '52px';
      ring.style.borderColor = 'var(--gold-light)';
      ring.style.opacity = '0.9';
    });
    el.addEventListener('mouseleave', () => {
      ring.style.width  = '36px';
      ring.style.height = '36px';
      ring.style.borderColor = 'var(--gold)';
      ring.style.opacity = '0.6';
    });
  });

  const revealObs = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) setTimeout(() => e.target.classList.add('visible'), i * 80);
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => revealObs.observe(el));

  function animCount(el, target, suffix) {
    let current = 0;
    const step = target / 60;
    const timer = setInterval(() => {
      current += step;
      if (current >= target) {
        el.textContent = target + suffix;
        clearInterval(timer);
      } else {
        el.textContent = Math.floor(current) + suffix;
      }
    }, 20);
  }

  const counterObs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        animCount(document.getElementById('cnt1'), 7, '+');
        animCount(document.getElementById('cnt2'), 14, '');
        animCount(document.getElementById('cnt3'), 3, '');
        counterObs.unobserve(e.target);
      }
    });
  }, { threshold: 0.5 });

  const strip = document.querySelector('.stats-strip');
  if (strip) counterObs.observe(strip);
</script>
</body>
</html>    .img-slot { position:relative; overflow:hidden; background:rgba(201,168,76,0.03); border:1px solid rgba(201,168,76,0.1); }
    .img-slot img { width:100%; height:100%; object-fit:cover; display:block; transition: transform 0.6s ease; }

    /* HERO */
    .hero { min-height:100vh; display:grid; grid-template-columns:1fr 1fr; position:relative; overflow:hidden; }
    .hero-left { display:flex; flex-direction:column; justify-content:flex-end; padding:80px 60px 80px 80px; position:relative; z-index:2; }
    .hero-right { position:relative; overflow:hidden; }
    .hero-right-overlay { position:absolute; inset:0; background:linear-gradient(to right, var(--black) 0%, transparent 40%); z-index:1; pointer-events:none; }
    .hero-bg-text { position:absolute; top:50%; right:-20px; transform:translateY(-50%) rotate(90deg); font-family:'Bebas Neue',sans-serif; font-size:clamp(120px,18vw,260px); color:transparent; -webkit-text-stroke:1px rgba(201,168,76,0.07); letter-spacing:0.05em; white-space:nowrap; pointer-events:none; z-index:0; user-select:none; }
    .hero-tag { font-size:11px; font-weight:500; letter-spacing:0.3em; text-transform:uppercase; color:var(--gold); margin-bottom:32px; opacity:0; animation:fadeUp 0.8s ease 0.2s forwards; }
    .hero-name { font-family:'Cormorant Garamond',serif; font-size:clamp(52px,7vw,96px); font-weight:300; line-height:0.95; letter-spacing:-0.02em; margin-bottom:8px; opacity:0; animation:fadeUp 0.9s ease 0.4s forwards; }
    .hero-name em { font-style:italic; color:var(--gold); }
    .hero-role { font-family:'Bebas Neue',sans-serif; font-size:clamp(13px,2vw,20px); letter-spacing:0.25em; color:var(--warm-gray); margin-bottom:56px; opacity:0; animation:fadeUp 0.9s ease 0.55s forwards; }
    .hero-divider { width:60px; height:1px; background:linear-gradient(to right,var(--gold),transparent); margin-bottom:36px; opacity:0; animation:fadeUp 0.8s ease 0.65s forwards; }
    .hero-intro { font-family:'Cormorant Garamond',serif; font-size:clamp(18px,2vw,24px); font-weight:300; line-height:1.65; color:var(--cream); max-width:480px; opacity:0; animation:fadeUp 1s ease 0.75s forwards; }
    .hero-intro strong { font-weight:600; color:var(--off-white); }
    .stage-light { position:absolute; top:-100px; left:50%; transform:translateX(-50%); width:2px; height:120vh; background:linear-gradient(to bottom,rgba(201,168,76,0.4) 0%,rgba(201,168,76,0.04) 60%,transparent 100%); filter:blur(8px); animation:flicker 4s ease-in-out infinite; z-index:0; }
    @keyframes flicker { 0%,100%{opacity:1} 50%{opacity:0.65} }
    .scroll-hint { position:absolute; bottom:40px; left:80px; display:flex; align-items:center; gap:12px; font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--warm-gray); opacity:0; animation:fadeUp 1s ease 1.2s forwards; z-index:3; }
    .scroll-line { width:40px; height:1px; background:var(--warm-gray); position:relative; overflow:hidden; }
    .scroll-line::after { content:''; position:absolute; top:0; left:-100%; width:100%; height:100%; background:var(--gold); animation:scanLine 2s ease-in-out 1.5s infinite; }
    @keyframes scanLine { to{left:200%} }

    /* STATS */
    .stats-strip { display:grid; grid-template-columns:repeat(4,1fr); border-top:1px solid rgba(201,168,76,0.15); border-bottom:1px solid rgba(201,168,76,0.15); }
    .stat-item { padding:48px 40px; border-right:1px solid rgba(201,168,76,0.1); position:relative; overflow:hidden; transition:background 0.4s; }
    .stat-item:last-child { border-right:none; }
    .stat-item::before { content:''; position:absolute; bottom:0; left:0; width:0; height:2px; background:var(--gold); transition:width 0.5s; }
    .stat-item:hover::before { width:100%; }
    .stat-item:hover { background:rgba(201,168,76,0.04); }
    .stat-number { font-family:'Bebas Neue',sans-serif; font-size:56px; color:var(--gold); line-height:1; margin-bottom:8px; }
    .stat-label { font-size:11px; letter-spacing:0.2em; text-transform:uppercase; color:var(--warm-gray); }

    /* IDENTITY */
    .identity-section { display:grid; grid-template-columns:1fr 1fr; }
    .identity-left { padding:100px 60px 100px 80px; display:flex; flex-direction:column; justify-content:center; border-right:1px solid rgba(201,168,76,0.1); }
    .identity-right { display:flex; flex-direction:column; }
    .section-label { font-size:10px; letter-spacing:0.35em; text-transform:uppercase; color:var(--gold); margin-bottom:24px; display:flex; align-items:center; gap:16px; }
    .section-label::before { content:''; display:inline-block; width:24px; height:1px; background:var(--gold); }
    .section-heading { font-family:'Cormorant Garamond',serif; font-size:clamp(36px,4.5vw,64px); font-weight:300; line-height:1.1; margin-bottom:36px; letter-spacing:-0.02em; }
    .section-heading em { font-style:italic; color:var(--gold); }
    .body-text { font-family:'Cormorant Garamond',serif; font-size:19px; font-weight:300; line-height:1.75; color:rgba(245,240,232,0.8); margin-bottom:20px; }
    .portrait-slot { flex:1; min-height:420px; }
    .portrait-slot img { filter: grayscale(10%); object-position: center 20%; }
    .trait-cards { padding:32px 40px; display:flex; flex-direction:column; gap:14px; border-top:1px solid rgba(201,168,76,0.08); }
    .trait-card { padding:18px 22px; border:1px solid rgba(201,168,76,0.12); position:relative; overflow:hidden; transition:border-color 0.3s,transform 0.3s; }
    .trait-card::before { content:''; position:absolute; top:0; left:0; width:3px; height:0; background:var(--gold); transition:height 0.4s; }
    .trait-card:hover { border-color:rgba(201,168,76,0.4); transform:translateX(4px); }
    .trait-card:hover::before { height:100%; }
    .trait-icon { font-size:16px; margin-bottom:6px; display:block; }
    .trait-title { font-family:'Bebas Neue',sans-serif; font-size:15px; letter-spacing:0.15em; color:var(--off-white); margin-bottom:5px; }
    .trait-desc { font-size:12px; line-height:1.65; color:var(--warm-gray); }

    /* OFFER */
    .offer-section { padding:100px 80px; border-top:1px solid rgba(201,168,76,0.1); }
    .offer-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:2px; margin-top:60px; background:rgba(201,168,76,0.08); }
    .offer-item { background:var(--black); padding:48px 40px; position:relative; overflow:hidden; transition:background 0.3s; }
    .offer-item:hover { background:#0f0d08; }
    .offer-number { font-family:'Bebas Neue',sans-serif; font-size:72px; color:rgba(201,168,76,0.07); line-height:1; margin-bottom:16px; transition:color 0.3s; }
    .offer-item:hover .offer-number { color:rgba(201,168,76,0.14); }
    .offer-title { font-family:'Cormorant Garamond',serif; font-size:26px; font-weight:400; margin-bottom:16px; }
    .offer-desc { font-size:13px; line-height:1.7; color:var(--warm-gray); }

    /* BOXING */
    .boxing-section { padding:0 80px 80px; }
    .boxing-card { padding:48px; border:1px solid rgba(201,168,76,0.2); background:linear-gradient(135deg,#0f0d08 0%,#0a0a0a 100%); display:grid; grid-template-columns:1fr 1fr; gap:40px; align-items:start; position:relative; overflow:hidden; }
    .boxing-card::before { content:''; position:absolute; top:0; right:0; width:300px; height:300px; background:radial-gradient(circle,rgba(201,168,76,0.05) 0%,transparent 70%); pointer-events:none; }
    .boxing-photos { display:grid; grid-template-columns:1fr 1fr; gap:2px; background:rgba(201,168,76,0.1); }
    .boxing-photo { aspect-ratio:3/4; }

    /* QUOTE */
    .quote-section { padding:100px 80px; text-align:center; position:relative; overflow:hidden; }
    .quote-section::before { content:'\201C'; position:absolute; top:-20px; left:50%; transform:translateX(-50%); font-family:'Cormorant Garamond',serif; font-size:400px; color:rgba(201,168,76,0.04); line-height:1; pointer-events:none; }
    .quote-text { font-family:'Cormorant Garamond',serif; font-size:clamp(24px,3.5vw,48px); font-weight:300; font-style:italic; line-height:1.4; max-width:800px; margin:0 auto 32px; position:relative; z-index:1; }
    .quote-source { font-size:11px; letter-spacing:0.3em; text-transform:uppercase; color:var(--gold); }

    /* GALLERY */
    .gallery-section { padding:80px; padding-bottom:80px; }
    .gallery-grid-2x2 { display:grid; grid-template-columns:1fr 1fr; gap:2px; margin-top:40px; background:rgba(201,168,76,0.06); }
    .gallery-cell { aspect-ratio:3/4; overflow:hidden; }
    .gallery-cell img { transition:transform 0.5s ease; }
    .gallery-cell:hover img { transform:scale(1.04); }
    .wide-strip { display:grid; grid-template-columns:1fr 1fr; gap:2px; margin-top:2px; background:rgba(201,168,76,0.06); }
    .wide-cell { aspect-ratio:16/9; overflow:hidden; }
    .wide-cell img { transition:transform 0.5s ease; }
    .wide-cell:hover img { transform:scale(1.04); }

/* PARTNERS */
    .partners-section { padding:100px 80px; background:#0c0b08; border-top:1px solid rgba(201,168,76,0.1); }
    .partners-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(150px,1fr)); gap:50px 30px; align-items:center; margin-top:60px; }
    .partner-item { display:flex; flex-direction:column; align-items:center; gap:15px; filter:grayscale(100%); opacity:1; transition:0.4s ease; }
    .partner-item:hover { filter:grayscale(0%); transform:translateY(-5px); }
    .partner-item img { width:100%; max-width:130px; height:75px; object-fit:contain; filter: brightness(0) invert(1); }
    .partner-item span { font-size:9px; letter-spacing:1px; text-transform:uppercase; color:var(--warm-gray); text-align:center; }

    /* BOTTOM */
    .bottom-section { display:grid; grid-template-columns:1fr 1fr; border-top:1px solid rgba(201,168,76,0.1); }
    .lang-section { padding:80px; border-right:1px solid rgba(201,168,76,0.1); display:flex; flex-direction:column; justify-content:center; }
    .lang-item { display:flex; align-items:center; justify-content:space-between; padding:20px 0; border-bottom:1px solid rgba(201,168,76,0.08); }
    .lang-name { font-family:'Cormorant Garamond',serif; font-size:22px; font-weight:300; }
    .lang-level { font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--gold); margin-top:4px; }
    .lang-bar { width:120px; height:1px; background:rgba(201,168,76,0.15); position:relative; }
    .lang-bar-fill { position:absolute; top:0; left:0; height:100%; background:var(--gold); }
    .cta-section { padding:80px; display:flex; flex-direction:column; justify-content:center; position:relative; overflow:hidden; }
    .cta-heading { font-family:'Cormorant Garamond',serif; font-size:clamp(28px,3vw,44px); font-weight:300; line-height:1.2; margin-bottom:32px; position:relative; z-index:2; }
    .cta-heading em { font-style:italic; color:var(--gold); }
    .cta-btn { display:inline-flex; align-items:center; gap:16px; padding:16px 36px; background:transparent; border:1px solid var(--gold); color:var(--gold); font-family:'DM Sans',sans-serif; font-size:11px; letter-spacing:0.25em; text-transform:uppercase; cursor:none; transition:all 0.3s; width:fit-content; text-decoration:none; margin-bottom:12px; position:relative; z-index:2; }
    .cta-btn:hover { background:var(--gold); color:var(--black); }

    footer { padding:32px 80px; border-top:1px solid rgba(201,168,76,0.1); display:flex; align-items:center; justify-content:space-between; }
    .footer-name { font-family:'Bebas Neue',sans-serif; font-size:20px; letter-spacing:0.2em; color:rgba(245,240,232,0.3); }
    .footer-nav { display:flex; gap:40px; }
    .footer-nav a { font-size:10px; letter-spacing:0.25em; text-transform:uppercase; color:var(--warm-gray); text-decoration:none; transition:color 0.2s; }
    .footer-nav a:hover { color:var(--gold); }

    @keyframes fadeUp { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }
    .reveal { opacity:0; transform:translateY(30px); transition:opacity 0.8s ease,transform 0.8s ease; }
    .reveal.visible { opacity:1; transform:translateY(0); }

    @media(max-width:900px){
      .hero,.identity-section,.bottom-section{grid-template-columns:1fr}
      .hero-right{height:55vw}
      .hero-left{padding:80px 32px}
      .stats-strip{grid-template-columns:repeat(2,1fr)}
      .offer-grid,.boxing-card,.gallery-grid-2x2,.wide-strip{grid-template-columns:1fr}
      .identity-left{padding:60px 32px}
      .offer-section,.quote-section,.gallery-section,.boxing-section,.partners-section{padding:60px 32px}
      .lang-section,.cta-section{padding:60px 32px}
      .lang-section{border-right:none;border-bottom:1px solid rgba(201,168,76,0.1)}
      .partners-grid{grid-template-columns:repeat(3,1fr);gap:30px 15px}
      footer{padding:32px;flex-direction:column;gap:20px}
      .scroll-hint{left:32px}
    }
  </style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- HERO -->
<section class="hero">
  <div class="hero-left">
    <p class="hero-tag">Media Professional · Event Host · Stage Director</p>
    <h1 class="hero-name">Yousef<br><em>Marghalani</em></h1>
    <p class="hero-role">Radio Presenter & MC · Jeddah, Saudi Arabia</p>
    <div class="hero-divider"></div>
    <p class="hero-intro">
      Seven years commanding airwaves and live stages. I don't just fill silence,
      I <strong>shape atmosphere</strong>, <strong>move audiences</strong>, and
      deliver moments that become memories.
    </p>
  </div>
  <div class="hero-right">
    <div class="img-slot" style="width:100%;height:100%">
      <img src="MicPic.png" alt="Yousef Marghalani on Microphone">
    </div>
    <div class="hero-right-overlay"></div>
    <div class="stage-light"></div>
  </div>
  <div class="hero-bg-text">PRESENCE</div>
  <div class="scroll-hint"><div class="scroll-line"></div>Scroll to explore</div>
</section>

<!-- STATS -->
<div class="stats-strip reveal">
  <div class="stat-item"><div class="stat-number" id="cnt1">7+</div><div class="stat-label">Years on Air</div></div>
  <div class="stat-item"><div class="stat-number" id="cnt2">14</div><div class="stat-label">Team Members Led</div></div>
  <div class="stat-item"><div class="stat-number" id="cnt3">3</div><div class="stat-label">Flagship Shows</div></div>
  <div class="stat-item"><div class="stat-number">2026</div><div class="stat-label">Latest Live Event</div></div>
</div>

<!-- IDENTITY -->
<section class="identity-section">
  <div class="identity-left reveal">
    <p class="section-label">Who I Am</p>
    <h2 class="section-heading">More than a voice —<br>a <em>stage presence</em></h2>
    <p class="body-text">
      I'm a Senior Radio Presenter and Media Manager with over seven years 
      crafting the energy that keeps audiences tuned in and showing up.
    </p>
    <p class="body-text">
      From managing daily live broadcasting at Mix FM across Jeddah and Riyadh, 
      to hosting the Jeddah Shopping Festival, City Walk Opening Ceremony, 
      Swiss Tourism Authority events, and the Saudi Boxing Federation Championship.
      I've learned that great hosting means reading the room and owning the moment.
    </p>
    <p class="body-text">
      Bilingual in Arabic and English, I move fluently between formal ceremony, 
      high-energy entertainment, and intimate audience engagement.
    </p>
  </div>
  <div class="identity-right">
    <div class="portrait-slot">
      <div class="img-slot" style="width:100%;height:100%;min-height:420px">
        <img src="Armedhand.png" alt="Yousef Action Shot">
      </div>
    </div>
    <div class="trait-cards">
      <div class="trait-card"><span class="trait-icon">🎙</span><div class="trait-title">Commanding Communicator</div><div class="trait-desc">Daily live broadcasting trained my instincts — I handle the unexpected without breaking stride.</div></div>
      <div class="trait-card"><span class="trait-icon">🎭</span><div class="trait-title">Stage Intelligence</div><div class="trait-desc">I read the room and adapt — pacing, tone, humor, and gravitas in service of the moment.</div></div>
      <div class="trait-card"><span class="trait-icon">🌐</span><div class="trait-title">Bilingual Fluency</div><div class="trait-desc">Native Arabic, professional English — ready for international conferences and national ceremonies.</div></div>
    </div>
  </div>
</section>

<!-- OFFER -->
<section id="experience" class="offer-section reveal">
  <p class="section-label">What I Bring to Your Event</p>
  <h2 class="section-heading" style="max-width:600px">From brief to <em>brilliance</em></h2>
  <div class="offer-grid">
    <div class="offer-item"><div class="offer-number">01</div><div class="offer-title">Master of Ceremonies</div><div class="offer-desc">Conference openings, award ceremonies, product launches, national events. I anchor the program with authority and warmth, keeping energy alive from start to finish.</div></div>
    <div class="offer-item"><div class="offer-number">02</div><div class="offer-title">Stage & Show Direction</div><div class="offer-desc">Coordinating production, technical, and talent teams is second nature. I ensure the vision translates seamlessly from rehearsal to the live moment.</div></div>
    <div class="offer-item"><div class="offer-number">03</div><div class="offer-title">Live Audience Engagement</div><div class="offer-desc">I turn passive audiences into active participants, creating shared energy that defines memorable events and leaves lasting impressions.</div></div>
    <div class="offer-item"><div class="offer-number">04</div><div class="offer-title">Content & Script Development</div><div class="offer-desc">I collaborate on run-of-show scripting, segment flow, and on-stage messaging that serves the event's purpose and brand identity.</div></div>
    <div class="offer-item"><div class="offer-number">05</div><div class="offer-title">Media & Brand Activation</div><div class="offer-desc">Deep roots in music programming and artist relations, I help brands connect to cultural moments through curated content and strategic partnerships.</div></div>
    <div class="offer-item"><div class="offer-number">06</div><div class="offer-title">Crisis-Calm Leadership</div><div class="offer-desc">Live broadcasting teaches that nothing goes exactly to plan. I stay composed, pivot gracefully, and protect the audience experience no matter what.</div></div>
  </div>
</section>

<!-- BOXING -->
<section class="boxing-section reveal" style="margin-top:80px">
  <div class="boxing-card">
    <div>
      <p class="section-label" style="margin-bottom:20px">Featured Event · April 18, 2026</p>
      <div style="display:flex;align-items:center;gap:15px;margin-bottom:24px">
        <img src="SaudiBoxing.png" alt="Saudi Boxing Federation Logo" style="width:50px;mix-blend-mode:screen">
        <div style="padding:6px 16px;border:1px solid rgba(201,168,76,0.3);font-size:10px;letter-spacing:0.2em;text-transform:uppercase;color:var(--gold)">Saudi Boxing Federation</div>
      </div>
      <h3 style="font-family:'Cormorant Garamond',serif;font-size:clamp(24px,3vw,40px);font-weight:300;line-height:1.15;margin-bottom:20px">
        Western & Southern Region<br><em style="color:var(--gold)">Boxing Championship</em>
      </h3>
      <p style="font-size:14px;color:var(--warm-gray);line-height:1.85;margin-bottom:20px">
        Official MC for the <strong style="color:var(--off-white)">Saudi Boxing Federation Championship</strong> — 
        Western & Southern Region, Men's and Women's age-group categories. 
        Organized under the Saudi Ministry of Sport, Jeddah 2026.
      </p>
      <div style="display:flex;flex-wrap:wrap;gap:10px;margin-top:8px">
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🥊 Men's Categories</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🥊 Women's Categories</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">🇸🇦 Ministry of Sport</span>
        <span style="padding:6px 14px;border:1px solid rgba(201,168,76,0.2);font-size:11px;color:rgba(201,168,76,0.7);letter-spacing:0.1em">📍 Jeddah</span>
      </div>
    </div>
    <div class="boxing-photos">
      <div class="boxing-photo"><div class="img-slot" style="width:100%;height:100%"><img src="Boxing1.jpg" alt="Boxing Event"></div></div>
      <div class="boxing-photo"><div class="img-slot" style="width:100%;height:100%"><img src="Boxing2.jpg" alt="Boxing Event"></div></div>
    </div>
  </div>
</section>

<!-- QUOTE -->
<section class="quote-section reveal">
  <p class="quote-text">"The stage doesn't make the host. The host makes the stage."</p>
  <p class="quote-source">A guiding principle</p>
</section>

<!-- GALLERY -->
<section id="projects" class="gallery-section reveal">
  <p class="section-label">Behind the Mic</p>
  <h2 class="section-heading" style="max-width:500px">Moments that <em>define the craft</em></h2>
  <p style="font-size:10px;letter-spacing:0.3em;text-transform:uppercase;color:var(--warm-gray);margin-top:48px;margin-bottom:12px">Mix FM Radio مكس إف إم</p>
  <div class="gallery-grid-2x2">
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="Indieshow1.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="MIXPM.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="SahSeh.jpg" alt="Mix FM Radio"></div></div>
    <div class="gallery-cell"><div class="img-slot" style="width:100%;height:100%"><img src="KickOFF.jpg" alt="Mix FM Radio"></div></div>
  </div>
  <p style="font-size:10px;letter-spacing:0.3em;text-transform:uppercase;color:var(--warm-gray);margin-top:32px;margin-bottom:12px">Radio Studio & Live Events</p>
  <div class="wide-strip">
    <div class="wide-cell"><div class="img-slot" style="width:100%;height:100%"><img src="Studio.jpg" alt="Radio Studio Mix FM"></div></div>
    <div class="wide-cell"><div class="img-slot" style="width:100%;height:100%"><img src="SwissMC.jpg" alt="Live Event Stage"></div></div>
  </div>
</section>

<!-- PARTNERS -->
<section class="partners-section reveal">
  <p class="section-label">Success Partners</p>
  <h2 class="section-heading">Brands I've <em>Collaborated</em> With</h2>
  <div class="partners-grid">
    <div class="partner-item"><img src="Mix Logo.png" alt="Mix FM"><span>Mix FM مكس</span></div>
    <div class="partner-item"><img src="GCAM.png" alt="GCAM"><span>GCAM الهيئة العامة لتنظيم الإعلام</span></div>
    <div class="partner-item"><img src="ABC.png" alt="ABC NEWS"><span>ABC NEWS Washington DC - Jeddah</span></div>
    <div class="partner-item"><img src="TheWhiteHouse.png" alt="The White House 2022"><span>The White House - PRESS CORPS JULY 2022</span></div>
    <div class="partner-item"><img src="MDLbeast.png" alt="MDL Beast"><span>MDL Beast SS21 & SS22</span></div>
    <div class="partner-item"><img src="Sela.png" alt="Sela"><span>Sela صلة</span></div>
    <div class="partner-item"><img src="RiyadhSeason 2022.png" alt="Riyadh Season 2022"><span>Riyadh Season 2022 موسم الرياض</span></div>
    <div class="partner-item"><img src="RUH BLVD Ramadan.png" alt="RUH BLVD"><span>Boulevard Riyadh City - Ramadan 2025</span></div>
    <div class="partner-item"><img src="CITYWALK.png" alt="City Walk Jeddah 2022"><span>City Walk Jeddah 2022</span></div>
    <div class="partner-item"><img src="JeddahPromenade.png" alt="Jeddah Promenade"><span>Jeddah Promenade 2025 يوم التأسيس</span></div>
    <div class="partner-item"><img src="F1JED22.png" alt="F1 Jeddah 2022"><span>FORMULA 1 STC SAUDI ARABIAN GRAND PRIX 2022</span></div>
    <div class="partner-item"><img src="Aroya.png" alt="Aroya Cruise"><span>Aroya Cruise أرويا كروز</span></div>
    <div class="partner-item"><img src="Emirates.png" alt="Emirates"><span>Emirates طيران الإمارات</span></div>
    <div class="partner-item"><img src="DUBAI.png" alt="Dubai Tourism"><span>Department of Economy & Tourism - DUBAI</span></div>
    <div class="partner-item"><img src="Geneva.png" alt="Geneva Tourism"><span>Geneva all season campaign 2026</span></div>
    <div class="partner-item"><img src="McDonaldKSA.png" alt="McDonald's KSA"><span>McDonald's KSA</span></div>
    <div class="partner-item"><img src="DunkingAR.png" alt="Dunkin Saudi"><span>Dunkin Saudi</span></div>
    <div class="partner-item"><img src="McCafeKSA.jpg" alt="McCafe KSA"><span>McCafe KSA</span></div>
    <div class="partner-item"><img src="AlmaneHSP.png" alt="Almane Hospital"><span>Almane Hospital مجموعة مستشفيات المانع</span></div>
    <div class="partner-item"><img src="Boost Jeddah.png" alt="Boost Jeddah"><span>Boost Jeddah بووست</span></div>
    <div class="partner-item"><img src="diriyah season.png" alt="Diriyah Season 2022"><span>Basketball 3X3 2022 موسم الدرعية</span></div>
    <div class="partner-item"><img src="SaudiInfra.png" alt="Saudi Infrastructure"><span>Saudi Infrastructure Expo 2025</span></div>
    <div class="partner-item"><img src="SaudiMaritime.png" alt="Saudi Maritime"><span>Saudi Maritime & Logistics Congress 2024</span></div>
    <div class="partner-item"><img src="big5.png" alt="The Big 5"><span>The Big 5 Construct Saudi 2025</span></div>
    <div class="partner-item"><img src="IHF.png" alt="IHF"><span>IHF - International Hardware Fair Saudi</span></div>
    <div class="partner-item"><img src="FSB.png" alt="FSB Sports"><span>FSB Sports Show Riyadh 2025</span></div>
    <div class="partner-item"><img src="OSN.png" alt="OSN PLUS"><span>OSN+ 2023</span></div>
    <div class="partner-item"><img src="disneyplus.png" alt="Disney+"><span>Disney+ 1 year Anniversary campaign 2023</span></div>
    <div class="partner-item"><img src="FIFAJED.png" alt="FIFA Club World Cup Saudi 2023"><span>FIFA Club World Cup Saudi Arabia 2023™</span></div>
    <div class="partner-item"><img src="AFC.png" alt="AFC Jeddah 2026"><span>The AFC Champions League Elite Finals Jeddah 2026</span></div>
    <div class="partner-item"><img src="Supercopa de Espana.png" alt="Supercopa de Espana 2026"><span>Supercopa de Espana 2026 - Jeddah</span></div>
    <div class="partner-item"><img src="SaudiBoxing.png" alt="Saudi Boxing"><span>بطولة المنطقة الغربية والجنوبية نخبة رجال وسيدات 2026</span></div>
    <div class="partner-item"><img src="SaudiBoxing.png" alt="Saudi Boxing"><span>بطولة المنطقة الغربية والجنوبية فئات سنية رجال وسيدات 2026</span></div>
  </div>
</section>

<!-- BOTTOM -->
<div class="bottom-section">
  <div class="lang-section reveal">
    <p class="section-label">Languages</p>
    <h3 class="section-heading" style="font-size:36px;margin-bottom:40px">I speak to <em>every room</em></h3>
    <div class="lang-item">
      <div><div class="lang-name">Arabic</div><div class="lang-level">Native</div></div>
      <div class="lang-bar"><div class="lang-bar-fill" style="width:100%"></div></div>
    </div>
    <div class="lang-item">
      <div><div class="lang-name">English</div><div class="lang-level">Professional</div></div>
      <div class="lang-bar"><div class="lang-bar-fill" style="width:85%"></div></div>
    </div>
  </div>
  <div class="cta-section reveal">
    <p class="section-label">Let's Work Together</p>
    <h3 class="cta-heading">Your next event deserves a host who <em>owns the stage</em>.</h3>
    <p style="font-size:14px;color:var(--warm-gray);margin-bottom:36px;font-weight:300;line-height:1.7">Corporate conferences, national ceremonies, live entertainment. I'm ready to be the voice that makes it unforgettable.</p>
    <a href="tel:+966565624247" class="cta-btn">
      +966 5656 24247
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
    </a>
    <a href="mailto:yosif_saber@yahoo.com" class="cta-btn" style="border-color:rgba(201,168,76,0.5);color:var(--warm-gray)">yosif_saber@yahoo.com</a>
    <a href="https://www.linkedin.com/in/yousef-marghalani-94442742" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">LinkedIn</a>
    <a href="https://www.instagram.com/yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">Instagram</a>
    <a href="https://www.tiktok.com/@yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">TikTok</a>
    <a href="https://x.com/yosefbinaziz" target="_blank" class="cta-btn" style="border-color:rgba(201,168,76,0.3);color:var(--warm-gray)">X</a>
  </div>
</div>

<footer>
  <div class="footer-name">Yousef Saber A. Marghalani · Portfolio</div>
  <nav class="footer-nav">
    <a href="#experience">Experience</a>
    <a href="#projects">Projects</a>
  </nav>
</footer>

<script>
  /* ── CURSOR — zero-lag dot, smooth ring ── */
  const cursor = document.getElementById('cursor');
  const ring   = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  /* Dot: instant, uses transform (no layout thrash) */
  document.addEventListener('mousemove', e => {
    mx = e.clientX;
    my = e.clientY;
    cursor.style.transform = `translate(${mx - 5}px, ${my - 5}px)`;
  }, { passive: true });

  /* Ring: lerp on rAF — 0.18 is snappy but still smooth */
  (function animRing() {
    rx += (mx - rx - 18) * 0.18;
    ry += (my - ry - 18) * 0.18;
    ring.style.transform = `translate(${rx}px, ${ry}px)`;
    requestAnimationFrame(animRing);
  })();

  /* Hover states: only resize ring, don't touch transform */
  document.querySelectorAll('a, button, .trait-card, .offer-item, .stat-item, .img-slot, .partner-item').forEach(el => {
    el.addEventListener('mouseenter', () => {
      ring.style.width  = '52px';
      ring.style.height = '52px';
      ring.style.borderColor = 'var(--gold-light)';
      ring.style.opacity = '0.9';
    });
    el.addEventListener('mouseleave', () => {
      ring.style.width  = '36px';
      ring.style.height = '36px';
      ring.style.borderColor = 'var(--gold)';
      ring.style.opacity = '0.6';
    });
  });

  /* ── SCROLL REVEAL ── */
  const revealObs = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) setTimeout(() => e.target.classList.add('visible'), i * 80);
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => revealObs.observe(el));

  /* ── COUNTERS ── */
  function animCount(el, target, suffix) {
    let current = 0;
    const step = target / 60;
    const timer = setInterval(() => {
      current += step;
      if (current >= target) {
        el.textContent = target + suffix;
        clearInterval(timer);
      } else {
        el.textContent = Math.floor(current) + suffix;
      }
    }, 20);
  }

  const counterObs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        animCount(document.getElementById('cnt1'), 7, '+');
        animCount(document.getElementById('cnt2'), 14, '');
        animCount(document.getElementById('cnt3'), 3, '');
        counterObs.unobserve(e.target);
      }
    });
  }, { threshold: 0.5 });

  const strip = document.querySelector('.stats-strip');
  if (strip) counterObs.observe(strip);
</script>
</body>
