<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Far Rock Shine — Quote Calculator</title>
<link rel="manifest" href="./manifest.json">
<meta name="theme-color" content="#0f4a30">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="FRS Quotes">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --deep:#082e1e;--mid:#0f4a30;--teal:#1a9a6c;--bright:#2dd4a0;
  --gold:#e8c06a;--red:#e05a5a;--cream:#f4f0e8;--muted:#5a6e65;--r:14px;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
html,body{min-height:100vh;background:var(--deep);}
body{font-family:'DM Sans',sans-serif;color:#111;}

/* ── HEADER ── */
.app-header{
  background:linear-gradient(135deg,var(--deep),var(--mid));
  padding:18px 20px 14px;text-align:center;
  border-bottom:1px solid rgba(45,212,160,.2);
  position:sticky;top:0;z-index:50;
}
.header-logo{display:flex;align-items:center;justify-content:center;gap:10px;margin-bottom:6px;}
.star-icon{width:30px;height:30px;}
.brand-name{font-family:'Syne',sans-serif;font-size:19px;color:#fff;}
.brand-sub{font-size:10px;color:var(--bright);letter-spacing:2px;text-transform:uppercase;}
.badge-row{display:flex;gap:8px;justify-content:center;margin-top:6px;flex-wrap:wrap;}
.badge{font-size:9px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;
  padding:3px 10px;border-radius:20px;border:1px solid;}
.badge-insured{color:var(--gold);border-color:var(--gold);background:rgba(232,192,106,.1);}
.badge-bilingual{color:var(--bright);border-color:var(--bright);background:rgba(45,212,160,.1);}

/* ── MODE TOGGLE (Calculator / Agreement) ── */
.mode-bar{
  background:var(--deep);padding:8px 16px;
  display:flex;gap:6px;border-bottom:1px solid rgba(45,212,160,.1);
}
.mode-btn{
  flex:1;padding:9px;border-radius:10px;font-family:'DM Sans',sans-serif;
  font-size:12px;font-weight:700;border:none;cursor:pointer;transition:.2s;
  color:rgba(255,255,255,.45);background:rgba(255,255,255,.06);letter-spacing:.3px;
}
.mode-btn.active{background:var(--teal);color:#fff;}

/* ── PROGRESS ── */
.progress-wrap{background:var(--mid);padding:12px 20px 0;}
.step-dots{display:flex;gap:6px;justify-content:center;margin-bottom:10px;}
.dot{width:8px;height:8px;border-radius:50%;background:rgba(255,255,255,.2);transition:.3s;}
.dot.active{background:var(--bright);width:24px;border-radius:4px;}
.dot.done{background:var(--teal);}
.step-label{text-align:center;font-size:11px;font-weight:600;color:rgba(255,255,255,.5);
  letter-spacing:1.5px;text-transform:uppercase;padding-bottom:12px;}

/* ── SCREENS ── */
.screen{display:none;}
.screen.active{display:block;}
.app-body{background:var(--cream);min-height:calc(100vh - 200px);padding:20px 16px 130px;}

/* ── STEP PANELS ── */
.step-panel{display:none;}
.step-panel.active{display:block;}
.step-title{font-family:'Syne',sans-serif;font-size:22px;font-weight:700;color:var(--deep);margin-bottom:4px;}
.step-sub{font-size:13px;color:var(--muted);margin-bottom:18px;}

/* ── CHOICE CARDS ── */
.choice-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.choice-grid.single-col{grid-template-columns:1fr;}
.choice-card{
  background:#fff;border:2px solid #e0dbd0;border-radius:var(--r);
  padding:14px 12px;cursor:pointer;transition:.2s;
  display:flex;align-items:center;gap:10px;
}
.choice-card:active{transform:scale(.97);}
.choice-card.selected{border-color:var(--teal);background:rgba(26,154,108,.06);}
.choice-icon{font-size:20px;flex-shrink:0;}
.choice-text{flex:1;min-width:0;}
.choice-name{font-weight:600;font-size:13px;color:var(--deep);}
.choice-name-es{font-size:10px;color:var(--muted);font-style:italic;}
.choice-check{width:20px;height:20px;border-radius:50%;border:2px solid #ccc;
  flex-shrink:0;display:flex;align-items:center;justify-content:center;transition:.2s;}
.choice-card.selected .choice-check{background:var(--teal);border-color:var(--teal);}
.checkmark{display:none;color:#fff;font-size:11px;font-weight:700;}
.choice-card.selected .checkmark{display:block;}

/* ── SERVICE CARDS ── */
.svc-card{
  background:#fff;border:2px solid #e0dbd0;border-radius:var(--r);
  padding:14px 16px;cursor:pointer;transition:.2s;
  display:flex;align-items:center;justify-content:space-between;grid-column:1/-1;
}
.svc-card.selected{border-color:var(--teal);background:rgba(26,154,108,.06);}
.svc-left{flex:1;}
.svc-name{font-weight:600;font-size:14px;color:var(--deep);}
.svc-name-es{font-size:11px;color:var(--muted);font-style:italic;}
.svc-price{font-family:'Syne',sans-serif;font-size:18px;font-weight:700;color:var(--teal);white-space:nowrap;margin-left:12px;}

/* ── SECTION HEADERS ── */
.section-header{
  font-size:10px;font-weight:700;letter-spacing:2px;text-transform:uppercase;
  color:var(--muted);margin:20px 0 10px;padding-bottom:6px;border-bottom:1px solid #e0dbd0;
}

/* ── ADDON ITEMS ── */
.addon-list{display:flex;flex-direction:column;gap:8px;}
.addon-item{
  background:#fff;border:2px solid #e0dbd0;border-radius:var(--r);
  padding:12px 14px;cursor:pointer;transition:.2s;
  display:flex;align-items:center;gap:12px;
}
.addon-item.selected{border-color:var(--teal);background:rgba(26,154,108,.06);}
.addon-toggle{
  width:22px;height:22px;border-radius:6px;border:2px solid #ccc;
  flex-shrink:0;display:flex;align-items:center;justify-content:center;
  font-size:13px;font-weight:700;color:#fff;transition:.2s;min-width:22px;
}
.addon-item.selected .addon-toggle{background:var(--teal);border-color:var(--teal);}
.addon-text{flex:1;min-width:0;}
.addon-name{font-weight:600;font-size:13px;color:var(--deep);}
.addon-name-es{font-size:10px;color:var(--muted);font-style:italic;}
.addon-price{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;color:var(--teal);white-space:nowrap;flex-shrink:0;}
.addon-note{font-size:10px;color:var(--red);font-weight:500;margin-top:2px;}

/* ── PROMO ── */
.promo-box{
  background:linear-gradient(135deg,var(--mid),var(--deep));
  border-radius:var(--r);padding:24px;margin-bottom:16px;text-align:center;
}
.promo-pct{font-family:'Syne',sans-serif;font-size:52px;font-weight:800;color:var(--bright);line-height:1;}
.promo-label{font-size:16px;font-weight:600;color:#fff;margin-top:4px;}
.promo-label-es{font-size:12px;color:rgba(255,255,255,.6);font-style:italic;}
.promo-note{font-size:11px;color:rgba(255,255,255,.5);margin-top:6px;}
.promo-toggle{
  background:#fff;border:2px solid #e0dbd0;border-radius:var(--r);
  padding:14px 16px;cursor:pointer;transition:.2s;
  display:flex;align-items:center;justify-content:space-between;gap:12px;
}
.promo-toggle.active{border-color:var(--gold);background:rgba(232,192,106,.06);}
.promo-toggle-text{font-weight:600;font-size:14px;color:var(--deep);}
.promo-toggle-sub{font-size:11px;color:var(--muted);}
.promo-switch{width:44px;height:24px;background:#ddd;border-radius:12px;position:relative;transition:.3s;flex-shrink:0;}
.promo-toggle.active .promo-switch{background:var(--gold);}
.promo-knob{width:18px;height:18px;background:#fff;border-radius:50%;
  position:absolute;top:3px;left:3px;transition:.3s;box-shadow:0 1px 4px rgba(0,0,0,.2);}
.promo-toggle.active .promo-knob{left:23px;}
.recurring-note{
  background:#fff;border-radius:var(--r);padding:14px;margin-top:12px;
  border-left:3px solid var(--bright);font-size:12px;color:var(--muted);
}

/* ── BOTTOM BAR ── */
.bottom-bar{
  position:fixed;bottom:0;left:0;right:0;
  background:linear-gradient(135deg,var(--mid),var(--deep));
  padding:12px 16px;box-shadow:0 -4px 20px rgba(0,0,0,.3);z-index:50;
}
.total-row{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:10px;}
.total-label{font-size:12px;color:rgba(255,255,255,.6);font-weight:500;}
.total-right{display:flex;align-items:baseline;gap:8px;}
.total-amount{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:var(--bright);}
.total-original{font-size:13px;color:rgba(255,255,255,.4);text-decoration:line-through;}
.btn-row{display:flex;gap:10px;}
.btn{flex:1;padding:14px;border-radius:12px;font-family:'DM Sans',sans-serif;
  font-size:14px;font-weight:700;border:none;cursor:pointer;transition:.2s;}
.btn:active{transform:scale(.97);}
.btn-back{background:rgba(255,255,255,.12);color:#fff;}
.btn-next{background:var(--bright);color:var(--deep);}
.btn-next:disabled{opacity:.4;cursor:not-allowed;}
.btn-copy{background:var(--gold);color:var(--deep);flex:2;}
.btn-reset{background:rgba(255,255,255,.12);color:#fff;flex:1;}
.btn-agreement{background:#e8c06a;color:var(--deep);flex:1;}

/* ── TOAST ── */
.toast{
  position:fixed;top:80px;left:50%;transform:translateX(-50%) translateY(-20px);
  background:var(--deep);color:var(--bright);padding:10px 20px;
  border-radius:20px;font-size:13px;font-weight:600;
  border:1px solid var(--bright);opacity:0;transition:.3s;pointer-events:none;z-index:999;white-space:nowrap;
}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}

/* ══════════════════════════════════════
   JOB AGREEMENT SCREEN
══════════════════════════════════════ */
.agreement-body{background:var(--cream);min-height:calc(100vh - 120px);padding:16px 16px 140px;}

/* Job summary card */
.job-summary{
  background:linear-gradient(135deg,var(--mid),var(--deep));
  border-radius:var(--r);padding:18px;margin-bottom:16px;
}
.job-summary-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;
  color:var(--bright);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px;}
.job-row{display:flex;justify-content:space-between;align-items:baseline;
  padding:5px 0;border-bottom:1px solid rgba(255,255,255,.08);}
.job-row:last-child{border-bottom:none;}
.job-key{font-size:11px;color:rgba(255,255,255,.5);}
.job-val{font-size:13px;font-weight:600;color:#fff;}
.job-total-val{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--bright);}

/* Client info inputs */
.field-group{margin-bottom:14px;}
.field-label{font-size:11px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;
  color:var(--muted);margin-bottom:6px;}
.field-label-es{font-size:10px;color:var(--muted);font-style:italic;font-weight:400;}
.field-input{
  width:100%;padding:12px 14px;border-radius:10px;
  border:2px solid #e0dbd0;background:#fff;
  font-family:'DM Sans',sans-serif;font-size:14px;color:var(--deep);
  outline:none;transition:.2s;
}
.field-input:focus{border-color:var(--teal);}

/* Advisory checklist */
.advisory-card{
  background:#fff;border-radius:var(--r);padding:16px;margin-bottom:14px;
  border-left:4px solid var(--gold);
}
.advisory-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;
  color:var(--deep);margin-bottom:4px;}
.advisory-sub{font-size:11px;color:var(--muted);font-style:italic;margin-bottom:12px;}
.advisory-item{
  display:flex;align-items:flex-start;gap:10px;padding:10px 0;
  border-bottom:1px solid #f0ebe0;cursor:pointer;
}
.advisory-item:last-child{border-bottom:none;}
.adv-check{
  width:22px;height:22px;border-radius:6px;border:2px solid #ccc;
  flex-shrink:0;display:flex;align-items:center;justify-content:center;
  font-size:12px;font-weight:700;color:#fff;transition:.2s;margin-top:1px;
}
.advisory-item.checked .adv-check{background:var(--teal);border-color:var(--teal);}
.adv-text{flex:1;}
.adv-main{font-size:13px;font-weight:600;color:var(--deep);}
.adv-sub{font-size:11px;color:var(--muted);margin-top:2px;line-height:1.4;}

/* Policy text */
.policy-card{
  background:#fff;border-radius:var(--r);padding:16px;margin-bottom:14px;
  border:1px solid #e0dbd0;
}
.policy-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;
  color:var(--deep);margin-bottom:12px;padding-bottom:8px;
  border-bottom:2px solid var(--teal);}
.policy-section{margin-bottom:12px;}
.policy-section-title{font-size:11px;font-weight:700;letter-spacing:1px;
  text-transform:uppercase;color:var(--teal);margin-bottom:4px;}
.policy-text{font-size:12px;color:#444;line-height:1.6;}

/* Signature pad */
.sig-card{
  background:#fff;border-radius:var(--r);padding:16px;margin-bottom:14px;
  border:1px solid #e0dbd0;
}
.sig-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;
  color:var(--deep);margin-bottom:4px;}
.sig-sub{font-size:11px;color:var(--muted);font-style:italic;margin-bottom:10px;}
.sig-canvas-wrap{
  border:2px dashed #ccc;border-radius:10px;background:#fafaf8;
  position:relative;overflow:hidden;
}
.sig-canvas-wrap.has-sig{border-color:var(--teal);border-style:solid;}
#sigCanvas{display:block;width:100%;height:140px;cursor:crosshair;touch-action:none;}
.sig-placeholder{
  position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);
  font-size:13px;color:#bbb;pointer-events:none;text-align:center;
}
.sig-placeholder.hidden{display:none;}
.sig-actions{display:flex;justify-content:flex-end;margin-top:8px;}
.btn-clear-sig{
  font-size:11px;font-weight:600;color:var(--red);background:none;border:none;
  cursor:pointer;padding:4px 8px;
}

/* Agreement bottom bar */
.agr-bottom{
  position:fixed;bottom:0;left:0;right:0;
  background:linear-gradient(135deg,var(--mid),var(--deep));
  padding:12px 16px;box-shadow:0 -4px 20px rgba(0,0,0,.3);z-index:50;
}
.agr-status{font-size:11px;color:rgba(255,255,255,.5);margin-bottom:8px;text-align:center;}
.agr-status.ready{color:var(--bright);font-weight:600;}
.agr-btn-row{display:flex;gap:10px;}
.btn-agr-back{background:rgba(255,255,255,.12);color:#fff;flex:1;}
.btn-agr-save{background:var(--bright);color:var(--deep);flex:2;font-weight:700;}
.btn-agr-save:disabled{opacity:.4;cursor:not-allowed;}
</style>
</head>
<body>

<!-- ═══ HEADER (always visible) ═══ -->
<div class="app-header">
  <div class="header-logo">
    <svg class="star-icon" viewBox="0 0 40 40" fill="none">
      <polygon points="20,3 25,14 37,15.5 28,24 30.5,37 20,31 9.5,37 12,24 3,15.5 15,14"
        fill="none" stroke="#2dd4a0" stroke-width="2"/>
      <polygon points="20,8 24,17 33,18 26,25 28,34 20,30 12,34 14,25 7,18 16,17" fill="#1a9a6c"/>
    </svg>
    <div>
      <div class="brand-name">Far Rock Shine</div>
      <div class="brand-sub" id="headerSub">Quote Calculator</div>
    </div>
  </div>
  <div class="badge-row">
    <span class="badge badge-insured">✓ Insured &amp; Bonded</span>
    <span class="badge badge-bilingual">Bilingual · Bilingüe</span>
  </div>
</div>

<!-- ═══ MODE TOGGLE ═══ -->
<div class="mode-bar">
  <button class="mode-btn active" id="modeCalc" onclick="switchMode('calc')">📋 Quote Calculator</button>
  <button class="mode-btn" id="modeAgr" onclick="switchMode('agr')">✍️ Job Agreement</button>
</div>

<!-- ════════════════════════════════════
     SCREEN 1 — QUOTE CALCULATOR
════════════════════════════════════ -->
<div class="screen active" id="screenCalc">

  <div class="progress-wrap">
    <div class="step-dots">
      <div class="dot active" id="dot0"></div>
      <div class="dot" id="dot1"></div>
      <div class="dot" id="dot2"></div>
      <div class="dot" id="dot3"></div>
      <div class="dot" id="dot4"></div>
    </div>
    <div class="step-label" id="stepLabel">Step 1 of 5 · Tipo de propiedad</div>
  </div>

  <div class="app-body">

    <!-- STEP 1: Property Type -->
    <div class="step-panel active" id="step0">
      <div class="step-title">Property Type</div>
      <div class="step-sub">Tipo de propiedad</div>
      <div class="choice-grid" id="typeGrid">
        <div class="choice-card" onclick="selectType('apt',this)">
          <div class="choice-icon">🏢</div>
          <div class="choice-text">
            <div class="choice-name">Apartment</div>
            <div class="choice-name-es">Apartamento</div>
          </div>
          <div class="choice-check"><span class="checkmark">✓</span></div>
        </div>
        <div class="choice-card" onclick="selectType('home',this)">
          <div class="choice-icon">🏠</div>
          <div class="choice-text">
            <div class="choice-name">House / Home</div>
            <div class="choice-name-es">Casa</div>
          </div>
          <div class="choice-check"><span class="checkmark">✓</span></div>
        </div>
        <div class="choice-card" onclick="selectType('commercial',this)">
          <div class="choice-icon">🏪</div>
          <div class="choice-text">
            <div class="choice-name">Commercial</div>
            <div class="choice-name-es">Comercial</div>
          </div>
          <div class="choice-check"><span class="checkmark">✓</span></div>
        </div>
        <div class="choice-card" onclick="selectType('airbnb',this)">
          <div class="choice-icon">🏖️</div>
          <div class="choice-text">
            <div class="choice-name">Airbnb / Rental</div>
            <div class="choice-name-es">Renta vacacional</div>
          </div>
          <div class="choice-check"><span class="checkmark">✓</span></div>
        </div>
      </div>
    </div>

    <!-- STEP 2: Size -->
    <div class="step-panel" id="step1">
      <div class="step-title">Property Size</div>
      <div class="step-sub">Tamaño de la propiedad</div>
      <div class="choice-grid single-col" id="sizeGrid"></div>
    </div>

    <!-- STEP 3: Service -->
    <div class="step-panel" id="step2">
      <div class="step-title">Select Service</div>
      <div class="step-sub">Elige el servicio</div>
      <div class="choice-grid single-col" id="serviceGrid"></div>
    </div>

    <!-- STEP 4: Add-ons -->
    <div class="step-panel" id="step3">
      <div class="step-title">Add-Ons</div>
      <div class="step-sub">Servicios adicionales · optional</div>
      <div id="addonList"></div>
    </div>

    <!-- STEP 5: Promo -->
    <div class="step-panel" id="step4">
      <div class="step-title">Promotions</div>
      <div class="step-sub">Descuentos y promociones</div>
      <div class="promo-box">
        <div class="promo-pct">20%</div>
        <div class="promo-label">OFF Your First Clean!</div>
        <div class="promo-label-es">¡Descuento en tu primera limpieza!</div>
        <div class="promo-note">Mention this when booking · Menciona esto al reservar</div>
      </div>
      <div class="promo-toggle" id="firstCleanToggle" onclick="togglePromo('first')">
        <div>
          <div class="promo-toggle-text">🎉 First Clean Discount (20% off)</div>
          <div class="promo-toggle-sub">New client · Nuevo cliente</div>
        </div>
        <div class="promo-switch"><div class="promo-knob"></div></div>
      </div>
      <div class="promo-toggle" style="margin-top:10px;" id="recurringToggle" onclick="togglePromo('recurring')">
        <div>
          <div class="promo-toggle-text">🔁 Recurring Client (10% off)</div>
          <div class="promo-toggle-sub">After 3 cleanings · Después de 3 limpiezas</div>
        </div>
        <div class="promo-switch"><div class="promo-knob"></div></div>
      </div>
      <div class="recurring-note" style="margin-top:14px;">
        💡 <strong>Tip:</strong> Book regular cleanings and save 10% from your 4th visit onward.
      </div>
    </div>

  </div><!-- /app-body -->

  <!-- CALC BOTTOM BAR -->
  <div class="bottom-bar">
    <div class="total-row">
      <div class="total-label">Estimated Total · Total Estimado</div>
      <div class="total-right">
        <div class="total-original" id="originalDisplay"></div>
        <div class="total-amount" id="totalDisplay">$0</div>
      </div>
    </div>
    <div class="btn-row" id="btnRow">
      <button class="btn btn-next" id="btnNext" onclick="nextStep()" disabled>Next →</button>
    </div>
  </div>

</div><!-- /screenCalc -->


<!-- ════════════════════════════════════
     SCREEN 2 — JOB AGREEMENT
════════════════════════════════════ -->
<div class="screen" id="screenAgr">
  <div class="agreement-body">

    <!-- Job summary pulled from calculator -->
    <div class="job-summary" id="jobSummaryCard">
      <div class="job-summary-title">📋 Job Summary · Resumen del Trabajo</div>
      <div id="jobSummaryRows">
        <div class="job-row">
          <span class="job-key">Service</span>
          <span class="job-val" id="sumService">—</span>
        </div>
        <div class="job-row">
          <span class="job-key">Add-Ons</span>
          <span class="job-val" id="sumAddons">None</span>
        </div>
        <div class="job-row">
          <span class="job-key">Discount</span>
          <span class="job-val" id="sumDiscount">None</span>
        </div>
        <div class="job-row">
          <span class="job-key">Agreed Total</span>
          <span class="job-total-val" id="sumTotal">$0</span>
        </div>
      </div>
    </div>

    <!-- Client Info -->
    <div class="section-header" style="margin-top:0;">Client Information · Información del Cliente</div>

    <div class="field-group">
      <div class="field-label">Client Full Name <span class="field-label-es">/ Nombre completo</span></div>
      <input class="field-input" id="clientName" type="text" placeholder="Full name · Nombre completo" oninput="checkAgrReady()">
    </div>
    <div class="field-group">
      <div class="field-label">Property Address <span class="field-label-es">/ Dirección</span></div>
      <input class="field-input" id="clientAddress" type="text" placeholder="Address · Dirección" oninput="checkAgrReady()">
    </div>
    <div class="field-group">
      <div class="field-label">Phone / Email <span class="field-label-es">/ Teléfono o correo</span></div>
      <input class="field-input" id="clientContact" type="text" placeholder="Phone or email · Teléfono o correo" oninput="checkAgrReady()">
    </div>
    <div class="field-group">
      <div class="field-label">Date &amp; Time <span class="field-label-es">/ Fecha y hora</span></div>
      <input class="field-input" id="jobDateTime" type="text" readonly>
    </div>

    <!-- ⚠ VALUABLES ADVISORY -->
    <div class="advisory-card">
      <div class="advisory-title">⚠️ Valuables Advisory · Aviso sobre Objetos de Valor</div>
      <div class="advisory-sub">Client must initial each item by tapping · El cliente debe confirmar cada punto</div>

      <div class="advisory-item" onclick="toggleAdvisory(this)">
        <div class="adv-check"></div>
        <div class="adv-text">
          <div class="adv-main">Cash, Jewelry &amp; Financial Items</div>
          <div class="adv-sub">I have removed or secured all cash, jewelry, credit cards, checkbooks, and financial documents from areas to be cleaned.</div>
        </div>
      </div>
      <div class="advisory-item" onclick="toggleAdvisory(this)">
        <div class="adv-check"></div>
        <div class="adv-text">
          <div class="adv-main">Electronics &amp; Devices</div>
          <div class="adv-sub">I have secured or removed laptops, tablets, phones, cameras, and other electronics from cleaning areas.</div>
        </div>
      </div>
      <div class="advisory-item" onclick="toggleAdvisory(this)">
        <div class="adv-check"></div>
        <div class="adv-text">
          <div class="adv-main">Medications &amp; Personal Items</div>
          <div class="adv-sub">I have secured all medications, prescriptions, and personal health items away from work areas.</div>
        </div>
      </div>
      <div class="advisory-item" onclick="toggleAdvisory(this)">
        <div class="adv-check"></div>
        <div class="adv-text">
          <div class="adv-main">Sentimental &amp; Collectible Items</div>
          <div class="adv-sub">I have secured irreplaceable items of sentimental or collectible value from areas to be cleaned.</div>
        </div>
      </div>
      <div class="advisory-item" onclick="toggleAdvisory(this)">
        <div class="adv-check"></div>
        <div class="adv-text">
          <div class="adv-main">Pre-Existing Damage Acknowledged</div>
          <div class="adv-sub">I confirm that any pre-existing damage (stains, chips, scratches, wear) in the property has been noted and Far Rock Shine is not responsible for these conditions.</div>
        </div>
      </div>
    </div>

    <!-- POLICY -->
    <div class="policy-card">
      <div class="policy-title">📄 Pre-Service Agreement · Acuerdo de Servicio</div>

      <div class="policy-section">
        <div class="policy-section-title">1. Personal Property &amp; Valuables</div>
        <div class="policy-text">Far Rock Shine and its staff are not liable for loss, theft, or damage to any unsecured personal property, cash, jewelry, electronics, medications, or documents left in cleaning areas. Client accepts full responsibility for securing all valuables prior to service.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">2. Staff Conduct Policy</div>
        <div class="policy-text">Far Rock Shine staff are strictly prohibited from opening drawers, cabinets, closets, or containers unless specifically instructed in writing. Staff will not handle personal belongings, financial items, medications, or documents. Any concerns about staff conduct must be reported immediately to (929) 803-6022.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">3. Pre-Existing Conditions</div>
        <div class="policy-text">Far Rock Shine is not responsible for pre-existing damage including permanent stains, chips, scratches, cracks, or wear present before service. Client confirms they have inspected and acknowledged all pre-existing conditions by signing this agreement.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">4. Limitation of Liability</div>
        <div class="policy-text">Far Rock Shine's maximum liability for any claim arising from services provided is strictly limited to the total cost of the service performed. We are not liable for indirect, incidental, consequential, or punitive damages of any kind.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">5. Fraud &amp; False Claims Prevention</div>
        <div class="policy-text">Any fraudulent claims regarding theft, property damage, or service quality are taken seriously. This signed agreement, including timestamp and client acknowledgment, constitutes a legal record of the pre-service condition. False or fraudulent claims will be reported to appropriate authorities and may result in civil action.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">6. Access &amp; Safe Conditions</div>
        <div class="policy-text">Client agrees to provide safe, unobstructed access to all areas to be cleaned. Client is responsible for securing pets and removing any hazardous materials from work areas prior to service.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">7. Payment Terms</div>
        <div class="policy-text">Payment is due in full upon completion of service. Accepted methods: Zelle, Venmo, Cash App, Apple Pay, Cash. Withheld payment without valid cause may result in collection action.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">8. Satisfaction &amp; Concerns</div>
        <div class="policy-text">Any concerns about service quality must be communicated within 24 hours of service completion. Far Rock Shine will address legitimate concerns at no additional charge. Concerns raised after 24 hours may not be eligible for remedy.</div>
      </div>

      <div class="policy-section">
        <div class="policy-section-title">9. Photo Documentation</div>
        <div class="policy-text">Far Rock Shine may photograph work areas before and after service for internal quality assurance records only. Photos will not be shared publicly without written client consent.</div>
      </div>

      <div style="margin-top:14px;padding:12px;background:#f9f5ee;border-radius:10px;
        font-size:11px;color:#666;line-height:1.6;border-left:3px solid var(--gold);">
        <strong>By signing below, client confirms:</strong> They have read and understood all terms above, completed the valuables advisory checklist, and agree to the full Pre-Service Agreement. This document is valid and binding upon signature.
        <br><br>
        <em>Al firmar abajo, el cliente confirma que ha leído, entendido y acepta todos los términos de este acuerdo.</em>
      </div>
    </div>

    <!-- SIGNATURE PAD -->
    <div class="sig-card">
      <div class="sig-title">✍️ Client Signature · Firma del Cliente</div>
      <div class="sig-sub">Sign with your finger in the box below · Firme con su dedo</div>
      <div class="sig-canvas-wrap" id="sigWrap">
        <canvas id="sigCanvas"></canvas>
        <div class="sig-placeholder" id="sigPlaceholder">
          <div style="font-size:28px;margin-bottom:4px;">✍️</div>
          Sign here · Firme aquí
        </div>
      </div>
      <div class="sig-actions">
        <button class="btn-clear-sig" onclick="clearSig()">✕ Clear / Borrar</button>
      </div>
    </div>

  </div><!-- /agreement-body -->

  <!-- AGREEMENT BOTTOM BAR -->
  <div class="agr-bottom">
    <div class="agr-status" id="agrStatus">Complete all fields, advisories &amp; signature to save</div>
    <div class="agr-btn-row">
      <button class="btn btn-agr-back" onclick="switchMode('calc')">← Back</button>
      <button class="btn btn-agr-save" id="btnSaveAgr" onclick="saveAgreement()" disabled>
        📋 Copy Agreement · Copiar
      </button>
    </div>
  </div>

</div><!-- /screenAgr -->

<!-- TOAST -->
<div class="toast" id="toast">✓ Copied! / ¡Copiado!</div>

<script>
// ══════════════════════════════════════════
// CALCULATOR DATA
// ══════════════════════════════════════════
const state = {
  step:0, type:null, size:null, service:null,
  addons:new Set(), promos:new Set()
};
const STEP_LABELS = [
  'Step 1 of 5 · Tipo de propiedad',
  'Step 2 of 5 · Tamaño',
  'Step 3 of 5 · Servicio',
  'Step 4 of 5 · Adicionales (opcional)',
  'Step 5 of 5 · Descuentos',
];
const SIZES = {
  apt:[
    {id:'s1br',  name:'Studio / 1 Bedroom',         es:'Estudio / 1 Habitación'},
    {id:'s23br', name:'2–3 Bedrooms',                es:'2–3 Habitaciones'},
  ],
  home:[
    {id:'h23',   name:'Small Home (2–3 BR)',         es:'Casa pequeña'},
    {id:'h4',    name:'Medium Home (4 BR)',           es:'Casa mediana'},
    {id:'h5p',   name:'Large Home (5+ BR)',           es:'Casa grande'},
  ],
  commercial:[
    {id:'c_office', name:'Small Office (≤1000 sqft)',es:'Oficina pequeña'},
    {id:'c_retail', name:'Retail Storefront',         es:'Tienda / Local'},
    {id:'c_resto',  name:'Restaurant / Food',         es:'Restaurante'},
  ],
  airbnb:[
    {id:'ab_studio', name:'Studio / 1 BR Unit',      es:'Estudio / 1 hab.'},
    {id:'ab_23',     name:'2–3 BR Unit',              es:'2–3 hab.'},
    {id:'ab_4p',     name:'4+ BR / Large Unit',       es:'4+ hab.'},
  ]
};
const SERVICES = {
  apt:{
    s1br:[
      {id:'reg',       name:'Regular Clean',          es:'Limpieza Regular',    price:85},
      {id:'deep',      name:'Deep Clean',              es:'Limpieza Profunda',   price:140},
      {id:'moveinout', name:'Move-In / Move-Out',      es:'Entrada / Salida',    price:160},
      {id:'kitchen',   name:'Kitchen & Bathrooms Only',es:'Cocina y Baños',      price:90},
    ],
    s23br:[
      {id:'reg',       name:'Regular Clean',          es:'Limpieza Regular',    price:120},
      {id:'deep',      name:'Deep Clean',              es:'Limpieza Profunda',   price:195},
      {id:'moveinout', name:'Move-In / Move-Out',      es:'Entrada / Salida',    price:220},
      {id:'kitchen',   name:'Kitchen & Bathrooms Only',es:'Cocina y Baños',      price:110},
      {id:'holiday',   name:'Holiday Cleanup',         es:'Limpieza de Fiestas', price:150},
    ]
  },
  home:{
    h23:[
      {id:'reg',       name:'Regular Clean',               es:'Limpieza Regular',    price:140},
      {id:'deep',      name:'Deep Clean',                   es:'Limpieza Profunda',   price:220},
      {id:'moveinout', name:'Move-In / Move-Out',           es:'Entrada / Salida',    price:250},
      {id:'postbeach', name:'Post-Beach / Airbnb Turnover', es:'Rentals de Playa',    price:185},
      {id:'holiday',   name:'Holiday Cleanup',              es:'Limpieza de Fiestas', price:175},
    ],
    h4:[
      {id:'reg',       name:'Regular Clean',               es:'Limpieza Regular',    price:175},
      {id:'deep',      name:'Deep Clean',                   es:'Limpieza Profunda',   price:275},
      {id:'moveinout', name:'Move-In / Move-Out',           es:'Entrada / Salida',    price:310},
      {id:'postbeach', name:'Post-Beach / Airbnb Turnover', es:'Rentals de Playa',    price:230},
      {id:'holiday',   name:'Holiday Cleanup',              es:'Limpieza de Fiestas', price:210},
    ],
    h5p:[
      {id:'reg',       name:'Regular Clean',               es:'Limpieza Regular',    price:210},
      {id:'deep',      name:'Deep Clean',                   es:'Limpieza Profunda',   price:330},
      {id:'moveinout', name:'Move-In / Move-Out',           es:'Entrada / Salida',    price:375},
      {id:'postbeach', name:'Post-Beach / Airbnb Turnover', es:'Rentals de Playa',    price:280},
      {id:'holiday',   name:'Holiday Cleanup',              es:'Limpieza de Fiestas', price:250},
    ]
  },
  commercial:{
    c_office:[
      {id:'reg',       name:'Regular Clean',      es:'Limpieza Regular',   price:120},
      {id:'deep',      name:'Deep Clean',          es:'Limpieza Profunda',  price:195},
      {id:'postevent', name:'Post-Event Cleanup',  es:'Después del Evento', price:150},
      {id:'periodic',  name:'Periodic Deep Clean', es:'Limpieza Periódica', price:175},
    ],
    c_retail:[
      {id:'reg',       name:'Regular Clean',      es:'Limpieza Regular',   price:140},
      {id:'deep',      name:'Deep Clean',          es:'Limpieza Profunda',  price:220},
      {id:'postevent', name:'Post-Event Cleanup',  es:'Después del Evento', price:175},
    ],
    c_resto:[
      {id:'reg',       name:'Regular Clean',      es:'Limpieza Regular',   price:180},
      {id:'deep',      name:'Deep Clean',          es:'Limpieza Profunda',  price:280},
      {id:'postevent', name:'Post-Event Cleanup',  es:'Después del Evento', price:220},
      {id:'periodic',  name:'Periodic Deep Clean', es:'Limpieza Periódica', price:250},
    ]
  },
  airbnb:{
    ab_studio:[
      {id:'turnover',  name:'Airbnb Turnover Clean', es:'Limpieza Airbnb',  price:110},
      {id:'deep',      name:'Deep Clean',             es:'Limpieza Profunda',price:150},
      {id:'postbeach', name:'Post-Beach Turnover',    es:'Después de Playa', price:120},
    ],
    ab_23:[
      {id:'turnover',  name:'Airbnb Turnover Clean', es:'Limpieza Airbnb',  price:155},
      {id:'deep',      name:'Deep Clean',             es:'Limpieza Profunda',price:200},
      {id:'postbeach', name:'Post-Beach Turnover',    es:'Después de Playa', price:165},
    ],
    ab_4p:[
      {id:'turnover',  name:'Airbnb Turnover Clean', es:'Limpieza Airbnb',  price:210},
      {id:'deep',      name:'Deep Clean',             es:'Limpieza Profunda',price:280},
      {id:'postbeach', name:'Post-Beach Turnover',    es:'Después de Playa', price:230},
    ]
  }
};
const ADDONS_STANDARD = [
  {id:'oven',       name:'Oven Deep Clean',                  es:'Limpieza de Horno',               price:35},
  {id:'fridge',     name:'Fridge Deep Clean',                es:'Limpieza de Nevera',              price:30},
  {id:'windows',    name:'Interior Windows (per room)',      es:'Ventanas interiores',             price:15},
  {id:'laundry',    name:'Laundry — Wash & Fold (per load)', es:'Lavandería (por carga)',           price:20},
  {id:'extrabath',  name:'Extra Bathroom',                   es:'Baño adicional',                  price:35},
  {id:'clutter',    name:'Heavy Clutter Removal',            es:'Remoción de desorden',            price:45},
  {id:'patio',      name:'Patio Sweep & Tidy',               es:'Limpieza de patio',               price:25},
  {id:'rush',       name:'Rush Booking (same day)',          es:'Reserva de emergencia',           price:40},
  {id:'stainless',  name:'Stainless Steel Appliance Polish', es:'Pulido de acero inoxidable',      price:20},
  {id:'goo',        name:'Sticker & Adhesive Removal',       es:'Remoción de pegamento',           price:30},
  {id:'upholstery', name:'Upholstery / Sofa Deep Clean',     es:'Limpieza de tapicería/sofá',      price:80},
  {id:'petstain',   name:'Pet Stain & Odor Treatment',       es:'Manchas y olores de mascotas',    price:35},
  {id:'mold',       name:'Mold & Mildew Surface Treatment',  es:'Tratamiento de moho (superficie)',price:45,
    note:'Tile & grout only · Solo baldosas y juntas'},
];
const ADDONS_PREMIUM = [
  {id:'pressure',   name:'Patio / Deck Pressure Wash',        es:'Lavado a presión',              price:110},
  {id:'acsplit',    name:'Mini-Split AC Cleaning (per unit)', es:'Limpieza de A/C split',          price:100,
    note:'Coil & filter only — no electrical · Solo bobina/filtro'},
];
const ALL_ADDONS = [...ADDONS_STANDARD, ...ADDONS_PREMIUM];

// ── CALC FUNCTIONS ──
function selectType(t, el){
  state.type=t; state.size=null; state.service=null;
  document.querySelectorAll('#typeGrid .choice-card').forEach(c=>c.classList.remove('selected'));
  el.classList.add('selected');
  renderBtnRow();
}
function renderSizes(){
  const grid=document.getElementById('sizeGrid');
  grid.innerHTML=(SIZES[state.type]||[]).map(s=>`
    <div class="choice-card" onclick="selectSize('${s.id}',this)">
      <div class="choice-text">
        <div class="choice-name">${s.name}</div>
        <div class="choice-name-es">${s.es}</div>
      </div>
      <div class="choice-check"><span class="checkmark">✓</span></div>
    </div>`).join('');
}
function selectSize(id,el){
  state.size=id; state.service=null;
  document.querySelectorAll('#sizeGrid .choice-card').forEach(c=>c.classList.remove('selected'));
  el.classList.add('selected'); renderBtnRow();
}
function renderServices(){
  const grid=document.getElementById('serviceGrid');
  const svcs=((SERVICES[state.type]||{})[state.size])||[];
  grid.innerHTML=svcs.map(s=>`
    <div class="svc-card" onclick="selectService('${s.id}',${s.price},this)">
      <div class="svc-left">
        <div class="svc-name">${s.name}</div>
        <div class="svc-name-es">${s.es}</div>
      </div>
      <div class="svc-price">$${s.price}</div>
    </div>`).join('');
}
function selectService(id,price,el){
  state.service={id,price};
  document.querySelectorAll('#serviceGrid .svc-card').forEach(c=>c.classList.remove('selected'));
  el.classList.add('selected'); updateTotal(); renderBtnRow();
}
function renderAddons(){
  const list=document.getElementById('addonList');
  const makeGroup=(items,title,es)=>
    `<div class="section-header">${title} · ${es}</div>
     <div class="addon-list">${items.map(a=>`
       <div class="addon-item${state.addons.has(a.id)?' selected':''}" onclick="toggleAddon('${a.id}',${a.price},this)">
         <div class="addon-toggle">${state.addons.has(a.id)?'✓':''}</div>
         <div class="addon-text">
           <div class="addon-name">${a.name}</div>
           <div class="addon-name-es">${a.es}</div>
           ${a.note?`<div class="addon-note">⚠ ${a.note}</div>`:''}
         </div>
         <div class="addon-price">+$${a.price}</div>
       </div>`).join('')}
     </div>`;
  list.innerHTML=
    makeGroup(ADDONS_STANDARD,'Standard Add-Ons','Adicionales Estándar')+
    makeGroup(ADDONS_PREMIUM,'Premium Services','Servicios Premium');
}
function toggleAddon(id,price,el){
  if(state.addons.has(id)){
    state.addons.delete(id); el.classList.remove('selected');
    el.querySelector('.addon-toggle').textContent='';
  } else {
    state.addons.add(id); el.classList.add('selected');
    el.querySelector('.addon-toggle').textContent='✓';
  }
  updateTotal();
}
function togglePromo(type){
  const el=document.getElementById(type==='first'?'firstCleanToggle':'recurringToggle');
  if(state.promos.has(type)){
    state.promos.delete(type); el.classList.remove('active');
  } else {
    state.promos.clear();
    document.querySelectorAll('.promo-toggle').forEach(e=>e.classList.remove('active'));
    state.promos.add(type); el.classList.add('active');
  }
  updateTotal();
}
function getTotal(){
  if(!state.service) return {base:0,addonsTotal:0,subtotal:0,discount:0,final:0};
  const base=state.service.price;
  let addonsTotal=0;
  state.addons.forEach(id=>{ const a=ALL_ADDONS.find(x=>x.id===id); if(a) addonsTotal+=a.price; });
  const subtotal=base+addonsTotal;
  let discount=0;
  if(state.promos.has('first'))     discount=Math.round(subtotal*.20);
  if(state.promos.has('recurring')) discount=Math.round(subtotal*.10);
  return {base,addonsTotal,subtotal,discount,final:subtotal-discount};
}
function updateTotal(){
  const {final,subtotal,discount}=getTotal();
  document.getElementById('totalDisplay').textContent=final?`$${final}`:'$0';
  document.getElementById('originalDisplay').textContent=discount>0?`$${subtotal}`:'';
}
function getSizeLabel(){ return (SIZES[state.type]||[]).find(s=>s.id===state.size)?.name||''; }
function getSvcLabel(){ return (((SERVICES[state.type]||{})[state.size])||[]).find(s=>s.id===state.service?.id)?.name||''; }

function buildQuote(){
  const {base,subtotal,discount,final}=getTotal();
  const addonLines=[...state.addons].map(id=>{ const a=ALL_ADDONS.find(x=>x.id===id); return a?`  + ${a.name}: $${a.price}`:''; }).filter(Boolean).join('\n');
  const promoLine=state.promos.has('first')?`\n  🎉 20% First Clean Discount: -$${discount}`:state.promos.has('recurring')?`\n  🔁 10% Recurring Discount: -$${discount}`:'';
  return `━━━━━━━━━━━━━━━━━━━━━━━
✨ FAR ROCK SHINE — ESTIMATE
   Cleaning Services · Far Rockaway, NY
━━━━━━━━━━━━━━━━━━━━━━━
📋 ${getSizeLabel()} — ${getSvcLabel()}
   Base: $${base}
${addonLines?'Add-Ons:\n'+addonLines:''}${promoLine}
━━━━━━━━━━━━━━━━━━━━━━━
💵 TOTAL: $${final}
━━━━━━━━━━━━━━━━━━━━━━━
📞 (929) 803-6022
📧 farrockshine@gmail.com
📱 @FarRockShine (IG & FB)
✅ Insured & Bonded
💳 Zelle · Venmo · Cash App · Apple Pay · Cash
━━━━━━━━━━━━━━━━━━━━━━━
Estimate only. Final price confirmed at booking.`;
}

// ── NAVIGATION ──
function nextStep(){
  if(state.step>=4) return;
  document.getElementById('step'+state.step).classList.remove('active');
  state.step++;
  document.getElementById('step'+state.step).classList.add('active');
  updateDots();
  if(state.step===1) renderSizes();
  if(state.step===2) renderServices();
  if(state.step===3) renderAddons();
  renderBtnRow();
}
function prevStep(){
  if(state.step<=0) return;
  document.getElementById('step'+state.step).classList.remove('active');
  state.step--;
  document.getElementById('step'+state.step).classList.add('active');
  updateDots(); renderBtnRow();
}
function updateDots(){
  for(let i=0;i<5;i++){
    const d=document.getElementById('dot'+i);
    d.className='dot'+(i<state.step?' done':i===state.step?' active':'');
  }
  document.getElementById('stepLabel').textContent=STEP_LABELS[state.step];
}
function renderBtnRow(){
  const row=document.getElementById('btnRow');
  const canNext=(state.step===0&&state.type)||(state.step===1&&state.size)||
                (state.step===2&&state.service)||state.step===3;
  if(state.step===4){
    row.innerHTML=`
      <button class="btn btn-reset" onclick="resetAll()">↺ Reset</button>
      <button class="btn btn-copy" onclick="copyQuote()">📋 Copy Quote</button>`;
  } else {
    row.innerHTML=`
      ${state.step>0?'<button class="btn btn-back" onclick="prevStep()">← Back</button>':''}
      <button class="btn btn-next" onclick="nextStep()" ${canNext?'':'disabled'}>Next →</button>`;
  }
}
function copyQuote(){
  clipCopy(buildQuote());
}
function resetAll(){
  state.step=0; state.type=null; state.size=null; state.service=null;
  state.addons.clear(); state.promos.clear();
  document.querySelectorAll('.step-panel').forEach(p=>p.classList.remove('active'));
  document.getElementById('step0').classList.add('active');
  document.querySelectorAll('#typeGrid .choice-card').forEach(c=>c.classList.remove('selected'));
  document.getElementById('totalDisplay').textContent='$0';
  document.getElementById('originalDisplay').textContent='';
  updateDots(); renderBtnRow();
}

// ══════════════════════════════════════════
// MODE SWITCHER
// ══════════════════════════════════════════
function switchMode(mode){
  document.getElementById('screenCalc').classList.toggle('active', mode==='calc');
  document.getElementById('screenAgr').classList.toggle('active', mode==='agr');
  document.getElementById('modeCalc').classList.toggle('active', mode==='calc');
  document.getElementById('modeAgr').classList.toggle('active', mode==='agr');
  document.getElementById('headerSub').textContent=mode==='calc'?'Quote Calculator':'Job Agreement';
  if(mode==='agr') populateJobSummary();
}

// ══════════════════════════════════════════
// AGREEMENT LOGIC
// ══════════════════════════════════════════
function populateJobSummary(){
  const {final,addonsTotal,discount}=getTotal();
  document.getElementById('sumService').textContent=
    state.service ? `${getSizeLabel()} — ${getSvcLabel()}` : 'No quote generated';
  const addonNames=[...state.addons].map(id=>ALL_ADDONS.find(x=>x.id===id)?.name).filter(Boolean);
  document.getElementById('sumAddons').textContent=addonNames.length?addonNames.join(', '):'None';
  document.getElementById('sumDiscount').textContent=
    discount>0 ? (state.promos.has('first')?'20% First Clean':'10% Recurring')+` (-$${discount})`:'None';
  document.getElementById('sumTotal').textContent=final?`$${final}`:'$0';
  // Auto-fill date/time
  const now=new Date();
  document.getElementById('jobDateTime').value=now.toLocaleDateString('en-US',{
    weekday:'long',year:'numeric',month:'long',day:'numeric',hour:'2-digit',minute:'2-digit'
  });
  initCanvas();
}

function toggleAdvisory(el){
  el.classList.toggle('checked');
  el.querySelector('.adv-check').textContent=el.classList.contains('checked')?'✓':'';
  checkAgrReady();
}

function checkAgrReady(){
  const name=document.getElementById('clientName').value.trim();
  const addr=document.getElementById('clientAddress').value.trim();
  const contact=document.getElementById('clientContact').value.trim();
  const items=document.querySelectorAll('.advisory-item');
  const allChecked=[...items].every(i=>i.classList.contains('checked'));
  const hasSig=sigHasContent;
  const ready=name&&addr&&contact&&allChecked&&hasSig;
  const btn=document.getElementById('btnSaveAgr');
  const status=document.getElementById('agrStatus');
  btn.disabled=!ready;
  if(ready){
    status.textContent='✓ Ready to save / Listo para guardar';
    status.className='agr-status ready';
  } else {
    const missing=[];
    if(!name) missing.push('client name');
    if(!addr) missing.push('address');
    if(!contact) missing.push('phone/email');
    if(!allChecked) missing.push('all advisory checkboxes');
    if(!hasSig) missing.push('signature');
    status.textContent='Missing: '+missing.join(', ');
    status.className='agr-status';
  }
}

function buildAgreementText(){
  const name=document.getElementById('clientName').value.trim();
  const addr=document.getElementById('clientAddress').value.trim();
  const contact=document.getElementById('clientContact').value.trim();
  const dt=document.getElementById('jobDateTime').value;
  const {final}=getTotal();
  const svc=state.service?`${getSizeLabel()} — ${getSvcLabel()}`:'Not specified';
  const addonNames=[...state.addons].map(id=>ALL_ADDONS.find(x=>x.id===id)?.name).filter(Boolean);
  return `━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ FAR ROCK SHINE — PRE-SERVICE AGREEMENT
   (929) 803-6022 · @FarRockShine
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CLIENT: ${name}
ADDRESS: ${addr}
CONTACT: ${contact}
DATE/TIME: ${dt}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SERVICE: ${svc}
ADD-ONS: ${addonNames.length?addonNames.join(', '):'None'}
AGREED TOTAL: $${final}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VALUABLES ADVISORY — CLIENT CONFIRMED:
  ✓ Cash, jewelry & financial items secured
  ✓ Electronics & devices secured
  ✓ Medications & personal items secured
  ✓ Sentimental & collectible items secured
  ✓ Pre-existing damage acknowledged
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CLIENT AGREEMENT — CONFIRMED:
  • Unsecured valuables: client responsibility
  • Staff conduct policy acknowledged
  • Pre-existing conditions acknowledged
  • Liability limited to service cost
  • Fraud/false claims policy acknowledged
  • Payment due upon completion
  • Concerns within 24hrs of service
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✍️ SIGNED BY: ${name}
   DATE: ${dt}
   [Digital signature captured on device]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Far Rock Shine · Insured & Bonded
This agreement is legally binding upon signature.`;
}

function saveAgreement(){
  clipCopy(buildAgreementText());
}

// ══════════════════════════════════════════
// SIGNATURE PAD
// ══════════════════════════════════════════
let sigCtx, sigDrawing=false, sigHasContent=false, sigLastX, sigLastY;

function initCanvas(){
  const canvas=document.getElementById('sigCanvas');
  const wrap=document.getElementById('sigWrap');
  canvas.width=canvas.offsetWidth||320;
  canvas.height=140;
  sigCtx=canvas.getContext('2d');
  sigCtx.strokeStyle='#082e1e';
  sigCtx.lineWidth=2.5;
  sigCtx.lineCap='round';
  sigCtx.lineJoin='round';
  sigHasContent=false;

  // Touch events
  canvas.addEventListener('touchstart',e=>{
    e.preventDefault();
    const t=e.touches[0];
    const r=canvas.getBoundingClientRect();
    sigDrawing=true;
    sigLastX=t.clientX-r.left;
    sigLastY=t.clientY-r.top;
  },{passive:false});
  canvas.addEventListener('touchmove',e=>{
    e.preventDefault();
    if(!sigDrawing) return;
    const t=e.touches[0];
    const r=canvas.getBoundingClientRect();
    const x=t.clientX-r.left;
    const y=t.clientY-r.top;
    drawLine(sigLastX,sigLastY,x,y);
    sigLastX=x; sigLastY=y;
  },{passive:false});
  canvas.addEventListener('touchend',()=>{ sigDrawing=false; });

  // Mouse events (desktop)
  canvas.addEventListener('mousedown',e=>{
    const r=canvas.getBoundingClientRect();
    sigDrawing=true;
    sigLastX=e.clientX-r.left; sigLastY=e.clientY-r.top;
  });
  canvas.addEventListener('mousemove',e=>{
    if(!sigDrawing) return;
    const r=canvas.getBoundingClientRect();
    const x=e.clientX-r.left; const y=e.clientY-r.top;
    drawLine(sigLastX,sigLastY,x,y);
    sigLastX=x; sigLastY=y;
  });
  canvas.addEventListener('mouseup',()=>{ sigDrawing=false; });
  canvas.addEventListener('mouseleave',()=>{ sigDrawing=false; });
}

function drawLine(x1,y1,x2,y2){
  sigCtx.beginPath();
  sigCtx.moveTo(x1,y1);
  sigCtx.lineTo(x2,y2);
  sigCtx.stroke();
  if(!sigHasContent){
    sigHasContent=true;
    document.getElementById('sigPlaceholder').classList.add('hidden');
    document.getElementById('sigWrap').classList.add('has-sig');
  }
  checkAgrReady();
}

function clearSig(){
  const canvas=document.getElementById('sigCanvas');
  sigCtx.clearRect(0,0,canvas.width,canvas.height);
  sigHasContent=false;
  document.getElementById('sigPlaceholder').classList.remove('hidden');
  document.getElementById('sigWrap').classList.remove('has-sig');
  checkAgrReady();
}

// ══════════════════════════════════════════
// CLIPBOARD UTILITY
// ══════════════════════════════════════════
function clipCopy(txt){
  if(navigator.clipboard&&navigator.clipboard.writeText){
    navigator.clipboard.writeText(txt).then(showToast).catch(()=>fallbackCopy(txt));
  } else { fallbackCopy(txt); }
}
function fallbackCopy(txt){
  const ta=document.createElement('textarea');
  ta.value=txt; ta.style.cssText='position:fixed;opacity:0;top:0;left:0;';
  document.body.appendChild(ta); ta.focus(); ta.select();
  try{ document.execCommand('copy'); showToast(); }catch(e){}
  document.body.removeChild(ta);
}
function showToast(){
  const t=document.getElementById('toast');
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2600);
}

// ── SERVICE WORKER ──
if('serviceWorker' in navigator &&
   location.hostname !== 'www.claudeusercontent.com' &&
   location.protocol === 'https:'){
  window.addEventListener('load',()=>{
    navigator.serviceWorker.register('./service-worker.js')
      .then(()=>console.log('FRS SW registered ✓'))
      .catch(e=>console.warn('SW failed:',e));
  });
}
</script>
</body>
</html>
