<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MkdMap - Ultra Luxury Directory</title>
    <style>
        /* --- 1. STILI PËR EKRANIN HYRËS (SPLASH SCREEN) --- */
        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #090d16; /* Edhe më i errët për kontrast */
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 1;
            transition: opacity 0.6s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .splash-text {
            color: #ffffff;
            font-family: 'Montserrat', sans-serif, system-ui;
            font-size: 2.2rem;
            font-weight: 800;
            letter-spacing: 4px;
            text-transform: uppercase;
            text-align: center;
            opacity: 0;
            transform: translateY(30px);
            animation: textIn 1s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        @keyframes textIn {
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- 2. STILI PËR FAQEN KRYESORE (HOME PAGE) --- */
        body {
            margin: 0;
            padding: 0;
            /* Sfondi i kaltër i mbyllur luksoz (65% errësirë e thellë) */
            background-color: #0f1a2c; 
            font-family: 'Montserrat', sans-serif, system-ui;
            color: #ffffff;
            overflow-x: hidden;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
        }

        /* --- TITULLI ULTRA LUXURY --- */
        header {
            margin-top: 30px;
            margin-bottom: 50px;
            opacity: 0;
            transform: scale(0.95);
            /* Animacioni që fillon pasi mbaron splash screen */
            animation: titleLuxuryIn 1s cubic-bezier(0.25, 1, 0.5, 1) forwards;
            animation-delay: 2.2s; 
        }

        .main-title {
            margin: 0;
            font-size: 2.5rem;
            font-weight: 900;
            letter-spacing: 12px; /* Shkronja të ndara për stil luksoz */
            text-transform: uppercase;
            /* Gradient Ari i Pastër */
            background: linear-gradient(135deg, #f3caf6 0%, #d4af37 50%, #aa7c11 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0px 4px 20px rgba(212, 175, 55, 0.15);
        }

        @keyframes titleLuxuryIn {
            to { opacity: 1; transform: scale(1); }
        }

        /* --- KUTIA E KËRKIMIT (SEARCH BAR) --- */
        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(212, 175, 55, 0.3); /* Kornizë e lehtë ari */
            backdrop-filter: blur(10px);
            border-radius: 50px;
            padding: 6px 6px 6px 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            margin-bottom: 40px;
            transition: all 0.3s ease;
        }

        .search-box:focus-within {
            border-color: #d4af37;
            box-shadow: 0 10px 30px rgba(212, 175, 55, 0.2);
        }

        .search-box input {
            flex: 1;
            background: none;
            border: none;
            outline: none;
            color: #ffffff;
            font-size: 1.1rem;
            font-family: inherit;
        }

        .search-box input::placeholder {
            color: #94a3b8;
        }

        .search-box button {
            background: linear-gradient(135deg, #d4af37, #aa7c11);
            border: none;
            color: #0f1a2c;
            font-weight: bold;
            padding: 12px 30px;
            border-radius: 50px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: transform 0.2s;
        }

        .search-box button:hover {
            transform: scale(1.05);
        }

        /* --- STRUKTURA E REZULTATEVE TË KËRKIMIT --- */
        .results-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 20px;
            margin-top: 20px;
        }

        .business-card {
            background: rgba(255, 255, 255, 0.03);
            border-left: 4px solid #d4af37; /* Vijë ari anash */
            border-top: 1px solid rgba(255,255,255,0.05);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            border-right: 1px solid rgba(255,255,255,0.05);
            padding: 20px;
            border-radius: 12px;
            text-align: left;
            transition: transform 0.3s, background 0.3s;
        }

        .business-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.07);
        }

        .biz-name {
            font-size: 1.3rem;
            font-weight: 700;
            color: #ffffff;
            margin: 0 0 5px 0;
        }

        .biz-category {
            font-size: 0.85rem;
            text-transform: uppercase;
            color: #d4af37;
            letter-spacing: 1px;
            margin-bottom: 10px;
        }

        .biz-info {
            color: #cbd5e1;
            font-size: 0.95rem;
            margin: 5px 0;
        }

        .no-results {
            color: #94a3b8;
            font-style: italic;
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <!-- 1. SPLASH SCREEN -->
    <div id="splash-screen">
        <div class="splash-text">Welcome to Macedonia</div>
    </div>

    <!-- 2. FAQJA KRYESORE LUXURY -->
    <div class="container">
        <header>
            <h1 class="main-title">mkdmap</h1>
        </header>

        <!-- KUTIA E KËRKIMIT -->
        <div class="search-box">
            <input type="text" id="search-input" placeholder="What are you looking for? (e.g., mechanic, hotel, cafe)...">
            <button onclick="searchBusinesses()">Search</button>
        </div>

        <!-- VENDI KU SHFAQEN REZULTATET -->
        <div class="results-container" id="results-box">
            <!-- Bizneset do të gjirohen këtu automatikisht nga JavaScript -->
        </div>
    </div>

    <!-- 3. SCRIPTET (ANIMACIONI & DATABASE I BIZNESEVE) -->
    <script>
        // Animacioni i zhdukjes së Splash Screen pas 2 sekondave
        window.addEventListener("DOMContentLoaded", function() {
            setTimeout(function() {
                var splash = document.getElementById("splash-screen");
                splash.style.opacity = "0";
                setTimeout(function() {
                    splash.style.display = "none";
                }, 600); 
            }, 2000);
            
            // Shfaqim të gjitha bizneset në fillim automatikisht
            showBusinesses(businesses);
        });

        // "DATABASE" I TESTIMIT (Këtu mund të shtosh sa të duash më vonë)
        const businesses = [
            { name: "Luxury Villa Mavrovo", category: "villa hotel", phone: "+389 70 123 456", location: "Mavrovo", description: "Exclusive villa with mountain view and private pool." },
            { name: "Skopje Auto Mechanic Pro", category: "mechanik mekanik service", phone: "+389 71 999 888", location: "Skopje (Shkup)", description: "24/7 emergency car repair for tourists. English speaking." },
            { name: "SmartFix Phone Service", category: "mjeshter telefoni service repair", phone: "+389 75 444 333", location: "Skopje", description: "Express screen and battery repair for all smartphones." },
            { name: "Metropolitan Lounge & Cafe", category: "cafene kafiteri drink", phone: "+389 72 555 555", location: "Skopje Center", description: "The finest coffee and premium cocktails in the heart of Shkup." },
            { name: "Golden Fork Restaurant", category: "restorant restorante food", phone: "+389 78 777 666", location: "Ohrid", description: "Traditional Macedonian food and fresh lake fish with premium luxury service." },
            { name: "Oasis Luxury Pool & Spa", category: "pishina pool", phone: "+389 70 888 888", location: "Kumanovo", description: "An elite swimming pool resort for summer relaxation." }
        ];

        // Funksioni që i vizaton bizneset në ekran
        function showBusinesses(list) {
            const box = document.getElementById("results-box");
            box.innerHTML = ""; // e pastrojmë kutinë iher

            if(list.length === 0) {
                box.innerHTML = "<p class='no-results'>No premium businesses found matching your request. Try searching 'mechanic' or 'hotel'.</p>";
                return;
            }

            list.forEach(biz => {
                box.innerHTML += `
                    <div class="business-card">
                        <div class="biz-name">${biz.name}</div>
                        <div class="biz-category">📍 ${biz.location} | ${biz.category.split(' ')[0]}</div>
                        <div class="biz-info"><strong>Description:</strong> ${biz.description}</div>
                        <div class="biz-info"><strong>Phone:</strong> ${biz.phone}</div>
                    </div>
                `;
            });
        }

        // Funksioni i kërkimit inteligjent
        function searchBusinesses() {
            const query = document.getElementById("search-input").value.toLowerCase().trim();
            
            if(query === "") {
                showBusinesses(businesses); // Nëse është zbrazët kërkimi, shfaqi të gjitha
                return;
            }

            // Filtrojmë bizneset në bazë të asaj që shkruan turisti
            const filtered = businesses.filter(biz => {
                return biz.name.toLowerCase().includes(query) || 
                       biz.category.toLowerCase().includes(query) || 
                       biz.location.toLowerCase().includes(query) ||
                       biz.description.toLowerCase().includes(query);
            });

            showBusinesses(filtered);
        }

        // Mundësojmë që kërkimi të bëhet edhe duke shtypur butonin "Enter" në tastierë
        document.getElementById("search-input").addEventListener("keypress", function(event) {
            if (event.key === "Enter") {
                searchBusinesses();
            }
        });
    </script>
</body>
</html>
