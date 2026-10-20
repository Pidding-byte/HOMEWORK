<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>马克思主义 · 真理之光</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --red: #c8102e;
    --deep-red: #8f0c1f;
    --gold: #f5c542;
    --ink: #2b2b2b;
    --paper: #f7f4ee;
  }

  body {
    font-family: "Noto Serif SC", "STSong", "SimSun", serif;
    color: var(--ink);
    background: var(--paper);
    line-height: 1.8;
  }

  /* ===== 顶部导航 ===== */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    display: flex; justify-content: space-between; align-items: center;
    padding: 14px 6%;
    background: rgba(200, 16, 46, .95);
    box-shadow: 0 2px 12px rgba(0,0,0,.25);
    z-index: 100;
  }
  nav .logo { color: #fff; font-size: 1.25rem; font-weight: bold; letter-spacing: 4px; }
  nav ul { list-style: none; display: flex; gap: 28px; }
  nav a { color: #ffe9e9; text-decoration: none; font-size: .95rem; transition: color .3s; }
  nav a:hover { color: var(--gold); }

  /* ===== 首屏横幅 ===== */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center; align-items: center;
    text-align: center;
    background:
      linear-gradient(rgba(120, 5, 20, .78), rgba(60, 0, 10, .85)),
      repeating-linear-gradient(45deg, #a50d24 0 14px, #8f0c1f 14px 28px);
    color: #fff;
    padding: 100px 8% 60px;
  }
  .hero .star { font-size: 3rem; color: var(--gold); margin-bottom: 20px; }
  .hero h1 { font-size: clamp(2.2rem, 6vw, 4rem); letter-spacing: 10px; margin-bottom: 18px; text-shadow: 0 4px 18px rgba(0,0,0,.5); }
  .hero p.sub { font-size: clamp(1rem, 2.4vw, 1.35rem); letter-spacing: 6px; color: #ffd7d7; margin-bottom: 40px; }
  .hero .motto {
    max-width: 720px;
    font-size: clamp(1.05rem, 2.2vw, 1.3rem);
    font-style: italic;
    color: #ffe9c9;
    border-left: 4px solid var(--gold);
    padding-left: 20px;
    text-align: left;
    background: rgba(0,0,0,.18);
    padding: 18px 22px;
    border-radius: 6px;
  }
  .scroll-hint { margin-top: 60px; color: #ffc9c9; font-size: .9rem; animation: bounce 2s infinite; }
  @keyframes bounce { 0%,100%{transform:translateY(0)} 50%{transform:translateY(10px)} }

  /* ===== 通用区块 ===== */
  section { padding: 90px 8%; }
  .section-title { text-align: center; margin-bottom: 55px; }
  .section-title h2 { font-size: 2rem; letter-spacing: 6px; color: var(--deep-red); }
  .section-title .line { width: 70px; height: 4px; background: var(--gold); margin: 14px auto 0; border-radius: 2px; }

  /* ===== 三大组成部分 ===== */
  .cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 30px; }
  .card {
    background: #fff;
    border-radius: 10px;
    padding: 36px 28px;
    box-shadow: 0 6px 24px rgba(0,0,0,.08);
    border-top: 5px solid var(--red);
    transition: transform .35s, box-shadow .35s;
  }
  .card:hover { transform: translateY(-8px); box-shadow: 0 14px 34px rgba(200,16,46,.18); }
  .card .icon { font-size: 2.4rem; margin-bottom: 14px; }
  .card h3 { color: var(--red); margin-bottom: 12px; letter-spacing: 2px; }
  .card p { font-size: .95rem; color: #555; }

  /* ===== 时间线 ===== */
  .timeline-wrap { background: #fff; }
  .timeline { position: relative; max-width: 820px; margin: 0 auto; }
  .timeline::before {
    content: ""; position: absolute; left: 18px; top: 0; bottom: 0;
    width: 4px; background: linear-gradient(var(--red), var(--gold));
    border-radius: 2px;
  }
  .t-item { position: relative; padding: 0 0 42px 60px; }
  .t-item::before {
    content: ""; position: absolute; left: 8px; top: 6px;
    width: 24px; height: 24px; border-radius: 50%;
    background: var(--paper); border: 5px solid var(--red);
  }
  .t-item .year { color: var(--deep-red); font-weight: bold; font-size: 1.15rem; letter-spacing: 2px; }
  .t-item h4 { margin: 4px 0 6px; font-size: 1.05rem; }
  .t-item p { color: #555; font-size: .93rem; }

  /* ===== 金句 ===== */
  .quotes { background: var(--deep-red); color: #fff; }
  .quotes .section-title h2 { color: #fff; }
  .quote-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 26px; }
  .quote {
    background: rgba(255,255,255,.07);
    border: 1px solid rgba(255,255,255,.15);
    border-radius: 10px;
    padding: 30px 26px;
    transition: background .3s;
  }
  .quote:hover { background: rgba(255,255,255,.14); }
  .quote .mark { font-size: 2.2rem; color: var(--gold); line-height: 1; }
  .quote p { font-style: italic; margin: 10px 0 14px; }
  .quote .who { color: var(--gold); font-size: .9rem; letter-spacing: 2px; }

  /* ===== 实践意义 ===== */
  .meaning p.lead { max-width: 860px; margin: 0 auto 30px; text-align: center; font-size: 1.1rem; color: #444; }
  .pillars { display: flex; flex-wrap: wrap; justify-content: center; gap: 16px; margin-top: 36px; }
  .pillar {
    background: #fff; border: 2px solid var(--red); color: var(--deep-red);
    padding: 12px 26px; border-radius: 999px; font-weight: bold; letter-spacing: 2px;
    transition: all .3s;
  }
  .pillar:hover { background: var(--red); color: #fff; transform: scale(1.06); }

  /* ===== 页脚 ===== */
  footer {
    background: #5c0813; color: #f3c9c9; text-align: center;
    padding: 40px 8% 30px; font-size: .9rem;
  }
  footer .foot-star { color: var(--gold); font-size: 1.4rem; margin-bottom: 10px; }
  footer p { margin: 4px 0; }

  @media (max-width: 640px) {
    nav ul { display: none; }
    section { padding: 60px 6%; }
  }
</style>
<base target="_blank">
</head>
<body>

<nav>
  <div class="logo">☭ 真理之光</div>
  <ul>
    <li><a href="#components">理论精髓</a></li>
    <li><a href="#timeline">发展脉络</a></li>
    <li><a href="#quotes">经典金句</a></li>
    <li><a href="#meaning">时代价值</a></li>
  </ul>
</nav>

<!-- 首屏 -->
<header class="hero">
  <div class="star">★</div>
  <h1>马克思主义</h1>
  <p class="sub">科学的世界观 · 人民的理论 · 实践的理论 · 开放的理论</p>
  <div class="motto">
    “马克思主义博大精深，归根到底就是一句话，为人类求解放。”
  </div>
  <div class="scroll-hint">▼ 向下滚动了解更多</div>
</header>

<!-- 三大组成部分 -->
<section id="components">
  <div class="section-title">
    <h2>理论的三大组成部分</h2>
    <div class="line"></div>
  </div>
  <div class="cards">
    <div class="card">
      <div class="icon">📖</div>
      <h3>马克思主义哲学</h3>
      <p>辩证唯物主义与历史唯物主义，揭示了自然界、人类社会和思维发展的一般规律，提供了科学的世界观和方法论。</p>
    </div>
    <div class="card">
      <div class="icon">⚖️</div>
      <h3>马克思主义政治经济学</h3>
      <p>透过商品与货币的现象，揭示剩余价值生产的秘密，剖析资本主义经济运行规律，论证其历史暂时性。</p>
    </div>
    <div class="card">
      <div class="icon">🚩</div>
      <h3>科学社会主义</h3>
      <p>唯物史观与剩余价值学说使社会主义从空想变为科学，指明了无产阶级解放全人类、实现共产主义的必由之路。</p>
    </div>
  </div>
</section>

<!-- 时间线 -->
<section id="timeline" class="timeline-wrap">
  <div class="section-title">
    <h2>发展脉络</h2>
    <div class="line"></div>
  </div>
  <div class="timeline">
    <div class="t-item">
      <div class="year">1818 · 1820</div>
      <h4>伟人诞生</h4>
      <p>马克思出生于德国特里尔，恩格斯出生于德国巴门，人类思想的两位巨人由此登上历史舞台。</p>
    </div>
    <div class="t-item">
      <div class="year">1848</div>
      <h4>《共产党宣言》发表</h4>
      <p>“一个幽灵，共产主义的幽灵，在欧洲游荡。”马克思主义正式诞生，成为无产阶级斗争的思想武器。</p>
    </div>
    <div class="t-item">
      <div class="year">1867</div>
      <h4>《资本论》第一卷出版</h4>
      <p>马克思以毕生心血揭示资本主义生产方式的运动规律，被誉为“工人阶级的圣经”。</p>
    </div>
    <div class="t-item">
      <div class="year">1917</div>
      <h4>十月革命</h4>
      <p>列宁领导俄国十月革命取得胜利，科学社会主义从理论变为现实，开辟了人类历史新纪元。</p>
    </div>
    <div class="t-item">
      <div class="year">1949</div>
      <h4>新中国成立</h4>
      <p>中国共产党把马克思主义基本原理同中国具体实际相结合，古老东方大国浴火重生。</p>
    </div>
    <div class="t-item">
      <div class="year">新时代</div>
      <h4>21世纪的中国实践</h4>
      <p>马克思主义在当代中国展现出强大生命力，中国特色社会主义道路越走越宽广。</p>
    </div>
  </div>
</section>

<!-- 经典金句 -->
<section id="quotes" class="quotes">
  <div class="section-title">
    <h2>经典金句</h2>
    <div class="line"></div>
  </div>
  <div class="quote-grid">
    <div class="quote">
      <div class="mark">“</div>
      <p>哲学家们只是解释世界，而问题在于改变世界。</p>
      <div class="who">—— 马克思《关于费尔巴哈的提纲》</div>
    </div>
    <div class="quote">
      <div class="mark">“</div>
      <p>人的本质不是单个人所固有的抽象物，在其现实性上，它是一切社会关系的总和。</p>
      <div class="who">—— 马克思</div>
    </div>
    <div class="quote">
      <div class="mark">“</div>
      <p>无产者在这场革命中失去的只是锁链，他们获得的将是整个世界。全世界无产者，联合起来！</p>
      <div class="who">—— 《共产党宣言》</div>
    </div>
    <div class="quote">
      <div class="mark">“</div>
      <p>在科学上没有平坦的大道，只有不畏劳苦沿着陡峭山路攀登的人，才有希望达到光辉的顶点。</p>
      <div class="who">—— 马克思《资本论》法文版序言</div>
    </div>
  </div>
</section>

<!-- 时代价值 -->
<section id="meaning" class="meaning">
  <div class="section-title">
    <h2>时代价值</h2>
    <div class="line"></div>
  </div>
  <p class="lead">
    马克思主义不仅是认识世界的科学工具，更是改造世界的伟大指南。在百年未有之大变局下，
    它依然闪耀着穿透时空的真理光芒，指引着人类追求公平正义与自由解放的道路。
  </p>
  <div class="pillars">
    <div class="pillar">人民立场</div>
    <div class="pillar">实践观点</div>
    <div class="pillar">矛盾分析</div>
    <div class="pillar">历史视野</div>
    <div class="pillar">人民民主</div>
    <div class="pillar">共同富裕</div>
    <div class="pillar">人的全面发展</div>
  </div>
</section>

<footer>
  <div class="foot-star">★ ★ ★</div>
  <p>让信仰之光点亮前行之路 · 让真理之树常青</p>
  <p>真理的光芒，永不过时 —— 静态宣传页</p>
</footer>

</body>
</html>
