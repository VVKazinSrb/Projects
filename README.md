<!doctype html>
<html lang="ru">
  <head><script>var __mr='all',__md='3amyjd62.qwenwork.page';document.addEventListener('DOMContentLoaded', function () {
  var BAR_HEIGHT = 48;
  var BRAND_URL = 'https://qwenwork.ai/';
  // 品牌资源直接引用官网上的国际版资产（与 CN 版引用 CDN 图片的做法一致）：注入脚本会
  // 进到每个用户页面，内联 data URI 会让每个 HTML 响应都多背十几 KB。
  var LOGO_URL = 'https://qwenwork.ai/assets/website-global/qwenwork-logo.svg';
  var FAVICON_URL = 'https://qwenwork.ai/app/favicon.svg';
  var isDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;

  if (!isDark) {
    try {
      var sample = getComputedStyle(document.body).backgroundColor;
      if (sample === 'rgba(0, 0, 0, 0)' || sample === 'transparent') {
        sample = getComputedStyle(document.documentElement).backgroundColor;
      }
      if (sample && sample !== 'rgba(0, 0, 0, 0)' && sample !== 'transparent') {
        var m = sample.match(/\d+/g);
        if (m) {
          var brightness = (parseInt(m[0]) * 299 + parseInt(m[1]) * 587 + parseInt(m[2]) * 114) / 1000;
          isDark = brightness < 128;
        }
      }
    } catch (e) {}
  }

  var SHARED_CSS = '<style>' +
    '.mulepage-close-dark{color:rgba(255,255,255,0.3);transition:color 0.2s ease}' +
    '.mulepage-close-dark:hover{color:#ffffff}' +
    '.mulepage-close-light{color:rgba(0,0,0,0.3);transition:color 0.2s ease}' +
    '.mulepage-close-light:hover{color:#000000}' +
    '#mulepage-footer-link{display:inline-flex;align-items:center;line-height:0;outline:none}' +
    '.mulepage-footer-brand{display:inline-flex;align-items:center;box-sizing:border-box;height:32px;max-width:156px;overflow:hidden;padding:4px 12px;border-radius:999px;background:' + (isDark ? 'rgba(26,26,26,0.85)' : 'rgba(255,255,255,0.85)') + ';backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);box-shadow:0 0 0 0.5px ' + (isDark ? 'rgba(255,255,255,0.12)' : 'rgba(0,0,0,0.12)') + ',0 8px 24px -4px ' + (isDark ? 'rgba(0,0,0,0.28)' : 'rgba(0,0,0,0.07)') + ';transition:max-width 260ms cubic-bezier(0.22,1,0.36,1);will-change:max-width;white-space:nowrap}' +
    '.mulepage-footer-brand-hint{display:inline-block;max-width:0;margin-left:0;overflow:hidden;opacity:0;color:' + (isDark ? 'rgba(255,255,255,0.72)' : 'rgba(0,0,0,0.64)') + ';font-size:14px;font-weight:400;line-height:20px;transition:max-width 260ms cubic-bezier(0.22,1,0.36,1),margin-left 260ms cubic-bezier(0.22,1,0.36,1),opacity 180ms ease-out;will-change:max-width,opacity}' +
    '#mulepage-footer:hover .mulepage-footer-brand,#mulepage-footer:focus-within .mulepage-footer-brand{max-width:360px}' +
    '#mulepage-footer:hover .mulepage-footer-brand-hint,#mulepage-footer:focus-within .mulepage-footer-brand-hint{max-width:188px;margin-left:8px;opacity:1}' +
    '.mulepage-float-close{display:inline-flex;align-items:center;justify-content:center;max-width:0;margin-left:0;overflow:hidden;opacity:0;transition:max-width 0.2s ease,margin-left 0.2s ease,opacity 0.15s ease;padding:0;border:none;background:none;cursor:pointer;font-size:16px;line-height:1;font-weight:300;height:16px;will-change:max-width,opacity}' +
    '.mulepage-float:hover .mulepage-float-close{max-width:14px;margin-left:4px;opacity:1}' +
    '</style>';
  document.head.insertAdjacentHTML('beforeend', SHARED_CSS);

  var brandAssetFilter = isDark ? 'filter:invert(1);' : '';
  var BRAND_MARK = '<img src="' + LOGO_URL + '" alt="QwenWork" width="132" height="24" style="display:block;user-select:none;' + brandAssetFilter + '" />';
  var TOP_BRAND_LOGO = '<span style="display:inline-flex;align-items:center;justify-content:center;width:156px;height:32px;padding:4px 12px;box-sizing:border-box;border-radius:999px;' +
    'background:' + (isDark ? 'rgba(255,255,255,0.12)' : '#f5f5f5') + ';">' + BRAND_MARK + '</span>';
  var FOOTER_BRAND_LOGO = '<span class="mulepage-footer-brand">' + BRAND_MARK +
    '<span class="mulepage-footer-brand-hint">AI-generated. Please verify.</span></span>';

  var bannerBg = isDark ? '#050505' : '#ffffff';
  var bannerBorder = isDark ? 'rgba(255,255,255,0.08)' : 'rgba(0,0,0,0.06)';
  var bannerColor = isDark ? '#fff' : '#000';
  var bannerDividerColor = isDark ? 'rgba(255,255,255,0.24)' : 'rgba(0,0,0,0.16)';
  var bannerCloseClass = isDark ? 'mulepage-close-dark' : 'mulepage-close-light';

  var BANNER = '<div id="mulepage-bar" dir="ltr" style="position:fixed;top:0;left:0;width:100%;height:' + BAR_HEIGHT + 'px;' +
    'background:' + bannerBg + ';border-bottom:1px solid ' + bannerBorder + ';color:' + bannerColor + ';' +
    'box-sizing:border-box;display:flex;align-items:center;gap:8px;padding:8px;' +
    'font-family:Inter,-apple-system,BlinkMacSystemFont,\'Segoe UI\',sans-serif;' +
    'font-size:14px;font-weight:500;line-height:20px;z-index:2147483647;">' +
    '<span aria-hidden="true" style="flex:1 1 0;height:32px;"></span>' +
    '<div style="display:flex;align-items:center;gap:8px;white-space:nowrap;">' +
    '<span>Created with</span>' +
    '<span id="mulepage-bar-link" role="link" tabindex="0" aria-label="Open QwenWork" style="display:inline-flex;align-items:center;cursor:pointer;line-height:0;">' +
    TOP_BRAND_LOGO + '</span>' +
    '<span aria-hidden="true" style="width:1px;height:16px;margin:0 4px;background:' + bannerDividerColor + ';"></span>' +
    '<span id="mulepage-bar-cta" role="link" tabindex="0" aria-label="Create a website with QwenWork" style="display:inline-flex;align-items:center;gap:4px;padding:6px 12px;border-radius:999px;cursor:pointer;">' +
    '<span>Create your website with AI</span><span aria-hidden="true" style="font-size:16px;line-height:16px;">\u2192</span></span>' +
    '</div>' +
    '<span style="flex:1 1 0;display:flex;justify-content:flex-end;align-items:center;">' +
    '<button id="mulepage-bar-close" class="' + bannerCloseClass + '" aria-label="Close QwenWork branding bar" style="display:inline-flex;align-items:center;justify-content:center;width:32px;height:32px;padding:8px;background:none;border:none;border-radius:999px;' +
    'font-size:18px;cursor:pointer;line-height:16px;font-weight:300;">\u00d7</button></span>' +
    '</div>';

  var floatCloseColor = isDark ? 'rgba(255,255,255,0.35)' : 'rgba(0,0,0,0.3)';
  var floatCloseHover = isDark ? '#ffffff' : '#000000';
  var FOOTER = '<div id="mulepage-footer" dir="ltr" class="mulepage-float" style="position:fixed !important;bottom:16px !important;right:16px !important;z-index:2147483646;' +
    'display:inline-flex;align-items:center;padding:0;cursor:pointer;background:transparent;border:0;box-shadow:none;' +
    'font-family:Inter,-apple-system,BlinkMacSystemFont,\'Segoe UI\',\'Helvetica Neue\',sans-serif;">' +
    '<span id="mulepage-footer-link" role="link" tabindex="0" aria-label="Open QwenWork" style="display:inline-flex;align-items:center;line-height:0;">' +
    FOOTER_BRAND_LOGO + '</span></div>';

  var openQwenWork = function (content) {
    window.open(BRAND_URL + '?utm_source=pages&utm_medium=banner&utm_campaign=pages_branding&utm_content=' + content, '_blank', 'noopener');
  };
  var bindActivation = function (element, content) {
    if (!element) return;
    element.addEventListener('click', function () { openQwenWork(content); });
    element.addEventListener('keydown', function (event) {
      if (event.key === 'Enter' || event.key === ' ') { event.preventDefault(); openQwenWork(content); }
    });
  };

  if (__mr === 'all') {
    document.body.insertAdjacentHTML('afterbegin', BANNER);
    bindActivation(document.getElementById('mulepage-bar-link'), 'top_bar');
    bindActivation(document.getElementById('mulepage-bar-cta'), 'top_bar');

    var existingIcon = document.querySelector('link[rel="icon"],link[rel="shortcut icon"]');
    if (!existingIcon) {
      var fi = document.createElement('link');
      fi.rel = 'icon';
      fi.type = 'image/svg+xml';
      fi.href = FAVICON_URL;
      document.head.appendChild(fi);
    }

    var origPT = parseFloat(getComputedStyle(document.body).paddingTop) || 0;
    document.body.style.paddingTop = (origPT + BAR_HEIGHT) + 'px';
    var all = document.querySelectorAll('*');
    var shifted = [];
    for (var i = 0; i < all.length; i++) {
      var el = all[i];
      if (el.id && el.id.indexOf('mulepage') === 0) continue;
      var cs = getComputedStyle(el);
      if (cs.position === 'fixed') {
        var t = parseFloat(cs.top);
        if (isNaN(t)) t = 0;
        el.style.top = (t + BAR_HEIGHT) + 'px';
        shifted.push({ el: el, orig: t });
      }
    }
    document.getElementById('mulepage-bar-close').addEventListener('click', function () {
      document.getElementById('mulepage-bar').remove();
      document.body.style.paddingTop = origPT + 'px';
      for (var j = 0; j < shifted.length; j++) shifted[j].el.style.top = shifted[j].orig + 'px';
    });
  }

  if (__mr) {
    document.body.insertAdjacentHTML('beforeend', FOOTER);
    bindActivation(document.getElementById('mulepage-footer-link'), 'bottom_bar');
    if (__mr === 'footer') {
      var floatEl = document.getElementById('mulepage-footer');
      if (floatEl) {
        var closeBtn = document.createElement('button');
        closeBtn.className = 'mulepage-float-close';
        closeBtn.style.color = floatCloseColor;
        closeBtn.setAttribute('aria-label', 'Close QwenWork badge');
        closeBtn.textContent = '\u00d7';
        closeBtn.addEventListener('mouseenter', function () { closeBtn.style.color = floatCloseHover; });
        closeBtn.addEventListener('mouseleave', function () { closeBtn.style.color = floatCloseColor; });
        closeBtn.addEventListener('click', function (event) { event.stopPropagation(); floatEl.remove(); });
        floatEl.appendChild(closeBtn);
      }
    }
  }

  var canon = document.createElement('link');
  canon.rel = 'canonical';
  canon.href = 'https://' + location.hostname + '/';
  document.head.appendChild(canon);

  var ogDomain = __md;
  var ogTitle = document.title || ogDomain;
  var ogTags = [
    ['og:title', ogTitle],
    ['og:url', 'https://' + location.hostname + '/'],
    ['og:type', 'website'],
    ['og:image', 'https://qwenwork.page/og/' + ogDomain + '.webp']
  ];
  for (var n = 0; n < ogTags.length; n++) {
    var existing = document.querySelector('meta[property="' + ogTags[n][0] + '"]');
    if (existing) existing.remove();
    var meta = document.createElement('meta');
    meta.setAttribute('property', ogTags[n][0]);
    meta.setAttribute('content', ogTags[n][1]);
    document.head.appendChild(meta);
  }
});
</script>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Интерактивная панель управления портфелем проектов Sber Devices: статусы проектов, загрузка ресурсов, реестр рисков и план митигации."
    />
    <title>Портфель проектов · панель управления</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&family=PT+Serif:ital,wght@0,400;0,700;1,400&display=swap"
      rel="stylesheet"
    />
    <script type="module" crossorigin src="/assets/index-CR3W-R66.js"></script>
    <link rel="stylesheet" crossorigin href="/assets/index-CgPA5v5t.css">
  </head>
  <body>
    <div id="app"></div>
    <div id="root"></div>
    <script src="/data.js"></script>
    <script src="/app.js"></script>
    <script src="/mode-project.js"></script>
    <script src="/mode-resources.js"></script>
    <script src="/mode-risks.js"></script>
  </body>
</html>
