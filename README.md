# Submission Akhir BMLP: Clustering dan Klasifikasi Transaksi Bank

Proyek ini merupakan submission akhir kelas **Belajar Machine Learning untuk Pemula (BMLP)** dari Dicoding. Tujuannya adalah mengelompokkan data transaksi bank menggunakan *clustering*, lalu memanfaatkan label hasil *clustering* tersebut untuk melatih model *klasifikasi*.

## Deskripsi Proyek

Proyek dibagi menjadi dua tahap yang saling terhubung:

1. **Clustering (Unsupervised Learning)** mengelompokkan ~2.512 record transaksi bank tanpa label menggunakan algoritma **K-Means**. Hasil pengelompokan disimpan sebagai kolom `Target`.
2. **Klasifikasi (Supervised Learning)** menggunakan label `Target` dari tahap clustering sebagai variabel target untuk melatih model **Decision Tree** dan **Random Forest**, lalu mengevaluasi performanya dengan *accuracy* dan *F1-score*.

## Dataset

Dataset berisi ~2.512 record transaksi bank yang dieksplorasi untuk keperluan deteksi anomali/fraud. Data dimuat saat *runtime* dari Google Sheets CSV (tidak ada salinan lokal). Beberapa fitur utamanya:

| Fitur | Keterangan |
|---|---|
| `TransactionID` | ID unik transaksi |
| `AccountID` | ID unik akun |
| `TransactionAmount` | Nilai transaksi |
| `TransactionType` | `Credit` atau `Debit` |
| `Location` | Kota tempat transaksi |
| `AccountBalance` | Saldo akun setelah transaksi |
| `Channel` | `Online`, `ATM`, atau `Branch` |
| `CustomerAge` | Usia pemilik akun |
| `CustomerOccupation` | Pekerjaan (Doctor, Engineer, Student, Retired) |
| `TransactionDuration` | Durasi transaksi (detik) |
| `LoginAttempts` | Jumlah percobaan login sebelum transaksi |

## Struktur File

```
Submission Machine Learning/
├── [Clustering]_Submission_Akhir_BMLP_Andry_Afrinaldo.ipynb    # Notebook tahap clustering
├── [Klasifikasi]_Submission_Akhir_BMLP_Andry_Afrinaldo.ipynb   # Notebook tahap klasifikasi
├── data_clustering.csv                  # Hasil clustering (data ter-scaling + label Target)
├── data_clustering_inverse.csv          # Hasil clustering (data asli/inverse + label Target)
├── model_clustering.h5                  # Model K-Means tersimpan
├── PCA_model_clustering.h5              # Model PCA untuk visualisasi 2D
├── decision_tree_model.h5              # Model Decision Tree
├── explore_RandomForest_classification.h5   # Model Random Forest
├── tuning_classification.h5            # Model hasil hyperparameter tuning
└── README.md
```

## Alur Pengerjaan

### Tahap 1: Clustering

1. **Import Library** semua dependensi dimuat di satu cell teratas.
2. **Memuat Dataset** membaca CSV dari Google Sheets, lalu inspeksi awal dengan `head()`, `info()`, dan `describe()`.
3. **Exploratory Data Analysis (EDA)** heatmap korelasi, histogram tiap kolom numerik, dan boxplot `TransactionAmount` per `CustomerOccupation`.
4. **Pembersihan dan Pra-Pemrosesan**
   - Cek dan hapus nilai *null* serta duplikat.
   - Drop kolom identifier/timestamp (mengandung `id`, `ip`, atau `date`).
   - *Label encoding* kolom kategorikal.
   - Penghapusan *outlier* berbasis IQR per kolom numerik.
   - *Feature scaling* dengan `StandardScaler`.
   - *Binning* `CustomerAge` menjadi `AgeGroup` lewat `pd.qcut`.
5. **Membangun Model Clustering**
   - Penentuan jumlah cluster optimal dengan *Elbow Method* (`KElbowVisualizer`).
   - Pelatihan `KMeans(n_clusters=2, random_state=42)`.
   - Evaluasi dengan **Silhouette Score (~0.57)**.
   - Visualisasi cluster 2D menggunakan **PCA**.
6. **Interpretasi Hasil Clustering** analisis karakteristik tiap cluster (mean, min, max tiap fitur).
7. **Mengeksport Data** menyimpan label ke kolom `Target`, lalu ekspor ke CSV.

### Tahap 2: Klasifikasi

1. **Memuat Dataset** membaca `data_clustering_inverse.csv` (data asli + label `Target`).
2. **Pra-Pemrosesan** *One-Hot Encoding* fitur kategorikal dengan `pd.get_dummies(drop_first=True)`.
3. **Data Splitting** `train_test_split` (80% latih, 20% uji, `stratify=y`).
4. **Membangun Model**
   - **Decision Tree Classifier**.
   - **Random Forest Classifier**.
5. **Evaluasi** menampilkan **accuracy** dan **F1-score** pada data uji lewat `classification_report`.
6. **Hyperparameter Tuning** optimasi model dengan `GridSearchCV`.

## Cara Menjalankan

1. Pastikan **Python 3** dan **Jupyter** sudah terpasang.
2. Install dependensi:

   ```bash
   pip install pandas matplotlib seaborn scikit-learn yellowbrick joblib
   ```

3. Jalankan notebook secara berurutan:
   - Jalankan **notebook Clustering** lebih dulu sampai menghasilkan `data_clustering.csv` dan `data_clustering_inverse.csv`.
   - Baru jalankan **notebook Klasifikasi** yang membaca output dari tahap clustering.
4. Disarankan menjalankan **Run All** dari cell pertama sampai terakhir agar semua output muncul.

## Teknologi yang Digunakan

- **Python 3**
- **pandas** manipulasi data
- **matplotlib** & **seaborn** visualisasi
- **scikit-learn** K-Means, PCA, Decision Tree, Random Forest, preprocessing, evaluasi
- **yellowbrick** visualisasi Elbow Method
- **joblib** menyimpan model

## Author

**Andry Afrinaldo**

Submission Akhir Kelas Belajar Machine Learning untuk Pemula (BMLP) Dicoding.
