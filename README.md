# html-css-loyhalar2
Jadval yaratishda ma'lumotlarni mantiqiy guruhlash juda muhim. Quyidagi sxemada selektorlar va atributlarning qayerda joylashishi ko'rsatilgan:

<thead>: Jadvalning sarlavha qismi. Ichida faqat <th> (Table Header) elementlari ishlatiladi.

<tbody>: Asosiy ma'lumotlar qatori. Ichida <td> (Table Data) elementlari bo'ladi.

<tfoot>: Yakunlovchi yoki umumlashtiruvchi qism.

CSS Selektorlari va Atributlar qanday ishlaydi?
1. Zebra Striping (tr:nth-child(even))
Bu selektor matematik qonuniyat asosida ishlaydi. tbody tr:nth-child(even) deganda brauzer faqat juft o'rindagi (2, 4, 6, ...) qatorlarni tanlaydi va ularga boshqa fon rangini beradi. Toq qatorlar uchun esa :nth-child(odd) ishlatilishi mumkin.

2. Hover Effekti (tr:hover)
Foydalanuvchi sichqoncha ko'rsatkichini jadval qatorining ustiga olib kelganda, o'sha qator ajralib turishi uchun xizmat qiladi. Bu foydalanuvchiga katta jadvallardagi raqamlarni adashmasdan ko'rishga yordam beradi (UX).

3. Ustunlarni Birlashtirish (colspan)
Agar biror katakcha o'zidan keyingi bir nechta ustun joyini egallashi kerak bo'lsa, unga colspan atributi beriladi. Masalan, colspan="4" yozilsa, o'sha katakcha 4 ta ustun kengligida cho'ziladi.

Mustahkamlash uchun amaliy mashq kodi:
Quyidagi kodni o'zingizda yozib, ranglarni o'zgartirib mashq qilib ko'ring:

HTML
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <title>Jadval Selektorlari Mashqi</title>
  <style>
    table {
      width: 100%;
      border-collapse: collapse; /* Katakchalar orasidagi bo'shliqni yo'qotadi */
    }

    th, td {
      border: 1px solid #cbd5e1;
      padding: 12px;
    }

    /* MASHQ: Sarlavha paneli uslubi */
    thead {
      background-color: #0f172a;
      color: white;
    }

    /* MASHQ: Zebra Striping (Juft qatorlarni bo'yash) */
    tbody tr:nth-child(even) {
      background-color: #f8fafc;
    }

    /* MASHQ: Hover effekti (Sichqoncha kelganda) */
    tbody tr:hover {
      background-color: #e2e8f0;
    }

    /* MASHQ: Yakuniy qator (Qalin matn) */
    tfoot {
      font-weight: bold;
      background-color: #f1f5f9;
    }
  </style>
</head>
<body>

  <table>
    <thead>
      <tr>
        <th>ID</th>
        <th>Kurs nomi</th>
        <th>Davomiyligi</th>
        <th>Narxi</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>01</td>
        <td>Frontend Dasturlash</td>
        <td>6 oy</td>
        <td>1 200 000 so'm</td>
      </tr>
      <tr>
        <td>02</td>
        <td>Backend (Node.js)</td>
        <td>5 oy</td>
        <td>1 500 000 so'm</td>
      </tr>
      <tr>
        <td>03</td>
        <td>UX/UI Dizayn</td>
        <td>3 oy</td>
        <td>1 000 000 so'm</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td colspan="3" style="text-align: right;">O'rtacha narx:</td>
        <td>1 233 000 so'm</td>
      </tr>
    </tfoot>
  </table>

</body>
</html>
