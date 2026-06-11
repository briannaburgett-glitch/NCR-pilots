<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NCR Pilots Dashboard</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/tabler-icons/2.44.0/iconfont/tabler-icons.min.css">
<style>
:root{--bg:#fff;--bg2:#f8f8f6;--bg3:#f1f0eb;--text:#1a1a18;--text2:#5f5e5a;--text3:#9a9890;--border:rgba(0,0,0,0.1);--border2:rgba(0,0,0,0.18);--blue-bg:#E6F1FB;--blue-text:#0C447C;--blue-mid:#378ADD;--green-bg:#E1F5EE;--green-text:#085041;--green-mid:#1D9E75;--amber-bg:#FAEEDA;--amber-text:#633806;--amber-mid:#BA7517;--red-bg:#FCEBEB;--red-text:#A32D2D;--red-border:#F7C1C1;--yellow-bg:#FAEEDA;--yellow-text:#633806;--yellow-border:#FAC775;--r:8px;--rl:12px}
@media(prefers-color-scheme:dark){:root{--bg:#1c1c1a;--bg2:#242422;--bg3:#2c2c2a;--text:#f0ede8;--text2:#b4b2a9;--text3:#666460;--border:rgba(255,255,255,0.08);--border2:rgba(255,255,255,0.15);--blue-bg:#0c2f50;--blue-text:#85B7EB;--green-bg:#053528;--green-text:#5DCAA5;--amber-bg:#3a2205;--amber-text:#EF9F27;--red-bg:#3a1010;--red-text:#F09595;--red-border:#A32D2D;--yellow-bg:#3a2205;--yellow-text:#EF9F27;--yellow-border:#854F0B}}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:var(--bg);color:var(--text);font-size:14px;line-height:1.5}
.wrap{max-width:900px;margin:0 auto;padding:1.5rem 1rem 3rem}
.dash-header{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:1.5rem;flex-wrap:wrap;gap:12px}
.dash-title{font-size:20px;font-weight:500}
.dash-sub{font-size:12px;color:var(--text2);margin-top:3px}
.total-arr{text-align:right}
.total-arr-label{font-size:11px;color:var(--text2)}
.total-arr-value{font-size:26px;font-weight:500}
.tab-bar{display:flex;gap:4px;border-bottom:.5px solid var(--border);margin-bottom:1.5rem;overflow-x:auto}
.tab-btn{padding:8px 14px;font-size:13px;font-weight:500;border:none;background:transparent;color:var(--text2);cursor:pointer;border-bottom:2px solid transparent;margin-bottom:-.5px;white-space:nowrap;transition:color .15s}
.tab-btn.active{color:var(--text);border-bottom-color:var(--text)}
.tab-btn:hover:not(.active){color:var(--text)}
.tab-pane{display:none}.tab-pane.active{display:block}

/* Overview cards */
.ov-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
@media(max-width:600px){.ov-grid{grid-template-columns:1fr}}
.ov-card{border:.5px solid var(--border);border-radius:var(--rl);padding:1rem;cursor:pointer;transition:border-color .15s}
.ov-card:hover{border-color:var(--border2)}
.ov-card-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:10px}
.ov-name{font-size:15px;font-weight:500}
.ov-arr{font-size:18px;font-weight:500;padding:4px 10px;border-radius:var(--r)}
.ov-arr.blue{background:var(--blue-bg);color:var(--blue-text)}
.ov-arr.green{background:var(--green-bg);color:var(--green-text)}
.ov-arr.amber{background:var(--amber-bg);color:var(--amber-text)}
.ov-field{font-size:12px;color:var(--text2);margin-top:5px}
.ov-field span{color:var(--text);font-weight:500}
.net-pill{display:inline-block;background:var(--bg2);border:.5px solid var(--border2);border-radius:var(--r);font-size:11px;padding:1px 7px;margin:1px 2px 0 0}

/* Editable field */
.ef{display:flex;align-items:flex-start;gap:6px;padding:6px 0;border-bottom:.5px solid var(--border)}
.ef:last-child{border-bottom:none}
.ef-label{font-size:10px;color:var(--text2);text-transform:uppercase;letter-spacing:.04em;min-width:130px;padding-top:3px;flex-shrink:0}
.ef-val{font-size:13px;color:var(--text);flex:1;cursor:text;min-height:20px;border-radius:4px;padding:1px 4px}
.ef-val:hover{background:var(--bg2)}
.ef-val[contenteditable=true]:focus{background:var(--bg2);outline:.5px solid var(--border2);outline-offset:1px}

/* Sections */
.section{margin-bottom:1.25rem}
.section-title{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.05em;color:var(--text2);margin-bottom:8px;display:flex;align-items:center;gap:6px}
.add-btn{margin-left:auto;font-size:11px;padding:2px 8px;border:.5px solid var(--border2);border-radius:var(--r);background:transparent;color:var(--text2);cursor:pointer;display:flex;align-items:center;gap:3px}
.add-btn:hover{background:var(--bg2);color:var(--text)}

/* Phases / blocks */
.phase-block{background:var(--bg2);border-radius:var(--r);padding:9px 12px;margin-bottom:6px;display:flex;align-items:flex-start;gap:8px}
.phase-block.red{background:var(--red-bg);border:.5px solid var(--red-border)}
.phase-block.yellow{background:var(--yellow-bg);border:.5px solid var(--yellow-border)}
.phase-content{flex:1}
.phase-label-el{font-size:11px;font-weight:500;color:var(--text2);margin-bottom:3px;cursor:text;min-height:16px}
.phase-label-el[contenteditable]:focus{outline:.5px solid var(--border2);border-radius:3px;padding:0 2px}
.phase-block.red .phase-label-el,.phase-block.red .phase-val-el{color:var(--red-text)}
.phase-block.yellow .phase-label-el,.phase-block.yellow .phase-val-el{color:var(--yellow-text)}
.phase-val-el{font-size:13px;cursor:text;min-height:18px}
.phase-val-el[contenteditable]:focus{outline:.5px solid var(--border2);border-radius:3px;padding:0 2px}
.del-btn{background:none;border:none;color:var(--text3);cursor:pointer;font-size:14px;padding:2px;border-radius:3px;flex-shrink:0;opacity:0;transition:opacity .15s}
.phase-block:hover .del-btn{opacity:1}

/* Checklist */
.checklist{list-style:none}
.checklist li{display:flex;align-items:flex-start;gap:8px;padding:5px 0;border-bottom:.5px solid var(--border);font-size:13px}
.checklist li:last-child{border-bottom:none}
.checklist li input[type=checkbox]{margin-top:2px;flex-shrink:0;cursor:pointer;accent-color:var(--blue-mid);width:14px;height:14px}
.checklist li label{flex:1;cursor:text}
.checklist li label[contenteditable]:focus{outline:.5px solid var(--border2);border-radius:3px;padding:0 2px}
.checklist li.done label{text-decoration:line-through;color:var(--text3)}
.checklist li .del-btn{opacity:0}
.checklist li:hover .del-btn{opacity:1}

/* Success tags */
.stags{display:flex;flex-wrap:wrap;gap:4px;margin-top:6px}
.stag{display:inline-flex;align-items:center;gap:4px;background:#EAF3DE;color:#3B6D11;font-size:11px;padding:2px 8px;border-radius:var(--r)}
@media(prefers-color-scheme:dark){.stag{background:#173404;color:#97C459}}
.stag .del-btn{opacity:0;font-size:12px;color:#3B6D11}
.stag:hover .del-btn{opacity:1}

/* Link list */
.link-list{display:flex;flex-direction:column;gap:6px}
.link-item{display:flex;align-items:flex-start;gap:8px;background:var(--bg2);border-radius:var(--r);padding:8px 10px}
.link-item-label{font-size:11px;color:var(--text2);cursor:text}
.link-item-label[contenteditable]:focus{outline:.5px solid var(--border2);border-radius:3px}
.link-item a{font-size:13px;color:var(--blue-text);cursor:text;word-break:break-all}
.link-item a[contenteditable]:focus{outline:.5px solid var(--border2);border-radius:3px}
.link-item .del-btn{opacity:0}
.link-item:hover .del-btn{opacity:1}

/* Calendar */
.cal-legend{display:flex;gap:12px;margin-bottom:1rem;flex-wrap:wrap}
.cal-legend-item{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--text2)}
.cal-legend-dot{width:12px;height:12px;border-radius:2px}
.cal-outer{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--border);border:.5px solid var(--border);border-radius:var(--r);overflow:hidden}
@media(max-width:600px){.cal-outer{grid-template-columns:repeat(2,1fr)}}
.cal-month{background:var(--bg);padding:10px}
.cal-month-title{font-size:11px;font-weight:500;color:var(--text2);margin-bottom:6px;text-transform:uppercase;letter-spacing:.05em}
.cal-week-row{display:grid;grid-template-columns:repeat(7,1fr);gap:1px;margin-bottom:1px}
.cal-dlabel{font-size:9px;color:var(--text3);text-align:center;padding:2px 0}
.cal-day{min-height:20px;border-radius:2px;font-size:9px;display:flex;align-items:center;justify-content:center;color:var(--text3)}
.cal-day.opnav{background:#B5D4F4;color:#0C447C;cursor:pointer}
.cal-day.osw{background:#9FE1CB;color:#085041;cursor:pointer}
.cal-day.dtra{background:#FAC775;color:#633806;cursor:pointer}
.cal-day.opnav-osw{background:linear-gradient(135deg,#B5D4F4 50%,#9FE1CB 50%);cursor:pointer}
.cal-day.osw-dtra{background:linear-gradient(135deg,#9FE1CB 50%,#FAC775 50%);cursor:pointer}

/* Popup */
.pop-ov{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.4);z-index:200;align-items:center;justify-content:center}
.pop-ov.open{display:flex}
.popup{background:var(--bg);border-radius:var(--rl);padding:1.25rem;max-width:360px;width:92%;border:.5px solid var(--border2);position:relative;max-height:88vh;overflow-y:auto}
.popup-close{position:absolute;top:10px;right:12px;background:none;border:none;font-size:18px;cursor:pointer;color:var(--text2)}
.popup-title{font-size:15px;font-weight:500;margin-bottom:12px;padding-right:24px}
.popup-goto{margin-top:12px}
.popup-goto button{font-size:12px;padding:5px 12px;cursor:pointer;background:var(--bg2);border:.5px solid var(--border2);border-radius:var(--r);color:var(--text)}

/* Callout */
.callout{background:var(--green-bg);border:.5px solid #9FE1CB;border-radius:var(--r);padding:8px 12px;font-size:12px;color:var(--green-text);margin-bottom:1rem;display:flex;gap:8px;align-items:flex-start}

/* Save indicator */
.save-dot{width:7px;height:7px;border-radius:50%;background:#9FE1CB;display:inline-block;margin-left:8px;opacity:0;transition:opacity .3s}
.save-dot.show{opacity:1}
</style>
</head>
<body>
<div class="wrap">
<div class="dash-header">
  <div>
    <div class="dash-title">NCR Pilot Dashboard <span class="save-dot" id="savedot"></span></div>
    <div class="dash-sub">OPNAV N9I · OSW IBP · DTRA J3/5/8 — FY26</div>
  </div>
  <div class="total-arr">
    <div class="total-arr-label">Total ARR target</div>
    <div class="total-arr-value" id="total-arr-display">$TBD</div>
  </div>
</div>

<div class="tab-bar">
  <button class="tab-btn active" onclick="switchTab('overview')"><i class="ti ti-layout-grid"></i> Overview</button>
  <button class="tab-btn" onclick="switchTab('calendar')"><i class="ti ti-calendar"></i> Calendar</button>
  <button class="tab-btn" onclick="switchTab('opnav')"><i class="ti ti-anchor"></i> OPNAV</button>
  <button class="tab-btn" onclick="switchTab('osw')"><i class="ti ti-briefcase"></i> OSW IBP</button>
  <button class="tab-btn" onclick="switchTab('dtra')"><i class="ti ti-shield"></i> DTRA</button>
</div>

<!-- OVERVIEW -->
<div id="tab-overview" class="tab-pane active">
  <div class="ov-grid">
    <div class="ov-card" onclick="switchTab('opnav')">
      <div class="ov-card-top">
        <div class="ov-name"><i class="ti ti-anchor" style="margin-right:5px"></i>OPNAV N9I</div>
        <div class="ov-arr blue" id="ov-arr-opnav">$TBD</div>
      </div>
      <div class="ov-field">Dates: <span id="ov-dates-opnav">18 May – 12 Jun 2025</span></div>
      <div class="ov-field">Networks: <span id="ov-net-opnav">IL6</span></div>
    </div>
    <div class="ov-card" onclick="switchTab('osw')">
      <div class="ov-card-top">
        <div class="ov-name"><i class="ti ti-briefcase" style="margin-right:5px"></i>OSW IBP</div>
        <div class="ov-arr green" id="ov-arr-osw">$1.2M</div>
      </div>
      <div class="ov-field">Dates: <span id="ov-dates-osw">1 Jul 2025 · 3 phases</span></div>
      <div class="ov-field">Networks: <span id="ov-net-osw">IL5 · AI Assist</span></div>
    </div>
    <div class="ov-card" onclick="switchTab('dtra')">
      <div class="ov-card-top">
        <div class="ov-name"><i class="ti ti-shield" style="margin-right:5px"></i>DTRA J3/5/8</div>
        <div class="ov-arr amber" id="ov-arr-dtra">$TBD</div>
      </div>
      <div class="ov-field">Dates: <span id="ov-dates-dtra">1 Aug – 31 Oct 2025</span></div>
      <div class="ov-field">Networks: <span id="ov-net-dtra">IL5 · IL6 · JWICS</span></div>
    </div>
  </div>
  <p style="font-size:11px;color:var(--text3);margin-top:12px">Click any card to view and edit full pilot details.</p>
</div>

<!-- CALENDAR -->
<div id="tab-calendar" class="tab-pane">
  <div class="cal-legend">
    <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#B5D4F4"></div>OPNAV</div>
    <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#9FE1CB"></div>OSW IBP</div>
    <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#FAC775"></div>DTRA J3/5/8</div>
  </div>
  <div id="cal-outer" class="cal-outer"></div>
  <p style="font-size:11px;color:var(--text3);margin-top:8px">Click any highlighted day to see pilot details.</p>
</div>

<!-- OPNAV DETAIL -->
<div id="tab-opnav" class="tab-pane">
  <div style="display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:1rem;flex-wrap:wrap;gap:8px">
    <div>
      <div style="font-size:18px;font-weight:500"><i class="ti ti-anchor" style="margin-right:6px"></i>OPNAV N9I</div>
      <div style="font-size:12px;color:var(--text2)" id="d-dates-opnav-display"></div>
    </div>
    <div class="ov-arr blue" id="d-arr-opnav-display" style="font-size:20px"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-info-circle"></i> Core info</div>
    <div class="ef"><div class="ef-label">ARR</div><div class="ef-val" contenteditable="true" data-key="opnav.arr" data-sync="ov-arr-opnav,d-arr-opnav-display"></div></div>
    <div class="ef"><div class="ef-label">Dates</div><div class="ef-val" contenteditable="true" data-key="opnav.dates" data-sync="ov-dates-opnav,d-dates-opnav-display"></div></div>
    <div class="ef"><div class="ef-label">Networks</div><div class="ef-val" contenteditable="true" data-key="opnav.networks" data-sync="ov-net-opnav"></div></div>
    <div class="ef"><div class="ef-label">Gov lead(s)</div><div class="ef-val" contenteditable="true" data-key="opnav.govlead"></div></div>
    <div class="ef"><div class="ef-label">Decision makers</div><div class="ef-val" contenteditable="true" data-key="opnav.dm"></div></div>
    <div class="ef"><div class="ef-label">Contracting / Sales</div><div class="ef-val" contenteditable="true" data-key="opnav.sales"></div></div>
    <div class="ef"><div class="ef-label">CR lead</div><div class="ef-val" contenteditable="true" data-key="opnav.crlead"></div></div>
    <div class="ef"><div class="ef-label">CR support</div><div class="ef-val" contenteditable="true" data-key="opnav.crsupport"></div></div>
    <div class="ef"><div class="ef-label">Expansion target</div><div class="ef-val" contenteditable="true" data-key="opnav.expansion"></div></div>
    <div class="ef"><div class="ef-label">Contracting notes</div><div class="ef-val" contenteditable="true" data-key="opnav.contracting"></div></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-list-check"></i> Workflows &amp; success criteria
      <button class="add-btn" onclick="addSuccess('opnav')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div class="ef"><div class="ef-label">Confirmed workflows</div><div class="ef-val" contenteditable="true" data-key="opnav.workflows"></div></div>
    <div class="stags" id="opnav-success"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist
      <button class="add-btn" onclick="addCheck('opnav')"><i class="ti ti-plus"></i> Add item</button>
    </div>
    <ul class="checklist" id="opnav-cl"></ul>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence
      <button class="add-btn" onclick="addBlock('opnav-checkins','','')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="opnav-checkins"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks
      <button class="add-btn" onclick="addBlock('opnav-risks','New risk','Describe mitigation here','red')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="opnav-risks"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-link"></i> Resources &amp; docs
      <button class="add-btn" onclick="addLink('opnav-links')"><i class="ti ti-plus"></i> Add link</button>
    </div>
    <div class="link-list" id="opnav-links"></div>
  </div>
</div>

<!-- OSW IBP DETAIL -->
<div id="tab-osw" class="tab-pane">
  <div style="display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:.75rem;flex-wrap:wrap;gap:8px">
    <div>
      <div style="font-size:18px;font-weight:500"><i class="ti ti-briefcase" style="margin-right:6px"></i>OSW IBP</div>
      <div style="font-size:12px;color:var(--text2)" id="d-dates-osw-display"></div>
    </div>
    <div class="ov-arr green" id="d-arr-osw-display" style="font-size:20px"></div>
  </div>
  <div class="callout"><i class="ti ti-topology-star-3"></i><span>Feeds broader OSW-wide goal. Related efforts: SecWar Front Office · P&amp;R re-engagement.</span></div>

  <div class="section">
    <div class="section-title"><i class="ti ti-info-circle"></i> Core info</div>
    <div class="ef"><div class="ef-label">ARR (FY27 target)</div><div class="ef-val" contenteditable="true" data-key="osw.arr" data-sync="ov-arr-osw,d-arr-osw-display"></div></div>
    <div class="ef"><div class="ef-label">Dates</div><div class="ef-val" contenteditable="true" data-key="osw.dates" data-sync="ov-dates-osw,d-dates-osw-display"></div></div>
    <div class="ef"><div class="ef-label">Networks</div><div class="ef-val" contenteditable="true" data-key="osw.networks" data-sync="ov-net-osw"></div></div>
    <div class="ef"><div class="ef-label">Gov lead(s)</div><div class="ef-val" contenteditable="true" data-key="osw.govlead"></div></div>
    <div class="ef"><div class="ef-label">Decision makers</div><div class="ef-val" contenteditable="true" data-key="osw.dm"></div></div>
    <div class="ef"><div class="ef-label">Contracting / Sales</div><div class="ef-val" contenteditable="true" data-key="osw.sales"></div></div>
    <div class="ef"><div class="ef-label">CR lead</div><div class="ef-val" contenteditable="true" data-key="osw.crlead"></div></div>
    <div class="ef"><div class="ef-label">CR support</div><div class="ef-val" contenteditable="true" data-key="osw.crsupport"></div></div>
    <div class="ef"><div class="ef-label">Expansion target</div><div class="ef-val" contenteditable="true" data-key="osw.expansion"></div></div>
    <div class="ef"><div class="ef-label">Contracting notes</div><div class="ef-val" contenteditable="true" data-key="osw.contracting"></div></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-list-tree"></i> Phase breakdown
      <button class="add-btn" onclick="addBlock('osw-phases','Phase','Description')"><i class="ti ti-plus"></i> Add phase</button>
    </div>
    <div id="osw-phases"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-trophy"></i> Success criteria
      <button class="add-btn" onclick="addSuccess('osw')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div class="stags" id="osw-success"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist
      <button class="add-btn" onclick="addCheck('osw')"><i class="ti ti-plus"></i> Add item</button>
    </div>
    <ul class="checklist" id="osw-cl"></ul>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence
      <button class="add-btn" onclick="addBlock('osw-checkins','','')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="osw-checkins"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks
      <button class="add-btn" onclick="addBlock('osw-risks','New risk','Describe mitigation here','red')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="osw-risks"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-circles-relation"></i> Related OSW efforts
      <button class="add-btn" onclick="addBlock('osw-related','Effort','Status')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="osw-related"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-link"></i> Resources &amp; docs
      <button class="add-btn" onclick="addLink('osw-links')"><i class="ti ti-plus"></i> Add link</button>
    </div>
    <div class="link-list" id="osw-links"></div>
  </div>
</div>

<!-- DTRA DETAIL -->
<div id="tab-dtra" class="tab-pane">
  <div style="display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:1rem;flex-wrap:wrap;gap:8px">
    <div>
      <div style="font-size:18px;font-weight:500"><i class="ti ti-shield" style="margin-right:6px"></i>DTRA J3/5/8</div>
      <div style="font-size:12px;color:var(--text2)" id="d-dates-dtra-display"></div>
    </div>
    <div class="ov-arr amber" id="d-arr-dtra-display" style="font-size:20px"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-info-circle"></i> Core info</div>
    <div class="ef"><div class="ef-label">ARR</div><div class="ef-val" contenteditable="true" data-key="dtra.arr" data-sync="ov-arr-dtra,d-arr-dtra-display"></div></div>
    <div class="ef"><div class="ef-label">Dates</div><div class="ef-val" contenteditable="true" data-key="dtra.dates" data-sync="ov-dates-dtra,d-dates-dtra-display"></div></div>
    <div class="ef"><div class="ef-label">Networks</div><div class="ef-val" contenteditable="true" data-key="dtra.networks" data-sync="ov-net-dtra"></div></div>
    <div class="ef"><div class="ef-label">Gov lead(s)</div><div class="ef-val" contenteditable="true" data-key="dtra.govlead"></div></div>
    <div class="ef"><div class="ef-label">Decision makers</div><div class="ef-val" contenteditable="true" data-key="dtra.dm"></div></div>
    <div class="ef"><div class="ef-label">Contracting / Sales</div><div class="ef-val" contenteditable="true" data-key="dtra.sales"></div></div>
    <div class="ef"><div class="ef-label">CR lead</div><div class="ef-val" contenteditable="true" data-key="dtra.crlead"></div></div>
    <div class="ef"><div class="ef-label">CR support</div><div class="ef-val" contenteditable="true" data-key="dtra.crsupport"></div></div>
    <div class="ef"><div class="ef-label">Expansion target</div><div class="ef-val" contenteditable="true" data-key="dtra.expansion"></div></div>
    <div class="ef"><div class="ef-label">Contracting notes</div><div class="ef-val" contenteditable="true" data-key="dtra.contracting"></div></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-list-check"></i> Workflows &amp; success criteria
      <button class="add-btn" onclick="addSuccess('dtra')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div class="ef"><div class="ef-label">Confirmed workflows</div><div class="ef-val" contenteditable="true" data-key="dtra.workflows"></div></div>
    <div class="stags" id="dtra-success"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist
      <button class="add-btn" onclick="addCheck('dtra')"><i class="ti ti-plus"></i> Add item</button>
    </div>
    <ul class="checklist" id="dtra-cl"></ul>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence
      <button class="add-btn" onclick="addBlock('dtra-checkins','','')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="dtra-checkins"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks
      <button class="add-btn" onclick="addBlock('dtra-risks','New risk','Describe mitigation here','red')"><i class="ti ti-plus"></i> Add</button>
    </div>
    <div id="dtra-risks"></div>
  </div>

  <div class="section">
    <div class="section-title"><i class="ti ti-link"></i> Resources &amp; docs
      <button class="add-btn" onclick="addLink('dtra-links')"><i class="ti ti-plus"></i> Add link</button>
    </div>
    <div class="link-list" id="dtra-links"></div>
  </div>
</div>

</div><!-- /wrap -->

<!-- POPUP -->
<div class="pop-ov" id="pop-ov" onclick="if(event.target.id==='pop-ov')closePop()">
  <div class="popup">
    <button class="popup-close" onclick="closePop()"><i class="ti ti-x"></i></button>
    <div class="popup-title" id="pop-title"></div>
    <div id="pop-body"></div>
    <div class="popup-goto"><button onclick="gotoTab()">View full detail →</button></div>
  </div>
</div>

<script>
// ── State ──────────────────────────────────────────────────────────────────
var DEFAULTS = {
  'opnav.arr':'$TBD','opnav.dates':'18 May – 12 Jun 2025','opnav.networks':'IL6',
  'opnav.govlead':'NOC / N33','opnav.dm':'N9 (champion + funding) · N3 (positive support) · APHIT (potential)',
  'opnav.sales':'Will W · Chris T','opnav.crlead':'Will W · Chris T','opnav.crsupport':'Phil · Brandon',
  'opnav.expansion':'N9 primary · N3 · APHIT · Navy-wide FY27','opnav.workflows':'NpI and X · NOC / N33',
  'osw.arr':'$1.2M','osw.dates':'1 Jul 2025 · 3 phases contracted','osw.networks':'IL5 · AI Assist',
  'osw.govlead':'TBD per phase','osw.dm':'Phase 3 IBP leadership (currently resistant)',
  'osw.sales':'Will W','osw.crlead':'Phil','osw.crsupport':'GDT – Scott',
  'osw.expansion':'Full IBP FY27 ($1.2M) · OSW-wide','osw.workflows':'Ph1: Industry Affairs · Ph2: Mismatch lead · Ph3: Industrial Base Policy + Front Office',
  'dtra.arr':'$TBD','dtra.dates':'1 Aug – 31 Oct 2025','dtra.networks':'IL5 · IL6 · JWICS · AI Assist',
  'dtra.govlead':'TBD','dtra.dm':'TBD','dtra.sales':'Will W',
  'dtra.crlead':'Sam Sok (potential, JS team)','dtra.crsupport':'Greg Nolan (GDT, joining July)',
  'dtra.expansion':'6-month CLIN → full DTRA mid-year','dtra.workflows':'OPORDs · FRAGORDs · Operational planning workflows'
};

var BLOCK_DEFAULTS = {
  'opnav-checkins':[{l:'Week 1',v:'Kickoff brief · account confirmation · baseline workflow walk-through'},{l:'Week 2',v:'Mid-pilot sync with gov lead · issue triage · engagement pulse'},{l:'End of pilot',v:'AAR · outcomes summary · expansion brief to N9'}],
  'opnav-risks':[{l:'Customer engagement',v:'Limited hands-on during pilot, particularly in the NOC. Identify dedicated NOC POC pre-launch.',c:'red'}],
  'osw-phases':[{l:'Phase 1',v:'Industry Affairs'},{l:'Phase 2',v:'Mismatch is lead'},{l:'Phase 3',v:'Industrial Base Policy + Front Office'}],
  'osw-checkins':[{l:'Pre-Phase 1',v:'Account creation · training · Phil/Scott alignment call'},{l:'Phase 1 mid-point',v:'Workflow review · issue log · engagement pulse'},{l:'Phase transition',v:'Phase AAR · brief to next phase team · docs status check'},{l:'End of Phase 3',v:'IBP-wide expansion brief · FY27 ARR target discussion'}],
  'osw-risks':[{l:'Primary',v:'Documents release date — must be live by Phase 1 start',c:'red'},{l:'Phase 3',v:'IBP leadership currently negative on adopting another digital tool.',c:'red'}],
  'osw-related':[{l:'SecWar Front Office',v:'Re-engagement opportunity — track status'},{l:'P&R',v:'Re-engagement — add when active'}],
  'dtra-checkins':[{l:'Pre-launch (July)',v:'Sam / Greg onboarding · account creation · stakeholder brief'},{l:'Month 1 (August)',v:'Kickoff · OPORD workflow walk-through · issue triage'},{l:'Month 2 (September)',v:'Mid-pilot sync · FRAGORD workflow · expansion conversation initiated'},{l:'Month 3 (October)',v:'AAR · CLIN add-on push · full expansion brief to DTRA leadership'}],
  'dtra-risks':[{l:'Funding',v:'Gov shutdown risk — primary. Contingency plan needed.',c:'red'},{l:'Documents feature',v:'Must be online by start date. Track with product.',c:'red'},{l:'Staffing',v:'CR lead (Sam) and CR support (Greg) not yet confirmed. Finalize by July.',c:'yellow'}]
};

var SUCCESS_DEFAULTS = {
  'opnav':['Gov hands-on engagement','NOC workflow completed','N9 positive feedback','Expansion brief delivered'],
  'osw':['Documents feature live by start','Ph1 workflow complete','Ph3 adoption / buy-in','IBP-wide expansion brief delivered'],
  'dtra':['OPORD workflow live','FRAGORD workflow live','6-month CLIN add-on initiated','Full DTRA expansion brief delivered']
};

var CL_DEFAULTS = [
  'Accounts created and tested on target network',
  'Training session scheduled with key users',
  'Stakeholder alignment brief delivered',
  'Workflow walk-through completed (CR + gov lead)',
  'Gov POC confirmed for pilot duration',
  'Success criteria finalized and agreed',
  'Check-in cadence and dates locked',
  'Issues / feedback channel established',
  'Kick-off deck / one-pager shared with customer',
  'AAR template prepared',
  'Expansion conversation owner identified',
  'All documents / feature dependencies confirmed live'
];

function load(k,def){try{var v=localStorage.getItem('ncr2:'+k);return v!==null?JSON.parse(v):def;}catch(e){return def;}}
function save(k,v){try{localStorage.setItem('ncr2:'+k,JSON.stringify(v));flash();}catch(e){}}

function flash(){var d=document.getElementById('savedot');d.classList.add('show');setTimeout(function(){d.classList.remove('show');},1200);}

// ── Fields ─────────────────────────────────────────────────────────────────
function initFields(){
  document.querySelectorAll('[data-key]').forEach(function(el){
    var k=el.dataset.key;
    var val=load('field:'+k,DEFAULTS[k]||'');
    el.textContent=val;
    syncField(el,val);
    el.addEventListener('input',function(){
      var v=el.textContent.trim();
      save('field:'+k,v);
      syncField(el,v);
    });
  });
}

function syncField(el,val){
  var ids=(el.dataset.sync||'').split(',').filter(Boolean);
  ids.forEach(function(id){
    var t=document.getElementById(id);
    if(t)t.textContent=val;
  });
}

// ── Blocks ─────────────────────────────────────────────────────────────────
function renderBlock(containerId,item,idx){
  var c=document.getElementById(containerId);
  if(!c)return;
  var div=document.createElement('div');
  div.className='phase-block'+(item.c?' '+item.c:'');
  div.dataset.idx=idx;
  div.innerHTML='<div class="phase-content"><div class="phase-label-el" contenteditable="true">'+escH(item.l)+'</div><div class="phase-val-el" contenteditable="true">'+escH(item.v)+'</div></div><button class="del-btn" onclick="delBlock(\''+containerId+'\','+idx+')" title="Delete"><i class="ti ti-x"></i></button>';
  div.querySelector('.phase-label-el').addEventListener('input',function(){saveBlockField(containerId,idx,'l',this.textContent.trim());});
  div.querySelector('.phase-val-el').addEventListener('input',function(){saveBlockField(containerId,idx,'v',this.textContent.trim());});
  c.appendChild(div);
}

function initBlocks(containerId){
  var c=document.getElementById(containerId);
  if(!c)return;
  c.innerHTML='';
  var items=load('blocks:'+containerId,BLOCK_DEFAULTS[containerId]||[]);
  items.forEach(function(item,i){renderBlock(containerId,item,i);});
}

function addBlock(containerId,defL,defV,defC){
  var items=load('blocks:'+containerId,BLOCK_DEFAULTS[containerId]||[]);
  items.push({l:defL||'Label',v:defV||'Description',c:defC||''});
  save('blocks:'+containerId,items);
  var c=document.getElementById(containerId);c.innerHTML='';
  items.forEach(function(item,i){renderBlock(containerId,item,i);});
}

function delBlock(containerId,idx){
  var items=load('blocks:'+containerId,BLOCK_DEFAULTS[containerId]||[]);
  items.splice(idx,1);
  save('blocks:'+containerId,items);
  var c=document.getElementById(containerId);c.innerHTML='';
  items.forEach(function(item,i){renderBlock(containerId,item,i);});
}

function saveBlockField(containerId,idx,field,val){
  var items=load('blocks:'+containerId,BLOCK_DEFAULTS[containerId]||[]);
  if(items[idx])items[idx][field]=val;
  save('blocks:'+containerId,items);
}

// ── Checklist ──────────────────────────────────────────────────────────────
function initChecklist(pid){
  var ul=document.getElementById(pid+'-cl');
  if(!ul)return;
  var items=load('cl2:'+pid,CL_DEFAULTS.map(function(t){return{t:t,c:false};}));
  ul.innerHTML='';
  items.forEach(function(item,i){renderCheckItem(pid,item,i);});
}

function renderCheckItem(pid,item,i){
  var ul=document.getElementById(pid+'-cl');
  var li=document.createElement('li');
  li.className=item.c?'done':'';
  li.dataset.idx=i;
  var chk=document.createElement('input');
  chk.type='checkbox';chk.checked=item.c;chk.id=pid+'-ci-'+i;
  chk.addEventListener('change',function(){saveCheckState(pid,i,this.checked);li.classList.toggle('done',this.checked);});
  var lbl=document.createElement('label');
  lbl.setAttribute('for',pid+'-ci-'+i);
  lbl.setAttribute('contenteditable','true');
  lbl.textContent=item.t;
  lbl.addEventListener('input',function(){saveCheckText(pid,i,this.textContent.trim());});
  var del=document.createElement('button');
  del.className='del-btn';del.title='Delete';del.innerHTML='<i class="ti ti-x"></i>';
  del.addEventListener('click',function(){delCheck(pid,i);});
  li.appendChild(chk);li.appendChild(lbl);li.appendChild(del);
  ul.appendChild(li);
}

function addCheck(pid){
  var items=load('cl2:'+pid,CL_DEFAULTS.map(function(t){return{t:t,c:false};}));
  items.push({t:'New checklist item',c:false});
  save('cl2:'+pid,items);
  initChecklist(pid);
}

function delCheck(pid,idx){
  var items=load('cl2:'+pid,CL_DEFAULTS.map(function(t){return{t:t,c:false};}));
  items.splice(idx,1);
  save('cl2:'+pid,items);
  initChecklist(pid);
}

function saveCheckState(pid,i,val){
  var items=load('cl2:'+pid,CL_DEFAULTS.map(function(t){return{t:t,c:false};}));
  if(items[i])items[i].c=val;
  save('cl2:'+pid,items);
}

function saveCheckText(pid,i,val){
  var items=load('cl2:'+pid,CL_DEFAULTS.map(function(t){return{t:t,c:false};}));
  if(items[i])items[i].t=val;
  save('cl2:'+pid,items);
}

// ── Success tags ───────────────────────────────────────────────────────────
function initSuccess(pid){
  var c=document.getElementById(pid+'-success');
  if(!c)return;
  var items=load('success:'+pid,SUCCESS_DEFAULTS[pid]||[]);
  c.innerHTML='';
  items.forEach(function(text,i){
    var span=document.createElement('span');
    span.className='stag';
    var lbl=document.createElement('span');
    lbl.setAttribute('contenteditable','true');
    lbl.textContent=text;
    lbl.addEventListener('input',function(){saveSuccessText(pid,i,this.textContent.trim());});
    var del=document.createElement('button');
    del.className='del-btn';del.innerHTML='<i class="ti ti-x"></i>';
    del.addEventListener('click',function(){delSuccess(pid,i);});
    span.appendChild(lbl);span.appendChild(del);
    c.appendChild(span);
  });
}

function addSuccess(pid){
  var items=load('success:'+pid,SUCCESS_DEFAULTS[pid]||[]);
  items.push('New criterion');
  save('success:'+pid,items);
  initSuccess(pid);
}

function delSuccess(pid,idx){
  var items=load('success:'+pid,SUCCESS_DEFAULTS[pid]||[]);
  items.splice(idx,1);
  save('success:'+pid,items);
  initSuccess(pid);
}

function saveSuccessText(pid,i,val){
  var items=load('success:'+pid,SUCCESS_DEFAULTS[pid]||[]);
  if(items[i]!==undefined)items[i]=val;
  save('success:'+pid,items);
}

// ── Links ──────────────────────────────────────────────────────────────────
function initLinks(containerId){
  var c=document.getElementById(containerId);
  if(!c)return;
  var defaults=containerId==='opnav-links'?[{label:'Pilot execution & AAR',url:'https://app.notion.com/p/onebrief/N9I-Pilot-Execution-and-AAR-097e3bddbaa883acb4ca014e0dcbe9f4'}]:[];
  var items=load('links:'+containerId,defaults);
  c.innerHTML='';
  items.forEach(function(item,i){renderLink(containerId,item,i);});
}

function renderLink(containerId,item,i){
  var c=document.getElementById(containerId);
  var div=document.createElement('div');
  div.className='link-item';
  var icon=document.createElement('i');
  icon.className='ti ti-file-text';icon.style.cssText='color:var(--text2);flex-shrink:0;font-size:14px;margin-top:2px';
  var inner=document.createElement('div');inner.style.flex='1';
  var lbl=document.createElement('div');lbl.className='link-item-label';lbl.setAttribute('contenteditable','true');lbl.textContent=item.label;
  lbl.addEventListener('input',function(){saveLinkField(containerId,i,'label',this.textContent.trim());});
  var a=document.createElement('a');a.setAttribute('contenteditable','true');a.textContent=item.url;
  a.addEventListener('input',function(){saveLinkField(containerId,i,'url',this.textContent.trim());});
  a.addEventListener('blur',function(){if(this.textContent.startsWith('http'))this.href=this.textContent.trim();});
  if(item.url.startsWith('http'))a.href=item.url;a.target='_blank';
  inner.appendChild(lbl);inner.appendChild(a);
  var del=document.createElement('button');
  del.className='del-btn';del.innerHTML='<i class="ti ti-x"></i>';
  del.addEventListener('click',function(){delLink(containerId,i);});
  div.appendChild(icon);div.appendChild(inner);div.appendChild(del);
  c.appendChild(div);
}

function addLink(containerId){
  var items=load('links:'+containerId,[]);
  items.push({label:'Link label',url:'https://'});
  save('links:'+containerId,items);
  initLinks(containerId);
}

function delLink(containerId,idx){
  var items=load('links:'+containerId,[]);
  items.splice(idx,1);
  save('links:'+containerId,items);
  initLinks(containerId);
}

function saveLinkField(containerId,i,field,val){
  var items=load('links:'+containerId,[]);
  if(items[i])items[i][field]=val;
  save('links:'+containerId,items);
}

// ── Calendar ───────────────────────────────────────────────────────────────
var CAL_MONTHS=[{name:'May 2025',y:2025,m:4,days:31},{name:'Jun 2025',y:2025,m:5,days:30},{name:'Jul 2025',y:2025,m:6,days:31},{name:'Aug 2025',y:2025,m:7,days:31}];
var DLABELS=['S','M','T','W','T','F','S'];

function pilotClass(y,m,d){
  var dt=new Date(y,m,d);
  var inOp=dt>=new Date(2025,4,18)&&dt<=new Date(2025,5,12);
  var inOsw=dt>=new Date(2025,6,1);
  var inDtra=dt>=new Date(2025,7,1)&&dt<=new Date(2025,9,31);
  if(inOp&&inOsw) return 'opnav-osw';
  if(inOsw&&inDtra) return 'osw-dtra';
  if(inOp) return 'opnav';
  if(inOsw) return 'osw';
  if(inDtra) return 'dtra';
  return '';
}

function pilotFromClass(cls){
  if(cls==='opnav-osw') return 'opnav';
  if(cls==='osw-dtra') return 'osw';
  return cls;
}

function buildCalendar(){
  var outer=document.getElementById('cal-outer');
  outer.innerHTML='';
  CAL_MONTHS.forEach(function(mo){
    var div=document.createElement('div');div.className='cal-month';
    var html='<div class="cal-month-title">'+mo.name+'</div>';
    html+='<div class="cal-week-row">'+DLABELS.map(function(l){return'<div class="cal-dlabel">'+l+'</div>';}).join('')+'</div>';
    var first=new Date(mo.y,mo.m,1).getDay();
    var cells=[];
    for(var i=0;i<first;i++) cells.push('<div class="cal-day"></div>');
    for(var d=1;d<=mo.days;d++){
      var pc=pilotClass(mo.y,mo.m,d);
      if(pc){var pk=pilotFromClass(pc);cells.push('<div class="cal-day '+pc+'" onclick="showPop(\''+pk+'\')" title="'+d+'">'+d+'</div>');}
      else cells.push('<div class="cal-day">'+d+'</div>');
      if(cells.length===7){html+='<div class="cal-week-row">'+cells.join('')+'</div>';cells=[];}
    }
    if(cells.length)html+='<div class="cal-week-row">'+cells.join('')+'</div>';
    div.innerHTML=html;outer.appendChild(div);
  });
}

// ── Popup ──────────────────────────────────────────────────────────────────
var curPopPilot='';
var POP_DATA={
  opnav:{name:'OPNAV N9I'},
  osw:{name:'OSW IBP'},
  dtra:{name:'DTRA J3/5/8'}
};

function showPop(pilot){
  curPopPilot=pilot;
  var keys=['arr','dates','networks','govlead','crlead','crsupport'];
  var labels=['ARR','Dates','Networks','Gov lead','CR lead','CR support'];
  var html='';
  keys.forEach(function(k,i){
    var v=load('field:'+pilot+'.'+k,DEFAULTS[pilot+'.'+k]||'—');
    html+='<div class="ef"><div class="ef-label">'+labels[i]+'</div><div class="ef-val">'+escH(v)+'</div></div>';
  });
  document.getElementById('pop-title').textContent=POP_DATA[pilot].name;
  document.getElementById('pop-body').innerHTML=html;
  document.getElementById('pop-ov').classList.add('open');
}

function closePop(){document.getElementById('pop-ov').classList.remove('open');}
function gotoTab(){closePop();switchTab(curPopPilot);}

// ── Tab switch ─────────────────────────────────────────────────────────────
function switchTab(id){
  document.querySelectorAll('.tab-btn').forEach(function(b){b.classList.remove('active');});
  document.querySelectorAll('.tab-pane').forEach(function(p){p.classList.remove('active');});
  document.getElementById('tab-'+id).classList.add('active');
  var map={overview:0,calendar:1,opnav:2,osw:3,dtra:4};
  document.querySelectorAll('.tab-btn')[map[id]].classList.add('active');
}

function escH(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}

// ── Init ───────────────────────────────────────────────────────────────────
initFields();
['opnav-checkins','opnav-risks','osw-phases','osw-checkins','osw-risks','osw-related','dtra-checkins','dtra-risks'].forEach(initBlocks);
['opnav','osw','dtra'].forEach(function(p){initChecklist(p);initSuccess(p);});
['opnav-links','osw-links','dtra-links'].forEach(initLinks);
buildCalendar();
</script>
</body>
</html>
