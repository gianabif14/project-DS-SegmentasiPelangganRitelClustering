# Segmentasi Profil dan Perilaku Pelanggan Ritel Berdasarkan Pendapatan dan Riwayat Transaksi Belanja Menggunakan Metode Clustering

**Kelompok 2 : Kata gian sama ito mau diet**  
---

## 1. Ringkasan Proyek

Proyek akhir ini bertujuan untuk menganalisis dan mengelompokkan pelanggan ritel (*customer segmentation*) berdasarkan profil demografis, tingkat pendapatan (*Income*), serta pola dan riwayat transaksi belanja di berbagai kanal penjualan maupun kategori produk.

Dengan menggunakan pendekatan **Clustering** (*unsupervised learning*), proyek ini disusun secara berurutan melalui 7 tahapan utama sesuai panduan proyek akhir:
- **Tahap A — Business Understanding**: Latar belakang masalah, pertanyaan bisnis, metode *clustering* (K-Means, Agglomerative Hierarchical Clustering, dan DBSCAN), serta metrik evaluasi (Inertia/Elbow, Silhouette Score, Davies-Bouldin Index, Calinski-Harabasz Index, uji generalisasi Train vs Test, serta validasi eksternal `Response`).
- **Tahap B — Data Gathering**: Pemuatan data mentah (`marketing_campaign.csv`), sumber dan kredibilitas dataset, alasan pemilihan, serta kamus data 29 kolom dalam 4 dimensi utama.
- **Tahap C — Exploratory Data Analysis (EDA)**: Statistik deskriptif dan visualisasi data disertai penjelasan temuan di bawah setiap grafik.
- **Tahap D — Cleaning, Preprocessing, dan Feature Selection**: Audit kualitas data, pembersihan data (komparasi sebelum vs sesudah), rekayasa fitur, seleksi fitur, *log-transform*, *scaling*, *train-test split*, dan PCA.
- **Tahap E — Modelling**: Pembuatan model utama (**K-Means**) serta model pembanding (**Agglomerative Hierarchical Clustering** dan **DBSCAN**) beserta alasan pada setiap langkah kode.
- **Tahap F — Evaluasi**: Perbandingan metrik penilaian, grafik pendukung, uji generalisasi (Train vs Test), pemilihan model terbaik, serta *profiling* segmen pelanggan.
- **Tahap G — Konklusi**: Jawaban atas pertanyaan bisnis, terjemahan metrik ke bahasa bisnis, rekomendasi strategis per segmen, dan keterbatasan proyek.

---

## 2. Anggota Kelompok & Kontribusi

Seluruh anggota berpartisipasi bersama dalam **pencarian dan validasi dataset** serta **penyusunan laporan proyek akhir** (penjelasan narasi, analisis temuan, dan kesimpulan), dengan pembagian peran spesifik yang merata sebagai berikut:

| No | Nama | NIM | Peran & Kontribusi |
| :--- | :--- | :--- | :--- |
| 1 | **Grahito Ardianto Purnomo** | 123240001 | **Koordinator Business Understanding & Data Gathering + Penyusun PPT Presentasi**: Bersama tim mencari dataset & menyusun laporan proyek akhir; merumuskan masalah bisnis, pertanyaan analisis, kamus data 29 kolom, serta merancang dan menyusun materi PPT presentasi. |
| 2 | **Fahri Hidayatullah** | 123240002 | **Pengembang Utama Kode Preprocessing & Penyusun `README.md`**: Bersama tim mencari dataset & menyusun laporan proyek akhir; menyusun dan merapikan `README.md` repository, mengelola berkas repository, serta mengembangkan kode tahap EDA, *cleaning*, *preprocessing*, rekayasa fitur, dan seleksi fitur di notebook. |
| 3 | **Krocasadigandra Arzaq Kubro M.** | 123240015 | **Pengembang Utama Kode Modelling & Evaluasi**: Bersama tim mencari dataset & menyusun laporan proyek akhir; mengembangkan implementasi kode algoritma *clustering* (K-Means, Agglomerative Hierarchical Clustering, dan DBSCAN), evaluasi metrik, uji generalisasi Train vs Test, serta *profiling* segmen. |
| 4 | **Gian Abi Firdaus** | 123240017 | **Penyusun Narasi Konklusi, Validasi Hasil & Pendukung PPT Presentasi**: Bersama tim mencari dataset & menyusun laporan proyek akhir; merumuskan jawaban pertanyaan bisnis, terjemahan metrik ke bahasa bisnis, rekomendasi per segmen, keterbatasan proyek, serta membantu penyiapan materi PPT presentasi. |

---

## 3. Sumber Data

- **Nama dataset**: Customer Personality Analysis
- **Berkas**: `marketing_campaign.csv` (pemisah kolom tab `\t`, terdiri atas 2.240 baris dan 29 kolom)
- **Tautan sumber**: [Kaggle - Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis) (diunggah oleh `imakash3011`, disediakan oleh Dr. Omar Romero-Hernandez)
- **Lisensi**: CC0: Public Domain
- **Periode data**: Pendaftaran pelanggan (`Dt_Customer`) tercatat dari 30 Juli 2012 hingga 29 Juni 2014

Kolom pada dataset terbagi ke dalam empat kelompok atribut utama:

1. **People** (profil dan demografi): `ID`, `Year_Birth`, `Education`, `Marital_Status`, `Income`, `Kidhome`, `Teenhome`, `Dt_Customer`, `Recency`, `Complain`.
2. **Products** (pengeluaran dua tahun terakhir): `MntWines`, `MntFruits`, `MntMeatProducts`, `MntFishProducts`, `MntSweetProducts`, `MntGoldProds`.
3. **Promotion** (diskon dan respons kampanye): `NumDealsPurchases`, `AcceptedCmp1`, `AcceptedCmp2`, `AcceptedCmp3`, `AcceptedCmp4`, `AcceptedCmp5`, `Response`.
4. **Place** (kanal pembelian dan kunjungan situs web): `NumWebPurchases`, `NumCatalogPurchases`, `NumStorePurchases`, `NumWebVisitsMonth`.

Terdapat pula dua kolom bernilai konstan pada seluruh baris, yaitu `Z_CostContact` (3) dan `Z_Revenue` (11), yang tidak digunakan dalam pemodelan. Pemeriksaan awal juga menemukan 24 nilai kosong (1,07%) pada kolom `Income`, 182 baris identik apabila kolom `ID` diabaikan, beberapa nilai anomali (`Year_Birth` 1893, 1899, 1900 serta `Income` 666.666), dan kategori tidak konsisten pada `Marital_Status` (`Alone`, `Absurd`, `YOLO`).

---

## 4. Struktur Repository

- `README.md` — Dokumentasi utama proyek
- `marketing_campaign.csv` — Dataset pelanggan ritel (delimiter Tab `\t`)
- `notebook.ipynb` — Jupyter Notebook berisi keseluruhan alur analisis (Tahap A–G)

---

## 5. Panduan Menjalankan Proyek

### Prasyarat
Pastikan lingkungan **Python 3.10+** (sesuai metadata kernel notebook) telah terpasang beserta pustaka berikut:
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scipy`
- `scikit-learn`
- `jupyter` (atau lingkungan Jupyter / VS Code / Google Colab)

### Langkah-Langkah
1. **Clone repository** ke komputer lokal:
   `git clone <url-repository-github-kalian>` lalu masuk ke folder proyek dengan `cd <nama-folder-repository>`.
2. **Instal dependensi** yang dibutuhkan:
   Jalankan `pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter` di terminal atau *command prompt*.
3. **Pastikan berkas dataset berada satu folder dengan notebook**:
   Notebook mengacu pada `DATA_PATH = "marketing_campaign.csv"` dan membacanya menggunakan `pd.read_csv(DATA_PATH, sep="\t")` dengan tahun referensi `REF_YEAR = 2014` serta `RANDOM_STATE = 42`.
4. **Buka dan jalankan notebook**:
   Jalankan `jupyter notebook` (atau buka langsung melalui VS Code / Google Colab), buka file `.ipynb` utama, lalu jalankan seluruh sel secara berurutan mulai dari **Bagian 0 (Setup Lingkungan & Import Library)** hingga **Tahap G (Konklusi)**.
