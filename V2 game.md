# 遊戲程式碼與開發文檔 (Game Code & Documentation)

專案名稱：The City That Lost Its Thought (失去思考的城市)
技術棧：HTML5, CSS3 (Tailwind CSS + Custom CSS), Vanilla JavaScript
架構：單一文件 (Single-file Web App)，無需伺服器即可在任何現代瀏覽器中運行。

## 1. 架構解析 (Architecture Overview)

遊戲完全建立在一個 `.html` 檔案中，分為三個主要部分：

1. **`<head>` (樣式與設置):** 載入 Tailwind CSS 框架，定義自定義字體 (Nunito, Inter)，以及處理背景圖片、角色浮動動畫和打字機游標效果的自定義 CSS。

2. **`<body>` (UI 結構):** 包含遊戲的所有介面層（層疊式設計）：
   * `stats-bar`: 頂部狀態列（顯示玩家屬性：Dependence 和 Thinking）。
   * `start-screen`: 開始畫面。
   * `scene-area`: 角色與背景顯示區。
   * `ui-layer`: 對話框與選擇按鈕區。
   * `end-screen`: 結局畫面。

3. **`<script>` (遊戲邏輯):** 控制遊戲流程、分數計算、打字機特效以及結局判定。

## 2. 核心邏輯說明 (Core Logic Explained)

* **數據狀態 (`stats`)**:
  使用一個 JavaScript Object 來追蹤玩家的數值：`dependence` (依賴) 和 `thinking` (思考)。
* **計分機制**:
  * 選項 A: Dependence +0, Thinking +0
  * 選項 B: Dependence +1, Thinking +1
  * 選項 C: Dependence +2, Thinking +2
* **結局判定 (`showEnding`)**:
  當玩家到達最後一個選項並觸發 `ENDING` 時，系統會根據總分 (`stats.thinking` 或 `stats.dependence`，兩者分數同步) 決定結局：
  * **6 分 (全部選 C)**: 真結局 (The Creator)
  * **5 分**: 結局 3 (The Wise User)
  * **3-4 分**: 結局 2 (The Half-Dependent)
  * **0-2 分**: 結局 1 (The Unthinking Person)

## 3. 完整原始碼 (Complete Source Code)

你可以將以下所有程式碼複製並貼上到一個名為 `game.html` 的檔案中即可運行。請確保你生成的背景圖片 (`1.png` 到 `7.png`) 與這個 HTML 檔案放在**同一個資料夾**內。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The City That Lost Its Thought</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Nunito:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Nunito', 'Inter', sans-serif;
            background-color: #1a1a2e;
            color: white;
            overflow: hidden; /* 防止視窗滾動 */
            touch-action: manipulation;
        }

        /* 遊戲場景背景圖片綁定 */
        .bg-city-day { background-image: url('1.png') !important; background-size: cover; background-position: center; }
        .bg-classroom { background-image: url('7.png') !important; background-size: cover; background-position: center; }
        .bg-lab { background-image: url('6.png') !important; background-size: cover; background-position: center; }
        .bg-park { background-image: url('5.png') !important; background-size: cover; background-position: center; }
        .bg-blackout { background-image: url('4.png') !important; background-size: cover; background-position: center; }
        .bg-ruins { background-image: url('3.png') !important; background-size: cover; background-position: center; }
        .bg-future { background-image: url('2.png') !important; background-size: cover; background-position: center; }

        /* 對話框樣式 */
        .dialog-box {
            background: rgba(15, 23, 42, 0.85);
            border: 4px solid #38bdf8;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5), inset 0 0 15px rgba(56, 189, 248, 0.3);
            backdrop-filter: blur(10px);
        }

        /* 角色浮動動畫 */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
        .sprite-float {
            animation: float 4s ease-in-out infinite;
        }

        /* 按鈕懸停效果 */
        .choice-btn {
            transition: all 0.2s;
            background: rgba(30, 41, 59, 0.9);
            border: 2px solid #94a3b8;
        }
        .choice-btn:hover {
            transform: scale(1.02) translateX(10px);
            background: #38bdf8;
            border-color: #bae6fd;
            color: #0f172a;
            box-shadow: 0 0 15px rgba(56,189,248,0.5);
        }

        /* 打字機閃爍游標 */
        .cursor::after {
            content: '▼';
            animation: blink 1s step-start infinite;
            margin-left: 5px;
            color: #38bdf8;
            font-size: 0.8em;
        }
        @keyframes blink { 50% { opacity: 0; } }

        /* 停電時的文字故障特效 */
        .glitch-text {
            color: red;
            text-shadow: 2px 2px 0px #0ff, -2px -2px 0px #f0f;
            animation: glitch 0.2s linear infinite;
        }
        @keyframes glitch {
            0% { transform: translate(0) }
            20% { transform: translate(-2px, 2px) }
            40% { transform: translate(-2px, -2px) }
            60% { transform: translate(2px, 2px) }
            80% { transform: translate(2px, -2px) }
            100% { transform: translate(0) }
        }

        /* 淡入動畫 */
        .fade-in { animation: fadeIn 0.5s ease-in; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body class="h-screen w-screen flex justify-center items-center bg-black">

    <!-- 遊戲主要容器 -->
    <div id="game-container" class="relative w-full max-w-4xl h-full max-h-[800px] sm:h-[90vh] sm:rounded-2xl overflow-hidden shadow-2xl transition-all duration-1000 flex flex-col bg-gray-900 bg-city-day">
        
        <!-- 頂部屬性狀態列 -->
        <div id="stats-bar" class="absolute top-0 left-0 w-full p-3 sm:p-4 flex flex-wrap justify-center gap-4 text-xs sm:text-sm font-bold z-20 hidden backdrop-blur-md bg-black/40 border-b border-white/20">
            <div class="bg-blue-900/80 border-2 border-blue-500 text-blue-100 px-4 py-1 sm:py-1.5 rounded-full shadow-[0_0_10px_rgba(59,130,246,0.5)] flex items-center gap-2">
                Dependence: <span id="stat-dep" class="text-blue-300 text-sm sm:text-base">0</span>
            </div>
            <div class="bg-green-900/80 border-2 border-green-500 text-green-100 px-4 py-1 sm:py-1.5 rounded-full shadow-[0_0_10px_rgba(34,197,94,0.5)] flex items-center gap-2">
                Thinking: <span id="stat-think" class="text-green-300 text-sm sm:text-base">0</span>
            </div>
        </div>

        <!-- 開始畫面 -->
        <div id="start-screen" class="absolute inset-0 flex flex-col justify-center items-center z-50 bg-gray-900 fade-in">
            <div class="text-center p-8 backdrop-blur-md bg-black/50 rounded-3xl border border-white/20 shadow-2xl">
                <h1 class="text-4xl sm:text-6xl font-extrabold mb-4 text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-500 drop-shadow-lg">
                    The City That Lost Its Thought
                </h1>
                <p class="text-xl text-gray-200 mb-8 italic drop-shadow-md">An Interactive Story about AI Literacy</p>
                <button onclick="startGame()" class="px-8 py-4 bg-blue-600 hover:bg-blue-500 text-white rounded-full font-bold text-xl shadow-[0_0_20px_rgba(37,99,235,0.7)] transition-all hover:scale-105 border-2 border-blue-400">
                    Start Game
                </button>
            </div>
        </div>

        <!-- 場景與角色顯示區 -->
        <div id="scene-area" class="flex-1 relative w-full flex justify-center items-end pb-48 sm:pb-64 z-10 hidden">
            <!-- Spark AI 角色 SVG -->
            <div id="character-sprite" class="sprite-float transition-opacity duration-300">
                <svg id="spark-svg" width="200" height="200" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="100" cy="100" r="60" fill="white" stroke="#38bdf8" stroke-width="8"/>
                    <circle cx="80" cy="90" r="10" fill="#0f172a"/>
                    <circle cx="120" cy="90" r="10" fill="#0f172a"/>
                    <path d="M 85 120 Q 100 130 115 120" stroke="#38bdf8" stroke-width="6" stroke-linecap="round"/>
                    <circle cx="100" cy="20" r="15" fill="#facc15"/>
                    <path d="M 100 35 L 100 40" stroke="#facc15" stroke-width="4"/>
                    <ellipse cx="100" cy="100" rx="90" ry="30" stroke="#bae6fd" stroke-width="2" stroke-dasharray="10 10" transform="rotate(20 100 100)"/>
                    <ellipse cx="100" cy="100" rx="90" ry="30" stroke="#bae6fd" stroke-width="2" stroke-dasharray="10 10" transform="rotate(-20 100 100)"/>
                </svg>
            </div>
        </div>

        <!-- UI 互動層 (對話框與選項) -->
        <div id="ui-layer" class="absolute bottom-0 w-full p-4 sm:p-6 z-30 hidden flex-col justify-end h-full pointer-events-none">
            <!-- 選項按鈕容器 -->
            <div id="choices-container" class="flex flex-col gap-3 mb-4 pointer-events-auto items-center w-full max-w-2xl mx-auto">
            </div>

            <!-- 對話框本體 -->
            <div id="dialog-wrapper" class="dialog-box w-full max-w-4xl mx-auto p-4 sm:p-6 relative pointer-events-auto cursor-pointer" onclick="advanceDialog()">
                <!-- 說話者名字 -->
                <div id="speaker-name" class="absolute -top-5 sm:-top-6 left-4 sm:left-8 bg-blue-600 text-white px-4 py-1 sm:py-2 rounded-lg font-bold text-sm sm:text-lg shadow-md border-2 border-blue-400">
                    Narrator
                </div>
                <!-- 對話內容 -->
                <div id="dialog-text" class="text-base sm:text-xl leading-relaxed min-h-[80px] sm:min-h-[96px] drop-shadow-md">
                    ...
                </div>
            </div>
        </div>

        <!-- 結局畫面 -->
        <div id="end-screen" class="absolute inset-0 flex flex-col justify-center items-center z-50 bg-black hidden p-8 text-center fade-in">
            <h2 id="end-title" class="text-4xl sm:text-5xl font-bold mb-6 text-white">Ending Title</h2>
            <p id="end-desc" class="text-lg sm:text-xl text-gray-300 mb-8 max-w-2xl leading-relaxed">Ending description goes here.</p>
            <div class="bg-gray-800 p-6 rounded-xl border-l-4 border-blue-500 mb-8">
                <p id="end-message" class="text-xl sm:text-2xl font-bold text-blue-300 italic">"Final Message"</p>
            </div>
            
            <div class="flex justify-center gap-6 mb-8 text-sm sm:text-base w-full max-w-md mx-auto">
                <div class="bg-gray-900 p-3 rounded flex-1">Dependence: <span id="final-dep" class="font-bold text-white">0</span></div>
                <div class="bg-gray-900 p-3 rounded flex-1">Thinking: <span id="final-think" class="font-bold text-white">0</span></div>
            </div>

            <button onclick="location.reload()" class="px-8 py-3 bg-white text-black hover:bg-gray-200 rounded-full font-bold text-lg transition-transform hover:scale-105">
                Play Again
            </button>
        </div>

    </div>

    <!-- 遊戲腳本邏輯 -->
    <script>
        // 玩家狀態追蹤
        let stats = {
            dependence: 0,
            thinking: 0
        };

        let currentSceneIndex = 0;
        let currentDialogIndex = 0;
        let isTyping = false;
        let typeTimeout;

        // 劇本結構定義
        const story = [
            // Scene 0: Intro
            {
                bg: "bg-city-day",
                showSpark: false,
                dialogs: [
                    { speaker: "Narrator", text: "The year is 2050. Welcome to 'Smart City'." },
                    { speaker: "Narrator", text: "Here, every student has a powerful AI assistant." },
                    { speaker: "Narrator", text: "Homework, drawings, essays, game guides... the AI gives the answer immediately." },
                    { speaker: "Narrator", text: "Slowly, the citizens are stopping to think for themselves." },
                    { speaker: "Narrator", text: "Today, you received the newest AI model." }
                ],
                choices: [
                    { text: "Turn on the AI.", nextScene: 1 }
                ]
            },
            // Scene 1: Chapter 1
            {
                bg: "bg-classroom",
                showSpark: true,
                dialogs: [
                    { speaker: "Spark", text: "Hello! I am Spark, your new AI assistant. I can solve any problem!" },
                    { speaker: "Teacher", text: "Class, your homework today is: 'Design a plan to save water in our city.'" },
                    { speaker: "Spark", text: "Ding! I have generated a perfect, 10-page water-saving plan for you. It guarantees an A+." }
                ],
                choices: [
                    { 
                        text: "A. Copy Spark's answer directly. It's easy!", 
                        effects: { dependence: 0, thinking: 0 },
                        nextScene: 2
                    },
                    { 
                        text: "B. Read Spark's answer, change it, and add my own ideas.", 
                        effects: { dependence: 1, thinking: 1 },
                        nextScene: 2
                    },
                    { 
                        text: "C. Think of my own ideas first, then ask Spark to organize them.", 
                        effects: { dependence: 2, thinking: 2 },
                        nextScene: 2
                    }
                ]
            },
            // Scene 2: Chapter 2
            {
                bg: "bg-lab",
                showSpark: true,
                dialogs: [
                    { speaker: "Narrator", text: "A few weeks later, you are in the School Science Competition." },
                    { speaker: "Teammate", text: "Wait... the experiment method Spark gave us looks wrong. It might explode!" },
                    { speaker: "Spark", text: "Trust me. My database shows a 99% success rate. Do not worry." }
                ],
                choices: [
                    { 
                        text: "A. Follow Spark. Ignore the teammate.", 
                        effects: { dependence: 0, thinking: 0 },
                        nextScene: 3
                    },
                    { 
                        text: "B. Check the information online and verify it myself.", 
                        effects: { dependence: 1, thinking: 1 },
                        nextScene: 3
                    },
                    { 
                        text: "C. Discuss with my teammates and compare different methods.", 
                        effects: { dependence: 2, thinking: 2 },
                        nextScene: 3
                    }
                ]
            },
            // Scene 3: Chapter 3
            {
                bg: "bg-park",
                showSpark: true,
                dialogs: [
                    { speaker: "Narrator", text: "After school, your best friend Hin looks very angry with you." },
                    { speaker: "Hin", text: "I can't believe you didn't wait for me!" },
                    { speaker: "Spark", text: "Scanning human emotions... Analyzing... Best plan: Ignore him until his anger level decreases." }
                ],
                choices: [
                    { 
                        text: "A. Follow Spark's advice. Ignore Hin.", 
                        effects: { dependence: 0, thinking: 0 },
                        nextScene: 4
                    },
                    { 
                        text: "B. Keep asking Spark for more opinions. Then, talk to Hin the next day.", 
                        effects: { dependence: 1, thinking: 1 },
                        nextScene: 4
                    },
                    { 
                        text: "C. Don't use AI. Go and talk to Hin face-to-face.", 
                        effects: { dependence: 2, thinking: 2 },
                        nextScene: 4
                    }
                ]
            },
            // Scene 4: Chapter 4 (Blackout)
            {
                bg: "bg-blackout",
                showSpark: true,
                dialogs: [
                    { speaker: "Narrator", text: "One night, the lights flicker." },
                    { speaker: "Narrator", text: "Then, the whole city loses power. The internet disappears." },
                    { speaker: "Spark", text: "<span class='glitch-text font-mono'>CONNECTION LOST... CONNECTION LOST...</span>" },
                    { speaker: "Spark", text: "<span class='glitch-text font-mono'>SYSTEM SHUTDOWN.</span>" }
                ],
                choices: [
                    { text: "What will happen to the city?", nextScene: 5 }
                ]
            },
            // Scene 5: Chapter 5
            {
                bg: "bg-ruins",
                showSpark: false,
                dialogs: [
                    { speaker: "Narrator", text: "Three days later. The AI is still broken." },
                    { speaker: "Narrator", text: "Everyone has big problems. They don't know how to do math, plan food, fix machines, or make decisions." },
                    { speaker: "Narrator", text: "It is time to see how you survived..." }
                ],
                choices: [
                    { text: "View my Ending", nextScene: "ENDING" }
                ]
            }
        ];

        // 獲取 DOM 元素
        const elGameContainer = document.getElementById('game-container');
        const elStartScreen = document.getElementById('start-screen');
        const elSceneArea = document.getElementById('scene-area');
        const elUiLayer = document.getElementById('ui-layer');
        const elDialogText = document.getElementById('dialog-text');
        const elSpeakerName = document.getElementById('speaker-name');
        const elChoicesContainer = document.getElementById('choices-container');
        const elCharacterSprite = document.getElementById('character-sprite');
        const elStatsBar = document.getElementById('stats-bar');

        // 更新 UI 上的屬性數值
        function updateStatsUI() {
            document.getElementById('stat-dep').innerText = stats.dependence;
            document.getElementById('stat-think').innerText = stats.thinking;
        }

        // 開始遊戲
        function startGame() {
            elStartScreen.classList.add('hidden');
            elSceneArea.classList.remove('hidden');
            elUiLayer.classList.remove('hidden');
            elUiLayer.classList.add('flex');
            elStatsBar.classList.remove('hidden');
            loadScene(0);
        }

        // 載入指定場景
        function loadScene(index) {
            currentSceneIndex = index;
            currentDialogIndex = 0;
            const scene = story[index];

            // 設置背景圖片
            elGameContainer.className = `relative w-full max-w-4xl h-full max-h-[800px] sm:h-[90vh] sm:rounded-2xl overflow-hidden shadow-2xl transition-all duration-1000 flex flex-col fade-in ${scene.bg}`;

            // 控制 Spark 角色顯示與特效
            if (scene.showSpark) {
                elCharacterSprite.classList.remove('hidden');
            } else {
                elCharacterSprite.classList.add('hidden');
            }
            
            if(scene.bg === 'bg-blackout') {
                document.getElementById('spark-svg').style.filter = "grayscale(100%) brightness(50%) hue-rotate(180deg)";
            } else {
                document.getElementById('spark-svg').style.filter = "none";
            }

            elChoicesContainer.innerHTML = '';
            showDialog();
        }

        // 顯示對話與打字機特效
        function showDialog() {
            const scene = story[currentSceneIndex];
            const dialog = scene.dialogs[currentDialogIndex];
            
            elSpeakerName.innerText = dialog.speaker;
            elSpeakerName.style.display = dialog.speaker ? 'block' : 'none';
            elChoicesContainer.innerHTML = ''; 
            
            isTyping = true;
            elDialogText.innerHTML = '';
            elDialogText.classList.remove('cursor');
            
            let i = 0;
            let currentText = dialog.text;
            
            // 處理帶有 HTML 標籤的特殊文本 (例如 glitch effect)
            if(currentText.includes('<span')) {
                elDialogText.innerHTML = currentText;
                isTyping = false;
                checkShowChoices();
                return;
            }

            function typeChar() {
                if (i < currentText.length) {
                    elDialogText.innerHTML += currentText.charAt(i);
                    i++;
                    typeTimeout = setTimeout(typeChar, 30); // 打字速度控制
                } else {
                    isTyping = false;
                    elDialogText.classList.add('cursor');
                    checkShowChoices();
                }
            }
            clearTimeout(typeTimeout);
            typeChar();
        }

        // 點擊對話框推進劇情
        function advanceDialog() {
            if (isTyping) {
                // 如果正在打字，點擊則直接顯示全句
                clearTimeout(typeTimeout);
                const scene = story[currentSceneIndex];
                const dialog = scene.dialogs[currentDialogIndex];
                elDialogText.innerHTML = dialog.text;
                isTyping = false;
                elDialogText.classList.add('cursor');
                checkShowChoices();
                return;
            }

            const scene = story[currentSceneIndex];
            if (currentDialogIndex < scene.dialogs.length - 1) {
                currentDialogIndex++;
                showDialog();
            }
        }

        // 檢查是否需要顯示選項
        function checkShowChoices() {
            const scene = story[currentSceneIndex];
            if (currentDialogIndex === scene.dialogs.length - 1 && !isTyping) {
                renderChoices(scene.choices);
                elDialogText.classList.remove('cursor');
            }
        }

        // 渲染選項按鈕
        function renderChoices(choices) {
            elChoicesContainer.innerHTML = '';
            choices.forEach(choice => {
                const btn = document.createElement('button');
                btn.className = "choice-btn w-full text-left p-3 sm:p-4 rounded-xl text-sm sm:text-base font-semibold shadow-lg text-white";
                btn.innerText = choice.text;
                btn.onclick = (e) => {
                    e.stopPropagation(); // 防止觸發 advanceDialog
                    makeChoice(choice);
                };
                elChoicesContainer.appendChild(btn);
            });
        }

        // 處理玩家選擇與屬性計算
        function makeChoice(choice) {
            if (choice.effects) {
                if (choice.effects.dependence !== undefined) stats.dependence += choice.effects.dependence;
                if (choice.effects.thinking !== undefined) stats.thinking += choice.effects.thinking;
                updateStatsUI();
            }

            if (choice.nextScene === "ENDING") {
                showEnding();
            } else {
                loadScene(choice.nextScene);
            }
        }

        // 結局判定與顯示
        function showEnding() {
            elSceneArea.classList.add('hidden');
            elUiLayer.classList.add('hidden');
            elStatsBar.classList.add('hidden');
            
            const endScreen = document.getElementById('end-screen');
            endScreen.classList.remove('hidden');
            endScreen.classList.add('flex');

            document.getElementById('final-dep').innerText = stats.dependence;
            document.getElementById('final-think').innerText = stats.thinking;

            const title = document.getElementById('end-title');
            const desc = document.getElementById('end-desc');
            const msg = document.getElementById('end-message');

            // 結局邏輯判斷
            if (stats.thinking === 6) {
                // 真結局: The Creator
                endScreen.className = "absolute inset-0 flex flex-col justify-center items-center z-50 bg-future p-8 text-center fade-in";
                title.innerText = "🌟 True Ending: The Creator";
                title.className = "text-4xl sm:text-5xl font-bold mb-6 text-yellow-300 drop-shadow-[0_0_10px_rgba(253,224,71,0.8)]";
                desc.innerText = "The AI finally comes back. The Mayor invites you to rebuild the city! You tell the Mayor: 'AI should not think FOR people. It should help people think.' A new AI is born. It does not give direct answers anymore. Instead, it asks questions, guides logic, and encourages creativity. Years later, you become the lead designer of the new AI.";
                msg.innerText = "The best user doesn't depend on AI; they think together with AI.";
            } 
            else if (stats.thinking >= 5) {
                // 結局 3: The Wise User
                title.innerText = "✅ Ending 3: The Wise User";
                title.className = "text-4xl sm:text-5xl font-bold mb-6 text-green-400";
                desc.innerText = "Many people are lost without the internet, but you are different. You start to analyze problems, find books for information, organize your classmates, and work together. Because you always questioned the AI and added your own ideas, you kept your ability to think! You lead everyone through the crisis.";
                msg.innerText = "AI is a magnifying glass, not a brain. Your own thinking is what truly matters.";
            }
            else if (stats.thinking >= 3) {
                // 結局 2: The Half-Dependent
                title.innerText = "⚠️ Ending 2: The Half-Dependent";
                title.className = "text-4xl sm:text-5xl font-bold mb-6 text-yellow-500";
                desc.innerText = "The AI is gone, but you still remember some things. You can survive, but it is very hard. When you face complex problems, you still wait for an easy answer and struggle to figure it out yourself.";
                msg.innerText = "AI can help me, but it cannot grow up for me.";
            }
            else {
                // 結局 1: The Unthinking Person
                title.innerText = "❌ Ending 1: The Unthinking Person";
                title.className = "text-4xl sm:text-5xl font-bold mb-6 text-red-500";
                desc.innerText = "You find it very hard to make decisions. You wait for the AI to come back. You can't even answer simple questions like 'How do we share the food?' or 'Where is the clean water?' You just sit and wait. Many people in the city do the same.";
                msg.innerText = "When we give our thinking to tools, we might lose our ability to think.";
            }
        }
    </script>
</body>
</html>
```