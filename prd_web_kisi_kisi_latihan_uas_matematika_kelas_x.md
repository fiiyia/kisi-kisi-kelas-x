# Product Requirements Document (PRD)
## Portal Kisi-Kisi & Latihan Interaktif UAS Matematika SMA Kelas X

| Informasi Dokumen | Detail |
| :--- | :--- |
| **Nama Produk** | MathPrep X — Portal Kisi-Kisi & Latihan UAS Matematika Kelas X |
| **Versi Dokumen** | 1.0 |
| **Tanggal** | 23 November 2026 |
| **Target Pengguna** | Siswa SMA Kelas X (Fase E) & Guru Matematika |
| **Status** | Draft Siap Pengembangan |

---

## 1. Ringkasan Eksekutif & Tujuan Produk

### 1.1 Latar Belakang
Untuk mempersiapkan siswa SMA Kelas X menghadapi Ujian Akhir Semester (UAS) Ganjil Matematika (alokasi 120 menit), siswa membutuhkan panduan belajar terstruktur berupa kisi-kisi resmi sekaligus sarana latihan mandiri. Latihan soal yang efektif harus mencerminkan struktur, proporsi materi, dan tingkat kesulitan ujian asli, namun tetap menggunakan konteks cerita, angka, serta variasi penyelesaian yang berbeda agar siswa benar-benar memahami konsep—bukan sekadar menghafal kunci jawaban.

### 1.2 Tujuan Produk
1. **Transparansi Materi:** Menyajikan kisi-kisi UAS Matematika Kelas X (Eksponen & Logaritma $30\%$, SPtLDV $50\%$, dan Persamaan Kuadrat $20\%$) secara rapi dan mudah dipahami siswa.
2. **Latihan Paralel (Anti-Bocoran):** Menyediakan paket latihan soal interaktif dengan tipe yang identik dengan UAS (Isian Singkat Narasi/LKPD, Menjodohkan, dan Uraian HOTS), tetapi menggunakan konteks dan parameter soal yang dimodifikasi.
3. **Akuntabilitas Siswa:** Mewajibkan pengisian identitas (**Nama Lengkap** dan **Kelas**) sehingga hasil latihan dapat dijadikan bukti belajar mandiri bagi guru.
4. **Umpan Balik Langsung:** Memberikan koreksi otomatis untuk soal objektif serta panduan langkah penyelesaian (pembahasan) dan rubrik penilaian mandiri untuk soal uraian.

---

## 2. Target Pengguna

1. **Siswa SMA Kelas X (Pengguna Utama):**
   * Membutuhkan akses cepat melalui ponsel (mobile-first) maupun laptop tanpa perlu membuat akun/password yang rumit.
   * Membutuhkan tampilan persamaan matematika (pangkat, logaritma basis kiri atas ala buku Erlangga seperti ${}^a\log b$, pertidaksamaan) dan grafik DHP yang jelas terbaca.
2. **Guru Matematika (Pengguna Sekunder / Fasilitator):**
   * Membutuhkan bukti bahwa siswa telah mengerjakan latihan (melalui laporan hasil yang memuat Nama, Kelas, waktu pengerjaan, dan skor).
   * Memastikan soal latihan tidak identik dengan naskah UAS asli.

---

## 3. Alur Pengguna (User Flow)

1. **Halaman Masuk / Identitas Siswa:**
   * Siswa membuka tautan web dan mengisi formulir wajib: **Nama Lengkap** dan **Kelas** (misalnya pilihan dropdown atau input teks seperti `X-1`, `X-2`, dst.).
   * Opsional: Memilih mode latihan (**Mode Belajar Santai** tanpa batas waktu atau **Mode Simulasi UAS** dengan hitung mundur 120 menit).
2. **Dashboard Utama (Navigasi Tab):**
   * **Tab 1: Kisi-Kisi UAS** — Menampilkan ringkasan proporsi materi, rincian indikator soal per bagian, dan catatan rumus penting.
   * **Tab 2: Latihan Soal** — Terbagi dalam 3 bagian terstruktur (Bagian I: Isian Narasi/LKPD, Bagian II: Menjodohkan, Bagian III: Uraian HOTS).
3. **Pengerjaan & Penyimpanan Otomatis:**
   * Jawaban siswa tersimpan otomatis di `localStorage` browser agar tidak hilang jika halaman tidak sengaja ter-refresh.
4. **Halaman Hasil & Pembahasan:**
   * Siswa menekan tombol **"Selesai & Periksa Jawaban"**.
   * Sistem menampilkan **Kartu Hasil Latihan** berisi Nama, Kelas, Tanggal/Jam selesai, Skor Bagian I & II, Evaluasi Mandiri Bagian III, serta rincian penguasaan per topik (Eksponen & Logaritma, SPtLDV, Persamaan Kuadrat).
   * Siswa dapat membaca pembahasan langkah demi langkah dan menekan tombol **"Cetak / Simpan PDF"** atau **"Salin Laporan"** untuk diserahkan ke guru.

---

## 4. Persyaratan Fungsional (Functional Requirements)

### FR-01: Formulir Identitas Siswa
* **Input Nama Lengkap:** Wajib diisi (minimal 3 karakter, validasi tidak boleh hanya spasi).
* **Input Kelas:** Wajib diisi/dipilih (format dapat dikonfigurasi guru, misalnya dropdown `X-1` sampai `X-12` atau input teks bebas dengan placeholder `Contoh: X-3`).
* Identitas siswa harus selalu tampil di *header* halaman selama pengerjaan dan tercantum jelas pada halaman laporan hasil akhir.
* Tersedia tombol **"Ganti Identitas / Reset Latihan"** dengan dialog konfirmasi.

### FR-02: Halaman Kisi-Kisi UAS Interaktif
* Menampilkan kartu ringkasan proporsi materi dan bobot skor:
  * **Eksponen & Logaritma:** $30\%$ (6 butir / 30 poin).
  * **Sistem Pertidaksamaan Linear Dua Variabel (SPtLDV):** $50\%$ (10 butir / 50 poin).
  * **Persamaan Kuadrat (Pemfaktoran & Rumus ABC):** $20\%$ (4 butir / 20 poin).
* Menampilkan tabel kisi-kisi lengkap berisi:
  * Materi Pokok & Submateri.
  * Bentuk Soal (Isian Narasi, Menjodohkan, Uraian HOTS).
  * Indikator Pencapaian Kompetensi (tanpa membocorkan angka/cerita soal UAS).
  * Level Kognitif (C2–C5) dan Tips Mengerjakan.
* Fitur **Filter per Materi** agar siswa bisa fokus mempelajari satu topik terlebih dahulu.

### FR-03: Modul Latihan Soal (3 Bagian)
* **Bagian I — Isian Singkat Berbasis Narasi / LKPD (10 Isian, Bobot 30 Poin):**
  * Soal berbentuk paragraf cerita/studi kasus dengan kotak input langsung di dalam teks (*fill-in-the-blank*).
  * Validasi jawaban cerdas (*smart grading*): menoleransi perbedaan spasi, pemisah ribuan (misalnya `4000` atau `4.000`), tanda desimal (`,` atau `.`), serta format penulisan pertidaksamaan sederhana (misalnya `x+y<=10` atau `x + y <= 10`).
  * Menyediakan tombol simbol bantuan cepat ($\le$, $\ge$) di dekat kotak input soal pertidaksamaan agar siswa mudah mengetik di ponsel.
* **Bagian II — Menjodohkan (5 Soal dengan 7 Opsi A–G, Bobot 20 Poin):**
  * Menampilkan 5 pernyataan/soal (termasuk 1 soal berbasis gambar grafik DHP) di sisi kiri dan 7 pilihan jawaban (A–G, terdiri dari 5 jawaban benar dan 2 pengecoh) di sisi kanan.
  * Interaksi menggunakan *dropdown* per nomor atau sistem klik-pasangkan (*tap-to-match*) agar nyaman di layar sentuh ponsel maupun desktop.
* **Bagian III — Uraian HOTS (5 Soal, Bobot 50 Poin):**
  * Menyediakan kotak teks jawaban untuk menuliskan langkah penyelesaian serta kotak input jawaban akhir.
  * Khusus soal SPtLDV yang meminta menggambar DHP, disediakan **Kanvas Sketsa Koordinat Interaktif** (opsional/sederhana untuk memplot titik potong dan arsir) atau panduan menggambar di kertas buram lalu mencocokkan dengan grafik kunci pada tahap pembahasan.
  * Sistem penilaian menggunakan kombinasi **cek jawaban akhir otomatis** dan **Rubrik Penilaian Mandiri (*Self-Assessment Checklist*)** per langkah (misalnya: "Apakah model matematika sudah benar?", "Apakah titik pojok sudah tepat?", "Apakah kesimpulan sudah ditulis?").

### FR-04: Visualisasi Rumus Matematika & Grafik
* Seluruh notasi matematika dirender dengan pustaka LaTeX (seperti KaTeX) agar rapi, termasuk notasi logaritma basis kiri atas ala buku Erlangga (contoh: ${}^2\log 32$, ${}^3\log 27$).
* Grafik DHP pada soal latihan dirender menggunakan **SVG vektor yang presisi** (garis koordinat, label sumbu $X$ dan $Y$, angka skala, titik potong, serta arsiran DHP yang kontras dan ramah cetak).

### FR-05: Timer & Navigasi Soal
* Indikator progres pengerjaan (misalnya: `12 / 20 Butir Terisi`).
* Timer opsional (120 menit) dengan opsi jeda (*pause*) atau sembunyikan agar tidak membuat siswa panik saat mode belajar mandiri.

### FR-06: Halaman Rekap, Pembahasan & Ekspor Bukti
* Menampilkan ringkasan skor per bagian dan grafik/bar persentase penguasaan tiap materi (Eksponen & Logaritma, SPtLDV, Persamaan Kuadrat).
* Menampilkan rekomendasi belajar otomatis berdasarkan materi dengan skor terendah.
* Pembahasan lengkap untuk setiap nomor baru muncul setelah siswa menekan tombol submit.
* Tombol **"Cetak / Simpan PDF"** (`window.print()` dengan CSS khusus `@media print` yang rapi) yang memuat Nama, Kelas, tanggal/waktu pengerjaan, skor total, dan rincian jawaban.

---

## 5. Spesifikasi Konten: Prinsip Variasi Soal Latihan

Agar latihan efektif tanpa membocorkan naskah UAS asli, soal latihan wajib mengikuti prinsip **Isomorfik Berbeda Konteks**: indikator kompetensi dan tingkat kesulitan setara dengan kisi-kisi UAS, tetapi konteks cerita, koefisien, arah optimasi, atau variasi aljabarnya berbeda.

| Bagian & Materi | Kisi-Kisi UAS Asli (Referensi) | Variasi untuk Web Latihan (Mirip Konsep, Berbeda Soal) |
| :--- | :--- | :--- |
| **Bag. I — Narasi 1** (Eksponen & Logaritma, 3 isian) | Pertumbuhan bakteri $N(t) = 250 \cdot 2^t$, mencari nilai fungsi, persamaan eksponen sederhana, dan logaritma ${}^2\log$. | **Pertumbuhan Investasi / Tabungan atau Pelipatan Viewer Video:** Misal fungsi $V(t) = 100 \cdot 3^t$ (kelipatan 3), mencari nilai saat $t=3$, mencari $t$ saat $V(t) = 8.100$, dan taksiran ${}^3\log 18$ dengan diketahui ${}^3\log 2 \approx 0,63$. |
| **Bag. I — Narasi 2** (SPtLDV, 5 isian + Grafik 1) | Paket perlengkapan ujian koperasi ($x + y \le 8$, $2x + y \le 12$), titik potong, dan laba maksimum. | **Produksi Kerajinan OSIS (Gantungan Kunci & Pin):** Misal kendala bahan dan waktu $x + y \le 10$ dan $x + 3y \le 18$, menentukan titik potong sumbu, titik pojok $(6, 4)$, dan pendapatan maksimum dengan grafik SVG baru. |
| **Bag. I — Narasi 3** (Persamaan Kuadrat, 2 isian) | Luas taman baca persegi panjang dengan selisih sisi 5 m ($x^2 + 5x - 84 = 0$). | **Desain Panggung Pentas Seni / Lapangan Mini:** Persegi panjang dengan panjang $(x + 4)$ meter dan lebar $x$ meter, luas $96\text{ m}^2$ menghasilkan $x^2 + 4x - 96 = 0$, melengkapi pemfaktoran dan menentukan lebar/keliling. |
| **Bag. II — No. 11–15** (Menjodohkan A–G) | Persamaan eksponen basis 3, sifat ${}^3\log$, baca grafik DHP tertutup, nilai minimum titik pojok, akar PK dengan $a=2$. | Basis eksponen diubah (misal $4^{x+1} = 8^{x-1}$), sifat ${}^2\log$, grafik DHP baru (misal melalui $(0,8)$–$(4,0)$ dan $(0,5)$–$(10,0)$), uji nilai **maksimum** dari titik pojok yang diberikan, dan pemfaktoran PK $3x^2 + 5x - 2 = 0$ + 2 pengecoh baru. |
| **Bag. III — No. 16** (Uraian Eksponen & Logaritma) | Peluruhan zat radioaktif $M(t) = 240 \cdot \left(\frac{1}{2}\right)^t$, mencari sisa massa, persamaan eksponen, dan batas aman dengan ${}^2\log 3$. | **Penyusutan Nilai Mesin / Peluruhan Konsentrasi Obat:** Misal dosis obat $D(t) = 320 \cdot \left(\frac{1}{2}\right)^t$ mg setiap 1 jam. Mencari sisa setelah 4 jam, waktu saat tersisa 10 mg, dan taksiran waktu saat tersisa 20 mg atau 30 mg menggunakan ${}^2\log 5 \approx 2,32$ untuk menyimpulkan jadwal konsumsi berikutnya. |
| **Bag. III — No. 17** (Uraian SPtLDV dari Grafik) | Menentukan SPtLDV, titik pojok, dan nilai minimum dari grafik DHP terbuka ke kanan atas. | Grafik DHP **terbuka** dengan garis batas berbeda (misal melalui $(0, 12)$–$(4, 0)$ dan $(0, 6)$–$(9, 0)$) dan fungsi objektif baru $f(x, y) = 5x + 3y$, menentukan sistem pertidaksamaan, titik pojok, dan nilai minimum. |
| **Bag. III — No. 18** (Uraian Cerita SPtLDV Maksimum) | Ibu Rina memproduksi Kue Lapis & Brownies (kendala tepung & gula), gambar DHP, cari laba maksimum. | **Usaha Minuman Sehat / Konveksi Jaket & Kaus:** Kendala dua bahan baku dengan satuan berbeda (misal liter & mililiter, atau meter & sentimeter) untuk menguji ketelitian konversi satuan, menggambar DHP tertutup, dan mencari keuntungan maksimum. |
| **Bag. III — No. 19** (Uraian Cerita SPtLDV Minimum + Keputusan HOTS) | Sewa Mobil Pikap & Van untuk bantuan bencana + cek kecukupan anggaran. | **Pembelian Paket Pupuk Pertanian / Suplemen Nutrisi:** Memenuhi kebutuhan minimum zat A dan zat B dari Pupuk X dan Pupuk Y, menggambar DHP terbuka, mencari biaya minimum, lalu mengevaluasi apakah anggaran petani mencukupi atau berapa kekurangannya. |
| **Bag. III — No. 20** (Uraian Persamaan Kuadrat) | a) Pemfaktoran $a > 1$, b) Rumus ABC bentuk akar, c) Soal cerita jalan setapak mengelilingi kolam. | a) Pemfaktoran $2x^2 + 7x - 15 = 0$, b) Rumus ABC $x^2 - 4x + 1 = 0$ atau $3x^2 - 6x + 2 = 0$ (hasil bentuk akar sederhana), c) **Bingkai Foto / Margin Poster:** Sebuah poster berukuran $12\text{ cm} \times 8\text{ cm}$ diberi bingkai/margin seragam selebar $x\text{ cm}$ di sekelilingnya sehingga luas total menjadi $192\text{ cm}^2$. |

---

## 6. Persyaratan Non-Fungsional & Rekomendasi Teknis

### 6.1 Non-Fungsional
* **Responsif (Mobile-First):** Tata letak harus nyaman digunakan di layar smartphone ($360\text{ px}$) maupun desktop ($1280\text{ px}$+). Tabel menjodohkan otomatis berubah menjadi tampilan tumpuk (*card-based*) pada layar kecil.
* **Ringan & Cepat:** Waktu muat awal $< 2$ detik pada koneksi 4G standar siswa.
* **Persistensi Data Lokal:** Seluruh progres (Nama, Kelas, dan isian soal) tersimpan di `localStorage` sehingga aman dari refresh tidak sengaja.
* **Ramah Cetak:** Halaman hasil latihan memiliki gaya cetak khusus agar bersih saat disimpan ke PDF oleh siswa.

### 6.2 Rekomendasi Arsitektur Teknis
* **Frontend:** Single-Page Application (SPA) menggunakan HTML5/React + Tailwind CSS.
* **Math Rendering:** **KaTeX** (lebih cepat dan ringan dibanding MathJax untuk aplikasi web interaktif).
* **Grafik DHP:** Inline **SVG** yang digenerate secara matematis agar koordinat, garis potong, dan arsiran 100% akurat tanpa pecah saat diperbesar.
* **Penyimpanan & Pengumpulan (Fase 1 / MVP):** Client-side (`localStorage`) + fitur Cetak PDF / Salin Ringkasan WhatsApp/Google Classroom.
* **Integrasi Opsional (Fase 2):** Pengiriman data skor otomatis ke **Google Sheets** melalui Google Apps Script Webhook (berisi kolom: Timestamp, Nama, Kelas, Skor Bag. I, Skor Bag. II, Skor Mandiri Bag. III, Total Skor).

---

## 7. Panduan Desain UI/UX

* **Skema Warna:** Nuansa edukatif dan tenang (misal biru navy/indigo sebagai warna utama, latar belakang abu-abu sangat terang `#F8FAFC`, hijau emerald untuk jawaban benar, dan merah lembut untuk koreksi).
* **Tipografi:** Font sans-serif yang jelas dibaca (seperti *Inter* atau *Plus Jakarta Sans*) untuk teks soal, dipadukan dengan font serif matematika dari KaTeX untuk rumus.
* **Umpan Balik Visual:**
  * Badge status di setiap nomor (`Belum Dijawab`, `Sudah Diisi`, `Benar`, `Perlu Dicek`).
  * Peringatan ramah jika siswa mencoba menekan tombol "Selesai" saat masih ada nomor yang kosong.

---

## 8. Metrik Keberhasilan & Rencana Pengembangan

### 8.1 Metrik Keberhasilan
* **Tingkat Penyelesaian:** $\ge 80\%$ siswa yang mengisi Nama dan Kelas menyelesaikan seluruh 3 bagian latihan hingga halaman hasil.
* **Kesiapan Ujian:** Siswa mampu mengenali pola soal tiap bagian (Isian Narasi, Menjodohkan, Uraian HOTS) dan memahami kesalahan konsep melalui pembahasan otomatis.

### 8.2 Roadmap Pengembangan
* **Tahap 1 (MVP — Siap Pakai Langsung):**
  * Form Nama & Kelas.
  * Halaman Kisi-Kisi UAS Lengkap (sesuai dokumen UAS).
  * 1 Paket Latihan Soal Lengkap (20 butir paralel) + 3 Grafik SVG + Auto-grading Bagian I & II + Rubrik & Pembahasan Bagian III + Cetak PDF Bukti Latihan.
* **Tahap 2 (Pengembangan Lanjutan):**
  * Integrasi rekap otomatis ke Google Sheets untuk guru.
  * Penambahan Paket Latihan B (variasi soal kedua) untuk remedial atau latihan tambahan.