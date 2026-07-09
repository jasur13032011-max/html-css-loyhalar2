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

Moslashuvchanlik (Responsiveness): .main ichidagi display: flex va flex-wrap: wrap xossasi tufayli, sahifa planshet yoki telefonda ochilganda 3 ta ustun siqilib ketmasdan, bir-birining ostiga tartib bilan joylashadi.
