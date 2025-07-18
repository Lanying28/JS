<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>借势 实操手册</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>💡</text></svg>">
    <style>
        :root {
            --bg-color: #fcfaf5;
            --text-color: #3d3d3d;
            --heading-color: #2c2c2c;
            --accent-color: #b9975b; /* 赤金石色 */
            --accent-light-color: #f3e9d2;
            --border-color: #e0dace;
            --shadow-light: 0 4px 20px rgba(0,0,0,0.05);
            --shadow-medium: 0 6px 30px rgba(0,0,0,0.08);
            --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
            --font-serif: 'Georgia', 'Times New Roman', 'Kaiti SC', 'KaiTi', 'STKaiti', serif;
            --font-sans: 'Helvetica Neue', 'Arial', 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', sans-serif;
            --transition-speed: 0.3s ease;
        }

        /* 纸张纹理背景优化 */
        body {
            font-family: var(--font-sans);
            margin: 0;
            background-color: var(--bg-color);
            background-image: url('data:image/svg+xml,%3Csvg width="60" height="60" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg"%3E%3Cg fill="none" fill-rule="evenodd"%3E%3Cg fill="%23e0dace" fill-opacity="0.1"%3E%3Cpath d="M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z"/%3E%3C/g%3E%3C/g%3E%3C/svg%3E');
            color: var(--text-color);
            line-height: 1.9;
            font-size: 17px;
            padding-bottom: 80px;
        }

        /* 容器与布局优化 - 更聚焦的阅读宽度 */
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 50px 20px;
        }

        /* 头部装饰元素优化 - 更精致的比例 */
        .decor-element {
            position: absolute;
            width: 30px;
            height: 30px;
            border: 1px solid var(--border-color);
            z-index: 0;
            opacity: 0.7;
        }
        .top-left { top: 25px; left: 25px; border-right: none; border-bottom: none; }
        .top-right { top: 25px; right: 25px; border-left: none; border-bottom: none; }
        .bottom-left { bottom: 25px; left: 25px; border-right: none; border-top: none; }
        .bottom-right { bottom: 25px; right: 25px; border-left: none; border-top: none; }

        /* 头部样式优化 - 增强层次感 */
        header {
            text-align: center;
            margin-bottom: 80px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 40px;
            position: relative;
            z-index: 1;
            padding-top: 20px;
        }
        header::after {
            content: "";
            position: absolute;
            bottom: -1px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background-color: var(--accent-color);
        }
        header h1 {
            font-family: var(--font-serif);
            font-size: 3.2em;
            font-weight: 500;
            color: var(--heading-color);
            margin: 0 0 20px;
            line-height: 1.3;
            letter-spacing: -0.5px;
            position: relative;
            display: inline-block;
        }
        header p {
            font-size: 1.1em;
            color: var(--accent-color);
            margin-top: 10px;
            letter-spacing: 1px;
        }
        
        /* 阶段样式优化 - 更柔和的阴影与间距 */
        .phase {
            margin-bottom: 90px;
            background-color: #fff;
            border-radius: 12px;
            padding: 45px 50px;
            box-shadow: var(--shadow-light);
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .phase:not(#summary) { /* Keep other sections contained */
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }

        .phase:hover:not(#summary) {
            transform: translateY(-5px);
            box-shadow: var(--shadow-medium);
        }
        .phase::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 8px;
            height: 100%;
            background-color: var(--accent-color);
            opacity: 0.7;
        }
        
        .phase-title {
            font-family: var(--font-serif);
            font-size: 2.2em;
            font-weight: 500;
            color: var(--heading-color);
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 10px;
            margin-bottom: 40px;
            display: inline-block;
            position: relative;
            padding-right: 20px;
        }
        .phase-title span {
            font-size: 0.5em;
            font-family: var(--font-sans);
            color: #9d8a6b;
            display: block;
            margin-top: 5px;
            letter-spacing: 2px;
            font-weight: 400;
        }
        
        /* 步骤样式优化 - 更清晰的层级 */
        .step {
            margin-bottom: 55px;
            padding-left: 30px;
            border-left: 2px dotted var(--border-color);
            position: relative;
        }
        .step:last-child {
            margin-bottom: 0;
        }
        .step::before {
            content: "";
            position: absolute;
            left: -10px;
            top: 15px;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background-color: var(--accent-color);
            box-shadow: 0 0 0 4px rgba(185, 151, 91, 0.1);
        }
        
        .step-title {
            font-family: var(--font-serif);
            font-size: 1.5em;
            font-weight: 500;
            color: var(--heading-color);
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        .step-title .step-number {
            color: var(--accent-color);
            margin-right: 15px;
            border-right: 1px solid var(--border-color);
            padding-right: 15px;
            font-weight: 600;
        }
        
        /* 行动清单优化 - 更精致的复选框 */
        .checklist {
            list-style: none;
            padding-left: 0;
            margin-top: 20px;
        }
        .checklist li {
            margin-bottom: 18px;
            display: flex;
            align-items: flex-start;
            transition: color var(--transition-speed), transform 0.2s ease, opacity var(--transition-speed);
            padding: 10px 15px;
            border-radius: 8px;
        }
        .checklist li:last-child {
            margin-bottom: 0;
        }
        .checklist li.completed {
            color: #a9a9a9;
            text-decoration: line-through;
            opacity: 0.6; /* Optimization: De-emphasize completed items */
        }
        .checklist input[type="checkbox"] {
            display: none;
        }
        .checklist label {
            cursor: pointer;
            display: flex;
            align-items: flex-start;
            width: 100%;
        }
        .checklist .custom-checkbox {
            width: 22px;
            height: 22px;
            border: 2px solid var(--border-color);
            border-radius: 4px;
            margin-right: 15px;
            flex-shrink: 0;
            margin-top: 5px;
            transition: all var(--transition-speed);
            position: relative;
        }
        .checklist li.completed .custom-checkbox {
            background-color: var(--accent-color);
            border-color: var(--accent-color);
            animation: checkboxPulse 0.3s ease;
        }
        @keyframes checkboxPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        .checklist .custom-checkbox::after {
            content: '✓';
            color: white;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%) scale(0);
            font-size: 16px;
            font-weight: bold;
            transition: transform var(--transition-speed);
        }
        .checklist li.completed .custom-checkbox::after {
            transform: translate(-50%, -50%) scale(1);
        }

        strong, b {
            font-weight: 600;
            color: var(--accent-color);
        }
        
        /* 高亮样式优化 - 更自然的效果 */
        .highlight {
            background-color: var(--accent-light-color);
            padding: 2px 8px;
            border-radius: 4px;
            position: relative;
            display: inline-block;
            transition: all 0.3s ease;
        }
        .highlight:hover {
            background-color: rgba(243, 233, 210, 0.8);
            transform: translateY(-2px);
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        .highlight::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background-color: rgba(185, 151, 91, 0.2);
            z-index: -1;
        }

        /* 战略便签优化 - 更舒适的书写区域 */
        .notes-area {
            margin-top: 40px;
            padding: 30px;
            background-color: #ffffff;
            border: 1px solid var(--border-color);
            border-radius: 10px;
            box-shadow: var(--shadow-light);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .notes-area::before {
            content: "“";
            position: absolute;
            top: 10px;
            right: 20px;
            font-size: 80px;
            color: rgba(224, 218, 206, 0.1);
            font-family: Georgia, serif;
            line-height: 1;
        }
        .notes-area:hover {
            box-shadow: var(--shadow-medium);
            border-color: rgba(185, 151, 91, 0.3);
        }
        .notes-area h4 {
            font-family: var(--font-serif);
            font-size: 1.2em;
            margin-top: 0;
            color: var(--heading-color);
            border-bottom: 1px dashed var(--border-color);
            padding-bottom: 15px;
            display: flex;
            align-items: center;
        }
        .notes-area h4::before {
            content: "📝";
            margin-right: 10px;
        }
        .notes-area textarea {
            width: 100%;
            height: 160px;
            border: none;
            background: transparent;
            font-family: var(--font-sans);
            font-size: 16px;
            line-height: 1.8;
            resize: vertical;
            outline: none;
            color: var(--text-color);
            padding: 5px 0;
            transition: all 0.3s ease;
        }
        .notes-area textarea:focus {
            border-left: 3px solid var(--accent-color);
            padding-left: 10px;
        }

        /* 目录导航优化 - 更清晰的导航体验 */
        .toc {
            background-color: #fff;
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 60px;
            box-shadow: var(--shadow-light);
            border: 1px solid var(--border-color);
        }
        .toc h3 {
            font-family: var(--font-serif);
            color: var(--heading-color);
            margin-top: 0;
            margin-bottom: 20px;
            font-size: 1.5em;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border-color);
        }
        .toc ul {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
        }
        .toc li {
            flex: 1;
            min-width: 200px;
        }
        .toc a {
            color: var(--text-color);
            text-decoration: none;
            display: flex;
            align-items: center;
            transition: all 0.3s ease;
            padding: 8px 12px;
            border-radius: 6px;
        }
        .toc a:hover {
            color: var(--accent-color);
            background-color: rgba(243, 233, 210, 0.2);
        }
        .toc a::before {
            content: "→";
            margin-right: 10px;
            color: var(--accent-color);
            opacity: 0.7;
            transition: transform 0.3s ease;
        }
        .toc a:hover::before {
            transform: translateX(5px);
        }
        
        /* 页脚优化 - 更精致的分隔 */
        footer {
            text-align: center;
            padding: 50px 20px;
            margin-top: 80px;
            color: #b0a99a;
            font-size: 0.9em;
            border-top: 1px solid var(--border-color);
            position: relative;
        }
        footer::before {
            content: "";
            position: absolute;
            top: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background-color: var(--accent-color);
            opacity: 0.5;
            border-radius: 3px;
        }
        footer p {
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.8;
        }
        
        /* 平滑滚动保持 */
        html {
            scroll-behavior: smooth;
        }

        /* 进度指示器优化 - 更细微的提示 */
        .progress-container {
            position: fixed;
            top: 0;
            z-index: 1001;
            width: 100%;
            height: 3px;
            background: transparent;
        }
        .progress-bar {
            height: 3px;
            background: var(--accent-color);
            width: 0%;
            transition: width 0.2s ease;
        }

        /* === PIANO KEYS SECTION STYLES START === */
        #summary.phase {
            max-width: none;
            width: 100%;
            background: #212529; /* Dark canvas background */
            padding: 80px 4vw;
            margin-bottom: 90px;
            border: none;
            border-bottom: 4px solid var(--accent-color);
            overflow: hidden;
            border-radius: 0; /* Full-width section shouldn't have rounded corners */
        }
        #summary.phase::before {
            display: none; /* Hide the left accent bar for this section */
        }
        
        #summary .phase-title {
            color: #ffffff;
            text-align: center;
            margin: 0 auto 60px auto;
            display: table;
            border-bottom-color: rgba(185, 151, 91, 0.5);
        }
        #summary .phase-title span {
            color: rgba(255,255,255,0.5);
        }

        .piano-container {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 25px;
            max-width: 1600px;
            margin: 0 auto;
        }

        .piano-key {
            border-radius: 8px;
            padding: 25px 20px;
            box-sizing: border-box;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            position: relative;
        }
        
        .piano-key.white-key {
            background: #f8f9fa;
            color: var(--text-color);
            border: 1px solid #dee2e6;
        }

        .piano-key.black-key {
            background: #343a40;
            color: #f8f9fa;
            border: 1px solid #495057;
        }

        .piano-key:hover {
            transform: translateY(-10px) scale(1.03);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            z-index: 10;
        }
        
        .key-header {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            margin-bottom: 15px;
            flex-shrink: 0;
        }

        .key-icon {
            width: 40px;
            height: 40px;
            margin-bottom: 10px;
        }
        .white-key .key-icon { color: var(--accent-color); }
        .black-key .key-icon { color: var(--accent-light-color); }

        .key-title {
            font-family: var(--font-serif);
            font-size: 1.5rem;
            font-weight: 600;
            line-height: 1.2;
        }
        .white-key .key-title { color: var(--heading-color); }
        .black-key .key-title { color: #ffffff; }

        .key-logic {
            font-size: 0.85rem;
            font-style: italic;
            text-align: center;
            padding-bottom: 15px;
            margin-bottom: 15px;
            flex-shrink: 0;
        }
        .white-key .key-logic {
            color: #6c757d;
            border-bottom: 1px solid var(--border-color);
        }
        .black-key .key-logic {
            color: #adb5bd;
            border-bottom: 1px solid #495057;
        }

        .key-points {
            list-style: none;
            padding-left: 0;
            margin: 0;
            flex-grow: 1; /* Allow list to take remaining space */
        }
        .key-points li {
            position: relative;
            padding-left: 18px;
            margin-bottom: 8px;
            font-size: 0.9rem;
            line-height: 1.6;
        }
        .key-points li::before {
            content: '•';
            position: absolute;
            left: 0;
            top: -1px;
            font-size: 1.2rem;
        }
        .white-key .key-points li::before { color: var(--accent-color); }
        .black-key .key-points li::before { color: var(--accent-light-color); }
        
        /* Responsive Piano Grid */
        @media (max-width: 1200px) {
            .piano-container {
                grid-template-columns: repeat(3, 1fr);
                gap: 20px;
            }
        }
        @media (max-width: 768px) {
            .piano-container {
                grid-template-columns: repeat(2, 1fr);
            }
        }
         @media (max-width: 576px) {
            .piano-container {
                grid-template-columns: repeat(1, 1fr);
            }
        }
        /* === PIANO KEYS SECTION STYLES END === */

         /* General Responsive Overrides */
        @media (max-width: 768px) {
            body { 
                font-size: 16px; 
                padding-bottom: 50px;
            }
            
            .container { padding: 30px 15px; }
            header { margin-bottom: 60px; padding-bottom: 30px; }
            header h1 { font-size: 2.2em; }
            .toc { padding: 20px; margin-bottom: 40px; }
            .toc ul { flex-direction: column; gap: 10px; }
            .toc li { min-width: auto; }
            
            .phase:not(#summary) { padding: 30px 25px; margin-bottom: 70px; }
            .phase-title { font-size: 1.8em; padding-right: 0; }
            .step { margin-bottom: 40px; padding-left: 15px; }
            .step-title { font-size: 1.3em; }
            .notes-area { padding: 20px; }
            .notes-area textarea { height: 140px; }
            footer { padding: 30px 15px; }
        }

        /* === NEWLY ADDED UTILITY STYLES START === */
        .footer-watermark {
            position: fixed;
            bottom: 24px;
            left: 24px;
            font-size: 0.875rem;
            color: #b0a99a;
            opacity: 0.7;
            z-index: 999;
            pointer-events: none;
            line-height: 1.6;
        }
        .footer-watermark p {
            margin: 0;
        }
        
        .back-to-top {
            position: fixed;
            bottom: 24px;
            right: 24px;
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background-color: var(--accent-color);
            color: white;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: var(--shadow-medium);
            transition: all 0.3s ease;
            opacity: 0;
            visibility: hidden;
            z-index: 1000;
        }

        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            background-color: #9d8a6b;
            transform: translateY(-4px);
        }
        /* === NEWLY ADDED UTILITY STYLES END === */

    </style>
</head>
<body>
    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <div class="container">
        <header>
            <div class="decor-element top-left"></div>
            <div class="decor-element top-right"></div>
            <div class="decor-element bottom-left"></div>
            <div class="decor-element bottom-right"></div>
            <h1>借势：实操手册</h1>
            <p>金枪大叔</p>
        </header>
    </div>
    
    <section id="summary" class="phase">
        <h2 class="phase-title">以弱胜强的黄金法则</h2>
        <div id="dashboard"></div>
    </section>

    <div class="container">
        <div class="toc">
            <ul>
                <li><a href="#phase-1">模块一：核心心法与战略定位</a></li>
                <li><a href="#phase-2">模块二：品牌冷启动与定位</a></li>
                <li><a href="#phase-3">模块三：增长飞轮与护城河</a></li>
                <li><a href="#phase-4">模块四：品牌生命周期管理</a></li>
                <li><a href="#phase-5">模块五：创始人与团队心经</a></li>
                <li><a href="#phase-6">模块六：终极战略</a></li>
            </ul>
        </div>
        
        <main>
            <section id="phase-1" class="phase">
                <h2 class="phase-title">模块一: 核心心法与战略定位 <span>Core Principles & Strategy</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">01</span> 核心比喻：语言是钉子，视觉是锤子</h3>
                    <p>您的每一个营销动作，都必须想清楚：我的“钉子”（核心广告语）是什么？我的“锤子”（主视觉、Logo、产品包装）是什么？二者必须协同，才能将品牌信息牢牢钉入用户心智。</p>
                </div>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">02</span> 商业模式评估：三流生意自检</h3>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>一流生意</strong>：每天都能赚钱 (如水、电、高频消费品)。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>二流生意</strong>：每个月都能赚钱 (如会员费、话费)。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>三流生意</strong>：每年才赚一次钱 (如广告项目)。</span></label></li>
                    </ul>
                    <p><strong>战略启示</strong>：思考如何将您的“三流生意”向“一流生意”改造，增加用户复购和日常互动。</p>
                </div>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">03</span> 生存空间选择：暗度陈仓法则</h3>
                    <p>对于初创企业，<span class="highlight">“做大不如做小，做小不如做精”</span>。 不要一开始就挑战巨头林立的主战场，而是寻找一个细分、被忽视的小市场，利用“暗度陈仓”的策略，避开竞争，获得宝贵的生存和发展空间。</p>
                </div>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块一</h4>
                    <textarea placeholder="在此记录下我关于核心战略的思考..."></textarea>
                </div>
            </section>
            
            <section id="phase-2" class="phase">
                <h2 class="phase-title">模块二: 品牌冷启动与定位 <span>Launch & Positioning</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">04</span> 自我诊断清单</h3>
                    <p><strong>价格锚点诊断</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>低端市场</strong>：强调 “省”。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>中端市场</strong>：强调 “专业 / 档次”。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>高端市场</strong>：强调 “文化 / 大师” (如“火锅大师”)。</span></label></li>
                    </ul>
                    <p style="margin-top:20px;"><strong>品牌情绪设定</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>初创品牌（推荐）</strong>：选择 <span class="highlight">“愤怒”</span>，借此获得关注。 <strong>行动项</strong>：找到行业里最让消费者不满的潜规则，并愤怒地指出来。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>低端品牌</strong>：选择 “快乐”。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>中端品牌</strong>：选择 “温柔”。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>高端品牌</strong>：选择 “伤感”。</span></label></li>
                    </ul>
                </div>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">05</span> 核心记忆点打造</h3>
                    <p><strong>品牌命名自检</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>名字是否等于品类？ (如“铂爵旅拍”)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>名字是否等于卖点？ (如“白加黑”)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>公式应用</strong>：可尝试“品牌名 + 核心差异点”的组合，如“Ulike蓝宝石脱毛仪”。</span></label></li>
                    </ul>
                     <p style="margin-top:20px;"><strong>一句话广告语创作</strong></p>
                     <p><strong>公式一：颠覆潜规则法。</strong>写下行业痛点，用一句“熟悉又陌生”的话颠覆它 (如“找工作，我要跟老板谈”)。</p>
                     <p><strong>公式二：激活潜台词法。</strong>不要只说功能，要把用户深层的欲望喊出来 (如“高级女人用高级的”)。</p>

                    <p style="margin-top:20px;"><strong>品牌故事万能公式</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第一步：卖惨</strong>。讲述一个令人同情的困境或痛点。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第二步：绝处逢生</strong>。描述一个戏剧性的转机或获得“秘方”的经历。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第三步：大爱分享</strong>。将成果普惠大众，塑造利他、有情怀的品牌形象。</span></label></li>
                    </ul>
                </div>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">06</span> 制造第一波声量</h3>
                     <p><strong>创造“流行”三要素</strong></p>
                     <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>足够叛逆</strong>：敢于挑战主流，引发足够多的反对和讨论。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>足够丑（有符号性）</strong>：设计要有强烈的、甚至略带争议的视觉符号。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>创造门槛</strong>：让大多数人感觉“预算不足”或难以获得，稀缺性是流行的底层代码。</span></label></li>
                    </ul>
                     <p style="margin-top:20px;"><strong>病毒式内容“流量密码”清单</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>美女</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>致富经</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>心灵鸡汤</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>底层逆袭</span></label></li>
                    </ul>
                </div>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块二</h4>
                    <textarea placeholder="在此规划我的品牌启动方案..."></textarea>
                </div>
            </section>

            <section id="phase-3" class="phase">
                <h2 class="phase-title">模块三: 增长飞轮与护城河 <span>Growth & Moat</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">07</span> 驾驭对手与争议</h3>
                     <p><strong>“黑粉”管理手册</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>识别“粉刺”</strong>：收集负面评价，它们是真实的痛点反馈。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>主动示弱</strong>：公开自嘲一个无伤大雅的缺点，会显得真实可爱，拉近心理距离。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>风格确立</strong>：将“黑粉”讨厌的点，强化为您的品牌风格，以此吸引“铁粉”。</span></label></li>
                    </ul>
                     <p style="margin-top:20px;"><strong>“制造刚需”三步公式</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第一步：树立对手</strong>。告诉用户：“您最讨厌/羡慕的人都在用了。”</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第二步：设置时间炸弹</strong>。告诉用户：“再不行动就晚了/没了。”</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>第三步：承诺终极利益</strong>。告诉用户：“拥有它，您就是人生赢家。”</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">08</span> 渗透用户心智</h3>
                     <p><strong>人性弱点激活清单</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>激活任性</strong>：文案多用“我要……”句式，赋予用户主导权。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>激活贪心</strong>：利用性价比、限时折扣等，让用户感觉“赚到了”。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>激活虚荣心</strong>：将产品与身份、品位挂钩，创造社交优越感。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>激活遗憾</strong>：用“最后一件”、“限时限量”等话术，制造稀缺。</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">09</span> 建立商业护城河</h3>
                     <p><strong>抬高行业门槛三法</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>资金门槛</strong>：用足够的钱砸出护城河。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>技术门槛</strong>：拥有垄断性技术，或用<span class="highlight">文化和审美</span>作为壁垒。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>时间门槛</strong>：在一个低利润行业长期坚持，成为“剩者为王”。</span></label></li>
                    </ul>
                     <p style="margin-top:20px;"><strong>“B+C双轮驱动”战略</strong></p>
                    <p>一个To B品牌和一个To C个人IP可以互为背书，形成强大合力。 To C内容为To B业务引流，To B业务为To C内容提供权威案例。</p>
                </div>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块三</h4>
                    <textarea placeholder="在此规划我的增长策略与护城河..."></textarea>
                </div>
            </section>
            
             <section id="phase-4" class="phase">
                <h2 class="phase-title">模块四: 品牌生命周期管理 <span>Lifecycle Management</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">10</span> “产品卖不动”升级三板斧</h3>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>升级价值观</strong>：重新定义购买理由，拔高品牌段位。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>升级包装</strong>：更新Logo、店面设计，审美领先潮流10%。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>升级代言人</strong>：检查您的代言人是否已“老了”或形象不符。</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">11</span> “品牌老化”焕新工具箱</h3>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>视觉年轻化 (漫画、插画)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>话语叛逆化 (说大狠话)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>代言人迭代 (签约流量明星)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>跨界联名 (找风马牛不相及的品牌)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>玩法潮流化 (推出盲盒)</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">12</span> “品牌末期”残值最大化策略</h3>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>营销技术迭代</strong>：产品不变，但广告、营销概念要不断翻新。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>多版本策略</strong>：不停地换颜色、换材质，推出各种限量版。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>降维打击</strong>：推出“简配青春版”，去蚕食中低端市场。</span></label></li>
                    </ul>
                </div>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块四</h4>
                    <textarea placeholder="在此记录我的品牌管理与升级计划..."></textarea>
                </div>
            </section>
            
             <section id="phase-5" class="phase">
                <h2 class="phase-title">模块五: 创始人与团队心经 <span>Founder & Team</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">13</span> 创始人个人品牌与修炼</h3>
                     <p><strong>角色渗透自省</strong>：创始人的性格决定品牌特质 (如雷军的“抠门”成就了小米的性价比)。 需反思个人性格对品牌的利弊。</p>
                     <p style="margin-top:20px;"><strong>寻找“三个贵人”</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>偶像</strong>：为您指明方向。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>伯乐</strong>：发现您的潜力。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>债主</strong>：倒逼您的成长。</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">14</span> 合作与避坑</h3>
                     <p><strong>“危险客户”识别清单</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>“老子天下第一”型</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>“华丽辞藻”型</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>“伸手党”型</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>“白嫖”型</span></label></li>
                    </ul>
                     <p style="margin-top:20px;"><strong>客户“砍价”信号识别</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>谈情怀、理想 -> 准备八折。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>讲奋斗史、泛泪花 -> 底线五折。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span>说“兄弟，入股吧” -> 一分钱不想出。</span></label></li>
                    </ul>
                    <p style="margin-top:20px;"><strong>合作第一铁律</strong>：<span class="highlight">定金为王</span>。不交定金的生意99%会黄。</p>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">15</span> 团队与招募</h3>
                     <p><strong>学会拒绝的艺术</strong>：为保证精力聚焦，必须学会拒绝<span class="highlight">无效社交、陌生赛道投资和人情绑架</span>。</p>
                     <p style="margin-top:20px;"><strong>人才分层</strong></p>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>重点招募“上等人才”</strong>：他们能“先知先觉”，洞察趋势，借力打力。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>培养“中等人才”</strong>：他们能“自知自觉”，在失败后能自我驱动，快速爬起。</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>避开“下等人才”</strong>：他们“不知不觉”，油盐不进，会成为团队的负资产。</span></label></li>
                    </ul>
                </div>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块五</h4>
                    <textarea placeholder="在此记录我的管理心得与反思..."></textarea>
                </div>
            </section>
            
             <section id="phase-6" class="phase">
                <h2 class="phase-title">模块六: 终极战略 <span>Ultimate Strategy</span></h2>
                <div class="step">
                    <h3 class="step-title"><span class="step-number">16</span> 新国货“最优路线”地理布局法</h3>
                    <ul class="checklist">
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>品牌注册 -> 上海</strong> (借时尚心智)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>市场营销 -> 北京</strong> (借信息高地)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>电商运营 -> 杭州</strong> (借人才资源)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>供应链 -> 广州</strong> (借制造优势)</span></label></li>
                        <li><label><input type="checkbox"><span class="custom-checkbox"></span><span><strong>投放测试 -> 成都</strong> (借消费文化)</span></label></li>
                    </ul>
                </div>
                 <div class="step">
                    <h3 class="step-title"><span class="step-number">17</span> 终极目标：从“借势”到“造势”</h3>
                    <p>借势是起步的巧劲，但品牌的终局是<span class="highlight">让自己成为那个被借的“势”</span>。 当您的品牌成为一个强大的文化IP或认知锚点时，就完成了从“借”到“造”的升级。</p>
                <div class="notes-area">
                    <h4>我的战略便签 | 模块六</h4>
                    <textarea placeholder="在此构想我的终局模式与扩张蓝图..."></textarea>
                </div>
            </section>
        </main>
    </div>
    

    <div class="footer-watermark"> 
        <p>BCRI｜商业认知研究院</p> 
        <p>Week191共学周</p> 
    </div>

    <button class="back-to-top" id="back-to-top" aria-label="回到顶部">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="18 15 12 9 6 15"></polyline>
        </svg>
    </button>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // === PIANO KEYS RENDERING SCRIPT START ===
            const strategies = [
                { title: "借定势", logic: "不创造认知, 只借用认知", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2L12 10M12 22L12 18M20 12L17 12M7 12L4 12M12 22A6 6 0 0 0 12 10A6 6 0 0 0 12 22zM12 10A6 6 0 0 1 12 22"></path><circle cx="12" cy="2" r="2" stroke-width="1.5" fill="var(--bg-color)"></circle></svg>`, points: ["品牌锚点: 按价格分层", "品牌情绪: 高端伤感", "品牌关系: 高端上下级", "老化与升级: 联名等"] },
                { title: "借万物", logic: "不平地抠饼, 只借用万物", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2v2m-6 6H4m16 0h-2M12 20v2M7 7l-2 2m14-2l-2 2m0 10l2 2m-14 0l2 2"></path><circle cx="12" cy="12" r="4.5"></circle><path d="M12 2a10 10 0 1 0 10 10"></path></svg>`, points: ["借力打力: 蹭热点、借权威", "贩卖情怀: 讲故事、复古IP", "美人经济: 降低用户警惕性", "暗度陈仓: 做小做精避竞争"] },
                { title: "借噪声", logic: "不纠结和声, 只借用噪声", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M21 12H16M3 12h1m8-9v2m0 14v2M7.5 7.5L6 6m12 0l-1.5 1.5M6 18l1.5-1.5m10.5 0l1.5 1.5"></path><path d="M12 4L4 8v8l8 4 8-4V8l-8-4z"></path><path d="M4 8l8 4 8-4"></path><path d="M12 16V4"></path></svg>`, points: ["以弱胜强: 细分战场, 局部优势", "无须定位: 先定价, 再谈定位", "客户红利: 投资思维服务客户", "至暗时刻: 情感溢价的资产"] },
                { title: "借感性", logic: "不追求理性, 只借用感性", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>`, points: ["取名技巧: 关联品类、卖点", "文案段位: 引发共鸣", "讲故事公式: 卖惨→逢生→分享", "角色渗透: 创始人性格"] },
                { title: "借趋势", logic: "不迷信永生, 只借用周期", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline><polyline points="17 6 23 6 23 12"></polyline></svg>`, points: ["时代风口: 三大生意心", "内卷破局: 三大共鸣", "个体创业: 三化机遇", "生命周期: 风口期做品牌"] },
                { title: "借杠杆", logic: "不突出优点, 只借用缺点", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M12 3v18M3 12h18"></path><path d="M16 16l-4-4-4 4"></path><path d="M8 8l4 4 4-4"></path></svg>`, points: ["信任背书: 五大来源", "创造优越感: 三大方法", "抬高门槛: 资金、技术、时间", "超我生意: 宏大叙事"] },
                { title: "借对手", logic: "不讨好铁粉, 只借用黑粉", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M23 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>`, points: ["创造流行: 叛逆、够丑、门槛", "制造矛盾: 提炼差异化", "主动示弱: 拉近距离", "缺陷价值: 争议胜于完美"] },
                { title: "借智慧", logic: "不拼体力, 只借用脑力", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"></path><path d="M9.09 9a3 3 0 0 1 5.83 1c0 1.66-1.34 3-3 3v1"></path><line x1="12" y1="18" x2="12.01" y2="18"></line></svg>`, points: ["破圈技术: 三化心法", "流量密码: 四大类型", "运营创意: 值钱的创意", "学会拒绝: 三种无效"] },
                { title: "借偏见", logic: "不尊重共识, 只借用偏见", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line><line x1="11" y1="8" x2="11" y2="14"></line><line x1="8" y1="11" x2="14" y2="11"></line></svg>`, points: ["人性弱点: 任性、贪心、虚荣", "群体心智: 富婆、宝妈、宅男", "消费冲动: 设计、社交驱动", "认知偏误: 幸存者偏差"] },
                { title: "借视角", logic: "不谦卑仰视, 只借用神之俯视", icon: `<svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>`, points: ["三流生意: 按赚钱周期分", "克服自卑: 三种方法", "三个贵人: 偶像、伯乐、债主", "人才分层: 三种境界"] }
            ];
            
            function renderPianoKeys() {
                const container = document.getElementById('dashboard');
                if (!container) return;

                const pianoContainer = document.createElement('div');
                pianoContainer.className = 'piano-container';
                
                strategies.forEach((strategy, index) => {
                    const key = document.createElement('div');
                    const keyType = index % 2 === 0 ? 'white-key' : 'black-key';
                    key.className = `piano-key ${keyType}`;
                    
                    const pointsHTML = strategy.points.map(point => `<li>${point}</li>`).join('');

                    key.innerHTML = `
                        <div class="key-header">
                            <div class="key-icon">${strategy.icon}</div>
                            <h3 class="key-title">${strategy.title}</h3>
                        </div>
                        <p class="key-logic">${strategy.logic}</p>
                        <ul class="key-points">
                            ${pointsHTML}
                        </ul>
                    `;
                    pianoContainer.appendChild(key);
                });

                container.appendChild(pianoContainer);
            }

            renderPianoKeys();
            // === PIANO KEYS RENDERING SCRIPT END ===


            // 检查项交互保持
            const checklistItems = document.querySelectorAll('.checklist li');
            checklistItems.forEach(item => {
                const checkbox = item.querySelector('input[type="checkbox"]');
                item.addEventListener('click', (e) => {
                    if(e.target.tagName.toLowerCase() !== 'input' && e.target.tagName.toLowerCase() !== 'label' ){
                        checkbox.checked = !checkbox.checked;
                    }
                    if (checkbox.checked) {
                        item.classList.add('completed');
                    } else {
                        item.classList.remove('completed');
                    }
                });
            });

            // 滚动动画增强 & 回到顶部按钮
            const backToTopButton = document.getElementById('back-to-top');

            const handleScroll = () => {
                // Animate sections
                const elementsToAnimate = document.querySelectorAll('.phase');
                elementsToAnimate.forEach(el => {
                    const elTop = el.getBoundingClientRect().top;
                    const windowHeight = window.innerHeight;
                    if (elTop < windowHeight * 0.9) {
                        el.style.opacity = '1';
                        el.style.transform = 'translateY(0)';
                    }
                });

                // Progress bar
                const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
                const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
                const scrolled = (winScroll / height) * 100;
                document.getElementById("progressBar").style.width = scrolled + "%";

                // Back to top button visibility
                if (window.pageYOffset > 300) {
                    if(backToTopButton) backToTopButton.classList.add('visible');
                } else {
                    if(backToTopButton) backToTopButton.classList.remove('visible');
                }
            };
            
            document.querySelectorAll('.phase').forEach(el => {
                el.style.opacity = '0';
                el.style.transform = 'translateY(20px)';
                el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            });

            window.addEventListener('scroll', handleScroll);
            handleScroll(); // Initial check

            // Back to top click event
            if(backToTopButton) {
                backToTopButton.addEventListener('click', () => {
                    window.scrollTo({
                        top: 0,
                        behavior: 'smooth'
                    });
                });
            }
        });
    </script>
</body>
</html>
