<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Programist-studio — Конструктор Сайтов</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        html, body {
            width: 100%;
            min-height: 100vh;
            background-color: #0b0f19;
            color: #f8fafc;
            overflow-x: hidden;
            overflow-y: auto;
        }

        /* Кастомный скроллбар */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0b0f19;
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #38bdf8;
        }

        /* АНИМАЦИИ НАЗВАНИЯ И МОЛНИИ */
        @keyframes textGradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes titlePulse {
            0% { transform: scale(1); filter: drop-shadow(0 0 5px rgba(56, 189, 248, 0.4)); }
            50% { transform: scale(1.03); filter: drop-shadow(0 0 15px rgba(168, 85, 247, 0.8)); }
            100% { transform: scale(1); filter: drop-shadow(0 0 5px rgba(56, 189, 248, 0.4)); }
        }

        .animated-site-title {
            background: linear-gradient(90deg, #38bdf8, #818cf8, #c084fc, #38bdf8);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: textGradient 3s linear infinite, titlePulse 2.5s ease-in-out infinite;
            display: inline-block;
            font-weight: 800;
        }

        @keyframes lightningStrike {
            0% { transform: translateY(-25px) scaleY(0.2); opacity: 0; filter: drop-shadow(0 0 0px transparent); }
            10% { transform: translateY(2px) scaleY(1.1); opacity: 1; filter: drop-shadow(0 0 15px #ffffff) drop-shadow(0 0 25px #38bdf8); }
            15% { transform: translateY(-1px) scaleY(0.95); opacity: 0.4; }
            20% { transform: translateY(1px) scaleY(1.05); opacity: 1; filter: drop-shadow(0 0 20px #ffffff) drop-shadow(0 0 35px #c084fc); }
            25% { transform: translateY(0) scaleY(1); opacity: 0.8; }
            30% { opacity: 1; filter: drop-shadow(0 0 10px #ffffff) drop-shadow(0 0 18px #38bdf8); }
            70% { transform: translateY(0) scaleY(1); opacity: 1; filter: drop-shadow(0 0 6px #ffffff) drop-shadow(0 0 10px #38bdf8); }
            100% { transform: translateY(-25px) scaleY(0.2); opacity: 0; filter: drop-shadow(0 0 0px transparent); }
        }

        .brand-icon {
            position: relative;
            width: 42px;
            height: 42px;
            background: linear-gradient(135deg, #0284c7, #6366f1, #9333ea);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.5);
            animation: pulseGlow 2.5s infinite alternate;
            overflow: hidden;
            flex-shrink: 0;
        }

        @keyframes pulseGlow {
            0% { box-shadow: 0 0 15px rgba(56, 189, 248, 0.4), 0 0 30px rgba(99, 102, 241, 0.2); }
            100% { box-shadow: 0 0 25px rgba(56, 189, 248, 0.8), 0 0 45px rgba(168, 85, 247, 0.5); }
        }

        .brand-icon svg {
            position: relative;
            width: 26px;
            height: 26px;
            z-index: 2;
            fill: none;
            stroke: #ffffff;
            stroke-width: 2.2;
            stroke-linecap: round;
            stroke-linejoin: round;
            animation: lightningStrike 2.2s cubic-bezier(0.22, 1, 0.36, 1) infinite;
            transform-origin: bottom center;
        }

        /* ПОЯВЛЕНИЕ ЭЛЕМЕНТОВ И HOVER ЭФФЕКТЫ */
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideInLeft { from { opacity: 0; transform: translateX(-30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }

        .anim-fade { animation: fadeIn 0.8s ease forwards; }
        .anim-slide-up { animation: slideUp 0.8s ease forwards; }
        .anim-slide-left { animation: slideInLeft 0.8s ease forwards; }
        .anim-zoom { animation: zoomIn 0.6s ease forwards; }

        .hover-zoom { transition: transform 0.3s ease; }
        .hover-zoom:hover { transform: scale(1.04); }
        .hover-glow { transition: box-shadow 0.3s ease, transform 0.3s ease; }
        .hover-glow:hover { box-shadow: 0 0 20px rgba(56, 189, 248, 0.6); transform: translateY(-3px); }

        /* Верхняя панель (Header) */
        .top-bar {
            height: 65px;
            background: rgba(30, 41, 59, 0.85);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
            position: sticky;
            top: 0;
            z-index: 100;
            gap: 15px;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 14px;
            font-size: 20px;
            font-weight: 800;
        }

        .tg-banner-link {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 6px 14px;
            background: linear-gradient(135deg, #0088cc, #229ed9);
            color: #ffffff;
            text-decoration: none;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 700;
            box-shadow: 0 0 12px rgba(34, 158, 217, 0.4);
            transition: all 0.3s ease;
        }

        .tg-banner-link:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 20px rgba(34, 158, 217, 0.8);
        }

        .view-toggle, .device-toggle, .history-toggle {
            display: flex;
            background-color: #0f172a;
            padding: 4px;
            border-radius: 10px;
            gap: 4px;
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .toggle-btn {
            padding: 6px 14px;
            border: none;
            background: transparent;
            color: #94a3b8;
            border-radius: 7px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: all 0.3s ease;
        }

        .toggle-btn:disabled {
            opacity: 0.3;
            cursor: not-allowed;
        }

        .toggle-btn.active {
            background: linear-gradient(135deg, #38bdf8, #3b82f6);
            color: #0f172a;
            box-shadow: 0 0 12px rgba(56, 189, 248, 0.4);
        }

        .top-actions {
            display: flex;
            gap: 10px;
        }

        /* Главный контейнер */
        .main-container {
            display: flex;
            min-height: calc(100vh - 65px);
            position: relative;
        }

        /* Боковые панели */
        .sidebar {
            width: 300px;
            background-color: #111827;
            border-right: 1px solid rgba(255, 255, 255, 0.08);
            display: flex;
            flex-direction: column;
            padding: 20px;
            gap: 10px;
            max-height: calc(100vh - 65px);
            position: sticky;
            top: 65px;
            overflow-y: auto;
            flex-shrink: 0;
        }

        .sidebar-right {
            border-right: none;
            border-left: 1px solid rgba(255, 255, 255, 0.08);
        }

        .sidebar h2 {
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 1.2px;
            color: #38bdf8;
            margin-top: 10px;
            margin-bottom: 3px;
            font-weight: 700;
        }

        .sidebar h2:first-child { margin-top: 0; }

        .btn-element {
            padding: 9px 12px;
            background: #1e293b;
            border: 1px solid #334155;
            color: #f8fafc;
            border-radius: 8px;
            cursor: pointer;
            text-align: left;
            font-weight: 500;
            font-size: 13px;
            transition: all 0.25s ease;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .btn-element:hover {
            background: linear-gradient(135deg, rgba(56, 189, 248, 0.15), rgba(99, 102, 241, 0.15));
            border-color: #38bdf8;
            color: #38bdf8;
            transform: translateX(3px);
        }

        .btn-preset {
            background: linear-gradient(135deg, rgba(168, 85, 247, 0.2), rgba(99, 102, 241, 0.2));
            border-color: #a855f7;
            color: #c084fc;
        }

        .btn-preset:hover {
            background: linear-gradient(135deg, #a855f7, #6366f1);
            color: #ffffff;
        }

        .btn-danger {
            background: rgba(239, 68, 68, 0.1);
            color: #f87171;
            border: 1px solid rgba(239, 68, 68, 0.3);
            margin-top: 10px;
        }

        .btn-danger:hover {
            background: #ef4444;
            color: #ffffff;
            transform: none;
        }

        /* РАБОЧАЯ ОБЛАСТЬ */
        .workspace {
            flex: 1;
            padding: 25px;
            display: flex;
            flex-direction: column;
            align-items: center;
            background: radial-gradient(circle at center, #1e293b 0%, #0b0f19 100%);
            min-height: calc(100vh - 65px);
            overflow-y: visible;
            transition: all 0.3s ease;
        }

        .canvas {
            width: 100%;
            max-width: 1200px;
            min-height: 600px;
            background-color: #ffffff;
            color: #1e293b;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
            transition: all 0.3s ease;
            margin-bottom: 100px;
            position: relative;
        }

        /* Тема оформления холста */
        .canvas.dark-theme {
            background-color: #0f172a;
            color: #f8fafc;
        }

        .canvas.tablet-mode { max-width: 768px; }
        .canvas.mobile-mode { max-width: 375px; padding: 15px; }

        .code-editor-container {
            width: 100%;
            max-width: 1200px;
            display: none;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 100px;
        }

        .code-editor {
            width: 100%;
            min-height: 550px;
            background-color: #0f172a;
            color: #38bdf8;
            border: 1px solid #334155;
            border-radius: 10px;
            padding: 18px;
            font-family: 'Fira Code', 'Courier New', Courier, monospace;
            font-size: 14px;
            line-height: 1.5;
            resize: vertical;
            outline: none;
        }

        .canvas-item {
            position: relative;
            margin-bottom: 15px;
            padding: 6px;
            border: 1px dashed transparent;
            border-radius: 6px;
            cursor: pointer;
            transition: border-color 0.2s;
        }

        .canvas-item:hover { border-color: #38bdf8; }
        .canvas-item.selected {
            border-color: #818cf8;
            outline: 2px solid #818cf8;
            box-shadow: 0 0 10px rgba(129, 140, 248, 0.3);
        }

        .canvas-item .delete-btn {
            position: absolute;
            top: -10px;
            right: -10px;
            background: linear-gradient(135deg, #f43f5e, #e11d48);
            color: white;
            border: none;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            font-size: 12px;
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
            z-index: 10;
        }

        .canvas-item:hover .delete-btn { display: flex; }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 6px;
            margin-bottom: 12px;
        }

        .control-group label { font-size: 12px; color: #94a3b8; }
        .control-group input, .control-group select {
            padding: 9px 12px;
            background-color: #0f172a;
            border: 1px solid #334155;
            color: #f8fafc;
            border-radius: 6px;
            font-size: 13px;
            outline: none;
        }

        .control-group input[type="color"] { height: 38px; cursor: pointer; padding: 4px; }

        .action-btn {
            padding: 8px 18px;
            background: linear-gradient(135deg, #0284c7, #38bdf8);
            color: #0f172a;
            border: none;
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 0 15px rgba(56, 189, 248, 0.3);
            font-size: 13px;
        }

        .action-btn:hover { transform: translateY(-1px); box-shadow: 0 0 22px rgba(56, 189, 248, 0.6); }

        .btn-preview {
            background: linear-gradient(135deg, #a855f7, #c084fc);
            color: #ffffff;
        }

        /* РЕЖИМ ПРЕДПРОСМОТРА PREVIEW */
        body.preview-mode .top-bar, body.preview-mode .sidebar { display: none !important; }
        body.preview-mode .main-container { min-height: 100vh; }
        body.preview-mode .workspace { padding: 0; background: #ffffff; }
        body.preview-mode .canvas {
            max-width: 100% !important;
            border-radius: 0;
            box-shadow: none;
            margin-bottom: 0;
            padding: 40px;
        }
        body.preview-mode .canvas-item { border: none !important; outline: none !important; }
        body.preview-mode .delete-btn { display: none !important; }

        #exit-preview-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 9999;
            display: none;
            background: #ef4444;
            color: white;
            padding: 12px 24px;
            border: none;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(0,0,0,0.4);
        }

        body.preview-mode #exit-preview-btn { display: block; }
    </style>
</head>
<body>

    <!-- Шапка конструктора -->
    <div class="top-bar">
        <div class="brand">
            <div class="brand-icon">
                <svg viewBox="0 0 24 24">
                    <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"></path>
                </svg>
            </div>
            <span class="animated-site-title">Programist-studio</span>
        </div>

        <!-- Ссылка на Telegram-канал -->
        <a href="https://t.me/programisstuz" target="_blank" class="tg-banner-link">
            🚀 Telegram Канал
        </a>

        <!-- Undo / Redo -->
        <div class="history-toggle">
            <button class="toggle-btn" id="btn-undo" onclick="undo()" title="Отменить (Ctrl+Z)" disabled>↩️ Назад</button>
            <button class="toggle-btn" id="btn-redo" onclick="redo()" title="Повторить (Ctrl+Y)" disabled>↪️ Вперед</button>
        </div>

        <!-- Адаптивные режимы -->
        <div class="device-toggle">
            <button class="toggle-btn active" id="btn-device-desktop" onclick="setDeviceMode('desktop')">🖥️ Desktop</button>
            <button class="toggle-btn" id="btn-device-tablet" onclick="setDeviceMode('tablet')">📱 Tablet</button>
            <button class="toggle-btn" id="btn-device-mobile" onclick="setDeviceMode('mobile')">📱 Mobile</button>
        </div>

        <div class="view-toggle">
            <button class="toggle-btn active" id="btn-view-visual" onclick="switchView('visual')">Визуальный редактор</button>
            <button class="toggle-btn" id="btn-view-code" onclick="switchView('code')">Код (HTML)</button>
        </div>

        <div class="top-actions">
            <button class="action-btn btn-preview" onclick="togglePreviewMode()">👁️ Предпросмотр</button>
            <button class="action-btn" onclick="exportHTML()">Скачать HTML</button>
        </div>
    </div>

    <!-- Основное пространство -->
    <div class="main-container">
        
        <!-- Левая панель -->
        <div class="sidebar">
            <h2>Готовые Шаблоны</h2>
            <button class="btn-element btn-preset" onclick="loadPreset('landing')">🚀 Лендинг услуг <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('portfolio')">🎨 Портфолио <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('shop')">🛒 Интернет-магазин <span>★</span></button>

            <h2>Анимированные блоки</h2>
            <button class="btn-element" onclick="addElement('site-title')">Анимированное Название <span>+</span></button>
            <button class="btn-element" onclick="addElement('countdown')">Счетчик обратного отсчета <span>+</span></button>

            <h2>Базовые блоки</h2>
            <button class="btn-element" onclick="addElement('navbar')">Шапка (Nav) <span>+</span></button>
            <button class="btn-element" onclick="addElement('header')">Заголовок <span>+</span></button>
            <button class="btn-element" onclick="addElement('text')">Текст <span>+</span></button>
            <button class="btn-element" onclick="addElement('button')">Кнопка «Узнать больше» <span>+</span></button>
            <button class="btn-element" onclick="addElement('image')">Изображение <span>+</span></button>
            <button class="btn-element" onclick="addElement('divider')">Разделитель <span>+</span></button>
            <button class="btn-element" onclick="addElement('footer')">Подвал (Footer) <span>+</span></button>

            <h2>Сложные блоки</h2>
            <button class="btn-element" onclick="addElement('pricing')">Таблица цен (3 тарифa) <span>+</span></button>
            <button class="btn-element" onclick="addElement('testimonials')">Блок отзывов <span>+</span></button>
            <button class="btn-element" onclick="addElement('floating-messengers')">Мессенджеры (Плавающие) <span>+</span></button>
            <button class="btn-element" onclick="addElement('card')">Карточка <span>+</span></button>
            <button class="btn-element" onclick="addElement('grid3')">Сетка (3 карточки) <span>+</span></button>
            <button class="btn-element" onclick="addElement('gallery2')">Галерея (2 фото) <span>+</span></button>
            <button class="btn-element" onclick="addElement('form')">Форма заявки <span>+</span></button>
            <button class="btn-element" onclick="addElement('faq')">Блок FAQ <span>+</span></button>

            <h2>Настройки страницы</h2>
            <div class="control-group">
                <label>Тема оформления:</label>
                <select id="page-theme" onchange="changeCanvasTheme(this.value)">
                    <option value="light">Светлая тема</option>
                    <option value="dark">Тёмная тема</option>
                </select>
            </div>
            <div class="control-group">
                <label>Фон холста:</label>
                <input type="color" id="page-bg-color" value="#ffffff" onchange="changeCanvasBg(this.value)">
            </div>
            <div class="control-group">
                <label>Отступы холста (px):</label>
                <input type="number" id="page-padding" value="25" min="0" max="100" onchange="changeCanvasPadding(this.value)">
            </div>
            <div class="control-group">
                <label>Шрифт страницы:</label>
                <select id="page-font" onchange="changeCanvasFont(this.value)">
                    <option value="'Segoe UI', sans-serif">Segoe UI</option>
                    <option value="Arial, sans-serif">Arial</option>
                    <option value="'Times New Roman', serif">Times New Roman</option>
                    <option value="'Courier New', monospace">Courier New</option>
                </select>
            </div>
            <button class="btn-element btn-danger" onclick="clearCanvas()">Очистить холст 🗑</button>
        </div>

        <!-- Центральная панель -->
        <div class="workspace">
            <div class="canvas" id="canvas">
                <p id="empty-msg" style="color: #64748b; text-align: center; margin-top: 250px;">
                    Выберите блоки или готовый шаблон на левой панели
                </p>
            </div>

            <div class="code-editor-container" id="code-container">
                <label style="color: #94a3b8; font-size: 13px;">Прямое редактирование HTML-кода:</label>
                <textarea class="code-editor" id="code-editor" oninput="applyCodeChanges()"></textarea>
            </div>
        </div>

        <!-- Правая панель -->
        <div class="sidebar sidebar-right">
            <h2>Свойства</h2>
            <div id="editor-controls">
                <p style="color: #64748b; font-size: 13px;">Выберите элемент на холсте для настройки</p>
            </div>
        </div>

    </div>

    <!-- Кнопка выхода из предпросмотра -->
    <button id="exit-preview-btn" onclick="togglePreviewMode()">✕ Выйти из предпросмотра</button>

    <script>
        const canvas = document.getElementById('canvas');
        const emptyMsg = document.getElementById('empty-msg');
        const editorControls = document.getElementById('editor-controls');
        const codeEditor = document.getElementById('code-editor');
        const codeContainer = document.getElementById('code-container');
        
        let selectedElement = null;
        let selectedWrapper = null;
        let elementCount = 0;
        let currentMode = 'visual';

        // ИСТОРИЯ ДЛЯ UNDO / REDO
        let historyStack = [];
        let historyIndex = -1;
        let isUndoRedoAction = false;

        function saveHistoryState() {
            if (isUndoRedoAction) return;
            
            // Если делали действие после отмен, обрезаем будущую историю
            if (historyIndex < historyStack.length - 1) {
                historyStack = historyStack.slice(0, historyIndex + 1);
            }

            historyStack.push(canvas.innerHTML);
            historyIndex++;

            updateHistoryButtons();
        }

        function updateHistoryButtons() {
            document.getElementById('btn-undo').disabled = (historyIndex <= 0);
            document.getElementById('btn-redo').disabled = (historyIndex >= historyStack.length - 1);
        }

        function undo() {
            if (historyIndex > 0) {
                isUndoRedoAction = true;
                historyIndex--;
                canvas.innerHTML = historyStack[historyIndex];
                rebindCanvasEvents();
                updateHistoryButtons();
                isUndoRedoAction = false;
            }
        }

        function redo() {
            if (historyIndex < historyStack.length - 1) {
                isUndoRedoAction = true;
                historyIndex++;
                canvas.innerHTML = historyStack[historyIndex];
                rebindCanvasEvents();
                updateHistoryButtons();
                isUndoRedoAction = false;
            }
        }

        // Горячие клавиши Ctrl+Z и Ctrl+Y
        document.addEventListener('keydown', (e) => {
            if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'z') {
                if (e.shiftKey) {
                    redo();
                } else {
                    undo();
                }
            } else if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'y') {
                redo();
            }
        });

        function rebindCanvasEvents() {
            const items = canvas.querySelectorAll('.canvas-item');
            if (items.length === 0 && emptyMsg) {
                emptyMsg.style.display = 'block';
            } else if (emptyMsg) {
                emptyMsg.style.display = 'none';
            }

            items.forEach(wrapper => {
                const targetEl = wrapper.firstElementChild;
                const deleteBtn = wrapper.querySelector('.delete-btn');

                if (deleteBtn) {
                    deleteBtn.onclick = (e) => {
                        e.stopPropagation();
                        wrapper.remove();
                        if (canvas.querySelectorAll('.canvas-item').length === 0 && emptyMsg) {
                            emptyMsg.style.display = 'block';
                        }
                        editorControls.innerHTML = '<p style="color: #64748b; font-size: 13px;">Выберите элемент на холсте для настройки</p>';
                        saveHistoryState();
                    };
                }

                wrapper.onclick = (e) => {
                    e.stopPropagation();
                    selectElement(wrapper, targetEl, targetEl.tagName.toLowerCase());
                };
            });
        }

        // Загрузка стартового состояния в историю
        window.onload = () => {
            saveHistoryState();
        };

        function switchView(mode) {
            currentMode = mode;
            document.getElementById('btn-view-visual').classList.toggle('active', mode === 'visual');
            document.getElementById('btn-view-code').classList.toggle('active', mode === 'code');

            if (mode === 'code') {
                updateCodeEditorFromCanvas();
                canvas.style.display = 'none';
                codeContainer.style.display = 'flex';
            } else {
                canvas.style.display = 'block';
                codeContainer.style.display = 'none';
            }
        }

        function setDeviceMode(mode) {
            document.getElementById('btn-device-desktop').classList.toggle('active', mode === 'desktop');
            document.getElementById('btn-device-tablet').classList.toggle('active', mode === 'tablet');
            document.getElementById('btn-device-mobile').classList.toggle('active', mode === 'mobile');

            canvas.classList.remove('tablet-mode', 'mobile-mode');
            if (mode === 'tablet') canvas.classList.add('tablet-mode');
            if (mode === 'mobile') canvas.classList.add('mobile-mode');
        }

        function togglePreviewMode() {
            document.body.classList.toggle('preview-mode');
        }

        function changeCanvasTheme(theme) {
            if (theme === 'dark') {
                canvas.classList.add('dark-theme');
                canvas.style.backgroundColor = '#0f172a';
                document.getElementById('page-bg-color').value = '#0f172a';
            } else {
                canvas.classList.remove('dark-theme');
                canvas.style.backgroundColor = '#ffffff';
                document.getElementById('page-bg-color').value = '#ffffff';
            }
        }

        function changeCanvasBg(color) { canvas.style.backgroundColor = color; }
        function changeCanvasPadding(val) { canvas.style.padding = val + 'px'; }
        function changeCanvasFont(font) { canvas.style.fontFamily = font; }

        function clearCanvas() {
            if (confirm("Очистить холст?")) {
                canvas.innerHTML = '';
                if (emptyMsg) {
                    emptyMsg.style.display = 'block';
                    canvas.appendChild(emptyMsg);
                }
                editorControls.innerHTML = '<p style="color: #64748b; font-size: 13px;">Выберите элемент на холсте для настройки</p>';
                saveHistoryState();
            }
        }

        // ШАБЛОНЫ САЙТОВ
        function loadPreset(presetName) {
            if (canvas.children.length > 1 && !confirm("Загрузка шаблона заменит существующие блоки. Продолжить?")) {
                return;
            }

            canvas.innerHTML = '';
            if (emptyMsg) emptyMsg.style.display = 'none';

            if (presetName === 'landing') {
                addElement('navbar');
                addElement('site-title');
                addElement('countdown');
                addElement('pricing');
                addElement('form');
                addElement('footer');
            } else if (presetName === 'portfolio') {
                addElement('navbar');
                addElement('header');
                addElement('text');
                addElement('gallery2');
                addElement('testimonials');
                addElement('floating-messengers');
                addElement('footer');
            } else if (presetName === 'shop') {
                addElement('navbar');
                addElement('header');
                addElement('grid3');
                addElement('pricing');
                addElement('faq');
                addElement('form');
                addElement('footer');
            }

            saveHistoryState();
        }

        function addElement(type) {
            if (emptyMsg) emptyMsg.style.display = 'none';

            elementCount++;
            const wrapper = document.createElement('div');
            wrapper.className = 'canvas-item';
            wrapper.id = 'item-' + elementCount;

            let el;
            if (type === 'site-title') {
                el = document.createElement('h1');
                el.className = 'animated-site-title';
                el.innerText = 'Programist-studio';
                el.style.fontSize = '36px';
                el.style.textAlign = 'center';
                el.style.width = '100%';
            } else if (type === 'countdown') {
                el = document.createElement('div');
                el.style.padding = '20px';
                el.style.backgroundColor = '#1e293b';
                el.style.color = '#38bdf8';
                el.style.borderRadius = '10px';
                el.style.textAlign = 'center';
                el.innerHTML = `
                    <h3 style="color:#ffffff; margin-bottom:10px;">🔥 До конца акции осталось:</h3>
                    <div style="display:flex; justify-content:center; gap:15px; font-size:22px; font-weight:bold;">
                        <div><span id="timer-hours">05</span><small style="display:block; font-size:10px; color:#94a3b8;">часов</small></div>:
                        <div><span id="timer-minutes">42</span><small style="display:block; font-size:10px; color:#94a3b8;">минут</small></div>:
                        <div><span id="timer-seconds">18</span><small style="display:block; font-size:10px; color:#94a3b8;">секунд</small></div>
                    </div>
                `;
            } else if (type === 'pricing') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(220px, 1fr))';
                el.style.gap = '15px';
                el.innerHTML = `
                    <div style="border:1px solid #e2e8f0; padding:20px; border-radius:10px; text-align:center; background:#f8fafc;">
                        <h3>Базовый</h3>
                        <p style="font-size:24px; font-weight:bold; color:#0284c7; margin:10px 0;">3 000 ₽</p>
                        <p style="font-size:12px; color:#64748b;">1 Страница<br>Базовый дизайн<br>Поддержка 24/7</p>
                        <button style="margin-top:15px; padding:8px 16px; background:#0284c7; color:white; border:none; border-radius:6px; cursor:pointer;">Заказать</button>
                    </div>
                    <div style="border:2px solid #38bdf8; padding:20px; border-radius:10px; text-align:center; background:#f0f9ff;">
                        <h3>Стандарт</h3>
                        <p style="font-size:24px; font-weight:bold; color:#0284c7; margin:10px 0;">5 000 ₽</p>
                        <p style="font-size:12px; color:#64748b;">До 5 Страниц<br>Индивидуальный дизайн<br>SEO оптимизация</p>
                        <button style="margin-top:15px; padding:8px 16px; background:#38bdf8; color:#0f172a; border:none; border-radius:6px; font-weight:bold; cursor:pointer;">Заказать</button>
                    </div>
                    <div style="border:1px solid #e2e8f0; padding:20px; border-radius:10px; text-align:center; background:#f8fafc;">
                        <h3>Премиум</h3>
                        <p style="font-size:24px; font-weight:bold; color:#0284c7; margin:10px 0;">10 000 ₽</p>
                        <p style="font-size:12px; color:#64748b;">Безлимит страниц<br>Интернет-магазин<br>Маркетинг поддержка</p>
                        <button style="margin-top:15px; padding:8px 16px; background:#0284c7; color:white; border:none; border-radius:6px; cursor:pointer;">Заказать</button>
                    </div>
                `;
            } else if (type === 'testimonials') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(250px, 1fr))';
                el.style.gap = '15px';
                el.innerHTML = `
                    <div style="border:1px solid #cbd5e1; padding:15px; border-radius:8px; background:#f8fafc; display:flex; gap:12px; align-items:center;">
                        <img src="https://via.placeholder.com/50" style="border-radius:50%; width:50px; height:50px;">
                        <div>
                            <strong>Алексей Иванов</strong>
                            <p style="font-size:11px; color:#64748b;">Предприниматель</p>
                            <p style="font-size:12px; margin-top:5px;">«Отличная работа! Сайт сделали быстро и качественно.»</p>
                        </div>
                    </div>
                `;
            } else if (type === 'floating-messengers') {
                el = document.createElement('div');
                el.style.display = 'flex';
                el.style.gap = '10px';
                el.style.justifyContent = 'center';
                el.style.padding = '10px';
                el.innerHTML = `
                    <a href="https://t.me/programisstuz" target="_blank" style="padding:8px 15px; background:#229ED9; color:white; text-decoration:none; border-radius:20px; font-size:12px; font-weight:bold;">Telegram</a>
                    <a href="https://whatsapp.com" target="_blank" style="padding:8px 15px; background:#25D366; color:white; text-decoration:none; border-radius:20px; font-size:12px; font-weight:bold;">WhatsApp</a>
                    <a href="https://vk.com" target="_blank" style="padding:8px 15px; background:#0077FF; color:white; text-decoration:none; border-radius:20px; font-size:12px; font-weight:bold;">VKontakte</a>
                `;
            } else if (type === 'navbar') {
                el = document.createElement('nav');
                el.style.display = 'flex';
                el.style.justifyContent = 'space-between';
                el.style.alignItems = 'center';
                el.style.padding = '12px 15px';
                el.style.backgroundColor = '#f1f5f9';
                el.style.borderRadius = '6px';
                el.innerHTML = '<strong style="font-size:18px;" class="animated-site-title">Programist-studio</strong><div><a href="#" style="margin-left:15px; text-decoration:none; color:#334155;">Главная</a><a href="#" style="margin-left:15px; text-decoration:none; color:#334155;">Услуги</a><a href="#" style="margin-left:15px; text-decoration:none; color:#334155;">Контакты</a></div>';
            } else if (type === 'header') {
                el = document.createElement('h1');
                el.innerText = 'Заголовок страницы';
                el.style.color = '#0f172a';
            } else if (type === 'text') {
                el = document.createElement('p');
                el.innerText = 'Это пример текстового блока. Введите сюда любой ваш текст...';
                el.style.color = '#334155';
            } else if (type === 'button') {
                let targetUrl = prompt("Введите ссылку для кнопки (URL):", "https://t.me/programisstuz");
                if (!targetUrl) targetUrl = "#";

                el = document.createElement('a');
                el.innerText = 'Узнать больше';
                el.href = targetUrl;
                el.target = "_blank";
                el.style.display = 'inline-block';
                el.style.padding = '10px 20px';
                el.style.backgroundColor = '#38bdf8';
                el.style.color = '#0f172a';
                el.style.textDecoration = 'none';
                el.style.borderRadius = '6px';
                el.style.fontWeight = 'bold';
            } else if (type === 'image') {
                el = document.createElement('img');
                el.src = 'https://via.placeholder.com/750x250';
                el.style.width = '100%';
                el.style.borderRadius = '6px';
            } else if (type === 'card') {
                el = document.createElement('div');
                el.style.border = '1px solid #e2e8f0';
                el.style.borderRadius = '8px';
                el.style.padding = '15px';
                el.style.backgroundColor = '#f8fafc';
                el.innerHTML = '<h3 style="color:#0f172a;">Название карточки</h3><p style="margin-top:8px; font-size:14px; color:#64748b;">Описание карточки товара или услуги.</p>';
            } else if (type === 'grid3') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(200px, 1fr))';
                el.style.gap = '15px';
                el.innerHTML = `
                    <div style="border:1px solid #e2e8f0; padding:15px; border-radius:6px; background:#f8fafc;">
                        <h4 style="color:#0f172a;">Услуга 1</h4>
                        <p style="font-size:13px; color:#64748b; margin-top:5px;">Описание первого блока услуг.</p>
                    </div>
                    <div style="border:1px solid #e2e8f0; padding:15px; border-radius:6px; background:#f8fafc;">
                        <h4 style="color:#0f172a;">Услуга 2</h4>
                        <p style="font-size:13px; color:#64748b; margin-top:5px;">Описание второго блока услуг.</p>
                    </div>
                    <div style="border:1px solid #e2e8f0; padding:15px; border-radius:6px; background:#f8fafc;">
                        <h4 style="color:#0f172a;">Услуга 3</h4>
                        <p style="font-size:13px; color:#64748b; margin-top:5px;">Описание третьего блока услуг.</p>
                    </div>
                `;
            } else if (type === 'gallery2') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = '1fr 1fr';
                el.style.gap = '15px';
                el.innerHTML = `
                    <img src="https://via.placeholder.com/350x200" style="width:100%; border-radius:6px;">
                    <img src="https://via.placeholder.com/350x200" style="width:100%; border-radius:6px;">
                `;
            } else if (type === 'form') {
                el = document.createElement('form');
                el.style.border = '1px solid #e2e8f0';
                el.style.padding = '20px';
                el.style.borderRadius = '8px';
                el.style.backgroundColor = '#f8fafc';
                el.onsubmit = (e) => e.preventDefault();
                el.innerHTML = `
                    <h3 style="margin-bottom:12px; color:#0f172a;">Оставить заявку</h3>
                    <input type="text" placeholder="Ваше имя" style="width:100%; padding:8px; margin-bottom:10px; border:1px solid #cbd5e1; border-radius:4px;">
                    <input type="email" placeholder="Ваш Email" style="width:100%; padding:8px; margin-bottom:10px; border:1px solid #cbd5e1; border-radius:4px;">
                    <textarea placeholder="Сообщение" style="width:100%; height:70px; padding:8px; margin-bottom:10px; border:1px solid #cbd5e1; border-radius:4px;"></textarea>
                    <button style="padding:10px 15px; background:#38bdf8; border:none; border-radius:4px; font-weight:bold; cursor:pointer;">Отправить</button>
                `;
            } else if (type === 'faq') {
                el = document.createElement('div');
                el.style.padding = '15px';
                el.style.borderLeft = '4px solid #38bdf8';
                el.style.backgroundColor = '#f1f5f9';
                el.innerHTML = `
                    <h4 style="color:#0f172a;">Вопрос: Как сделать заказ?</h4>
                    <p style="margin-top:5px; font-size:14px; color:#475569;">Ответ: Заполните форму заявки выше или свяжитесь с нами по контактам.</p>
                `;
            } else if (type === 'divider') {
                el = document.createElement('hr');
                el.style.border = 'none';
                el.style.borderTop = '1px solid #cbd5e1';
                el.style.margin = '15px 0';
            } else if (type === 'footer') {
                el = document.createElement('footer');
                el.style.textAlign = 'center';
                el.style.padding = '15px 0';
                el.style.color = '#94a3b8';
                el.style.fontSize = '12px';
                el.innerText = '© 2026 Все права защищены.';
            }

            wrapper.appendChild(el);

            const deleteBtn = document.createElement('button');
            deleteBtn.className = 'delete-btn';
            deleteBtn.innerText = '✕';
            deleteBtn.onclick = (e) => {
                e.stopPropagation();
                wrapper.remove();
                if (canvas.querySelectorAll('.canvas-item').length === 0 && emptyMsg) {
                    emptyMsg.style.display = 'block';
                }
                editorControls.innerHTML = '<p style="color: #64748b; font-size: 13px;">Выберите элемент на холсте для настройки</p>';
                saveHistoryState();
            };
            wrapper.appendChild(deleteBtn);

            wrapper.onclick = (e) => {
                e.stopPropagation();
                selectElement(wrapper, el, type);
            };

            canvas.appendChild(wrapper);
            selectElement(wrapper, el, type);

            if (currentMode === 'code') {
                updateCodeEditorFromCanvas();
            }

            saveHistoryState();
        }

        function selectElement(wrapper, targetEl, type) {
            document.querySelectorAll('.canvas-item').forEach(item => item.classList.remove('selected'));
            wrapper.classList.add('selected');
            selectedElement = targetEl;
            selectedWrapper = wrapper;

            let html = '';

            if (type === 'site-title' || type === 'header' || type === 'text' || type === 'button' || type === 'footer') {
                html += `
                    <div class="control-group">
                        <label>Текст блока:</label>
                        <input type="text" id="prop-text" value="${targetEl.innerText}">
                    </div>
                `;
            }

            html += `
                <div class="control-group">
                    <label>Анимация появления:</label>
                    <select id="prop-animation">
                        <option value="">Без анимации</option>
                        <option value="anim-fade" ${wrapper.classList.contains('anim-fade') ? 'selected' : ''}>Плавное проявление</option>
                        <option value="anim-slide-up" ${wrapper.classList.contains('anim-slide-up') ? 'selected' : ''}>Появление снизу</option>
                        <option value="anim-slide-left" ${wrapper.classList.contains('anim-slide-left') ? 'selected' : ''}>Появление слева</option>
                        <option value="anim-zoom" ${wrapper.classList.contains('anim-zoom') ? 'selected' : ''}>Увеличение (Zoom)</option>
                    </select>
                </div>
                <div class="control-group">
                    <label>Эффект при наведении (Hover):</label>
                    <select id="prop-hover">
                        <option value="">Без эффекта</option>
                        <option value="hover-zoom" ${wrapper.classList.contains('hover-zoom') ? 'selected' : ''}>Увеличение (Hover Zoom)</option>
                        <option value="hover-glow" ${wrapper.classList.contains('hover-glow') ? 'selected' : ''}>Свечение (Hover Glow)</option>
                    </select>
                </div>
            `;

            if (type === 'button') {
                html += `
                    <div class="control-group">
                        <label>Ссылка (URL):</label>
                        <input type="text" id="prop-href" value="${targetEl.getAttribute('href')}">
                    </div>
                    <div class="control-group">
                        <label>Цвет кнопки:</label>
                        <input type="color" id="prop-bg" value="${rgbToHex(targetEl.style.backgroundColor)}">
                    </div>
                `;
            }

            if (type === 'image') {
                html += `
                    <div class="control-group">
                        <label>URL Изображения:</label>
                        <input type="text" id="prop-src" value="${targetEl.src}">
                    </div>
                `;
            }

            if (type === 'card' || type === 'navbar' || type === 'form' || type === 'faq' || type === 'countdown') {
                html += `
                    <div class="control-group">
                        <label>Фон блока:</label>
                        <input type="color" id="prop-bg" value="${rgbToHex(targetEl.style.backgroundColor)}">
                    </div>
                `;
            }

            if (type === 'header' || type === 'text' || type === 'footer' || type === 'site-title') {
                if (type !== 'site-title') {
                    html += `
                        <div class="control-group">
                            <label>Цвет текста:</label>
                            <input type="color" id="prop-color" value="${rgbToHex(targetEl.style.color)}">
                        </div>
                    `;
                }
                html += `
                    <div class="control-group">
                        <label>Выравнивание:</label>
                        <select id="prop-align">
                            <option value="left" ${targetEl.style.textAlign === 'left' ? 'selected' : ''}>Слева</option>
                            <option value="center" ${targetEl.style.textAlign === 'center' ? 'selected' : ''}>По центру</option>
                            <option value="right" ${targetEl.style.textAlign === 'right' ? 'selected' : ''}>Справа</option>
                        </select>
                    </div>
                `;
            }

            editorControls.innerHTML = html;

            const propText = document.getElementById('prop-text');
            if (propText) propText.oninput = (e) => { targetEl.innerText = e.target.value; saveHistoryState(); };

            const propAnim = document.getElementById('prop-animation');
            if (propAnim) {
                propAnim.onchange = (e) => {
                    wrapper.classList.remove('anim-fade', 'anim-slide-up', 'anim-slide-left', 'anim-zoom');
                    if (e.target.value) wrapper.classList.add(e.target.value);
                    saveHistoryState();
                };
            }

            const propHover = document.getElementById('prop-hover');
            if (propHover) {
                propHover.onchange = (e) => {
                    wrapper.classList.remove('hover-zoom', 'hover-glow');
                    if (e.target.value) wrapper.classList.add(e.target.value);
                    saveHistoryState();
                };
            }

            const propHref = document.getElementById('prop-href');
            if (propHref) propHref.oninput = (e) => { targetEl.setAttribute('href', e.target.value); saveHistoryState(); };

            const propBg = document.getElementById('prop-bg');
            if (propBg) propBg.oninput = (e) => { targetEl.style.backgroundColor = e.target.value; saveHistoryState(); };

            const propSrc = document.getElementById('prop-src');
            if (propSrc) propSrc.oninput = (e) => { targetEl.src = e.target.value; saveHistoryState(); };

            const propColor = document.getElementById('prop-color');
            if (propColor) propColor.oninput = (e) => { targetEl.style.color = e.target.value; saveHistoryState(); };

            const propAlign = document.getElementById('prop-align');
            if (propAlign) propAlign.onchange = (e) => { targetEl.style.textAlign = e.target.value; saveHistoryState(); };
        }

        function updateCodeEditorFromCanvas() {
            const cloneCanvas = canvas.cloneNode(true);
            cloneCanvas.querySelectorAll('.delete-btn').forEach(btn => btn.remove());
            cloneCanvas.querySelectorAll('#empty-msg').forEach(msg => msg.remove());
            
            let cleanHTML = '';
            cloneCanvas.querySelectorAll('.canvas-item').forEach(item => {
                cleanHTML += item.firstElementChild.outerHTML + '\n';
            });

            codeEditor.value = cleanHTML.trim();
        }

        function applyCodeChanges() {
            const newHTML = codeEditor.value;
            canvas.innerHTML = '';
            
            const tempDiv = document.createElement('div');
            tempDiv.innerHTML = newHTML;

            if (tempDiv.children.length === 0) {
                if (emptyMsg) {
                    emptyMsg.style.display = 'block';
                    canvas.appendChild(emptyMsg);
                }
                saveHistoryState();
                return;
            }

            Array.from(tempDiv.children).forEach(child => {
                elementCount++;
                const wrapper = document.createElement('div');
                wrapper.className = 'canvas-item';
                wrapper.id = 'item-' + elementCount;
                wrapper.appendChild(child.cloneNode(true));

                const deleteBtn = document.createElement('button');
                deleteBtn.className = 'delete-btn';
                deleteBtn.innerText = '✕';
                deleteBtn.onclick = (e) => {
                    e.stopPropagation();
                    wrapper.remove();
                    saveHistoryState();
                };
                wrapper.appendChild(deleteBtn);

                wrapper.onclick = (e) => {
                    e.stopPropagation();
                    selectElement(wrapper, wrapper.firstElementChild, child.tagName.toLowerCase());
                };

                canvas.appendChild(wrapper);
            });

            saveHistoryState();
        }

        function rgbToHex(rgb) {
            if (!rgb) return '#ffffff';
            const res = rgb.match(/\d+/g);
            if (!res) return '#ffffff';
            return "#" + ((1 << 24) + (parseInt(res[0]) << 16) + (parseInt(res[1]) << 8) + parseInt(res[2])).toString(16).slice(1);
        }

        function exportHTML() {
            if (currentMode === 'code') applyCodeChanges();

            const cloneCanvas = canvas.cloneNode(true);
            cloneCanvas.querySelectorAll('.delete-btn').forEach(btn => btn.remove());
            cloneCanvas.querySelectorAll('#empty-msg').forEach(msg => msg.remove());

            let cleanContent = '';
            cloneCanvas.querySelectorAll('.canvas-item').forEach(item => {
                cleanContent += `  <div class="${item.className}" style="margin-bottom: 15px;">\n    ${item.firstElementChild.outerHTML}\n  </div>\n`;
            });

            const bgColor = canvas.style.backgroundColor || '#ffffff';
            const padding = canvas.style.padding || '25px';
            const fontFamily = canvas.style.fontFamily || "'Segoe UI', sans-serif";

            const fullPageCode = `<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Мой Сайт</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { 
            font-family: ${fontFamily}; 
            padding: ${padding}; 
            max-width: 1200px; 
            margin: 0 auto; 
            background-color: ${bgColor};
            min-height: 100vh;
            overflow-y: auto;
        }

        @keyframes textGradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes titlePulse {
            0% { transform: scale(1); filter: drop-shadow(0 0 5px rgba(56, 189, 248, 0.4)); }
            50% { transform: scale(1.03); filter: drop-shadow(0 0 15px rgba(168, 85, 247, 0.8)); }
            100% { transform: scale(1); filter: drop-shadow(0 0 5px rgba(56, 189, 248, 0.4)); }
        }

        .animated-site-title {
            background: linear-gradient(90deg, #38bdf8, #818cf8, #c084fc, #38bdf8);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: textGradient 3s linear infinite, titlePulse 2.5s ease-in-out infinite;
            display: inline-block;
            font-weight: 800;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideInLeft { from { opacity: 0; transform: translateX(-30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }

        .anim-fade { animation: fadeIn 0.8s ease forwards; }
        .anim-slide-up { animation: slideUp 0.8s ease forwards; }
        .anim-slide-left { animation: slideInLeft 0.8s ease forwards; }
        .anim-zoom { animation: zoomIn 0.6s ease forwards; }

        .hover-zoom { transition: transform 0.3s ease; }
        .hover-zoom:hover { transform: scale(1.04); }
        .hover-glow { transition: box-shadow 0.3s ease, transform 0.3s ease; }
        .hover-glow:hover { box-shadow: 0 0 20px rgba(56, 189, 248, 0.6); transform: translateY(-3px); }
    </style>
</head>
<body>
${cleanContent}
</body>
</html>`;

            const blob = new Blob([fullPageCode], { type: 'text/html' });
            const a = document.createElement('a');
            a.href = URL.createObjectURL(blob);
            a.download = 'index.html';
            a.click();
        }
    </script>
</body>
</html>
