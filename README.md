
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>GitHub 个人主页 README 设计 | 炫酷开发者名片</title>
    <!-- 引入 Font Awesome 6 (免费图标库) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- 使用现代、干净的基础样式与暗色主题风格，适合 GitHub README 风格但更生动 -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(145deg, #0a0c10 0%, #12161c 100%);
            font-family: 'Segoe UI', 'Fira Code', 'Courier New', 'SF Mono', monospace, system-ui;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 2rem;
        }

        /* 模拟 GitHub Markdown 卡片风格，但又带一些玻璃拟态效果 */
        .readme-card {
            max-width: 1000px;
            width: 100%;
            background: rgba(13, 17, 23, 0.85);
            backdrop-filter: blur(2px);
            border-radius: 32px;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.6), 0 0 0 1px rgba(48, 54, 61, 0.3);
            overflow: hidden;
            transition: all 0.2s ease;
        }

        /* 内容容器，模拟 README 内边距 */
        .readme-content {
            padding: 2rem 2rem 2.5rem;
        }

        /* 头部区域 - 带徽章 */
        .header-badge {
            display: inline-block;
            background: #238636;
            color: white;
            font-size: 0.7rem;
            font-weight: bold;
            padding: 0.2rem 0.8rem;
            border-radius: 30px;
            letter-spacing: 0.5px;
            margin-bottom: 1.5rem;
            font-family: monospace;
            border: 1px solid #2ea043;
        }

        /* 主要标题区域 */
        .greeting {
            margin-bottom: 1.2rem;
        }

        .greeting h1 {
            font-size: 2.7rem;
            font-weight: 700;
            background: linear-gradient(135deg, #ffffff, #b9c8ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
        }

        .greeting .wave {
            display: inline-block;
            animation: waveAnim 1.8s infinite;
            transform-origin: 70% 70%;
        }

        @keyframes waveAnim {
            0% { transform: rotate(0deg); }
            20% { transform: rotate(14deg); }
            40% { transform: rotate(-8deg); }
            60% { transform: rotate(14deg); }
            80% { transform: rotate(-4deg); }
            100% { transform: rotate(0deg); }
        }

        .bio {
            color: #adbac7;
            font-size: 1.05rem;
            margin-top: 0.6rem;
            line-height: 1.5;
            border-left: 3px solid #2f81f7;
            padding-left: 1rem;
        }

        /* 统计快捷区域 三列布局 类似 github 状态 */
        .stats-mini {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin: 2rem 0 2rem 0;
            justify-content: space-between;
        }

        .stat-item {
            background: #161b22;
            border-radius: 24px;
            padding: 0.8rem 1.2rem;
            flex: 1;
            min-width: 100px;
            text-align: center;
            border: 1px solid #2d333b;
            transition: all 0.2s;
        }

        .stat-item i {
            font-size: 1.8rem;
            color: #539bf5;
            margin-bottom: 0.4rem;
            display: inline-block;
        }

        .stat-number {
            font-size: 1.6rem;
            font-weight: bold;
            color: #e6edf3;
            font-family: monospace;
        }

        .stat-label {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #8b949e;
        }

        /* 技能与工具区域 */
        .section-title {
            font-size: 1.5rem;
            font-weight: 600;
            margin: 1.8rem 0 1rem 0;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #f0f6fc;
            border-bottom: 2px solid #30363d;
            padding-bottom: 0.5rem;
        }

        .skills-cloud {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 1rem;
        }

        .skill-tag {
            background: #21262d;
            color: #c9d1d9;
            padding: 6px 16px;
            border-radius: 40px;
            font-size: 0.85rem;
            font-weight: 500;
            font-family: monospace;
            transition: 0.2s;
            border: 1px solid #30363d;
        }

        .skill-tag i {
            margin-right: 8px;
            font-size: 0.9rem;
        }

        .skill-tag:hover {
            background: #2f81f7;
            color: white;
            border-color: #2f81f7;
            transform: translateY(-2px);
        }

        /* 项目展示网格 */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.4rem;
            margin: 1rem 0 1.2rem;
        }

        .project-card {
            background: #0d1117;
            border-radius: 20px;
            padding: 1.2rem;
            border: 1px solid #30363d;
            transition: all 0.25s;
        }

        .project-card:hover {
            border-color: #2f81f7;
            transform: translateY(-3px);
            box-shadow: 0 12px 20px -12px rgba(0, 0, 0, 0.4);
        }

        .project-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: #58a6ff;
        }

        .project-desc {
            color: #8b949e;
            font-size: 0.85rem;
            line-height: 1.4;
            margin-bottom: 1rem;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 1rem;
        }

        .tech-badge {
            font-size: 0.7rem;
            background: #21262d;
            padding: 2px 8px;
            border-radius: 20px;
            color: #c9d1d9;
        }

        .project-link {
            font-size: 0.8rem;
            text-decoration: none;
            color: #2f81f7;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        .project-link i {
            font-size: 0.7rem;
        }

        /* GitHub 统计数据卡片风格 */
        .github-stats {
            background: #161b22;
            border-radius: 24px;
            padding: 1.2rem 1.5rem;
            margin: 1.8rem 0 1.2rem;
            border: 1px solid #2d333b;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 1rem;
        }

        .stats-text {
            font-family: monospace;
            color: #e6edf3;
        }

        .stats-text strong {
            color: #ff7b72;
        }

        .cta-button {
            background: #238636;
            padding: 8px 20px;
            border-radius: 40px;
            text-decoration: none;
            color: white;
            font-weight: bold;
            font-size: 0.9rem;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .cta-button:hover {
            background: #2ea043;
            transform: scale(1.02);
        }

        /* footer 社交链接 */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 32px;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 1px solid #30363d;
            flex-wrap: wrap;
        }

        .social-icon {
            color: #8b949e;
            font-size: 1.5rem;
            transition: 0.2s;
        }

        .social-icon:hover {
            color: #58a6ff;
            transform: translateY(-3px);
        }

        /* 响应式调整 */
        @media (max-width: 680px) {
            .readme-content {
                padding: 1.5rem;
            }
            .greeting h1 {
                font-size: 1.9rem;
            }
            .stats-mini {
                flex-direction: column;
            }
        }

        /* 装饰小元素 */
        .comment-note {
            text-align: center;
            font-size: 0.7rem;
            color: #484f58;
            margin-top: 1.5rem;
            font-family: monospace;
        }
    </style>
</head>
<body>
<div class="readme-card">
    <div class="readme-content">
        <!-- 模拟 GitHub 个人资料 README 的趣味徽章 -->
        <div class="header-badge">
            <i class="fas fa-code-branch"></i>  GitHub Profile README
        </div>

        <!-- 打招呼区域 🌟 动态波浪效果 -->
        <div class="greeting">
            <h1>
                <span class="wave">👋</span> Hi, I'm <span style="background: linear-gradient(120deg, #79c2ff, #a5d8ff); -webkit-background-clip:text; background-clip:text; color:transparent;">Alex Rivera</span>
            </h1>
            <div class="bio">
                <i class="fas fa-terminal" style="margin-right: 8px; color:#58a6ff;"></i> 
                Full-stack developer & open-source enthusiast · 构建优雅的代码，创造有影响力的产品。
            </div>
        </div>

        <!-- 简易指标 (模拟GitHub动态) -->
        <div class="stats-mini">
            <div class="stat-item">
                <i class="fab fa-github-alt"></i>
                <div class="stat-number">34</div>
                <div class="stat-label">Repositories</div>
            </div>
            <div class="stat-item">
                <i class="fas fa-users"></i>
                <div class="stat-number">1.2k</div>
                <div class="stat-label">Followers</div>
            </div>
            <div class="stat-item">
                <i class="fas fa-star"></i>
                <div class="stat-number">458</div>
                <div class="stat-label">Stars earned</div>
            </div>
            <div class="stat-item">
                <i class="fas fa-code-branch"></i>
                <div class="stat-number">127</div>
                <div class="stat-label">Contributions</div>
            </div>
        </div>

        <!-- 技术栈 (Languages & Tools) -->
        <div class="section-title">
            <i class="fas fa-cogs"></i> Tech Stack & Tools
        </div>
        <div class="skills-cloud">
            <span class="skill-tag"><i class="fab fa-js"></i> JavaScript/TS</span>
            <span class="skill-tag"><i class="fab fa-python"></i> Python</span>
            <span class="skill-tag"><i class="fab fa-react"></i> React</span>
            <span class="skill-tag"><i class="fab fa-node-js"></i> Node.js</span>
            <span class="skill-tag"><i class="fas fa-database"></i> MongoDB/PostgreSQL</span>
            <span class="skill-tag"><i class="fab fa-docker"></i> Docker</span>
            <span class="skill-tag"><i class="fab fa-git-alt"></i> Git/GitHub Actions</span>
            <span class="skill-tag"><i class="fas fa-cloud"></i> AWS/Azure</span>
            <span class="skill-tag"><i class="fab fa-rust"></i> Rust</span>
            <span class="skill-tag"><i class="fab fa-vuejs"></i> Vue.js</span>
        </div>
        
        <!-- 特色项目展示 - 吸引访客 -->
        <div class="section-title">
            <i class="fas fa-rocket"></i> ✨ 精选项目
        </div>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-title">✨ Nexus AI</div>
                <div class="project-desc">下一代对话式AI辅助工具，集成大语言模型与实时协作功能，赋能开发团队。</div>
                <div class="project-tech">
                    <span class="tech-badge">Python</span>
                    <span class="tech-badge">FastAPI</span>
                    <span class="tech-badge">React</span>
                </div>
                <a href="#" class="project-link"><i class="fab fa-github"></i> 仓库地址 <i class="fas fa-arrow-right"></i></a>
            </div>
            <div class="project-card">
                <div class="project-title">📊 DevMetrics</div>
                <div class="project-desc">开发者仪表盘 - 聚合 GitHub 数据，可视化贡献图谱，帮你追踪编程习惯。</div>
                <div class="project-tech">
                    <span class="tech-badge">TypeScript</span>
                    <span class="tech-badge">Next.js</span>
                    <span class="tech-badge">Chart.js</span>
                </div>
                <a href="#" class="project-link"><i class="fab fa-github"></i> 仓库地址 <i class="fas fa-arrow-right"></i></a>
            </div>
            <div class="project-card">
                <div class="project-title">⚡ ViteStart</div>
                <div class="project-desc">现代 Web 应用模版，开箱即用 Vite + Tailwind + React Router，高效原型构建。</div>
                <div class="project-tech">
                    <span class="tech-badge">Vite</span>
                    <span class="tech-badge">TailwindCSS</span>
                    <span class="tech-badge">React</span>
                </div>
                <a href="#" class="project-link"><i class="fab fa-github"></i> 仓库地址 <i class="fas fa-arrow-right"></i></a>
            </div>
        </div>
        
        <!-- GitHub 状态 + 趣味动态信息 -->
        <div class="github-stats">
            <div class="stats-text">
                📈 <strong>GitHub 活跃动态</strong>  ·  最近一周提交了 <strong>12</strong> 次代码  ·  解决了 <strong>5</strong> 个 issues
                <br/>
                🔥 开源贡献者 @awesome-org  ·  🏆 2025 GitHub 北极代码贡献者
            </div>
            <a href="#" class="cta-button"><i class="fab fa-github"></i> 关注我</a>
        </div>

        <!-- 更有趣的扩展: "我日常用" + 访客数动态风格 -->
        <div class="section-title">
            <i class="fas fa-mug-hot"></i> 日常小栈
        </div>
        <div class="skills-cloud" style="margin-bottom: 0.2rem;">
            <span class="skill-tag"><i class="fas fa-terminal"></i> Neovim</span>
            <span class="skill-tag"><i class="fab fa-linux"></i> Arch Linux</span>
            <span class="skill-tag"><i class="fas fa-brain"></i> 机器学习探索</span>
            <span class="skill-tag"><i class="fas fa-palette"></i> UI/UX 设计</span>
            <span class="skill-tag"><i class="fas fa-microphone-alt"></i> 技术演讲</span>
        </div>
        
        <!-- 代码格言 + 趣味引用 (展示个性) -->
        <div style="background: #0a0e14; border-radius: 20px; padding: 1rem; margin: 1.5rem 0 0.8rem; border-left: 4px solid #f78166;">
            <i class="fas fa-quote-left" style="color:#f78166; margin-right: 10px;"></i>
            <span style="color:#c9d1d9; font-family: monospace; font-size: 0.9rem;">
                “代码是写给人看的，只是顺便能让机器运行。” — 编程的艺术
            </span>
        </div>
        
        <!-- 活动 & 流 & 社交链接 -->
        <div class="social-links">
            <a href="#" class="social-icon" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
            <a href="#" class="social-icon" aria-label="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" class="social-icon" aria-label="Dev.to"><i class="fab fa-dev"></i></a>
            <a href="#" class="social-icon" aria-label="个人博客"><i class="fas fa-blog"></i></a>
            <a href="#" class="social-icon" aria-label="Discord"><i class="fab fa-discord"></i></a>
            <a href="#" class="social-icon" aria-label="Stack Overflow"><i class="fab fa-stack-overflow"></i></a>
        </div>
        
        <!-- 最后加一个计数器风格 动态 其实可以加访客，但出于美观-->
        <div class="comment-note">
            <i class="far fa-eye"></i>  ✦ 自述文件动态刷新  ✦  欢迎交流，一起构建未来
            <span style="display: inline-block; margin-left: 8px;">✨</span>
        </div>
        
        <!-- 为了更接近真实的 GitHub README 效果，增加一段隐藏 markdown 注释风格 但是作为html灵感 -->
        <div style="height: 8px;"></div>
    </div>
</div>

<!-- 增加一点交互趣味：控制台输出欢迎语 (纯粹好玩) -->
<script>
    (function() {
        console.log("%c✨ 欢迎来到 Alex Rivera 的 GitHub 主页！ ✨", "color: #2f81f7; font-size: 16px; font-weight: bold;");
        console.log("%c🔧 技术热爱者 | 开源贡献者 | 全栈工程师", "color: #8b949e; font-size: 12px;");
        console.log("📌 记得关注我的仓库，一起探索代码世界！");
    })();
</script>
</body>
</html>
