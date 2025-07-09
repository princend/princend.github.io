---
title: Princend's blog
feature_text: |  
  
    
      
  
feature_image: "assets/sunflower-banner.jpg"
excerpt: ""
---

<style>
.welcome-message {
  text-align: center;
  font-size: 1.5em;
  margin-bottom: 2em;
}
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}
.card {
  border-radius: 8px;
  padding: 1.5rem;
  height: 100%; /* 讓同一行的卡片等高 */
  transition: background-color 0.3s, border-color 0.3s, transform 0.2s, box-shadow 0.3s;
  cursor: pointer;
}
.card h3 {
  margin-top: 0;
  padding-bottom: 0.5rem;
}
.card h4 {
  margin-top: 1.5rem;
}
.card ul {
  list-style-type: none;
  padding-left: 0;
}
.card li {
  padding: 0.3rem 0;
}
.card blockquote {
  font-size: 1rem;
  padding-left: 1rem;
  margin-left: 0;
  font-style: italic;
}

/* Light Mode */
body.light-mode .card {
  background: #fdfdfd;
  border: 1px solid #ddd;
  box-shadow: 0 4px 8px rgba(0,0,0,0.05);
}
body.light-mode .card h3 {
  border-bottom: 2px solid #eee;
}
body.light-mode .card blockquote {
  border-left: 4px solid #ccc;
  color: #555;
}
body.light-mode .card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
}
body.light-mode .card:active {
  transform: translateY(1px) scale(0.99);
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

/* Dark Mode */
body.dark-mode .card {
  background: #3c3c3c;
  border: 1px solid #555;
  box-shadow: 0 4px 8px rgba(0,0,0,0.25);
}
body.dark-mode .card h3 {
  border-bottom: 2px solid #555;
}
body.dark-mode .card blockquote {
  border-left: 4px solid #666;
  color: #ccc;
}
body.dark-mode .card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.35);
}
body.dark-mode .card:active {
  transform: translateY(1px) scale(0.99);
  box-shadow: 0 2px 4px rgba(0,0,0,0.25);
}
</style>

<div class="welcome-message">
  歡迎來到我的部落格ㄛ(❍ᴥ❍ʋ).
  <br>
  這裡會放一些工作、學習跟生活日記。
</div>

<div class="grid-container">
  <div class="card">
    <h3>關於我 (About Me)</h3>
    <h4>名字 (Name)</h4>
    <blockquote>你可以叫我 Princend 或是 John</blockquote>
    <h4>名稱由來 (Why Princend?)</h4>
    <blockquote><strong>Princend</strong> = <strong>Prince</strong> + <strong>and</strong><br>因為 "Prince" 這個ID已被使用，而我中文名字的最後一個字發音像 "and"，所以組合成了 "Princend"。</blockquote>
    <h4>座右銘 (Motto)</h4>
    <ul>
      <li>👉 興趣可以當飯吃嗎？只能把吃飯當興趣。</li>
      <li>👉 無人自願作惡。</li>
    </ul>
  </div>

  <div class="card">
    <h3>學經歷 (Education &amp; Experience)</h3>
    <h4>學歷</h4>
    <ul>
      <li>🎓 國立臺灣科技大學</li>
      <li>🎓 臺中市立臺中工業高級中等學校</li>
      <li>🎓 臺中市立神岡國民中學</li>
      <li>🎓 臺中市岸裡國民小學</li>
    </ul>
    <h4>工作經驗</h4>
    <ul>
      <li>👨‍💻 軟體工程師</li>
      <li>👨‍💻 前端工程師</li>
      <li>👨‍💻 全端工程師</li>
    </ul>
  </div>

  <div class="card">
    <h3>技能與興趣 (Skills &amp; Hobbies)</h3>
    <h4>電腦語言</h4>
    <ul>
      <li>- C++</li>
      <li>- TypeScript</li>
      <li>- Python</li>
    </ul>
    <h4>興趣</h4>
    <ul>
      <li>🏊 游泳</li>
      <li>🏸 羽球</li>
      <li>🏋️ 健身</li>
      <li>🏃 慢跑</li>
      <li>🚲 單車</li>
    </ul>
    <h4>曾參與社團</h4>
    <ul>
      <li>🕺 熱舞社</li>
      <li>🎸 吉他社</li>
      <li>🥋 武術社</li>
    </ul>
  </div>

  <div class="card">
    <h3>近期專案 (Recent Projects)</h3>
    <p>近期熱衷於開發與研究：</p>
    <ul>
      <li><strong>Line Bot</strong>
        <ul style="padding-left: 1.5rem; list-style-type: circle;">
          <li>AI 問答</li>
          <li>夜市營業表</li>
          <li>台灣各地區天氣</li>
        </ul>
      </li>
      <li><strong>n8n 工作流</strong>
        <ul style="padding-left: 1.5rem; list-style-type: circle;">
          <li>擷取Brief AI電子報發送至Line群組</li>
          <li>英文造句文法檢查</li>
          <li>串接Google Sheet儲存單字</li>
        </ul>
      </li>
      <li><strong>React與Vue框架學習</strong></li>
      <li><strong>RAG 技術</strong>
        <ul style="padding-left: 1.5rem; list-style-type: circle;">
          <li>LangChain</li>
          <li>LangGraph</li>
          <li>Vector DB</li>
        </ul>
      </li>
    </ul>
  </div>
</div>

<!--
  如果你想展示你的寵物，