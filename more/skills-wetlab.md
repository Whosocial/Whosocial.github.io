---
layout: page
title: 湿实验与微流控
permalink: /more/skills-wetlab/
---

<!-- 页面专属 CSS 样式 -->
<style>
  /* 全局介绍段落 */
  .intro-text {
    font-size: 1.1rem;
    color: #4a5568;
    line-height: 1.8;
    margin-bottom: 3rem;
    text-align: center;
  }
  
  /* 技能大标题 */
  .skill-title {
    border-bottom: 2px solid #eaecef;
    padding-bottom: 0.3em;
    margin-top: 3.5rem;
    margin-bottom: 1.5rem;
    color: #24292e;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  /* 4列网格布局 (用于4个流程的技能) */
  .grid-4-cols {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 20px;
    margin-bottom: 2rem;
  }

  /* 3列网格布局 (用于3个流程的技能) */
  .grid-3-cols {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
    margin-bottom: 2rem;
  }

  /* 上图下文卡片样式 */
  .process-card {
    background: #ffffff;
    border: 1px solid #e1e4e8;
    border-radius: 10px;
    overflow: hidden;
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
  }
  .process-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0,0,0,0.06);
    border-color: #319795;
  }
  
  /* 卡片中的图片区域 */
  .process-img-wrapper {
    width: 100%;
    aspect-ratio: 4/3; /* 锁定图片比例为4:3 */
    background: #f6f8fa;
    border-bottom: 1px solid #e1e4e8;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  .process-img-wrapper img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .img-placeholder-text {
    font-size: 0.85rem;
    color: #6a737d;
    text-align: center;
    padding: 10px;
    line-height: 1.4;
  }

  /* 卡片中的文字区域 */
  .process-text {
    padding: 15px;
    flex: 1;
  }
  .process-text h4 {
    margin-top: 0;
    margin-bottom: 8px;
    color: #0366d6;
    font-size: 1.05rem;
    text-align: center;
  }
  .process-text p {
    font-size: 0.9rem;
    color: #586069;
    margin-bottom: 0;
    line-height: 1.5;
  }
</style>

<div class="intro-text">
  严谨的实验操作是获取可靠科研数据的第一步。<br>
  这里展示了我在博士期间建立并熟练掌握的核心实验技术体系，从微观流体控制到单细胞精度的荧光成像，再到多组学的数据挖掘。
</div>

<!-- ========================================== -->
<!-- 技能一：微流控实验平台 (4个流程) -->
<!-- ========================================== -->
<h2 class="skill-title"><span>💧 01. 微流控实验平台开发全流程</span></h2>
<p style="color: #586069; font-size: 0.95rem; margin-bottom: 1.5rem;">
  具备独立完成微流控芯片设计、加工及动态成像平台搭建的全链路能力，用于在体外精准模拟复杂的细菌生长微环境。
</p>

<div class="grid-4-cols">
  <div class="process-card">
    <div class="process-img-wrapper">
      <!-- <img src="/assets/images/wetlab-microfluidics-1.jpg" alt="设计"> -->
      <div class="img-placeholder-text">🖼️ AutoCAD<br>芯片设计图纸</div>
    </div>
    <div class="process-text">
      <h4>1. 芯片设计</h4>
      <p>利用 AutoCAD 建立二维/三维流道模型，精确计算流体通道尺寸与微观化学梯度。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <!-- <img src="/assets/images/wetlab-microfluidics-2.jpg" alt="光刻"> -->
      <div class="img-placeholder-text">🖼️ 黄光室<br>光刻工艺实拍</div>
    </div>
    <div class="process-text">
      <h4>2. 光刻制模</h4>
      <p>在超净间操作匀胶机与曝光机，使用 SU-8 等光刻胶将设计转化为高精度硅片阳模。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <!-- <img src="/assets/images/wetlab-microfluidics-3.jpg" alt="制作"> -->
      <div class="img-placeholder-text">🖼️ PDMS<br>倒模与键合</div>
    </div>
    <div class="process-text">
      <h4>3. PDMS 制作</h4>
      <p>熟练掌握 PDMS 倒模固化流程，使用等离子清洗机将芯片与盖玻片进行不可逆键合。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <!-- <img src="/assets/images/wetlab-microfluidics-4.jpg" alt="平台搭建"> -->
      <div class="img-placeholder-text">🖼️ 流体控制<br>与成像平台</div>
    </div>
    <div class="process-text">
      <h4>4. 平台搭建</h4>
      <p>集成注射泵、恒温系统与显微镜，实现高度可控的长时程活细胞动态培养平台。</p>
    </div>
  </div>
</div>


<!-- ========================================== -->
<!-- 技能二：菌株基因编辑与改造 (3个流程) -->
<!-- ========================================== -->
<h2 class="skill-title"><span>🧬 02. 菌株基因编辑与改造</span></h2>
<p style="color: #586069; font-size: 0.95rem; margin-bottom: 1.5rem;">
  熟练掌握微生物学核心实验操作，能够从分子层面快速构建所需的目标菌株体系。
</p>

<div class="grid-3-cols">
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 厌氧/好氧<br>菌株培养实拍</div>
    </div>
    <div class="process-text">
      <h4>1. 菌株培养</h4>
      <p>熟练掌握大肠杆菌等模式微生物的厌氧与好氧培养技术，精准控制生长条件及生长曲线的测定。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 质粒图谱<br>或克隆验证图</div>
    </div>
    <div class="process-text">
      <h4>2. 基因编辑与质粒改造</h4>
      <p>熟练应用 CRISPR-Cas 系统及传统同源重组技术进行高效的基因敲除、敲入，以及质粒载体的构建与改造。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 药敏实验<br>或表型对比图</div>
    </div>
    <div class="process-text">
      <h4>3. 生理表征</h4>
      <p>通过 MIC/MBC 测定、生长曲线、形态学观察等手段，系统评估改造后菌株在特定环境压力下的生理表型变化。</p>
    </div>
  </div>
</div>


<!-- ========================================== -->
<!-- 技能三：组学实验与分析 (4个流程) -->
<!-- ========================================== -->
<h2 class="skill-title"><span>📊 03. 组学实验与分析</span></h2>
<p style="color: #586069; font-size: 0.95rem; margin-bottom: 1.5rem;">
  打通了从上游湿实验样本制备到下游干实验生物信息学数据挖掘的完整技术闭环。
</p>

<div class="grid-4-cols">
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 提取纯化<br>或质检电泳图</div>
    </div>
    <div class="process-text">
      <h4>1. 样品收集与制备</h4>
      <p>严格控制酶解与降解，高质量完成代谢物提取、总 RNA 提取提纯以及标准化的转录组文库构建 (建库)。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 测序仪<br>或送样单展示</div>
    </div>
    <div class="process-text">
      <h4>2. 样品上机</h4>
      <p>完成样本的精确定量与质控（QC），熟知主流高通量测序平台及质谱平台的上机标准与参数要求。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 火山图<br>或通路富集代码</div>
    </div>
    <div class="process-text">
      <h4>3. 数据分析</h4>
      <p>处理下机原始数据，完成序列比对、差异表达基因 (DEG) 筛选以及 KEGG/GO 等下游代谢通路的富集分析。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 组学数据<br>高级可视化图表</div>
    </div>
    <div class="process-text">
      <h4>4. 可视化呈现</h4>
      <p>利用 Python 或 R 语言将海量多维的组学数据转化为直观、可解释的学术级热图、PCA 图与网络图。</p>
    </div>
  </div>
</div>


<!-- ========================================== -->
<!-- 技能四：显微成像 (3个流程) -->
<!-- ========================================== -->
<h2 class="skill-title"><span>📸 04. 显微成像技术</span></h2>
<p style="color: #586069; font-size: 0.95rem; margin-bottom: 1.5rem;">
  擅长通过多维度的显微成像技术，捕捉微观生命活动的动态瞬间，为机制解析提供最直观的视觉证据。
</p>

<div class="grid-3-cols">
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 高清单细胞<br>荧光成像图</div>
    </div>
    <div class="process-text">
      <h4>1. 单细胞成像</h4>
      <p>在极高倍率下实现单细胞精度的形态学追踪与细胞内荧光探针定位，记录个体细胞的异质性代谢状态与死亡过程。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 生物被膜<br>大规模群体成像</div>
    </div>
    <div class="process-text">
      <h4>2. 群体成像</h4>
      <p>利用图像拼接与大视野扫描技术，捕捉细菌生物被膜等复杂群落的整体空间结构分布与亚群动态扩展演化过程。</p>
    </div>
  </div>

  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ 激光共聚焦<br>显微镜操作实况</div>
    </div>
    <div class="process-text">
      <h4>3. 显微镜高阶操作</h4>
      <p>精通宽场荧光显微镜及激光共聚焦显微镜 (CLSM) 的操作与调试，熟练设置 Z 轴层扫 (Z-stack) 及时间序列多通道采集参数。</p>
    </div>
  </div>
</div>


<!-- ========================================== -->
<!-- 技能五：占位符 (待填充) -->
<!-- ========================================== -->
<h2 class="skill-title"><span>🧪 05. [技能五名称待填充]</span></h2>
<p style="color: #586069; font-size: 0.95rem; margin-bottom: 1.5rem;">
  [此处可用于展示你的第 5 项湿实验技能，例如：常规分子生物学实验 (PCR/WB等)、动物模型构建等]
</p>

<div class="grid-3-cols">
  <!-- 流程 1 -->
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ [图片占位]</div>
    </div>
    <div class="process-text">
      <h4>1. [流程一名称]</h4>
      <p>[在此处添加流程描述文字...]</p>
    </div>
  </div>

  <!-- 流程 2 -->
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ [图片占位]</div>
    </div>
    <div class="process-text">
      <h4>2. [流程二名称]</h4>
      <p>[在此处添加流程描述文字...]</p>
    </div>
  </div>
  
  <!-- 流程 3 (如需4列可复制上方 process-card 代码并更改外层 div class 为 grid-4-cols) -->
  <div class="process-card">
    <div class="process-img-wrapper">
      <div class="img-placeholder-text">🖼️ [图片占位]</div>
    </div>
    <div class="process-text">
      <h4>3. [流程三名称]</h4>
      <p>[在此处添加流程描述文字...]</p>
    </div>
  </div>
</div>
