<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Saksham Gairola | Software Engineer & Designer</title>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #050505;
            --surface-color: #111;
            --text-primary: #f0f0f0;
            --text-secondary: #a0a0a0;
            --accent-glow: #00ffcc;
            --accent-secondary: #7000ff;
            --card-border: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-primary);
            overflow-x: hidden;
        }

        /* --- Background Animation --- */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            background: radial-gradient(circle at 15% 50%, rgba(112, 0, 255, 0.08), transparent 25%),
                        radial-gradient(circle at 85% 30%, rgba(0, 255, 204, 0.08), transparent 25%);
            animation: backgroundShift 20s infinite alternate linear;
        }

        @keyframes backgroundShift {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

        /* --- Layout & Typography --- */
        section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 5rem 10%;
            opacity: 0;
            transform: translateY(40px);
            transition: all 1s ease-out;
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        h2.section-title {
            font-size: 3rem;
            margin-bottom: 3rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            background: linear-gradient(90deg, var(--text-primary), var(--text-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
        }

        h2.section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 50px;
            height: 3px;
            background: var(--accent-glow);
            box-shadow: 0 0 10px var(--accent-glow);
        }

        /* --- Hero Section --- */
        .hero {
            text-align: center;
            opacity: 1; /* Hero is visible immediately */
            transform: translateY(0);
        }

        .hero h1 {
            font-size: 5vw;
            font-weight: 800;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--accent-glow), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(0, 255, 204, 0.2);
        }

        .typewriter-container {
            font-size: 2rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
            height: 45px;
        }

        .cursor {
            display: inline-block;
            width: 4px;
            background-color: var(--accent-glow);
            animation: blink 0.8s infinite;
        }

        .hero p {
            max-width: 600px;
            font-size: 1.2rem;
            line-height: 1.6;
            margin: 0 auto 3rem auto;
            color: var(--text-secondary);
        }

        .btn-group {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
        }

        .btn {
            padding: 15px 35px;
            font-size: 1.1rem;
            font-weight: bold;
            text-decoration: none;
            border-radius: 30px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: transparent;
            color: var(--accent-glow);
            border: 2px solid var(--accent-glow);
            box-shadow: 0 0 15px rgba(0, 255, 204, 0.2);
        }

        .btn-primary:hover {
            background: var(--accent-glow);
            color: var(--bg-color);
            box-shadow: 0 0 30px rgba(0, 255, 204, 0.6);
        }

        .btn-secondary {
            background: var(--surface-color);
            color: var(--text-primary);
            border: 2px solid var(--card-border);
        }

        .btn-secondary:hover {
            border-color: var(--accent-secondary);
            box-shadow: 0 0 20px rgba(112, 0, 255, 0.4);
        }

        /* --- Skills Grid --- */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            width: 100%;
            max-width: 1200px;
        }

        .skill-card {
            background: var(--surface-color);
            border: 1px solid var(--card-border);
            padding: 2.5rem;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.4s ease, box-shadow 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.05), transparent);
            transition: left 0.5s ease;
        }

        .skill-card:hover::before {
            left: 100%;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent-glow);
            box-shadow: 0 10px 30px rgba(0, 255, 204, 0.15);
        }

        .skill-card i {
            font-size: 3rem;
            color: var(--accent-glow);
            margin-bottom: 1.5rem;
        }

        .skill-card h3 {
            font-size: 1.4rem;
            margin-bottom: 1rem;
        }

        .skill-card p {
            color: var(--text-secondary);
            font-size: 0.95rem;
            line-height: 1.5;
        }

        /* --- Projects Section --- */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
            width: 100%;
            max-width: 1200px;
        }

        .project-card {
            background: var(--surface-color);
            border-radius: 15px;
            overflow: hidden;
            border: 1px solid var(--card-border);
            transition: all 0.3s ease;
        }

        .project-card:hover {
            transform: scale(1.02);
            border-color: var(--accent-secondary);
            box-shadow: 0 0 25px rgba(112, 0, 255, 0.2);
        }

        .project-img {
            width: 100%;
            height: 200px;
            background: #222; /* Placeholder for images */
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: #333;
        }

        .project-info {
            padding: 2rem;
        }

        .project-info h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .project-info p {
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .tag-container {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .tag {
            font-size: 0.8rem;
            padding: 5px 12px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            color: var(--accent-glow);
        }

        /* --- Animations --- */
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        /* --- Floating Elements --- */
        .mouse-icon {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 50px;
            border: 2px solid var(--text-secondary);
            border-radius: 15px;
            display: flex;
            justify-content: center;
            padding-top: 10px;
        }

        .mouse-wheel {
            width: 4px;
            height: 8px;
            background: var(--accent-glow);
            border-radius: 2px;
            animation: scroll 1.5s infinite;
        }

        @keyframes scroll {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(15px); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="bg-animation"></div>

    <!-- HERO SECTION -->
    <section class="hero" id="home">
        <h1>Saksham Gairola</h1>
        <div class="typewriter-container">
            I am a <span id="typewriter"></span><span class="cursor">&nbsp;</span>
        </div>
        <p>
            An engineer and creative bridging the gap between high-performance code, striking UI/UX, and data-driven marketing. Specializing in scaling e-commerce platforms and integrating advanced AI workflows.
        </p>
        <div class="btn-group">
            <a href="https://saksham.webzineworld.in/" class="btn btn-primary" target="_blank">View Full Portfolio</a>
            <a href="#skills" class="btn btn-secondary">Explore Skills</a>
        </div>
        
        <div class="mouse-icon">
            <div class="mouse-wheel"></div>
        </div>
    </section>

    <!-- SKILLS SECTION -->
    <section id="skills">
        <h2 class="section-title">Core Architecture</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <i class="fab fa-hubspot"></i>
                <h3>CMS Development</h3>
                <p>Architecting custom themes, modules, and landing pages across HubSpot CMS, WordPress, Divi, and Elementor ecosystems.</p>
            </div>
            <div class="skill-card">
                <i class="fa-solid fa-code"></i>
                <h3>Web Engineering</h3>
                <p>Developing responsive, lightning-fast interfaces using modern HTML, CSS, JavaScript, and dynamic framework integrations.</p>
            </div>
            <div class="skill-card">
                <i class="fa-solid fa-chart-line"></i>
                <h3>E-Commerce & Marketing</h3>
                <p>Scaling brands, managing product sales funnels, executing digital marketing campaigns, and deploying affiliate strategies.</p>
            </div>
            <div class="skill-card">
                <i class="fa-solid fa-robot"></i>
                <h3>AI & Automation</h3>
                <p>Leveraging the latest AI tools to streamline design iterations, automate content generation, and optimize technical workflows.</p>
            </div>
        </div>
    </section>

    <!-- PROJECTS SECTION -->
    <section id="projects">
        <h2 class="section-title">Digital Ventures</h2>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-img">
                    <i class="fa-solid fa-cart-shopping"></i>
                </div>
                <div class="project-info">
                    <h3>WebzineWorld Ecosystem</h3>
                    <p>Designed and developed the structural framework and corporate identity for an end-to-end e-commerce product selling platform.</p>
                    <div class="tag-container">
                        <span class="tag">E-Commerce</span>
                        <span class="tag">UI/UX</span>
                        <span class="tag">Marketing</span>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-img">
                    <i class="fa-solid fa-server"></i>
                </div>
                <div class="project-info">
                    <h3>HubSpot Custom Infrastructure</h3>
                    <p>Built out a technical custom website theme, resolving compiler errors and assembling intricate design manager files and page templates.</p>
                    <div class="tag-container">
                        <span class="tag">HubSpot CMS</span>
                        <span class="tag">Development</span>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-img">
                    <i class="fa-solid fa-video"></i>
                </div>
                <div class="project-info">
                    <h3>Digital Media Branding</h3>
                    <p>Generated multi-platform promotional assets, custom banner designs, and algorithmic SEO tags for behavioral psychology and narrative channels.</p>
                    <div class="tag-container">
                        <span class="tag">Graphic Design</span>
                        <span class="tag">Content Strategy</span>
                        <span class="tag">AI Tools</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- JS FOR ANIMATIONS -->
    <script>
        // --- Typewriter Effect ---
        const roles = [
            "Software Engineer.",
            "Web Developer.",
            "E-Commerce Strategist.",
            "UI/UX Designer.",
            "Digital Marketer."
        ];
        
        let roleIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typewriterElement = document.getElementById("typewriter");

        function type() {
            const currentRole = roles[roleIndex];
            
            if (isDeleting) {
                typewriterElement.textContent = currentRole.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typewriterElement.textContent = currentRole.substring(0, charIndex + 1);
                charIndex++;
            }

            let typeSpeed = isDeleting ? 40 : 80;

            if (!isDeleting && charIndex === currentRole.length) {
                typeSpeed = 2000; 
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                roleIndex = (roleIndex + 1) % roles.length;
                typeSpeed = 400; 
            }
            setTimeout(type, typeSpeed);
        }

        window.onload = () => {
            type();
            // Trigger observer on load for elements already in view
            document.querySelectorAll('section').forEach(sec => observer.observe(sec));
        };

        // --- Scroll Reveal Animation ---
        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.2
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);
    </script>
</body>
</html>
