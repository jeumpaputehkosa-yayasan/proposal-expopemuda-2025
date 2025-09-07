# proposal-expopemuda-2025
EXPO SUMPAH PEMUDA 2025: Proposal Interaktif Proposal interaktif ini dibuat untuk Expo Sumpah Pemuda 2025 yang diselenggarakan oleh Yayasan Jeumpa Puteh Kosa. Proposal ini bertujuan untuk memberikan informasi yang menarik dan komprehensif kepada calon mitra dan sponsor.
<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EXPO SUMPAH PEMUDA 2025: Proposal Interaktif</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Aceh Serenity -->
    <!-- Application Structure Plan: Menggunakan struktur SPA vertikal dengan navigasi sticky untuk memudahkan eksplorasi. Konten dipecah menjadi beberapa bagian tematik: Hero, Tentang Expo, Target Dampak (KPI divisualisasikan), Detail Acara (zona interaktif & jadwal), Alokasi Anggaran (diagram lingkaran), Peluang Kemitraan, dan Tim. Struktur ini mengubah proposal statis menjadi narasi yang menarik, dimulai dari 'mengapa' (visi), 'apa' (dampak & acara), hingga 'bagaimana' (anggaran & tim), yang lebih efektif untuk menarik minat mitra dan sponsor. -->
    <!-- Visualization & Content Choices: 
        - KPI (Target Dampak): Goal: Inform/Impress -> Method: Dynamic counters (JS) & icons (HTML/Unicode) -> Interaction: Angka beranimasi saat di-scroll -> Justification: Lebih menarik & mudah diingat daripada daftar statis.
        - Event Zones: Goal: Organize/Explore -> Method: Grid kartu interaktif (HTML/Tailwind) -> Interaction: Klik untuk menampilkan detail -> Justification: Mendorong eksplorasi mandiri oleh pengguna.
        - Budget Allocation: Goal: Compare/Inform -> Method: Donut Chart (Chart.js) -> Interaction: Hover untuk tooltip, detail tabel -> Justification: Visualisasi anggaran memberikan pemahaman cepat tentang alokasi dana, penting bagi sponsor.
        - Schedule: Goal: Inform -> Method: Visual timeline (HTML/Tailwind) -> Interaction: Hover effects -> Justification: Lebih mudah dipindai daripada tabel teks.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8f7f2; /* Warm Neutral Background */
            color: #3d3d3d;
        }
        .accent-color { color: #059669; } /* Emerald Green */
        .accent-bg { background-color: #059669; }
        .secondary-bg { background-color: #ffffff; }
        .navbar-scrolled {
            background-color: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 450px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 450px;
        }
        @media (min-width: 768px) {
            .chart-container { height: 400px; }
        }
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .modal-content {
            background-color: white;
            padding: 2.5rem;
            border-radius: 1rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            width: 90%;
            max-width: 700px;
            position: relative;
        }
        .tts-button {
            background-color: transparent;
            border: none;
            padding: 0;
            margin-left: 8px;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header & Navigasi -->
    <header id="navbar" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex-shrink-0">
                    <a href="#hero" class="text-xl font-bold text-gray-800">Jeumpa Puteh Kosa</a>
                </div>
                <div class="hidden md:block">
                    <nav class="ml-10 flex items-baseline space-x-4">
                        <a href="#about" class="px-3 py-2 rounded-md text-sm font-medium text-gray-700 hover:accent-color">Tentang</a>
                        <a href="#impact" class="px-3 py-2 rounded-md text-sm font-medium text-gray-700 hover:accent-color">Dampak</a>
                        <a href="#event" class="px-3 py-2 rounded-md text-sm font-medium text-gray-700 hover:accent-color">Acara</a>
                        <a href="#budget" class="px-3 py-2 rounded-md text-sm font-medium text-gray-700 hover:accent-color">Anggaran</a>
                        <a href="#partner" class="px-3 py-2 rounded-md text-sm font-medium text-gray-700 hover:accent-color">Kemitraan</a>
                    </nav>
                </div>
                <div class="md:hidden">
                    <button id="mobile-menu-button" class="inline-flex items-center justify-center p-2 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none">
                        <span class="sr-only">Open main menu</span>
                        <div class="w-6 h-0.5 bg-gray-600 my-1"></div>
                        <div class="w-6 h-0.5 bg-gray-600 my-1"></div>
                        <div class="w-6 h-0.5 bg-gray-600 my-1"></div>
                    </button>
                </div>
            </div>
        </div>
        <div id="mobile-menu" class="md:hidden hidden">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3 bg-white">
                <a href="#about" class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:accent-color hover:bg-gray-50">Tentang</a>
                <a href="#impact" class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:accent-color hover:bg-gray-50">Dampak</a>
                <a href="#event" class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:accent-color hover:bg-gray-50">Acara</a>
                <a href="#budget" class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:accent-color hover:bg-gray-50">Anggaran</a>
                <a href="#partner" class="block px-3 py-2 rounded-md text-base font-medium text-gray-700 hover:accent-color hover:bg-gray-50">Kemitraan</a>
            </div>
        </div>
    </header>

    <main>
        <!-- Hero Section -->
        <section id="hero" class="relative pt-24 sm:pt-32 pb-16 sm:pb-24 min-h-screen flex items-center">
             <div class="absolute inset-0 bg-gradient-to-b from-stone-100 to-f8f7f2 opacity-50"></div>
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center relative">
                <div class="flex items-center justify-center">
                    <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight text-gray-900">
                        <span class="block">EXPO SUMPAH PEMUDA 2025</span>
                        <span class="block accent-color text-3xl sm:text-4xl lg:text-5xl mt-2">Menebar Harum di Kota Gemilang</span>
                    </h1>
                    <button id="tts-hero" class="tts-button text-4xl accent-color hover:text-emerald-800 transition-colors">✨</button>
                </div>
                <p id="hero-text" class="mt-6 max-w-2xl mx-auto text-lg sm:text-xl text-gray-600">Sebuah platform untuk aksi nyata pemuda dalam merawat kehidupan. Dipersembahkan oleh Yayasan Jeumpa Puteh Kosa.</p>
                <div class="mt-8 text-lg font-semibold text-gray-800">
                    <p>🗓️ 27-28 Oktober 2025 | 📍 Lapangan Blang Padang, Banda Aceh</p>
                </div>
                <div class="mt-10 flex justify-center gap-4">
                    <a href="#partner" class="inline-block accent-bg text-white font-bold py-3 px-8 rounded-lg shadow-lg hover:opacity-90 transition-transform transform hover:scale-105">Jadi Mitra Kami</a>
                    <a href="#event" class="inline-block bg-white text-gray-800 font-bold py-3 px-8 rounded-lg shadow-lg hover:bg-gray-50 transition-transform transform hover:scale-105">Lihat Rangkaian Acara</a>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="py-20 secondary-bg">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center">
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Tentang Expo Sumpah Pemuda 2025</h2>
                    <p id="about-text" class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
                        Proyek ini lahir dari semangat Sumpah Pemuda untuk menggerakkan aksi nyata. Terinspirasi dari filosofi bunga Jeumpa Puteh, simbol keharuman dan ketulusan, kami bertujuan menyebarkan dampak positif dari pemuda Aceh untuk Indonesia.
                    </p>
                    <button id="tts-about" class="tts-button text-2xl accent-color hover:text-emerald-800 transition-colors">✨ Dengarkan</button>
                </div>
                <div class="mt-16 grid grid-cols-1 md:grid-cols-3 gap-12 text-center">
                    <div class="p-6">
                        <div class="text-4xl accent-color mb-4">✨</div>
                        <h3 class="text-xl font-semibold mb-2">Visi Kami</h3>
                        <p class="text-gray-600">Menjadi episentrum gerakan pemuda paling berpengaruh di Aceh pada tahun 2025, yang mendorong lahirnya solusi nyata untuk tantangan sosial dan ekonomi.</p>
                    </div>
                    <div class="p-6">
                        <div class="text-4xl accent-color mb-4">🎯</div>
                        <h3 class="text-xl font-semibold mb-2">Misi Kami</h3>
                        <p class="text-gray-600">Memfasilitasi inspirasi, pemberdayaan, aksi kemanusiaan, dan kolaborasi melalui expo dua hari yang menghubungkan pemuda kreatif dengan para pemangku kebijakan.</p>
                    </div>
                    <div class="p-6">
                         <div class="text-4xl accent-color mb-4">🚀</div>
                        <h3 class="text-xl font-semibold mb-2">Momentum Penting</h3>
                        <p class="text-gray-600">Expo ini sekaligus menjadi deklarasi publik eksistensi Yayasan Jeumpa Puteh Kosa sebagai inkubator pemberdayaan pemuda yang kredibel dan berdampak.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Impact/KPI Section -->
        <section id="impact" class="py-20 bg-stone-100">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Target Dampak yang Ingin Dicapai</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
                        Kami menetapkan target yang terukur untuk memastikan acara ini memberikan manfaat nyata dan berkelanjutan bagi masyarakat.
                    </p>
                </div>
                <div id="kpi-section" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-8 text-center">
                    <div class="p-6 secondary-bg rounded-xl shadow-md">
                        <div class="text-4xl mb-2">👥</div>
                        <p class="text-4xl font-extrabold accent-color kpi-number" data-target="3000">0</p>
                        <p class="text-gray-600 font-medium">Pengunjung</p>
                    </div>
                    <div class="p-6 secondary-bg rounded-xl shadow-md">
                        <div class="text-4xl mb-2">🎓</div>
                        <p class="text-4xl font-extrabold accent-color kpi-number" data-target="200">0</p>
                        <p class="text-gray-600 font-medium">Peserta Lokakarya</p>
                    </div>
                    <div class="p-6 secondary-bg rounded-xl shadow-md">
                        <div class="text-4xl mb-2">🛍️</div>
                        <p class="text-4xl font-extrabold accent-color kpi-number" data-target="50">0</p>
                        <p class="text-gray-600 font-medium">UMKM & Komunitas</p>
                    </div>
                    <div class="p-6 secondary-bg rounded-xl shadow-md">
                        <div class="text-4xl mb-2">🩸</div>
                        <p class="text-4xl font-extrabold accent-color kpi-number" data-target="150">0</p>
                        <p class="text-gray-600 font-medium">Kantong Darah</p>
                    </div>
                    <div class="p-6 secondary-bg rounded-xl shadow-md col-span-2 lg:col-span-1">
                        <div class="text-4xl mb-2">🤝</div>
                        <p class="text-4xl font-extrabold accent-color kpi-number" data-target="5">0</p>
                        <p class="text-gray-600 font-medium">MoU Strategis</p>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Event Details Section -->
        <section id="event" class="py-20 secondary-bg">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Jelajahi Rangkaian Acara</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
                        EXPO SUMPAH PEMUDA 2025 adalah sebuah pengalaman yang terbagi dalam lima zona tematik. Setiap zona dirancang untuk memenuhi misi kami, mulai dari menginspirasi ide baru hingga melakukan aksi nyata. Klik setiap zona untuk menemukan aktivitas unik di dalamnya.
                    </p>
                </div>
                <!-- Zones -->
                <div id="zone-container" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-6">
                </div>
                 <!-- Schedule -->
                <div class="mt-20">
                    <h3 class="text-2xl font-bold text-center mb-10">Jadwal Acara</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                        <!-- Day 1 -->
                        <div>
                            <h4 class="text-xl font-bold border-b-2 border-emerald-600 pb-2 mb-6">Hari 1: Senin, 27 Oktober 2025 (Pemberdayaan & Kolaborasi)</h4>
                            <ul class="space-y-4">
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">☀️ Pagi:</span> <span>Grand Opening, Deklarasi Ikrar Pemuda, Panggung Kolaborasi (MoU).</span></li>
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">☀️ Siang:</span> <span>Lokakarya Intensif (Digital Marketing & AI, Personal Branding), Klinik Bisnis, Talkshow Inspiratif.</span></li>
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">🌙 Malam:</span> <span>Malam Apresiasi Budaya & Networking Night.</span></li>
                            </ul>
                        </div>
                        <!-- Day 2 -->
                        <div>
                            <h4 class="text-xl font-bold border-b-2 border-emerald-600 pb-2 mb-6">Hari 2: Selasa, 28 Oktober 2025 (Aksi & Kontribusi)</h4>
                            <ul class="space-y-4">
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">☀️ Pagi:</span> <span>Funbike "Gowes Menebar Semangat".</span></li>
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">🔄 Seharian:</span> <span>Aksi Donor Darah, Expo UMKM & Komunitas Kreatif.</span></li>
                                <li class="flex items-start"><span class="accent-color font-bold mr-3">🌇 Sore:</span> <span>UMKM & Community Showcase, Upacara Penutupan, Grand Launching Program Unggulan Yayasan.</span></li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Budget Section -->
        <section id="budget" class="py-20 bg-stone-100">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Alokasi Anggaran Proyek</h2>
                     <p class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
                        Dengan total anggaran Rp 100.000.000, kami memastikan setiap dana dialokasikan secara efisien dan transparan untuk memaksimalkan dampak acara.
                    </p>
                </div>
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                    <div class="chart-container">
                        <canvas id="budgetChart"></canvas>
                    </div>
                    <div class="overflow-x-auto">
                       <table class="min-w-full bg-white rounded-lg shadow">
                           <thead class="accent-bg text-white">
                               <tr>
                                   <th class="text-left py-3 px-4 uppercase font-semibold text-sm">Komponen</th>
                                   <th class="text-right py-3 px-4 uppercase font-semibold text-sm">Estimasi (IDR)</th>
                               </tr>
                           </thead>
                           <tbody class="text-gray-700">
                                <tr>
                                    <td class="text-left py-3 px-4">Acara & Konten</td>
                                    <td class="text-right py-3 px-4 font-mono">45.000.000</td>
                                </tr>
                                <tr class="bg-gray-50">
                                    <td class="text-left py-3 px-4">Operasional & Logistik</td>
                                    <td class="text-right py-3 px-4 font-mono">30.000.000</td>
                                </tr>
                                <tr>
                                    <td class="text-left py-3 px-4">Publikasi & Promosi</td>
                                    <td class="text-right py-3 px-4 font-mono">15.000.000</td>
                                </tr>
                                <tr class="bg-gray-50">
                                    <td class="text-left py-3 px-4">Kesekretariatan & Administrasi</td>
                                    <td class="text-right py-3 px-4 font-mono">5.000.000</td>
                                </tr>
                                <tr>
                                    <td class="text-left py-3 px-4">Biaya Tak Terduga</td>
                                    <td class="text-right py-3 px-4 font-mono">5.000.000</td>
                                </tr>
                                <tr class="font-bold border-t-2">
                                     <td class="text-left py-4 px-4">Total Anggaran</td>
                                     <td class="text-right py-4 px-4 font-mono">100.000.000</td>
                                </tr>
                           </tbody>
                       </table>
                    </div>
                </div>
            </div>
        </section>

        <!-- Partnership Section -->
        <section id="partner" class="py-24 secondary-bg">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Mari Berkolaborasi!</h2>
                <p id="partner-text" class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
                    EXPO SUMPAH PEMUDA 2025 adalah investasi kolektif untuk masa depan pemuda Aceh. Kami mengundang perusahaan, lembaga, dan instansi untuk menjadi bagian dari gerakan nyata ini.
                </p>
                <button id="tts-partner" class="tts-button text-2xl accent-color hover:text-emerald-800 transition-colors">✨ Dengarkan</button>
                 <div class="mt-12 flex flex-col items-center max-w-lg mx-auto p-8 rounded-xl bg-gray-50 shadow-inner">
                    <p class="text-gray-700 mb-4">Ingin bermitra? Masukkan nama perusahaan Anda untuk membuat draf email perkenalan otomatis.</p>
                    <input type="text" id="companyInput" placeholder="Nama Perusahaan Anda..." class="w-full px-4 py-2 mb-4 rounded-md border border-gray-300 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                    <button id="generateEmailBtn" class="w-full accent-bg text-white font-bold py-3 px-8 rounded-lg shadow-lg hover:opacity-90 transition-transform transform hover:scale-105">
                        ✨ Buat Draf Email Kemitraan
                    </button>
                    <p id="copyMessage" class="mt-4 text-sm text-emerald-600 hidden">Draf berhasil disalin ke clipboard!</p>
                </div>
                <div class="mt-12 flex flex-col sm:flex-row justify-center gap-4">
                     <a href="mailto:jeumpaputehkosa@gmail.com?subject=Kemitraan Expo Sumpah Pemuda 2025" class="inline-block accent-bg text-white font-bold py-4 px-10 rounded-lg shadow-xl hover:opacity-90 transition-transform transform hover:scale-105 text-lg">Hubungi Via Email</a>
    <a href="tel:+6281313555666" class="inline-block bg-gray-50 text-gray-800 font-bold py-4 px-10 rounded-lg shadow-xl hover:bg-gray-100 transition-transform transform hover:scale-105 text-lg">Hubungi Via Telepon</a>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-gray-800 text-white">
        <div class="container mx-auto py-12 px-4 sm:px-6 lg:px-8">
            <div class="text-center">
                <h3 class="text-lg font-semibold">Yayasan Jeumpa Puteh Kosa</h3>
                <p class="mt-2 text-gray-400">Jl. Rawasakti barat lorong IX no. 02 perumnas lingke, Kec. Syiah Kuala Kota Banda Aceh, Provinsi Aceh, Indonesia.</p>
                <p class="mt-1 text-gray-400">Telepon: +62 813-1355-5666</p>
                <p class="mt-4 text-sm text-gray-500">&copy; 2025 Yayasan Jeumpa Puteh Kosa. Seluruh hak cipta dilindungi.</p>
            </div>
        </div>
    </footer>

    <!-- Modal for Email Draft -->
    <div id="emailModal" class="modal-overlay hidden">
        <div class="modal-content">
            <h3 class="text-2xl font-bold mb-4">Draf Email Kemitraan</h3>
            <p class="text-gray-600 mb-4">Draf ini dibuat secara otomatis. Silakan salin, tempel, dan edit sesuai kebutuhan Anda.</p>
            <textarea id="emailDraftTextarea" rows="10" class="w-full p-4 border rounded-lg resize-none focus:outline-none focus:ring-2 focus:ring-emerald-500"></textarea>
            <div class="mt-6 flex justify-end space-x-4">
                <button id="copyEmailBtn" class="bg-emerald-600 text-white font-bold py-2 px-6 rounded-lg hover:bg-emerald-700 transition">Salin Draf</button>
                <button id="closeModalBtn" class="bg-gray-300 text-gray-800 font-bold py-2 px-6 rounded-lg hover:bg-gray-400 transition">Tutup</button>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            document.querySelectorAll('#mobile-menu a').forEach(link => {
                link.addEventListener('click', () => {
                    mobileMenu.classList.add('hidden');
                });
            });

            const navbar = document.getElementById('navbar');
            window.addEventListener('scroll', () => {
                if (window.scrollY > 50) {
                    navbar.classList.add('navbar-scrolled');
                } else {
                    navbar.classList.remove('navbar-scrolled');
                }
            });

            const kpiObserver = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const kpiNumbers = document.querySelectorAll('.kpi-number');
                        kpiNumbers.forEach(numberEl => {
                            const target = +numberEl.getAttribute('data-target');
                            const duration = 2000;
                            const stepTime = Math.abs(Math.floor(duration / target));
                            let current = 0;
                            const timer = setInterval(() => {
                                current += 1;
                                numberEl.innerText = current.toLocaleString('id-ID');
                                if (current === target) {
                                    clearInterval(timer);
                                    numberEl.innerText = target.toLocaleString('id-ID') + (target === 3000 || target === 200 ? '+' : '');
                                }
                            }, stepTime < 1 ? 1 : stepTime);
                        });
                        observer.unobserve(entry.target);
                    }
                });
            }, { threshold: 0.5 });
            const kpiSection = document.getElementById('kpi-section');
            if(kpiSection) kpiObserver.observe(kpiSection);

            const zoneData = [
                { name: "Panggung Gemilang", icon: "🌟", desc: "Panggung utama untuk seremonial, talkshow inspiratif, dan pertunjukan seni budaya." },
                { name: "Ruang Berkarya", icon: "💡", desc: "Paviliun khusus untuk lokakarya intensif (Digital Marketing & AI) dan klinik konsultasi bisnis gratis." },
                { name: "Pasar Harapan", icon: "🛒", desc: "Area bazaar untuk pameran dan penjualan produk UMKM kreatif serta showcase komunitas." },
                { name: "Oase Kebaikan", icon: "❤️", desc: "Area steril dan profesional yang didedikasikan untuk kegiatan donor darah bersama PMI." },
                { name: "Arena Semangat", icon: "🚴", desc: "Titik pusat kegiatan olahraga, termasuk start/finish Funbike 'Gowes Menebar Semangat'." }
            ];

            const zoneContainer = document.getElementById('zone-container');
            zoneData.forEach(zone => {
                const zoneEl = document.createElement('div');
                zoneEl.className = 'p-6 secondary-bg rounded-xl shadow-lg hover:shadow-2xl hover:-translate-y-2 transition-all duration-300 cursor-pointer text-center';
                zoneEl.innerHTML = `
                    <div class="text-6xl mb-4">${zone.icon}</div>
                    <h4 class="text-xl font-bold mb-2">${zone.name}</h4>
                    <p class="text-gray-600">${zone.desc}</p>
                `;
                zoneContainer.appendChild(zoneEl);
            });

            const ctx = document.getElementById('budgetChart');
            if (ctx) {
                new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                        labels: ['Acara & Konten', 'Operasional & Logistik', 'Publikasi & Promosi', 'Administrasi', 'Tak Terduga'],
                        datasets: [{
                            label: 'Alokasi Anggaran',
                            data: [45, 30, 15, 5, 5],
                            backgroundColor: [
                                'rgba(5, 150, 105, 0.8)',
                                'rgba(13, 148, 136, 0.8)',
                                'rgba(15, 118, 110, 0.8)',
                                'rgba(20, 83, 45, 0.8)',
                                'rgba(163, 163, 163, 0.8)'
                            ],
                            borderColor: '#ffffff',
                            borderWidth: 3
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: {
                                position: 'bottom',
                                labels: {
                                    padding: 20,
                                    font: {
                                        size: 14,
                                        family: "'Inter', sans-serif"
                                    }
                                }
                            },
                            tooltip: {
                                callbacks: {
                                    label: function(context) {
                                        let label = context.label || '';
                                        if (label) {
                                            label += ': ';
                                        }
                                        if (context.parsed !== null) {
                                            label += new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(context.parsed * 1000000) + ' (' + context.parsed + '%)';
                                        }
                                        return label;
                                    }
                                }
                            }
                        },
                        cutout: '60%'
                    }
                });
            }

            // Gemini API Integration for Email Generation
            const generateEmailBtn = document.getElementById('generateEmailBtn');
            const companyInput = document.getElementById('companyInput');
            const emailModal = document.getElementById('emailModal');
            const emailDraftTextarea = document.getElementById('emailDraftTextarea');
            const copyEmailBtn = document.getElementById('copyEmailBtn');
            const closeModalBtn = document.getElementById('closeModalBtn');
            const copyMessage = document.getElementById('copyMessage');
            
            // New logic to handle closing the modal
            emailModal.addEventListener('click', (event) => {
                if (event.target === emailModal) {
                    emailModal.classList.add('hidden');
                    copyMessage.classList.add('hidden');
                }
            });

            closeModalBtn.addEventListener('click', () => {
                emailModal.classList.add('hidden');
                copyMessage.classList.add('hidden');
            });


            generateEmailBtn.addEventListener('click', async () => {
                const companyName = companyInput.value.trim() || "Calon Mitra";
                
                generateEmailBtn.innerHTML = 'Membuat Draf...';
                generateEmailBtn.disabled = true;

                try {
                    const prompt = `Buat draf email profesional yang singkat untuk mengajukan kemitraan kepada perusahaan bernama "${companyName}". 
                    Tujuan email adalah untuk memperkenalkan "EXPO SUMPAH PEMUDA 2025: Menebar Harum di Kota Gemilang" yang diselenggarakan oleh Yayasan Jeumpa Puteh Kosa. 
                    Sebutkan secara singkat bahwa expo ini adalah platform pemberdayaan pemuda, wirausaha, dan aksi sosial (donor darah). 
                    Akhiri dengan ajakan untuk berdiskusi lebih lanjut tentang peluang kolaborasi yang saling menguntungkan. 
                    Format draf email ini dengan subjek yang menarik dan isi yang ringkas. Jangan sertakan salam pembuka, salam penutup, atau nama pengirim di dalam draf.`;
                    
                    const payload = {
                        contents: [{ parts: [{ text: prompt }] }],
                        generationConfig: {
                            responseMimeType: "text/plain",
                        },
                        model: "gemini-2.5-flash-preview-05-20"
                    };

                    const apiKey = ""; 
                    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;

                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    const result = await response.json();
                    const text = result.candidates?.[0]?.content?.parts?.[0]?.text;

                    if (text) {
                        emailDraftTextarea.value = text;
                        emailModal.classList.remove('hidden');
                    } else {
                        emailDraftTextarea.value = "Maaf, terjadi kesalahan saat membuat draf. Silakan coba lagi.";
                        emailModal.classList.remove('hidden');
                    }

                } catch (error) {
                    emailDraftTextarea.value = "Maaf, terjadi kesalahan saat membuat draf. Silakan coba lagi.";
                    emailModal.classList.remove('hidden');
                } finally {
                    generateEmailBtn.innerHTML = '✨ Buat Draf Email Kemitraan';
                    generateEmailBtn.disabled = false;
                }
            });

            copyEmailBtn.addEventListener('click', () => {
                emailDraftTextarea.select();
                document.execCommand('copy');
                copyMessage.classList.remove('hidden');
            });

            // New Gemini API Integration for Text-to-Speech (TTS)
            const heroTTSBtn = document.getElementById('tts-hero');
            const aboutTTSBtn = document.getElementById('tts-about');
            const partnerTTSBtn = document.getElementById('tts-partner');
            const audioPlayer = new Audio();
            let isPlaying = false;
            let currentPlayingButton = null;

            function base64ToArrayBuffer(base64) {
                const binaryString = atob(base64);
                const len = binaryString.length;
                const bytes = new Uint8Array(len);
                for (let i = 0; i < len; i++) {
                    bytes[i] = binaryString.charCodeAt(i);
                }
                return bytes.buffer;
            }

            function pcmToWav(pcmData, sampleRate) {
                const dataLength = pcmData.length * 2;
                const buffer = new ArrayBuffer(44 + dataLength);
                const view = new DataView(buffer);

                function writeString(view, offset, string) {
                    for (let i = 0; i < string.length; i++) {
                        view.setUint8(offset + i, string.charCodeAt(i));
                    }
                }

                writeString(view, 0, 'RIFF'); // ChunkID
                view.setUint32(4, 36 + dataLength, true); // ChunkSize
                writeString(view, 8, 'WAVE'); // Format
                writeString(view, 12, 'fmt '); // Subchunk1ID
                view.setUint32(16, 16, true); // Subchunk1Size
                view.setUint16(20, 1, true); // AudioFormat (1=PCM)
                view.setUint16(22, 1, true); // NumChannels
                view.setUint32(24, sampleRate, true); // SampleRate
                view.setUint32(28, sampleRate * 2, true); // ByteRate
                view.setUint16(32, 2, true); // BlockAlign
                view.setUint16(34, 16, true); // BitsPerSample
                writeString(view, 36, 'data'); // Subchunk2ID
                view.setUint32(40, dataLength, true); // Subchunk2Size

                const pcm16 = new Int16Array(buffer, 44);
                pcm16.set(pcmData);

                return new Blob([view], { type: 'audio/wav' });
            }

            async function generateAndPlayTTS(text, button) {
                if (isPlaying) {
                    audioPlayer.pause();
                    audioPlayer.currentTime = 0;
                    isPlaying = false;
                    if (currentPlayingButton) {
                        currentPlayingButton.innerHTML = '✨ Dengarkan';
                        currentPlayingButton.disabled = false;
                    }
                    if (currentPlayingButton === button) {
                        currentPlayingButton = null;
                        return;
                    }
                }

                button.innerHTML = '...';
                button.disabled = true;
                currentPlayingButton = button;

                try {
                    const prompt = `Baca teks berikut: ${text}`;
                    const payload = {
                        contents: [{
                            parts: [{ text: prompt }]
                        }],
                        generationConfig: {
                            responseModalities: ["AUDIO"],
                            speechConfig: {
                                voiceConfig: {
                                    prebuiltVoiceConfig: { voiceName: "Kore" }
                                }
                            }
                        },
                        model: "gemini-2.5-flash-preview-tts"
                    };

                    const apiKey = "";
                    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${apiKey}`;

                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    const result = await response.json();
                    const part = result?.candidates?.[0]?.content?.parts?.[0];
                    const audioData = part?.inlineData?.data;
                    const mimeType = part?.inlineData?.mimeType;

                    if (audioData && mimeType && mimeType.startsWith("audio/L16")) {
                        const sampleRate = parseInt(mimeType.match(/rate=(\d+)/)[1], 10);
                        const pcmData = new Int16Array(base64ToArrayBuffer(audioData));
                        const wavBlob = pcmToWav(pcmData, sampleRate);
                        const audioUrl = URL.createObjectURL(wavBlob);
                        
                        audioPlayer.src = audioUrl;
                        audioPlayer.play();
                        isPlaying = true;

                        audioPlayer.onended = () => {
                            isPlaying = false;
                            button.innerHTML = '✨ Dengarkan';
                            button.disabled = false;
                            currentPlayingButton = null;
                        };
                    } else {
                        console.error("Failed to get audio data from API response.");
                        button.innerHTML = 'Gagal';
                    }
                } catch (error) {
                    console.error("Error generating or playing audio:", error);
                    button.innerHTML = 'Gagal';
                }
            }

            // Attaching event listeners to TTS buttons
            heroTTSBtn.addEventListener('click', () => {
                const text = `Expo Sumpah Pemuda 2025. Menebar harum di Kota Gemilang. ${document.getElementById('hero-text').innerText}`;
                generateAndPlayTTS(text, heroTTSBtn);
            });
            aboutTTSBtn.addEventListener('click', () => {
                generateAndPlayTTS(document.getElementById('about-text').innerText, aboutTTSBtn);
            });
            partnerTTSBtn.addEventListener('click', () => {
                generateAndPlayTTS(document.getElementById('partner-text').innerText, partnerTTSBtn);
            });
        });
    </script>
</body>
</html>
