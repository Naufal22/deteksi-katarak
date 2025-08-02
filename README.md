# 👁️ Deteksi Katarak Menggunakan Machine Learning Klasik

Proyek ini bertujuan untuk membangun model klasifikasi *machine learning* yang mampu mendeteksi keberadaan katarak pada citra mata. Berdasarkan data gambar mata sehat (*normal*) dan mata dengan katarak (*cataract*), proyek ini mengimplementasikan alur kerja *data science* mulai dari pra-pemrosesan data, ekstraksi fitur visual, hingga perbandingan beberapa model untuk menemukan performa terbaik.

Proyek ini dibuat untuk menyelesaikan tugas program magang (*internship*) dari **Dibimbing.id** dengan studi kasus dari **Bukit Vista**.

---

## 📊 Dataset

- **Sumber**: Dataset yang digunakan adalah *Eye Diseases Classification* yang tersedia di Kaggle, dengan fokus pada kelas `cataract` dan `normal`.
- **Fitur Asli**: Citra mata dalam format `.jpg` dan `.png`.
- **Fitur Hasil Ekstraksi (digunakan untuk model)**:
    - `brightness`: Tingkat kecerahan rata-rata gambar.
    - `blurriness`: Tingkat keburaman yang diukur dengan variansi Laplacian.
    - `hist_red_0` s.d. `hist_red_7`: Distribusi intensitas warna pada channel merah (8 bin).
- **Ukuran**: Total 2.112 sampel gambar, dengan distribusi kelas yang seimbang.
- **Target**: `label` (0 untuk *Normal*, 1 untuk *Cataract*).

---

## 🎯 Tujuan Proyek

- Melakukan pra-pemrosesan pada dataset gambar, termasuk membuat tabel data terstruktur.
- Menganalisis dan memvisualisasikan data untuk mendapatkan *insight* awal mengenai karakteristik visual mata katarak dan normal.
- Menerapkan teknik *feature engineering* untuk mengekstraksi fitur-fitur numerik yang relevan dari setiap gambar.
- Membangun, melatih, dan membandingkan beberapa model klasifikasi *machine learning*.
- Mengevaluasi dan menentukan model dengan akurasi dan performa terbaik untuk mendeteksi katarak.

---

## ⚙️ Alur Kerja & Metodologi

Proyek ini dibagi menjadi dua fase utama yang terdokumentasi dalam dua *notebook* terpisah:

1.  **Eksplorasi & Ekstraksi Fitur** (`dibimbing_intern_bukit_vista.ipynb`):
    - **Pra-pemrosesan Data**: Memuat *path* gambar ke dalam DataFrame Pandas dan melakukan *label encoding* pada kelas target. Pengecekan menunjukkan tidak ada data duplikat atau file yang hilang.
    - **Eksplorasi Data (EDA)**: Menganalisis distribusi kelas dan memvisualisasikan sampel gambar. Ditemukan bahwa gambar katarak cenderung lebih buram dan pudar, sedangkan gambar normal lebih tajam dan kontras.
    - **Ekstraksi Fitur**: Berdasarkan *insight* EDA, fitur-fitur numerik diekstraksi dari setiap gambar, meliputi:
        - **Brightness**: Rata-rata nilai piksel pada gambar *grayscale*.
        - **Blurriness**: Variansi dari citra hasil filter **Laplacian**, di mana nilai yang lebih rendah mengindikasikan gambar yang lebih buram.
        - **Color Histogram**: Distribusi intensitas warna pada *channel* merah.
    - **Output**: Sebuah file `ekstraksi_fitur.csv` yang berisi data numerik hasil ekstraksi.

2.  **Pemodelan Machine Learning** (`dibimbing_model.ipynb`):
    - **Pra-pemrosesan Data**:
        - Memuat dataset hasil ekstraksi fitur.
        - Menerapkan **StandardScaler** untuk menormalisasi skala fitur, yang penting karena adanya perbedaan rentang nilai dan *outlier*.
        - Membagi data menjadi 80% data latih dan 20% data uji menggunakan `train_test_split` dengan stratifikasi.
    - **Pemodelan & Evaluasi**:
        - Melatih empat model klasifikasi berbeda: **Logistic Regression**, **Decision Tree**, **Random Forest**, dan **SVM**.
        - Setiap model dievaluasi performanya pada data uji menggunakan metrik *accuracy*, *precision*, *recall*, dan *F1-score*.
    - **Analisis Hasil**: Membandingkan hasil dari keempat model untuk menentukan yang paling efektif.

---

## 🧪 Hasil

- Model **Random Forest** memberikan performa terbaik secara keseluruhan dengan **akurasi 87.47%**. Model ini juga menunjukkan keseimbangan yang baik antara *precision* dan *recall* untuk kedua kelas.
- Model **SVM** menempati urutan kedua dengan **akurasi 86.76%** dan menunjukkan **recall yang sangat tinggi (0.99)** untuk kelas "Normal". Ini menjadikannya pilihan yang kuat jika prioritasnya adalah meminimalkan kesalahan identifikasi pada mata yang sehat.
- **Rekomendasi Model**: **Random Forest** direkomendasikan sebagai model utama karena akurasi dan keseimbangan performa yang superior pada dataset ini.

| Model | Accuracy | F1-Score (Normal) | F1-Score (Cataract) |
| :--- | :---: | :---: | :---: |
| **Random Forest** | **87.47%** | **0.88** | **0.87** |
| **SVM** | 86.76% | 0.88 | 0.85 |
| **Logistic Regression** | 85.58% | 0.87 | 0.84 |
| **Decision Tree** | 85.34% | 0.86 | 0.85 |

*(Analisis lengkap dan classification report untuk setiap model terdapat di dalam notebook `dibimbing_model.ipynb`)*.

---

## 💻 Teknologi yang Digunakan

- **Python**
- **Pandas** & **NumPy** (untuk manipulasi data)
- **Scikit-learn** (untuk `StandardScaler`, `train_test_split`, dan model-model klasifikasi)
- **OpenCV-Python (`cv2`)** (untuk pemrosesan citra dan ekstraksi fitur)
- **Matplotlib** & **Seaborn** (untuk visualisasi data)

---




## 🙋 Kontak

**Muhammad Naufal Aqil**
- **Email**: muhammadnaufalaqil20@gmail.com
- **GitHub**: [Naufal22](https://github.com/Naufal22)
- **LinkedIn**: [Muhammad Naufal Aqil](https://www.linkedin.com/in/muhammad-naufal-aqil-b6114424a/)
