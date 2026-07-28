# English-word<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SmartVocab - 英文單字記憶助手</title>
  <style>
    :root {
      --primary-color: #4a6fa5;
      --primary-hover: #3b5984;
      --bg-color: #f4f7f6;
      --card-bg: #ffffff;
      --danger-color: #e63946;
      --warning-color: #ffb703;
      --success-color: #2a9d8f;
      --text-color: #2b2d42;
      --border-radius: 8px;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg-color);
      color: var(--text-color);
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background-color: var(--primary-color);
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 0 1rem;
      width: 100%;
      box-sizing: border-box;
    }

    .nav-btn {
      background-color: transparent;
      border: 1px solid white;
      color: white;
      padding: 0.5rem 1rem;
      border-radius: var(--border-radius);
      cursor: pointer;
      margin-left: 0.5rem;
      transition: all 0.2s;
    }

    .nav-btn:hover, .nav-btn.active {
      background-color: white;
      color: var(--primary-color);
    }

    .card {
      background: var(--card-bg);
      border-radius: var(--border-radius);
      padding: 1.5rem;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
      margin-bottom: 1.5rem;
    }

    .form-group {
      margin-bottom: 1rem;
    }

    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: bold;
    }

    input, select, textarea {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid #ccc;
      border-radius: var(--border-radius);
      box-sizing: border-box;
      font-size: 1rem;
    }

    .btn {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 0.75rem 1.5rem;
      border-radius: var(--border-radius);
      cursor: pointer;
      font-size: 1rem;
      transition: background 0.2s;
    }

    .btn:hover { background-color: var(--primary-hover); }
    .btn-danger { background-color: var(--danger-color); }
    .btn-danger:hover { background-color: #c1121f; }
    .btn-warning { background-color: var(--warning-color); color: #000; }

    /* 單字列表 */
    .word-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 1rem;
    }

    .word-card {
      border: 1px solid #e0e0e0;
      border-radius: var(--border-radius);
      padding: 1rem;
      background: white;
      position: relative;
    }

    .word-card.error-marked {
      border-left: 5px solid var(--danger-color);
    }

    .badge {
      display: inline-block;
      padding: 0.25rem 0.5rem;
      border-radius: 4px;
      font-size: 0.8rem;
      background: #e9ecef;
      margin-right: 0.5rem;
    }

    .badge-pos { background: #d8f3dc; color: #1b4332; }
    .badge-error { background: #ffccd5; color: #a71e34; }

    .word-actions {
      margin-top: 1rem;
      display: flex;
      justify-content: space-between;
    }

    /* 測驗區塊 */
    .quiz-box {
      text-align: center;
      padding: 2rem;
    }

    .quiz-word {
      font-size: 2.5rem;
      font-weight: bold;
      margin-bottom: 1rem;
    }

    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .option-btn {
      padding: 1rem;
      font-size: 1.1rem;
      background-color: #f8f9fa;
      border: 2px solid #dee2e6;
      border-radius: var(--border-radius);
      cursor: pointer;
      text-align: left;
    }

    .option-btn:hover { background-color: #e9ecef; }

    .hidden { display: none !important; }
  </style>
</head>
<body>

  <header>
    <h2>📚 SmartVocab</h2>
    <div id="user-info">
      <span id="current-user-display">未登入</span>
      <button class="nav-btn" onclick="logout()">切換使用者</button>
    </div>
  </header>

  <div class="container">
    <!-- 登入區塊 -->
    <div id="auth-section" class="card">
      <h3>👤 使用者登入 / 載入記憶檔</h3>
      <p>輸入你的名字以載入專屬單字庫與學習紀錄：</p>
      <div class="form-group">
        <input type="text" id="username-input" placeholder="請輸入使用者名稱 (例如: Alex)" />
      </div>
      <button class="btn" onclick="login()">進入系統</button>
    </div>

    <!-- 主要功能分頁按鈕 -->
    <div id="app-nav" class="hidden" style="margin-bottom: 1.5rem;">
      <button class="nav-btn active" onclick="switchTab('list')">📖 單字庫管理</button>
      <button class="nav-btn" onclick="switchTab('add')">➕ 新增單字</button>
      <button class="nav-btn" onclick="switchTab('quiz')">✍️ 隨堂測驗</button>
    </div>

    <!-- 1. 單字列表頁面 -->
    <div id="list-tab" class="tab-content hidden">
      <div class="card">
        <h3>📖 單字庫列表</h3>
        <div style="display: flex; gap: 1rem; margin-bottom: 1rem;">
          <input type="text" id="search-input" placeholder="搜尋單字或中文解釋..." oninput="renderWordList()">
          <select id="filter-select" onchange="renderWordList()" style="width: 200px;">
            <option value="all">顯示全部</option>
            <option value="error">僅顯示易錯單字</option>
          </select>
        </div>
        <div id="word-list" class="word-grid"></div>
      </div>
    </div>

    <!-- 2. 新增單字頁面 -->
    <div id="add-tab" class="tab-content hidden">
      <div class="card">
        <h3>➕ 新增英文單字</h3>
        <form id="add-word-form" onsubmit="addWord(event)">
          <div class="form-group">
            <label>英文單字 (Word)</label>
            <input type="text" id="word-spelling" required placeholder="例如: persistent">
          </div>
          <div class="form-group">
            <label>詞性 (Part of Speech)</label>
            <select id="word-pos">
              <option value="n.">n. 名詞</option>
              <option value="v.">v. 動詞</option>
              <option value="adj.">adj. 形容詞</option>
              <option value="adv.">adv. 副詞</option>
              <option value="prep.">prep. 介系詞</option>
              <option value="conj.">conj. 連接詞</option>
              <option value="other">other 其他</option>
            </select>
          </div>
          <div class="form-group">
            <label>中文解釋 (Meaning)</label>
            <input type="text" id="word-meaning" required placeholder="例如: 堅持不懈的，持續的">
          </div>
          <button type="submit" class="btn">新增至單字庫</button>
        </form>
      </div>
    </div>

    <!-- 3. 測驗頁面 -->
    <div id="quiz-tab" class="tab-content hidden">
      <div class="card quiz-box" id="quiz-start-box">
        <h3>✍️ 單字自我測驗</h3>
        <p>測驗將隨機出題，答錯的單字將自動被標註為「易錯單字」。</p>
        <button class="btn" onclick="startQuiz()">開始測驗</button>
      </div>

      <div class="card quiz-box hidden" id="quiz-running-box">
        <div style="text-align: right; color: #666;" id="quiz-progress">題號 1 / 5</div>
        <div class="quiz-word" id="quiz-question-word">Word</div>
        <div class="options-grid" id="quiz-options"></div>
      </div>

      <!-- 4. 考後反省頁面 -->
      <div class="card hidden" id="quiz-result-box">
        <h3>📊 測驗結算與考後反省</h3>
        <p id="quiz-score-summary"></p>
        <hr>
        <h4>❌ 錯題列表（已自動歸類為易錯單字）：</h4>
        <div id="wrong-words-container"></div>
        <br>
        <button class="btn" onclick="startQuiz()">再測一次</button>
      </div>
    </div>
  </div>

  <script>
    let currentUser = "";
    let vocabData = [];
    let currentQuizIndex = 0;
    let currentQuizQuestions = [];
    let wrongAnswers = [];

    // 初始化與預設資料
    const defaultVocab = [
      { id: 1, word: "apple", pos: "n.", meaning: "蘋果", isError: false, errorCount: 0 },
      { id: 2, word: "resilient", pos: "adj.", meaning: "有彈性的；能迅速恢復的", isError: true, errorCount: 2 },
      { id: 3, word: "calculate", pos: "v.", meaning: "計算", isError: false, errorCount: 0 }
    ];

    // 登入
    function login() {
      const username = document.getElementById("username-input").value.trim();
      if (!username) return alert("請輸入使用者名稱！");
      
      currentUser = username;
      document.getElementById("current-user-display").innerText = `👤 使用者: ${currentUser}`;
      document.getElementById("auth-section").classList.add("hidden");
      document.getElementById("app-nav").classList.remove("hidden");
      
      loadUserData();
      switchTab('list');
    }

    function logout() {
      currentUser = "";
      document.getElementById("auth-section").classList.remove("hidden");
      document.getElementById("app-nav").classList.add("hidden");
      document.querySelectorAll(".tab-content").forEach(el => el.classList.add("hidden"));
      document.getElementById("current-user-display").innerText = "未登入";
    }

    // 資料持久化 (localStorage)
    function loadUserData() {
      const savedData = localStorage.getItem(`vocab_data_${currentUser}`);
      if (savedData) {
        vocabData = JSON.parse(savedData);
      } else {
        vocabData = [...defaultVocab];
        saveUserData();
      }
    }

    function saveUserData() {
      if (currentUser) {
        localStorage.setItem(`vocab_data_${currentUser}`, JSON.stringify(vocabData));
      }
    }

    // 切換分頁
    function switchTab(tabName) {
      document.querySelectorAll(".tab-content").forEach(el => el.classList.add("hidden"));
      document.querySelectorAll("#app-nav .nav-btn").forEach(el => el.classList.remove("active"));

      if (tabName === 'list') {
        document.getElementById("list-tab").classList.remove("hidden");
        renderWordList();
      } else if (tabName === 'add') {
        document.getElementById("add-tab").classList.remove("hidden");
      } else if (tabName === 'quiz') {
        document.getElementById("quiz-tab").classList.remove("hidden");
        resetQuizUI();
      }
    }

    // 渲染單字列表 (功能二 & 三)
    function renderWordList(highlightWordId = null) {
      const listContainer = document.getElementById("word-list");
      const searchKeyword = document.getElementById("search-input").value.toLowerCase();
      const filter = document.getElementById("filter-select").value;

      listContainer.innerHTML = "";

      let filtered = vocabData.filter(item => {
        const matchesSearch = item.word.toLowerCase().includes(searchKeyword) || item.meaning.includes(searchKeyword);
        const matchesFilter = filter === 'all' || (filter === 'error' && item.isError);
        return matchesSearch && matchesFilter;
      });

      if (filtered.length === 0) {
        listContainer.innerHTML = `<p style="grid-column: 1/-1; color: #888;">查無單字資料。</p>`;
        return;
      }

      filtered.forEach(item => {
        const card = document.createElement("div");
        card.className = `word-card ${item.isError ? 'error-marked' : ''}`;
        card.id = `word-card-${item.id}`;

        card.innerHTML = `
          <div style="font-size: 1.3rem; font-weight: bold;">
            ${item.word} 
            ${item.isError ? '<span class="badge badge-error">易錯</span>' : ''}
          </div>
          <div style="margin: 0.5rem 0;">
            <span class="badge badge-pos">${item.pos}</span>
            <span>${item.meaning}</span>
          </div>
          ${item.errorCount > 0 ? `<small style="color: var(--danger-color);">錯誤累積: ${item.errorCount} 次</small>` : ''}
          <div class="word-actions">
            <button class="btn btn-warning" style="padding: 0.3rem 0.6rem; font-size: 0.8rem;" onclick="toggleError(${item.id})">
              ${item.isError ? '取消易錯標註' : '標註為易錯'}
            </button>
            <button class="btn btn-danger" style="padding: 0.3rem 0.6rem; font-size: 0.8rem;" onclick="deleteWord(${item.id})">刪除</button>
          </div>
        `;

        listContainer.appendChild(card);
      });

      // 如果有指定反省跳轉的單字，進行高亮標示並捲動
      if (highlightWordId) {
        setTimeout(() => {
          const targetCard = document.getElementById(`word-card-${highlightWordId}`);
          if (targetCard) {
            targetCard.scrollIntoView({ behavior: 'smooth', block: 'center' });
            targetCard.style.outline = "3px solid var(--primary-color)";
            setTimeout(() => targetCard.style.outline = "none", 2500);
          }
        }, 100);
      }
    }

    // 新增單字
    function addWord(e) {
      e.preventDefault();
      const spelling = document.getElementById("word-spelling").value.trim();
      const pos = document.getElementById("word-pos").value;
      const meaning = document.getElementById("word-meaning").value.trim();

      const newWord = {
        id: Date.now(),
        word: spelling,
        pos: pos,
        meaning: meaning,
        isError: false,
        errorCount: 0
      };

      vocabData.push(newWord);
      saveUserData();
      alert("單字新增成功！");
      document.getElementById("add-word-form").reset();
      switchTab('list');
    }

    // 刪除單字
    function deleteWord(id) {
      if (confirm("確定要刪除這個單字嗎？")) {
        vocabData = vocabData.filter(item => item.id !== id);
        saveUserData();
        renderWordList();
      }
    }

    // 切換易錯標註
    function toggleError(id) {
      const item = vocabData.find(w => w.id === id);
      if (item) {
        item.isError = !item.isError;
        saveUserData();
        renderWordList();
      }
    }

    // --- 測驗功能 ---
    function resetQuizUI() {
      document.getElementById("quiz-start-box").classList.remove("hidden");
      document.getElementById("quiz-running-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.add("hidden");
    }

    function startQuiz() {
      if (vocabData.length < 2) {
        return alert("單字庫數量太少（至少需要2個單字）才能開始測驗！");
      }

      // 洗牌並取出最多 5 題
      currentQuizQuestions = [...vocabData].sort(() => 0.5 - Math.random()).slice(0, 5);
      currentQuizIndex = 0;
      wrongAnswers = [];

      document.getElementById("quiz-start-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.add("hidden");
      document.getElementById("quiz-running-box").classList.remove("hidden");

      showNextQuestion();
    }

    function showNextQuestion() {
      if (currentQuizIndex >= currentQuizQuestions.length) {
        return finishQuiz();
      }

      const q = currentQuizQuestions[currentQuizIndex];
      document.getElementById("quiz-progress").innerText = `題號 ${currentQuizIndex + 1} / ${currentQuizQuestions.length}`;
      document.getElementById("quiz-question-word").innerText = q.word;

      // 產生選項（包含正確答案與干擾項）
      let options = [q];
      let otherOptions = vocabData.filter(item => item.id !== q.id).sort(() => 0.5 - Math.random());
      
      while (options.length < Math.min(4, vocabData.length)) {
        options.push(otherOptions.pop());
      }
      options.sort(() => 0.5 - Math.random()); // 洗牌選項

      const optionsGrid = document.getElementById("quiz-options");
      optionsGrid.innerHTML = "";
      options.forEach(opt => {
        const btn = document.createElement("button");
        btn.className = "option-btn";
        btn.innerText = `${opt.pos} ${opt.meaning}`;
        btn.onclick = () => handleAnswer(opt.id === q.id, q);
        optionsGrid.appendChild(btn);
      });
    }

    function handleAnswer(isCorrect, questionWord) {
      if (!isCorrect) {
        // 答錯：自動標註為易錯單字，並增加計數
        const target = vocabData.find(w => w.id === questionWord.id);
        if (target) {
          target.isError = true;
          target.errorCount = (target.errorCount || 0) + 1;
          saveUserData();
        }
        wrongAnswers.push(questionWord);
      }

      currentQuizIndex++;
      showNextQuestion();
    }

    // 考後反省 (功能二需求)
    function finishQuiz() {
      document.getElementById("quiz-running-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.remove("hidden");

      const total = currentQuizQuestions.length;
      const correctCount = total - wrongAnswers.length;
      document.getElementById("quiz-score-summary").innerText = `本次測驗得分：${correctCount} / ${total} 題 (正確率: ${Math.round(correctCount/total * 100)}%)`;

      const wrongContainer = document.getElementById("wrong-words-container");
      wrongContainer.innerHTML = "";

      if (wrongAnswers.length === 0) {
        wrongContainer.innerHTML = "<p style='color: var(--success-color); font-weight: bold;'>🎉 太厲害了！本次測驗完全沒有錯題！</p>";
      } else {
        wrongAnswers.forEach(item => {
          const div = document.createElement("div");
          div.style.cssText = "display: flex; justify-content: space-between; align-items: center; padding: 0.8rem; border-bottom: 1px solid #eee;";
          div.innerHTML = `
            <div>
              <strong style="font-size: 1.1rem; color: var(--danger-color);">${item.word}</strong> 
              <span class="badge badge-pos">${item.pos}</span> ${item.meaning}
            </div>
            <button class="btn" style="padding: 0.3rem 0.8rem; font-size: 0.85rem;" onclick="jumpToWordDetail(${item.id})">
              一鍵直達單字頁 ➔
            </button>
          `;
          wrongContainer.appendChild(div);
        });
      }
    }

    // 一鍵直達反省頁面
    function jumpToWordDetail(wordId) {
      switchTab('list');
      renderWordList(wordId);
    }
  </script>
</body>
</html>

no
