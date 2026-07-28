<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VocabMaster - 智慧英文單字學習系統</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #4f46e5;
      --primary-hover: #4338ca;
      --primary-light: #e0e7ff;
      --bg: #f8fafc;
      --card-bg: #ffffff;
      --text-main: #0f172a;
      --text-muted: #64748b;
      --danger: #ef4444;
      --danger-light: #fee2e2;
      --warning: #f59e0b;
      --success: #10b981;
      --border: #e2e8f0;
      --radius: 12px;
      --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03);
    }

    * {
      box-sizing: border-box;
      font-family: 'Inter', system-ui, -apple-system, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text-main);
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background: linear-gradient(135deg, #4f46e5, #3b82f6);
      color: white;
      padding: 1.2rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 12px rgba(79, 70, 229, 0.15);
    }

    header h1 {
      margin: 0;
      font-size: 1.5rem;
      font-weight: 700;
      letter-spacing: -0.025em;
    }

    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 0 1.5rem;
      width: 100%;
    }

    .card {
      background: var(--card-bg);
      border-radius: var(--radius);
      padding: 2rem;
      box-shadow: var(--shadow);
      border: 1px solid var(--border);
      margin-bottom: 1.5rem;
    }

    .nav-bar {
      display: flex;
      gap: 0.5rem;
      margin-bottom: 1.5rem;
      background: #e2e8f0;
      padding: 0.3rem;
      border-radius: var(--radius);
    }

    .nav-btn {
      flex: 1;
      border: none;
      background: transparent;
      padding: 0.75rem 1rem;
      border-radius: 8px;
      font-weight: 600;
      color: var(--text-muted);
      cursor: pointer;
      transition: all 0.2s;
    }

    .nav-btn.active {
      background: white;
      color: var(--primary);
      box-shadow: var(--shadow);
    }

    .btn {
      background-color: var(--primary);
      color: white;
      border: none;
      padding: 0.75rem 1.5rem;
      border-radius: var(--radius);
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .btn:hover { background-color: var(--primary-hover); transform: translateY(-1px); }
    .btn-secondary { background-color: #f1f5f9; color: var(--text-main); }
    .btn-secondary:hover { background-color: #e2e8f0; }
    .btn-danger { background-color: var(--danger); }
    .btn-danger:hover { background-color: #dc2626; }
    .btn-warning { background-color: var(--warning); color: white; }

    .form-group {
      margin-bottom: 1.2rem;
    }

    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 600;
      font-size: 0.9rem;
      color: var(--text-muted);
    }

    input, select, textarea {
      width: 100%;
      padding: 0.8rem 1rem;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      font-size: 1rem;
      transition: border-color 0.2s;
    }

    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1);
    }

    /* 單字卡片格線 */
    .word-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 1.2rem;
    }

    .word-card {
      background: white;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.2rem;
      transition: all 0.2s;
      position: relative;
    }

    .word-card:hover {
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05);
      border-color: #cbd5e1;
    }

    .word-card.error-marked {
      border-left: 4px solid var(--danger);
    }

    .badge {
      display: inline-block;
      padding: 0.2rem 0.6rem;
      border-radius: 20px;
      font-size: 0.75rem;
      font-weight: 600;
    }

    .badge-pos { background: var(--primary-light); color: var(--primary); }
    .badge-error { background: var(--danger-light); color: var(--danger); }

    /* 測驗區塊 */
    .quiz-container {
      text-align: center;
    }

    .quiz-type-selector {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1rem;
      margin-bottom: 2rem;
    }

    .type-card {
      border: 2px solid var(--border);
      border-radius: var(--radius);
      padding: 1.2rem;
      cursor: pointer;
      transition: all 0.2s;
    }

    .type-card:hover, .type-card.selected {
      border-color: var(--primary);
      background: var(--primary-light);
    }

    .quiz-word {
      font-size: 2.2rem;
      font-weight: 700;
      color: var(--text-main);
      margin: 1.5rem 0;
    }

    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .option-btn {
      padding: 1.2rem;
      font-size: 1.05rem;
      background: #f8fafc;
      border: 2px solid var(--border);
      border-radius: var(--radius);
      cursor: pointer;
      font-weight: 500;
      transition: all 0.2s;
      text-align: left;
    }

    .option-btn:hover {
      border-color: var(--primary);
      background: white;
    }

    .hidden { display: none !important; }
  </style>
</head>
<body>

  <header>
    <h1>✨ VocabMaster</h1>
    <div id="user-info">
      <span id="current-user-display" style="margin-right: 1rem; font-weight: 500;">未登入</span>
      <button class="btn btn-secondary" style="padding: 0.4rem 0.8rem; font-size: 0.85rem;" onclick="logout()">切換帳號</button>
    </div>
  </header>

  <div class="container">
    <div id="auth-section" class="card">
      <h2 style="margin-top:0;">👋 歡迎使用 VocabMaster</h2>
      <p style="color: var(--text-muted);">請輸入您的名字以載入個人專屬單字庫與學習進度：</p>
      <div class="form-group">
        <input type="text" id="username-input" placeholder="例如: Alex" />
      </div>
      <button class="btn" style="width: 100%;" onclick="login()">進入單字庫</button>
    </div>

    <div id="app-nav" class="nav-bar hidden">
      <button class="nav-btn active" onclick="switchTab('list')">📖 單字總覽</button>
      <button class="nav-btn" onclick="switchTab('add')">➕ 新增單字</button>
      <button class="nav-btn" onclick="switchTab('quiz')">✍️ 多樣化測驗</button>
    </div>

    <div id="list-tab" class="tab-content hidden">
      <div class="card">
        <div style="display: flex; gap: 1rem; margin-bottom: 1.5rem;">
          <input type="text" id="search-input" placeholder="🔍 搜尋單字、中文解釋..." oninput="renderWordList()">
          <select id="filter-select" onchange="renderWordList()" style="width: 180px;">
            <option value="all">顯示全部</option>
            <option value="error">僅顯示易錯單字</option>
          </select>
        </div>
        <div id="word-list" class="word-grid"></div>
      </div>
    </div>

    <div id="add-tab" class="tab-content hidden">
      <div class="card">
        <h2 style="margin-top:0;">➕ 新增英文單字</h2>
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
            </select>
          </div>
          <div class="form-group">
            <label>中文解釋 (Meaning)</label>
            <input type="text" id="word-meaning" required placeholder="例如: 堅持不懈的">
          </div>
          <div class="form-group">
            <label>英文例句 (Sentence) - 可選，用於句子翻譯題</label>
            <textarea id="word-sentence" rows="2" placeholder="例如: She is persistent in pursuing her goal."></textarea>
          </div>
          <button type="submit" class="btn" style="width: 100%;">儲存至單字庫</button>
        </form>
      </div>
    </div>

    <div id="quiz-tab" class="tab-content hidden">
      <div class="card quiz-container" id="quiz-start-box">
        <h2>🎯 選擇測驗模式</h2>
        <p style="color: var(--text-muted); margin-bottom: 2rem;">請選擇您希望進行的測驗類型：</p>
        
        <div class="quiz-type-selector">
          <div class="type-card selected" onclick="selectQuizType('choice_en_zh', this)">
            <h3>🔠 英譯中選擇</h3>
            <p style="font-size: 0.85rem; color: var(--text-muted);">看英文，選擇正確中文解釋</p>
          </div>
          <div class="type-card" onclick="selectQuizType('choice_zh_en', this)">
            <h3>🔠 中譯英選擇</h3>
            <p style="font-size: 0.85rem; color: var(--text-muted);">看中文，選擇正確英文單字</p>
          </div>
          <div class="type-card" onclick="selectQuizType('spelling', this)">
            <h3>✍️ 拼字填空題</h3>
            <p style="font-size: 0.85rem; color: var(--text-muted);">看中文與提示，拼寫英文單字</p>
          </div>
        </div>

        <button class="btn" style="padding: 0.8rem 2.5rem;" onclick="startQuiz()">開始測驗</button>
      </div>

      <div class="card quiz-container hidden" id="quiz-running-box">
        <div style="text-align: right; color: var(--text-muted);" id="quiz-progress">題號 1 / 5</div>
        <div class="quiz-word" id="quiz-question-display">Word</div>
        <div id="quiz-sub-prompt" style="color: var(--text-muted); margin-bottom: 1rem;"></div>

        <div class="options-grid" id="quiz-options-container"></div>

        <div id="quiz-input-container" class="hidden">
          <input type="text" id="quiz-type-input" placeholder="請輸入對應的英文單字..." style="max-width: 400px; text-align: center; margin-bottom: 1rem;">
          <br>
          <button class="btn" onclick="submitInputAnswer()">提交答案</button>
        </div>
      </div>

      <div class="card hidden" id="quiz-result-box">
        <h2>📊 測驗結算與考後反省</h2>
        <p id="quiz-score-summary" style="font-size: 1.1rem; font-weight: 600;"></p>
        <hr style="border: none; border-top: 1px solid var(--border); margin: 1.5rem 0;">
        <h3>❌ 本次錯題反省列表（已自動歸類為易錯單字）：</h3>
        <div id="wrong-words-container"></div>
        <br>
        <button class="btn" onclick="startQuiz()">再測一次</button>
      </div>
    </div>
  </div>

  <script>
    let currentUser = "";
    let vocabData = [];
    let currentQuizType = "choice_en_zh";
    let currentQuizIndex = 0;
    let currentQuizQuestions = [];
    let wrongAnswers = [];

    const defaultVocab = [
      { id: 1, word: "apple", pos: "n.", meaning: "蘋果", sentence: "I eat an apple every day.", isError: false, errorCount: 0 },
      { id: 2, word: "resilient", pos: "adj.", meaning: "有彈性的；適應力強的", sentence: "She is resilient in the face of difficulties.", isError: true, errorCount: 2 },
      { id: 3, word: "calculate", pos: "v.", meaning: "計算", sentence: "We need to calculate the total cost.", isError: false, errorCount: 0 }
    ];

    function login() {
      const username = document.getElementById("username-input").value.trim();
      if (!username) return alert("請輸入使用者名稱！");
      currentUser = username;
      document.getElementById("current-user-display").innerText = `👤 ${currentUser}`;
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
    }

    function loadUserData() {
      const savedData = localStorage.getItem(`vocab_data_${currentUser}`);
      vocabData = savedData ? JSON.parse(savedData) : [...defaultVocab];
      saveUserData();
    }

    function saveUserData() {
      if (currentUser) localStorage.setItem(`vocab_data_${currentUser}`, JSON.stringify(vocabData));
    }

    function switchTab(tabName) {
      document.querySelectorAll(".tab-content").forEach(el => el.classList.add("hidden"));
      document.querySelectorAll(".nav-btn").forEach(el => el.classList.remove("active"));
      
      if (tabName === 'list') {
        document.getElementById("list-tab").classList.remove("hidden");
        event.target.classList.add("active");
        renderWordList();
      } else if (tabName === 'add') {
        document.getElementById("add-tab").classList.remove("hidden");
        event.target.classList.add("active");
      } else if (tabName === 'quiz') {
        document.getElementById("quiz-tab").classList.remove("hidden");
        event.target.classList.add("active");
        resetQuizUI();
      }
    }

    function renderWordList(highlightId = null) {
      const container = document.getElementById("word-list");
      const keyword = document.getElementById("search-input").value.toLowerCase();
      const filter = document.getElementById("filter-select").value;

      container.innerHTML = "";
      let filtered = vocabData.filter(item => {
        const matchesKey = item.word.toLowerCase().includes(keyword) || item.meaning.includes(keyword);
        const matchesFilter = filter === 'all' || (filter === 'error' && item.isError);
        return matchesKey && matchesFilter;
      });

      if (filtered.length === 0) {
        container.innerHTML = `<p style="grid-column: 1/-1; color: var(--text-muted);">尚無單字資料。</p>`;
        return;
      }

      filtered.forEach(item => {
        const card = document.createElement("div");
        card.className = `word-card ${item.isError ? 'error-marked' : ''}`;
        card.id = `word-card-${item.id}`;
        card.innerHTML = `
          <div style="font-size: 1.25rem; font-weight: 700; margin-bottom: 0.3rem;">
            ${item.word} ${item.isError ? '<span class="badge badge-error">易錯</span>' : ''}
          </div>
          <div style="margin-bottom: 0.5rem;">
            <span class="badge badge-pos">${item.pos}</span>
            <span style="font-weight: 500;">${item.meaning}</span>
          </div>
          ${item.sentence ? `<p style="font-size: 0.85rem; color: var(--text-muted); margin: 0.5rem 0;">💬 ${item.sentence}</p>` : ''}
          <div style="margin-top: 1rem; display: flex; justify-content: space-between;">
            <button class="btn btn-secondary" style="padding: 0.3rem 0.6rem; font-size: 0.8rem;" onclick="toggleError(${item.id})">
              ${item.isError ? '取消易錯' : '標註易錯'}
            </button>
            <button class="btn btn-danger" style="padding: 0.3rem 0.6rem; font-size: 0.8rem;" onclick="deleteWord(${item.id})">刪除</button>
          </div>
        `;
        container.appendChild(card);
      });

      if (highlightId) {
        setTimeout(() => {
          const el = document.getElementById(`word-card-${highlightId}`);
          if (el) {
            el.scrollIntoView({ behavior: 'smooth', block: 'center' });
            el.style.boxShadow = "0 0 0 3px var(--primary)";
            setTimeout(() => el.style.boxShadow = "none", 2500);
          }
        }, 100);
      }
    }

    function addWord(e) {
      e.preventDefault();
      const spelling = document.getElementById("word-spelling").value.trim();
      const pos = document.getElementById("word-pos").value;
      const meaning = document.getElementById("word-meaning").value.trim();
      const sentence = document.getElementById("word-sentence").value.trim();

      vocabData.push({ id: Date.now(), word: spelling, pos, meaning, sentence, isError: false, errorCount: 0 });
      saveUserData();
      alert("單字新增成功！");
      document.getElementById("add-word-form").reset();
      switchTab('list');
    }

    function deleteWord(id) {
      if (confirm("確定要刪除此單字？")) {
        vocabData = vocabData.filter(i => i.id !== id);
        saveUserData();
        renderWordList();
      }
    }

    function toggleError(id) {
      const item = vocabData.find(i => i.id === id);
      if (item) {
        item.isError = !item.isError;
        saveUserData();
        renderWordList();
      }
    }

    // 測驗機制
    function selectQuizType(type, el) {
      currentQuizType = type;
      document.querySelectorAll(".type-card").forEach(c => c.classList.remove("selected"));
      el.classList.add("selected");
    }

    function resetQuizUI() {
      document.getElementById("quiz-start-box").classList.remove("hidden");
      document.getElementById("quiz-running-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.add("hidden");
    }

    function startQuiz() {
      if (vocabData.length < 2) return alert("單字庫至少需要有 2 個單字才能開始測驗！");
      currentQuizQuestions = [...vocabData].sort(() => 0.5 - Math.random()).slice(0, 5);
      currentQuizIndex = 0;
      wrongAnswers = [];

      document.getElementById("quiz-start-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.add("hidden");
      document.getElementById("quiz-running-box").classList.remove("hidden");
      showNextQuestion();
    }

    function showNextQuestion() {
      if (currentQuizIndex >= currentQuizQuestions.length) return finishQuiz();

      const q = currentQuizQuestions[currentQuizIndex];
      document.getElementById("quiz-progress").innerText = `題號 ${currentQuizIndex + 1} / ${currentQuizQuestions.length}`;
      
      const optionsContainer = document.getElementById("quiz-options-container");
      const inputContainer = document.getElementById("quiz-input-container");
      optionsContainer.classList.add("hidden");
      inputContainer.classList.add("hidden");

      if (currentQuizType === 'choice_en_zh') {
        document.getElementById("quiz-question-display").innerText = q.word;
        document.getElementById("quiz-sub-prompt").innerText = `請選擇正確的中文解釋（詞性：${q.pos}）`;
        optionsContainer.classList.remove("hidden");
        renderOptions(q, 'meaning');
      } else if (currentQuizType === 'choice_zh_en') {
        document.getElementById("quiz-question-display").innerText = `${q.pos} ${q.meaning}`;
        document.getElementById("quiz-sub-prompt").innerText = "請選擇正確的英文單字";
        optionsContainer.classList.remove("hidden");
        renderOptions(q, 'word');
      } else if (currentQuizType === 'spelling') {
        document.getElementById("quiz-question-display").innerText = `${q.pos} ${q.meaning}`;
        document.getElementById("quiz-sub-prompt").innerText = `請拼寫出英文單字 (首字母: ${q.word[0]})`;
        inputContainer.classList.remove("hidden");
        document.getElementById("quiz-type-input").value = "";
        document.getElementById("quiz-type-input").focus();
      }
    }

    function renderOptions(q, key) {
      let options = [q];
      let others = vocabData.filter(i => i.id !== q.id).sort(() => 0.5 - Math.random());
      while (options.length < Math.min(4, vocabData.length)) options.push(others.pop());
      options.sort(() => 0.5 - Math.random());

      const container = document.getElementById("quiz-options-container");
      container.innerHTML = "";
      options.forEach(opt => {
        const btn = document.createElement("button");
        btn.className = "option-btn";
        btn.innerText = opt[key];
        btn.onclick = () => checkAnswer(opt.id === q.id, q);
        container.appendChild(btn);
      });
    }

    function submitInputAnswer() {
      const userInput = document.getElementById("quiz-type-input").value.trim().toLowerCase();
      const q = currentQuizQuestions[currentQuizIndex];
      checkAnswer(userInput === q.word.toLowerCase(), q);
    }

    function checkAnswer(isCorrect, questionObj) {
      if (!isCorrect) {
        const item = vocabData.find(i => i.id === questionObj.id);
        if (item) {
          item.isError = true;
          item.errorCount = (item.errorCount || 0) + 1;
          saveUserData();
        }
        wrongAnswers.push(questionObj);
      }
      currentQuizIndex++;
      showNextQuestion();
    }

    function finishQuiz() {
      document.getElementById("quiz-running-box").classList.add("hidden");
      document.getElementById("quiz-result-box").classList.remove("hidden");

      const total = currentQuizQuestions.length;
      const correct = total - wrongAnswers.length;
      document.getElementById("quiz-score-summary").innerText = `🎯 測驗完成！得分：${correct} / ${total} (正確率: ${Math.round(correct/total * 100)}%)`;

      const wrongContainer = document.getElementById("wrong-words-container");
      wrongContainer.innerHTML = "";

      if (wrongAnswers.length === 0) {
        wrongContainer.innerHTML = "<p style='color: var(--success); font-weight: 600;'>🎉 恭喜！本次測驗全對，太棒了！</p>";
      } else {
        wrongAnswers.forEach(item => {
          const div = document.createElement("div");
          div.style.cssText = "display: flex; justify-content: space-between; align-items: center; padding: 1rem; border-bottom: 1px solid var(--border);";
          div.innerHTML = `
            <div>
              <strong style="font-size: 1.1rem; color: var(--danger);">${item.word}</strong>
              <span class="badge badge-pos">${item.pos}</span> ${item.meaning}
            </div>
            <button class="btn btn-secondary" style="font-size: 0.85rem;" onclick="jumpToWord(${item.id})">
              一鍵直達單字頁 ➔
            </button>
          `;
          wrongContainer.appendChild(div);
        });
      }
    }

    function jumpToWord(id) {
      switchTab('list');
      renderWordList(id);
    }
  </script>
</body>
</html>
