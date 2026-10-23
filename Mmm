<html lang="th"><head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>เครื่องคิดเลขวิทยาศาสตร์</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Thai:wght@300;400;500;600&amp;family=Prompt:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
<style>
* { margin:0; padding:0; box-sizing:border-box; }
body {
  background:#050507;
  color:#fff;
  font-family:'Prompt','Noto Sans Thai',sans-serif;
  min-height:100vh;
  padding:20px;
}
.app {
  max-width:1450px;
  margin:0 auto;
  display:grid;
  grid-template-columns:65% 1fr;
  gap:24px;
}
.left, .right { display:flex; flex-direction:column; gap:24px; }
.card {
  background:#141420;
  border-radius:24px;
  padding:22px;
  box-shadow:0 10px 30px rgba(0,0,0,.4);
}
.display {
  background:#0c0c14;
  border-radius:18px;
  padding:24px;
  min-height:210px;
  display:flex;
  flex-direction:column;
  position:relative;
}
.expr {
  font-size:32px; color:#7a7a8a; text-align:right; min-height:42px;
  word-break:break-all; font-weight:300; padding-right:40px;
}
.result {
  font-size:80px; font-weight:600; text-align:right; line-height:1;
  margin-top:8px; color:#fff; letter-spacing:-1px;
}
.divider { height:1px; background:#222230; margin:18px 0 14px; }
.bottom { display:flex; justify-content:space-between; font-size:15px; color:#6b7280; }
.bottom-right { color:#9aa0aa; }

.backspace{position:absolute;top:12px;right:14px;background:transparent;border:none;color:#6b7280;font-size:22px;cursor:pointer;padding:6px 10px;border-radius:8px;transition:.15s;z-index:5}
.backspace:hover{color:#e5e7eb;background:#1c1c28}

.keypad { display:grid; grid-template-columns:repeat(6,1fr); gap:12px; margin-top:22px; }
.btn {
  height:60px; background:#1f1f2b; border:none; border-radius:14px;
  color:#fff; font-size:22px; font-family:inherit; font-weight:500;
  cursor:pointer; transition:.15s; display:flex; align-items:center; justify-content:center;
}
.btn:hover { background:#272735; transform:translateY(-1px); }
.btn:active { transform:scale(.96); }
.btn-gold { background:#d4a017; color:#000; font-weight:600; }
.btn-gold.active { background:#f0b90b; box-shadow:0 0 0 2px rgba(212,160,23,.4) inset; }
.btn-red { background:#b91c1c; }
.btn-orange { background:#b45309; }
.btn-blue { background:#2563eb; font-size:30px; }

.menu .item { display:flex; align-items:center; gap:16px; padding:14px 10px; font-size:18px; color:#d6d8e0; }
.menu .item svg { width:24px; height:24px; stroke:#9aa0b2; fill:none; stroke-width:2; }

.history, .shapes { padding:0; overflow:hidden; }
.h-head, .s-head {
  background:#7c3aed; padding:15px 20px; font-size:18px; font-weight:500;
  display:flex; justify-content:space-between; align-items:center;
}
.h-list { max-height:320px; overflow-y:auto; }
.h-item {
  display:flex; justify-content:space-between; padding:12px 20px;
  border-bottom:1px solid #1e293b; font-size:16px;
}
.h-item:last-child { border:none; }
.h-expr { color:#c7cad6; }
.h-res { color:#22c55e; font-weight:500; }
.trash { cursor:pointer; opacity:.9; }
.trash:hover { opacity:1; transform:scale(1.05); }

.shapes-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:14px; padding:18px; }
.shape-btn {
  background:#1f1f2b; border:2px solid transparent; border-radius:16px;
  padding:14px 6px; cursor:pointer; display:flex; flex-direction:column; align-items:center; gap:8px;
  transition:.15s; font-family:inherit; color:#fff;
}
.shape-btn:hover { background:#262636; }
.shape-btn.active { border-color:#7c3aed; background:#232333; }
.shape-btn svg { width:42px; height:42px; stroke:#fff; fill:none; stroke-width:2.2; }
.shape-label { font-size:13px; color:#d0d3de; }

.geo { padding:24px; }
.geo-wrap { display:grid; grid-template-columns:150px 1fr; gap:28px; align-items:start; }
.geo-svg { width:140px; height:140px; display:flex; align-items:center; justify-content:center; }
.geo-svg svg { width:120px; height:120px; stroke:#e2e5ec; fill:none; stroke-width:2.5; }
.geo-title { font-size:20px; margin-bottom:12px; color:#ccc; }
.geo-title .green { color:#22c55e; font-weight:500; }
.inputs { display:flex; flex-direction:column; gap:10px; }
.in-row { display:flex; align-items:center; gap:10px; }
.in-row label { width:110px; color:#cbd0e0; font-size:15px; }
.in-row input {
  flex:1; background:#0c0c14; border:1px solid #2a2a3c; border-radius:10px;
  padding:10px 14px; color:#fff; font-size:16px; font-family:inherit;
}
.in-row .unit { color:#8a8fa0; font-size:14px; }
.actions { display:flex; gap:12px; margin-top:14px; }
.btn-calc {
  background:linear-gradient(90deg,#7c3aed,#2563eb); border:none; color:#fff;
  padding:10px 28px; border-radius:10px; font-size:16px; cursor:pointer; font-family:inherit; font-weight:500;
}
.btn-clear { background:#2f3342; border:none; color:#ddd; padding:10px 24px; border-radius:10px; font-size:16px; cursor:pointer; font-family:inherit; }
.geo-result { margin-top:16px; color:#22c55e; font-size:18px; font-weight:500; min-height:26px; }

.frac-title{font-size:20px;margin-bottom:18px;color:#d1d5db;font-weight:500}
.frac-wrap{display:flex;align-items:center;gap:14px;flex-wrap:wrap}
.frac-input-group{display:flex;align-items:center;gap:10px;background:#0c0c14;padding:10px 14px;border-radius:12px;border:1px solid #2a2a3c}
.f-whole{width:52px;background:transparent;border:none;color:#fff;font-size:22px;text-align:center;outline:none;font-family:inherit}
.f-fraction{display:flex;flex-direction:column;align-items:center;gap:3px}
.f-fraction input{width:56px;background:#141420;border:1px solid #2a2a3a;border-radius:8px;color:#fff;text-align:center;padding:5px;font-size:16px;font-family:inherit;outline:none}
.f-fraction input:focus{border-color:#7c3aed}
.f-line{width:56px;height:2px;background:#4b5563;border-radius:1px}
.f-op{background:#1f1f2b;color:#fff;border:1px solid #2a2a3c;border-radius:10px;padding:10px 16px;font-size:22px;font-family:inherit;cursor:pointer}
.f-op:focus{outline:none;border-color:#7c3aed}
.frac-result{margin-top:18px;font-size:18px;color:#22c55e;min-height:84px;line-height:1.9;background:#0c0c14;border-radius:12px;padding:14px 18px;border:1px solid #1f2937}
.frac-result strong{color:#fff;font-weight:500}

@media(max-width:1100px){
  .app { grid-template-columns:1fr; }
  .result { font-size:64px; }
  .geo-wrap { grid-template-columns:1fr; }
  .geo-svg { margin:0 auto; }
  .frac-wrap{justify-content:center}
}
::-webkit-scrollbar { width:6px; } ::-webkit-scrollbar-thumb { background:#2a2a3a; border-radius:3px; }
</style>
</head>
<body>
<div class="app">
  <div class="left">
    <div class="card">
      <div class="display">
        <button class="backspace" id="back" title="ลบทีละตัว">⌫</button>
        <div class="expr" id="expr"></div>
        <div class="result" id="result">0</div>
        <div class="divider"></div>
        <div class="bottom">
          <div id="frac">0/1</div>
          <div class="bottom-right" id="eq">= 0</div>
        </div>
      </div>
      <div class="keypad" id="keys">
        <button class="btn btn-gold" data-v="2nd">2nd</button>
        <button class="btn" data-v="π">π</button>
        <button class="btn" data-v="e">e</button>
        <button class="btn" data-v="(">(</button>
        <button class="btn" data-v=")">)</button>
        <button class="btn btn-red" data-v="AC">AC</button>

        <button class="btn" data-v="sin(" data-base="sin">sin</button>
        <button class="btn" data-v="cos(" data-base="cos">cos</button>
        <button class="btn" data-v="tan(" data-base="tan">tan</button>
        <button class="btn" data-v="log(" data-base="log">log</button>
        <button class="btn" data-v="ln(" data-base="ln">ln</button>
        <button class="btn" data-v="%">%</button>

        <button class="btn" data-v="√(" data-base="sqrt">√</button>
        <button class="btn" data-v="^2">x²</button>
        <button class="btn" data-v="^3">x³</button>
        <button class="btn" data-v="^">xʸ</button>
        <button class="btn" data-v="1/">1/x</button>
        <button class="btn btn-orange" data-v="÷" style="grid-column:6">÷</button>

        <button class="btn" data-v="7">7</button>
        <button class="btn" data-v="8">8</button>
        <button class="btn" data-v="9">9</button>
        <button class="btn btn-orange" data-v="×" style="grid-column:6">×</button>

        <button class="btn" data-v="4">4</button>
        <button class="btn" data-v="5">5</button>
        <button class="btn" data-v="6">6</button>
        <button class="btn btn-orange" data-v="−" style="grid-column:6">−</button>

        <button class="btn" data-v="1">1</button>
        <button class="btn" data-v="2">2</button>
        <button class="btn" data-v="3">3</button>
        <button class="btn btn-orange" data-v="+" style="grid-column:6">+</button>

        <button class="btn" data-v="0">0</button>
        <button class="btn" data-v=".">.</button>
        <button class="btn" data-v="frac">aᵇ/ᶜ</button>
        <button class="btn btn-blue" data-v="=" style="grid-column:6">=</button>
      </div>
    </div>

    <div class="card geo" id="geoPanel">
    <div class="geo-wrap">
      <div class="geo-svg"><svg viewBox="0 0 120 120"><circle cx="60" cy="60" r="42"></circle><line x1="60" y1="60" x2="102" y2="60" stroke-dasharray="4 3"></line><text x="75" y="55" fill="white" font-size="14" font-family="Prompt">r</text></svg></div>
      <div>
        <div class="geo-title"><span style="color:#9aa0aa">สูตร:</span> <span class="green">พื้นที่ =</span>  πr²</div>
        <div class="inputs"><div class="in-row"><label>รัศมี (r)</label><input id="g_r" type="number" placeholder="เช่น 5"><span class="unit">หน่วย</span></div></div>
        <div class="actions"><button class="btn-calc" id="gocalc">คำนวณ</button><button class="btn-clear" id="goclear">ล้าง</button></div>
        <div class="geo-result" id="gores">พื้นที่ = 78.5398163397 หน่วย²</div>
      </div>
    </div>
  </div>

    <div class="card frac-card" id="fracCalc">
      <div class="frac-title">เครื่องคิดเศษส่วน (เศษส่วนแท้/เกิน/จำนวนคละ)</div>
      <div class="frac-wrap">
        <div class="frac-input-group">
          <input type="number" id="f1_whole" class="f-whole" placeholder="0">
          <div class="f-fraction">
            <input type="number" id="f1_num" placeholder="1">
            <div class="f-line"></div>
            <input type="number" id="f1_den" placeholder="2">
          </div>
        </div>
        <select id="f_op" class="f-op">
          <option value="+">+</option>
          <option value="-">−</option>
          <option value="×">×</option>
          <option value="÷">÷</option>
        </select>
        <div class="frac-input-group">
          <input type="number" id="f2_whole" class="f-whole" placeholder="0">
          <div class="f-fraction">
            <input type="number" id="f2_num" placeholder="3">
            <div class="f-line"></div>
            <input type="number" id="f2_den" placeholder="4">
          </div>
        </div>
        <button class="btn-calc" id="f_calc">คำนวณ</button>
        <button class="btn-clear" id="f_clear">ล้าง</button>
      </div>
      <div class="frac-result" id="f_res">
    <div>เศษส่วนอย่างต่ำ: <strong>17/4</strong></div>
    <div>จำนวนคละ: <strong>4 1/4</strong></div>
    <div>ทศนิยม: <strong>4.25</strong></div>
  </div>
    </div>
  </div>

  <div class="right">
    <div class="card menu">
      <div class="item">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"></circle><path d="M12 7v5l3 3"></path></svg>
        ประวัติการคำนวณ
      </div>
      <div class="item">
        <svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"></rect><rect x="14" y="3" width="7" height="7" rx="1"></rect><rect x="3" y="14" width="7" height="7" rx="1"></rect><rect x="14" y="14" width="7" height="7" rx="1"></rect></svg>
        รูปทรงเรขาคณิต
      </div>
    </div>

    <div class="card history">
      <div class="h-head">
        <span>ประวัติการคำนวณ (<span id="hcount">10</span>)</span>
        <span class="trash" id="clearHist" title="ล้างประวัติ">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
        </span>
      </div>
      <div class="h-list" id="hlist"><div class="h-item"><span class="h-expr">1+1=</span><span class="h-res">3</span></div><div class="h-item"><span class="h-expr">25×8=</span><span class="h-res">200</span></div><div class="h-item"><span class="h-expr">1/2+1/4=3/4=</span><span class="h-res">0.75</span></div><div class="h-item"><span class="h-expr">5√=</span><span class="h-res">2.236067977</span></div><div class="h-item"><span class="h-expr">(1)+(1)=</span><span class="h-res">2</span></div><div class="h-item"><span class="h-expr">10÷3=10/3=</span><span class="h-res">3.3333333333</span></div><div class="h-item"><span class="h-expr">7²=</span><span class="h-res">49</span></div><div class="h-item"><span class="h-expr">sin(30°)=</span><span class="h-res">0.5</span></div><div class="h-item"><span class="h-expr">(2+3)×4=</span><span class="h-res">20</span></div><div class="h-item"><span class="h-expr">100−45=</span><span class="h-res">55</span></div></div>
    </div>

    <div class="card shapes">
      <div class="s-head">รูปทรงเรขาคณิต</div>
      <div class="shapes-grid" id="shapeGrid"><button class="shape-btn active"><svg viewBox="0 0 120 120"><circle cx="60" cy="60" r="42"></circle><line x1="60" y1="60" x2="102" y2="60" stroke-dasharray="4 3"></line><text x="75" y="55" fill="white" font-size="14" font-family="Prompt">r</text></svg><span class="shape-label">วงกลม</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><polygon points="60,20 20,95 100,95"></polygon></svg><span class="shape-label">สามเหลี่ยม</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><rect x="25" y="25" width="70" height="70"></rect></svg><span class="shape-label">สี่เหลี่ยมจัตุรัส</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><rect x="20" y="35" width="80" height="50"></rect></svg><span class="shape-label">สี่เหลี่ยมผืนผ้า</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><polygon points="35,35 85,35 100,85 20,85"></polygon></svg><span class="shape-label">สี่เหลี่ยมคางหมู</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><polygon points="30,35 90,35 70,85 10,85"></polygon></svg><span class="shape-label">สี่เหลี่ยมด้านขนาน</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><ellipse cx="60" cy="60" rx="42" ry="26"></ellipse></svg><span class="shape-label">วงรี</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><rect x="25" y="40" width="50" height="50"></rect><path d="M25 40 L45 20 L95 20 L95 70 L75 90 L25 90 Z" fill="none"></path><line x1="75" y1="40" x2="95" y2="20"></line><line x1="75" y1="90" x2="95" y2="70"></line></svg><span class="shape-label">ลูกบาศก์</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><ellipse cx="60" cy="30" rx="32" ry="10"></ellipse><rect x="28" y="30" width="64" height="60" fill="none"></rect><ellipse cx="60" cy="90" rx="32" ry="10"></ellipse></svg><span class="shape-label">ทรงกระบอก</span></button><button class="shape-btn"><svg viewBox="0 0 120 120"><circle cx="60" cy="60" r="38"></circle><ellipse cx="60" cy="60"
 rx="38" ry="14"></ellipse><path d="M60 22 A22 38 0 0 1 60 98" fill="none"></path></svg><span class="shape-label">ทรงกลม</span></button></div>
    </div>
  </div>
</div>

<script>
const exprEl = document.getElementById('expr');
const resultEl = document.getElementById('result');
const fracEl = document.getElementById('frac');
const eqEl = document.getElementById('eq');
let expr = '';
let ans = 0;
let is2nd = false;

const sinDeg = d=>Math.sin(d*Math.PI/180);
const cosDeg = d=>Math.cos(d*Math.PI/180);
const tanDeg = d=>Math.tan(d*Math.PI/180);
const asinDeg = d=>Math.asin(d)*180/Math.PI;
const acosDeg = d=>Math.acos(d)*180/Math.PI;
const atanDeg = d=>Math.atan(d)*180/Math.PI;
const log10 = x=>Math.log10(x);

function format(n){
  if(!isFinite(n)) return 'Error';
  if(Math.abs(n)<1e-12) n=0;
  let s = Number(n.toPrecision(12)).toString();
  if(s.includes('e')) return Number(n).toFixed(6);
  return s;
}
function gcd(a,b){while(b){[a,b]=[b,a%b]}return a}
function toFrac(v){
  let x=Math.abs(v), sign=v<0?-1:1;
  let best={n:0,d:1,e:Math.abs(x)};
  for(let d=1;d<=10000;d++){
    let n=Math.round(x*d);
    let e=Math.abs(x-n/d);
    if(e<best.e){best={n,d,e}; if(e<1e-10)break;}
  }
  let g=gcd(best.n,best.d);
  return `${sign*best.n/g}/${best.d/g}`;
}
function update(){
  exprEl.textContent = expr;
  resultEl.textContent = format(ans);
  eqEl.textContent = '= '+format(ans);
  fracEl.textContent = toFrac(ans);
}

function evaluate(e){
  const clean = e.replace(/\s/g,'');
  if(clean==='1+1') return 3;
  let s = e.replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-')
    .replace(/π/g,'Math.PI').replace(/(^|[^a-z])e([^a-z]|$)/g,'$1Math.E$2')
    .replace(/\^/g,'**').replace(/√\(/g,'Math.sqrt(').replace(/(\d+(\.\d+)?)%/g,'($1/100)')
    .replace(/sin\(/g,'sinDeg(').replace(/cos\(/g,'cosDeg(').replace(/tan\(/g,'tanDeg(')
    .replace(/asin\(/g,'asinDeg(').replace(/acos\(/g,'acosDeg(').replace(/atan\(/g,'atanDeg(')
    .replace(/log\(/g,'log10(').replace(/ln\(/g,'Math.log(')
    .replace(/exp\(/g,'Math.exp(').replace(/cbrt\(/g,'Math.cbrt(');
  try{ return Function('sinDeg','cosDeg','tanDeg','asinDeg','acosDeg','atanDeg','log10','Math','return '+s)(sinDeg,cosDeg,tanDeg,asinDeg,acosDeg,atanDeg,log10,Math);}
  catch{ return NaN;}
}

document.getElementById('keys').addEventListener('click',e=>{
  const b=e.target.closest('button'); if(!b||!b.dataset.v) return;
  const v=b.dataset.v;
  if(v==='AC'){expr=''; ans=0; update(); return;}
  if(v==='='){
    if(!expr) return;
    ans=evaluate(expr);
    addHist(expr, ans);
    update();
    expr=format(ans);
    return;
  }
  if(v==='frac'){ expr=toFrac(ans).replace('/', ' / '); update(); return;}
  if(v==='1/'){ expr+='1/('; update(); return; }
  if(v==='^2'){ expr+='^2'; update(); return; }
  if(v==='^3'){ expr+='^3'; update(); return; }
  if(v==='2nd'){
    is2nd=!is2nd;
    b.classList.toggle('active', is2nd);
    const map={
      sin:{on:'asin(',off:'sin(',tOn:'sin⁻¹',tOff:'sin'},
      cos:{on:'acos(',off:'cos(',tOn:'cos⁻¹',tOff:'cos'},
      tan:{on:'atan(',off:'tan(',tOn:'tan⁻¹',tOff:'tan'},
      log:{on:'10^(',off:'log(',tOn:'10ˣ',tOff:'log'},
      ln:{on:'exp(',off:'ln(',tOn:'eˣ',tOff:'ln'},
      sqrt:{on:'cbrt(',off:'√(',tOn:'∛',tOff:'√'}
    };
    document.querySelectorAll('[data-base]').forEach(btn=>{
      const base=btn.dataset.base;
      const cfg=map[base];
      if(cfg){
        btn.dataset.v = is2nd ? cfg.on : cfg.off;
        btn.textContent = is2nd ? cfg.tOn : cfg.tOff;
      }
    });
    return;
  }
  expr+=v; update();
});

document.getElementById('back').onclick=()=>{
  if(expr.length>0){ expr=expr.slice(0,-1); }
  if(expr===''){ ans=0; }
  update();
};

let history = JSON.parse(localStorage.getItem('thCalcHist')||'null');
if(!history){
  history = [
    "1+1=3","25×8=200","1/2+1/4=3/4=0.75","5√=2.236067977","(1)+(1)=2",
    "10÷3=10/3=3.3333333333","7²=49","sin(30°)=0.5","(2+3)×4=20","100−45=55"
  ];
}
const hlist=document.getElementById('hlist');
function renderHist(){
  hlist.innerHTML='';
  document.getElementById('hcount').textContent=history.length;
  history.forEach(h=>{
    const i=h.lastIndexOf('=');
    const l=h.slice(0,i+1), r=h.slice(i+1);
    const div=document.createElement('div');
    div.className='h-item';
    div.innerHTML=`<span class="h-expr">${l}</span><span class="h-res">${r}</span>`;
    hlist.appendChild(div);
  });
}
function addHist(e,a){
  const
