# 🗑️ Sistem Sortir Sampah Otomatis
### Proyek Final Deep Learning — Soal 1

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-orange?logo=pytorch)
![ONNX](https://img.shields.io/badge/ONNX-Runtime-purple)
![Gradio](https://img.shields.io/badge/Gradio-UI-yellow)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📋 Deskripsi Proyek

Proyek ini mensimulasikan sistem mesin sortir sampah otomatis. Sistem menggunakan deep learning untuk mengklasifikasikan jenis sampah secara real-time ke dalam **5 kategori**:

| Kelas | Emoji | Contoh |
|-------|-------|--------|
| Organik | 🌿 | Sisa makanan, daun, sayuran |
| Plastik | 🧴 | Botol, kantong, sedotan |
| Kertas | 📄 | Kardus, koran, buku |
| Logam | 🔩 | Kaleng, besi, aluminium |
| Kaca | 🪟 | Botol kaca, cermin |

---

## ✨ Fitur Utama

- ✅ **Transfer Learning** — MobileNetV3-Large pretrained ImageNet
- ✅ **Data Augmentation** — RandomCrop, ColorJitter, Flip, RandomErasing
- ✅ **Mixed Precision Training** — FP16 AMP untuk training lebih cepat
- ✅ **Sliding Window + NMS** — Deteksi objek multi-scale klasik
- ✅ **Grad-CAM** — Visualisasi area keputusan model (XAI)
- ✅ **ONNX Export** — Deployment lintas platform
- ✅ **Gradio Web UI** — Antarmuka interaktif berbasis web
- ✅ **Real-time Webcam** — Klasifikasi langsung dari kamera

---

## 🚀 Improvisasi Pengembangan
Proyek ini mengimplementasikan:

### GradCAM Visualizer
Implementasi Gradient-weighted Class Activation Mapping dari scratch menggunakan PyTorch hooks. Menghasilkan heatmap overlay yang menunjukkan area gambar paling berpengaruh pada prediksi model, membantu interpretasi dan debugging model.

### Mobile-optimized Classifier
Menggunakan MobileNetV3-Large yang dioptimasi untuk deployment ringan, dikombinasikan dengan export ke ONNX dan benchmark inference. Model ini cocok untuk di-deploy ke perangkat edge seperti Raspberry Pi atau smartphone.

### Model Explainability Dashboard
Menggabungkan Grad-CAM visualization, Confusion Matrix per kelas, Classification Report (Precision/Recall/F1), statistik distribusi prediksi, dan kurva training dalam satu notebook yang komprehensif.

---

## 🧠 Konsep Deep Learning yang Diintegrasikan

| No | Konsep | Implementasi |
|----|--------|-------------|
| 1 | Transfer Learning | MobileNetV3-Large + custom head |
| 2 | CNN Architecture | Backbone + classifier head |
| 3 | Data Augmentation | 7 teknik augmentasi training |
| 4 | Batch Norm & Dropout | Terintegrasi di MobileNetV3 |
| 5 | Loss Function | CrossEntropyLoss + Label Smoothing |
| 6 | Optimizer | AdamW + CosineAnnealingLR |
| 7 | Backpropagation | Mixed Precision FP16 (AMP) |
| 8 | Deteksi Objek | Sliding Window Multi-Scale + NMS |
| 9 | Metrik Evaluasi | Accuracy, F1, Confusion Matrix |
| 10 | GradCAM | Visualisasi area keputusan |
| 11 | Deployment ONNX | Export + Benchmark |
| 12 | Real-time | Gradio UI + Webcam stream |

---

## 📁 Struktur Repositori

```
sistem-sortir-sampah/
├── sistem_sortir_sampah.ipynb   # Notebook utama
├── sampah_classifier.onnx       # Model ONNX (siap deploy)
├── class_names.json             # Mapping kelas
├── README.md                    # Dokumentasi ini
└── output_images/
    ├── training_curves.png      # Grafik loss & accuracy
    ├── confusion_matrix.png     # Confusion matrix test set
    ├── gradcam.png              # Visualisasi Grad-CAM
    ├── statistics.png           # Statistik distribusi prediksi
    └── augmentation_preview.png # Preview augmentasi
```

---

## ⬇️ Download Model Weights

File `best_model.pth` tidak disertakan langsung di repo karena ukurannya.

📥 **Download di sini:** [Google Drive — best_model.pth](https://drive.google.com/YOUR_LINK_HERE)

Setelah download, letakkan file di root folder proyek:
```
sistem-sortir-sampah/
└── best_model.pth   ← letakkan di sini
```

---

## 🛠️ Setup & Cara Menjalankan

### 1. Clone Repository
```bash
git clone (https://github.com/Rini-O/Sistem-Sortir-Sampah.git)
cd sistem-sortir-sampah
```

### 2. Install Dependencies
```bash
pip install torch torchvision kaggle gradio onnx onnxruntime \
            matplotlib seaborn scikit-learn pillow opencv-python-headless
```

### 3. Setup Kaggle API
```bash
# Letakkan kaggle.json di:
~/.kaggle/kaggle.json

# Atau di Google Colab:
from google.colab import files
files.upload()  # upload kaggle.json
```

### 4. Jalankan Notebook
Buka `sistem_sortir_sampah.ipynb` dan jalankan sel **secara berurutan dari atas ke bawah**.

> 💡 **Disarankan menggunakan Google Colab dengan runtime GPU** untuk training yang lebih cepat.

---

## 📊 Hasil & Performa

| Metrik | Nilai |
|--------|-------|
| Best Validation Accuracy | lihat output Cell 8 |
| Test Accuracy | lihat output Cell 10 |
| ONNX Inference Speed | lihat output Cell 14 |

---

## 🗂️ Dataset

**Sumber:** [Garbage Classification — Kaggle](https://www.kaggle.com/datasets/asdasdasasdas/garbage-classification)

- 12 kelas asli → dipetakan ke 5 kelas target
- Maksimal 600 gambar per kelas (balanced)
- Split: 70% train / 15% val / 15% test

---


