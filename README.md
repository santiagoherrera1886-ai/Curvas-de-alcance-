<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Honda · Curvas de Alcance 2026</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --red:#CC0000;--red2:#990000;--red3:#FF2D2D;
  --bg:#0A0A0A;--bg2:#111;--bg3:#1A1A1A;--bg4:#222;
  --border:rgba(255,255,255,0.08);--border2:rgba(255,255,255,0.14);
  --text:#fff;--text2:rgba(255,255,255,0.65);--text3:rgba(255,255,255,0.35);
  --card:rgba(255,255,255,0.04);
}
html,body{height:100%;background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;overflow:hidden}
#app{display:flex;flex-direction:column;height:100vh;overflow:hidden}

/* HEADER */
.header{
  display:flex;align-items:center;justify-content:space-between;
  padding:14px 28px;border-bottom:1px solid var(--border);
  background:rgba(10,10,10,0.95);backdrop-filter:blur(20px);
  flex-shrink:0;gap:16px;
}
.header-brand{display:flex;align-items:center;gap:12px}
.header-logo{
  width:40px;height:40px;border-radius:10px;
  background:linear-gradient(135deg,var(--red),var(--red2));
  display:flex;align-items:center;justify-content:center;
  font-size:18px;box-shadow:0 4px 16px rgba(204,0,0,0.4);
  flex-shrink:0;
}
.header-title{font-size:17px;font-weight:800;letter-spacing:-0.03em}
.header-sub{font-size:11px;color:var(--text3);margin-top:1px;font-family:'DM Mono',monospace}
.model-tabs{display:flex;gap:4px;background:var(--card);border:1px solid var(--border);border-radius:12px;padding:3px}
.model-tab{
  padding:7px 16px;border-radius:9px;font-size:12px;font-weight:700;
  cursor:pointer;border:none;background:transparent;color:var(--text3);
  transition:all 0.2s;letter-spacing:0.01em;white-space:nowrap;
}
.model-tab.active{background:var(--red);color:#fff;box-shadow:0 2px 12px rgba(204,0,0,0.4)}

/* MAIN LAYOUT */
.main{display:flex;flex:1;overflow:hidden}
.sidebar{
  width:300px;flex-shrink:0;border-right:1px solid var(--border);
  display:flex;flex-direction:column;overflow:hidden;
}
.content{flex:1;overflow-y:auto;overflow-x:hidden}
.content::-webkit-scrollbar{width:4px}
.content::-webkit-scrollbar-thumb{background:rgba(255,255,255,0.1);border-radius:4px}

/* SIDEBAR */
.sidebar-section{padding:18px 20px;border-bottom:1px solid var(--border)}
.section-label{font-size:10px;font-weight:700;color:var(--text3);text-transform:uppercase;letter-spacing:0.1em;margin-bottom:12px;font-family:'DM Mono',monospace}
.seg-grid{display:flex;flex-direction:column;gap:5px}
.seg-btn{
  display:flex;justify-content:space-between;align-items:center;
  padding:8px 12px;border-radius:9px;border:1px solid var(--border);
  background:transparent;color:var(--text2);font-size:12px;font-weight:600;
  cursor:pointer;transition:all 0.15s;text-align:left;
}
.seg-btn:hover{background:var(--card);border-color:var(--border2)}
.seg-btn.active{background:rgba(204,0,0,0.12);border-color:rgba(204,0,0,0.35);color:#fff}
.seg-btn .seg-univ{font-size:10px;color:var(--text3);font-family:'DM Mono',monospace}
.seg-btn.active .seg-univ{color:rgba(204,0,0,0.7)}

/* SLIDERS */
.slider-block{margin-bottom:16px}
.slider-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:9px}
.slider-label{font-size:13px;font-weight:600;color:var(--text2)}
.slider-val{font-size:16px;font-weight:800;font-family:'DM Mono',monospace;color:var(--red3)}
.slider-track{position:relative;height:28px;display:flex;align-items:center}
.slider-bg{position:absolute;left:0;right:0;height:4px;background:rgba(255,255,255,0.1);border-radius:2px;overflow:hidden}
.slider-fill{height:100%;background:var(--red);border-radius:2px;transition:width 0.05s}
.slider-input{position:absolute;left:0;right:0;width:100%;opacity:0;height:28px;cursor:pointer;margin:0}
.slider-thumb{position:absolute;width:20px;height:20px;border-radius:50%;background:#fff;border:2.5px solid var(--red);box-shadow:0 2px 8px rgba(0,0,0,0.4);pointer-events:none;transition:left 0.05s}
.slider-minmax{display:flex;justify-content:space-between;margin-top:3px}
.slider-minmax span{font-size:10px;color:var(--text3);font-family:'DM Mono',monospace}

/* RESULT BOX */
.result-box{
  background:linear-gradient(135deg,rgba(204,0,0,0.15),rgba(153,0,0,0.08));
  border:1px solid rgba(204,0,0,0.25);border-radius:14px;
  padding:16px;text-align:center;margin-top:4px;
}
.result-label{font-size:11px;color:rgba(204,0,0,0.7);font-weight:700;text-transform:uppercase;letter-spacing:0.08em;margin-bottom:4px;font-family:'DM Mono',monospace}
.result-number{font-size:30px;font-weight:800;color:var(--red3);letter-spacing:-0.03em;line-height:1.1}
.result-sub{font-size:11px;color:var(--text3);margin-top:5px}
.result-pct{font-size:13px;font-weight:700;color:var(--red);margin-top:3px}

/* CONTENT PANELS */
.panels{padding:20px;display:flex;flex-direction:column;gap:16px}
.panel{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:18px}
.panel-title{font-size:10px;font-weight:700;color:var(--text3);text-transform:uppercase;letter-spacing:0.1em;margin-bottom:14px;font-family:'DM Mono',monospace}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.grid4{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
.metric{background:rgba(255,255,255,0.03);border:1px solid var(--border);border-radius:12px;padding:12px 14px}
.metric-label{font-size:10px;color:var(--text3);text-transform:uppercase;letter-spacing:0.08em;font-family:'DM Mono',monospace;margin-bottom:5px}
.metric-val{font-size:20px;font-weight:800;letter-spacing:-0.02em;line-height:1}
.metric-sub{font-size:11px;color:var(--text3);margin-top:4px}

/* TABLE */
.dep-table{width:100%;border-collapse:collapse;font-size:12px}
.dep-table th{text-align:left;font-size:9px;font-weight:700;color:var(--text3);text-transform:uppercase;letter-spacing:0.08em;padding:6px 10px;border-bottom:1px solid var(--border);font-family:'DM Mono',monospace}
.dep-table th.r{text-align:right}
.dep-table td{padding:8px 10px;border-bottom:1px solid rgba(255,255,255,0.04);color:var(--text2);transition:background 0.1s}
.dep-table td.r{text-align:right;font-family:'DM Mono',monospace;font-size:11px}
.dep-table tr:hover td{background:rgba(255,255,255,0.02)}
.dep-table .dep-name{font-weight:600;color:#fff;display:flex;align-items:center;gap:7px}
.bar-cell{display:flex;align-items:center}
.bar{height:5px;border-radius:3px;background:var(--red);opacity:0.6;min-width:2px;transition:width 0.3s}

/* CANVAS */
canvas{display:block;width:100%!important}

/* FOOTER NOTE */
.footnote{font-size:10px;color:var(--text3);margin-top:10px;font-family:'DM Mono',monospace;line-height:1.5}

@keyframes fadeUp{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
.fade-up{animation:fadeUp 0.3s ease both}

/* scrollbar content */
.content::-webkit-scrollbar-track{background:transparent}
</style>
</head>
<body>
<div id="app">
  <div class="header">
    <div class="header-brand">
      <div class="header-logo">🏍</div>
      <div>
        <div class="header-title">Honda · Curvas de Alcance</div>
        <div class="header-sub">CAMPAÑA 2026 · META ADS · DATA REAL DEL FLOW</div>
      </div>
    </div>
    <div class="model-tabs" id="modelTabs"></div>
  </div>
  <div class="main">
    <div class="sidebar">
      <div class="sidebar-section">
        <div class="section-label">Segmento Meta</div>
        <div class="seg-grid" id="segGrid"></div>
      </div>
      <div class="sidebar-section">
        <div class="section-label">Simulador</div>
        <div class="slider-block">
          <div class="slider-header">
            <span class="slider-label">Inversión</span>
            <span class="slider-val" id="invVal">$100M</span>
          </div>
          <div class="slider-track">
            <div class="slider-bg"><div class="slider-fill" id="invFill" style="width:16%"></div></div>
            <input type="range" class="slider-input" id="invSlider" min="5" max="650" step="5" value="100">
            <div class="slider-thumb" id="invThumb" style="left:calc(16% - 10px)"></div>
          </div>
          <div class="slider-minmax"><span>$5M</span><span>$650M</span></div>
        </div>
        <div class="slider-block">
          <div class="slider-header">
            <span class="slider-label">Frecuencia</span>
            <span class="slider-val" id="freqVal" style="color:#FF9500">5.0×</span>
          </div>
          <div class="slider-track">
            <div class="slider-bg"><div class="slider-fill" id="freqFill" style="background:#FF9500;width:21%"></div></div>
            <input type="range" class="slider-input" id="freqSlider" min="1" max="20" step="0.5" value="5">
            <div class="slider-thumb" id="freqThumb" style="left:calc(21% - 10px);border-color:#FF9500"></div>
          </div>
          <div class="slider-minmax"><span>1×</span><span>20×</span></div>
        </div>
        <div class="result-box" id="resultBox">
          <div class="result-label">Alcance Estimado</div>
          <div class="result-number" id="resultNum">—</div>
          <div class="result-pct" id="resultPct">—% del universo</div>
          <div class="result-sub" id="resultSub">selecciona un segmento</div>
        </div>
      </div>
      <div class="sidebar-section" style="flex:1;overflow-y:auto">
        <div class="section-label">CPM por formato</div>
        <canvas id="cpmCanvas" height="220"></canvas>
      </div>
    </div>
    <div class="content">
      <div class="panels">
        <!-- metric cards -->
        <div class="grid4" id="metricCards"></div>
        <!-- curve + deps -->
        <div class="grid2">
          <div class="panel">
            <div class="panel-title" id="curveTitle">Curva de Alcance</div>
            <canvas id="reachCanvas" height="200"></canvas>
            <div class="footnote" id="curveLegend"></div>
          </div>
          <div class="panel">
            <div class="panel-title" id="depBarTitle">Top Departamentos</div>
            <canvas id="depCanvas" height="200"></canvas>
            <div class="footnote" id="depLegend"></div>
          </div>
        </div>
        <!-- dep table -->
        <div class="panel">
          <div class="panel-title">Detalle por departamento</div>
          <table class="dep-table">
            <thead>
              <tr>
                <th>Departamento</th>
                <th class="r">Universo seg.</th>
                <th class="r">Alcance est.</th>
                <th class="r">% Alcance</th>
                <th class="r">Inv. ref.</th>
                <th></th>
              </tr>
            </thead>
            <tbody id="depTableBody"></tbody>
          </table>
          <div class="footnote">* Universo seg. = universo total × share ventas departamento. Alcance calculado con modelo logarítmico de saturación (Meta Reach & Frequency).</div>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
// ─── DATA ────────────────────────────────────────────────────────────────────
const MODELS = {
  CB100F:{
    label:'CB100F',color:'#CC0000',
    universos:{Nacional:9500000,Regiones:6350000,Domiciliarios:2600000,Independientes:7950000,Mototaxistas:464800,Younger:3952335},
    cpm:{'FB Video Ad':1266,'TikTok Top Feed':1381,'TikTok In Feed':600,'YouTube Instream':1375,'Konekti':30500,'Rappi In App':30400,'Yango Display':130000,'LeadGenios':25000},
    refPct:0.85,refFreq:5.17,segDefault:'Regiones',
    deps:{'Valle del Cauca':0.1198,'Antioquia':0.1159,'Bolívar':0.0857,'Santander':0.0798,'Cundinamarca':0.0798,'Córdoba':0.0682,'Atlántico':0.0545,'Nariño':0.0516,'Putumayo':0.0370,'Huila':0.0351,'Tolima':0.0341,'Cauca':0.0331,'Cesar':0.0302,'Nte. Santander':0.0282,'Sucre':0.0273,'Magdalena':0.0263,'Caquetá':0.0234,'Meta':0.0136,'Caldas':0.0097,'Risaralda':0.0078}
  },
  CB125F:{
    label:'CB125F',color:'#E30000',
    universos:{'Nac. excl.':8350000,Regiones:7800000},
    cpm:{'FB Video Dep.':1369,'FB Video Nac.':786,'TikTok Top Feed':1381,'TikTok In Feed':600,'YouTube Instream':1375,'Konekti':30500,'Rappi In App':30400},
    refPct:0.83,refFreq:10.41,segDefault:'Regiones',
    deps:{'Valle del Cauca':0.1444,'Antioquia':0.1028,'Cundinamarca':0.0992,'Santander':0.0627,'Tolima':0.0545,'Nte. Santander':0.0545,'Cauca':0.0488,'Huila':0.0473,'Nariño':0.0462,'Bolívar':0.0416,'Córdoba':0.0401,'Atlántico':0.0360,'Putumayo':0.0288,'Caquetá':0.0267,'Meta':0.0221,'Risaralda':0.0211,'Cesar':0.0185,'Sucre':0.0185,'Magdalena':0.0175,'Casanare':0.0170}
  },
  XR150L:{
    label:'XR150L',color:'#B00000',
    universos:{'Nac. excl.':4000000,Regiones:4000000},
    cpm:{'FB Video Dep.':1190,'FB Video Nac.':854,'TikTok Top Feed':1381,'TikTok In Feed':600,'YouTube Instream':1375,'LeadGenios':25000,'Seedtag':22880},
    refPct:0.74,refFreq:5.02,segDefault:'Regiones',
    deps:{'Antioquia':0.1671,'Valle del Cauca':0.0840,'Huila':0.0689,'Cundinamarca':0.0673,'Cauca':0.0586,'Santander':0.0527,'Caquetá':0.0463,'Córdoba':0.0428,'Magdalena':0.0388,'Atlántico':0.0368,'Bolívar':0.0333,'Nariño':0.0345,'Sucre':0.0309,'Putumayo':0.0293,'Tolima':0.0289,'Arauca':0.0250,'Cesar':0.0242,'Meta':0.0198,'Caldas':0.0186,'Casanare':0.0178}
  },
  XR190L:{
    label:'XR190L',color:'#990000',
    universos:{'Nac. excl.':7500000,Regiones:7600000},
    cpm:{'FB Video Dep.':1061,'FB Video Nac.':791,'TikTok Top Feed':1381,'TikTok In Feed':600,'YouTube Instream':1375,'Konekti':30500,'Adslive Podcast':432},
    refPct:0.81,refFreq:4.90,segDefault:'Regiones',
    deps:{'Antioquia':0.1815,'Valle del Cauca':0.0962,'Cundinamarca':0.0914,'Santander':0.0532,'Cauca':0.0461,'Córdoba':0.0447,'Nariño':0.0447,'Huila':0.0409,'Atlántico':0.0334,'Magdalena':0.0324,'Sucre':0.0317,'Bolívar':0.0307,'Tolima':0.0297,'Caquetá':0.0266,'Nte. Santander':0.0249,'Caldas':0.0246,'Cesar':0.0246,'Putumayo':0.0239,'Meta':0.0218,'Casanare':0.0212}
  },
  PCX160:{
    label:'PCX160',color:'#FF2D2D',
    universos:{Nacional:8350000,Medellín:1200000,Cali:900000,Bucaramanga:650000,Bogotá:2500000,'Resto país':3100000},
    cpm:{'FB Video Ad':1000,'TikTok Top View':4000,'TikTok Top Feed':2000,'TikTok In Feed':1500,'YouTube Instream':1900,'Nequi Video':15000,'Yango In App':18000,'Konekti':30500},
    refPct:0.64,refFreq:7.16,segDefault:'Nacional',
    deps:{'Antioquia':0.22,'Bogotá D.C.':0.20,'Valle del Cauca':0.10,'Cundinamarca':0.09,'Santander':0.07,'Atlántico':0.05,'Bolívar':0.04,'Risaralda':0.03,'Nariño':0.03,'Caldas':0.03,'Tolima':0.025,'Córdoba':0.02,'Huila':0.02,'Meta':0.015,'Cesar':0.015,'Magdalena':0.015}
  }
};

// ─── STATE ───────────────────────────────────────────────────────────────────
let curModel = 'CB100F';
let curSeg   = 'Regiones';
let inv      = 100;  // millones
let freq     = 5.0;

// ─── UTILS ───────────────────────────────────────────────────────────────────
const fmt  = n => new Intl.NumberFormat('es-CO').format(Math.round(n));
const fmtM = n => '$' + n + 'M';

function calcReach(invM, univ, avgCPM, fr) {
  const imps = (invM * 1e6) / avgCPM * 1000;
  const rawR = imps / fr;
  const sat  = 1 - Math.exp(-rawR / (univ * 0.9));
  return Math.min(sat * univ, univ * 0.95);
}

function getAvgCPM(m) {
  const v = Object.values(m.cpm);
  return v.reduce((a,b)=>a+b,0)/v.length;
}

// ─── BUILD MODEL TABS ────────────────────────────────────────────────────────
function buildModelTabs() {
  const container = document.getElementById('modelTabs');
  container.innerHTML = '';
  Object.keys(MODELS).forEach(k => {
    const btn = document.createElement('button');
    btn.className = 'model-tab' + (k === curModel ? ' active' : '');
    btn.textContent = MODELS[k].label;
    btn.onclick = () => { curModel = k; curSeg = MODELS[k].segDefault; buildAll(); };
    container.appendChild(btn);
  });
}

// ─── BUILD SEG GRID ──────────────────────────────────────────────────────────
function buildSegGrid() {
  const m = MODELS[curModel];
  const container = document.getElementById('segGrid');
  container.innerHTML = '';
  Object.entries(m.universos).forEach(([seg, univ]) => {
    const btn = document.createElement('button');
    btn.className = 'seg-btn' + (seg === curSeg ? ' active' : '');
    btn.innerHTML = `<span>${seg}</span><span class="seg-univ">${fmt(univ)}</span>`;
    btn.onclick = () => { curSeg = seg; buildAll(); };
    container.appendChild(btn);
  });
}

// ─── BUILD METRIC CARDS ──────────────────────────────────────────────────────
function buildMetrics() {
  const m    = MODELS[curModel];
  const segs = Object.keys(m.universos);
  const seg  = segs.includes(curSeg) ? curSeg : segs[0];
  const univ = m.universos[seg];
  const avg  = getAvgCPM(m);
  const reach = calcReach(inv, univ, avg, freq);
  const pct   = (reach/univ*100).toFixed(1);

  const cards = [
    {label:'Universo',       val:fmt(univ),                                     sub:seg,                  col:'#CC0000'},
    {label:'CPM promedio',   val:'$'+Math.round(avg).toLocaleString('es-CO'),   sub:'pesos por 1.000 imp.',col:'#CC0000'},
    {label:'Alcance estimado',val:pct+'%',                                       sub:fmt(Math.round(reach))+' personas', col: reach/univ>0.7?'#34C759':'#FF6B6B'},
    {label:'Frecuencia ref.',val:m.refFreq+'×',                                  sub:'benchmark campaña',  col:'#FF9500'},
  ];
  document.getElementById('metricCards').innerHTML = cards.map(c=>`
    <div class="metric fade-up">
      <div class="metric-label">${c.label}</div>
      <div class="metric-val" style="color:${c.col}">${c.val}</div>
      <div class="metric-sub">${c.sub}</div>
    </div>`).join('');
}

// ─── UPDATE RESULT BOX ───────────────────────────────────────────────────────
function updateResult() {
  const m    = MODELS[curModel];
  const segs = Object.keys(m.universos);
  const seg  = segs.includes(curSeg) ? curSeg : segs[0];
  const univ = m.universos[seg];
  const avg  = getAvgCPM(m);
  const reach = calcReach(inv, univ, avg, freq);
  const pct   = (reach/univ*100).toFixed(1);
  document.getElementById('resultNum').textContent  = fmt(Math.round(reach));
  document.getElementById('resultPct').textContent  = pct + '% del universo';
  document.getElementById('resultSub').textContent  = 'con $'+inv+'M COP · frec. '+freq.toFixed(1)+'× · '+seg;
}

// ─── DRAW REACH CURVE ────────────────────────────────────────────────────────
function drawReachCurve() {
  const cv  = document.getElementById('reachCanvas');
  const m   = MODELS[curModel];
  const segs= Object.keys(m.universos);
  const seg = segs.includes(curSeg) ? curSeg : segs[0];
  const univ= m.universos[seg];
  const avg = getAvgCPM(m);

  cv.width  = cv.parentElement.clientWidth - 36;
  const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  ctx.clearRect(0,0,W,H);

  // grid lines
  ctx.strokeStyle = 'rgba(255,255,255,0.06)';
  ctx.lineWidth = 1;
  for(let i=1;i<5;i++){
    ctx.beginPath(); ctx.moveTo(0,H*i/5); ctx.lineTo(W,H*i/5); ctx.stroke();
  }

  const maxInv = Math.max(inv * 2, 400);
  const PAD = 8;
  const pts = [];
  for(let i=1;i<=100;i++){
    const x = (maxInv/100)*i;
    const r = calcReach(x, univ, avg, freq);
    pts.push({ x: PAD + (i/100)*(W-PAD*2), y: H-PAD - (r/univ)*(H-PAD*2) });
  }

  // gradient fill
  const grad = ctx.createLinearGradient(0,0,0,H);
  grad.addColorStop(0,'rgba(204,0,0,0.18)');
  grad.addColorStop(1,'rgba(204,0,0,0.01)');
  ctx.beginPath(); ctx.moveTo(pts[0].x, H);
  pts.forEach(p=>ctx.lineTo(p.x,p.y));
  ctx.lineTo(W-PAD, H); ctx.closePath();
  ctx.fillStyle = grad; ctx.fill();

  // curve
  ctx.beginPath(); ctx.moveTo(pts[0].x, pts[0].y);
  for(let i=1;i<pts.length-1;i++){
    const mx = (pts[i].x+pts[i+1].x)/2, my = (pts[i].y+pts[i+1].y)/2;
    ctx.quadraticCurveTo(pts[i].x,pts[i].y,mx,my);
  }
  ctx.strokeStyle = '#CC0000'; ctx.lineWidth = 2.5; ctx.stroke();

  // current investment marker
  const cx = PAD + (inv/maxInv)*(W-PAD*2);
  const reach = calcReach(inv, univ, avg, freq);
  const cy = H - PAD - (reach/univ)*(H-PAD*2);

  ctx.setLineDash([4,4]);
  ctx.beginPath(); ctx.moveTo(cx,H); ctx.lineTo(cx,cy);
  ctx.strokeStyle='rgba(255,255,255,0.2)'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.setLineDash([]);

  // glow dot
  ctx.beginPath(); ctx.arc(cx,cy,10,0,Math.PI*2);
  ctx.fillStyle='rgba(204,0,0,0.2)'; ctx.fill();
  ctx.beginPath(); ctx.arc(cx,cy,5,0,Math.PI*2);
  ctx.fillStyle='#FF2D2D'; ctx.fill();

  // x-axis labels
  ctx.fillStyle='rgba(255,255,255,0.3)'; ctx.font='9px DM Mono, monospace'; ctx.textAlign='center';
  [0.25,0.5,0.75,1].forEach(p=>{
    const v=Math.round(maxInv*p);
    ctx.fillText('$'+v+'M', PAD+(p*(W-PAD*2)), H-1);
  });

  // y-axis labels
  ctx.textAlign='left';
  [0.25,0.5,0.75,1].forEach(p=>{
    const v=Math.round(univ*p);
    const y = H - PAD - p*(H-PAD*2);
    ctx.fillText(v>=1e6?(v/1e6).toFixed(1)+'M':Math.round(v/1000)+'K', 2, y-2);
  });

  document.getElementById('curveTitle').textContent = `Curva de alcance · ${m.label} · ${seg}`;
  document.getElementById('curveLegend').textContent = `Universo: ${fmt(univ)} · CPM promedio: $${Math.round(avg).toLocaleString('es-CO')} · Punto: $${inv}M → ${(reach/univ*100).toFixed(1)}%`;
}

// ─── DRAW CPM CHART ──────────────────────────────────────────────────────────
function drawCPM() {
  const cv  = document.getElementById('cpmCanvas');
  const m   = MODELS[curModel];
  cv.width  = cv.parentElement.clientWidth - 40;
  const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  ctx.clearRect(0,0,W,H);

  const labels = Object.keys(m.cpm);
  const vals   = Object.values(m.cpm);
  const maxV   = Math.max(...vals);
  const bH     = Math.floor((H-8)/labels.length) - 4;

  labels.forEach((lbl,i) => {
    const v = vals[i];
    const bW = Math.max(3, (v/maxV)*(W*0.45));
    const y  = 4 + i*(bH+4);
    const alpha = v < 2000 ? 0.85 : v < 10000 ? 0.5 : 0.25;
    ctx.fillStyle = `rgba(204,0,0,${alpha})`;
    if(ctx.roundRect) ctx.roundRect(0,y,bW,bH,3); else ctx.rect(0,y,bW,bH);
    ctx.fill();
    ctx.fillStyle = v < 2000 ? 'rgba(255,255,255,0.8)' : 'rgba(255,255,255,0.5)';
    ctx.font = `${Math.max(9,Math.min(11,bH*0.7))}px DM Sans, sans-serif`;
    ctx.textAlign = 'left';
    const priceStr = '$' + v.toLocaleString('es-CO');
    ctx.fillText(lbl, bW + 5, y + bH*0.73);
    ctx.fillStyle = 'rgba(255,255,255,0.35)';
    ctx.fillText(priceStr, bW + 5 + ctx.measureText(lbl).width + 5, y + bH*0.73);
  });
}

// ─── DRAW DEP BARS ───────────────────────────────────────────────────────────
function drawDepBars() {
  const cv  = document.getElementById('depCanvas');
  const m   = MODELS[curModel];
  const segs= Object.keys(m.universos);
  const seg = segs.includes(curSeg) ? curSeg : segs[0];
  const univ= m.universos[seg];
  const avg = getAvgCPM(m);
  const reach= calcReach(inv, univ, avg, freq);

  cv.width  = cv.parentElement.clientWidth - 36;
  const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  ctx.clearRect(0,0,W,H);

  const deps   = Object.entries(m.deps).sort((a,b)=>b[1]-a[1]).slice(0,12);
  const maxR   = reach * deps[0][1];
  const bH     = Math.floor((H-8)/deps.length) - 3;

  deps.forEach(([dep,share],i) => {
    const r  = reach * share;
    const bW = Math.max(3,(r/maxR)*(W*0.5));
    const y  = 4 + i*(bH+3);
    const alpha = i<3 ? 0.8 : 0.4;
    ctx.fillStyle = `rgba(204,0,0,${alpha})`;
    if(ctx.roundRect) ctx.roundRect(0,y,bW,bH,3); else ctx.rect(0,y,bW,bH);
    ctx.fill();
    ctx.fillStyle = i<3?'rgba(255,255,255,0.85)':'rgba(255,255,255,0.5)';
    ctx.font = `${Math.max(9,Math.min(11,bH*0.7))}px DM Sans, sans-serif`;
    ctx.textAlign = 'left';
    const rStr = fmt(Math.round(r));
    ctx.fillText(dep, bW+5, y+bH*0.73);
    ctx.fillStyle='rgba(255,255,255,0.3)';
    ctx.fillText(rStr, bW+5+ctx.measureText(dep).width+5, y+bH*0.73);
  });

  document.getElementById('depBarTitle').textContent = `Top departamentos · $${inv}M · ${seg}`;
  document.getElementById('depLegend').textContent   = `Alcance total estimado: ${fmt(Math.round(reach))} personas. Distribución según ventas reales por dpto.`;
}

// ─── BUILD DEP TABLE ─────────────────────────────────────────────────────────
function buildDepTable() {
  const m    = MODELS[curModel];
  const segs = Object.keys(m.universos);
  const seg  = segs.includes(curSeg) ? curSeg : segs[0];
  const univ = m.universos[seg];
  const avg  = getAvgCPM(m);
  const reach= calcReach(inv, univ, avg, freq);

  const sorted = Object.entries(m.deps).sort((a,b)=>b[1]-a[1]).slice(0,15);
  const maxShare = sorted[0][1];

  document.getElementById('depTableBody').innerHTML = sorted.map(([dep,share],i)=>{
    const dU   = Math.round(univ * share);
    const dR   = Math.round(reach * share);
    const dPct = (dR/dU*100).toFixed(0);
    const dInv = Math.round(inv * share);
    const barW = Math.round((share/maxShare)*90);
    const medal = i===0?'🥇':i===1?'🥈':i===2?'🥉':'';
    return `<tr>
      <td><div class="dep-name">${medal?`<span style="font-size:13px">${medal}</span>`:''}<span>${dep}</span></div></td>
      <td class="r">${fmt(dU)}</td>
      <td class="r" style="color:#FF6B6B;font-weight:700">${fmt(dR)}</td>
      <td class="r" style="color:rgba(255,255,255,0.55)">${dPct}%</td>
      <td class="r" style="color:rgba(255,255,255,0.4)">~$${dInv}M</td>
      <td style="padding:8px 10px 8px 4px;min-width:100px">
        <div class="bar-cell"><div class="bar" style="width:${barW}px"></div></div>
      </td>
    </tr>`;
  }).join('');
}

// ─── SLIDERS ─────────────────────────────────────────────────────────────────
function updateSliderUI(id, val, min, max, fillColor) {
  const pct = (val-min)/(max-min)*100;
  document.getElementById(id+'Fill').style.width  = pct+'%';
  document.getElementById(id+'Fill').style.background = fillColor||'#CC0000';
  document.getElementById(id+'Thumb').style.left  = `calc(${pct}% - 10px)`;
  document.getElementById(id+'Thumb').style.borderColor = fillColor||'#CC0000';
}

document.getElementById('invSlider').addEventListener('input', function(){
  inv = parseInt(this.value);
  document.getElementById('invVal').textContent = '$'+inv+'M';
  updateSliderUI('inv', inv, 5, 650, '#CC0000');
  updateResult(); drawReachCurve(); drawDepBars(); buildDepTable(); buildMetrics();
});
document.getElementById('freqSlider').addEventListener('input', function(){
  freq = parseFloat(this.value);
  document.getElementById('freqVal').textContent = freq.toFixed(1)+'×';
  updateSliderUI('freq', freq, 1, 20, '#FF9500');
  updateResult(); drawReachCurve(); drawDepBars(); buildDepTable(); buildMetrics();
});

// ─── MAIN BUILD ──────────────────────────────────────────────────────────────
function buildAll() {
  buildModelTabs();
  buildSegGrid();
  buildMetrics();
  updateResult();
  drawReachCurve();
  drawCPM();
  drawDepBars();
  buildDepTable();
  // reset sliders to ref freq
  const m = MODELS[curModel];
  freq = m.refFreq;
  document.getElementById('freqSlider').value = freq;
  document.getElementById('freqVal').textContent = freq.toFixed(1)+'×';
  updateSliderUI('freq', freq, 1, 20, '#FF9500');
  // reset inv to sensible default
  inv = Math.round(m.refPct * 200 / 5) * 5;
  if(inv < 5) inv = 50;
  document.getElementById('invSlider').value = inv;
  document.getElementById('invVal').textContent = '$'+inv+'M';
  updateSliderUI('inv', inv, 5, 650, '#CC0000');
}

// Redraw canvases on resize
window.addEventListener('resize', () => { drawReachCurve(); drawCPM(); drawDepBars(); });

// Init
buildAll();
</script>
</body>
</html>
