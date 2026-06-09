# Portfolio Reka Adrian — Design Spec

Date: 2026-06-09

## Tujuan

Mengubah template portfolio existing (milik "Ahwanulm") menjadi portfolio
pribadi Reka Adrian, dengan konten bersumber dari CV. Ini adalah pekerjaan
edit konten pada `index.html` (single-file, TailwindCSS + Chart.js), bukan
membangun dari nol.

## Identitas & Kontak

- Nama: REKA ADRIAN
- Title: Full Stack Web Developer
- Lokasi: Yogyakarta, DI Yogyakarta
- Email: Adrianreka71@gmail.com
- WhatsApp / Phone: +62 878-7338-0473
- GitHub: https://github.com/NOMADEB
- LinkedIn: https://linkedin.com/in/reka-adrian-4479ab292
- Foto profil: tetap `./img/Profile.jpg` (placeholder; diisi user sendiri)
- Hapus semua jejak sosial lama: Telegram, Instagram, Facebook

## Struktur Navigasi

Dari 5 tab (Home, Project, Services, Payment, About me) menjadi 4 tab:
**Home, Experience, Skills, About me**. Nav desktop + drawer mobile + ikon
SVG mobile disesuaikan. Logo `<Ahwanulm/>` → `<RekaAdrian/>`.

## Tab 1 — Home

- Hero: "Hello, I'm" + REKA ADRIAN + "Full Stack Web Developer"
- Paragraf ringkasan dari Summary CV (Informatics, technical support & web
  systems development, troubleshooting, testing, game development)
- Badge lokasi: Yogyakarta, Indonesia
- Badge email: Adrianreka71@gmail.com
- Ikon sosial: Email, GitHub, LinkedIn, WhatsApp
- Kartu kanan (dulu website amstream.pro dll): ganti jadi 1 proyek nyata
  **sanurpro.co.id** + highlight singkat. Kartu lain dihapus / dijadikan
  highlight skill agar tidak kosong.

## Tab 2 — Experience

Card per pengalaman (4 card), tiap card: judul peran, perusahaan, periode,
poin tugas dari CV.

1. Full Stack Web Developer — PT. SanurPro IndoTeknologi (Aug 2025 - Present)
2. Cyber Analyst — Hacktober Fest, not officially finished (Oct 2024)
3. Thesis Writing Services — Freelance (Jan 2025 - Present)
4. Front-End Developer — Freelance (Feb 2024 - Aug 2024)

## Tab 3 — Skills

Gabungan badge + radar chart.

- Badge Technical Skills: Laravel, PHP, MySQL, HTML & CSS, Kotlin,
  Kali Linux, Troubleshoot, Operating Software
- Badge Soft Skills: Good communication, Team work, Problem solving
- Radar chart (Chart.js) kategori besar: Web Development, Backend, Security,
  Problem Solving, Communication. Nilai estimasi wajar (user bisa sesuaikan).
- Bar chart lama: dihapus atau diselaraskan dengan kategori di atas.

## Tab 4 — About me

- Foto + bio (dari Summary)
- Education: Mercu Buana University of Yogyakarta, Computer Science
  (Aug 2021 - Aug 2025); fokus AI game development, Godot engine, asset
  creation RPG, AI boss movement
- Certification: Microsoft Azure Basic
- Lokasi & kontak (email, WA, GitHub, LinkedIn)

## Hal teknis

- Update `<title>` dan semua atribut `alt` yang menyebut Ahwanulm
- Update data & label Chart.js
- Update semua link `mailto:`, `wa.me`, `github.com`, dan popup kontak
- Tidak menambah dependensi baru; tetap TailwindCSS + Chart.js
- Setelah edit: build CSS (`npm run build`) tetap jalan dan verifikasi di
  browser bahwa semua tab tampil benar

## Out of scope

- Membuat ulang struktur/komponen dari nol
- Menambah tab Payment/Services
- Mengganti foto profil (diisi user)
