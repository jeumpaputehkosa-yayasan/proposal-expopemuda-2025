# proposal-expopemuda-2025
EXPO SUMPAH PEMUDA 2025: Proposal Interaktif Proposal interaktif ini dibuat untuk Expo Sumpah Pemuda 2025 yang diselenggarakan oleh Yayasan Jeumpa Puteh Kosa. Proposal ini bertujuan untuk memberikan informasi yang menarik dan komprehensif kepada calon mitra dan sponsor.
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Proposal Expo Pemuda 2025</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0fff4; /* Warna hijau muda yang sangat cerah (Off-white) */
            color: #2d3748; /* Warna teks abu-abu gelap */
        }
        .container {
            max-width: 1000px;
        }
        /* Style card untuk section */
        .card {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
            border: 1px solid #e2e8f0;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
        }
        /* Style untuk tombol utama (dominant green) */
        .btn-primary {
            background-color: #5cb85c; /* Hijau yang lebih menarik */
            color: white;
            border-radius: 9999px;
            padding: 8px 28px; /* Mengedit ukuran tombol menjadi lebih tipis */
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px #4cae4c;
        }
        .btn-primary:hover {
            background-color: #4cae4c;
            transform: translateY(-2px);
            box-shadow: 0 6px #3e8e41;
        }
        .btn-primary:active {
            box-shadow: 0 2px #3e8e41;
            transform: translateY(2px);
        }
        /* Style untuk tombol sekunder (black) */
        .btn-secondary {
            background-color: #212121; /* Hitam */
            color: white;
            border-radius: 9999px;
            padding: 8px 28px; /* Mengedit ukuran tombol menjadi lebih tipis */
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px #000000;
        }
        .btn-secondary:hover {
            background-color: #333333;
            transform: translateY(-2px);
            box-shadow: 0 6px #111111;
        }
        .btn-secondary:active {
            box-shadow: 0 2px #111111;
            transform: translateY(2px);
        }
        /* Style untuk modal (pop-up) */
        .modal {
            display: none;
        }
        .modal-overlay {
            background-color: rgba(0, 0, 0, 0.6);
        }
        .modal-content {
            animation: slide-up 0.3s ease-out;
        }
        @keyframes slide-up {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        /* Style untuk pesan notifikasi "Tersalin!" */
        .copy-message {
            display: none;
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #16a34a;
            color: white;
            padding: 8px 24px;
            border-radius: 9999px;
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.3s ease-in-out;
        }
        .copy-message.show {
            display: block;
            opacity: 1;
        }
    </style>
</head>
<body class="p-6 sm:p-10">

    <!-- Modal untuk Draft Email -->
    <div id="emailModal" class="modal fixed inset-0 z-50 flex items-center justify-center p-4">
        <div class="modal-overlay absolute inset-0"></div>
        <div class="modal-content relative w-full max-w-lg p-8 bg-white rounded-2xl shadow-xl">
            <h3 class="text-xl font-semibold mb-4 text-gray-800">Draf Email Kemitraan</h3>
            <p class="text-sm text-gray-600 mb-6">Draf ini dibuat secara otomatis. Silakan salin, tempel, dan edit sesuai kebutuhan Anda.</p>
            <div id="emailDraftText" class="p-6 bg-gray-100 rounded-xl text-sm text-gray-800 leading-relaxed"></div>
            <div class="mt-8 flex justify-end space-x-3">
                <button onclick="copyToClipboard()" class="btn-primary flex items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M8 3a1 1 0 011-1h2a1 1 0 110 2H9a1 1 0 01-1-1z" />
                        <path d="M5 4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2V6a2 2 0 00-2-2H5zm7 2h-1V4h1a2 2 0 012 2v2a2 2 0 01-2 2h-1V6z" />
                        <path d="M9 13a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1z" />
                        <path fill-rule="evenodd" d="M12 11h-2v2h2V11z" clip-rule="evenodd" />
                        <path fill-rule="evenodd" d="M14 13h-2v2h2V13z" clip-rule="evenodd" />
                        <path fill-rule="evenodd" d="M16 13h-2v2h2V13z" clip-rule="evenodd" />
                    </svg>
                    Salin Draf
                </button>
                <button onclick="closeModal()" class="btn-secondary">
                    Tutup
                </button>
            </div>
        </div>
    </div>
    
    <!-- Notifikasi "Tersalin!" -->
    <div id="copyMessage" class="copy-message rounded-full text-sm">Tersalin!</div>

    <!-- Halaman Utama -->
    <div class="container mx-auto">
        <!-- Kepala Halaman dengan Gambar -->
        <header class="mb-10">
            <img src="Logo Yayasan Jeumpa Puteh Kosa.jpg" alt="Logo Yayasan Jeumpa Puteh Kosa" class="w-2/3 md:w-1/4 h-auto mx-auto mb-8 rounded-full shadow-lg transition-transform duration-300 hover:scale-105">
            <img src="Poster Expo Pemuda Kosa.jpg" alt="Poster Expo Pemuda Kosa 2025" class="w-full h-auto rounded-3xl shadow-xl transition-transform duration-300 hover:scale-105">
        </header>

        <main class="space-y-12 px-4 sm:px-0">
            <!-- Tentang Expo -->
            <section class="card p-8 sm:p-10">
                <h2 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-4">Tentang Expo</h2>
                <p class="text-gray-700 leading-relaxed text-justify">
                    Proposal interaktif ini dibuat untuk Expo Sumpah Pemuda 2025 yang diselenggarakan oleh Yayasan Jeumpa Puteh Kosa. Expo ini bertujuan untuk memberikan informasi yang menarik dan komprehensif kepada calon mitra dan sponsor.
                </p>
            </section>

            <!-- Informasi Yayasan -->
            <section class="card p-8 sm:p-10">
                <h2 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-4">Informasi Yayasan</h2>
                <div class="grid md:grid-cols-2 gap-8">
                    <div>
                        <h3 class="font-semibold text-xl text-gray-700">Struktur Pengurus</h3>
                        <ul class="list-disc list-inside mt-4 text-gray-600 space-y-2">
                            <li> Ketua Pembina: Ali Mulyagusdin</li>
                            <li> Wakil Pembina: T. Arafat</li>
                            <li> Ketua: Abdi Indra</li>
                            <li> Sekretaris: M. Azis</li>
                            <li> Bendahara: Mada Philea</li>
                            <li> Ketua Pengawas: T. Subhan</li>
                            <li> Wakil Pengawas : Edo Mara Nasution</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="font-semibold text-xl text-gray-700">Alamat Yayasan</h3>
                        <p class="mt-4 text-gray-600">
                            Jl. Rawasakti barat lorong IX no. 02 perumnas lingke, Kec. Syiah Kuala Kota Banda Aceh, Provinsi Aceh, Indonesia.
                        </p>
                    </div>
                </div>
                <!-- Memindahkan tombol ke bagian ini -->
                <hr class="my-8 border-t-2 border-gray-200">
                <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4 justify-center items-center">
                    <a href="tel:+6281313555666" class="btn-primary flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                            <path d="M2 3a1 1 0 011-1h2a1 1 0 01.996.906L8 5.75l.004-.055a1 1 0 011.832 0l.004.055L12 5.75l2.004-.844A1 1 0 0115 5h2a1 1 0 011 1v1a1 1 0 01-1 1h-2a1 1 0 01-1-1v-1a1 1 0 00-.996-.906L12 5.25l-.004.055a1 1 0 01-1.832 0L8 5.25l-2.004.844A1 1 0 015 6H3a1 1 0 01-1-1V3z" />
                            <path d="M2 13a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 01-1 1H3a1 1 0 01-1-1v-2zM8 13a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 01-1 1h-2a1 1 0 01-1-1v-2zM14 13a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 01-1 1h-2a1 1 0 01-1-1v-2z" />
                        </svg>
                        Hubungi Kami
                    </a>
                    <a href="mailto:jeumpaputehkosa@gmail.com" class="btn-primary flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                            <path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z" />
                            <path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z" />
                        </svg>
                        Kirim Email
                    </a>
                </div>
            </section>

            <!-- Bagian Lainnya (seperti Anggaran, Kemitraan) - Anda bisa tambahkan lebih banyak di sini -->
            <section class="card p-8 sm:p-10">
                <h2 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-4">Rancangan Anggaran</h2>
                <p class="text-gray-700 leading-relaxed text-justify">
                    Kami telah menyusun rancangan anggaran yang transparan dan terperinci untuk memastikan setiap dukungan yang diberikan digunakan secara efektif. Kami sangat terbuka untuk berdiskusi mengenai alokasi dana dan menyesuaikannya dengan kebutuhan dan preferensi mitra kami. Silakan hubungi kami untuk mendapatkan dokumen lengkap.
                </p>
            </section>

            <!-- Bagian Kemitraan -->
            <section class="card p-8 sm:p-10 flex flex-col items-center text-center">
                <h2 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-6">Kemitraan</h2>
                <p class="text-gray-700 leading-relaxed mb-8 max-w-xl">
                    Tertarik menjadi mitra atau sponsor? Klik tombol di bawah ini untuk melihat proposal lengkap atau hubungi kami untuk mendapatkan draf email.
                </p>
                <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
                    <a href="proposal-expo-pemuda-2025.md" class="btn-secondary flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                            <path fill-rule="evenodd" d="M4 4a2 2 0 012-2h8a2 2 0 012 2v12a2 2 0 01-2 2H6a2 2 0 01-2-2V4zm2-1a1 1 0 00-1 1v12a1 1 0 001 1h8a1 1 0 001-1V4a1 1 0 00-1-1H6z" clip-rule="evenodd" />
                            <path d="M8 8a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1zm0 4a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1zm0 4a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1z" />
                        </svg>
                        Lihat Lampiran
                    </a>
                    <button onclick="openModal()" class="btn-secondary flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                            <path d="M8 3a1 1 0 011-1h2a1 1 0 110 2H9a1 1 0 01-1-1z" />
                            <path d="M5 4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2V6a2 2 0 00-2-2H5zm7 2h-1V4h1a2 2 0 012 2v2a2 2 0 01-2 2h-1V6z" />
                            <path d="M9 13a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1z" />
                            <path fill-rule="evenodd" d="M12 11h-2v2h2V11z" clip-rule="evenodd" />
                            <path fill-rule="evenodd" d="M14 13h-2v2h2V13z" clip-rule="evenodd" />
                            <path fill-rule="evenodd" d="M16 13h-2v2h2V13z" clip-rule="evenodd" />
                        </svg>
                        Buat Draf Email
                    </button>
                </div>
            </section>
        </main>

        <!-- Footer dengan warna latar hitam dan teks putih -->
        <footer class="mt-12 text-center text-sm bg-black text-white p-6 rounded-t-3xl">
            <p>&copy; 2025 Yayasan Jeumpa Puteh Kosa</p>
        </footer>
    </div>

    <script>
        const openModal = () => {
            document.getElementById('emailModal').classList.remove('hidden');
            const emailDraft = `Assalamu'alaikum Warrahmatullahi Wabarakatuh.

Kepada Yth. Bapak Walikota Banda Aceh,

Dengan hormat,

Bersama ini kami Yayasan Jeumpa Puteh Kosa, sebuah organisasi yang bergerak di bidang Pendidikan, Kesehatan dan lingkungan yang berbasis sosial, mengajukan proposal untuk Expo Sumpah Pemuda 2025. Expo ini bertujuan untuk memperkenalkan program-program yayasan, memperluas jaringan, dan menginspirasi kolaborasi positif.

Kami percaya kerja sama dengan Ibu Walikota Banda Aceh akan memberikan nilai tambah yang signifikan bagi acara ini. Sebagai mitra, kami menawarkan berbagai paket kemitraan yang dapat disesuaikan.

Lampiran terlampir adalah proposal lengkap kami. Kami sangat menantikan kesempatan untuk berdiskusi lebih lanjut dengan Anda.

Terima kasih atas perhatian dan waktu Bapak.

Hormat kami,

Abdi Indra
Ketua Yayasan Jeumpa Puteh Kosa`;
            document.getElementById('emailDraftText').innerText = emailDraft;
        };

        const closeModal = () => {
            document.getElementById('emailModal').classList.add('hidden');
        };

        const copyToClipboard = () => {
            const emailDraftText = document.getElementById('emailDraftText').innerText;
            const tempInput = document.createElement('textarea');
            tempInput.value = emailDraftText;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);

            // Tampilkan pesan "Tersalin!"
            const message = document.getElementById('copyMessage');
            message.classList.add('show');
            setTimeout(() => {
                message.classList.remove('show');
            }, 2000);
        };
        
        // Menutup modal ketika overlay diklik
        document.getElementById('emailModal').addEventListener('click', (event) => {
            if (event.target.id === 'emailModal' || event.target.classList.contains('modal-overlay')) {
                closeModal();
            }
        });
    </script>
</body>
</html>

