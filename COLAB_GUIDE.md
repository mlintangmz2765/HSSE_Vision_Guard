# PANDUAN MENJALANKAN HSSE VISION GUARD DI GOOGLE COLAB

## Prasyarat
- Akun Google (untuk akses Google Colab)
- Koneksi internet stabil
- Browser (Chrome/Firefox direkomendasikan)

---

## LANGKAH 1: Persiapan File

### Opsi A: Upload dari Komputer Lokal
1. Buka https://colab.research.google.com/
2. Klik "Upload" > Pilih file `app.py`
3. Upload juga file `requirements.txt`

### Opsi B: Dari Google Drive
1. Upload file ke Google Drive
2. Buka Google Colab
3. Klik folder icon di kiri > Mount Drive > Pilih file

---

## LANGKAH 2: Install Dependencies

Buat cell baru dan jalankan:

```python
# Install semua dependencies
!pip install -q streamlit ultralytics torch torchvision pandas numpy plotly matplotlib opencv-python Pillow scikit-learn
```

Tunggu sampai install selesai (~2-3 menit)

---

## LANGKAH 3: Load YOLOv8 Model

Buat cell baru:

```python
# Import library
from ultralytics import YOLO

# Download dan load model YOLOv8 nano
# Model ini pre-trained untuk deteksi objek
print("📥 Downloading YOLOv8 nano model...")
model = YOLO('yolov8n.pt')
print("✅ Model berhasil dimuat!")
```

---

## LANGKAH 4: Jalankan Streamlit App

Buat cell baru:

```python
# Jalankan Streamlit
# App akan berjalan di localhost:8501
!streamlit run app.py --server.port 8501 &
```

Tekan Enter setelah menjalankan cell. Biarkan proses berjalan.

---

## LANGKAH 5: Akses Aplikasi via LocalTunnel

### Cara 1: LocalTunnel (Recommended)
1. Buka menu Runtime > Manage Sessions
2. Klik "New terminal"
3. Ketik perintah berikut:

```bash
!npx localtunnel --port 8501
```

4. Akan muncul link seperti: `https://some-random-words.loca.lt`
5. Buka link tersebut di browser baru
6. **PENTING:** Masukkan IP address Cloudflare/Colab saat diminta (ketik IP publik)

### Cara 2: Ngrok (Lebih Stabil)
1. Daftar di https://ngrok.com/ (GRATIS)
2. Copy authtoken dari dashboard
3. Buat cell baru:

```python
# Setup ngrok
!pip install pyngrok
!ngrok authtoken YOUR_NGROK_AUTHTOKEN

# Jalankan streamlit
!streamlit run app.py --server.port 8501 &

# Buat tunnel
from pyngrok import ngrok
public_url = ngrok.connect(8501)
print(f"🔗 Akses app di: {public_url}")
```

---

## LANGKAH 6: Upload Gambar untuk Testing

Setelah app berjalan:

1. Buka tab aplikasi di browser
2. Pilih modul **"APD Detector"**
3. Pilih **"Upload Gambar"**
4. Upload gambar pekerja (bisa download dari internet)

---

## TROUBLESHOOTING

### Error: "Module not found"
Jalankan ulang cell install dependencies

### Error: "Connection refused"
Pastikan streamlit sudah berjalan. Cek di Runtime > Manage Sessions

### App tidak muncul
Refresh browser atau buka di tab baru dengan link localtunnel/ngrok

### Model YOLOv8 error
Tambahkan cell untuk re-download:
```python
import os
os.remove('yolov8n.pt')  # Hapus model lama
model = YOLO('yolov8n.pt')  # Download ulang
```

---

## HASIL YANG DIHARAPKAN

Setelah berhasil:
1. ✅ Dashboard HSSE Vision Guard muncul
2. ✅ Bisa navigasi antar modul (Dashboard, APD Detector, dll)
3. ✅ Bisa upload gambar untuk deteksi APD
4. ✅ Safety Dashboard menampilkan grafik interaktif
5. ✅ Risk Predictor menghitung skor risikos

---

## ESTIMASI WAKTU

| Langkah | Waktu |
|---------|-------|
| Upload file | 1-2 menit |
| Install dependencies | 3-5 menit |
| Load model | 1-2 menit |
| Setup tunnel | 2-3 menit |
| **Total** | **~10 menit** |

---

Selamat mencoba! 🚀
