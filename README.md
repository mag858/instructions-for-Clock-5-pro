
<html lang="ru">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  <meta name="theme-color" content="#D5E7FF">
  <title>Clock-5 Pro / Pro Max — руководство | MAG industries</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;700;800&family=Orbitron:wght@600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --mag-red: #F31200;
      --mag-gold: #F3A000;
      --mag-amber: #fab002;
      --bg-soft: #D5E7FF;
      --bg-deep: #0a0f1a;
      --text: #0d1117;
      --text-muted: #4a5568;
      --card: rgba(255, 255, 255, 0.92);
      --shadow: 0 12px 40px rgba(15, 23, 42, 0.12);
      --radius: 18px;
      --ease-out: cubic-bezier(0.22, 1, 0.36, 1);
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      font-family: "Manrope", system-ui, sans-serif;
      color: var(--text);
      background: var(--bg-soft);
      line-height: 1.65;
      overflow-x: hidden;
      -webkit-text-size-adjust: 100%;
      text-size-adjust: 100%;
    }

    /* Animated background grid */
    .bg-grid {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      background-image:
        linear-gradient(rgba(243, 18, 0, 0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(243, 160, 0, 0.05) 1px, transparent 1px);
      background-size: 48px 48px;
      animation: gridDrift 28s linear infinite;
    }

    @keyframes gridDrift {
      0% { transform: translate(0, 0); }
      100% { transform: translate(-48px, -48px); }
    }

    .glow-orb {
      position: fixed;
      width: min(70vw, 520px);
      height: min(70vw, 520px);
      border-radius: 50%;
      filter: blur(80px);
      opacity: 0.45;
      pointer-events: none;
      z-index: 0;
    }

    .glow-orb--1 {
      top: -10%;
      right: -15%;
      background: radial-gradient(circle, var(--mag-red), transparent 70%);
      animation: float1 14s ease-in-out infinite;
    }

    .glow-orb--2 {
      bottom: 10%;
      left: -20%;
      background: radial-gradient(circle, var(--mag-gold), transparent 70%);
      animation: float2 18s ease-in-out infinite;
    }

    @keyframes float1 {
      0%, 100% { transform: translate(0, 0) scale(1); }
      50% { transform: translate(-30px, 40px) scale(1.08); }
    }

    @keyframes float2 {
      0%, 100% { transform: translate(0, 0) scale(1); }
      50% { transform: translate(40px, -30px) scale(1.05); }
    }

    .wrap {
      position: relative;
      z-index: 1;
      max-width: 900px;
      margin: 0 auto;
      padding: 0 max(16px, env(safe-area-inset-left)) max(48px, env(safe-area-inset-bottom)) max(16px, env(safe-area-inset-right));
      padding-top: max(12px, env(safe-area-inset-top));
    }

    header.site-header {
      padding: 28px 0 8px;
      animation: heroIn 1s var(--ease-out) both;
    }

    @keyframes heroIn {
      from {
        opacity: 0;
        transform: translateY(-16px);
      }
    }

    .brand-block {
      text-align: center;
      margin-bottom: 4px;
    }

    .brand {
      display: inline-block;
      font-family: "Orbitron", sans-serif;
      font-weight: 700;
      font-size: clamp(1.35rem, 5.5vw, 2rem);
      color: var(--mag-red);
      letter-spacing: 0.04em;
      text-decoration: none;
      transition: transform 0.35s var(--ease-out), filter 0.35s;
    }

    .brand:hover {
      transform: scale(1.02);
      filter: drop-shadow(0 0 12px rgba(243, 18, 0, 0.35));
    }

    .brand:focus-visible {
      outline: 3px solid var(--mag-gold);
      outline-offset: 4px;
      border-radius: 4px;
    }

    .tagline {
      margin-top: 10px;
      font-weight: 800;
      color: var(--mag-gold);
      font-size: clamp(1rem, 3.2vw, 1.2rem);
      text-align: center;
      line-height: 1.3;
    }

    .tagline-sub {
      margin-top: 4px;
      font-size: clamp(0.88rem, 2.8vw, 0.95rem);
      color: var(--text-muted);
      font-style: italic;
      text-align: center;
      line-height: 1.35;
      padding: 0 8px;
    }

    .hero {
      margin-top: 24px;
      padding: clamp(22px, 5vw, 44px);
      border-radius: var(--radius);
      text-align: center;
      background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(213,231,255,0.85) 100%);
      border: 1px solid rgba(243, 18, 0, 0.12);
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
      animation: heroIn 1s 0.1s var(--ease-out) both;
    }

    .hero::before {
      content: "";
      position: absolute;
      top: 0;
      left: -100%;
      width: 60%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(250, 176, 2, 0.15), transparent);
      animation: shine 6s ease-in-out infinite;
    }

    @keyframes shine {
      0% { left: -100%; }
      40%, 100% { left: 120%; }
    }

    .hero h1 {
      margin: 0 0 8px;
      font-family: "Orbitron", sans-serif;
      font-size: clamp(1.35rem, 4vw, 1.85rem);
      color: var(--text);
      line-height: 1.25;
    }

    .hero-badge {
      display: inline-flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
      padding: 6px 14px;
      border-radius: 999px;
      background: linear-gradient(90deg, var(--mag-red), #ff5c4d);
      color: #fff;
      font-size: 0.75rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      margin-bottom: 16px;
      animation: pulseBadge 3s ease-in-out infinite;
    }

    @keyframes pulseBadge {
      0%, 100% { box-shadow: 0 0 0 0 rgba(243, 18, 0, 0.35); }
      50% { box-shadow: 0 0 0 10px rgba(243, 18, 0, 0); }
    }

    .hero-meta {
      font-size: 0.9rem;
      color: var(--text-muted);
    }

    nav.toc {
      margin-top: 28px;
      padding: 20px 22px;
      border-radius: var(--radius);
      background: var(--card);
      border: 1px solid rgba(0,0,0,0.06);
      box-shadow: var(--shadow);
      animation: fadeUp 0.8s 0.25s var(--ease-out) both;
    }

    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
    }

    nav.toc h2 {
      margin: 0 0 14px;
      font-size: 0.95rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--mag-red);
      text-align: center;
    }

    .toc-list {
      list-style: none;
      margin: 0;
      padding: 0;
      display: grid;
      gap: 8px;
    }

    .toc-list a {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 14px 14px;
      min-height: 48px;
      border-radius: 12px;
      color: var(--text);
      text-decoration: none;
      font-weight: 600;
      font-size: clamp(0.95rem, 3.5vw, 1rem);
      -webkit-tap-highlight-color: rgba(243, 160, 0, 0.25);
      transition: background 0.25s, transform 0.25s var(--ease-out), color 0.2s;
    }

    .toc-list a::before {
      content: "";
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--mag-gold);
      flex-shrink: 0;
      transition: transform 0.3s var(--ease-out);
    }

    .toc-list a:hover,
    .toc-list a:active {
      background: rgba(243, 160, 0, 0.12);
    }

    @media (hover: hover) and (pointer: fine) {
      .toc-list a:hover {
        transform: translateX(4px);
      }
      .toc-list a:hover::before {
        transform: scale(1.4);
        background: var(--mag-red);
      }
    }

    section {
      margin-top: 36px;
      padding: 26px 26px 28px;
      border-radius: var(--radius);
      background: var(--card);
      border: 1px solid rgba(0,0,0,0.06);
      box-shadow: var(--shadow);
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.65s var(--ease-out), transform 0.65s var(--ease-out);
      transition-delay: var(--reveal-delay, 0s);
    }

    section.is-visible {
      opacity: 1;
      transform: translateY(0);
    }

    section:nth-of-type(1) { --reveal-delay: 0.02s; }
    section:nth-of-type(2) { --reveal-delay: 0.06s; }
    section:nth-of-type(3) { --reveal-delay: 0.1s; }
    section:nth-of-type(4) { --reveal-delay: 0.14s; }
    section:nth-of-type(5) { --reveal-delay: 0.18s; }
    section:nth-of-type(6) { --reveal-delay: 0.22s; }
    section:nth-of-type(7) { --reveal-delay: 0.26s; }
    section:nth-of-type(8) { --reveal-delay: 0.3s; }
    section:nth-of-type(9) { --reveal-delay: 0.34s; }

    section h2 {
      margin: 0 0 18px;
      font-family: "Orbitron", sans-serif;
      font-size: clamp(1rem, 3.8vw, 1.15rem);
      color: var(--mag-red);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 10px 12px;
      line-height: 1.35;
    }

    section h2 .num {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-width: 36px;
      height: 36px;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--mag-amber), var(--mag-gold));
      color: #1a1a1a;
      font-size: 0.85rem;
      font-weight: 800;
    }

    section ul {
      margin: 0;
      padding-left: 1.2rem;
    }

    section li {
      margin-bottom: 10px;
    }

    section li strong {
      color: var(--text);
    }

    .steps {
      counter-reset: step;
      list-style: none;
      padding: 0;
      margin: 0;
    }

    .steps li {
      position: relative;
      padding-left: 48px;
      margin-bottom: 16px;
      counter-increment: step;
    }

    .steps li::before {
      content: counter(step);
      position: absolute;
      left: 0;
      top: 0;
      width: 34px;
      height: 34px;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--mag-red), #ff6b5c);
      color: #fff;
      font-weight: 800;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 14px rgba(243, 18, 0, 0.35);
    }

    .note {
      margin-top: 16px;
      padding: 16px 16px;
      border-radius: 12px;
      background: linear-gradient(90deg, rgba(250, 176, 2, 0.2), rgba(213, 231, 255, 0.5));
      border-left: 4px solid var(--mag-gold);
      font-size: clamp(0.9rem, 3.2vw, 0.95rem);
      line-height: 1.55;
      word-wrap: break-word;
      overflow-wrap: break-word;
    }

    .note a {
      color: var(--mag-red);
      font-weight: 700;
      text-decoration: underline;
      text-underline-offset: 3px;
    }

    .spec-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.92rem;
      margin-top: 8px;
    }

    .spec-table th,
    .spec-table td {
      text-align: left;
      padding: 12px 14px;
      border-bottom: 1px solid rgba(0,0,0,0.08);
    }

    .spec-table th {
      width: 42%;
      color: var(--text-muted);
      font-weight: 600;
    }

    .footer-bar {
      margin-top: 48px;
      padding: 28px;
      border-radius: var(--radius);
      text-align: center;
      background: linear-gradient(135deg, #1a1f2e 0%, var(--bg-deep) 100%);
      color: #e2e8f0;
      animation: fadeUp 0.8s 0.4s var(--ease-out) both;
    }

    .footer-bar a {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      margin-top: 14px;
      padding: 14px 22px;
      min-height: 48px;
      width: 100%;
      max-width: 100%;
      box-sizing: border-box;
      border-radius: 999px;
      background: linear-gradient(90deg, var(--mag-amber), var(--mag-gold));
      color: #1a1a1a;
      font-weight: 800;
      font-size: clamp(0.9rem, 3.5vw, 1rem);
      text-decoration: none;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0.15);
      transition: transform 0.25s var(--ease-out), box-shadow 0.25s;
    }

    @media (min-width: 480px) {
      .footer-bar a {
        width: auto;
        max-width: none;
      }
    }

    @media (hover: hover) and (pointer: fine) {
      .footer-bar a:hover {
        transform: translateY(-2px) scale(1.02);
        box-shadow: 0 8px 24px rgba(250, 176, 2, 0.45);
      }
    }

    .footer-bar p {
      margin: 0;
      font-size: clamp(0.88rem, 3.2vw, 0.95rem);
      line-height: 1.55;
      opacity: 0.9;
      padding: 0 4px;
    }

    .pro-max-tag {
      display: inline-block;
      margin-left: 8px;
      padding: 2px 8px;
      border-radius: 6px;
      background: rgba(243, 18, 0, 0.12);
      color: var(--mag-red);
      font-size: 0.7rem;
      font-weight: 800;
      vertical-align: middle;
      letter-spacing: 0.04em;
    }

    @media (max-width: 600px) {
      .wrap {
        padding-left: max(14px, env(safe-area-inset-left));
        padding-right: max(14px, env(safe-area-inset-right));
      }
      .brand {
        padding: 10px 16px;
        margin: -6px 0;
      }
      section { padding: 20px 16px; margin-top: 28px; }
      nav.toc { padding: 18px 14px; }
      .spec-table th, .spec-table td { display: block; width: 100%; }
      .spec-table th { padding-bottom: 4px; border: none; }
      .glow-orb { opacity: 0.32; filter: blur(64px); }
      .bg-grid { background-size: 36px 36px; }
    }

    @media (prefers-reduced-motion: reduce) {
      .bg-grid, .glow-orb--1, .glow-orb--2, .hero::before, .hero-badge {
        animation: none !important;
      }
      html { scroll-behavior: auto; }
      section {
        opacity: 1 !important;
        transform: none !important;
        transition: none !important;
      }
    }
  </style>
</head>
<body>
  <div class="bg-grid" aria-hidden="true"></div>
  <div class="glow-orb glow-orb--1" aria-hidden="true"></div>
  <div class="glow-orb glow-orb--2" aria-hidden="true"></div>

  <div class="wrap">
    <header class="site-header">
      <div class="brand-block">
        <a class="brand" href="https://mag858.github.io/MAG-industries/">MAG INDUSTRIES</a>
        <div class="tagline">future — right now</div>
        <div class="tagline-sub">будущее — прямо сейчас</div>
      </div>

      <div class="hero">
        <span class="hero-badge">Руководство пользователя</span>
        <h1>Смарт-часы Clock-5 Pro / Clock-5 Pro Max</h1>
        <p class="hero-meta">Универсальная инструкция · апрель 2026</p>
      </div>

      <nav class="toc" aria-label="Содержание">
        <h2>Содержание</h2>
        <ul class="toc-list">
          <li><a href="#safety">Безопасность и предупреждения</a></li>
          <li><a href="#kit">Комплект поставки</a></li>
          <li><a href="#controls">Внешний вид и управление</a></li>
          <li><a href="#first">Первое включение и зарядка</a></li>
          <li><a href="#usage">Работа с часами</a></li>
          <li><a href="#settings">Основные настройки</a></li>
          <li><a href="#battery">Экономия заряда</a></li>
          <li><a href="#trouble">Устранение неисправностей</a></li>
          <li><a href="#specs">Технические характеристики</a></li>
        </ul>
      </nav>
    </header>

    <section id="safety">
      <h2><span class="num">1</span> Меры безопасности и важные предупреждения</h2>
      <ul>
        <li>Не допускайте попадания часов в воду.</li>
        <li>Не разбирайте устройство самостоятельно.</li>
        <li>При появлении раздражения кожи снимите часы и перенастройте ремешок.</li>
      </ul>
    </section>

    <section id="kit">
      <h2><span class="num">2</span> Комплект поставки</h2>
      <ul>
        <li>Смарт-часы</li>
        <li>Ремешок (силиконовый / кожаный / металлический)</li>
        <li>QR-код с инструкцией</li>
      </ul>
    </section>

    <section id="controls">
      <h2><span class="num">3</span> Внешний вид и элементы управления</h2>
      <ul>
        <li><strong>Сенсорный экран</strong> — основное управление касаниями и свайпами.</li>
        <li><strong>Боковая кнопка:</strong> одно нажатие — включение / выключение. (НЕ ВЫКЛЮЧАТЬ ЧАСЫ ПО КНОПКЕ ИНАЧЕ СБИВАЕТЬСЯ ВРЕМЯ)</li>
        <li><strong>Разъём USB Type-C</strong> для зарядки.</li>
        <li><strong>Разъём под карту памяти SD</strong> (если предусмотрен в вашей комплектации).</li>
      </ul>
    </section>

    <section id="first">
      <h2><span class="num">4</span> Первое включение и зарядка</h2>
      <ol class="steps">
        <li>Подключите зарядное устройство к часам.</li>
        <li>Зарядите не менее 1–2 часов (первый раз рекомендуется до 100%).</li>
        <li>Нажмите кнопку — появится логотип, часы включатся.</li>
        <li>Выберите язык. По умолчанию — английский; при необходимости латиницы выберите русский в разделе Quick Settings → Language.</li>
      </ol>
    </section>

    <section id="usage">
      <h2><span class="num">5</span> Работа с часами</h2>
      <ul>
        <li>Свайпы влево и вправо переключают циферблаты по кругу.</li>
        <li>Свайп сверху вниз открывает быстрые настройки (фонарик, Wi‑Fi, режим энергосбережения, перезагрузка и др.).</li>
        <li>Свайп снизу вверх открывает приложения (секундомер, календарь, дыхательная гимнастика).</li>
        <li><strong>Калибровка времени:</strong> удерживайте палец на дисплее около 3 секунд — время синхронизируется при подключённом Wi‑Fi.</li>
        <li><strong>Wi‑Fi:</strong> в быстрых настройках нажмите значок Wi‑Fi, затем удерживайте около 3 секунд — откроется список сетей. Выберите сеть, введите пароль. Должно отображаться <strong>connected</strong>. Чтобы выйти, нажмите на свою сеть в списке.</li>
        <li><strong>Обновление прошивки:</strong> быстрые настройки → Настройки → вкладка Updates. Если статус <strong>none</strong> — прошивка актуальна; если <strong>update</strong> — нажмите Install. Обновление занимает около 2 минут.</li>
      </ul>
    </section>

    <section id="settings">
      <h2><span class="num">6</span> Основные настройки (Настройки / ⚙️)</h2>
      <ul>
        <li><strong>Время</strong> — ручная дата и время без Wi‑Fi; настройка отображения циферблата.</li>
        <li><strong>Обновления</strong> — обновление прошивки и сведения об устройстве.</li>
        <li><strong>Дисплей</strong> — яркость 0–100%, включение экрана по 1 или 2 касаниям, автозатухание.</li>
        <li><strong>Батарея</strong> — ёмкость, число циклов зарядки, износ аккумулятора.</li>
        <li><strong>Язык</strong> — переключение с английского на латиницу (русский).</li>
        <li><strong>Действия</strong> — включение при поднятии руки, отключение вибрации и др. <span class="pro-max-tag">только Pro Max</span></li>
      </ul>
    </section>

    <section id="battery">
      <h2><span class="num">7</span> Рекомендации по экономии заряда</h2>
      <ul>
        <li>Уменьшите яркость до 40–60%.</li>
        <li>Включайте режим энергосбережения.</li>
        <li>Используйте автозатухание яркости экрана.</li>
      </ul>
    </section>

    <section id="trouble">
      <h2><span class="num">8</span> Устранение неисправностей</h2>
      <ul>
        <li><strong>Экран не реагирует</strong> — протрите сухой мягкой тканью, снимите защитную плёнку (если есть), перезагрузите час боковой кнопкой.</li>
        <li><strong>Не подключаются к Wi‑Fi</strong> — «забудьте» сеть в настройках Wi‑Fi на часах, перезагрузите устройство и подключитесь заново.</li>
      </ul>
      <div class="note">Если проблема не решается, обратитесь в <strong>техническую поддержку на официальном сайте</strong> — <a href="https://mag858.github.io/MAG-industries/">mag858.github.io/MAG-industries</a></div>
    </section>

    <section id="specs">
      <h2><span class="num">9</span> Технические характеристики (типичные значения)</h2>
      <table class="spec-table">
        <tr><th>Экран</th><td>1,28″ IPS / TFT, сенсорный</td></tr>
        <tr><th>Аккумулятор</th><td>500 мА·ч</td></tr>
        <tr><th>Время работы</th><td>1–5 дней (зависит от модели и сценария использования)</td></tr>
        <tr><th>Водозащита</th><td>Нет</td></tr>
        <tr><th>Bluetooth</th><td>4.0–5.2 <span class="pro-max-tag">Pro Max</span></td></tr>
      </table>
    </section>

    <div class="footer-bar">
      <p><strong>Поддержка и помощь:</strong> по вопросам обращайтесь в техническую поддержку на официальном сайте MAG Industries.</p>
      <a href="https://mag858.github.io/MAG-industries/">Техподдержка — официальный сайт</a>
      <p style="margin-top:20px;font-size:0.8rem;">© 2026 MAG Industries. Спасибо за покупку!</p>
    </div>
  </div>

  <script>
    (function () {
      var sections = document.querySelectorAll("section");
      if (!("IntersectionObserver" in window)) {
        sections.forEach(function (s) { s.classList.add("is-visible"); });
        return;
      }
      var io = new IntersectionObserver(
        function (entries) {
          entries.forEach(function (e) {
            if (e.isIntersecting) e.target.classList.add("is-visible");
          });
        },
        { rootMargin: "0px 0px -8% 0px", threshold: 0.08 }
      );
      sections.forEach(function (s) { io.observe(s); });
    })();
  </script>
</body>
</html>

