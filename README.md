<!DOCTYPE html>
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
                2px 2px 0 rgba(216, 150, 173, 0.3);
            animation: glitchLogo 3s infinite;
            cursor: pointer;
        }
        
        @keyframes glitchLogo {
            0%, 90%, 100% { 
                transform: translate(0);
                text-shadow: 
                    0 0 5px rgba(255, 255, 255, 0.1),
                    2px 2px 0 rgba(216, 150, 173, 0.3);
            }
            92% { 
                transform: translate(-2px, 2px);
                text-shadow: 
                    0 0 5px rgba(216, 150, 173, 0.2),
                    2px -2px 0 rgba(200, 200, 200, 0.3);
            }
            94% { 
                transform: translate(2px, -2px);
                text-shadow: 
                    0 0 5px rgba(255, 255, 255, 0.15),
                    -2px 2px 0 rgba(216, 150, 173, 0.2);
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
                radial-gradient(circle at 20% 50%, rgba(216, 150, 173, 0.03) 0%, transparent 50%),
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
            text-shadow: 0 0 3px rgba(216, 150, 173, 0.2);
            font-weight: 700;
        }
        
        /* Visualizer with Mandala Shapes */
        .visualizer {
            width: 100%;
            max-width: 700px;
            height: 300px;
            position: relative;
            margin-bottom: 3rem;
        }
        
        .mandala-shape {
            position: absolute;
            animation: rotateFloat 8s ease-in-out infinite;
        }
        
        .mandala-shape svg {
            filter: drop-shadow(0 0 10px rgba(200, 200, 200, 0.1));
        }
        
        .mandala-1 {
            left: 5%;
            top: 10%;
            animation-delay: 0s;
        }
        
        .mandala-2 {
            right: 10%;
            top: 5%;
            animation-delay: 1s;
        }
        
        .mandala-3 {
            left: 40%;
            bottom: 10%;
            animation-delay: 2s;
        }
        
        @keyframes rotateFloat {
            0%, 100% { 
                transform: translate(0, 0) rotate(0deg) scale(1);
            }
            25% { 
                transform: translate(15px, -20px) rotate(90deg) scale(1.05);
            }
            50% { 
                transform: translate(0, -30px) rotate(180deg) scale(0.95);
            }
            75% { 
                transform: translate(-15px, -10px) rotate(270deg) scale(1.02);
            }
        }
        
        /* CTA Button */
        .cta-button {
            padding: 1.2rem 3rem;
            font-size: 1.2rem;
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            background: linear-gradient(135deg, #4a4a4a 0%, #2a2a2a 100%);
            color: #e8e8e8;
            border: 2px solid #d896ad;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.2rem;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 0 20px rgba(216, 150, 173, 0.15);
        }
        
        .cta-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(216, 150, 173, 0.25);
            border-color: #e8a6bd;
        }
        
        .cta-button::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.1);
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
            color: #d896ad;
            text-shadow: 0 0 5px rgba(216, 150, 173, 0.2);
            border-left: 4px solid #d896ad;
            padding-left: 1rem;
        }
        
        /* Manifest Section */
        .manifest {
            background: linear-gradient(135deg, rgba(216, 150, 173, 0.03) 0%, rgba(200, 200, 200, 0.02) 100%);
            border: 2px solid #333;
            position: relative;
        }
        
        .manifest-visual {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 5rem;
            padding: 4rem 2rem;
            margin-bottom: 2rem;
        }
        
        .energy-shape {
            position: relative;
        }
        
        .energy-shape svg {
            filter: drop-shadow(0 0 15px rgba(216, 150, 173, 0.2));
        }
        
        .energy-shape.glitch-active svg {
            animation: chaosGlitch 2s infinite;
        }
        
        @keyframes chaosGlitch {
            0%, 100% { transform: translate(0) rotate(0deg) scale(1); }
            10% { transform: translate(-5px, 5px) rotate(5deg) scale(1.05); }
            20% { transform: translate(5px, -5px) rotate(-5deg) scale(0.95); }
            30% { transform: translate(-3px, -3px) rotate(3deg) scale(1.02); }
            40% { transform: translate(3px, 3px) rotate(-3deg) scale(0.98); }
            50% { transform: translate(0) rotate(0deg) scale(1); }
        }
        
        .energy-shape.resolved svg {
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
            border-left: 3px solid #d896ad;
            background: rgba(216, 150, 173, 0.02);
        }
        
        .manifesto-block:last-child {
            margin-bottom: 0;
        }
        
        .directive-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
            color: #d896ad;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 0.1rem;
        }
        
        .manifest-content p {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 1rem;
            color: #b0b0b0;
        }
        
        .manifest-content .pop-magic {
            color: #d896ad;
            font-weight: 700;
            font-style: italic;
            font-size: 1.15rem;
            text-shadow: 0 0 3px rgba(216, 150, 173, 0.2);
        }
        
        /* Methodology Section */
        .methodology {
            background: #1a1a1a;
        }
        
        .method-window {
            border: 2px solid #4a4a4a;
            background: #0f0f0f;
            margin: 2rem 0;
            box-shadow: 0 0 15px rgba(200, 200, 200, 0.08);
        }
        
        .window-header {
            background: linear-gradient(180deg, #333 0%, #1a1a1a 100%);
            padding: 0.5rem 1rem;
            border-bottom: 2px solid #4a4a4a;
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
        
        .dot.red { background: #d896ad; opacity: 0.6; }
        .dot.yellow { background: #c0c0c0; opacity: 0.6; }
        .dot.green { background: #8a8a8a; opacity: 0.6; }
        
        .window-content {
            padding: 2rem;
        }
        
        .phase {
            margin-bottom: 2rem;
        }
        
        .phase h3 {
            color: #d896ad;
            font-family: 'Orbitron', sans-serif;
            margin-bottom: 0.5rem;
            font-size: 1.3rem;
        }
        
        .phase p {
            color: #b0b0b0;
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
            border-color: #8a8a8a;
            box-shadow: 0 0 20px rgba(200, 200, 200, 0.15);
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
                    #8a8a8a 0px,
                    transparent 2px,
                    transparent 4px,
                    rgba(216, 150, 173, 0.3) 6px
                );
            opacity: 0.2;
            animation: glitchBurst 0.3s;
        }
        
        @keyframes glitchBurst {
            0%, 100% { transform: translate(0); opacity: 0.2; }
            25% { transform: translate(-5px, 5px); opacity: 0.3; }
            50% { transform: translate(5px, -5px); opacity: 0.25; }
            75% { transform: translate(-3px, -3px); opacity: 0.35; }
        }
        
        .project-info {
            padding: 1.5rem;
        }
        
        .project-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.2rem;
            color: #d896ad;
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
            color: #d896ad;
            font-family: 'Orbitron', sans-serif;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            background: #0a0a0a;
            border: 2px solid #333;
            color: #e8e8e8;
            font-family: 'Space Mono', monospace;
            transition: all 0.3s;
        }
        
        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #d896ad;
            box-shadow: 0 0 10px rgba(216, 150, 173, 0.15);
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
            border-top: 2px solid #3a3a3a;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 1rem;
        }
        
        .social-links a {
            color: #d896ad;
            text-decoration: none;
            transition: all 0.3s;
            font-size: 1.1rem;
        }
        
        .social-links a:hover {
            color: #e8a6bd;
            text-shadow: 0 0 5px rgba(216, 150, 173, 0.3);
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
            
            .manifest-visual {
                gap: 2rem;
                flex-direction: column;
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
            <!-- Complex Mandala Shape 1 -->
            <div class="mandala-shape mandala-1">
                <svg width="120" height="120" viewBox="0 0 120 120">
                    <circle cx="60" cy="60" r="50" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.3"/>
                    <circle cx="60" cy="60" r="40" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.4"/>
                    <circle cx="60" cy="60" r="30" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.5"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(45 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(90 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(135 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(180 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(225 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(270 60 60)"/>
                    <path d="M60,10 L65,50 L60,60 L55,50 Z" fill="#8a8a8a" opacity="0.2" transform="rotate(315 60 60)"/>
                    <circle cx="60" cy="60" r="8" fill="#d896ad" opacity="0.5"/>
                </svg>
            </div>
            
            <!-- Complex Mandala Shape 2 -->
            <div class="mandala-shape mandala-2">
                <svg width="100" height="100" viewBox="0 0 100 100">
                    <polygon points="50,5 95,95 5,95" fill="none" stroke="#d896ad" stroke-width="2" opacity="0.4"/>
                    <polygon points="50,15 85,85 15,85" fill="none" stroke="#d896ad" stroke-width="1.5" opacity="0.3"/>
                    <polygon points="50,25 75,75 25,75" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.3"/>
                    <line x1="50" y1="5" x2="50" y2="95" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="5" y1="95" x2="95" y2="95" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="95" y1="95" x2="50" y2="5" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <circle cx="50" cy="50" r="15" fill="none" stroke="#d896ad" stroke-width="1" opacity="0.4"/>
                    <circle cx="50" cy="50" r="5" fill="#d896ad" opacity="0.3"/>
                </svg>
            </div>
            
            <!-- Complex Mandala Shape 3 -->
            <div class="mandala-shape mandala-3">
                <svg width="90" height="90" viewBox="0 0 90 90">
                    <rect x="10" y="10" width="70" height="70" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.3"/>
                    <rect x="20" y="20" width="50" height="50" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.4" transform="rotate(45 45 45)"/>
                    <circle cx="45" cy="45" r="30" fill="none" stroke="#d896ad" stroke-width="1.5" opacity="0.3"/>
                    <circle cx="45" cy="45" r="20" fill="none" stroke="#d896ad" stroke-width="1" opacity="0.4"/>
                    <line x1="45" y1="15" x2="45" y2="75" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="15" y1="45" x2="75" y2="45" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="20" y1="20" x2="70" y2="70" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="70" y1="20" x2="20" y2="70" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <circle cx="45" cy="45" r="8" fill="none" stroke="#d896ad" stroke-width="2" opacity="0.5"/>
                </svg>
            </div>
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
            <!-- Chaotic Glitch Shape -->
            <div class="energy-shape glitch-active">
                <svg width="140" height="140" viewBox="0 0 140 140">
                    <polygon points="70,10 130,130 10,130" fill="none" stroke="#d896ad" stroke-width="2" opacity="0.4"/>
                    <polygon points="70,20 120,120 20,120" fill="none" stroke="#8a8a8a" stroke-width="1.5" opacity="0.3"/>
                    <circle cx="70" cy="70" r="45" fill="none" stroke="#d896ad" stroke-width="1" opacity="0.3"/>
                    <circle cx="70" cy="70" r="30" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.4"/>
                    <line x1="70" y1="10" x2="70" y2="130" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="10" y1="130" x2="130" y2="130" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <line x1="130" y1="130" x2="70" y2="10" stroke="#8a8a8a" stroke-width="0.5" opacity="0.3"/>
                    <rect x="50" y="50" width="40" height="40" fill="none" stroke="#d896ad" stroke-width="1" opacity="0.3" transform="rotate(45 70 70)"/>
                    <circle cx="70" cy="70" r="10" fill="#d896ad" opacity="0.4"/>
                </svg>
            </div>
            
            <!-- Resolved Geometric Shape -->
            <div class="energy-shape resolved">
                <svg width="120" height="120" viewBox="0 0 120 120">
                    <circle cx="60" cy="60" r="50" fill="none" stroke="#8a8a8a" stroke-width="2" opacity="0.4"/>
                    <circle cx="60" cy="60" r="40" fill="none" stroke="#8a8a8a" stroke-width="1.5" opacity="0.3"/>
                    <polygon points="60,15 105,105 15,105" fill="none" stroke="#d896ad" stroke-width="2" opacity="0.5"/>
                    <polygon points="60,25 95,95 25,95" fill="none" stroke="#8a8a8a" stroke-width="1" opacity="0.3"/>
                    <path d="M60,15 L65,55 L60,60 L55,55 Z" fill="#d896ad" opacity="0.2"/>
                    <path d="M60,15 L65,55 L60,60 L55,55 Z" fill="#d896ad" opacity="0.2" transform="rotate(120 60 60)"/>
                    <path d="M60,15 L65,55 L60,60 L55,55 Z" fill="#d896ad" opacity="0.2" transform="rotate(240 60 60)"/>
                    <circle cx="60" cy="60" r="15" fill="none" stroke="#d896ad" stroke-width="2" opacity="0.5"/>
                    <circle cx="60" cy="60" r="8" fill="#d896ad" opacity="0.4"/>
                </svg>
            </div>
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
        
        <div class="
