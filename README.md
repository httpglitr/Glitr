HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MALWARE | Soft Systems</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Silkscreen&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">

    <style>
        /* --- ORGANIC CSS STYLING --- */
        :root {
            /* Palette: Deep Organic Dark with Dusty Rose Accents */
            --bg-color: #1a181a;       /* Very dark warm grey/purple */
            --card-bg: #252225;        /* Slightly lighter card background */
            --text-color: #e6dee0;     /* Off-white pinkish text */
            --accent-color: #d68c9e;   /* Dusty Rose */
            --secondary-accent: #a89fce; /* Soft Lavender */
            
            /* Fonts */
            --font-logo: 'Silkscreen', cursive; /* The Pixel Font */
            --font-body: 'Space Mono', monospace; /* Clean, tech but soft */
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: var(--font-body);
            overflow-x: hidden;
            line-height: 1.7; /* More breathing room for text */
        }

        /* Navigation - Glassmorphism effect */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 50px;
            position: fixed;
            width: 100%;
            background-color: rgba(26, 24, 26, 0.85); /* See-through */
            backdrop-filter: blur(8px); /* Blurs what's behind it */
            z-index: 1000;
            border-bottom: 1px solid rgba(214, 140, 158, 0.2);
        }

        .logo-text {
            font-family: var(--font-logo);
            font-size: 1.8rem;
            color: var(--accent-color);
            letter-spacing: 1px;
            cursor: pointer;
        }

        .nav-links a {
            color: var(--text-color);
            text-decoration: none;
            margin-left: 30px;
            font-size: 0.9rem;
            opacity: 0.7;
            transition: 0.3s;
        }

        .nav-links a:hover {
            opacity: 1;
            color: var(--secondary-accent);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            /* Subtle organic gradient in background */
            background: radial-gradient(circle at 50% 50%, rgba(214, 140, 158, 0.05) 0%, rgba(26, 24, 26, 0) 60%);
        }

        /* The Main Logo Text */
        h1.brand-name {
            font-family: var(--font-logo);
            font-size: 5rem;
            color: var(--accent-color);
            text-shadow: 0 0 20px rgba(214, 140, 158, 0.3);
            /* Organic Float Animation */
            animation: float 6s ease-in-out infinite;
        }

        .subtitle {
            margin-top: 10px;
            font-size: 1rem;
            color: var(--secondary-accent);
            opacity: 0.8;
            font-weight: 400;
            letter-spacing: 2px;
        }

        /* Content Section */
        .section {
            padding: 100px 50px;
        }

        .section-title {
            font-family: var(--font-logo);
            color: var(--accent-color);
            margin-bottom: 40px;
            font-size: 2rem;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        /* Organic Cards */
        .card {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 20px; /* Rounded corners for organic feel */
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: 0.4s ease;
        }

        .card h3 {
            font-family: var(--font-logo);
            margin-bottom: 10px;
            color: var(--text-color);
        }

        .card:hover {
            transform: translateY(-10px); /* Lifts up slowly */
            border-color: var(--accent-color);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        /* Organic Button */
        .cta-button {
            margin-top: 40px;
            padding: 15px 50px;
            background: rgba(214, 140, 158, 0.1);
            border: 1px solid var(--accent-color);
            border-radius: 50px; /* Pill shape */
            color: var(--accent-color);
            font-family: var(--font-body);
            font-size: 1rem;
            cursor: pointer;
            transition: 0.3s;
        }

        .cta-button:hover {
            background: var(--accent-color);
            color: var(--bg-color);
            box-shadow: 0 0 20px rgba(214, 140, 158, 0.4);
        }

        footer {
            text-align: center;
            padding: 40px;
            font-size: 0.8rem;
            opacity: 0.5;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        /* Keyframes */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); } /* Floating up */
            100% { transform: translateY(0px); }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo-text">malware.sys</div>
        <div class="nav-links">
            <a href="#about">About</a>
            <a href="#work">Projects</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <header class="hero">
        <h1 class="brand-name">MALWARE</h1>
        <p class="subtitle">soft systems // organic errors</p>
        <button class="cta-button" onclick="softGlitch()">ENTER SYSTEM</button>
    </header>

    <section id="about" class="section">
        <h2 class="section-title">01_ABOUT</h2>
        <p style="max-width: 600px; line-height: 2;">
            We explore the beauty in system failures. Moving away from hard crashes into soft reboots. Our design philosophy blends the digital past with organic futures.
        </p>
    </section>

    <section id="work" class="section">
        <h2 class="section-title">02_DIRECTORY</h2>
        <div class="grid">
            <div class="card">
                <h3>Floral_Code</h3>
                <p>Web design that feels alive. Growing borders and breathing animations.</p>
            </div>
            <div class="card">
                <h3>Soft_Error</h3>
                <p>Branding for the digital age, focused on muted tones and rounded pixels.</p>
            </div>
            <div class="card">
                <h3>Y2K_Archive</h3>
                <p>Restoring the aesthetic of the early web with modern sensibilities.</p>
            </div>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 MALWARE. All systems stable.</p>
    </footer>

    <script>
        // A softer interaction script
        function softGlitch() {
            const title = document.querySelector('.brand-name');
            const originalText = "MALWARE";
            const chars = "ma1war3_sy$tem"; // Less random, more thematic characters
            
            // Temporary text shift
            title.innerText = "l0ad_ing...";
            
            setTimeout(() => {
                title.innerText = originalText;
            }, 800);
        }
    </script>
</body>
</html>
