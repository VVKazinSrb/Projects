
# Status Реле 1 и 2 канала
IT Projects (status)
# Status Matter-лампы

//тестирование страницы
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Трудозатраты Хаб 2.0 для РубАрх — ver.1.4</title>
<style>
  :root {
    --bg: #f5f6f8;
    --card: #ffffff;
    --ink: #1c2530;
    --muted: #6b7785;
    --line: #e2e6ec;
    --accent: #2f6fed;
    --accent-soft: #eaf1fe;
    --head: #22303f;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    padding: 32px 20px 64px;
    background: var(--bg);
    color: var(--ink);
    font: 15px/1.5 -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  }
  .wrap { max-width: 1180px; margin: 0 auto; }
  header h1 { margin: 0 0 6px; font-size: 26px; letter-spacing: -.02em; }
  header p.sub { margin: 0; color: var(--muted); font-size: 14px; }
  .meta { margin: 14px 0 26px; display: flex; flex-wrap: wrap; gap: 8px; }
  .chip {
    background: var(--card); border: 1px solid var(--line); border-radius: 999px;
    padding: 5px 12px; font-size: 13px; color: var(--muted);
  }
  .chip b { color: var(--ink); font-weight: 600; }
  .kpis { display: grid; grid-template-columns: repeat(auto-fit, minmax(210px, 1fr)); gap: 14px; margin-bottom: 30px; }
  .kpi {
    background: var(--card); border: 1px solid var(--line); border-radius: 12px;
    padding: 16px 18px;
  }
  .kpi .lbl { font-size: 12px; text-transform: uppercase; letter-spacing: .06em; color: var(--muted); }
  .kpi .val { font-size: 26px; font-weight: 700; margin-top: 6px; }
  .kpi .hint { font-size: 12px; color: var(--muted); margin-top: 4px; }
  .kpi.hl { background: var(--accent-soft); border-color: #c9dcff; }
  .kpi.hl .val { color: var(--accent); }

  h2 { font-size: 18px; margin: 34px 0 12px; }
  .card { background: var(--card); border: 1px solid var(--line); border-radius: 12px; overflow: hidden; }
  table { width: 100%; border-collapse: collapse; }
  th, td { padding: 9px 12px; text-align: left; border-bottom: 1px solid var(--line); font-size: 14px; }
  thead th {
    background: var(--head); color: #fff; font-weight: 600; font-size: 12.5px;
    text-transform: uppercase; letter-spacing: .04em; position: sticky; top: 0;
  }
  tbody tr:nth-child(even) { background: #fafbfc; }
  tbody tr:hover { background: var(--accent-soft); }
  td.num, th.num { text-align: right; white-space: nowrap; font-variant-numeric: tabular-nums; }
  .bar { height: 7px; border-radius: 4px; background: var(--accent); display: inline-block; vertical-align: middle; }
  tfoot td { font-weight: 700; background: #eef1f5; border-top: 2px solid var(--line); }
  .team { font-weight: 600; }
  .grp td { background: #f0f3f7; font-weight: 700; font-size: 13px; text-transform: uppercase; letter-spacing: .03em; color: var(--head); }
  .note { color: var(--muted); font-size: 13px; margin: 8px 0 0; }
  ul.extras { list-style: none; padding: 0; margin: 0; }
  ul.extras li { display: flex; justify-content: space-between; padding: 10px 14px; border-bottom: 1px solid var(--line); font-size: 14px; }
  ul.extras li:last-child { border-bottom: 0; }
  ul.extras li span:last-child { font-variant-numeric: tabular-nums; font-weight: 600; }
  .foot { margin-top: 26px; color: var(--muted); font-size: 13px; }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <h1>Трудозатраты «Хаб 2.0 для РубАрх»</h1>
    <p class="sub">План по командам и месяцам · версия файла 1.4</p>
  </header>

  <div class="meta">
    <span class="chip">Период: <b>ноя 2026 — окт 2027</b></span>
    <span class="chip">Ставка: <b>700 000 ₽ / чел-мес</b></span>
    <span class="chip">Позиций команд: <b>14</b></span>
    <span class="chip">Маркетинг: <b>не в расчёте</b></span>
  </div>

  <div class="kpis">
    <div class="kpi hl">
      <div class="lbl">Итого чел/мес</div>
      <div class="val">78,95</div>
      <div class="hint">сумма по всем командам</div>
    </div>
    <div class="kpi">
      <div class="lbl">Стоимость ставок</div>
      <div class="val">55,27 млн ₽</div>
      <div class="hint">78,95 × 700 000 ₽</div>
    </div>
    <div class="kpi">
      <div class="lbl">Доп. затраты</div>
      <div class="val">7,5 млн ₽</div>
      <div class="hint">NRE, пресс-формы, стенды, резерв</div>
    </div>
    <div class="kpi hl">
      <div class="lbl">Тотал с доп. затратами</div>
      <div class="val">63,27 млн ₽</div>
      <div class="hint">55,27 + 7,5</div>
    </div>
  </div>

  <h2>Трудозатраты по командам</h2>
  <div class="card">
    <table>
      <thead>
        <tr>
          <th>Команда</th>
          <th class="num">Q4&nbsp;26</th>
          <th class="num">янв 27</th>
          <th class="num">фев 27</th>
          <th class="num">мар 27</th>
          <th class="num">апр 27</th>
          <th class="num">май 27</th>
          <th class="num">июн 27</th>
          <th class="num">июл 27</th>
          <th class="num">авг 27</th>
          <th class="num">сен 27</th>
          <th class="num">окт 27</th>
          <th class="num">Итого чел/мес</th>
          <th class="num">Стоимость, ₽</th>
          <th>Доля</th>
        </tr>
      </thead>
      <tbody>
        <tr><td class="team">kernel / moira team</td><td class="num">0</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">1,2</td><td class="num">1,2</td><td class="num">1,2</td><td class="num">19,00</td><td class="num">13 300 000</td><td><span class="bar" style="width:96px"></span></td></tr>
        <tr><td class="team">Management</td><td class="num">2,9</td><td class="num">1,8</td><td class="num">1,8</td><td class="num">1,8</td><td class="num">1,9</td><td class="num">2,0</td><td class="num">2,1</td><td class="num">2,2</td><td class="num">2,35</td><td class="num">2,15</td><td class="num">1,5</td><td class="num">22,50</td><td class="num">15 750 000</td><td><span class="bar" style="width:100%"></span></td></tr>
        <tr><td class="team">QA</td><td class="num">0</td><td class="num">0,2</td><td class="num">1,9</td><td class="num">1,9</td><td class="num">2,1</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">2,2</td><td class="num">1,8</td><td class="num">0,8</td><td class="num">0,4</td><td class="num">15,70</td><td class="num">10 990 000</td><td><span class="bar" style="width:78px"></span></td></tr>
        <tr><td class="team">Salute / SHBE</td><td class="num">0,8</td><td class="num">0,0</td><td class="num">0,3</td><td class="num">1,9</td><td class="num">1,8</td><td class="num">1,9</td><td class="num">1,5</td><td class="num">1,5</td><td class="num">0,5</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">10,40</td><td class="num">7 280 000</td><td><span class="bar" style="width:52px"></span></td></tr>
        <tr><td class="team">Package</td><td class="num">0</td><td class="num">0</td><td class="num">0,95</td><td class="num">0,7</td><td class="num">0,4</td><td class="num">0,25</td><td class="num">0,4</td><td class="num">0,4</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">3,10</td><td class="num">2 170 000</td><td><span class="bar" style="width:15px"></span></td></tr>
        <tr><td class="team">Chamber (Телешов)</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0,1</td><td class="num">0,2</td><td class="num">0,7</td><td class="num">0,7</td><td class="num">0,7</td><td class="num">0,1</td><td class="num">0</td><td class="num">0</td><td class="num">2,50</td><td class="num">1 750 000</td><td><span class="bar" style="width:13px"></span></td></tr>
        <tr><td class="team">Production</td><td class="num">0,1</td><td class="num">0,05</td><td class="num">0,05</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,3</td><td class="num">0,3</td><td class="num">0,45</td><td class="num">0,35</td><td class="num">0,15</td><td class="num">0</td><td class="num">2,00</td><td class="num">1 400 000</td><td><span class="bar" style="width:10px"></span></td></tr>
        <tr><td class="team">Сорсинг</td><td class="num">0,9</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0,1</td><td class="num">0</td><td class="num">1,80</td><td class="num">1 260 000</td><td><span class="bar" style="width:9px"></span></td></tr>
        <tr><td class="team">RnD</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0,1</td><td class="num">0,2</td><td class="num">0,3</td><td class="num">0,3</td><td class="num">0,2</td><td class="num">0,1</td><td class="num">0</td><td class="num">0</td><td class="num">1,20</td><td class="num">840 000</td><td><span class="bar" style="width:6px"></span></td></tr>
        <tr><td class="team">Other</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0</td><td class="num">0,25</td><td class="num">0,25</td><td class="num">0,25</td><td class="num">0</td><td class="num">0</td><td class="num">0,75</td><td class="num">525 000</td><td><span class="bar" style="width:4px"></span></td></tr>
        <tr><td class="team">GTM Stream</td><td class="num" colspan="11">0</td><td class="num">0</td><td class="num">0</td><td></td></tr>
      </tbody>
      <tfoot>
        <tr>
          <td>Всего ставок</td>
          <td class="num">4,70</td>
          <td class="num">4,35</td>
          <td class="num">6,35</td>
          <td class="num">9,00</td>
          <td class="num">9,20</td>
          <td class="num">9,40</td>
          <td class="num">9,65</td>
          <td class="num">10,05</td>
          <td class="num">7,85</td>
          <td class="num">5,05</td>
          <td class="num">3,35</td>
          <td class="num">78,95</td>
          <td class="num">55 265 000</td>
          <td></td>
        </tr>
      </tfoot>
    </table>
    <p class="note" style="padding:10px 14px">
      Столбец Q4 26 — суммарно ноябрь + декабрь 2026 (1,95 + 2,75 чел/мес).
      «GTM Stream» и «Marketing» вложены в отдельные строки, но по плану равны нулю.
    </p>
  </div>

  <h2>Дополнительные затраты</h2>
  <div class="card">
    <ul class="extras">
      <li><span>NRE</span><span>1 000 000 ₽</span></li>
      <li><span>Пресс-формы</span><span>4 500 000 ₽</span></li>
      <li><span>Стенды, образцы, командировки</span><span>1 500 000 ₽</span></li>
      <li><span>Маркетинг (по необходимости)</span><span>0 ₽</span></li>
      <li><span>Иное / резерв</span><span>1 000 000 ₽</span></li>
      <li><span><b>Итого доп. затраты</b></span><span>7 500 000 ₽</span></li>
    </ul>
  </div>

  <h2>Распределение по месяцам</h2>
  <div class="card">
    <table>
      <thead>
        <tr><th>Месяц</th><th class="num">Чел/мес</th><th class="num">Стоимость, ₽</th><th>Профиль нагрузки</th></tr>
      </thead>
      <tbody>
        <tr><td>Ноябрь 2026</td><td class="num">1,95</td><td class="num">1 365 000</td><td><span class="bar" style="width:19px"></span></td></tr>
        <tr><td>Декабрь 2026</td><td class="num">2,75</td><td class="num">1 925 000</td><td><span class="bar" style="width:27px"></span></td></tr>
        <tr><td>Январь 2027</td><td class="num">4,35</td><td class="num">3 045 000</td><td><span class="bar" style="width:43px"></span></td></tr>
        <tr><td>Февраль 2027</td><td class="num">6,35</td><td class="num">4 445 000</td><td><span class="bar" style="width:63px"></span></td></tr>
        <tr><td>Март 2027</td><td class="num">9,00</td><td class="num">6 300 000</td><td><span class="bar" style="width:90px"></span></td></tr>
        <tr><td>Апрель 2027</td><td class="num">9,20</td><td class="num">6 440 000</td><td><span class="bar" style="width:92px"></span></td></tr>
        <tr><td>Май 2027</td><td class="num">9,40</td><td class="num">6 580 000</td><td><span class="bar" style="width:94px"></span></td></tr>
        <tr><td>Июнь 2027</td><td class="num">9,65</td><td class="num">6 755 000</td><td><span class="bar" style="width:96px"></span></td></tr>
        <tr><td>Июль 2027</td><td class="num">10,05</td><td class="num">7 035 000</td><td><span class="bar" style="width:100%"></span></td></tr>
        <tr><td>Август 2027</td><td class="num">7,85</td><td class="num">5 495 000</td><td><span class="bar" style="width:78px"></span></td></tr>
        <tr><td>Сентябрь 2027</td><td class="num">5,05</td><td class="num">3 535 000</td><td><span class="bar" style="width:50px"></span></td></tr>
        <tr><td>Октябрь 2027</td><td class="num">3,35</td><td class="num">2 345 000</td><td><span class="bar" style="width:33px"></span></td></tr>
      </tbody>
      <tfoot>
        <tr><td>Итого</td><td class="num">78,95</td><td class="num">55 265 000</td><td></td></tr>
      </tfoot>
    </table>
  </div>

  <div class="foot">
    Источник: «Трудозатраты Хаб 2.0 для РубАрх_ver.1.4.xlsx».
    Тотал с дополнительными затратами — 63 265 000 ₽.
  </div>

</div>
</body>
</html>
