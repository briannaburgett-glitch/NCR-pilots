<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NCR Pilots Dashboard</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/tabler-icons/2.44.0/iconfont/tabler-icons.min.css">
<style>
  :root {
    --bg: #ffffff; --bg2: #f8f8f6; --bg3: #f1f0eb;
    --text: #1a1a18; --text2: #5f5e5a; --text3: #888780;
    --border: rgba(0,0,0,0.12); --border2: rgba(0,0,0,0.2);
    --blue-bg: #E6F1FB; --blue-text: #0C447C; --blue-border: #B5D4F4;
    --green-bg: #E1F5EE; --green-text: #085041; --green-border: #9FE1CB;
    --amber-bg: #FAEEDA; --amber-text: #633806; --amber-border: #FAC775;
    --red-bg: #FCEBEB; --red-text: #A32D2D; --red-border: #F7C1C1;
    --yellow-bg: #FAEEDA; --yellow-text: #633806; --yellow-border: #FAC775;
    --radius: 8px; --radius-lg: 12px;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #1c1c1a; --bg2: #242422; --bg3: #2c2c2a;
      --text: #f0ede8; --text2: #b4b2a9; --text3: #888780;
      --border: rgba(255,255,255,0.1); --border2: rgba(255,255,255,0.18);
      --blue-bg: #0c2f50; --blue-text: #85B7EB; --blue-border: #185FA5;
      --green-bg: #053528; --green-text: #5DCAA5; --green-border: #0F6E56;
      --amber-bg: #3a2205; --amber-text: #EF9F27; --amber-border: #854F0B;
      --red-bg: #3a1010; --red-text: #F09595; --red-border: #A32D2D;
    }
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; background: var(--bg); color: var(--text); font-size: 14px; line-height: 1.5; }
  .wrap { max-width: 900px; margin: 0 auto; padding: 1.5rem 1rem 3rem; }

  /* Header */
  .dash-header { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 1.5rem; flex-wrap: wrap; gap: 12px; }
  .dash-title { font-size: 20px; font-weight: 500; }
  .dash-sub { font-size: 12px; color: var(--text2); margin-top: 3px; }
  .total-arr { text-align: right; }
  .total-arr-label { font-size: 11px; color: var(--text2); }
  .total-arr-value { font-size: 26px; font-weight: 500; }
  .total-arr-note { font-size: 10px; color: var(--text3); }

  /* Tabs */
  .tab-bar { display: flex; gap: 4px; border-bottom: 0.5px solid var(--border); margin-bottom: 1.5rem; overflow-x: auto; }
  .tab-btn { padding: 8px 14px; font-size: 13px; font-weight: 500; border: none; background: transparent; color: var(--text2); cursor: pointer; border-bottom: 2px solid transparent; margin-bottom: -0.5px; white-space: nowrap; transition: color .15s; }
  .tab-btn.active { color: var(--text); border-bottom-color: var(--text); }
  .tab-btn:hover:not(.active) { color: var(--text); }
  .tab-pane { display: none; }
  .tab-pane.active { display: block; }

  /* Cards */
  .pilot-card { background: var(--bg); border: 0.5px solid var(--border); border-radius: var(--radius-lg); padding: 1.25rem; margin-bottom: 1rem; }
  .card-header { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 1rem; gap: 12px; flex-wrap: wrap; }
  .card-name { font-size: 16px; font-weight: 500; }
  .card-dates { font-size: 12px; color: var(--text2); margin-top: 3px; }
  .arr-badge { font-size: 20px; font-weight: 500; padding: 6px 14px; border-radius: var(--radius); text-align: center; min-width: 90px; }
  .arr-badge.blue { background: var(--blue-bg); color: var(--blue-text); }
  .arr-badge.green { background: var(--green-bg); color: var(--green-text); }
  .arr-badge.amber { background: var(--amber-bg); color: var(--amber-text); }
  .arr-sub { font-size: 10px; color: var(--text3); text-align: center; margin-top: 3px; }

  /* Fields grid */
  .fields-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px 20px; }
  @media (max-width: 520px) { .fields-grid { grid-template-columns: 1fr; } }
  .field-row { padding: 4px 0; border-bottom: 0.5px solid var(--border); }
  .field-label { font-size: 10px; color: var(--text2); text-transform: uppercase; letter-spacing: .04em; margin-bottom: 2px; }
  .field-value { font-size: 13px; color: var(--text); }
  .net-pill { display: inline-block; background: var(--bg2); border: 0.5px solid var(--border2); border-radius: var(--radius); font-size: 11px; padding: 1px 7px; margin: 1px 2px 0 0; }

  /* Risk / callout badges */
  .risk-wrap { margin-top: 8px; display: flex; flex-wrap: wrap; gap: 4px; }
  .risk-tag { display: inline-flex; align-items: center; gap: 4px; background: var(--red-bg); color: var(--red-text); border: 0.5px solid var(--red-border); font-size: 11px; padding: 3px 8px; border-radius: var(--radius); }
  .risk-tag.yellow { background: var(--yellow-bg); color: var(--yellow-text); border-color: var(--yellow-border); }
  .callout { background: var(--green-bg); border: 0.5px solid var(--green-border); border-radius: var(--radius); padding: 8px 12px; font-size: 12px; color: var(--green-text); margin-top: 8px; display: flex; gap: 8px; align-items: flex-start; }

  /* Detail section */
  .detail-section { margin-bottom: 1.25rem; }
  .section-title { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: .05em; color: var(--text2); margin-bottom: 8px; display: flex; align-items: center; gap: 6px; }
  .phase-block { background: var(--bg2); border-radius: var(--radius); padding: 9px 12px; margin-bottom: 6px; }
  .phase-label { font-size: 11px; font-weight: 500; color: var(--text2); margin-bottom: 3px; }
  .phase-value { font-size: 13px; }
  .phase-block.red { background: var(--red-bg); border: 0.5px solid var(--red-border); }
  .phase-block.red .phase-label, .phase-block.red .phase-value { color: var(--red-text); }
  .phase-block.yellow { background: var(--yellow-bg); border: 0.5px solid var(--yellow-border); }
  .phase-block.yellow .phase-label, .phase-block.yellow .phase-value { color: var(--yellow-text); }

  /* Checklist */
  .checklist { list-style: none; }
  .checklist li { display: flex; align-items: flex-start; gap: 8px; padding: 5px 0; border-bottom: 0.5px solid var(--border); font-size: 13px; }
  .checklist li:last-child { border-bottom: none; }
  .checklist li input[type=checkbox] { margin-top: 2px; flex-shrink: 0; cursor: pointer; accent-color: var(--blue-text); width: 14px; height: 14px; }
  .checklist li.done label { text-decoration: line-through; color: var(--text3); }

  /* Success tags */
  .success-tags { display: flex; flex-wrap: wrap; gap: 4px; margin-top: 6px; }
  .success-tag { display: inline-block; background: #EAF3DE; color: #3B6D11; font-size: 11px; padding: 2px 8px; border-radius: var(--radius); }
  @media (prefers-color-scheme: dark) { .success-tag { background: #173404; color: #97C459; } }

  /* Calendar */
  .cal-legend { display: flex; gap: 12px; margin-bottom: 1rem; flex-wrap: wrap; }
  .cal-legend-item { display: flex; align-items: center; gap: 6px; font-size: 12px; color: var(--text2); }
  .cal-legend-dot { width: 12px; height: 12px; border-radius: 2px; }
  .cal-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1px; background: var(--border); border: 0.5px solid var(--border); border-radius: var(--radius); overflow: hidden; }
  @media (max-width: 600px) { .cal-grid { grid-template-columns: repeat(2, 1fr); } }
  .cal-month { background: var(--bg); padding: 10px; }
  .cal-month-title { font-size: 11px; font-weight: 500; color: var(--text2); margin-bottom: 6px; text-transform: uppercase; letter-spacing: .05em; }
  .cal-week-row { display: grid; grid-template-columns: repeat(7, 1fr); gap: 1px; margin-bottom: 1px; }
  .cal-day-label { font-size: 9px; color: var(--text3); text-align: center; padding: 2px 0; }
  .cal-day { min-height: 20px; border-radius: 2px; font-size: 9px; display: flex; align-items: center; justify-content: center; color: var(--text3); }
  .cal-day.opnav { background: var(--blue-border); color: var(--blue-text); cursor: pointer; }
  .cal-day.osw { background: var(--green-border); color: var(--green-text); cursor: pointer; }
  .cal-day.dtra { background: var(--amber-border); color: var(--amber-text); cursor: pointer; }

  /* Popup */
  .popup-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,.4); z-index: 200; align-items: center; justify-content: center; }
  .popup-overlay.open { display: flex; }
  .popup { background: var(--bg); border-radius: var(--radius-lg); padding: 1.25rem; max-width: 380px; width: 92%; border: 0.5px solid var(--border2); position: relative; max-height: 90vh; overflow-y: auto; }
  .popup-close { position: absolute; top: 10px; right: 12px; background: none; border: none; font-size: 18px; cursor: pointer; color: var(--text2); }
  .popup-title { font-size: 15px; font-weight: 500; margin-bottom: 12px; padding-right: 24px; }
  .popup-goto { font-size: 12px; margin-top: 12px; }
  .popup-goto button { font-size: 12px; padding: 5px 12px; cursor: pointer; background: var(--bg2); border: 0.5px solid var(--border2); border-radius: var(--radius); color: var(--text); }

  /* Link list */
  .link-list { display: flex; flex-direction: column; gap: 6px; }
  .link-item { display: flex; align-items: flex-start; gap: 8px; background: var(--bg2); border-radius: var(--radius); padding: 8px 10px; }
  .link-item a { font-size: 13px; color: var(--blue-text); text-decoration: none; word-break: break-all; }
  .link-item a:hover { text-decoration: underline; }
  .link-item-label { font-size: 11px; color: var(--text2); }
  .link-add { font-size: 11px; color: var(--text3); font-style: italic; }
</style>
</head>
<body>
<div class="wrap">

  <div class="dash-header">
    <div>
      <div class="dash-title">NCR Pilot Dashboard</div>
      <div class="dash-sub">OPNAV N9I · OSW IBP · DTRA J3/5/8 — FY26 Execution</div>
    </div>
    <div class="total-arr">
      <div class="total-arr-label">Total ARR target</div>
      <div class="total-arr-value">$TBD</div>
      <div class="total-arr-note">Update when confirmed</div>
    </div>
  </div>

  <div class="tab-bar">
    <button class="tab-btn active" onclick="switchTab('overview')"><i class="ti ti-layout-grid"></i> Overview</button>
    <button class="tab-btn" onclick="switchTab('calendar')"><i class="ti ti-calendar"></i> Calendar</button>
    <button class="tab-btn" onclick="switchTab('opnav')"><i class="ti ti-anchor"></i> OPNAV</button>
    <button class="tab-btn" onclick="switchTab('osw')"><i class="ti ti-briefcase"></i> OSW IBP</button>
    <button class="tab-btn" onclick="switchTab('dtra')"><i class="ti ti-shield"></i> DTRA J3/5/8</button>
  </div>

  <!-- OVERVIEW -->
  <div id="tab-overview" class="tab-pane active">

    <div class="pilot-card">
      <div class="card-header">
        <div>
          <div class="card-name"><i class="ti ti-anchor" style="margin-right:6px"></i>OPNAV N9I</div>
          <div class="card-dates">18 May – 12 June 2025 · IL6</div>
        </div>
        <div><div class="arr-badge blue">$TBD</div><div class="arr-sub">→ Navy-wide FY27</div></div>
      </div>
      <div class="fields-grid">
        <div class="field-row"><div class="field-label">Networks</div><div class="field-value"><span class="net-pill">IL6</span></div></div>
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">NOC / N33</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">N9 (champion + funding) · N3 (positive) · APHIT (potential)</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W · Chris T</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Will W · Chris T</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">Phil · Brandon</div></div>
        <div class="field-row"><div class="field-label">Deliverables / Workflows</div><div class="field-value">NpI and X · NOC / N33</div></div>
        <div class="field-row"><div class="field-label">Expansion target</div><div class="field-value">N9 primary · N3 · APHIT · Navy-wide FY27</div></div>
      </div>
      <div class="risk-wrap"><span class="risk-tag"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: limited hands-on during pilot, esp. NOC</span></div>
    </div>

    <div class="pilot-card">
      <div class="card-header">
        <div>
          <div class="card-name"><i class="ti ti-briefcase" style="margin-right:6px"></i>OSW IBP</div>
          <div class="card-dates">1 July 2025 · 3 phases contracted · IL5 + AI Assist</div>
        </div>
        <div><div class="arr-badge green">$1.2M</div><div class="arr-sub">FY27 — full IBP</div></div>
      </div>
      <div class="callout"><i class="ti ti-topology-star-3"></i><span>Feeds broader OSW-wide goal. Related: SecWar Front Office · P&amp;R re-engagement.</span></div>
      <div class="fields-grid" style="margin-top:10px">
        <div class="field-row"><div class="field-label">Networks</div><div class="field-value"><span class="net-pill">IL5</span><span class="net-pill">AI Assist</span></div></div>
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">TBD per phase</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">Ph3 IBP leadership (currently resistant)</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Phil</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">GDT – Scott</div></div>
        <div class="field-row"><div class="field-label">Deliverables / Workflows</div><div class="field-value">Ph1: Industry Affairs · Ph2: Mismatch lead · Ph3: Industrial Base Policy + Front Office</div></div>
        <div class="field-row"><div class="field-label">Expansion target</div><div class="field-value">Full IBP FY27 ($1.2M) · OSW-wide</div></div>
      </div>
      <div class="risk-wrap">
        <span class="risk-tag"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: documents release date</span>
        <span class="risk-tag"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: Phase 3 resistance</span>
      </div>
    </div>

    <div class="pilot-card">
      <div class="card-header">
        <div>
          <div class="card-name"><i class="ti ti-shield" style="margin-right:6px"></i>DTRA J3/5/8</div>
          <div class="card-dates">1 Aug – 31 Oct 2025 · IL5/IL6/JWICS + AI Assist</div>
        </div>
        <div><div class="arr-badge amber">$TBD</div><div class="arr-sub">→ Full DTRA mid-year</div></div>
      </div>
      <div class="fields-grid">
        <div class="field-row"><div class="field-label">Networks</div><div class="field-value"><span class="net-pill">IL5</span><span class="net-pill">IL6</span><span class="net-pill">JWICS</span><span class="net-pill">AI Assist</span></div></div>
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">TBD</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">TBD</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Sam Sok (potential, JS team)</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">Greg Nolan (GDT, joining July)</div></div>
        <div class="field-row"><div class="field-label">Deliverables / Workflows</div><div class="field-value">OPORDs · FRAGORDs · Operational workflows</div></div>
        <div class="field-row"><div class="field-label">Expansion target</div><div class="field-value">6-month CLIN → full DTRA mid-year</div></div>
      </div>
      <div class="risk-wrap">
        <span class="risk-tag"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: funding / gov shutdown</span>
        <span class="risk-tag"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: docs feature readiness</span>
        <span class="risk-tag yellow"><i class="ti ti-alert-triangle" style="font-size:11px"></i>Risk: staffing not confirmed</span>
      </div>
    </div>

  </div><!-- /overview -->

  <!-- CALENDAR -->
  <div id="tab-calendar" class="tab-pane">
    <div class="cal-legend">
      <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#B5D4F4"></div>OPNAV</div>
      <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#9FE1CB"></div>OSW IBP</div>
      <div class="cal-legend-item"><div class="cal-legend-dot" style="background:#FAC775"></div>DTRA J3/5/8</div>
    </div>
    <div id="cal-grid" class="cal-grid"></div>
    <p style="font-size:11px;color:var(--text3);margin-top:8px">Click any highlighted day to see pilot details.</p>
  </div>

  <!-- OPNAV DETAIL -->
  <div id="tab-opnav" class="tab-pane">
    <div class="card-header">
      <div><div class="card-name"><i class="ti ti-anchor" style="margin-right:6px"></i>OPNAV N9I</div><div class="card-dates">18 May – 12 June 2025 · IL6</div></div>
      <div><div class="arr-badge blue">$TBD ARR</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-users"></i> People & ownership</div>
      <div class="fields-grid">
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">NOC / N33</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">N9 (champion + funding) · N3 · APHIT</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W · Chris T</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Will W · Chris T</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">Phil · Brandon</div></div>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-list-check"></i> Workflows & success criteria</div>
      <div class="phase-block"><div class="phase-label">Confirmed workflows</div><div class="phase-value">NpI and X · NOC / N33</div></div>
      <div class="success-tags">
        <span class="success-tag">Gov hands-on engagement</span>
        <span class="success-tag">NOC workflow completed</span>
        <span class="success-tag">N9 positive feedback</span>
        <span class="success-tag">Expansion brief delivered</span>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist</div>
      <ul class="checklist" id="opnav-cl"></ul>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence</div>
      <div class="phase-block"><div class="phase-label">Week 1</div><div class="phase-value">Kickoff brief · account confirmation · baseline workflow walk-through</div></div>
      <div class="phase-block"><div class="phase-label">Week 2</div><div class="phase-value">Mid-pilot sync with gov lead · issue triage · engagement pulse</div></div>
      <div class="phase-block"><div class="phase-label">End of pilot</div><div class="phase-value">AAR · outcomes summary · expansion brief to N9</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks</div>
      <div class="phase-block red"><div class="phase-label">Customer engagement</div><div class="phase-value">Limited hands-on during pilot, particularly in NOC. Mitigation: identify dedicated NOC POC pre-launch; schedule structured use blocks.</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-link"></i> Resources & docs</div>
      <div class="link-list">
        <div class="link-item"><i class="ti ti-file-text" style="color:var(--text2);flex-shrink:0"></i><div><div class="link-item-label">Pilot execution & AAR</div><a href="https://app.notion.com/p/onebrief/N9I-Pilot-Execution-and-AAR-097e3bddbaa883acb4ca014e0dcbe9f4" target="_blank">N9I Notion page ↗</a></div></div>
        <div class="link-item"><i class="ti ti-plus" style="color:var(--text3);flex-shrink:0"></i><div><div class="link-add">Add additional links in Notion</div></div></div>
      </div>
    </div>
  </div>

  <!-- OSW IBP DETAIL -->
  <div id="tab-osw" class="tab-pane">
    <div class="card-header">
      <div><div class="card-name"><i class="ti ti-briefcase" style="margin-right:6px"></i>OSW IBP</div><div class="card-dates">1 July 2025 · IL5 + AI Assist · 3 phases contracted</div></div>
      <div><div class="arr-badge green">$1.2M FY27</div></div>
    </div>
    <div class="callout" style="margin-bottom:1rem"><i class="ti ti-topology-star-3"></i><span><strong>OSW-wide opportunity</strong> — This pilot feeds a broader OSW goal. Related efforts: SecWar Front Office · P&amp;R re-engagement.</span></div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-users"></i> People & ownership</div>
      <div class="fields-grid">
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">TBD per phase</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">Ph3 IBP leadership (currently resistant)</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Phil</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">GDT – Scott</div></div>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-list-tree"></i> Phase breakdown</div>
      <div class="phase-block"><div class="phase-label">Phase 1</div><div class="phase-value">Industry Affairs</div></div>
      <div class="phase-block"><div class="phase-label">Phase 2</div><div class="phase-value">Mismatch is lead</div></div>
      <div class="phase-block"><div class="phase-label">Phase 3</div><div class="phase-value">Industrial Base Policy + Front Office</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-trophy"></i> Success criteria</div>
      <div class="success-tags">
        <span class="success-tag">Documents feature live by start</span>
        <span class="success-tag">Ph1 workflow complete</span>
        <span class="success-tag">Ph3 adoption / buy-in</span>
        <span class="success-tag">IBP-wide expansion brief delivered</span>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist</div>
      <ul class="checklist" id="osw-cl"></ul>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence</div>
      <div class="phase-block"><div class="phase-label">Pre-Phase 1</div><div class="phase-value">Account creation · training · Phil/Scott alignment call</div></div>
      <div class="phase-block"><div class="phase-label">Phase 1 mid-point</div><div class="phase-value">Workflow review · issue log · engagement pulse</div></div>
      <div class="phase-block"><div class="phase-label">Phase transition</div><div class="phase-value">Phase AAR · brief to next phase team · docs status check</div></div>
      <div class="phase-block"><div class="phase-label">End of Phase 3</div><div class="phase-value">IBP-wide expansion brief · FY27 ARR target discussion</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks</div>
      <div class="phase-block red"><div class="phase-label">Primary</div><div class="phase-value">Documents release date — must be live by Phase 1 start</div></div>
      <div class="phase-block red"><div class="phase-label">Phase 3</div><div class="phase-value">IBP leadership currently negative on adopting another digital tool. Requires early engagement and clear ROI narrative.</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-circles-relation"></i> Related OSW efforts</div>
      <div class="phase-block"><div class="phase-label">SecWar Front Office</div><div class="phase-value">Re-engagement opportunity — track status</div></div>
      <div class="phase-block"><div class="phase-label">P&amp;R</div><div class="phase-value">Re-engagement — add when active</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-link"></i> Resources & docs</div>
      <div class="link-list">
        <div class="link-item"><i class="ti ti-plus" style="color:var(--text3);flex-shrink:0"></i><div><div class="link-add">Add links in Notion</div></div></div>
      </div>
    </div>
  </div>

  <!-- DTRA DETAIL -->
  <div id="tab-dtra" class="tab-pane">
    <div class="card-header">
      <div><div class="card-name"><i class="ti ti-shield" style="margin-right:6px"></i>DTRA J3/5/8</div><div class="card-dates">1 Aug – 31 Oct 2025 · IL5/IL6/JWICS + AI Assist</div></div>
      <div><div class="arr-badge amber">$TBD ARR</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-users"></i> People & ownership</div>
      <div class="fields-grid">
        <div class="field-row"><div class="field-label">Gov lead(s)</div><div class="field-value">TBD</div></div>
        <div class="field-row"><div class="field-label">Decision makers</div><div class="field-value">TBD</div></div>
        <div class="field-row"><div class="field-label">Contracting / Sales</div><div class="field-value">Will W</div></div>
        <div class="field-row"><div class="field-label">CR lead</div><div class="field-value">Sam Sok (potential, JS team)</div></div>
        <div class="field-row"><div class="field-label">CR support</div><div class="field-value">Greg Nolan (GDT, joining July)</div></div>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-list-check"></i> Workflows & success criteria</div>
      <div class="phase-block"><div class="phase-label">Confirmed workflows</div><div class="phase-value">OPORDs · FRAGORDs · Operational planning workflows</div></div>
      <div class="success-tags">
        <span class="success-tag">OPORD workflow live</span>
        <span class="success-tag">FRAGORD workflow live</span>
        <span class="success-tag">6-month CLIN add-on initiated</span>
        <span class="success-tag">Full DTRA expansion brief delivered</span>
      </div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-clipboard-check"></i> Pre-pilot checklist</div>
      <ul class="checklist" id="dtra-cl"></ul>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-refresh"></i> Check-in cadence</div>
      <div class="phase-block"><div class="phase-label">Pre-launch (July)</div><div class="phase-value">Sam / Greg onboarding · account creation · stakeholder brief</div></div>
      <div class="phase-block"><div class="phase-label">Month 1 (August)</div><div class="phase-value">Kickoff · OPORD workflow walk-through · issue triage</div></div>
      <div class="phase-block"><div class="phase-label">Month 2 (September)</div><div class="phase-value">Mid-pilot sync · FRAGORD workflow · expansion conversation initiated</div></div>
      <div class="phase-block"><div class="phase-label">Month 3 (October)</div><div class="phase-value">AAR · CLIN add-on push · full expansion brief to DTRA leadership</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-alert-triangle"></i> Risks</div>
      <div class="phase-block red"><div class="phase-label">Funding</div><div class="phase-value">Gov shutdown risk — primary. Contingency plan needed.</div></div>
      <div class="phase-block red"><div class="phase-label">Documents feature</div><div class="phase-value">Must be online by start date. Track release timeline with product.</div></div>
      <div class="phase-block yellow"><div class="phase-label">Staffing</div><div class="phase-value">CR lead (Sam) and CR support (Greg) not yet confirmed. Finalize by July.</div></div>
    </div>
    <div class="detail-section">
      <div class="section-title"><i class="ti ti-link"></i> Resources & docs</div>
      <div class="link-list">
        <div class="link-item"><i class="ti ti-plus" style="color:var(--text3);flex-shrink:0"></i><div><div class="link-add">Add links in Notion</div></div></div>
      </div>
    </div>
  </div>

</div><!-- /wrap -->

<!-- POPUP -->
<div class="popup-overlay" id="popup-overlay" onclick="if(event.target.id==='popup-overlay')closePopup()">
  <div class="popup">
    <button class="popup-close" onclick="closePopup()"><i class="ti ti-x"></i></button>
    <div class="popup-title" id="popup-title"></div>
    <div id="popup-body"></div>
    <div class="popup-goto"><button onclick="gotoTab()">View full detail →</button></div>
  </div>
</div>

<script>
var currentPopupPilot = '';

function switchTab(id) {
  document.querySelectorAll('.tab-btn').forEach(function(b){b.classList.remove('active');});
  document.querySelectorAll('.tab-pane').forEach(function(p){p.classList.remove('active');});
  document.getElementById('tab-'+id).classList.add('active');
  var map = {overview:0,calendar:1,opnav:2,osw:3,dtra:4};
  document.querySelectorAll('.tab-btn')[map[id]].classList.add('active');
}

var PILOTS = {
  opnav: {name:'OPNAV N9I', dates:'18 May – 12 June 2025', net:'IL6', crLead:'Will W · Chris T', crSupport:'Phil · Brandon', govLead:'NOC / N33', wf:'NpI and X · NOC/N33', exp:'N9 · N3 · APHIT · Navy-wide FY27', risk:'Limited customer hands-on, esp. NOC'},
  osw: {name:'OSW IBP', dates:'1 July 2025, 3 phases', net:'IL5 + AI Assist', crLead:'Phil', crSupport:'GDT – Scott', govLead:'TBD per phase', wf:'Industry Affairs · Mismatch · Industrial Base Policy', exp:'Full IBP FY27 ($1.2M)', risk:'Docs release date · Phase 3 resistance'},
  dtra: {name:'DTRA J3/5/8', dates:'1 Aug – 31 Oct 2025', net:'IL5/IL6/JWICS + AI Assist', crLead:'Sam Sok (potential)', crSupport:'Greg Nolan (joining July)', govLead:'TBD', wf:'OPORDs · FRAGORDs · Ops workflows', exp:'6-month CLIN → full DTRA mid-year', risk:'Funding/shutdown · Docs feature · Staffing unconfirmed'}
};

function showPopup(pilot) {
  currentPopupPilot = pilot;
  var p = PILOTS[pilot];
  document.getElementById('popup-title').textContent = p.name + ' — ' + p.dates;
  document.getElementById('popup-body').innerHTML =
    '<div class="fields-grid" style="margin-bottom:8px">' +
    fRow('Networks', p.net) + fRow('Gov lead', p.govLead) +
    fRow('CR lead', p.crLead) + fRow('CR support', p.crSupport) +
    fRow('Workflows', p.wf) + fRow('Expansion', p.exp) +
    '</div><div class="risk-tag" style="font-size:11px"><i class="ti ti-alert-triangle" style="font-size:11px;margin-right:3px"></i>' + p.risk + '</div>';
  document.getElementById('popup-overlay').classList.add('open');
}

function fRow(label, val) {
  return '<div class="field-row"><div class="field-label">'+label+'</div><div class="field-value">'+val+'</div></div>';
}

function gotoTab() {
  closePopup();
  switchTab(currentPopupPilot);
}

function closePopup() {
  document.getElementById('popup-overlay').classList.remove('open');
}

var CL_ITEMS = [
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

function buildCL(pid) {
  var ul = document.getElementById(pid+'-cl');
  if (!ul) return;
  var saved = {};
  try { saved = JSON.parse(localStorage.getItem('ncr-cl-'+pid) || '{}'); } catch(e) {}
  ul.innerHTML = CL_ITEMS.map(function(item, i) {
    var chk = saved[i] ? 'checked' : '';
    var cls = saved[i] ? 'done' : '';
    return '<li class="'+cls+'"><input type="checkbox" id="'+pid+'-'+i+'" '+chk+' onchange="saveCL(\''+pid+'\','+i+',this.checked)"><label for="'+pid+'-'+i+'">'+item+'</label></li>';
  }).join('');
}

function saveCL(pid, i, val) {
  var saved = {};
  try { saved = JSON.parse(localStorage.getItem('ncr-cl-'+pid) || '{}'); } catch(e) {}
  saved[i] = val;
  try { localStorage.setItem('ncr-cl-'+pid, JSON.stringify(saved)); } catch(e) {}
  var li = document.getElementById(pid+'-'+i).parentElement;
  li.classList.toggle('done', val);
}

['opnav','osw','dtra'].forEach(buildCL);

// Calendar
var MONTHS = [
  {name:'May 2025', y:2025, m:4, days:31},
  {name:'Jun 2025', y:2025, m:5, days:30},
  {name:'Jul 2025', y:2025, m:6, days:31},
  {name:'Aug 2025', y:2025, m:7, days:31}
];

function pilotClass(y, m, d) {
  var dt = new Date(y, m, d);
  if (dt >= new Date(2025,4,18) && dt <= new Date(2025,5,12)) return 'opnav';
  if (dt >= new Date(2025,6,1)) return 'osw';
  if (dt >= new Date(2025,7,1) && dt <= new Date(2025,9,31)) return 'dtra';
  return '';
}

var grid = document.getElementById('cal-grid');
var DLABELS = ['S','M','T','W','T','F','S'];

MONTHS.forEach(function(mo) {
  var div = document.createElement('div');
  div.className = 'cal-month';
  var html = '<div class="cal-month-title">'+mo.name+'</div>';
  html += '<div class="cal-week-row">'+DLABELS.map(function(l){return '<div class="cal-day-label">'+l+'</div>';}).join('')+'</div>';
  var firstDay = new Date(mo.y, mo.m, 1).getDay();
  var cells = [];
  for (var i=0; i<firstDay; i++) cells.push('<div class="cal-day"></div>');
  for (var d=1; d<=mo.days; d++) {
    var pc = pilotClass(mo.y, mo.m, d);
    if (pc) {
      cells.push('<div class="cal-day '+pc+'" onclick="showPopup(\''+pc+'\')" title="'+d+'">'+d+'</div>');
    } else {
      cells.push('<div class="cal-day">'+d+'</div>');
    }
    if (cells.length === 7) {
      html += '<div class="cal-week-row">'+cells.join('')+'</div>';
      cells = [];
    }
  }
  if (cells.length) html += '<div class="cal-week-row">'+cells.join('')+'</div>';
  div.innerHTML = html;
  grid.appendChild(div);
});
</script>
</body>
</html>
