
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Elite VPN</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    min-height: 100vh;
    background: radial-gradient(circle at 50% 0%, #1a1207, #060503 70%);
    font-family: 'Segoe UI', Roboto, sans-serif;
    color: #f0e6d2;
    display: flex;
    justify-content: center;
    padding: 24px 16px 60px;
  }

  .wrap {
    width: 100%;
    max-width: 460px;
    display: flex;
    flex-direction: column;
    gap: 18px;
  }

  /* ====== ОБЩИЕ РАМКИ ====== */
  .card {
    background: linear-gradient(160deg, #14100a, #0a0805);
    border: 1px solid #4a3418;
    border-radius: 22px;
    padding: 22px 18px;
    box-shadow: 0 8px 30px rgba(0,0,0,.6), inset 0 1px 0 rgba(200,150,70,.08);
    position: relative;
    overflow: hidden;
  }

  /* ====== ПЕРВАЯ РАМКА ====== */
  .hero {
    text-align: center;
    padding-top: 30px;
  }

  .free-badge {
    position: absolute;
    top: 14px;
    right: 16px;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 1px;
    color: #c9a86a;
    text-shadow: 0 0 12px rgba(201,168,106,.6);
  }

  .avatar-zone {
    position: relative;
    width: 150px;
    height: 150px;
    margin: 0 auto 18px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .thin-ring {
    position: absolute;
    inset: -12px;
    border-radius: 50%;
    border: 1.5px solid #7a5a2e;
    box-shadow: 0 0 18px rgba(180,130,60,.35);
  }

  .sparkles {
    position: absolute;
    inset: -25px;
    border-radius: 50%;
    background:
      radial-gradient(circle at 20% 30%, rgba(255,215,130,.9) 0 2px, transparent 3px),
      radial-gradient(circle at 80% 20%, rgba(255,200,90,.8) 0 1.5px, transparent 3px),
      radial-gradient(circle at 15% 75%, rgba(255,225,150,.85) 0 2px, transparent 3px),
      radial-gradient(circle at 88% 70%, rgba(255,190,80,.8) 0 1.5px, transparent 3px),
      radial-gradient(circle at 50% 5%, rgba(255,230,160,.9) 0 2px, transparent 3px),
      radial-gradient(circle at 5% 50%, rgba(255,210,110,.7) 0 1.5px, transparent 3px),
      radial-gradient(circle at 95% 45%, rgba(255,220,130,.8) 0 2px, transparent 3px),
      radial-gradient(circle at 45% 95%, rgba(255,200,100,.75) 0 1.5px, transparent 3px);
    animation: twinkle 3s infinite ease-in-out;
  }
  @keyframes twinkle {
    0%,100% { opacity: .55; transform: scale(1); }
    50%     { opacity: 1;   transform: scale(1.06); }
  }

  .elite-square {
    position: relative;
    width: 128px;
    height: 128px;
    border-radius: 20px;
    border: 2px solid #a07a3c;
    background: linear-gradient(160deg, #1c1508, #0d0904);
    box-shadow: 0 0 25px rgba(200,150,70,.55), inset 0 0 20px rgba(200,150,70,.15);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2;
    cursor: pointer;
    transition: transform .12s ease, box-shadow .25s ease;
    animation: idle 3s infinite ease-in-out;
  }
  @keyframes idle {
    0%,100% { transform: translateY(0) rotate(0deg); }
    50%     { transform: translateY(-4px) rotate(-1deg); }
  }
  .elite-square.pressed { animation: press .45s ease; }
  @keyframes press {
    0%   { transform: scale(1) rotate(0deg); }
    20%  { transform: scale(.88) rotate(-6deg); box-shadow: 0 0 40px rgba(255,215,130,.9); }
    40%  { transform: scale(1.08) rotate(4deg); }
    60%  { transform: scale(.95) rotate(-3deg); }
    80%  { transform: scale(1.03) rotate(2deg); }
    100% { transform: scale(1) rotate(0deg); }
  }

  .elite-square span {
    font-size: 18px;
    font-weight: 800;
    letter-spacing: 2px;
    background: linear-gradient(135deg, #f5dd9b, #b8893f, #f5dd9b);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    text-shadow: 0 0 14px rgba(245,221,155,.4);
    text-align: center;
    line-height: 1.3;
    padding: 0 8px;
    pointer-events: none;
  }

  .float-tag {
    position: absolute;
    font-size: 10px;
    font-weight: 700;
    color: #e0b877;
    border: 1px solid #7a5a2e;
    border-radius: 20px;
    padding: 4px 9px;
    background: rgba(20,15,8,.85);
    box-shadow: 0 0 10px rgba(180,130,60,.4);
    z-index: 3;
    white-space: nowrap;
  }
  .tag-1 { top: -6px;  left: -18px;  animation: float1 4s infinite ease-in-out; }
  .tag-2 { bottom: 6px; right: -22px; animation: float2 4.5s infinite ease-in-out; }

  @keyframes float1 {
    0%,100% { transform: translate(0,0) rotate(-6deg); }
    50%     { transform: translate(-6px,-8px) rotate(-6deg); }
  }
  @keyframes float2 {
    0%,100% { transform: translate(0,0) rotate(5deg); }
    50%     { transform: translate(6px,8px) rotate(5deg); }
  }

  .headline {
    font-size: 17px;
    font-weight: 800;
    letter-spacing: .5px;
    line-height: 1.4;
    background: linear-gradient(90deg, #e8c887, #b8893f, #e8c887);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    margin-top: 6px;
  }

  /* ====== ВТОРАЯ РАМКА ====== */
  .card-title {
    font-size: 15px;
    font-weight: 700;
    color: #b8893f;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 16px;
    text-align: center;
  }

  .feature {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 11px 4px;
    border-bottom: 1px solid rgba(122,90,46,.25);
  }
  .feature:last-child { border-bottom: none; }

  .feature-icon { font-size: 20px; width: 26px; text-align: center; }
  .feature-label { color: #b8893f; font-weight: 600; font-size: 14px; min-width: 92px; }
  .feature-value { color: #f0e6d2; font-size: 14px; }

  /* ====== КНОПКА ПОДПИСКА 👉 ====== */
  .sub-link-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 100%;
    padding: 18px;
    border: none;
    cursor: pointer;
    border-radius: 16px;
    font-size: 18px;
    font-weight: 800;
    letter-spacing: 1.5px;
    color: #0a0805;
    background: linear-gradient(135deg, #f5dd9b, #b8893f, #f5dd9b);
    background-size: 200% 200%;
    box-shadow: 0 8px 28px rgba(184,137,63,.5);
    transition: .25s;
    animation: shine 4s infinite;
    font-family: inherit;
  }
  .sub-link-btn:hover { transform: translateY(-2px); filter: brightness(1.12); }
  .sub-link-btn:active { transform: scale(.97); }

  .sub-link-btn .arrow {
    display: inline-block;
    animation: arrowMove 1.2s infinite ease-in-out;
  }
  @keyframes arrowMove {
    0%,100% { transform: translateX(0); }
    50%     { transform: translateX(6px); }
  }

  /* ====== МОДАЛЬНОЕ ОКНО (успех) ====== */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,.75);
    backdrop-filter: blur(6px);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 100;
    padding: 20px;
  }
  .modal-overlay.active { display: flex; }

  .modal {
    width: 100%;
    max-width: 340px;
    background: linear-gradient(160deg, #1a1408, #0a0805);
    border: 1.5px solid #b8893f;
    border-radius: 22px;
    padding: 30px 22px;
    text-align: center;
    box-shadow: 0 0 45px rgba(184,137,63,.5);
    animation: modalIn .3s ease;
  }
  @keyframes modalIn {
    0%   { transform: scale(.8); opacity: 0; }
    100% { transform: scale(1);  opacity: 1; }
  }

  .modal-icon {
    font-size: 46px;
    margin-bottom: 12px;
    animation: pop .5s ease;
  }
  @keyframes pop {
    0%   { transform: scale(0); }
    70%  { transform: scale(1.2); }
    100% { transform: scale(1); }
  }

  .modal-title {
    font-size: 20px;
    font-weight: 800;
    color: #f5dd9b;
    letter-spacing: 1px;
    margin-bottom: 8px;
    text-shadow: 0 0 14px rgba(245,221,155,.5);
  }

  .modal-text {
    font-size: 13px;
    color: #c9b184;
    margin-bottom: 22px;
    line-height: 1.5;
    word-break: break-all;
  }

  .modal-back-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 100%;
    padding: 14px;
    border: none;
    cursor: pointer;
    border-radius: 14px;
    font-size: 16px;
    font-weight: 800;
    letter-spacing: 1px;
    color: #0a0805;
    background: linear-gradient(135deg, #e8c887, #b8893f, #e8c887);
    background-size: 200% 200%;
    box-shadow: 0 6px 22px rgba(184,137,63,.45);
    transition: .25s;
    animation: shine 4s infinite;
    font-family: inherit;
  }
  .modal-back-btn:hover { transform: translateY(-2px); filter: brightness(1.1); }
  .modal-back-btn:active { transform: scale(.97); }

  /* ====== ТРЕТЬЯ РАМКА ====== */
  .channel-card { text-align: center; }

  .channel-title {
    font-size: 16px;
    font-weight: 700;
    color: #b8893f;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 18px;
  }

  .subscribe-btn {
    display: inline-block;
    width: 100%;
    padding: 16px;
    border-radius: 14px;
    text-decoration: none;
    font-size: 16px;
    font-weight: 700;
    letter-spacing: 1px;
    color: #0a0805;
    background: linear-gradient(135deg, #e8c887, #b8893f, #e8c887);
    background-size: 200% 200%;
    box-shadow: 0 6px 22px rgba(184,137,63,.45);
    transition: .25s;
    animation: shine 4s infinite;
  }
  .subscribe-btn:hover { transform: translateY(-2px); filter: brightness(1.1); }
  .subscribe-btn:active { transform: scale(.98); }

  @keyframes shine {
    0%   { background-position: 0% 50%; }
    50%  { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  .bolt {
    display: inline-block;
    animation: pulse 1.6s infinite;
  }
  @keyframes pulse {
    0%,100% { transform: scale(1); filter: drop-shadow(0 0 4px #e8c887); }
    50%     { transform: scale(1.25); filter: drop-shadow(0 0 12px #ffdb8a); }
  }
</style>
</head>
<body>

<div class="wrap">

  <!-- ===== РАМКА 1: ELITE КВАДРАТ ===== -->
  <div class="card hero">
    <div class="free-badge">✨ FREE</div>

    <div class="avatar-zone">
      <div class="sparkles"></div>
      <div class="thin-ring"></div>
      <div class="float-tag tag-1">до 1 Гбит/с</div>
      <div class="float-tag tag-2">до 1 Гбит/с</div>
      <div class="elite-square" id="eliteSquare">
        <span>ELITE<br>⚡️</span>
      </div>
    </div>

    <div class="headline">САМЫЙ ЛУЧШИЙ ОБХОДИТ ВСЕ БЛОКИРОВКИ 🚀</div>
  </div>

  <!-- ===== РАМКА 2: О СЕРВИСЕ ===== -->
  <div class="card">
    <div class="card-title">О сервисе</div>

    <div class="feature">
      <div class="feature-icon">⚡</div>
      <div class="feature-label">Скорость</div>
      <div class="feature-value">1 Гбит</div>
    </div>

    <div class="feature">
      <div class="feature-icon">🌐</div>
      <div class="feature-label">Серверы</div>
      <div class="feature-value">множество серверов</div>
    </div>

    <div class="feature">
      <div class="feature-icon">📱</div>
      <div class="feature-label">Устройства</div>
      <div class="feature-value">без ограничений</div>
    </div>
  </div>

  <!-- ===== КНОПКА ПОДПИСКА 👉 ===== -->
  <button class="sub-link-btn" id="subBtn">
    ПОДПИСКА <span class="arrow">👉</span>
  </button>

  <!-- ===== РАМКА 3: О КАНАЛЕ ===== -->
  <div class="card channel-card">
    <div class="channel-title">О Канале <span class="bolt">⚡️</span></div>
    <a class="subscribe-btn" href="https://t.me/FREEVPN444" target="_blank" rel="noopener">
      ПОДПИСАТЬСЯ НА КАНАЛ
    </a>
  </div>

</div>

<!-- ===== МОДАЛЬНОЕ ОКНО УСПЕХА ===== -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
    <div class="modal-icon">✅</div>
    <div class="modal-title">Скопировано успешно!</div>
    <div class="modal-text" id="copiedLink"></div>
    <button class="modal-back-btn" id="backBtn">Назад 🔙</button>
  </div>
</div>

<script>
  /* ====== Анимация рамки ELITE ⚡️ ====== */
  const eliteSquare = document.getElementById('eliteSquare');
  eliteSquare.addEventListener('click', () => {
    eliteSquare.classList.remove('pressed');
    void eliteSquare.offsetWidth;
    eliteSquare.classList.add('pressed');
    setTimeout(() => eliteSquare.classList.remove('pressed'), 500);
  });

  /* ====== Логика ПОДПИСКА 👉 ====== */
  const SUB_URL = 'https://plainraw.com/raw/11f3b65ff172';

  const subBtn       = document.getElementById('subBtn');
  const modalOverlay = document.getElementById('modalOverlay');
  const copiedLink   = document.getElementById('copiedLink');
  const backBtn      = document.getElementById('backBtn');

  subBtn.addEventListener('click', async () => {
    // копируем ссылку в буфер обмена
    try {
      if (navigator.clipboard && window.isSecureContext) {
        await navigator.clipboard.writeText(SUB_URL);
      } else {
        // фолбэк для старых браузеров / http
        const ta = document.createElement('textarea');
        ta.value = SUB_URL;
        ta.style.position = 'fixed';
        ta.style.opacity = '0';
        document.body.appendChild(ta);
        ta.select();
        document.execCommand('copy');
        document.body.removeChild(ta);
      }
      showSuccess();
    } catch (e) {
      showSuccess(); // всё равно показываем окно
    }
  });

  function showSuccess() {
    copiedLink.textContent = SUB_URL;
    modalOverlay.classList.add('active');
  }

  // Назад 🔙 — закрыть модалку
  backBtn.addEventListener('click', () => {
    modalOverlay.classList.remove('active');
  });

  // Клик по фону — тоже закрыть
  modalOverlay.addEventListener('click', (e) => {
    if (e.target === modalOverlay) modalOverlay.classList.remove('active');
  });
</script>

</body>
</html>
