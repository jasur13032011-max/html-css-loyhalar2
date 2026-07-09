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
HTML va CSS yordamida barcha semantik bo'limlar (thead, tbody, tfoot), qatlamli uslublar va so'ralgan funksiyalar qamrab olingan, toza va chiroyli jadval (table) kodi:

HTML va CSS Kodu
HTML
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chiroyli va Semantik Jadval</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f8fafc;
      padding: 40px 20px;
      color: #333;
    }

    /* Konteyner - jadval katta bo'lsa, mobil ekranda skroll bo'lishi uchun */
    .table-container {
      max-width: 1000px;
      margin: 0 auto;
      overflow-x: auto;
      background-color: #ffffff;
      box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
      border: 1px solid #e2e8f0;
    }

    /* Asosiy jadval uslublari */
    table {
      width: 100%;
      border-collapse: collapse; /* Chegaralarni birlashtirish */
      text-align: left;
    }

    /* Padding va Border qoidalari */
    th, td {
      padding: 14px 18px;
      border-bottom: 1px solid #e2e8f0;
      font-size: 15px;
    }

    /* Ustunlar bo'yicha matnni tekislash (Raqamlar o'ngga, matnlar chapga) */
    .text-right {
      text-align: right;
    }
    .text-center {
      text-align: center;
    }

    /* thead uslubi */
    thead {
      background-color: #1e3a8a; /* To'q ko'k font */
      color: #ffffff;
    }

    th {
      font-weight: 600;
      letter-spacing: 0.5px;
    }

    /* Zebra striping - tr:nth-child(even) orqali juft qatorlarni bo'yash */
    tbody tr:nth-child(even) {
      background-color: #f1f5f9; /* Och kulrang/ko'kish fon */
    }

    /* Hover effect - tr:hover sichqoncha kelganda qatorni ajratib ko'rsatadi */
    tbody tr:hover {
      background-color: #e2e8f0;
      transition: background-color 0.2s ease;
      cursor: pointer;
    }

    /* tfoot uslubi */
    tfoot {
      background-color: #f8fafc;
      font-weight: 700; /* Qalin matn */
      color: #1e3a8a;
    }

    tfoot td {
      border-top: 2px solid #cbd5e1; /* Jami qismini ajratuvchi qalinroq chiziq */
      border-bottom: none;
    }
  </style>
</head>
<body>

  <div class="table-container">
    <table>
      <thead>
        <tr>
          <th>Mahsulot nomi</th>
          <th>Tavsif</th>
          <th class="text-right">Narxi</th>
          <th class="text-center">Soni</th>
          <th class="text-right">Jami</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <td>Premium Noutbuk</td>
          <td>16GB RAM, 512GB SSD, Kulrang Intel i7</td>
          <td class="text-right">12 000 000 so'm</td>
          <td class="text-center">2</td>
          <td class="text-right">24 000 000 so'm</td>
        </tr>
        <tr>
          <td>Simsiz Sichqoncha</td>
          <td>Ergonomik dizayn, 2.4GHz Bluetooth</td>
          <td class="text-right">250 000 so'm</td>
          <td class="text-center">5</td>
          <td class="text-right">1 250 000 so'm</td>
        </tr>
        <tr>
          <td>Mexanik Klaviatura</td>
          <td>RGB yoritgichli, Red switches</td>
          <td class="text-right">800 000 so'm</td>
          <td class="text-center">1</td>
          <td class="text-right">800 000 so'm</td>
        </tr>
        <tr>
          <td>UltraWide Monitor</td>
          <td>27 dyuym, 144Hz IPS panel</td>
          <td class="text-right">3 500 000 so'm</td>
          <td class="text-center">2</td>
          <td class="text-right">7 000 000 so'm</td>
        </tr>
      </tbody>

      <tfoot>
        <tr>
          <td colspan="4" class="text-right">Umumiy hisob (Jami):</td>
          <td class="text-right">33 050 000 so'm</td>
        </tr>
      </tfoot>
    </table>
  </div>

</body>
</html>
Kod bo'yicha muhim eslatmalar:
border-collapse: collapse: Agar bu xossa berilmasa, jadval katakchalari orasida yoqimsiz bo'shliqlar qolib ketadi va chegaralar (border) ikki qavat bo'lib ko'rinadi.

colspan="4": tfoot ichidagi birinchi td katakchasiga berildi. U dastlabki 4 ta ustunni (Nom, Tavsif, Narx, Soni) bitta qilib birlashtiradi va oxirgi 5-ustun (Jami) o'z joyida to'g'ri hisob-kitobni ko'rsatib turadi.

Zebra Striping (:nth-child(even)): Faqat tbody tr lariga berildi, toki bu uslub thead yoki tfoot bo'limlarining ranglariga taqalluq qilmasin.

Moslashuvchanlik (Responsiveness): .main ichidagi display: flex va flex-wrap: wrap xossasi tufayli, sahifa planshet yoki telefonda ochilganda 3 ta ustun siqilib ketmasdan, bir-birining ostiga tartib bilan joylashadi.
