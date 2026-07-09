# html-css-loyhalar2
Taqdim etilgan talablar boʻyicha sahifaning strukturaviy maketi (layout) tayyorlandi. Bu yerda CSS Box Model qoidalariga rioya qilingan va veb-sahifa har qanday ekran oʻlchamida toza va tartibli koʻrinishi uchun moslashuvchan (responsive) qilib tuzilgan.

CSS va HTML Kodu
HTML
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Box Model Layout</title>
  <style>
    /* 1. Global ravishda box-sizing: border-box qo'llash */
    /* Bu padding va border elementning umumiy o'lchamiga ta'sir qilmasligini ta'minlaydi */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: sans-serif;
      background-color: #f4f6f9;
      color: #333;
      line-height: 1.6;
    }

    /* 2. max-width: 1200px va markazlashtirish */
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 15px; /* Kichik ekranlar uchun chekka qismlarda joy qoldiradi */
    }

    /* 3. Har bir bo'lim uchun umumiy padding, border va margin */
    .box {
      padding: 20px;
      border: 2px solid #ccc;
      margin-bottom: 20px;
      border-radius: 6px;
    }

    /* 4. Background-color orqali bo'limlarni aniq ajratish */
    .header {
      background-color: #1e3a8a; /* To'q ko'k */
      color: white;
      border-color: #1d4ed8;
    }

    /* Main ichidagi ustunlarni yonma-yon qilish uchun Flexbox */
    .main {
      background-color: #ffffff; /* Oq fon */
      border-color: #e5e7eb;
      display: flex;
      gap: 20px;
      flex-wrap: wrap; /* Kichik ekranlarda ustunlar pastga tushadi */
    }

    /* Ustunlar uchun umumiy uslub */
    .col {
      padding: 15px;
      border: 1px solid #cbd5e1;
      border-radius: 4px;
      flex: 1; /* Ustunlar teng joy egallaydi */
      min-width: 250px; /* Telefonlarda ustun bir qatorni to'liq egallashi uchun */
    }

    /* Ustunlarni alohida ranglar bilan ajratish */
    .left-col {
      background-color: #eff6ff; /* Och ko'k */
    }

    .center-col {
      background-color: #f0fdf4; /* Och yashil */
      flex: 2; /* Markaziy ustun kengroq bo'ladi */
    }

    .right-col {
      background-color: #fff7ed; /* Och jigarrang/sariq */
    }

    .footer {
      background-color: #334155; /* To'q kulrang */
      color: white;
      border-color: #1e293b;
      text-align: center;
      margin-bottom: 0; /* Eng oxirgi element bo'lgani uchun */
    }
  </style>
</head>
<body>

  <div class="container">

    <div class="header box">
      <h1>Veb-sahifa sarlavhasi (.header)</h1>
    </div>

    <div class="main box">
      
      <div class="left-col col">
        <h3>Chap ustun (.left-col)</h3>
        <p>Bu yerda yon menyu yoki qo'shimcha havolalar joylashishi mumkin.</p>
      </div>

      <div class="center-col col">
        <h2>Asosiy kontent (.center-col)</h2>
        <p>Sahifaning eng muhim ma'lumotlari shu yerda aks etadi. Bu ustun boshqalariga qaraganda kengroq qilib sozlangan.</p>
      </div>

      <div class="right-col col">
        <h3>O'ng ustun (.right-col)</h3>
        <p>Bu yerda reklama bloklari yoki vidjetlar joylashishi mumkin.</p>
      </div>

    </div>

    <div class="footer box">
      <p>Mualliflik huquqlari himoyalangan &copy; 2026 (.footer)</p>
    </div>

  </div>

</body>
</html>
Kodning muhim jihatlari:
box-sizing: border-box: Agar bu berilmaganda, har bir .box va .col elementiga qo'shilgan padding va border ularning kengligini kattalashtirib, maketning buzilishiga olib kelardi.
Flexbox va Media Query yordamida zamonaviy, to'liq moslashuvchan (responsive) Navigatsiya paneli (Navbar) va Hero bo'limi kodi:

HTML va CSS Kodu
HTML
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flexbox va Responsive Layout</title>
  <style>
    /* Global reset va border-box */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f8fafc;
      color: #1e293b;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }

    /* ==========================================
       NAVBAR USLUBLARI
       ========================================== */
    .header {
      background-color: #ffffff;
      box-shadow: 0 2px 4px rgba(0,0,0,0.05);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    /* Logo + Links + CTA guruhini space-between va markazlash orqali tekislash */
    .nav-container {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 0;
    }

    .logo {
      font-size: 24px;
      font-weight: 700;
      color: #2563eb;
      text-decoration: none;
    }

    .nav-links {
      display: flex;
      list-style: none;
      gap: 30px; /* Masofa uchun margin emas, gap ishlatildi */
    }

    .nav-links a {
      text-decoration: none;
      color: #64748b;
      font-weight: 500;
      transition: color 0.3s ease, transform 0.2s ease;
      display: inline-block;
    }

    /* Hover effekti */
    .nav-links a:hover {
      color: #2563eb;
      transform: translateY(-2px);
    }

    /* Call To Action (CTA) tugmasi */
    .cta-btn {
      background-color: #2563eb;
      color: #ffffff;
      padding: 10px 20px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: 600;
      transition: background-color 0.3s ease;
    }

    .cta-btn:hover {
      background-color: #1d4ed8;
    }


    /* ==========================================
       HERO BO'LIMI USLUBLARI
       ========================================== */
    .hero {
      padding: 60px 0;
    }

    /* 3 ta teng ustun yaratish uchun Flex va gap */
    .hero-grid {
      display: flex;
      gap: 24px; /* Ustunlar aro masofa */
    }

    /* Har bir ustun teng joy egallashi uchun flex: 1 */
    .hero-col {
      flex: 1;
      background-color: #ffffff;
      padding: 30px;
      border-radius: 8px;
      border: 1px solid #e2e8f0;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
    }

    .hero-col h2 {
      color: #0f172a;
      margin-bottom: 12px;
      font-size: 20px;
    }

    .hero-col p {
      color: #475569;
      font-size: 15px;
      line-height: 1.6;
    }


    /* ==========================================
       MEDIA QUERY (RESPONSIVE)
       ========================================== */
    /* Ekran 768px yoki undan kichik bo'lganda ustun shakliga (column) o'tish */
    @media (max-width: 768px) {
      .nav-container {
        flex-direction: column;
        gap: 15px; /* Elementlar ostma-ost tushgandagi masofa */
        text-align: center;
      }

      .nav-links {
        gap: 20px;
      }

      .hero-grid {
        flex-direction: column; /* Ustunlar yonma-yonlikdan qatorga o'tadi */
        gap: 16px;
      }
    }
  </style>
</head>
<body>

  <header class="header">
    <div class="container nav-container">
      <a href="#" class="logo">DevPRO</a>

      <ul class="nav-links">
        <li><a href="#home">Asosiy</a></li>
        <li><a href="#services">Xizmatlar</a></li>
        <li><a href="#portfolio">Portfolioma</a></li>
        <li><a href="#contact">Aloqa</a></li>
      </ul>

      <a href="#register" class="cta-btn">Boshlash</a>
    </div>
  </header>

  <main class="container hero">
    <div class="hero-grid">
      
      <div class="hero-col">
        <h2>Tezkor Kreativlik</h2>
        <p>Biznesingiz uchun eng zamonaviy va unikal dizaynlarni qisqa muddatlarda tayyorlab beramiz.</p>
      </div>

      <div class="hero-col">
        <h2>Mukammal Kod</h2>
        <p>Barcha loyihalarimiz eng so'nggi texnologiyalar va toza kodlash standartlari asosida yaratiladi.</p>
      </div>

      <div class="hero-col">
        <h2>Doimiy Qo'llab-quvvatlash</h2>
        <p>Sizning loyihangiz ishga tushgandan keyin ham uni rivojlantirish va himoya qilishda yordam beramiz.</p>
      </div>

    </div>
  </main>

</body>
</html>
Amalga oshirilgan talablar:
Nav tekisligi: justify-content: space-between orqali Logo, Menyu va CTA tugmasi chetlarga tarqatildi, align-items: center esa ularni vertikal o'rtaga keltirdi.

Hero ustunlari: .hero-col klassiga flex: 1 berilgani sababli, 3 ta blok kontent hajmidan qat'i nazar har doim teng kenglikni egallaydi.

Responsive dizayn: @media (max-width: 768px) ichida flex-direction: column qo'llanildi. Bu planshet va telefonlarda navbar elementlarini ham, hero ustunlarini ham chiroyli tarzda ustma-ust joylashtiradi.

Masofalar: Elementlar orasidagi barcha bo'shliqlar uchun eski margin usulidan emas, zamonaviy va qulay gap xossasidan foydalanildi.

Moslashuvchanlik (Responsiveness): .main ichidagi display: flex va flex-wrap: wrap xossasi tufayli, sahifa planshet yoki telefonda ochilganda 3 ta ustun siqilib ketmasdan, bir-birining ostiga tartib bilan joylashadi.
