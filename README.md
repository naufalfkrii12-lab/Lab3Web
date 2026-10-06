# Lab3Web - Praktikum 3: CSS Dasar

| | |
|---|---|
| **Nama** | Naufal Fikri |
| **NIM** | 312510350 |
| **Kelas** | I252.A |
| **Mata Kuliah** | Pemrograman Web |
| **Universitas** | Universitas Pelita Bangsa, Bekasi |

## Struktur File

```
Lab3Web/
├── lab2_css_dasar.html     # dokumen HTML (CSS internal + inline + link eksternal)
├── style_eksternal.css     # CSS eksternal (nav, ID selector, class selector)
├── README.md               # laporan praktikum
└── screenshots/            # screenshot tiap langkah
```

## Tujuan

1. Memahami konsep dasar CSS
2. Memahami aturan penulisan CSS
3. Memahami selector sebagai pengontrol CSS
4. Membuat pengaturan CSS pada HTML

---

## Langkah-langkah Praktikum

### 1. Membuat Dokumen HTML
Dibuat file `lab2_css_dasar.html` berisi struktur dasar HTML: `<header>` dengan `<h1>`, `<nav>` berisi tiga link, serta `<div id="intro">` yang berisi heading, paragraf, dan link dengan class `button btn-primary`. Pada tahap ini belum ada CSS sehingga tampilan masih bawaan browser.

![Dokumen HTML](screenshots/01-dokumen-html.png)

### 2. Mendeklarasikan CSS Internal
CSS internal ditulis di dalam tag `<style>` pada bagian `<head>`. Aturan yang ditambahkan:
- `body` : font `Open Sans`, sans-serif
- `header` : tinggi minimal 80px dan garis bawah biru muda
- `h1` : ukuran 24px, warna `#0F189F`, rata tengah, padding
- `h1 i` : teks miring di dalam h1 berwarna abu-abu `#6d6a6b`

![CSS Internal](screenshots/02-css-internal.png)

### 3. Menambahkan Inline CSS
CSS inline ditambahkan sebagai atribut `style` pada tag `<p>`:

```html
<p style="text-align: center; color: #ccd8e4;">
```
Paragraf menjadi rata tengah dengan warna abu-abu kebiruan terang. Inline CSS hanya berpengaruh pada elemen tersebut.

![Inline CSS](screenshots/03-inline-css.png)

### 4. Membuat CSS Eksternal
Dibuat file `style_eksternal.css` berisi aturan untuk `nav`, `nav a`, dan `nav .active, nav a:hover`. File dihubungkan ke HTML dengan tag `<link>` di `<head>`:

```html
<link rel="stylesheet" href="style_eksternal.css" type="text/css">
```
Navigasi tampil dengan latar hijau `#20A759`, teks putih, dan tanpa garis bawah link.

![CSS Eksternal](screenshots/04-css-eksternal.png)

### 5. Menambahkan CSS Selector
Pada `style_eksternal.css` ditambahkan:
- **ID Selector** `#intro` dan `#intro h1` (latar biru `#418fb1`, heading putih rata kiri)
- **Class Selector** `.button` dan `.btn-primary` (tombol merah `#E42A42` dengan `display: inline-block`)

![ID dan Class Selector](screenshots/05-id-class-selector.png)

### Validasi
Kode CSS divalidasi melalui https://jigsaw.w3.org/css-validator/ (silakan tambahkan screenshot hasil validasi Anda di sini).

---

## Pertanyaan dan Tugas

### 1. Eksperimen properti CSS
Properti dan nilai pada kode CSS dapat diubah, misalnya mengganti `color`, `font-size`, `padding`, atau menambah `border-radius` pada `.button`. Setiap perubahan terlihat setelah file disimpan dan browser di-refresh.

### 2. Perbedaan `h1 {...}` dengan `#intro h1 {...}`
- `h1 {...}` adalah **element selector**: berlaku untuk **semua** elemen `<h1>` di dokumen (heading di header maupun di dalam `#intro`).
- `#intro h1 {...}` adalah **descendant selector** yang dikombinasikan dengan ID: hanya berlaku untuk `<h1>` yang berada **di dalam** elemen ber-id `intro`.

Karena `#intro h1` lebih spesifik, aturannya menimpa `h1` biasa. Pada praktikum ini `h1` global berwarna biru dan rata tengah, sedangkan `<h1>Hello World</h1>` di dalam `#intro` menjadi putih dan rata kiri. Heading "CSS Internal dan Inline CSS" di `<header>` tetap memakai aturan `h1` global.

### 3. Prioritas CSS internal, eksternal, dan inline pada elemen yang sama
Yang ditampilkan adalah **inline CSS**, karena inline memiliki prioritas tertinggi. Untuk internal dan eksternal, dengan spesifisitas selector yang sama, yang menang adalah yang **ditulis paling akhir** (aturan *cascade*): jika `<link>` diletakkan setelah `<style>`, eksternal menimpa internal, dan sebaliknya.

Urutan prioritas: **Inline > Internal/Eksternal (tergantung urutan) > default browser**.

Contoh:
```html
<head>
  <link rel="stylesheet" href="style.css">  <!-- p { color: green; } -->
  <style> p { color: blue; } </style>        <!-- internal -->
</head>
<body>
  <p style="color: red;">Teks ini berwarna merah</p>
</body>
```
Teks berwarna **merah** (inline menang). Jika atribut `style` dihapus, teks berwarna **biru** karena `<style>` ditulis setelah `<link>`.

### 4. Prioritas ID dan Class pada elemen yang sama
Contoh elemen: `<p id="paragraf-1" class="textparagraf">`

Yang ditampilkan adalah deklarasi **ID selector**, karena spesifisitas ID (`#`) lebih tinggi daripada class (`.`), tanpa memandang urutan penulisan.

Contoh:
```css
.textparagraf { color: blue; }
#paragraf-1  { color: red; }
```
Paragraf akan berwarna **merah**. Urutan spesifisitas: inline > ID > class > elemen.

---

## Kesimpulan
CSS dapat ditulis secara internal, eksternal, dan inline. CSS eksternal paling efisien untuk banyak halaman, sedangkan selector (elemen, class, ID) menentukan elemen mana yang terkena aturan, dengan prioritas ditentukan oleh spesifisitas dan urutan penulisan.
