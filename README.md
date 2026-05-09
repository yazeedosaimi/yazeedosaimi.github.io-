# yazeedosaimi.github.io-

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CS285 – Discrete Math Study Hub</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0b0d12;
    --surface: #13161f;
    --surface2: #1c2030;
    --border: #2a2f42;
    --border2: #363d55;
    --accent: #6c8dff;
    --accent2: #a78bfa;
    --green: #34d399;
    --amber: #fbbf24;
    --red: #f87171;
    --text: #e8ecf7;
    --text2: #8892b0;
    --text3: #4a5175;
    --mono: 'IBM Plex Mono', monospace;
    --sans: 'IBM Plex Sans Arabic', sans-serif;
    --r: 10px;
    --r2: 16px;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 15px;
    line-height: 1.7;
    min-height: 100vh;
  }

  /* ── LAYOUT ── */
  .shell { display: flex; min-height: 100vh; }

  .sidebar {
    width: 260px; flex-shrink: 0;
    background: var(--surface);
    border-left: 1px solid var(--border);
    padding: 24px 0;
    position: sticky; top: 0; height: 100vh;
    overflow-y: auto;
    display: flex; flex-direction: column;
  }
  .sidebar-logo {
    padding: 0 20px 20px;
    border-bottom: 1px solid var(--border);
    margin-bottom: 16px;
  }
  .sidebar-logo .course { font-size: 11px; font-family: var(--mono); color: var(--accent); letter-spacing: .08em; margin-bottom: 4px; }
  .sidebar-logo h1 { font-size: 16px; font-weight: 600; color: var(--text); line-height: 1.3; }

  .nav-section { padding: 0 12px; margin-bottom: 8px; }
  .nav-label { font-size: 10px; font-family: var(--mono); color: var(--text3); letter-spacing: .12em; text-transform: uppercase; padding: 0 8px; margin-bottom: 6px; }
  .nav-item {
    display: flex; align-items: center; gap: 10px;
    padding: 9px 10px; border-radius: var(--r);
    cursor: pointer; transition: all .15s;
    color: var(--text2); font-size: 13.5px;
    border: 1px solid transparent;
  }
  .nav-item:hover { background: var(--surface2); color: var(--text); }
  .nav-item.active { background: rgba(108,141,255,.12); color: var(--accent); border-color: rgba(108,141,255,.25); }
  .nav-item .ch { font-family: var(--mono); font-size: 10px; color: var(--text3); min-width: 28px; }
  .nav-item.active .ch { color: var(--accent); opacity: .7; }

  .sidebar-footer { margin-top: auto; padding: 16px 20px 0; border-top: 1px solid var(--border); }
  .progress-bar { height: 4px; background: var(--surface2); border-radius: 99px; overflow: hidden; margin: 8px 0 4px; }
  .progress-fill { height: 100%; background: linear-gradient(90deg, var(--accent), var(--accent2)); border-radius: 99px; transition: width .4s; }
  .progress-label { font-size: 11px; color: var(--text3); font-family: var(--mono); }

  /* ── MAIN ── */
  .main { flex: 1; padding: 32px 36px; max-width: 960px; }

  .page { display: none; }
  .page.active { display: block; }

  /* ── HOME ── */
  .hero { margin-bottom: 36px; }
  .hero-tag { font-family: var(--mono); font-size: 11px; color: var(--accent); letter-spacing: .1em; margin-bottom: 10px; }
  .hero h2 { font-size: 28px; font-weight: 700; color: var(--text); margin-bottom: 8px; }
  .hero p { color: var(--text2); font-size: 14px; max-width: 520px; }

  .cards-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 14px; margin-bottom: 32px; }
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r2);
    padding: 20px;
    cursor: pointer;
    transition: all .18s;
    position: relative; overflow: hidden;
  }
  .card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--card-color, var(--accent)) 0%, transparent 60%);
    opacity: 0; transition: opacity .2s;
  }
  .card:hover { border-color: var(--border2); transform: translateY(-2px); }
  .card:hover::before { opacity: .04; }
  .card-ch { font-family: var(--mono); font-size: 10px; color: var(--text3); margin-bottom: 8px; }
  .card-icon { font-size: 24px; margin-bottom: 10px; }
  .card h3 { font-size: 14px; font-weight: 600; color: var(--text); margin-bottom: 5px; }
  .card p { font-size: 12px; color: var(--text2); line-height: 1.5; }
  .card-topics { display: flex; flex-wrap: wrap; gap: 5px; margin-top: 12px; }
  .tag { font-size: 10px; font-family: var(--mono); padding: 3px 8px; border-radius: 5px; background: var(--surface2); color: var(--text3); border: 1px solid var(--border); }

  /* ── SECTION PAGE ── */
  .section-header { margin-bottom: 28px; padding-bottom: 20px; border-bottom: 1px solid var(--border); }
  .section-header .back { font-size: 12px; font-family: var(--mono); color: var(--text3); cursor: pointer; margin-bottom: 12px; display: flex; align-items: center; gap: 6px; }
  .section-header .back:hover { color: var(--accent); }
  .section-badge { display: inline-flex; align-items: center; gap: 6px; font-family: var(--mono); font-size: 11px; color: var(--accent); background: rgba(108,141,255,.1); border: 1px solid rgba(108,141,255,.25); border-radius: 6px; padding: 4px 10px; margin-bottom: 10px; }
  .section-header h2 { font-size: 22px; font-weight: 700; margin-bottom: 6px; }
  .section-header p { color: var(--text2); font-size: 13px; }

  .tabs { display: flex; gap: 4px; margin-bottom: 24px; background: var(--surface); border: 1px solid var(--border); border-radius: var(--r); padding: 4px; width: fit-content; }
  .tab { padding: 7px 16px; border-radius: 7px; font-size: 13px; cursor: pointer; color: var(--text2); transition: all .15s; }
  .tab.active { background: var(--surface2); color: var(--text); border: 1px solid var(--border2); }

  /* ── SUMMARY ── */
  .summary-block { background: var(--surface); border: 1px solid var(--border); border-radius: var(--r2); padding: 22px; margin-bottom: 16px; }
  .summary-block h3 { font-size: 14px; font-weight: 600; color: var(--accent); margin-bottom: 12px; display: flex; align-items: center; gap: 8px; }
  .summary-block ul { list-style: none; }
  .summary-block ul li { font-size: 13.5px; color: var(--text2); padding: 5px 0; border-bottom: 1px solid var(--border); display: flex; gap: 10px; }
  .summary-block ul li:last-child { border-bottom: none; }
  .summary-block ul li::before { content: '→'; color: var(--accent); opacity: .6; flex-shrink: 0; font-family: var(--mono); }
  .formula-box {
    background: var(--bg); border: 1px solid var(--border2);
    border-radius: var(--r); padding: 14px 18px; margin: 10px 0;
    font-family: var(--mono); font-size: 13px; color: var(--accent2);
    border-right: 3px solid var(--accent2);
  }
  .note-box { background: rgba(251,191,36,.06); border: 1px solid rgba(251,191,36,.2); border-radius: var(--r); padding: 12px 16px; margin: 10px 0; font-size: 13px; color: #fcd34d; }

  /* ── FLASHCARDS ── */
  .fc-container { perspective: 1000px; max-width: 560px; margin: 0 auto; }
  .fc-wrapper { position: relative; height: 220px; margin-bottom: 20px; }
  .fc-card {
    width: 100%; height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform .55s cubic-bezier(.4,0,.2,1);
    cursor: pointer;
  }
  .fc-card.flipped { transform: rotateY(180deg); }
  .fc-face {
    position: absolute; inset: 0;
    backface-visibility: hidden;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r2);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    padding: 28px; text-align: center;
  }
  .fc-face.back { transform: rotateY(180deg); background: var(--surface2); border-color: var(--accent); }
  .fc-label { font-family: var(--mono); font-size: 10px; color: var(--text3); margin-bottom: 14px; }
  .fc-q { font-size: 15px; font-weight: 500; color: var(--text); line-height: 1.5; }
  .fc-a { font-size: 14px; color: var(--accent2); line-height: 1.6; font-family: var(--mono); }
  .fc-controls { display: flex; align-items: center; justify-content: center; gap: 12px; margin-bottom: 16px; }
  .fc-btn {
    padding: 9px 20px; border-radius: var(--r); font-size: 13px; font-family: var(--sans);
    border: 1px solid var(--border2); background: var(--surface);
    color: var(--text); cursor: pointer; transition: all .15s;
  }
  .fc-btn:hover { background: var(--surface2); border-color: var(--accent); color: var(--accent); }
  .fc-btn.know { border-color: rgba(52,211,153,.4); color: var(--green); }
  .fc-btn.know:hover { background: rgba(52,211,153,.08); }
  .fc-btn.skip { border-color: rgba(248,113,113,.4); color: var(--red); }
  .fc-btn.skip:hover { background: rgba(248,113,113,.08); }
  .fc-counter { font-family: var(--mono); font-size: 12px; color: var(--text3); text-align: center; }
  .fc-hint { font-size: 11px; color: var(--text3); text-align: center; margin-top: 8px; }

  /* ── QUIZ ── */
  .quiz-q { background: var(--surface); border: 1px solid var(--border); border-radius: var(--r2); padding: 22px; margin-bottom: 16px; }
  .quiz-qnum { font-family: var(--mono); font-size: 10px; color: var(--text3); margin-bottom: 8px; }
  .quiz-qtext { font-size: 15px; font-weight: 500; color: var(--text); margin-bottom: 18px; line-height: 1.6; }
  .quiz-opts { display: grid; gap: 8px; }
  .quiz-opt {
    padding: 12px 16px; border-radius: var(--r);
    border: 1px solid var(--border); background: var(--surface2);
    color: var(--text2); font-size: 13.5px; cursor: pointer; transition: all .15s;
    text-align: right;
  }
  .quiz-opt:hover { border-color: var(--border2); color: var(--text); }
  .quiz-opt.correct { border-color: var(--green); color: var(--green); background: rgba(52,211,153,.08); }
  .quiz-opt.wrong { border-color: var(--red); color: var(--red); background: rgba(248,113,113,.08); }
  .quiz-exp { background: rgba(108,141,255,.08); border: 1px solid rgba(108,141,255,.2); border-radius: var(--r); padding: 14px 16px; margin-top: 12px; font-size: 13px; color: var(--text2); display: none; }
  .quiz-exp.show { display: block; }
  .quiz-exp strong { color: var(--accent); }
  .quiz-score { text-align: center; padding: 40px 20px; }
  .quiz-score .big { font-size: 56px; font-weight: 700; font-family: var(--mono); color: var(--accent); }
  .quiz-score .label { color: var(--text2); font-size: 14px; margin-top: 6px; }

  .btn-primary {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 24px; border-radius: var(--r);
    background: var(--accent); color: #fff;
    font-size: 13px; font-family: var(--sans); font-weight: 500;
    border: none; cursor: pointer; transition: all .15s;
  }
  .btn-primary:hover { background: #5577ee; transform: translateY(-1px); }
  .btn-ghost {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 10px 22px; border-radius: var(--r);
    background: transparent; color: var(--text2);
    font-size: 13px; font-family: var(--sans);
    border: 1px solid var(--border2); cursor: pointer; transition: all .15s;
  }
  .btn-ghost:hover { color: var(--text); border-color: var(--text3); }

  /* ── MINDMAP ── */
  .mindmap-wrap { background: var(--surface); border: 1px solid var(--border); border-radius: var(--r2); padding: 20px; overflow-x: auto; }
  .mmap { display: flex; align-items: flex-start; gap: 20px; min-width: 700px; }
  .mmap-center { background: var(--accent); color: #fff; border-radius: var(--r); padding: 12px 18px; font-weight: 600; font-size: 13px; white-space: nowrap; align-self: center; }
  .mmap-branches { display: flex; flex-direction: column; gap: 12px; flex: 1; }
  .mmap-branch { display: flex; align-items: center; gap: 12px; }
  .mmap-line { height: 1px; width: 24px; background: var(--border2); flex-shrink: 0; }
  .mmap-node { background: var(--surface2); border: 1px solid var(--border); border-radius: var(--r); padding: 10px 14px; font-size: 12.5px; color: var(--text2); }
  .mmap-node strong { color: var(--text); display: block; font-size: 12px; margin-bottom: 3px; }
  .mmap-node span { font-size: 11px; }

  /* scrollbar */
  ::-webkit-scrollbar { width: 5px; height: 5px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 99px; }

  @media (max-width: 700px) {
    .sidebar { display: none; }
    .main { padding: 20px 16px; }
  }
</style>
</head>
<body>

<div class="shell">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-logo">
      <div class="course">CS285</div>
      <h1>Discrete Math<br>Study Hub</h1>
    </div>

    <div class="nav-section">
      <div class="nav-label">الصفحة الرئيسية</div>
      <div class="nav-item active" onclick="nav('home')">
        <span class="ch">—</span> نظرة عامة
      </div>
    </div>

    <div class="nav-section">
      <div class="nav-label">المواضيع</div>
      <div class="nav-item" onclick="nav('logic')"><span class="ch">ch1</span> المنطق والمجموعات</div>
      <div class="nav-item" onclick="nav('sets')"><span class="ch">ch2</span> المجموعات والدوال</div>
      <div class="nav-item" onclick="nav('numtheory')"><span class="ch">ch4</span> نظرية الأعداد والتشفير</div>
      <div class="nav-item" onclick="nav('induction')"><span class="ch">ch5</span> الاستقراء الرياضي</div>
      <div class="nav-item" onclick="nav('counting')"><span class="ch">ch6</span> العد والترتيب</div>
      <div class="nav-item" onclick="nav('advanced')"><span class="ch">ch8</span> العد المتقدم</div>
      <div class="nav-item" onclick="nav('relations')"><span class="ch">ch9</span> العلاقات</div>
    </div>

    <div class="sidebar-footer">
      <div style="font-size:11px;color:var(--text3);margin-bottom:6px">تقدمك</div>
      <div class="progress-bar"><div class="progress-fill" id="prog-fill" style="width:0%"></div></div>
      <div class="progress-label" id="prog-label">0 / 7 مواضيع</div>
    </div>
  </aside>

  <!-- MAIN -->
  <main class="main">

    <!-- HOME PAGE -->
    <div class="page active" id="page-home">
      <div class="hero">
        <div class="hero-tag">// CS285 DISCRETE MATHEMATICS</div>
        <h2>مرحباً! من أين تبدأ؟ 👋</h2>
        <p>اختر موضوع لتذاكره — لكل موضوع ملخص + بطاقات تعليمية + اختبار قصير.</p>
      </div>

      <div class="cards-grid">
        <div class="card" onclick="nav('logic')" style="--card-color:#6c8dff">
          <div class="card-ch">CHAPTER 1</div>
          <div class="card-icon">🧠</div>
          <h3>المنطق الرياضي</h3>
          <p>Propositions, Truth Tables, Connectives, Predicates</p>
          <div class="card-topics">
            <span class="tag">¬p ∧ ∨</span><span class="tag">Truth Table</span><span class="tag">Quantifiers</span>
          </div>
        </div>
        <div class="card" onclick="nav('sets')" style="--card-color:#a78bfa">
          <div class="card-ch">CHAPTER 2</div>
          <div class="card-icon">🔵</div>
          <h3>المجموعات والدوال</h3>
          <p>Sets, Functions, Sequences, Matrices</p>
          <div class="card-topics">
            <span class="tag">Subset</span><span class="tag">Bijection</span><span class="tag">Cardinality</span>
          </div>
        </div>
        <div class="card" onclick="nav('numtheory')" style="--card-color:#34d399">
          <div class="card-ch">CHAPTER 4</div>
          <div class="card-icon">🔐</div>
          <h3>نظرية الأعداد</h3>
          <p>Divisibility, GCD, Modular Arithmetic, Cryptography</p>
          <div class="card-topics">
            <span class="tag">GCD</span><span class="tag">mod</span><span class="tag">Caesar</span>
          </div>
        </div>
        <div class="card" onclick="nav('induction')" style="--card-color:#fbbf24">
          <div class="card-ch">CHAPTER 5</div>
          <div class="card-icon">🔁</div>
          <h3>الاستقراء الرياضي</h3>
          <p>Math Induction, Recursion, Recursive Functions</p>
          <div class="card-topics">
            <span class="tag">Basis</span><span class="tag">Inductive</span><span class="tag">Recursion</span>
          </div>
        </div>
        <div class="card" onclick="nav('counting')" style="--card-color:#f87171">
          <div class="card-ch">CHAPTER 6</div>
          <div class="card-icon">🔢</div>
          <h3>العد والترتيب</h3>
          <p>Sum/Product Rule, Permutations, Combinations</p>
          <div class="card-topics">
            <span class="tag">P(n,r)</span><span class="tag">C(n,r)</span><span class="tag">Inclusion-Exclusion</span>
          </div>
        </div>
        <div class="card" onclick="nav('advanced')" style="--card-color:#818cf8">
          <div class="card-ch">CHAPTER 8</div>
          <div class="card-icon">📈</div>
          <h3>العد المتقدم</h3>
          <p>Sequences, Recurrence Relations</p>
          <div class="card-topics">
            <span class="tag">Geometric</span><span class="tag">Arithmetic</span><span class="tag">Recurrence</span>
          </div>
        </div>
        <div class="card" onclick="nav('relations')" style="--card-color:#38bdf8">
          <div class="card-ch">CHAPTER 9</div>
          <div class="card-icon">🔗</div>
          <h3>العلاقات</h3>
          <p>Relations, Properties, Representation</p>
          <div class="card-topics">
            <span class="tag">Reflexive</span><span class="tag">Symmetric</span><span class="tag">Transitive</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ TEMPLATE: each topic page ═══ -->

    <!-- LOGIC PAGE -->
    <div class="page" id="page-logic" data-ch="ch1">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 1</div>
        <h2>المنطق الرياضي — Propositional Logic</h2>
        <p>Propositions, Connectives, Truth Tables, Predicates, Quantifiers, Rules of Inference</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'logic','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'logic','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'logic','quiz')">✏️ اختبار</div>
      </div>

      <div id="logic-summary">
        <div class="summary-block">
          <h3>📌 ما هي الـ Proposition؟</h3>
          <ul>
            <li>جملة خبرية لها قيمة True أو False وليس الاثنين معاً</li>
            <li>مثال ✅: "2+2=4" — مثال ❌: "ما الساعة؟" (سؤال مش proposition)</li>
            <li>نرمز للـ propositions بالرموز: p, q, r, s</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>⚡ العمليات المنطقية الأساسية</h3>
          <ul>
            <li><strong style="color:var(--text);font-family:var(--mono)">¬p</strong> — Negation: عكس القيمة (NOT)</li>
            <li><strong style="color:var(--text);font-family:var(--mono)">p ∧ q</strong> — Conjunction: صح فقط لو الاثنين صح (AND)</li>
            <li><strong style="color:var(--text);font-family:var(--mono)">p ∨ q</strong> — Disjunction: صح لو واحد على الأقل صح (OR)</li>
            <li><strong style="color:var(--text);font-family:var(--mono)">p → q</strong> — Implication: غلط فقط لو p صح وq غلط</li>
            <li><strong style="color:var(--text);font-family:var(--mono)">p ↔ q</strong> — Biconditional: صح لو الاثنين متساويين</li>
          </ul>
          <div class="formula-box">
            p → q ≡ ¬p ∨ q &nbsp;|&nbsp; Contrapositive: ¬q → ¬p
          </div>
        </div>
        <div class="summary-block">
          <h3>🔢 Quantifiers</h3>
          <ul>
            <li><strong style="color:var(--text);font-family:var(--mono)">∀x P(x)</strong> — Universal: صح لكل قيم x</li>
            <li><strong style="color:var(--text);font-family:var(--mono)">∃x P(x)</strong> — Existential: صح لوجود قيمة واحدة على الأقل</li>
            <li>نفي ∀x P(x) = ∃x ¬P(x) &nbsp;|&nbsp; نفي ∃x P(x) = ∀x ¬P(x)</li>
          </ul>
        </div>
        <div class="note-box">💡 تذكير: جدول الحقيقة لـ p → q — الحالة الوحيدة اللي تجيب False هي لما p = T وq = F</div>
      </div>

      <div id="logic-flash" style="display:none">
        <div class="fc-container" id="fc-logic"></div>
      </div>
      <div id="logic-quiz" style="display:none">
        <div id="qz-logic"></div>
      </div>
    </div>

    <!-- SETS PAGE -->
    <div class="page" id="page-sets" data-ch="ch2">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 2</div>
        <h2>المجموعات والدوال — Sets & Functions</h2>
        <p>Set notation, Operations, Subsets, Functions Types, Cardinality, Sequences</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'sets','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'sets','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'sets','quiz')">✏️ اختبار</div>
      </div>
      <div id="sets-summary">
        <div class="summary-block">
          <h3>📦 تعريف المجموعة</h3>
          <ul>
            <li>مجموعة = collection غير مرتبة من العناصر المميزة</li>
            <li>a ∈ A يعني a عضو في A &nbsp;|&nbsp; a ∉ A يعني ليس عضواً</li>
            <li>∅ = المجموعة الفارغة &nbsp;|&nbsp; A ⊆ B يعني A مجموعة جزئية من B</li>
          </ul>
          <div class="formula-box">
            |A ∪ B| = |A| + |B| − |A ∩ B|  ← Inclusion-Exclusion
          </div>
        </div>
        <div class="summary-block">
          <h3>🔄 أنواع الدوال</h3>
          <ul>
            <li><strong style="color:var(--text)">Injective (One-to-One)</strong>: كل عنصران مختلفان في A لهما صور مختلفة</li>
            <li><strong style="color:var(--text)">Surjective (Onto)</strong>: كل عنصر في B له سابقة في A</li>
            <li><strong style="color:var(--text)">Bijective</strong>: Injective + Surjective معاً</li>
            <li>الدالة العكسية f⁻¹ موجودة فقط إذا كانت الدالة Bijective</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🔢 Cardinality</h3>
          <ul>
            <li>|A| = عدد عناصر A</li>
            <li>المجموعة العدّادة (Countable): إما Finite أو لها تقابل Bijective مع ℕ</li>
            <li>ℕ, ℤ, ℚ = Countable &nbsp;|&nbsp; ℝ = Uncountable</li>
          </ul>
        </div>
      </div>
      <div id="sets-flash" style="display:none"><div class="fc-container" id="fc-sets"></div></div>
      <div id="sets-quiz" style="display:none"><div id="qz-sets"></div></div>
    </div>

    <!-- NUM THEORY PAGE -->
    <div class="page" id="page-numtheory" data-ch="ch4">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 4</div>
        <h2>نظرية الأعداد والتشفير</h2>
        <p>Divisibility, Primes, GCD, LCM, Modular Arithmetic, Caesar Cipher, RSA</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'numtheory','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'numtheory','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'numtheory','quiz')">✏️ اختبار</div>
      </div>
      <div id="numtheory-summary">
        <div class="summary-block">
          <h3>➗ القسمة والأعداد الأولية</h3>
          <ul>
            <li>a | b يعني a يقسم b (توجد c صحيح بحيث b = a·c)</li>
            <li>العدد الأولي p &gt; 1: عوامله الموجبة فقط 1 و p</li>
            <li>كل عدد صحيح &gt; 1 يكتب بصورة وحيدة كناتج عوامل أولية (FTA)</li>
            <li>إذا كان n مركباً فله عامل أولي ≤ √n</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🔢 GCD و LCM</h3>
          <ul>
            <li>gcd(a,b) = أكبر مقسوم عليه مشترك</li>
            <li>lcm(a,b) = أصغر مضاعف مشترك</li>
            <li>العلاقة: gcd(a,b) × lcm(a,b) = a × b</li>
          </ul>
          <div class="formula-box">
            gcd(24,36): 24=2³×3 | 36=2²×3² → gcd = 2²×3 = 12 | lcm = 2³×3² = 72
          </div>
        </div>
        <div class="summary-block">
          <h3>🔄 الحساب المعياري (Modular Arithmetic)</h3>
          <ul>
            <li>a mod m = باقي قسمة a على m (دائماً ≥ 0)</li>
            <li>a ≡ b (mod m) يعني m | (a−b)</li>
            <li>−11 mod 3: −11 = 3×(−4)+1 → باقي = 1</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🔐 Caesar Cipher</h3>
          <ul>
            <li>تشفير: f(p) = (p + k) mod 26</li>
            <li>فك التشفير: f⁻¹(p) = (p − k) mod 26</li>
            <li>مثال k=3: A→D, B→E, ... Z→C</li>
          </ul>
          <div class="formula-box">Affine Cipher: f(p) = (a·p + b) mod 26 | شرط: gcd(a,26)=1</div>
        </div>
      </div>
      <div id="numtheory-flash" style="display:none"><div class="fc-container" id="fc-numtheory"></div></div>
      <div id="numtheory-quiz" style="display:none"><div id="qz-numtheory"></div></div>
    </div>

    <!-- INDUCTION PAGE -->
    <div class="page" id="page-induction" data-ch="ch5">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 5</div>
        <h2>الاستقراء الرياضي والتعريف التكراري</h2>
        <p>Mathematical Induction, Strong Induction, Recursively Defined Functions</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'induction','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'induction','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'induction','quiz')">✏️ اختبار</div>
      </div>
      <div id="induction-summary">
        <div class="summary-block">
          <h3>📐 خطوات الاستقراء الرياضي</h3>
          <ul>
            <li><strong style="color:var(--green)">خطوة الأساس (Basis Step)</strong>: أثبت أن P(1) صحيحة</li>
            <li><strong style="color:var(--accent)">خطوة الاستقراء (Inductive Step)</strong>: افترض P(k) صحيحة، ثم أثبت P(k+1)</li>
            <li>الاستنتاج: P(n) صحيحة لكل n ≥ 1</li>
          </ul>
          <div class="formula-box">
            مثال: 1+2+...+n = n(n+1)/2<br>
            Basis: n=1 → LHS=1, RHS=1(2)/2=1 ✓<br>
            Inductive: LHS(k+1) = k(k+1)/2 + (k+1) = (k+1)(k+2)/2 ✓
          </div>
        </div>
        <div class="summary-block">
          <h3>📋 صيغ مهمة تثبت بالاستقراء</h3>
          <ul>
            <li>1+2+...+n = n(n+1)/2</li>
            <li>1²+2²+...+n² = n(n+1)(2n+1)/6</li>
            <li>1+3+5+...+(2n-1) = n²</li>
            <li>1+2+2²+...+2ⁿ = 2ⁿ⁺¹ − 1</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🔁 التعريف التكراري (Recursion)</h3>
          <ul>
            <li>يتكون من جزأين: Basis (القيمة الابتدائية) + Recursive Step</li>
            <li>مثال: Factorial → f(0)=1, f(n)=n·f(n−1)</li>
            <li>Fibonacci: f₀=0, f₁=1, fₙ=fₙ₋₁+fₙ₋₂</li>
          </ul>
        </div>
        <div class="note-box">💡 الاستقراء والتعريف التكراري متكاملان: الـ Recursive Definition يعطي طريقة طبيعية لإثبات خصائص المتتاليات بالاستقراء</div>
      </div>
      <div id="induction-flash" style="display:none"><div class="fc-container" id="fc-induction"></div></div>
      <div id="induction-quiz" style="display:none"><div id="qz-induction"></div></div>
    </div>

    <!-- COUNTING PAGE -->
    <div class="page" id="page-counting" data-ch="ch6">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 6</div>
        <h2>العد والترتيب — Counting</h2>
        <p>Sum Rule, Product Rule, Inclusion-Exclusion, Permutations, Combinations</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'counting','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'counting','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'counting','quiz')">✏️ اختبار</div>
      </div>
      <div id="counting-summary">
        <div class="summary-block">
          <h3>➕ Sum Rule & ✖️ Product Rule</h3>
          <ul>
            <li><strong style="color:var(--text)">Sum Rule</strong>: لو A و B مجموعتان منفصلتان → |A ∪ B| = |A| + |B|</li>
            <li><strong style="color:var(--text)">Product Rule</strong>: لو المهمة تتكون من خطوتين → الاحتمالات = m × n</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🔢 الترتيبات والتوافيق</h3>
          <ul>
            <li>P(n,r) = n! / (n−r)! — ترتيب r عنصر من n (الترتيب مهم)</li>
            <li>C(n,r) = n! / (r! × (n−r)!) — اختيار r عنصر من n (الترتيب غير مهم)</li>
            <li>C(n,r) = C(n, n−r)</li>
          </ul>
          <div class="formula-box">
            P(5,2) = 5×4 = 20 &nbsp;|&nbsp; C(5,2) = 10<br>
            n! = n × (n−1) × ... × 2 × 1 &nbsp;|&nbsp; 0! = 1
          </div>
        </div>
        <div class="summary-block">
          <h3>🔄 Inclusion-Exclusion</h3>
          <ul>
            <li>|A ∪ B| = |A| + |B| − |A ∩ B|</li>
            <li>|A ∪ B ∪ C| = |A|+|B|+|C| − |A∩B| − |A∩C| − |B∩C| + |A∩B∩C|</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>📐 نظرية ذات الحدين</h3>
          <ul>
            <li>(x+y)ⁿ = Σ C(n,k) × xⁿ⁻ᵏ × yᵏ</li>
            <li>مثلث باسكال: كل عنصر = مجموع العنصرين فوقه</li>
          </ul>
        </div>
      </div>
      <div id="counting-flash" style="display:none"><div class="fc-container" id="fc-counting"></div></div>
      <div id="counting-quiz" style="display:none"><div id="qz-counting"></div></div>
    </div>

    <!-- ADVANCED PAGE -->
    <div class="page" id="page-advanced" data-ch="ch8">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 8</div>
        <h2>العد المتقدم — Advanced Counting</h2>
        <p>Sequences, Recurrence Relations, Geometric & Arithmetic Sequences</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'advanced','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'advanced','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'advanced','quiz')">✏️ اختبار</div>
      </div>
      <div id="advanced-summary">
        <div class="summary-block">
          <h3>📈 المتتاليات الهندسية والحسابية</h3>
          <ul>
            <li><strong style="color:var(--text)">Arithmetic</strong>: aₙ = a₁ + (n−1)d &nbsp;|&nbsp; الفرق ثابت = d</li>
            <li><strong style="color:var(--text)">Geometric</strong>: aₙ = a₁ × rⁿ⁻¹ &nbsp;|&nbsp; النسبة ثابتة = r</li>
          </ul>
          <div class="formula-box">
            Sum Geometric: Sₙ = a(rⁿ−1)/(r−1) لـ r≠1
          </div>
        </div>
        <div class="summary-block">
          <h3>🔁 علاقات التكرار (Recurrence Relations)</h3>
          <ul>
            <li>معادلة تعرّف كل حد من المتتالية بدلالة الحدود السابقة</li>
            <li>مثال: Fibonacci: aₙ = aₙ₋₁ + aₙ₋₂</li>
            <li>الحل يتطلب: إيجاد الحل العام + تطبيق الشروط الابتدائية</li>
          </ul>
        </div>
      </div>
      <div id="advanced-flash" style="display:none"><div class="fc-container" id="fc-advanced"></div></div>
      <div id="advanced-quiz" style="display:none"><div id="qz-advanced"></div></div>
    </div>

    <!-- RELATIONS PAGE -->
    <div class="page" id="page-relations" data-ch="ch9">
      <div class="section-header">
        <div class="back" onclick="nav('home')">← رجوع للرئيسية</div>
        <div class="section-badge">CHAPTER 9</div>
        <h2>العلاقات — Relations</h2>
        <p>Binary Relations, Properties, Equivalence, Matrices, Closure</p>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="switchTab(this,'relations','summary')">📖 ملخص</div>
        <div class="tab" onclick="switchTab(this,'relations','flash')">🃏 بطاقات</div>
        <div class="tab" onclick="switchTab(this,'relations','quiz')">✏️ اختبار</div>
      </div>
      <div id="relations-summary">
        <div class="summary-block">
          <h3>🔗 تعريف العلاقة</h3>
          <ul>
            <li>علاقة ثنائية R على A: مجموعة جزئية من A × A</li>
            <li>تُمثَّل بـ: مجموعة الأزواج المرتبة / مصفوفة / جراف</li>
          </ul>
        </div>
        <div class="summary-block">
          <h3>🏷️ خصائص العلاقات</h3>
          <ul>
            <li><strong style="color:var(--green)">Reflexive</strong>: (a,a) ∈ R لكل a ∈ A</li>
            <li><strong style="color:var(--accent)">Irreflexive</strong>: (a,a) ∉ R لكل a ∈ A</li>
            <li><strong style="color:var(--amber)">Symmetric</strong>: إذا (a,b)∈R فـ (b,a)∈R</li>
            <li><strong style="color:var(--red)">Antisymmetric</strong>: إذا (a,b)∈R و(b,a)∈R فـ a=b</li>
            <li><strong style="color:var(--accent2)">Transitive</strong>: إذا (a,b)∈R و(b,c)∈R فـ (a,c)∈R</li>
          </ul>
          <div class="note-box">💡 علاقة Equivalence = Reflexive + Symmetric + Transitive معاً</div>
        </div>
        <div class="summary-block">
          <h3>🔢 تمثيل العلاقات بالمصفوفات</h3>
          <ul>
            <li>M[i][j] = 1 إذا (aᵢ, aⱼ) ∈ R &nbsp;|&nbsp; 0 إذا لم تكن</li>
            <li>Reflexive ↔ القطر الرئيسي كله 1s</li>
            <li>Symmetric ↔ المصفوفة متماثلة (M = Mᵀ)</li>
          </ul>
        </div>
      </div>
      <div id="relations-flash" style="display:none"><div class="fc-container" id="fc-relations"></div></div>
      <div id="relations-quiz" style="display:none"><div id="qz-relations"></div></div>
    </div>

  </main>
</div>

<script>
// ── DATA ──────────────────────────────────────────────────────────────
const DATA = {
  logic: {
    flash: [
      { q: 'ما الفرق بين Proposition وغير Proposition؟', a: 'Proposition: جملة خبرية لها قيمة T أو F فقط\nمثال: "2+2=5" (F) ✓\nليست Proposition: "ما الساعة؟" أو "افعل كذا"' },
      { q: 'متى تكون p → q خاطئة (False)؟', a: 'فقط عندما p = True وq = False\nبقية الحالات كلها تعطي True!' },
      { q: 'ما معنى ¬(p ∧ q)؟ وهل يساوي ¬p ∨ ¬q؟', a: 'نعم! هذا قانون De Morgan:\n¬(p ∧ q) ≡ ¬p ∨ ¬q\n¬(p ∨ q) ≡ ¬p ∧ ¬q' },
      { q: 'ما الفرق بين ∀x P(x) و ∃x P(x)؟', a: '∀x P(x): P(x) صحيحة لكل قيم x\n∃x P(x): توجد قيمة واحدة على الأقل تجعل P(x) صحيحة' },
      { q: 'ما نفي ∀x P(x)؟', a: '¬(∀x P(x)) ≡ ∃x ¬P(x)\nمثال: نفي "كل الطلاب نجحوا" = "يوجد طالب لم ينجح"' },
      { q: 'ما الفرق بين Converse وContrapositive لـ p→q؟', a: 'Converse: q → p (ليس مكافئاً)\nContrapositive: ¬q → ¬p (مكافئ دائماً لـ p→q)' },
    ],
    quiz: [
      { q: 'أي مما يلي ليس Proposition؟', opts: ['"الأرض كروية"','"2+3=6"','"ما اسمك؟"','"الرياض عاصمة السعودية"'], ans: 2, exp: 'السؤال "ما اسمك؟" ليس له قيمة True أو False، لذلك ليس Proposition.' },
      { q: 'إذا كانت p = True وq = False، ما قيمة p → q؟', opts: ['True','False','لا يمكن تحديدها','يعتمد على السياق'], ans: 1, exp: 'p → q تكون False فقط عندما p=T وq=F. هذه الحالة بالضبط.' },
      { q: 'أيهما مكافئ لـ p → q؟', opts: ['q → p','¬p ∨ q','p ∧ ¬q','¬q → ¬p فقط'], ans: 1, exp: 'p → q ≡ ¬p ∨ q. والـ Contrapositive ¬q→¬p مكافئ أيضاً، لكن الخيار الوحيد الصحيح هنا هو ¬p ∨ q.' },
      { q: 'ما نفي ∃x P(x)؟', opts: ['∃x ¬P(x)','∀x P(x)','∀x ¬P(x)','¬∃x P(x)'], ans: 2, exp: '¬(∃x P(x)) ≡ ∀x ¬P(x). مثال: نفي "يوجد طالب نجح" = "كل الطلاب رسبوا"' },
      { q: 'p ↔ q تكون True عندما:', opts: ['p=T فقط','q=F فقط','p وq لهما نفس القيمة','p=T وq=F'], ans: 2, exp: 'Biconditional صحيحة عندما يكون الطرفان بنفس القيمة: (T,T) أو (F,F).' },
    ]
  },
  sets: {
    flash: [
      { q: 'ما الفرق بين A ⊆ B و A ⊂ B؟', a: 'A ⊆ B: A مجموعة جزئية أو مساوية لـ B\nA ⊂ B: A مجموعة جزئية حقيقية (A≠B)\nكل مجموعة ⊆ نفسها، والـ ∅ ⊆ أي مجموعة' },
      { q: 'ما الفرق بين Injective وSurjective وBijective؟', a: 'Injective: عناصر مختلفة → صور مختلفة (one-to-one)\nSurjective: كل عنصر في B له سابقة (onto)\nBijective: الاثنين معاً → الدالة العكسية موجودة' },
      { q: 'ما Power Set لـ {a,b}؟', a: 'P({a,b}) = {∅, {a}, {b}, {a,b}}\nإذا |A| = n فـ |P(A)| = 2ⁿ\nهنا |A|=2 فـ |P(A)|=4' },
      { q: 'ما الفرق بين ∅ و {∅}؟', a: '∅: المجموعة الفارغة، لا تحتوي عناصر، |∅|=0\n{∅}: مجموعة تحتوي عنصراً واحداً هو ∅، |{∅}|=1' },
      { q: 'متى تكون المجموعة Countable؟', a: 'إما Finite أو لها تقابل Bijective مع ℕ\nℕ, ℤ, ℚ = Countable Infinite\nℝ = Uncountable (أكبر من عدد ℕ)' },
    ],
    quiz: [
      { q: 'إذا A = {1,2,3} وB = {2,3,4}، ما A ∩ B؟', opts: ['{1,2,3,4}','{2,3}','{1,4}','{1,2,3,4,5}'], ans: 1, exp: 'A ∩ B = العناصر المشتركة = {2,3}' },
      { q: 'كم عنصراً في P({a,b,c})؟', opts: ['3','6','8','9'], ans: 2, exp: '|P(A)| = 2^|A| = 2³ = 8' },
      { q: 'الدالة f(x) = x² من ℝ إلى ℝ هي:', opts: ['Injective فقط','Surjective فقط','Bijective','لا Injective ولا Surjective'], ans: 3, exp: 'f(2)=f(-2)=4 إذن ليست Injective. و-4 ليس في المجال المقابل إذن ليست Surjective.' },
      { q: 'A-B (الفرق) يساوي:', opts: ['A ∩ B','A ∩ Bᶜ','Aᶜ ∩ B','A ∪ Bᶜ'], ans: 1, exp: 'A-B = {x | x∈A ∧ x∉B} = A ∩ Bᶜ' },
    ]
  },
  numtheory: {
    flash: [
      { q: 'ما معنى a | b؟ ومتى يكون صحيحاً؟', a: 'a | b يعني "a يقسم b"\nيكون صحيحاً إذا وجد عدد صحيح c بحيث b = a×c\nمثال: 3|12 (12=3×4) ✓ | 3|7 ✗' },
      { q: 'كيف تحسب gcd(48, 18)؟', a: '48 = 2⁴ × 3\n18 = 2 × 3²\ngcd = 2^min(4,1) × 3^min(1,2) = 2¹ × 3¹ = 6' },
      { q: 'احسب 113 mod 24', a: '113 = 24 × 4 + 17\nإذن 113 mod 24 = 17' },
      { q: 'ما هو Caesar Cipher بـ k=3؟', a: 'تشفير: f(p) = (p+3) mod 26\nفك: f⁻¹(c) = (c-3) mod 26\nA(0)→D(3), M(12)→P(15)' },
      { q: 'ما شرط وجود الـ Affine Cipher f(p)=(ap+b) mod 26؟', a: 'يجب أن gcd(a, 26) = 1\nأي a يجب أن يكون أولياً نسبياً مع 26\nمثال: a=7 يصلح ✓ | a=2 لا يصلح ✗' },
    ],
    quiz: [
      { q: 'ما قيمة -29 mod 7؟', opts: ['−1','6','−29','1'], ans: 1, exp: '-29 = 7×(-5) + 6. الباقي يجب أن يكون ≥0 إذن -29 mod 7 = 6' },
      { q: 'gcd(120, 500) = ?', opts: ['10','20','40','60'], ans: 1, exp: '120=2³×3×5 | 500=2²×5³ → gcd=2²×5=20' },
      { q: 'أي من الأعداد التالية أولي؟', opts: ['91','97','99','100'], ans: 1, exp: '97 أولي (√97≈9.8، لا يقسمه 2,3,5,7). 91=7×13' },
      { q: 'إذا k=11، ما تشفير حرف S (=18) بـ Shift Cipher؟', opts: ['T','D','C','Y'], ans: 1, exp: 'f(18) = (18+11) mod 26 = 29 mod 26 = 3 = D' },
      { q: 'lcm(24, 36) = ?', opts: ['12','72','144','48'], ans: 1, exp: '24=2³×3 | 36=2²×3² → lcm=2³×3²=72' },
    ]
  },
  induction: {
    flash: [
      { q: 'ما الخطوتان الأساسيتان في الاستقراء الرياضي؟', a: '1. Basis Step: أثبت P(1) صحيحة\n2. Inductive Step: افترض P(k) صحيحة ثم أثبت P(k+1)\nالنتيجة: P(n) صحيحة لكل n≥1' },
      { q: 'أثبت بالاستقراء: 1+3+...+(2n-1) = n²', a: 'Basis: n=1 → LHS=1, RHS=1² ✓\nInductive: افرض صح لـ k\nLHS(k+1) = k² + (2k+1) = (k+1)² = RHS ✓' },
      { q: 'ما f(3) إذا كان f(0)=1 وf(n)=n·f(n-1)؟', a: 'هذه الـ Factorial!\nf(1) = 1×f(0) = 1×1 = 1\nf(2) = 2×f(1) = 2×1 = 2\nf(3) = 3×f(2) = 3×2 = 6 = 3!' },
      { q: 'ما أول 5 أعداد فيبوناتشي؟', a: 'f₀=0, f₁=1\nf₂=f₁+f₀=1\nf₃=f₂+f₁=2\nf₄=f₃+f₂=3\nإذن: 0, 1, 1, 2, 3, 5, 8, ...' },
      { q: 'إذا f(0)=3 وf(n+1)=2f(n)+3، ما f(3)؟', a: 'f(0)=3\nf(1)=2(3)+3=9\nf(2)=2(9)+3=21\nf(3)=2(21)+3=45' },
    ],
    quiz: [
      { q: 'في خطوة Inductive Step، ماذا نفترض؟', opts: ['P(1) صحيحة','P(n) صحيحة لكل n','P(k) صحيحة لعدد صحيح k≥1','P(k+1) صحيحة'], ans: 2, exp: 'نفترض P(k) صحيحة (Inductive Hypothesis) ثم نثبت P(k+1)' },
      { q: 'ما ناتج 1+2+3+...+100 بالصيغة n(n+1)/2؟', opts: ['5000','5050','4950','10000'], ans: 1, exp: 'n=100 → 100×101/2 = 10100/2 = 5050' },
      { q: 'إذا f(0)=3, f(n+1)=2f(n), ما f(4)؟', opts: ['24','48','96','384'], ans: 1, exp: 'f(0)=3, f(1)=6, f(2)=12, f(3)=24, f(4)=48' },
      { q: 'مجموع 1²+2²+...+n² = ?', opts: ['n(n+1)/2','n²(n+1)²/4','n(n+1)(2n+1)/6','n(n+1)(n+2)/6'], ans: 2, exp: 'الصيغة الصحيحة هي n(n+1)(2n+1)/6' },
    ]
  },
  counting: {
    flash: [
      { q: 'ما الفرق بين Sum Rule وProduct Rule؟', a: 'Sum Rule: لو A∩B=∅ → |A∪B|=|A|+|B|\nاستخدمه عندما تختار من مجموعة OR أخرى\nProduct Rule: خطوة أولى m خيار × خطوة ثانية n خيار = m×n' },
      { q: 'ما الفرق بين Permutation وCombination؟', a: 'Permutation P(n,r): الترتيب مهم\nP(n,r) = n!/(n-r)!\nCombination C(n,r): الترتيب غير مهم\nC(n,r) = n!/(r!(n-r)!)' },
      { q: 'احسب C(6,2) وP(6,2)', a: 'C(6,2) = 6!/(2!×4!) = (6×5)/(2×1) = 15\nP(6,2) = 6!/(4!) = 6×5 = 30' },
      { q: 'في كم طريقة يمكن ترتيب كلمة MATH؟', a: 'كلها حروف مختلفة → 4! = 24 طريقة\nلو كان في حروف مكررة مثل NOON:\n4! / 2! = 12 (لأن N مكررة مرتين)' },
      { q: 'ما معنى Inclusion-Exclusion؟', a: '|A∪B| = |A| + |B| - |A∩B|\nنطرح التقاطع لأننا حسبناه مرتين\nمثال: |A|=30, |B|=20, |A∩B|=10 → |A∪B|=40' },
    ],
    quiz: [
      { q: 'كم عدد كلمات (bit strings) طولها 4 بتات تبدأ بـ 1؟', opts: ['4','8','16','2'], ans: 1, exp: 'الأولى ثابتة=1، الباقي 3 بتات حرة: 2×2×2 = 8' },
      { q: 'في كم طريقة يختار فريق 3 طلاب من 10؟', opts: ['30','120','720','210'], ans: 2, exp: 'C(10,3) = 10!/(3!×7!) = (10×9×8)/(3×2×1) = 120' },
      { q: 'C(n,r) = C(n, ?)', opts: ['r+1','r−1','n−r','n+r'], ans: 2, exp: 'C(n,r) = C(n, n-r). مثال: C(5,2)=C(5,3)=10' },
      { q: 'P(5,3) = ?', opts: ['10','60','20','120'], ans: 1, exp: 'P(5,3) = 5!/(5-3)! = 5!/2! = 120/2 = 60' },
      { q: '|A|=50, |B|=30, |A∩B|=10. ما |A∪B|؟', opts: ['70','80','90','10'], ans: 0, exp: '|A∪B| = 50 + 30 - 10 = 70' },
    ]
  },
  advanced: {
    flash: [
      { q: 'ما الفرق بين المتتالية الحسابية والهندسية؟', a: 'Arithmetic: الفرق بين حدود متتالية ثابت (d)\naₙ = a₁ + (n-1)d\nGeometric: النسبة بين حدود متتالية ثابتة (r)\naₙ = a₁ × rⁿ⁻¹' },
      { q: 'ما مجموع المتتالية الهندسية 1+2+4+...+2ⁿ؟', a: 'Sₙ = a(rⁿ⁺¹-1)/(r-1)\nهنا a=1, r=2, n حدود\n= (2ⁿ⁺¹ - 1)/(2-1) = 2ⁿ⁺¹ - 1' },
      { q: 'ما المتتالية: 3, 6, 12, 24, ...؟ وما الحد العاشر؟', a: 'هندسية بـ a₁=3, r=2\na₁₀ = 3 × 2⁹ = 3 × 512 = 1536' },
      { q: 'ما هي Recurrence Relation؟', a: 'معادلة تعرّف كل حد aₙ بدلالة حدود سابقة\nمثال: aₙ = aₙ₋₁ + 2، a₁ = 3\n→ 3, 5, 7, 9, ... (حسابية d=2)' },
    ],
    quiz: [
      { q: 'المتتالية 2, 5, 8, 11, ... هي:', opts: ['هندسية r=3','حسابية d=3','هندسية r=2.5','حسابية d=2.5'], ans: 1, exp: 'الفرق بين الحدود = 3 ثابت → حسابية بـ d=3' },
      { q: 'الحد العاشر للمتتالية 1, 2, 4, 8, ... هو:', opts: ['512','256','1024','128'], ans: 0, exp: 'هندسية a₁=1, r=2 → a₁₀ = 2⁹ = 512' },
      { q: 'إذا aₙ = 2aₙ₋₁ و a₁=3، ما a₄؟', opts: ['12','24','48','6'], ans: 1, exp: 'a₁=3, a₂=6, a₃=12, a₄=24' },
      { q: 'مجموع 1+2+4+...+2¹⁰ = ?', opts: ['1023','2047','2048','1024'], ans: 1, exp: '2¹¹ - 1 = 2048 - 1 = 2047' },
    ]
  },
  relations: {
    flash: [
      { q: 'متى تكون العلاقة Reflexive؟', a: '(a,a) ∈ R لكل a ∈ A\nمثال: R = {(1,1),(1,2),(2,2),(3,3)}\n→ Reflexive على {1,2,3}' },
      { q: 'ما الفرق بين Symmetric وAntisymmetric؟', a: 'Symmetric: (a,b)∈R → (b,a)∈R\nAntisymmetric: (a,b)∈R ∧ (b,a)∈R → a=b\nيمكن أن تكون العلاقة الاثنين معاً إذا كل أزواجها من شكل (a,a)' },
      { q: 'كيف تحدد Transitivity من المصفوفة؟', a: 'Transitive: لو M[i][j]=1 وM[j][k]=1 → M[i][k]=1\nبمعنى: لو يوجد مسار من i إلى j إلى k\nفيجب أن يوجد حافة مباشرة من i إلى k' },
      { q: 'ما شروط علاقة التكافؤ (Equivalence Relation)؟', a: 'يجب أن تكون:\n1. Reflexive\n2. Symmetric\n3. Transitive\nمثال: "=" على ℤ هي Equivalence Relation' },
      { q: 'كيف تمثل العلاقة R={(1,2),(2,3),(1,3)} بمصفوفة على {1,2,3}؟', a: '     1  2  3\n1  [ 0  1  1 ]\n2  [ 0  0  1 ]\n3  [ 0  0  0 ]\nملاحظة: (1,3) موجود → Transitive!' },
    ],
    quiz: [
      { q: 'العلاقة R = {(1,1),(2,2),(3,3)} على {1,2,3} هي:', opts: ['Reflexive فقط','Symmetric فقط','Reflexive, Symmetric, Transitive','Antisymmetric فقط'], ans: 2, exp: 'Reflexive ✓ (كل (a,a) موجود) | Symmetric ✓ (لا أزواج غير قطرية) | Transitive ✓' },
      { q: 'في المصفوفة، Reflexive تعني:', opts: ['المصفوفة متماثلة','القطر الرئيسي كله أصفار','القطر الرئيسي كله آحاد','الصفوف متساوية'], ans: 2, exp: 'Reflexive ↔ كل (a,a) ∈ R ↔ كل عناصر القطر الرئيسي = 1' },
      { q: 'أيٌّ من هذه علاقات التكافؤ؟', opts: ['"<" على ℤ','"≤" على ℤ','"=" على ℤ','علاقة الأخوة'], ans: 2, exp: '"=" هي Reflexive+Symmetric+Transitive. "<" ليست Reflexive. "≤" ليست Symmetric.' },
      { q: 'Composite Relation R∘S تعني:', opts: ['R ∩ S','اتحاد R وS','(a,c) إذا وجد b بحيث (a,b)∈S و(b,c)∈R','نفي R'], ans: 2, exp: 'R∘S: نطبق S أولاً ثم R. (a,c)∈R∘S إذا وجد b: (a,b)∈S و(b,c)∈R' },
      { q: 'العلاقة "aRb إذا a≠b" على {1,2,3} هي:', opts: ['Reflexive','Irreflexive وSymmetric','Transitive','Antisymmetric'], ans: 1, exp: 'لا توجد (a,a) → Irreflexive. إذا a≠b فـ b≠a → Symmetric. ليست Transitive: (1,2)∧(2,1) لكن (1,1)∉R.' },
    ]
  }
};

// ── STATE ─────────────────────────────────────────────────────────────
let visited = new Set();
let fcState = {};
let qzState = {};

// ── NAVIGATION ────────────────────────────────────────────────────────
function nav(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  const ni = document.querySelector(`.nav-item[onclick*="'${id}'"]`);
  if (ni) ni.classList.add('active');
  if (id !== 'home') {
    visited.add(id);
    updateProgress();
    initFlash(id);
    initQuiz(id);
  }
  window.scrollTo(0, 0);
}

function updateProgress() {
  const total = 7;
  const done = visited.size;
  document.getElementById('prog-fill').style.width = (done/total*100) + '%';
  document.getElementById('prog-label').textContent = done + ' / ' + total + ' مواضيع';
}

// ── TABS ──────────────────────────────────────────────────────────────
function switchTab(el, topic, tab) {
  const parent = el.closest('.page');
  parent.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  el.classList.add('active');
  const tabs = ['summary','flash','quiz'];
  tabs.forEach(t => {
    const el2 = document.getElementById(topic + '-' + t);
    if (el2) el2.style.display = (t === tab) ? 'block' : 'none';
  });
}

// ── FLASHCARDS ────────────────────────────────────────────────────────
function initFlash(topic) {
  if (fcState[topic]) return;
  fcState[topic] = { idx: 0, flipped: false, known: 0, skipped: 0 };
  renderFlash(topic);
}

function renderFlash(topic) {
  const s = fcState[topic];
  const cards = DATA[topic].flash;
  const container = document.getElementById('fc-' + topic);
  if (!container) return;
  if (s.idx >= cards.length) {
    container.innerHTML = `<div style="text-align:center;padding:40px 20px">
      <div style="font-size:40px;margin-bottom:16px">🎉</div>
      <div style="font-size:18px;font-weight:600;color:var(--text);margin-bottom:8px">انتهيت من كل البطاقات!</div>
      <div style="color:var(--text2);font-size:13px;margin-bottom:20px">عرفت: <span style="color:var(--green)">${s.known}</span> | راجع: <span style="color:var(--red)">${s.skipped}</span></div>
      <button class="btn-primary" onclick="fcState['${topic}']={idx:0,flipped:false,known:0,skipped:0};renderFlash('${topic}')">إعادة من البداية</button>
    </div>`;
    return;
  }
  const card = cards[s.idx];
  s.flipped = false;
  container.innerHTML = `
    <div class="fc-container">
      <div class="fc-wrapper">
        <div class="fc-card" id="fc-card-${topic}" onclick="flipCard('${topic}')">
          <div class="fc-face front">
            <div class="fc-label">سؤال ${s.idx+1} / ${cards.length}</div>
            <div class="fc-q">${card.q}</div>
          </div>
          <div class="fc-face back">
            <div class="fc-label">الجواب</div>
            <div class="fc-a">${card.a.replace(/\n/g,'<br>')}</div>
          </div>
        </div>
      </div>
      <div class="fc-hint" id="fc-hint-${topic}">اضغط على البطاقة لتقليبها</div>
      <div class="fc-controls" id="fc-btns-${topic}" style="display:none">
        <button class="fc-btn skip" onclick="fcAction('${topic}','skip')">🔄 راجع</button>
        <button class="fc-btn know" onclick="fcAction('${topic}','know')">✓ عارفه</button>
      </div>
      <div class="fc-counter">عرفت: <span style="color:var(--green)">${s.known}</span> | راجع: <span style="color:var(--red)">${s.skipped}</span></div>
    </div>`;
}

function flipCard(topic) {
  const s = fcState[topic];
  s.flipped = !s.flipped;
  const card = document.getElementById('fc-card-' + topic);
  if (card) card.classList.toggle('flipped', s.flipped);
  const btns = document.getElementById('fc-btns-' + topic);
  const hint = document.getElementById('fc-hint-' + topic);
  if (btns) btns.style.display = s.flipped ? 'flex' : 'none';
  if (hint) hint.style.display = s.flipped ? 'none' : 'block';
}

function fcAction(topic, action) {
  const s = fcState[topic];
  if (action === 'know') s.known++;
  else s.skipped++;
  s.idx++;
  renderFlash(topic);
}

// ── QUIZ ──────────────────────────────────────────────────────────────
function initQuiz(topic) {
  if (qzState[topic]) return;
  qzState[topic] = { idx: 0, score: 0, answered: false };
  renderQuiz(topic);
}

function renderQuiz(topic) {
  const s = qzState[topic];
  const qs = DATA[topic].quiz;
  const container = document.getElementById('qz-' + topic);
  if (!container) return;
  if (s.idx >= qs.length) {
    const pct = Math.round(s.score / qs.length * 100);
    const emoji = pct >= 80 ? '🏆' : pct >= 60 ? '👍' : '📚';
    container.innerHTML = `<div class="quiz-score">
      <div style="font-size:40px;margin-bottom:16px">${emoji}</div>
      <div class="big">${s.score}/${qs.length}</div>
      <div class="label">نتيجتك: ${pct}%</div>
      <div style="margin-top:24px;display:flex;gap:10px;justify-content:center">
        <button class="btn-primary" onclick="qzState['${topic}']={idx:0,score:0,answered:false};renderQuiz('${topic}')">إعادة الاختبار</button>
      </div>
    </div>`;
    return;
  }
  const q = qs[s.idx];
  s.answered = false;
  container.innerHTML = `<div class="quiz-q">
    <div class="quiz-qnum">سؤال ${s.idx+1} / ${qs.length}</div>
    <div class="quiz-qtext">${q.q}</div>
    <div class="quiz-opts">
      ${q.opts.map((o,i)=>`<div class="quiz-opt" id="qopt-${topic}-${i}" onclick="answerQuiz('${topic}',${i})">${o}</div>`).join('')}
    </div>
    <div class="quiz-exp" id="qexp-${topic}">${q.exp}</div>
  </div>
  <div style="margin-top:12px;display:flex;justify-content:flex-end" id="qnext-${topic}" style="display:none"></div>`;
}

function answerQuiz(topic, chosen) {
  const s = qzState[topic];
  if (s.answered) return;
  s.answered = true;
  const q = DATA[topic].quiz[s.idx];
  for (let i = 0; i < q.opts.length; i++) {
    const el = document.getElementById(`qopt-${topic}-${i}`);
    if (el) {
      el.style.pointerEvents = 'none';
      if (i === q.ans) el.classList.add('correct');
      else if (i === chosen && chosen !== q.ans) el.classList.add('wrong');
    }
  }
  if (chosen === q.ans) s.score++;
  const exp = document.getElementById('qexp-' + topic);
  if (exp) exp.classList.add('show');
  const next = document.getElementById('qnext-' + topic);
  if (next) {
    next.style.display = 'flex';
    next.innerHTML = `<button class="btn-primary" onclick="qzState['${topic}'].idx++;qzState['${topic}'].answered=false;renderQuiz('${topic}')">${s.idx+1 < DATA[topic].quiz.length ? 'السؤال التالي ←' : 'عرض النتيجة 🏁'}</button>`;
  }
}
</script>
</body>
</html>
