# DISCO XIV - Website Statis (Front-End Only)
### D'Information System Community Outbound XIV
**Himpunan Mahasiswa Sistem Informasi (HIMSI) Universitas Multimedia Nusantara**

---

## 1. Ikhtisar Proyek
Website statis murni (pure HTML & CSS, **tanpa JavaScript**) untuk perhelatan tahunan **DISCO XIV**. 

- **Konsep Acara**: Jamuan Makan Malam Bangsawan & Malam Keakraban di Villa Pegunungan (*Royal Banquet & Highland Villa Gathering*).
- **Tagline**: *"Satu Meja, Berjuta Cerita"* (EN: *"One Table, Endless Stories"*).
- **Hashtag**: `#SatuMejaBerjutaCerita`
- **Tahun Pelaksanaan**: 2027 *(Placeholder dapat disesuaikan)*.
- **Teknologi**: **HTML5 & CSS3 Murni**. Tidak ada ketergantungan (dependencies), package.json, React, Tailwind, Bootstrap, build step, maupun file/tag `<script>` JavaScript.

---

## 2. Cara Membuka & Menjalankan Website
Situs ini dirancang untuk dapat langsung dibuka secara lokal tanpa server web:
1. Navigasi ke folder proyek `disco-xiv/`.
2. Klik ganda (double-click) pada file **`index.html`** untuk versi Bahasa Indonesia.
3. Untuk versi Bahasa Inggris, klik ganda pada **`en/index.html`**, atau klik tombol pill switcher **`[ ID | EN ]`** pada bilah navigasi di setiap halaman.

---

## 3. Struktur File
```text
disco-xiv/
├── index.html                  # Beranda (Bahasa Indonesia)
├── divisi.html                 # Rincian 8 Divisi Kepanitiaan & Modal :target (ID)
├── masuk.html                  # Halaman Masuk / Login Tamu (ID)
├── daftar.html                 # Formulir RSVP Multi-Step Murni CSS (ID)
├── en/
│   ├── index.html              # Home (English)
│   ├── divisi.html             # Divisions & Committees (EN)
│   ├── masuk.html              # Noble Guest Login (EN)
│   └── daftar.html             # RSVP Multi-Step Registration Form (EN)
├── css/
│   ├── tokens.css              # Variabel warna, tipografi, jarak, radius, dan bayangan
│   ├── base.css                # CSS reset, tipografi dasar, aksesibilitas, scroll reveal
│   ├── components.css          # Navbar floating pill, tombol royal, kartu, modal, stepper, footer
│   └── pages.css               # Gaya spesifik halaman (hero 100vh, timeline, auth envelopes)
├── assets/
│   ├── logo-disco-xiv.svg      # Logo lambang kerajaan DISCO XIV (cloche, mahkota, laurel)
│   ├── mascot-sir-disco.svg    # Maskot resmi "Sir Disco" (chibi, jubah beludru, monokel, menu)
│   ├── mascot-badge.svg        # Lencana bulat Sir Disco untuk footer & stempel
│   ├── ornaments/
│   │   ├── corner-flourish.svg # Ornamen sudut Victorian filigree emas
│   │   ├── divider.svg         # Pembatas garis emas berornamen fleur-de-lis
│   │   ├── damask-pattern.svg  # Pola wallpaper damask barok mulus (seamless tile)
│   │   └── wax-seal.svg        # Segel lilin merah anggur dengan emboss "XIV"
│   └── images/
│       ├── villa-hero.jpg      # Foto/ilustrasi latar belakang malam villa pegunungan
│       └── villa-hero.svg      # Vektor resolusi tinggi atmosfer malam villa
└── README.md                   # Petunjuk teknis dan dokumentasi proyek
```

---

## 4. Panduan Menyesuaikan Konten & Aset

### A. Mengubah Teks & Tanggal Acara
Semua teks placeholder ditandai dengan komentar `<!-- TODO: ... -->` di dalam file HTML:
- **Tanggal Acara**: Cari teks `Jumat–Minggu, 6–8 November 2027` pada `index.html` dan `en/index.html`.
- **Nama Villa**: Ubah `Villa Kawasan Puncak — TBA` pada bagian Rangkaian Acara & Countdown.
- **Sosial Media**: Ubah tautan `@discoumn_si` pada bagian footer setiap halaman.

### B. Mengubah Warna & Tema Visual
Buka file **`css/tokens.css`**:
- Warna Burgundy Primer: `--color-burgundy-primary` (default: `#4A0E1B`)
- Warna Deep Wine: `--color-burgundy-deep` (default: `#6B1A2B`)
- Warna Emas Antik: `--color-gold-antique` (default: `#C9A24B`)
- Warna Emas Terang: `--color-gold-light` (default: `#E6CF8B`)
- Warna Kertas Perkamen: `--color-parchment-ivory` (default: `#F3E9D2`)

### C. Mengganti Maskot & Logo
Jika tim desain grafis memiliki ilustrasi final:
- Ganti file `assets/mascot-sir-disco.svg` dengan ilustrasi maskot final (pertahankan nama file yang sama).
- Ganti file `assets/logo-disco-xiv.svg` dengan logo resmi final.
- Ganti file `assets/images/villa-hero.jpg` jika ingin menggunakan foto nyata villa tempat outbound berlangsung.

---

## 5. Fitur Interaktif Murni CSS (Strictly No JavaScript)
Sesuai batasan teknis (Tech Constraints), seluruh interaktivitas dibangun murni menggunakan fitur modern CSS3:

1. **Meja Jamuan Bundar Interaktif (`divisi.html`)**:
   - Menghadirkan **Meja Jamuan Bundar Kerajaan** (*"Satu Meja, Berjuta Cerita"*), menggantikan konsep orbit planet luar angkasa tahun lalu menjadi konsep perjamuan bangsawan mewah dengan tekstur ukiran kayu mahoni gelap bertabur tatahan emas (*inlaid gold filigree*) dan cahaya lilin temaram.
   - Piring kehormatan (*charger plates*) dari 9 pilar divisi berputar perlahan secara otomatis mengelilingi piring saji utama (*centerpiece*) berlambang DISCO XIV via `@keyframes royalTableSpin`.
   - Menggunakan teknik *counter-rotation* (`@keyframes counterPlateSpin`) sehingga seluruh logo dan nama divisi senantiasa tegak dan mudah dibaca saat meja berputar.
   - Bersifat **interaktif murni CSS**: Mengklik piring kehormatan atau tombol navigasi kursi akan langsung menyorot (*spotlight*) divisi tersebut dan membuka kartu menu rincian lengkapnya secara instan tanpa reload. Dilengkapi tombol *Putar/Jeda Meja* (`#toggle-spin`).
2. **Menu Hamburger Mobile**:
   Menggunakan *checkbox hack* (`#nav-toggle:checked ~ .navbar-pill .navbar-nav`). Menu overlay terbuka mulus tanpa JavaScript.
3. **Modal Rincian Divisi (`divisi.html`)**:
   Menggunakan pseudo-class **`:target`**. Tautan `<a href="#modal-acara">` mengaktifkan elemen `.modal-backdrop:target`. Tombol silang tutup memiliki `href="#"` yang menghapus hash target dan menutup modal.
4. **Formulir Pendaftaran Multi-Step (`daftar.html`)**:
   Menggunakan kombinasi input radio tersembunyi (`#step-1`, `#step-2`, `#step-3`, `#step-success`) dan pemilih CSS **`:has()`** untuk menampilkan panel aktif serta menyalakan indikator lilin emas per langkah. Dilengkapi validasi form bawaan HTML5 (`required`, `pattern`, `minlength`, `type="email"`).
5. **Marquee Logo Mitra / Sponsor**:
   Menggunakan animasi CSS `@keyframes marqueeScroll` dengan efek pudar tepi (*edge fade*) via `mask-image: linear-gradient(...)` serta jeda otomatis saat di-*hover* (`animation-play-state: paused`). Pada layar kecil disediakan fallback *CSS scroll-snap*.
6. **Scroll Reveal**:
   Menggunakan fitur modern `@supports (animation-timeline: view())` dengan fallback anggun: elemen tetap terlihat 100% (*visible by default*) jika browser belum mendukung spesifikasi tersebut.

---

## 6. Daftar Elemen yang Bersifat Statis (Tanpa JS)
Elemen-elemen berikut sengaja dibuat statis karena JavaScript tidak diperkenankan:
1. **Penghitung Waktu Mundur (Countdown Timer)**:
   Angka hari, jam, menit, dan detik pada section *Masa Penantian Jamuan Utama* adalah angka statis yang didesain elegan dalam bingkai jam saku kuno. Kode HTML telah dilengkapi komentar penanda (*JavaScript Extension Point*) sehingga tim pengembang dapat dengan mudah menghubungkan script timer dinamis di masa depan.
2. **Statistik Angka**:
   Angka `450+ Tamu Kehormatan`, `65+ Kurator Jamuan`, `14 Edisi`, dan `120K+ Sorotan` ditampilkan statis dalam bingkai berornamen emas ganda.
3. **Formulir Otentikasi & RSVP**:
   Halaman Masuk (`masuk.html`) dan Pendaftaran (`daftar.html`) adalah *visual UI only*. Formulir menggunakan atribut `action="#"` dan tidak mengirimkan maupun menyimpan data ke server mana pun.

---

## 7. Aksesibilitas & Responsivitas
- **Standar Aksesibilitas**: Menggunakan tag semantik HTML5 (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<address>`), tautan ramah pembaca layar (*Skip to Content*), teks `alt` deskriptif pada gambar/SVG, serta indikator fokus `:focus-visible` dengan kontras tinggi.
- **Responsif**: Dioptimalkan dan diuji untuk tampilan mobile (375px), tablet (768px), hingga monitor desktop lebar (1440px+).
- **Prefers Reduced Motion**: Semua animasi `@keyframes` dan transisi dinonaktifkan atau diminimalkan secara otomatis saat pengguna mengaktifkan preferensi *Reduced Motion* pada sistem operasi.
