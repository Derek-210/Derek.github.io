<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>四級詞彙大闖關 - CET-4 Master</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&family=Noto+Sans+SC:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #6366f1;
            --primary-light: #e0e7ff;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #1e293b;
            --text-light: #64748b;
            --radius: 20px;
            --shadow: 0 10px 25px -5px rgba(99, 102, 241, 0.1), 0 8px 10px -6px rgba(99, 102, 241, 0.1);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', 'Noto Sans SC', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 12px;
        }

        .container {
            width: 100%;
            max-width: 480px;
            background: var(--card-bg);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 680px;
            position: relative;
        }

        /* Screens */
        .screen {
            display: none;
            flex-direction: column;
            flex: 1;
            padding: 24px;
            animation: fadeIn 0.3s ease-in-out;
        }

        .screen.active {
            display: flex;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Header & Common */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 14px 24px;
            border-radius: 14px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
            width: 100%;
            text-align: center;
        }

        .btn:active {
            transform: scale(0.97);
        }

        .btn-secondary {
            background: #f1f5f9;
            color: var(--text);
            box-shadow: none;
        }

        .btn-danger {
            background: var(--danger);
            box-shadow: 0 4px 12px rgba(239, 68, 68, 0.3);
        }

        /* Home Screen */
        .home-hero {
            text-align: center;
            margin: auto 0;
        }

        .home-hero h1 {
            font-size: 32px;
            font-weight: 800;
            color: var(--primary);
            margin-bottom: 12px;
        }

        .home-hero p {
            color: var(--text-light);
            font-size: 15px;
            margin-bottom: 32px;
            line-height: 1.6;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: var(--bg);
            padding: 16px;
            border-radius: 14px;
            text-align: center;
        }

        .stat-card .num {
            font-size: 24px;
            font-weight: 800;
            color: var(--primary);
        }

        .stat-card .label {
            font-size: 13px;
            color: var(--text-light);
            margin-top: 4px;
        }

        /* Game Screen */
        .game-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
        }

        .progress-bar-container {
            flex: 1;
            height: 8px;
            background: #f1f5f9;
            border-radius: 4px;
            margin: 0 16px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            background: var(--primary);
            width: 0%;
            transition: width 0.3s ease;
        }

        .game-info {
            display: flex;
            justify-content: space-between;
            font-size: 14px;
            font-weight: 600;
            color: var(--text-light);
            margin-bottom: 16px;
        }

        .combo-badge {
            background: var(--primary-light);
            color: var(--primary);
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 700;
        }

        .shield-badge {
            background: #d1fae5;
            color: var(--success);
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 700;
        }

        .question-card {
            background: #f8fafc;
            border: 2px solid #e2e8f0;
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 20px;
            text-align: center;
        }

        .question-type {
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: var(--primary);
            font-weight: 700;
            margin-bottom: 8px;
        }

        .question-title {
            font-size: 22px;
            font-weight: 700;
            margin-bottom: 12px;
            color: var(--text);
        }

        .audio-btn {
            background: var(--primary-light);
            color: var(--primary);
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            margin: 0 auto 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(99, 102, 241, 0.2);
        }

        .question-sub {
            font-size: 14px;
            color: var(--text-light);
            line-height: 1.5;
        }

        .options-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 20px;
        }

        .option-btn {
            background: white;
            border: 2px solid #e2e8f0;
            padding: 16px;
            border-radius: 14px;
            font-size: 15px;
            font-weight: 600;
            color: var(--text);
            cursor: pointer;
            text-align: left;
            transition: all 0.2s;
        }

        .option-btn:hover {
            border-color: var(--primary);
            background: var(--primary-light);
        }

        .option-btn.correct {
            background: #d1fae5 !important;
            border-color: var(--success) !important;
            color: #065f46 !important;
        }

        .option-btn.wrong {
            background: #fee2e2 !important;
            border-color: var(--danger) !important;
            color: #991b1b !important;
        }

        /* Result Screen */
        .result-hero {
            text-align: center;
            margin: auto 0;
        }

        .stars {
            font-size: 40px;
            margin-bottom: 16px;
        }

        .result-hero h2 {
            font-size: 28px;
            font-weight: 800;
            margin-bottom: 8px;
        }

        .result-score {
            font-size: 48px;
            font-weight: 800;
            color: var(--primary);
            margin-bottom: 24px;
        }
    </style>
</head>
<body>

<div class="container">
    <!-- 首頁畫面 -->
    <div id="home-screen" class="screen active">
        <div class="home-hero">
            <h1>CET-4 Master</h1>
            <p>沉浸式四級闖關，結合限時挑戰、連擊護盾與錯題訂正，輕鬆攻克核心詞彙！</p>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="num" id="stat-total">60</div>
                    <div class="label">核心詞庫</div>
                </div>
                <div class="stat-card">
                    <div class="num" id="stat-wrong">0</div>
                    <div class="label">錯題本</div>
                </div>
            </div>

            <button class="btn" onclick="startGame('normal')">開始闖關挑戰</button>
            <button class="btn btn-secondary" style="margin-top: 10px;" onclick="startGame('wrong')" id="review-btn" disabled>錯題複習 (0)</button>
        </div>
    </div>

    <!-- 遊戲畫面 -->
    <div id="game-screen" class="screen">
        <div class="game-top">
            <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 13px;" onclick="quitGame()">退出</button>
            <div class="progress-bar-container">
                <div class="progress-bar" id="progress-bar"></div>
            </div>
            <span id="timer" style="font-weight: 700; color: var(--danger);">15s</span>
        </div>

        <div class="game-info">
            <span class="combo-badge" id="combo-display">連擊 x0</span>
            <span class="shield-badge" id="shield-display">🛡️ 護盾 x1</span>
        </div>

        <div class="question-card">
            <div class="question-type" id="q-type">單字辨義</div>
            <div class="question-title" id="q-title">Loading...</div>
            <button class="audio-btn" id="audio-btn" onclick="playAudio()" style="display: none;">🔊</button>
            <div class="question-sub" id="q-sub"></div>
        </div>

        <div class="options-list" id="options-list">
            <!-- 動態選項 -->
        </div>
    </div>

    <!-- 結算畫面 -->
    <div id="result-screen" class="screen">
        <div class="result-hero">
            <div class="stars" id="result-stars">⭐⭐⭐</div>
            <h2>闖關完成！</h2>
            <div class="result-score" id="result-score">100 分</div>
            <p id="result-desc" style="color: var(--text-light); margin-bottom: 32px;">太棒了！你的詞彙掌握度非常高。</p>
            <button class="btn" onclick="showScreen('home-screen')">返回首頁</button>
        </div>
    </div>
</div>

<script>
    // 60個核心CET-4詞庫（內置短例句與多種題型支援）
    const vocabData = [
        { word: "abandon", meaning: "放棄、拋棄", sentence: "He had to abandon his car in the snow.", type: "meaning" },
        { word: "ability", meaning: "能力、才能", sentence: "She has the ability to learn languages quickly.", type: "meaning" },
        { word: "absence", meaning: "缺席、不在", sentence: "His absence was noticed by the teacher.", type: "meaning" },
        { word: "absolute", meaning: "絕對的、完全的", sentence: "I have absolute confidence in you.", type: "meaning" },
        { word: "absorb", meaning: "吸收、吸引", sentence: "Plants absorb water from the soil.", type: "meaning" },
        { word: "abstract", meaning: "抽象的", sentence: "Art can be very abstract sometimes.", type: "meaning" },
        { word: "academic", meaning: "學術的、學院的", sentence: "He has a strong academic background.", type: "meaning" },
        { word: "access", meaning: "接近、通道、入口", sentence: "Students have free access to the library.", type: "meaning" },
        { word: "accompany", meaning: "陪伴、伴隨", sentence: "Thunder usually accompanies lightning.", type: "meaning" },
        { word: "accomplish", meaning: "完成、實現", sentence: "We can accomplish this task together.", type: "meaning" },
        { word: "accurate", meaning: "準確的、精確的", sentence: "Make sure your information is accurate.", type: "meaning" },
        { word: "accuse", meaning: "指責、控告", sentence: "They accused him of stealing money.", type: "meaning" },
        { word: "achieve", meaning: "實現、取得", sentence: "Hard work helps you achieve your goals.", type: "meaning" },
        { word: "acknowledge", meaning: "承認、致謝", sentence: "She acknowledged her mistake openly.", type: "meaning" },
        { word: "acquire", meaning: "取得、獲得", sentence: "He managed to acquire a new skill.", type: "meaning" },
        { word: "adapt", meaning: "適應、改編", sentence: "You must adapt to the new environment.", type: "meaning" },
        { word: "adequate", meaning: "足夠的、適當的", sentence: "The room is adequate for one person.", type: "meaning" },
        { word: "adjust", meaning: "調整、調節", sentence: "Adjust your seat before driving.", type: "meaning" },
        { word: "administration", meaning: "管理、行政", sentence: "She works in business administration.", type: "meaning" },
        { word: "admit", meaning: "承認、准許進入", sentence: "He admitted that he was wrong.", type: "meaning" },
        { word: "adopt", meaning: "採用、收養", sentence: "They decided to adopt a rescue dog.", type: "meaning" },
        { word: "advanced", meaning: "先進的、高級的", sentence: "This is an advanced English course.", type: "meaning" },
        { word: "afford", meaning: "負擔得起", sentence: "I can't afford a brand new laptop.", type: "meaning" },
        { word: "aggressive", meaning: "侵略的、積極進取的", sentence: "He has an aggressive sales strategy.", type: "meaning" },
        { word: "allocate", meaning: "分配、分派", sentence: "The manager allocated tasks to everyone.", type: "meaning" },
        { word: "alter", meaning: "改變、修改", sentence: "The weather began to alter rapidly.", type: "meaning" },
        { word: "ambitious", meaning: "有雄心的、野心勃勃的", sentence: "She is an ambitious young architect.", type: "meaning" },
        { word: "analyze", meaning: "分析", sentence: "Scientists analyze data to find results.", type: "meaning" },
        { word: "annual", meaning: "每年的、年度的", sentence: "The company holds an annual meeting.", type: "meaning" },
        { word: "anticipate", meaning: "預料、期望", sentence: "We anticipate a great turnout tonight.", type: "meaning" },
        { word: "anxious", meaning: "焦慮的、渴望的", sentence: "She felt anxious about the exam results.", type: "meaning" },
        { word: "apparent", meaning: "顯而易見的", sentence: "It became apparent that we were lost.", type: "meaning" },
        { word: "approach", meaning: "接近、方法", sentence: "Winter is approaching fast.", type: "meaning" },
        { word: "appropriate", meaning: "合適的、恰當的", sentence: "Wear appropriate clothes for the party.", type: "meaning" },
        { word: "approve", meaning: "批准、贊成", sentence: "My parents approved my study plan.", type: "meaning" },
        { word: "aspect", meaning: "方面、觀點", sentence: "We must consider every aspect of the plan.", type: "meaning" },
        { word: "assess", meaning: "評估、評判", sentence: "Teachers assess student performance termly.", type: "meaning" },
        { word: "assign", meaning: "分配、指派", sentence: "The boss assigned new duties to him.", type: "meaning" },
        { word: "assist", meaning: "協助、幫助", sentence: "Can you assist me with this luggage?", type: "meaning" },
        { word: "assume", meaning: "假定、假設", sentence: "I assume you are ready for the test.", type: "meaning" },
        { word: "attach", meaning: "貼上、附加", sentence: "Please attach your resume to the email.", type: "meaning" },
        { word: "attempt", meaning: "嘗試、企图", sentence: "He made an attempt to break the record.", type: "meaning" },
        { word: "attitude", meaning: "態度、看法", sentence: "A positive attitude is crucial.", type: "meaning" },
        { word: "attribute", meaning: "歸因於、屬性", sentence: "She attributed her success to hard work.", type: "meaning" },
        { word: "audience", meaning: "觀眾、聽眾", sentence: cheered as the band entered.", type: "meaning" },
        { word: "authority", meaning: "權威、官方", sentence: "She is an authority on ancient history.", type: "meaning" },
        { word: "available", meaning: "可獲得的、有空的", sentence: "Is this seat available?", type: "meaning" },
        { word: "average", meaning: "平均的、平常的", sentence: "The average temperature is 20 degrees.", type: "meaning" },
        { word: "award", meaning: "獎品、授予", sentence: "He won an award for best design.", type: "meaning" },
        { word: "aware", meaning: "意識到的、知道的", sentence: "Are you aware of the danger?", type: "meaning" },
        { word: "balance", meaning: "平衡、結餘", sentence: "Keep your balance on the bicycle.", type: "meaning" },
        { word: "barrier", meaning: "障礙、屏障", sentence: "Language is a barrier to communication.", type: "meaning" },
        { word: "benefit", meaning: "利益、好處", sentence: "Fresh air brings benefit to health.", type: "meaning" },
        { word: "budget", meaning: "預算", sentence: "We need to plan our monthly budget.", type: "meaning" },
        { word: "capable", meaning: "有能力的", sentence: "She is capable of doing a great job.", type: "meaning" },
        { word: "category", meaning: "種類、類別", sentence: "Books are sorted by category.", type: "meaning" },
        { word: "cease", meaning: "停止、終止", sentence: "Rain will cease by tomorrow morning.", type: "meaning" },
        { word: "challenge", meaning: "挑戰", sentence: "Learning a new skill is a challenge.", type: "meaning" },
        { word: "circumstance", meaning: "環境、情況", sentence: "We must adapt to the circumstance.", type: "meaning" },
        { word: "collapse", meaning: "倒塌、崩潰", sentence: "The old bridge might collapse soon.", type: "meaning" }
    ];

    // 遊戲狀態
    let gameState = {
        score: 0,
        combo: 0,
        shield: 1,
        currentIndex: 0,
        questions: [],
        wrongList: JSON.parse(localStorage.getItem('cet4_wrong') || '[]'),
        timer: null,
        timeLeft: 15,
        mode: 'normal'
    };

    function showScreen(screenId) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
        document.getElementById(screenId).classList.add('active');
        if(screenId === 'home-screen') {
            updateHomeStats();
        }
    }

    function updateHomeStats() {
        document.getElementById('stat-total').innerText = vocabData.length;
        document.getElementById('stat-wrong').innerText = gameState.wrongList.length;
        const reviewBtn = document.getElementById('review-btn');
        if(gameState.wrongList.length > 0) {
            reviewBtn.disabled = false;
            reviewBtn.innerText = `錯題複習 (${gameState.wrongList.length})`;
        } else {
            reviewBtn.disabled = true;
            reviewBtn.innerText = `錯題複習 (0)`;
        }
    }

    function startGame(mode) {
        gameState.mode = mode;
        gameState.score = 0;
        gameState.combo = 0;
        gameState.shield = 1;
        gameState.currentIndex = 0;

        let pool = mode === 'wrong' ? vocabData.filter(v => gameState.wrongList.includes(v.word)) : [...vocabData];
        // 隨機抽10題進行闖關
        gameState.questions = pool.sort(() => 0.5 - Math.random()).slice(0, 10);

        showScreen('game-screen');
        loadQuestion();
    }

    function loadQuestion() {
        clearInterval(gameState.timer);
        if(gameState.currentIndex >= gameState.questions.length) {
            endGame();
            return;
        }

        const q = gameState.questions[gameState.currentIndex];
        const progress = (gameState.currentIndex / gameState.questions.length) * 100;
        document.getElementById('progress-bar').style.width = progress + '%';
        document.getElementById('combo-display').innerText = `連擊 x${gameState.combo}`;
        document.getElementById('shield-display').innerText = `🛡️ 護盾 x${gameState.shield}`;

        // 隨機題型：0:單字辨義, 1:情境填空, 2:聽音辨字, 3:中譯英
        const typePool = ['meaning', 'context', 'audio', 'translation'];
        const qType = typePool[Math.floor(Math.random() * typePool.length)];
        q.currentType = qType;

        const titleEl = document.getElementById('q-title');
        const subEl = document.getElementById('q-sub');
        const typeEl = document.getElementById('q-type');
        const audioBtn = document.getElementById('audio-btn');
        audioBtn.style.display = 'none';

        let correctAns = q.meaning;
        let options = [correctAns];

        // 產生干擾選項
        while(options.length < 4) {
            let randomVocab = vocabData[Math.floor(Math.random() * vocabData.length)];
            if(!options.includes(randomVocab.meaning)) {
                options.push(randomVocab.meaning);
            }
        }
        options.sort(() => 0.5 - Math.random());

        if(qType === 'meaning') {
            typeEl.innerText = '單字辨義';
            titleEl.innerText = q.word;
            subEl.innerText = '請選擇正確的中 義：';
        } else if(qType === 'context') {
            typeEl.innerText = '情境填空';
            titleEl.innerText = q.sentence.replace(new RegExp(q.word, 'gi'), '______');
            subEl.innerText = `提示：句中空格對應的單字意思是什麼？`;
        } else if(qType === 'audio') {
            typeEl.innerText = '聽音辨字';
            titleEl.innerText = '🎵 點擊發音按鈕聆聽';
            audioBtn.style.display = 'flex';
            subEl.innerText = `辨識發音並選出對應的中文意思`;
            playAudio(q.word);
        } else if(qType === 'translation') {
            typeEl.innerText = '中譯英';
            titleEl.innerText = q.meaning;
            subEl.innerText = '請選出對應的英文單字：';
            options = [q.word];
            while(options.length < 4) {
                let randomVocab = vocabData[Math.floor(Math.random() * vocabData.length)];
                if(!options.includes(randomVocab.word)) {
                    options.push(randomVocab.word);
                }
            }
            options.sort(() => 0.5 - Math.random());
            correctAns = q.word;
        }

        const listEl = document.getElementById('options-list');
        listEl.innerHTML = '';
        options.forEach(opt => {
            const btn = document.createElement('button');
            btn.className = 'option-btn';
            btn.innerText = opt;
            btn.onclick = () => checkAnswer(opt, correctAns, q.word);
            listEl.appendChild(btn);
        });

        // 計時器 15 秒
        gameState.timeLeft = 15;
        document.getElementById('timer').innerText = gameState.timeLeft + 's';
        gameState.timer = setInterval(() => {
            gameState.timeLeft--;
            document.getElementById('timer').innerText = gameState.timeLeft + 's';
            if(gameState.timeLeft <= 0) {
                clearInterval(gameState.timer);
                handleWrongAnswer(q.word);
            }
        }, 1000);
    }

    function playAudio(word) {
        const q = gameState.questions[gameState.currentIndex];
        const textToSpeak = word || q.word;
        if('speechSynthesis' in window) {
            const utterance = new SpeechSynthesisUtterance(textToSpeak);
            utterance.lang = 'en-US';
            window.speechSynthesis.speak(utterance);
        }
    }

    function checkAnswer(selected, correct, word) {
        clearInterval(gameState.timer);
        const buttons = document.querySelectorAll('.option-btn');
        buttons.forEach(btn => {
            btn.disabled = true;
            if(btn.innerText === correct) btn.classList.add('correct');
            if(btn.innerText === selected && selected !== correct) btn.classList.add('wrong');
        });

        if(selected === correct) {
            gameState.combo++;
            gameState.score += 10 + gameState.combo * 2;
            // 答對若在錯題本中則移除
            gameState.wrongList = gameState.wrongList.filter(w => w !== word);
        } else {
            handleWrongAnswer(word);
        }

        setTimeout(() => {
            gameState.currentIndex++;
            loadQuestion();
        }, 900);
    }

    function handleWrongAnswer(word) {
        if(gameState.shield > 0) {
            gameState.shield--;
            // 護盾抵擋失敗懲罰
        } else {
            gameState.combo = 0;
        }
        if(!gameState.wrongList.includes(word)) {
            gameState.wrongList.push(word);
        }
        localStorage.setItem('cet4_wrong', JSON.stringify(gameState.wrongList));
    }

    function endGame() {
        showScreen('result-screen');
        document.getElementById('result-score').innerText = `${gameState.score} 分`;
        let stars = '⭐⭐⭐';
        if(gameState.score < 60) stars = '⭐';
        else if(gameState.score < 100) stars = '⭐⭐';
        document.getElementById('result-stars').innerText = stars;
        updateHomeStats();
    }

    function quitGame() {
        clearInterval(gameState.timer);
        showScreen('home-screen');
    }

    // 初始化首頁統計
    updateHomeStats();
</script>

</body>
</html>
