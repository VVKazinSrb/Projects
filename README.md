
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Хаб 2.0 для РубАрх — ресурсы и бюджет</title>
<style>
:root{
  --bg:#eef6fb; --panel:#ffffff; --ink:#12303f; --muted:#5b7788;
  --line:#d3e5f0; --line2:#bcd8e8; --acc:#1b7fb8; --acc2:#3aa6d8;
  --soft:#f4fafd; --shadow:0 1px 2px rgba(20,70,100,.06),0 6px 20px rgba(20,70,100,.06);
  --ok:#1c7a52; --warn:#a8710f; --risk:#b23c3c;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);
  font:15px/1.55 -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;}
.wrap{max-width:1080px;margin:0 auto;padding:28px 20px 64px}
header.top{background:linear-gradient(135deg,#ffffff 0%,#e7f3fa 100%);
  border:1px solid var(--line);border-radius:14px;padding:22px 26px;box-shadow:var(--shadow)}
h1{margin:0 0 6px;font-size:23px;letter-spacing:.2px}
.sub{color:var(--muted);font-size:13.5px}
.meta{margin-top:10px;font-size:12.5px;color:var(--muted)}
.switch{display:inline-flex;gap:6px;margin:20px 0 22px;background:#fff;border:1px solid var(--line);
  border-radius:12px;padding:6px;box-shadow:var(--shadow)}
.switch button{appearance:none;border:0;background:transparent;color:var(--muted);font:inherit;font-weight:600;
  padding:9px 22px;border-radius:8px;cursor:pointer;transition:.18s}
.switch button:hover{color:var(--acc)}
.switch button.on{background:linear-gradient(180deg,#2f9fd0,#1b7fb8);color:#fff;box-shadow:0 2px 8px rgba(27,127,184,.28)}
section.mode{display:none;animation:fade .25s ease}
section.mode.on{display:block}
@keyframes fade{from{opacity:0;transform:translateY(3px)}to{opacity:1}}
.card{background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:18px 20px;box-shadow:var(--shadow);margin-bottom:18px}
h2{font-size:17px;margin:0 0 12px;padding-bottom:9px;border-bottom:1px solid var(--line)}
h3{font-size:14.5px;margin:0 0 10px;color:#1c5f81}
.hint{font-size:12.5px;color:var(--muted);margin:-4px 0 12px}
select{font:inherit;padding:10px 12px;border:1px solid var(--line2);border-radius:9px;background:#fff;color:var(--ink);min-width:290px}
select:focus{outline:2px solid var(--acc2);outline-offset:1px}
table{width:100%;border-collapse:collapse;font-size:13.5px}
th,td{padding:9px 10px;border-bottom:1px solid var(--line);text-align:left;vertical-align:top}
th{background:var(--soft);font-size:12px;text-transform:uppercase;letter-spacing:.4px;color:#3d6479;position:sticky;top:0}
td.num,th.num{text-align:right;white-space:nowrap;font-variant-numeric:tabular-nums}
tbody tr:hover{background:#f7fbfe}
tfoot td{font-weight:700;background:var(--soft);border-top:2px solid var(--line2)}
.tblwrap{max-height:520px;overflow:auto;border:1px solid var(--line);border-radius:10px}
.pill{display:inline-block;font-size:11px;padding:2px 8px;border-radius:20px;background:#eaf5fc;color:#1b7fb8;border:1px solid #cfe7f5}
.bars{display:grid;grid-template-columns:repeat(auto-fit,minmax(215px,1fr));gap:12px;margin-bottom:18px}
.bcard{background:linear-gradient(180deg,#fbfdff,#eef7fc);border:1px solid var(--line);border-radius:11px;padding:14px 15px}
.bcard .lbl{font-size:12.5px;color:var(--muted);min-height:32px}
.bcard .val{font-size:19px;font-weight:700;color:#12587d;margin-top:4px;font-variant-numeric:tabular-nums}
.bcard .pct{font-size:12px;color:var(--muted);margin-top:3px}
.bcard.big .val{font-size:22px}
.bwrap{background:#fff;border:1px solid var(--line);border-radius:12px;padding:10px 8px;overflow:auto}
svg .bar{fill:url(#gr);transition:.15s}
svg .bar:hover{fill:#12587d}
svg .gline{stroke:var(--line);stroke-width:1;stroke-dasharray:3 4}
svg .glab{font-size:11px;fill:var(--muted)}
svg .bmon{font-size:11.5px;fill:#547082}
svg .bval{font-size:12.5px;fill:#0f4f70;font-weight:700}
ul{margin:6px 0 0;padding-left:18px}
li{margin-bottom:5px}
.callout{border-left:3px solid var(--acc);background:var(--soft);padding:10px 14px;border-radius:0 8px 8px 0;margin-top:10px;font-size:13.5px}
.badge{display:inline-block;font-size:10.5px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;
  background:#e8f4fb;color:#17729f;border:1px solid #c8e3f2;border-radius:5px;padding:2px 7px;margin-left:8px;vertical-align:middle}
.badge.hi{background:#fdeeee;color:#a33;border-color:#f3cfcf}
.badge.mid{background:#fdf6e7;color:#8a6209;border-color:#f0e0bb}
.badge.ok{background:#eaf7f0;color:#1c7a52;border-color:#c9e8d8}
.concl{border:1px solid var(--line);border-radius:11px;padding:14px 16px;margin-bottom:12px;background:#fff}
.concl.p{border-color:#f3d3d3;background:#fef8f8}
.concl.r{border-color:#f0e0bb;background:#fffdf6}
.concl.s{border-color:#c9e8d8;background:#f6fdf9}
.concl h4{margin:0 0 8px;font-size:14px;display:flex;align-items:center;gap:8px}
footer{margin-top:26px;color:var(--muted);font-size:12.5px;text-align:center}
.tooltip{position:fixed;pointer-events:none;background:#0f3c54;color:#fff;font-size:12px;padding:5px 9px;border-radius:6px;opacity:0;transition:.12s;z-index:9}
.empty{padding:18px;color:var(--muted);font-size:13.5px}
@media(max-width:720px){.wrap{padding:16px 12px 48px}h1{font-size:19px}select{min-width:0;width:100%}.tblwrap{max-height:none}}
</style>
</head>
<body>
<div class="wrap">
<header class="top">
  <h1>Хаб 2.0 для РубАрх — ресурсная модель и бюджет</h1>
  <div class="sub">Термостат RS485 · версия документа 1.3 · горизонт планирования: окт 2026 — сен 2027</div>
  <div class="meta">Источник: файл «Трудозатраты Хаб 2.0 для РубАрх_ver.1.3.xlsx», лист «Термостат RS485». Все суммы — в рублях. Блоки, отмеченные <span class="badge">данные от ИИ</span>, сгенерированы по результатам анализа данных файла.</div>
</header>

<div class="switch" role="tablist">
  <button id="tRes" class="on" onclick="setMode('res')">Ресурсы</button>
  <button id="tBud" onclick="setMode('bud')">Бюджет</button>
</div>

<!-- ================= RESOURCES ================= -->
<section class="mode on" id="mRes">
  <div class="card">
    <h2>Фильтр по ресурсу</h2>
    <div class="hint">Выберите ресурс, чтобы отфильтровать таблицу трудозатрат. Значение «Все ресурсы» показывает полный состав.</div>
    <label for="resSel" class="hint">Ресурс</label><br>
    <select id="resSel" onchange="filterRes()">
      <option value="">Все ресурсы</option>
    </select>
    <div class="callout" id="resInfo">Показаны все ресурсы проекта.</div>
  </div>

  <div class="card">
    <h2>Таблица ресурсов</h2>
    <div class="hint">Профили команды, загрузка в человеко-месяцах (чел/мес) и стоимость по документу. Ставка: ПАО — 700 000 руб./чел-мес, ДЗО — 1 000 000 руб./чел-мес (по данным файла).</div>
    <div class="tblwrap">
      <table id="resTbl">
        <thead><tr>
          <th>Профиль / роль</th><th>Направление</th><th>В штате</th>
          <th class="num">Чел/мес</th><th class="num">Ставка, руб.</th><th class="num">Стоимость, руб.</th>
        </tr></thead>
        <tbody></tbody>
        <tfoot><tr><td colspan="3">Итого по показанным</td><td class="num" id="fQ">—</td><td></td><td class="num" id="fC">—</td></tr></tfoot>
      </table>
    </div>
  </div>

  <div class="card">
    <h2>Основные выводы по распределению ресурсов <span class="badge hi">данные от ИИ</span></h2>
    <div class="concl p">
      <h4>Проблемы</h4>
      <ul>
        <li>Совокупная потребность <b>76.7 чел/мес</b> при пиковой одновременной загрузке до <b>10.0 условных ставок</b> в месяц — ресурс распределён неравномерно.</li>
        <li>Две трети объёма сосредоточены в трёх направлениях: Management, Ядро/Moira и QA — остальные 6 направлений вместе дают менее трети трудозатрат.</li>
        <li>Значительная часть профилей помечена как «не в штате» (GTM, Marketing, PR, Редакция, Go scenarios, GO Agent WB и др.) — их трудозатраты в файле не оценены.</li>
      </ul>
    </div>
    <div class="concl r">
      <h4>Риски</h4>
      <ul>
        <li>Пик загрузки приходится на январь—июнь 2027 — риск конкуренции за одни и те же роли (TPM, QA, дизайн) в смежных проектах.</li>
        <li>Ключевые компетенции завязаны на узкие команды (ядро/Moira, Salute/SHBE, Chamber) — выпадение одной команды критично.</li>
        <li>Доля управления (Management ~27% ФОТ) высока относительно исполнительских направлений.</li>
      </ul>
    </div>
    <div class="concl s">
      <h4>Сходимость</h4>
      <ul>
        <li>Расчётные трудозатраты из таблицы сходятся с итогом файла: строки «Total ставки» (76,75 чел/мес) и стоимость ФОТ <b>56 875 000 руб.</b>.</li>
        <li>Разбивка по направлениям и по месяцам взаимно согласована — сумма месячных затрат равна годовому ФОТ.</li>
      </ul>
    </div>
  </div>
</section>

<!-- ================= BUDGET ================= -->
<section class="mode" id="mBud">
  <div class="card">
    <h2>Общие затраты по категориям</h2>
    <div class="hint">Структура бюджета проекта по данным файла. ФОТ рассчитан умножением трудозатрат на ставку соответствующего контура.</div>
    <div class="bars">
      <div class="bcard big"><div class="lbl">ФОТ (оплата труда)</div><div class="val">56 875 000 руб.</div><div class="pct">94% всех затрат</div></div>
      <div class="bcard"><div class="lbl">NRE</div><div class="val">1 000 000 руб.</div><div class="pct">разовые инженерные затраты</div></div>
      <div class="bcard"><div class="lbl">Стенды, образцы, командировки</div><div class="val">1 500 000 руб.</div><div class="pct">инфраструктура и образцы</div></div>
      <div class="bcard"><div class="lbl">Материалы (пресс-формы)</div><div class="val">0 руб.</div><div class="pct">по данным файла</div></div>
      <div class="bcard"><div class="lbl">Иное / резерв</div><div class="val">1 000 000 руб.</div><div class="pct">резерв проекта</div></div>
      <div class="bcard"><div class="lbl">Маркетинг</div><div class="val">0 руб.</div><div class="pct">не включён в расчёт</div></div>
      <div class="bcard big"><div class="lbl">ИТОГО по проекту</div><div class="val">60 375 000 руб.</div><div class="pct">с учётом доп. затрат 3 500 000 руб.</div></div>
    </div>
  </div>

  <div class="card">
    <h2>Помесячные затраты</h2>
    <div class="hint">Ось X — время, ось Y — стоимость (млн руб.). Значения рассчитаны по загрузке профилей и их ставкам; максимум — 7 030 000 руб. в 05.2027.</div>
    <div class="bwrap">
      <svg viewBox="0 0 880 340" width="100%" height="340" role="img" aria-label="График помесячных затрат">
        <defs><linearGradient id="gr" x1="0" y1="0" x2="0" y2="1">
          <stop offset="0" stop-color="#4fb4e0"/><stop offset="1" stop-color="#1b7fb8"/></linearGradient></defs>
        <line class="gline" x1="70" y1="294.0" x2="860" y2="294.0"/><text class="glab" x="62" y="298.0" text-anchor="end">0.0 млн</text><line class="gline" x1="70" y1="225.5" x2="860" y2="225.5"/><text class="glab" x="62" y="229.5" text-anchor="end">1.8 млн</text><line class="gline" x1="70" y1="157.0" x2="860" y2="157.0"/><text class="glab" x="62" y="161.0" text-anchor="end">3.5 млн</text><line class="gline" x1="70" y1="88.5" x2="860" y2="88.5"/><text class="glab" x="62" y="92.5" text-anchor="end">5.3 млн</text><line class="gline" x1="70" y1="20.0" x2="860" y2="20.0"/><text class="glab" x="62" y="24.0" text-anchor="end">7.0 млн</text>
        <line x1="70" y1="294" x2="860" y2="294" stroke="#bcd8e8"/>
        <rect class="bar" x="82.5" y="248.4" width="40.8" height="45.6" rx="3" data-full="1 170 000" data-m="10.2026"></rect><text class="bval" x="102.9" y="242.4" text-anchor="middle">1170т</text><text class="bmon" x="102.9" y="310" text-anchor="middle">окт 26</text><rect class="bar" x="148.3" y="212.9" width="40.8" height="81.1" rx="3" data-full="2 080 000" data-m="11.2026"></rect><text class="bval" x="168.8" y="206.9" text-anchor="middle">2080т</text><text class="bmon" x="168.8" y="310" text-anchor="middle">ноя 26</text><rect class="bar" x="214.2" y="168.5" width="40.8" height="125.5" rx="3" data-full="3 220 000" data-m="12.2026"></rect><text class="bval" x="234.6" y="162.5" text-anchor="middle">3220т</text><text class="bmon" x="234.6" y="310" text-anchor="middle">дек 26</text><rect class="bar" x="280.0" y="92.7" width="40.8" height="201.3" rx="3" data-full="5 165 000" data-m="01.2027"></rect><text class="bval" x="300.4" y="86.7" text-anchor="middle">5165т</text><text class="bmon" x="300.4" y="310" text-anchor="middle">янв 27</text><rect class="bar" x="345.8" y="26.6" width="40.8" height="267.4" rx="3" data-full="6 860 000" data-m="02.2027"></rect><text class="bval" x="366.2" y="20.6" text-anchor="middle">6860т</text><text class="bmon" x="366.2" y="310" text-anchor="middle">фев 27</text><rect class="bar" x="411.7" y="23.9" width="40.8" height="270.1" rx="3" data-full="6 930 000" data-m="03.2027"></rect><text class="bval" x="432.1" y="17.9" text-anchor="middle">6930т</text><text class="bmon" x="432.1" y="310" text-anchor="middle">мар 27</text><rect class="bar" x="477.5" y="30.3" width="40.8" height="263.7" rx="3" data-full="6 765 000" data-m="04.2027"></rect><text class="bval" x="497.9" y="24.3" text-anchor="middle">6765т</text><text class="bmon" x="497.9" y="310" text-anchor="middle">апр 27</text><rect class="bar" x="543.3" y="20.0" width="40.8" height="274.0" rx="3" data-full="7 030 000" data-m="05.2027"></rect><text class="bval" x="563.8" y="14.0" text-anchor="middle">7030т</text><text class="bmon" x="563.8" y="310" text-anchor="middle">май 27</text><rect class="bar" x="609.2" y="25.5" width="40.8" height="268.5" rx="3" data-full="6 890 000" data-m="06.2027"></rect><text class="bval" x="629.6" y="19.5" text-anchor="middle">6890т</text><text class="bmon" x="629.6" y="310" text-anchor="middle">июн 27</text><rect class="bar" x="675.0" y="105.9" width="40.8" height="188.1" rx="3" data-full="4 825 000" data-m="07.2027"></rect><text class="bval" x="695.4" y="99.9" text-anchor="middle">4825т</text><text class="bmon" x="695.4" y="310" text-anchor="middle">июл 27</text><rect class="bar" x="740.8" y="155.1" width="40.8" height="138.9" rx="3" data-full="3 565 000" data-m="08.2027"></rect><text class="bval" x="761.2" y="149.1" text-anchor="middle">3565т</text><text class="bmon" x="761.2" y="310" text-anchor="middle">авг 27</text><rect class="bar" x="806.7" y="201.4" width="40.8" height="92.6" rx="3" data-full="2 375 000" data-m="09.2027"></rect><text class="bval" x="827.1" y="195.4" text-anchor="middle">2375т</text><text class="bmon" x="827.1" y="310" text-anchor="middle">сен 27</text>
      </svg>
    </div>
  </div>

  <div class="card">
    <h2>Основные выводы по бюджету и затратам <span class="badge hi">данные от ИИ</span></h2>
    <div class="concl r">
      <h4>Риски</h4>
      <ul>
        <li>ФОТ занимает 94% бюджета — проект крайне чувствителен к ставкам и численности персонала.</li>
        <li>Затраты резко растут с декабря 2026 по февраль 2027 (пик 7 030 000 руб.) — кассовый разрыв при равномерном финансировании.</li>
        <li>Доп. затраты (3 500 000 руб.) не разнесены по месяцам — фактический профиль платежей может смещаться.</li>
      </ul>
    </div>
    <div class="concl s">
      <h4>Сходимость и резервы</h4>
      <ul>
        <li>Сумма месячных затрат равна годовому ФОТ 56 875 000 руб.; вместе с доп. затратами итог совпадает со строкой «ТОТАЛ» файла — 60 375 000 руб..</li>
        <li>Резерв «Иное / резерв» и NRE (2 000 000 руб.) формируют буфер на непредвиденные работы.</li>
      </ul>
    </div>
    <div class="concl p">
      <h4>Проблемы</h4>
      <ul>
        <li>Около 60% затрат приходится на 5 месяцев пика — требуется синхронизация с sourcing и производством.</li>
        <li>Затраты на материалы и маркетинг в документе равны нулю — при уточнении объёмов бюджет вырастет.</li>
      </ul>
    </div>
  </div>
</section>

<footer>Документ сгенерирован из xlsx-источника · суммы в рублях · блоки «данные от ИИ» построены на основе анализа файла</footer>
</div>
<div class="tooltip" id="tip"></div>
<script>
const ROWS=[{"n": "Lead  / System analist (Шапкин)", "c": "Ядро / Moira team", "s": "да", "q": "2.0", "r": "700 000", "cost": "1 400 000"}, {"n": "Connectivity Team (команда Шапкина)", "c": "Ядро / Moira team", "s": "да", "q": "17.0", "r": "700 000", "cost": "11 900 000"}, {"n": "HW/FW QA (мануал тест)", "c": "QA", "s": "да", "q": "7.6", "r": "700 000", "cost": "5 320 000"}, {"n": "HW/FW QA автом. тест (грубо)", "c": "QA", "s": "да", "q": "2.4", "r": "700 000", "cost": "1 680 000"}, {"n": "SW QA", "c": "QA", "s": "да", "q": "1.7", "r": "700 000", "cost": "1 190 000"}, {"n": "SZ engineers team", "c": "QA", "s": "да", "q": "4.0", "r": "700 000", "cost": "2 800 000"}, {"n": "Сорсинг manager", "c": "Сорсинг", "s": "да", "q": "1.7", "r": "700 000", "cost": "1 190 000"}, {"n": "Production manager", "c": "Production", "s": "да", "q": "1.8", "r": "700 000", "cost": "1 260 000"}, {"n": "Logistic", "c": "Production", "s": "да", "q": "0.1", "r": "700 000", "cost": "105 000"}, {"n": "Tech writer", "c": "Other", "s": "да", "q": "0.5", "r": "700 000", "cost": "350 000"}, {"n": "Constructive designer", "c": "Package", "s": "да", "q": "0.8", "r": "700 000", "cost": "525 000"}, {"n": "Digital designer", "c": "Package", "s": "да", "q": "1.1", "r": "700 000", "cost": "770 000"}, {"n": "Package tech writer", "c": "Package", "s": "да", "q": "0.8", "r": "700 000", "cost": "595 000"}, {"n": "Product Owner", "c": "Management", "s": "да", "q": "3.5", "r": "700 000", "cost": "2 450 000"}, {"n": "LPM", "c": "Management", "s": "да", "q": "4.2", "r": "700 000", "cost": "2 940 000"}, {"n": "SW TPM", "c": "Management", "s": "да", "q": "4.5", "r": "700 000", "cost": "3 150 000"}, {"n": "HW TPM", "c": "Management", "s": "да", "q": "5.1", "r": "700 000", "cost": "3 570 000"}, {"n": "SZ team (Midas + Elling)", "c": "Management", "s": "да", "q": "4.9", "r": "700 000", "cost": "3 430 000"}, {"n": "PO Salute", "c": "Salute / SHBE", "s": "да", "q": "0.9", "r": "1 000 000", "cost": "900 000"}, {"n": "System Analyst", "c": "Salute / SHBE", "s": "да", "q": "0.3", "r": "1 000 000", "cost": "300 000"}, {"n": "Android", "c": "Salute / SHBE", "s": "да", "q": "0.5", "r": "1 000 000", "cost": "500 000"}, {"n": "iOS", "c": "Salute / SHBE", "s": "да", "q": "0.5", "r": "1 000 000", "cost": "500 000"}, {"n": "Frontend", "c": "Salute / SHBE", "s": "да", "q": "1.5", "r": "1 000 000", "cost": "1 500 000"}, {"n": "Go scenarios", "c": "Salute / SHBE", "s": "—", "q": "2.1", "r": "1 000 000", "cost": "2 100 000"}, {"n": "Designer", "c": "Salute / SHBE", "s": "да", "q": "0.3", "r": "1 000 000", "cost": "300 000"}, {"n": "Go Core", "c": "Salute / SHBE", "s": "да", "q": "2.3", "r": "1 000 000", "cost": "2 300 000"}, {"n": "GO Agent WB", "c": "Salute / SHBE", "s": "—", "q": "2.1", "r": "1 000 000", "cost": "2 100 000"}, {"n": "Chamber specialist", "c": "Chamber", "s": "—", "q": "1.9", "r": "700 000", "cost": "1 330 000"}, {"n": "Chamber HW TPM", "c": "Chamber", "s": "—", "q": "0.6", "r": "700 000", "cost": "420 000"}];
const CRE={"Ядро / Moira team": 13300000.0, "QA": 10990000.0, "Сорсинг": 1190000.0, "Production": 1365000.0, "Other": 350000.0, "Package": 1890000.0, "Management": 15540000.0, "Salute / SHBE": 10500000.0, "Chamber": 1750000.0};
const sel=document.getElementById('resSel');
ROWS.forEach(r=>{const o=document.createElement('option');o.value=r.n;o.textContent=r.n;sel.appendChild(o);});
const tb=document.querySelector('#resTbl tbody');
function fmS(s){return s;}
function render(list){
  tb.innerHTML=list.map(r=>`<tr><td>${r.n}</td><td><span class="pill">${r.c}</span></td><td>${r.s}</td>
    <td class="num">${r.q}</td><td class="num">${r.r}</td><td class="num">${r.cost}</td></tr>`).join('');
  let q=0,c=0;list.forEach(r=>{q+=parseFloat(r.q);c+=parseFloat(String(r.cost).replace(/ /g,''));});
  document.getElementById('fQ').textContent=q.toFixed(1).replace('.',',');
  document.getElementById('fC').textContent=Math.round(c).toLocaleString('ru-RU');
}
render(ROWS);
function filterRes(){
  const v=sel.value;const list=v?ROWS.filter(r=>r.n===v):ROWS;render(list);
  document.getElementById('resInfo').textContent=v?`Показан ресурс «${v}» — направление: ${list[0].c}. Трудозатраты: ${list[0].q} чел/мес.`:'Показаны все ресурсы проекта.';
}
function setMode(m){
  const res=m==='res';
  document.getElementById('mRes').classList.toggle('on',res);
  document.getElementById('mBud').classList.toggle('on',!res);
  document.getElementById('tRes').classList.toggle('on',res);
  document.getElementById('tBud').classList.toggle('on',!res);
  window.scrollTo({top:0,behavior:'smooth'});
}
const tip=document.getElementById('tip');
document.querySelectorAll('svg .bar').forEach(b=>{
  b.addEventListener('mousemove',e=>{tip.style.opacity=1;tip.style.left=(e.clientX+12)+'px';tip.style.top=(e.clientY-28)+'px';
    tip.textContent=b.dataset.m+': '+b.dataset.full+' руб.';});
  b.addEventListener('mouseleave',()=>tip.style.opacity=0);
});
</script>
</body>
</html>
