<!DOCTYPE html>
<html lang="he" dir="rtl" id="root">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SHARE-PEN — Campaign Navigator</title>
  <link href="https://fonts.googleapis.com/css2?family=Frank+Ruhl+Libre:wght@400;700;900&family=Playfair+Display:wght@400;700;900&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    *{box-sizing:border-box;margin:0;padding:0}
    body{background:#0a0a0a;color:#F5F0E8;font-family:'Inter',sans-serif;min-height:100vh;transition:direction 0.1s}
    /* Lang Bar */
    #lang-bar{background:rgba(201,168,76,0.06);border-bottom:1px solid rgba(201,168,76,0.15);padding:0.5rem 2rem;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:0.5rem;direction:ltr}
    #lang-bar span{font-size:0.75rem;color:#8A8278}
    .lang-btns{display:flex;gap:0.5rem;flex-wrap:wrap}
    .lang-btn{background:transparent;border:1px solid rgba(201,168,76,0.25);color:#8A8278;padding:0.25rem 0.65rem;border-radius:20px;cursor:pointer;font-size:0.72rem;transition:all 0.2s;font-family:'Inter',sans-serif}
    .lang-btn:hover,.lang-btn.active{background:rgba(201,168,76,0.15);border-color:#C9A84C;color:#C9A84C}
    /* Header */
    header{background:#0D0D0D;border-bottom:1px solid rgba(201,168,76,0.2);padding:2rem 3rem;display:flex;align-items:center;justify-content:space-between}
    .logo{font-family:'Playfair Display',serif;font-size:1.8rem;font-weight:900;color:#C9A84C;letter-spacing:0.1em;direction:ltr}
    .logo-sub{font-size:0.75rem;color:#8A8278;margin-top:0.2rem;letter-spacing:0.3em}
    .header-meta{font-size:0.8rem;color:#8A8278;text-align:left;direction:ltr}
    /* Hero */
    .hero{padding:4rem 3rem 2rem;text-align:center}
    .hero h1{font-family:'Frank Ruhl Libre',serif;font-size:clamp(2rem,5vw,4rem);font-weight:900;margin-bottom:1rem}
    .hero p{color:#8A8278;font-size:1.1rem;max-width:640px;margin:0 auto}
    /* Cards Grid */
    .sections{padding:3rem;display:grid;grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:2rem;max-width:1400px;margin:0 auto}
    .section-card{background:#111;border:1px solid rgba(255,255,255,0.07);border-radius:8px;overflow:hidden;transition:all 0.3s}
    .section-card:hover{border-color:rgba(201,168,76,0.4);transform:translateY(-4px)}
    .card-header{padding:1.5rem;border-bottom:1px solid rgba(255,255,255,0.06);display:flex;align-items:center;gap:1rem}
    .card-icon{width:48px;height:48px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:1.4rem;flex-shrink:0}
    .card-title{font-family:'Frank Ruhl Libre',serif;font-size:1.2rem;font-weight:700}
    .card-desc{font-size:0.8rem;color:#8A8278;margin-top:0.2rem}
    .card-links{padding:1rem 1.5rem;display:flex;flex-direction:column;gap:0.5rem}
    .link-item{display:flex;align-items:center;justify-content:space-between;padding:0.7rem 1rem;background:rgba(255,255,255,0.03);border-radius:6px;text-decoration:none;color:#F5F0E8;font-size:0.9rem;transition:all 0.2s;border:1px solid transparent}
    .link-item:hover{background:rgba(201,168,76,0.08);border-color:rgba(201,168,76,0.3);color:#C9A84C}
    .link-badge{font-size:0.65rem;padding:0.2rem 0.5rem;border-radius:10px;font-weight:600;white-space:nowrap}
    .badge-live{background:rgba(76,175,80,0.2);color:#4CAF50}
    .badge-video{background:rgba(201,168,76,0.2);color:#C9A84C}
    .badge-doc{background:rgba(100,100,255,0.2);color:#8888ff}
    .badge-social{background:rgba(255,100,100,0.2);color:#ff8888}
    .arrow{opacity:0.4;font-size:0.8rem}
    /* Stats */
    .stats-bar{background:#111;border-top:1px solid rgba(255,255,255,0.05);padding:2rem 3rem;display:grid;grid-template-columns:repeat(4,1fr);gap:2rem;text-align:center}
    .stat-n{font-family:'Playfair Display',serif;font-size:2rem;font-weight:900;color:#C9A84C}
    .stat-l{font-size:0.8rem;color:#8A8278;margin-top:0.3rem}
    /* Responsive */
    @media(max-width:768px){.sections{padding:1rem;grid-template-columns:1fr}.stats-bar{grid-template-columns:repeat(2,1fr)}.hero{padding:2rem 1rem}header{padding:1.5rem}}
  </style>
</head>
<body>

<!-- ══ LANG BAR ══ -->
<div id="lang-bar">
  <span>🌍</span>
  <div class="lang-btns">
    <button class="lang-btn active" onclick="setLang('he')">🇮🇱 עברית</button>
    <button class="lang-btn" onclick="setLang('en')">🇺🇸 English</button>
    <button class="lang-btn" onclick="setLang('ar')">🇸🇦 العربية</button>
    <button class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button>
    <button class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button>
    <button class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button>
  </div>
</div>

<header>
  <div>
    <div class="logo">SHARE-PEN</div>
    <div class="logo-sub" data-i18n="nav-sub">CAMPAIGN NAVIGATOR</div>
  </div>
  <div class="header-meta">
    <div style="color:#C9A84C;font-weight:600">share-pen.com</div>
    <div data-i18n="nav-pkg">Campaign Package 2024</div>
  </div>
</header>

<div class="hero">
  <h1><span data-i18n="hero-h1">כל חומרי הקמפיין</span> <span style="color:#C9A84C" data-i18n="hero-h1-span">במקום אחד</span></h1>
  <p data-i18n="hero-p">דפי נחיתה · סרטונים · מצגות · סושיאל מדיה · מיתוג — הכל כאן</p>
</div>

<div class="sections">

  <!-- LANDING PAGES -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(201,168,76,0.1)">🌐</div>
      <div>
        <div class="card-title" data-i18n="s1-title">דפי נחיתה</div>
        <div class="card-desc" data-i18n="s1-desc">3 דפים מלאים, RTL עברי, responsive</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../landing-pages/index.html" class="link-item" target="_blank">
        <span data-i18n="lp-home">🏠 דף ראשי — share-pen.com</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/en/index.html" class="link-item" target="_blank">
        <span>🇺🇸 English — share-pen.com</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/ar/index.html" class="link-item" target="_blank">
        <span>🇸🇦 العربية — share-pen.com</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/es/index.html" class="link-item" target="_blank">
        <span>🇪🇸 Español — share-pen.com</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/fr/index.html" class="link-item" target="_blank">
        <span>🇫🇷 Français — share-pen.com</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/writers.html" class="link-item" target="_blank">
        <span data-i18n="lp-writers">✍️ לכותבים — Writers</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
      <a href="../landing-pages/readers.html" class="link-item" target="_blank">
        <span data-i18n="lp-readers">📖 לקוראים — Readers</span>
        <span><span class="link-badge badge-live">LIVE READY</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- VIDEOS -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(255,100,100,0.1)">🎬</div>
      <div>
        <div class="card-title" data-i18n="s2-title">סרטונים מונפשים</div>
        <div class="card-desc" data-i18n="s2-desc">4 סרטוני kinetic typography — מתנגנים בדפדפן</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../videos/film-01-the-heist/video.html" class="link-item" target="_blank">
        <span>🎭 Film 01 — The Heist</span>
        <span><span class="link-badge badge-video" data-i18n="dur-90s">90 שניות</span> <span class="arrow">←</span></span>
      </a>
      <a href="../videos/film-02-process/video.html" class="link-item" target="_blank">
        <span>📹 Film 02 — Process is Product</span>
        <span><span class="link-badge badge-video" data-i18n="dur-60s">60 שניות</span> <span class="arrow">←</span></span>
      </a>
      <a href="../videos/film-03-the-letter/video.html" class="link-item" target="_blank">
        <span>✉️ Film 03 — The Letter</span>
        <span><span class="link-badge badge-video" data-i18n="dur-45s">45 שניות</span> <span class="arrow">←</span></span>
      </a>
      <a href="../videos/film-04-manifesto/video.html" class="link-item" target="_blank">
        <span>🔥 Film 04 — The Manifesto</span>
        <span><span class="link-badge badge-video" data-i18n="dur-2m">2 דקות</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- PRESENTATIONS -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(100,100,255,0.1)">📊</div>
      <div>
        <div class="card-title" data-i18n="s3-title">מצגות</div>
        <div class="card-desc" data-i18n="s3-desc">ניווט עם חצי מקלדת ← →</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../videos/presentations/investor-deck.html" class="link-item" target="_blank">
        <span>💼 Investor & Partner Deck</span>
        <span><span class="link-badge badge-doc" data-i18n="slides-12">12 שקופיות</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- INSTAGRAM -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(255,100,150,0.1)">📸</div>
      <div>
        <div class="card-title">Instagram</div>
        <div class="card-desc" data-i18n="s4-desc">90 יום תוכן + 5 Reels מונפשים (6 שפות)</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../social-media/instagram/90-day-content-calendar.md" class="link-item" target="_blank">
        <span data-i18n="ig-cal">📅 לוח תוכן 90 ימים</span>
        <span><span class="link-badge badge-social" data-i18n="ig-posts">90 פוסטים</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-01-revolution.html" class="link-item" target="_blank">
        <span>🖼 Post 01 — The Revolution</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-02-night-writer.html" class="link-item" target="_blank">
        <span>🌙 Post 02 — Night Writer</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-03-stats-carousel.html" class="link-item" target="_blank">
        <span>📊 Post 03 — Stats Carousel</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-04-manifesto-quote.html" class="link-item" target="_blank">
        <span>📜 Post 04 — Manifesto Quote</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-05-success-story.html" class="link-item" target="_blank">
        <span>⭐ Post 05 — Success Story</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-06-writing-tip.html" class="link-item" target="_blank">
        <span>💡 Post 06 — Writing Tip</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/posts/post-07-cta-final.html" class="link-item" target="_blank">
        <span>🚀 Post 07 — Final CTA</span>
        <span><span class="link-badge badge-social">Post</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/reels/reel-01-the-math.html" class="link-item" target="_blank">
        <span>🎬 Reel 01 — The Math (8% vs 100%)</span>
        <span><span class="link-badge badge-video" data-i18n="animated">מונפש</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/reels/reel-02-rejection-to-freedom.html" class="link-item" target="_blank">
        <span>🎬 Reel 02 — Rejection to Freedom</span>
        <span><span class="link-badge badge-video" data-i18n="animated">מונפש</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/reels/reel-03-book-reveal.html" class="link-item" target="_blank">
        <span>🎬 Reel 03 — Book Cover Reveal</span>
        <span><span class="link-badge badge-video" data-i18n="animated">מונפש</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/reels/reel-04-manifesto.html" class="link-item" target="_blank">
        <span>🎬 Reel 04 — The Manifesto</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/instagram/reels/reel-05-writer-challenge.html" class="link-item" target="_blank">
        <span>🎬 Reel 05 — Writer Challenge</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- TIKTOK -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(0,200,200,0.1)">🎵</div>
      <div>
        <div class="card-title">TikTok</div>
        <div class="card-desc" data-i18n="s5-desc">10 סרטונים מונפשים — 6 שפות לכל סרטון</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../social-media/tiktok/videos/tiktok-01-pov-rejected.html" class="link-item" target="_blank">
        <span>🎬 01 — POV: Publisher Rejected You</span>
        <span><span class="link-badge badge-video">30s</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-02-8-percent.html" class="link-item" target="_blank">
        <span>🎬 02 — 8% vs 100%</span>
        <span><span class="link-badge badge-video">15s</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-03-first-month.html" class="link-item" target="_blank">
        <span>🎬 03 — My First Month</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-04-stitch.html" class="link-item" target="_blank">
        <span>🎬 04 — Stitch This</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-05-grwm.html" class="link-item" target="_blank">
        <span>🎬 05 — GRWM Writing Edition</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-06-publishers.html" class="link-item" target="_blank">
        <span>🎬 06 — Publishers Won't Tell You</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-07-bookstagram-vs-booktok.html" class="link-item" target="_blank">
        <span>🎬 07 — Bookstagram vs BookTok</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-08-rejection-letters.html" class="link-item" target="_blank">
        <span>🎬 08 — 50 Rejection Letters</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-09-day-in-life.html" class="link-item" target="_blank">
        <span>🎬 09 — Author Day in Life</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <a href="../social-media/tiktok/videos/tiktok-10-cover-reveal.html" class="link-item" target="_blank">
        <span>🎬 10 — Book Cover Reveal</span>
        <span><span class="link-badge badge-video">6 <span data-i18n="langs">שפות</span> ✦</span> <span class="arrow">←</span></span>
      </a>
      <div style="padding:0.5rem 0;border-top:1px solid rgba(255,255,255,0.05);margin-top:0.5rem">
        <div style="font-size:0.72rem;color:#8A8278;margin-bottom:0.5rem" data-i18n="tt-by-lang">גרסאות לפי שפה:</div>
        <div style="display:flex;gap:0.4rem;flex-wrap:wrap">
          <a href="../social-media/tiktok/videos/he/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇮🇱 עב׳</a>
          <a href="../social-media/tiktok/videos/en/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇺🇸 EN</a>
          <a href="../social-media/tiktok/videos/ar/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇸🇦 AR</a>
          <a href="../social-media/tiktok/videos/es/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇪🇸 ES</a>
          <a href="../social-media/tiktok/videos/ru/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇷🇺 RU</a>
          <a href="../social-media/tiktok/videos/pt/" style="font-size:0.7rem;background:rgba(201,168,76,0.1);border:1px solid rgba(201,168,76,0.3);color:#C9A84C;padding:0.2rem 0.5rem;border-radius:4px;text-decoration:none" target="_blank">🇧🇷 PT</a>
        </div>
      </div>
      <a href="../social-media/tiktok/tiktok-scripts.md" class="link-item" target="_blank">
        <span data-i18n="tt-scripts">📄 סקריפטים מקוריים</span>
        <span><span class="link-badge badge-social">10 scripts</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- FACEBOOK -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(100,100,255,0.1)">👥</div>
      <div>
        <div class="card-title">Facebook</div>
        <div class="card-desc" data-i18n="s6-desc">פוסטים + Groups + Ads מוכנות</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../social-media/facebook/facebook-strategy.md" class="link-item" target="_blank">
        <span data-i18n="fb-link">📢 אסטרטגיה + מודעות</span>
        <span><span class="link-badge badge-social">5 ads</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- TWITTER -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(100,180,255,0.1)">🐦</div>
      <div>
        <div class="card-title">Twitter / X</div>
        <div class="card-desc" data-i18n="s7-desc">Threads ויראליים + tweets מוכנים</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../social-media/twitter/twitter-strategy.md" class="link-item" target="_blank">
        <span data-i18n="tw-link">🧵 Threads + Viral Tweets</span>
        <span><span class="link-badge badge-social">3 threads</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

  <!-- BRAND -->
  <div class="section-card">
    <div class="card-header">
      <div class="card-icon" style="background:rgba(201,168,76,0.1)">🎨</div>
      <div>
        <div class="card-title" data-i18n="s8-title">מיתוג ומניפסט</div>
        <div class="card-desc" data-i18n="s8-desc">Brand guide + מניפסט מודפס</div>
      </div>
    </div>
    <div class="card-links">
      <a href="../brand/brand-guide.md" class="link-item" target="_blank">
        <span data-i18n="brand-guide">📐 Brand Guide מלא</span>
        <span><span class="link-badge badge-doc" data-i18n="guide">מדריך</span> <span class="arrow">←</span></span>
      </a>
      <a href="../brand/manifesto-print.html" class="link-item" target="_blank">
        <span data-i18n="manifesto">📜 מניפסט — A4 / PDF</span>
        <span><span class="link-badge badge-live">PRINT READY</span> <span class="arrow">←</span></span>
      </a>
    </div>
  </div>

</div>

<div class="stats-bar">
  <div><div class="stat-n">60+</div><div class="stat-l" data-i18n="stat1">קבצים מוכנים</div></div>
  <div><div class="stat-n">19</div><div class="stat-l" data-i18n="stat2">סרטונים מונפשים</div></div>
  <div><div class="stat-n">6</div><div class="stat-l" data-i18n="stat3">שפות לכל סרטון</div></div>
  <div><div class="stat-n">90</div><div class="stat-l" data-i18n="stat4">ימי תוכן מוכן</div></div>
</div>

<script>
const LANGS = {
  he: {
    dir:'rtl', lang:'he',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'Campaign Package 2024',
    'hero-h1':'כל חומרי הקמפיין',
    'hero-h1-span':'במקום אחד',
    'hero-p':'דפי נחיתה · סרטונים · מצגות · סושיאל מדיה · מיתוג — הכל כאן',
    's1-title':'דפי נחיתה','s1-desc':'דפים מלאים ב-5 שפות, responsive',
    'lp-home':'🏠 דף ראשי — share-pen.com','lp-writers':'✍️ לכותבים — Writers','lp-readers':'📖 לקוראים — Readers',
    's2-title':'סרטונים מונפשים','s2-desc':'4 סרטוני kinetic typography — מתנגנים בדפדפן',
    'dur-90s':'90 שניות','dur-60s':'60 שניות','dur-45s':'45 שניות','dur-2m':'2 דקות',
    's3-title':'מצגות','s3-desc':'ניווט עם חצי מקלדת ← →','slides-12':'12 שקופיות',
    's4-desc':'90 יום תוכן + 5 Reels מונפשים (6 שפות)',
    'ig-cal':'📅 לוח תוכן 90 ימים','ig-posts':'90 פוסטים','animated':'מונפש','langs':'שפות',
    's5-desc':'10 סרטונים מונפשים — 6 שפות לכל סרטון',
    'tt-by-lang':'גרסאות לפי שפה:','tt-scripts':'📄 סקריפטים מקוריים',
    's6-desc':'פוסטים + Groups + Ads מוכנות','fb-link':'📢 אסטרטגיה + מודעות',
    's7-desc':'Threads ויראליים + tweets מוכנים','tw-link':'🧵 Threads + Viral Tweets',
    's8-title':'מיתוג ומניפסט','s8-desc':'Brand guide + מניפסט מודפס',
    'brand-guide':'📐 Brand Guide מלא','guide':'מדריך','manifesto':'📜 מניפסט — A4 / PDF',
    'stat1':'קבצים מוכנים','stat2':'סרטונים מונפשים','stat3':'שפות לכל סרטון','stat4':'ימי תוכן מוכן'
  },
  en: {
    dir:'ltr', lang:'en',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'Campaign Package 2024',
    'hero-h1':'All Campaign Materials',
    'hero-h1-span':'in One Place',
    'hero-p':'Landing pages · Videos · Presentations · Social media · Branding — all here',
    's1-title':'Landing Pages','s1-desc':'Full pages in 5 languages, responsive',
    'lp-home':'🏠 Main page — share-pen.com','lp-writers':'✍️ For Writers','lp-readers':'📖 For Readers',
    's2-title':'Animated Videos','s2-desc':'4 kinetic typography films — play in browser',
    'dur-90s':'90 sec','dur-60s':'60 sec','dur-45s':'45 sec','dur-2m':'2 min',
    's3-title':'Presentations','s3-desc':'Navigate with ← → keyboard arrows','slides-12':'12 slides',
    's4-desc':'90 days content + 5 animated Reels (6 languages)',
    'ig-cal':'📅 90-Day Content Calendar','ig-posts':'90 posts','animated':'Animated','langs':'langs',
    's5-desc':'10 animated videos — 6 languages each',
    'tt-by-lang':'Versions by language:','tt-scripts':'📄 Original Scripts',
    's6-desc':'Posts + Groups + Ready Ads','fb-link':'📢 Strategy + Ads',
    's7-desc':'Viral Threads + ready tweets','tw-link':'🧵 Threads + Viral Tweets',
    's8-title':'Branding & Manifesto','s8-desc':'Brand guide + print-ready manifesto',
    'brand-guide':'📐 Full Brand Guide','guide':'Guide','manifesto':'📜 Manifesto — A4 / PDF',
    'stat1':'Ready files','stat2':'Animated videos','stat3':'Languages per video','stat4':'Days of content'
  },
  ar: {
    dir:'rtl', lang:'ar',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'حزمة الحملة 2024',
    'hero-h1':'جميع مواد الحملة',
    'hero-h1-span':'في مكان واحد',
    'hero-p':'صفحات الهبوط · مقاطع الفيديو · عروض تقديمية · سوشيال ميديا · علامة تجارية — كل شيء هنا',
    's1-title':'صفحات الهبوط','s1-desc':'صفحات كاملة بـ 5 لغات، متجاوبة',
    'lp-home':'🏠 الصفحة الرئيسية','lp-writers':'✍️ للكتّاب','lp-readers':'📖 للقراء',
    's2-title':'مقاطع فيديو متحركة','s2-desc':'4 أفلام kinetic typography — تشتغل في المتصفح',
    'dur-90s':'90 ثانية','dur-60s':'60 ثانية','dur-45s':'45 ثانية','dur-2m':'دقيقتان',
    's3-title':'عروض تقديمية','s3-desc':'التنقل بأسهم لوحة المفاتيح ← →','slides-12':'12 شريحة',
    's4-desc':'محتوى 90 يوم + 5 Reels متحركة (6 لغات)',
    'ig-cal':'📅 تقويم محتوى 90 يوم','ig-posts':'90 منشور','animated':'متحرك','langs':'لغات',
    's5-desc':'10 مقاطع متحركة — 6 لغات لكل مقطع',
    'tt-by-lang':'نسخ حسب اللغة:','tt-scripts':'📄 السكريبتات الأصلية',
    's6-desc':'منشورات + مجموعات + إعلانات جاهزة','fb-link':'📢 الاستراتيجية + الإعلانات',
    's7-desc':'خيوط فيروسية + تغريدات جاهزة','tw-link':'🧵 خيوط + تغريدات فيروسية',
    's8-title':'العلامة التجارية والبيان','s8-desc':'دليل العلامة التجارية + بيان للطباعة',
    'brand-guide':'📐 دليل العلامة التجارية الكامل','guide':'دليل','manifesto':'📜 البيان — A4 / PDF',
    'stat1':'ملفات جاهزة','stat2':'فيديوهات متحركة','stat3':'لغات لكل فيديو','stat4':'أيام من المحتوى'
  },
  es: {
    dir:'ltr', lang:'es',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'Paquete de Campaña 2024',
    'hero-h1':'Todos los materiales de campaña',
    'hero-h1-span':'en un solo lugar',
    'hero-p':'Landing pages · Videos · Presentaciones · Redes sociales · Branding — todo aquí',
    's1-title':'Páginas de destino','s1-desc':'Páginas completas en 5 idiomas, responsive',
    'lp-home':'🏠 Página principal','lp-writers':'✍️ Para escritores','lp-readers':'📖 Para lectores',
    's2-title':'Videos animados','s2-desc':'4 films kinetic typography — se reproducen en el navegador',
    'dur-90s':'90 seg','dur-60s':'60 seg','dur-45s':'45 seg','dur-2m':'2 min',
    's3-title':'Presentaciones','s3-desc':'Navegar con flechas ← → del teclado','slides-12':'12 diapositivas',
    's4-desc':'90 días de contenido + 5 Reels animados (6 idiomas)',
    'ig-cal':'📅 Calendario de contenido 90 días','ig-posts':'90 publicaciones','animated':'Animado','langs':'idiomas',
    's5-desc':'10 videos animados — 6 idiomas por video',
    'tt-by-lang':'Versiones por idioma:','tt-scripts':'📄 Scripts originales',
    's6-desc':'Publicaciones + Grupos + Anuncios listos','fb-link':'📢 Estrategia + Anuncios',
    's7-desc':'Hilos virales + tweets listos','tw-link':'🧵 Hilos + Tweets virales',
    's8-title':'Marca y Manifiesto','s8-desc':'Guía de marca + manifiesto para imprimir',
    'brand-guide':'📐 Guía de marca completa','guide':'Guía','manifesto':'📜 Manifiesto — A4 / PDF',
    'stat1':'Archivos listos','stat2':'Videos animados','stat3':'Idiomas por video','stat4':'Días de contenido'
  },
  ru: {
    dir:'ltr', lang:'ru',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'Пакет кампании 2024',
    'hero-h1':'Все материалы кампании',
    'hero-h1-span':'в одном месте',
    'hero-p':'Лендинги · Видео · Презентации · Соцсети · Брендинг — всё здесь',
    's1-title':'Лендинги','s1-desc':'Полные страницы на 5 языках, адаптивные',
    'lp-home':'🏠 Главная страница','lp-writers':'✍️ Для писателей','lp-readers':'📖 Для читателей',
    's2-title':'Анимационные видео','s2-desc':'4 кинетических film-типографических видео — работают в браузере',
    'dur-90s':'90 сек','dur-60s':'60 сек','dur-45s':'45 сек','dur-2m':'2 мин',
    's3-title':'Презентации','s3-desc':'Навигация стрелками ← → клавиатуры','slides-12':'12 слайдов',
    's4-desc':'90 дней контента + 5 анимированных Reels (6 языков)',
    'ig-cal':'📅 Контент-план 90 дней','ig-posts':'90 постов','animated':'Анимированный','langs':'языка',
    's5-desc':'10 анимированных видео — 6 языков для каждого',
    'tt-by-lang':'Версии по языкам:','tt-scripts':'📄 Оригинальные сценарии',
    's6-desc':'Посты + Группы + Готовая реклама','fb-link':'📢 Стратегия + Реклама',
    's7-desc':'Вирусные треды + готовые твиты','tw-link':'🧵 Треды + Вирусные твиты',
    's8-title':'Брендинг и Манифест','s8-desc':'Руководство по бренду + манифест для печати',
    'brand-guide':'📐 Полное руководство по бренду','guide':'Руководство','manifesto':'📜 Манифест — A4 / PDF',
    'stat1':'Готовых файлов','stat2':'Анимированных видео','stat3':'Языков на видео','stat4':'Дней контента'
  },
  fr: {
    dir:'ltr', lang:'fr',
    'nav-sub':'CAMPAIGN NAVIGATOR',
    'nav-pkg':'Pack Campagne 2024',
    'hero-h1':'Tous les matériaux de campagne',
    'hero-h1-span':'en un seul endroit',
    'hero-p':'Pages d\'atterrissage · Vidéos · Présentations · Réseaux sociaux · Branding — tout ici',
    's1-title':'Pages d\'atterrissage','s1-desc':'Pages complètes en 5 langues, responsive',
    'lp-home':'🏠 Page principale','lp-writers':'✍️ Pour les auteurs','lp-readers':'📖 Pour les lecteurs',
    's2-title':'Vidéos animées','s2-desc':'4 films kinetic typography — lisibles dans le navigateur',
    'dur-90s':'90 sec','dur-60s':'60 sec','dur-45s':'45 sec','dur-2m':'2 min',
    's3-title':'Présentations','s3-desc':'Navigation avec les flèches ← → du clavier','slides-12':'12 diapositives',
    's4-desc':'90 jours de contenu + 5 Reels animés (6 langues)',
    'ig-cal':'📅 Calendrier de contenu 90 jours','ig-posts':'90 publications','animated':'Animé','langs':'langues',
    's5-desc':'10 vidéos animées — 6 langues par vidéo',
    'tt-by-lang':'Versions par langue:','tt-scripts':'📄 Scripts originaux',
    's6-desc':'Publications + Groupes + Publicités prêtes','fb-link':'📢 Stratégie + Publicités',
    's7-desc':'Fils viraux + tweets prêts','tw-link':'🧵 Fils + Tweets viraux',
    's8-title':'Marque & Manifeste','s8-desc':'Guide de marque + manifeste pour impression',
    'brand-guide':'📐 Guide de marque complet','guide':'Guide','manifesto':'📜 Manifeste — A4 / PDF',
    'stat1':'Fichiers prêts','stat2':'Vidéos animées','stat3':'Langues par vidéo','stat4':'Jours de contenu'
  }
};

function setLang(code) {
  const L = LANGS[code];
  if (!L) return;
  // Update root element direction/lang
  const root = document.getElementById('root');
  root.setAttribute('lang', L.lang);
  root.setAttribute('dir', L.dir);
  // Update all translatable elements
  document.querySelectorAll('[data-i18n]').forEach(el => {
    const key = el.getAttribute('data-i18n');
    if (L[key] !== undefined) el.textContent = L[key];
  });
  // Active button
  document.querySelectorAll('.lang-btn').forEach(b => {
    b.classList.toggle('active', b.getAttribute('onclick') === `setLang('${code}')`);
  });
}
</script>

</body>
</html>
