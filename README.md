# SHUNA AI — Machine Learning & NLP User Feedback Intelligence Platform

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3+-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0+-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![MSIB Kampus Merdeka](https://img.shields.io/badge/MSIB%20Batch%206-Skilvul%20Score%2081.8-0284c7?style=for-the-badge)](https://skilvul.com/)

</div>

> **Sistem Analitik Data & Pemrosesan Bahasa Alami (NLP) untuk Ekstraksi Sentimen, Aspek Ulasan, dan Prediksi Retensi Pengguna**  
> *Proyek Capstone / Proyek Akhir **Kelompok 26** pada Program **Studi Independen Bersertifikat (MSIB) Batch 6 Kampus Merdeka @ Skilvul** (Track: Machine Learning • **Nilai Akhir: 81.8**).*  
> *Arsitektur dan implementasi kode (95%+ end-to-end technical execution) dibangun secara mandiri oleh **Rizki Ananda, S.Kom** ([@InfiniteNull](https://github.com/InfiniteNull)) sebagai **Ketua Tim (Lead Developer & Core Architect)**.*

---

## 📌 Latar Belakang & Pernyataan Masalah

Pada era platform edukasi dan teknologi daring, institusi menerima ribuan masukan (*feedback*), ulasan, dan survei kepuasan siswa setiap minggunya. Memproses ulasan ini secara manual memerlukan sumber daya besar dan rawan bias subjektif.

**SHUNA AI** dibangun untuk mentransformasikan data teks ulasan mentah menjadi wawasan bisnis yang terukur dan dapat ditindaklanjuti secara instan melalui kombinasi:
1. **Pipeline Pemrosesan Bahasa Alami (NLP)** dengan kamus normalisasi bahasa gaul / *Indonesian Slang & Typo Normalizer*.
2. **Ekstraksi Fitur TF-IDF ($n$-gram)** dan klasifikasi sentimen deterministik (*Positive, Neutral, Negative*).
3. **Multi-Model Machine Learning Arena** (Logistic Regression, Linear SVM, Naive Bayes, Random Forest) dengan evaluasi kurva **ROC-AUC (AUC = 0.962)**.
4. **Simulator Prediksi Retensi & Risiko Dropout Tabular** (Sigmoid Logistic Regression) untuk mendeteksi siswa yang berisiko keluar dari program pelatihan.
5. **Peramalan Runtun Waktu (Holt-Winters Exponential Smoothing)** dan deteksi lonjakan anomali ulasan negatif (*Rolling Z-Score*).
6. **Dashboard Interaktif Berbasis Web** (Flask & Streamlit) untuk visualisasi distribusi metrik dan pelaporan ulasan real-time.

---

## 🏆 Kredensial & Kepemilikan Teknis Proyek

* **Program:** Studi Independen Bersertifikat (MSIB) Batch 6 — Kampus Merdeka Republik Indonesia
* **Mitra Penyelenggara:** Skilvul (PT Impactbyte Teknologi Edukasi)
* **Track:** Machine Learning & Artificial Intelligence
* **Entitas Proyek:** **Proyek Capstone Kelompok 26 (Group 26)**
* **Nilai Akhir Evaluasi:** **81.8 / 100**
* **Ketua Tim & Core Architect:** Rizki Ananda, S.Kom ([@InfiniteNull](https://github.com/InfiniteNull))
* **Kontribusi Implementasi:** 95%+ implementasi kode end-to-end (Data exploration, preprocessing pipeline, model training, evaluation metrics, web integration, and technical documentation).

---

## ✨ Fitur & Kemampuan Utama

### 1. 🧠 Pipeline NLP & Normalisasi Slang Indonesia
* **Text Preprocessing:** Case folding, sanitasi regex, pembersihan tanda baca, tokenisasi kata, dan stopword removal bahasa Indonesia & Inggris.
* **Indonesian Slang & Informal Normalizer:** Memetakan singkatan dan kata informal (`bgt` ➔ `sangat`, `gak/ga` ➔ `tidak`, `lemot` ➔ `lambat`, `recom` ➔ `rekomendasi`, `ancur` ➔ `hancur`) untuk meningkatkan representasi vektor TF-IDF.
* **TF-IDF Feature Extraction:** Menghitung signifikansi kata dengan formula Term Frequency-Inverse Document Frequency pada $n$-gram unigram dan bigram.

### 2. ⚔️ Multi-Model Benchmark Arena & Evaluasi ROC-AUC
* Komparasi empat algoritma klasifikasi machine learning:
  * **Logistic Regression:** Akurasi **93.5%** • F1-Score: **93.1%**
  * **Linear Support Vector Machine (SVM):** Akurasi **94.0%** • F1-Score: **93.8%**
  * **Multinomial Naive Bayes:** Akurasi **91.2%** • F1-Score: **90.9%**
  * **Random Forest Classifier:** Akurasi **92.4%** • F1-Score: **92.0%**
* **Dynamic Decision Threshold Slider ($	au$):** Simulasi trade-off Precision-Recall pada kurva ROC-AUC empiris (AUC = 0.962) dengan Confusion Matrix dinamis ($TP, FP, TN, FN$).

### 3. 📊 Ekstraksi Aspek & Triage Urgensi
* Klasifikasi otomatis aspek ulasan ke dalam 5 domain operasional:
  * **Kurikulum & Materi:** Struktur modul, silabus, dan kedalaman materi.
  * **Mentor & Pengajar:** Kecepatan respon, kualitas bimbingan, dan diskusi teknis.
  * **Platform & Video Player:** Stabilitas streaming, server buffering, dan bug portal.
  * **Dukungan & Administrasi:** Respon tiket Customer Support, sertifikat, dan presensi.
  * **Tugas & Proyek:** Kejelasan rubrik penilaian dan studi kasus *capstone*.
* **Triage Urgensi:** Menandai otomatis keluhan kritis (*Critical Escalation*) dari ulasan bernada negatif berbobot tinggi.

### 4. 📈 Simulator Prediksi Retensi & Dropout Siswa
* Memodelkan probabilitas kelulusan siswa bootcamp berdasarkan 5 parameter tabular:
  * Skor sentimen ulasan rata-rata ($[0.0, 1.0]$)
  * Persentase penyelesaian modul / Completion Rate ($[0, 100]\%$)
  * Jumlah kehadiran sesi live mentoring ($[0, 12]$ sesi)
  * Rata-rata nilai penugasan ($[0, 100]$)
  * Waktu penyelesaian tiket kendala teknis (jam)
* Menghitung probabilitas $P(	ext{Retention}) = \sigma(\mathbf{w}^T \mathbf{x} + b)$ dan mengelompokkan risiko ke dalam *Low Risk*, *Moderate Risk*, atau *High Risk / Churn Alert*.

### 5. 📉 Time-Series Forecasting & Deteksi Anomali
* **Holt's Linear Exponential Smoothing (Holt-Winters):** Memproyeksikan volume ulasan mendatang dengan estimasi Level ($L_t$) dan Trend ($T_t$).
* **Rolling Z-Score Anomaly Detector ($k=7$):** Menandai lonjakan anomali komplain ulasan negatif ($Z \ge 2.0$) untuk deteksi dini *server downtime* atau kendala platform massal.

---

## 📐 Formulasi Matematika & Algoritma

### 1. Pembobotan TF-IDF (Term Frequency-Inverse Document Frequency)
$$\text{TF-IDF}(t, d, D) = \text{TF}(t, d) \times \ln\left(\frac{1 + |D|}{1 + |\{d \in D : t \in d\}|}\right) + 1$$

### 2. Klasifikasi Probabilitas Sigmoid & Binary Cross-Entropy
$$\sigma(z) = \frac{1}{1 + e^{-z}}, \quad z = \mathbf{w}^T \mathbf{x} + b$$
$$\mathcal{L}(\mathbf{w}) = -\frac{1}{m}\sum_{i=1}^m \left[ y^{(i)}\ln(\hat{y}^{(i)}) + (1-y^{(i)})\ln(1-\hat{y}^{(i)}) \right]$$

### 3. Peramalan Runtun Waktu Holt's Linear Trend
$$L_t = \alpha X_t + (1 - \alpha)(L_{t-1} + T_{t-1})$$
$$T_t = \beta (L_t - L_{t-1}) + (1 - \beta)T_{t-1}$$
$$\hat{Y}_{t+m} = L_t + m T_t$$

---

## 📁 Struktur Direktori Repositori

```text
SHUNA-AI/
├── app/
│   ├── models/
│   │   ├── logistic_regression_model.pkl   # Serialized Model Scikit-Learn
│   │   └── tfidf_vectorizer.pkl            # Serialized Fitted TF-IDF Vectorizer
│   ├── static/
│   │   ├── css/                            # Custom UI Stylesheets
│   │   ├── img/                            # Asset Icon & Ilustrasi Web
│   │   └── js/                             # Interactive Client-Side Logic
│   ├── templates/
│   │   ├── index.html                      # Landing Page SHUNA AI
│   │   ├── dashboard.html                  # Analytics & Sentiment Monitor UI
│   │   ├── login.html                      # Portal Login Autentikasi
│   │   └── register.html                   # Registrasi Pengguna
│   └── utils/
│       ├── app.py                          # Flask Web Application Server
│       ├── streamlit_app.py                # Streamlit Live Interactive Dashboard
│       ├── train_and_save_model.py         # Skrip Pelatihan Model & Export Pickle
│       └── load_and_predict.py             # Pipeline Inferensi Teks & Prediksi
├── data/
│   └── sentiment-data.csv                  # Dataset Ulasan & Feedback Pelatihan
├── notebooks/
│   └── data_analysis.ipynb                 # Jupyter Notebook EDA, TF-IDF & Evaluasi
├── requirements.txt                        # Daftar Dependensi Python
└── README.md                               # Dokumentasi Teknis Repositori
```

---

## 🚀 Panduan Instalasi & Menjalankan Aplikasi

### 1. Prasyarat Sistem
* Python 3.10 atau versi yang lebih baru
* `pip` dan `git`

### 2. Kloning Repositori & Persiapan Lingkungan
```bash
# Clone repositori
git clone https://github.com/InfiniteNull/SHUNA-AI.git
cd SHUNA-AI

# Buat virtual environment (direkomendasikan)
python -m venv venv

# Aktivasi virtual environment:
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependensi
pip install -r requirements.txt
```

### 3. Menjalankan Dashboard Streamlit
```bash
streamlit run app/utils/streamlit_app.py
```
Aplikasi Streamlit akan aktif di: `http://localhost:8501`

### 4. Menjalankan Aplikasi Web Flask
```bash
python app/utils/app.py
```
Aplikasi Flask akan aktif di: `http://127.0.0.1:5000`

### 5. Melatih Ulang Model Machine Learning
```bash
python app/utils/train_and_save_model.py
```

---

## 🌐 Live Interactive Web Platform

SHUNA AI juga telah diintegrasikan sebagai **Proyek Unggulan ke-3** pada portal portofolio interaktif:  
👉 **[https://infinitenull.github.io/#shuna-ai](https://infinitenull.github.io/#shuna-ai)**

Fitur web interaktif di live platform meliputi:
* Live NLP Tokenizer & Indonesian Slang Normalizer Sandbox
* Interactive Word Cloud & Bigrams Explorer
* Live Multi-Model Benchmark Arena & ROC-AUC Operating Point Slider
* Tabular Student Retention & Churn Risk Calculator
* Time-Series Anomaly Forecaster
* Client-Side Batch CSV Upload, Processing & Report Exporter

---

## 👥 Tim Proyek & Kontribusi

* **Kelompok:** **Kelompok 26** — MSIB Batch 6 Kampus Merdeka @ Skilvul
* **Ketua Tim (Lead Developer & Architect):** [Rizki Ananda, S.Kom (@InfiniteNull)](https://github.com/InfiniteNull)
* **Lisensi:** MIT License
