# PANDUAN MENJALANKAN HSSE VISION GUARD DI GOOGLE COLAB

Dokumen ini merupakan panduan resmi untuk menjalankan purwarupa sistem **HSSE Vision Guard** menggunakan lingkungan komputasi Google Colab. Seluruh modul aplikasi, termasuk antarmuka Streamlit dan model deteksi YOLOv8, telah dipaketkan ke dalam satu berkas *notebook* mandiri (*self-contained notebook*) untuk memudahkan proses pengujian dan evaluasi tanpa perlu konfigurasi lokal tambahan.

## Prasyarat
- Akun Google (untuk akses Google Colab)
- Koneksi internet stabil
- Browser modern (Chrome/Firefox direkomendasikan)

---

## LANGKAH 1: Mengunggah Notebook ke Colab

1. Buka [Google Colab](https://colab.research.google.com/) melalui browser Anda.
2. Pada jendela *popup* awal, pilih *tab* **"Upload"**.
3. Pilih dan unggah berkas `HSSE_Vision_Guard_Colab.ipynb` dari repositori ini ke dalam platform.

---

## LANGKAH 2: Inisialisasi Sistem (Eksekusi Cell)

Berkas `.ipynb` ini dirancang untuk melakukan *deployment* secara otomatis. Proses inisialisasi akan mengunduh dependensi pustaka, memuat model AI praletih (*pre-trained* YOLOv8 *nano*), dan menyusun fail inti aplikasi (`app.py`) ke dalam mesin virtual Colab secara dinamis.

1. Setelah berkas terbuka, jalankan seluruh perintah eksekusi dengan mengklik menu **Runtime > Run all** (Jalankan semua) pada bilah navigasi atas.
2. Tunggu sekitar 2-3 menit hingga proses instalasi modul (seperti Streamlit, Ultralytics, dan Plotly) selesai secara keseluruhan. 
3. Pastikan proses berjalan hingga tuntas tanpa memunculkan pesan galat (*error*) pada hasil keluaran *cell* pertama.

---

## LANGKAH 3: Mengakses Antarmuka Aplikasi (Dashboard)

Aplikasi *HSSE Vision Guard* dijalankan pada *localhost* server Colab. Untuk menayangkan antarmuka (*User Interface*) aplikasi ke peramban (browser) Anda, diperlukan pembuatan jalur akses publik menggunakan *Localtunnel*.

1. Buka menu Colab di bagian atas: **Runtime > Manage Sessions** (Kelola Sesi).
2. Pada daftar sesi yang aktif, klik tombol **"New terminal"** (Terminal baru).
3. Di dalam terminal yang terbuka pada panel bawah, ketik perintah berikut dan tekan *Enter*:
   ```bash
   npx localtunnel --port 8501
   ```
4. Terminal akan memproses jalur (*tunnel*) dan menampilkan sebuah tautan publik (contoh: `https://some-random-words.loca.lt`). Klik tautan tersebut untuk membukanya di *tab* baru.
5. **Verifikasi Keamanan:** Layanan Localtunnel mewajibkan pengguna untuk memasukkan *Endpoint IP* server. 
   - Untuk mengetahui IP publik mesin Colab Anda, ketik perintah `curl ipv4.icanhazip.com` di dalam terminal Colab yang sama (tekan ikon **+** untuk menambah tab terminal jika perlu). 
   - Salin angka IP yang dimunculkan, tempel (*paste*) ke kolom input di halaman Localtunnel, dan tekan **Submit**.
6. Dasbor interaktif *HSSE Vision Guard* akan langsung dimuat.

---

## PANDUAN PENGUJIAN MODUL

Setelah sistem berhasil diakses secara penuh, Anda dapat menguji seluruh fungsionalitas purwarupa melalui bilah navigasi kiri (*sidebar*):

1. **Dashboard Overview:** Menampilkan analitik metrik keselamatan terpadu dan indikator insiden.
2. **APD Detector:** Modul evaluasi *Computer Vision*. Unggah (*upload*) gambar pekerja lapangan untuk menguji tingkat kepercayaan (*confidence*) deteksi model dalam mengenali atribut keselamatan.
3. **Risk Predictor:** Modul simulasi kalkulasi risiko berbasis input dinamis (usia alat, skor pemeliharaan, cuaca).
4. **UAV Simulator:** Tinjauan simulasi *waypoint* inspeksi fasilitas menggunakan kapabilitas nirawak.

---

## PENYELESAIAN MASALAH (TROUBLESHOOTING)

- **Aplikasi Terputus (Timeout):** Jika jalur Localtunnel terputus secara *idle*, hentikan proses di terminal dengan kombinasi `Ctrl+C`, kemudian jalankan kembali perintah `npx localtunnel --port 8501`.
- **IP Address Ditolak:** Pastikan IP yang disubmit adalah IP publik server mesin Colab (melalui perintah `curl`), BUKAN IP jaringan internet lokal Anda.
- **ModuleNotFoundError:** Apabila terindikasi kegagalan pemuatan pustaka pihak ketiga, ulangi proses inisialisasi dengan mengklik **Run All** sekali lagi.

---
*Dikembangkan untuk HSSE Innovation Challenge 2026.*
