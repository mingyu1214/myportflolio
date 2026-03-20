<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Full-Stack Developer Portfolio</title>
  <style>
    :root {
      --bg: #0b1020;
      --bg-soft: #121933;
      --card: rgba(18, 25, 51, 0.72);
      --line: rgba(255,255,255,0.08);
      --text: #eef2ff;
      --muted: #aab3d1;
      --primary: #6ea8fe;
      --secondary: #7ef0c7;
      --accent: #a78bfa;
      --shadow: 0 20px 50px rgba(0,0,0,0.32);
      --radius: 22px;
      --max: 1180px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: Inter, "Noto Sans KR", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at 10% 20%, rgba(110,168,254,0.22), transparent 30%),
        radial-gradient(circle at 90% 10%, rgba(167,139,250,0.18), transparent 25%),
        radial-gradient(circle at 50% 100%, rgba(126,240,199,0.12), transparent 30%),
        linear-gradient(180deg, #060916 0%, #0b1020 100%);
      min-height: 100vh;
      overflow-x: hidden;
    }

    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }

    .container {
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
    }

    .blur-orb {
      position: fixed;
      width: 340px;
      height: 340px;
      border-radius: 50%;
      filter: blur(90px);
      opacity: 0.18;
      pointer-events: none;
      z-index: 0;
    }
    .orb-1 { background: var(--primary); top: 2%; left: -80px; }
    .orb-2 { background: var(--accent); top: 30%; right: -100px; }
    .orb-3 { background: var(--secondary); bottom: 0; left: 30%; }

    header {
      position: sticky;
      top: 0;
      z-index: 50;
      backdrop-filter: blur(14px);
      background: rgba(6, 9, 22, 0.56);
      border-bottom: 1px solid rgba(255,255,255,0.06);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      min-height: 72px;
      gap: 20px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 700;
      letter-spacing: -0.03em;
    }

    .brand-badge {
      width: 38px;
      height: 38px;
      border-radius: 14px;
      display: grid;
      place-items: center;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      box-shadow: var(--shadow);
      font-weight: 800;
    }

    .menu {
      display: flex;
      gap: 18px;
      align-items: center;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .menu a {
      padding: 10px 12px;
      border-radius: 12px;
      transition: 0.25s ease;
    }

    .menu a:hover,
    .menu a.active {
      color: var(--text);
      background: rgba(255,255,255,0.06);
    }

    .menu-toggle {
      display: none;
      width: 44px;
      height: 44px;
      border-radius: 14px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,0.04);
      color: var(--text);
      cursor: pointer;
    }

    .hero {
      position: relative;
      z-index: 1;
      padding: 72px 0 34px;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 26px;
      align-items: center;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 8px 14px;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,0.08);
      background: rgba(255,255,255,0.04);
      color: var(--secondary);
      font-size: 0.92rem;
      margin-bottom: 18px;
    }

    .hero h1 {
      margin: 0;
      font-size: clamp(2.4rem, 5vw, 5rem);
      line-height: 1.04;
      letter-spacing: -0.045em;
    }

    .gradient-text {
      background: linear-gradient(135deg, #ffffff 10%, var(--primary) 40%, var(--secondary) 75%, var(--accent) 100%);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .hero p {
      color: var(--muted);
      font-size: 1.05rem;
      line-height: 1.8;
      margin: 22px 0 30px;
      max-width: 62ch;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      margin-bottom: 24px;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 14px 18px;
      border-radius: 16px;
      font-weight: 600;
      border: 1px solid transparent;
      transition: transform .2s ease, background .2s ease, border-color .2s ease;
      cursor: pointer;
    }

    .btn:hover { transform: translateY(-2px); }
    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--accent));
      color: white;
      box-shadow: var(--shadow);
    }
    .btn-secondary {
      background: rgba(255,255,255,0.04);
      border-color: var(--line);
      color: var(--text);
    }

    .hero-meta {
      display: grid;
      grid-template-columns: repeat(3, minmax(0,1fr));
      gap: 14px;
    }

    .meta-card,
    .glass-card {
      background: var(--card);
      border: 1px solid var(--line);
      backdrop-filter: blur(14px);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
    }

    .meta-card {
      padding: 18px;
    }

    .meta-card strong {
      display: block;
      font-size: 1.4rem;
      margin-bottom: 6px;
    }

    .meta-card span {
      color: var(--muted);
      font-size: 0.92rem;
    }

    .hero-panel {
      padding: 22px;
      position: relative;
      overflow: hidden;
    }

    .hero-panel::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(110,168,254,0.16), rgba(167,139,250,0.05), rgba(126,240,199,0.08));
      pointer-events: none;
    }

    .profile-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 14px;
      margin-bottom: 22px;
      position: relative;
      z-index: 1;
    }

    .avatar {
      width: 76px;
      height: 76px;
      border-radius: 24px;
      display: grid;
      place-items: center;
      font-size: 1.35rem;
      font-weight: 800;
      background: linear-gradient(135deg, rgba(110,168,254,0.25), rgba(167,139,250,0.3));
      border: 1px solid rgba(255,255,255,0.08);
    }

    .status {
      padding: 8px 12px;
      border-radius: 999px;
      font-size: 0.88rem;
      color: var(--secondary);
      background: rgba(126,240,199,0.08);
      border: 1px solid rgba(126,240,199,0.2);
      white-space: nowrap;
    }

    .panel-list {
      position: relative;
      z-index: 1;
      display: grid;
      gap: 12px;
    }

    .panel-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 14px;
      padding: 14px 16px;
      border-radius: 16px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.05);
    }

    .panel-item b { display: block; margin-bottom: 4px; }
    .panel-item span { color: var(--muted); font-size: 0.92rem; }
    .tag {
      padding: 8px 10px;
      border-radius: 999px;
      font-size: 0.8rem;
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.08);
      white-space: nowrap;
    }

    section {
      position: relative;
      z-index: 1;
      padding: 42px 0;
    }

    .section-title {
      display: flex;
      justify-content: space-between;
      align-items: end;
      gap: 16px;
      margin-bottom: 22px;
    }

    .section-title h2 {
      margin: 0;
      font-size: clamp(1.7rem, 3vw, 2.4rem);
      letter-spacing: -0.03em;
    }

    .section-title p {
      margin: 8px 0 0;
      color: var(--muted);
      max-width: 56ch;
      line-height: 1.7;
    }

    .skill-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 18px;
    }

    .filter-btn {
      padding: 10px 14px;
      border-radius: 999px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,0.04);
      color: var(--text);
      cursor: pointer;
      transition: 0.2s ease;
      font-weight: 600;
    }

    .filter-btn.active,
    .filter-btn:hover {
      background: linear-gradient(135deg, rgba(110,168,254,0.18), rgba(167,139,250,0.18));
      border-color: rgba(110,168,254,0.35);
    }

    .skills-grid,
    .projects-grid,
    .timeline,
    .contact-grid {
      display: grid;
      gap: 18px;
    }

    .skills-grid {
      grid-template-columns: repeat(4, minmax(0,1fr));
    }

    .skill-card {
      padding: 20px;
      transition: transform .25s ease, border-color .25s ease;
    }

    .skill-card:hover {
      transform: translateY(-4px);
      border-color: rgba(110,168,254,0.28);
    }

    .skill-card .icon {
      width: 48px;
      height: 48px;
      border-radius: 16px;
      display: grid;
      place-items: center;
      font-size: 1.25rem;
      margin-bottom: 14px;
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.08);
    }

    .skill-card h3 {
      margin: 0 0 8px;
      font-size: 1.08rem;
    }

    .skill-card p {
      margin: 0 0 16px;
      color: var(--muted);
      line-height: 1.65;
      font-size: 0.95rem;
    }

    .progress {
      height: 9px;
      border-radius: 999px;
      background: rgba(255,255,255,0.06);
      overflow: hidden;
    }

    .progress span {
      display: block;
      height: 100%;
      border-radius: inherit;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      width: 0;
      transition: width 1s ease;
    }

    .projects-grid {
      grid-template-columns: repeat(3, minmax(0,1fr));
    }

    .project-card {
      overflow: hidden;
      transition: transform .25s ease, border-color .25s ease;
    }

    .project-card:hover {
      transform: translateY(-5px);
      border-color: rgba(167,139,250,0.24);
    }

    .project-visual {
      aspect-ratio: 16 / 10;
      border-bottom: 1px solid var(--line);
      background:
        radial-gradient(circle at 20% 20%, rgba(110,168,254,0.3), transparent 30%),
        radial-gradient(circle at 80% 20%, rgba(167,139,250,0.25), transparent 28%),
        linear-gradient(135deg, rgba(255,255,255,0.08), rgba(255,255,255,0.02));
      position: relative;
      overflow: hidden;
    }

    .project-visual::after {
      content: attr(data-label);
      position: absolute;
      bottom: 16px;
      left: 16px;
      font-size: 0.82rem;
      padding: 8px 10px;
      border-radius: 999px;
      background: rgba(10,14,28,0.7);
      border: 1px solid rgba(255,255,255,0.08);
      color: var(--text);
    }

    .project-body {
      padding: 20px;
    }

    .project-body h3 {
      margin: 0 0 10px;
      font-size: 1.12rem;
    }

    .project-body p {
      color: var(--muted);
      line-height: 1.7;
      margin: 0 0 16px;
      font-size: 0.95rem;
    }

    .stack {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 18px;
    }

    .stack span {
      padding: 7px 10px;
      border-radius: 999px;
      font-size: 0.82rem;
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.06);
      color: var(--muted);
    }

    .project-links {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .project-links a {
      font-size: 0.92rem;
      font-weight: 600;
      padding: 10px 12px;
      border-radius: 12px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.06);
    }

    .timeline {
      grid-template-columns: repeat(2, minmax(0,1fr));
    }

    .timeline-card {
      padding: 22px;
    }

    .timeline-card small {
      display: inline-block;
      color: var(--secondary);
      margin-bottom: 10px;
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    .timeline-card h3 {
      margin: 0 0 10px;
      font-size: 1.1rem;
    }

    .timeline-card p {
      margin: 0;
      color: var(--muted);
      line-height: 1.75;
    }

    .contact-grid {
      grid-template-columns: 1fr 1fr;
      align-items: stretch;
    }

    .contact-card {
      padding: 24px;
    }

    .contact-list {
      display: grid;
      gap: 12px;
      margin-top: 18px;
    }

    .contact-item {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      padding: 14px 16px;
      border-radius: 16px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.06);
      color: var(--muted);
    }

    .contact-item b { color: var(--text); }

    .contact-form {
      display: grid;
      gap: 14px;
    }

    .contact-form input,
    .contact-form textarea {
      width: 100%;
      padding: 14px 16px;
      border-radius: 16px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,0.04);
      color: var(--text);
      outline: none;
      resize: vertical;
      font: inherit;
    }

    .contact-form input:focus,
    .contact-form textarea:focus {
      border-color: rgba(110,168,254,0.36);
      box-shadow: 0 0 0 4px rgba(110,168,254,0.12);
    }

    .footer {
      padding: 26px 0 40px;
      color: var(--muted);
      text-align: center;
      font-size: 0.95rem;
    }

    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity .7s ease, transform .7s ease;
    }

    .reveal.show {
      opacity: 1;
      transform: translateY(0);
    }

    @media (max-width: 1024px) {
      .hero-grid,
      .contact-grid,
      .timeline,
      .skills-grid,
      .projects-grid {
        grid-template-columns: 1fr 1fr;
      }
      .hero-grid { grid-template-columns: 1fr; }
    }

    @media (max-width: 760px) {
      .menu-toggle { display: inline-grid; place-items: center; }
      .menu {
        position: absolute;
        top: 72px;
        left: 16px;
        right: 16px;
        flex-direction: column;
        align-items: stretch;
        padding: 12px;
        border-radius: 18px;
        background: rgba(8, 12, 28, 0.95);
        border: 1px solid var(--line);
        box-shadow: var(--shadow);
        display: none;
      }
      .menu.open { display: flex; }
      .hero-meta,
      .skills-grid,
      .projects-grid,
      .timeline,
      .contact-grid {
        grid-template-columns: 1fr;
      }
      .hero {
        padding-top: 46px;
      }
      .hero-actions {
        flex-direction: column;
        align-items: stretch;
      }
      .section-title {
        flex-direction: column;
        align-items: start;
      }
    }
  </style>
</head>
<body>
  <div class="blur-orb orb-1"></div>
  <div class="blur-orb orb-2"></div>
  <div class="blur-orb orb-3"></div>

  <header>
    <div class="container nav">
      <a href="#home" class="brand">
        <div class="brand-badge">FM</div>
        <div>
          <div>Portfolio</div>
          <small style="color: var(--muted); font-weight: 500;">Full-Stack · AI · Cloud</small>
        </div>
      </a>

      <button class="menu-toggle" id="menuToggle" aria-label="메뉴 열기">☰</button>
      <nav class="menu" id="menu">
        <a href="#about">소개</a>
        <a href="#skills">전문분야</a>
        <a href="#projects">프로젝트</a>
        <a href="#experience">경력</a>
        <a href="#contact">연락처</a>
      </nav>
    </div>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="container hero-grid">
        <div class="reveal">
          <div class="eyebrow">● Azure Cloud · Data Analytics · Machine Learning · AI</div>
          <h1>
            비즈니스 문제를<br />
            <span class="gradient-text">확장 가능한 제품과 데이터 기반 인사이트</span>로 해결하는
            풀스택 개발자
          </h1>
          <p>
            웹 애플리케이션 설계부터 클라우드 인프라 구축, 데이터 분석 파이프라인 구성,
            머신러닝 모델 적용, 인공지능 서비스 연계까지 전 과정을 아우르는 개발 포트폴리오입니다.
            사용자 경험과 운영 효율, 그리고 실질적인 성과를 함께 고려하는 개발을 지향합니다.
          </p>

          <div class="hero-actions">
            <a href="#projects" class="btn btn-primary">주요 프로젝트 보기</a>
            <a href="#contact" class="btn btn-secondary">협업 문의하기</a>
          </div>

          <div class="hero-meta">
            <div class="meta-card glass-card">
              <strong>10+</strong>
              <span>실무형 기술 스택</span>
            </div>
            <div class="meta-card glass-card">
              <strong>4개</strong>
              <span>핵심 전문분야</span>
            </div>
            <div class="meta-card glass-card">
              <strong>End-to-End</strong>
              <span>기획부터 배포까지</span>
            </div>
          </div>
        </div>

        <div class="hero-panel glass-card reveal">
          <div class="profile-top">
            <div style="display:flex; align-items:center; gap:14px;">
              <div class="avatar">AI</div>
              <div>
                <strong style="font-size: 1.1rem; display:block; margin-bottom:6px;">최민규 · Full-Stack Developer</strong>
                <span style="color: var(--muted); line-height:1.6;">Azure Cloud · Data Analyst · ML Engineer · AI Specialist</span>
              </div>
            </div>
            <div class="status">Available for Project</div>
          </div>

          <div class="panel-list">
            <div class="panel-item">
              <div>
                <b>Frontend & Backend</b>
                <span>반응형 UI, API 설계, 인증, 배포 자동화</span>
              </div>
              <div class="tag">Full-Stack</div>
            </div>
            <div class="panel-item">
              <div>
                <b>Azure Cloud Architecture</b>
                <span>App Service, Functions, Storage, CI/CD, 모니터링</span>
              </div>
              <div class="tag">Cloud</div>
            </div>
            <div class="panel-item">
              <div>
                <b>Data & ML Workflow</b>
                <span>분석 대시보드, 예측 모델, 자동화 파이프라인</span>
              </div>
              <div class="tag">Analytics</div>
            </div>
            <div class="panel-item">
              <div>
                <b>AI Product Integration</b>
                <span>추천, 분류, 생성형 AI, 운영형 서비스 연결</span>
              </div>
              <div class="tag">AI</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="about">
      <div class="container">
        <div class="section-title reveal">
          <div>
            <h2>소개</h2>
            <p>
              기술을 단순히 구현하는 것을 넘어, 사용성과 확장성, 그리고 데이터 기반의 개선 가능성까지 고려하는 개발을 수행합니다.
              서비스 개발과 클라우드 운영, 분석 자동화, 머신러닝 적용을 유기적으로 연결하는 것이 강점입니다.
            </p>
          </div>
        </div>
      </div>
    </section>

    <section id="skills">
      <div class="container">
        <div class="section-title reveal">
          <div>
            <h2>전문분야</h2>
            <p>버튼을 눌러 분야별 역량 카드를 필터링할 수 있습니다.</p>
          </div>
        </div>

        <div class="skill-filters reveal">
          <button class="filter-btn active" data-filter="all">전체</button>
          <button class="filter-btn" data-filter="fullstack">풀스택 개발</button>
          <button class="filter-btn" data-filter="azure">Azure 클라우드</button>
          <button class="filter-btn" data-filter="data">데이터 분석</button>
          <button class="filter-btn" data-filter="ml">머신러닝/인공지능</button>
        </div>

        <div class="skills-grid">
          <article class="skill-card glass-card reveal" data-category="fullstack">
            <div class="icon">⚙️</div>
            <h3>웹 애플리케이션 아키텍처</h3>
            <p>프론트엔드와 백엔드를 연결하는 구조 설계, REST API 구성, 인증 처리, 상태 관리까지 일관된 흐름으로 구현합니다.</p>
            <div class="progress"><span data-width="92%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="fullstack">
            <div class="icon">🖥️</div>
            <h3>반응형 UI/UX 개발</h3>
            <p>모바일, 태블릿, 데스크톱 환경에서 자연스럽게 작동하는 인터페이스를 구성하고 상호작용 요소를 설계합니다.</p>
            <div class="progress"><span data-width="89%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="azure">
            <div class="icon">☁️</div>
            <h3>Azure 클라우드 인프라</h3>
            <p>Azure App Service, Storage, Functions, Key Vault, Monitor 기반으로 안정적인 운영 환경을 설계하고 배포합니다.</p>
            <div class="progress"><span data-width="90%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="azure">
            <div class="icon">🚀</div>
            <h3>CI/CD 및 운영 자동화</h3>
            <p>GitHub Actions와 클라우드 환경을 연동하여 테스트, 빌드, 배포 흐름을 자동화하고 운영 효율을 높입니다.</p>
            <div class="progress"><span data-width="87%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="data">
            <div class="icon">📊</div>
            <h3>데이터 시각화 및 인사이트</h3>
            <p>수집한 데이터를 정제하고 KPI 중심으로 시각화하여 의사결정에 필요한 인사이트를 명확하게 전달합니다.</p>
            <div class="progress"><span data-width="91%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="data">
            <div class="icon">🗂️</div>
            <h3>데이터 파이프라인 설계</h3>
            <p>ETL 흐름, 스케줄링, 저장 구조 설계, 분석용 데이터셋 구성 등 데이터 활용을 위한 기반을 마련합니다.</p>
            <div class="progress"><span data-width="84%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="ml">
            <div class="icon">🤖</div>
            <h3>머신러닝 모델 적용</h3>
            <p>분류, 예측, 추천 문제에 적합한 모델을 선택하고 성능 평가와 개선 과정을 통해 실서비스 적용 가능성을 높입니다.</p>
            <div class="progress"><span data-width="88%"></span></div>
          </article>

          <article class="skill-card glass-card reveal" data-category="ml">
            <div class="icon">🧠</div>
            <h3>인공지능 서비스 연계</h3>
            <p>생성형 AI, 자연어 처리, 자동 분류, 대화형 기능 등을 서비스와 연결하여 사용자 경험을 고도화합니다.</p>
            <div class="progress"><span data-width="86%"></span></div>
          </article>
        </div>
      </div>
    </section>

    <section id="projects">
      <div class="container">
        <div class="section-title reveal">
          <div>
            <h2>프로젝트</h2>
            <p>GitHub 포트폴리오에 적합하도록 기술 역량이 분명하게 드러나는 예시 프로젝트 섹션입니다.</p>
          </div>
        </div>

        <div class="projects-grid">
          <article class="project-card glass-card reveal">
            <div class="project-visual" data-label="Full-Stack + Azure"></div>
            <div class="project-body">
              <h3>스마트 업무 관리 플랫폼</h3>
              <p>사용자 인증, 프로젝트 관리, 실시간 대시보드, 알림 기능을 포함한 협업형 웹 애플리케이션입니다. Azure 기반으로 배포 및 운영 자동화를 구성했습니다.</p>
              <div class="stack">
                <span>HTML/CSS/JS</span><span>Node.js</span><span>Azure App Service</span><span>GitHub Actions</span>
              </div>
              <div class="project-links">
                <a href="#">Live Demo</a>
                <a href="#">GitHub Repo</a>
              </div>
            </div>
          </article>

          <article class="project-card glass-card reveal">
            <div class="project-visual" data-label="Data Analytics"></div>
            <div class="project-body">
              <h3>매출 데이터 분석 대시보드</h3>
              <p>다양한 원천 데이터를 정제하고 핵심 KPI를 시각화하여 운영 성과를 빠르게 파악할 수 있도록 설계한 분석형 서비스입니다.</p>
              <div class="stack">
                <span>Python</span><span>SQL</span><span>Dashboard</span><span>ETL</span>
              </div>
              <div class="project-links">
                <a href="#">Case Study</a>
                <a href="#">GitHub Repo</a>
              </div>
            </div>
          </article>

          <article class="project-card glass-card reveal">
            <div class="project-visual" data-label="ML · AI"></div>
            <div class="project-body">
              <h3>AI 기반 예측 및 추천 엔진</h3>
              <p>사용자 행동 데이터와 이력 정보를 기반으로 예측 모델과 추천 로직을 적용하여 개인화 경험을 제공하는 프로젝트입니다.</p>
              <div class="stack">
                <span>Machine Learning</span><span>Azure ML</span><span>API Integration</span><span>Model Serving</span>
              </div>
              <div class="project-links">
                <a href="#">Model Report</a>
                <a href="#">GitHub Repo</a>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="experience">
      <div class="container">
        <div class="section-title reveal">
          <div>
            <h2>경력 및 작업 방식</h2>
            <p>기술 스택을 실제 결과물로 연결하는 과정에서 중요하게 생각하는 원칙과 업무 흐름입니다.</p>
          </div>
        </div>

        <div class="timeline">
          <article class="timeline-card glass-card reveal">
            <small>STEP 01</small>
            <h3>문제 정의와 요구사항 분석</h3>
            <p>비즈니스 목표와 사용자 요구를 분석하여 핵심 기능, 데이터 구조, 인프라 방향을 먼저 설계합니다.</p>
          </article>
          <article class="timeline-card glass-card reveal">
            <small>STEP 02</small>
            <h3>서비스 중심의 풀스택 구현</h3>
            <p>사용자 경험과 운영 편의성을 동시에 고려하여 프론트엔드, 백엔드, 데이터 흐름을 통합적으로 구현합니다.</p>
          </article>
          <article class="timeline-card glass-card reveal">
            <small>STEP 03</small>
            <h3>클라우드 배포 및 안정화</h3>
            <p>Azure 환경에서 확장성과 보안, 운영 모니터링을 고려해 배포 구조를 잡고 자동화 흐름을 정리합니다.</p>
          </article>
          <article class="timeline-card glass-card reveal">
            <small>STEP 04</small>
            <h3>데이터 분석과 AI 고도화</h3>
            <p>사용 로그와 비즈니스 데이터를 기반으로 분석 대시보드를 만들고, 필요 시 머신러닝/AI 기능으로 서비스 가치를 높입니다.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="section-title reveal">
          <div>
            <h2>연락처</h2>
            <p>실제 GitHub Pages 배포 시 아래 정보는 사용자 정보에 맞게 교체하여 활용하시면 됩니다.</p>
          </div>
        </div>

        <div class="contact-grid">
          <article class="contact-card glass-card reveal">
            <h3 style="margin-top:0; font-size:1.2rem;">기본 정보</h3>
            <div class="contact-list">
              <div class="contact-item"><b>Email</b><span>your.email@example.com</span></div>
              <div class="contact-item"><b>GitHub</b><span>github.com/yourname</span></div>
              <div class="contact-item"><b>LinkedIn</b><span>linkedin.com/in/yourname</span></div>
              <div class="contact-item"><b>Focus</b><span>Full-Stack · Azure · Data · AI</span></div>
            </div>
          </article>

          <article class="contact-card glass-card reveal">
            <h3 style="margin-top:0; font-size:1.2rem;">문의 폼 UI 예시</h3>
            <form class="contact-form" onsubmit="event.preventDefault(); showToast();">
              <input type="text" placeholder="성함" />
              <input type="email" placeholder="이메일" />
              <textarea rows="5" placeholder="문의 내용을 입력해 주세요."></textarea>
              <button class="btn btn-primary" type="submit">문의 보내기</button>
            </form>
          </article>
        </div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="container">© 2026 Full-Stack Developer Portfolio. Built for GitHub Pages.</div>
  </footer>

  <script>
    const menuToggle = document.getElementById('menuToggle');
    const menu = document.getElementById('menu');
    const navLinks = [...document.querySelectorAll('.menu a')];

    menuToggle.addEventListener('click', () => {
      menu.classList.toggle('open');
    });

    navLinks.forEach(link => {
      link.addEventListener('click', () => menu.classList.remove('open'));
    });

    const revealEls = document.querySelectorAll('.reveal');
    const revealObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('show');
          const progressBar = entry.target.querySelector('.progress span');
          if (progressBar) {
            progressBar.style.width = progressBar.dataset.width;
          }
        }
      });
    }, { threshold: 0.14 });

    revealEls.forEach(el => revealObserver.observe(el));

    const filterButtons = document.querySelectorAll('.filter-btn');
    const skillCards = document.querySelectorAll('.skill-card');

    filterButtons.forEach(button => {
      button.addEventListener('click', () => {
        filterButtons.forEach(btn => btn.classList.remove('active'));
        button.classList.add('active');
        const filter = button.dataset.filter;

        skillCards.forEach(card => {
          const category = card.dataset.category;
          const show = filter === 'all' || filter === category;
          card.style.display = show ? 'block' : 'none';
        });
      });
    });

    const sections = document.querySelectorAll('main section[id]');
    const navObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          navLinks.forEach(link => {
            link.classList.toggle('active', link.getAttribute('href') === '#' + entry.target.id);
          });
        }
      });
    }, { threshold: 0.35 });

    sections.forEach(section => navObserver.observe(section));

    function showToast() {
      const existing = document.querySelector('.toast-message');
      if (existing) existing.remove();

      const toast = document.createElement('div');
      toast.className = 'toast-message';
      toast.textContent = '문의 폼 UI 예시입니다. 실제 전송 기능은 백엔드 또는 Form 서비스와 연동해 주세요.';
      Object.assign(toast.style, {
        position: 'fixed',
        bottom: '24px',
        right: '24px',
        maxWidth: '320px',
        padding: '14px 16px',
        borderRadius: '16px',
        color: '#eef2ff',
        background: 'rgba(10,14,28,0.92)',
        border: '1px solid rgba(255,255,255,0.08)',
        boxShadow: '0 16px 40px rgba(0,0,0,0.35)',
        zIndex: '1000',
        lineHeight: '1.6'
      });
      document.body.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }
  </script>
</body>
</html>
