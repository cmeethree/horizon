<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KEEP — Horizon Roadmap</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg: #161f1f;
  --bg2: #1e2929;
  --bg3: #253030;
  --teal: #486160;
  --tl: #6e9e9b;
  --tl2: #4a7876;
  --warm: #f5ede8;
  --bdr: rgba(110,158,155,0.18);
  --bdr2: rgba(110,158,155,0.38);
  --now: #6e9e9b;
  --next: #9ea86a;
  --later: #7a8aaa;
  --tx: #d8e8e7;
  --txm: #7aa8a5;
  --txd: #4a7270;
  --rbg: rgba(255,255,255,0.025);
  --rhv: rgba(110,158,155,0.06);
  --bnow: rgba(110,158,155,0.12);
  --bnext: rgba(158,168,106,0.12);
  --blater: rgba(122,138,170,0.12);
  --crit: #d96060;
  --high: #c8a050;
  --med: #7aa8a5;
  --low: #4a7270;
}

html, body {
  height: 100%;
  background: var(--bg);
  color: var(--tx);
  font-family: 'DM Sans', system-ui, sans-serif;
  font-size: 13px;
  line-height: 1.5;
}

/* ── LAYOUT ── */
.shell {
  display: flex;
  flex-direction: column;
  height: 100vh;
  overflow: hidden;
}

.topbar {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 28px;
  height: 56px;
  background: var(--bg2);
  border-bottom: 0.5px solid var(--bdr2);
  gap: 16px;
}

.topbar-left { display: flex; align-items: center; gap: 20px; }
.wordmark {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 19px; color: var(--tl);
  letter-spacing: 0.05em;
}
.subt {
  font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--txd); padding-left: 16px;
  border-left: 0.5px solid var(--bdr2);
}

.topbar-right { display: flex; gap: 8px; align-items: center; }

.fpill {
  padding: 5px 13px; border-radius: 20px; font-size: 11px;
  cursor: pointer; border: 0.5px solid var(--bdr); color: var(--txm);
  background: transparent; transition: all 0.12s; letter-spacing: 0.05em;
  font-family: inherit;
}
.fpill:hover { border-color: var(--tl); color: var(--tl); }
.fpill.on-all  { background: rgba(110,158,155,0.1); border-color: var(--bdr2); color: var(--tx); }
.fpill.on-now  { background: var(--bnow); border-color: var(--now); color: var(--now); }
.fpill.on-next { background: var(--bnext); border-color: var(--next); color: var(--next); }
.fpill.on-later   { background: var(--blater);    border-color: var(--later);    color: var(--later); }
.fpill.on-complete{ background: rgba(90,122,90,0.12);  border-color: #5a7a5a; color: #5a7a5a; }
.fpill.on-suggest { background: rgba(122,106,138,0.12); border-color: #7a6a8a; color: #7a6a8a; }

.addbtn {
  padding: 5px 14px; border-radius: 20px; font-size: 11px;
  cursor: pointer; border: 0.5px solid var(--bdr2); color: var(--tx);
  background: rgba(110,158,155,0.1); transition: all 0.12s;
  letter-spacing: 0.05em; font-family: inherit; margin-left: 8px;
}
.addbtn:hover { background: rgba(110,158,155,0.2); }

/* ── MAIN SCROLL AREA ── */
.main {
  flex: 1;
  overflow-y: auto;
  overflow-x: auto;
  padding: 0 28px 40px;
}

/* ── TABLE ── */
.tbl-wrap { min-width: 900px; }

.col-heads {
  display: grid;
  grid-template-columns: 26px 2.4fr 88px 110px 80px 56px 64px 96px 80px;
  gap: 0;
  padding: 10px 0 8px;
  border-bottom: 0.5px solid var(--bdr2);
  font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--txd);
  position: sticky; top: 0;
  background: var(--bg);
  z-index: 20;
}
.ch { padding: 0 6px; }

/* ── HORIZON ── */
.hz-hdr {
  display: flex; align-items: center; gap: 10px;
  padding: 18px 0 8px;
  position: sticky; top: 36px;
  background: var(--bg);
  z-index: 15;
}
.hz-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
.hz-lbl { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; font-weight: 500; }
.hz-ct { font-size: 11px; color: var(--txd); }
.hz-line { flex: 1; height: 0.5px; background: var(--bdr); }
.hz-add {
  padding: 3px 11px; border-radius: 20px; font-size: 10px;
  cursor: pointer; border: 0.5px solid var(--bdr); color: var(--txm);
  background: transparent; font-family: inherit; letter-spacing: 0.05em;
  transition: all 0.12s;
}
.hz-add:hover { border-color: var(--tl); color: var(--tl); }

.empty-zone {
  padding: 14px 0; text-align: center; font-size: 11px; color: var(--txd);
  border-bottom: 0.5px solid var(--bdr);
  cursor: default;
}

/* ── ROW ── */
.rwrap { position: relative; }
.rwrap.dragging { opacity: 0.3; }
.rwrap.dov-a::before {
  content: ''; position: absolute; top: 0; left: 0; right: 0;
  height: 2px; background: var(--tl); z-index: 30; border-radius: 1px;
}
.rwrap.dov-b::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0;
  height: 2px; background: var(--tl); z-index: 30; border-radius: 1px;
}

.row {
  display: grid;
  grid-template-columns: 26px 2.4fr 88px 110px 80px 56px 64px 96px 80px;
  gap: 0; align-items: center;
  border-bottom: 0.5px solid var(--bdr);
  background: var(--rbg);
  min-height: 44px;
  transition: background 0.1s;
}
.row:hover { background: var(--rhv); }

.dh {
  width: 26px; display: flex; align-items: center; justify-content: center;
  cursor: grab; color: var(--txd); font-size: 13px; user-select: none;
}
.dh:active { cursor: grabbing; }

.cell { padding: 5px 6px; min-width: 0; }

.cell input, .cell select, .cell textarea {
  width: 100%; background: transparent; border: none; outline: none;
  font-family: 'DM Sans', system-ui, sans-serif; font-size: 12px;
  color: var(--tx); padding: 0; resize: none;
}
.cell input::placeholder { color: var(--txd); }
.cell select { cursor: pointer; appearance: none; -webkit-appearance: none; }
.cell select option { background: #1e2929; color: #d8e8e7; }

.cell input:focus, .cell select:focus, .cell textarea:focus {
  background: rgba(110,158,155,0.08); border-radius: 3px;
  box-shadow: 0 0 0 1px var(--tl2); padding: 2px 4px;
}

.row-actions { display: flex; align-items: center; gap: 4px; padding: 0 4px; }
.exptgl {
  cursor: pointer; font-size: 10px; color: var(--txm);
  user-select: none; padding: 4px 9px;
  transition: all 0.12s; line-height: 1;
  background: rgba(110,158,155,0.08); border: 0.5px solid var(--bdr);
  border-radius: 20px; font-family: inherit; letter-spacing: 0.04em;
  white-space: nowrap;
}
.exptgl:hover { color: var(--tl); border-color: var(--tl); background: rgba(110,158,155,0.14); }
.delbtn {
  width: 22px; height: 22px; display: flex; align-items: center; justify-content: center;
  cursor: pointer; color: var(--txd); border: none; background: transparent;
  font-size: 12px; opacity: 0; transition: opacity 0.12s, color 0.12s;
  border-radius: 3px; font-family: inherit;
}
.row:hover .delbtn { opacity: 1; }
.delbtn:hover { color: #e26060; }

/* ── EXPAND ROW ── */
.exprow { display: none; border-bottom: 0.5px solid var(--bdr); background: rgba(0,0,0,0.12); }
.exprow.open { display: block; }
.expgrid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 10px;
  padding: 10px 34px 14px;
}
.expfield { display: flex; flex-direction: column; gap: 4px; }
.explbl { font-size: 9px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--txd); }
.exptxa {
  background: rgba(110,158,155,0.04); border: 0.5px solid var(--bdr);
  border-radius: 4px; padding: 7px 8px; font-size: 11px; color: var(--tx);
  font-family: 'DM Sans', system-ui, sans-serif; resize: vertical;
  min-height: 60px; outline: none; width: 100%; line-height: 1.55;
}
.exptxa:focus { border-color: var(--tl2); box-shadow: 0 0 0 1px var(--tl2); }
.expinp {
  background: rgba(110,158,155,0.04); border: 0.5px solid var(--bdr);
  border-radius: 4px; padding: 6px 8px; font-size: 11px; color: var(--tx);
  font-family: 'DM Sans', system-ui, sans-serif; outline: none; width: 100%;
}
.expinp:focus { border-color: var(--tl2); }
.expinp-link { color: var(--tl); }

/* expand tabs */
.exp-tabs { display:flex; gap:0; border-bottom:0.5px solid var(--bdr); padding: 0 34px; }
.exp-tab {
  padding: 8px 14px; font-size:10px; letter-spacing:0.09em; text-transform:uppercase;
  color:var(--txd); cursor:pointer; border-bottom: 1.5px solid transparent;
  margin-bottom:-0.5px; background:none; border-top:none; border-left:none; border-right:none;
  font-family:inherit; transition: color 0.12s, border-color 0.12s;
}
.exp-tab:hover { color:var(--txm); }
.exp-tab.active { color:var(--tl); border-bottom-color:var(--tl); }
.exp-pane { display:none; }
.exp-pane.active { display:block; }

/* job stories */
.jobs-wrap { padding: 10px 34px 14px; display:flex; flex-direction:column; gap:10px; }
.job-card {
  background: rgba(110,158,155,0.04); border:0.5px solid var(--bdr);
  border-radius:4px; padding:10px 12px; display:grid;
  grid-template-columns: 80px 1fr; gap:6px 10px; align-items:start;
  position:relative;
}
.job-lbl { font-size:9px; letter-spacing:0.1em; text-transform:uppercase; color:var(--txd); padding-top:6px; }
.job-inp {
  background:transparent; border:none; border-bottom:0.5px solid var(--bdr);
  outline:none; font-family:inherit; font-size:11px; color:var(--tx);
  padding: 4px 0; width:100%; transition: border-color 0.12s;
}
.job-inp:focus { border-bottom-color:var(--tl2); }
.job-inp::placeholder { color:var(--txd); }
.job-del {
  position:absolute; top:8px; right:8px; background:none; border:none;
  color:var(--txd); font-size:11px; cursor:pointer; opacity:0; transition:opacity 0.12s, color 0.12s;
  font-family:inherit;
}
.job-card:hover .job-del { opacity:1; }
.job-del:hover { color:#e26060; }
.add-job-btn {
  align-self:flex-start; padding:4px 12px; border-radius:20px; font-size:10px;
  cursor:pointer; border:0.5px solid var(--bdr); color:var(--txm);
  background:transparent; font-family:inherit; letter-spacing:0.05em; transition:all 0.12s;
}
.add-job-btn:hover { border-color:var(--tl); color:var(--tl); }

/* ── STATS BAR ── */
.statsbar {
  display: flex; gap: 24px;
  padding: 14px 28px;
  border-top: 0.5px solid var(--bdr);
  background: var(--bg2);
  font-size: 10px; color: var(--txm); letter-spacing: 0.06em;
  flex-shrink: 0;
}
.sv { font-size: 20px; color: var(--tx); font-weight: 400; display: block; line-height: 1.2; font-family: 'DM Serif Display', Georgia, serif; }
</style>
</head>
<body>

<div class="shell">

  <!-- TOP BAR -->
  <div class="topbar">
    <div class="topbar-left">
      <span class="wordmark">KEEP</span>
      <span class="subt">Horizon Roadmap</span>
    </div>
    <div class="topbar-right">
      <button class="fpill on-all" id="f-all"   onclick="setFilter('all')">All</button>
      <button class="fpill"        id="f-now"   onclick="setFilter('now')">Now</button>
      <button class="fpill"        id="f-next"  onclick="setFilter('next')">Next</button>
      <button class="fpill"        id="f-later"    onclick="setFilter('later')">Later</button>
      <button class="fpill"        id="f-complete" onclick="setFilter('complete')">Complete</button>
      <button class="fpill"        id="f-suggest"  onclick="setFilter('suggest')">Suggestion Box</button>
      <button class="addbtn" onclick="addRow(null)">+ Add initiative</button>
    </div>
  </div>

  <!-- SCROLL BODY -->
  <div class="main" id="main">
    <div class="tbl-wrap" id="root"></div>
  </div>

  <!-- STATS BAR -->
  <div class="statsbar" id="sb"></div>

</div>

<script>
// ── DATA ──
let filter = 'all';
let dragSrc = null, dragOver = null, dragPos = null;

const CATS  = ['KAI','Analytics','KEEP Cold','Experience (CX)','Operations','Engineering',''];
const AREAS = ['Product','Engineering','Experience (CX)','Operations',''];
const PRIS  = ['Critical','High','Medium','Low'];
const SIZES = ['XS','S','M','L','XL','XXL'];
const VALS  = ['$','$$','$$$','$$$$'];

let rows = [
  {id:1, sprint:'now', cat:'KAI', area:'Product',
   title:'Daily Symptom Tracking', priority:'Medium', size:'S', value:'$$',
   problem:'Users cannot track individual symptoms in Kai or understand daily/weekly patterns over time.',
   why:'Would allow us to begin developing and testing engagement moments via email and build a habit loop around symptom logging.',
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:2, sprint:'now', cat:'KAI', area:'Product',
   title:'Saved Snippets / Bookmarking', priority:'High', size:'L', value:'$$$',
   problem:'Users cannot save tips or useful content — they have to ask Kai for the same information each time they want it.',
   why:'Would add more value to Kai and give users a tool to understand patterns over time that they can share with their HCP. Verified by user survey.',
   kpi:'WAU',
   scope:'• Daily/weekly symptom tracking initiation\n• Nudges to log symptom severity\n• Custom reminders with Kai\n• Contextual tips and content related to tracking\n• Weekly symptom report/summary\n• Saveable "report card" shareable with HCP',
   notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:3, sprint:'now', cat:'KAI', area:'Product',
   title:'Enhanced Onboarding', priority:'Medium', size:'M', value:'$$',
   problem:"Currently does not feel like users are being onboarded in a guided way — feels like choose your own adventure.",
   why:"Two-fold: (1) capture disease/history context to give Kai more intelligence, (2) create a guided experience that helps users understand what Kai is and can do.",
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:4, sprint:'now', cat:'KAI', area:'Product',
   title:'Scale check-in for other disease states', priority:'Critical', size:'M', value:'$$$',
   problem:"Check-in process is engineered solely for PBC — difficult to scale to other disease states.",
   why:'Scalability is a requirement to expand. Kai must leverage the right check-in templates per disease so relevant questions are asked.',
   kpi:'',
   scope:'• Modify check-in to support other disease states (templated process)\n• Allow business owners to create and manage flows outside of code\n• Allow admin users to modify flows without pushing app updates',
   notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:5, sprint:'now', cat:'KAI', area:'Product',
   title:'Save Doctor Questions', priority:'Critical', size:'XL', value:'$$$',
   problem:"Example HCP questions Kai prepares are not saved — users cannot access this content later when talking to their doctor.",
   why:"Users need to access Kai-generated HCP questions at a later date. Also useful to save Iqirvo/drug summary info introduced at end of weekly check-in.",
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:6, sprint:'now', cat:'KAI', area:'Product',
   title:'User Satisfaction Feedback', priority:'Medium', size:'M', value:'$$',
   problem:"Not able to collect whether Kai has addressed user concerns — do not know if Kai is closing the loop on conversations.",
   why:"Getting positive/negative feedback at the end of a conversation stream helps us understand if Kai is successfully helping users.",
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:7, sprint:'now', cat:'KAI', area:'Product',
   title:'Auto-fill prompt suggestions (ChatGPT style)', priority:'High', size:'L', value:'$$',
   problem:"Users sometimes do not know what to ask Kai — no disease-specific prompt scaffolding exists.",
   why:'Would give users ideas specific to their disease and make Kai feel contextually aware of what patients might want to discuss.',
   kpi:'', scope:'', notes:'Similar to how ChatGPT offers prompt suggestions when a user starts typing', ref:'', expanded:false},

  {id:8, sprint:'now', cat:'Analytics', area:'Product',
   title:'Connect KEEP Cold hardware to mobile app', priority:'Low', size:'L', value:'$$$',
   problem:'Require ability to connect new hardware to mobile for launch.',
   why:'Core requirement for KEEP Cold program launch and unified user experience.',
   kpi:'', scope:'', notes:'Do we want to connect KEEP Cold to legacy or new app (KAI)?', ref:'', expanded:false},

  {id:9, sprint:'now', cat:'KAI', area:'Experience (CX)',
   title:'Centralized intelligent engagement engine (Braze)', priority:'Low', size:'L', value:'$$$',
   problem:'Fragmented process to intelligently engage users across touchpoints.',
   why:'Scalable engagement infrastructure, reduced user churn.',
   kpi:'', scope:'', notes:'Cost structure and ability to sign BAA / health privacy', ref:'', expanded:false},

  {id:10, sprint:'now', cat:'KEEP Cold', area:'Engineering',
   title:'Merge legacy app into KAI', priority:'Medium', size:'L', value:'$$$',
   problem:'Fragmented codebase creates development inefficiency and inconsistent user experience.',
   why:'Development efficiency, easier upkeep, and improved user experience across the platform.',
   kpi:'', scope:'', notes:'Can we handle adverse event reporting and is the lift worth it?', ref:'', expanded:false},

  {id:11, sprint:'next', cat:'KAI', area:'Operations',
   title:'New Indication / Therapeutic Onboarding', priority:'Medium', size:'L', value:'$$$',
   problem:'Ability to streamline the onboarding flow for new disease states / therapeutic programs.',
   why:'Ease of onboarding new programs — reduces time-to-launch for new brand partnerships.',
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:12, sprint:'later', cat:'KAI', area:'Experience (CX)',
   title:'Export Insight Cards for Email Engagement', priority:'High', size:'L', value:'$$$',
   problem:'No way to export or distribute Kai-generated insight cards outside the app.',
   why:'Would allow us to develop and test engagement moments via email and extend Kai reach beyond the app.',
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:13, sprint:'later', cat:'Analytics', area:'Operations',
   title:'Self Serve Enterprise Data Platform', priority:'Medium', size:'XXL', value:'$$$',
   problem:"Enterprise customers want to login to a platform and engage with their data independently without reaching out to the KEEP team.",
   why:"Creates a platform buying experience similar to other tools our ICPs purchase — reduces support overhead and increases perceived value.",
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:14, sprint:'later', cat:'KAI', area:'Experience (CX)',
   title:'Progress Meter to Payment + Gifting Integration', priority:'Medium', size:'L', value:'$$$',
   problem:"If we are compensating users for using Kai, there is no visibility into progress toward payment eligibility.",
   why:'A progress meter for every check-in creates a gamified motivation loop and increases session completion rates.',
   kpi:'',
   scope:'• View amount of compensation\n• See progress toward payment threshold\n• View weeks and sessions completed to meet payment requirement\n• See days to payment eligibility',
   notes:'', ref:'https://patient-compensation-272u.bolt.host/', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},

  {id:15, sprint:'later', cat:'KAI', area:'Operations',
   title:'B2B sponsor question submission (insight targeting)', priority:'Medium', size:'M', value:'$$',
   problem:'No mechanism for B2B customers (sponsors) to submit specific questions they want answered from patient conversations.',
   why:'Creates a direct value exchange for pharma brand teams — they get structured real-world evidence, we unlock a new revenue lever.',
   kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}]},
];

let nid = 16;

const HZ = [
  { key:'now',       label:'Now',            dot:'#6e9e9b' },
  { key:'next',      label:'Next',           dot:'#9ea86a' },
  { key:'later',     label:'Later',          dot:'#7a8aaa' },
  { key:'complete',  label:'Complete',       dot:'#5a7a5a' },
  { key:'suggest',   label:'Suggestion Box', dot:'#7a6a8a' },
];

// ── FILTER ──
function setFilter(f) {
  filter = f;
  ['all','now','next','later','complete','suggest'].forEach(k => {
    const el = document.getElementById('f-'+k);
    if (!el) return;
    el.className = 'fpill';
    if (k === f) {
      if (k==='all') el.classList.add('on-all');
      else if (k==='now') el.classList.add('on-now');
      else if (k==='next') el.classList.add('on-next');
      else if (k==='later') el.classList.add('on-later');
      else if (k==='complete') el.classList.add('on-complete');
      else el.classList.add('on-suggest');
    }
  });
  render();
}

// ── CRUD ──
function addRow(sprint) {
  const s = sprint || (filter !== 'all' ? filter : 'now');
  rows.push({ id:nid++, sprint:s, cat:'KAI', area:'Product', title:'', priority:'Medium',
    size:'M', value:'$$', problem:'', why:'', kpi:'', scope:'', notes:'', ref:'', expanded:false, jobs:[{as:'',when:'',want:'',so:'',inorder:''}] });
  render();
  setTimeout(() => {
    const els = document.querySelectorAll('.title-input');
    if (els.length) els[els.length-1].focus();
  }, 40);
}

function del(id) { rows = rows.filter(r => r.id !== id); render(); }

function upd(id, f, v) {
  const r = rows.find(r => r.id === id);
  if (!r) return;
  r[f] = v;
  if (f === 'sprint') render();
}

function tog(id) {
  const r = rows.find(r => r.id === id);
  if (r) r.expanded = !r.expanded;
  render();
}

// ── DRAG ──
function dstart(e, id) {
  dragSrc = id;
  e.dataTransfer.effectAllowed = 'move';
  setTimeout(() => {
    const el = document.querySelector(`[data-rid="${id}"]`);
    if (el) el.classList.add('dragging');
  }, 0);
}

function dover(e, id) {
  e.preventDefault();
  if (id === dragSrc) return;
  const el = document.querySelector(`[data-rid="${id}"]`);
  if (dragOver && dragOver !== el) dragOver.classList.remove('dov-a','dov-b');
  if (el) {
    const rect = el.getBoundingClientRect();
    const p = e.clientY < rect.top + rect.height / 2 ? 'above' : 'below';
    dragPos = p;
    el.classList.remove('dov-a','dov-b');
    el.classList.add(p === 'above' ? 'dov-a' : 'dov-b');
    dragOver = el;
  }
}

function ddrop(e, tid, ts) {
  e.preventDefault();
  if (dragOver) dragOver.classList.remove('dov-a','dov-b');
  if (dragSrc === null) return;
  const src = rows.find(r => r.id === dragSrc);
  if (!src) return;
  src.sprint = ts;
  if (dragSrc !== tid) {
    const si = rows.findIndex(r => r.id === dragSrc);
    rows.splice(si, 1);
    const ti = rows.findIndex(r => r.id === tid);
    rows.splice(dragPos === 'below' ? ti + 1 : ti, 0, src);
  }
  dragSrc = null; dragOver = null; dragPos = null;
  render();
}

function dzone(e, s) {
  e.preventDefault();
  if (dragOver) dragOver.classList.remove('dov-a','dov-b');
  const src = rows.find(r => r.id === dragSrc);
  if (src) src.sprint = s;
  dragSrc = null; dragOver = null; dragPos = null;
  render();
}

function dend() {
  if (dragOver) dragOver.classList.remove('dov-a','dov-b');
  document.querySelectorAll('.dragging').forEach(el => el.classList.remove('dragging'));
  dragSrc = null; dragOver = null; dragPos = null;
}

// ── HELPERS ──
function priColor(p) {
  return p==='Critical'?'#d96060': p==='High'?'#c8a050': p==='Medium'?'#7aa8a5':'#4a7270';
}
function valColor(v) {
  return v==='$'?'#4a7270': v==='$$'?'#7aa8a5': v==='$$$'?'#9ea86a':'#c8a050';
}
function esc(s) {
  return String(s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// ── RENDER ROW ──
function rRow(r) {
  const pc = priColor(r.priority);
  const vc = valColor(r.value);
  return `
<div class="rwrap" data-rid="${r.id}" draggable="true"
  ondragstart="dstart(event,${r.id})"
  ondragover="dover(event,${r.id})"
  ondrop="ddrop(event,${r.id},'${r.sprint}')"
  ondragend="dend()">
  <div class="row">
    <div class="dh" title="Drag to reorder">⠿</div>
    <div class="cell">
      <input class="title-input" type="text" value="${esc(r.title)}" placeholder="Initiative title…"
        oninput="upd(${r.id},'title',this.value)" />
    </div>
    <div class="cell">
      <select onchange="upd(${r.id},'cat',this.value)">
        ${CATS.map(c=>`<option value="${c}" ${r.cat===c?'selected':''}>${c||'— Category'}</option>`).join('')}
      </select>
    </div>
    <div class="cell">
      <select onchange="upd(${r.id},'area',this.value)">
        ${AREAS.map(a=>`<option value="${a}" ${r.area===a?'selected':''}>${a||'— Area'}</option>`).join('')}
      </select>
    </div>
    <div class="cell">
      <select onchange="upd(${r.id},'priority',this.value)" style="color:${pc}">
        ${PRIS.map(p=>`<option value="${p}" ${r.priority===p?'selected':''} style="color:${priColor(p)}">${p}</option>`).join('')}
      </select>
    </div>
    <div class="cell" style="text-align:center">
      <select onchange="upd(${r.id},'size',this.value)" style="color:var(--txm);text-align:center;width:100%">
        ${SIZES.map(s=>`<option value="${s}" ${r.size===s?'selected':''}>${s}</option>`).join('')}
      </select>
    </div>
    <div class="cell" style="text-align:center">
      <select onchange="upd(${r.id},'value',this.value)" style="color:${vc};text-align:center;width:100%">
        ${VALS.map(v=>`<option value="${v}" ${r.value===v?'selected':''}>${v}</option>`).join('')}
      </select>
    </div>
    <div class="cell">
      <select onchange="upd(${r.id},'sprint',this.value)" style="font-size:11px;color:var(--txm);width:100%">
        <option value="now"      ${r.sprint==='now'      ?'selected':''}>1 – Now</option>
        <option value="next"     ${r.sprint==='next'     ?'selected':''}>2 – Next</option>
        <option value="later"    ${r.sprint==='later'    ?'selected':''}>3 – Later</option>
        <option value="complete" ${r.sprint==='complete' ?'selected':''}>4 – Complete</option>
        <option value="suggest"  ${r.sprint==='suggest'  ?'selected':''}>5 – Suggestion Box</option>
      </select>
    </div>
    <div class="cell row-actions">
      <button class="exptgl" onclick="tog(${r.id})">${r.expanded?'▾ Close':'▸ Details'}</button>
      <button class="delbtn" onclick="del(${r.id})" title="Remove row">✕</button>
    </div>
  </div>
  <div class="exprow ${r.expanded?'open':''}">
    <div class="exp-tabs">
      <button class="exp-tab ${r.activeTab!=='jobs'?'active':''}" onclick="setTab(${r.id},'context')">Context</button>
      <button class="exp-tab ${r.activeTab==='jobs'?'active':''}" onclick="setTab(${r.id},'jobs')">Job Stories</button>
    </div>
    <div class="exp-pane ${r.activeTab!=='jobs'?'active':''}" id="pane-ctx-${r.id}">
      <div class="expgrid">
        <div class="expfield">
          <label class="explbl">What is the problem / opportunity?</label>
          <textarea class="exptxa" style="min-height:72px" oninput="upd(${r.id},'problem',this.value)">${esc(r.problem)}</textarea>
        </div>
        <div class="expfield">
          <label class="explbl">Why is this important?</label>
          <textarea class="exptxa" style="min-height:72px" oninput="upd(${r.id},'why',this.value)">${esc(r.why)}</textarea>
        </div>
        <div class="expfield">
          <label class="explbl">Scope (Capabilities)</label>
          <textarea class="exptxa" style="min-height:72px" oninput="upd(${r.id},'scope',this.value)">${esc(r.scope)}</textarea>
        </div>
        <div class="expfield" style="display:flex;flex-direction:column;gap:8px;">
          <div class="expfield">
            <label class="explbl">KPI</label>
            <input class="expinp" type="text" value="${esc(r.kpi)}" placeholder="e.g. WAU, DAU…" oninput="upd(${r.id},'kpi',this.value)" />
          </div>
          <div class="expfield">
            <label class="explbl">Notes / Comments</label>
            <input class="expinp" type="text" value="${esc(r.notes)}" placeholder="Internal notes…" oninput="upd(${r.id},'notes',this.value)" />
          </div>
          <div class="expfield">
            <label class="explbl">Reference Link</label>
            <input class="expinp expinp-link" type="text" value="${esc(r.ref)}" placeholder="https://…" oninput="upd(${r.id},'ref',this.value)" />
          </div>
        </div>
      </div>
    </div>
    <div class="exp-pane ${r.activeTab==='jobs'?'active':''}" id="pane-jobs-${r.id}">
      <div class="jobs-wrap">
        ${(r.jobs||[]).map((j,ji) => `
        <div class="job-card">
          <span class="job-lbl">As a</span>
          <input class="job-inp" type="text" value="${esc(j.as)}" placeholder="e.g. patient with PBC…" oninput="updJob(${r.id},${ji},'as',this.value)" />
          <span class="job-lbl">When I</span>
          <input class="job-inp" type="text" value="${esc(j.when)}" placeholder="e.g. completing my weekly check-in…" oninput="updJob(${r.id},${ji},'when',this.value)" />
          <span class="job-lbl">I want to</span>
          <input class="job-inp" type="text" value="${esc(j.want)}" placeholder="e.g. log how itchy I felt each day…" oninput="updJob(${r.id},${ji},'want',this.value)" />
          <span class="job-lbl">So I can</span>
          <input class="job-inp" type="text" value="${esc(j.so)}" placeholder="e.g. see patterns over time…" oninput="updJob(${r.id},${ji},'so',this.value)" />
          <span class="job-lbl">In order to</span>
          <input class="job-inp" type="text" value="${esc(j.inorder)}" placeholder="e.g. have a more informed conversation with my HCP…" oninput="updJob(${r.id},${ji},'inorder',this.value)" />
          <button class="job-del" onclick="delJob(${r.id},${ji})">✕</button>
        </div>`).join('')}
        <button class="add-job-btn" onclick="addJob(${r.id})">+ Add job story</button>
      </div>
    </div>
  </div>
</div>`;
}

// ── RENDER ALL ──
function render() {
  const root = document.getElementById('root');
  const vis  = filter === 'all' ? HZ : HZ.filter(h => h.key === filter);

  let html = `
<div class="col-heads">
  <div class="ch"></div>
  <div class="ch">Initiative</div>
  <div class="ch">Category</div>
  <div class="ch">Area</div>
  <div class="ch">Priority</div>
  <div class="ch" style="text-align:center">Size</div>
  <div class="ch" style="text-align:center">Value</div>
  <div class="ch">Sprint group</div>
  <div class="ch"></div>
</div>`;

  vis.forEach(h => {
    const hrows = rows.filter(r => r.sprint === h.key);
    html += `
<div>
  <div class="hz-hdr">
    <div class="hz-dot" style="background:${h.dot}"></div>
    <span class="hz-lbl" style="color:${h.dot}">${h.label}</span>
    <span class="hz-ct">${hrows.length} initiative${hrows.length !== 1 ? 's' : ''}</span>
    <div class="hz-line"></div>
    <button class="hz-add" onclick="addRow('${h.key}')">+ Add</button>
  </div>
  <div ondragover="event.preventDefault()" ondrop="dzone(event,'${h.key}')">
    ${hrows.length === 0
      ? `<div class="empty-zone" ondragover="event.preventDefault()" ondrop="dzone(event,'${h.key}')">Drop an initiative here or click + Add</div>`
      : hrows.map(rRow).join('')}
  </div>
</div>`;
  });

  root.innerHTML = html;

  // Stats
  const total = rows.length;
  const now   = rows.filter(r => r.sprint === 'now').length;
  const next  = rows.filter(r => r.sprint === 'next').length;
  const later = rows.filter(r => r.sprint === 'later').length;
  const crit  = rows.filter(r => r.priority === 'Critical').length;
  const high  = rows.filter(r => r.priority === 'High').length;

  const complete = rows.filter(r => r.sprint === 'complete').length;
  const suggest  = rows.filter(r => r.sprint === 'suggest').length;
  document.getElementById('sb').innerHTML = `
    <div><span class="sv">${total}</span>total</div>
    <div><span class="sv" style="color:#6e9e9b">${now}</span>now</div>
    <div><span class="sv" style="color:#9ea86a">${next}</span>next</div>
    <div><span class="sv" style="color:#7a8aaa">${later}</span>later</div>
    <div><span class="sv" style="color:#5a7a5a">${complete}</span>complete</div>
    <div><span class="sv" style="color:#7a6a8a">${suggest}</span>suggestions</div>
    <div style="margin-left:auto;display:flex;gap:24px;">
      <div><span class="sv" style="color:#d96060">${crit}</span>critical</div>
      <div><span class="sv" style="color:#c8a050">${high}</span>high</div>
    </div>`;
}

function setTab(id, tab) {
  const r = rows.find(r => r.id === id);
  if (r) r.activeTab = tab;
  render();
}

function addJob(id) {
  const r = rows.find(r => r.id === id);
  if (!r) return;
  if (!r.jobs) r.jobs = [];
  r.jobs.push({as:'', when:'', want:'', so:'', inorder:''});
  render();
}

function delJob(id, ji) {
  const r = rows.find(r => r.id === id);
  if (!r || !r.jobs) return;
  r.jobs.splice(ji, 1);
  render();
}

function updJob(id, ji, field, value) {
  const r = rows.find(r => r.id === id);
  if (!r || !r.jobs || !r.jobs[ji]) return;
  r.jobs[ji][field] = value;
}

render();
</script>
</body>
</html>
