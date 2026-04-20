<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Adarsh Verma · Electronics Engineer | Embedded Systems & IoT</title>
    <!-- Google Fonts & Font Awesome -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=Space+Grotesk:wght@400;500;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Anime.js for lightweight 3D motion (optional) -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: radial-gradient(circle at 20% 30%, #0a0f1e, #03060c);
            font-family: 'Inter', 'Space Grotesk', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 2rem 1.5rem;
        }

        /* main glassmorphic card with 3D transform & subtle rotation */
        .readme-card {
            max-width: 1100px;
            width: 100%;
            background: rgba(12, 20, 30, 0.65);
            backdrop-filter: blur(14px);
            border-radius: 3rem;
            border: 1px solid rgba(0, 247, 255, 0.25);
            box-shadow: 0 30px 50px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(0, 247, 255, 0.1) inset, 0 0 20px rgba(0, 247, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            transform-style: preserve-3d;
            perspective: 1200px;
            overflow: hidden;
        }

        .readme-card:hover {
            transform: translateY(-8px) rotateX(1deg) rotateY(0.5deg);
            box-shadow: 0 40px 60px rgba(0, 0, 0, 0.6), 0 0 0 2px rgba(0, 247, 255, 0.3) inset;
        }

        /* inner content with slight 3d depth */
        .card-inner {
            padding: 2.2rem 2rem;
            background: radial-gradient(ellipse at top left, rgba(20, 40, 55, 0.3), rgba(2, 8, 18, 0.6));
            border-radius: 3rem;
        }

        /* typing header SVG style replacement */
        .typing-header {
            text-align: center;
            margin-bottom: 2rem;
        }
        .glow-text {
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(135deg, #a5f0ff, #2ad4e3, #0aa0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 2px 5px rgba(0,255,255,0.2);
            letter-spacing: -0.5px;
        }
        .subhead {
            color: #bbf0ff;
            font-weight: 500;
            letter-spacing: 0.3px;
            border-bottom: 1px dashed #2ad4e3;
            display: inline-block;
            padding-bottom: 6px;
        }

        /* Profile badge row */
        .profile-badge {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            background: rgba(0, 20, 30, 0.5);
            border-radius: 2rem;
            padding: 0.8rem 1.5rem;
            backdrop-filter: blur(4px);
            border: 1px solid rgba(0,247,255,0.2);
        }
        .contact-info i {
            margin-right: 8px;
            color: #2ad4e3;
        }
        .contact-info span, .location {
            font-size: 0.9rem;
            font-weight: 500;
            color: #caf0ff;
        }
        .view-counter {
            background: #0a1424;
            padding: 6px 14px;
            border-radius: 40px;
            font-size: 0.85rem;
            font-weight: 600;
            color: #00e0ff;
            box-shadow: 0 0 6px cyan;
        }

        /* section styles */
        .section {
            margin: 2.2rem 0;
        }
        .section-title {
            font-size: 1.7rem;
            font-weight: 700;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 12px;
            border-left: 5px solid #0ff;
            padding-left: 1rem;
            color: #eef5ff;
            letter-spacing: -0.3px;
            text-shadow: 0 0 3px rgba(0,255,255,0.4);
        }
        .section-title i {
            font-size: 1.6rem;
            color: #0ff;
        }

        .about-text, .edu-desc {
            background: rgba(0, 0, 0, 0.35);
            padding: 1.2rem 1.5rem;
            border-radius: 1.5rem;
            border: 1px solid rgba(0, 247, 255, 0.2);
            backdrop-filter: blur(2px);
            color: #e2edf7;
            line-height: 1.5;
            font-weight: 400;
            transition: all 0.2s;
        }

        /* 3D tech stack grid with icons & hover depth */
        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 1rem;
            justify-content: center;
        }
        .tech-item {
            background: rgba(16, 32, 48, 0.7);
            backdrop-filter: blur(8px);
            padding: 0.7rem 1.3rem;
            border-radius: 2rem;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            font-size: 1rem;
            border: 1px solid rgba(0, 247, 255, 0.4);
            color: #ddf4ff;
            transition: all 0.25s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            transform: translateZ(0);
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
        }
        .tech-item i, .tech-item img {
            font-size: 1.4rem;
            width: 28px;
            text-align: center;
        }
        .tech-item:hover {
            transform: translateY(-6px) scale(1.05) rotateZ(0.5deg);
            background: #0a2a3ae0;
            border-color: #0ff;
            box-shadow: 0 15px 20px -8px rgba(0,200,255,0.3);
        }

        /* skills grid (similar list style with 3d badges) */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 12px;
        }
        .skill-badge {
            background: linear-gradient(145deg, #10222e, #07121c);
            padding: 8px 20px;
            border-radius: 40px;
            font-weight: 500;
            font-size: 0.85rem;
            color: #b3f0ff;
            border: 1px solid #2ad4e360;
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
            transition: 0.2s;
        }
        .skill-badge:hover {
            transform: translateY(-3px);
            background: #0c3e52;
            border-color: cyan;
            box-shadow: 0 8px 14px rgba(0,200,255,0.2);
        }

        /* Education row style */
        .edu-card {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: baseline;
            background: rgba(0, 0, 0, 0.4);
            padding: 1.2rem 1.5rem;
            border-radius: 1.8rem;
            border-left: 4px solid cyan;
        }
        .edu-degree {
            font-weight: 800;
            font-size: 1.2rem;
            color: #eef5ff;
        }
        .edu-date {
            color: #2ad4e3;
            font-weight: 500;
        }
        .course-list {
            margin-top: 12px;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }
        .course-chip {
            background: #02141f;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 500;
            color: #9eeaff;
        }

        /* Stats / contribution style minimal but crisp */
        .stats-row {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin: 2rem 0 1rem;
        }
        .stat-card {
            background: rgba(2, 15, 25, 0.7);
            border-radius: 1.5rem;
            padding: 1rem 1.8rem;
            text-align: center;
            backdrop-filter: blur(8px);
            border: 1px solid cyan;
            flex: 1;
            min-width: 160px;
            transition: 0.2s;
        }
        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            color: #0ff;
        }
        .snake-animation {
            background: #010a12;
            border-radius: 1.8rem;
            margin: 1.5rem 0;
            padding: 0.5rem;
            text-align: center;
        }

        .connect-icons {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 1.5rem 0 0.5rem;
        }
        .social-link {
            background: #071a24;
            padding: 10px 20px;
            border-radius: 40px;
            transition: all 0.25s;
            font-size: 1.1rem;
            font-weight: 500;
            color: white;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 12px;
            border: 1px solid #2ad4e380;
        }
        .social-link:hover {
            transform: translateY(-5px);
            background: #0e3a4b;
            border-color: cyan;
            box-shadow: 0 10px 18px rgba(0,0,0,0.4);
        }
        footer {
            text-align: center;
            margin-top: 2rem;
            font-size: 0.75rem;
            color: #6e9eb0;
        }
        hr {
            border-color: #2ad4e320;
            margin: 1rem 0;
        }
        @media (max-width: 680px) {
            .card-inner { padding: 1.5rem; }
            .glow-text { font-size: 1.5rem; }
            .section-title { font-size: 1.4rem; }
        }
        .fake-svg {
            background: #03141e;
            border-radius: 20px;
            padding: 8px;
            text-align: center;
            font-family: monospace;
        }
    </style>
</head>
<body>

<div class="readme-card">
    <div class="card-inner">
        
        <!-- Animated Header (Typing effect simulation) -->
        <div class="typing-header">
            <h1 class="glow-text">
                <i class="fas fa-microchip"></i> Adarsh Verma · Electronics Frontier
            </h1>
            <div style="margin-top: 8px;">
                <span class="subhead">⚡ B.Tech (ECE) @ Gautam Buddha University | Embedded Systems & IoT | Circuit Design</span>
            </div>
        </div>

        <!-- Profile row: location + contact + view counter (3D style) -->
        <div class="profile-badge">
            <div class="contact-info">
                <i class="fas fa-map-marker-alt"></i> <span>Delhi, India</span>&nbsp;&nbsp;|&nbsp;
                <i class="fas fa-envelope"></i> <span>adarsh.verma@example.com</span>&nbsp;&nbsp;
                <i class="fab fa-linkedin"></i> <span>/in/adarsh-verma</span>
            </div>
            <div class="view-counter">
                <i class="fas fa-eye"></i> Profile views: <span id="viewCount">1.2k</span> 
            </div>
        </div>

        <!-- About Section with student details from image -->
        <div class="section">
            <div class="section-title">
                <i class="fas fa-user-astronaut"></i> 
                <span>About Me</span>
            </div>
            <div class="about-text">
                I am a motivated B.Tech student in Electronics and Communication Engineering at Gautam Buddha University with a strong interest in embedded systems, circuit design, and emerging communication technologies. <br/><br/>
                I have worked on projects such as <strong>“Dual Display Smart Health Monitoring System with Alert Mechanism,”</strong> where I was involved in sensor integration, microcontroller interfacing, and real-time alert system implementation. This project strengthened my understanding of hardware-software integration and system optimization.<br/><br/>
                I am continuously enhancing my technical skills in embedded systems, IoT, and programming. I am seeking opportunities in internships, research, and technical collaborations where I can contribute, learn, and grow as a future electronics engineer.
            </div>
        </div>

        <!-- Education Section (details from image) -->
        <div class="section">
            <div class="section-title">
                <i class="fas fa-graduation-cap"></i>
                <span>Education</span>
            </div>
            <div class="edu-card">
                <div>
                    <div class="edu-degree"><i class="fas fa-university"></i> Gautam Buddha University</div>
                    <div>Bachelor of Technology - BTech, Electronics & Communication Engineering (ECE)</div>
                    <div class="course-list">
                        <span class="course-chip">Python</span>
                        <span class="course-chip">C Programming</span>
                        <span class="course-chip">Embedded Systems</span>
                        <span class="course-chip">Analog Electronics</span>
                        <span class="course-chip">Signal & Systems</span>
                        <span class="course-chip">IoT Basics</span>
                        <span class="course-chip">HTML</span>
                    </div>
                </div>
                <div class="edu-date">2025 – Present</div>
            </div>
        </div>

        <!-- Tech Stack: CANVA, PYTHON, C, HTML, VS CODE + additional icons as required -->
        <div class="section">
            <div class="section-title">
                <i class="fas fa-code"></i>
                <span>Tech Stack & Tools</span>
            </div>
            <div class="tech-stack">
                <div class="tech-item"><i class="fab fa-python"></i> Python</div>
                <div class="tech-item"><i class="fas fa-code"></i> C</div>
                <div class="tech-item"><i class="fab fa-html5"></i> HTML5</div>
                <div class="tech-item"><i class="fas fa-paintbrush"></i> Canva</div>
                <div class="tech-item"><i class="fas fa-laptop-code"></i> VS Code</div>
                <div class="tech-item"><i class="fas fa-microchip"></i> Embedded C</div>
                <div class="tech-item"><i class="fas fa-chart-line"></i> IoT Frameworks</div>
            </div>
        </div>

        <!-- Skills Section: from given details (Python, C, HTML, Embedded Systems, Analog Electronics etc) -->
        <div class="section">
            <div class="section-title">
                <i class="fas fa-cogs"></i>
                <span>Core Competencies</span>
            </div>
            <div class="skills-grid">
                <span class="skill-badge">Embedded Systems</span>
                <span class="skill-badge">Analog Electronics</span>
                <span class="skill-badge">Signal & Systems</span>
                <span class="skill-badge">IoT Basics</span>
                <span class="skill-badge">C Programming</span>
                <span class="skill-badge">Python</span>
                <span class="skill-badge">HTML & CSS</span>
                <span class="skill-badge">Microcontroller Interfacing</span>
                <span class="skill-badge">Circuit Design</span>
                <span class="skill-badge">Real-time Alert Systems</span>
            </div>
        </div>

        <!-- GitHub-like stats with 3D cards (simulated metrics) -->
        <div class="stats-row">
            <div class="stat-card">
                <div class="stat-number"><i class="fas fa-project-diagram"></i> 6+</div>
                <div>Hardware Projects</div>
                <small style="color:#7fcdff;">Embedded & IoT</small>
            </div>
            <div class="stat-card">
                <div class="stat-number"><i class="fas fa-code-branch"></i> 12+</div>
                <div>Repositories</div>
                <small style="color:#7fcdff;">C, Python, IoT</small>
            </div>
            <div class="stat-card">
                <div class="stat-number"><i class="fas fa-trophy"></i> 2</div>
                <div>Project Showcase</div>
                <small style="color:#7fcdff;">Health Monitoring</small>
            </div>
        </div>

        <!-- Snake Animation / Fun Zone (SVG snake eating contributions) -->
        <div class="snake-animation">
            <div style="display: flex; justify-content: space-between; align-items: center; padding: 0 12px;">
                <span style="color:#0ff;"><i class="fas fa-gamepad"></i> 🐍 GitHub contributions snake</span>
                <span style="font-size: 12px; color:#4aa3c2;">commits & activity</span>
            </div>
            <!-- Custom snake animation placeholder using inline SVG with moving effect (animated via CSS/JS) -->
            <div style="margin-top: 10px; background: #02101a; border-radius: 32px; padding: 8px; text-align: center;">
                <svg width="100%" height="80" viewBox="0 0 800 80" xmlns="http://www.w3.org/2000/svg" style="display: block; margin: 0 auto;">
                    <rect width="800" height="80" fill="#05161f" rx="20" ry="20" />
                    <g>
                        <circle cx="40" cy="40" r="8" fill="#0f0" stroke="#0ff" stroke-width="1.5">
                            <animate attributeName="cx" values="40;760;40" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="60" cy="40" r="8" fill="#0fa" stroke="#0ff">
                            <animate attributeName="cx" values="60;740;60" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="80" cy="40" r="8" fill="#0fa" stroke="#0ff">
                            <animate attributeName="cx" values="80;720;80" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <!-- Snake body segments -->
                        <circle cx="100" cy="40" r="7" fill="#1f9">
                            <animate attributeName="cx" values="100;700;100" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="120" cy="40" r="7" fill="#2aa">
                            <animate attributeName="cx" values="120;680;120" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="140" cy="40" r="7" fill="#3cb">
                            <animate attributeName="cx" values="140;660;140" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="160" cy="40" r="7" fill="#4ec">
                            <animate attributeName="cx" values="160;640;160" dur="6s" repeatCount="indefinite" />
                        </circle>
                        <!-- Food dots -->
                        <circle cx="300" cy="40" r="5" fill="#ff4d4d">
                            <animate attributeName="cx" values="300;500;300" dur="4s" repeatCount="indefinite" />
                        </circle>
                        <circle cx="600" cy="40" r="5" fill="#ffaa33">
                            <animate attributeName="cx" values="600;200;600" dur="5s" repeatCount="indefinite" />
                        </circle>
                    </g>
                    <text x="400" y="70" fill="#aaf0ff" font-size="10" text-anchor="middle" font-family="monospace">🐍 snake eating commits → interactive fun zone</text>
                </svg>
            </div>
        </div>

        <!-- Connect with Me (socials and email) -->
        <div class="connect-icons">
            <a href="#" class="social-link"><i class="fab fa-github"></i> github/adarsh-verma</a>
            <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
            <a href="#" class="social-link"><i class="fas fa-envelope"></i> adarsh.verma@ieee.org</a>
        </div>
        
        <!-- Additional footer & quote with 3d border -->
        <hr />
        <div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap; margin: 0.8rem 0;">
            <span style="background:#051e2c; padding: 5px 12px; border-radius: 30px;"><i class="fas fa-microchip"></i> Embedded Systems Enthusiast</span>
            <span style="background:#051e2c; padding: 5px 12px; border-radius: 30px;"><i class="fas fa-waveform"></i> Signal Processing</span>
            <span style="background:#051e2c; padding: 5px 12px; border-radius: 30px;"><i class="fas fa-plug"></i> IoT & Circuit Design</span>
        </div>
        <footer>
            ⚡ “Bridging hardware and software for smarter solutions” — Adarsh Verma<br/>
            📍 Delhi, India | Open for internships & research collaborations 🚀
        </footer>
        <div style="text-align: center; margin-top: 12px; font-size: 12px;">
            <i class="fas fa-crown"></i> from <strong>@adarshverma_ece</strong> · 3D interactive profile
        </div>
    </div>
</div>

<script>
    // simple animation for view counter, plus optional glitch
    (function(){
        // dynamic view count updater (just for fun)
        let count = 1247;
        const viewSpan = document.getElementById('viewCount');
        if(viewSpan){
            setInterval(() => {
                let increment = Math.floor(Math.random() * 3) + 1;
                count += increment;
                if(count > 2100) count = 1250;
                viewSpan.innerText = count.toLocaleString();
            }, 8000);
        }

        // additional 3D tilt effect on card using mousemove (optional)
        const card = document.querySelector('.readme-card');
        if(card){
            document.body.addEventListener('mousemove', (e) => {
                let xAxis = (window.innerWidth / 2 - e.pageX) / 35;
                let yAxis = (window.innerHeight / 2 - e.pageY) / 35;
                if(Math.abs(xAxis) < 8 && Math.abs(yAxis) < 8){
                    card.style.transform = `perspective(1000px) rotateY(${xAxis * 0.5}deg) rotateX(${yAxis * -0.3}deg) translateY(-5px)`;
                } else {
                    card.style.transform = `perspective(1000px) rotateY(${xAxis * 0.7}deg) rotateX(${yAxis * -0.5}deg) translateY(-4px)`;
                }
            });
            document.body.addEventListener('mouseleave', () => {
                card.style.transform = 'perspective(1200px) rotateX(0deg) rotateY(0deg) translateY(0px)';
            });
        }
    })();
</script>
</body>
</html>
