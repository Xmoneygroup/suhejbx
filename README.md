<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>XKAPO | Official</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body, html { 
            width: 100%; height: 100%; 
            background-color: #000; 
            overflow: hidden; 
            position: fixed; 
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
        }

        /* 1. INTRO SPLASH - LOGOJA E MADHE */
        #intro-splash {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-color: #000;
            display: flex; justify-content: center; align-items: center;
            z-index: 10000;
        }

        .logo-anim {
            width: 550px; 
            max-width: 90%; 
            height: auto;
            opacity: 0;
            animation: logoFlash 2s forwards;
        }

        @keyframes logoFlash {
            0% { opacity: 0; transform: scale(0.9); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(1.1); }
        }

        /* 2. NEON GLOW BACKGROUND */
        #neon-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: 1; pointer-events: none; opacity: 0; transition: opacity 2s ease;
        }
        .neon-spark {
            position: absolute; top: -150px; left: -150px;
            width: 700px; height: 700px;
            border-radius: 50%; filter: blur(160px);
            background: rgba(0, 255, 255, 0.2);
            animation: neonShift 12s infinite alternate ease-in-out;
        }
        @keyframes neonShift {
            0% { background: rgba(0, 255, 255, 0.2); }
            50% { background: rgba(255, 0, 255, 0.15); }
            100% { background: rgba(255, 255, 255, 0.1); }
        }

        /* 3. HOME CONTENT */
        #home-content { opacity: 0; width: 100%; height: 100%; position: relative; transition: opacity 1s; z-index: 10; }

        /* HEADER CENTER - LOGOJA SI TITULL (PA TË ZEZA) */
        .header-center {
            position: absolute; top: 10%; width: 100%;
            display: flex; justify-content: center; align-items: center;
            z-index: 2000;
        }
        .xkapo-title-wrap { display: flex; align-items: center; gap: 30px; }
        
        .wing {
            width: 100px; height: 2px;
            background: linear-gradient(to right, transparent, #fff);
        }
        .wing.right { background: linear-gradient(to left, transparent, #fff); }

        /* KODI QË HEQ TË ZEZA NGA FOTOJA DHE E BËN TITULL */
        .main-logo-title {
            width: 300px; /* Madhësia e logos si titull */
            height: auto;
            mix-blend-mode: screen; /* Ky rresht zhduk prapavijën e zezë të fotos */
            filter: brightness(1.2);
            animation: titleGlow 4s infinite ease-in-out;
        }

        @keyframes titleGlow {
            0%, 100% { opacity: 0.9; transform: scale(1); filter: brightness(1); }
            50% { opacity: 1; transform: scale(1.05); filter: brightness(1.5); }
        }

        /* CONTACT US - DJATHTAS POSHTË */
        .contact-wrap {
            position: absolute; bottom: 40px; right: 40px; z-index: 2000;
        }
        .contact-btn {
            color: #fff; text-decoration: none; font-size: 13px; letter-spacing: 4px;
            border: 1px solid rgba(255,255,255,0.6); padding: 12px 35px;
            text-transform: uppercase; transition: 0.4s;
            background: rgba(0,0,0,0.3); backdrop-filter: blur(5px);
        }
        .contact-btn:hover { background: #fff; color: #000; border-color: #fff; box-shadow: 0 0 20px #fff; }

        /* SLIDER */
        .slider-container { width: 100%; height: 100%; position: relative; }
        .slide {
            position: absolute; width: 100%; height: 100%;
            background-size: cover; background-position: center;
            opacity: 0; transition: opacity 1.5s ease-in-out;
            z-index: 5;
        }
        .slide.active { opacity: 1; z-index: 6; }

        .overlay {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle, transparent 10%, rgba(0,0,0,0.7) 100%);
            z-index: 15; pointer-events: none;
        }
    </style>
</head>
<body>

    <div id="intro-splash">
        <img src="9BA7D80D-DB0A-4D39-9C65-6FD915BCF247.jpg" alt="XKAPO" class="logo-anim">
    </div>

    <div id="neon-bg">
        <div class="neon-spark"></div>
    </div>

    <div id="home-content">
        <div class="header-center">
            <div class="xkapo-title-wrap">
                <div class="wing"></div>
                <img src="9BA7D80D-DB0A-4D39-9C65-6FD915BCF247.jpg" class="main-logo-title" alt="XKAPO">
                <div class="wing right"></div>
            </div>
        </div>

        <div class="contact-wrap">
            <a href="tel:+389070878227" class="contact-btn">Contact Us</a>
        </div>

        <div class="slider-container">
            <div class="overlay"></div>
            <div class="slide active" style="background-image: url('IMG_1022.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1024.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1025.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1026.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1027.jpg');"></div>
        </div>
    </div>

    <script>
        window.addEventListener('load', () => {
            const splash = document.getElementById('intro-splash');
            const home = document.getElementById('home-content');
            const neon = document.getElementById('neon-bg');
            
            initSlider();

            setTimeout(() => {
                splash.style.opacity = '0';
                neon.style.opacity = '1';
                setTimeout(() => {
                    splash.style.display = 'none';
                    home.style.opacity = '1';
                }, 800);
            }, 2000);
        });

        function initSlider() {
            const slides = document.querySelectorAll('.slide');
            let current = 0;
            setInterval(() => {
                slides[current].classList.remove('active');
                current = (current + 1) % slides.length;
                slides[current].classList.add('active');
            }, 3500);
        }
    </script>
</body>
</html>
