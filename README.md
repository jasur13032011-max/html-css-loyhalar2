# html-css-loyhalar2
![Uploading Gemini_Generated_Image_uspi70uspi70uspi.png…]()
CSS position xususiyatlari (sticky, relative, absolute, fixed) va z-index qatlamlarini to'g'ri boshqarish mukammal interfeys yaratishning asosidir.

Siz so'ragan barcha talablar (kartochkalar, nishonlar/badglar, yuqoriga chiqish tugmasi va silliq harakatlanish) to'liq qamrab olingan, real loyihalarda ishlatishga tayyor kod taqdim etiladi.

HTML va CSS Kodu
HTML
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Positioning va Qatlamlar</title>
  <style>
    /* Silliq skroll (Smooth Scroll) ta'minlash */
    html {
      scroll-behavior: smooth;
    }

    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Segoe UI', system-ui, sans-serif;
      background-color: #f1f5f9;
      color: #1e293b;
      padding-bottom: 100px; /* Sahifa pastida joy qolishi uchun */
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }

    /* ==========================================
       1. STICKY NAVBAR (Tepada yopishib qoluvchi)
       ========================================== */
    .navbar {
      position: sticky;
      top: 0;
      /* z-index: 100 - boshqa barcha elementlardan ustida turishini ta'minlaydi */
      z-index: 100; 
      background-color: #ffffff;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
      padding: 15px 0;
    }

    .nav-container {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-links {
      display: flex;
      gap: 20px;
      list-style: none;
    }

    .nav-links a {
      text-decoration: none;
      color: #475569;
      font-weight: 500;
      transition: color 0.2s ease; /* Transition effekti */
    }

    .nav-links a:hover {
      color: #2563eb;
    }

    /* Bo'sh joy yaratish uchun kontent bloki */
    .hero-section {
      padding: 60px 0 30px;
      text-align: center;
    }

    /* ==========================================
       2. KARTОCHKALAR TARMOQCHASI (Grid)
       ========================================== */
    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
      margin-top: 40px;
    }

    /* Parent element: position: relative */
    .card {
      position: relative;
      background-color: #ffffff;
      padding: 30px 20px;
      border-radius: 12px;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
      border: 1px solid #e2e8f0;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    /* Kartochka hover bo'lganda yuqoriga biroz ko'tariladi */
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
    }

    .card h3 {
      margin-top: 15px;
      margin-bottom: 10px;
    }

    /* ==========================================
       3. ABSOLUTE BADGE (Nishon) VA TOOLTIP
       ========================================== */
    /* Kartochka burchagidagi nishon (Badge) */
    .card-badge {
      position: absolute;
      top: 15px;
      right: 15px;
      background-color: #ef4444; /* Qizil */
      color: white;
      font-size: 12px;
      font-weight: 700;
      padding: 4px 10px;
      border-radius: 20px;
      text-transform: uppercase;
    }

    .badge-popular {
      background-color: #10b981; /* Yashil */
    }

    /* Yashirin Tooltip konteyneri */
    .info-icon {
      display: inline-block;
      background-color: #cbd5e1;
      color: #475569;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      text-align: center;
      line-height: 20px;
      font-size: 12px;
      cursor: help;
      position: relative; /* Tooltip uchun ikkinchi darajali parent */
    }

    /* Hover bo'lganda chiquvchi tooltip matni */
    .info-icon::after {
      content: "Ushbu kurs sertifikat bilan ta'minlanadi.";
      position: absolute;
      bottom: 125%; /* Ikonkadan tepada turishi uchun */
      left: 50%;
      transform: translateX(-50%) scale(0.8);
      background-color: #1e293b;
      color: #ffffff;
      padding: 6px 12px;
      border-radius: 6px;
      font-size: 12px;
      white-space: nowrap;
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.2s ease, transform 0.2s ease;
      z-index: 10; /* Kartochka matnlaridan ustun turishi shart */
    }

    /* Ikonkaga sichqoncha kelganda Tooltip ko'rinishi */
    .info-icon:hover::after {
      opacity: 1;
      visibility: visible;
      transform: translateX(-50%) scale(1);
    }

    /* Sun'iy uzun kontent (Skroll hosil qilish uchun) */
    .spacer {
      height: 800px;
    }

    /* ==========================================
       4. FIXED 'YUQORIGA' TUGMASI
       ========================================== */
    .scroll-top-btn {
      position: fixed;
      bottom: 30px;
      right: 30px;
      /* z-index: 90 - navbardan (100) pastroq, lekin kontentdan ustun */
      z-index: 90; 
      background-color: #2563eb;
      color: #ffffff;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      border: none;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      box-shadow: 0 4px 10px rgba(37, 99, 235, 0.3);
      text-decoration: none;
      transition: background-color 0.2s ease, transform 0.2s ease;
    }

    .scroll-top-btn:hover {
      background-color: #1d4ed8;
      transform: translateY(-3px);
    }
  </style>
</head>
<body>

  <div id="top"></div>

  <nav class="navbar">
    <div class="container nav-container">
      <h2>Akademiya</h2>
      <ul class="nav-links">
        <li><a href="#top">Bosh sahifa</a></li>
        <li><a href="#courses">Kurslar</a></li>
        <li><a href="#about">Biz haqimizda</a></li>
      </ul>
    </div>
  </nav>

  <main class="container">
    <section class="hero-section">
      <h1>Zamonaviy Kasblarni Biz Bilan O'rganing</h1>
      <p>Position xususiyatlari yordamida joylashtirilgan interaktiv komponentlar</p>
    </section>

    <section id="courses" class="card-grid">
      
      <div class="card">
        <span class="card-badge">Yangi</span>
        <h3>Frontend Dasturlash</h3>
        <p>HTML, CSS, JavaScript va React texnologiyalarini noldan o'rganing. <span class="info-icon">i</span></p>
      </div>

      <div class="card">
        <span class="card-badge badge-popular">Top</span>
        <h3>Python Backend</h3>
        <p>Django va FastAPI frameworklarida kuchli tizimlar yaratishni o'rganing. <span class="info-icon">i</span></p>
      </div>

      <div class="card">
        <h3>UI/UX Dizayn</h3>
        <p>Figma dasturida zamonaviy veb-sayt va mobil ilovalar dizaynini yarating. <span class="info-icon">i</span></p>
      </div>

    </section>

    <div class="spacer" id="about"></div>
  </main>

  <a href="#top" class="scroll-top-btn" aria-label="Yuqoriga chiqish">↑</a>

</body>
</html>
Kod mantiqi qanday ishlaydi?
position: sticky (Navbar): top: 0 berilgani sababli, foydalanuvchi sahifani pastga surganida, menyu oynaning eng tepasiga yetganda qotib qoladi.

position: relative va absolute (Kartochka va Nishon): .card elementiga relative berildi, uning ichidagi .card-badgega esa absolute berildi. Bu nishonni kartochkaning aynan o'ng yuqori burchagidan (top: 15px, right: 15px) siljimay turishini kafolatlaydi.

Tooltip: Har bir i harfli aylananing ustiga sichqoncha kelganda (:hover), uning ::after psevdo-elementi opacity: 1 holatiga kelib, silliq (transition orqali) ko'rinadi.

position: fixed (Yuqoriga tugmasi): Bu tugma butun veb-sahifaning koordinatalariga bog'lanadi. Skroll qilinishidan qat'i nazar, ekranning o'ng pastki qismida (bottom: 30px, right: 30px) har doim bir joyda qotib turadi.

scroll-behavior: smooth: CSS-ning eng yuqori qismida html elementiga berilgan ushbu xossa fixed tugma bosilganda sahifani keskin emas, balki silliq (smooth) tarzda tepaga aylantirib beradi.
