<!doctype html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Интерактивная панель: проект 22.10 (сверка) — статусы, ресурсы, риски. Источник — MSPDI-файл.">
<title>Портфель проектов · панель (сверка 22.10)</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&family=PT+Serif:wght@400;700&display=swap" rel="stylesheet">
<style>
/* Портфель проектов · панель управления. Светлый деловой стиль. */
:root{
  --paper:#f5f4ef; --card:#fffdf9; --ink:#212a3b; --ink2:#586074; --ink3:#8a90a0;
  --line:#e5dfd1; --line2:#d5cebc; --navy:#26344e; --brass:#8a6d2f;
  --ok:#15794f; --ok-bg:#e6f2eb; --ok-bd:#c8e4d2;
  --warn:#a9670a; --warn-bg:#fbf0da; --warn-bd:#ecd6ac;
  --bad:#ac282d; --bad-bg:#fae9e8; --bad-bd:#eccdcb;
  --none:#66707f; --none-bg:#edeff2; --none-bd:#dadfe5;
  --serif:"PT Serif",Georgia,serif; --sans:"IBM Plex Sans","Segoe UI",sans-serif; --mono:"IBM Plex Mono",Consolas,monospace;
}
*{box-sizing:border-box}
html{color-scheme:light}
body{margin:0;min-height:100vh;color:var(--ink);font:14.5px/1.5 var(--sans);
  background:radial-gradient(1100px 480px at 88% -8%,#eee7d8 0,transparent 60%),var(--paper);
  -webkit-font-smoothing:antialiased}
.wrap{max-width:1220px;margin:0 auto;padding:26px 24px 64px}
.mono{font-family:var(--mono);font-size:.92em}
.muted{color:var(--ink3)}
strong{color:var(--ink)}

/* Шапка */
.top{display:flex;flex-wrap:wrap;gap:20px;justify-content:space-between;align-items:flex-end;
  padding-bottom:18px;border-bottom:3px double var(--line2)}
.eyebrow{font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:var(--brass);margin-bottom:6px}
.title{font:700 clamp(26px,4vw,40px)/1.05 var(--serif);margin:0;color:var(--navy);letter-spacing:-.01em}
.meta{margin-top:9px;display:flex;flex-wrap:wrap;gap:5px 16px;font-size:12.5px;color:var(--ink2)}
.meta strong{color:var(--ink)}
.switch{display:flex;flex-direction:column;gap:6px;align-items:flex-end}
.seg{display:inline-flex;padding:3px;gap:2px;background:var(--card);border:1px solid var(--line2);border-radius:9px;box-shadow:0 1px 0 var(--line)}
.seg button{border:0;background:transparent;padding:8px 14px;border-radius:6px;cursor:pointer;
  font:600 13px/1 var(--sans);color:var(--ink2);transition:.15s}
.seg button:hover{background:#efe9db}
.seg button.on{background:var(--navy);color:#f7f5f0}
.switch .hint{font-size:11px;color:var(--ink3);letter-spacing:.04em}

/* Легенда */
.legend-bar{margin:13px 0 20px}
.legend{display:flex;flex-wrap:wrap;gap:8px 16px;align-items:center;padding:8px 12px;
  border:1px dashed var(--line2);border-radius:8px;background:#fbf9f4;font-size:12px;color:var(--ink2)}
.legend b{font:600 10.5px var(--sans);letter-spacing:.09em;text-transform:uppercase;color:var(--brass)}

/* Чипы статусов */
.chip{display:inline-flex;align-items:center;gap:6px;padding:2px 10px 2px 8px;border-radius:20px;
  font:600 11.8px var(--sans);white-space:nowrap;border:1px solid transparent}
.chip::before{content:"";width:8px;height:8px;border-radius:50%}
.s-ok{color:var(--ok);background:var(--ok-bg);border-color:var(--ok-bd)}.s-ok::before{background:var(--ok)}
.s-warn{color:var(--warn);background:var(--warn-bg);border-color:var(--warn-bd)}.s-warn::before{background:var(--warn)}
.s-bad{color:var(--bad);background:var(--bad-bg);border-color:var(--bad-bd)}.s-bad::before{background:var(--bad)}
.s-none{color:var(--none);background:var(--none-bg);border-color:var(--none-bd)}.s-none::before{background:var(--none)}
.ai{display:inline-block;margin-left:6px;padding:1px 6px;border-radius:4px;font:700 9.6px var(--sans);
  letter-spacing:.06em;text-transform:uppercase;color:#584784;background:#efecf7;border:1px solid #d8d1ec;vertical-align:1px}
.tag{display:inline-block;padding:1px 7px;border-radius:4px;margin-left:8px;font:600 10.4px var(--sans);vertical-align:1px}
.tag.cp{color:var(--bad);background:var(--bad-bg);border:1px solid var(--bad-bd)}
.tag.shift{display:block;width:max-content;margin:6px 0 0;color:var(--warn);background:var(--warn-bg);border:1px solid var(--warn-bd)}

/* KPI */
.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:14px;margin-bottom:20px}
.kpi{background:var(--card);border:1px solid var(--line);border-top:3px solid var(--ink3);
  border-radius:9px;padding:14px 16px;min-height:104px}
.kpi.ok{border-top-color:var(--ok)}.kpi.warn{border-top-color:var(--warn)}
.kpi.bad{border-top-color:var(--bad)}.kpi.none{border-top-color:var(--none)}
.kpi .l{font-size:10.5px;letter-spacing:.09em;text-transform:uppercase;color:var(--ink3);margin-bottom:8px}
.kpi .v{font:700 20px/1.15 var(--serif);color:var(--navy)}
.kpi .n{margin-top:8px;font-size:11.6px;color:var(--ink2);display:flex;flex-wrap:wrap;gap:5px;align-items:center}

/* Карточки разделов */
.card{background:var(--card);border:1px solid var(--line);border-radius:10px;margin-bottom:18px;overflow:hidden;
  box-shadow:0 1px 2px rgba(34,41,59,.04);animation:rise .3s both}
@keyframes rise{from{opacity:0;transform:translateY(6px)}to{opacity:1}}
.card>.head{display:flex;justify-content:space-between;align-items:baseline;gap:16px;padding:16px 20px 12px;border-bottom:1px solid var(--line)}
.card>.head .t{font:700 18px var(--serif);color:var(--navy);margin:0;display:flex;align-items:center;gap:9px;flex-wrap:wrap}
.card>.head .sub{margin:5px 0 0;font-size:12.2px;color:var(--ink2);max-width:78ch}
.card>.body{padding:16px 20px 18px}
.mini{font:600 12px var(--sans);letter-spacing:.08em;text-transform:uppercase;color:var(--brass);margin:22px 0 10px}
.foot-note{margin:12px 0 0;font-size:12px;color:var(--ink3)}

/* Выбор проекта */
.picker{display:flex;align-items:center;gap:12px;flex-wrap:wrap;padding:2px 0 16px}
.picker label{font-size:12.5px;color:var(--ink2)}
.picker select{min-width:320px;font:600 14px var(--sans);color:var(--navy);background:#fff;
  border:1.5px solid var(--line2);border-radius:8px;padding:10px 12px;cursor:pointer}
.tablist{display:flex;flex-wrap:wrap;gap:7px}
.ptab{border:1px solid var(--line2);background:#fff;border-radius:20px;padding:6px 13px;cursor:pointer;
  font:600 12.5px var(--sans);color:var(--ink2);display:inline-flex;align-items:center;gap:7px;transition:.15s}
.ptab:hover{border-color:var(--navy)}
.ptab.on{background:var(--navy);color:#fff;border-color:var(--navy)}
.ptab .d{width:8px;height:8px;border-radius:50%}
.d-ok{background:var(--ok)}.d-warn{background:var(--warn)}.d-bad{background:var(--bad)}.d-none{background:var(--none)}
.ptab.on .d{outline:1.5px solid #fff;outline-offset:-2px}

/* Таблицы */
.twrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:13.3px}
th{text-align:left;padding:7px 14px 7px 0;border-bottom:1.6px solid var(--line2);white-space:nowrap;
  font:600 10.6px var(--sans);letter-spacing:.07em;text-transform:uppercase;color:var(--ink3)}
td{padding:10px 14px 10px 0;border-bottom:1px solid var(--line);vertical-align:top}
tr:last-child td{border-bottom:0}
td .cn{font-size:11.9px;color:#6b7080;margin-top:3px;max-width:50ch}

/* Нет данных */
.nodata{margin:14px 0 0;padding:10px 14px;border-left:3px solid var(--none);background:var(--none-bg);
  border-radius:0 7px 7px 0;font-size:12.5px;color:var(--ink2)}
.nodata b{color:var(--ink)}

/* Вероятность */
.prob{display:inline-flex;align-items:center;gap:8px;font:600 12px var(--sans);white-space:nowrap}
.pb{width:48px;height:5px;border-radius:3px;background:#e9e5da;overflow:hidden}
.pf{display:block;height:100%;border-radius:3px}
.p-high{color:var(--bad)}.p-high .pf{background:var(--bad)}
.p-mid{color:var(--warn)}.p-mid .pf{background:var(--warn)}
.p-low{color:var(--ok)}.p-low .pf{background:var(--ok)}

/* Тепловая карта загрузки */
.heat{overflow-x:auto}
.heat table{border-collapse:separate;border-spacing:2px;font-size:11.5px;min-width:760px}
.heat th{text-align:center;padding:4px 2px;border:0;font:600 9.5px var(--sans);color:var(--ink3)}
.heat td{text-align:center;padding:0;border:0;width:32px;height:24px;line-height:24px;border-radius:3px;color:#fff;font:600 10px var(--mono)}
.heat td.rl{width:110px;text-align:left;font:500 12px var(--sans);color:var(--ink);background:transparent;padding-right:8px}
.h0{background:#f0eee7;color:#c7c2b4}.h1{background:#dcefe1}.h2{background:#bfe0cc;color:#15653f}
.h3{background:#f2dca3;color:#8a5c07}.h4{background:#e6a45f;color:#682c05}.h5{background:#c9564f;color:#fff}.h6{background:#9c2f2c;color:#fff}

/* Диаграмма-минигант загрузки роли */
.bar{height:6px;border-radius:3px;background:#eceadf;position:relative;overflow:hidden}
.bar>i{position:absolute;top:0;bottom:0;left:0;background:linear-gradient(90deg,#d59a5a,#c9564f)}
.bar>u{position:absolute;top:0;bottom:0;left:0;background:#79a487}

/* Критический путь (портфель) */
.cprail{position:relative;margin:8px 0 18px;padding:22px 6px 4px;border-top:1px solid var(--line)}
.cprow{display:flex;align-items:center;gap:10px;margin-bottom:9px;font-size:12px}
.cprow .lab{width:170px;flex:none;color:var(--ink2);font-weight:600}
.cpbar{flex:1;height:20px;border-radius:4px;display:flex;font:600 10px/20px var(--mono);color:#fff;overflow:hidden}
.cpbar span{white-space:nowrap;padding:0 6px}
.cp-track{position:relative;flex:1;height:24px;background:linear-gradient(90deg,#e7e3d8,#f3efe4);border-radius:4px}
.cp-fill{position:absolute;top:0;bottom:0;border-radius:4px;display:flex;align-items:center;justify-content:center}

.flagbad{margin-top:16px;padding:11px 14px;border-radius:8px;font-size:13px}
.flagbad.cp{background:var(--bad-bg);border:1px solid var(--bad-bd);color:var(--bad);font-weight:600}

.grid2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:860px){.grid2{grid-template-columns:1fr}.wrap{padding:18px 14px 48px}.switch{align-items:stretch;width:100%}.seg{width:100%}.seg button{flex:1;padding:8px 6px}}
.pfoot{margin-top:26px;padding-top:14px;border-top:1px solid var(--line2);font-size:11.6px;color:var(--ink3);max-width:100ch}
::-webkit-scrollbar{height:9px;width:9px}::-webkit-scrollbar-thumb{background:#cfc8b8;border-radius:5px}
td .cn{font-size:11.9px;color:#6b7080;margin-top:3px;max-width:50ch}
.cn,.foot-note,.kpi .n{color:#666c7d}
.rolelist span{white-space:normal}
.abbr{margin-top:10px;font-size:11.8px;color:var(--ink3)}

#root{display:none}
.picker select{min-width:320px}

</style>
</head>
<body>
<div id="app"></div>
<script>
// Данные: «Проект 22-10 лдя сверки.xml» (MSPDI). Единый источник чисел панели.
window.DASH = {"meta": {"reportDate": "2026-10-22", "projectStart": "2026-10-26", "projectFinish": "2026-11-27", "title": "Проект1", "subtitle": "Трансформация отдела продаж", "stagesN": 4, "milestonesN": 13, "deviantsN": 2, "workH": 0, "asgN": 35, "linksN": 27}, "startReportBefore": true, "allStartsCollapsed": true, "stages": [{"wbs": "1", "name": "Стадия 1: Диагностика и проектирование", "start": "2026-10-26", "finish": "2026-11-20", "bStart": "2026-10-26", "bFinish": "2026-11-20", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "crit": false, "slack": 0.0, "rollupMax": "2026-11-10", "products": [{"wbs": "1.1", "name": "Продукт: Новая организационная модель ОП", "finish": "2026-11-10", "bFinish": "2026-11-10", "dv": 0, "rollupMax": "2026-11-05", "tasks": [{"wbs": "1.1.1", "name": "Проведение ABC-XYZ анализа базы в 1С", "finish": "2026-11-05", "bFinish": "2026-10-30", "dv": 6, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Ведущий аналитик 1С"]}, {"wbs": "1.1.2", "name": "Разработка нового штатного расписания", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["HR-директор"]}, {"wbs": "1.1.3", "name": "Описание профилей должностей и регламентов", "finish": "2026-10-29", "bFinish": "2026-10-29", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["РОП"]}]}, {"wbs": "1.2", "name": "Продукт: Система мотивации и развития", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "rollupMax": "2026-10-30", "tasks": [{"wbs": "1.2.1", "name": "Разработка матрицы KPI и положения о премировании", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["HR-директор"]}]}, {"wbs": "1.3", "name": "Продукт: Инструмент аналитики и поддержки", "finish": "2026-11-10", "bFinish": "2026-11-03", "dv": 7, "rollupMax": "2026-11-02", "tasks": [{"wbs": "1.3.1", "name": "Проектирование алгоритма подсказок Next Best Action", "finish": "2026-10-29", "bFinish": "2026-10-29", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Руководитель проекта / Аналитик"]}, {"wbs": "1.3.2", "name": "Аудит качества данных в 1С", "finish": "2026-11-02", "bFinish": "2026-10-28", "dv": 5, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Ведущий аналитик 1С"]}]}]}, {"wbs": "2", "name": "Стадия 2: Разработка и подготовка", "start": "2026-10-26", "finish": "2026-11-27", "bStart": "2026-10-26", "bFinish": "2026-11-27", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "crit": false, "slack": 0.0, "rollupMax": "2026-11-17", "products": [{"wbs": "2.1", "name": "Продукт: Новая организационная модель ОП (Подготовка)", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "rollupMax": "2026-10-28", "tasks": [{"wbs": "2.1.1", "name": "Согласование списков на сокращение и удержание", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Куратор проекта / РОП"]}, {"wbs": "2.1.2", "name": "Юридическое оформление изменений штатного расписания", "finish": "2026-10-27", "bFinish": "2026-10-27", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["HR-директор"]}]}, {"wbs": "2.2", "name": "Продукт: Инструмент аналитики и поддержки (Настройка)", "finish": "2026-11-17", "bFinish": "2026-11-17", "dv": 0, "rollupMax": "2026-11-06", "tasks": [{"wbs": "2.2.1", "name": "Настройка модуля сегментации и интеграция с 1С", "finish": "2026-11-06", "bFinish": "2026-11-06", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Внешний подрядчик (Интегратор)"]}, {"wbs": "2.2.2", "name": "Программирование интерфейса ежедневных подсказок", "finish": "2026-11-03", "bFinish": "2026-11-03", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Внешний подрядчик (Разработчик)"]}]}, {"wbs": "2.3", "name": "Продукт: Система мотивации и развития (Материалы)", "finish": "2026-11-04", "bFinish": "2026-11-04", "dv": 0, "rollupMax": "2026-10-30", "tasks": [{"wbs": "2.3.1", "name": "Создание обучающих материалов и чек-листов", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["РОП / Методолог"]}, {"wbs": "2.3.2", "name": "Отбор и инструктаж внутренних наставников", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["РОП"]}]}]}, {"wbs": "3", "name": "Стадия 3: Внедрение и запуск", "start": "2026-10-26", "finish": "2026-11-20", "bStart": "2026-10-26", "bFinish": "2026-11-20", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "crit": false, "slack": 0.0, "rollupMax": "2026-11-13", "products": [{"wbs": "3.1", "name": "Продукт: Обученный персонал нового штата", "finish": "2026-11-13", "bFinish": "2026-11-13", "dv": 0, "rollupMax": "2026-11-06", "tasks": [{"wbs": "3.1.1", "name": "Проведение процедуры оптимизации штата", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["HR-директор"]}, {"wbs": "3.1.2", "name": "Обучение оставшихся сотрудников работе с инструментом", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Внутренние наставники"]}, {"wbs": "3.1.3", "name": "Запуск программы наставничества", "finish": "2026-11-06", "bFinish": "2026-11-06", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["РОП"]}]}, {"wbs": "3.2", "name": "Продукт: Интегрированная база данных клиентов", "finish": "2026-10-30", "bFinish": "2026-10-30", "dv": 0, "rollupMax": "2026-10-28", "tasks": [{"wbs": "3.2.1", "name": "Очистка базы данных от дублей и некорректных записей", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Ведущий аналитик 1С"]}, {"wbs": "3.2.2", "name": "Тестовый запуск рассылок предложений по алгоритму", "finish": "2026-10-27", "bFinish": "2026-10-27", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["РОП"]}]}, {"wbs": "3.3", "name": "Продукт: Система мотивации и развития (Запуск)", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "rollupMax": "2026-10-28", "tasks": [{"wbs": "3.3.1", "name": "Внедрение новой матрицы KPI в расчетную систему", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Бухгалтер / Аналитик 1С"]}]}]}, {"wbs": "4", "name": "Стадия 4: Стабилизация и передача", "start": "2026-10-26", "finish": "2026-11-06", "bStart": "2026-10-26", "bFinish": "2026-11-06", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "crit": false, "slack": 0.0, "rollupMax": "2026-11-03", "products": [{"wbs": "4.1", "name": "Продукт: Оптимизированная система управления эффективностью", "finish": "2026-11-03", "bFinish": "2026-11-03", "dv": 0, "rollupMax": "2026-10-28", "tasks": [{"wbs": "4.1.1", "name": "Замер первых операционных результатов", "finish": "2026-10-28", "bFinish": "2026-10-28", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Руководитель проекта"]}, {"wbs": "4.1.2", "name": "Внесение точечных корректировок в алгоритмы", "finish": "2026-10-27", "bFinish": "2026-10-27", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["IT-директор / Аналитик"]}, {"wbs": "4.1.3", "name": "Подготовка итогового отчета и акта приема-передачи", "finish": "2026-10-27", "bFinish": "2026-10-27", "dv": 0, "workH": 0.0, "bWorkH": 0.0, "pct": 0.0, "slack": 0.0, "ms": false, "roles": ["Руководитель проекта"]}]}]}], "deviants": [{"wbs": "1.1.1", "name": "Проведение ABC-XYZ анализа базы в 1С", "finish": "2026-11-05", "bFinish": "2026-10-30", "dv": 6}, {"wbs": "1.3.2.1", "name": "Веха: Требования к аналитике зафиксированы", "finish": "2026-10-27", "bFinish": "2026-10-26", "dv": 1}], "roles": [{"name": "Руководитель проекта", "max": 1.0, "tasks": 6, "taskWbs": ["1", "2", "3", "4", "4.1.1", "4.1.3"], "peak": 6.0, "overDays": 20, "windows": [{"from": "2026-10-26", "to": "2026-11-20"}]}, {"name": "РОП / HR-директор", "max": 1.0, "tasks": 1, "taskWbs": ["1.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Ведущий аналитик 1С", "max": 1.0, "tasks": 2, "taskWbs": ["1.1.1", "3.2.1"], "peak": 2.0, "overDays": 3, "windows": [{"from": "2026-10-26", "to": "2026-10-28"}]}, {"name": "HR-директор", "max": 1.0, "tasks": 4, "taskWbs": ["1.1.2", "2.3", "3.1.1", "3.3"], "peak": 4.0, "overDays": 5, "windows": [{"from": "2026-10-26", "to": "2026-10-30"}]}, {"name": "РОП", "max": 1.0, "tasks": 5, "taskWbs": ["1.1.3", "2.3.2", "3.1", "3.1.3", "3.2.2"], "peak": 5.0, "overDays": 10, "windows": [{"from": "2026-10-26", "to": "2026-11-06"}]}, {"name": "HR-директор", "max": 1.0, "tasks": 1, "taskWbs": ["1.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "HR-директор", "max": 1.0, "tasks": 1, "taskWbs": ["1.2.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "IT-директор", "max": 1.0, "tasks": 2, "taskWbs": ["1.3", "3.2"], "peak": 2.0, "overDays": 5, "windows": [{"from": "2026-10-26", "to": "2026-10-30"}]}, {"name": "Руководитель проекта / Аналитик", "max": 1.0, "tasks": 1, "taskWbs": ["1.3.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Ведущий аналитик 1С", "max": 1.0, "tasks": 1, "taskWbs": ["1.3.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "HR-директор", "max": 1.0, "tasks": 1, "taskWbs": ["2.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Куратор проекта / РОП", "max": 1.0, "tasks": 1, "taskWbs": ["2.1.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "HR-директор", "max": 1.0, "tasks": 1, "taskWbs": ["2.1.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "IT-директор", "max": 1.0, "tasks": 1, "taskWbs": ["2.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Внешний подрядчик (Интегратор)", "max": 1.0, "tasks": 1, "taskWbs": ["2.2.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Внешний подрядчик (Разработчик)", "max": 1.0, "tasks": 1, "taskWbs": ["2.2.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "РОП / Методолог", "max": 1.0, "tasks": 1, "taskWbs": ["2.3.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Внутренние наставники", "max": 1.0, "tasks": 1, "taskWbs": ["3.1.2"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Бухгалтер / Аналитик 1С", "max": 1.0, "tasks": 1, "taskWbs": ["3.3.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "Куратор проекта", "max": 1.0, "tasks": 1, "taskWbs": ["4.1"], "peak": 1.0, "overDays": 0, "windows": []}, {"name": "IT-директор / Аналитик", "max": 1.0, "tasks": 1, "taskWbs": ["4.1.2"], "peak": 1.0, "overDays": 0, "windows": []}], "dups": {"Ведущий аналитик 1С": ["uid 3", "uid 10"], "HR-директор": ["uid 4", "uid 6", "uid 7", "uid 11", "uid 13"], "IT-директор": ["uid 8", "uid 14"]}, "milestones": [{"wbs": "1.1.3.1", "name": "Веха: Организационная структура утверждена", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "1.2.1.1", "name": "Веха: Система мотивации разработана", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "1.3.2.1", "name": "Веха: Требования к аналитике зафиксированы", "finish": "2026-10-27", "slack": 0.0}, {"wbs": "1.3.2.2", "name": "Веха: Этап Диагностики завершен", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "2.1.2.1", "name": "Веха: Кадровые решения оформлены", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "2.2.2.1", "name": "Веха: Инструмент аналитики готов к тестированию", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "2.3.2.1", "name": "Веха: База для обучения подготовлена", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "2.3.2.2", "name": "Веха: Этап Разработки завершен", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "3.1.3.1", "name": "Веха: Персонал обучен и работает по новым стандартам", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "3.2.2.1", "name": "Веха: База данных очищена и протестирована", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "3.3.1.1", "name": "Веха: Новая система мотивации активирована", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "3.3.1.2", "name": "Веха: Этап Внедрения завершен", "finish": "2026-10-26", "slack": 0.0}, {"wbs": "4.1.3.1", "name": "Веха: Проект успешно завершен и передан заказчику", "finish": "2026-10-26", "slack": 25.0}]};

;
/* Каркас панели «Портфель проектов» (файл «Проект 22-10 лдя сверки.xml»).
   Единый источник чисел — window.DASH. Статусы: зелёный — в плане, жёлтый — угроза,
   красный — отклонение (от базового плана либо внутреннее расхождение данных). */
(function () {
  const C = window.DASH;
  const app = document.getElementById("app");
  const esc = (s) => String(s).replace(/[&<>"']/g, (c) => ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" }[c]));
  const ru = (iso) => { if (!iso) return "—"; const [y, m, d] = iso.slice(0, 10).split("-"); return `${d}.${m}.${y}`; };
  const chip = (s, label) => `<span class="chip s-${s}">${esc(label || { ok: "в плане", warn: "есть угроза", bad: "отклонение", none: "нет данных" }[s])}</span>`;
  const AI = `<span class="ai">оценка ИИ</span>`;
  const wd = (n) => n === 1 ? "раб. день" : n < 5 ? "раб. дня" : "раб. дней";
  const pl = (n, a, b, c) => { const t = n % 10, h = n % 100; return t === 1 && h !== 11 ? a : (t >= 2 && t <= 4 && (h < 12 || h > 14)) ? b : c; };
  window.u = { esc, ru, chip, AI, wd, pl };

  const state = { mode: "project", stage: "ALL" };
  const MODES = [["project", "Проект"], ["resources", "Ресурсы"], ["risks", "Риски"]];

  function shell() {
    const m = C.meta;
    app.innerHTML = `
    <div class="wrap">
      <header class="top">
        <div>
          <div class="eyebrow">Статус-отчёт · данные плана Microsoft Project (MSPDI)</div>
          <h1 class="title">Портфель проектов</h1>
          <div class="meta">
            <span>Отчётная дата: <strong>${ru(m.reportDate)}</strong></span>
            <span>${esc(m.title)} — ${esc(m.subtitle)} · старт ${ru(m.projectStart)} · финиш ${ru(m.projectFinish)} · ${m.stagesN} стадии · ${m.workH.toLocaleString("ru-RU")} ч плана</span>
          </div>
        </div>
        <nav class="switch" aria-label="Режимы">
          <div class="seg" role="tablist">${MODES.map(([k, l]) => `<button role="tab" aria-selected="${state.mode === k}" class="${state.mode === k ? "on" : ""}" data-mode="${k}">${l}</button>`).join("")}</div>
          <div class="hint">${{ project: "прогноз, инциденты, риски по проекту и стадиям", resources: "кто перегружен и где", risks: "реестр рисков и план митигации" }[state.mode]}</div>
        </nav>
      </header>
      <div class="legend-bar"><div class="legend"><b>Обозначения</b>${chip("ok")}${chip("warn")}${chip("bad")}${chip("none")}
        <span>${AI} — вывод ИИ из данных файла, а не прямой факт</span></div></div>
      <main id="view"></main>
      <footer class="pfoot">
        Источник всех цифр — файл «Проект 22-10 лдя сверки.xml» (MS Project, MSPDI; дата среза ${ru(m.reportDate)}, сохранение 22.10.2026 15:40).
        Отчётная дата (${ru(m.reportDate)}) предшествует старту работ (${ru(m.projectStart)}): фактического исполнения в файле нет
        (Прогресс 0% по всем задачам), поэтому «прогноз» = текущее расписание файла, а отклонения считаются
        относительно базового плана (он в файле сохранён). Всё, чего в файле нет, помечено «нет данных».
        Имена исполнителей в файле не указаны — ресурсы названы должностями; ответственные в рекомендациях — должности.
      </footer>
    </div>`;
  }
  function draw() {
    shell();
    document.querySelectorAll("[data-mode]").forEach((b) => b.addEventListener("click", () => { state.mode = b.dataset.mode; draw(); }));
    window.Views[state.mode](document.getElementById("view"), state);
  }
  window.Views = {};
  window.setStage = (k) => { state.stage = k; draw(); };
  if (document.readyState === "loading") document.addEventListener("DOMContentLoaded", draw); else draw();
})();

;
/* Режим «Проект»: разрез «весь проект / стадия», прогноз к базовому плану,
   инциденты и изменения, риски на будущий период. Все числа — из файла-среза. */
(function () {
  const D = window.DASH, U = window.u;
  const { esc, ru, chip, AI, wd } = U;
  const S = D.stages;

  // рабочие дни календаря проекта (26.10–27.11)
  const PWD = (() => { let n = 0, c = new Date(D.meta.projectStart), e = new Date(D.meta.projectFinish);
    while (c <= e) { const d = c.getDay(); if (d > 0 && d < 6) n++; c = new Date(c.getTime() + 864e5); } return n; })();

  window.Views.project = function (v, state) {
    v.innerHTML = picker(state.stage) + (state.stage === "ALL" ? overview() : stageView(state.stage));
    const sel = v.querySelector("#ssel");
    sel && sel.addEventListener("change", () => window.setStage(sel.value));
  };

  function picker(cur) {
    return `<div class="picker"><label for="ssel">Разрез</label>
      <select id="ssel" aria-label="Выбор стадии">
        <option value="ALL" ${cur === "ALL" ? "selected" : ""}>Весь проект — ${esc(D.meta.title)}</option>
        ${S.map(s => `<option value="${s.wbs}" ${cur === s.wbs ? "selected" : ""}>${esc(s.name)}</option>`).join("")}
      </select>
      <span class="muted">в исходном файле один проект; стадия — уровень детализации</span></div>`;
  }

  /* ---------- правила статусов (оценка ИИ, правила едины) ---------- */
  function gapFinish(s) { return s.rollupMax && s.finish > s.rollupMax ? Math.round((new Date(s.finish) - new Date(s.rollupMax)) / 864e5) : 0; }
  function stFor(x) {
    const g = gapFinish(x);
    if (x.dv > 0) return { s: "bad", label: "отклонение от базы", why: `срок ушёл к базовому плану на +${x.dv} кал. дн` };
    if (g > 5) return { s: "bad", label: "расхождение в плане", why: `сводная дата на ${g} кал. дн позже последней работы — проставлена вручную, не из работ` };
    if (g > 0) return { s: "warn", label: "есть угроза", why: `небольшой разбек сводной даты с работами (+${g} дн)` };
    if (x.crit || x.slack === 0) return { s: "warn", label: "есть угроза", why: "нулевой резерв времени (TF=0)" };
    return { s: "ok", label: "в плане" , why: "срок совпадает с базовым планом"};
  }

  function projectStatus() {
    let s = "ok", why = [];
    S.forEach(st => { const r = stFor(st); if (r.s !== "ok") why.push(`${st.name.replace("Стадия ", "")} — ${r.label}`); if (r.s === "bad") s = "bad"; else if (r.s === "warn" && s !== "bad") s = "warn"; });
    return { s, label: s === "bad" ? "отклонение" : s === "warn" ? "есть угроза" : "в плане", why: why.join("; ") };
  }

  /* ---------- весь проект ---------- */
  function overview() {
    const st = projectStatus();
    const devN = D.deviants.length;
    const over = D.roles.filter(r => r.overDays > 0);
    return `
    <div class="kpis">
      ${kpi(st.s, "Статус проекта", chip(st.s, st.label), AI + " " + esc(st.why || "все сроки совпадают с базой"))}
      ${kpi("ok", "Срок завершения проекта", ru(D.meta.projectFinish), "план = база, Δ 0 дн; внутренние сдвиги работ (см. инциденты) в финальный срок ещё не перекатились")}
      ${kpi("bad", "Работ с отклонением к базе", devN + " <span class='muted'>из 24</span>", D.deviants.map(x => `«${esc(x.name)}»: +${x.dv} дн`).join(" · "))}
      ${kpi(over.length ? "warn" : "ok", "Перегруженных исполнителей", over.length + ` <span class="muted">из ${D.roles.length}</span>`, `${over.reduce((a, r) => a + r.overDays, 0)} раб. дней суммарного перегруза в окне ${ru(D.meta.projectStart)} — ${ru(D.meta.projectFinish)} (≈${PWD} раб. дн). Верхняя граница: пики завышены схлопнутыми стартами`)}
    </div>

    ${card("Прогноз по ключевым параметрам: окончания стадий",
      "План — базовый план из файла (он сохранён), прогноз — текущее расписание среза 22.10.2026.", null,
      tbl(["Стадия", "План (база)", "Прогноз (тек. план)", "Отклонение", "Ожид. результат по работам", "Статус"],
        S.map(s => {
          const r = stFor(s);
          const m = D.milestones.find(x => x.wbs.startsWith(s.wbs + ".") && /Этап|Проект/.test(x.name));
          return [`<strong>${esc(s.name)}</strong>`, ru(s.bFinish), ru(s.finish),
            s.dv > 0 ? `<span class="bad-t">+${s.dv} кал. дн</span>` : `0${gapFinish(s) ? " <span class='muted'>(внутри: +" + gapFinish(s) + " к работам)</span>" : ""}`,
            m ? esc(m.name.replace(/^Веха:\s*/, "")) + ` <span class="mono">(${ru(m.finish)})</span>` + (m.finish.slice(0, 10) === "2026-10-26" ? " <span class='muted'>— дата-заглушка</span>" : "") : "—",
            chip(r.s, r.label) + (r.why ? `<div class="cn">${esc(r.why)}</div>` : "")];
        })) +
      `<div class="foot-note">Правило статусов единое: красным — отклонение от базового плана или внутреннее расхождение сводных дат >5 дней; жёлтым — разбег 1–5 дней или TF=0 при внешнем перегрузе. <span class="ai">оценка ИИ</span></div>`)}

    ${card("Инциденты и изменения за отчётный период", "Срез 22.10.2026: расхождения текущего плана к базовому и внутренние противоречия вёрстки плана. Работы ещё не начинались (старт 26.10), фактического прогресса нет.", null,
      incidentsTable(D.deviants))}

    ${card("Риски на будущий период", "Рассчитаны по окнам перегрузки конкретных исполнителей (Units > мощности); риск структуры плана добавлен отдельно.", AI,
      risksTable(flatRisks()))}
    `;
  }

  /* ---------- стадия ---------- */
  function stageView(wbs) {
    const s = S.find(x => x.wbs === wbs); if (!s) return "<p>нет такой стадии в данных</p>";
    const r = stFor(s);
    const devIn = D.deviants.filter(d => d.wbs.startsWith(s.wbs + "."));
    const rows = [];
    s.products.forEach(p => {
      rows.push([`<span class="mono">${esc(p.wbs)}</span> <strong>${esc(p.name)}</strong>`, ru(p.bFinish || "—"), ru(p.finish),
        p.dv > 0 ? `<span class="bad-t">+${p.dv}</span>` : "0", "", "", chip(...prodStatus(p))]);
      p.tasks.forEach(q => rows.push([`<span class="mono">${esc(q.wbs)}</span> ${q.ms ? "<em>" : ""}${esc(q.name)}${q.ms ? "</em>" : ""}`,
        ru(q.bFinish || "—"), ru(q.finish),
        q.dv > 0 ? `<span class="bad-t">+${q.dv}</span>` : q.dv < 0 ? `<span class="bad-t">${q.dv}</span>` : "0",
        `${q.workH} ч${q.bWorkH ? ` <span class="muted">база ${q.bWorkH} ч</span>` : ""}`,
        esc((q.roles || []).join(", ") || "—"),
        chip(q.dv > 0 ? "bad" : (s.slack === 0 ? "warn" : "ok"), q.dv > 0 ? "вне базы" : q.slack === 0 || s.slack === 0 ? "TF=0" : "в плане")]));
    });
    return `
    <div class="kpis">
      ${kpi(r.s, "Стадия · статус", chip(r.s, r.label), AI + " " + esc(r.why || ""))}
      ${kpi("ok", "Окончание (база → прогноз)", `${ru(s.bFinish)} → ${ru(s.finish)}`, "Δ по сводной " + (s.dv > 0 ? "+" + s.dv : 0) + " дн; сводная позже работ на " + gapFinish(s) + " кал. дн — см. таблицу")}
      ${kpi(devIn.length ? "bad" : "ok", "Сдвигов к базе", String(devIn.length), devIn.length ? devIn.map(x => `+${x.dv} дн: «${esc(x.name)}»`).join(" · ") : "работы стадии в границах базы")}
      ${kpi("none", "Фактический прогресс", "нет данных", "0% по всем работам; отчётная дата (22.10) раньше старта (26.10)")}
    </div>
    ${card("Работы и вехи стадии: план (база) / прогноз / Δ", "Δ — разность окончаний «текущий план − база», календарные дни. Труд — из тех же полей; веха отмечена курсивом.", null,
      tbl(["Работа / веха", "База", "Прогноз", "Δ дн", "Труд", "Исполнитель (должность)", "Статус"], rows) +
      (gapFinish(s) ? `<div class="nodata"><b>Расхождение вёрстки.</b> Сводная дата стадии ${ru(s.finish)} на ${gapFinish(s)} кал. дн позже последней работы (${ru(s.rollupMax)}). В отчёте использована дата работ; сводная требует уточнения у планировщика. <span class="ai">оценка ИИ</span></div>` : ""))}
    ${card("Инциденты и изменения стадии", devIn.length ? "Работы со сдвигом относительно базового плана + системные аномалии вёрстки." : "Работы стадии в границах базы.", null,
      incidentsTable(devIn, { sysOnly: !devIn.length }))}
    ${card("Риски по стадии", "Перегруз исполнителей, назначенных на работы стадии, и нулевой резерв.", AI,
      risksTable(flatRisks().filter(x => x.stages.includes(s.name))) )}
    `;
  }
  function prodStatus(p) {
    const g = p.finish > p.rollupMax ? Math.round((new Date(p.finish) - new Date(p.rollupMax)) / 864e5) : 0;
    if (p.dv > 0) return ["bad", "отклонение от базы"];
    if (g > 5) return ["bad", "сводная ≠ работы"];
    if (g > 0) return ["warn", "есть угроза"];
    return ["ok", "в плане"];
  }

  /* ---------- блоки ---------- */
  const SYS_INCIDENTS = [
    { at: "срез 22.10.2026", th: "<strong>Даты начала схлопнуты:</strong> у всех работ и в плане, и в базе старт = 26.10.2026 при разных окончаниях",
      imp: "календарь не разведён по зависимостям: 12 из 13 вех стоят на 26.10 (дата-заглушка); расчёт критического пути и резервов по такому файлу недостоверен", s: "bad" },
    { at: "срез 22.10.2026", th: "<strong>Окончания сводных задач позже дочерних работ:</strong> стадия 1 +10 кал. дн, стадия 2 +10, продукт 2.2 +11, стадия 3 +7, прочие +2…+6",
      imp: "итог по стадии и итог по работам дают разные сроки; в отчёте показан оба числа и источник каждой", s: "bad" },
    { at: "срез 22.10.2026", th: "<strong>Трудоёмкость выросла к базе:</strong> 1.1.1 ABC-XYZ — 72 ч против 40 ч в базе (+80%); 1.3.2 аудит данных — 48 ч против 24 ч (+100%)",
      imp: "при тех же сроках стадии прирост объёма ложится на исполнителей — см. окна перегруза", s: "warn" },
    { at: "срез 22.10.2026", th: "<strong>«Веха: Проект успешно завершен» стоит на 26.10.2026</strong> при финише проекта 27.11.2026 (резерв 25 раб. дн)",
      imp: "контрольная веха приёмки выпада из календаря: по файлу нельзя проверить факт завершения этапа 4", s: "warn" },
  ];
  function incidentsTable(list, opt = {}) {
    const facts = (list || []).filter(d => d.dv > 0).map(d => [ru(d.finish),
      `<strong>${esc(d.name)}</strong> <span class="mono">${esc(d.wbs)}</span>`,
      `сдвиг к базе +${d.dv} кал. дн (${ru(d.bFinish)} → ${ru(d.finish)}); работа ещё не начата — сдвиг заложен в план до старта`,
      chip("bad", "вне базы")]);
    const sys = (opt.sysOnly ? SYS_INCIDENTS : list && list.length ? SYS_INCIDENTS.slice(0, 2) : SYS_INCIDENTS)
      .map(e => [e.at, e.th, e.imp, chip(e.s, e.s === "bad" ? "расхождение" : "есть угроза")]);
    return tbl(["Когда заметили", "Инцидент / изменение", "Как влияет на проект", "Статус"], facts.concat(sys));
  }
  function flatRisks() {
    const rs = [];
    D.roles.filter(r => r.overDays > 0).forEach(r => {
      const stages = [...new Set(r.taskWbs.map(w => (S.find(s => w.startsWith(s.wbs + ".")) || {}).name).filter(Boolean))];
      rs.push({ who: r.name, subj: "Ресурс", prob: Math.min(0.9, 0.35 + 0.5 * (r.overDays / PWD)),
        impact: `в окне ${r.windows.map(x => ru(x.from) + "–" + ru(x.to)).join(", ")} загрузка ${Math.round(r.peak * 100)}% при мощности 100% (назначено ${r.tasks} работ)`,
        short: `просрочка любой работы окна сдвигает вехи стадии (TF=0)`,
        when: `${ru(r.windows[0].from)} — ${ru(r.windows[r.windows.length - 1].to)} (${r.overDays} ${wd(r.overDays)})`,
        stages, dup: D.dups[r.name] ? D.dups[r.name].length : 0 });
    });
    rs.push({ who: "Структура плана", subj: "Данные", prob: 0.75,
      impact: "схлопнутые старты, ручные сводные даты, нулевые резервы — прогнозная дата 27.11 и вся цепочка вех недостоверны, пока план не пересобран",
      short: "ошибки прогноза до +2 недель на ровном месте", when: "сейчас", stages: [], dup: 0 });
    return rs.sort((a, b) => b.prob - a.prob);
  }
  function risksTable(rs) {
    if (!rs.length) return "<div class='nodata'>Рисков, подтверждённых данными этого разреза, нет.</div>";
    return tbl(["Объект риска", "Тип", "Риск (что показывает план)", "Вероятность", "Влияние", "Когда может реализоваться"],
      rs.map(r => [
        `<strong>${esc(r.who)}</strong>${r.dup ? ` <span class="tag" title="в реестре ресурсов ${r.dup} записи с одинаковой должностью — суммарная мощность выше">дубль ×${r.dup}</span>` : ""}`,
        r.subj, esc(r.impact), probBar(r.prob), esc(r.short || r.impact), `<span class="mono">${esc(r.when)}</span>`]));
  }
  function probBar(p) { const c = p >= 0.6 ? "high" : p >= 0.4 ? "mid" : "low";
    return `<span class="prob p-${c}"><span class="pb"><span class="pf" style="width:${Math.round(p * 100)}%"></span></span>${Math.round(p * 100)}%</span>`; }
  function kpi(s, l, v, n) { return `<div class="kpi ${s}"><div class="l">${l}</div><div class="v">${v}</div><div class="n">${n || ""}</div></div>`; }
  function card(t, sub, aib, body) {
    return `<section class="card"><div class="head"><h2 class="t">${t} ${aib || ""}</h2>${sub ? `<p class="sub">${sub}</p>` : ""}</div><div class="body">${body}</div></section>`;
  }
  function tbl(head, rows) {
    return `<div class="twrap"><table><thead><tr>${head.map(h => `<th>${h}</th>`).join("")}</tr></thead><tbody>${rows.map(r => `<tr>${r.map(x => `<td>${x}</td>`).join("")}</tr>`).join("")}</tbody></table></div>`;
  }
  const css = document.createElement("style");
  css.textContent = `.bad-t{color:#b02a2e;font-weight:600}`;
  document.head.appendChild(css);
})();

;
/* Режим «Ресурсы»: загрузка конкретных исполнителей (должностей из реестра ресурсов),
   окна перегрузки, дубли должностей,.capacity суммарно по роли. */
(function () {
  const D = window.DASH, U = window.u;
  const { esc, ru, chip, AI } = U;

  window.Views.resources = function (v) {
    const roles = D.roles;
    const over = roles.filter(r => r.overDays > 0);
    // суммарная мощность по должности
    const capByTitle = {};
    roles.forEach(r => { capByTitle[r.name] = (capByTitle[r.name] || 0) + r.max; });

    const worst = [...over].sort((a, b) => b.overDays - a.overDays)[0];
    const proj = roles.find(r => r.name === "Руководитель проекта");

    v.innerHTML = `
    <div class="kpis">
      ${kpi(over.length ? "warn" : "ok", "Исполнителей с перегрузом", over.length + ` <span class="muted">из ${roles.length}</span>`,
        `окна суммарной загрузки >100% между ${ru(D.meta.projectStart)} и ${ru(D.meta.projectFinish)}`)}
      ${kpi("bad", "Самый острый дефицит", esc(worst ? worst.name : "—"),
        worst ? `пик ${Math.round(worst.peak * 100)}%, ${U.wd(worst.overDays)} в окне ${ru(worst.windows[0].from)} — ${ru(worst.windows[worst.windows.length - 1].to)}` : "")}
      ${kpi("none", "Дубли должностей в реестре", String(Object.keys(D.dups).length),
        esc(Object.entries(D.dups).map(([k, v]) => `${k} ×${v.length}`).join(", ")) + " — разные люди или дублирование карточек? от ответа зависит реальная мощность")}
      ${kpi("none", "Стоимость ресурсов", "нет данных", "ставки в файле нулевые; бюджеты и оплаченные дни не рассчитываются")}
    </div>

    ${card("Обзор дефицита ресурсов: исполнители, длительность нехватки, статус",
      "Мощность записи реестра = 100% (Max Units 1,0). Перегруз = сумма Units назначений исполнителя в рабочий день. Оговорка: так как старты всех работ в файле схлопнуты в 26.10, одновременность назначений (а значит и пики) завышена искажённой вёрсткой расписания — до пересборки календаря (см. план митигации, R6–R7) пики следует читать как верхнюю границу.", null,
      tbl(["Исполнитель (должность)", "Работ назначено", "Пик загрузки", "Окна перегруза", "Длительность нехватки", "Статус"],
        roles.map(r => {
          const st = r.overDays === 0 ? "ok" : r.overDays > 8 ? "bad" : "warn";
          return [`<strong>${esc(r.name)}</strong>${D.dups[r.name] ? ` <span class="tag" title="в реестре ${D.dups[r.name].length} записи с этой должностью; суммарная мощность — ${D.dups[r.name].length}×100%">дубль ×${D.dups[r.name].length}</span>` : ""}`,
            r.tasks,
            meter(r.peak),
            r.windows.length ? r.windows.map(w => `<span class="mono">${ru(w.from)} → ${ru(w.to)}</span>`).join("<br>") : '<span class="muted">—</span>',
            r.overDays ? U.wd(r.overDays) : "—",
            chip(st, st === "ok" ? "в плане" : st === "bad" ? "перегруз >8 дн" : "нехватка")];
        })) +
      `<div class="foot-note">Пунктир на шкале — мощность одной записи реестра (100%). Окна рассчитаны по рабочим дням; вехи и суммарные строки в загрузку не входят.</div>`)}

    ${card("Свод по должностям (альтернатива: дубли = один человек)",
      "Если все записи с одинаковой должностью — это один сотрудник (частая ошибка реестра), его мощность остаётся 100% и картина риска меняется.", AI,
      tbl(["Должность", "Записей в реестре", "Макс. пик по записям", "Вывод (оценка ИИ)", "Статус"],
        Object.keys(capByTitle).sort().map(n => {
          const rs = roles.filter(r => r.name === n);
          const peakOne = Math.max(...rs.map(r => r.peak), 0);
          const verdict = peakOne <= 1.02
            ? "перегруза нет ни при какой трактовке реестра"
            : (rs.length > 1
              ? `если это ${rs.length} разных людей (по записи) — пик каждой ≤ 100%, проблема снимается; если один — перегруз до ${Math.round(peakOne * 100)}% покрывать нечем`
              : "единственная запись — перегруз покрывать нечем, требуется второй исполнитель или перенос работ");
          const color = peakOne <= 1.02 ? "ok" : (rs.length > 1 ? "warn" : "bad");
          return [`<strong>${esc(n)}</strong>`, rs.length, Math.round(peakOne * 100) + "%", verdict,
            chip(color, color === "ok" ? "в плане" : color === "warn" ? "зависит от трактовки реестра" : "отклонение при одном человеке")];
        })))}
    `;
  };

  function kpi(s, l, v, n) { return `<div class="kpi ${s}"><div class="l">${l}</div><div class="v">${v}</div><div class="n">${n || ""}</div></div>`; }
  function card(t, sub, aib, body) { return `<section class="card"><div class="head"><h2 class="t">${t} ${aib || ""}</h2>${sub ? `<p class="sub">${sub}</p>` : ""}</div><div class="body">${body}</div></section>`; }
  function tbl(head, rows) { return `<div class="twrap"><table><thead><tr>${head.map(h => `<th>${h}</th>`).join("")}</tr></thead><tbody>${rows.map(r => `<tr>${r.map(x => `<td>${x}</td>`).join("")}</tr>`).join("")}</tbody></table></div>`; }
  function meter(peak) {
    const w = Math.min(100, peak * 50), col = peak >= 1.6 ? "#c9564f" : peak > 1.02 ? "#d59a5a" : peak > 0 ? "#79a487" : "#cfc8b8";
    return `<span class="mwrap" title="пик одновременной загрузки в рабочий день: ${Math.round(peak * 100)}%"><i></i><b style="width:${w}%;background:${col}"></b></span><span class="mval">${Math.round(peak * 100)}%</span>`;
  }
  const css = document.createElement("style");
  css.textContent = `.tag{display:inline-block;padding:1px 7px;border-radius:4px;margin-left:6px;font:600 10.4px var(--sans);background:#eef0f3;color:#41627e;vertical-align:1px}
  .mwrap{display:inline-block;width:96px;height:8px;background:#eceadf;border-radius:4px;position:relative;vertical-align:middle}.mwrap i{position:absolute;left:50%;top:-3px;bottom:-3px;width:0;border-left:1.5px dashed #8a6d2f}.mwrap b{position:absolute;left:0;top:0;bottom:0;border-radius:4px}.mval{display:inline-block;width:44px;text-align:right;margin-left:6px;font:500 11.5px var(--mono)}`;
  document.head.appendChild(css);
})();

;
/* Режим «Риски»: детальный статус-отчёт — развёрнутый прогноз и инциденты по всем
   стадиям, реестр рисков (перегруз ресурсов + структура плана) и план митигации. */
(function () {
  const D = window.DASH, U = window.u;
  const { esc, ru, chip, AI, wd } = U;
  const S = D.stages;
  const PWD = (() => { let n = 0, c = new Date(D.meta.projectStart), e = new Date(D.meta.projectFinish);
    while (c <= e) { const d = c.getDay(); if (d > 0 && d < 6) n++; c = new Date(c.getTime() + 864e5); } return n; })();

  window.Views.risks = function (v) {
    const risks = register();
    const kpi = (s, l, val, n) => `<div class="kpi ${s}"><div class="l">${l}</div><div class="v">${val}</div><div class="n">${n || ""}</div></div>`;
    v.innerHTML = `
    <div class="kpis">
      ${kpi(risks.some(r => r.s === "bad") ? "bad" : "warn", "Реестр рисков", String(risks.length), `${risks.filter(r => r.s === "bad").length} красных · ${risks.filter(r => r.s === "warn").length} жёлтых · все выведены из полей плана`)}
      ${kpi("bad", "Точка отказа", "Руководитель проекта", (p=>`по файлу: ${p.tasks} работ, пик ${Math.round(p.peak*100)}%, ${U.wd(p.overDays)} перегруза, дублей должности нет`)(D.roles.find(r=>r.name==="Руководитель проекта")))}
      ${kpi("warn", "Надёжность расписания", "низкая", `связей ${D.meta.linksN} на ${D.meta.stagesN * 6} работ; старты схлопнуты; 12 из 13 вех — даты-заглушки ${AI}`)}
      ${kpi("none", "Стоимостные риски", "нет данных", "нулевые ставки и бюджетные поля в файле")}
    </div>

    ${card("Развёрнутый прогноз: стадии и продукты к базовому плану",
      "Δ = тек. план − база (кал. дни). Статус продукта считается по его работам.", AI,
      tbl(["Стадия / продукт", "Работ", "База → прогноз", "Δ макс, дн", "Работ вне базы", "Статус"],
        S.flatMap(st => {
          const rows = [];
          st.products.forEach(p => {
            const outside = p.tasks.filter(q => (q.dv || 0) > 0).length;
            rows.push([`<span class="mono">${esc(p.wbs)}</span> ${esc(p.name)}`, p.tasks.length,
              `${ru(p.bFinish)} → ${ru(p.finish)}`,
              p.dv > 0 ? `<span class="bad-t">+${p.dv}</span>` : "0",
              outside ? `<span class="bad-t">${outside}</span>` : "0",
              chip(outside ? "bad" : (p.dv || 0) > 0 ? "bad" : (p.finish > p.rollupMax ? "warn" : "ok"), outside ? "вне базы" : p.finish > p.rollupMax ? "сводная ≠ работы" : "в плане")]);
          });
          rows.unshift([`<strong>${esc(st.name)}</strong>`, "", `${ru(st.bFinish)} → ${ru(st.finish)}`,
            st.dv > 0 ? `+${st.dv}` : "0", "", chip(st.dv > 0 || (st.finish > st.rollupMax) ? "warn" : "ok", "по сводной — см. продукты")]);
          return rows;
        })
      ))}

    ${card("Инциденты и изменения за отчётный период (полный список)",
      `Отчётная дата ${ru(D.meta.reportDate)} — до старта работ ${ru(D.meta.projectStart)}. Фактического исполнения нет; все инциденты — расхождения плана к базе и внутренней вёрстке.`, null,
      tbl(["Период", "Инцидент / изменение", "Как влияет", "Статус"], [
        ["26.10–05.11", `<strong>ABC-XYZ анализ 1С (1.1.1):</strong> план 05.11 против базы 30.10 (<span class="bad-t">+6 кал. дн</span>) при росте объёма 40→72 ч (+80%)`,
          "стадия 1 стартует с уже заложенным опозданием ключевой аналитической работы; резерва TF=0 — пойдёт вперёд по цепочке", chip("bad", "отклонение от базы")],
        ["26–27.10", "<strong>Веха 1.3.2.1 «Требования к аналитике зафиксированы»</strong> сдвинута с 26.10 на 27.10 (+1 дн)",
          "единственная «живая» веха — ранний сигнал сползания диагностики", chip("bad", "отклонение от базы")],
        ["22.10.2026", "<strong>Старты всех работ схлопнуты в 26.10</strong> (план и база) при 27 связях на 41 задаче",
          "прогноз зависимостей недостоверен: 12 из 13 вех стоят на 26.10, контрольные точки этапов потеряны", chip("bad", "расхождение плана")],
        ["22.10.2026", "<strong>Сводные окончания позже работ:</strong> стадия 1 +10 кал. дн, стадия 2 +10 (продукт 2.2 +11), стадия 3 +7, стадия 4 +3",
          "отчёт по стадиям ≠ отчёт по работам; планfinish 27.11 сводной может не соответствовать фактической логике", chip("bad", "расхождение плана")],
        ["22.10.2026", "<strong>Аудит данных 1С (1.3.2):</strong> объём 24→48 ч (+100%) при тех же границах и назначенном на 3 дня слоте",
          "закладка на перегруз Ведущего аналитика 1С и HR-директора (uid4) в конце октября", chip("warn", "есть угроза")],
        ["22.10.2026", "<strong>Дубли должностей в реестре:</strong> HR-директор ×5, IT-директор ×2, Ведущий аналитик 1С ×2",
          "если это один человек — его фактическая мощность завышена в 2–5 раз и перегрузов ещё больше; нужно подтверждение", chip("warn", "есть угроза")],
      ]))}

    ${card("Реестр рисков (обзор рисков: нехватка ресурсов, длительность, резервы)",
      "Вероятность: доля перегруженных дней в горизонте проекта, минимум 0,25; влияние — по нулевым резервам (TF=0 цепочек).", AI,
      tbl(["Код", "Риск", "Объект", "Вероятность", "Влияние", "Когда", "Резерв", "Статус"],
        risks.map(r => [`<span class="mono">${r.id}</span>`, r.what, r.who,
          `<span class="prob p-${r.prob >= 0.6 ? "high" : r.prob >= 0.4 ? "mid" : "low"}"><span class="pb"><span class="pf" style="width:${Math.round(r.prob * 100)}%"></span></span>${Math.round(r.prob * 100)}%</span>`,
          r.impact, `<span class="mono">${r.when}</span>`, r.cover ? `<span class="muted">×${r.cover} записей</span>` : '<span class="bad-t">0 — нет</span>',
          chip(r.s, r.s === "bad" ? "критично" : "есть угроза")
        ])))}

    ${card("План митигации: вернуть проект в план и закрыть дефициты", "Действие, закрываемый риск, ответственный-должность, срок и проверка результата — вывод из окон рисков и вех плана.", AI,
      tbl(["Действие", "Закрывает риски", "Ответственный (должность)", "Срок", "Проверка результата"], [
        ["Пересобрать расписание: назначить реальные старты по зависимостям и разнести вехи этапов по фактическим датам", "R6, R7", "Руководитель проекта + PMO", `<span class="mono">до 26.10.2026</span> (до старта)`, "появится критический путь; вехи перестанут быть заглушками"],
        ["Подтвердить у функциональных руководителей, сколько реальных людей стоит за 21 должностью в реестре (HR-директор ×5 и др.)", "R5", "Куратор проекта", "25.10.2026", "мощность по ролям либо снята, либо подтверждена дублями"],
        ["Снять 4–5 управляющих работ с единственного РП (делегируемую часть — на Куратора и РОП-замену внутри окон 3–4)", "R1", "Куратор проекта", "29.10.2026", "пик загрузки РП ≤100% в 26.10–20.11"],
        ["Разнести одновременные работы РОП (10 раб. дн перегруза 26.10–06.11) по резервам 2.3 и 1.2", "R2", "Руководитель проекта", "30.10.2026", "перегруз РОП = 0 дней"],
        ["Внести изменения базы по 1.1.1 и 1.3.2 (объём +80%/+100%) или зафиксировать срез базы для отчётности", "R4, R7", "PMO", "до окончания стадии 1 (10.11.2026)", "отчёт «план/факт» снова сравним с утверждённой базой"],
        ["Синхронизировать сводные даты стадий с работами (ручные финиши убрать, включить rollup)", "R8", "PMO", "14.11.2026", "сводная = максимум работ, отчёт по стадии не расходится"],
        ["Завести еженедельное заполнение Progress/Actual с 26.10 (иначе отчётность 30.11 вновь будет «0%»)", "все", "Руководитель проекта", "еженедельно", "значения PercentWorkComplete отличны от 0"],
      ]) +
      `<div class="foot-note">Ответственные указаны должностями: имён исполнителей MSPDI-файл не содержит. Сроки привязаны к датам начала окон риска и вехам плана. <span class="ai">оценка ИИ</span></div>`)}

    ${card("Чего не хватает в данных", "Блоки с неполной информацией показаны честно.", null,
      `<ul class="obs">
        <li><b>Фактическое исполнение:</b> Progress/Actual по всем работам 0 — статус на 22.10 описывает только план.</li>
        <li><b>Бюджет и стоимость:</b> нулевые ставки и Work-contour — финансовые риски и EVM недоступны.</li>
        <li><b>Имена и роли людей:</b> ресурсы-должности без привязки к персонам; дубли должностей не расшифрованы.</li>
        <li><b>Зависимости:</b> ${D.meta.linksN} связей на 41 строку — календарь частично «расставлен руками».</li>
      </ul>`)}
    `;
  };

  function register() {
    const out = [];
    D.roles.filter(r => r.overDays > 0).forEach((r, i) => {
      out.push({ id: "R" + (i + 1), who: r.name, prob: Math.min(0.9, 0.25 + (r.overDays / PWD) * 0.75),
        what: `нехватка мощности: пик ${Math.round(r.peak * 100)}% при 100% доступности, ${r.tasks} назначенных работ${D.dups[r.name] ? `, в реестре ${D.dups[r.name].length} записи этой должности` : ""}`,
        impact: r.overDays > 8 ? "задержки в этом окне сдвигают финиши работ с TF=0, далее — вехи «Этап завершён»" : "локальные просрочки работ внутри стадии; пока терпится в резервы продуктов",
        when: `${r.windows.map(w => ru(w.from)).join(", ")} (${U.wd(r.overDays)})`, cover: D.dups[r.name] ? D.dups[r.name].length : 0, s: r.overDays > 8 ? "bad" : "warn",
      });
    });
    const n = out.length;
    out.push({ id: "R" + (n + 1), who: "Единственный РП без дубля", prob: 0.85,
      what: `Руководитель проекта ведёт ${(()=>{const p=D.roles.find(r=>r.name==="Руководитель проекта");return p.tasks+" работ"+", пик "+Math.round(p.peak*100)+"%"})()} — второго руководителя в реестре нет (пики завышены схлопнутыми стартами — см. оговорку)`,
      impact: "отпуск/болезнь РП останавливает все четыре стадии; срок 27.11 держится на одном человеке",
      when: "26.10 — 20.11", cover: 0, s: "bad" });
    out.push({ id: "R" + (n + 2), who: "Структура плана", prob: 0.75,
      what: "схлопнутые старты и ручные сводные даты: расчёт критического пути и прогноза 27.11 недостоверен",
      impact: "любой прогноз в дашборде наследует ошибку вёрстки; отклонения вскроются после начала работ",
      when: "постоянно до пересборки", cover: 0, s: "bad" });
    out.push({ id: "R" + (n + 3), who: "Объём к базе (1.1.1)", prob: 0.6,
      what: "рост трудозатрат +32 ч и сдвиг +6 дн без изменения базы",
      impact: "оценка «в плане» стадии 1 на самом деле уже опоздывающая; база искажает отчётность",
      when: "26.10 — 05.11", cover: 0, s: "warn" });
    return out;
  }
  function card(t, sub, aib, body) {
    return `<section class="card"><div class="head"><h2 class="t">${t} ${aib || ""}</h2>${sub ? `<p class="sub">${sub}</p>` : ""}</div><div class="body">${body}</div></section>`;
  }
  function tbl(head, rows) {
    return `<div class="twrap"><table><thead><tr>${head.map(h => `<th>${h}</th>`).join("")}</tr></thead><tbody>${rows.map(r => `<tr>${r.map(x => `<td>${x}</td>`).join("")}</tr>`).join("")}</tbody></table></div>`;
  }
  const css = document.createElement("style");
  css.textContent = `.bad-t{color:#b02a2e;font-weight:600}.obs{margin:0;padding-left:20px;font-size:13px;color:#666c7d}.obs li{margin-bottom:7px}`;
  document.head.appendChild(css);
})();

;

</script>
</body>
</html>
