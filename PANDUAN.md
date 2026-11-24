# Asisten Pribadi: panduan pasang gratis

Isi folder ini adalah website lengkap. Tidak perlu server, database berbayar, atau kode tambahan.

| File | Gunanya |
|---|---|
| index.html | Aplikasinya |
| manifest.webmanifest, icon-*.png | Supaya bisa dipasang di HP seperti aplikasi |
| sw.js | Supaya tetap terbuka saat sinyal hilang, dan untuk notifikasi |
| firestore.rules | Aturan keamanan, hanya dipakai bila Anda mengaktifkan sinkron Firebase |

---

## 1. Online-kan gratis (pilih salah satu)

### A. Netlify Drop (paling mudah, ±2 menit)
1. Ekstrak file zip sampai muncul folder **asisten-pribadi**.
2. Buka **https://app.netlify.com/drop**, lalu masuk atau daftar gratis (bisa dengan akun Google/GitHub).
3. Seret folder **asisten-pribadi** ke kotak di halaman itu.
4. Selesai. Anda mendapat alamat seperti `https://nama-acak.netlify.app`.
5. Supaya alamatnya mudah diingat: **Site configuration → Change site name**, misalnya `asisten-saya` sehingga menjadi `asisten-saya.netlify.app`.
6. Untuk memperbarui aplikasi nanti: menu **Deploys**, lalu seret folder versi baru ke kotak "Drag and drop".

### B. GitHub Pages
1. Buat repository baru di GitHub, misalnya `asisten-pribadi`.
2. Upload semua file di folder ini (Add file → Upload files).
3. **Settings → Pages → Branch: main / root → Save**.
4. Alamatnya: `https://NAMA-GITHUB.github.io/asisten-pribadi/`.

> Aplikasi harus dibuka lewat alamat `https://`. Membuka index.html langsung dari folder komputer tetap bisa dipakai, tetapi fitur pasang di HP dan notifikasi tidak aktif.

---

## 2. Pasang di HP seperti aplikasi
- **Android (Chrome):** buka alamat website, tekan tombol **Pasang aplikasi** di atas atau menu ⋮ → **Instal aplikasi / Tambahkan ke layar utama**.
- **iPhone (Safari):** tombol Bagikan → **Tambah ke Layar Utama**. Notifikasi di iPhone hanya berjalan bila dibuka dari ikon di layar utama (iOS 16.4 ke atas).
- Lalu buka menu **Pengingat → Izinkan notifikasi**.

### Tentang pengingat
- Notifikasi muncul selama aplikasi terbuka atau masih berjalan di latar belakang, lengkap dengan tombol "Kirim ke WA".
- Agar HP tetap berbunyi walaupun aplikasi ditutup, buka **Data & ekspor → Ekspor ke kalender HP**, lalu buka file .ics tersebut di Google Calendar atau kalender iPhone. Pengingat otomatis ikut menjadi alarm. Ulangi ekspor setiap kali ada jadwal baru.
- **Kirim ke WA** membuka WhatsApp dengan pesan yang sudah tersusun. Anda tinggal memilih grup lalu menekan kirim. WhatsApp tidak mengizinkan pengiriman ke grup secara otomatis tanpa layanan bisnis berbayar.

---

## 3. (Opsional) Sinkron HP dan laptop dengan Firebase, gratis tanpa kartu kredit
Tanpa langkah ini, data tersimpan di browser masing-masing perangkat. Gunakan **Unduh cadangan** secara berkala.

1. Buka **https://console.firebase.google.com**, lalu **Create a project** (misalnya `asisten-pribadi`). Google Analytics boleh dimatikan. Tetap di paket **Spark (gratis)**.
2. **Build → Authentication → Get started → Sign-in method → Google → Enable → Save**.
3. Masih di Authentication, buka **Settings → Authorized domains → Add domain**, lalu isi alamat website Anda, misalnya `asisten-saya.netlify.app`.
4. **Build → Firestore Database → Create database**. Pilih lokasi `asia-southeast2 (Jakarta)` dan **production mode**.
5. Di Firestore buka tab **Rules**, hapus isinya, tempel isi file **firestore.rules**, lalu **Publish**.
6. Klik ikon roda gigi → **Project settings → Your apps →** ikon **</>** (Web) → beri nama → **Register app**. Salin seluruh bagian `firebaseConfig = { ... }`.
7. Di aplikasi buka **Data & ekspor → Sinkron antar perangkat**, tempel konfigurasinya, lalu tekan **Simpan & sambungkan**.
8. Tekan **Masuk dengan Google** di bagian atas. Data yang sudah ada di perangkat ikut diunggah otomatis.
9. Di HP/laptop lain: buka alamat yang sama, tempel konfigurasi yang sama, lalu masuk dengan akun Google yang sama.

Batas gratis Firebase (1 GiB data, 20.000 penulisan per hari) jauh di atas kebutuhan pemakaian pribadi.

---

## 4. (Opsional) Baca foto lebih pintar dengan Gemini
Tanpa langkah ini, foto dan PDF hasil scan dibaca dengan OCR gratis di perangkat. Hasilnya bagus untuk teks rapi, tetapi kurang untuk tabel rumit atau tulisan tangan.

1. Buka **https://aistudio.google.com**, masuk dengan akun Google, lalu **Get API key → Create API key**.
2. Di aplikasi buka **Data & ekspor → Baca foto lebih pintar**, tempel key-nya, lalu tekan **Tes koneksi**.
3. Bila muncul pesan model tidak ditemukan, salin nama model "Flash" terbaru dari AI Studio ke kolom **Model**.

**Penting soal kerahasiaan:** pada paket gratis, Google dapat memakai data yang dikirim untuk meningkatkan produknya. Untuk berkas perkara yang rahasia, kosongkan API key supaya dokumen dibaca dengan OCR di perangkat saja dan tidak dikirim ke mana pun.

---

## 5. Kebiasaan aman
- Unduh cadangan (Data & ekspor → Unduh cadangan) sebulan sekali, terutama bila tidak memakai Firebase.
- Menghapus data browser atau riwayat situs akan menghapus data lokal, kecuali Anda memakai Firebase.
