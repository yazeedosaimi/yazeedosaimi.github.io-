<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CS285 — Discrete Math Study Hub</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg:       #f7f5f0;
  --paper:    #ffffff;
  --ink:      #1a1814;
  --ink2:     #5a5650;
  --ink3:     #b0ada8;
  --rule:     #e8e5e0;
  --rule2:    #d0cdc8;
  --ch1:      #c8523a;
  --ch2:      #3a7dc8;
  --ch4:      #4ab87a;
  --ch5:      #e8a030;
  --ch6:      #9b59b6;
  --ch8:      #e05080;
  --ch9:      #2ab8b8;
  --mono:     'DM Mono', monospace;
  --serif:    'DM Serif Display', serif;
  --sans:     'DM Sans', sans-serif;
  --r:        8px;
  --r2:       14px;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background: var(--bg);
  color: var(--ink);
  font-family: var(--sans);
  font-size: 15px;
  line-height: 1.65;
  min-height: 100vh;
}

/* ── SHELL ── */
.shell { display: flex; min-height: 100vh; }

/* ── SIDEBAR ── */
.sidebar {
  width: 248px; flex-shrink: 0;
  background: var(--ink);
  color: #f0ece4;
  padding: 28px 0;
  position: sticky; top: 0; height: 100vh;
  overflow-y: auto;
  display: flex; flex-direction: column;
}
.sb-brand {
  padding: 0 22px 24px;
  border-bottom: 1px solid rgba(255,255,255,.08);
  margin-bottom: 20px;
}
.sb-course {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: .14em;
  color: rgba(255,255,255,.35);
  margin-bottom: 6px;
  text-transform: uppercase;
}
.sb-title {
  font-family: var(--serif);
  font-size: 19px;
  color: #f0ece4;
  line-height: 1.25;
}

.sb-section { padding: 0 12px; margin-bottom: 6px; }
.sb-sec-label {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: .16em;
  color: rgba(255,255,255,.25);
  text-transform: uppercase;
  padding: 0 10px;
  margin-bottom: 5px;
}
.sb-item {
  display: flex; align-items: center; gap: 10px;
  padding: 8px 10px;
  border-radius: var(--r);
  cursor: pointer;
  color: rgba(255,255,255,.5);
  font-size: 13px;
  transition: all .15s;
  border: 1px solid transparent;
}
.sb-item:hover { background: rgba(255,255,255,.07); color: rgba(255,255,255,.85); }
.sb-item.active { background: rgba(255,255,255,.1); color: #fff; border-color: rgba(255,255,255,.12); }
.sb-ch {
  font-family: var(--mono);
  font-size: 9px;
  min-width: 26px;
  color: rgba(255,255,255,.25);
}
.sb-item.active .sb-ch { color: rgba(255,255,255,.45); }
.sb-dot {
  width: 6px; height: 6px; border-radius: 50%;
  background: currentColor; flex-shrink: 0; opacity: .5;
}

.sb-footer {
  margin-top: auto;
  padding: 20px 22px 0;
  border-top: 1px solid rgba(255,255,255,.08);
}
.sb-prog-label { font-size: 11px; color: rgba(255,255,255,.3); font-family: var(--mono); margin-bottom: 8px; }
.sb-prog-bar { height: 3px; background: rgba(255,255,255,.1); border-radius: 99px; overflow: hidden; }
.sb-prog-fill { height: 100%; background: #f0ece4; border-radius: 99px; transition: width .5s ease; }
.sb-prog-count { font-family: var(--mono); font-size: 10px; color: rgba(255,255,255,.25); margin-top: 6px; }

/* ── MAIN ── */
.main { flex: 1; padding: 40px 44px 60px; max-width: 900px; }

.page { display: none; animation: fadeUp .22s ease; }
.page.active { display: block; }
@keyframes fadeUp { from { opacity:0; transform:translateY(6px); } to { opacity:1; transform:none; } }

/* ── HOME ── */
.home-header { margin-bottom: 40px; }
.home-eyebrow {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: .14em;
  color: var(--ink3);
  text-transform: uppercase;
  margin-bottom: 12px;
}
.home-title { font-family: var(--serif); font-size: 36px; color: var(--ink); line-height: 1.15; margin-bottom: 10px; }
.home-sub { color: var(--ink2); font-size: 14px; max-width: 480px; }

.topic-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(230px, 1fr)); gap: 12px; }
.topic-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: var(--r2);
  padding: 20px 20px 16px;
  cursor: pointer;
  transition: all .18s;
  position: relative;
  overflow: hidden;
}
.topic-card::after {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: var(--accent, var(--ink));
  border-radius: var(--r2) var(--r2) 0 0;
}
.topic-card:hover { border-color: var(--rule2); transform: translateY(-3px); box-shadow: 0 8px 24px rgba(0,0,0,.07); }
.tc-ch { font-family: var(--mono); font-size: 9px; letter-spacing: .12em; color: var(--ink3); text-transform: uppercase; margin-bottom: 10px; }
.tc-icon { font-size: 22px; margin-bottom: 8px; }
.tc-title { font-size: 14px; font-weight: 600; color: var(--ink); margin-bottom: 5px; }
.tc-desc { font-size: 12px; color: var(--ink2); line-height: 1.45; margin-bottom: 12px; }
.tc-tags { display: flex; flex-wrap: wrap; gap: 4px; }
.tc-tag { font-family: var(--mono); font-size: 10px; padding: 2px 7px; border-radius: 4px; background: var(--bg); color: var(--ink3); border: 1px solid var(--rule); }

/* ── TOPIC PAGE ── */
.tp-header { margin-bottom: 28px; padding-bottom: 22px; border-bottom: 1px solid var(--rule); }
.tp-back { font-family: var(--mono); font-size: 11px; color: var(--ink3); cursor: pointer; margin-bottom: 14px; display: inline-flex; align-items: center; gap: 5px; transition: color .15s; }
.tp-back:hover { color: var(--ink); }
.tp-badge {
  display: inline-flex; align-items: center; gap: 6px;
  font-family: var(--mono); font-size: 10px;
  background: var(--accent-bg, var(--bg));
  color: var(--accent, var(--ink2));
  border: 1px solid var(--accent-border, var(--rule));
  border-radius: 6px; padding: 4px 10px;
  margin-bottom: 10px;
  text-transform: uppercase; letter-spacing: .1em;
}
.tp-title { font-family: var(--serif); font-size: 26px; color: var(--ink); margin-bottom: 6px; line-height: 1.2; }
.tp-desc { color: var(--ink2); font-size: 13px; }

/* ── TABS ── */
.tabs { display: flex; gap: 0; margin-bottom: 26px; border-bottom: 1px solid var(--rule); }
.tab { padding: 10px 20px; font-size: 13px; cursor: pointer; color: var(--ink3); transition: all .15s; border-bottom: 2px solid transparent; margin-bottom: -1px; }
.tab:hover { color: var(--ink2); }
.tab.active { color: var(--ink); border-bottom-color: var(--ink); font-weight: 500; }

/* ── SUMMARY ── */
.sum-block {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: var(--r2);
  padding: 22px 24px;
  margin-bottom: 14px;
}
.sum-block h3 {
  font-size: 13px;
  font-weight: 600;
  color: var(--ink);
  margin-bottom: 14px;
  display: flex; align-items: center; gap: 8px;
  padding-bottom: 10px;
  border-bottom: 1px solid var(--rule);
}
.sum-block ul { list-style: none; }
.sum-block li {
  display: flex; gap: 10px;
  padding: 6px 0;
  font-size: 13.5px;
  color: var(--ink2);
  border-bottom: 1px solid var(--rule);
}
.sum-block li:last-child { border-bottom: none; }
.sum-block li::before { content: '—'; color: var(--ink3); flex-shrink: 0; font-family: var(--mono); }
.sum-block li strong { color: var(--ink); }
.formula {
  font-family: var(--mono);
  font-size: 12.5px;
  background: var(--bg);
  border: 1px solid var(--rule2);
  border-left: 3px solid var(--accent, var(--ink));
  border-radius: 0 var(--r) var(--r) 0;
  padding: 12px 16px;
  margin: 12px 0;
  color: var(--ink);
  line-height: 1.7;
}
.callout {
  background: #fffbf0;
  border: 1px solid #f0e8c0;
  border-radius: var(--r);
  padding: 11px 15px;
  margin: 10px 0;
  font-size: 13px;
  color: #7a6010;
}

/* ── FLASHCARDS ── */
.fc-wrap { max-width: 540px; margin: 0 auto; }
.fc-scene { perspective: 1200px; height: 210px; margin-bottom: 20px; }
.fc-card {
  width: 100%; height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform .5s cubic-bezier(.4,0,.2,1);
  cursor: pointer;
}
.fc-card.flipped { transform: rotateY(180deg); }
.fc-face {
  position: absolute; inset: 0;
  backface-visibility: hidden;
  border-radius: var(--r2);
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  padding: 28px 32px;
  text-align: center;
}
.fc-face.front {
  background: var(--paper);
  border: 1px solid var(--rule);
}
.fc-face.back {
  background: var(--ink);
  border: 1px solid var(--ink);
  transform: rotateY(180deg);
}
.fc-face-label { font-family: var(--mono); font-size: 9px; letter-spacing: .14em; text-transform: uppercase; margin-bottom: 14px; }
.fc-face.front .fc-face-label { color: var(--ink3); }
.fc-face.back .fc-face-label { color: rgba(255,255,255,.3); }
.fc-q { font-size: 15px; font-weight: 500; color: var(--ink); line-height: 1.5; }
.fc-a { font-family: var(--mono); font-size: 12.5px; color: #d0c8b8; line-height: 1.7; white-space: pre-line; }
.fc-hint { text-align: center; font-size: 11px; color: var(--ink3); margin-bottom: 14px; font-family: var(--mono); }
.fc-controls { display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 14px; }
.fc-btn {
  padding: 9px 22px; border-radius: var(--r);
  font-size: 13px; font-family: var(--sans);
  cursor: pointer; transition: all .14s;
  border: 1px solid var(--rule2);
  background: var(--paper);
  color: var(--ink2);
}
.fc-btn:hover { border-color: var(--ink2); color: var(--ink); }
.fc-btn.good { border-color: #4ab87a; color: #2a8050; }
.fc-btn.good:hover { background: #f0fbf5; }
.fc-btn.again { border-color: #e05050; color: #c03030; }
.fc-btn.again:hover { background: #fff5f5; }
.fc-tally { text-align: center; font-family: var(--mono); font-size: 11px; color: var(--ink3); }
.fc-prog { height: 3px; background: var(--rule); border-radius: 99px; margin-bottom: 16px; overflow: hidden; }
.fc-prog-fill { height: 100%; background: var(--accent, var(--ink)); border-radius: 99px; transition: width .4s; }

/* ── QUIZ ── */
.qz-block {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: var(--r2);
  padding: 24px;
  margin-bottom: 14px;
}
.qz-num { font-family: var(--mono); font-size: 9px; letter-spacing: .14em; color: var(--ink3); text-transform: uppercase; margin-bottom: 10px; }
.qz-text { font-size: 15px; font-weight: 500; color: var(--ink); margin-bottom: 20px; line-height: 1.55; }
.qz-opts { display: grid; gap: 8px; }
.qz-opt {
  padding: 12px 16px;
  border-radius: var(--r);
  border: 1px solid var(--rule);
  background: var(--bg);
  color: var(--ink2);
  font-size: 13.5px;
  cursor: pointer;
  transition: all .14s;
  text-align: left;
}
.qz-opt:hover:not([disabled]) { border-color: var(--rule2); color: var(--ink); background: var(--paper); }
.qz-opt.correct { border-color: #4ab87a; color: #1a6040; background: #f0fbf5; font-weight: 500; }
.qz-opt.wrong { border-color: #e08080; color: #902020; background: #fff5f5; }
.qz-exp {
  margin-top: 14px; padding: 12px 16px;
  background: #f8f6f0; border: 1px solid var(--rule);
  border-left: 3px solid var(--accent, var(--ink));
  border-radius: 0 var(--r) var(--r) 0;
  font-size: 13px; color: var(--ink2);
  display: none;
}
.qz-exp.show { display: block; }
.qz-next-row { display: flex; justify-content: flex-end; margin-top: 14px; }

/* ── SCORE ── */
.score-screen { text-align: center; padding: 50px 20px; }
.score-emoji { font-size: 48px; margin-bottom: 16px; }
.score-num { font-family: var(--serif); font-size: 64px; color: var(--ink); line-height: 1; }
.score-denom { font-family: var(--mono); font-size: 18px; color: var(--ink3); }
.score-label { color: var(--ink2); font-size: 14px; margin-top: 8px; }

/* ── BUTTONS ── */
.btn {
  display: inline-flex; align-items: center; gap: 7px;
  padding: 10px 22px; border-radius: var(--r);
  font-size: 13px; font-family: var(--sans); font-weight: 500;
  cursor: pointer; transition: all .15s;
}
.btn-dark { background: var(--ink); color: #f0ece4; border: 1px solid var(--ink); }
.btn-dark:hover { background: #2e2a24; }
.btn-outline { background: transparent; color: var(--ink2); border: 1px solid var(--rule2); }
.btn-outline:hover { border-color: var(--ink2); color: var(--ink); }

/* ── DONE CARD ── */
.done-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: var(--r2);
  padding: 36px;
  text-align: center;
}
.done-card p { color: var(--ink2); font-size: 13px; margin: 8px 0 24px; }

/* scrollbar */
::-webkit-scrollbar { width: 5px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--rule2); border-radius: 99px; }

@media (max-width: 720px) {
  .sidebar { display: none; }
  .main { padding: 24px 18px 48px; }
}
</style>
</head>
<body>
<div class="shell">

<!-- ── SIDEBAR ── -->
<aside class="sidebar">
  <div class="sb-brand">
    <div class="sb-course">CS285 · Discrete Math</div>
    <div class="sb-title">Study<br>Hub</div>
  </div>

  <div class="sb-section">
    <div class="sb-sec-label">Overview</div>
    <div class="sb-item active" onclick="nav('home')">
      <span class="sb-ch">—</span> All Topics
    </div>
  </div>

  <div class="sb-section">
    <div class="sb-sec-label">Chapters</div>
    <div class="sb-item" onclick="nav('logic')"><span class="sb-ch">ch1</span><span class="sb-dot" style="color:#c8523a"></span> Logic &amp; Propositions</div>
    <div class="sb-item" onclick="nav('sets')"><span class="sb-ch">ch2</span><span class="sb-dot" style="color:#3a7dc8"></span> Sets &amp; Functions</div>
    <div class="sb-item" onclick="nav('numtheory')"><span class="sb-ch">ch4</span><span class="sb-dot" style="color:#4ab87a"></span> Number Theory</div>
    <div class="sb-item" onclick="nav('induction')"><span class="sb-ch">ch5</span><span class="sb-dot" style="color:#e8a030"></span> Induction &amp; Recursion</div>
    <div class="sb-item" onclick="nav('counting')"><span class="sb-ch">ch6</span><span class="sb-dot" style="color:#9b59b6"></span> Counting</div>
    <div class="sb-item" onclick="nav('advanced')"><span class="sb-ch">ch8</span><span class="sb-dot" style="color:#e05080"></span> Advanced Counting</div>
    <div class="sb-item" onclick="nav('relations')"><span class="sb-ch">ch9</span><span class="sb-dot" style="color:#2ab8b8"></span> Relations</div>
  </div>

  <div class="sb-footer">
    <div class="sb-prog-label">Progress</div>
    <div class="sb-prog-bar"><div class="sb-prog-fill" id="prog-fill" style="width:0%"></div></div>
    <div class="sb-prog-count" id="prog-count">0 / 7 topics visited</div>
  </div>
</aside>

<!-- ── MAIN ── -->
<main class="main">

<!-- HOME -->
<div class="page active" id="page-home">
  <div class="home-header">
    <div class="home-eyebrow">// Discrete Mathematics · CS285</div>
    <h1 class="home-title">What are we<br>studying today?</h1>
    <p class="home-sub">Pick a chapter — each has a summary, flashcards, and a short quiz.</p>
  </div>
  <div class="topic-grid">
    <div class="topic-card" onclick="nav('logic')" style="--accent:#c8523a;--accent-bg:#fdf3f1;--accent-border:#f0d0c8">
      <div class="tc-ch">Chapter 1</div>
      <div class="tc-icon">🧠</div>
      <div class="tc-title">Logic &amp; Propositions</div>
      <div class="tc-desc">Connectives, truth tables, predicates, quantifiers, inference rules.</div>
      <div class="tc-tags"><span class="tc-tag">¬ ∧ ∨ →</span><span class="tc-tag">Truth Table</span><span class="tc-tag">∀ ∃</span></div>
    </div>
    <div class="topic-card" onclick="nav('sets')" style="--accent:#3a7dc8;--accent-bg:#f0f5fd;--accent-border:#c8d8f0">
      <div class="tc-ch">Chapter 2</div>
      <div class="tc-icon">🔵</div>
      <div class="tc-title">Sets &amp; Functions</div>
      <div class="tc-desc">Set notation, operations, function types, cardinality, sequences.</div>
      <div class="tc-tags"><span class="tc-tag">Subset</span><span class="tc-tag">Bijection</span><span class="tc-tag">Power Set</span></div>
    </div>
    <div class="topic-card" onclick="nav('numtheory')" style="--accent:#4ab87a;--accent-bg:#f0fbf5;--accent-border:#b8e8d0">
      <div class="tc-ch">Chapter 4</div>
      <div class="tc-icon">🔐</div>
      <div class="tc-title">Number Theory</div>
      <div class="tc-desc">Divisibility, primes, GCD/LCM, modular arithmetic, cryptography.</div>
      <div class="tc-tags"><span class="tc-tag">GCD</span><span class="tc-tag">mod</span><span class="tc-tag">Caesar</span></div>
    </div>
    <div class="topic-card" onclick="nav('induction')" style="--accent:#e8a030;--accent-bg:#fdf8ee;--accent-border:#f0d898">
      <div class="tc-ch">Chapter 5</div>
      <div class="tc-icon">🔁</div>
      <div class="tc-title">Induction &amp; Recursion</div>
      <div class="tc-desc">Mathematical induction steps, recursive definitions, Fibonacci.</div>
      <div class="tc-tags"><span class="tc-tag">Basis</span><span class="tc-tag">Inductive</span><span class="tc-tag">Recursive</span></div>
    </div>
    <div class="topic-card" onclick="nav('counting')" style="--accent:#9b59b6;--accent-bg:#f7f0fd;--accent-border:#d8c0f0">
      <div class="tc-ch">Chapter 6</div>
      <div class="tc-icon">🔢</div>
      <div class="tc-title">Counting</div>
      <div class="tc-desc">Sum/product rules, inclusion-exclusion, permutations, combinations.</div>
      <div class="tc-tags"><span class="tc-tag">P(n,r)</span><span class="tc-tag">C(n,r)</span><span class="tc-tag">Binomial</span></div>
    </div>
    <div class="topic-card" onclick="nav('advanced')" style="--accent:#e05080;--accent-bg:#fdf0f4;--accent-border:#f0c0d0">
      <div class="tc-ch">Chapter 8</div>
      <div class="tc-icon">📈</div>
      <div class="tc-title">Advanced Counting</div>
      <div class="tc-desc">Sequences, recurrence relations, geometric &amp; arithmetic series.</div>
      <div class="tc-tags"><span class="tc-tag">Geometric</span><span class="tc-tag">Arithmetic</span><span class="tc-tag">Recurrence</span></div>
    </div>
    <div class="topic-card" onclick="nav('relations')" style="--accent:#2ab8b8;--accent-bg:#f0fbfb;--accent-border:#b0e8e8">
      <div class="tc-ch">Chapter 9</div>
      <div class="tc-icon">🔗</div>
      <div class="tc-title">Relations</div>
      <div class="tc-desc">Binary relations, reflexivity, symmetry, transitivity, matrices.</div>
      <div class="tc-tags"><span class="tc-tag">Reflexive</span><span class="tc-tag">Symmetric</span><span class="tc-tag">Transitive</span></div>
    </div>
  </div>
</div>

<!-- ── CH1: LOGIC ── -->
<div class="page" id="page-logic" style="--accent:#c8523a;--accent-bg:#fdf3f1;--accent-border:#f0d0c8">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 1</div>
    <div class="tp-title">Logic &amp; Propositions</div>
    <div class="tp-desc">Propositional logic, connectives, truth tables, predicates, quantifiers, and rules of inference.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'logic','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'logic','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'logic','quiz')">Quiz</div>
  </div>
  <div id="logic-summary">
    <div class="sum-block">
      <h3>📌 What is a Proposition?</h3>
      <ul>
        <li>A declarative sentence that is either <strong>True</strong> or <strong>False</strong> — never both.</li>
        <li><strong>Is a proposition:</strong> "2 + 2 = 5" (F), "Riyadh is the capital of SA" (T)</li>
        <li><strong>Not a proposition:</strong> "What time is it?" or "Do your homework."</li>
        <li>Propositional variables: <strong>p, q, r, s</strong> — represent any proposition.</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>⚡ Logical Connectives</h3>
      <ul>
        <li><strong>¬p</strong> — Negation (NOT): flips the truth value</li>
        <li><strong>p ∧ q</strong> — Conjunction (AND): true only when both are true</li>
        <li><strong>p ∨ q</strong> — Disjunction (OR): true when at least one is true</li>
        <li><strong>p → q</strong> — Implication: false <em>only</em> when p=T and q=F</li>
        <li><strong>p ↔ q</strong> — Biconditional: true when p and q have the same value</li>
      </ul>
      <div class="formula">p → q ≡ ¬p ∨ q &nbsp;|&nbsp; Contrapositive: ¬q → ¬p (logically equivalent to p → q)</div>
    </div>
    <div class="sum-block">
      <h3>🔍 Quantifiers</h3>
      <ul>
        <li><strong>∀x P(x)</strong> — Universal: P(x) holds for all x in the domain</li>
        <li><strong>∃x P(x)</strong> — Existential: P(x) holds for at least one x</li>
        <li>Negation: ¬(∀x P(x)) ≡ ∃x ¬P(x) &nbsp;|&nbsp; ¬(∃x P(x)) ≡ ∀x ¬P(x)</li>
      </ul>
    </div>
    <div class="callout">💡 Key trick: p → q is <strong>false</strong> in exactly one case — p is True and q is False. All other combinations are True.</div>
  </div>
  <div id="logic-flash" style="display:none"><div class="fc-wrap" id="fc-logic"></div></div>
  <div id="logic-quiz" style="display:none"><div id="qz-logic"></div></div>
</div>

<!-- ── CH2: SETS ── -->
<div class="page" id="page-sets" style="--accent:#3a7dc8;--accent-bg:#f0f5fd;--accent-border:#c8d8f0">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 2</div>
    <div class="tp-title">Sets &amp; Functions</div>
    <div class="tp-desc">Set notation, Venn diagrams, operations, function types, sequences, and cardinality.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'sets','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'sets','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'sets','quiz')">Quiz</div>
  </div>
  <div id="sets-summary">
    <div class="sum-block">
      <h3>📦 Set Basics</h3>
      <ul>
        <li>A set is an <strong>unordered collection</strong> of distinct objects (elements).</li>
        <li><strong>a ∈ A</strong>: a is an element of A &nbsp;|&nbsp; <strong>a ∉ A</strong>: a is not an element</li>
        <li><strong>∅</strong> = empty set (no elements) &nbsp;|&nbsp; A ⊆ B: A is a subset of B</li>
        <li><strong>Power set P(A)</strong>: the set of all subsets of A. If |A|=n, then |P(A)| = 2ⁿ</li>
      </ul>
      <div class="formula">|A ∪ B| = |A| + |B| − |A ∩ B| &nbsp;← Inclusion-Exclusion Principle</div>
    </div>
    <div class="sum-block">
      <h3>🔄 Function Types</h3>
      <ul>
        <li><strong>Injective (one-to-one)</strong>: distinct inputs → distinct outputs; f(a)=f(b) ⇒ a=b</li>
        <li><strong>Surjective (onto)</strong>: every element of the codomain has a pre-image</li>
        <li><strong>Bijective</strong>: both injective and surjective — inverse f⁻¹ exists</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>♾️ Cardinality</h3>
      <ul>
        <li>A set is <strong>countable</strong> if it is finite OR has a bijection with ℕ</li>
        <li>ℕ, ℤ, ℚ are <strong>countably infinite</strong></li>
        <li>ℝ is <strong>uncountable</strong> — "larger" than ℕ (Cantor's diagonal argument)</li>
      </ul>
    </div>
  </div>
  <div id="sets-flash" style="display:none"><div class="fc-wrap" id="fc-sets"></div></div>
  <div id="sets-quiz" style="display:none"><div id="qz-sets"></div></div>
</div>

<!-- ── CH4: NUMBER THEORY ── -->
<div class="page" id="page-numtheory" style="--accent:#4ab87a;--accent-bg:#f0fbf5;--accent-border:#b8e8d0">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 4</div>
    <div class="tp-title">Number Theory &amp; Cryptography</div>
    <div class="tp-desc">Divisibility, prime numbers, GCD, LCM, modular arithmetic, and classical ciphers.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'numtheory','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'numtheory','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'numtheory','quiz')">Quiz</div>
  </div>
  <div id="numtheory-summary">
    <div class="sum-block">
      <h3>➗ Divisibility &amp; Primes</h3>
      <ul>
        <li><strong>a | b</strong>: a divides b — there exists integer c such that b = a·c</li>
        <li>A positive integer p &gt; 1 is <strong>prime</strong> if its only positive divisors are 1 and p</li>
        <li><strong>Fundamental Theorem of Arithmetic</strong>: every integer &gt;1 has a unique prime factorization</li>
        <li>To test if n is prime: check all primes ≤ √n</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>🔢 GCD &amp; LCM</h3>
      <ul>
        <li><strong>gcd(a,b)</strong>: largest integer that divides both a and b</li>
        <li><strong>lcm(a,b)</strong>: smallest positive integer divisible by both</li>
        <li>Key relation: <strong>gcd(a,b) × lcm(a,b) = a × b</strong></li>
      </ul>
      <div class="formula">gcd(24,36): 24=2³·3 | 36=2²·3² → gcd=2²·3=12 | lcm=2³·3²=72</div>
    </div>
    <div class="sum-block">
      <h3>🔄 Modular Arithmetic</h3>
      <ul>
        <li><strong>a mod m</strong>: remainder when a is divided by m (always ≥ 0)</li>
        <li><strong>a ≡ b (mod m)</strong>: m divides (a − b)</li>
        <li>For negative numbers: −11 mod 3 → −11 = 3·(−4) + 1 → remainder = <strong>1</strong></li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>🔐 Caesar &amp; Shift Ciphers</h3>
      <ul>
        <li><strong>Encrypt:</strong> f(p) = (p + k) mod 26</li>
        <li><strong>Decrypt:</strong> f⁻¹(c) = (c − k) mod 26</li>
        <li><strong>Affine cipher:</strong> f(p) = (a·p + b) mod 26, condition: gcd(a, 26) = 1</li>
      </ul>
      <div class="formula">Example k=3: A(0)→D(3), M(12)→P(15), Z(25)→C(2)</div>
    </div>
  </div>
  <div id="numtheory-flash" style="display:none"><div class="fc-wrap" id="fc-numtheory"></div></div>
  <div id="numtheory-quiz" style="display:none"><div id="qz-numtheory"></div></div>
</div>

<!-- ── CH5: INDUCTION ── -->
<div class="page" id="page-induction" style="--accent:#e8a030;--accent-bg:#fdf8ee;--accent-border:#f0d898">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 5</div>
    <div class="tp-title">Mathematical Induction &amp; Recursion</div>
    <div class="tp-desc">Proof by induction, strong induction, recursively defined functions and sequences.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'induction','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'induction','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'induction','quiz')">Quiz</div>
  </div>
  <div id="induction-summary">
    <div class="sum-block">
      <h3>📐 The Two Steps of Induction</h3>
      <ul>
        <li><strong>Basis Step:</strong> prove P(1) is true (or P(0), whatever the starting case)</li>
        <li><strong>Inductive Step:</strong> assume P(k) is true, then prove P(k+1) is true</li>
        <li><strong>Conclusion:</strong> P(n) is true for all integers n ≥ 1</li>
      </ul>
      <div class="formula">Example: prove 1+2+…+n = n(n+1)/2
Basis: n=1 → LHS=1, RHS=1·2/2=1 ✓
Inductive: LHS(k+1) = k(k+1)/2 + (k+1) = (k+1)(k+2)/2 ✓</div>
    </div>
    <div class="sum-block">
      <h3>📋 Important Formulas Proved by Induction</h3>
      <ul>
        <li>1 + 2 + … + n = n(n+1)/2</li>
        <li>1² + 2² + … + n² = n(n+1)(2n+1)/6</li>
        <li>1 + 3 + 5 + … + (2n−1) = n²</li>
        <li>1 + 2 + 2² + … + 2ⁿ = 2ⁿ⁺¹ − 1</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>🔁 Recursive Definitions</h3>
      <ul>
        <li>Two parts: <strong>Basis</strong> (initial value) + <strong>Recursive Step</strong> (rule using prior values)</li>
        <li><strong>Factorial:</strong> f(0) = 1, f(n) = n · f(n−1) for n ≥ 1</li>
        <li><strong>Fibonacci:</strong> f₀ = 0, f₁ = 1, fₙ = fₙ₋₁ + fₙ₋₂ for n ≥ 2</li>
      </ul>
    </div>
    <div class="callout">💡 Recursive definitions and induction complement each other: a recursive definition naturally gives rise to inductive proofs about that sequence.</div>
  </div>
  <div id="induction-flash" style="display:none"><div class="fc-wrap" id="fc-induction"></div></div>
  <div id="induction-quiz" style="display:none"><div id="qz-induction"></div></div>
</div>

<!-- ── CH6: COUNTING ── -->
<div class="page" id="page-counting" style="--accent:#9b59b6;--accent-bg:#f7f0fd;--accent-border:#d8c0f0">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 6</div>
    <div class="tp-title">Counting</div>
    <div class="tp-desc">Sum rule, product rule, inclusion-exclusion, permutations, combinations, and the binomial theorem.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'counting','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'counting','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'counting','quiz')">Quiz</div>
  </div>
  <div id="counting-summary">
    <div class="sum-block">
      <h3>➕ Sum Rule &amp; ✖ Product Rule</h3>
      <ul>
        <li><strong>Sum Rule:</strong> if A∩B=∅, then |A∪B| = |A|+|B|. Use when choosing from one group <em>or</em> another.</li>
        <li><strong>Product Rule:</strong> if a task has step₁ with m choices and step₂ with n choices, total = m×n.</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>🔢 Permutations vs Combinations</h3>
      <ul>
        <li><strong>P(n,r)</strong> = n!/(n−r)! — ordered selection of r from n (order matters)</li>
        <li><strong>C(n,r)</strong> = n! / (r!(n−r)!) — unordered selection (order doesn't matter)</li>
        <li>Symmetry: C(n,r) = C(n, n−r)</li>
      </ul>
      <div class="formula">P(5,2) = 5×4 = 20 &nbsp;|&nbsp; C(5,2) = (5×4)/(2×1) = 10
n! = n×(n−1)×…×2×1 &nbsp;|&nbsp; 0! = 1</div>
    </div>
    <div class="sum-block">
      <h3>🔄 Inclusion-Exclusion</h3>
      <ul>
        <li>|A ∪ B| = |A| + |B| − |A ∩ B|</li>
        <li>|A ∪ B ∪ C| = |A|+|B|+|C| − |A∩B| − |A∩C| − |B∩C| + |A∩B∩C|</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>📐 Binomial Theorem</h3>
      <ul>
        <li>(x+y)ⁿ = Σ C(n,k) · xⁿ⁻ᵏ · yᵏ, summed from k=0 to n</li>
        <li>Pascal's triangle: each entry = sum of the two entries above it</li>
        <li>C(n,0) = C(n,n) = 1 &nbsp;|&nbsp; C(n,k) = C(n−1,k−1) + C(n−1,k)</li>
      </ul>
    </div>
  </div>
  <div id="counting-flash" style="display:none"><div class="fc-wrap" id="fc-counting"></div></div>
  <div id="counting-quiz" style="display:none"><div id="qz-counting"></div></div>
</div>

<!-- ── CH8: ADVANCED ── -->
<div class="page" id="page-advanced" style="--accent:#e05080;--accent-bg:#fdf0f4;--accent-border:#f0c0d0">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 8</div>
    <div class="tp-title">Advanced Counting Techniques</div>
    <div class="tp-desc">Sequences, recurrence relations, geometric and arithmetic series, and solving recurrences.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'advanced','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'advanced','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'advanced','quiz')">Quiz</div>
  </div>
  <div id="advanced-summary">
    <div class="sum-block">
      <h3>📈 Arithmetic vs Geometric Sequences</h3>
      <ul>
        <li><strong>Arithmetic:</strong> constant difference d between consecutive terms. aₙ = a₁ + (n−1)d</li>
        <li><strong>Geometric:</strong> constant ratio r between consecutive terms. aₙ = a₁ · rⁿ⁻¹</li>
      </ul>
      <div class="formula">Geometric sum: Sₙ = a(rⁿ−1)/(r−1) for r≠1
Example: 1+2+4+8+…+2ⁿ = 2ⁿ⁺¹ − 1</div>
    </div>
    <div class="sum-block">
      <h3>🔁 Recurrence Relations</h3>
      <ul>
        <li>An equation defining each term in terms of previous terms</li>
        <li><strong>Example:</strong> aₙ = aₙ₋₁ + 2, a₁=3 → 3, 5, 7, 9, … (arithmetic, d=2)</li>
        <li><strong>Fibonacci recurrence:</strong> fₙ = fₙ₋₁ + fₙ₋₂, f₀=0, f₁=1</li>
        <li>To solve: find general solution + apply initial conditions</li>
      </ul>
    </div>
  </div>
  <div id="advanced-flash" style="display:none"><div class="fc-wrap" id="fc-advanced"></div></div>
  <div id="advanced-quiz" style="display:none"><div id="qz-advanced"></div></div>
</div>

<!-- ── CH9: RELATIONS ── -->
<div class="page" id="page-relations" style="--accent:#2ab8b8;--accent-bg:#f0fbfb;--accent-border:#b0e8e8">
  <div class="tp-header">
    <div class="tp-back" onclick="nav('home')">← back to all topics</div>
    <div class="tp-badge">Chapter 9</div>
    <div class="tp-title">Relations</div>
    <div class="tp-desc">Binary relations, properties (reflexive, symmetric, transitive), equivalence relations, and matrix representation.</div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab(this,'relations','summary')">Summary</div>
    <div class="tab" onclick="switchTab(this,'relations','flash')">Flashcards</div>
    <div class="tab" onclick="switchTab(this,'relations','quiz')">Quiz</div>
  </div>
  <div id="relations-summary">
    <div class="sum-block">
      <h3>🔗 What is a Binary Relation?</h3>
      <ul>
        <li>A relation R on set A is a subset of A × A (ordered pairs)</li>
        <li>Can be represented as: set of ordered pairs / zero-one matrix / directed graph</li>
      </ul>
    </div>
    <div class="sum-block">
      <h3>🏷️ Five Key Properties</h3>
      <ul>
        <li><strong>Reflexive:</strong> (a,a) ∈ R for every a ∈ A</li>
        <li><strong>Irreflexive:</strong> (a,a) ∉ R for every a ∈ A</li>
        <li><strong>Symmetric:</strong> (a,b) ∈ R → (b,a) ∈ R</li>
        <li><strong>Antisymmetric:</strong> (a,b) ∈ R and (b,a) ∈ R → a = b</li>
        <li><strong>Transitive:</strong> (a,b) ∈ R and (b,c) ∈ R → (a,c) ∈ R</li>
      </ul>
      <div class="callout">💡 An <strong>Equivalence Relation</strong> is Reflexive + Symmetric + Transitive. Example: "=" on ℤ.</div>
    </div>
    <div class="sum-block">
      <h3>🔢 Matrix Representation</h3>
      <ul>
        <li>M[i][j] = 1 if (aᵢ, aⱼ) ∈ R, else 0</li>
        <li>Reflexive ↔ all diagonal entries are 1</li>
        <li>Symmetric ↔ M = Mᵀ (matrix equals its transpose)</li>
      </ul>
    </div>
  </div>
  <div id="relations-flash" style="display:none"><div class="fc-wrap" id="fc-relations"></div></div>
  <div id="relations-quiz" style="display:none"><div id="qz-relations"></div></div>
</div>

</main>
</div><!-- end shell -->

<script>
// ═══════════════════════════════════════════════════
// DATA
// ═══════════════════════════════════════════════════
const DATA = {
  logic: {
    flash: [
      { q: "What makes a sentence a proposition?", a: "It must be a declarative sentence with a definite truth value — either True or False, but not both.\n✓ '2+2=5' (False)\n✗ 'What time is it?' (not declarative)" },
      { q: "When is p → q (implication) FALSE?", a: "ONLY when p = True and q = False.\nAll other combinations are True:\n(T→T)=T, (F→T)=T, (F→F)=T" },
      { q: "What is the contrapositive of p → q? Is it equivalent?", a: "Contrapositive: ¬q → ¬p\nYES — it is logically equivalent to p → q.\nConverse (q → p) is NOT equivalent." },
      { q: "State De Morgan's Laws.", a: "¬(p ∧ q) ≡ ¬p ∨ ¬q\n¬(p ∨ q) ≡ ¬p ∧ ¬q\nTip: negate the whole thing, flip AND↔OR" },
      { q: "What is the negation of ∀x P(x)?", a: "¬(∀x P(x)) ≡ ∃x ¬P(x)\nExample: negate 'All students passed'\n→ 'There exists a student who did not pass'" },
      { q: "What does p ↔ q mean? When is it true?", a: "Biconditional: 'p if and only if q'\nTrue when p and q have the SAME truth value:\n(T,T)→T and (F,F)→T\n(T,F)→F and (F,T)→F" },
    ],
    quiz: [
      { q: "Which of the following is NOT a proposition?", opts: ["'The Earth is round'", "'2 + 3 = 6'", "'What is your name?'", "'Riyadh is the capital of Saudi Arabia'"], ans: 2, exp: "'What is your name?' is a question — it has no truth value, so it cannot be a proposition." },
      { q: "If p = True and q = False, what is the value of p → q?", opts: ["True", "False", "Indeterminate", "Depends on context"], ans: 1, exp: "Implication p → q is False only when p=T and q=F. This is exactly that case." },
      { q: "Which expression is logically equivalent to p → q?", opts: ["q → p", "¬p ∨ q", "p ∧ ¬q", "¬p ∧ q"], ans: 1, exp: "p → q ≡ ¬p ∨ q. This is a fundamental equivalence worth memorizing." },
      { q: "What is the negation of ∃x P(x)?", opts: ["∃x ¬P(x)", "∀x P(x)", "∀x ¬P(x)", "¬∃x ¬P(x)"], ans: 2, exp: "¬(∃x P(x)) ≡ ∀x ¬P(x). If no such x exists, then for all x, P(x) is false." },
      { q: "p ↔ q is TRUE when:", opts: ["p is True only", "q is False only", "p and q have the same truth value", "p is True and q is False"], ans: 2, exp: "Biconditional is true in exactly two cases: both True (T,T) or both False (F,F)." },
    ]
  },

  sets: {
    flash: [
      { q: "What is the difference between A ⊆ B and A ⊂ B?", a: "A ⊆ B: A is a subset of B (allows A = B)\nA ⊂ B: A is a proper subset (A ≠ B)\nNote: ∅ ⊆ every set, and every set ⊆ itself" },
      { q: "What is the power set of {a, b}?", a: "P({a,b}) = { ∅, {a}, {b}, {a,b} }\nRule: if |A| = n, then |P(A)| = 2ⁿ\nHere n=2, so |P(A)| = 4" },
      { q: "What is the difference between Injective, Surjective, and Bijective?", a: "Injective (1-1): f(a)=f(b) ⇒ a=b\nSurjective (onto): every codomain element has a pre-image\nBijective: both — inverse f⁻¹ exists" },
      { q: "Why is ∅ ≠ {∅}?", a: "∅ is the empty set — contains NO elements, |∅|=0\n{∅} is a set containing one element (∅), |{∅}|=1\nThey are fundamentally different objects" },
      { q: "Is ℚ (rationals) countable?", a: "YES — ℚ is countably infinite.\nℕ, ℤ, ℚ are all countably infinite.\nℝ is uncountable (larger cardinality)." },
    ],
    quiz: [
      { q: "If A = {1,2,3} and B = {2,3,4}, what is A ∩ B?", opts: ["{1,2,3,4}", "{2,3}", "{1,4}", "{1,2,3}"], ans: 1, exp: "A ∩ B contains only elements common to both sets: {2,3}" },
      { q: "How many elements are in P({a,b,c})?", opts: ["3", "6", "8", "9"], ans: 2, exp: "|P(A)| = 2^|A| = 2³ = 8" },
      { q: "f(x) = x² from ℝ to ℝ is:", opts: ["Injective only", "Surjective only", "Bijective", "Neither injective nor surjective"], ans: 3, exp: "Not injective: f(2)=f(−2)=4. Not surjective: −4 has no real pre-image." },
      { q: "A − B (set difference) equals:", opts: ["A ∩ B", "A ∩ Bᶜ", "Aᶜ ∩ B", "A ∪ Bᶜ"], ans: 1, exp: "A − B = {x | x∈A and x∉B} = A ∩ Bᶜ" },
    ]
  },

  numtheory: {
    flash: [
      { q: "What does a | b mean? Give an example.", a: "'a divides b' — there exists integer c such that b = a·c\n✓ 3|12 because 12 = 3·4\n✗ 5|13 because 13 = 5·2 + 3 (remainder ≠ 0)" },
      { q: "How do you find gcd(48, 18) using prime factorization?", a: "48 = 2⁴ · 3\n18 = 2 · 3²\ngcd = 2^min(4,1) · 3^min(1,2) = 2¹ · 3¹ = 6" },
      { q: "Compute 113 mod 24 and −29 mod 7.", a: "113 = 24·4 + 17 → 113 mod 24 = 17\n−29 = 7·(−5) + 6 → −29 mod 7 = 6\n(Remainder must always be ≥ 0)" },
      { q: "Encrypt 'M' (=12) using Caesar cipher with k=3.", a: "f(p) = (p+k) mod 26\nf(12) = (12+3) mod 26 = 15 = 'P'\nDecrypt: f⁻¹(c) = (c−k) mod 26" },
      { q: "What condition must 'a' satisfy in the Affine cipher f(p)=(ap+b) mod 26?", a: "gcd(a, 26) = 1\n(a must be coprime with 26)\n✓ a=7 works | ✗ a=2 doesn't (gcd(2,26)=2≠1)" },
    ],
    quiz: [
      { q: "What is −29 mod 7?", opts: ["−1", "6", "−29", "1"], ans: 1, exp: "−29 = 7·(−5) + 6. Since the remainder must be ≥ 0, and 7·(−5) = −35, we get −29 − (−35) = 6." },
      { q: "What is gcd(120, 500)?", opts: ["10", "20", "40", "60"], ans: 1, exp: "120 = 2³·3·5 | 500 = 2²·5³ → gcd = 2²·5 = 20" },
      { q: "Which number is prime?", opts: ["91", "97", "99", "100"], ans: 1, exp: "97 is prime (√97 ≈ 9.8; not divisible by 2,3,5,7). Note: 91 = 7×13." },
      { q: "Using shift cipher k=11, encrypt 'S' (=18).", opts: ["'T'", "'D'", "'C'", "'Y'"], ans: 1, exp: "f(18) = (18+11) mod 26 = 29 mod 26 = 3 = 'D'" },
      { q: "lcm(24, 36) = ?", opts: ["12", "72", "144", "48"], ans: 1, exp: "24=2³·3 | 36=2²·3² → lcm = 2³·3² = 72. Check: gcd=12, and 24·36/12 = 72 ✓" },
    ]
  },

  induction: {
    flash: [
      { q: "State the two steps of mathematical induction.", a: "1. Basis Step: Prove P(1) is true\n2. Inductive Step: Assume P(k) is true for some k≥1, then prove P(k+1) is true\nConclusion: P(n) holds for all n≥1" },
      { q: "Prove by induction: 1+3+…+(2n−1) = n²", a: "Basis: n=1 → LHS=1, RHS=1²=1 ✓\nInductive: Assume 1+3+…+(2k−1)=k²\nLHS(k+1) = k² + (2k+1) = (k+1)² = RHS ✓" },
      { q: "Given f(0)=3, f(n+1)=2f(n)+3. Find f(3).", a: "f(0) = 3\nf(1) = 2(3)+3 = 9\nf(2) = 2(9)+3 = 21\nf(3) = 2(21)+3 = 45" },
      { q: "What are the first 7 Fibonacci numbers?", a: "f₀=0, f₁=1, f₂=1, f₃=2\nf₄=3, f₅=5, f₆=8\nSequence: 0, 1, 1, 2, 3, 5, 8, 13, …" },
      { q: "What is the sum 1+2+4+…+2ⁿ? Prove the pattern.", a: "Sum = 2ⁿ⁺¹ − 1\nBasis: n=0 → LHS=1, RHS=2¹−1=1 ✓\nInductive: assume sum to 2ᵏ = 2ᵏ⁺¹−1\nAdd 2ᵏ⁺¹: get 2·2ᵏ⁺¹−1 = 2ᵏ⁺²−1 ✓" },
    ],
    quiz: [
      { q: "In the Inductive Step, what do we ASSUME?", opts: ["P(1) is true", "P(n) is true for all n", "P(k) is true for some k≥1", "P(k+1) is true"], ans: 2, exp: "We assume P(k) — this is called the Inductive Hypothesis — and use it to prove P(k+1)." },
      { q: "What is 1 + 2 + 3 + … + 100 using the formula n(n+1)/2?", opts: ["5000", "5050", "4950", "10000"], ans: 1, exp: "n=100 → 100·101/2 = 10100/2 = 5050" },
      { q: "Given f(0)=3, f(n+1)=2f(n), what is f(4)?", opts: ["24", "48", "96", "384"], ans: 1, exp: "f(0)=3, f(1)=6, f(2)=12, f(3)=24, f(4)=48" },
      { q: "What is 1² + 2² + … + n² equal to?", opts: ["n(n+1)/2", "n²(n+1)²/4", "n(n+1)(2n+1)/6", "n(n+1)(n+2)/6"], ans: 2, exp: "The formula is n(n+1)(2n+1)/6. For n=3: 1+4+9=14 and 3·4·7/6=14 ✓" },
    ]
  },

  counting: {
    flash: [
      { q: "Sum Rule vs Product Rule — when do you use each?", a: "Sum Rule: choosing from group A OR group B (disjoint)\n|A ∪ B| = |A| + |B|\nProduct Rule: doing step₁ AND step₂\nTotal = m × n choices" },
      { q: "What is the difference between P(n,r) and C(n,r)?", a: "P(n,r) = n!/(n−r)! — ORDER MATTERS\n'arrange 3 books from 5'\nC(n,r) = n!/(r!(n−r)!) — ORDER DOESN'T MATTER\n'choose a committee of 3 from 5'" },
      { q: "Compute C(6,2) and P(6,2).", a: "C(6,2) = 6!/(2!·4!) = (6·5)/(2·1) = 15\nP(6,2) = 6!/(4!) = 6·5 = 30\nNote: P(n,r) = r! · C(n,r)" },
      { q: "How many ways to arrange the letters in NOON?", a: "4 letters, N appears twice\n= 4! / 2! = 24/2 = 12\nGeneral rule: n!/(n₁!·n₂!·…) for repeated elements" },
      { q: "State the Inclusion-Exclusion principle for 2 sets.", a: "|A ∪ B| = |A| + |B| − |A ∩ B|\nWe subtract the intersection because it gets counted twice.\nFor 3 sets: add all singles, subtract all pairs, add the triple." },
    ],
    quiz: [
      { q: "How many 4-bit strings start with 1?", opts: ["4", "8", "16", "2"], ans: 1, exp: "First bit is fixed (1). The remaining 3 bits each have 2 choices: 2×2×2 = 8." },
      { q: "How many ways can 3 students be chosen from 10?", opts: ["30", "120", "720", "210"], ans: 1, exp: "C(10,3) = 10!/(3!·7!) = (10·9·8)/(3·2·1) = 120" },
      { q: "C(n,r) = C(n, ?)", opts: ["r+1", "r−1", "n−r", "n+r"], ans: 2, exp: "C(n,r) = C(n,n−r). Example: C(5,2) = C(5,3) = 10" },
      { q: "P(5,3) = ?", opts: ["10", "60", "20", "120"], ans: 1, exp: "P(5,3) = 5!/(5−3)! = 5!/2! = 120/2 = 60" },
      { q: "|A|=50, |B|=30, |A∩B|=10. Find |A∪B|.", opts: ["70", "80", "90", "10"], ans: 0, exp: "|A∪B| = 50 + 30 − 10 = 70" },
    ]
  },

  advanced: {
    flash: [
      { q: "How do you tell if a sequence is arithmetic or geometric?", a: "Arithmetic: constant DIFFERENCE between terms (d)\naₙ = a₁ + (n−1)d\nGeometric: constant RATIO between terms (r)\naₙ = a₁ · rⁿ⁻¹" },
      { q: "What is the sum of the geometric series 1+2+4+…+2ⁿ?", a: "Sₙ = a(rⁿ⁺¹−1)/(r−1), where a=1, r=2\n= (2ⁿ⁺¹ − 1)/(2−1) = 2ⁿ⁺¹ − 1\nFor n=3: 1+2+4+8 = 15 = 2⁴−1 ✓" },
      { q: "The sequence 3, 6, 12, 24, … — what is a₁₀?", a: "Geometric: a₁=3, r=2\na₁₀ = 3 · 2⁹ = 3 · 512 = 1536" },
      { q: "What is a recurrence relation? Give an example.", a: "An equation defining aₙ using previous terms.\nExample: aₙ = aₙ₋₁ + 2, a₁=3\n→ 3, 5, 7, 9, 11, … (arithmetic, d=2)" },
    ],
    quiz: [
      { q: "The sequence 2, 5, 8, 11, … is:", opts: ["Geometric with r=3", "Arithmetic with d=3", "Geometric with r=2.5", "Arithmetic with d=2.5"], ans: 1, exp: "The difference between consecutive terms is constant: 5−2=3, 8−5=3 → arithmetic with d=3." },
      { q: "What is the 10th term of 1, 2, 4, 8, …?", opts: ["512", "256", "1024", "128"], ans: 0, exp: "Geometric: a₁=1, r=2 → a₁₀ = 1·2⁹ = 512" },
      { q: "If aₙ = 2aₙ₋₁ and a₁=3, what is a₄?", opts: ["12", "24", "48", "6"], ans: 1, exp: "a₁=3, a₂=6, a₃=12, a₄=24" },
      { q: "What is 1 + 2 + 4 + … + 2¹⁰?", opts: ["1023", "2047", "2048", "1024"], ans: 1, exp: "Sum = 2¹¹ − 1 = 2048 − 1 = 2047" },
    ]
  },

  relations: {
    flash: [
      { q: "Define a Reflexive relation. Give an example.", a: "(a,a) ∈ R for every a ∈ A\nExample: R = {(1,1),(2,2),(3,3),(1,2)} on {1,2,3}\n→ Reflexive ✓ (all (a,a) pairs present)" },
      { q: "What is the difference between Symmetric and Antisymmetric?", a: "Symmetric: (a,b)∈R → (b,a)∈R\nAntisymmetric: (a,b)∈R ∧ (b,a)∈R → a=b\nA relation can be BOTH if it only has (a,a) pairs!" },
      { q: "How do you verify Transitivity from a matrix?", a: "M is transitive if: M[i][j]=1 and M[j][k]=1 → M[i][k]=1\nEquivalently: M² (boolean) has no 1s where M has 0s\nCheck every pair of connected nodes" },
      { q: "What are the three requirements for an Equivalence Relation?", a: "1. Reflexive: (a,a) ∈ R for all a\n2. Symmetric: (a,b)∈R → (b,a)∈R\n3. Transitive: (a,b)∈R ∧ (b,c)∈R → (a,c)∈R\nExample: '=' on ℤ satisfies all three." },
      { q: "Write the matrix for R={(1,2),(2,3),(1,3)} on {1,2,3}.", a: "     1  2  3\n1  [ 0  1  1 ]\n2  [ 0  0  1 ]\n3  [ 0  0  0 ]\nNote: (1,3) exists — is R transitive? Yes! (1→2→3 covered by (1,3))" },
    ],
    quiz: [
      { q: "R = {(1,1),(2,2),(3,3)} on {1,2,3} is:", opts: ["Reflexive only", "Symmetric only", "Reflexive, Symmetric, and Transitive", "Antisymmetric only"], ans: 2, exp: "Reflexive ✓ (all (a,a) present). Symmetric ✓ (no non-diagonal pairs). Transitive ✓ (vacuously)." },
      { q: "In a zero-one matrix, Reflexive means:", opts: ["Matrix is symmetric", "All diagonal entries are 0", "All diagonal entries are 1", "All rows are equal"], ans: 2, exp: "Reflexive ↔ (a,a)∈R for all a ↔ M[i][i]=1 for all i ↔ main diagonal = all 1s." },
      { q: "Which relation is an equivalence relation?", opts: ["'<' on ℤ", "'≤' on ℤ", "'=' on ℤ", "'Parent of' on people"], ans: 2, exp: "'=' is reflexive (a=a), symmetric (a=b→b=a), and transitive (a=b∧b=c→a=c)." },
      { q: "The composite relation R∘S means:", opts: ["R ∩ S", "Union of R and S", "(a,c) if ∃b: (a,b)∈S and (b,c)∈R", "Negation of R"], ans: 2, exp: "R∘S: apply S first, then R. (a,c)∈R∘S iff there exists b such that (a,b)∈S and (b,c)∈R." },
      { q: "The relation 'aRb iff a≠b' on {1,2,3} is:", opts: ["Reflexive", "Irreflexive and Symmetric", "Transitive", "Antisymmetric"], ans: 1, exp: "No (a,a): Irreflexive ✓. If a≠b then b≠a: Symmetric ✓. Not Transitive: (1,2)∧(2,1) but (1,1)∉R." },
    ]
  }
};

// ═══════════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════════
const visited = new Set();
const fcState = {};
const qzState = {};

// ═══════════════════════════════════════════════════
// NAVIGATION
// ═══════════════════════════════════════════════════
function nav(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  document.querySelectorAll('.sb-item').forEach(n => n.classList.remove('active'));
  const ni = document.querySelector(`.sb-item[onclick*="'${id}'"]`);
  if (ni) ni.classList.add('active');
  if (id !== 'home') {
    visited.add(id);
    updateProgress();
    if (!fcState[id]) initFlash(id);
    if (!qzState[id]) initQuiz(id);
  }
  window.scrollTo(0,0);
}

function updateProgress() {
  const pct = (visited.size / 7) * 100;
  document.getElementById('prog-fill').style.width = pct + '%';
  document.getElementById('prog-count').textContent = visited.size + ' / 7 topics visited';
}

// ═══════════════════════════════════════════════════
// TABS
// ═══════════════════════════════════════════════════
function switchTab(el, topic, tab) {
  const page = el.closest('.page');
  page.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  el.classList.add('active');
  ['summary','flash','quiz'].forEach(t => {
    const el2 = document.getElementById(topic + '-' + t);
    if (el2) el2.style.display = (t === tab ? 'block' : 'none');
  });
}

// ═══════════════════════════════════════════════════
// FLASHCARDS
// ═══════════════════════════════════════════════════
function initFlash(topic) {
  fcState[topic] = { idx: 0, known: 0, again: 0 };
  renderFlash(topic);
}

function renderFlash(topic) {
  const s = fcState[topic];
  const cards = DATA[topic].flash;
  const el = document.getElementById('fc-' + topic);
  if (!el) return;

  if (s.idx >= cards.length) {
    el.innerHTML = `<div class="done-card">
      <div style="font-size:36px;margin-bottom:12px">🎉</div>
      <div style="font-family:var(--serif);font-size:20px;color:var(--ink);">All cards done!</div>
      <p>Got it: <strong style="color:#2a8050">${s.known}</strong> &nbsp;·&nbsp; Review again: <strong style="color:#c03030">${s.again}</strong></p>
      <button class="btn btn-dark" onclick="fcState['${topic}']={idx:0,known:0,again:0};renderFlash('${topic}')">Restart deck</button>
    </div>`;
    return;
  }

  const c = cards[s.idx];
  const pct = Math.round(s.idx / cards.length * 100);

  el.innerHTML = `
    <div class="fc-prog"><div class="fc-prog-fill" style="width:${pct}%"></div></div>
    <div class="fc-scene">
      <div class="fc-card" id="fcc-${topic}" onclick="flipFC('${topic}')">
        <div class="fc-face front">
          <div class="fc-face-label">Card ${s.idx+1} of ${cards.length}</div>
          <div class="fc-q">${c.q}</div>
        </div>
        <div class="fc-face back">
          <div class="fc-face-label">Answer</div>
          <div class="fc-a">${c.a}</div>
        </div>
      </div>
    </div>
    <div class="fc-hint" id="fch-${topic}">Click the card to reveal the answer</div>
    <div class="fc-controls" id="fcctrl-${topic}" style="display:none">
      <button class="fc-btn again" onclick="fcAction('${topic}','again')">↩ Review again</button>
      <button class="fc-btn good" onclick="fcAction('${topic}','good')">✓ Got it</button>
    </div>
    <div class="fc-tally">Got it: <span style="color:#2a8050">${s.known}</span> &nbsp;·&nbsp; Review: <span style="color:#c03030">${s.again}</span></div>`;
}

function flipFC(topic) {
  const card = document.getElementById('fcc-' + topic);
  const ctrl = document.getElementById('fcctrl-' + topic);
  const hint = document.getElementById('fch-' + topic);
  const flipped = card.classList.toggle('flipped');
  ctrl.style.display = flipped ? 'flex' : 'none';
  hint.style.display = flipped ? 'none' : 'block';
}

function fcAction(topic, action) {
  const s = fcState[topic];
  if (action === 'good') s.known++; else s.again++;
  s.idx++;
  renderFlash(topic);
}

// ═══════════════════════════════════════════════════
// QUIZ
// ═══════════════════════════════════════════════════
function initQuiz(topic) {
  qzState[topic] = { idx: 0, score: 0, answered: false };
  renderQuiz(topic);
}

function renderQuiz(topic) {
  const s = qzState[topic];
  const qs = DATA[topic].quiz;
  const el = document.getElementById('qz-' + topic);
  if (!el) return;

  if (s.idx >= qs.length) {
    const pct = Math.round(s.score / qs.length * 100);
    const emoji = pct >= 80 ? '🏆' : pct >= 60 ? '👍' : '📚';
    const msg = pct >= 80 ? 'Excellent work!' : pct >= 60 ? 'Good job!' : 'Keep studying!';
    el.innerHTML = `<div class="score-screen">
      <div class="score-emoji">${emoji}</div>
      <div class="score-num">${s.score}<span class="score-denom"> / ${qs.length}</span></div>
      <div class="score-label">${pct}% — ${msg}</div>
      <div style="margin-top:28px;display:flex;gap:10px;justify-content:center">
        <button class="btn btn-dark" onclick="qzState['${topic}']={idx:0,score:0,answered:false};renderQuiz('${topic}')">Retake quiz</button>
        <button class="btn btn-outline" onclick="switchTabById('${topic}','flash')">Review flashcards</button>
      </div>
    </div>`;
    return;
  }

  const q = qs[s.idx];
  s.answered = false;

  el.innerHTML = `<div class="qz-block">
    <div class="qz-num">Question ${s.idx+1} / ${qs.length}</div>
    <div class="qz-text">${q.q}</div>
    <div class="qz-opts">
      ${q.opts.map((o,i) => `<div class="qz-opt" id="qo-${topic}-${i}" onclick="answerQ('${topic}',${i})">${o}</div>`).join('')}
    </div>
    <div class="qz-exp" id="qe-${topic}">${q.exp}</div>
  </div>
  <div class="qz-next-row" id="qnr-${topic}"></div>`;
}

function answerQ(topic, chosen) {
  const s = qzState[topic];
  if (s.answered) return;
  s.answered = true;
  const q = DATA[topic].quiz[s.idx];
  for (let i = 0; i < q.opts.length; i++) {
    const opt = document.getElementById(`qo-${topic}-${i}`);
    if (!opt) continue;
    opt.setAttribute('disabled','');
    opt.style.pointerEvents = 'none';
    if (i === q.ans) opt.classList.add('correct');
    else if (i === chosen) opt.classList.add('wrong');
  }
  if (chosen === q.ans) s.score++;
  const exp = document.getElementById('qe-' + topic);
  if (exp) exp.classList.add('show');
  const nxt = document.getElementById('qnr-' + topic);
  if (nxt) {
    const last = s.idx + 1 >= DATA[topic].quiz.length;
    nxt.innerHTML = `<button class="btn btn-dark" onclick="qzState['${topic}'].idx++;qzState['${topic}'].answered=false;renderQuiz('${topic}')">${last ? 'See results →' : 'Next question →'}</button>`;
  }
}

function switchTabById(topic, tab) {
  const page = document.getElementById('page-' + topic);
  const tabEl = Array.from(page.querySelectorAll('.tab')).find(t => t.getAttribute('onclick').includes("'"+tab+"'"));
  if (tabEl) switchTab(tabEl, topic, tab);
}
</script>
</body>
</html>
