# SHUNA AI — NLP Sentiment & Machine Learning Analytics

[![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3+-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0+-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://streamlit.io/)

Sistem analitik data dan pemrosesan teks ulasan pengguna berbasis Natural Language Processing (NLP) dan Machine Learning. Proyek ini mencakup pipeline pembersihan teks dan normalisasi bahasa informal (slang ID), ekstraksi fitur TF-IDF, klasifikasi sentimen multi-model, simulasi retensi siswa tabular, serta peramalan runtun waktu dengan deteksi anomali.

---

## Informasi Proyek

* **Program:** Studi Independen Bersertifikat (MSIB) Batch 6 Kampus Merdeka @ Skilvul
* **Track:** Machine Learning
* **Kelompok:** Kelompok 26 (Proyek Akhir / Capstone)
* **Nilai Akhir:** 81.8 / 100
* **Lead Developer & Core Architect:** Rizki Ananda, S.Kom ([@InfiniteNull](https://github.com/InfiniteNull))
* **Implementasi:** 95%+ implementasi kode end-to-end (data pipeline, text preprocessing, feature engineering, pemodelan klasifikasi, evaluasi metrik, dan integrasi antarmuka web).

---

## Arsitektur & Modul Teknis

### 1. NLP Pipeline & Indonesian Slang Normalizer
* **Text Preprocessing:** Case folding, pembersihan tanda baca (regex), stopword filtering (Indonesian & English), dan tokenisasi.
* **Slang & Typo Normalizer:** Kamus pemetaan kata informal dan singkatan ke bentuk baku (misal: `bgt` → `sangat`, `gak/ga` → `tidak`, `lemot` → `lambat`, `recom` → `rekomendasi`).
* **TF-IDF Vectorization:** Pembobotan signifikansi kata menggunakan Term Frequency-Inverse Document Frequency pada $n$-gram unigram dan bigram.

### 2. Klasifikasi Sentimen & Benchmark Model
Perbandingan performa 4 model klasifikasi terlatih:
* **Logistic Regression:** Akurasi 93.5% | F1-Score 93.1%
* **Linear Support Vector Machine (SVM):** Akurasi 94.0% | F1-Score 93.8%
* **Multinomial Naive Bayes:** Akurasi 91.2% | F1-Score 90.9%
* **Random Forest:** Akurasi 92.4% | F1-Score 92.0%
* **Evaluasi ROC-AUC:** Kurva ROC empiris (AUC = 0.962) dengan simulasi decision threshold $\tau \in [0.10, 0.90]$.

### 3. Ekstraksi Aspek & Triage Urgensi
* Kategorisasi aspek ulasan: Kurikulum & Materi, Kualitas Mentor, Stabilitas Platform/Video, Layanan CS/Administrasi, dan Penugasan.
* Deteksi ulasan berkategori kritis (*Critical Escalation*) untuk penanganan prioritas.

### 4. Simulator Retensi Tabular
* Klasifikasi probabilitas retensi dan risiko dropout siswa berbasis Sigmoid Logistic Regression menggunakan 5 parameter: skor sentimen rata-rata, completion rate, kehadiran sesi mentoring, nilai tugas, dan waktu resolusi tiket kendala.

### 5. Time-Series Forecasting & Anomaly Detection
* Peramalan tren ulasan menggunakan Holt's Linear Exponential Smoothing (Holt-Winters).
* Deteksi lonjakan anomali ulasan negatif berbasis rolling Z-Score ($k=7, Z \ge 2.0$).

---

## Formulasi Matematika

### TF-IDF (Term Frequency-Inverse Document Frequency)
$$\text{TF-IDF}(t, d, D) = \text{TF}(t, d) \times \ln\left(\frac{1 + |D|}{1 + |\{d \in D : t \in d\}|}\right) + 1$$

### Klasifikasi Sigmoid
$$\sigma(z) = \frac{1}{1 + e^{-z}}, \quad z = \mathbf{w}^T \mathbf{x} + b$$

### Holt's Linear Trend Forecasting
$$L_t = \alpha X_t + (1 - \alpha)(L_{t-1} + T_{t-1})$$
$$T_t = \beta (L_t - L_{t-1}) + (1 - \beta)T_{t-1}$$
$$\hat{Y}_{t+m} = L_t + m T_t$$

---

## Struktur Direktori

```text
SHUNA-AI/
├── app/
│   ├── models/
│   │   ├── logistic_regression_model.pkl   # Serialized trained model
│   │   └── tfidf_vectorizer.pkl            # Serialized fitted vectorizer
│   ├── static/
│   │   ├── css/
│   │   ├── img/
│   │   └── js/
│   ├── templates/
│   │   ├── index.html                      # Landing page
│   │   ├── dashboard.html                  # Analytics dashboard
│   │   ├── login.html
│   │   └── register.html
│   └── utils/
│       ├── app.py                          # Flask application server
│       ├── streamlit_app.py                # Streamlit dashboard
│       ├── train_and_save_model.py         # Model training script
│       └── load_and_predict.py             # Inference pipeline
├── data/
│   └── sentiment-data.csv                  # Dataset ulasan pelatihan
├── notebooks/
│   └── data_analysis.ipynb                 # EDA, preprocessing & visualisasi
├── requirements.txt
└── README.md
```

---

## Panduan Instalasi & Eksekusi

### Prasyarat
* Python 3.10+
* pip

### Instalasi Dependensi
```bash
git clone https://github.com/InfiniteNull/SHUNA-AI.git
cd SHUNA-AI

python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/macOS:
source venv/bin/activate

pip install -r requirements.txt
```

### Menjalankan Streamlit Dashboard
```bash
streamlit run app/utils/streamlit_app.py
```
Akses di browser: `http://localhost:8501`

### Menjalankan Flask Server
```bash
python app/utils/app.py
```
Akses di browser: `http://127.0.0.1:5000`

### Training Model
```bash
python app/utils/train_and_save_model.py
```

---

## Live Platform
Versi interaktif sistem ini juga dapat diakses pada web portofolio:  
[https://infinitenull.github.io/#shuna-ai](https://infinitenull.github.io/#shuna-ai)

---

## Lisensi
MIT License — Rizki Ananda, S.Kom ([@InfiniteNull](https://github.com/InfiniteNull)).
