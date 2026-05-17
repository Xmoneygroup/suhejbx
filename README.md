<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MkdMap - Global Luxury Directory</title>
    <!-- Fusim fontin Montserrat për stil luksoz -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        /* --- 1. STILI PËR EKRANIN HYRËS (SPLASH SCREEN) --- */
        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #060911;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 1;
            transition: opacity 0.6s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .splash-text {
            color: #ffffff;
            font-family: 'Montserrat', sans-serif;
            font-size: 2.2rem;
            font-weight: 300; /* Shkronja më elegante dhe të bukura */
            text-transform: uppercase;
            text-align: center;
            white-space: nowrap;
            letter-spacing: -5px; /* Nis me shkronja të mbledhura */
            opacity: 0;
            /* Animacioni horizontal dhe shfaqja graduale */
            animation: textSpreadIn 1.5s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        @keyframes textSpreadIn {
            to { 
                opacity: 1; 
                letter-spacing: 6px; /* Shkronjat hapen horizontalisht */
            }
        }

        /* --- 2. STILI I RI UNIK I HOME PAGE --- */
        body {
            margin: 0;
            padding: 0;
            background: radial-gradient(circle at top, #111a2e 0%, #050811 100%);
            font-family: 'Montserrat', sans-serif;
            color: #f8fafc;
            overflow-x: hidden;
            min-height: 100vh;
        }

        #main-content {
            display: none; 
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 20px;
            text-align: center;
        }

        /* --- TITULLI ULTRA LUXURY --- */
        header {
            margin-top: 10px;
            margin-bottom: 25px;
            opacity: 0;
            transform: translateY(-20px);
            animation: titleLuxuryIn 1s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        .main-title {
            margin: 0;
            font-size: 3.5rem;
            font-weight: 900;
            letter-spacing: 16px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #fff 30%, #d4af37 70%, #aa7c11 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0px 4px 15px rgba(212, 175, 55, 0.2));
        }

        @keyframes titleLuxuryIn {
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- SELEKTORI MODERN I GJUHËVE (50 GJUHË) --- */
        .lang-container {
            margin-bottom: 50px;
        }

        .lang-select {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(212, 175, 55, 0.2);
            color: #cbd5e1;
            padding: 10px 20px;
            border-radius: 30px;
            font-family: inherit;
            font-size: 0.85rem;
            letter-spacing: 1px;
            cursor: pointer;
            outline: none;
            transition: all 0.4s ease;
            backdrop-filter: blur(10px);
        }

        .lang-select:hover, .lang-select:focus {
            border-color: #d4af37;
            background: rgba(212, 175, 55, 0.08);
            color: #ffffff;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.1);
        }

        .lang-select option {
            background-color: #090d16;
            color: #ffffff;
        }

        /* --- KUTIA E KËRKIMIT DIZAJN MINIMALIST --- */
        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
            border-radius: 100px;
            padding: 8px 8px 8px 25px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
            margin-bottom: 60px;
            max-width: 650px;
            margin-left: auto;
            margin-right: auto;
            transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .search-box:focus-within {
            border-color: rgba(212, 175, 55, 0.5);
            background: rgba(255, 255, 255, 0.04);
            box-shadow: 0 20px 40px rgba(212, 175, 55, 0.05), 0 0 30px rgba(212, 175, 55, 0.05);
        }

        .search-box input {
            flex: 1;
            background: none;
            border: none;
            outline: none;
            color: #ffffff;
            font-size: 1.05rem;
            font-family: inherit;
            letter-spacing: 0.5px;
        }

        .search-box input::placeholder {
            color: #64748b;
        }

        .search-box button {
            background: #ffffff;
            border: none;
            color: #050811;
            font-weight: 700;
            padding: 14px 35px;
            border-radius: 100px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            font-size: 0.85rem;
            transition: all 0.3s ease;
        }

        .search-box button:hover {
            background: linear-gradient(135deg, #d4af37, #aa7c11);
            color: #ffffff;
            transform: scale(1.02);
        }

        /* --- ANIMACIONI I PLLAKATAVE --- */
        .results-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 30px;
            margin-top: 20px;
        }

        .business-card {
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(255, 255, 255, 0.04);
            padding: 30px;
            border-radius: 20px;
            text-align: left;
            position: relative;
            overflow: hidden;
            transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1), 
                        background 0.4s ease, 
                        border-color 0.4s ease, 
                        box-shadow 0.4s ease;
        }

        .business-card:hover {
            transform: translateY(-8px);
            background: rgba(255, 255, 255, 0.03);
            border-color: rgba(212, 175, 55, 0.3);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5), 0 0 25px rgba(212, 175, 55, 0.05);
        }

        .business-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, #d4af37, #aa7c11);
            transform: scaleX(0);
            transition: transform 0.4s ease;
        }
        .business-card:hover::before {
            transform: scaleX(1);
        }

        .biz-name {
            font-size: 1.4rem;
            font-weight: 700;
            color: #ffffff;
            margin: 0 0 12px 0;
            letter-spacing: 0.5px;
        }

        .biz-desc {
            color: #94a3b8;
            font-size: 0.95rem;
            margin: 0 0 25px 0;
            line-height: 1.6;
            font-weight: 300;
        }

        /* --- FOOTER-I I KARTELËS --- */
        .biz-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            padding-top: 15px;
            margin-top: auto;
            font-size: 0.85rem;
        }

        /* Stilet e reja për vegëzat që të mos duken si linja të thjeshta tekstesh */
        .biz-loc-link, .biz-phone-link {
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .biz-loc {
            color: #d4af37;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 5px;
            letter-spacing: 0.5px;
        }
        
        .biz-loc-link:hover .biz-loc {
            color: #ffffff;
            text-shadow: 0 0 10px rgba(212, 175, 55, 0.6);
        }

        .biz-phone {
            color: #cbd5e1;
            font-weight: 400;
            display: flex;
            align-items: center;
            gap: 5px;
            background: rgba(255, 255, 255, 0.04);
            padding: 5px 14px;
            border-radius: 30px;
            border: 1px solid rgba(255, 255, 255, 0.02);
        }

        .biz-phone-link:hover .biz-phone {
            background: rgba(212, 175, 55, 0.15);
            color: #ffffff;
            border-color: #d4af37;
        }

        .no-results {
            color: #64748b;
            font-style: italic;
            margin-top: 30px;
            grid-column: 1 / -1;
        }

        @media (max-width: 480px) {
            .main-title { font-size: 2.2rem; letter-spacing: 10px; }
            .search-box { padding: 5px 5px 5px 18px; margin-bottom: 40px; }
            .search-box button { padding: 12px 22px; font-size: 0.8rem; }
            .results-container { grid-template-columns: 1fr; gap: 20px; }
            .biz-footer { flex-direction: row; font-size: 0.8rem; }
        }
    </style>
</head>
<body>

    <!-- 1. SPLASH SCREEN -->
    <div id="splash-screen">
        <div class="splash-text">Welcome to Macedonia</div>
    </div>

    <!-- 2. HOME PAGE UNIQUE DESIGN -->
    <div id="main-content">
        <div class="container">
            <header>
                <h1 class="main-title">mkdmap</h1>
            </header>

            <!-- SELEKTORI ME 50 GJUHË TË NDRYSHME -->
            <div class="lang-container">
                <select class="lang-select" id="language-picker" onchange="changeLanguage()">
                    <option value="en"> English (EN)</option>
                    <option value="sq"> Shqip (SQ)</option>
                    <option value="mk"> Maqedonisht (MK)</option>
                    <option value="sr"> Srpski (SR)</option>
                    <option value="tr"> Türkçe (TR)</option>
                    <option value="de"> Deutsch (DE)</option>
                    <option value="ru"> Русский (RU)</option>
                    <option value="fr"> Français (FR)</option>
                    <option value="it"> Italiano (IT)</option>
                    <option value="es"> Español (ES)</option>
                    <option value="el"> Ελληνικά (EL)</option>
                    <option value="bg"> Български (BG)</option>
                    <option value="ro"> Română (RO)</option>
                    <option value="pl"> Polski (PL)</option>
                    <option value="nl"> Nederlands (NL)</option>
                    <option value="pt"> Português (PT)</option>
                    <option value="sv"> Svenska (SV)</option>
                    <option value="no"> Norsk (NO)</option>
                    <option value="da"> Dansk (DA)</option>
                    <option value="fi"> Suomi (FI)</option>
                    <option value="cs"> Čeština (CS)</option>
                    <option value="hu"> Magyar (HU)</option>
                    <option value="uk"> Українська (UK)</option>
                    <option value="hr"> Hrvatski (HR)</option>
                    <option value="bs"> Bosanski (BS)</option>
                    <option value="sl"> Slovenščina (SL)</option>
                    <option value="sk"> Slovenčina (SK)</option>
                    <option value="lt"> Lietuvių (LT)</option>
                    <option value="lv"> Latviešu (LV)</option>
                    <option value="et"> Eesti (ET)</option>
                    <option value="zh"> 中文 (ZH)</option>
                    <option value="ja"> 日本語 (JA)</option>
                    <option value="ko"> 한국어 (KO)</option>
                    <option value="ar"> العربية (AR)</option>
                    <option value="he"> עבריtext (HE)</option>
                    <option value="hi"> हिन्दी (HI)</option>
                    <option value="id"> Bahasa Indonesia (ID)</option>
                    <option value="ms"> Bahasa Melayu (MS)</option>
                    <option value="th"> ไทย (TH)</option>
                    <option value="vi"> Tiếng Việt (VI)</option>
                    <option value="fa"> فارسی (FA)</option>
                    <option value="ur"> اردو (UR)</option>
                    <option value="bn"> বাংলা (BN)</option>
                    <option value="pa"> ਪੰਜਾਬੀ (PA)</option>
                    <option value="ka"> ქართული (KA)</option>
                    <option value="hy"> Հայերեն (HY)</option>
                    <option value="az"> Azərbaycanca (AZ)</option>
                    <option value="sq_AL"> Shqip Kosovë (SQ-KS)</option>
                    <option value="la"> Latina (LA)</option>
                    <option value="af"> Afrikaans (AF)</option>
                </select>
            </div>

            <!-- KUTIA E KËRKIMIT -->
            <div class="search-box">
                <input type="text" id="search-input" placeholder="What are you looking for? (e.g., mechanic, hotel, villa)...">
                <button id="search-btn" onclick="searchBusinesses()">Search</button>
            </div>

            <!-- ZONA E REZULTATEVE -->
            <div class="results-container" id="results-box">
                <!-- Mbushet dinamikisht nga JS -->
            </div>
        </div>
    </div>

    <script>
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
                }, 600); 
            }, 2500); // Pak më shumë kohë që të dallohet animacioni i bukur horizontal
        });

        // DATABASE ME PËRKTHIME DHE LOKACIONET NGA GOOGLE MAPS
        const businesses = [
            {
                phone: "+38970123456", // Numri i pastër për thirrje direkte
                phoneDisplay: "+389 70 123 456",
                mapUrl: "https://maps.google.com/?q=Mavrovo+Lake", // Linku i Google Maps
                tags: "villa hotel vilë vila вила хотел",
                en: { name: "Luxury Villa Mavrovo", location: "Mavrovo", desc: "Exclusive villa with mountain view and private pool." },
                sq: { name: "Vila Luksoze Mavrovë", location: "Mavrovë", desc: "Vilë ekskluzive me pamje spektakolare nga mali dhe pishinë private." },
                mk: { name: "Луксузна Вила Маврово", location: "Маврово", desc: "Ексклузивна вила со прекрасен поглед на планина и приватен базен." }
            },
            {
                phone: "+38971999888",
                phoneDisplay: "+389 71 999 888",
                mapUrl: "https://maps.google.com/?q=Skopje+Center",
                tags: "mechanik mekanik service auto авто механичар",
                en: { name: "Skopje Auto Mechanic Pro", location: "Skopje", desc: "24/7 emergency car repair for tourists. English speaking support." },
                sq: { name: "Mekanik Auto Pro Shkup", location: "Shkup", desc: "Riparim urgjent i makinave 24/7 për turistët dhe vendasit. Flasim Shqip." },
                mk: { name: "Авто Механичар Про Скопје", location: "Скопје", desc: "24/7 итна поправка на возила за туристи. Зборуваме англиски и германски." }
            },
            {
                phone: "+38975444333",
                phoneDisplay: "+389 75 444 333",
                mapUrl: "https://maps.google.com/?q=City+Mall+Skopje",
                tags: "mjeshter telefoni service repair сервис mobilni",
                en: { name: "SmartFix Phone Service", location: "Skopje", desc: "Express screen and battery repair for all premium smartphones." },
                sq: { name: "Servis Telefonash SmartFix", location: "Shkup", desc: "Riparim i shpejtë dhe i garantuar i ekranit dhe baterisë për smartfonë." },
                mk: { name: "Сервис за Мобилни SmartFix", location: "Скопје", desc: "Брза и квалитетна поправка на екрани и батерии за сите смартфони." }
            }
        ];

        function showBusinesses(list) {
            const box = document.getElementById("results-box");
            box.innerHTML = "";

            if(list.length === 0) {
                let noResultText = "No businesses found.";
                if(currentLang === 'sq') noResultText = "Nuk u gjet asnjë biznes.";
                if(currentLang === 'mk') noResultText = "Не се пронајдени бизниси.";
                box.innerHTML = `<p class='no-results'>${noResultText}</p>`;
                return;
            }

            list.forEach(biz => {
                const data = biz[currentLang] || biz['en']; 

                box.innerHTML += `
                    <div class="business-card">
                        <div class="biz-name">${data.name}</div>
                        <p class="biz-desc">${data.desc}</p>
                        
                        <div class="biz-footer">
                            <!-- Vegëza për hapjen e lokacionit direkt në Google Maps -->
                            <a href="${biz.mapUrl}" target="_blank" class="biz-loc-link" title="Open in Google Maps">
                                <span class="biz-loc">📍 ${data.location}</span>
                            </a>
                            <!-- Vegëza 'tel:' për thirrje të menjëhershme nga celulari -->
                            <a href="tel:${biz.phone}" class="biz-phone-link">
                                <span class="biz-phone">📞 ${biz.phoneDisplay}</span>
                            </a>
                        </div>
                    </div>
                `;
            });
        }

        function changeLanguage() {
            currentLang = document.getElementById("language-picker").value;
            const input = document.getElementById("search-input");
            const btn = document.getElementById("search-btn");
            
            if(currentLang === "sq" || currentLang === "sq_AL") {
                input.placeholder = "Çfarë po kërkoni? (psh., mekanik, vilë, servis)...";
                btn.innerText = "Kërko";
            } else if(currentLang === "mk") {
                input.placeholder = "Што барате? (на пр. механичар, вила, сервис)...";
                btn.innerText = "Пребарај";
            } else if(currentLang === "sr") {
                input.placeholder = "Šta tražite? (npr. mehaničar, vila, kafić)...";
                btn.innerText = "Traži";
            } else if(currentLang === "tr") {
                input.placeholder = "Ne arıyorsunuz? (örn. tamirci, villa, otel)...";
                btn.innerText = "Ara";
            } else if(currentLang === "de") {
                input.placeholder = "Was suchen Sie? (z.B. Mechaniker, Villa)...";
                btn.innerText = "Suche";
            } else {
                input.placeholder = "What are you looking for? (e.g., mechanic, villa, cafe)...";
                btn.innerText = "Search";
            }

            searchBusinesses(); 
        }

        function searchBusinesses() {
            const query = document.getElementById("search-input").value.toLowerCase().trim();
            
            if(query === "") {
                showBusinesses(businesses);
                return;
            }

            const filtered = businesses.filter(biz => {
                return (biz.en && biz.en.name.toLowerCase().includes(query)) || 
                       (biz.sq && biz.sq.name.toLowerCase().includes(query)) || 
                       (biz.mk && biz.mk.name.toLowerCase().includes(query)) || 
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
