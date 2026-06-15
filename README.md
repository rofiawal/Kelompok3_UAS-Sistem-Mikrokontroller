## 📖 Latar Belakang & Deskripsi Proyek

Proyek **SAPI BERITA (Sistem Absensi & Akses Pintar Berbasis Enkripsi Real Time)** ini dikembangkan sebagai pemenuhan Tugas Akhir (UAS) untuk mata kuliah Sistem Mikrokontroler. 

Sistem ini dirancang untuk memberikan solusi terhadap kelemahan sistem presensi manual dan manajemen kunci ruangan konvensional yang seringkali rentan terhadap manipulasi data (seperti titip absen) serta minimnya pencatatan riwayat akses. Dengan memanfaatkan ekosistem **Internet of Things (IoT)**, kami mengintegrasikan mikrokontroler **ESP32-CAM** dan sensor pembaca **RFID (RC522)** untuk menciptakan otomasi kehadiran terpusat.

Fokus utama dari pengembangan prototipe ini tidak hanya sekadar membaca kartu, melainkan menitikberatkan pada:
1. **Keamanan Transmisi Data (Enkripsi):** Menerapkan pengamanan pada data ID kartu untuk mencegah risiko kloning identitas atau pencurian data akses.
2. **Pemantauan Real-Time:** Setiap log aktivitas (waktu masuk, identitas, dan status izin) akan langsung dikirimkan ke *database* melalui jaringan Wi-Fi, memungkinkan administrator untuk memantau pergerakan akses kapan saja.
3. **Interaksi Pengguna yang Intuitif:** Dilengkapi dengan antarmuka visual (LCD I2C dan indikator LED) serta audio (Buzzer) untuk memberikan respons instan kepada pengguna terkait status akses mereka (Diterima/Ditolak).

Melalui proyek ini, diharapkan dapat tercipta sebuah infrastruktur keamanan ruangan dan presensi yang lebih efisien, akurat, dan terpercaya.

## 👥 Anggota Kelompok 3
* **Muhammad Rofi Awaluddin (23552011025)** 
* **Muhammad Yusuf Firdaus**
* **Sandy Wijaya Sugiarto**
  
## 🛠️ Komponen Hardware dan Fungsinya
Untuk merealisasikan sistem "SAPI BERITA" ini, kami menggunakan perangkat keras berikut:

* **ESP32-CAM:** Sebagai mikrokontroler utama yang menjadi "otak" sistem. Modul ini memproses data, menangani koneksi Wi-Fi ke *database*, dan menggunakan kameranya untuk pemantauan visual.
* **Modul RFID (RC522):** Sebagai pemindai (*scanner*) yang berfungsi membaca data terenkripsi dari kartu identitas pengguna.
* **Kartu RFID (Tags/Mifare):** Token fisik (seperti ID Card/KTM) yang dipegang pengguna untuk melakukan proses *tap* absensi.
* **LCD I2C 16x2:** Layar antarmuka untuk menampilkan instruksi dan status secara *real-time* kepada pengguna (contoh: "Silakan Tap Kartu" atau "Akses Diterima").
* **Buzzer 5V:** Memberikan indikator audio atau *feedback* suara (misal: bunyi *beep* pendek saat absen berhasil, atau *beep* panjang peringatan saat kartu tidak dikenali).
* **LED (Merah & Hijau):** Sebagai indikator visual tambahan. LED Hijau menyala saat akses diizinkan, dan LED Merah menyala jika akses ditolak.
* **Breadboard:** Papan *prototyping* untuk merangkai semua komponen elektronik di atas secara sementara tanpa memerlukan proses penyolderan.
* **Kabel Jumper (Male-to-Male/Male-to-Female):** Kabel penghubung untuk mengalirkan arus listrik dan jalur komunikasi data antar komponen di *breadboard*.

## 💻 Kebutuhan Software & Web Dashboard serta fungsinya
Selain perangkat keras, sistem ini didukung oleh tumpukan perangkat lunak (*software stack*) untuk memproses logika alat dan menyediakan antarmuka web (*dashboard*) bagi administrator.

**1. Pemrograman Mikrokontroler:**
*   **Arduino IDE / VS Code:** Lingkungan pengembangan terpadu (IDE) yang digunakan untuk menulis, mengompilasi, dan mengunggah (*flashing*) kode program C/C++ ke dalam memori ESP32-CAM.

**2. Pengembangan Web Dashboard & Database:**
*   **Laravel (PHP):** *Framework backend* yang akan digunakan untuk membangun logika situs web, mengamankan sesi *login* admin, dan memproses data absensi yang masuk.
*   **MySQL:** Sistem manajemen basis data relasional untuk menyimpan data identitas mahasiswa, kredensial kartu RFID (yang sudah terenkripsi), serta mencatat riwayat log absensi (*waktu masuk dan keluar*).
*   **HTML, CSS, JavaScript & Bootstrap:** Digunakan untuk membangun *frontend* atau antarmuka visual *dashboard* web agar tampilannya interaktif, modern, dan responsif (bisa dibuka di laptop maupun *smartphone*).

**3. Protokol Komunikasi (IoT):**
*   **REST API / HTTP GET & POST:** Protokol komunikasi yang digunakan oleh modul ESP32-CAM untuk mengirimkan paket data hasil pemindaian RFID melalui jaringan Wi-Fi langsung ke *server* web.

## 📋 Rencana Alur Kerja (Timeline Proyek)

**Fase 1: Persiapan & Perancangan (Perangkat Keras)**
- [x] Membuat Repository GitHub 
- [x] Menentukan ide, judul proyek, dan kebutuhan komponen
- [x] Membeli dan mengumpulkan komponen hardware (ESP32-CAM, RFID, LCD, dll) tetapi beberapa ada yang belum
- [ ] Merancang skema *wiring* (diagram kabel) secara keseluruhan

**Fase 2: Pengembangan Perangkat Keras (IoT)**
- [ ] Menulis kode dasar pengenalan dan pembacaan RFID RC522 pada ESP32
- [ ] Menulis program kontrol aktuator dan indikator (LCD I2C, Buzzer, LED)
- [ ] Mengonfigurasi koneksi jaringan Wi-Fi pada mikrokontroler

**Fase 3: Pengembangan Software & Web Dashboard**
- [ ] Merancang struktur *Database* MySQL (tabel *users*, *rfid_cards*, *logs*)
- [ ] Membangun *Backend* menggunakan Framework Laravel
- [ ] Merancang *Frontend Dashboard* interaktif (Halaman Login, Tabel Absensi, dll)
- [ ] Membuat REST API untuk jalur komunikasi antara alat dan *server* web

**Fase 4: Integrasi & Keamanan Sistem**
- [ ] Mengintegrasikan pengiriman data absensi dari ESP32 ke Web *Database* secara *real-time*
- [ ] Mengaktifkan fitur kamera ESP32-CAM untuk menangkap gambar saat *tap* kartu
- [ ] Menerapkan sistem keamanan enkripsi pada pengiriman data identitas

**Fase 5: Pengujian & Penyelesaian (Finishing)**
- [ ] Melakukan pengujian sistem secara menyeluruh (*System Testing & Bug Fixing*)
- [ ] Merapikan instalasi kabel perangkat keras ke dalam wadah pelindung (*casing*)
- [ ] Menyusun Laporan Akhir UAS dan dokumentasi proyek
- [ ] Membuat video demonstrasi atau persiapan presentasi akhir
