# HSSE Vision Guard

![HSSE Innovation Challenge 2026](https://img.shields.io/badge/HSSE-2026-blue)
![Python](https://img.shields.io/badge/Python-3.8+-green)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Nano-orange)
![License](https://img.shields.io/badge/License-MIT-green)

## 🤖 AI-Powered Safety Monitoring System

> **HSSE Innovation Challenge 2026 - PT Pertamina HSE Training Center**

HSSE Vision Guard adalah sistem monitoring keselamatan kerja terintegrasi yang menggabungkan tiga teknologi canggih: **Digital Twin**, **Kecerdasan Buatan (AI)**, dan **Unmanned Aerial Vehicle (UAV)** untuk industri energi Indonesia.

> *"HSSE Innovation for a Safe, Smart, and Sustainable Energy Future"*

---

## 🎯 About This Project

**Authors:** M Lintang Maulana Zulfan | Universitas Gadjah Mada

**Competition:** HSSE Innovation Challenge 2026 - PT Pertamina HSE Training Center

### Problem Statement

Industri energi di Indonesia menghadapi tantangan serius dalam aspek Health, Safety, Security, and Environment (HSSE). Angka kecelakaan kerja di sektor ini masih signifikan, dan diperlukan pendekatan inovatif untuk menekan tingkat insiden.

### Solution

Pengembangan sistem monitoring keselamatan kerja terintegrasi berbasis:
- **Digital Twin** - Replika digital untuk simulasi dan prediksi
- **Kecerdasan Buatan (AI)** - Deteksi objek dan analisis prediktif
- **UAV** - Inspeksi area berbahaya tanpa risiko langsung

---

## ✨ Features

### 1. 🦺 APD Detector (Alat Pelindung Diri)

```
┌─────────────────────────────────┐
│  Input: Webcam / Gambar / Video │
│  Model: YOLOv8 Nano (82.1% mAP) │
│  Output: Bounding Box + Label   │
└─────────────────────────────────┘
```

- Real-time object detection menggunakan YOLOv8
- Support webcam, image upload, video upload
- Bounding box visualization
- Confidence scoring untuk setiap deteksi

### 2. 📊 Safety Dashboard

```
┌─────────────────────────────────┐
│  KPIs | Charts | Zone Overview  │
│  Plotly Interactive Charts      │
└─────────────────────────────────┘
```

- Key Performance Indicators (KPIs) real-time
- 12-month incident trend visualization
- Zone safety overview
- Severity distribution charts (Pie, Bar)

### 3. ⚠️ Risk Predictor

```
┌─────────────────────────────────┐
│  Input: Zone, Equipment, Weather│
│  Output: Risk Score + Actions   │
└─────────────────────────────────┘
```

- ML-based risk scoring (0-100)
- Multi-factor analysis
- Equipment age, maintenance score, weather
- Actionable recommendations

### 4. 🚁 UAV Simulator

```
┌─────────────────────────────────┐
│  5 Waypoints | Progress Bar     │
│  Inspection Result Summary      │
└─────────────────────────────────┘
```

- Waypoint inspection simulation
- Real-time progress tracking
- Inspection result summary

---

## 🏗️ System Architecture

### 4-Layer Architecture

```mermaid
flowchart TD
    subgraph L4["LAYER 4: Application & Decision Layer"]
        D["Dashboard"]
        AS["Alert System"]
        DS["Decision Support"]
        R["Reporting"]
        TM["Training Module (VR/AR)"]
    end

    subgraph L3["LAYER 3: Digital Twin & AI Layer"]
        DT["Digital Twin Engine<br>• Real-time Sync<br>• Simulation<br>• Risk Modeling"]
        AI["AI Analytics Engine<br>• Machine Learning<br>• Deep Learning (YOLO)<br>• NLP Analysis"]
        KB["Knowledge Base<br>Incident DB | Best Practices | Procedures"]
    end

    subgraph L2["LAYER 2: Connectivity Layer"]
        direction LR
        N["5G/IoT"] --- EC["Edge Computing"] --- C["Cloud"] --- CS["Cybersecurity"]
        BC["Blockchain (Data Integrity)"]
    end

    subgraph L1["LAYER 1: Physical Layer"]
        SN["Sensor Network<br>Temp/Humidity/Gas"]
        UAV["UAV Fleet<br>4K/Thermal/LiDAR"]
        WD["Wearable Devices<br>Smart Helmet/Vest"]
        CCTV["CCTV + Video Analytics"]
    end

    L1 --> L2
    L2 --> L3
    L3 --> L4
    
    style L4 fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#000
    style L3 fill:#fff3e0,stroke:#ef6c00,stroke-width:2px,color:#000
    style L2 fill:#e8eaf6,stroke:#3f51b5,stroke-width:2px,color:#000
    style L1 fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000
```

---

## 🛠️ Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| Python | 3.8+ | Programming Language |
| Streamlit | 1.28+ | Web Application Framework |
| YOLOv8 (Ultralytics) | 8.0+ | Object Detection |
| Plotly | 5.15+ | Data Visualization |
| Pandas | 2.0+ | Data Processing |
| NumPy | 1.24+ | Numerical Computing |
| OpenCV | 4.8+ | Image/Video Processing |

---

## 🚀 Getting Started

### Option 1: Google Colab (Recommended - No Installation!)

```
1. Buka https://colab.research.google.com/
2. Upload file app.py
3. Jalankan cell:

!pip install -q streamlit ultralytics pandas numpy plotly matplotlib opencv-python Pillow scikit-learn

from ultralytics import YOLO
model = YOLO('yolov8n.pt')

!streamlit run app.py --server.port 8501

4. Akses via localtunnel:
!npx localtunnel --port 8501
```

Lihat [COLAB_GUIDE.md](COLAB_GUIDE.md) untuk panduan lengkap.

### Option 2: Local Installation

```bash
# Clone repository
git clone https://github.com/mlintangmz2765/HSSE_Vision_Guard.git
cd HSSE_Vision_Guard

# Install dependencies
pip install -r requirements.txt

# Run application
streamlit run app.py

# Buka browser: http://localhost:8501
```

---

## 📊 Research Summary

### Key Results

| Metric | Result |
|--------|--------|
| APD Detection Accuracy | 82.1% mAP (YOLOv8) |
| Incident Prediction Improvement | Up to 35% |
| Potential Incident Reduction | Up to 40% |
| Real-time Response Time | < 3 seconds |
| Video Analytics FPS | ~30 FPS (CPU) |

### Literature Base

15+ international journal references including:

| Author (Year) | Institution | Topic |
|---------------|-------------|-------|
| Petropoulos et al. (2025) | IEEE | Safety in Industry 5.0 |
| Kairanbay et al. (2025) | IEEE | LLM Predictive Incident Detection |
| Shadrin & Igumen'scheva (2025) | Angarsk TU | Digital Twin & Predictive Analytics |
| Aromoye et al. (2025) | CMES | UAV Pipeline Monitoring |
| Pandey et al. (2025) | J. Manufacturing Systems | Predictive Analytics |
| Al-Tayar et al. (2025) | IEEE | XAI PPE Decision Support |
| Ababio et al. (2025) | MDPI/Future Internet | Blockchain FL Digital Twins |

---

## 📂 Project Structure

```
HSSE_Vision_Guard/
├── app.py                          # Main Streamlit application
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── COLAB_GUIDE.md                 # Google Colab guide
├── HSSE_Vision_Guard_Colab.ipynb  # Colab notebook
├── .gitignore                     # Git ignore file
└── LICENSE                         # MIT License
```

---

## 🎥 Screenshots

### Dashboard Overview

![Dashboard Overview](screenshots/dashboard.png)

### APD Detector

![APD Detector](screenshots/apd_detector.png)

### Risk Predictor & UAV Simulator

![Risk Predictor](screenshots/risk_predictor.png)
![UAV Simulator](screenshots/uav_simulator.png)

---

## 🎯 Roadmap

```mermaid
timeline
    title Strategi Implementasi HSSE Vision Guard
    2026 : Phase 1 (Pilot Project)
         : APD Detection + Dashboard
         : Target 1 PT Pertamina facility
    2027 : Phase 2 (Expansion)
         : Risk Predictor + UAV Integration
         : Target 5 facilities
    2028+ : Phase 3 (Enterprise Integration)
          : Full Digital Twin + AI
          : Enterprise-wide deployment
```

---

## 📅 Competition Timeline

| Activity | Date |
|----------|------|
| Registration | 27 April - 22 May 2026 |
| **Submission** | **25 - 29 May 2026** |
| Winner Announcement | Minggu Pertamina June 2026 |

---

## Author
- **M Lintang Maulana Zulfan**
- **Universitas Gadjah Mada**
- GitHub: [@mlintangmz2765](https://github.com/mlintangmz2765)

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.

---

Made with ❤️ for HSSE Innovation Challenge 2026
PT Pertamina HSE Training Center
