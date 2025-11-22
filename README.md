[malwahr_skade_portal (1).html](https://github.com/user-attachments/files/23687177/malwahr_skade_portal.1.html)
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
            text-al
