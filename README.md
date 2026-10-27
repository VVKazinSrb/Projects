<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Трудозатраты Хаб 2.0 для РубАрх — ресурсы и бюджет</title>
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
label.fld{display:block;font-weight:600;color:#1c5f81;margin-bottom:7px;font-size:13px}
table{width:100%;border-collapse:collapse;font-size:13px}
th,td{padding:8px 9px;border-bottom:1px solid var(--line);text-align:left;vertical-align:top}
th{background:var(--soft);font-size:11.5px;text-transform:uppercase;letter-spacing:.4px;color:#3d6479;position:sticky;top:0;z-index:2}
td.num,th.num{text-align:right;white-space:nowrap;font-variant-numeric:tabular-nums}
td.l,th.l{white-space:normal;min-width:200px}
tbody tr:hover{background:#f7fbfe}
tr.grp{background:var(--soft);font-weight:700}
tr.grp td{color:#12587d}
tr.totalrow{background:#e8f4fb;font-weight:700}
tr.totalrow td{color:#0f4f70;border-top:2px solid var(--line2)}
tfoot td{font-weight:700;background:var(--soft);border-top:2px solid var(--line2)}
.tblwrap{max-height:540px;overflow:auto;border:1px solid var(--line);border-radius:10px}
.pill{display:inline-block;font-size:11px;padding:2px 8px;border-radius:20px;background:#eaf5fc;color:#1b7fb8;border:1px solid #cfe7f5}
.bars{display:grid;grid-template-columns:repeat(auto-fit,minmax(215px,1fr));gap:12px;margin-bottom:6px}
.bcard{background:linear-gradient(180deg,#fbfdff,#eef7fc);border:1px solid var(--line);border-radius:11px;padding:14px 15px}
.bcard .lbl{font-size:12.5px;color:var(--muted);min-height:32px}
.bcard .val{font-size:19px;font-weight:700;color:#12587d;margin-top:4px;font-variant-numeric:tabular-nums}
.bcard .pct{font-size:12px;color:var(--muted);margin-top:3px}
.bcard.big .val{font-size:22px}
.bwrap{background:#fff;border:1px solid var(--line);border-radius:12px;padding:10px 8px;overflow:auto}
svg .bar{fill:url(#gr);transition:.15s;cursor:pointer}
svg .bar:hover{fill:#12587d}
svg .gline{stroke:var(--line);stroke-width:1;stroke-dasharray:3 4}
svg .glab{font-size:11px;fill:var(--muted)}
svg .bmon{font-size:11px;fill:#547082}
svg .bval{font-size:11.5px;fill:#0f4f70;font-weight:700}
ul{margin:6px 0 0;padding-left:18px}
li{margin-bottom:5px}
.callout{border-left:3px solid var(--acc);background:var(--soft);padding:10px 14px;border-radius:0 8px 8px 0;margin-top:12px;font-size:13.5px}
.badge{display:inline-block;font-size:10.5px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;
  background:#e8f4fb;color:#17729f;border:1px solid #c8e3f2;border-radius:5px;padding:2px 7px;margin-left:8px;vertical-align:middle}
.badge.gen{background:#eaf7f0;color:#1c7a52;border-color:#c9e8d8}
.concl{border:1px solid var(--line);border-radius:11px;padding:14px 16px;margin-bottom:12px;background:#fff}
.concl.p{border-color:#f3d3d3;background:#fef8f8}
.concl.r{border-color:#f0e0bb;background:#fffdf6}
.concl.s{border-color:#c9e8d8;background:#f6fdf9}
.concl h4{margin:0 0 8px;font-size:14px;display:flex;align-items:center;gap:8px}
.risktag{font-weight:700;color:var(--risk)}
footer{margin-top:26px;color:var(--muted);font-size:12.5px;text-align:center}
.tooltip{position:fixed;pointer-events:none;background:#0f3c54;color:#fff;font-size:12px;padding:5px 9px;border-radius:6px;opacity:0;transition:.12s;z-index:9}
@media(max-width:720px){.wrap{padding:16px 12px 48px}h1{font-size:19px}select{min-width:0;width:100%}.switch{flex-direction:column;width:100%}.switch button{width:100%}}
</style>
</head>
<body>
<div class="wrap">
<header class="top">
  <h1>Трудозатраты Хаб 2.0 для РубАрх — ресурсная модель и бюджет</h1>
  <div class="sub">Термостат RS485 · версия документа 1.4 · горизонт планирования: ноябрь 2026 — октябрь 2027</div>
  <div class="meta">Источник: файл «Трудозатраты Хаб 2.0 для РубАрх_ver.1.4.xlsx», лист «Термостат RS485». Все суммы — в рублях, ставка 700 000 руб./чел-мес. Блоки, отмеченные <span class="badge gen">сгенерировано ИИ</span>, построены по результатам анализа данных файла.</div>
</header>

<div class="switch" role="tablist">
  <button id="tRes" class="on" onclick="setMode('res')">Ресурсы</button>
  <button id="tBud" onclick="setMode('bud')">Бюджет</button>
</div>

<!-- ================= RESOURCES ================= -->
<section class="mode on" id="mRes">
  <div class="card">
    <h2>Фильтр по ресурсу</h2>
    <div class="hint">Выберите ресурс, чтобы отфильтровать таблицу трудозатрат и гистограмму ниже. Значение «Все ресурсы» показывает полный состав.</div>
    <label for="resSel" class="fld">Ресурс / направление</label>
    <select id="resSel" onchange="applyFilter()">
      <option value="__all__">Все ресурсы</option>
    </select>
    <div class="callout" id="resInfo">Показаны все ресурсы проекта.</div>
  </div>

  <div class="card">
    <h2>Таблица ресурсов</h2>
    <div class="hint" id="tblHint">Профили команды, загрузка в человеко-месяцах (чел/мес) и стоимость по документу. Ставка: ПАО — 700 000 руб./чел-мес, ДЗО — 1 000 000 руб./чел-мес (по данным файла).</div>
    <div class="tblwrap">
      <table id="resTbl">
        <thead><tr>
          <th>Профиль / роль</th><th>Направление</th><th>В штате</th>
          <th class="num">Чел/мес</th><th class="num">Ставка, руб.</th><th class="num">Стоимость, руб.</th>
        </tr></thead>
        <tbody id="resBody"></tbody>
        <tfoot><tr><td colspan="3">Итого по показанным</td><td class="num" id="fQ">—</td><td></td><td class="num" id="fC">—</td></tr></tfoot>
      </table>
    </div>
  </div>

  <div class="card">
    <h2>Гистограмма загрузки по месяцам</h2>
    <div class="hint" id="chartTitle">Ось X — месяц, ось Y — человеко-месяцы (чел/мес). Наведите курсор на столбец для точного значения.</div>
    <div class="bwrap" id="resChart"></div>
  </div>

  <div class="card">
    <h2>Выводы по распределению ресурсов <span class="badge gen">сгенерировано ИИ</span></h2>
    <div class="concl p">
      <h4>Проблемы</h4>
      <ul>
        <li>Пиковая загрузка приходится на июль—сентябрь 2027 (10,05; 7,85; 5,05 чел/мес в сводной строке) — ресурсы сжимаются в узкое окно второй половины проекта.</li>
        <li>Резкий спад после сентября 2027: с 7,85 до 3,35 чел/мес за два месяца — требуется аккуратное высвобождение команд и передача задач.</li>
        <li>Ряды без числовых значений по месяцам (GTM, Marketing, Dig.designer, PR, Редакция, PM Salute, Kotlin back, StarOS App, B2B Present PM/Go) в расчёт не включены; маркетинг в файле помечен как «не включён в расчёт».</li>
      </ul>
    </div>
    <div class="concl r">
      <h4>Риски</h4>
      <ul>
        <li><span class="risktag">Концентрация экспертизы:</span> крупнейшие группы — Management (22,5 чел/мес) и kernel/moira team (19,0 чел/мес) — формируют более половины объёма; выпадение ключевого участника бьёт по критическому пути.</li>
        <li><span class="risktag">Пиковые месяцы:</span> одновременная загрузка kernel/moira, QA, Package и Salute в июле—августе 2027 создаёт дефицит профильных специалистов.</li>
        <li><span class="risktag">Поздний старт:</span> производственные и логистические роли выходят на проект только в июле—октябре 2027, сжимая окно подготовки образцов и валидации.</li>
        <li><span class="risktag">Низкая автотестовая нагрузка:</span> HW/FW QA авт. тест идёт только февраль—июль 2027 и обрывается, тогда как ручной тест продолжается — риск ручного регресса в конце проекта.</li>
      </ul>
    </div>
    <div class="concl s">
      <h4>Сходимость</h4>
      <ul>
        <li>Сумма по месяцам сводной строки составляет 78,95 чел/мес и в точности совпадает с итогом файла — расхождения между помесячной разбивкой и итогом нет.</li>
        <li>Итог по ресурсам (78,95 чел/мес) за вычетом строк kernel/moira (19,0) и Management (22,5) показывает, что исполнительские команды суммарно сопоставимы с управленческим блоком.</li>
        <li>Профиль загрузки описывает классическую кривую разработки: разгон ноябрь 2026 — апрель 2027, плато, пик середины проекта, спад к октябрю 2027.</li>
      </ul>
    </div>
  </div>
</section>

<!-- ================= BUDGET ================= -->
<section class="mode" id="mBud">
  <div class="card">
    <h2>Общие затраты по категориям</h2>
    <div class="hint">Структура бюджета по данным файла. ФОТ рассчитан умножением трудозатрат на ставку 700 000 руб./чел-мес.</div>
    <div class="bars">
      <div class="bcard big"><div class="lbl">ФОТ (оплата труда)</div><div class="val">55 265 000 руб.</div><div class="pct">трудозатраты × ставка</div></div>
      <div class="bcard big"><div class="lbl">ИТОГО по проекту</div><div class="val">63 265 000 руб.</div><div class="pct">строка «ТОТАЛ» файла</div></div>
    </div>
    <div class="bars" style="margin-top:12px">
      <div class="bcard"><div class="lbl">NRE</div><div class="val">1 000 000 руб.</div><div class="pct">по данным файла</div></div>
      <div class="bcard"><div class="lbl">Пресс-формы</div><div class="val">4 500 000 руб.</div><div class="pct">по данным файла</div></div>
      <div class="bcard"><div class="lbl">Стенды, образцы, командировки</div><div class="val">1 500 000 руб.</div><div class="pct">по данным файла</div></div>
      <div class="bcard"><div class="lbl">Иное / резерв</div><div class="val">1 000 000 руб.</div><div class="pct">по данным файла</div></div>
    </div>
    <div class="bars" style="margin-top:12px">
      <div class="bcard"><div class="lbl">Доп. затраты (всего)</div><div class="val">8 000 000 руб.</div><div class="pct">12,6% от итога</div></div>
      <div class="bcard"><div class="lbl">Трудозатраты</div><div class="val">78,95 чел/мес</div><div class="pct">итог файла по месяцам</div></div>
    </div>
  </div>

  <div class="card">
    <h2>Помесячные затраты</h2>
    <div class="hint">Ось X — время, ось Y — стоимость (млн руб.). Значения рассчитаны по загрузке и ставке файла; максимум — 7 035 000 руб. в июле 2027.</div>
    <div class="bwrap" id="budChart"></div>
  </div>

  <div class="card">
    <h2>Выводы по бюджету и затратам <span class="badge gen">сгенерировано ИИ</span></h2>
    <div class="concl p">
      <h4>Структура затрат</h4>
      <ul>
        <li>ФОТ (55 265 000 руб.) формирует основную часть бюджета, доп. затраты (8 000 000 руб.) — около 13% от итоговых 63 265 000 руб.</li>
        <li>Крупнейшая статья доп. затрат — пресс-формы (4 500 000 руб.), далее NRE и стенды/образцы/командировки — 1 000 000 и 1 500 000 руб.</li>
        <li>Статья «Иное / резерв» (1 000 000 руб.) заложена на непредвиденные расходы; маркетинг в расчёт не включён (0 руб.).</li>
      </ul>
    </div>
    <div class="concl r">
      <h4>Риски</h4>
      <ul>
        <li><span class="risktag">Пиковая стоимость:</span> максимум затрат приходится на месяцы максимальной загрузки — перенос сроков середины проекта сразу повышает стоимость.</li>
        <li><span class="risktag">Доп. затраты с фиксированной суммой:</span> пресс-формы и NRE не масштабируются вместе с ФОТ и являются отдельным бюджетным риском при сдвиге сроков.</li>
        <li><span class="risktag">Резерв 1 000 000 руб.</span> покрывает лишь небольшую долю проекта — при существенном смещении графика может быть израсходован досрочно.</li>
      </ul>
    </div>
    <div class="concl s">
      <h4>Сходимость</h4>
      <ul>
        <li>Сумма помесячных затрат в точности равна ФОТ из файла — 55 265 000 руб.; расчёт сходится с источником.</li>
        <li>ФОТ + доп. затраты = 63 265 000 руб., что совпадает со значением «ТОТАЛ» в документе.</li>
        <li>Ставка 700 000 руб. за человеко-месяц применяется единообразно ко всем ресурсам.</li>
      </ul>
    </div>
  </div>
</section>

<footer>Собрано из xlsx-источника · суммы в рублях · блоки «сгенерировано ИИ» построены на основе анализа файла</footer>
</div>
<div class="tooltip" id="tip"></div>
<script>
const D={"months":["Ноя 2026","Дек 2026","Янв 2027","Фев 2027","Мар 2027","Апр 2027","Май 2027","Июн 2027","Июл 2027","Авг 2027","Сен 2027","Окт 2027"],"rows":[{"name":"kernel/moira team","group":null,"m":[0.0,0.0,2.2,2.2,2.2,2.2,2.2,2.2,2.2,1.2,1.2,1.2],"total":19.0},{"name":"Lead / System analist (Шапкин)","group":"kernel/moira team","m":[0.0,0.0,0.2,0.2,0.2,0.2,0.2,0.2,0.2,0.2,0.2,0.2],"total":2.0},{"name":"Connectivity Team (команда Шапкина)","group":"kernel/moira team","m":[0.0,0.0,2.0,2.0,2.0,2.0,2.0,2.0,2.0,1.0,1.0,1.0],"total":17.0},{"name":"QA","group":null,"m":[0.0,0.0,0.2,1.9,1.9,2.1,2.2,2.2,2.2,1.8,0.8,0.4],"total":15.7},{"name":"HW/FW QA (мануал тест)","group":"QA","m":[0.0,0.0,0.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,0.3,0.3],"total":7.6},{"name":"HW/FW QA автом. тест (грубо)","group":"QA","m":[0.0,0.0,0.0,0.4,0.4,0.4,0.4,0.4,0.4,0.0,0.0,0.0],"total":2.4},{"name":"SW QA","group":"QA","m":[0.0,0.0,0.0,0.0,0.0,0.2,0.3,0.3,0.3,0.3,0.3,0.0],"total":1.7},{"name":"SZ engineers team","group":null,"m":[0.0,0.0,0.2,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.2,0.1],"total":4.0},{"name":"Сорсинг","group":null,"m":[0.5,0.4,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.0],"total":1.8},{"name":"Сорсинг manager","group":"Сорсинг","m":[0.5,0.4,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.1,0.0],"total":1.8},{"name":"Production","group":null,"m":[0.05,0.05,0.05,0.05,0.05,0.1,0.1,0.3,0.3,0.45,0.35,0.15],"total":2.0},{"name":"Production manager","group":"Production","m":[0.05,0.05,0.05,0.05,0.05,0.1,0.1,0.3,0.3,0.4,0.3,0.1],"total":1.85},{"name":"Logistic","group":"Production","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.05,0.05,0.05],"total":0.15},{"name":"Other","group":null,"m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.25,0.25,0.25,0.0],"total":0.75},{"name":"Tech writer","group":"Other","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.25,0.25,0.25,0.0],"total":0.75},{"name":"Package","group":null,"m":[0.0,0.0,0.0,0.0,0.95,0.7,0.4,0.25,0.4,0.4,0.0,0.0],"total":3.1},{"name":"Constructive designer","group":"Package","m":[0.0,0.0,0.0,0.0,0.3,0.2,0.05,0.1,0.1,0.1,0.0,0.0],"total":0.85},{"name":"Digital designer","group":"Package","m":[0.0,0.0,0.0,0.0,0.15,0.4,0.25,0.1,0.2,0.2,0.0,0.0],"total":1.3},{"name":"Package tech writer","group":"Package","m":[0.0,0.0,0.0,0.0,0.5,0.1,0.1,0.05,0.1,0.1,0.0,0.0],"total":0.95},{"name":"Management","group":null,"m":[1.0,1.9,1.8,1.8,1.8,1.9,2.0,2.1,2.2,2.35,2.15,1.5],"total":22.5},{"name":"Product Owner","group":"Management","m":[0.5,0.5,0.4,0.2,0.2,0.2,0.2,0.2,0.2,0.35,0.35,0.2],"total":3.5},{"name":"LPM","group":"Management","m":[0.3,0.5,0.4,0.3,0.3,0.3,0.4,0.4,0.4,0.5,0.5,0.1],"total":4.4},{"name":"SW TPM","group":"Management","m":[0.1,0.2,0.3,0.3,0.3,0.4,0.4,0.5,0.6,0.5,0.5,0.5],"total":4.6},{"name":"HW TPM","group":"Management","m":[0.1,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.3,0.2],"total":5.1},{"name":"GTM","group":"Management","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"SZ team (Midas + Elling)","group":"Management","m":[0.0,0.2,0.2,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5],"total":4.9},{"name":"GTM Stream","group":null,"m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Marketing","group":"GTM Stream","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Dig.designer","group":"GTM Stream","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"PR","group":"GTM Stream","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Редакция","group":"GTM Stream","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","group":null,"m":[0.4,0.4,0.0,0.3,1.9,1.8,1.9,1.5,1.5,0.5,0.1,0.1],"total":10.4},{"name":"PO Salute","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.1,0.2,0.1,0.1,0.1,0.1,0.1,0.1,0.1],"total":1.0},{"name":"PM Salute","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"System Analyst","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.1,0.1,0.1,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.3},{"name":"Android","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.1,0.1,0.1,0.1,0.1,0.1,0.0,0.0],"total":0.6},{"name":"iOS","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.1,0.1,0.1,0.1,0.1,0.1,0.0,0.0],"total":0.6},{"name":"Kotlin back","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Frontend","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.3,0.3,0.3,0.3,0.3,0.1,0.0,0.0],"total":1.6},{"name":"Go scenarios","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.5,0.5,0.5,0.3,0.3,0.0,0.0,0.0],"total":2.1},{"name":"StarOS App","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Designer","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.1,0.1,0.1,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.3},{"name":"Go Core","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.4,0.4,0.0,0.0,0.0,0.0,0.3,0.3,0.3,0.1,0.0,0.0],"total":1.8},{"name":"GO Agent WB","group":"Salute(Исаева Мария)/SHBE (Вадим Трегубов)","m":[0.0,0.0,0.0,0.0,0.5,0.5,0.5,0.3,0.3,0.0,0.0,0.0],"total":2.1},{"name":"Extra","group":null,"m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"B2B Present PM","group":"Extra","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"B2B Present Go","group":"Extra","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"total":0.0},{"name":"Chamber (Телешов)","group":null,"m":[0.0,0.0,0.0,0.0,0.0,0.1,0.2,0.7,0.7,0.7,0.1,0.0],"total":2.5},{"name":"Chamber specialist","group":"Chamber (Телешов)","m":[0.0,0.0,0.0,0.0,0.0,0.1,0.2,0.5,0.5,0.5,0.1,0.0],"total":1.9},{"name":"Chamber HW TPM","group":"Chamber (Телешов)","m":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.2,0.2,0.2,0.0,0.0],"total":0.6},{"name":"RnD","group":null,"m":[0.0,0.0,0.0,0.0,0.1,0.2,0.3,0.3,0.2,0.1,0.0,0.0],"total":1.2},{"name":"Валидация образцов,PRD, HW","group":"RnD","m":[0.0,0.0,0.0,0.0,0.1,0.2,0.3,0.3,0.2,0.1,0.0,0.0],"total":1.2}],"total":[1.95,2.75,4.35,6.35,9.0,9.2,9.4,9.65,10.05,7.85,5.05,3.35],"group_fot":{"kernel/moira team":13299999.999999998,"QA":10990000,"Сорсинг":1260000.0000000005,"Production":1400000,"Other":525000,"Package":2169999.9999999995,"Management":15750000,"GTM Stream":0,"Salute(Исаева Мария)/SHBE (Вадим Трегубов)":7280000,"Extra":0,"Chamber (Телешов)":1750000,"RnD":840000.0000000001},"group_total":{"kernel/moira team":19.0,"QA":15.7,"Сорсинг":1.8,"Production":2.0,"Other":0.75,"Package":3.1,"Management":22.5,"GTM Stream":0.0,"Salute(Исаева Мария)/SHBE (Вадим Трегубов)":10.4,"Extra":0.0,"Chamber (Телешов)":2.5,"RnD":1.2,"SZ engineers team":0.07},"rate":700000,"budget_month":[1365000,1925000,3045000,4445000,6300000,6440000,6580000,6755000,7035000,5495000,3535000,2345000],"fot_total":55265000,"total_all":63265000,"extra":[["NRE",1000000],["Пресс-формы",4500000],["Стенды, образцы, командировки",1500000],["Маркетинг (по необходимости)",0],["Иное / резерв",1000000]],"extra_sum":8000000};
const MONTHS=D.months;
const fmt=v=>(v===null||v===undefined)?"—":(v===0?"0":(Math.round(v*100)/100).toString().replace(".",","));
const money=v=>Math.round(v).toString().replace(/\B(?=(\d{3})+(?!\d))/g," ");
const monLab=m=>{const[a,b]=m.split(" ");return a.toLowerCase()+" "+b.slice(2);};
const monNum=m=>{const[a,b]=m.split(" ");const i=["янв","фев","мар","апр","май","июн","июл","авг","сен","окт","ноя","дек"].indexOf(a);return String(i+1).padStart(2,"0")+"."+b;};

const AX=70,BX=860,YB=294,YT=20;
function svgChart(el,values,o){
  const n=values.length,step=(BX-AX)/n,bw=Math.min(40.8,step-9);
  const gid=o.gid||"gr";
  let vmax=Math.max.apply(null,values.concat([o.floor||0.0001]));
  if(o.axMax)vmax=o.axMax;
  let s='<svg viewBox="0 0 880 340" width="100%" height="340" role="img" aria-label="'+o.aria+'">'+
    '<defs><linearGradient id="'+gid+'" x1="0" y1="0" x2="0" y2="1">'+
    '<stop offset="0" stop-color="#4fb4e0"/><stop offset="1" stop-color="#1b7fb8"/></linearGradient></defs>';
  for(let i=0;i<=4;i++){
    const y=YB-(YB-YT)*i/4;
    s+='<line class="gline" x1="'+AX+'" y1="'+y.toFixed(1)+'" x2="'+BX+'" y2="'+y.toFixed(1)+'"/>'+
       '<text class="glab" x="62" y="'+(y+3.8).toFixed(1)+'" text-anchor="end">'+o.axis(vmax*i/4)+'</text>';
  }
  s+='<line x1="'+AX+'" y1="'+YB+'" x2="'+BX+'" y2="'+YB+'" stroke="#bcd8e8"/>';
  values.forEach((v,i)=>{
    const h=Math.max(1.5,v/vmax*(YB-YT)),y=YB-h;
    const x=AX+step*i+(step-bw)/2,cx=x+bw/2;
    s+='<rect class="bar" style="fill:url(#'+gid+')" x="'+x.toFixed(1)+'" y="'+y.toFixed(1)+'" width="'+bw.toFixed(1)+'" height="'+h.toFixed(1)+'" rx="3" data-full="'+o.full(v)+'" data-m="'+o.m(i)+'"></rect>'+
       '<text class="bval" x="'+cx.toFixed(1)+'" y="'+(y-5.5).toFixed(1)+'" text-anchor="middle">'+o.val(v)+'</text>'+
       '<text class="bmon" x="'+cx.toFixed(1)+'" y="310" text-anchor="middle">'+o.mon(i)+'</text>';
  });
  el.innerHTML=s+'</svg>';
}

/* ---------- вкладки ---------- */
function setMode(m){
  const res=m==="res";
  document.getElementById("mRes").classList.toggle("on",res);
  document.getElementById("mBud").classList.toggle("on",!res);
  document.getElementById("tRes").classList.toggle("on",res);
  document.getElementById("tBud").classList.toggle("on",!res);
  window.scrollTo({top:0,behavior:"smooth"});
}

/* ---------- таблица ресурсов ---------- */
const DIRMAP={
  "kernel/moira team":"Ядро / Moira team",
  "Salute(Исаева Мария)/SHBE (Вадим Трегубов)":"Salute / SHBE",
  "Chamber (Телешов)":"Chamber"
};
const dirOf=g=>DIRMAP[g]||g;
const DZO="Salute(Исаева Мария)/SHBE (Вадим Трегубов)";
const NO_STAFF=["Go scenarios","GO Agent WB","Chamber specialist","Chamber HW TPM"];
const RATE_PAO=700000,RATE_DZO=1000000;

/* плоский список ролей: дети групп + самостоятельные роли без вложенных */
const ROLES=[];
D.rows.filter(r=>r.group).forEach(r=>ROLES.push({
  n:r.name,dir:dirOf(r.group),m:r.m,q:r.total,
  rate:r.group===DZO?RATE_DZO:RATE_PAO,staff:NO_STAFF.includes(r.name)?"—":"да"
}));
D.rows.filter(r=>!r.group&&!D.rows.some(x=>x.group===r.name)).forEach(r=>ROLES.push({
  n:r.name,dir:"QA",m:r.m,q:r.total,rate:RATE_PAO,staff:NO_STAFF.includes(r.name)?"—":"да"
}));
const _all=ROLES.splice(0,ROLES.length);
_all.filter(r=>r.q>0).forEach(r=>ROLES.push(r));
ROLES.forEach(r=>r.cost=r.q*r.rate);
const DIRS=[...new Set(ROLES.map(r=>r.dir))];

const rowHtml=r=>'<tr><td class="l">'+r.n+'</td><td><span class="pill">'+r.dir+'</span></td>'+
  '<td>'+r.staff+'</td><td class="num">'+fmt(r.q)+'</td>'+
  '<td class="num">'+money(r.rate)+'</td><td class="num">'+money(r.cost)+'</td></tr>';
function renderTable(f){
  const list=f==="__all__"?ROLES:ROLES.filter(r=>r.dir===f);
  document.getElementById("resBody").innerHTML=list.map(rowHtml).join("");
  document.getElementById("fQ").textContent=fmt(list.reduce((a,r)=>a+r.q,0));
  document.getElementById("fC").textContent=money(list.reduce((a,r)=>a+r.cost,0));
  const who=f==="__all__"?"Профили команды, загрузка":("Направление «"+f+"», загрузка");
  document.getElementById("tblHint").textContent=who+" в человеко-месяцах (чел/мес) и стоимость по документу. Ставка: ПАО — 700 000 руб./чел-мес, ДЗО — 1 000 000 руб./чел-мес (по данным файла).";
  document.getElementById("chartTitle").textContent=(f==="__all__"?"Загрузка всех ресурсов":"Загрузка направления «"+f+"»")+
    " по месяцам, чел/мес. Ось X — месяц, ось Y — чел/мес. Наведите курсор на столбец для точного значения.";
}
function seriesFor(f){
  if(f==="__all__")return D.total;
  return MONTHS.map((_,i)=>ROLES.filter(r=>r.dir===f).reduce((a,r)=>a+(r.m[i]||0),0));
}
function renderChart(f){
  svgChart(document.getElementById("resChart"),seriesFor(f),{
    aria:"Гистограмма загрузки по месяцам",floor:0.2,gid:"grRes",
    axis:v=>fmt(Math.round(v*10)/10),
    val:v=>fmt(v),full:v=>fmt(v)+" чел/мес",
    mon:i=>MONTHS[i],m:i=>monNum(MONTHS[i])
  });
}
function applyFilter(){
  const v=document.getElementById("resSel").value;
  renderTable(v);renderChart(v);
  const list=v==="__all__"?ROLES:ROLES.filter(r=>r.dir===v);
  document.getElementById("resInfo").textContent=v==="__all__"
    ? "Показаны все ресурсы проекта. Итог по месяцам — 78,95 чел/мес, профилей: "+ROLES.length+"."
    : "Показано направление «"+v+"»: профилей "+list.length+", трудозатраты "+fmt(list.reduce((a,r)=>a+r.q,0))+" чел/мес.";
}
(function initRes(){
  const sel=document.getElementById("resSel");
  DIRS.forEach(g=>{const o=document.createElement("option");o.value=g;o.textContent=g;sel.appendChild(o);});
  applyFilter();
})();

/* ---------- бюджет ---------- */
(function initBud(){
  svgChart(document.getElementById("budChart"),D.budget_month,{
    aria:"График помесячных затрат",axMax:Math.max.apply(null,D.budget_month),gid:"grBud",
    axis:v=>(v/1e6).toFixed(1).replace(".",",")+" млн",
    val:v=>fmt(v/1e6)+" млн.",full:v=>fmt(v/1e6)+" млн. руб.",
    mon:i=>MONTHS[i],m:i=>monNum(MONTHS[i])
  });
  const tip=document.getElementById("tip");
  document.querySelectorAll(".bwrap svg .bar").forEach(b=>{
    b.addEventListener("mousemove",e=>{
      const[v,u]=String(b.dataset.full).split(" ");
      tip.style.opacity=1;tip.style.left=(e.clientX+12)+"px";tip.style.top=(e.clientY-28)+"px";
      tip.textContent=b.dataset.m+": "+b.dataset.full;
    });
    b.addEventListener("mouseleave",()=>{tip.style.opacity=0;});
  });
})();

/* ---------- подсказки для гистограммы ресурсов ---------- */
(function wireTip(){
  const tip=document.getElementById("tip");
  document.getElementById("resChart").addEventListener("mousemove",e=>{
    const b=e.target.closest(".bar");if(!b)return;
    tip.style.opacity=1;tip.style.left=(e.clientX+12)+"px";tip.style.top=(e.clientY-28)+"px";
    tip.textContent=b.dataset.m+": "+b.dataset.full;
  });
  document.getElementById("resChart").addEventListener("mouseleave",()=>{tip.style.opacity=0;});
})();
</script>
</body>
</html>
