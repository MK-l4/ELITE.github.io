<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite — обходит все глушилки</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background-color: #3b2a1c;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
            padding: 20px;
            background-image: radial-gradient(circle at 20% 30%, #5a3f2b 0%, #2e1f14 90%);
        }

        .container {
            text-align: center;
            max-width: 800px;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 30px;
            padding: 30px 20px;
            border-radius: 60px 60px 40px 40px;
            background: rgba(0, 0, 0, 0.15);
            backdrop-filter: blur(2px);
            box-shadow: 0 20px 30px rgba(0,0,0,0.6), inset 0 1px 4px rgba(255, 215, 0, 0.2);
            border: 1px solid rgba(255, 215, 0, 0.25);
        }

        .elite-header {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-bottom: 10px;
        }

        .avatar {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            background: linear-gradient(135deg, #f5d742, #b8860b, #ffd966);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 0 3px #3b2a1c, 0 0 0 6px #d4af37, 0 8px 20px rgba(0,0,0,0.6);
            transition: transform 0.2s ease;
        }

        .avatar:hover {
            transform: scale(1.02);
        }

        .avatar span {
            font-size: 3rem;
            font-weight: 900;
            color: #3b2a1c;
            text-shadow: 0 2px 2px #ffd966;
            letter-spacing: 2px;
        }

        .elite-text {
            font-size: 5.5rem;
            font-weight: 900;
            letter-spacing: 6px;
            text-transform: uppercase;
            color: #ffd966;
            text-shadow: 
                0 0 8px #ffb347,
                0 0 20px #d4af37,
                2px 4px 10px #000000,
                0 0 40px #b8860b;
            font-family: 'Impact', 'Arial Black', sans-serif;
            line-height: 1;
        }

        .bypass-area {
            margin-top: 20px;
            width: 100%;
            display: flex;
            justify-content: center;
        }

        .bypass-text {
            font-size: 1.7rem;
            font-weight: 600;
            color: #e6c68a;
            text-shadow: 0 2px 8px #1a0f07, 0 0 20px #7a5a2e;
            cursor: pointer;
            padding: 10px 28px;
            border-radius: 50px;
            background: rgba(70, 45, 25, 0.7);
            border: 1px solid #b98f4b;
            transition: all 0.25s ease;
            box-shadow: 0 5px 0 #1e130b;
            user-select: none;
            letter-spacing: 1px;
            backdrop-filter: blur(4px);
        }

        .bypass-text:hover {
            background: rgba(110, 75, 40, 0.9);
            color: #fff0c0;
            border-color: #ffd966;
            box-shadow: 0 5px 0 #1e130b, 0 0 20px #d4af37;
            transform: translateY(-1px);
        }

        .bypass-text:active {
            transform: translateY(4px);
            box-shadow: 0 1px 0 #1e130b;
        }

        .bypass-message {
            margin-top: 18px;
            font-size: 1.5rem;
            font-weight: 700;
            color: #ffecb3;
            background: #2b1b0f;
            padding: 14px 28px;
            border-radius: 40px;
            border-left: 8px solid #d4af37;
            border-right: 8px solid #d4af37;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.4), inset 0 0 15px #3f2b12;
            opacity: 0;
            transform: scale(0.95);
            transition: opacity 0.3s ease, transform 0.3s ease;
            pointer-events: none;
            max-width: 90%;
            line-height: 1.4;
            letter-spacing: 1px;
            text-shadow: 0 2px 5px black;
        }

        .bypass-message.show {
            opacity: 1;
            transform: scale(1);
            pointer-events: auto;
        }

        .btn-subscribe {
            background: linear-gradient(145deg, #f5d742, #b8860b);
            border: none;
            color: #1e140e;
            font-weight: 900;
            font-size: 1.8rem;
            text-transform: uppercase;
            padding: 18px 42px;
            border-radius: 60px;
            letter-spacing: 3px;
            cursor: pointer;
            box-shadow: 0 12px 0 #4d2e0e, 0 10px 25px black;
            transition: all 0.1s ease;
            font-family: 'Segoe UI', 'Arial Black', sans-serif;
            margin-top: 20px;
            border: 1px solid #fff3c9;
            text-shadow: 0 1px 2px rgba(255,255,200,0.8);
        }

        .btn-subscribe:hover {
            background: linear-gradient(145deg, #ffe07a, #c99c2b);
            box-shadow: 0 12px 0 #4d2e0e, 0 0 30px #ffd966;
            transform: scale(1.01);
        }

        .btn-subscribe:active {
            transform: translateY(8px);
            box-shadow: 0 4px 0 #4d2e0e, 0 10px 20px black;
        }

        /* Модальное окно */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(8px);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            padding: 20px;
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal-card {
            background: linear-gradient(145deg, #4d3624, #2e1f14);
            border-radius: 60px;
            padding: 40px 30px;
            max-width: 700px;
            width: 100%;
            box-shadow: 0 0 0 2px #d4af37, 0 30px 50px black;
            border: 1px solid #ffd966;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 25px;
            position: relative;
        }

        .modal-title {
            color: #ffd966;
            font-size: 2rem;
            font-weight: 800;
            text-shadow: 0 4px 8px black;
            letter-spacing: 2px;
            text-align: center;
        }

        .link-box {
            background: #1f140c;
            padding: 18px 22px;
            border-radius: 50px;
            width: 100%;
            font-size: 1.25rem;
            color: #e6c68a;
            word-break: break-all;
            border: 2px solid #b8860b;
            box-shadow: inset 0 0 20px #000000;
            font-family: monospace;
            text-align: center;
            letter-spacing: 0.5px;
        }

        .btn-copy {
            background: #d4af37;
            border: none;
            color: #1e140e;
            font-weight: 800;
            font-size: 1.6rem;
            padding: 18px 40px;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 0 #6b4f1a, 0 8px 15px black;
            transition: all 0.1s ease;
            letter-spacing: 2px;
            text-transform: uppercase;
            width: 100%;
            max-width: 420px;
        }

        .btn-copy:active {
            transform: translateY(5px);
            box-shadow: 0 3px 0 #6b4f1a, 0 8px 15px black;
        }

        .btn-copy:hover {
            background: #e6c35c;
        }

        .btn-close {
            background: #6e4f2e;
            border: none;
            color: #f0e0b0;
            font-weight: 700;
            font-size: 1.2rem;
            padding: 12px 32px;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 6px 0 #2e1f14, 0 8px 15px black;
            transition: all 0.1s ease;
            letter-spacing: 1px;
        }

        .btn-close:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 #2e1f14, 0 8px 15px black;
        }

        .btn-close:hover {
            background: #8b653c;
        }

        .success-message {
            font-size: 2rem;
            font-weight: 800;
            color: #b9ff9b;
            text-shadow: 0 0 15px #2ecc71, 0 0 30px #1e6b2e, 0 4px 8px black;
            letter-spacing: 2px;
            opacity: 0;
            transition: opacity 0.4s ease;
            background: #1e3a1e;
            padding: 12px 38px;
            border-radius: 50px;
            border: 2px solid #7ed957;
            box-shadow: 0 0 30px #2ecc71;
            pointer-events: none;
        }

        .success-message.show {
            opacity: 1;
        }

        @media (max-width: 600px) {
            .elite-text {
                font-size: 3.8rem;
                letter-spacing: 4px;
            }
            .avatar {
                width: 70px;
                height: 70px;
            }
            .avatar span {
                font-size: 2.4rem;
            }
            .bypass-text {
                font-size: 1.3rem;
                padding: 8px 18px;
            }
            .btn-subscribe {
                font-size: 1.4rem;
                padding: 14px 24px;
                letter-spacing: 2px;
            }
            .modal-title {
                font-size: 1.5rem;
            }
            .btn-copy {
                font-size: 1.2rem;
                padding: 14px 20px;
            }
            .link-box {
                font-size: 1rem;
                padding: 14px 16px;
            }
            .success-message {
                font-size: 1.5rem;
                padding: 10px 24px;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="elite-header">
        <div class="avatar">
            <span>⚡</span>
        </div>
        <div class="elite-text">Elite</div>
    </div>

    <div class="bypass-area">
        <div class="bypass-text" id="bypassTrigger">обходит все глушилки</div>
    </div>

    <div class="bypass-message" id="bypassMessage">
        Не суда, А на получить подписку.
    </div>

    <button class="btn-subscribe" id="subscribeBtn">Получить подписку</button>
</div>

<!-- Модальное окно -->
<div class="modal-overlay" id="modalOverlay">
    <div class="modal-card">
        <div class="modal-title">🔗 ВАША ПОДПИСКА</div>
        <div class="link-box" id="linkText">https://plainraw.com/raw/11f3b65ff172</div>
        <button class="btn-copy" id="copyBtn">📋 Скопировать подписку</button>
        <div class="success-message" id="successMsg">Успешно ✅</div>
        <button class="btn-close" id="closeBtn">Закрыть</button>
    </div>
</div>

<script>
    (function() {
        const bypassTrigger = document.getElementById('bypassTrigger');
        const bypassMessage = document.getElementById('bypassMessage');
        const subscribeBtn = document.getElementById('subscribeBtn');
        const modalOverlay = document.getElementById('modalOverlay');
        const copyBtn = document.getElementById('copyBtn');
        const closeBtn = document.getElementById('closeBtn');
        const successMsg = document.getElementById('successMsg');

        const SUBSCRIPTION_URL = 'https://plainraw.com/raw/11f3b65ff172';

        // Клик по "обходит все глушилки" — toggle сообщения
        bypassTrigger.addEventListener('click', function() {
            bypassMessage.classList.toggle('show');
        });

        // Открытие модального окна по кнопке "Получить подписку"
        subscribeBtn.addEventListener('click', function() {
            modalOverlay.classList.add('active');
            successMsg.classList.remove('show');
        });

        // Закрытие модалки
        function closeModal() {
            modalOverlay.classList.remove('active');
            successMsg.classList.remove('show');
        }

        closeBtn.addEventListener('click', closeModal);

        modalOverlay.addEventListener('click', function(e) {
            if (e.target === modalOverlay) {
                closeModal();
            }
        });

        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape' && modalOverlay.classList.contains('active')) {
                closeModal();
            }
        });

        // Копирование ссылки
        copyBtn.addEventListener('click', function() {
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(SUBSCRIPTION_URL)
                    .then(showSuccess)
                    .catch(() => fallbackCopy(SUBSCRIPTION_URL));
            } else {
                fallbackCopy(SUBSCRIPTION_URL);
            }
        });

        function fallbackCopy(text) {
            const textarea = document.createElement('textarea');
            textarea.value = text;
            textarea.style.position = 'fixed';
            textarea.style.opacity = '0';
            document.body.appendChild(textarea);
            textarea.select();
            try {
                document.execCommand('copy');
                showSuccess();
            } catch (err) {
                alert('Не удалось скопировать. Скопируйте вручную.');
            }
            document.body.removeChild(textarea);
        }

        function showSuccess() {
            successMsg.classList.add('show');
            setTimeout(() => {
                successMsg.classList.remove('show');
            }, 2500);
        }

        // Инициализация
        bypassMessage.classList.remove('show');
    })();
</script>

<style>
    .bypass-text, .btn-subscribe, .btn-copy, .btn-close {
        user-select: none;
    }
</style>
</body>
</html>
