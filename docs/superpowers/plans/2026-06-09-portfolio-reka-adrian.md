# Portfolio Reka Adrian — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Ubah template portfolio "Ahwanulm" menjadi portfolio Reka Adrian dengan konten dari CV, dalam 4 tab: Home, Experience, Skills, About me.

**Architecture:** Single-file edit pada `index.html` (TailwindCSS + Chart.js, vanilla JS tab switching via `showTab()`). Section existing di-rename/rebuild: `tab-project`→`tab-experience`, `tab-services`→`tab-skills`, `tab-payment` dihapus. `tab-home` & `tab-about` diedit kontennya.

**Tech Stack:** HTML, TailwindCSS (CLI build ke `output.css`), Chart.js (CDN), vanilla JS.

**Verification:** Tidak ada test framework (static HTML). Verifikasi = `npm run build` sukses + buka di browser, klik tiap tab, cek konten & link benar.

**Catatan data CV:**
- Nama: REKA ADRIAN · Title: Full Stack Web Developer · Lokasi: Yogyakarta, Indonesia
- Email: Adrianreka71@gmail.com · WA/Phone: +62 878-7338-0473 (wa.me: 6287873380473)
- GitHub: https://github.com/NOMADEB · LinkedIn: https://linkedin.com/in/reka-adrian-4479ab292
- Proyek nyata: https://sanurpro.co.id

---

### Task 1: Update head, nav, dan mobile drawer (5 tab → 4 tab)

**Files:**
- Modify: `index.html` (head ~line 7, nav ~line 19-53, mobile drawer ~line 56-98)

- [ ] **Step 1: Update `<title>`**

Ganti `<title>Ahwanulm - Full Stack Developer</title>` menjadi:
```html
<title>Reka Adrian - Full Stack Web Developer</title>
```

- [ ] **Step 2: Update logo nav**

Ganti `<span class="text-gray-400">&lt;</span>Ahwanulm<span class="text-gray-400">/&gt;</span>` menjadi:
```html
<span class="text-gray-400">&lt;</span>RekaAdrian<span class="text-gray-400">/&gt;</span>
```

- [ ] **Step 3: Update desktop nav links (line ~26-30)**

Ganti 5 button (home/project/services/payment/about) menjadi 4:
```html
<button onclick="showTab('home')" class="nav-link active" data-tab="home">Home</button>
<button onclick="showTab('experience')" class="nav-link" data-tab="experience">Experience</button>
<button onclick="showTab('skills')" class="nav-link" data-tab="skills">Skills</button>
<button onclick="showTab('about')" class="nav-link" data-tab="about">About me</button>
```

- [ ] **Step 4: Update mobile drawer links (line ~56-98)**

Ganti blok mobile-nav-link menjadi 4 item (Home, Experience, Skills, About me). Pertahankan struktur `<button onclick="showTab('X'); closeMobileMenu();" class="mobile-nav-link" data-tab="X">` + SVG ikon. Gunakan SVG yang sudah ada untuk Home & About; untuk Experience pakai ikon briefcase, Skills pakai ikon chart/bar. Contoh Experience:
```html
<button onclick="showTab('experience'); closeMobileMenu();" class="mobile-nav-link" data-tab="experience">
    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
    </svg>
    Experience
</button>
```
Skills:
```html
<button onclick="showTab('skills'); closeMobileMenu();" class="mobile-nav-link" data-tab="skills">
    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"></path>
    </svg>
    Skills
</button>
```

- [ ] **Step 5: Verifikasi build**

Run: `npm run build`
Expected: sukses tanpa error (file `output.css` ter-generate).

---

### Task 2: Update tab Home (hero, kontak, sosial, kartu proyek)

**Files:**
- Modify: `index.html` (section `tab-home`, line ~103-244)

- [ ] **Step 1: Update hero text (line ~120-135)**

- "Hello, I'm" tetap.
- Ganti `AHWANULM` → `REKA ADRIAN`.
- Ganti subtitle `Full Stack Developer` → `Full Stack Web Developer`.
- Ganti paragraf ringkasan menjadi:
```html
<p class="text-gray-500 leading-relaxed max-w-sm">
    Bachelor's degree in Informatics with experience in technical support and
    web systems development. Skilled in hardware and software troubleshooting,
    system installation, and delivering technical solutions. Ready to contribute
    in IT support and web development.
</p>
```

- [ ] **Step 2: Update badge lokasi & email (line ~146, ~152)**

- Lokasi: `Lombok, Indonesia` → `Yogyakarta, Indonesia`
- Email badge: `ahwanulm1@gmail.com` → `Adrianreka71@gmail.com`

- [ ] **Step 3: Update ikon sosial (line ~156-192)**

Pertahankan 4 ikon: Email, GitHub, LinkedIn, WhatsApp. Hapus Telegram, Facebook, Instagram.
- Email: `href="mailto:Adrianreka71@gmail.com"`
- GitHub: `href="https://github.com/NOMADEB"`
- Ganti ikon Telegram menjadi LinkedIn: `href="https://linkedin.com/in/reka-adrian-4479ab292"` dengan path SVG LinkedIn:
```html
<a href="https://linkedin.com/in/reka-adrian-4479ab292" target="_blank" class="social-icon">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
        <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.225 0z"/>
    </svg>
</a>
```
- Ganti ikon Facebook menjadi WhatsApp: `href="https://wa.me/6287873380473"` dengan path SVG WhatsApp:
```html
<a href="https://wa.me/6287873380473" target="_blank" class="social-icon">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.149-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.999-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
    </svg>
</a>
```

- [ ] **Step 4: Update alt foto profil (line ~198)**

`alt="Ahwanulm"` → `alt="Reka Adrian"`. Path `./img/Profile.jpg` tetap (placeholder user).

- [ ] **Step 5: Ganti website cards jadi proyek sanurpro (line ~206-243)**

Ganti 3 kartu (amstream/klipers/pixelnest) menjadi 1 kartu proyek nyata + 2 highlight. Kartu utama:
```html
<a href="https://sanurpro.co.id" target="_blank"
    class="skill-card block hover:shadow-xl transition-all group cursor-pointer website-card">
    <div class="flex items-center gap-2 lg:gap-4 mb-1 lg:mb-2">
        <div class="w-10 h-8 lg:w-16 lg:h-12 rounded-lg bg-gradient-to-br from-blue-500 to-cyan-500 flex items-center justify-center text-white font-bold text-xs lg:text-sm">SP</div>
    </div>
    <p class="text-gray-700 font-semibold text-xs lg:text-sm">sanurpro.co.id</p>
    <p class="text-gray-400 text-[10px] lg:text-xs">Full Stack Web Project</p>
    <span class="text-blue-500 text-[10px] lg:text-xs font-medium hidden lg:inline">Visit →</span>
</a>
```
Dua kartu highlight (bukan link, sebagai pengisi):
```html
<div class="skill-card lg:ml-6 block website-card">
    <p class="text-gray-700 font-semibold text-xs lg:text-sm">Backend</p>
    <p class="text-gray-400 text-[10px] lg:text-xs">Laravel · Node.js · MySQL</p>
</div>
<div class="skill-card block website-card">
    <p class="text-gray-700 font-semibold text-xs lg:text-sm">Security</p>
    <p class="text-gray-400 text-[10px] lg:text-xs">OWASP ZAP · Burp Suite</p>
</div>
```

- [ ] **Step 6: Verifikasi**

Run: `npm run build` → sukses. Buka `index.html` di browser, tab Home tampil dengan nama Reka Adrian, 4 ikon sosial, kartu sanurpro.

---

### Task 3: Pindahkan/bersihkan chart dari Home & rebuild tab Experience

**Files:**
- Modify: `index.html` (Experience graph block dalam tab-home line ~645-806; section `tab-project` line ~809-1039)

- [ ] **Step 1: Hapus blok "Experience Graph Section" dari tab-home**

Hapus blok dari `<!-- Experience Graph Section -->` (line ~645) sampai sebelum penutup section tab-home (sebelum `</section>` yang menutup tab-home, sekitar line ~806). Chart skill akan dipindah ke tab Skills (Task 4), jadi di Home cukup hero + tech stack marquee. Pastikan tidak menghapus `</div></section>` penutup tab-home.

- [ ] **Step 2: Rename section project → experience**

Ganti `<section id="tab-project" class="tab-content hidden">` menjadi `<section id="tab-experience" class="tab-content hidden">`. Update komentar `<!-- TAB: PROJECT -->` → `<!-- TAB: EXPERIENCE -->`.

- [ ] **Step 3: Ganti heading section experience**

Ganti heading (line ~814-817):
```html
<h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-4">Experience</h2>
<p class="text-gray-500 mt-3 max-w-2xl mx-auto">My professional journey in web development and tech.</p>
```

- [ ] **Step 4: Ganti grid project cards menjadi 4 experience cards**

Ganti seluruh isi `<div class="grid md:grid-cols-3 ...">` (line ~821 dst, semua kartu project) dengan grid 4 card berikut:
```html
<div class="grid md:grid-cols-2 gap-6 max-w-5xl mx-auto mb-12">
    <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6">
        <div class="flex items-start justify-between mb-2">
            <h3 class="font-bold text-gray-900">Full Stack Web Developer</h3>
            <span class="text-xs text-green-600 font-medium">● Present</span>
        </div>
        <p class="text-sm text-gray-500 mb-1">PT. SanurPro IndoTeknologi · Full Time</p>
        <p class="text-xs text-gray-400 mb-4">Aug 2025 - Present</p>
        <ul class="text-gray-500 text-sm space-y-2 list-disc list-inside">
            <li>Develop and build end-to-end web applications covering front-end and back-end systems.</li>
            <li>Design responsive, user-friendly UI/UX with HTML, CSS, JavaScript, and modern frameworks.</li>
            <li>Build and maintain back-end services using Node.js or PHP Laravel, including RESTful APIs.</li>
            <li>Manage and integrate MySQL databases for efficient, scalable data handling.</li>
            <li>Handle deployment, maintenance, troubleshooting, and performance optimization.</li>
        </ul>
    </div>
    <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6">
        <div class="flex items-start justify-between mb-2">
            <h3 class="font-bold text-gray-900">Cyber Analyst</h3>
            <span class="text-xs text-gray-400 font-medium">Hacktober Fest</span>
        </div>
        <p class="text-sm text-gray-500 mb-1">Open Source Contribution (not officially finished)</p>
        <p class="text-xs text-gray-400 mb-4">October 2024</p>
        <ul class="text-gray-500 text-sm space-y-2 list-disc list-inside">
            <li>Perform vulnerability scanning and security analysis on websites as ethical contribution.</li>
            <li>Identify and report vulnerabilities such as SQL Injection, XSS, and misconfiguration.</li>
            <li>Use tools like OWASP ZAP and Burp Suite for analysis and testing.</li>
            <li>Work with project maintainers to understand architecture and suggest mitigations.</li>
        </ul>
    </div>
    <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6">
        <div class="flex items-start justify-between mb-2">
            <h3 class="font-bold text-gray-900">Thesis Writing Services</h3>
            <span class="text-xs text-green-600 font-medium">● Present</span>
        </div>
        <p class="text-sm text-gray-500 mb-1">Freelance</p>
        <p class="text-xs text-gray-400 mb-4">Jan 2025 - Present</p>
        <ul class="text-gray-500 text-sm space-y-2 list-disc list-inside">
            <li>Create and write thesis proposals and build the code clients need.</li>
        </ul>
    </div>
    <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6">
        <div class="flex items-start justify-between mb-2">
            <h3 class="font-bold text-gray-900">Front-End Developer</h3>
            <span class="text-xs text-gray-400 font-medium">Freelance</span>
        </div>
        <p class="text-sm text-gray-500 mb-1">eBook & Web Content</p>
        <p class="text-xs text-gray-400 mb-4">Feb 2024 - Aug 2024</p>
        <ul class="text-gray-500 text-sm space-y-2 list-disc list-inside">
            <li>Design and write informative eBooks according to client website needs.</li>
            <li>Conduct research to ensure data accuracy and content relevance.</li>
            <li>Design eBook layouts using Canva / Adobe InDesign.</li>
            <li>Coordinate with content team and website owner for revisions.</li>
        </ul>
    </div>
</div>
```
Hapus sisa konten lama section ini (apapun setelah grid sampai `</section>` penutup tab-project), sisakan hanya grid card di atas + penutup `</div></section>`.

- [ ] **Step 5: Verifikasi**

Run: `npm run build` → sukses. Browser: klik tab Experience → 4 card tampil benar, klik Home → tidak ada lagi chart, marquee tetap ada.

---

### Task 4: Rebuild tab Skills (badge + radar chart)

**Files:**
- Modify: `index.html` (section `tab-services` line ~1041-1232)

- [ ] **Step 1: Rename section services → skills**

Ganti `<section id="tab-services" class="tab-content hidden">` → `<section id="tab-skills" class="tab-content hidden">`. Komentar `<!-- TAB: SERVICES -->` → `<!-- TAB: SKILLS -->`.

- [ ] **Step 2: Ganti seluruh isi section dengan badge + radar**

Ganti isi dalam section (semua konten services lama) dengan:
```html
<div class="py-12 md:py-16 px-6 md:px-12">
    <div class="text-center mb-10">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-4">Skills</h2>
        <p class="text-gray-500 mt-3 max-w-2xl mx-auto">Technical and soft skills I bring to every project.</p>
    </div>
    <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
        <div>
            <h3 class="text-lg font-bold text-gray-900 mb-4">Technical Skills</h3>
            <div class="flex flex-wrap gap-2 mb-8">
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Laravel</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">PHP</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">MySQL</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">HTML &amp; CSS</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Kotlin</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Kali Linux</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Troubleshoot</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Operating Software</span>
            </div>
            <h3 class="text-lg font-bold text-gray-900 mb-4">Soft Skills</h3>
            <div class="flex flex-wrap gap-2">
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Good Communication</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Team Work</span>
                <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Problem Solving</span>
            </div>
        </div>
        <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6 flex items-center justify-center">
            <canvas id="radarChart" height="260"></canvas>
        </div>
    </div>
</div>
```

- [ ] **Step 3: Tambah/relokasi init Chart.js radar**

Pastikan ada script init radar chart. Hapus init bar chart lama (skillsChart) yang ikut terhapus bersama blok Home di Task 3. Tambahkan sebelum `</body>` (atau pertahankan blok radar yang ada, sesuaikan id `radarChart`):
```html
<script>
    document.addEventListener('DOMContentLoaded', function () {
        const radarCtx = document.getElementById('radarChart');
        if (radarCtx && typeof Chart !== 'undefined') {
            new Chart(radarCtx, {
                type: 'radar',
                data: {
                    labels: ['Web Development', 'Backend', 'Security', 'Problem Solving', 'Communication'],
                    datasets: [{
                        label: 'Skill Areas',
                        data: [85, 80, 70, 80, 85],
                        backgroundColor: 'rgba(59,130,246,0.2)',
                        borderColor: 'rgba(59,130,246,1)',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    scales: { r: { beginAtZero: true, max: 100, ticks: { display: false } } },
                    plugins: { legend: { display: false } }
                }
            });
        }
    });
</script>
```
Catatan: jika init Chart.js lama (line ~699-806) sudah terhapus di Task 3, tambahkan script ini baru. Jika masih ada referensi `skillsChart`, hapus bagian itu agar tidak error null.

- [ ] **Step 4: Verifikasi**

Run: `npm run build` → sukses. Browser: tab Skills tampil badge + radar chart ter-render tanpa error console.

---

### Task 5: Update tab About me (bio, education, certification, kontak) & hapus tab Payment

**Files:**
- Modify: `index.html` (section `tab-about` line ~1234-1396; section `tab-payment` line ~1398-1443; Skills section dalam about line ~1311)

- [ ] **Step 1: Update foto & bio about (line ~1253, ~1270)**

- `alt="Ahwanulm"` → `alt="Reka Adrian"`.
- Ganti bio menjadi:
```html
Hi! I'm Reka Adrian, a Full Stack Web Developer based in Yogyakarta, Indonesia.
I hold a Bachelor's degree in Informatics with experience in technical support,
web systems development, and troubleshooting. I enjoy building functional,
user-focused web solutions and continuously learning new technologies.
```

- [ ] **Step 2: Update lokasi & kontak about (line ~1293, ~1366, ~1383)**

- Lokasi `Lombok, Indonesia` → `Yogyakarta, Indonesia`.
- Link `mailto:ahwanulm1@gmail.com` → `mailto:Adrianreka71@gmail.com`.
- Link Instagram → ganti jadi LinkedIn `https://linkedin.com/in/reka-adrian-4479ab292` (atau GitHub `https://github.com/NOMADEB`). Hapus jejak instagram/ahwanulm.

- [ ] **Step 3: Ganti "Skills Section" dalam about jadi Education & Certification (line ~1311 dst)**

Ganti blok Skills/Tech Stack di dalam about (heading "Tech Stack" line ~1313) dengan Education + Certification:
```html
<div class="mt-8">
    <h3 class="text-lg font-bold text-gray-900 mb-6 text-center">Education</h3>
    <div class="bg-white rounded-2xl shadow-md border border-gray-100 p-6 max-w-2xl mx-auto mb-6">
        <div class="flex items-start justify-between mb-1">
            <h4 class="font-bold text-gray-900">Mercu Buana University of Yogyakarta</h4>
            <span class="text-xs text-gray-400">Aug 2021 - Aug 2025</span>
        </div>
        <p class="text-sm text-gray-500 mb-3">Computer Science</p>
        <ul class="text-gray-500 text-sm space-y-1 list-disc list-inside">
            <li>AI game development</li>
            <li>Godot engine</li>
            <li>Asset creation in RPG games</li>
            <li>AI boss movement creation</li>
        </ul>
    </div>
    <h3 class="text-lg font-bold text-gray-900 mb-4 text-center">Certification</h3>
    <div class="max-w-2xl mx-auto text-center">
        <span class="bg-gray-50 text-gray-700 text-sm px-4 py-2 rounded-full border border-gray-100">Microsoft Azure Basic</span>
    </div>
</div>
```

- [ ] **Step 4: Hapus section tab-payment (line ~1398-1443)**

Hapus seluruh blok `<!-- TAB: PAYMENT -->` + `<section id="tab-payment" ...>...</section>`. Pastikan tidak ada referensi `showTab('payment')` yang tersisa (sudah dihapus di Task 1).

- [ ] **Step 5: Update contact popup (line ~1445 dst) & wa.me**

Dalam `#contactPopup`: ganti semua `ahwanulm1@gmail.com` → `Adrianreka71@gmail.com`, `wa.me/6287875506478` → `wa.me/6287873380473`, `+62 878-7550-6478` → `+62 878-7338-0473`, `t.me/ahwanulm1`/`@ahwanulm1` → LinkedIn atau hapus, `github.com/ahwanulm` → `github.com/NOMADEB`, instagram → hapus. Update teks pesan wa.me yang menyebut "Hi Ahwanulm" → "Hi Reka".

- [ ] **Step 6: Verifikasi build**

Run: `npm run build` → sukses.

---

### Task 6: Verifikasi akhir & bersihkan sisa "Ahwanulm"

**Files:**
- Modify: `index.html` (mana saja yang masih menyebut data lama)

- [ ] **Step 1: Cari sisa referensi lama**

Run: `grep -ni "ahwanulm\|lombok\|amstream\|klipers\|pixelnest\|6287875506478\|t.me/\|instagram\|facebook" index.html`
Expected: tidak ada hasil (atau hanya yang memang disengaja). Perbaiki tiap temuan.

- [ ] **Step 2: Cek referensi tab lama di JS**

Run: `grep -ni "project\|services\|payment" index.html`
Expected: tidak ada `showTab('project'|'services'|'payment')` atau `id="tab-project|services|payment"` yang tersisa. `showTab()` di line ~1557 generik (pakai parameter) jadi tidak perlu diubah, tapi pastikan default `'home'` masih valid.

- [ ] **Step 3: Build final**

Run: `npm run build`
Expected: sukses, `output.css` ter-generate.

- [ ] **Step 4: Verifikasi browser (manual)**

Buka `index.html`. Cek: keempat tab (Home, Experience, Skills, About me) bisa diklik dan kontennya benar; semua link (email, WA, GitHub, LinkedIn, sanurpro) mengarah benar; radar chart render; tidak ada error di console; mobile menu (drawer) menampilkan 4 item. Catat apa yang tidak bisa diverifikasi otomatis.
