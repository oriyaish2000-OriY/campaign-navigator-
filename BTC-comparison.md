<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>המהפכה המקבילה — Share-Pen vs. The BTC Standard</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,400;1,600&family=Heebo:wght@300;400;500;700&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --dark:    #060408;
      --dark2:   #0e0c10;
      --dark3:   #16131a;
      --gold:    #d4a535;
      --gold-lt: #e8c060;
      --gold-dk: #a07820;
      --white:   #f0ead8;
      --muted:   #8a7f72;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--dark);
      color: var(--white);
      font-family: 'Heebo', sans-serif;
      font-weight: 300;
      line-height: 1.75;
      overflow-x: hidden;
    }

    /* ── DOT GRID ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: radial-gradient(circle, rgba(212,165,53,0.07) 1px, transparent 1px);
      background-size: 36px 36px;
      pointer-events: none;
      z-index: 0;
    }

    /* ── LAYOUT ── */
    .wrap {
      position: relative;
      z-index: 1;
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 2rem;
    }

    /* ── HEADER ── */
    header {
      position: relative;
      text-align: center;
      padding: 6rem 2rem 4rem;
      border-bottom: 1px solid rgba(212,165,53,0.18);
      overflow: hidden;
    }
    header::after {
      content: '';
      position: absolute;
      bottom: -1px;
      left: 50%;
      transform: translateX(-50%);
      width: 120px;
      height: 2px;
      background: var(--gold);
    }
    .header-label {
      font-family: 'Heebo', sans-serif;
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.35em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.4rem;
    }
    .header-title-he {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.6rem, 6vw, 4.8rem);
      font-weight: 300;
      color: var(--white);
      line-height: 1.1;
      margin-bottom: 0.4rem;
    }
    .header-title-en {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.2rem, 3vw, 1.9rem);
      font-weight: 300;
      font-style: italic;
      color: var(--gold);
      margin-bottom: 2rem;
    }
    .header-sub {
      font-size: 0.95rem;
      color: var(--muted);
      letter-spacing: 0.12em;
    }
    .vs-badge {
      display: inline-flex;
      align-items: center;
      gap: 1rem;
      background: rgba(212,165,53,0.08);
      border: 1px solid rgba(212,165,53,0.25);
      border-radius: 100px;
      padding: 0.5rem 1.8rem;
      margin-top: 2rem;
      font-family: 'Heebo', sans-serif;
      font-size: 0.85rem;
      letter-spacing: 0.12em;
    }
    .vs-badge span.vs { color: var(--gold); font-weight: 700; font-size: 1rem; }

    /* ── SECTIONS ── */
    section { padding: 5rem 0; }
    section + section { border-top: 1px solid rgba(212,165,53,0.1); }

    .section-eyebrow {
      font-size: 0.7rem;
      font-weight: 500;
      letter-spacing: 0.4em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1rem;
    }
    .section-heading {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.8rem, 4vw, 3rem);
      font-weight: 400;
      line-height: 1.15;
      color: var(--white);
      margin-bottom: 2rem;
    }
    .section-heading em { color: var(--gold); font-style: italic; }

    /* ── INTRO ── */
    .intro-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
      align-items: start;
      margin-top: 2.5rem;
    }
    @media (max-width: 720px) { .intro-grid { grid-template-columns: 1fr; } }
    .intro-body {
      font-size: 1.05rem;
      color: rgba(240,234,216,0.82);
      line-height: 1.85;
    }
    .intro-body p + p { margin-top: 1.1rem; }
    .principles-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.85rem;
    }
    .principles-list li {
      display: flex;
      align-items: flex-start;
      gap: 0.9rem;
      font-size: 0.95rem;
      color: rgba(240,234,216,0.78);
    }
    .principles-list li::before {
      content: '◆';
      color: var(--gold);
      font-size: 0.6rem;
      margin-top: 0.35rem;
      flex-shrink: 0;
    }

    /* ── COMPARISON TABLE ── */
    .table-wrap {
      overflow-x: auto;
      border-radius: 16px;
      border: 1px solid rgba(212,165,53,0.2);
      margin-top: 2.5rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.95rem;
    }
    thead tr {
      background: rgba(212,165,53,0.1);
    }
    thead th {
      padding: 1.1rem 1.4rem;
      text-align: right;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.05rem;
      font-weight: 600;
      color: var(--gold);
      letter-spacing: 0.05em;
      border-bottom: 1px solid rgba(212,165,53,0.25);
    }
    thead th:first-child { width: 22%; }
    thead th:nth-child(2),
    thead th:nth-child(3) { width: 39%; }

    tbody tr {
      border-bottom: 1px solid rgba(212,165,53,0.08);
      transition: background 0.2s;
    }
    tbody tr:last-child { border-bottom: none; }
    tbody tr:hover { background: rgba(212,165,53,0.04); }
    tbody tr:nth-child(odd) { background: rgba(255,255,255,0.015); }
    tbody tr:nth-child(odd):hover { background: rgba(212,165,53,0.06); }

    td {
      padding: 1.05rem 1.4rem;
      vertical-align: top;
      color: rgba(240,234,216,0.82);
      line-height: 1.6;
    }
    td:first-child {
      font-family: 'Heebo', sans-serif;
      font-weight: 500;
      font-size: 0.88rem;
      letter-spacing: 0.04em;
      color: var(--gold-lt);
    }
    .row-num {
      display: inline-block;
      background: rgba(212,165,53,0.15);
      color: var(--gold);
      font-size: 0.7rem;
      font-weight: 700;
      padding: 1px 6px;
      border-radius: 4px;
      margin-left: 6px;
    }

    /* ── POSITIONING STATEMENT ── */
    .pos-block {
      background: linear-gradient(135deg, rgba(212,165,53,0.08) 0%, rgba(6,4,8,0) 60%);
      border: 1px solid rgba(212,165,53,0.3);
      border-radius: 20px;
      padding: 3rem 3.5rem;
      margin-top: 2.5rem;
      position: relative;
      overflow: hidden;
    }
    .pos-block::before {
      content: '"';
      position: absolute;
      top: -1.5rem;
      right: 2rem;
      font-family: 'Cormorant Garamond', serif;
      font-size: 14rem;
      color: rgba(212,165,53,0.06);
      line-height: 1;
      pointer-events: none;
    }
    .pos-block p {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.25rem, 2.5vw, 1.75rem);
      font-weight: 400;
      font-style: italic;
      line-height: 1.65;
      color: var(--white);
    }
    .pos-block p strong { color: var(--gold); font-style: normal; font-weight: 600; }

    /* ── COMPETITOR CARDS ── */
    .comp-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 1.5rem;
      margin-top: 2.5rem;
    }
    .comp-card {
      background: var(--dark2);
      border: 1px solid rgba(212,165,53,0.15);
      border-radius: 14px;
      padding: 1.6rem;
      transition: border-color 0.25s, transform 0.25s;
    }
    .comp-card:hover {
      border-color: rgba(212,165,53,0.4);
      transform: translateY(-3px);
    }
    .comp-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.3rem;
      font-weight: 600;
      color: var(--gold);
      margin-bottom: 0.3rem;
    }
    .comp-what {
      font-size: 0.82rem;
      color: var(--muted);
      margin-bottom: 1rem;
      font-style: italic;
    }
    .comp-row {
      display: flex;
      align-items: flex-start;
      gap: 0.6rem;
      margin-bottom: 0.55rem;
      font-size: 0.88rem;
      line-height: 1.5;
    }
    .comp-label {
      font-size: 0.68rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 2px 7px;
      border-radius: 4px;
      white-space: nowrap;
      margin-top: 2px;
    }
    .comp-label.gap  { background: rgba(255,80,80,0.15);  color: #ff8080; }
    .comp-label.edge { background: rgba(212,165,53,0.15); color: var(--gold); }
    .comp-text { color: rgba(240,234,216,0.78); }

    /* ── CONCLUSION ── */
    .conclusion-block {
      text-align: center;
      padding: 5rem 2rem 6rem;
    }
    .conclusion-block .big-quote {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.5rem, 3.5vw, 2.6rem);
      font-weight: 400;
      font-style: italic;
      color: var(--white);
      line-height: 1.4;
      max-width: 820px;
      margin: 0 auto 2.5rem;
    }
    .conclusion-block .big-quote em { color: var(--gold); font-style: normal; }
    .gold-line {
      width: 60px;
      height: 2px;
      background: var(--gold);
      margin: 0 auto 2.5rem;
    }
    .conclusion-tagline {
      font-family: 'Heebo', sans-serif;
      font-size: 1rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
    }

    /* ── FOOTER ── */
    footer {
      border-top: 1px solid rgba(212,165,53,0.12);
      padding: 2.5rem;
      text-align: center;
      font-size: 0.8rem;
      color: var(--muted);
      letter-spacing: 0.08em;
    }
    footer strong { color: var(--gold); }
  </style>
</head>
<body>

<!-- ══════════════════════════════════════ HEADER ══════════════════════════════════════ -->
<header>
  <div class="wrap">
    <div class="header-label">Strategic Analysis · ניתוח אסטרטגי</div>
    <h1 class="header-title-he">המהפכה המקבילה</h1>
    <div class="header-title-en">The Parallel Revolution</div>
    <div class="vs-badge">
      Share-Pen &nbsp;<span class="vs">VS</span>&nbsp; The BTC Standard
    </div>
    <p class="header-sub" style="margin-top:1.8rem;">
      מה שביטקוין עשה לכסף — Share-Pen עושה למילה הכתובה
    </p>
  </div>
</header>

<!-- ══════════════════════════════════════ INTRO ══════════════════════════════════════ -->
<section>
  <div class="wrap">
    <div class="section-eyebrow">The Framework · המסגרת</div>
    <h2 class="section-heading">
      המוצרים הגדולים ביותר בהיסטוריה<br />
      <em>לא משפרים את הקיים — הם מחזירים כוח לפרט</em>
    </h2>
    <div class="intro-grid">
      <div class="intro-body">
        <p>
          ב-2008, אדם (או קבוצה) בשם סאטושי נקמוטו פרסם מסמך של תשעה עמודים שהפך את העולם הפיננסי על פיו.
          הוא לא בנה בנק טוב יותר — הוא ביטל את הצורך בבנקים. ביטקוין לא שיפר את המערכת הקיימת; הוא
          עקף אותה לחלוטין ומסר את הריבונות הפיננסית חזרה לכל אדם על פני האדמה.
        </p>
        <p>
          זוהי מסגרת חשיבה רבת עוצמה לזיהוי מוצרים מהפכניים אמיתיים. לא כלים שמייעלים תהליכים —
          כלים שמשנים יחסי כוח. המבחן הפשוט: האם המוצר מחזיר לאדם הפשוט גישה למשהו שהיה שמור
          עד כה לבעלי פריבילגיה, השער, הגישה?
        </p>
        <p>
          Share-Pen עומד בדיוק על קו זה. הוא אינו "כלי כתיבה עם AI". הוא פרוטוקול אנושי לסיפור
          — מחזיר את שליטת הנרטיב לכל אדם שיש לו סיפור לספר.
        </p>
      </div>
      <ul class="principles-list">
        <li>מחזיר כוח לפרט — מסיר תלות במתווכים ושומרי הסף</li>
        <li>מסיר מתווכים — ביטקוין ביטל בנקים; Share-Pen מבטל את "הדף הלבן הגורלי"</li>
        <li>יוצר שפה נטיבית חדשה — קריפטו, ארנקים, בלוקצ'יין; נרטיב שיתופי, מניפסט, קורפוס</li>
        <li>בונה קהילה גלובלית סביב אמונה משותפת</li>
        <li>מגובה במניפסט בלתי עציר (Whitepaper של סאטושי = מניפסט GENESIS של Share-Pen)</li>
        <li>גדל דרך אפקטי רשת — ככל שיש יותר משתמשים, כך הרשת חזקה יותר</li>
        <li>דמוקרטיזציה של גישה למשהו שנשמר עד כה לאליטה</li>
      </ul>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ TABLE ══════════════════════════════════════ -->
<section>
  <div class="wrap">
    <div class="section-eyebrow">Comparative Matrix · מטריצת השוואה</div>
    <h2 class="section-heading">
      ביטקוין <em>מול</em> Share-Pen — 11 קריטריונים
    </h2>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>קריטריון</th>
            <th>Bitcoin ₿</th>
            <th>Share-Pen ✒</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="row-num">01</span> הבטחה מהפכנית</td>
            <td>"בנקים לא שולטים בכסף שלך"</td>
            <td>"שומרי הסף לא שולטים בסיפור שלך"</td>
          </tr>
          <tr>
            <td><span class="row-num">02</span> האויב</td>
            <td>מוסדות פיננסיים מרכזיים — בנקים, ממשלות, FED</td>
            <td>הדף הלבן + שומרי הסף של ההוצאה לאור</td>
          </tr>
          <tr>
            <td><span class="row-num">03</span> הגיבור</td>
            <td>כל אדם עם חיבור לאינטרנט</td>
            <td>כל אדם שיש לו סיפור לספר</td>
          </tr>
          <tr>
            <td><span class="row-num">04</span> טכנולוגיית הליבה</td>
            <td>Blockchain — אמון מבוזר ומוצפן</td>
            <td>AI — יצירתיות מבוזרת ומכפילה</td>
          </tr>
          <tr>
            <td><span class="row-num">05</span> אפקט רשת</td>
            <td>יותר משתמשים = רשת חזקה יותר ועמידה יותר</td>
            <td>יותר כותבים = קורפוס קהילתי עשיר יותר</td>
          </tr>
          <tr>
            <td><span class="row-num">06</span> המניפסט</td>
            <td>White Paper של סאטושי נקמוטו (אוקטובר 2008)</td>
            <td>מניפסט GENESIS של Share-Pen (2026)</td>
          </tr>
          <tr>
            <td><span class="row-num">07</span> שפה נטיבית</td>
            <td>אמת קריפטוגרפית — hash, block, chain, wallet</td>
            <td>נרטיב שיתופי — co-write, corpus, voice, flow</td>
          </tr>
          <tr>
            <td><span class="row-num">08</span> היקף גלובלי</td>
            <td>106M+ ארנקים, 190+ מדינות, $1.3T שווי שוק</td>
            <td>יעד: 5 שפות, TAM של $86B, כל אדם עם סיפור</td>
          </tr>
          <tr>
            <td><span class="row-num">09</span> מודל אמון</td>
            <td>Trustless — לא צריך לסמוך על אדם או מוסד</td>
            <td>Trustful — שיתוף פעולה מניב יצירות גדולות מסכומן</td>
          </tr>
          <tr>
            <td><span class="row-num">10</span> ריבונות</td>
            <td>ריבונות פיננסית — "Be your own bank"</td>
            <td>ריבונות נרטיבית — "Be your own publisher"</td>
          </tr>
          <tr>
            <td><span class="row-num">11</span> מודל שפע</td>
            <td>סופי ומדויק — 21 מיליון מטבעות בלבד</td>
            <td>אינסופי ומכפיל — כל שיתוף מגדיל את הערך הכולל</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ POSITIONING ══════════════════════════════════════ -->
<section>
  <div class="wrap">
    <div class="section-eyebrow">Positioning Statement · הצהרת מיצוב</div>
    <h2 class="section-heading">
      לא מוצר — <em>פרוטוקול אנושי</em>
    </h2>
    <div class="pos-block">
      <p>
        Share-Pen is not building a product. It is launching a <strong>protocol</strong> — a human protocol for storytelling.
        Just as Bitcoin made every person their own bank, <strong>Share-Pen makes every person their own publisher.</strong>
        <br /><br />
        כשם שביטקוין לא ביקש רשות מהבנקים לשנות את מערכת הכספים — Share-Pen אינו מבקש רשות
        מהמו"לים, מהאלגוריתמים, מ"האמנות האמיתית" — לשנות את מי שמורשה לספר סיפורים.
        <br /><br />
        <strong>כולם מורשים. תמיד היו מורשים. עכשיו יש להם את הכלים.</strong>
      </p>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ COMPETITIVE LANDSCAPE ══════════════════════════════════════ -->
<section>
  <div class="wrap">
    <div class="section-eyebrow">Competitive Landscape · מפת התחרות</div>
    <h2 class="section-heading">
      מי עוד בשטח —<br /><em>ולמה הם לא Share-Pen</em>
    </h2>
    <div class="comp-grid">

      <div class="comp-card">
        <div class="comp-name">Jasper AI</div>
        <div class="comp-what">AI copywriting &amp; marketing content tool</div>
        <div class="comp-row">
          <span class="comp-label gap">GAP</span>
          <span class="comp-text">כלי שיווקי מונוליתי, חד-לשוני, לא מבין ניואנסים תרבותיים, ממוקד ב-ROI ולא בקול האישי</span>
        </div>
        <div class="comp-row">
          <span class="comp-label edge">EDGE</span>
          <span class="comp-text">Share-Pen: שיתופי, ממוקד אנושי, רב-לשוני, בונה קהילה — לא רק תוכן</span>
        </div>
      </div>

      <div class="comp-card">
        <div class="comp-name">Notion AI</div>
        <div class="comp-what">Productivity-embedded writing assistant</div>
        <div class="comp-row">
          <span class="comp-label gap">GAP</span>
          <span class="comp-text">תוספת לתוכנת פרודקטיביות — לא מבין סיפורים, לא עוצב לנרטיב, אין ממד של קוד הקול</span>
        </div>
        <div class="comp-row">
          <span class="comp-label edge">EDGE</span>
          <span class="comp-text">Share-Pen: פלטפורמה ייעודית לסיפור, לא לרשימות משימות — בנויה מהיסוד לכוונה נרטיבית</span>
        </div>
      </div>

      <div class="comp-card">
        <div class="comp-name">Medium</div>
        <div class="comp-what">Open publishing platform for writers</div>
        <div class="comp-row">
          <span class="comp-label gap">GAP</span>
          <span class="comp-text">הפצה בלבד — לא עוזר ליצור, לא שיתופי, נשלט על ידי אלגוריתם, אנגלית-דומיננטי</span>
        </div>
        <div class="comp-row">
          <span class="comp-label edge">EDGE</span>
          <span class="comp-text">Share-Pen: AI כשותף ביצירה ולא רק בהפצה — מה שאתה כותב הוא הטוב ביותר שיכולת לכתוב</span>
        </div>
      </div>

      <div class="comp-card">
        <div class="comp-name">Wattpad</div>
        <div class="comp-what">Community storytelling &amp; fan fiction platform</div>
        <div class="comp-row">
          <span class="comp-label gap">GAP</span>
          <span class="comp-text">קהילה בלי AI, איכות לא אחידה, תדמית של "כתיבת תחביב", חסרת כלים מקצועיים</span>
        </div>
        <div class="comp-row">
          <span class="comp-label edge">EDGE</span>
          <span class="comp-text">Share-Pen: שיתוף הקהילה + איכות מקצועית AI — כתיבת תחביב שמרגישה כמו פרסום אמיתי</span>
        </div>
      </div>

      <div class="comp-card">
        <div class="comp-name">Grammarly</div>
        <div class="comp-what">AI-powered grammar &amp; style correction</div>
        <div class="comp-row">
          <span class="comp-label gap">GAP</span>
          <span class="comp-text">תיקון בלבד — לא יוצר, לא מעצב קול, לא מבין כוונה נרטיבית, לא שיתופי</span>
        </div>
        <div class="comp-row">
          <span class="comp-label edge">EDGE</span>
          <span class="comp-text">Share-Pen: שותפות יצירתית מלאה — לא "הצעה לתיקון" אלא "הפלא מה שכתבת"</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ CONCLUSION ══════════════════════════════════════ -->
<section style="padding-bottom:0;">
  <div class="wrap">
    <div class="conclusion-block">
      <div class="gold-line"></div>
      <p class="big-quote">
        "The question is not whether the writing revolution will happen.<br />
        It will.<br />
        The question is whether <em>Share-Pen leads it</em>."
      </p>
      <div class="gold-line"></div>
      <div style="margin-bottom:1.5rem; font-family:'Cormorant Garamond',serif; font-size:1.2rem; font-style:italic; color:rgba(240,234,216,0.6);">
        השאלה אינה אם מהפכת הכתיבה תקרה.<br />
        היא תקרה.<br />
        השאלה היא אם Share-Pen תוביל אותה.
      </div>
      <div class="conclusion-tagline">Write with Purpose · כתוב בכוונה</div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ FOOTER ══════════════════════════════════════ -->
<footer>
  <strong>Share-Pen</strong> · GENESIS Campaign · Strategic Analysis Document · 2026
  <br />
  <span style="font-size:0.72rem; opacity:0.6; margin-top:0.4rem; display:block;">
    Not AI instead of you — AI because of you
  </span>
</footer>

</body>
</html>
