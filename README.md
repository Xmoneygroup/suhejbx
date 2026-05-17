<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MkdMap - Ultra Luxury Multi-Language Directory</title>
    <style>
        /* --- 1. STILI PËR EKRANIN HYRËS (SPLASH SCREEN) --- */
        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #090d16;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 1;
            transition: opacity 0.5s ease;
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
            background-color: #0f1a2c; 
            font-family: 'Montserrat', sans-serif, system-ui;
            color: #ffffff;
            overflow-x: hidden;
        }

        #main-content {
            display: none; 
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
        }

        /* --- TITULLI ULTRA LUXURY --- */
        header {
            margin-top: 20px;
            margin-bottom: 20px;
            opacity: 0;
            transform: scale(0.95);
            animation: titleLuxuryIn 0.8s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        .main-title {
            margin: 0;
            font-size: 2.5rem;
            font-weight: 900;
            letter-spacing: 12px;
            background: linear-gradient(135deg, #f3caf6 0%, #d4af37 50%, #aa7c11 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0px 4px 20px rgba(212, 175, 55, 0.15);
        }

        @keyframes titleLuxuryIn {
            to { opacity: 1; transform: scale(1); }
        }

        /* --- SELEKTORI I GJUHËVE --- */
        .lang-container {
            margin-bottom: 40px;
        }

        .lang-select {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(212, 175, 55, 0.3);
            color: #ffffff;
            padding: 8px 15px;
            border-radius: 20px;
            font-family: inherit;
            font-size: 0.9rem;
            cursor: pointer;
            outline: none;
            transition: all 0.3s ease;
        }

        .lang-select:hover, .lang-select:focus {
            border-color: #d4af37;
            background: rgba(255, 255, 255, 0.1);
        }

        .lang-select option {
            background-color: #0f1a2c;
            color: #ffffff;
        }

        /* --- KUTIA E KËRKIMIT (SEARCH BAR) --- */
        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(212, 175, 55, 0.3);
            backdrop-filter: blur(10px);
            border-radius: 50px;
            padding: 6px 6px 6px 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            margin-bottom: 40px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
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

        /* --- REZULTATET --- */
        .results-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }

        .business-card {
            background: rgba(255, 255, 255, 0.03);
            border-left: 4px solid #d4af37;
            border-top: 1px solid rgba(255,255,255,0.05);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            border-right: 1px solid rgba(255,255,255,0.05);
            padding: 25px;
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
            margin-bottom: 15px;
        }

        .biz-info {
            color: #cbd5e1;
            font-size: 0.95rem;
            margin: 8px 0;
            line-height: 1.4;
        }

        .no-results {
            color: #94a3b8;
            font-style: italic;
            margin-top: 30px;
            grid-column: 1 / -1;
        }

        @media (max-width: 480px) {
            .main-title { font-size: 2rem; letter-spacing: 8px; }
            .search-box { padding: 4px 4px 4px 15px; }
            .search-box button { padding: 10px 20px; font-size: 0.9rem; }
        }
    </style>
</head>
<body>

    <!-- 1. SPLASH SCREEN -->
    <div id="splash-screen">
        <div class="splash-text">Welcome to Macedonia</div>
    </div>

    <!-- 2. FAQJA KRYESORE -->
    <div id="main-content">
        <div class="container">
            <header>
                <h1 class="main-title">mkdmap</h1>
            </header>

            <!-- SELEKTORI I GJUHËS -->
            <div class="lang-container">
                <select class="lang-select" id="language-picker" onchange="changeLanguage()">
                    <option value="en">🌐 Language: English (EN)</option>
                    <option value="sq">🌐 Language: Shqip (SQ)</option>
                    <option value="mk">🌐 Language: Maqedonisht (MK)</option>
                </select>
            </div>

            <!-- KUTIA E KËRKIMIT -->
            <div class="search-box">
                <input type="text" id="search-input" placeholder="What are you looking for? (e.g., mechanic, hotel, cafe)...">
                <button id="search-btn" onclick="searchBusinesses()">Search</button>
            </div>

            <!-- REZULTATET -->
            <div class="results-container" id="results-box">
                <!-- Mbushen nga JS -->
            </div>
        </div>
    </div>

    <script>
        // Ruajmë gjuhën aktuale (në fillim është Anglisht 'en')
        let currentLang = 'en';

        window.addEventListener("DOMContentLoaded", function() {
            showBusinesses(businesses);

            setTimeout(function() {
                var splash = document.getElementById("splash-screen");
                var mainContent = document.getElementById("main-content");
                
                splash.style.opacity = "0";
                mainContent.style.display = "block";
                
                setTimeout(function() {
                    splash.style.display = "none";
                }, 500); 
            }, 2000);
        });

        // FIKS ÇFARË KËRKUAT: Bizneset tani kanë përkthime për EN, SQ dhe MK
        const businesses = [
            {
                phone: "+389 70 123 456",
                tags: "villa hotel vilë vila вила хотел",
                en: { name: "Luxury Villa Mavrovo", location: "Mavrovo", desc: "Exclusive villa with mountain view and private pool.", labelDesc: "Description", labelPhone: "Phone" },
                sq: { name: "Vila Luksoze Mavrovë", location: "Mavrovë", desc: "Vilë ekskluzive me pamje nga mali dhe pishinë private.", labelDesc: "Përshkrimi", labelPhone: "Telefoni" },
                mk: { name: "Луксузна Вила Маврово", location: "Маврово", desc: "Ексклузивна вила со поглед на планина и приватен базен.", labelDesc: "Опис", labelPhone: "Телефон" }
            },
            {
                phone: "+389 71 999 888",
                tags: "mechanik mekanik service auto авто механичар",
                en: { name: "Skopje Auto Mechanic Pro", location: "Skopje", desc: "24/7 emergency car repair for tourists. English speaking.", labelDesc: "Description", labelPhone: "Phone" },
                sq: { name: "Mekanik Auto Pro Shkup", location: "Shkup", desc: "Riparim urgjent i makinave 24/7 për turistët. Flasim Shqip dhe Anglisht.", labelDesc: "Përshkrimi", labelPhone: "Telefoni" },
                mk: { name: "Авто Механичар Про Скопје", location: "Скопје", desc: "24/7 итна поправка на автомобили за туристи. Зборуваме англиски.", labelDesc: "Опис", labelPhone: "Телефон" }
            },
            {
                phone: "+389 75 444 333",
                tags: "mjeshter telefoni service repair сервис мобилни",
                en: { name: "SmartFix Phone Service", location: "Skopje", desc: "Express screen and battery repair for all smartphones.", labelDesc: "Description", labelPhone: "Phone" },
                sq: { name: "Servis Telefonash SmartFix", location: "Shkup", desc: "Riparim i shpejtë i ekranit dhe baterisë për të gjithë smartfonët.", labelDesc: "Përshkrimi", labelPhone: "Telefoni" },
                mk: { name: "Сервис за Мобилни SmartFix", location: "Скопје", desc: "Експресна поправка на екрани и батерии за сите смартфони.", labelDesc: "Опис", labelPhone: "Телефон" }
            }
        ];

        // Funksioni që shfaq bizneset në bazë të gjuhës së zgjedhur (currentLang)
        function showBusinesses(list) {
            const box = document.getElementById("results-box");
            box.innerHTML = "";

            if(list.length === 0) {
                let noResultText = "No premium businesses found.";
                if(currentLang === 'sq') noResultText = "Nuk u gjet asnjë biznes premium.";
                if(currentLang === 'mk') noResultText = "Не се пронајдени премиум бизниси.";
                
                box.innerHTML = `<p class='no-results'>${noResultText}</p>`;
                return;
            }

            list.forEach(biz => {
                // Marrim fiks përkthimin që na duhet tani (en, sq apo mk)
                const data = biz[currentLang]; 

                box.innerHTML += `
                    <div class="business-card">
                        <div class="biz-name">${data.name}</div>
                        <div class="biz-category">📍 ${data.location}</div>
                        <div class="biz-info"><strong>${data.labelDesc}:</strong> ${data.desc}</div>
                        <div class="biz-info"><strong>${data.labelPhone}:</strong> ${biz.phone}</div>
                    </div>
                `;
            });
        }

        // Ndryshimi i gjuhës nga menuja
        function changeLanguage() {
            // Përditësojmë gjuhën globale
            currentLang = document.getElementById("language-picker").value;
            
            const input = document.getElementById("search-input");
            const btn = document.getElementById("search-btn");
            
            // Ndryshojmë tekstet e kërkimit sipas gjuhës
            if(currentLang === "sq") {
                input.placeholder = "Çfarë po kërkoni? (psh., mekanik, vilë, servis)...";
                btn.innerText = "Kërko";
            } else if(currentLang === "mk") {
                input.placeholder = "Што барате? (на пр. механичар, вила, сервис)...";
                btn.innerText = "Пребарај";
            } else {
                input.placeholder = "What are you looking for? (e.g., mechanic, villa, cafe)...";
                btn.innerText = "Search";
            }

            // RI-SHFAQIM BIZNESET DIREKT ME GJUHËN E RE!
            searchBusinesses(); 
        }

        // Funksioni i kërkimit (punon në të gjitha gjuhët njëkohësisht)
        function searchBusinesses() {
            const query = document.getElementById("search-input").value.toLowerCase().trim();
            
            if(query === "") {
                showBusinesses(businesses);
                return;
            }

            const filtered = businesses.filter(biz => {
                // Kërkon te emrat në anglisht, shqip, maqedonisht dhe tek fjalët kyçe (tags)
                return biz.en.name.toLowerCase().includes(query) || 
                       biz.sq.name.toLowerCase().includes(query) || 
                       biz.mk.name.toLowerCase().includes(query) || 
                       biz.tags.includes(query);
            });

            showBusinesses(filtered);
        }

        document.getElementById("search-input").addEventListener("keypress", function(event) {
            if (event.key === "Enter") {
                searchBusinesses();
            }
        });
    </script>
</body>
</html>
