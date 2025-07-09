---
title: 歡迎來到我的部落格ㄛ(❍ᴥ❍ʋ). 這裡會放一些工作、學習跟生活日記。
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
  /* grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); */
  gap: 2rem;
}
.card {
  border-radius: 8px;
  padding: 1.5rem;
  height: 100%; /* 讓同一行的卡片等高 */
  transition: background-color 0.3s, border-color 0.3s, transform 0.2s, box-shadow 0.3s;
  /* cursor: pointer; */
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

/* Timeline */
.timeline {
  position: relative;
  list-style: none;
  padding-left: 1.5rem;
  margin: 1.5rem 0 0 0.5rem;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0.5rem;
  bottom: 0.5rem;
  width: 2px;
}
.timeline-item {
  position: relative;
  margin-bottom: 1.2rem;
}
.timeline-item:last-child {
  margin-bottom: 0;
}
.timeline-dot {
  position: absolute;
  left: -1.5rem; /* Match padding-left of .timeline */
  top: 0.35em;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  transform: translateX(-4px); /* Center the dot on the line */
}
.timeline-content h5 {
  margin: 0 0 0.25rem 0;
  font-weight: 600;
}
.timeline-content p {
  margin: 0;
  font-size: 0.9em;
  font-style: italic;
}

/* Light Mode Timeline */
body.light-mode .timeline::before { background: #eee; }
body.light-mode .timeline-dot { background: #aaa; border: 2px solid #fdfdfd; }
body.light-mode .timeline-content p { color: #666; }

/* Dark Mode Timeline */
body.dark-mode .timeline::before { background: #555; }
body.dark-mode .timeline-dot { background: #888; border: 2px solid #3c3c3c; }
body.dark-mode .timeline-content p { color: #bbb; }

/* Experience Section - Base */
.experience {
  border-radius: 15px;
  padding: 30px;
  max-width: 700px;
  margin: auto;
  position: relative;
  transition: background-color 0.3s, border-color 0.3s, box-shadow 0.3s, transform 0.2s;
}
.experience h2 {
  margin-bottom: 20px;
}
.job {
  margin-bottom: 30px;
  position: relative;
  padding-left: 30px;
}
.job::before {
  content: "";
  position: absolute;
  top: 30px;
  left: 9px;
  width: 2px;
  height: 100%;
}
.job::after {
  content: "";
  position: absolute;
  top: 8px;
  left: 4px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  z-index: 1;
}
.job:last-child::before {
  height: 0px; /* 最後一個只畫到圓點為止 */
}
.job-title {
  font-weight: bold;
  font-size: 1.2em;
}
.company {
  margin-top: 4px;
  margin-bottom: 8px;
}
.description {
  line-height: 1.6;
}

/* Experience Section - Light Mode */
body.light-mode .experience { background: #f8f9fa; border: 1px solid #ddd; box-shadow: 0 4px 8px rgba(0,0,0,0.05); }
body.light-mode .experience h2 { color: #333; }
body.light-mode .job::before { background-color: #ddd; }
body.light-mode .job::after { background-color: #aaa; }
body.light-mode .job-title { color: #222; }
body.light-mode .company { color: #007bff; }
body.light-mode .description { color: #555; }
body.light-mode .experience:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
}
body.light-mode .experience:active {
  transform: translateY(1px) scale(0.99);
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

/* Experience Section - Dark Mode */
body.dark-mode .experience { background-color: #1e293b; border: 1px solid #277496; box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4); }
body.dark-mode .experience h2 { color: #e0f2fe; }
body.dark-mode .job::before { background-color: #277496; }
body.dark-mode .job::after { background-color: #38bdf8; }
body.dark-mode .job-title { color: #f1f5f9; }
body.dark-mode .company { color: #38bdf8; }
body.dark-mode .description { color: #94a3b8; }
body.dark-mode .experience:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.35);
}
body.dark-mode .experience:active {
  transform: translateY(1px) scale(0.99);
  box-shadow: 0 2px 4px rgba(0,0,0,0.25);
}
</style>

<div class="welcome-message">
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
      <li> 興趣可以當飯吃嗎？只能把吃飯當興趣。</li>
      <li> 無人自願作惡。</li>
    </ul>
  </div>

  <div class="card">
    <h3>學經歷 (Education &amp; Experience)</h3>
    <ul class="timeline">
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>軟體工程師</h5>
          <p>工作經驗</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>前端工程師</h5>
          <p>工作經驗</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>全端工程師</h5>
          <p>工作經驗</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>國立臺灣科技大學</h5>
          <p>學歷</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>臺中市立臺中工業高級中等學校</h5>
          <p>學歷</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>臺中市立神岡國民中學</h5>
          <p>學歷</p>
        </div>
      </li>
      <li class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h5>臺中市岸裡國民小學</h5>
          <p>學歷</p>
        </div>
      </li>
    </ul>
  </div>

  <div class="experience">
     <h2>工作經歷</h2>
        <div class="job">
            <div class="job-title">前端開發工程師</div>
            <div class="company">科技公司・2022 - 現在</div>
            <div class="description">
                負責開發和維護公司主要產品的前端介面，使用 React 和 TypeScript 建構高效能的 Web 應用程式，並與設計師和後端工程師密切合作。
            </div>
        </div>
        <div class="job">
            <div class="job-title">初級前端開發者</div>
            <div class="company">新創公司・2021 - 2022</div>
            <div class="description">
                參與多個客戶專案的開發，學習現代前端框架和工具，並建立了紮實的 JavaScript 和 CSS 基礎。
            </div>
        </div>
    </div>

  <div class="card">
    <h3>技能與興趣 (Skills &amp; Hobbies)</h3>
    <h4>電腦語言</h4>
    <ul>
      <li> C++</li>
      <li> TypeScript</li>
      <li> Python</li>
    </ul>
    <h4>興趣</h4>
    <ul>
      <li> 游泳</li>
      <li> 羽球</li>
      <li> 健身</li>
      <li> 慢跑</li>
      <li> 單車</li>
    </ul>
    <h4>曾參與社團</h4>
    <ul>
      <li> 熱舞社</li>
      <li> 吉他社</li>
      <li> 武術社</li>
    </ul>
  </div>

  <div class="card">
    <h3>近期專案 (Recent Projects)</h3>
    <p>近期熱衷於開發與研究：</p>
      <h4>Line Bot</h4>
        <ul>
          <li>AI 問答</li>
          <li>夜市營業表</li>
          <li>台灣各地區天氣</li>
        </ul>
      <h4>n8n 工作流</h4>
        <ul>
          <li>擷取Brief AI電子報發送至Line群組</li>
          <li>英文造句文法檢查</li>
          <li>串接Google Sheet儲存單字</li>
        </ul>
      <h4>React與Vue框架學習</h4>
      <h4>RAG 技術</h4>
        <ul>
          <li>LangChain</li>
          <li>LangGraph</li>
          <li>Vector DB</li>
        </ul>
  </div>
</div>
