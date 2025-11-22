HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MALWARE | Brand Official</title>
    <style>
        /* --- CSS STYLING --- */
        :root {
            --bg-color: #0a0a0a;
            --text-color: #e0e0e0;
            --accent-color: #00ff41; /* Matrix Green */
            --secondary-accent: #ff0055; /* Glitch Pink */
            --font-main: 'Courier New', Courier, monospace;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: var(--font-main);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 50px;
            border-bottom: 1px solid #333;
            position: fixed;
            width: 100%;
            background-color: rgba(10, 10, 10, 0.9);
            z-index: 1000;
        }

        .logo img {
            height: 40px; /* Adjusted for navbar */
            width: auto;
        }

        .nav-links a {
            color: var(--text-color);
            text-decoration: none;
            margin-left: 30px;
            text-transform: uppercase;
            font-size: 0.9rem;
        }

        .nav-links a:hover {
            color: var(--secondary-accent);
            text-decoration: line-through;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        /* Main Logo Integration */
        .hero-logo {
            max-width: 80%;
            height: auto;
            margin-bottom: 30px;
        }

        .subtitle {
            margin-top: 20px;
            font-size: 1.2rem;
            opacity: 0;
            animation: fadeIn 2s forwards 1s;
        }

        /* Content Section */
        .section {
            padding: 80px 50px;
            border-top: 1px solid #333;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }

        .card {
            border: 1px solid #333;
            padding: 20px;
            transition: 0.3s;
        }

        .card:hover {
            border-color: var(--accent-color);
            transform: translateY(-5px);
            box-shadow: 0 0 15px rgba(0, 255, 65, 0.2);
        }

        /* Button */
        .cta-button {
            margin-top: 30px;
            padding: 15px 40px;
            background: transparent;
            border: 1px solid var(--accent-color);
            color: var(--accent-color);
            font-family: var(--font-main);
            font-size: 1rem;
            cursor: pointer;
            transition: 0.3s;
        }

        .cta-button:hover {
            background: var(--accent-color);
            color: var(--bg-color);
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 40px;
            font-size: 0.8rem;
            color: #555;
        }

        /* Keyframes */
        @keyframes fadeIn {
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">
            <img src="Simple%20Malware.png" alt="MALWARE Logo">
        </div>
        <div class="nav-links">
            <a href="#about">About</a>
            <a href="#work">Projects</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <header class="hero">
        <img src="Simple%20Malware.png" alt="MALWARE Brand Logo" class="hero-logo">
        <p class="subtitle" id="subtitle-text">INFECTIOUS DESIGN // SYSTEM OVERRIDE</p>
        <button class="cta-button" onclick="scrambleText()">INITIATE PROTOCOL</button>
    </header>

    <section id="about" class="section">
        <h2>// SYSTEM_LOG: ABOUT</h2>
        <p style="margin-top: 20px; max-width: 600px;">
            Malware is not a bug; it's a feature. We specialize in disruptive aesthetics, high-contrast visuals, and breaking the rules of traditional design.
        </p>
    </section>

    <section id="work" class="section">
        <h2>// DIRECTORY: PROJECTS</h2>
        <div class="grid">
            <div class="card">
                <h3>PROJECT_01</h3>
                <p>Web Development</p>
            </div>
            <div class="card">
                <h3>PROJECT_02</h3>
                <p>Cyber Security Branding</p>
            </div>
            <div class="card">
                <h3>PROJECT_03</h3>
                <p>Glitch Art Series</p>
            </div>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 MALWARE BRAND. ALL RIGHTS RESERVED.</p>
    </footer>

    <script>
        // --- JAVASCRIPT INTERACTIVITY ---
        
        // Function to scramble text effect on the button click
        function scrambleText() {
            const title = document.getElementById('subtitle-text');
            const originalText = title.innerText;
            const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()';
            let iterations = 0;
            
            const interval = setInterval(() => {
                title.innerText = title.innerText.split('')
                    .map((letter, index) => {
                        if(index < iterations) {
                            return originalText[index];
                        }
                        return characters[Math.floor(Math.random() * 26)];
                    })
                    .join('');
                
                if(iterations >= originalText.length){ 
                    clearInterval(interval);
                    title.innerText = originalText;
                }
                
                iterations += 1/3;
            }, 30);
        }

        // Console "Easter Egg" for developers
        console.log("%c WARNING: AUTHORIZED ACCESS ONLY ", "background: red; color: white; font-size: 20px; padding: 5px;");
        console.log("Welcome to the Malware Brand backend.");
    </script>
</body>
</html>
