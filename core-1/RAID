<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RAID Interactive Quiz — CompTIA A+</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;900&display=swap');
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Poppins',sans-serif;background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);min-height:100vh;padding:20px;}

/* ── LAYOUT ── */
.wrapper{max-width:900px;margin:0 auto;}
header{text-align:center;color:white;margin-bottom:30px;}
header h1{font-size:2.6em;font-weight:900;text-shadow:2px 2px 8px rgba(0,0,0,0.3);}
header p{font-size:1.1em;opacity:.9;margin-top:6px;}

/* ── MODE PICKER ── */
.mode-bar{display:flex;gap:12px;justify-content:center;margin-bottom:28px;flex-wrap:wrap;}
.mode-btn{padding:12px 28px;border:3px solid white;background:transparent;color:white;border-radius:50px;font-size:1em;font-weight:700;cursor:pointer;font-family:'Poppins',sans-serif;transition:all .25s;}
.mode-btn:hover,.mode-btn.active{background:white;color:#764ba2;}

/* ── PROGRESS ── */
.progress-bar-wrap{background:rgba(255,255,255,.25);border-radius:20px;height:14px;margin-bottom:20px;overflow:hidden;}
.progress-bar-fill{height:100%;background:white;border-radius:20px;transition:width .4s ease;width:0%;}
.progress-label{color:white;text-align:center;font-size:.95em;font-weight:600;margin-bottom:16px;}

/* ── CARD ── */
.card{background:white;border-radius:22px;padding:40px;box-shadow:0 16px 50px rgba(0,0,0,0.25);min-height:340px;display:flex;flex-direction:column;justify-content:space-between;}
.card-meta{font-size:.85em;font-weight:700;text-transform:uppercase;letter-spacing:2px;color:#667eea;margin-bottom:14px;}
.card-question{font-size:1.5em;font-weight:700;color:#2c3e50;line-height:1.4;margin-bottom:24px;}

/* ── FLASHCARD FLIP ── */
.flip-container{perspective:1100px;cursor:pointer;min-height:260px;}
.flip-inner{position:relative;width:100%;min-height:260px;transform-style:preserve-3d;transition:transform .55s cubic-bezier(.4,.2,.2,1);}
.flip-container.flipped .flip-inner{transform:rotateY(180deg);}
.flip-face{position:absolute;width:100%;min-height:260px;backface-visibility:hidden;border-radius:16px;padding:30px;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;}
.flip-front{background:linear-gradient(135deg,#667eea,#764ba2);color:white;}
.flip-back{background:linear-gradient(135deg,#11998e,#38ef7d);color:#1a3a2a;transform:rotateY(180deg);}
.flip-front .q-text{font-size:1.35em;font-weight:700;line-height:1.5;}
.flip-back .a-text{font-size:1.2em;font-weight:600;line-height:1.6;}
.flip-hint{font-size:.85em;opacity:.75;margin-top:16px;}
.flip-badge{font-size:2.5em;margin-bottom:14px;}

.fc-nav{display:flex;gap:12px;justify-content:center;margin-top:24px;flex-wrap:wrap;}
.fc-btn{padding:12px 28px;border:none;border-radius:50px;font-size:.95em;font-weight:700;cursor:pointer;font-family:'Poppins',sans-serif;transition:all .2s;}
.fc-btn:hover{transform:scale(1.05);}
.btn-know{background:#2ecc71;color:white;}
.btn-learning{background:#e74c3c;color:white;}
.btn-skip{background:#95a5a6;color:white;}

/* ── MULTIPLE CHOICE ── */
.choices{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-top:10px;}
.choice-btn{padding:16px 20px;border:2.5px solid #e0e0e0;background:white;border-radius:14px;font-size:1em;font-weight:600;cursor:pointer;font-family:'Poppins',sans-serif;transition:all .2s;text-align:left;color:#2c3e50;line-height:1.4;}
.choice-btn:hover:not(:disabled){border-color:#667eea;background:#f0f2ff;transform:translateY(-2px);}
.choice-btn.correct{background:#d4edda;border-color:#28a745;color:#155724;}
.choice-btn.wrong{background:#f8d7da;border-color:#dc3545;color:#721c24;}
.choice-btn:disabled{cursor:not-allowed;}

.mc-feedback{margin-top:20px;padding:16px 20px;border-radius:12px;font-size:1em;font-weight:600;display:none;}
.mc-feedback.show{display:block;}
.mc-feedback.correct-fb{background:#d4edda;color:#155724;border-left:5px solid #28a745;}
.mc-feedback.wrong-fb{background:#f8d7da;color:#721c24;border-left:5px solid #dc3545;}

.mc-next{margin-top:16px;padding:13px 36px;background:linear-gradient(135deg,#667eea,#764ba2);color:white;border:none;border-radius:50px;font-size:1em;font-weight:700;cursor:pointer;font-family:'Poppins',sans-serif;display:none;transition:all .2s;}
.mc-next:hover{transform:scale(1.05);}
.mc-next.show{display:inline-block;}

/* ── SCORE PANEL ── */
.score-strip{display:flex;gap:16px;justify-content:center;margin-bottom:22px;flex-wrap:wrap;}
.score-pill{background:rgba(255,255,255,.2);color:white;padding:8px 20px;border-radius:50px;font-weight:700;font-size:.95em;}
.score-pill span{font-size:1.3em;}

/* ── RESULTS SCREEN ── */
.results{background:white;border-radius:22px;padding:50px 40px;text-align:center;box-shadow:0 16px 50px rgba(0,0,0,0.25);display:none;}
.results.show{display:block;}
.results h2{font-size:2.2em;color:#2c3e50;margin-bottom:10px;}
.results .big-score{font-size:5em;font-weight:900;color:#667eea;margin:10px 0;}
.results p{font-size:1.1em;color:#555;margin-bottom:28px;}
.results .restart-btn{padding:15px 45px;background:linear-gradient(135deg,#667eea,#764ba2);color:white;border:none;border-radius:50px;font-size:1.1em;font-weight:700;cursor:pointer;font-family:'Poppins',sans-serif;transition:all .2s;}
.results .restart-btn:hover{transform:scale(1.05);}
.grade-msg{font-size:1.4em;font-weight:700;margin-bottom:10px;}

/* ── MEMORY HOOKS SECTION ── */
.hooks-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:14px;margin-top:8px;}
.hook-tile{border-radius:14px;padding:18px 14px;color:white;text-align:center;}
.hook-tile .lvl{font-size:1.8em;font-weight:900;margin-bottom:6px;}
.hook-tile .txt{font-size:.88em;font-weight:600;line-height:1.5;}
.h0{background:linear-gradient(135deg,#c0392b,#e74c3c);}
.h1{background:linear-gradient(135deg,#1a5276,#2980b9);}
.h5{background:linear-gradient(135deg,#1e8449,#27ae60);}
.h6{background:linear-gradient(135deg,#0e6655,#17a589);}
.h10{background:linear-gradient(135deg,#6c3483,#9b59b6);}

.hook-card{background:white;border-radius:22px;padding:30px;box-shadow:0 16px 50px rgba(0,0,0,0.25);}
.hook-card h2{color:#764ba2;font-size:1.5em;margin-bottom:20px;font-weight:700;}

@media(max-width:600px){
  .choices{grid-template-columns:1fr;}
  header h1{font-size:1.9em;}
  .card{padding:24px;}
}
</style>
</head>
<body>
<div class="wrapper">

  <header>
    <h1>💾 RAID Quiz</h1>
    <p>CompTIA A+ Core 1 — Interactive Practice</p>
  </header>

  <!-- Mode buttons -->
  <div class="mode-bar">
    <button class="mode-btn active" onclick="setMode('flashcard')">🃏 Flashcards</button>
    <button class="mode-btn" onclick="setMode('mc')">🎯 Multiple Choice</button>
    <button class="mode-btn" onclick="setMode('hooks')">🧠 Memory Hooks</button>
  </div>

  <!-- Score strip (MC only) -->
  <div class="score-strip" id="scoreStrip" style="display:none;">
    <div class="score-pill">✅ Correct: <span id="scoreCorrect">0</span></div>
    <div class="score-pill">❌ Wrong: <span id="scoreWrong">0</span></div>
    <div class="score-pill">📋 Remaining: <span id="scoreLeft">0</span></div>
  </div>

  <!-- Progress -->
  <div class="progress-label" id="progressLabel">Card 1 of 46</div>
  <div class="progress-bar-wrap"><div class="progress-bar-fill" id="progressFill"></div></div>

  <!-- ── FLASHCARD MODE ── -->
  <div id="flashcardMode">
    <div class="flip-container" id="flipContainer" onclick="flipCard()">
      <div class="flip-inner" id="flipInner">
        <div class="flip-face flip-front">
          <div class="flip-badge" id="fcBadge">💾</div>
          <div class="flip-hint">Category</div>
          <div class="q-text" id="fcQuestion">Loading...</div>
          <div class="flip-hint" style="margin-top:20px;">👆 Tap to reveal answer</div>
        </div>
        <div class="flip-face flip-back">
          <div class="flip-badge">✅</div>
          <div class="a-text" id="fcAnswer">Answer</div>
          <div class="flip-hint">Did you know this?</div>
        </div>
      </div>
    </div>
    <div class="fc-nav">
      <button class="fc-btn btn-learning" onclick="markCard('learning')">❌ Still Learning</button>
      <button class="fc-btn btn-skip" onclick="markCard('skip')">⏭ Skip</button>
      <button class="fc-btn btn-know" onclick="markCard('know')">✅ I Know It</button>
    </div>
    <div style="text-align:center;margin-top:16px;color:rgba(255,255,255,.8);font-size:.9em;" id="fcKnownCount">Known: 0 / 46</div>
  </div>

  <!-- ── MULTIPLE CHOICE MODE ── -->
  <div id="mcMode" style="display:none;">
    <div class="card" id="mcCard">
      <div>
        <div class="card-meta" id="mcMeta">RAID CONCEPT</div>
        <div class="card-question" id="mcQuestion">Question loads here</div>
        <div class="choices" id="mcChoices"></div>
        <div class="mc-feedback" id="mcFeedback"></div>
      </div>
      <div style="text-align:center;">
        <button class="mc-next" id="mcNextBtn" onclick="nextMcQuestion()">Next Question →</button>
      </div>
    </div>
  </div>

  <!-- ── MEMORY HOOKS MODE ── -->
  <div id="hooksMode" style="display:none;">
    <div class="hook-card">
      <h2>🧠 Memory Hooks — All RAID Levels</h2>
      <div class="hooks-grid">
        <div class="hook-tile h0"><div class="lvl">RAID 0</div><div class="txt">0 = Zero safety 💀<br>Peppermint stripe<br>Fast but fragile</div></div>
        <div class="hook-tile h1"><div class="lvl">RAID 1</div><div class="txt">Mirror 🪞<br>Same reflection<br>50% space gone</div></div>
        <div class="hook-tile h5"><div class="lvl">RAID 5</div><div class="txt">Five is Alive 🔺<br>Parity = 2+3=5<br>Min 3 drives</div></div>
        <div class="hook-tile h6"><div class="lvl">RAID 6</div><div class="txt">Double Shield 🛡️🛡️<br>RAID 5 + 1 parity<br>Min 4 drives</div></div>
        <div class="hook-tile h10"><div class="lvl">RAID 10</div><div class="txt">Perfect TEN 🔟<br>🪞⚡ Mirror+Stripe<br>Best of both</div></div>
      </div>

      <div style="margin-top:30px;">
        <table style="width:100%;border-collapse:collapse;font-size:.95em;">
          <tr style="background:linear-gradient(135deg,#667eea,#764ba2);color:white;">
            <th style="padding:12px;border-radius:8px 0 0 0;">RAID</th>
            <th style="padding:12px;">Min Drives</th>
            <th style="padding:12px;">Tolerance</th>
            <th style="padding:12px;">Space</th>
            <th style="padding:12px;border-radius:0 8px 0 0;">Keyword</th>
          </tr>
          <tr style="background:#fde8e8;"><td style="padding:11px;font-weight:700;color:#c0392b;">RAID 0</td><td style="padding:11px;text-align:center;">2</td><td style="padding:11px;color:#c0392b;font-weight:700;">❌ None</td><td style="padding:11px;text-align:center;">100%</td><td style="padding:11px;">Striping</td></tr>
          <tr style="background:#d6eaf8;"><td style="padding:11px;font-weight:700;color:#1a5276;">RAID 1</td><td style="padding:11px;text-align:center;">2</td><td style="padding:11px;color:#1e8449;font-weight:700;">✅ 1 drive</td><td style="padding:11px;text-align:center;">50%</td><td style="padding:11px;">Mirroring</td></tr>
          <tr style="background:#d5f5e3;"><td style="padding:11px;font-weight:700;color:#1e8449;">RAID 5</td><td style="padding:11px;text-align:center;">3</td><td style="padding:11px;color:#1e8449;font-weight:700;">✅ 1 drive</td><td style="padding:11px;text-align:center;">Total−1</td><td style="padding:11px;">Parity</td></tr>
          <tr style="background:#d1f2eb;"><td style="padding:11px;font-weight:700;color:#0e6655;">RAID 6</td><td style="padding:11px;text-align:center;">4</td><td style="padding:11px;color:#1e8449;font-weight:700;">✅✅ 2 drives</td><td style="padding:11px;text-align:center;">Total−2</td><td style="padding:11px;">Double Parity</td></tr>
          <tr style="background:#e8daef;"><td style="padding:11px;font-weight:700;color:#6c3483;">RAID 10</td><td style="padding:11px;text-align:center;">4</td><td style="padding:11px;color:#1e8449;font-weight:700;">✅ 1/pair</td><td style="padding:11px;text-align:center;">50%</td><td style="padding:11px;">Stripe of Mirrors</td></tr>
        </table>
      </div>

      <div style="margin-top:24px;background:#eef2ff;border-radius:12px;padding:20px;">
        <div style="font-weight:700;color:#667eea;margin-bottom:10px;">🎓 The Parity Math Trick</div>
        <div style="color:#2c3e50;font-size:1em;line-height:1.8;">
          <strong>2 + 3 = 5</strong><br>
          Remove any number — the other two rebuild it:<br>
          <strong>? + 3 = 5</strong> → 2 &nbsp;|&nbsp; <strong>2 + ? = 5</strong> → 3<br>
          That's RAID 5 parity. One disk gone = rebuilt from the rest.
        </div>
      </div>
    </div>
  </div>

  <!-- ── RESULTS SCREEN ── -->
  <div class="results" id="resultsScreen">
    <div style="font-size:3em;">🏆</div>
    <h2>Quiz Complete!</h2>
    <div class="big-score" id="finalScore">0%</div>
    <div class="grade-msg" id="gradeMsg"></div>
    <p id="finalDetail"></p>
    <button class="restart-btn" onclick="restartMC()">🔄 Try Again</button>
  </div>

</div>

<script>
// ─── DATA ───────────────────────────────────────────────────────────────────
const cards = [
  {cat:"WHAT IS RAID",q:"What does RAID stand for?",a:"Redundant Array of Independent Disks\nCombines multiple physical disks into one logical drive",badge:"💾"},
  {cat:"RAID 0 — STRIPING",q:"What is the keyword for RAID 0?",a:"STRIPING\nData is split across all drives — odds on one, evens on the other",badge:"⚡"},
  {cat:"RAID 0 — STRIPING",q:"What is the minimum number of drives for RAID 0?",a:"2 drives minimum",badge:"💽"},
  {cat:"RAID 0 — STRIPING",q:"What is the fault tolerance of RAID 0?",a:"ZERO ❌\nIf 1 drive fails, ALL data is lost",badge:"💀"},
  {cat:"RAID 0 — STRIPING",q:"What is the usable space in RAID 0 with 2× 800MB drives?",a:"1600MB (100%)\nNo space lost to redundancy",badge:"📦"},
  {cat:"RAID 0 — STRIPING",q:"What is RAID 0 best used for?",a:"Speed-only tasks:\nVideo editing, gaming, temp/cache storage",badge:"🎮"},
  {cat:"RAID 0 — STRIPING",q:"What is the memory hook for RAID 0?",a:"0 = Zero safety 💀\nPeppermint stripe — odd on Disk 1, even on Disk 2",badge:"🧠"},
  {cat:"RAID 1 — MIRRORING",q:"What is the keyword for RAID 1?",a:"MIRRORING\nExact copy written to every drive simultaneously",badge:"🪞"},
  {cat:"RAID 1 — MIRRORING",q:"What is the minimum number of drives for RAID 1?",a:"2 drives minimum",badge:"💽"},
  {cat:"RAID 1 — MIRRORING",q:"What is the fault tolerance of RAID 1?",a:"1 entire drive can fail\nData survives on the mirror ✅",badge:"🛡️"},
  {cat:"RAID 1 — MIRRORING",q:"What is the usable space in RAID 1 with 2× 800MB drives?",a:"800MB (50%)\nHalf is used for the mirror copy",badge:"📦"},
  {cat:"RAID 1 — MIRRORING",q:"What is RAID 1 best used for?",a:"OS drives, critical data, small business\nBest basic redundancy",badge:"💻"},
  {cat:"RAID 1 — MIRRORING",q:"What is the memory hook for RAID 1?",a:"Mirror on the wall 🪞\nSame exact reflection\n1 = 1 mirror",badge:"🧠"},
  {cat:"RAID 5 — PARITY",q:"What is the keyword for RAID 5?",a:"STRIPING WITH PARITY\nParity rotates across all drives",badge:"🔺"},
  {cat:"RAID 5 — PARITY",q:"What is the minimum number of drives for RAID 5?",a:"3 drives minimum (can use more)",badge:"💽"},
  {cat:"RAID 5 — PARITY",q:"What is the fault tolerance of RAID 5?",a:"1 drive can fail\nParity data rebuilds the missing disk ✅",badge:"🛡️"},
  {cat:"RAID 5 — PARITY",q:"What is the usable space in RAID 5 with 3× 80GB drives?",a:"160GB\nTotal minus 1 drive worth of parity",badge:"📦"},
  {cat:"RAID 5 — PARITY",q:"What is RAID 5 best used for?",a:"File servers, NAS, small businesses\nMost common RAID in production",badge:"🖥️"},
  {cat:"RAID 5 — PARITY",q:"What is parity in RAID 5?",a:"Math-based recovery data\nLike 2+3=5 — remove any one number and the other two reveal it",badge:"🔢"},
  {cat:"RAID 5 — PARITY",q:"What is the memory hook for RAID 5?",a:"Five is Alive 🔺\nTriangle = 3 sides = 3 min drives\nP rotates across disks",badge:"🧠"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"What is the keyword for RAID 6?",a:"STRIPING WITH DOUBLE PARITY\nTwo parity blocks (P and Q) per row",badge:"🛡️"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"What is the minimum number of drives for RAID 6?",a:"4 drives minimum",badge:"💽"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"What is the fault tolerance of RAID 6?",a:"2 drives can fail simultaneously ✅✅\nStill operational",badge:"🛡️"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"What is the usable space in RAID 6 with 4× 1TB drives?",a:"2TB\nTotal minus 2 drives for double parity",badge:"📦"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"How does RAID 6 differ from RAID 5?",a:"RAID 6 has DOUBLE parity (P+Q)\nvs RAID 5 single parity (P)\nSurvives 2 failures vs 1",badge:"⚖️"},
  {cat:"RAID 6 — DOUBLE PARITY",q:"What is the memory hook for RAID 6?",a:"Double shield 🛡️🛡️\nRAID 5 + 1 extra parity\n6=5+1 | Min 4 drives (square has 4 sides)",badge:"🧠"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"What is RAID 10 also called?",a:"RAID 1+0 or Stripe of Mirrors\nA RAID of RAIDs",badge:"🔟"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"What is the minimum number of drives for RAID 10?",a:"4 drives (always an even number)",badge:"💽"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"How does RAID 10 work?",a:"Creates mirrored pairs (RAID 1)\nThen stripes data across the pairs (RAID 0)\nMirror first → stripe second",badge:"🪞"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"What is the fault tolerance of RAID 10?",a:"1 drive per mirror pair can fail ✅\nSystem survives",badge:"🛡️"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"What is the usable space in RAID 10?",a:"50%\nMirrors consume half the total capacity",badge:"📦"},
  {cat:"RAID 10 — STRIPE OF MIRRORS",q:"What is the memory hook for RAID 10?",a:"Perfect TEN 🔟\nRAID 1 + RAID 0\n🪞⚡ Mirror first, stripe second",badge:"🧠"},
  {cat:"RAID CATEGORIES",q:"Which RAID is failure resistant?",a:"RAID 1 and RAID 5\nProtect against data loss when a single disk fails",badge:"⚠️"},
  {cat:"RAID CATEGORIES",q:"Which RAID is fault tolerant?",a:"RAID 1, RAID 5, RAID 6\nArray keeps functioning after component failure",badge:"🛡️"},
  {cat:"RAID CATEGORIES",q:"Which RAID is disaster tolerant?",a:"RAID 10\nTwo independent zones, each with full data access\nLose half the array — still runs",badge:"💥"},
  {cat:"EXAM TRAPS",q:"Which RAID gives the most speed with no redundancy?",a:"RAID 0\nPure striping, fastest read/write\nZero fault tolerance",badge:"⚡"},
  {cat:"EXAM TRAPS",q:"Which RAID gives full redundancy with only 2 drives?",a:"RAID 1\nMirroring — simplest protection\n50% usable space",badge:"🪞"},
  {cat:"EXAM TRAPS",q:"Which RAIDs use parity to recover data?",a:"RAID 5 (single parity)\nRAID 6 (double parity)",badge:"🔢"},
  {cat:"EXAM TRAPS",q:"What happens in RAID 5 if 2 disks fail?",a:"The entire array fails ❌\nRAID 5 only tolerates 1 disk failure\nUse RAID 6 for 2-disk tolerance",badge:"💀"},
  {cat:"EXAM TRAPS",q:"Does RAID replace backups?",a:"NO ❌\nRAID provides redundancy/uptime\nBackups protect against accidental deletion, ransomware, fire, etc.",badge:"🚨"},
  {cat:"HARDWARE CONCEPTS",q:"Hardware RAID vs Software RAID?",a:"Hardware: dedicated controller card, faster, supports hot-swap\nSoftware: OS-based, cheaper, slower",badge:"🔧"},
  {cat:"HARDWARE CONCEPTS",q:"What is hot-swapping in RAID?",a:"Replacing a failed disk WITHOUT shutting down the OS\nCommon in hardware RAID",badge:"🔥"},
  {cat:"HARDWARE CONCEPTS",q:"What does the OS see in any RAID array?",a:"One single logical drive\nThe array appears as one volume regardless of physical disk count",badge:"💻"},
  {cat:"HARDWARE CONCEPTS",q:"What must be true about disks in a RAID array?",a:"Identical capacity, type, and performance\nSmallest disk determines max usable space",badge:"⚠️"},
  {cat:"EXAM TRAPS",q:"Which RAID loses exactly 1/3 of space to parity with 3 drives?",a:"RAID 5\n3 drives → 1 drive equivalent used for parity = 33% overhead",badge:"🔢"},
  {cat:"EXAM TRAPS",q:"If asked for redundancy using PARITY specifically, which RAID?",a:"RAID 5\nThe exam keyword is parity = RAID 5\n(Not RAID 1 which uses mirroring)",badge:"🎯"},
];

// ─── MULTIPLE CHOICE DATA ────────────────────────────────────────────────────
const mcQuestions = [
  {q:"A company needs MAXIMUM read/write speed and does NOT care about data loss. Which RAID?",correct:"RAID 0",choices:["RAID 0","RAID 1","RAID 5","RAID 10"],exp:"RAID 0 is pure striping — fastest possible, zero redundancy."},
  {q:"Which RAID requires the MINIMUM number of drives to achieve fault tolerance?",correct:"RAID 1",choices:["RAID 0","RAID 1","RAID 5","RAID 10"],exp:"RAID 1 needs only 2 drives and provides full mirroring."},
  {q:"A RAID 5 array has 3 drives of 500GB each. How much usable space is available?",correct:"1000 GB",choices:["500 GB","1000 GB","1500 GB","750 GB"],exp:"RAID 5 loses 1 drive equivalent to parity. 3×500GB − 500GB = 1000GB usable."},
  {q:"Which RAID can survive TWO simultaneous drive failures?",correct:"RAID 6",choices:["RAID 0","RAID 1","RAID 5","RAID 6"],exp:"RAID 6 has double parity (P+Q) allowing 2 simultaneous drive failures."},
  {q:"What is the keyword you must remember for RAID 5?",correct:"Parity",choices:["Striping","Mirroring","Parity","Redundancy"],exp:"RAID 5 = Striping with Parity. The parity rotates across all disks."},
  {q:"A technician has RAID 10 with 4 drives. How much usable space from 4× 1TB drives?",correct:"2 TB",choices:["4 TB","1 TB","2 TB","3 TB"],exp:"RAID 10 uses 50% for mirroring. 4TB total × 50% = 2TB usable."},
  {q:"Which RAID level is described as a 'RAID of RAIDs'?",correct:"RAID 10",choices:["RAID 5","RAID 6","RAID 10","RAID 1"],exp:"RAID 10 is two RAID 1 mirror pairs placed inside a RAID 0 stripe."},
  {q:"Which RAID offers zero fault tolerance?",correct:"RAID 0",choices:["RAID 1","RAID 5","RAID 6","RAID 0"],exp:"RAID 0 has zero redundancy. One disk fails = all data is lost."},
  {q:"What is the minimum number of drives required for RAID 5?",correct:"3",choices:["2","3","4","5"],exp:"RAID 5 requires a minimum of 3 drives — think triangle (3 sides)."},
  {q:"Which RAID is categorized as 'disaster tolerant'?",correct:"RAID 10",choices:["RAID 1","RAID 5","RAID 6","RAID 10"],exp:"RAID 10 has two independent zones — lose an entire mirror pair, still runs."},
  {q:"RAID 1 with 2× 1TB drives. How much usable storage does the OS see?",correct:"1 TB",choices:["2 TB","1 TB","500 GB","1.5 TB"],exp:"RAID 1 mirrors everything — 50% usable. 2×1TB = 1TB available."},
  {q:"A server needs parity-based redundancy and can survive 1 disk failure. Minimum 3 drives. Which RAID?",correct:"RAID 5",choices:["RAID 0","RAID 1","RAID 5","RAID 10"],exp:"RAID 5 = striping with parity, min 3 drives, survives 1 failure."},
  {q:"Which statement about RAID is TRUE?",correct:"RAID appears as a single logical drive to the OS",choices:["RAID replaces backups","RAID 0 has full redundancy","RAID appears as a single logical drive to the OS","RAID 5 needs minimum 4 drives"],exp:"The OS always sees RAID as one logical drive. RAID does NOT replace backups."},
  {q:"What allows replacing a failed RAID disk without shutting down the system?",correct:"Hot-swapping",choices:["Cold swap","Hot-swapping","Mirroring","Parity rebuild"],exp:"Hot-swapping = replace a disk while the system is running. Common in hardware RAID."},
  {q:"Which RAID uses BOTH striping AND mirroring together?",correct:"RAID 10",choices:["RAID 5","RAID 6","RAID 1","RAID 10"],exp:"RAID 10 = RAID 0 (stripe) + RAID 1 (mirror). Mirror pairs, then stripe across them."},
];

// ─── STATE ───────────────────────────────────────────────────────────────────
let mode = 'flashcard';
let fcIndex = 0;
let fcKnown = new Set();
let fcFlipped = false;
let fcOrder = [...Array(cards.length).keys()];

let mcIndex = 0;
let mcOrder = [];
let mcCorrect = 0;
let mcWrong = 0;
let mcAnswered = false;

// ─── MODE SWITCH ─────────────────────────────────────────────────────────────
function setMode(m) {
  mode = m;
  document.querySelectorAll('.mode-btn').forEach(b => b.classList.remove('active'));
  event.target.classList.add('active');
  document.getElementById('flashcardMode').style.display = 'none';
  document.getElementById('mcMode').style.display = 'none';
  document.getElementById('hooksMode').style.display = 'none';
  document.getElementById('scoreStrip').style.display = 'none';
  document.getElementById('resultsScreen').classList.remove('show');
  document.getElementById('progressLabel').style.display = 'block';
  document.getElementById('progressFill').parentElement.style.display = 'block';

  if (m === 'flashcard') {
    document.getElementById('flashcardMode').style.display = 'block';
    loadFlashcard();
  } else if (m === 'mc') {
    document.getElementById('scoreStrip').style.display = 'flex';
    document.getElementById('mcMode').style.display = 'block';
    startMC();
  } else {
    document.getElementById('hooksMode').style.display = 'block';
    document.getElementById('progressLabel').style.display = 'none';
    document.getElementById('progressFill').parentElement.style.display = 'none';
  }
}

// ─── FLASHCARD LOGIC ─────────────────────────────────────────────────────────
function loadFlashcard() {
  const i = fcOrder[fcIndex];
  const c = cards[i];
  fcFlipped = false;
  document.getElementById('flipInner').style.transform = '';
  document.getElementById('flipContainer').classList.remove('flipped');
  document.getElementById('fcBadge').textContent = c.badge;
  document.getElementById('fcQuestion').textContent = c.q;
  document.getElementById('fcAnswer').textContent = c.a;
  updateProgress(fcIndex + 1, cards.length, `Card ${fcIndex + 1} of ${cards.length}`);
  document.getElementById('fcKnownCount').textContent = `Known: ${fcKnown.size} / ${cards.length}`;
}

function flipCard() {
  document.getElementById('flipContainer').classList.toggle('flipped');
  fcFlipped = !fcFlipped;
}

function markCard(status) {
  const i = fcOrder[fcIndex];
  if (status === 'know') fcKnown.add(i);
  else fcKnown.delete(i);
  fcIndex = (fcIndex + 1) % cards.length;
  loadFlashcard();
}

// ─── MC LOGIC ────────────────────────────────────────────────────────────────
function startMC() {
  mcOrder = shuffle([...Array(mcQuestions.length).keys()]);
  mcIndex = 0; mcCorrect = 0; mcWrong = 0;
  updateScoreStrip();
  loadMC();
}

function loadMC() {
  if (mcIndex >= mcOrder.length) { showResults(); return; }
  mcAnswered = false;
  const q = mcQuestions[mcOrder[mcIndex]];
  document.getElementById('mcMeta').textContent = `Question ${mcIndex + 1} of ${mcOrder.length}`;
  document.getElementById('mcQuestion').textContent = q.q;
  const shuffled = shuffle([...q.choices]);
  document.getElementById('mcChoices').innerHTML = shuffled.map(c =>
    `<button class="choice-btn" onclick="answerMC(this,'${c.replace(/'/g,"\\'")}','${q.correct.replace(/'/g,"\\'")}','${q.exp.replace(/'/g,"\\'")}')">${c}</button>`
  ).join('');
  const fb = document.getElementById('mcFeedback');
  fb.className = 'mc-feedback'; fb.textContent = '';
  document.getElementById('mcNextBtn').className = 'mc-next';
  updateProgress(mcIndex + 1, mcOrder.length, `Question ${mcIndex + 1} of ${mcOrder.length}`);
}

function answerMC(btn, chosen, correct, exp) {
  if (mcAnswered) return;
  mcAnswered = true;
  const all = document.querySelectorAll('.choice-btn');
  all.forEach(b => {
    b.disabled = true;
    if (b.textContent === correct) b.classList.add('correct');
  });
  const fb = document.getElementById('mcFeedback');
  if (chosen === correct) {
    btn.classList.add('correct');
    mcCorrect++;
    fb.className = 'mc-feedback correct-fb show';
    fb.textContent = '✅ Correct! ' + exp;
  } else {
    btn.classList.add('wrong');
    mcWrong++;
    fb.className = 'mc-feedback wrong-fb show';
    fb.textContent = '❌ Wrong. ' + exp;
  }
  document.getElementById('mcNextBtn').className = 'mc-next show';
  updateScoreStrip();
}

function nextMcQuestion() { mcIndex++; loadMC(); }

function restartMC() {
  document.getElementById('resultsScreen').classList.remove('show');
  document.getElementById('mcMode').style.display = 'block';
  document.getElementById('scoreStrip').style.display = 'flex';
  document.getElementById('progressLabel').style.display = 'block';
  document.getElementById('progressFill').parentElement.style.display = 'block';
  startMC();
}

function showResults() {
  document.getElementById('mcMode').style.display = 'none';
  document.getElementById('scoreStrip').style.display = 'none';
  document.getElementById('progressLabel').style.display = 'none';
  document.getElementById('progressFill').parentElement.style.display = 'none';
  const pct = Math.round((mcCorrect / mcOrder.length) * 100);
  document.getElementById('finalScore').textContent = pct + '%';
  document.getElementById('finalDetail').textContent = `You got ${mcCorrect} of ${mcOrder.length} questions correct.`;
  let msg = pct >= 90 ? '🏆 Exam Ready!' : pct >= 75 ? '👍 Almost there! Review the tricky ones.' : '📚 Keep studying — you\'ve got this!';
  document.getElementById('gradeMsg').textContent = msg;
  document.getElementById('resultsScreen').classList.add('show');
}

function updateScoreStrip() {
  document.getElementById('scoreCorrect').textContent = mcCorrect;
  document.getElementById('scoreWrong').textContent = mcWrong;
  document.getElementById('scoreLeft').textContent = mcOrder.length - mcIndex;
}

// ─── HELPERS ─────────────────────────────────────────────────────────────────
function updateProgress(cur, total, label) {
  document.getElementById('progressLabel').textContent = label;
  document.getElementById('progressFill').style.width = Math.round((cur / total) * 100) + '%';
}

function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
  return arr;
}

// Keyboard shortcuts
document.addEventListener('keydown', e => {
  if (mode === 'flashcard') {
    if (e.key === ' ' || e.key === 'Enter') { e.preventDefault(); flipCard(); }
    if (e.key === 'ArrowRight' || e.key === 'k') markCard('know');
    if (e.key === 'ArrowLeft' || e.key === 'x') markCard('learning');
    if (e.key === 'ArrowDown' || e.key === 's') markCard('skip');
  }
  if (mode === 'mc' && e.key === 'ArrowRight' && document.getElementById('mcNextBtn').classList.contains('show')) nextMcQuestion();
});

// Init
loadFlashcard();
</script>
</body>
</html>
