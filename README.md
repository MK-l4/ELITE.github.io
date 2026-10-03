<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Elite VPN</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    min-height: 100vh;
    background: radial-gradient(circle at 50% 0%, #1a1a1a 0%, #000 70%);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 30px 20px;
    overflow: hidden;
    position: relative;
  }

  /* Кружок с логотипом */
  .logo-circle {
    width: 160px;
    height: 160px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 30%, #2a2a2a, #000);
    border: 3px solid #d4af37;
    box-shadow:
      0 0 25px rgba(212, 175, 55, 0.6),
      0 0 60px rgba(212, 175, 55, 0.3),
      inset 0 0 30px rgba(212, 175, 55, 0.15);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 25px;
    animation: pulse 3s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 25px rgba(212,175,55,0.6), 0 0 60px rgba(212,175,55,0.3); }
    50%      { box-shadow: 0 0 40px rgba(212,175,55,0.9), 0 0 90px rgba(212,175,55,0.5); }
  }

  .logo-circle span {
    font-size: 22px;
    font-weight: 800;
    letter-spacing: 1px;
    background: linear-gradient(135deg, #f5d76e, #d4af37, #b8860b);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    text-align: center;
    line-height: 1.2;
  }

  /* Заголовок */
  h1 {
    font-size: 32px;
    font-weight: 800;
    background: linear-gradient(135deg, #f5d76e, #d4af37, #b8860b);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
    text-align: center;
  }

  .subtitle {
    color: #888;
    font-size: 14px;
    margin-bottom: 30px;
    text-align: center;
  }

  /* Летающие надписи */
  .fly-zone {
    position: fixed;
    inset: 0;
    pointer-events: none;
    overflow: hidden;
    z-index: 0;
  }

  .fly-text {
    position: absolute;
    color: #d4af37;
    font-weight: 700;
    font-size: 18px;
    text-shadow: 0 0 10px rgba(212,175,55,0.8), 0 0 20px rgba(212,175,55,0.4);
    white-space: nowrap;
    animation: flyAcross linear infinite;
    opacity: 0.85;
  }

  @keyframes flyAcross {
    0%   { transform: translateX(-30vw) translateY(0); opacity: 0; }
    10%  { opacity: 0.9; }
    90%  { opacity: 0.9; }
    100% { transform: translateX(130vw) translateY(-30px); opacity: 0; }
  }

  /* Кнопка */
  .btn {
    position: relative;
    z-index: 2;
    padding: 18px 50px;
    font-size: 18px;
    font-weight: 800;
    letter-spacing: 1px;
    color: #000;
    background: linear-gradient(135deg, #f5d76e, #d4af37, #b8860b);
    border: none;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 8px 30px rgba(212,175,55,0.5);
    transition: transform 0.2s, box-shadow 0.2s;
    text-transform: uppercase;
  }

  .btn:active {
    transform: scale(0.96);
    box-shadow: 0 4px 15px rgba(212,175,55,0.7);
  }

  /* Модальное окно */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(8px);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 100;
    padding: 20px;
  }

  .modal-overlay.active { display: flex; }

  .modal {
    background: linear-gradient(160deg, #1a1a1a, #0a0a0a);
    border: 2px solid #d4af37;
    border-radius: 24px;
    padding: 30px 25px;
    max-width: 400px;
    width: 100%;
    text-align: center;
    box-shadow: 0 0 60px rgba(212,175,55,0.4);
    animation: popIn 0.3s ease;
  }

  @keyframes popIn {
    from { transform: scale(0.85); opacity: 0; }
    to   { transform: scale(1); opacity: 1; }
  }

  .modal h2 {
    color: #d4af37;
    font-size: 22px;
    margin-bottom: 20px;
  }

  .link-box {
    background: #000;
    border: 1px solid #333;
    border-radius: 12px;
    padding: 14px;
    font-size: 13px;
    color: #d4af37;
    word-break: break-all;
    margin-bottom: 15px;
    font-family: monospace;
  }

  .copy-btn {
    width: 100%;
    padding: 16px;
    font-size: 16px;
    font-weight: 700;
    color: #000;
    background: linear-gradient(135deg, #f5d76e, #d4af37);
    border: none;
    border-radius: 14px;
    cursor: pointer;
    transition: transform 0.15s;
    text-transform: uppercase;
  }

  .copy-btn:active { transform: scale(0.96); }

  .copy-btn.copied {
    background: linear-gradient(135deg, #4ade80, #22c55e);
  }

  .close-btn {
    margin-top: 12px;
    background: none;
    border: none;
    color: #666;
    font-size: 14px;
    cursor: pointer;
  }
</style>
</head>
<body>

  <!-- Летающие надписи -->
  <div class="fly-zone" id="flyZone"></div>

  <!-- Логотип -->
  <div class="logo-circle"><span>ELITE<br>VPN</span></div>

  <h1>Elite VPN</h1>
  <p class="subtitle">Быстро. Безопасно. Анонимно.</p>

  <button class="btn" onclick="openModal()">Получить подписку</button>

  <!-- Модальное окно -->
  <div class="modal-overlay" id="modal">
    <div class="modal">
      <h2>🎉 Ваша подписка</h2>
      <div class="link-box" id="linkText">https://plainraw.com/raw/11f3b65ff172</div>
      <button class="copy-btn" id="copyBtn" onclick="copyLink()">📋 Скопировать ссылку</button>
      <button class="close-btn" onclick="closeModal()">Закрыть</button>
    </div>
  </div>

<script>
  /* ===== Летающие надписи ===== */
  const flyZone = document.getElementById('flyZone');

  const texts = [
    '10 mbit/s',
    'Много серверов',
    '10 mbit/s',
    'Без логов',
    'Много серверов',
    '10 mbit/s',
    'Стабильно',
    'Много серверов'
  ];

  function createFlyText() {
    const el = document.createElement('div');
    el.className = 'fly-text';
    el.textContent = texts[Math.floor(Math.random() * texts.length)];
    el.style.top = (Math.random() * 90 + 5) + 'vh';
    el.style.fontSize = (14 + Math.random() * 10) + 'px';
    const duration = 8 + Math.random() * 8;
    el.style.animationDuration = duration + 's';
    el.style.animationDelay = (Math.random() * 2) + 's';
    flyZone.appendChild(el);

    setTimeout(() => el.remove(), (duration + 2) * 1000);
  }

  // Запускаем постоянно
  setInterval(createFlyText, 900);
  // Стартовая пачка
  for (let i = 0; i < 6; i++) setTimeout(createFlyText, i * 300);

  /* ===== Модальное окно ===== */
  const SUB_URL = 'https://plainraw.com/raw/11f3b65ff172';

  function openModal() {
    document.getElementById('modal').classList.add('active');
  }

  function closeModal() {
    document.getElementById('modal').classList.remove('active');
    const btn = document.getElementById('copyBtn');
    btn.textContent = '📋 Скопировать ссылку';
    btn.classList.remove('copied');
  }

  function copyLink() {
    const btn = document.getElementById('copyBtn');

    const done = () => {
      btn.textContent = '✅ Скопировано!';
      btn.classList.add('copied');
      setTimeout(() => {
        btn.textContent = '📋 Скопировать ссылку';
        btn.classList.remove('copied');
      }, 2000);
    };

    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(SUB_URL).then(done).catch(fallbackCopy);
    } else {
      fallbackCopy();
    }

    function fallbackCopy() {
      const ta = document.createElement('textarea');
      ta.value = SUB_URL;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); done(); } catch(e) { alert('Скопируйте вручную:\n' + SUB_URL); }
      document.body.removeChild(ta);
    }
  }

  // Закрытие по клику вне окна
  document.getElementById('modal').addEventListener('click', (e) => {
    if (e.target.id === 'modal') closeModal();
  });
</script>
</body>
</html>
