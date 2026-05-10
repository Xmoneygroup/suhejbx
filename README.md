<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XKAPO | Authority</title>
    <style>
        /* General Reset */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: #000;
            color: #fff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }

        /* 2-Second Intro Animation */
        #intro-splash {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .logo-anim {
            width: 250px;
            opacity: 0;
            transform: scale(0.8);
            animation: splashEffect 2s forwards;
        }

        @keyframes splashEffect {
            0% { opacity: 0; transform: scale(0.8); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(1.1); }
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 30px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-sizing: border-box;
            z-index: 1000;
            background: linear-gradient(to bottom, rgba(0,0,0,0.7), transparent);
        }

        .nav-logo {
            font-weight: bold;
            letter-spacing: 5px;
            font-size: 1.5rem;
        }

        .contact-link {
            text-decoration: none;
            color: #fff;
            border: 1px solid #fff;
            padding: 10px 25px;
            font-size: 0.9rem;
            letter-spacing: 2px;
            transition: all 0.3s ease;
        }

        .contact-link:hover {
            background: #fff;
            color: #000;
        }

        /* Home Page Slider */
        #home-content {
            opacity: 0;
            transition: opacity 1s ease;
        }

        .slider-container {
            position: relative;
            width: 100%;
            height: 100vh;
        }

        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1.5s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        /* Overlay for that Mansory vibe */
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.3);
            pointer-events: none;
        }
    </style>
</head>
<body>

    <div id="intro-splash">
        <img src="logo.png" alt="XKAPO" class="logo-anim">
    </div>

    <div id="home-content">
        <nav>
            <div class="nav-logo">XKAPO</div>
            <a href="tel:+389070878227" class="contact-link">CONTACT US</a>
        </nav>

        <div class="slider-container">
            <div class="overlay"></div>
            <div class="slide active" style="background-image: url('img1.jpg');"></div>
            <div class="slide" style="background-image: url('img2.jpg');"></div>
            <div class="slide" style="background-image: url('img3.jpg');"></div>
            <div class="slide" style="background-image: url('img4.jpg');"></div>
            <div class="slide" style="background-image: url('img5.jpg');"></div>
        </div>
    </div>

    <script>
        // Handle Intro Animation
        window.addEventListener('DOMContentLoaded', () => {
            setTimeout(() => {
                const splash = document.getElementById('intro-splash');
                const home = document.getElementById('home-content');
                
                splash.style.opacity = '0';
                setTimeout(() => {
                    splash.style.display = 'none';
                    home.style.opacity = '1';
                    startImageSlider();
                }, 500);
            }, 2000);
        });

        // Handle Slide Rotation (3.5 Seconds)
        function startImageSlider() {
            const slides = document.querySelectorAll('.slide');
            let currentIndex = 0;

            setInterval(() => {
                slides[currentIndex].classList.remove('active');
                currentIndex = (currentIndex + 1) % slides.length;
                slides[currentIndex].classList.add('active');
            }, 3500);
        }
    </script>
</body>
</html>
