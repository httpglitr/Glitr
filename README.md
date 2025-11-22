[malwahr_skade_portal.html](https://github.com/user-attachments/files/23687155/malwahr_skade_portal.html)
        .shape {
            position: absolute;
            border: 2px solid #6a6a6a;
            box-shadow: 0 0 10px rgba(200, 200, 200, 0.1);
            animation: float 4s ease-in-out infinite;
        }
        
        .shape:nth-child(1) {
            width: 100px;
            height: 100px;
            left: 10%;
            top: 20%;
            animation-delay: 0s;
        }
        
        .shape:nth-child(2) {
            width: 80px;
            height: 80px;
            right: 15%;<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MALWAHR - The Skade Program</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Orbitron:wght@400;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Space Mono', monospace;
            background: #0a0a0a;
            color: #e8e8e8;
            overflow-x: hidden;
            line-height: 1.6;
        }
        
        /* Scanline overlay */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(255, 255, 255, 0.01) 0px,
                transparent 2px,
                transparent 4px
            );
            pointer-events: none;
            z-index: 9999;
            animation: scanlines 8s linear infinite;
        }
        
        @keyframes scanlines {
            0% { transform: translateY(0); }
            100% { transform: translateY(20px); }
        }
        
        /* Header */
        header {
            padding: 2rem;
            text-align: center;
            background: linear-gradient(180deg, #1a1a1a 0%, #0a0a0a 100%);
            border-bottom: 2px solid #3a3a3a;
            position: relative;
        }
        
        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            font-weight: 900;
            letter-spacing: 0.3rem;
            color: #e8e8e8;
            text-shadow: 
                0 0 5px rgba(255, 255, 255, 0.1),
                2px 2px 0 rgba(255, 105, 180, 0.3);
            animation: glitchLogo 3s infinite;
            cursor: pointer;
        }
        
        @keyframes glitchLogo {
            0%, 90%, 100% { 
                transform: translate(0);
                text-shadow: 
                    0 0 5px rgba(255, 255, 255, 0.1),
                    2px 2px 0 rgba(255, 105, 180, 0.3);
            }
            92% { 
                transform: translate(-2px, 2px);
                text-shadow: 
                    0 0 5px rgba(255, 105, 180, 0.2),
                    2px -2px 0 rgba(200, 200, 200, 0.3);
            }
            94% { 
                transform: translate(2px, -2px);
                text-shadow: 
                    0 0 5px rgba(255, 255, 255, 0.15),
                    -2px 2px 0 rgba(255, 105, 180, 0.2);
            }
            96% {
                transform: translate(-2px, 0);
            }
        }
        
        /* Hero Section */
        .hero {
            min-height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 4rem 2rem;
            position: relative;
            background: 
                radial-gradient(circle at 20% 50%, rgba(255, 105, 180, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 80% 50%, rgba(200, 200, 200, 0.03) 0%, transparent 50%),
                #0a0a0a;
        }
        
        .hero-text {
            font-size: 2rem;
            max-width: 900px;
            text-align: center;
            margin-bottom: 3rem;
            line-height: 1.4;
            position: relative;
            z-index: 2;
            color: #d0d0d0;
        }
        
        .hero-text .highlight {
            color: #c0c0c0;
            text-shadow: 0 0 3px rgba(255, 255, 255, 0.1);
            font-weight: 700;
        }
        
        .hero-text .magic {
            color: #d896ad;
            text-shadow: 0 0 3px rgba(255, 105, 180, 0.2);
            font-weight: 700;
        }
        
        /* Visualizer */
        .visualizer {
            width: 100%;
            max-width: 600px;
            height: 200px;
            position: relative;
            margin-bottom: 3rem;
        }
        
        .shape {
            position: absolute;
            border: 2px solid #00ffff;
            box-shadow: 0 0 20px #00ffff;
            animation: float 4s ease-in-out infinite;
        }
        
        .shape:nth-child(1) {
            width: 100px;
            height: 100px;
            left: 10%;
            top: 20%;
            animation-delay: 0s;
        }
        
        .shape:nth-child(2) {
            width: 80px;
            height: 80px;
            right: 15%;
            top: 10%;
            border-color: #ff00ff;
            box-shadow: 0 0 20px #ff00ff;
            animation-delay: 0.5s;
        }
        
        .shape:nth-child(3) {
            width: 60px;
            height: 60px;
            left: 45%;
            bottom: 20%;
            border-color: #00ff00;
            box-shadow: 0 0 20px #00ff00;
            animation-delay: 1s;
        }
        
        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(10px, -20px) rotate(120deg); }
            66% { transform: translate(-10px, 10px) rotate(240deg); }
        }
        
        /* CTA Button */
        .cta-button {
            padding: 1.2rem 3rem;
            font-size: 1.2rem;
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            background: linear-gradient(135deg, #00ffff 0%, #ff00ff 100%);
            color: #000;
            border: none;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.2rem;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.5);
        }
        
        .cta-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 50px rgba(0, 255, 255, 0.8);
        }
        
        .cta-button::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.3);
            transform: rotate(45deg);
            transition: all 0.5s;
        }
        
        .cta-button:hover::before {
            left: 100%;
        }
        
        /* Section Styles */
        section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .section-header {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 2rem;
            color: #00ffff;
            text-shadow: 0 0 10px #00ffff;
            border-left: 4px solid #00ffff;
            padding-left: 1rem;
        }
        
        /* Manifest Section */
        .manifest {
            background: linear-gradient(135deg, rgba(255, 0, 255, 0.05) 0%, rgba(0, 255, 255, 0.05) 100%);
            border: 2px solid #333;
            position: relative;
        }
        
        .manifest-visual {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 4rem;
            padding: 3rem 2rem;
            margin-bottom: 2rem;
        }
        
        .energy-shape {
            width: 120px;
            height: 120px;
            position: relative;
        }
        
        .energy-shape.glitch-active {
            border: 3px solid #ff00ff;
            box-shadow: 
                0 0 20px #ff00ff,
                inset 0 0 20px rgba(255, 0, 255, 0.3);
            animation: chaosGlitch 2s infinite;
        }
        
        .energy-shape.glitch-active::before,
        .energy-shape.glitch-active::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: 3px solid #00ffff;
            animation: glitchShift 1.5s infinite;
        }
        
        .energy-shape.glitch-active::after {
            border-color: #00ff00;
            animation-delay: 0.3s;
        }
        
        @keyframes chaosGlitch {
            0%, 100% { transform: translate(0) rotate(0deg) scale(1); }
            10% { transform: translate(-5px, 5px) rotate(5deg) scale(1.05); }
            20% { transform: translate(5px, -5px) rotate(-5deg) scale(0.95); }
            30% { transform: translate(-3px, -3px) rotate(3deg) scale(1.02); }
            40% { transform: translate(3px, 3px) rotate(-3deg) scale(0.98); }
            50% { transform: translate(0) rotate(0deg) scale(1); }
        }
        
        @keyframes glitchShift {
            0%, 100% { transform: translate(0); opacity: 0.5; }
            25% { transform: translate(-10px, 5px); opacity: 0.7; }
            50% { transform: translate(10px, -5px); opacity: 0.3; }
            75% { transform: translate(-5px, -10px); opacity: 0.6; }
        }
        
        .energy-shape.resolved {
            width: 100px;
            height: 100px;
            border: 3px solid #00ffff;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.5);
            background: linear-gradient(135deg, rgba(0, 255, 255, 0.1) 0%, rgba(255, 0, 255, 0.1) 100%);
            clip-path: polygon(50% 0%, 100% 38%, 82% 100%, 18% 100%, 0% 38%);
            animation: gentleFloat 4s ease-in-out infinite;
        }
        
        @keyframes gentleFloat {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(5deg); }
        }
        
        .manifest-content {
            padding: 2rem;
            background: rgba(0, 0, 0, 0.5);
        }
        
        .manifesto-block {
            margin-bottom: 3rem;
            padding: 2rem;
            border-left: 3px solid #00ffff;
            background: rgba(0, 255, 255, 0.02);
        }
        
        .manifesto-block:last-child {
            margin-bottom: 0;
        }
        
        .directive-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
            color: #00ffff;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 0.1rem;
        }
        
        .manifest-content p {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 1rem;
            color: #cccccc;
        }
        
        .manifest-content .pop-magic {
            color: #ff00ff;
            font-weight: 700;
            font-style: italic;
            font-size: 1.15rem;
            text-shadow: 0 0 5px rgba(255, 0, 255, 0.3);
        }
        
        /* Methodology Section */
        .methodology {
            background: #1a1a1a;
        }
        
        .method-window {
            border: 2px solid #00ffff;
            background: #0f0f0f;
            margin: 2rem 0;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
        }
        
        .window-header {
            background: linear-gradient(180deg, #333 0%, #1a1a1a 100%);
            padding: 0.5rem 1rem;
            border-bottom: 2px solid #00ffff;
            font-family: 'Orbitron', sans-serif;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .window-dots {
            display: flex;
            gap: 0.3rem;
        }
        
        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }
        
        .dot.red { background: #ff0000; }
        .dot.yellow { background: #ffff00; }
        .dot.green { background: #00ff00; }
        
        .window-content {
            padding: 2rem;
        }
        
        .phase {
            margin-bottom: 2rem;
        }
        
        .phase h3 {
            color: #00ffff;
            font-family: 'Orbitron', sans-serif;
            margin-bottom: 0.5rem;
            font-size: 1.3rem;
        }
        
        .phase p {
            color: #cccccc;
            line-height: 1.6;
        }
        
        /* Portfolio Section */
        .portfolio {
            background: #0a0a0a;
        }
        
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }
        
        .project-card {
            background: #1a1a1a;
            border: 2px solid #333;
            overflow: hidden;
            cursor: pointer;
            position: relative;
            transition: all 0.3s;
        }
        
        .project-card:hover {
            border-color: #00ffff;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.4);
            transform: translateY(-5px);
        }
        
        .project-thumbnail {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            color: #666;
            position: relative;
            overflow: hidden;
        }
        
        .project-card:hover .project-thumbnail::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                repeating-linear-gradient(
                    0deg,
                    #00ffff 0px,
                    transparent 2px,
                    transparent 4px,
                    #ff00ff 6px
                );
            opacity: 0.3;
            animation: glitchBurst 0.3s;
        }
        
        @keyframes glitchBurst {
            0%, 100% { transform: translate(0); opacity: 0.3; }
            25% { transform: translate(-5px, 5px); opacity: 0.5; }
            50% { transform: translate(5px, -5px); opacity: 0.4; }
            75% { transform: translate(-3px, -3px); opacity: 0.6; }
        }
        
        .project-info {
            padding: 1.5rem;
        }
        
        .project-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.2rem;
            color: #00ffff;
            margin-bottom: 0.5rem;
        }
        
        .project-type {
            color: #999;
            font-size: 0.9rem;
        }
        
        /* Contact Section */
        .contact {
            background: linear-gradient(180deg, #0a0a0a 0%, #1a1a1a 100%);
            text-align: center;
        }
        
        .contact-form {
            max-width: 600px;
            margin: 3rem auto;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
            text-align: left;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #00ffff;
            font-family: 'Orbitron', sans-serif;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            background: #0a0a0a;
            border: 2px solid #333;
            color: #fff;
            font-family: 'Space Mono', monospace;
            transition: all 0.3s;
        }
        
        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #00ffff;
            box-shadow: 0 0 10px rgba(0, 255, 255, 0.3);
        }
        
        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }
        
        /* Footer */
        footer {
            background: #000;
            padding: 2rem;
            text-align: center;
            border-top: 2px solid #00ffff;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 1rem;
        }
        
        .social-links a {
            color: #00ffff;
            text-decoration: none;
            transition: all 0.3s;
            font-size: 1.1rem;
        }
        
        .social-links a:hover {
            color: #ff00ff;
            text-shadow: 0 0 10px #ff00ff;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .logo {
                font-size: 2rem;
            }
            
            .hero-text {
                font-size: 1.3rem;
            }
            
            .section-header {
                font-size: 1.8rem;
            }
            
            .portfolio-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">MALWAHR</div>
    </header>

    <section class="hero">
        <div class="visualizer">
            <div class="shape"></div>
            <div class="shape"></div>
            <div class="shape"></div>
        </div>
        <div class="hero-text">
            We <span class="highlight">hack the visual system</span> to unlock your <span class="magic">flow state</span>, translating your pure, mysterious energy into <span class="highlight">real, unstoppable design</span>.
        </div>
        <button class="cta-button" onclick="document.querySelector('.manifest').scrollIntoView({behavior: 'smooth'})">
            Begin Your Experiment
        </button>
    </section>

    <section class="manifest">
        <h2 class="section-header">// SKADE PROGRAM: The Energy Manifesto //</h2>
        
        <div class="manifest-visual">
            <div class="energy-shape glitch-active"></div>
            <div class="energy-shape resolved"></div>
        </div>
        
        <div class="manifest-content">
            <div class="manifesto-block">
                <h3 class="directive-title">The Core Directive: Expression</h3>
                <p class="pop-magic">Design is the language that speaks when talking is hard. We are here to translate the beautiful things, the sweet, little nothings you carry inside—the decision to set your surroundings based on how you feel—into a visual reality.</p>
                <p>We promote expression and doing whatever your heart desires through creative experimentation. This is how we begin.</p>
            </div>
            
            <div class="manifesto-block">
                <h3 class="directive-title">The Destination: Flow State</h3>
                <p class="pop-magic">The goal of the Skade Program is to move forward and never stop, allowing your allowance and energy to enter a Flow State.</p>
                <p>We provide the platform for this. By embracing your different, your mysterious, bold, simple, YOU, we help you put your soul into something that will bring life to this world.</p>
            </div>
            
            <div class="manifesto-block">
                <h3 class="directive-title">The Promise: Reality</h3>
                <p class="pop-magic">This is not just graphics; this is putting energy into something real.</p>
                <p>We create something uniquely your own, ensuring your purpose and authenticity are clearly understood by the right audience. Your brand is the ultimate form of self-expression.</p>
            </div>
        </div>
    </section>

    <section class="methodology">
        <h2 class="section-header">The Systematic Enchantment</h2>
        <p style="color: #999; font-size: 1.1rem; margin-bottom: 2rem;">Our Scaffold Method</p>
        
        <div class="method-window">
            <div class="window-header">
                <div class="window-dots">
                    <div class="dot red"></div>
                    <div class="dot yellow"></div>
                    <div class="dot green"></div>
                </div>
                <span>METHODOLOGY.exe</span>
            </div>
            <div class="window-content">
                <div class="phase">
                    <h3>Phase I: The Authentic Algorithm</h3>
                    <p>Decoding the founder's "Why" to ensure the project is uniquely their own. We dive deep into your story, extracting the essence that makes your vision irreplaceable. This isn't about trends—it's about truth.</p>
                </div>
                
                <div class="phase">
                    <h3>Phase II: Systematic Enchantment</h3>
                    <p>Applying Gestalt and Geometry to build an organized design structure that the brain comprehends. We construct the scaffold—the invisible architecture that makes complex ideas feel effortless and intuitive.</p>
                </div>
                
                <div class="phase">
                    <h3>Phase III: Visual Efficiency Hack</h3>
                    <p>Adhering to Less = More, ensuring every element serves the purpose and exudes pure creative energy. We strip away the noise, leaving only what matters—design that breathes, moves, and lives.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="portfolio">
        <h2 class="section-header">Translated into Real</h2>
        <div class="portfolio-grid">
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 01</div>
                <div class="project-info">
                    <div class="project-title">Brand Identity System</div>
                    <div class="project-type">Identity · Strategy</div>
                </div>
            </div>
            
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 02</div>
                <div class="project-info">
                    <div class="project-title">Digital Experience</div>
                    <div class="project-type">Web Design · Development</div>
                </div>
            </div>
            
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 03</div>
                <div class="project-info">
                    <div class="project-title">Visual Language</div>
                    <div class="project-type">Illustration · Motion</div>
                </div>
            </div>
            
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 04</div>
                <div class="project-info">
                    <div class="project-title">System Architecture</div>
                    <div class="project-type">UI/UX · Product</div>
                </div>
            </div>
            
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 05</div>
                <div class="project-info">
                    <div class="project-title">Creative Direction</div>
                    <div class="project-type">Art Direction · Brand</div>
                </div>
            </div>
            
            <div class="project-card">
                <div class="project-thumbnail">PROJECT 06</div>
                <div class="project-info">
                    <div class="project-title">Flow State Interface</div>
                    <div class="project-type">Interactive · Experience</div>
                </div>
            </div>
        </div>
    </section>

    <section class="contact">
        <h2 class="section-header">Initiate the Download</h2>
        <p style="font-size: 1.2rem; margin-bottom: 2rem; color: #999;">Ready to exert your pure energy into something real?</p>
        <p style="font-size: 1.3rem; color: #00ffff; margin-bottom: 3rem;">Book a FREE 30-Minute Discovery Call</p>
        
        <div class="contact-form">
            <div class="form-group">
                <label>Name</label>
                <input type="text" placeholder="Enter your name">
            </div>
            <div class="form-group">
                <label>Email</label>
                <input type="email" placeholder="your@email.com">
            </div>
            <div class="form-group">
                <label>Message</label>
                <textarea placeholder="Tell us about your project..."></textarea>
            </div>
            <button class="cta-button">Initialize Connection</button>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 MALWAHR. All rights reserved.</p>
        <div class="social-links">
            <a href="#">Instagram</a>
            <a href="#">Twitter</a>
            <a href="#">LinkedIn</a>
            <a href="#">Email</a>
        </div>
    </footer>
</body>
</html>
