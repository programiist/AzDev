<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Programist-studio — Конструктор Сайтов с AI, RGB & Drag-and-Drop</title>
    <!-- Google Fonts -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Comfortaa:wght@400;600;700&family=Exo+2:wght@400;600;800&family=Inter:wght@400;600;800&family=JetBrains+Mono:wght@700&family=Lora:ital,wght@0,400;0,600;1,400&family=Montserrat:wght@400;600;800&family=Nunito:wght@400;600;800&family=Open+Sans:wght@400;600;800&family=Oswald:wght@400;600;700&family=Pacifico&family=Playfair+Display:wght@400;600;800&family=Poppins:wght@400;600;800&family=Raleway:wght@400;600;800&family=Roboto:wght@400;600;800&family=Roboto+Mono:wght@700&family=Source+Sans+3:wght@400;600;800&display=swap">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', 'Segoe UI', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        html, body {
            width: 100%;
            min-height: 100vh;
            background-color: #070b14;
            background-image:
                radial-gradient(at 10% 15%, rgba(56, 189, 248, 0.28) 0px, transparent 45%),
                radial-gradient(at 90% 10%, rgba(168, 85, 247, 0.26) 0px, transparent 45%),
                radial-gradient(at 50% 85%, rgba(236, 72, 153, 0.22) 0px, transparent 50%),
                radial-gradient(at 85% 90%, rgba(16, 185, 129, 0.18) 0px, transparent 45%),
                radial-gradient(at 30% 60%, rgba(99, 102, 241, 0.12) 0px, transparent 40%);
            background-attachment: fixed;
            background-size: 200% 200%;
            animation: meshDrift 20s ease-in-out infinite;
            color: #f8fafc;
            overflow-x: hidden;
        }

        @keyframes meshDrift {
            0%, 100% { background-position: 0% 0%, 100% 0%, 50% 100%, 100% 100%, 30% 50%; }
            33% { background-position: 8% 10%, 92% 15%, 48% 90%, 88% 85%, 35% 55%; }
            66% { background-position: 15% 20%, 85% 8%, 55% 80%, 95% 92%, 25% 65%; }
        }

        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0b0f19;
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 3px;
        }

        /* --- RGB АНИМАЦИИ И ЭФФЕКТЫ --- */
        @keyframes rgbBorder {
            0% { border-color: #ff0055; box-shadow: 0 0 18px rgba(255, 0, 85, 0.7); }
            20% { border-color: #ff8800; box-shadow: 0 0 18px rgba(255, 136, 0, 0.7); }
            40% { border-color: #00ffcc; box-shadow: 0 0 18px rgba(0, 255, 204, 0.7); }
            60% { border-color: #3388ff; box-shadow: 0 0 18px rgba(51, 136, 255, 0.7); }
            80% { border-color: #9900ff; box-shadow: 0 0 18px rgba(153, 0, 255, 0.7); }
            100% { border-color: #ff0055; box-shadow: 0 0 18px rgba(255, 0, 85, 0.7); }
        }

        @keyframes rgbGlowText {
            0% { text-shadow: 0 0 8px #ff0055, 0 0 16px #ff0055; color: #fff; }
            20% { text-shadow: 0 0 8px #ff8800, 0 0 16px #ff8800; color: #fff; }
            40% { text-shadow: 0 0 8px #00ffcc, 0 0 16px #00ffcc; color: #fff; }
            60% { text-shadow: 0 0 8px #3388ff, 0 0 16px #3388ff; color: #fff; }
            80% { text-shadow: 0 0 8px #9900ff, 0 0 16px #9900ff; color: #fff; }
            100% { text-shadow: 0 0 8px #ff0055, 0 0 16px #ff0055; color: #fff; }
        }

        @keyframes rgbBorderFire {
            0% { border-color: #ff0000; box-shadow: 0 0 18px rgba(255, 0, 0, 0.7); }
            50% { border-color: #ffcc00; box-shadow: 0 0 18px rgba(255, 204, 0, 0.7); }
            100% { border-color: #ff0000; box-shadow: 0 0 18px rgba(255, 0, 0, 0.7); }
        }
        @keyframes rgbGlowTextFire {
            0% { text-shadow: 0 0 8px #ff3300, 0 0 16px #ff3300; color: #fff; }
            50% { text-shadow: 0 0 8px #ffcc00, 0 0 16px #ffcc00; color: #fff; }
            100% { text-shadow: 0 0 8px #ff3300, 0 0 16px #ff3300; color: #fff; }
        }

        @keyframes rgbBorderOcean {
            0% { border-color: #0ea5e9; box-shadow: 0 0 18px rgba(14, 165, 233, 0.7); }
            50% { border-color: #22d3ee; box-shadow: 0 0 18px rgba(34, 211, 238, 0.7); }
            100% { border-color: #0ea5e9; box-shadow: 0 0 18px rgba(14, 165, 233, 0.7); }
        }
        @keyframes rgbGlowTextOcean {
            0% { text-shadow: 0 0 8px #0ea5e9, 0 0 16px #0ea5e9; color: #fff; }
            50% { text-shadow: 0 0 8px #22d3ee, 0 0 16px #22d3ee; color: #fff; }
            100% { text-shadow: 0 0 8px #0ea5e9, 0 0 16px #0ea5e9; color: #fff; }
        }

        @keyframes rgbBorderNeon {
            0% { border-color: #ec4899; box-shadow: 0 0 18px rgba(236, 72, 153, 0.7); }
            50% { border-color: #a855f7; box-shadow: 0 0 18px rgba(168, 85, 247, 0.7); }
            100% { border-color: #ec4899; box-shadow: 0 0 18px rgba(236, 72, 153, 0.7); }
        }
        @keyframes rgbGlowTextNeon {
            0% { text-shadow: 0 0 8px #ec4899, 0 0 16px #ec4899; color: #fff; }
            50% { text-shadow: 0 0 8px #a855f7, 0 0 16px #a855f7; color: #fff; }
            100% { text-shadow: 0 0 8px #ec4899, 0 0 16px #ec4899; color: #fff; }
        }

        .rgb-card { border: 2px solid #ff0055 !important; animation: rgbBorder 4s linear infinite !important; }
        .rgb-text-glow { animation: rgbGlowText 3s linear infinite !important; }

        .rgb-theme-fire.rgb-card { animation: rgbBorderFire 2.6s ease-in-out infinite !important; }
        .rgb-theme-fire.rgb-text-glow { animation: rgbGlowTextFire 2.2s ease-in-out infinite !important; }

        .rgb-theme-ocean.rgb-card { animation: rgbBorderOcean 3s ease-in-out infinite !important; }
        .rgb-theme-ocean.rgb-text-glow { animation: rgbGlowTextOcean 2.6s ease-in-out infinite !important; }

        .rgb-theme-neon.rgb-card { animation: rgbBorderNeon 2.4s ease-in-out infinite !important; }
        .rgb-theme-neon.rgb-text-glow { animation: rgbGlowTextNeon 2s ease-in-out infinite !important; }

        .rgb-theme-rainbow.rgb-card { animation: rgbBorder 4s linear infinite !important; }
        .rgb-theme-rainbow.rgb-text-glow { animation: rgbGlowText 3s linear infinite !important; }

        @keyframes rgbBorderEmerald {
            0% { border-color: #10b981; box-shadow: 0 0 18px rgba(16, 185, 129, 0.7); }
            50% { border-color: #a3e635; box-shadow: 0 0 18px rgba(163, 230, 53, 0.7); }
            100% { border-color: #10b981; box-shadow: 0 0 18px rgba(16, 185, 129, 0.7); }
        }
        @keyframes rgbGlowTextEmerald {
            0% { text-shadow: 0 0 8px #10b981, 0 0 16px #10b981; color: #fff; }
            50% { text-shadow: 0 0 8px #a3e635, 0 0 16px #a3e635; color: #fff; }
            100% { text-shadow: 0 0 8px #10b981, 0 0 16px #10b981; color: #fff; }
        }
        .rgb-theme-emerald.rgb-card { animation: rgbBorderEmerald 2.8s ease-in-out infinite !important; }
        .rgb-theme-emerald.rgb-text-glow { animation: rgbGlowTextEmerald 2.4s ease-in-out infinite !important; }

        /* --- ДОПОЛНИТЕЛЬНЫЕ АНИМАЦИИ --- */
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

        @keyframes floatAnim {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }

        @keyframes pulseGlow {
            0% { box-shadow: 0 0 0 0 rgba(56, 189, 248, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(56, 189, 248, 0); }
            100% { box-shadow: 0 0 0 0 rgba(56, 189, 248, 0); }
        }

        @keyframes flipIn {
            0% { transform: rotateY(-90deg); opacity: 0; }
            100% { transform: rotateY(0deg); opacity: 1; }
        }

        @keyframes bounceAnim {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-15px); }
            60% { transform: translateY(-7px); }
        }

        @keyframes shakeAnim {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-5px); }
            40%, 80% { transform: translateX(5px); }
        }

        @keyframes rotateAnim {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes sparkleGlow {
            0% { filter: drop-shadow(0 0 2px #38bdf8); }
            50% { filter: drop-shadow(0 0 12px #ec4899); }
            100% { filter: drop-shadow(0 0 2px #38bdf8); }
        }

        .animated-site-title {
            background: linear-gradient(90deg, #38bdf8, #818cf8, #c084fc, #f472b6, #38bdf8);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: textGradient 4s linear infinite, titlePulse 2.8s ease-in-out infinite;
            display: inline-block;
            font-weight: 800;
            letter-spacing: -0.02em;
        }

        .title-theme-fire { background: linear-gradient(90deg, #ff3300, #ff8800, #ffcc00, #ff3300) !important; background-size: 300% 300% !important; }
        .title-theme-ocean { background: linear-gradient(90deg, #0ea5e9, #22d3ee, #38bdf8, #0ea5e9) !important; background-size: 300% 300% !important; }
        .title-theme-neon { background: linear-gradient(90deg, #ec4899, #a855f7, #6366f1, #ec4899) !important; background-size: 300% 300% !important; }
        .title-theme-rainbow { background: linear-gradient(90deg, #ff0055, #ff8800, #ffee00, #00ffcc, #3388ff, #9900ff, #ff0055) !important; background-size: 400% 400% !important; }
        .title-theme-emerald { background: linear-gradient(90deg, #10b981, #22c55e, #a3e635, #10b981) !important; background-size: 300% 300% !important; }

        @keyframes codeSymbolPulse {
            0% { transform: scale(1) rotate(0deg); filter: drop-shadow(0 0 6px #38bdf8) drop-shadow(0 0 12px rgba(56,189,248,0.4)); }
            25% { transform: scale(1.08) rotate(3deg); filter: drop-shadow(0 0 10px #818cf8) drop-shadow(0 0 18px rgba(129,140,248,0.5)); }
            50% { transform: scale(1.15) rotate(-5deg); filter: drop-shadow(0 0 14px #c084fc) drop-shadow(0 0 22px rgba(192,132,252,0.6)); }
            75% { transform: scale(1.08) rotate(2deg); filter: drop-shadow(0 0 10px #f472b6) drop-shadow(0 0 18px rgba(244,114,182,0.5)); }
            100% { transform: scale(1) rotate(0deg); filter: drop-shadow(0 0 6px #38bdf8) drop-shadow(0 0 12px rgba(56,189,248,0.4)); }
        }

        @keyframes codeSymbolGradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes brandIconGlow {
            0%, 100% { box-shadow: 0 0 12px rgba(56, 189, 248, 0.5), 0 0 24px rgba(99, 102, 241, 0.25), inset 0 0 12px rgba(255,255,255,0.08); }
            50% { box-shadow: 0 0 20px rgba(168, 85, 247, 0.7), 0 0 36px rgba(236, 72, 153, 0.35), inset 0 0 16px rgba(255,255,255,0.12); }
        }

        .brand-icon {
            position: relative;
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #0284c7, #6366f1, #9333ea, #ec4899);
            background-size: 200% 200%;
            animation: textGradient 6s linear infinite, brandIconGlow 3s ease-in-out infinite;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            flex-shrink: 0;
        }

        .brand-icon::before {
            content: '';
            position: absolute;
            inset: 1px;
            border-radius: 11px;
            background: linear-gradient(135deg, rgba(15,23,42,0.85), rgba(30,41,59,0.9));
            z-index: 0;
        }

        .brand-icon span {
            position: relative;
            z-index: 1;
            font-family: 'JetBrains Mono', 'Roboto Mono', 'Courier New', monospace;
            font-weight: 800;
            font-size: 15px;
            letter-spacing: -1.5px;
            background: linear-gradient(90deg, #ffffff, #38bdf8, #c084fc, #f472b6, #ffffff);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: codeSymbolGradient 2.5s linear infinite, codeSymbolPulse 2.8s ease-in-out infinite;
            display: inline-block;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideInLeft { from { opacity: 0; transform: translateX(-30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes slideInRight { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes slideDown { from { opacity: 0; transform: translateY(-30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }
        @keyframes zoomOut { from { opacity: 0; transform: scale(1.2); } to { opacity: 1; transform: scale(1); } }
        @keyframes swingAnim { 0%, 100% { transform: rotate(0deg); } 20% { transform: rotate(6deg); } 40% { transform: rotate(-5deg); } 60% { transform: rotate(3deg); } 80% { transform: rotate(-2deg); } }
        @keyframes wobbleAnim { 0%, 100% { transform: translateX(0) rotate(0); } 25% { transform: translateX(-4px) rotate(-1.5deg); } 75% { transform: translateX(4px) rotate(1.5deg); } }
        @keyframes glowPulseColor { 0% { box-shadow: 0 0 12px rgba(56,189,248,0.6); } 33% { box-shadow: 0 0 18px rgba(168,85,247,0.6); } 66% { box-shadow: 0 0 18px rgba(236,72,153,0.6); } 100% { box-shadow: 0 0 12px rgba(56,189,248,0.6); } }
        @keyframes heartbeat { 0%, 100% { transform: scale(1); } 14% { transform: scale(1.08); } 28% { transform: scale(1); } 42% { transform: scale(1.08); } 70% { transform: scale(1); } }
        @keyframes blurIn { from { opacity: 0; filter: blur(8px); } to { opacity: 1; filter: blur(0); } }
        @keyframes flipY { 0% { transform: perspective(400px) rotateY(90deg); opacity: 0; } 100% { transform: perspective(400px) rotateY(0); opacity: 1; } }

        .anim-fade { animation: fadeIn 0.8s ease forwards; }
        .anim-slide-up { animation: slideUp 0.8s ease forwards; }
        .anim-slide-left { animation: slideInLeft 0.8s ease forwards; }
        .anim-slide-right { animation: slideInRight 0.8s ease forwards; }
        .anim-slide-down { animation: slideDown 0.8s ease forwards; }
        .anim-zoom { animation: zoomIn 0.6s ease forwards; }
        .anim-zoom-out { animation: zoomOut 0.6s ease forwards; }
        .anim-float { animation: floatAnim 3s ease-in-out infinite; }
        .anim-pulse { animation: pulseGlow 2s infinite; }
        .anim-flip { animation: flipIn 0.8s ease forwards; }
        .anim-flip-y { animation: flipY 0.9s ease forwards; }
        .anim-bounce { animation: bounceAnim 2s infinite; }
        .anim-shake { animation: shakeAnim 2s infinite; }
        .anim-rotate { animation: rotateAnim 10s linear infinite; }
        .anim-sparkle { animation: sparkleGlow 2s ease-in-out infinite; }
        .anim-swing { animation: swingAnim 2.5s ease-in-out infinite; transform-origin: top center; }
        .anim-wobble { animation: wobbleAnim 2s ease-in-out infinite; }
        .anim-glow-pulse { animation: glowPulseColor 3s ease-in-out infinite; }
        .anim-heartbeat { animation: heartbeat 1.5s ease-in-out infinite; }
        .anim-blur-in { animation: blurIn 0.9s ease forwards; }

        .top-bar {
            min-height: 60px;
            background: rgba(30, 41, 59, 0.85);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            padding: 8px 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            gap: 10px;
        }

        .top-bar::after {
            content: '';
            position: absolute;
            left: 0; right: 0; bottom: -1px;
            height: 2px;
            background: linear-gradient(90deg, #38bdf8, #a855f7, #ec4899, #38bdf8);
            background-size: 300% 100%;
            animation: textGradient 6s linear infinite;
            opacity: 0.7;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 18px;
            font-weight: 800;
        }

        .tg-banner-link {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 6px 12px;
            background: linear-gradient(135deg, #0088cc, #229ed9);
            color: #ffffff;
            text-decoration: none;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 700;
            box-shadow: 0 0 10px rgba(34, 158, 217, 0.4);
            white-space: nowrap;
        }

        .save-badge {
            font-size: 11px;
            color: #10b981;
            background: rgba(16, 185, 129, 0.1);
            padding: 4px 8px;
            border-radius: 12px;
            border: 1px solid rgba(16, 185, 129, 0.3);
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .view-toggle, .device-toggle, .history-toggle, .page-manager, .zoom-controls {
            display: flex;
            background-color: #0f172a;
            padding: 3px;
            border-radius: 8px;
            gap: 2px;
            border: 1px solid rgba(255, 255, 255, 0.08);
            align-items: center;
        }

        .page-select {
            background: transparent;
            color: #38bdf8;
            border: none;
            font-size: 12px;
            font-weight: bold;
            padding: 4px 8px;
            outline: none;
        }

        .toggle-btn {
            padding: 6px 10px;
            border: none;
            background: transparent;
            color: #94a3b8;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 12px;
            transition: all 0.2s ease;
            white-space: nowrap;
        }

        .toggle-btn:disabled {
            opacity: 0.3;
            cursor: not-allowed;
        }

        .toggle-btn.active {
            background: linear-gradient(135deg, #38bdf8, #3b82f6);
            color: #0f172a;
            box-shadow: 0 0 8px rgba(56, 189, 248, 0.4);
        }

        .top-actions {
            display: flex;
            gap: 8px;
        }

        .mobile-tabs {
            display: none;
            width: 100%;
            background: #111827;
            border-bottom: 1px solid #334155;
            position: sticky;
            top: 60px;
            z-index: 99;
        }

        .mobile-tab-btn {
            flex: 1;
            padding: 12px;
            background: transparent;
            border: none;
            color: #94a3b8;
            font-size: 13px;
            font-weight: bold;
            cursor: pointer;
            text-align: center;
        }

        .mobile-tab-btn.active {
            color: #38bdf8;
            border-bottom: 3px solid #38bdf8;
            background: rgba(56, 189, 248, 0.05);
        }

        .main-container {
            display: flex;
            min-height: calc(100vh - 60px);
            position: relative;
        }

        .sidebar {
            width: 280px;
            background-color: #111827;
            border-right: 1px solid rgba(255, 255, 255, 0.08);
            display: flex;
            flex-direction: column;
            padding: 15px;
            gap: 8px;
            max-height: calc(100vh - 60px);
            position: sticky;
            top: 60px;
            overflow-y: auto;
            flex-shrink: 0;
            z-index: 20;
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
            margin-bottom: 2px;
            font-weight: 700;
        }

        .sidebar h2:first-child { margin-top: 0; }

        .btn-element {
            padding: 10px 12px;
            background: #1e293b;
            border: 1px solid #334155;
            color: #f8fafc;
            border-radius: 8px;
            cursor: pointer;
            text-align: left;
            font-weight: 500;
            font-size: 13px;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: space-between;
            touch-action: manipulation;
        }

        .btn-element:active {
            transform: scale(0.98);
        }

        .btn-element:hover {
            border-color: #38bdf8;
            box-shadow: 0 4px 14px rgba(56, 189, 248, 0.18);
            transform: translateY(-1px);
        }

        .btn-ai-wizard {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, #a855f7, #38bdf8, #ec4899);
            background-size: 220% 220%;
            animation: textGradient 5s linear infinite;
            color: #ffffff;
            border: none;
            border-radius: 10px;
            font-weight: 800;
            font-size: 14px;
            cursor: pointer;
            box-shadow: 0 6px 20px rgba(168, 85, 247, 0.35);
            margin-bottom: 6px;
        }

        #ai-wizard-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(5, 8, 15, 0.72);
            backdrop-filter: blur(3px);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        .ai-wizard-box {
            background: #111827;
            border: 1px solid #334155;
            border-radius: 14px;
            max-width: 420px;
            width: 100%;
            padding: 22px;
            color: #f8fafc;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0,0,0,0.6);
        }

        .ai-wizard-checks label {
            display: flex;
            align-items: center;
            gap: 6px;
            color: #f8fafc;
            font-size: 12px;
            padding: 2px 0;
        }

        .inner-link-block {
            border-top: 1px dashed #334155;
            padding-top: 8px;
            margin-top: 4px;
        }

        .btn-ai {
            background: linear-gradient(135deg, rgba(168, 85, 247, 0.3), rgba(236, 72, 153, 0.3));
            border-color: #a855f7;
            color: #e879f9;
            font-weight: 700;
        }

        .btn-preset {
            background: linear-gradient(135deg, rgba(56, 189, 248, 0.15), rgba(99, 102, 241, 0.15));
            border-color: #38bdf8;
            color: #38bdf8;
        }

        .btn-rgb-effect {
            background: linear-gradient(90deg, #ff0055, #00ffcc, #9900ff);
            background-size: 200% 200%;
            animation: textGradient 3s linear infinite;
            color: #ffffff;
            font-weight: bold;
            border: none;
        }

        .btn-danger {
            background: rgba(239, 68, 68, 0.1);
            color: #f87171;
            border: 1px solid rgba(239, 68, 68, 0.3);
            margin-top: 10px;
        }

        .workspace {
            flex: 1;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            background:
                radial-gradient(circle at 15% 10%, rgba(56, 189, 248, 0.22), transparent 45%),
                radial-gradient(circle at 85% 0%, rgba(168, 85, 247, 0.20), transparent 45%),
                radial-gradient(circle at 50% 100%, rgba(236, 72, 153, 0.16), transparent 55%),
                radial-gradient(circle at 70% 40%, rgba(16, 185, 129, 0.08), transparent 40%),
                radial-gradient(circle at center, #1a2332 0%, #070b14 100%);
            min-height: calc(100vh - 60px);
            overflow-x: auto;
        }

        .canvas-wrapper {
            width: 100%;
            display: flex;
            justify-content: center;
            transition: transform 0.2s ease;
            transform-origin: top center;
        }

        .canvas {
            width: 100%;
            max-width: 1200px;
            min-height: 700px;
            background-color: #ffffff;
            color: #1e293b;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            transition: background-color 0.3s ease, color 0.3s ease;
            margin-bottom: 40px;
            position: relative;
        }

        .canvas.dark-theme {
            background-color: #0d1117 !important;
            color: #ffffff !important;
        }
        
        .canvas.dark-theme div, .canvas.dark-theme p, .canvas.dark-theme h1, .canvas.dark-theme h2, .canvas.dark-theme h3 {
            color: inherit;
        }
        .canvas.dark-theme .dark-card {
            background-color: #161b22 !important;
            color: #f0f6fc !important;
            border-color: #30363d !important;
        }

        .canvas.tablet-mode { max-width: 768px; }
        .canvas.mobile-mode { max-width: 375px; padding: 12px; }

        .code-editor-container {
            width: 100%;
            max-width: 1200px;
            display: none;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 40px;
        }

        .code-editor {
            width: 100%;
            min-height: 450px;
            background-color: #0f172a;
            color: #38bdf8;
            border: 1px solid #334155;
            border-radius: 8px;
            padding: 12px;
            font-family: monospace;
            font-size: 13px;
            line-height: 1.4;
            resize: vertical;
            outline: none;
        }

        .canvas-item {
            position: relative;
            margin-bottom: 12px;
            padding: 4px;
            border: 2px dashed transparent;
            border-radius: 6px;
            cursor: pointer;
            transition: border-color 0.2s ease, box-shadow 0.2s ease, transform 0.2s ease;
        }

        .canvas-item.drag-over {
            border-color: #a855f7 !important;
            background-color: rgba(168, 85, 247, 0.08);
            transform: scale(1.01);
        }

        .canvas-item.is-draggable {
            position: absolute;
            z-index: 100;
            cursor: move;
            user-select: none;
            touch-action: none;
        }

        .canvas-item.selected {
            border-color: #818cf8;
            outline: 2px solid #818cf8;
            box-shadow: 0 0 12px rgba(129, 140, 248, 0.4);
        }

        .canvas-item .delete-btn {
            position: absolute;
            top: -10px;
            right: -10px;
            background: #ef4444;
            color: white;
            border: none;
            border-radius: 50%;
            width: 26px;
            height: 26px;
            font-size: 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 6px rgba(0,0,0,0.4);
            z-index: 10;
        }

        .drag-handle {
            position: absolute;
            top: -10px;
            left: -10px;
            background: #38bdf8;
            color: #0f172a;
            border-radius: 4px;
            padding: 2px 6px;
            font-size: 10px;
            font-weight: bold;
            cursor: grab;
            z-index: 10;
            display: none;
        }

        .canvas-item.selected .drag-handle {
            display: block;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
            margin-bottom: 10px;
        }

        .control-group label { 
            font-size: 12px; 
            color: #94a3b8; 
            display: flex; 
            justify-content: space-between; 
        }

        .control-group input, .control-group select, .control-group textarea {
            padding: 8px 10px;
            background-color: #0f172a;
            border: 1px solid #334155;
            color: #f8fafc;
            border-radius: 6px;
            font-size: 13px;
            outline: none;
        }

        .control-group input[type="range"] {
            padding: 0;
            height: 6px;
            accent-color: #38bdf8;
            cursor: pointer;
        }

        .control-group input[type="color"] { height: 38px; cursor: pointer; padding: 2px; }

        .btn-row-controls {
            display: flex;
            gap: 5px;
            margin-bottom: 10px;
        }

        .btn-row-controls button {
            flex: 1;
            padding: 8px;
            background: #1e293b;
            border: 1px solid #334155;
            color: #f8fafc;
            border-radius: 6px;
            font-size: 11px;
            font-weight: bold;
            cursor: pointer;
        }

        .btn-row-controls button:hover {
            background: #334155;
        }

        .action-btn {
            padding: 8px 14px;
            background: linear-gradient(135deg, #0284c7, #38bdf8);
            color: #0f172a;
            border: none;
            border-radius: 6px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 12px;
            white-space: nowrap;
        }

        .btn-gen-ai {
            background: linear-gradient(135deg, #a855f7, #ec4899);
            color: #ffffff;
            margin-top: 4px;
            padding: 8px;
            border: none;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            font-size: 12px;
        }

        .btn-preview {
            background: linear-gradient(135deg, #a855f7, #c084fc);
            color: #ffffff;
        }

        body.preview-mode .top-bar, 
        body.preview-mode .sidebar,
        body.preview-mode .mobile-tabs { display: none !important; }
        body.preview-mode .main-container { min-height: 100vh; }
        body.preview-mode .workspace { padding: 0; background: #ffffff; }
        body.preview-mode .canvas-wrapper { transform: scale(1) !important; }
        body.preview-mode .canvas {
            max-width: 100% !important;
            border-radius: 0;
            box-shadow: none;
            margin-bottom: 0;
            padding: 20px;
        }
        body.preview-mode .canvas-item { border: none !important; outline: none !important; }
        body.preview-mode .delete-btn, body.preview-mode .drag-handle { display: none !important; }

        #exit-preview-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 9999;
            display: none;
            background: #ef4444;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
            font-size: 13px;
        }

        body.preview-mode #exit-preview-btn { display: block; }
        body.preview-mode #ai-wizard-overlay { display: none !important; }

        @media (max-width: 1024px) {
            .main-container { flex-direction: column; }
            .mobile-tabs { display: flex; }
            .sidebar { 
                width: 100%; 
                max-height: none; 
                position: relative; 
                top: 0; 
                display: none; 
                border: none; 
                padding: 12px;
            }
            .sidebar.active-tab { display: flex; }
            .workspace { display: flex; width: 100%; padding: 8px; }
            .workspace.hidden-tab { display: none; }
            .zoom-controls { display: none; }
            .top-bar { justify-content: space-between; gap: 5px; padding: 6px 10px; }
            .btn-element { padding: 13px 12px; font-size: 14px; min-height: 44px; }
            .control-group input, .control-group select, .control-group textarea { padding: 11px; font-size: 15px; }
            .canvas-item .delete-btn { width: 30px; height: 30px; font-size: 14px; }
            .drag-handle { padding: 6px 10px; font-size: 12px; }
            .device-toggle { gap: 3px; }
            .device-toggle .toggle-btn { padding: 8px; }
        }

        @media (max-width: 820px) {
            .device-toggle #btn-device-tablet span, .device-toggle #btn-device-mobile span { display: none; }
        }

        @media (max-width: 600px) {
            .brand span { font-size: 14px; }
            .tg-banner-link span { display: none; }
            .top-actions { width: 100%; justify-content: space-between; margin-top: 5px; }
            .action-btn { flex: 1; text-align: center; padding: 12px 8px; font-size: 13px; }
            .canvas { padding: 10px; min-height: 500px; }
            .save-badge { display: none; }
            .page-manager { max-width: 130px; }
            .device-toggle { display: none; }
            .history-toggle .toggle-btn { padding: 8px 10px; }
            .btn-row-controls button { padding: 10px 6px; font-size: 12px; }
            .mobile-tab-btn { padding: 14px 8px; font-size: 12px; }
            .ai-wizard-box { padding: 16px; max-width: 100%; }
        }

        @media (max-width: 380px) {
            .brand span { display: none; }
            .top-bar { padding: 6px 8px; }
            .page-manager { max-width: 100px; }
            .page-select { font-size: 11px; }
        }

        @media (hover: none) and (pointer: coarse) {
            .btn-element, .toggle-btn, .action-btn, .delete-btn { touch-action: manipulation; }
            .canvas-item { padding: 6px; }
            .canvas-item .delete-btn { width: 32px; height: 32px; font-size: 15px; top: -12px; right: -12px; }
        }
    </style>
</head>
<body>

    <div class="top-bar">
        <div class="brand">
            <div class="brand-icon">
                <span>&lt;/&gt;</span>
            </div>
            <span class="animated-site-title">Programist-studio</span>
        </div>

        <a href="https://t.me/programisstuz" target="_blank" class="tg-banner-link">
            🚀 <span>Telegram</span>
        </a>

        <div class="page-manager">
            <span style="font-size:11px; color:#94a3b8; padding-left:5px;">📄</span>
            <select id="pages-select" class="page-select" onchange="switchPage(this.value)">
                <option value="index">Главная (index)</option>
                <option value="about">О нас (about)</option>
                <option value="services">Услуги (services)</option>
                <option value="contact">Контакты (contact)</option>
            </select>
            <button class="toggle-btn" onclick="addNewPage()" title="Добавить страницу">+</button>
        </div>

        <div class="zoom-controls">
            <button class="toggle-btn" onclick="setZoom(0.5)">50%</button>
            <button class="toggle-btn" onclick="setZoom(0.75)">75%</button>
            <button class="toggle-btn active" id="zoom-100" onclick="setZoom(1)">100%</button>
            <button class="toggle-btn" onclick="setZoom(1.25)">125%</button>
        </div>

        <div class="save-badge">
            <span>💾</span> <span id="save-status-text">Сохранено</span>
        </div>

        <div class="history-toggle">
            <button class="toggle-btn" id="btn-undo" onclick="undo()" title="Отменить" disabled>↩️</button>
            <button class="toggle-btn" id="btn-redo" onclick="redo()" title="Повторить" disabled>↪️</button>
        </div>

        <div class="device-toggle">
            <button class="toggle-btn active" id="btn-device-desktop" onclick="setDeviceMode('desktop')">🖥️</button>
            <button class="toggle-btn" id="btn-device-tablet" onclick="setDeviceMode('tablet')">📱 <span>Tablet</span></button>
            <button class="toggle-btn" id="btn-device-mobile" onclick="setDeviceMode('mobile')">📱 <span>Phone</span></button>
        </div>

        <div class="view-toggle">
            <button class="toggle-btn active" id="btn-view-visual" onclick="switchView('visual')">Визуал</button>
            <button class="toggle-btn" id="btn-view-code" onclick="switchView('code')">HTML</button>
        </div>

        <div class="top-actions">
            <button class="action-btn btn-preview" onclick="togglePreviewMode()">👁️ Просмотр</button>
            <button class="action-btn" onclick="exportHTML()">Скачать</button>
        </div>
    </div>

    <div class="mobile-tabs">
        <button class="mobile-tab-btn" id="mtab-elements" onclick="switchMobileTab('elements')">📦 Блоки</button>
        <button class="mobile-tab-btn active" id="mtab-canvas" onclick="switchMobileTab('canvas')">🎨 Холст</button>
        <button class="mobile-tab-btn" id="mtab-props" onclick="switchMobileTab('props')">⚙️ Свойства</button>
    </div>

    <div class="main-container">
        
        <div class="sidebar" id="sidebar-left">
            <button class="btn-ai-wizard" onclick="openAIWizard()">🤖 AI-Помощник: создать сайт целиком</button>

            <h2>AI Дизайн & Цвета</h2>
            <button class="btn-element btn-ai" onclick="generateAIPalette()">🎨 Сгенерировать AI-палитру <span>★</span></button>
            <button class="btn-element btn-ai" onclick="enhanceCanvasDesignAI()">✨ Улучшить стиль (AI) <span>★</span></button>
            <button class="btn-element btn-ai" onclick="generateElementDesignAI()">🤖 AI Стили элемента <span>★</span></button>
            <button class="btn-element btn-rgb-effect" onclick="applyRGBEffectToSelected()">🌈 RGB Подсветка (Выделенное)</button>

            <h2>Готовые Шаблоны</h2>
            <button class="btn-element btn-preset" onclick="loadPreset('landing')">🚀 Лендинг услуг <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('portfolio')">🎨 Портфолио <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('shop')">🛒 Интернет-магазин <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('saas')">⚡ SaaS Продукт <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('blog')">📰 Блог / Медиа <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('event')">🎉 Событие / Ивент <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('education')">🎓 Курс / Инфопродукт <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('restaurant')">🍕 Еда & Ресторан <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('corporate')">🏢 Корпоративный сайт <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('beauty')">💅 Салон красоты <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('fitness')">🏋️ Фитнес-клуб <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('realestate')">🏠 Недвижимость <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('medical')">🩺 Медицинский центр <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('travel')">✈️ Туристическое агентство <span>★</span></button>
            <button class="btn-element btn-preset" onclick="loadPreset('wedding')">💍 Свадьбы & Праздники <span>★</span></button>

            <h2>Анимированные и Интерактивные</h2>
            <button class="btn-element" onclick="addElement('site-theme-toggle')">Переключатель темы (☀️/🌙) <span>+</span></button>
            <button class="btn-element" onclick="addElement('site-title')">Анимированное Название <span>+</span></button>
            <button class="btn-element" onclick="addElement('countdown')">Счетчик отсчета <span>+</span></button>
            <button class="btn-element" onclick="addElement('draggable-icon')">✋ Перетаскиваемая Иконка <span>+</span></button>
            <button class="btn-element" onclick="addElement('image-slider')">🖼️ Слайдер Картинок <span>+</span></button>
            <button class="btn-element" onclick="addElement('popup-btn')">🪟 Всплывающее Окно (Popup) <span>+</span></button>
            <button class="btn-element" onclick="addElement('modal-form')">📋 Модальная форма <span>+</span></button>

            <h2>Базовые блоки</h2>
            <button class="btn-element" onclick="addElement('navbar')">Шапка (Nav) <span>+</span></button>
            <button class="btn-element" onclick="addElement('header')">Заголовок <span>+</span></button>
            <button class="btn-element" onclick="addElement('text')">Текст <span>+</span></button>
            <button class="btn-element" onclick="addElement('button')">Кнопка <span>+</span></button>
            <button class="btn-element" onclick="addElement('image')">Изображение <span>+</span></button>
            <button class="btn-element" onclick="addElement('video')">🎬 Видео плеер <span>+</span></button>
            <button class="btn-element" onclick="addElement('audio')">🎵 Аудио плеер <span>+</span></button>
            <button class="btn-element" onclick="addElement('divider')">Разделитель <span>+</span></button>
            <button class="btn-element" onclick="addElement('footer')">Подвал (Footer) <span>+</span></button>

            <h2>Сложные блоки & Маркетинг</h2>
            <button class="btn-element" onclick="addElement('promo-banner')">🏷️ Баннер Акции <span>+</span></button>
            <button class="btn-element" onclick="addElement('pricing')">Тарифы / Цены (редактируемые) <span>+</span></button>
            <button class="btn-element" onclick="addElement('form')">Форма заявки <span>+</span></button>
            <button class="btn-element" onclick="addElement('star-reviews')">Отзывы со звездами (5★) <span>+</span></button>
            <button class="btn-element" onclick="addElement('social-share')">Соцсети & Поделиться <span>+</span></button>
            <button class="btn-element" onclick="addElement('testimonials')">Простой отзыв <span>+</span></button>
            <button class="btn-element" onclick="addElement('floating-messengers')">Мессенджеры <span>+</span></button>
            <button class="btn-element" onclick="addElement('card')">Карточка <span>+</span></button>
            <button class="btn-element" onclick="addElement('grid2')">Колонки (2 блока) <span>+</span></button>
            <button class="btn-element" onclick="addElement('grid3')">Сетка (3 блока) <span>+</span></button>
            <button class="btn-element" onclick="addElement('features')">Блок Преимуществ <span>+</span></button>
            <button class="btn-element" onclick="addElement('stats')">📊 Статистика / Цифры <span>+</span></button>
            <button class="btn-element" onclick="addElement('gallery2')">Галерея (2 фото) <span>+</span></button>
            <button class="btn-element" onclick="addElement('faq')">Блок FAQ <span>+</span></button>
            <button class="btn-element" onclick="addElement('map')">📍 Карта / Геолокация <span>+</span></button>

            <h2>Новые конструкторы</h2>
            <button class="btn-element" onclick="addElement('hero-split')">🖼️ Герой (Текст + Фото) <span>+</span></button>
            <button class="btn-element" onclick="addElement('cta-banner')">📣 CTA-баннер <span>+</span></button>
            <button class="btn-element" onclick="addElement('team')">👥 Команда <span>+</span></button>
            <button class="btn-element" onclick="addElement('newsletter')">📩 Подписка на новости <span>+</span></button>
            <button class="btn-element" onclick="addElement('logos-strip')">🏷️ Логотипы клиентов <span>+</span></button>
            <button class="btn-element" onclick="addElement('timeline')">🧭 Этапы работы (Таймлайн) <span>+</span></button>

            <h2>Настройки страницы</h2>
            <div class="control-group">
                <label>Размер холста (Ширина):</label>
                <select id="canvas-width-select" onchange="changeCanvasWidth(this.value)">
                    <option value="900px">900px (Узкий)</option>
                    <option value="1100px">1100px</option>
                    <option value="1200px">1200px (Стандарт)</option>
                    <option value="1400px">1400px (Широкий)</option>
                    <option value="1600px">1600px (Очень широкий)</option>
                    <option value="100%">100% (Во весь экран)</option>
                </select>
            </div>
            <div class="control-group">
                <label>Мин. высота холста:</label>
                <select id="canvas-height-select" onchange="changeCanvasHeight(this.value)">
                    <option value="500px">500px (Компактный)</option>
                    <option value="700px">700px (Авто)</option>
                    <option value="900px">900px</option>
                    <option value="1000px">1000px</option>
                    <option value="1200px">1200px</option>
                    <option value="1500px">1500px (Длинный лендинг)</option>
                    <option value="2000px">2000px</option>
                    <option value="2500px">2500px (Очень длинный)</option>
                    <option value="3000px">3000px</option>
                </select>
            </div>
            <div class="control-group">
                <label>Шрифт сайта:</label>
                <select id="global-font" onchange="changeGlobalFont(this.value)">
                    <option value="Inter">Inter</option>
                    <option value="Montserrat">Montserrat</option>
                    <option value="Poppins">Poppins</option>
                    <option value="Roboto">Roboto</option>
                    <option value="Open Sans">Open Sans</option>
                    <option value="Nunito">Nunito</option>
                    <option value="Raleway">Raleway</option>
                    <option value="Source Sans 3">Source Sans 3</option>
                    <option value="Oswald">Oswald</option>
                    <option value="Exo 2">Exo 2</option>
                    <option value="Playfair Display">Playfair Display</option>
                    <option value="Lora">Lora</option>
                    <option value="Comfortaa">Comfortaa</option>
                    <option value="Caveat">Caveat (Рукописный)</option>
                    <option value="Pacifico">Pacifico (Декоративный)</option>
                    <option value="JetBrains Mono">JetBrains Mono (Код)</option>
                </select>
            </div>
            <div class="control-group">
                <label>Тема конструктора:</label>
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
                <label>Отступы (px):</label>
                <input type="number" id="page-padding" value="20" min="0" max="100" onchange="changeCanvasPadding(this.value)">
            </div>
            <button class="btn-element btn-danger" onclick="clearCanvas()">Очистить холст 🗑</button>
            <button class="btn-element btn-danger" style="background: rgba(239,68,68,0.2); color:#fca5a5;" onclick="resetLocalStorage()">💾 Сбросить сохранение</button>
        </div>

        <div class="workspace" id="workspace-area">
            <div class="canvas-wrapper" id="canvas-wrapper">
                <div class="canvas" id="canvas">
                    <p id="empty-msg" style="color: #64748b; text-align: center; margin-top: 150px; font-size: 14px;">
                        Выберите блоки во вкладке «Блоки» или загрузите готовый шаблон!
                    </p>
                </div>
            </div>

            <div class="code-editor-container" id="code-container">
                <label style="color: #94a3b8; font-size: 12px;">Редактирование HTML:</label>
                <textarea class="code-editor" id="code-editor" oninput="applyCodeChanges()"></textarea>
            </div>
        </div>

        <div class="sidebar sidebar-right" id="sidebar-right">
            <h2>Свойства элемента</h2>
            <div id="editor-controls">
                <p style="color: #64748b; font-size: 13px;">Нажмите на любой элемент на холсте для его настройки</p>
            </div>
        </div>

    </div>

    <button id="exit-preview-btn" onclick="togglePreviewMode()">✕ Выйти</button>

    <div id="ai-wizard-overlay">
        <div class="ai-wizard-box">
            <h2 style="font-size:18px; margin-bottom:4px;">🤖 AI-Помощник создания сайта</h2>
            <p style="font-size:12px; color:#94a3b8; margin-bottom:16px;">Ответьте на несколько вопросов — и я соберу для вас готовый сайт из блоков и текстов.</p>

            <div class="control-group">
                <label>Название бизнеса/проекта:</label>
                <input type="text" id="ai-wizard-name" placeholder="Например: Programist-studio">
            </div>

            <div class="control-group">
                <label>Сфера деятельности:</label>
                <select id="ai-wizard-category">
                    <option value="it">💻 IT-Студия / Разработка</option>
                    <option value="restaurant">🍕 Ресторан / Доставка</option>
                    <option value="courses">🎓 Курсы / Обучение</option>
                    <option value="shop">🛒 Магазин / Товары</option>
                    <option value="beauty">💅 Салон красоты</option>
                    <option value="fitness">🏋️ Фитнес-клуб</option>
                    <option value="realestate">🏠 Недвижимость</option>
                    <option value="medical">🩺 Медицина</option>
                    <option value="travel">✈️ Путешествия</option>
                    <option value="wedding">💍 Свадьбы & Праздники</option>
                </select>
            </div>

            <div class="control-group">
                <label>Стиль оформления:</label>
                <select id="ai-wizard-style">
                    <option value="dark">🌌 Тёмный премиум</option>
                    <option value="light">☀️ Светлый минимализм</option>
                    <option value="vibrant">🌈 Яркий RGB</option>
                </select>
            </div>

            <div class="control-group">
                <label>Какие блоки включить:</label>
                <div class="ai-wizard-checks">
                    <label><input type="checkbox" id="aiw-hero" checked> Шапка + заголовок + текст</label>
                    <label><input type="checkbox" id="aiw-features" checked> Преимущества</label>
                    <label><input type="checkbox" id="aiw-pricing" checked> Тарифы / Цены</label>
                    <label><input type="checkbox" id="aiw-reviews" checked> Отзывы</label>
                    <label><input type="checkbox" id="aiw-faq" checked> FAQ</label>
                    <label><input type="checkbox" id="aiw-contact" checked> Форма заявки</label>
                </div>
            </div>

            <div style="display:flex; gap:8px; margin-top:16px;">
                <button class="action-btn" style="flex:1; background:#334155; color:#f8fafc;" onclick="closeAIWizard()">Отмена</button>
                <button class="btn-gen-ai" style="flex:1; padding:10px;" onclick="aiWizardGenerate()">✨ Сгенерировать сайт</button>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const canvasWrapper = document.getElementById('canvas-wrapper');
        const emptyMsg = document.getElementById('empty-msg');
        const editorControls = document.getElementById('editor-controls');
        const codeEditor = document.getElementById('code-editor');
        const codeContainer = document.getElementById('code-container');
        
        let selectedElement = null;
        let selectedWrapper = null;
        let elementCount = 0;
        let currentMode = 'visual';
        let currentPage = 'index';
        let draggedWrapper = null;

        let pagesData = {
            'index': { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' },
            'about': { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' },
            'services': { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' },
            'contact': { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' }
        };

        let historyStack = [];
        let historyIndex = -1;
        let isUndoRedoAction = false;

        const LOCAL_STORAGE_KEY = 'programist_studio_site_data_v6';

        const aiTextDatabase = {
            it: {
                headers: ["Разработка сайтов и ПО под ключ", "Инновационные решения для вашего бизнеса", "Увеличьте продажи с помощью IT", "Премиум веб-дизайн и веб-разработка"],
                texts: ["Создаем современные веб-решения, мобильные приложения и Telegram-боты любой сложности.", "Помогаем компаниям цифровизировать процессы и привлекать клиентов из интернета.", "Высокая скорость работы, современные технологии и гарантия качества."],
                buttons: ["Заказать проект", "Обсудить задачу", "Рассчитать стоимость", "Связаться с нами"],
                cards: ["Веб-разработка\nСоздание сайтов любой сложности от лендингов до маркетплейсов.", "Мобильные приложения\nРазработка UI/UX дизайна и сборка приложений на iOS и Android."]
            },
            restaurant: {
                headers: ["Вкуснейшие блюда авторской кухни", "Уютная атмосфера и лучшая кулинария", "Гастрономическое удовольствие каждый день", "Доставка горячей еды за 30 минут"],
                texts: ["Свежие ингредиенты, профессиональные шеф-повара и незабываемый вкус в каждом блюде.", "Забронируйте столик прямо сейчас и получите фирменный десерт в подарок!", "Быстрая доставка еды домой или в офис."],
                buttons: ["Забронировать стол", "Заказать доставку", "Посмотреть меню", "Заказать еду"],
                cards: ["Пицца Пепперони\nСочная пицца с пикантными колбасками и сыром моцарелла.", "Стейк Рибай\nНежнейшая мраморная говядина со специями."]
            },
            courses: {
                headers: ["Освойте профессию мечты с нуля", "Практические курсы от экспертов", "Получите навыки, которые приносят доход", "Станьте востребованным специалистом"],
                texts: ["80% практики, персональный ментор и помощь с трудоустройством после обучения.", "Обучение в удобном темпе без отрыва от основной работы.", "Присоединяйтесь к сообществу выпускников и начните зарабатывать уже через 3 месяца."],
                buttons: ["Записаться на курс", "Начать бесплатно", "Получить программу", "Учиться сейчас"],
                cards: ["Курс Веб-Дизайн\nОсвойте Figma и основы интерфейсов за 2 месяца.", "Курс Python-Разработчик\nИзучите самый популярный язык программирования."]
            },
            shop: {
                headers: ["Распродажа сезона — Скидки до 50%", "Премиум качество по лучшим ценам", "Новая коллекция уже в продаже", "Все необходимое в одном месте"],
                texts: ["Быстрая доставка по всей стране. Гарантия качества на всю продукцию.", "Оформите заказ сегодня и получите подарок в каждом комплекте.", "Удобная оплата при получении или картой на сайте."],
                buttons: ["В каталог", "Купить со скидкой", "Оформить заказ", "Перейти в магазин"],
                cards: ["Беспроводные наушники\nЧистый звук и мощный бас. До 24 часов работы.", "Смарт-часы 2026\nСпортивные функции и мониторинг здоровья."]
            },
            beauty: {
                headers: ["Красота и уход, которым доверяют", "Преображение начинается здесь", "Салон красоты премиум-класса", "Ваша лучшая версия — уже сегодня"],
                texts: ["Профессиональные мастера, премиальная косметика и индивидуальный подход к каждому клиенту.", "Запишитесь на процедуру и получите скидку на первое посещение.", "Более 10 лет создаём безупречный образ для наших клиентов."],
                buttons: ["Записаться на процедуру", "Выбрать мастера", "Узнать цены", "Забронировать время"],
                cards: ["Маникюр и педикюр\nАккуратный уход за руками и ногами с долговременным покрытием.", "Стрижка и укладка\nСоздание образа с учётом типа лица и структуры волос."]
            },
            fitness: {
                headers: ["Тренируйтесь с удовольствием и результатом", "Фитнес-клуб мирового уровня", "Ваша форма мечты — реальность", "Спорт, который меняет жизнь"],
                texts: ["Современное оборудование, персональные тренеры и групповые программы для любого уровня.", "Первое занятие — бесплатно! Приходите и убедитесь сами.", "Гибкие абонементы и удобное расписание для вашего образа жизни."],
                buttons: ["Записаться на тренировку", "Купить абонемент", "Пробное занятие", "Выбрать программу"],
                cards: ["Персональные тренировки\nИндивидуальная программа с личным тренером.", "Групповые занятия\nЙога, кроссфит, бокс и другие направления."]
            },
            realestate: {
                headers: ["Недвижимость вашей мечты", "Квартиры и дома от надёжного застройщика", "Инвестируйте в качественную недвижимость", "Найдите свой идеальный дом"],
                texts: ["Широкий выбор объектов, юридическое сопровождение сделки и выгодные условия рассрочки.", "Более 500 довольных клиентов и безупречная репутация на рынке.", "Помогаем подобрать недвижимость под любой бюджет и цели."],
                buttons: ["Смотреть объекты", "Записаться на просмотр", "Получить консультацию", "Узнать цену"],
                cards: ["3-комнатная квартира\nСовременная планировка, развитая инфраструктура района.", "Загородный дом\nПросторный дом с участком в экологически чистом районе."]
            },
            medical: {
                headers: ["Ваше здоровье — наш приоритет", "Медицинский центр нового поколения", "Качественная диагностика и лечение", "Забота о здоровье каждый день"],
                texts: ["Опытные врачи, современное оборудование и индивидуальный подход к каждому пациенту.", "Запишитесь на приём онлайн в удобное для вас время.", "Полный спектр медицинских услуг под одной крышей."],
                buttons: ["Записаться на приём", "Пройти диагностику", "Получить консультацию", "Выбрать врача"],
                cards: ["Терапевт\nОбщая диагностика и консультация по вопросам здоровья.", "Стоматология\nЛечение и профилактика заболеваний зубов и дёсен."]
            },
            travel: {
                headers: ["Путешествия вашей мечты", "Откройте мир вместе с нами", "Лучшие туры по доступным ценам", "Незабываемый отдых начинается здесь"],
                texts: ["Индивидуальные и групповые туры, помощь с визами и полное сопровождение поездки.", "Забронируйте тур сейчас и получите скидку на раннее бронирование.", "Более 50 направлений по всему миру для любого бюджета."],
                buttons: ["Выбрать тур", "Забронировать поездку", "Получить консультацию", "Смотреть направления"],
                cards: ["Тур на Бали\n7 ночей на берегу океана, завтраки включены.", "Экскурсия по Европе\nПосещение 5 стран за 10 дней с русскоговорящим гидом."]
            },
            wedding: {
                headers: ["Свадьба вашей мечты", "Организация праздников под ключ", "Незабываемый день для двоих", "Создаём идеальные торжества"],
                texts: ["Полная организация свадьбы: от декора до банкета, с вниманием к каждой детали.", "Индивидуальный подход и учёт всех пожеланий молодожёнов.", "Более 200 свадеб организовано с любовью и заботой."],
                buttons: ["Заказать организацию", "Получить смету", "Обсудить детали", "Записаться на консультацию"],
                cards: ["Оформление зала\nСтильный декор в выбранной цветовой гамме и стиле.", "Выездная церемония\nОрганизация регистрации на природе или в уникальной локации."]
            }
        };

        const aiPalettes = [
            { bg: '#0f172a', cardBg: '#1e293b', text: '#f8fafc', accent: '#38bdf8', btnText: '#0f172a' },
            { bg: '#ffffff', cardBg: '#f8fafc', text: '#0f172a', accent: '#0284c7', btnText: '#ffffff' },
            { bg: '#090d16', cardBg: '#131c2e', text: '#f1f5f9', accent: '#a855f7', btnText: '#ffffff' },
            { bg: '#052e16', cardBg: '#14532d', text: '#f0fdf4', accent: '#22c55e', btnText: '#052e16' },
            { bg: '#18181b', cardBg: '#27272a', text: '#fafafa', accent: '#f97316', btnText: '#ffffff' },
            { bg: '#fff7ed', cardBg: '#ffedd5', text: '#431407', accent: '#ea580c', btnText: '#ffffff' },
            { bg: '#2e1065', cardBg: '#3b0764', text: '#faf5ff', accent: '#c084fc', btnText: '#0f172a' },
            { bg: '#030712', cardBg: '#111827', text: '#f9fafb', accent: '#ec4899', btnText: '#ffffff' },
            { bg: '#f0fdf4', cardBg: '#dcfce7', text: '#14532d', accent: '#16a34a', btnText: '#ffffff' },
            { bg: '#000000', cardBg: '#121212', text: '#00ffcc', accent: '#ff0055', btnText: '#ffffff' },
            { bg: '#1e1b4b', cardBg: '#312e81', text: '#e0e7ff', accent: '#6366f1', btnText: '#ffffff' },
            { bg: '#fef2f2', cardBg: '#ffe4e6', text: '#881337', accent: '#e11d48', btnText: '#ffffff' }
        ];

        function clearSelection() {
            document.querySelectorAll('.canvas-item').forEach(item => item.classList.remove('selected'));
            selectedElement = null;
            selectedWrapper = null;
            if (editorControls) {
                editorControls.innerHTML = '<p style="color: #64748b; font-size: 13px;">Нажмите на любой элемент на холсте для его настройки</p>';
            }
        }

        document.addEventListener('click', (e) => {
            if (!e.target.closest('.canvas-item') && !e.target.closest('.sidebar') && !e.target.closest('.top-bar') && !e.target.closest('.mobile-tabs')) {
                clearSelection();
            }
        });

        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                clearSelection();
            }
        });

        function setZoom(scale) {
            canvasWrapper.style.transform = `scale(${scale})`;
            document.querySelectorAll('.zoom-controls .toggle-btn').forEach(btn => btn.classList.remove('active'));
            if (window.event && window.event.target) window.event.target.classList.add('active');
        }

        function changeCanvasWidth(val) { canvas.style.maxWidth = val; }
        function changeCanvasHeight(val) { canvas.style.minHeight = val; }

        function moveSelectedUp() {
            if (selectedWrapper && selectedWrapper.previousElementSibling && selectedWrapper.previousElementSibling.id !== 'empty-msg') {
                canvas.insertBefore(selectedWrapper, selectedWrapper.previousElementSibling);
                saveHistoryState();
            }
        }

        function moveSelectedDown() {
            if (selectedWrapper && selectedWrapper.nextElementSibling) {
                canvas.insertBefore(selectedWrapper.nextElementSibling, selectedWrapper);
                saveHistoryState();
            }
        }

        function duplicateSelected() {
            if (selectedWrapper) {
                elementCount++;
                const clone = selectedWrapper.cloneNode(true);
                clone.id = 'item-' + elementCount;
                canvas.insertBefore(clone, selectedWrapper.nextElementSibling);
                rebindCanvasEvents();
                selectElement(clone, clone.firstElementChild, clone.firstElementChild ? clone.firstElementChild.tagName.toLowerCase() : 'block');
                saveHistoryState();
            }
        }

        function switchPage(pageKey) {
            pagesData[currentPage] = {
                html: canvas.innerHTML,
                bg: canvas.style.backgroundColor || '#ffffff',
                padding: canvas.style.padding || '20px',
                font: canvas.style.fontFamily || 'Inter',
                theme: document.getElementById('page-theme').value || 'light'
            };

            currentPage = pageKey;
            const p = pagesData[currentPage] || { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' };

            canvas.innerHTML = p.html || '';
            canvas.style.backgroundColor = p.bg;
            canvas.style.padding = p.padding;
            canvas.style.fontFamily = p.font;
            document.getElementById('page-bg-color').value = rgbToHex(p.bg);
            document.getElementById('global-font').value = p.font;
            document.getElementById('page-theme').value = p.theme;

            clearSelection();
            rebindCanvasEvents();
            saveHistoryState();
        }

        function addNewPage() {
            const name = prompt("Введите имя новой страницы (например, blog):");
            if (name) {
                const key = name.toLowerCase().replace(/[^a-z0-9]/g, '');
                if (key && !pagesData[key]) {
                    pagesData[key] = { html: '', bg: '#ffffff', padding: '20px', font: 'Inter', theme: 'light' };
                    const select = document.getElementById('pages-select');
                    const opt = document.createElement('option');
                    opt.value = key;
                    opt.innerText = name + ' (' + key + ')';
                    select.appendChild(opt);
                    select.value = key;
                    switchPage(key);
                }
            }
        }

        function makeDraggable(el) {
            let posX = 0, posY = 0, mouseX = 0, mouseY = 0;
            el.onmousedown = dragMouseDown;
            el.ontouchstart = dragTouchStart;

            function dragMouseDown(e) {
                e.preventDefault();
                mouseX = e.clientX;
                mouseY = e.clientY;
                document.onmouseup = closeDragElement;
                document.onmousemove = elementDrag;
            }

            function elementDrag(e) {
                e.preventDefault();
                posX = mouseX - e.clientX;
                posY = mouseY - e.clientY;
                mouseX = e.clientX;
                mouseY = e.clientY;
                el.style.top = (el.offsetTop - posY) + "px";
                el.style.left = (el.offsetLeft - posX) + "px";
            }

            function closeDragElement() {
                document.onmouseup = null;
                document.onmousemove = null;
                saveHistoryState();
            }

            function dragTouchStart(e) {
                const touch = e.touches[0];
                mouseX = touch.clientX;
                mouseY = touch.clientY;
                document.ontouchend = closeTouchDrag;
                document.ontouchmove = touchDrag;
            }

            function touchDrag(e) {
                const touch = e.touches[0];
                posX = mouseX - touch.clientX;
                posY = mouseY - touch.clientY;
                mouseX = touch.clientX;
                mouseY = touch.clientY;
                el.style.top = (el.offsetTop - posY) + "px";
                el.style.left = (el.offsetLeft - posX) + "px";
            }

            function closeTouchDrag() {
                document.ontouchend = null;
                document.ontouchmove = null;
                saveHistoryState();
            }
        }

        function saveToLocalStorage() {
            pagesData[currentPage] = {
                html: canvas.innerHTML,
                bg: canvas.style.backgroundColor || '#ffffff',
                padding: canvas.style.padding || '20px',
                font: canvas.style.fontFamily || 'Inter',
                theme: document.getElementById('page-theme').value || 'light'
            };

            const dataToSave = {
                pagesData: pagesData,
                currentPage: currentPage,
                elementCount: elementCount
            };
            localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(dataToSave));
            
            const statusText = document.getElementById('save-status-text');
            if (statusText) {
                statusText.innerText = 'Сохранено';
                setTimeout(() => { statusText.innerText = 'Автосохранение'; }, 1500);
            }
        }

        function loadFromLocalStorage() {
            const savedData = localStorage.getItem(LOCAL_STORAGE_KEY);
            if (savedData) {
                try {
                    const parsed = JSON.parse(savedData);
                    if (parsed.pagesData) {
                        pagesData = parsed.pagesData;
                        currentPage = parsed.currentPage || 'index';
                        elementCount = parsed.elementCount || 0;

                        const select = document.getElementById('pages-select');
                        select.innerHTML = '';
                        Object.keys(pagesData).forEach(pKey => {
                            const opt = document.createElement('option');
                            opt.value = pKey;
                            opt.innerText = pKey;
                            select.appendChild(opt);
                        });
                        select.value = currentPage;

                        const p = pagesData[currentPage];
                        canvas.innerHTML = p.html || '';
                        canvas.style.backgroundColor = p.bg || '#ffffff';
                        canvas.style.padding = p.padding || '20px';
                        canvas.style.fontFamily = p.font || 'Inter';

                        document.getElementById('page-bg-color').value = rgbToHex(p.bg) || '#ffffff';
                        document.getElementById('page-padding').value = parseInt(p.padding) || 20;
                        document.getElementById('global-font').value = p.font || 'Inter';
                        document.getElementById('page-theme').value = p.theme || 'light';

                        if (p.theme === 'dark') canvas.classList.add('dark-theme');

                        rebindCanvasEvents();
                        return true;
                    }
                } catch (e) {
                    console.error("Ошибка при загрузке данных:", e);
                }
            }
            return false;
        }

        function resetLocalStorage() {
            if (confirm("Вы уверены, что хотите сбросить сохраненный проект? Вся работа будет удалена.")) {
                localStorage.removeItem(LOCAL_STORAGE_KEY);
                clearCanvas();
            }
        }

        function generateAIPalette() {
            const randomPalette = aiPalettes[Math.floor(Math.random() * aiPalettes.length)];
            
            canvas.style.backgroundColor = randomPalette.bg;
            document.getElementById('page-bg-color').value = randomPalette.bg;

            const wrappers = canvas.querySelectorAll('.canvas-item');
            wrappers.forEach(w => {
                const el = w.firstElementChild;
                if (!el) return;

                const tag = el.tagName.toLowerCase();
                if (['h1', 'h2', 'h3', 'p', 'strong', 'span'].includes(tag)) {
                    if (!el.classList.contains('animated-site-title') && !el.classList.contains('rgb-text-glow')) {
                        el.style.color = randomPalette.text;
                    }
                } else if (tag === 'a' || tag === 'button') {
                    if (!el.classList.contains('site-theme-toggle-btn')) {
                        el.style.backgroundColor = randomPalette.accent;
                        el.style.color = randomPalette.btnText;
                    }
                } else if (['div', 'form', 'nav', 'footer'].includes(tag)) {
                    el.style.backgroundColor = randomPalette.cardBg;
                    el.style.color = randomPalette.text;
                }
            });

            saveHistoryState();
        }

        function enhanceCanvasDesignAI() {
            const wrappers = canvas.querySelectorAll('.canvas-item');
            const shadowStyles = [
                '0 10px 25px rgba(0,0,0,0.10)',
                '0 12px 30px rgba(56,189,248,0.15)',
                '0 12px 30px rgba(168,85,247,0.15)',
                '0 12px 30px rgba(236,72,153,0.12)'
            ];
            wrappers.forEach(w => {
                const el = w.firstElementChild;
                if (!el) return;
                el.style.borderRadius = (Math.floor(Math.random() * 10) + 10) + 'px';
                el.style.boxShadow = shadowStyles[Math.floor(Math.random() * shadowStyles.length)];
                el.style.transition = 'all 0.3s ease';
            });
            saveHistoryState();
        }

        function generateElementDesignAI() {
            if (!selectedElement) {
                alert("Сначала выберите блок на холсте!");
                return;
            }
            const gradients = [
                'linear-gradient(135deg, #38bdf8, #6366f1)',
                'linear-gradient(135deg, #a855f7, #ec4899)',
                'linear-gradient(135deg, #f59e0b, #ef4444)',
                'linear-gradient(135deg, #10b981, #14b8a6)',
                'linear-gradient(135deg, #0ea5e9, #22d3ee)',
                'linear-gradient(135deg, #ec4899, #f43f5e)',
                'linear-gradient(135deg, #6366f1, #a855f7, #ec4899)',
                'linear-gradient(135deg, #f97316, #f59e0b)'
            ];
            const colors = ['#38bdf8', '#a855f7', '#ec4899', '#10b981', '#f59e0b', '#6366f1', '#14b8a6', '#f43f5e'];
            const randomGradient = gradients[Math.floor(Math.random() * gradients.length)];
            const randomColor = colors[Math.floor(Math.random() * colors.length)];
            const randomRadius = Math.floor(Math.random() * 25) + 'px';
            const randomShadowSize = Math.floor(Math.random() * 20) + 15;

            selectedElement.style.borderRadius = randomRadius;
            selectedElement.style.transition = 'all 0.3s ease';

            const tag = selectedElement.tagName.toLowerCase();
            if (tag === 'a' || tag === 'button') {
                selectedElement.style.background = randomGradient;
                selectedElement.style.color = '#ffffff';
                selectedElement.style.border = 'none';
                selectedElement.style.boxShadow = `0 6px ${randomShadowSize}px ${randomColor}66`;
            } else {
                const useGradientBg = Math.random() > 0.5;
                if (useGradientBg) {
                    selectedElement.style.background = randomGradient;
                    selectedElement.style.color = '#ffffff';
                    selectedElement.style.border = 'none';
                } else {
                    selectedElement.style.borderColor = randomColor;
                    selectedElement.style.borderWidth = '2px';
                    selectedElement.style.borderStyle = 'solid';
                }
                selectedElement.style.boxShadow = `0 8px ${randomShadowSize}px ${randomColor}44`;
            }
            saveHistoryState();
        }

        function applyColorTheme(theme) {
            if (!selectedElement) return;
            const el = selectedElement;
            const rgbThemes = ['rgb-theme-fire', 'rgb-theme-ocean', 'rgb-theme-neon', 'rgb-theme-rainbow', 'rgb-theme-emerald'];
            const titleThemes = ['title-theme-fire', 'title-theme-ocean', 'title-theme-neon', 'title-theme-rainbow', 'title-theme-emerald'];
            rgbThemes.forEach(c => el.classList.remove(c));
            titleThemes.forEach(c => el.classList.remove(c));

            if (el.classList.contains('rgb-card') || el.classList.contains('rgb-text-glow')) {
                el.classList.add('rgb-theme-' + theme);
            }
            if (el.classList.contains('animated-site-title')) {
                el.classList.add('title-theme-' + theme);
            }
            saveHistoryState();
        }

        function applyRGBEffectToSelected() {
            if (!selectedElement) {
                alert("Сначала выберите элемент на холсте!");
                return;
            }
            const isText = ['h1', 'h2', 'h3', 'p', 'span', 'strong'].includes(selectedElement.tagName.toLowerCase());
            if (isText) {
                selectedElement.classList.toggle('rgb-text-glow');
            } else {
                selectedElement.classList.toggle('rgb-card');
            }
            saveHistoryState();
        }

        function generateAIText(topic, elType) {
            const category = aiTextDatabase[topic] || aiTextDatabase.it;
            let options = category.headers;

            if (elType === 'button') options = category.buttons;
            else if (elType === 'text') options = category.texts;
            else if (elType === 'card') options = category.cards;

            const randomText = options[Math.floor(Math.random() * options.length)];

            if (selectedElement) {
                if (elType === 'card') {
                    const h3 = selectedElement.querySelector('h3');
                    const p = selectedElement.querySelector('p');
                    const parts = randomText.split('\n');
                    if (h3) h3.innerText = parts[0];
                    if (p) p.innerText = parts[1];
                } else {
                    selectedElement.innerText = randomText;
                }
                const propInput = document.getElementById('prop-text');
                if (propInput) propInput.value = randomText;
                saveHistoryState();
            }
        }

        function saveHistoryState() {
            if (isUndoRedoAction) return;
            if (historyIndex < historyStack.length - 1) {
                historyStack = historyStack.slice(0, historyIndex + 1);
            }
            historyStack.push(canvas.innerHTML);
            historyIndex++;
            updateHistoryButtons();
            saveToLocalStorage();
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
                clearSelection();
                rebindCanvasEvents();
                updateHistoryButtons();
                saveToLocalStorage();
                isUndoRedoAction = false;
            }
        }

        function redo() {
            if (historyIndex < historyStack.length - 1) {
                isUndoRedoAction = true;
                historyIndex++;
                canvas.innerHTML = historyStack[historyIndex];
                clearSelection();
                rebindCanvasEvents();
                updateHistoryButtons();
                saveToLocalStorage();
                isUndoRedoAction = false;
            }
        }

        function switchMobileTab(tab) {
            document.getElementById('mtab-elements').classList.toggle('active', tab === 'elements');
            document.getElementById('mtab-canvas').classList.toggle('active', tab === 'canvas');
            document.getElementById('mtab-props').classList.toggle('active', tab === 'props');

            const sLeft = document.getElementById('sidebar-left');
            const sRight = document.getElementById('sidebar-right');
            const wArea = document.getElementById('workspace-area');

            sLeft.classList.remove('active-tab');
            sRight.classList.remove('active-tab');
            wArea.classList.remove('hidden-tab');

            if (tab === 'elements') {
                sLeft.classList.add('active-tab');
                wArea.classList.add('hidden-tab');
            } else if (tab === 'props') {
                sRight.classList.add('active-tab');
                wArea.classList.add('hidden-tab');
            }
        }

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

                if (wrapper.classList.contains('is-draggable')) {
                    makeDraggable(wrapper);
                } else {
                    wrapper.setAttribute('draggable', 'true');
                    
                    wrapper.ondragstart = (e) => {
                        draggedWrapper = wrapper;
                        e.dataTransfer.setData('text/plain', wrapper.id);
                        setTimeout(() => wrapper.style.opacity = '0.4', 0);
                    };

                    wrapper.ondragend = () => {
                        wrapper.style.opacity = '1';
                        canvas.querySelectorAll('.canvas-item').forEach(i => i.classList.remove('drag-over'));
                        draggedWrapper = null;
                        saveHistoryState();
                    };

                    wrapper.ondragover = (e) => {
                        e.preventDefault();
                        if (draggedWrapper && draggedWrapper !== wrapper) {
                            wrapper.classList.add('drag-over');
                        }
                    };

                    wrapper.ondragleave = () => {
                        wrapper.classList.remove('drag-over');
                    };

                    wrapper.ondrop = (e) => {
                        e.preventDefault();
                        wrapper.classList.remove('drag-over');
                        if (draggedWrapper && draggedWrapper !== wrapper) {
                            const children = Array.from(canvas.children);
                            const draggedIndex = children.indexOf(draggedWrapper);
                            const targetIndex = children.indexOf(wrapper);

                            if (draggedIndex < targetIndex) {
                                canvas.insertBefore(draggedWrapper, wrapper.nextElementSibling);
                            } else {
                                canvas.insertBefore(draggedWrapper, wrapper);
                            }
                        }
                    };
                }

                if (deleteBtn) {
                    deleteBtn.onclick = (e) => {
                        e.stopPropagation();
                        wrapper.remove();
                        if (canvas.querySelectorAll('.canvas-item').length === 0 && emptyMsg) {
                            emptyMsg.style.display = 'block';
                        }
                        clearSelection();
                        saveHistoryState();
                    };
                }

                wrapper.onclick = (e) => {
                    e.stopPropagation();
                    let type = 'block';
                    if (wrapper.classList.contains('is-draggable')) type = 'draggable-icon';
                    else if (targetEl) type = targetEl.tagName.toLowerCase();
                    selectElement(wrapper, targetEl, type);
                };
            });

            canvas.querySelectorAll('[contenteditable="true"]').forEach(el => {
                el.onblur = () => saveHistoryState();
            });
        }

        window.onload = () => {
            const loaded = loadFromLocalStorage();
            if (!loaded) {
                saveHistoryState();
            } else {
                updateHistoryButtons();
            }
        };

        function switchView(mode) {
            currentMode = mode;
            document.getElementById('btn-view-visual').classList.toggle('active', mode === 'visual');
            document.getElementById('btn-view-code').classList.toggle('active', mode === 'code');

            if (mode === 'code') {
                updateCodeEditorFromCanvas();
                canvasWrapper.style.display = 'none';
                codeContainer.style.display = 'flex';
            } else {
                canvasWrapper.style.display = 'flex';
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
            clearSelection();
            document.body.classList.toggle('preview-mode');
        }

        function changeGlobalFont(fontFamily) {
            canvas.style.fontFamily = fontFamily;
            saveHistoryState();
        }

        function changeCanvasTheme(theme) {
            if (theme === 'dark') {
                canvas.classList.add('dark-theme');
                canvas.style.backgroundColor = '#0d1117';
                canvas.style.color = '#ffffff';
                document.getElementById('page-bg-color').value = '#0d1117';
            } else {
                canvas.classList.remove('dark-theme');
                canvas.style.backgroundColor = '#ffffff';
                canvas.style.color = '#1e293b';
                document.getElementById('page-bg-color').value = '#ffffff';
            }
            saveHistoryState();
        }

        function toggleCreatedSiteTheme() {
            const isDark = canvas.classList.toggle('dark-theme');
            if (isDark) {
                canvas.style.backgroundColor = '#0d1117';
                canvas.style.color = '#ffffff';
                document.getElementById('page-bg-color').value = '#0d1117';
                document.getElementById('page-theme').value = 'dark';
            } else {
                canvas.style.backgroundColor = '#ffffff';
                canvas.style.color = '#1e293b';
                document.getElementById('page-bg-color').value = '#ffffff';
                document.getElementById('page-theme').value = 'light';
            }
            saveHistoryState();
        }

        function changeAudioSource(selectEl) {
            const player = selectEl.parentElement.querySelector('audio');
            if (player) {
                player.src = selectEl.value;
                player.play();
            }
        }

        function changeCanvasBg(color) { 
            canvas.style.backgroundColor = color; 
            saveHistoryState();
        }

        function changeCanvasPadding(val) { 
            canvas.style.padding = val + 'px'; 
            saveHistoryState();
        }

        function clearCanvas() {
            if (confirm("Очистить весь холст текущей страницы?")) {
                canvas.innerHTML = '';
                if (emptyMsg) {
                    emptyMsg.style.display = 'block';
                    canvas.appendChild(emptyMsg);
                }
                clearSelection();
                saveHistoryState();
            }
        }

        function openAIWizard() {
            document.getElementById('ai-wizard-overlay').style.display = 'flex';
        }

        function closeAIWizard() {
            document.getElementById('ai-wizard-overlay').style.display = 'none';
        }

        function aiWizardGenerate() {
            const name = document.getElementById('ai-wizard-name').value.trim() || 'Ваш бизнес';
            const category = document.getElementById('ai-wizard-category').value;
            const style = document.getElementById('ai-wizard-style').value;
            const data = aiTextDatabase[category] || aiTextDatabase.it;

            if (canvas.querySelectorAll('.canvas-item').length > 0) {
                if (!confirm('Текущий холст будет очищен и заменён сгенерированным сайтом. Продолжить?')) return;
            }

            canvas.innerHTML = '';
            if (emptyMsg) emptyMsg.style.display = 'none';

            addElement('navbar');
            if (document.getElementById('aiw-hero').checked) {
                addElement('site-title');
                addElement('header');
                addElement('text');
            }
            if (document.getElementById('aiw-features').checked) addElement('features');
            if (document.getElementById('aiw-pricing').checked) addElement('pricing');
            if (document.getElementById('aiw-reviews').checked) addElement('star-reviews');
            if (document.getElementById('aiw-faq').checked) addElement('faq');
            if (document.getElementById('aiw-contact').checked) addElement('form');
            addElement('footer');

            canvas.querySelectorAll('.canvas-item').forEach(wrapper => {
                const el = wrapper.firstElementChild;
                if (!el) return;

                const navTitle = el.querySelector ? el.querySelector('.animated-site-title') : null;
                if (navTitle) navTitle.innerText = name;

                if (el.classList && el.classList.contains('animated-site-title')) {
                    el.innerText = name;
                } else if (el.tagName === 'H1') {
                    el.innerText = data.headers[Math.floor(Math.random() * data.headers.length)];
                } else if (el.tagName === 'P') {
                    el.innerText = data.texts[Math.floor(Math.random() * data.texts.length)];
                } else if (el.tagName === 'FOOTER') {
                    el.innerText = `© 2026 ${name}. Все права защищены.`;
                }
            });

            let palette;
            if (style === 'dark') palette = aiPalettes[0];
            else if (style === 'vibrant') palette = aiPalettes[9];
            else palette = aiPalettes[1];

            canvas.style.backgroundColor = palette.bg;
            canvas.style.color = palette.text;
            document.getElementById('page-bg-color').value = palette.bg;
            canvas.querySelectorAll('.dark-card').forEach(el => {
                el.style.backgroundColor = palette.cardBg;
                el.style.color = palette.text;
                el.style.borderColor = palette.accent;
            });

            closeAIWizard();
            clearSelection();
            if (window.innerWidth <= 1024) switchMobileTab('canvas');
            saveHistoryState();
        }

        function loadPreset(presetName) {
            canvas.innerHTML = '';
            if (emptyMsg) emptyMsg.style.display = 'none';

            if (presetName === 'landing') {
                addElement('promo-banner');
                addElement('site-theme-toggle');
                addElement('navbar');
                addElement('site-title');
                addElement('image-slider');
                addElement('countdown');
                addElement('features');
                addElement('pricing');
                addElement('star-reviews');
                addElement('form');
                addElement('footer');
            } else if (presetName === 'portfolio') {
                addElement('site-theme-toggle');
                addElement('navbar');
                addElement('header');
                addElement('text');
                addElement('stats');
                addElement('gallery2');
                addElement('star-reviews');
                addElement('social-share');
                addElement('floating-messengers');
                addElement('footer');
            } else if (presetName === 'shop') {
                addElement('promo-banner');
                addElement('site-theme-toggle');
                addElement('navbar');
                addElement('header');
                addElement('grid3');
                addElement('pricing');
                addElement('star-reviews');
                addElement('faq');
                addElement('form');
                addElement('footer');
            } else if (presetName === 'saas') {
                addElement('promo-banner');
                addElement('navbar');
                addElement('header');
                addElement('text');
                addElement('button');
                addElement('video');
                addElement('features');
                addElement('pricing');
                addElement('faq');
                addElement('footer');
            } else if (presetName === 'blog') {
                addElement('navbar');
                addElement('header');
                addElement('grid3');
                addElement('audio');
                addElement('divider');
                addElement('star-reviews');
                addElement('social-share');
                addElement('footer');
            } else if (presetName === 'event') {
                addElement('promo-banner');
                addElement('site-title');
                addElement('countdown');
                addElement('grid2');
                addElement('modal-form');
                addElement('map');
                addElement('footer');
            } else if (presetName === 'education') {
                addElement('navbar');
                addElement('header');
                addElement('video');
                addElement('features');
                addElement('stats');
                addElement('pricing');
                addElement('faq');
                addElement('form');
                addElement('footer');
            } else if (presetName === 'restaurant') {
                addElement('promo-banner');
                addElement('navbar');
                addElement('site-title');
                addElement('image-slider');
                addElement('grid3');
                addElement('modal-form');
                addElement('star-reviews');
                addElement('map');
                addElement('footer');
            } else if (presetName === 'corporate') {
                addElement('navbar');
                addElement('header');
                addElement('features');
                addElement('stats');
                addElement('grid2');
                addElement('form');
                addElement('footer');
            } else if (['beauty', 'fitness', 'realestate', 'medical', 'travel', 'wedding'].includes(presetName)) {
                addElement('navbar');
                addElement('site-title');
                addElement('hero-split');
                addElement('logos-strip');
                addElement('features');
                addElement('team');
                addElement('timeline');
                addElement('pricing');
                addElement('star-reviews');
                addElement('faq');
                addElement('newsletter');
                addElement('cta-banner');
                addElement('form');
                addElement('footer');

                const data = aiTextDatabase[presetName] || aiTextDatabase.it;
                canvas.querySelectorAll('.canvas-item').forEach(wrapper => {
                    const el = wrapper.firstElementChild;
                    if (!el) return;
                    if (el.tagName === 'H1' && !el.classList.contains('animated-site-title')) {
                        el.innerText = data.headers[Math.floor(Math.random() * data.headers.length)];
                    } else if (el.tagName === 'H2') {
                        el.innerText = data.headers[Math.floor(Math.random() * data.headers.length)];
                    }
                });
            }

            clearSelection();
            if (window.innerWidth <= 1024) switchMobileTab('canvas');
            saveHistoryState();
        }

        function addElement(type) {
            if (emptyMsg) emptyMsg.style.display = 'none';

            elementCount++;
            const wrapper = document.createElement('div');
            wrapper.className = 'canvas-item';
            wrapper.id = 'item-' + elementCount;

            let el;
            if (type === 'draggable-icon') {
                wrapper.classList.add('is-draggable');
                wrapper.style.top = '50px';
                wrapper.style.left = '50px';
                el = document.createElement('div');
                el.className = 'icon-container';
                el.style.fontSize = '32px';
                el.style.cursor = 'grab';
                el.innerText = '🚀';
                makeDraggable(wrapper);
            } else if (type === 'promo-banner') {
                el = document.createElement('div');
                el.className = 'rgb-card';
                el.style.background = 'linear-gradient(90deg, #38bdf8, #818cf8)';
                el.style.color = '#0f172a';
                el.style.padding = '8px 15px';
                el.style.textAlign = 'center';
                el.style.fontWeight = 'bold';
                el.style.borderRadius = '6px';
                el.style.fontSize = '12px';
                el.innerText = '🔥 RGB АКЦИЯ! Скидка 20% на все услуги до конца недели!';
            } else if (type === 'image-slider') {
                el = document.createElement('div');
                el.style.position = 'relative';
                el.style.borderRadius = '8px';
                el.style.overflow = 'hidden';
                el.style.backgroundColor = '#000';
                el.innerHTML = `
                    <div style="display:flex; transition:transform 0.5s ease;">
                        <img src="https://via.placeholder.com/800x300/38bdf8/ffffff?text=Слайд+1" style="width:100%; flex-shrink:0;">
                    </div>
                    <div style="position:absolute; bottom:10px; width:100%; text-align:center;">
                        <span style="display:inline-block; width:8px; height:8px; background:white; border-radius:50%; margin:0 3px;"></span>
                        <span style="display:inline-block; width:8px; height:8px; background:rgba(255,255,255,0.5); border-radius:50%; margin:0 3px;"></span>
                    </div>
                `;
            } else if (type === 'popup-btn') {
                el = document.createElement('div');
                el.style.textAlign = 'center';
                el.innerHTML = `
                    <button class="anim-pulse" onclick="alert('Пример работы интерактива!')" style="padding:10px 20px; background:#a855f7; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer;">
                        🪟 Открыть всплывающее окно
                    </button>
                `;
            } else if (type === 'modal-form') {
                el = document.createElement('div');
                el.style.textAlign = 'center';
                el.innerHTML = `
                    <button onclick="document.getElementById('demo-modal').style.display='flex'" style="padding:12px 24px; background:linear-gradient(135deg,#10b981,#059669); color:white; border:none; border-radius:8px; font-weight:bold; cursor:pointer;">
                        📋 Быстрая Заявка (Модальное окно)
                    </button>
                    <div id="demo-modal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.6); z-index:999; justify-content:center; align-items:center;">
                        <div style="background:#fff; padding:20px; border-radius:10px; max-width:320px; width:90%; color:#0f172a; position:relative;">
                            <span onclick="this.parentElement.parentElement.style.display='none'" style="position:absolute; right:10px; top:5px; cursor:pointer; font-size:18px;">✕</span>
                            <h3 style="margin-bottom:10px;">Заказать звонок</h3>
                            <input type="text" placeholder="Ваше Имя" style="width:100%; padding:8px; margin-bottom:8px; border:1px solid #ccc; border-radius:4px;">
                            <input type="text" placeholder="Телефон" style="width:100%; padding:8px; margin-bottom:8px; border:1px solid #ccc; border-radius:4px;">
                            <button onclick="alert('Спасибо за заявку!'); document.getElementById('demo-modal').style.display='none'" style="width:100%; padding:8px; background:#10b981; color:white; border:none; border-radius:4px; font-weight:bold;">Отправить</button>
                        </div>
                    </div>
                `;
            } else if (type === 'map') {
                el = document.createElement('div');
                el.style.width = '100%';
                el.style.height = '200px';
                el.style.backgroundColor = '#e2e8f0';
                el.style.borderRadius = '8px';
                el.style.display = 'flex';
                el.style.alignItems = 'center';
                el.style.justifyContent = 'center';
                el.style.color = '#64748b';
                el.style.fontWeight = 'bold';
                el.innerText = '📍 Интерактивная Карта (Google / Яндекс Maps)';
            } else if (type === 'video') {
                el = document.createElement('div');
                el.style.position = 'relative';
                el.style.paddingBottom = '56.25%';
                el.style.height = '0';
                el.style.overflow = 'hidden';
                el.style.borderRadius = '8px';
                el.innerHTML = `<iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" style="position:absolute; top:0; left:0; width:100%; height:100%; border:0;" allowfullscreen></iframe>`;
            } else if (type === 'audio') {
                el = document.createElement('div');
                el.style.padding = '15px';
                el.style.background = '#1e293b';
                el.style.borderRadius = '8px';
                el.style.textAlign = 'center';
                el.className = 'dark-card';
                el.innerHTML = `
                    <label style="display:block; font-size:12px; color:#38bdf8; margin-bottom:6px; font-weight:bold;">🎵 Выберите аудиозапись:</label>
                    <select onchange="changeAudioSource(this)" style="width:100%; max-width:400px; padding:6px; background:#0f172a; color:#fff; border:1px solid #334155; border-radius:6px; margin-bottom:10px; font-size:12px;">
                        <option value="https://www.w3schools.com/html/horse.mp3">🐴 Лошадь (Звук)</option>
                        <option value="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">🎶 Мелодия 1 (SoundHelix)</option>
                        <option value="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3">🎶 Мелодия 2 (SoundHelix)</option>
                    </select>
                    <audio controls style="width:100%; max-width:400px; display:block; margin:0 auto;">
                        <source src="https://www.w3schools.com/html/horse.mp3" type="audio/mpeg">
                    </audio>
                `;
            } else if (type === 'site-theme-toggle') {
                el = document.createElement('div');
                el.style.display = 'flex';
                el.style.justifyContent = 'flex-end';
                el.style.padding = '5px';
                el.innerHTML = `
                    <button class="site-theme-toggle-btn" onclick="toggleCreatedSiteTheme()" style="padding:8px 14px; background:#1e293b; color:#f8fafc; border:1px solid #334155; border-radius:20px; font-size:12px; font-weight:bold; cursor:pointer; display:flex; align-items:center; gap:6px;">
                        <span>🌙</span> <span>Переключить тему</span>
                    </button>
                `;
            } else if (type === 'star-reviews') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.padding = '15px';
                el.style.backgroundColor = '#f8fafc';
                el.style.border = '1px solid #e2e8f0';
                el.style.borderRadius = '10px';
                el.innerHTML = `
                    <h3 style="font-size:16px; margin-bottom:12px; color:#0f172a; text-align:center;">⭐ Отзывы клиентов</h3>
                    <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(200px, 1fr)); gap:10px;">
                        <div style="background:#ffffff; padding:12px; border-radius:8px; border:1px solid #cbd5e1;" class="dark-card">
                            <div style="color:#f59e0b; font-size:14px; margin-bottom:4px;">★★★★★</div>
                            <p style="font-size:12px; color:#334155; margin-bottom:6px;">«Превосходное качество работы! Все выполнено точно в срок.»</p>
                            <strong style="font-size:11px; color:#0284c7;">— Дмитрий В.</strong>
                        </div>
                        <div style="background:#ffffff; padding:12px; border-radius:8px; border:1px solid #cbd5e1;" class="dark-card">
                            <div style="color:#f59e0b; font-size:14px; margin-bottom:4px;">★★★★★</div>
                            <p style="font-size:12px; color:#334155; margin-bottom:6px;">«Заказывали веб-сайт под ключ, результат превзошел все ожидания.»</p>
                            <strong style="font-size:11px; color:#0284c7;">— Елена К.</strong>
                        </div>
                    </div>
                `;
            } else if (type === 'social-share') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.padding = '12px';
                el.style.textAlign = 'center';
                el.style.backgroundColor = '#f1f5f9';
                el.style.borderRadius = '8px';
                el.innerHTML = `
                    <p style="font-size:12px; font-weight:bold; color:#475569; margin-bottom:8px;">Мы в соцсетях & Поделиться:</p>
                    <div style="display:flex; justify-content:center; gap:8px; flex-wrap:wrap;">
                        <a href="https://t.me/programisstuz" target="_blank" style="padding:6px 12px; background:#0088cc; color:white; text-decoration:none; border-radius:6px; font-size:11px; font-weight:bold;">Telegram</a>
                        <a href="#" onclick="alert('Ссылка скопирована!'); return false;" style="padding:6px 12px; background:#6366f1; color:white; text-decoration:none; border-radius:6px; font-size:11px; font-weight:bold;">🔗 Поделиться</a>
                        <a href="https://vk.com" target="_blank" style="padding:6px 12px; background:#0077ff; color:white; text-decoration:none; border-radius:6px; font-size:11px; font-weight:bold;">ВКонтакте</a>
                    </div>
                `;
            } else if (type === 'site-title') {
                el = document.createElement('h1');
                el.className = 'animated-site-title';
                el.innerText = 'Programist-studio';
                el.style.fontSize = '28px';
                el.style.textAlign = 'center';
                el.style.width = '100%';
            } else if (type === 'countdown') {
                el = document.createElement('div');
                el.style.padding = '15px';
                el.style.backgroundColor = '#1e293b';
                el.style.color = '#38bdf8';
                el.style.borderRadius = '10px';
                el.style.textAlign = 'center';
                el.className = 'dark-card';
                el.innerHTML = `
                    <h3 style="color:#ffffff; margin-bottom:8px; font-size:16px;">🔥 До конца акции:</h3>
                    <div style="display:flex; justify-content:center; gap:10px; font-size:18px; font-weight:bold;">
                        <div><span>05</span><small style="display:block; font-size:9px; color:#94a3b8;">часов</small></div>:
                        <div><span>42</span><small style="display:block; font-size:9px; color:#94a3b8;">минут</small></div>:
                        <div><span>18</span><small style="display:block; font-size:9px; color:#94a3b8;">секунд</small></div>
                    </div>
                `;
            } else if (type === 'pricing') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(200px, 1fr))';
                el.style.gap = '10px';
                el.innerHTML = `
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:15px; border-radius:8px; text-align:center; background:#f8fafc;">
                        <h3 style="font-size:16px;" contenteditable="true">Название тарифа 1</h3>
                        <p style="font-size:20px; font-weight:bold; color:#0284c7; margin:6px 0;" contenteditable="true">Ваша цена</p>
                        <p style="font-size:11px; color:#64748b;" contenteditable="true">Описание тарифа<br>Что входит в пакет</p>
                        <a href="https://t.me/programisstuz" target="_blank" style="display:inline-block; margin-top:10px; padding:6px 12px; background:#0284c7; color:white; text-decoration:none; border-radius:4px; font-size:12px;" contenteditable="true">Кнопка заказа</a>
                    </div>
                    <div class="rgb-card dark-card" style="padding:15px; border-radius:8px; text-align:center; background:#f0f9ff;">
                        <h3 style="font-size:16px;" contenteditable="true">Название тарифа 2</h3>
                        <p style="font-size:20px; font-weight:bold; color:#0284c7; margin:6px 0;" contenteditable="true">Ваша цена</p>
                        <p style="font-size:11px; color:#64748b;" contenteditable="true">Описание тарифа<br>Что входит в пакет</p>
                        <a href="https://t.me/programisstuz" target="_blank" style="display:inline-block; margin-top:10px; padding:6px 12px; background:#38bdf8; color:#0f172a; text-decoration:none; border-radius:4px; font-weight:bold; font-size:12px;" contenteditable="true">Кнопка заказа</a>
                    </div>
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:15px; border-radius:8px; text-align:center; background:#f8fafc;">
                        <h3 style="font-size:16px;" contenteditable="true">Название тарифа 3</h3>
                        <p style="font-size:20px; font-weight:bold; color:#0284c7; margin:6px 0;" contenteditable="true">Ваша цена</p>
                        <p style="font-size:11px; color:#64748b;" contenteditable="true">Описание тарифа<br>Что входит в пакет</p>
                        <a href="https://t.me/programisstuz" target="_blank" style="display:inline-block; margin-top:10px; padding:6px 12px; background:#0284c7; color:white; text-decoration:none; border-radius:4px; font-size:12px;" contenteditable="true">Кнопка заказа</a>
                    </div>
                `;
            } else if (type === 'features') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(180px, 1fr))';
                el.style.gap = '12px';
                el.style.padding = '10px 0';
                el.innerHTML = `
                    <div class="dark-card" style="padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px; text-align:center;">
                        <div style="font-size:24px; margin-bottom:4px;">⚡</div>
                        <strong style="font-size:13px; color:#0f172a;">Высокая скорость</strong>
                        <p style="font-size:11px; color:#64748b; margin-top:4px;">Оптимизированный код и моментальная загрузка.</p>
                    </div>
                    <div class="dark-card" style="padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px; text-align:center;">
                        <div style="font-size:24px; margin-bottom:4px;">🛡️</div>
                        <strong style="font-size:13px; color:#0f172a;">Надежная защита</strong>
                        <p style="font-size:11px; color:#64748b; margin-top:4px;">Защита от атак и полная сохранность данных.</p>
                    </div>
                    <div class="dark-card" style="padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px; text-align:center;">
                        <div style="font-size:24px; margin-bottom:4px;">🎨</div>
                        <strong style="font-size:13px; color:#0f172a;">AI Дизайн</strong>
                        <p style="font-size:11px; color:#64748b; margin-top:4px;">Современный внешний вид с адаптивностью.</p>
                    </div>
                `;
            } else if (type === 'stats') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.display = 'flex';
                el.style.justifyContent = 'space-around';
                el.style.padding = '15px';
                el.style.background = 'linear-gradient(135deg, #0f172a, #1e293b)';
                el.style.borderRadius = '10px';
                el.style.color = '#ffffff';
                el.style.flexWrap = 'wrap';
                el.style.gap = '10px';
                el.innerHTML = `
                    <div style="text-align:center;">
                        <div style="font-size:22px; font-weight:800; color:#38bdf8;">150+</div>
                        <div style="font-size:11px; color:#94a3b8;">Проектов</div>
                    </div>
                    <div style="text-align:center;">
                        <div style="font-size:22px; font-weight:800; color:#a855f7;">99%</div>
                        <div style="font-size:11px; color:#94a3b8;">Довольных клиентов</div>
                    </div>
                    <div style="text-align:center;">
                        <div style="font-size:22px; font-weight:800; color:#10b981;">24/7</div>
                        <div style="font-size:11px; color:#94a3b8;">Поддержка</div>
                    </div>
                `;
            } else if (type === 'testimonials') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.border = '1px solid #cbd5e1';
                el.style.padding = '12px';
                el.style.borderRadius = '8px';
                el.style.background = '#f8fafc';
                el.style.display = 'flex';
                el.style.gap = '10px';
                el.style.alignItems = 'center';
                el.innerHTML = `
                    <img src="https://via.placeholder.com/40" style="border-radius:50%; width:40px; height:40px;">
                    <div>
                        <strong style="font-size:13px;">Алексей Иванов</strong>
                        <p style="font-size:11px; color:#64748b;">«Отличный сервис, рекомендую!»</p>
                    </div>
                `;
            } else if (type === 'floating-messengers') {
                el = document.createElement('div');
                el.style.display = 'flex';
                el.style.gap = '8px';
                el.style.justifyContent = 'center';
                el.style.flexWrap = 'wrap';
                el.innerHTML = `
                    <a href="https://t.me/programisstuz" target="_blank" style="padding:8px 14px; background:#229ED9; color:white; text-decoration:none; border-radius:20px; font-size:11px; font-weight:bold;">Telegram</a>
                    <a href="https://whatsapp.com" target="_blank" style="padding:8px 14px; background:#25D366; color:white; text-decoration:none; border-radius:20px; font-size:11px; font-weight:bold;">WhatsApp</a>
                `;
            } else if (type === 'navbar') {
                el = document.createElement('nav');
                el.className = 'dark-card';
                el.style.display = 'flex';
                el.style.justifyContent = 'space-between';
                el.style.alignItems = 'center';
                el.style.padding = '10px';
                el.style.backgroundColor = '#f1f5f9';
                el.style.borderRadius = '6px';
                el.innerHTML = '<strong style="font-size:14px;" class="animated-site-title">Programist-studio</strong><div style="font-size:12px;"><a href="https://t.me/programisstuz" target="_blank" style="margin-left:8px; text-decoration:none; color:inherit;">Главная</a><a href="https://t.me/programisstuz" target="_blank" style="margin-left:8px; text-decoration:none; color:inherit;">Услуги</a><a href="https://t.me/programisstuz" target="_blank" style="margin-left:8px; text-decoration:none; color:inherit;">Контакты</a></div>';
            } else if (type === 'header') {
                el = document.createElement('h1');
                el.innerText = 'Заголовок страницы';
                el.style.fontSize = '22px';
            } else if (type === 'text') {
                el = document.createElement('p');
                el.innerText = 'Это пример текстового блока для вашего нового сайта.';
                el.style.fontSize = '14px';
            } else if (type === 'button') {
                el = document.createElement('a');
                el.innerText = 'Узнать больше';
                el.href = "https://t.me/programisstuz";
                el.target = "_blank";
                el.style.display = 'inline-block';
                el.style.padding = '10px 18px';
                el.style.backgroundColor = '#38bdf8';
                el.style.color = '#0f172a';
                el.style.textDecoration = 'none';
                el.style.borderRadius = '6px';
                el.style.fontWeight = 'bold';
                el.style.fontSize = '13px';
            } else if (type === 'image') {
                el = document.createElement('img');
                el.src = 'https://via.placeholder.com/600x200';
                el.style.width = '100%';
                el.style.borderRadius = '6px';
            } else if (type === 'card') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.border = '1px solid #e2e8f0';
                el.style.borderRadius = '8px';
                el.style.padding = '12px';
                el.style.backgroundColor = '#f8fafc';
                el.innerHTML = '<h3 style="font-size:15px;">Название карточки</h3><p style="margin-top:5px; font-size:12px; color:#64748b;">Описание товара или услуги.</p>';
            } else if (type === 'grid2') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(220px, 1fr))';
                el.style.gap = '10px';
                el.innerHTML = `
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:12px; border-radius:6px; background:#f8fafc;">
                        <h4 style="font-size:14px;">Колонка 1</h4>
                        <p style="font-size:12px; color:#64748b; margin-top:4px;">Текст описания для первой колонки.</p>
                    </div>
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:12px; border-radius:6px; background:#f8fafc;">
                        <h4 style="font-size:14px;">Колонка 2</h4>
                        <p style="font-size:12px; color:#64748b; margin-top:4px;">Текст описания для второй колонки.</p>
                    </div>
                `;
            } else if (type === 'grid3') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(140px, 1fr))';
                el.style.gap = '8px';
                el.innerHTML = `
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:10px; border-radius:6px; background:#f8fafc;">
                        <h4 style="font-size:13px;">Услуга 1</h4>
                    </div>
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:10px; border-radius:6px; background:#f8fafc;">
                        <h4 style="font-size:13px;">Услуга 2</h4>
                    </div>
                    <div class="dark-card" style="border:1px solid #e2e8f0; padding:10px; border-radius:6px; background:#f8fafc;">
                        <h4 style="font-size:13px;">Услуга 3</h4>
                    </div>
                `;
            } else if (type === 'gallery2') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = '1fr 1fr';
                el.style.gap = '8px';
                el.innerHTML = `
                    <img src="https://via.placeholder.com/200x120" style="width:100%; border-radius:4px;">
                    <img src="https://via.placeholder.com/200x120" style="width:100%; border-radius:4px;">
                `;
            } else if (type === 'form') {
                el = document.createElement('form');
                el.className = 'dark-card';
                el.style.border = '1px solid #e2e8f0';
                el.style.padding = '12px';
                el.style.borderRadius = '8px';
                el.style.backgroundColor = '#f8fafc';
                el.onsubmit = (e) => e.preventDefault();
                el.innerHTML = `
                    <h3 style="margin-bottom:8px; font-size:15px;">Оставить заявку</h3>
                    <input type="text" placeholder="Ваше Имя" style="width:100%; padding:8px; margin-bottom:8px; border:1px solid #cbd5e1; border-radius:4px; font-size:13px;">
                    <input type="text" placeholder="Телефон / Telegram" style="width:100%; padding:8px; margin-bottom:8px; border:1px solid #cbd5e1; border-radius:4px; font-size:13px;">
                    <button style="width:100%; padding:8px; background:#38bdf8; border:none; border-radius:4px; font-weight:bold; font-size:13px; cursor:pointer;">Отправить заявку</button>
                `;
            } else if (type === 'faq') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.padding = '10px';
                el.style.borderLeft = '3px solid #38bdf8';
                el.style.backgroundColor = '#f1f5f9';
                el.innerHTML = `
                    <h4 style="font-size:13px;">Вопрос: Как быстро готовится сайт?</h4>
                    <p style="margin-top:3px; font-size:12px; color:#64748b;">Сроки изготовления от 1 до 3 дней в зависимости от сложности.</p>
                `;
            } else if (type === 'divider') {
                el = document.createElement('hr');
                el.style.border = 'none';
                el.style.borderTop = '1px solid #cbd5e1';
                el.style.margin = '10px 0';
            } else if (type === 'footer') {
                el = document.createElement('footer');
                el.style.textAlign = 'center';
                el.style.padding = '10px 0';
                el.style.color = '#94a3b8';
                el.style.fontSize = '11px';
                el.innerText = '© 2026 Programist-studio. Все права защищены.';
            } else if (type === 'hero-split') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(220px, 1fr))';
                el.style.gap = '20px';
                el.style.alignItems = 'center';
                el.innerHTML = `
                    <div>
                        <h2 style="font-size:24px; margin-bottom:8px;">Заголовок вашего предложения</h2>
                        <p style="font-size:13px; color:#64748b; margin-bottom:14px;">Краткое описание преимуществ продукта или услуги в одном-двух предложениях.</p>
                        <a href="https://t.me/programisstuz" target="_blank" style="display:inline-block; padding:10px 20px; background:#38bdf8; color:#0f172a; text-decoration:none; border-radius:6px; font-weight:bold; font-size:13px;">Начать сейчас</a>
                    </div>
                    <img src="https://via.placeholder.com/500x350/38bdf8/ffffff?text=Ваше+фото" style="width:100%; border-radius:10px;">
                `;
            } else if (type === 'cta-banner') {
                el = document.createElement('div');
                el.className = 'rgb-card';
                el.style.padding = '24px';
                el.style.borderRadius = '12px';
                el.style.textAlign = 'center';
                el.style.background = 'linear-gradient(135deg, #1e293b, #0f172a)';
                el.style.color = '#ffffff';
                el.innerHTML = `
                    <h2 style="font-size:22px; margin-bottom:8px;">Готовы начать свой проект?</h2>
                    <p style="font-size:13px; color:#94a3b8; margin-bottom:14px;">Оставьте заявку и получите бесплатную консультацию уже сегодня.</p>
                    <a href="https://t.me/programisstuz" target="_blank" style="display:inline-block; padding:12px 26px; background:#38bdf8; color:#0f172a; text-decoration:none; border-radius:30px; font-weight:bold; font-size:14px;">Связаться с нами</a>
                `;
            } else if (type === 'team') {
                el = document.createElement('div');
                el.style.display = 'grid';
                el.style.gridTemplateColumns = 'repeat(auto-fit, minmax(140px, 1fr))';
                el.style.gap = '12px';
                el.innerHTML = `
                    <div class="dark-card" style="text-align:center; padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px;">
                        <img src="https://via.placeholder.com/80" style="width:70px; height:70px; border-radius:50%; margin-bottom:8px;">
                        <strong style="font-size:13px; display:block;">Алишер Валиев</strong>
                        <span style="font-size:11px; color:#64748b;">Основатель</span>
                    </div>
                    <div class="dark-card" style="text-align:center; padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px;">
                        <img src="https://via.placeholder.com/80" style="width:70px; height:70px; border-radius:50%; margin-bottom:8px;">
                        <strong style="font-size:13px; display:block;">Диана Ким</strong>
                        <span style="font-size:11px; color:#64748b;">Менеджер проекта</span>
                    </div>
                    <div class="dark-card" style="text-align:center; padding:12px; background:#f8fafc; border:1px solid #e2e8f0; border-radius:8px;">
                        <img src="https://via.placeholder.com/80" style="width:70px; height:70px; border-radius:50%; margin-bottom:8px;">
                        <strong style="font-size:13px; display:block;">Тимур Расулов</strong>
                        <span style="font-size:11px; color:#64748b;">Разработчик</span>
                    </div>
                `;
            } else if (type === 'newsletter') {
                el = document.createElement('div');
                el.className = 'dark-card';
                el.style.padding = '18px';
                el.style.background = 'linear-gradient(135deg, #0f172a, #1e293b)';
                el.style.borderRadius = '10px';
                el.style.textAlign = 'center';
                el.style.color = '#ffffff';
                el.innerHTML = `
                    <h3 style="margin-bottom:6px; font-size:16px;">📩 Подпишитесь на новости</h3>
                    <p style="font-size:12px; color:#94a3b8; margin-bottom:12px;">Будьте в курсе акций и новых предложений первыми.</p>
                    <form onsubmit="return false;" style="display:flex; gap:8px; max-width:360px; margin:0 auto; flex-wrap:wrap;">
                        <input type="email" placeholder="Ваш email" style="flex:1; min-width:160px; padding:9px; border-radius:6px; border:none; font-size:13px;">
                        <button style="padding:9px 16px; background:#38bdf8; color:#0f172a; border:none; border-radius:6px; font-weight:bold; font-size:13px; cursor:pointer;">Подписаться</button>
                    </form>
                `;
            } else if (type === 'logos-strip') {
                el = document.createElement('div');
                el.style.display = 'flex';
                el.style.justifyContent = 'space-around';
                el.style.alignItems = 'center';
                el.style.flexWrap = 'wrap';
                el.style.gap = '16px';
                el.style.padding = '10px 0';
                el.style.opacity = '0.8';
                el.innerHTML = `
                    <strong style="font-size:16px; color:#94a3b8;">ACME</strong>
                    <strong style="font-size:16px; color:#94a3b8;">NovaTech</strong>
                    <strong style="font-size:16px; color:#94a3b8;">Orbit</strong>
                    <strong style="font-size:16px; color:#94a3b8;">Vertex</strong>
                    <strong style="font-size:16px; color:#94a3b8;">Prisma</strong>
                `;
            } else if (type === 'timeline') {
                el = document.createElement('div');
                el.style.display = 'flex';
                el.style.flexDirection = 'column';
                el.style.gap = '14px';
                el.innerHTML = `
                    <div style="display:flex; gap:12px; align-items:flex-start;">
                        <div style="width:28px; height:28px; border-radius:50%; background:#38bdf8; color:#0f172a; display:flex; align-items:center; justify-content:center; font-weight:bold; flex-shrink:0;">1</div>
                        <div><strong style="font-size:13px;">Заявка и брифинг</strong><p style="font-size:12px; color:#64748b;">Обсуждаем детали и цели проекта.</p></div>
                    </div>
                    <div style="display:flex; gap:12px; align-items:flex-start;">
                        <div style="width:28px; height:28px; border-radius:50%; background:#a855f7; color:#fff; display:flex; align-items:center; justify-content:center; font-weight:bold; flex-shrink:0;">2</div>
                        <div><strong style="font-size:13px;">Дизайн и разработка</strong><p style="font-size:12px; color:#64748b;">Создаём макет и воплощаем в коде.</p></div>
                    </div>
                    <div style="display:flex; gap:12px; align-items:flex-start;">
                        <div style="width:28px; height:28px; border-radius:50%; background:#ec4899; color:#fff; display:flex; align-items:center; justify-content:center; font-weight:bold; flex-shrink:0;">3</div>
                        <div><strong style="font-size:13px;">Запуск проекта</strong><p style="font-size:12px; color:#64748b;">Тестируем и публикуем готовый сайт.</p></div>
                    </div>
                `;
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
                clearSelection();
                saveHistoryState();
            };
            wrapper.appendChild(deleteBtn);

            const dragHandle = document.createElement('div');
            dragHandle.className = 'drag-handle';
            dragHandle.innerText = '⋮⋮ Перетащить';
            wrapper.appendChild(dragHandle);

            canvas.appendChild(wrapper);
            rebindCanvasEvents();
            selectElement(wrapper, el, type);

            if (currentMode === 'code') {
                updateCodeEditorFromCanvas();
            }

            if (window.innerWidth <= 1024) switchMobileTab('canvas');

            saveHistoryState();
        }

        function selectElement(wrapper, targetEl, type) {
            document.querySelectorAll('.canvas-item').forEach(item => item.classList.remove('selected'));
            wrapper.classList.add('selected');
            selectedElement = targetEl;
            selectedWrapper = wrapper;

            let html = `
                <div class="btn-row-controls">
                    <button onclick="moveSelectedUp()">⬆️ Вверх</button>
                    <button onclick="moveSelectedDown()">⬇️ Вниз</button>
                    <button onclick="duplicateSelected()">📋 Клон</button>
                </div>
            `;

            if (type === 'draggable-icon') {
                html += `
                    <div class="control-group">
                        <label>Выберите иконку (Emoji):</label>
                        <select id="prop-icon-select">
                            <option value="🚀">🚀 Ракета</option>
                            <option value="⭐">⭐ Звезда</option>
                            <option value="🔥">🔥 Огонь</option>
                            <option value="💡">💡 Лампочка</option>
                            <option value="⚡">⚡ Молния</option>
                            <option value="💎">💎 Бриллиант</option>
                            <option value="🛒">🛒 Корзина</option>
                            <option value="❤️">❤️ Сердце</option>
                            <option value="🎯">🎯 Цель</option>
                            <option value="👑">👑 Корона</option>
                        </select>
                    </div>
                    <div class="control-group">
                        <label>Размер иконки (px):</label>
                        <input type="number" id="prop-icon-size" value="${parseInt(targetEl.style.fontSize) || 32}" min="12" max="120">
                    </div>
                `;
            } else if (type === 'video') {
                const iframe = targetEl.querySelector('iframe');
                const src = iframe ? iframe.src : '';
                html += `
                    <div class="control-group">
                        <label>Ссылка на YouTube (Embed URL):</label>
                        <input type="text" id="prop-video-src" value="${src}">
                    </div>
                `;
            }

            if (['site-title', 'header', 'text', 'button', 'footer', 'card', 'promo-banner', 'cta-banner', 'hero-split'].includes(type)) {
                html += `
                    <div class="control-group">
                        <label>Тематика для AI-генерации:</label>
                        <select id="ai-topic-select">
                            <option value="it">💻 IT-Студия / Разработка</option>
                            <option value="restaurant">🍕 Ресторан / Доставка</option>
                            <option value="courses">🎓 Курсы / Обучение</option>
                            <option value="shop">🛒 Магазин / Товары</option>
                            <option value="beauty">💅 Салон красоты</option>
                            <option value="fitness">🏋️ Фитнес-клуб</option>
                            <option value="realestate">🏠 Недвижимость</option>
                            <option value="medical">🩺 Медицина</option>
                            <option value="travel">✈️ Путешествия</option>
                            <option value="wedding">💍 Свадьбы & Праздники</option>
                        </select>
                        <button class="btn-gen-ai" onclick="generateAIText(document.getElementById('ai-topic-select').value, '${type}')">✨ Сгенерировать текст (AI)</button>
                    </div>
                `;
            }

            if (['site-title', 'header', 'text', 'button', 'footer', 'promo-banner'].includes(type)) {
                html += `
                    <div class="control-group">
                        <label>Текст блока:</label>
                        <input type="text" id="prop-text" value="${targetEl.innerText}">
                    </div>
                `;
            }

            html += `
                <div class="control-group">
                    <label>Шрифт элемента:</label>
                    <select id="prop-font">
                        <option value="inherit">По умолчанию (как у сайта)</option>
                        <option value="Inter" ${targetEl.style.fontFamily.includes('Inter') ? 'selected' : ''}>Inter</option>
                        <option value="Montserrat" ${targetEl.style.fontFamily.includes('Montserrat') ? 'selected' : ''}>Montserrat</option>
                        <option value="Poppins" ${targetEl.style.fontFamily.includes('Poppins') ? 'selected' : ''}>Poppins</option>
                        <option value="Roboto" ${targetEl.style.fontFamily.includes('Roboto') ? 'selected' : ''}>Roboto</option>
                        <option value="Open Sans" ${targetEl.style.fontFamily.includes('Open Sans') ? 'selected' : ''}>Open Sans</option>
                        <option value="Nunito" ${targetEl.style.fontFamily.includes('Nunito') ? 'selected' : ''}>Nunito</option>
                        <option value="Raleway" ${targetEl.style.fontFamily.includes('Raleway') ? 'selected' : ''}>Raleway</option>
                        <option value="Source Sans 3" ${targetEl.style.fontFamily.includes('Source Sans 3') ? 'selected' : ''}>Source Sans 3</option>
                        <option value="Oswald" ${targetEl.style.fontFamily.includes('Oswald') ? 'selected' : ''}>Oswald</option>
                        <option value="Exo 2" ${targetEl.style.fontFamily.includes('Exo 2') ? 'selected' : ''}>Exo 2</option>
                        <option value="Playfair Display" ${targetEl.style.fontFamily.includes('Playfair Display') ? 'selected' : ''}>Playfair Display</option>
                        <option value="Lora" ${targetEl.style.fontFamily.includes('Lora') ? 'selected' : ''}>Lora</option>
                        <option value="Comfortaa" ${targetEl.style.fontFamily.includes('Comfortaa') ? 'selected' : ''}>Comfortaa</option>
                        <option value="Caveat" ${targetEl.style.fontFamily.includes('Caveat') ? 'selected' : ''}>Caveat</option>
                        <option value="Pacifico" ${targetEl.style.fontFamily.includes('Pacifico') ? 'selected' : ''}>Pacifico</option>
                        <option value="JetBrains Mono" ${targetEl.style.fontFamily.includes('JetBrains Mono') ? 'selected' : ''}>JetBrains Mono</option>
                    </select>
                </div>
                <div class="control-group">
                    <label>Цвет текста элемента:</label>
                    <input type="color" id="prop-color" value="${rgbToHex(targetEl.style.color)}">
                </div>
            `;

            const currentRadius = parseInt(targetEl.style.borderRadius) || 0;
            const hasShadow = targetEl.style.boxShadow && targetEl.style.boxShadow !== 'none';
            const shadowVal = hasShadow ? 15 : 0;

            html += `
                <div class="control-group">
                    <label>Скругление углов: <span id="val-radius">${currentRadius}px</span></label>
                    <input type="range" id="prop-radius" min="0" max="50" value="${currentRadius}">
                </div>
                <div class="control-group">
                    <label>Глубина тени: <span id="val-shadow">${shadowVal}px</span></label>
                    <input type="range" id="prop-shadow" min="0" max="40" value="${shadowVal}">
                </div>
            `;

            html += `
                <div class="control-group">
                    <label>Анимация появления & эффекты:</label>
                    <select id="prop-animation">
                        <option value="">Без анимации</option>
                        <option value="anim-fade" ${wrapper.classList.contains('anim-fade') ? 'selected' : ''}>Плавная (Fade)</option>
                        <option value="anim-slide-up" ${wrapper.classList.contains('anim-slide-up') ? 'selected' : ''}>Снизу (Slide Up)</option>
                        <option value="anim-slide-down" ${wrapper.classList.contains('anim-slide-down') ? 'selected' : ''}>Сверху (Slide Down)</option>
                        <option value="anim-slide-left" ${wrapper.classList.contains('anim-slide-left') ? 'selected' : ''}>Слева (Slide Left)</option>
                        <option value="anim-slide-right" ${wrapper.classList.contains('anim-slide-right') ? 'selected' : ''}>Справа (Slide Right)</option>
                        <option value="anim-zoom" ${wrapper.classList.contains('anim-zoom') ? 'selected' : ''}>Zoom In</option>
                        <option value="anim-zoom-out" ${wrapper.classList.contains('anim-zoom-out') ? 'selected' : ''}>Zoom Out</option>
                        <option value="anim-blur-in" ${wrapper.classList.contains('anim-blur-in') ? 'selected' : ''}>Размытие (Blur In)</option>
                        <option value="anim-float" ${wrapper.classList.contains('anim-float') ? 'selected' : ''}>Парение (Floating)</option>
                        <option value="anim-pulse" ${wrapper.classList.contains('anim-pulse') ? 'selected' : ''}>Пульсация (Pulse Glow)</option>
                        <option value="anim-heartbeat" ${wrapper.classList.contains('anim-heartbeat') ? 'selected' : ''}>Сердцебиение (Heartbeat)</option>
                        <option value="anim-flip" ${wrapper.classList.contains('anim-flip') ? 'selected' : ''}>Переворот (3D Flip)</option>
                        <option value="anim-flip-y" ${wrapper.classList.contains('anim-flip-y') ? 'selected' : ''}>Переворот Y (Flip Y)</option>
                        <option value="anim-bounce" ${wrapper.classList.contains('anim-bounce') ? 'selected' : ''}>Прыжки (Bounce)</option>
                        <option value="anim-shake" ${wrapper.classList.contains('anim-shake') ? 'selected' : ''}>Тряска (Shake)</option>
                        <option value="anim-rotate" ${wrapper.classList.contains('anim-rotate') ? 'selected' : ''}>Вращение (Rotate)</option>
                        <option value="anim-sparkle" ${wrapper.classList.contains('anim-sparkle') ? 'selected' : ''}>Сияние (Sparkle)</option>
                        <option value="anim-swing" ${wrapper.classList.contains('anim-swing') ? 'selected' : ''}>Качание (Swing)</option>
                        <option value="anim-wobble" ${wrapper.classList.contains('anim-wobble') ? 'selected' : ''}>Колыхание (Wobble)</option>
                        <option value="anim-glow-pulse" ${wrapper.classList.contains('anim-glow-pulse') ? 'selected' : ''}>Цветное свечение (Glow Pulse)</option>
                    </select>
                </div>
            `;

            html += `
                <div class="control-group">
                    <label>Тема переливания цвета (RGB/Градиент):</label>
                    <select id="prop-color-theme" onchange="applyColorTheme(this.value)">
                        <option value="rainbow">🌈 Радуга (по умолчанию)</option>
                        <option value="fire">🔥 Огонь</option>
                        <option value="ocean">🌊 Океан</option>
                        <option value="neon">💜 Неон</option>
                        <option value="emerald">💚 Изумруд</option>
                    </select>
                </div>
            `;

            if (type === 'button' || targetEl.tagName.toLowerCase() === 'a') {
                html += `
                    <div class="control-group">
                        <label>Ссылка (URL):</label>
                        <input type="text" id="prop-href" value="${targetEl.getAttribute('href') || 'https://t.me/programisstuz'}">
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
                        <label>URL Фото:</label>
                        <input type="text" id="prop-src" value="${targetEl.src}">
                    </div>
                `;
            }

            if (['card', 'navbar', 'form', 'faq', 'countdown', 'star-reviews', 'social-share', 'promo-banner', 'features', 'stats', 'audio', 'cta-banner', 'team', 'newsletter', 'logos-strip', 'timeline'].includes(type)) {
                html += `
                    <div class="control-group">
                        <label>Фон блока:</label>
                        <input type="color" id="prop-bg" value="${rgbToHex(targetEl.style.backgroundColor)}">
                    </div>
                `;
            }

            const nestedLinks = targetEl.querySelectorAll ? targetEl.querySelectorAll('a') : [];
            if (nestedLinks.length) {
                html += `<h2 style="margin-top:14px;">🔗 Ссылки внутри блока</h2>`;
                nestedLinks.forEach((linkEl, idx) => {
                    html += `
                        <div class="control-group inner-link-block">
                            <label>Текст ссылки ${idx + 1}:</label>
                            <input type="text" class="inner-link-text" data-idx="${idx}" value="${(linkEl.innerText || '').replace(/"/g, '&quot;')}">
                            <label>URL ссылки ${idx + 1}:</label>
                            <input type="text" class="inner-link-href" data-idx="${idx}" value="${(linkEl.getAttribute('href') || '').replace(/"/g, '&quot;')}">
                        </div>
                    `;
                });
            }

            const nestedImgs = targetEl.querySelectorAll ? targetEl.querySelectorAll('img') : [];
            if (nestedImgs.length) {
                html += `<h2 style="margin-top:14px;">🖼️ Изображения внутри блока</h2>`;
                nestedImgs.forEach((imgEl, idx) => {
                    html += `
                        <div class="control-group inner-link-block">
                            <label>URL картинки ${idx + 1}:</label>
                            <input type="text" class="inner-img-src" data-idx="${idx}" value="${(imgEl.getAttribute('src') || '').replace(/"/g, '&quot;')}">
                        </div>
                    `;
                });
            }

            editorControls.innerHTML = html;

            editorControls.querySelectorAll('.inner-link-text').forEach(inp => {
                inp.oninput = (e) => {
                    const idx = parseInt(e.target.dataset.idx);
                    const linkEl = targetEl.querySelectorAll('a')[idx];
                    if (linkEl) linkEl.innerText = e.target.value;
                    saveHistoryState();
                };
            });

            editorControls.querySelectorAll('.inner-link-href').forEach(inp => {
                inp.oninput = (e) => {
                    const idx = parseInt(e.target.dataset.idx);
                    const linkEl = targetEl.querySelectorAll('a')[idx];
                    if (linkEl) linkEl.setAttribute('href', e.target.value);
                    saveHistoryState();
                };
                inp.onblur = (e) => {
                    const idx = parseInt(e.target.dataset.idx);
                    const linkEl = targetEl.querySelectorAll('a')[idx];
                    const normalized = normalizeUrl(e.target.value);
                    e.target.value = normalized;
                    if (linkEl) linkEl.setAttribute('href', normalized);
                    saveHistoryState();
                };
            });

            editorControls.querySelectorAll('.inner-img-src').forEach(inp => {
                inp.oninput = (e) => {
                    const idx = parseInt(e.target.dataset.idx);
                    const imgEl = targetEl.querySelectorAll('img')[idx];
                    if (imgEl) imgEl.setAttribute('src', e.target.value);
                    saveHistoryState();
                };
            });

            const propIconSelect = document.getElementById('prop-icon-select');
            if (propIconSelect) propIconSelect.onchange = (e) => { targetEl.innerText = e.target.value; saveHistoryState(); };

            const propIconSize = document.getElementById('prop-icon-size');
            if (propIconSize) propIconSize.oninput = (e) => { targetEl.style.fontSize = e.target.value + 'px'; saveHistoryState(); };

            const propVideoSrc = document.getElementById('prop-video-src');
            if (propVideoSrc) {
                propVideoSrc.oninput = (e) => {
                    const iframe = targetEl.querySelector('iframe');
                    if (iframe) iframe.src = e.target.value;
                    saveHistoryState();
                };
            }

            const propText = document.getElementById('prop-text');
            if (propText) propText.oninput = (e) => { targetEl.innerText = e.target.value; saveHistoryState(); };

            const propColor = document.getElementById('prop-color');
            if (propColor) propColor.oninput = (e) => { targetEl.style.color = e.target.value; saveHistoryState(); };

            const propFont = document.getElementById('prop-font');
            if (propFont) {
                propFont.onchange = (e) => {
                    targetEl.style.fontFamily = e.target.value === 'inherit' ? 'inherit' : e.target.value;
                    saveHistoryState();
                };
            }

            const propRadius = document.getElementById('prop-radius');
            if (propRadius) {
                propRadius.oninput = (e) => {
                    const val = e.target.value;
                    targetEl.style.borderRadius = val + 'px';
                    document.getElementById('val-radius').innerText = val + 'px';
                    saveHistoryState();
                };
            }

            const propShadow = document.getElementById('prop-shadow');
            if (propShadow) {
                propShadow.oninput = (e) => {
                    const val = e.target.value;
                    targetEl.style.boxShadow = val > 0 ? `0 ${val / 2}px ${val}px rgba(0, 0, 0, 0.15)` : 'none';
                    document.getElementById('val-shadow').innerText = val + 'px';
                    saveHistoryState();
                };
            }

            const propAnim = document.getElementById('prop-animation');
            if (propAnim) {
                propAnim.onchange = (e) => {
                    wrapper.classList.remove('anim-fade', 'anim-slide-up', 'anim-slide-down', 'anim-slide-left', 'anim-slide-right', 'anim-zoom', 'anim-zoom-out', 'anim-blur-in', 'anim-float', 'anim-pulse', 'anim-heartbeat', 'anim-flip', 'anim-flip-y', 'anim-bounce', 'anim-shake', 'anim-rotate', 'anim-sparkle', 'anim-swing', 'anim-wobble', 'anim-glow-pulse');
                    if (e.target.value) wrapper.classList.add(e.target.value);
                    saveHistoryState();
                };
            }

            const propHref = document.getElementById('prop-href');
            if (propHref) {
                propHref.oninput = (e) => { targetEl.setAttribute('href', e.target.value); saveHistoryState(); };
                propHref.onblur = (e) => {
                    const normalized = normalizeUrl(e.target.value);
                    e.target.value = normalized;
                    targetEl.setAttribute('href', normalized);
                    saveHistoryState();
                };
            }

            const propBg = document.getElementById('prop-bg');
            if (propBg) propBg.oninput = (e) => { targetEl.style.backgroundColor = e.target.value; saveHistoryState(); };

            const propSrc = document.getElementById('prop-src');
            if (propSrc) {
                propSrc.oninput = (e) => { targetEl.src = e.target.value; saveHistoryState(); };
                propSrc.onblur = (e) => {
                    let val = e.target.value.trim();
                    if (val && !/^(https?:\/\/|data:|\/)/i.test(val)) val = 'https://' + val;
                    e.target.value = val;
                    targetEl.src = val;
                    saveHistoryState();
                };
            }
        }

        function updateCodeEditorFromCanvas() {
            const cloneCanvas = canvas.cloneNode(true);
            cloneCanvas.querySelectorAll('.delete-btn, .drag-handle').forEach(btn => btn.remove());
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

                const dragHandle = document.createElement('div');
                dragHandle.className = 'drag-handle';
                dragHandle.innerText = '⋮⋮ Перетащить';
                wrapper.appendChild(dragHandle);

                canvas.appendChild(wrapper);
            });

            rebindCanvasEvents();
            saveHistoryState();
        }

        function normalizeUrl(url) {
            if (!url) return '#';
            url = url.trim();
            if (url === '') return '#';
            if (/^(https?:\/\/|mailto:|tel:|#|\/)/i.test(url)) return url;
            return 'https://' + url;
        }

        function rgbToHex(rgb) {
            if (!rgb) return '#ffffff';
            if (rgb.startsWith('#')) return rgb;
            const res = rgb.match(/\d+/g);
            if (!res || res.length < 3) return '#ffffff';
            return "#" + ((1 << 24) + (parseInt(res[0]) << 16) + (parseInt(res[1]) << 8) + parseInt(res[2])).toString(16).slice(1);
        }

        function exportHTML() {
            const cloneCanvas = canvas.cloneNode(true);
            cloneCanvas.querySelectorAll('.delete-btn, .drag-handle').forEach(b => b.remove());
            cloneCanvas.querySelectorAll('#empty-msg').forEach(m => m.remove());
            cloneCanvas.querySelectorAll('[contenteditable]').forEach(el => el.removeAttribute('contenteditable'));
            const items = Array.from(cloneCanvas.querySelectorAll('.canvas-item'));
            items.forEach(item => {
                const child = item.firstElementChild;
                if (child) {
                    Array.from(item.classList).filter(c => c.startsWith('anim-')).forEach(c => child.classList.add(c));
                    item.replaceWith(child);
                } else item.remove();
            });

            const isDark = canvas.classList.contains('dark-theme');
            const bg = canvas.style.backgroundColor || (isDark ? '#0d1117' : '#ffffff');
            const font = (canvas.style.fontFamily || 'Inter').replace(/['"]/g, '');
            const padding = canvas.style.padding || '20px';
            const textColor = isDark ? '#ffffff' : '#1e293b';

            const fullPageCode = `<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>${currentPage.toUpperCase()} — Сгенерировано в Programist-studio</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Comfortaa:wght@400;600;700&family=Exo+2:wght@400;600;800&family=Inter:wght@400;600;800&family=JetBrains+Mono:wght@700&family=Lora:ital,wght@0,400;0,600;1,400&family=Montserrat:wght@400;600;800&family=Nunito:wght@400;600;800&family=Open+Sans:wght@400;600;800&family=Oswald:wght@400;600;700&family=Pacifico&family=Playfair+Display:wght@400;600;800&family=Poppins:wght@400;600;800&family=Raleway:wght@400;600;800&family=Roboto:wght@400;600;800&family=Source+Sans+3:wght@400;600;800&display=swap">
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background-color: ${bg}; font-family: '${font}', system-ui, sans-serif; padding: ${padding}; color: ${textColor}; min-height: 100vh; line-height: 1.5; }
        img { max-width: 100%; height: auto; }
        .dark-card { background-color: ${isDark ? '#161b22' : '#f8fafc'}; color: ${isDark ? '#f0f6fc' : 'inherit'}; }
        @keyframes textGradient { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }
        @keyframes titlePulse { 0% { transform: scale(1); } 50% { transform: scale(1.03); } 100% { transform: scale(1); } }
        @keyframes floatAnim { 0% { transform: translateY(0px); } 50% { transform: translateY(-10px); } 100% { transform: translateY(0px); } }
        @keyframes pulseGlow { 0% { box-shadow: 0 0 0 0 rgba(56, 189, 248, 0.7); } 70% { box-shadow: 0 0 0 15px rgba(56, 189, 248, 0); } 100% { box-shadow: 0 0 0 0 rgba(56, 189, 248, 0); } }
        @keyframes rotateAnim { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        @keyframes bounceAnim { 0%, 20%, 50%, 80%, 100% { transform: translateY(0); } 40% { transform: translateY(-15px); } 60% { transform: translateY(-7px); } }
        @keyframes shakeAnim { 0%, 100% { transform: translateX(0); } 20%, 60% { transform: translateX(-5px); } 40%, 80% { transform: translateX(5px); } }
        @keyframes flipIn { 0% { transform: rotateY(-90deg); opacity: 0; } 100% { transform: rotateY(0deg); opacity: 1; } }
        @keyframes sparkleGlow { 0% { filter: drop-shadow(0 0 2px #38bdf8); } 50% { filter: drop-shadow(0 0 12px #ec4899); } 100% { filter: drop-shadow(0 0 2px #38bdf8); } }
        @keyframes swingAnim { 0%, 100% { transform: rotate(0deg); } 20% { transform: rotate(6deg); } 40% { transform: rotate(-5deg); } 60% { transform: rotate(3deg); } 80% { transform: rotate(-2deg); } }
        @keyframes wobbleAnim { 0%, 100% { transform: translateX(0) rotate(0); } 25% { transform: translateX(-4px) rotate(-1.5deg); } 75% { transform: translateX(4px) rotate(1.5deg); } }
        @keyframes glowPulseColor { 0% { box-shadow: 0 0 12px rgba(56,189,248,0.6); } 33% { box-shadow: 0 0 18px rgba(168,85,247,0.6); } 66% { box-shadow: 0 0 18px rgba(236,72,153,0.6); } 100% { box-shadow: 0 0 12px rgba(56,189,248,0.6); } }
        @keyframes rgbBorder { 0% { border-color: #ff0055; box-shadow: 0 0 18px rgba(255, 0, 85, 0.7); } 20% { border-color: #ff8800; box-shadow: 0 0 18px rgba(255, 136, 0, 0.7); } 40% { border-color: #00ffcc; box-shadow: 0 0 18px rgba(0, 255, 204, 0.7); } 60% { border-color: #3388ff; box-shadow: 0 0 18px rgba(51, 136, 255, 0.7); } 80% { border-color: #9900ff; box-shadow: 0 0 18px rgba(153, 0, 255, 0.7); } 100% { border-color: #ff0055; box-shadow: 0 0 18px rgba(255, 0, 85, 0.7); } }
        @keyframes rgbGlowText { 0% { text-shadow: 0 0 8px #ff0055, 0 0 16px #ff0055; color: #fff; } 20% { text-shadow: 0 0 8px #ff8800, 0 0 16px #ff8800; color: #fff; } 40% { text-shadow: 0 0 8px #00ffcc, 0 0 16px #00ffcc; color: #fff; } 60% { text-shadow: 0 0 8px #3388ff, 0 0 16px #3388ff; color: #fff; } 80% { text-shadow: 0 0 8px #9900ff, 0 0 16px #9900ff; color: #fff; } 100% { text-shadow: 0 0 8px #ff0055, 0 0 16px #ff0055; color: #fff; } }
        @keyframes rgbBorderFire { 0% { border-color: #ff0000; box-shadow: 0 0 18px rgba(255,0,0,0.7);} 50% { border-color: #ffcc00; box-shadow: 0 0 18px rgba(255,204,0,0.7);} 100% { border-color: #ff0000; box-shadow: 0 0 18px rgba(255,0,0,0.7);} }
        @keyframes rgbGlowTextFire { 0% { text-shadow:0 0 8px #ff3300,0 0 16px #ff3300; color:#fff;} 50% { text-shadow:0 0 8px #ffcc00,0 0 16px #ffcc00; color:#fff;} 100% { text-shadow:0 0 8px #ff3300,0 0 16px #ff3300; color:#fff;} }
        @keyframes rgbBorderOcean { 0% { border-color: #0ea5e9; box-shadow: 0 0 18px rgba(14,165,233,0.7);} 50% { border-color: #22d3ee; box-shadow: 0 0 18px rgba(34,211,238,0.7);} 100% { border-color: #0ea5e9; box-shadow: 0 0 18px rgba(14,165,233,0.7);} }
        @keyframes rgbGlowTextOcean { 0% { text-shadow:0 0 8px #0ea5e9,0 0 16px #0ea5e9; color:#fff;} 50% { text-shadow:0 0 8px #22d3ee,0 0 16px #22d3ee; color:#fff;} 100% { text-shadow:0 0 8px #0ea5e9,0 0 16px #0ea5e9; color:#fff;} }
        @keyframes rgbBorderNeon { 0% { border-color: #ec4899; box-shadow: 0 0 18px rgba(236,72,153,0.7);} 50% { border-color: #a855f7; box-shadow: 0 0 18px rgba(168,85,247,0.7);} 100% { border-color: #ec4899; box-shadow: 0 0 18px rgba(236,72,153,0.7);} }
        @keyframes rgbGlowTextNeon { 0% { text-shadow:0 0 8px #ec4899,0 0 16px #ec4899; color:#fff;} 50% { text-shadow:0 0 8px #a855f7,0 0 16px #a855f7; color:#fff;} 100% { text-shadow:0 0 8px #ec4899,0 0 16px #ec4899; color:#fff;} }
        @keyframes rgbBorderEmerald { 0% { border-color: #10b981; box-shadow: 0 0 18px rgba(16,185,129,0.7);} 50% { border-color: #a3e635; box-shadow: 0 0 18px rgba(163,230,53,0.7);} 100% { border-color: #10b981; box-shadow: 0 0 18px rgba(16,185,129,0.7);} }
        @keyframes rgbGlowTextEmerald { 0% { text-shadow:0 0 8px #10b981,0 0 16px #10b981; color:#fff;} 50% { text-shadow:0 0 8px #a3e635,0 0 16px #a3e635; color:#fff;} 100% { text-shadow:0 0 8px #10b981,0 0 16px #10b981; color:#fff;} }
        .animated-site-title { background: linear-gradient(90deg, #38bdf8, #818cf8, #c084fc, #38bdf8); background-size: 300% 300%; -webkit-background-clip: text; -webkit-text-fill-color: transparent; animation: textGradient 3s linear infinite, titlePulse 2.5s ease-in-out infinite; display: inline-block; font-weight: 800; }
        .title-theme-fire { background: linear-gradient(90deg, #ff3300, #ff8800, #ffcc00, #ff3300) !important; background-size: 300% 300% !important; }
        .title-theme-ocean { background: linear-gradient(90deg, #0ea5e9, #22d3ee, #38bdf8, #0ea5e9) !important; background-size: 300% 300% !important; }
        .title-theme-neon { background: linear-gradient(90deg, #ec4899, #a855f7, #6366f1, #ec4899) !important; background-size: 300% 300% !important; }
        .title-theme-rainbow { background: linear-gradient(90deg, #ff0055, #ff8800, #ffee00, #00ffcc, #3388ff, #9900ff, #ff0055) !important; background-size: 400% 400% !important; }
        .title-theme-emerald { background: linear-gradient(90deg, #10b981, #22c55e, #a3e635, #10b981) !important; background-size: 300% 300% !important; }
        .rgb-card { border: 2px solid #ff0055 !important; animation: rgbBorder 4s linear infinite !important; }
        .rgb-text-glow { animation: rgbGlowText 3s linear infinite !important; }
        .rgb-theme-fire.rgb-card { animation: rgbBorderFire 2.6s ease-in-out infinite !important; }
        .rgb-theme-fire.rgb-text-glow { animation: rgbGlowTextFire 2.2s ease-in-out infinite !important; }
        .rgb-theme-ocean.rgb-card { animation: rgbBorderOcean 3s ease-in-out infinite !important; }
        .rgb-theme-ocean.rgb-text-glow { animation: rgbGlowTextOcean 2.6s ease-in-out infinite !important; }
        .rgb-theme-neon.rgb-card { animation: rgbBorderNeon 2.4s ease-in-out infinite !important; }
        .rgb-theme-neon.rgb-text-glow { animation: rgbGlowTextNeon 2s ease-in-out infinite !important; }
        .rgb-theme-emerald.rgb-card { animation: rgbBorderEmerald 2.8s ease-in-out infinite !important; }
        .rgb-theme-emerald.rgb-text-glow { animation: rgbGlowTextEmerald 2.4s ease-in-out infinite !important; }
        .anim-fade { animation: fadeIn 0.8s ease forwards; }
        .anim-slide-up { animation: slideUp 0.8s ease forwards; }
        .anim-slide-down { animation: slideDown 0.8s ease forwards; }
        .anim-slide-left { animation: slideInLeft 0.8s ease forwards; }
        .anim-slide-right { animation: slideInRight 0.8s ease forwards; }
        .anim-zoom { animation: zoomIn 0.6s ease forwards; }
        .anim-zoom-out { animation: zoomOut 0.6s ease forwards; }
        .anim-blur-in { animation: blurIn 0.9s ease forwards; }
        .anim-float { animation: floatAnim 3s ease-in-out infinite; }
        .anim-pulse { animation: pulseGlow 2s infinite; }
        .anim-heartbeat { animation: heartbeat 1.5s ease-in-out infinite; }
        .anim-flip { animation: flipIn 0.8s ease forwards; }
        .anim-flip-y { animation: flipY 0.9s ease forwards; }
        .anim-bounce { animation: bounceAnim 2s infinite; }
        .anim-shake { animation: shakeAnim 2s infinite; }
        .anim-rotate { animation: rotateAnim 10s linear infinite; }
        .anim-sparkle { animation: sparkleGlow 2s ease-in-out infinite; }
        .anim-swing { animation: swingAnim 2.5s ease-in-out infinite; transform-origin: top center; }
        .anim-wobble { animation: wobbleAnim 2s ease-in-out infinite; }
        .anim-glow-pulse { animation: glowPulseColor 3s ease-in-out infinite; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideInLeft { from { opacity: 0; transform: translateX(-30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes slideInRight { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes slideDown { from { opacity: 0; transform: translateY(-30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }
        @keyframes zoomOut { from { opacity: 0; transform: scale(1.2); } to { opacity: 1; transform: scale(1); } }
        @keyframes blurIn { from { opacity: 0; filter: blur(8px); } to { opacity: 1; filter: blur(0); } }
        @keyframes flipY { 0% { transform: perspective(400px) rotateY(90deg); opacity: 0; } 100% { transform: perspective(400px) rotateY(0); opacity: 1; } }
        @keyframes heartbeat { 0%, 100% { transform: scale(1); } 14% { transform: scale(1.08); } 28% { transform: scale(1); } 42% { transform: scale(1.08); } 70% { transform: scale(1); } }
    </style>
</head>
<body>
${cloneCanvas.innerHTML}
</body>
</html>`;

            const blob = new Blob([fullPageCode], { type: 'text/html' });
            const a = document.createElement('a');
            a.href = URL.createObjectURL(blob);
            a.download = `${currentPage}_page.html`;
            a.click();
        }
    </script>
</body>
</html>
