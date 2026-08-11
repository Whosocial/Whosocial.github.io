---
layout: page
title: 了解更多
permalink: /more/
---

<!-- 页面内嵌 CSS，用于实现卡片的悬浮动态效果 -->
<style>
  .hub-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin-top: 2rem;
  }
  .hub-card {
    background: #fafbfc;
    border: 1px solid #e1e4e8;
    border-radius: 12px;
    padding: 30px 25px;
    text-decoration: none;
    color: inherit;
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .hub-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.08);
    border-color: #319795;
    text-decoration: none;
  }
  .hub-icon {
    font-size: 2.5rem;
    margin-bottom: 15px;
  }
  .hub-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #24292e;
    margin-bottom: 10px;
  }
  .hub-desc {
    font-size: 0.95rem;
    color: #586069;
    line-height: 1.6;
    margin-bottom: 20px;
  }
  .hub-link-text {
    font-size: 0.9rem;
    color: #319795;
    font-weight: 600;
    display: flex;
    align-items: center;
  }
</style>

<p style="font-size: 1.1rem; color: #4a5568; margin-bottom: 2rem; text-align: center;">
  这里是我更详细的个人档案与资源分享，欢迎深入探索。👇
</p>

<div class="hub-grid">
  
  <!-- 板块 1：科研生涯 -->
  <a href="/more/career/" class="hub-card">
    <div>
      <div class="hub-icon">🔬</div>
      <div class="hub-title">科研生涯</div>
      <div class="hub-desc">详细记录我的学术轨迹、主导的核心科研项目背后的故事，以及我对科研的深度思考与复盘。</div>
    </div>
    <div class="hub-link-text">阅读详情 <span>&rarr;</span></div>
  </a>

  <!-- 板块 2：荣誉大厅 -->
  <a href="/more/honors/" class="hub-card">
    <div>
      <div class="hub-icon">🏆</div>
      <div class="hub-title">荣誉大厅</div>
      <div class="hub-desc">记录一路走来获得的奖学金、学术认可与各类荣誉。这是对过去的肯定，也是对未来的鞭策。</div>
    </div>
    <div class="hub-link-text">阅读详情 <span>&rarr;</span></div>
  </a>

  <!-- 板块 3：技能展示 -->
  <a href="/more/skills/" class="hub-card">
    <div>
      <div class="hub-icon">🛠️</div>
      <div class="hub-title">技能展示</div>
      <div class="hub-desc">全面拆解我在湿实验、微流控、编程与数据分析方面的硬核技能，以及我的手工 DIY 跨界能力。</div>
    </div>
    <div class="hub-link-text">阅读详情 <span>&rarr;</span></div>
  </a>

  <!-- 板块 4：他山之石 -->
  <a href="/more/resources/" class="hub-card">
    <div>
      <div class="hub-icon">⛰️</div>
      <div class="hub-title">他山之石</div>
      <div class="hub-desc">“可以攻玉”。分享我平时收集的科研效率工具和有趣的跨界学习资源。</div>
    </div>
    <div class="hub-link-text">阅读详情 <span>&rarr;</span></div>
  </a>

</div>
