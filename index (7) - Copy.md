<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio - Software Engineer & Data Analyst</title>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #00ff88;
            --secondary: #ff0080;
            --darker: #050816;
            --text: #e0e6ff;
            --text-dim: #8892b0;
            --accent: #64ffda;
        }
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'JetBrains Mono', monospace;
            background: var(--darker);
            color: var(--text);
            overflow-x: hidden;
            line-height: 1.6;
        }
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(100, 255, 218, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(100, 255, 218, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: gridMove 20s linear infinite;
            pointer-events: none;
            z-index: 0;
        }
        @keyframes gridMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.3;
            pointer-events: none;
            z-index: 0;
            animation: float 20s ease-in-out infinite;
        }
        .orb-1 {
            width: 500px;
            height: 500px;
            background: var(--primary);
            top: -200px;
            left: -200px;
        }
        .orb-2 {
            width: 400px;
            height: 400px;
            background: var(--secondary);
            bottom: -150px;
            right: -150px;
            animation-delay: -10s;
        }
        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            33% { transform: translate(100px, -100px) scale(1.1); }
            66% { transform: translate(-50px, 100px) scale(0.9); }
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            position: relative;
            z-index: 1;
        }
        header {
            padding: 2rem 0;
            position: sticky;
            top: 0;
            background: rgba(10, 14, 39, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(100, 255, 218, 0.1);
            z-index: 100;
            animation: slideDown 0.8s ease-out;
        }
        @keyframes slideDown {
            from { transform: translateY(-100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .logo {
            font-family: 'Syne', sans-serif;
            font-size: 1.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }
        nav a {
            color: var(--text-dim);
            text-decoration: none;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            position: relative;
        }
        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }
        nav a:hover {
            color: var(--primary);
        }
        nav a:hover::after {
            width: 100%;
        }
        .lang-toggle {
            background: rgba(0, 255, 136, 0.1);
            border: 1px solid rgba(0, 255, 136, 0.2);
            border-radius: 6px;
            padding: 0.5rem 1rem;
            color: var(--primary);
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            font-family: 'JetBrains Mono', monospace;
        }
        .lang-toggle:hover {
            background: rgba(0, 255, 136, 0.2);
            border-color: var(--primary);
        }
        .menu-toggle {
            display: none;
            background: none;
            border: none;
            color: var(--primary);
            font-size: 1.5rem;
            cursor: pointer;
            padding: 0.5rem;
        }
        .menu-toggle:hover {
            color: var(--accent);
        }
        .hero {
            min-height: 90vh;
            display: flex;
            align-items: center;
            padding: 4rem 0;
        }
        .hero-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            width: 100%;
        }
        .hero-content {
            animation: fadeInUp 1s ease-out 0.2s both;
        }
        .hero-image {
            animation: fadeInUp 1s ease-out 0.4s both;
            display: flex;
            justify-content: center;
        }
        .profile-picture {
            position: relative;
            width: 400px;
            height: 400px;
        }
        .profile-picture::before {
            content: '';
            position: absolute;
            top: -20px;
            left: -20px;
            right: 20px;
            bottom: 20px;
            border: 3px solid var(--primary);
            border-radius: 12px;
            z-index: -1;
        }
        .profile-picture img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 12px;
            filter: grayscale(10%);
            transition: all 0.3s ease;
        }
        .profile-picture img:hover {
            filter: grayscale(0%);
            transform: translate(-10px, -10px);
        }
        .profile-picture::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary), transparent);
            opacity: 0.2;
            border-radius: 12px;
            pointer-events: none;
            transition: opacity 0.3s ease;
        }
        .profile-picture:hover::after {
            opacity: 0;
        }
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .hero-tag {
            color: var(--primary);
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }
        .hero h1 {
            font-family: 'Syne', sans-serif;
            font-size: clamp(2.5rem, 8vw, 5rem);
            font-weight: 800;
            line-height: 1.1;
            margin-bottom: 1.5rem;
        }
        .gradient-text {
            background: linear-gradient(135deg, var(--primary), var(--accent), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero p {
            font-size: 1.2rem;
            color: var(--text-dim);
            max-width: 600px;
            margin-bottom: 2.5rem;
        }
        .cta-buttons {
            display: flex;
            gap: 1.5rem;
            flex-wrap: wrap;
        }
        .btn {
            padding: 1rem 2rem;
            border: none;
            border-radius: 8px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }
        .btn-primary {
            background: var(--primary);
            color: var(--darker);
            box-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 30px rgba(0, 255, 136, 0.5);
        }
        .btn-secondary {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }
        .btn-secondary:hover {
            background: rgba(0, 255, 136, 0.1);
            transform: translateY(-2px);
        }
        section {
            padding: 6rem 0;
        }
        .section-title {
            font-family: 'Syne', sans-serif;
            font-size: clamp(2rem, 5vw, 3rem);
            font-weight: 700;
            margin-bottom: 3rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        .section-title::before {
            content: '';
            width: 60px;
            height: 3px;
            background: var(--primary);
        }
        .section-number {
            color: var(--primary);
            font-size: 1.2rem;
            margin-right: 0.5rem;
        }
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }
        .skill-card {
            background: rgba(100, 255, 218, 0.03);
            border: 1px solid rgba(100, 255, 218, 0.1);
            border-radius: 12px;
            padding: 2rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .skill-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
        }
        .skill-card:hover::before {
            opacity: 0.05;
        }
        .skill-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--primary);
            position: relative;
        }
        .skill-card p {
            color: var(--text-dim);
            margin-bottom: 1rem;
            position: relative;
        }
        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            position: relative;
        }
        .tag {
            background: rgba(0, 255, 136, 0.1);
            color: var(--primary);
            padding: 0.3rem 0.8rem;
            border-radius: 4px;
            font-size: 0.8rem;
            border: 1px solid rgba(0, 255, 136, 0.2);
        }
        .projects-grid {
            display: grid;
            gap: 2rem;
        }
        .project-card {
            background: rgba(100, 255, 218, 0.03);
            border: 1px solid rgba(100, 255, 218, 0.1);
            border-radius: 12px;
            padding: 2.5rem;
            transition: all 0.3s ease;
        }
        .project-card:hover {
            border-color: var(--primary);
            transform: translateX(5px);
        }
        .project-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 1rem;
        }
        .project-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.8rem;
            color: var(--text);
            margin-bottom: 0.5rem;
        }
        .project-links {
            display: flex;
            gap: 1rem;
        }
        .project-link {
            color: var(--primary);
            text-decoration: none;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }
        .project-link:hover {
            color: var(--accent);
        }
        .project-card p {
            color: var(--text-dim);
            line-height: 1.8;
            margin-bottom: 1.5rem;
        }
        .experience-timeline {
            display: grid;
            gap: 2rem;
            position: relative;
        }
        .experience-timeline::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(180deg, var(--primary), transparent);
        }
        .experience-card {
            background: rgba(100, 255, 218, 0.03);
            border: 1px solid rgba(100, 255, 218, 0.1);
            border-radius: 12px;
            padding: 2.5rem;
            margin-left: 3rem;
            transition: all 0.3s ease;
            position: relative;
        }
        .experience-card::before {
            content: '';
            position: absolute;
            left: -3rem;
            top: 2.5rem;
            width: 12px;
            height: 12px;
            background: var(--primary);
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(0, 255, 136, 0.5);
        }
        .experience-card:hover {
            border-color: var(--primary);
            transform: translateX(10px);
        }
        .experience-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
            gap: 1rem;
        }
        .experience-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.6rem;
            color: var(--text);
            margin-bottom: 0.5rem;
        }
        .company-name {
            color: var(--primary);
            font-size: 1.1rem;
            font-weight: 600;
        }
        .experience-date {
            color: var(--text-dim);
            font-size: 0.9rem;
            background: rgba(0, 255, 136, 0.1);
            padding: 0.5rem 1rem;
            border-radius: 6px;
            border: 1px solid rgba(0, 255, 136, 0.2);
        }
        .experience-list {
            list-style: none;
            margin-bottom: 1.5rem;
        }
        .experience-list li {
            color: var(--text-dim);
            line-height: 1.8;
            margin-bottom: 0.8rem;
            padding-left: 1.5rem;
            position: relative;
        }
        .experience-list li::before {
            content: '▹';
            color: var(--primary);
            position: absolute;
            left: 0;
            font-size: 1.2rem;
        }
        .contact-content {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }
        .contact-content h2 {
            font-family: 'Syne', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
        }
        .contact-content p {
            color: var(--text-dim);
            margin-bottom: 2rem;
            font-size: 1.1rem;
        }
        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 3rem;
        }
        .social-link {
            color: var(--text-dim);
            font-size: 1.5rem;
            transition: all 0.3s ease;
            text-decoration: none;
        }
        .social-link:hover {
            color: var(--primary);
            transform: translateY(-3px);
        }
        footer {
            text-align: center;
            padding: 3rem 0;
            border-top: 1px solid rgba(100, 255, 218, 0.1);
            color: var(--text-dim);
        }
        @media (max-width: 768px) {
            .container {
                padding: 0 1.5rem;
            }
            header {
                padding: 1.5rem 0;
            }
            .logo {
                font-size: 1.1rem;
            }
            .menu-toggle {
                display: block;
            }
            nav ul {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                max-width: 300px;
                height: 100vh;
                background: rgba(10, 14, 39, 0.98);
                backdrop-filter: blur(10px);
                flex-direction: column;
                justify-content: center;
                gap: 2rem;
                padding: 2rem;
                transition: right 0.3s ease;
                border-left: 1px solid rgba(100, 255, 218, 0.1);
                z-index: 1000;
            }
            nav ul.active {
                right: 0;
            }
            nav ul li {
                width: 100%;
                text-align: center;
            }
            nav a {
                font-size: 1.1rem;
                display: block;
                padding: 0.5rem;
            }
            .lang-toggle {
                width: 100%;
            }
            .hero-wrapper {
                grid-template-columns: 1fr;
                gap: 3rem;
            }
            .hero-image {
                order: -1;
            }
            .profile-picture {
                width: 280px;
                height: 280px;
            }
            .cta-buttons {
                flex-direction: column;
            }
            .skills-grid {
                grid-template-columns: 1fr;
            }
            .experience-timeline::before {
                left: 0;
            }
            .experience-card {
                margin-left: 2rem;
                padding: 1.5rem;
            }
            .experience-card::before {
                left: -2rem;
            }
        }
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease-out;
        }
        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>

    <header>
        <div class="container">
            <nav>
                <div class="logo">{"< ESPOIR DOUTI />"}</div>
                <button class="menu-toggle" onclick="toggleMenu()" aria-label="Toggle menu">
                    <span>☰</span>
                </button>
                <ul id="nav-menu">
                    <li><a href="#about" class="lang-text" data-en="About" data-fr="À propos" onclick="closeMenu()">About</a></li>
                    <li><a href="#skills" class="lang-text" data-en="Skills" data-fr="Compétences" onclick="closeMenu()">Skills</a></li>
                    <li><a href="#projects" class="lang-text" data-en="Projects" data-fr="Projets" onclick="closeMenu()">Projects</a></li>
                    <li><a href="#experience" class="lang-text" data-en="Experience" data-fr="Expérience" onclick="closeMenu()">Experience</a></li>
                    <li><a href="#contact" class="lang-text" data-en="Contact" data-fr="Contact" onclick="closeMenu()">Contact</a></li>
                    <li><button class="lang-toggle" onclick="toggleLanguage()">FR</button></li>
                </ul>
            </nav>
        </div>
    </header>

    <main class="container">
        <section class="hero">
            <div class="hero-wrapper">
                <div class="hero-content">
                    <div class="hero-tag lang-text" data-en="// Software Engineer & Data Analyst" data-fr="// Ingénieur Logiciel & Analyste de Données">// Software Engineer & Data Analyst</div>
                    <h1>
                        <span class="lang-text" data-en="Building the future with" data-fr="Construire l'avenir avec">Building the future with</span><br>
                        <span class="gradient-text lang-text" data-en="Code & Data" data-fr="Code & Données">Code & Data</span>
                    </h1>
                    <p class="lang-text" data-en="Transforming complex data into actionable insights and crafting intelligent solutions powered by AI. Passionate about turning ideas into reality through clean code and innovative thinking." data-fr="Transformer des données complexes en informations exploitables et créer des solutions intelligentes alimentées par l'IA. Passionné par la transformation d'idées en réalité grâce à un code propre et une pensée innovante.">
                        Transforming complex data into actionable insights and crafting intelligent 
                        solutions powered by AI. Passionate about turning ideas into reality through 
                        clean code and innovative thinking.
                    </p>
                    <div class="cta-buttons">
                        <a href="#projects" class="btn btn-primary lang-text" data-en="View My Work" data-fr="Voir mes Projets">View My Work</a>
                        <a href="#contact" class="btn btn-secondary lang-text" data-en="Get In Touch" data-fr="Me Contacter">Get In Touch</a>
                    </div>
                </div>
                <div class="hero-image">
                    <div class="profile-picture">
                        <img src="your-photo.jpg" alt="Profile Picture">
                    </div>
                </div>
            </div>
        </section>

        <section id="about" class="fade-in">
            <h2 class="section-title">
                <span class="section-number">01.</span> <span class="lang-text" data-en="About Me" data-fr="À Propos">About Me</span>
            </h2>
            <p class="lang-text" style="color: var(--text-dim); font-size: 1.1rem; line-height: 1.8; max-width: 800px;" data-en="I'm a software engineer and data analyst with a deep passion for artificial intelligence and machine learning. My journey in tech has equipped me with a unique blend of development skills and analytical expertise, allowing me to build robust applications while extracting meaningful insights from data. I thrive on solving complex problems and am constantly exploring the latest advancements in AI to create innovative solutions that make a real impact." data-fr="Je suis ingénieur logiciel et analyste de données avec une passion profonde pour l'intelligence artificielle et l'apprentissage automatique. Mon parcours dans la technologie m'a doté d'un mélange unique de compétences en développement et d'expertise analytique, me permettant de créer des applications robustes tout en extrayant des informations significatives des données. Je m'épanouis dans la résolution de problèmes complexes et j'explore constamment les dernières avancées en IA pour créer des solutions innovantes qui ont un impact réel.">
                I'm a software engineer and data analyst with a deep passion for artificial intelligence 
                and machine learning. My journey in tech has equipped me with a unique blend of development 
                skills and analytical expertise, allowing me to build robust applications while extracting 
                meaningful insights from data. I thrive on solving complex problems and am constantly exploring 
                the latest advancements in AI to create innovative solutions that make a real impact.
            </p>
        </section>

        <section id="skills" class="fade-in">
            <h2 class="section-title">
                <span class="section-number">02.</span> <span class="lang-text" data-en="Skills & Expertise" data-fr="Compétences & Expertise">Skills & Expertise</span>
            </h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <h3 class="lang-text" data-en="Software Engineering" data-fr="Ingénierie Logicielle">Software Engineering</h3>
                    <p class="lang-text" data-en="Building scalable applications with modern technologies and best practices." data-fr="Création d'applications évolutives avec des technologies modernes et les meilleures pratiques.">Building scalable applications with modern technologies and best practices.</p>
                    <div class="skill-tags">
                        <span class="tag">Python</span>
                        <span class="tag">JavaScript</span>
                        <span class="tag">React</span>
                        <span class="tag">Node.js</span>
                        <span class="tag">SQL</span>
                        <span class="tag">Git</span>
                    </div>
                </div>
                <div class="skill-card">
                    <h3 class="lang-text" data-en="Data Analysis" data-fr="Analyse de Données">Data Analysis</h3>
                    <p class="lang-text" data-en="Extracting insights and creating data-driven solutions for business problems." data-fr="Extraction d'informations et création de solutions basées sur les données pour les problèmes d'affaires.">Extracting insights and creating data-driven solutions for business problems.</p>
                    <div class="skill-tags">
                        <span class="tag">Pandas</span>
                        <span class="tag">NumPy</span>
                        <span class="tag">SQL</span>
                        <span class="tag">Tableau</span>
                        <span class="tag">Excel</span>
                        <span class="tag lang-text" data-en="Statistics" data-fr="Statistiques">Statistics</span>
                    </div>
                </div>
                <div class="skill-card">
                    <h3 class="lang-text" data-en="AI & Machine Learning" data-fr="IA & Apprentissage Automatique">AI & Machine Learning</h3>
                    <p class="lang-text" data-en="Developing intelligent systems and exploring cutting-edge AI technologies." data-fr="Développement de systèmes intelligents et exploration des technologies d'IA de pointe.">Developing intelligent systems and exploring cutting-edge AI technologies.</p>
                    <div class="skill-tags">
                        <span class="tag">TensorFlow</span>
                        <span class="tag">PyTorch</span>
                        <span class="tag">Scikit-learn</span>
                        <span class="tag">NLP</span>
                        <span class="tag lang-text" data-en="Deep Learning" data-fr="Apprentissage Profond">Deep Learning</span>
                        <span class="tag">LLMs</span>
                    </div>
                </div>
            </div>
        </section>

        <section id="projects" class="fade-in">
            <h2 class="section-title">
                <span class="section-number">03.</span> <span class="lang-text" data-en="Featured Projects" data-fr="Projets Mis en Avant">Featured Projects</span>
            </h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-header">
                        <div>
                            <h3 class="lang-text" data-en="AI-Powered Analytics Dashboard" data-fr="Tableau de Bord d'Analyse Alimenté par l'IA">AI-Powered Analytics Dashboard</h3>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">GitHub →</a>
                            <a href="#" class="project-link">Live →</a>
                        </div>
                    </div>
                    <p class="lang-text" data-en="Built a comprehensive analytics dashboard using React and Python that leverages machine learning models to provide predictive insights. Features real-time data visualization, automated reporting, and intelligent anomaly detection." data-fr="Création d'un tableau de bord d'analyse complet utilisant React et Python qui exploite des modèles d'apprentissage automatique pour fournir des informations prédictives. Comprend la visualisation de données en temps réel, le reporting automatisé et la détection intelligente d'anomalies.">
                        Built a comprehensive analytics dashboard using React and Python that leverages 
                        machine learning models to provide predictive insights. Features real-time data 
                        visualization, automated reporting, and intelligent anomaly detection.
                    </p>
                    <div class="skill-tags">
                        <span class="tag">React</span>
                        <span class="tag">Python</span>
                        <span class="tag">TensorFlow</span>
                        <span class="tag">PostgreSQL</span>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div>
                            <h3 class="lang-text" data-en="Natural Language Processing Tool" data-fr="Outil de Traitement du Langage Naturel">Natural Language Processing Tool</h3>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">GitHub →</a>
                        </div>
                    </div>
                    <p class="lang-text" data-en="Developed an NLP application for sentiment analysis and text classification using transformer models. Achieved 94% accuracy on custom dataset and deployed as a REST API for seamless integration." data-fr="Développement d'une application NLP pour l'analyse de sentiment et la classification de texte utilisant des modèles transformers. Atteint 94% de précision sur un ensemble de données personnalisé et déployé comme API REST pour une intégration transparente.">
                        Developed an NLP application for sentiment analysis and text classification using 
                        transformer models. Achieved 94% accuracy on custom dataset and deployed as a 
                        REST API for seamless integration.
                    </p>
                    <div class="skill-tags">
                        <span class="tag">Python</span>
                        <span class="tag">PyTorch</span>
                        <span class="tag">FastAPI</span>
                        <span class="tag">Docker</span>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div>
                            <h3 class="lang-text" data-en="Data Visualization Platform" data-fr="Plateforme de Visualisation de Données">Data Visualization Platform</h3>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">GitHub →</a>
                            <a href="#" class="project-link">Live →</a>
                        </div>
                    </div>
                    <p class="lang-text" data-en="Created an interactive data visualization platform that transforms complex datasets into intuitive visual stories. Supports multiple data sources and offers customizable chart types with export capabilities." data-fr="Création d'une plateforme de visualisation de données interactive qui transforme des ensembles de données complexes en récits visuels intuitifs. Prend en charge plusieurs sources de données et offre des types de graphiques personnalisables avec des capacités d'exportation.">
                        Created an interactive data visualization platform that transforms complex datasets 
                        into intuitive visual stories. Supports multiple data sources and offers customizable 
                        chart types with export capabilities.
                    </p>
                    <div class="skill-tags">
                        <span class="tag">JavaScript</span>
                        <span class="tag">D3.js</span>
                        <span class="tag">Node.js</span>
                        <span class="tag">MongoDB</span>
                    </div>
                </div>
            </div>
        </section>

        <section id="experience" class="fade-in">
            <h2 class="section-title">
                <span class="section-number">04.</span> <span class="lang-text" data-en="Professional Experience" data-fr="Expérience Professionnelle">Professional Experience</span>
            </h2>
            <div class="experience-timeline">
                <div class="experience-card">
                    <div class="experience-header">
                        <div>
                            <h3 class="lang-text" data-en="Senior Software Engineer" data-fr="Ingénieur Logiciel Senior">Senior Software Engineer</h3>
                            <p class="company-name lang-text" data-en="Tech Company Inc." data-fr="Tech Company Inc.">Tech Company Inc.</p>
                        </div>
                        <span class="experience-date lang-text" data-en="2022 - Present" data-fr="2022 - Présent">2022 - Present</span>
                    </div>
                    <ul class="experience-list">
                        <li class="lang-text" data-en="Led development of microservices architecture serving 1M+ users, improving system performance by 40%" data-fr="Direction du développement d'une architecture de microservices desservant plus d'1M d'utilisateurs, améliorant les performances du système de 40%">Led development of microservices architecture serving 1M+ users, improving system performance by 40%</li>
                        <li class="lang-text" data-en="Implemented machine learning models for predictive analytics, increasing revenue forecasting accuracy by 25%" data-fr="Mise en œuvre de modèles d'apprentissage automatique pour l'analyse prédictive, augmentant la précision des prévisions de revenus de 25%">Implemented machine learning models for predictive analytics, increasing revenue forecasting accuracy by 25%</li>
                        <li class="lang-text" data-en="Mentored junior developers and conducted code reviews to maintain high code quality standards" data-fr="Mentorat de développeurs juniors et réalisation de revues de code pour maintenir des normes de qualité élevées">Mentored junior developers and conducted code reviews to maintain high code quality standards</li>
                    </ul>
                    <div class="skill-tags">
                        <span class="tag">Python</span>
                        <span class="tag">React</span>
                        <span class="tag">AWS</span>
                        <span class="tag">Docker</span>
                    </div>
                </div>

                <div class="experience-card">
                    <div class="experience-header">
                        <div>
                            <h3 class="lang-text" data-en="Data Analyst" data-fr="Analyste de Données">Data Analyst</h3>
                            <p class="company-name lang-text" data-en="Analytics Solutions Ltd." data-fr="Analytics Solutions Ltd.">Analytics Solutions Ltd.</p>
                        </div>
                        <span class="experience-date">2020 - 2022</span>
                    </div>
                    <ul class="experience-list">
                        <li class="lang-text" data-en="Designed and maintained data pipelines processing 10TB+ of data daily using Python and SQL" data-fr="Conception et maintenance de pipelines de données traitant plus de 10TB de données quotidiennement avec Python et SQL">Designed and maintained data pipelines processing 10TB+ of data daily using Python and SQL</li>
                        <li class="lang-text" data-en="Created interactive dashboards and reports using Tableau, enabling data-driven decision making across teams" data-fr="Création de tableaux de bord et rapports interactifs avec Tableau, permettant une prise de décision basée sur les données">Created interactive dashboards and reports using Tableau, enabling data-driven decision making across teams</li>
                        <li class="lang-text" data-en="Performed A/B testing and statistical analysis to optimize product features, resulting in 15% user engagement increase" data-fr="Réalisation de tests A/B et analyses statistiques pour optimiser les fonctionnalités produit, résultant en une augmentation de 15% de l'engagement utilisateur">Performed A/B testing and statistical analysis to optimize product features, resulting in 15% user engagement increase</li>
                    </ul>
                    <div class="skill-tags">
                        <span class="tag">SQL</span>
                        <span class="tag">Python</span>
                        <span class="tag">Tableau</span>
                        <span class="tag">Statistics</span>
                    </div>
                </div>

                <div class="experience-card">
                    <div class="experience-header">
                        <div>
                            <h3 class="lang-text" data-en="Junior Software Developer" data-fr="Développeur Logiciel Junior">Junior Software Developer</h3>
                            <p class="company-name lang-text" data-en="StartUp Innovations" data-fr="StartUp Innovations">StartUp Innovations</p>
                        </div>
                        <span class="experience-date">2018 - 2020</span>
                    </div>
                    <ul class="experience-list">
                        <li class="lang-text" data-en="Developed full-stack web applications using JavaScript, React, and Node.js" data-fr="Développement d'applications web full-stack utilisant JavaScript, React et Node.js">Developed full-stack web applications using JavaScript, React, and Node.js</li>
                        <li class="lang-text" data-en="Collaborated with cross-functional teams to deliver features on tight deadlines" data-fr="Collaboration avec des équipes interfonctionnelles pour livrer des fonctionnalités dans des délais serrés">Collaborated with cross-functional teams to deliver features on tight deadlines</li>
                        <li class="lang-text" data-en="Participated in agile development processes and contributed to sprint planning" data-fr="Participation aux processus de développement agile et contribution à la planification des sprints">Participated in agile development processes and contributed to sprint planning</li>
                    </ul>
                    <div class="skill-tags">
                        <span class="tag">JavaScript</span>
                        <span class="tag">React</span>
                        <span class="tag">Node.js</span>
                        <span class="tag">MongoDB</span>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="fade-in">
            <div class="contact-content">
                <span class="section-number" style="display: block; margin-bottom: 1rem;">05.</span>
                <h2 class="lang-text" data-en="Let's Build Something Amazing" data-fr="Construisons Quelque Chose d'Incroyable">Let's Build Something Amazing</h2>
                <p class="lang-text" data-en="I'm always interested in hearing about new projects and opportunities. Whether you have a question or just want to say hi, feel free to reach out!" data-fr="Je suis toujours intéressé par de nouveaux projets et opportunités. Que vous ayez une question ou que vous vouliez simplement dire bonjour, n'hésitez pas à me contacter !">
                    I'm always interested in hearing about new projects and opportunities. 
                    Whether you have a question or just want to say hi, feel free to reach out!
                </p>
                <a href="/cdn-cgi/l/email-protection#0a73657f78246f676b63664a6f726b677a666f24696567" class="btn btn-primary lang-text" data-en="Say Hello" data-fr="Dites Bonjour">Say Hello</a>
                
                <div class="social-links">
                    <a href="https://github.com/yourusername" class="social-link" target="_blank">GitHub</a>
                    <a href="https://linkedin.com/in/yourprofile" class="social-link" target="_blank">LinkedIn</a>
                    <a href="https://twitter.com/yourhandle" class="social-link" target="_blank">Twitter</a>
                </div>
            </div>
        </section>
    </main>

    <footer>
        <div class="container">
            <p class="lang-text" data-en="© 2024 Your Name. Built with passion and curiosity." data-fr="© 2024 Votre Nom. Conçu avec passion et curiosité.">&copy; 2024 Your Name. Built with passion and curiosity.</p>
        </div>
    </footer>

    <script data-cfasync="false" src="/cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js"></script><script>
        let currentLang = 'en';

        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'fr' : 'en';
            document.querySelector('.lang-toggle').textContent = currentLang === 'en' ? 'FR' : 'EN';
            
            document.querySelectorAll('.lang-text').forEach(element => {
                const text = element.getAttribute('data-' + currentLang);
                if (text) {
                    element.textContent = text;
                }
            });

            localStorage.setItem('preferredLanguage', currentLang);
        }

        function toggleMenu() {
            const navMenu = document.getElementById('nav-menu');
            navMenu.classList.toggle('active');
        }

        function closeMenu() {
            const navMenu = document.getElementById('nav-menu');
            navMenu.classList.remove('active');
        }

        window.addEventListener('DOMContentLoaded', () => {
            const savedLang = localStorage.getItem('preferredLanguage');
            if (savedLang && savedLang !== currentLang) {
                toggleLanguage();
            }
        });

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => {
            observer.observe(el);
        });
    </script>