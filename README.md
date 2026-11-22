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

- **Nama File**: `marketing_campaign.csv`
- **Sumber Dataset**: Customer Personality Analysis — Kaggle ; yang dapat diakses melalui link berikut : https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis
- **Dimensi Data**: 2.240 baris dan 29 kolom
- **Deskripsi Singkat Fitur**:
  - **Demografi & Profil**: `ID`, `Year_Birth` (tahun lahir), `Education` (tingkat pendidikan), `Marital_Status` (status pernikahan), `Income` (pendapatan tahunan rumah tangga), `Kidhome` (jumlah anak kecil), `Teenhome` (jumlah remaja), `Dt_Customer` (tanggal bergabung menjadi pelanggan), `Recency` (jumlah hari sejak pembelian terakhir), `Complain` (riwayat keluhan dalam 2 tahun terakhir).
  - **Pengeluaran Produk (2 tahun terakhir)**: `MntWines`, `MntFruits`, `MntMeatProducts`, `MntFishProducts`, `MntSweetProducts`, `MntGoldProds`.
  - **Perilaku & Kanal Pembelian**: `NumDealsPurchases` (pembelian dengan diskon), `NumWebPurchases` (pembelian via web), `NumCatalogPurchases` (pembelian via katalog), `NumStorePurchases` (pembelian langsung di toko), `NumWebVisitsMonth` (kunjungan web per bulan).
  - **Respons Kampanye**: `AcceptedCmp1` – `AcceptedCmp5`, `Response`, serta atribut konstanta `Z_CostContact` dan `Z_Revenue`.

---

## 4. Struktur Repository

```text
├── README.md                  # Dokumentasi utama proyek
├── marketing_campaign.csv     # Dataset pelanggan ritel 
└── notebook.ipynb             # Jupyter Notebook berisi keseluruhan alur analisis
