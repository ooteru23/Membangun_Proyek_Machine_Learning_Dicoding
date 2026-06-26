# Submission Akhir BMLP: Clustering & Klasifikasi

Proyek ini merupakan submission akhir kelas **Belajar Machine Learning untuk Pemula (BMLP) Dicoding** oleh **Andry Afrinaldo**. Proyek terdiri dari dua tahap utama yang saling berkaitan, yaitu *unsupervised learning* (clustering) untuk membentuk label, lalu *supervised learning* (klasifikasi) untuk memprediksi label tersebut.

## Deskripsi Proyek

Dataset menyajikan gambaran perilaku transaksi dan pola aktivitas keuangan sehingga ideal untuk eksplorasi **deteksi penipuan (fraud detection)** dan **identifikasi anomali**. Dataset mencakup sekitar **2.512 sampel transaksi** dengan beragam atribut numerik maupun kategorikal.

Alur kerja proyek:

1. **Clustering**: Mengelompokkan data transaksi menggunakan *unsupervised learning*. Hasil cluster dijadikan label target.
2. **Klasifikasi**: Membangun model yang memprediksi label hasil clustering, lengkap dengan *hyperparameter tuning* dan evaluasi.

## Struktur Repositori

| Berkas | Keterangan |
| --- | --- |
| `[Clustering]_Submission_Akhir_BMLP_Andry_Afrinaldo.ipynb` | Notebook tahap clustering (EDA, preprocessing, pemodelan cluster). |
| `[Klasifikasi]_Submission_Akhir_BMLP_Andry_Afrinaldo.ipynb` | Notebook tahap klasifikasi (splitting, training, tuning, evaluasi). |
| `data_clustering.csv` | Dataset hasil proses clustering (data ternormalisasi). |
| `data_clustering_inverse.csv` | Dataset hasil clustering dalam skala asli (inverse transform). |
| `model_clustering.h5` | Model clustering yang telah dilatih. |
| `PCA_model_clustering.h5` | Model PCA untuk reduksi dimensi pada tahap clustering. |
| `decision_tree_model.h5` | Model klasifikasi Decision Tree. |
| `explore_RandomForest_classification.h5` | Model eksplorasi Random Forest. |
| `tuning_classification.h5` | Model klasifikasi hasil *hyperparameter tuning*. |

## Dataset

Berkas `data_clustering.csv` memiliki kolom berikut:

- `TransactionAmount`: Nominal transaksi.
- `TransactionType`: Jenis transaksi.
- `Location`: Lokasi transaksi.
- `Channel`: Kanal transaksi.
- `CustomerAge`: Usia nasabah.
- `CustomerOccupation`: Pekerjaan nasabah.
- `TransactionDuration`: Durasi transaksi.
- `LoginAttempts`: Jumlah percobaan login.
- `AccountBalance`: Saldo rekening.
- `AgeGroup`: Kelompok usia.
- `Target`: Label hasil clustering (digunakan sebagai target klasifikasi).

## Teknologi yang Digunakan

- **Python 3**
- **Pandas** dan **NumPy** untuk manipulasi data.
- **scikit-learn** untuk pemodelan clustering dan klasifikasi.
- **Matplotlib** dan **Seaborn** untuk visualisasi.
- **Jupyter Notebook** sebagai lingkungan pengembangan.

## Cara Menjalankan

1. Klon repositori ini.

   ```bash
   git clone https://github.com/<username>/<nama-repo>.git
   cd <nama-repo>
   ```

2. Pasang dependensi yang dibutuhkan.

   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```

3. Buka notebook melalui Jupyter.

   ```bash
   jupyter notebook
   ```

4. Jalankan notebook dengan urutan: **Clustering** terlebih dahulu, kemudian **Klasifikasi**.

## Alur Kerja Machine Learning

1. **Import Library**: Memuat seluruh pustaka yang diperlukan.
2. **Memuat Dataset**: Membaca data transaksi ke dalam DataFrame.
3. **Exploratory Data Analysis (EDA)**: Memahami distribusi dan karakteristik data.
4. **Preprocessing**: Pembersihan data, encoding, dan normalisasi.
5. **Clustering**: Pembentukan cluster sebagai label target.
6. **Data Splitting**: Memisahkan data latih dan data uji.
7. **Pemodelan Klasifikasi**: Melatih model Decision Tree dan model lain.
8. **Hyperparameter Tuning**: Mengoptimalkan performa model.
9. **Evaluasi**: Mengukur akurasi dan metrik lainnya.

## Penulis

**Andry Afrinaldo**: Submission Akhir BMLP Dicoding.
