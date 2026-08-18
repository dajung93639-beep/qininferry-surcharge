[index.html](https://github.com/user-attachments/files/31167028/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>진인해운 | 인천-진황도 부대비용 조회</title>
<style>
  :root{
    --ink:#1f2430;
    --sub:#5b6270;
    --line:#e2e4ea;
    --bg:#f7f7f9;
    --card:#ffffff;
    --accent:#33427a;
    --accent-bg:#eaedf6;
    --brand-red:#c14432;
    --brand-red-bg:#fbeae7;
    --usd:#8a5a1e;
    --usd-bg:#fbf1e2;
    --won:#1e6b4f;
    --won-bg:#e9f5f0;
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Noto Sans KR',sans-serif;
    background:var(--bg);
    color:var(--ink);
    padding:32px 16px;
  }
  .wrap{max-width:760px;margin:0 auto;}
  .brand-bar{height:4px;border-radius:4px;background:var(--brand-red);margin-bottom:24px;}
  .top-row{display:flex;justify-content:space-between;align-items:center;gap:16px;margin-bottom:8px;}
  .brand{display:flex;align-items:center;gap:14px;}
  .brand img{height:52px;width:auto;display:block;}
  .brand-text h1{font-size:19px;font-weight:700;margin:0 0 2px;letter-spacing:-0.01em;}
  .sub{color:var(--sub);font-size:13.5px;margin:0 0 22px;line-height:1.5;}
  .lang-toggle{
    flex-shrink:0;
    display:flex;
    border:1px solid var(--line);
    border-radius:8px;
    overflow:hidden;
  }
  .lang-btn{
    padding:8px 14px;
    font-size:13px;
    font-weight:600;
    background:#fff;
    color:var(--sub);
    border:none;
    cursor:pointer;
  }
  .lang-btn.active{background:var(--accent);color:#fff;}

  .tabs{display:flex;gap:4px;margin-bottom:16px;border-bottom:2px solid var(--line);}
  .tab-btn{
    flex:1;
    padding:12px 0;
    text-align:center;
    font-size:15px;
    font-weight:600;
    color:var(--sub);
    background:none;
    border:none;
    border-bottom:3px solid transparent;
    cursor:pointer;
    margin-bottom:-2px;
  }
  .tab-btn.active{color:var(--accent);border-bottom-color:var(--brand-red);}

  .card{
    background:var(--card);
    border:1px solid var(--line);
    border-radius:14px;
    padding:24px;
    margin-bottom:16px;
  }
  label.grouplabel{display:block;font-size:13px;color:var(--sub);margin-bottom:8px;font-weight:600;}
  .check-group{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:8px;}
  .check-item{
    display:flex;
    align-items:center;
    gap:6px;
    padding:8px 12px;
    border:1px solid var(--line);
    border-radius:8px;
    cursor:pointer;
    font-size:14px;
    user-select:none;
  }
  .check-item input{cursor:pointer;}
  .check-item.checked{border-color:var(--accent);background:var(--accent-bg);color:var(--accent);font-weight:600;}

  table{width:100%;border-collapse:collapse;margin-top:16px;font-size:14px;}
  .table-scroll{overflow-x:auto;border:1px solid var(--line);border-radius:10px;border-top:3px solid var(--brand-red);}
  th, td{text-align:left;padding:7px 12px;white-space:nowrap;}
  thead th{
    background:var(--accent);
    color:#ffffff;
    font-weight:600;
    font-size:11px;
    text-transform:uppercase;
    letter-spacing:.03em;
  }
  tbody tr{border-bottom:1px solid var(--line);}
  tbody tr:last-child{border-bottom:none;}
  tbody tr:nth-child(even){background:var(--bg);}
  td.num, th.num{text-align:right;font-variant-numeric:tabular-nums;}
  .badge{
    display:inline-block;
    font-size:10px;
    font-weight:700;
    padding:2px 7px;
    border-radius:20px;
    letter-spacing:.02em;
  }
  .badge.usd{background:var(--usd-bg);color:var(--usd);}
  .badge.won{background:var(--won-bg);color:var(--won);}
  .total-row td{font-weight:700;border-bottom:none;}
  .total-row.usd td{color:var(--usd);}
  .total-row.won td{color:var(--won);}
  .total-row.first td{border-top:2px solid var(--ink);padding-top:12px;}
  .note{
    font-size:12.5px;
    color:var(--sub);
    background:var(--accent-bg);
    border-radius:8px;
    padding:10px 12px;
    margin-top:14px;
    line-height:1.5;
  }
  .empty-hint{font-size:13px;color:var(--sub);padding:16px 0;text-align:center;}
  .footer-note{font-size:12px;color:var(--sub);text-align:center;margin-top:20px;}
  .copy-btn{
    margin-top:14px;
    width:100%;
    padding:11px;
    border:none;
    border-radius:8px;
    background:var(--accent);
    color:#fff;
    font-size:14px;
    font-weight:600;
    cursor:pointer;
  }
  .copy-btn:active{opacity:.85;}
  .copy-status{font-size:12.5px;color:var(--won);text-align:center;margin-top:8px;height:16px;}
  .panel{display:none;}
  .panel.active{display:block;}
  .mail-row{margin-top:14px;display:flex;gap:8px;}
  .mail-row input[type="email"]{flex:1;padding:10px 12px;border:1px solid var(--line);border-radius:8px;font-size:15px;}
  .mail-btn{
    padding:11px 16px;
    border:none;
    border-radius:8px;
    background:var(--won);
    color:#fff;
    font-size:14px;
    font-weight:600;
    cursor:pointer;
    white-space:nowrap;
  }
  .mail-btn:active{opacity:.85;}
  .mail-status{font-size:12.5px;color:var(--sub);margin-top:6px;height:16px;}
</style>
</head>
<body>
<div class="wrap">
  <div class="brand-bar"></div>
  <div class="top-row">
    <div class="brand">
      <img src="data:image/png;base64,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" alt="Qin In Shipping logo">
      <div class="brand-text">
        <h1 id="txtTitle">진인해운 인천-진황도 부대비용 조회</h1>
      </div>
    </div>
    <div class="lang-toggle">
      <button class="lang-btn active" id="langBtnKo" onclick="setLanguage('ko')">한국어</button>
      <button class="lang-btn" id="langBtnEn" onclick="setLanguage('en')">English</button>
    </div>
  </div>
  <p class="sub" id="txtSubtitle">수출/수입을 선택하고, 조회할 컨테이너 타입을 하나 이상 선택하세요.</p>

  <div class="tabs">
    <button class="tab-btn active" id="tabBtnExport" onclick="switchTab('export')">수출</button>
    <button class="tab-btn" id="tabBtnImport" onclick="switchTab('import')">수입</button>
  </div>

  <div class="panel active" id="panelExport">
    <div class="card">
      <label class="grouplabel" id="lblExportTypes">컨테이너 타입 선택 (다중 선택 가능)</label>
      <div class="check-group" id="exportTypeGroup"></div>

      <div class="table-scroll">
        <table id="exportTable"><thead></thead><tbody id="exportBody"></tbody></table>
      </div>
      <div class="empty-hint" id="exportEmptyHint" style="display:none;"></div>

      <div class="note" id="noteExport">수출 항목: BAF(USD), THC/DOC/WFG/PSF/PFS/SLC(WON)</div>

      <button class="copy-btn" onclick="copyResult('export')" id="copyBtnExport">화주 회신용 문구로 복사</button>
      <div class="copy-status" id="exportCopyStatus"></div>

      <div class="mail-row">
        <input type="email" id="exportEmail" class="mailInput" placeholder="화주 이메일 주소 입력">
        <button class="mail-btn" onclick="sendMail('export')" id="mailBtnExport">메일 작성하기</button>
      </div>
      <div class="mail-status" id="exportMailStatus"></div>
    </div>
  </div>

  <div class="panel" id="panelImport">
    <div class="card">
      <label class="grouplabel" id="lblImportTypes">컨테이너 타입 선택 (다중 선택 가능)</label>
      <div class="check-group" id="importTypeGroup"></div>

      <div class="table-scroll">
        <table id="importTable"><thead></thead><tbody id="importBody"></tbody></table>
      </div>
      <div class="empty-hint" id="importEmptyHint" style="display:none;"></div>

      <div class="note" id="noteImport">수입 항목: BAF/CAF/CRS(USD), THC/DOC/WFG/CCF/PSF/PFS(WON)</div>

      <button class="copy-btn" onclick="copyResult('import')" id="copyBtnImport">화주 회신용 문구로 복사</button>
      <div class="copy-status" id="importCopyStatus"></div>

      <div class="mail-row">
        <input type="email" id="importEmail" class="mailInput" placeholder="화주 이메일 주소 입력">
        <button class="mail-btn" onclick="sendMail('import')" id="mailBtnImport">메일 작성하기</button>
      </div>
      <div class="mail-status" id="importMailStatus"></div>
    </div>
  </div>

  <p class="footer-note" id="txtFooter">인천-진황도 항로 전용 · 요율 변경 시 데이터 영역만 수정하면 반영됩니다.</p>
  <p class="footer-note" id="txtLastUpdated" style="margin-top:4px;"></p>
</div>

<script>
// ---- 요율 데이터 ----
const CONTAINER_TYPES = ["20DRY", "40HQ", "20RF", "40RF"];

const RATES = {
  export: {
    BAF: { currency: 'USD', "20DRY": 100, "40HQ": 200, "20RF": 100, "40RF": 200 },
    THC: { currency: 'WON', "20DRY": 150000, "40HQ": 210000, "20RF": 250000, "40RF": 375000 },
    DOC: { currency: 'WON', "20DRY": 40000,  "40HQ": 40000,  "20RF": 40000,  "40RF": 40000  },
    WFG: { currency: 'WON', "20DRY": 4200,   "40HQ": 8400,   "20RF": 4200,   "40RF": 8400   },
    PSF: { currency: 'WON', "20DRY": 259,    "40HQ": 518,    "20RF": 259,    "40RF": 518    },
    PFS: { currency: 'WON', "20DRY": 145,    "40HQ": 290,    "20RF": 145,    "40RF": 290    },
    SLC: { currency: 'WON', "20DRY": 8000,   "40HQ": 8000,   "20RF": 8000,   "40RF": 8000   }
  },
  import: {
    BAF: { currency: 'USD', "20DRY": 190, "40HQ": 380, "20RF": 190, "40RF": 380 },
    CAF: { currency: 'USD', "20DRY": 30,  "40HQ": 60,  "20RF": 30,  "40RF": 60  },
    THC: { currency: 'WON', "20DRY": 150000, "40HQ": 210000, "20RF": 250000, "40RF": 375000 },
    DOC: { currency: 'WON', "20DRY": 40000,  "40HQ": 40000,  "20RF": 40000,  "40RF": 40000  },
    WFG: { currency: 'WON', "20DRY": 4200,   "40HQ": 8400,   "20RF": 4200,   "40RF": 8400   },
    CCF: { currency: 'WON', "20DRY": 35000,  "40HQ": 50000,  "20RF": 45000,  "40RF": 60000  },
    CRS: { currency: 'USD', "20DRY": 40,  "40HQ": 80,  "20RF": 40,  "40RF": 80  },
    PSF: { currency: 'WON', "20DRY": 259,    "40HQ": 518,    "20RF": 259,    "40RF": 518    },
    PFS: { currency: 'WON', "20DRY": 145,    "40HQ": 290,    "20RF": 145,    "40RF": 290    }
  }
};

// ---- 언어별 텍스트 ----
const STRINGS = {
  ko: {
    title: '진인해운 인천-진황도 부대비용 조회',
    subtitle: '수출/수입을 선택하고, 조회할 컨테이너 타입을 하나 이상 선택하세요.',
    tabExport: '수출', tabImport: '수입',
    typeGroupLabel: '컨테이너 타입 선택 (다중 선택 가능)',
    typeLabel: { "20DRY": "20DRY", "40HQ": "40HQ", "20RF": "20RF (냉동)", "40RF": "40RF (냉동)" },
    thItem: '항목', thUnit: '단위',
    thAmount: '금액',
    usdTotal: 'USD 합계', krwTotal: 'KRW 합계',
    noteExport: '수출 항목: BAF(USD), THC/DOC/WFG/PSF/PFS/SLC(WON)',
    noteImport: '수입 항목: BAF/CAF/CRS(USD), THC/DOC/WFG/CCF/PSF/PFS(WON)',
    copyBtn: '화주 회신용 문구로 복사',
    mailPlaceholder: '화주 이메일 주소 입력',
    mailBtn: '메일 작성하기',
    footer: '인천-진황도 항로 전용 · 요율 변경 시 데이터 영역만 수정하면 반영됩니다.',
    lastUpdated: (name, date) => `최종 변경자: ${name}${date ? ' (' + date + ')' : ''}`,
    sheetLoadFail: '(구글 시트 연결에 실패하여 기본 요율로 표시 중입니다)',
    copied: '복사되었습니다. 이메일에 붙여넣으세요.',
    copyFail: '복사에 실패했습니다. 직접 선택 후 복사해주세요.',
    mailInvalid: '화주 이메일 주소를 정확히 입력해주세요.',
    mailOpened: '메일 프로그램이 열립니다. 본문에 Ctrl+V(붙여넣기)로 표를 삽입해주세요.',
    mailOpenedNoCopy: '메일 프로그램이 열립니다. (표 복사에 실패했으니 "화주 회신용 문구로 복사"를 눌러 다시 시도해주세요.)',
    emptyHint: '조회할 컨테이너 타입을 하나 이상 선택해주세요.',
    labelExport: '수출', labelImport: '수입',
    routeExport: '인천-진황도', routeImport: '진황도-인천',
    subjectPrefix: '[진인해운]',
    subjectSuffix: '부대비용',
    greeting: '안녕하세요, 진인해운입니다.',
    introLine: (label, route) => `${route} 항로 ${label} 부대비용을 안내드립니다.`,
    typeSectionTitle: (type) => `[${type}]`,
    usdTotalLine: (v) => `USD 합계: ${v}`,
    krwTotalLine: (v) => `KRW 합계: ${v}`,
    frtNote: '※ FRT, LSS 등 변동성 항목은 상기 금액에 포함되어 있지 않으니 참고 부탁드립니다.',
    thanks: '감사합니다.',
    signature: '진인해운 고객지원팀 02-797-8896'
  },
  en: {
    title: 'Qin In Shipping | Incheon-Qinhuangdao Surcharge Inquiry',
    subtitle: 'Select Export or Import, then choose one or more container types to check.',
    tabExport: 'Export', tabImport: 'Import',
    typeGroupLabel: 'Select container type(s) (multiple allowed)',
    typeLabel: { "20DRY": "20DRY", "40HQ": "40HQ", "20RF": "20RF (Reefer)", "40RF": "40RF (Reefer)" },
    thItem: 'Item', thUnit: 'Unit',
    thAmount: 'Amount',
    usdTotal: 'USD total', krwTotal: 'KRW total',
    noteExport: 'Export items: BAF (USD), THC/DOC/WFG/PSF/PFS/SLC (WON)',
    noteImport: 'Import items: BAF/CAF/CRS (USD), THC/DOC/WFG/CCF/PSF/PFS (WON)',
    copyBtn: 'Copy reply text for customer',
    mailPlaceholder: 'Enter customer email address',
    mailBtn: 'Compose email',
    footer: 'Incheon-Qinhuangdao route only &middot; Update the rate data section to reflect any rate changes.',
    lastUpdated: (name, date) => `Last updated by: ${name}${date ? ' (' + date + ')' : ''}`,
    sheetLoadFail: '(Could not connect to the Google Sheet — showing default rates.)',
    copied: 'Copied. Paste it into your email.',
    copyFail: 'Copy failed. Please select and copy manually.',
    mailInvalid: 'Please enter a valid customer email address.',
    mailOpened: 'Your email client will open. Paste (Ctrl+V) into the body to insert the table.',
    mailOpenedNoCopy: 'Your email client will open. (Copying the table failed — please click "Copy reply text for customer" and try again.)',
    emptyHint: 'Please select one or more container types.',
    labelExport: 'Export', labelImport: 'Import',
    routeExport: 'Incheon-Qinhuangdao', routeImport: 'Qinhuangdao-Incheon',
    subjectPrefix: '[Qin In Shipping]',
    subjectSuffix: 'Surcharge Notice',
    greeting: 'Hello,',
    introLine: (label, route) => `This is Qin In Shipping. Please find below the ${label} surcharge details for the ${route} route.`,
    typeSectionTitle: (type) => `[${type}]`,
    usdTotalLine: (v) => `USD total: ${v}`,
    krwTotalLine: (v) => `KRW total: ${v}`,
    frtNote: '* Please note that variable items such as FRT and LSS are not included in the above amount.',
    thanks: 'Thank you.',
    signature: 'Qin In Shipping, Customer Support Team +82-2-797-8896'
  }
};

let currentLang = 'ko';
const selectedTypes = { export: ["20DRY"], import: ["20DRY"] };

function fmt(n){ return String(n).replace(/\B(?=(\d{3})+(?!\d))/g, ','); }

function buildCheckGroup(mode){
  const s = STRINGS[currentLang];
  const container = document.getElementById(mode + 'TypeGroup');
  container.innerHTML = '';
  CONTAINER_TYPES.forEach(type => {
    const id = mode + 'Chk_' + type;
    const checked = selectedTypes[mode].includes(type);
    const wrap = document.createElement('label');
    wrap.className = 'check-item' + (checked ? ' checked' : '');
    wrap.setAttribute('for', id);
    wrap.innerHTML = `<input type="checkbox" id="${id}" ${checked ? 'checked' : ''} data-type="${type}"> <span>${s.typeLabel[type]}</span>`;
    wrap.querySelector('input').addEventListener('change', (e) => {
      toggleType(mode, type, e.target.checked);
    });
    container.appendChild(wrap);
  });
}

function toggleType(mode, type, isChecked){
  const list = selectedTypes[mode];
  const idx = list.indexOf(type);
  if(isChecked && idx === -1){ list.push(type); }
  if(!isChecked && idx !== -1){ list.splice(idx, 1); }
  buildCheckGroup(mode);
  calculate(mode);
}

function switchTab(tab){
  document.getElementById('panelExport').classList.toggle('active', tab === 'export');
  document.getElementById('panelImport').classList.toggle('active', tab === 'import');
  document.getElementById('tabBtnExport').classList.toggle('active', tab === 'export');
  document.getElementById('tabBtnImport').classList.toggle('active', tab === 'import');
}

function calculate(mode){
  const s = STRINGS[currentLang];
  const rates = RATES[mode];
  const types = CONTAINER_TYPES.filter(t => selectedTypes[mode].includes(t));
  const table = document.getElementById(mode + 'Table');
  const thead = table.querySelector('thead');
  const tbody = document.getElementById(mode + 'Body');
  const emptyHint = document.getElementById(mode + 'EmptyHint');

  if(types.length === 0){
    thead.innerHTML = '';
    tbody.innerHTML = '';
    emptyHint.style.display = 'block';
    emptyHint.textContent = s.emptyHint;
    return;
  }
  emptyHint.style.display = 'none';

  // 헤더
  let headHtml = `<tr><th>${s.thItem}</th>`;
  types.forEach(t => headHtml += `<th class="num">${t}</th>`);
  headHtml += '</tr>';
  thead.innerHTML = headHtml;

  // 본문
  tbody.innerHTML = '';
  const totals = {};
  types.forEach(t => totals[t] = { USD: 0, WON: 0 });

  Object.keys(rates).forEach(item => {
    const rate = rates[item];
    let rowHtml = `<td>${item}</td>`;
    types.forEach(t => {
      const unit = rate[t];
      totals[t][rate.currency] += unit;
      const symbol = rate.currency === 'USD' ? '$' : '₩';
      rowHtml += `<td class="num">${symbol}${fmt(unit)}</td>`;
    });
    const tr = document.createElement('tr');
    tr.innerHTML = rowHtml;
    tbody.appendChild(tr);
  });

  document.getElementById(mode + 'CopyStatus').textContent = '';
}



function buildHtmlBody(mode){
  const s = STRINGS[currentLang];
  const rates = RATES[mode];
  const types = CONTAINER_TYPES.filter(t => selectedTypes[mode].includes(t));
  const label = mode === 'export' ? s.labelExport : s.labelImport;
  const route = mode === 'export' ? s.routeExport : s.routeImport;

  const ACCENT = '#33427a';
  const BRAND_RED = '#c14432';
  const LINE = '#e2e4ea';
  const STRIPE = '#f7f7f9';
  const USD_TXT = '#8a5a1e', USD_BG = '#fbf1e2';
  const WON_TXT = '#1e6b4f', WON_BG = '#e9f5f0';

  let html = '';
  html += `<div style="font-family:Arial,'Malgun Gothic',sans-serif;font-size:14px;color:#1f2430;">`;
  html += `<p style="margin:0 0 10px;">${s.greeting}</p>`;
  html += `<p style="margin:0 0 14px;">${s.introLine(label, route)}</p>`;

  html += `<table style="border-collapse:collapse;font-size:13px;margin-bottom:10px;border:1px solid ${LINE};border-top:3px solid ${BRAND_RED};" cellpadding="0" cellspacing="0">`;
  html += `<tr>
    <th style="padding:7px 12px;background:${ACCENT};color:#ffffff;text-align:left;font-size:11px;letter-spacing:.03em;text-transform:uppercase;">${s.thItem}</th>`;
  types.forEach(type => {
    html += `<th style="padding:7px 12px;background:${ACCENT};color:#ffffff;text-align:right;font-size:11px;letter-spacing:.03em;text-transform:uppercase;">${type}</th>`;
  });
  html += `</tr>`;

  Object.keys(rates).forEach((item, idx) => {
    const rate = rates[item];
    const rowBg = idx % 2 === 1 ? STRIPE : '#ffffff';
    html += `<tr style="background:${rowBg};">
      <td style="padding:6px 12px;border-bottom:1px solid ${LINE};">${item}</td>`;
    types.forEach(type => {
      const unit = rate[type];
      const symbol = rate.currency === 'USD' ? '$' : '₩';
      html += `<td style="padding:6px 12px;border-bottom:1px solid ${LINE};text-align:right;">${symbol}${fmt(unit)}</td>`;
    });
    html += `</tr>`;
  });
  html += `</table>`;

  html += `<p style="margin:0 0 4px;color:#5b6270;font-size:12.5px;">${s.frtNote}</p>`;
  html += `<p style="margin:14px 0 0;">${s.thanks}<br>${s.signature}</p>`;
  html += `</div>`;
  return html;
}

function buildBody(mode){
  const s = STRINGS[currentLang];
  const rates = RATES[mode];
  const types = CONTAINER_TYPES.filter(t => selectedTypes[mode].includes(t));
  const label = mode === 'export' ? s.labelExport : s.labelImport;
  const route = mode === 'export' ? s.routeExport : s.routeImport;

  let lines = [];
  lines.push(s.greeting);
  lines.push('');
  lines.push(s.introLine(label, route));
  lines.push('');

  // 헤더 라인: 항목 [탭] 20DRY [탭] 40HQ ...
  let header = ' '.repeat(6);
  types.forEach(type => { header += type.padEnd(12); });
  lines.push(header);

  Object.keys(rates).forEach(item => {
    const rate = rates[item];
    let row = item.padEnd(6);
    types.forEach(type => {
      const unit = rate[type];
      const symbol = rate.currency === 'USD' ? '$' : '₩';
      row += `${symbol}${fmt(unit)}`.padEnd(12);
    });
    lines.push(row);
  });
  lines.push('');

  lines.push(s.frtNote);
  lines.push('');
  lines.push(s.thanks);
  lines.push(s.signature);

  return lines.join('\n');
}

function copyResult(mode){
  const s = STRINGS[currentLang];
  const htmlText = buildHtmlBody(mode);
  const plainText = buildBody(mode);
  const statusEl = document.getElementById(mode + 'CopyStatus');

  if(window.ClipboardItem){
    const item = new ClipboardItem({
      'text/html': new Blob([htmlText], { type: 'text/html' }),
      'text/plain': new Blob([plainText], { type: 'text/plain' })
    });
    navigator.clipboard.write([item]).then(() => {
      statusEl.textContent = s.copied;
    }).catch(() => {
      navigator.clipboard.writeText(plainText).then(() => {
        statusEl.textContent = s.copied;
      }).catch(() => { statusEl.textContent = s.copyFail; });
    });
  } else {
    navigator.clipboard.writeText(plainText).then(() => {
      statusEl.textContent = s.copied;
    }).catch(() => { statusEl.textContent = s.copyFail; });
  }
}

function sendMail(mode){
  const s = STRINGS[currentLang];
  const label = mode === 'export' ? s.labelExport : s.labelImport;
  const route = mode === 'export' ? s.routeExport : s.routeImport;
  const emailInput = document.getElementById(mode + 'Email');
  const statusEl = document.getElementById(mode + 'MailStatus');
  const to = emailInput.value.trim();

  if(!to || !to.includes('@')){
    statusEl.style.color = '#a32d2d';
    statusEl.textContent = s.mailInvalid;
    return;
  }

  const htmlText = buildHtmlBody(mode);
  const plainText = buildBody(mode);

  const subject = encodeURIComponent(`${s.subjectPrefix} ${route} ${label} ${s.subjectSuffix}`);
  const cc = encodeURIComponent('mkt@qininferry.com');
  const mailtoUrl = `mailto:${encodeURIComponent(to)}?cc=${cc}&subject=${subject}`;

  let copyPromise;
  if(window.ClipboardItem){
    copyPromise = navigator.clipboard.write([new ClipboardItem({
      'text/html': new Blob([htmlText], { type: 'text/html' }),
      'text/plain': new Blob([plainText], { type: 'text/plain' })
    })]);
  } else {
    copyPromise = navigator.clipboard.writeText(plainText);
  }

  statusEl.style.color = 'var(--sub)';
  statusEl.textContent = s.mailOpened;

  window.location.href = mailtoUrl;

  copyPromise.catch(() => {
    statusEl.textContent = s.mailOpenedNoCopy;
  });
}

function setLanguage(lang){
  currentLang = lang;
  const s = STRINGS[lang];

  document.getElementById('langBtnKo').classList.toggle('active', lang === 'ko');
  document.getElementById('langBtnEn').classList.toggle('active', lang === 'en');

  document.getElementById('txtTitle').innerHTML = s.title;
  document.getElementById('txtSubtitle').textContent = s.subtitle;
  document.getElementById('tabBtnExport').textContent = s.tabExport;
  document.getElementById('tabBtnImport').textContent = s.tabImport;

  document.getElementById('lblExportTypes').textContent = s.typeGroupLabel;
  document.getElementById('lblImportTypes').textContent = s.typeGroupLabel;

  document.getElementById('noteExport').textContent = s.noteExport;
  document.getElementById('noteImport').textContent = s.noteImport;

  document.getElementById('copyBtnExport').textContent = s.copyBtn;
  document.getElementById('copyBtnImport').textContent = s.copyBtn;

  document.querySelectorAll('.mailInput').forEach(el => el.placeholder = s.mailPlaceholder);
  document.getElementById('mailBtnExport').textContent = s.mailBtn;
  document.getElementById('mailBtnImport').textContent = s.mailBtn;

  document.getElementById('txtFooter').innerHTML = s.footer;

  document.getElementById('exportCopyStatus').textContent = '';
  document.getElementById('importCopyStatus').textContent = '';
  document.getElementById('exportMailStatus').textContent = '';
  document.getElementById('importMailStatus').textContent = '';

  buildCheckGroup('export');
  buildCheckGroup('import');
  calculate('export');
  calculate('import');
  renderLastUpdated();
}

buildCheckGroup('export');
buildCheckGroup('import');
calculate('export');
calculate('import');

// ---- 구글 시트 실시간 요율 연동 ----
const SHEET_CSV_URL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vQSz3zaZG65CdUBIjePb8MFJHyAfGXO3E1NqtmkQgTJnzHTQdg8clLph0hZIkHMa9dlHHNCHWG0y_TF/pub?gid=0&single=true&output=csv';
let lastUpdatedInfo = { name: '', date: '' };

function parseCSVLine(line){
  const result = [];
  let cur = '';
  let inQuotes = false;
  for(let i = 0; i < line.length; i++){
    const ch = line[i];
    if(inQuotes){
      if(ch === '"'){
        if(line[i+1] === '"'){ cur += '"'; i++; }
        else { inQuotes = false; }
      } else {
        cur += ch;
      }
    } else {
      if(ch === '"'){ inQuotes = true; }
      else if(ch === ','){ result.push(cur); cur = ''; }
      else { cur += ch; }
    }
  }
  result.push(cur);
  return result.map(c => c.trim());
}

function parseSheetCSV(text){
  const rows = text.split(/\r?\n/).filter(l => l.length > 0).map(parseCSVLine);

  const result = { import: {}, export: {} };
  let section = null;
  let colTypeMap = {}; // 열 인덱스 -> 컨테이너 타입

  rows.forEach(row => {
    const first = (row[0] || '').trim();

    if(first === '수입' || first.toLowerCase() === 'import'){ section = 'import'; colTypeMap = {}; return; }
    if(first === '수출' || first.toLowerCase() === 'export'){ section = 'export'; colTypeMap = {}; return; }
    if(first === '최종변경자'){ lastUpdatedInfo.name = row[1] || ''; return; }
    if(first === '최종변경일'){ lastUpdatedInfo.date = row[1] || ''; return; }

    // 헤더 행 감지 (20DRY, 40HQ 등이 포함된 행)
    const hasTypeCol = row.some(cell => CONTAINER_TYPES.includes((cell || '').toUpperCase()));
    if(hasTypeCol){
      colTypeMap = {};
      row.forEach((cell, idx) => {
        const upper = (cell || '').toUpperCase();
        if(CONTAINER_TYPES.includes(upper)){ colTypeMap[idx] = upper; }
      });
      return;
    }

    // 항목 데이터 행
    if(section && first && Object.keys(colTypeMap).length > 0){
      const currencyCell = row.find(c => /^(USD|WON)$/i.test((c || '').trim()));
      if(!currencyCell) return;
      const currency = currencyCell.toUpperCase();
      const entry = { currency };
      let hasValue = false;
      Object.keys(colTypeMap).forEach(idx => {
        const raw = (row[idx] || '').replace(/,/g, '').trim();
        const num = parseFloat(raw);
        if(!isNaN(num)){ entry[colTypeMap[idx]] = num; hasValue = true; }
      });
      if(hasValue){ result[section][first] = entry; }
    }
  });

  return result;
}

function renderLastUpdated(){
  const s = STRINGS[currentLang];
  const el = document.getElementById('txtLastUpdated');
  if(!el) return;
  if(lastUpdatedInfo.name){
    el.textContent = s.lastUpdated(lastUpdatedInfo.name, lastUpdatedInfo.date);
  } else {
    el.textContent = '';
  }
}

async function loadRatesFromSheet(){
  try{
    const res = await fetch(SHEET_CSV_URL, { cache: 'no-store' });
    if(!res.ok) throw new Error('시트 응답 오류');
    const text = await res.text();
    const parsed = parseSheetCSV(text);

    if(Object.keys(parsed.import).length > 0){ RATES.import = parsed.import; }
    if(Object.keys(parsed.export).length > 0){ RATES.export = parsed.export; }

    calculate('export');
    calculate('import');
    renderLastUpdated();
  } catch(err){
    const el = document.getElementById('txtLastUpdated');
    if(el){ el.textContent = STRINGS[currentLang].sheetLoadFail; }
    console.error('요율 시트 로딩 실패:', err);
  }
}

loadRatesFromSheet();
</script>
</body>
</html>
