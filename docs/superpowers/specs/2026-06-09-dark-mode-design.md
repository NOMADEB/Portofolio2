# Dark Mode — Design Spec

Date: 2026-06-09

## Tujuan

Menambahkan fitur mode gelap (dark mode) ke portfolio Reka Adrian agar
terlihat lebih profesional. Pengunjung bisa beralih antara tema terang dan
gelap lewat tombol di navbar. Pekerjaan ini mengedit `index.html`,
`style.css`, dan `tailwind.config.js` pada project single-file existing
(TailwindCSS CLI → `output.css`, Chart.js via CDN, vanilla JS).

## Pendekatan teknis

Tailwind `darkMode: 'class'`: class `dark` ditaruh di elemen `<html>`, lalu
tiap elemen yang perlu beda warna diberi varian `dark:` (mis.
`bg-white dark:bg-gray-800`). Ini cara standar Tailwind dan selaras dengan
gaya utility yang sudah dipakai.

## Komponen

### 1. Konfigurasi (`tailwind.config.js`)
- Tambah `darkMode: 'class'` agar varian `dark:` ter-generate ke `output.css`.

### 2. Tombol toggle (navbar)
- Ditaruh di navbar, sebelah tombol "LET'S TALK".
- Ikon bulan saat mode terang, ikon matahari saat mode gelap (saling ganti).
- Satu toggle di navbar desktop + satu di menu mobile drawer, agar bisa
  diakses di kedua tampilan.
- Tombol punya `aria-label` untuk aksesibilitas.

### 3. Logika JS (di `<script>` `index.html`)
- Fungsi `applyTheme(theme)`: tambah/hapus class `dark` di `<html>`,
  sesuaikan ikon (bulan/matahari) di kedua toggle.
- Fungsi `toggleTheme()`: balik tema sekarang, simpan ke `localStorage`
  key `theme` ('dark'|'light'), panggil `applyTheme`.
- Saat load (`DOMContentLoaded` dan/atau skrip head): baca `localStorage.theme`.
  Jika ada, pakai itu. Jika belum pernah, ikut `window.matchMedia(
  '(prefers-color-scheme: dark)')` (tema OS).
- Skrip anti-flicker kecil di `<head>` (sebelum body render): set class `dark`
  lebih awal berdasarkan localStorage/sistem agar tidak ada kedipan putih
  saat membuka halaman dalam mode gelap.

### 4. Styling gelap (`dark:` di HTML + rule di `style.css`)
Elemen yang dapat varian gelap:
- Body: `dark:bg-gray-900`. Kartu utama `.main-card` & semua kartu:
  `dark:bg-gray-800`.
- Teks: judul `dark:text-gray-100`; paragraf `dark:text-gray-300` /
  `dark:text-gray-400`.
- Border: `dark:border-gray-700`.
- Badge skill, nav link, mobile nav link, social icon, floating icon,
  contact popup, tombol — semua punya varian gelap. Aksen biru dipertahankan.
- Gradient putih di bawah foto profil diganti agar menyatu di mode gelap
  (mis. `dark:from-gray-800`).
- Marquee Tech Stack & foto profil tetap tampil; latar bulat logo
  disesuaikan jika perlu agar kontras.
- `style.css`: tambahkan rule gelap untuk `::selection`, scrollbar,
  `.main-card`, `.skill-card`, `.nav-link`, `.mobile-nav-link` (gunakan
  selector `.dark` parent atau `@apply` dengan `dark:`).

### 5. Radar chart (Chart.js)
- Atur warna grid, garis sumbu, dan label lewat opsi Chart.js agar terbaca
  di kedua mode. Karena chart digambar saat load, ambil warna sesuai tema
  aktif saat inisialisasi. (Re-render saat toggle bersifat opsional; minimal
  chart terbaca di mode default.)

## Hal teknis & urutan kerja

Karena menyentuh banyak elemen, dikerjakan bertahap dan build diverifikasi
tiap langkah:
1. Config `darkMode: 'class'` + skrip toggle/JS + anti-flicker.
2. Styling global (body, main-card, navbar, style.css).
3. Styling per tab: Home, Experience, Skills, About.
4. Contact popup + radar chart + verifikasi akhir.

Verifikasi: `npm run build` sukses tiap langkah; buka di browser, toggle
gelap/terang, cek semua tab terbaca, refresh tetap ingat pilihan, tidak ada
kedipan putih saat load gelap.

## Out of scope

- Tema selain gelap/terang (mis. multiple color theme).
- Animasi transisi tema yang rumit (cukup transisi warna halus standar).
- Mengubah konten/struktur tab yang sudah ada.
