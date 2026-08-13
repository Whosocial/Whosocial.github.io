---
layout: home
---

<!-- 动态粒子背景容器与样式 -->
<style>
  #particles-js {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1; /* 确保背景在最底层，不遮挡任何文字和链接 */
    background-color: #ffffff; /* 干净的纯白底色 */
  }
  /* 给主内容区增加一点半透明的白色背板，确保文字在粒子穿过时依然清晰 */
  .home-content-wrapper {
    position: relative;
    z-index: 1;
    background: rgba(255, 255, 255, 0.75);
    backdrop-filter: blur(3px); /* 轻微的毛玻璃效果 */
    padding: 20px;
    border-radius: 12px;
  }
</style>

<div id="particles-js"></div>

<!-- 引入 particles.js 脚本 -->
<script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
<script>
  particlesJS("particles-js", {
    "particles": {
      "number": { "value": 60, "density": { "enable": true, "value_area": 800 } },
      "color": { "value": "#319795" }, /* 采用清新的孔雀绿，类似荧光标记 */
      "shape": { "type": "circle" },
      "opacity": { "value": 0.5, "random": true, "anim": { "enable": true, "speed": 1, "opacity_min": 0.1, "sync": false } },
      "size": { "value": 4, "random": true, "anim": { "enable": true, "speed": 2, "size_min": 0.1, "sync": false } },
      "line_linked": { "enable": true, "distance": 150, "color": "#319795", "opacity": 0.3, "width": 1 },
      "move": { "enable": true, "speed": 1.5, "direction": "none", "random": true, "straight": false, "out_mode": "out", "bounce": false }
    },
    "interactivity": {
      "detect_on": "canvas",
      "events": {
        "onhover": { "enable": true, "mode": "grab" }, /* 鼠标悬浮时产生连接线条 */
        "onclick": { "enable": true, "mode": "push" }, /* 点击时增加粒子 */
        "resize": true
      },
      "modes": {
        "grab": { "distance": 200, "line_linked": { "opacity": 0.8 } },
        "push": { "particles_nb": 3 }
      }
    },
    "retina_detect": true
  });
</script>

<!-- ================= 以下为你原本的首页内容 ================= -->
<div class="home-content-wrapper">

  <div style="text-align: center; margin-top: 2rem; margin-bottom: 3rem;">
    <!-- 头像 -->
    <img src="/assets/images/20260808170010.jpg" alt="古月的头像" style="width: 160px; height: 160px; border-radius: 50%; object-fit: cover; box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1); border: 4px solid #f8f9fa;">

    <h1 style="margin-top: 1.5rem; font-weight: bold; font-size: 2.2rem;">你好，我是古月 👋</h1>
    <p style="font-size: 1.2rem; color: #4a5568; max-width: 600px; margin: 0 auto; line-height: 1.6;">
      欢迎来到我的数字花园。我是一位刚刚取得基础医学博士学位的“研究僧”。<br>热衷于探索微观世界的秩序与奥秘。
    </p>
  </div>

  <hr style="border: 0; height: 1px; background-image: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0)); margin: 3rem 0;">

  <div style="text-align: center;">
    <h3 style="color: #2d3748; margin-bottom: 1.5rem;">🔬 我的研究领域</h3>
    
    <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 12px;">
      <span style="background: #ebf4ff; color: #2b6cb0; padding: 6px 16px; border-radius: 9999px; font-size: 0.95rem; font-weight: 500;">🦠 细菌群落与生物被膜</span>
      <span style="background: #f0fff4; color: #2f855a; padding: 6px 16px; border-radius: 9999px; font-size: 0.95rem; font-weight: 500;">🧬 代谢异质性</span>
      <span style="background: #fff5f5; color: #c53030; padding: 6px 16px; border-radius: 9999px; font-size: 0.95rem; font-weight: 500;">💊 抗生素响应</span>
      <span style="background: #faf5ff; color: #6b46c1; padding: 6px 16px; border-radius: 9999px; font-size: 0.95rem; font-weight: 500;">🔬 荧光成像与系统生物学</span>
    </div>
  </div>

  <hr style="border: 0; height: 1px; background-image: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0)); margin: 3rem 0;">

  <div style="max-width: 600px; margin: 0 auto;">
    <h3 style="text-align: center; color: #2d3748; margin-bottom: 1.5rem;">📝 博客记录</h3>
    <ul style="list-style-type: none; padding: 0; line-height: 2;">
      <li><strong>💡 灵光乍现：</strong> 记录突然涌现的科研点子或生活趣事</li>
      <li><strong>📚 思考与感悟：</strong> 读书笔记与文献阅读的心得</li>
      <li><strong>🧬 科研手记：</strong> 实验中的踩坑记录与经验总结</li>
      <li><strong>💻 效率工具：</strong> 好玩好用的软件、脚本推荐</li>
      <li><strong>🌱 动手尝试：</strong> 从零开始的各种折腾（比如这个网站）</li>
    </ul>
  </div>

</div>

