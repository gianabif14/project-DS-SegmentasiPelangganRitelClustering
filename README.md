# Segmentasi Profil dan Perilaku Pelanggan Ritel Berdasarkan Pendapatan dan Riwayat Transaksi Belanja Menggunakan Metode Clustering

**Kelompok 2 : Kata gian sama ito mau diet**  
---

## 1. Ringkasan Proyek

Proyek akhir ini bertujuan untuk menganalisis dan mengelompokkan pelanggan ritel (*customer segmentation*) berdasarkan profil demografis, tingkat pendapatan (*Income*), serta pola dan riwayat transaksi belanja di berbagai kanal penjualan maupun kategori produk.

Dengan menggunakan pendekatan **Clustering** (*unsupervised learning*), proyek ini disusun melalui alur kerja *Data Science* yang meliputi:
- **Business Understanding**: Perumusan masalah segmentasi pelanggan, tujuan analisis, serta pemilihan metode dan metrik evaluasi klaster (seperti *Silhouette Score* / *Inertia*).
- **Data Gathering**: Pemuatan serta pemahaman struktur dan deskripsi setiap atribut pada dataset pelanggan ritel.
- **Exploratory Data Analysis (EDA)**: Eksplorasi statistik deskriptif dan visualisasi distribusi demografi, pendapatan, serta pengeluaran produk.
- **Data Cleaning & Preprocessing**: Penanganan *missing values* (seperti pada kolom `Income`), pengecekan duplikat dan *outlier*, transformasi fitur, penskalaan data (*feature scaling*), serta *feature selection*.
- **Modelling**: Penerapan algoritma *clustering* sesuai materi praktikum untuk membentuk segmen pelanggan yang optimal.
- **Evaluasi & Konklusi**: Evaluasi kualitas klaster yang terbentuk, interpretasi karakteristik masing-masing segmen pelanggan, serta rekomendasi strategi pemasaran yang relevan.

---

## 2. Anggota Kelompok & Kontribusi

| No | Nama | NIM | Peran & Kontribusi |
| :--- | :--- | :--- | :--- |
| 1 | **Grahito Ardianto Purnomo** | 123240001 |
| 2 | **Fahri Hidayatullah** | 123240002 |
| 3 | **Krocasadigandra Arzaq Kubro M.** | 123240015 |
| 4 | **Gian Abi Firdaus** | 123240017 |

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

```text
├── README.md                  # Dokumentasi utama proyek
├── marketing_campaign.csv     # Dataset pelanggan ritel 
└── notebook.ipynb             # Jupyter Notebook berisi keseluruhan alur analisis
