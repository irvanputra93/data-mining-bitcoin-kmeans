# Pemetaan Profil Risiko Investasi Bitcoin Menggunakan K-Means Clustering

Proyek mata kuliah **Data Mining** (Prodi Sistem Informasi, UTDI) yang melakukan *Exploratory Data Analysis* (EDA) dan klasterisasi tanpa pengawasan (*unsupervised learning*) menggunakan algoritma **K-Means Clustering** pada data historis Bitcoin.

## Dataset
- **Sumber:** Kaggle — *Bitcoin Historical Dataset for Market Analysis* (`bitcoin_dataset.csv`)
- **Cakupan:** 4.280 data harian (17 September 2014 – 5 Juni 2026) dengan atribut `Date`, `Open`, `High`, `Low`, `Close`, `Adj Close`, dan `Volume`
- **Kualitas Data:** 0 *missing values* dan 0 baris duplikat

## Ringkasan Alur & Hasil
1. **Preprocessing & Feature Engineering:** Konversi kolom `Date` ke format *datetime*, pengurutan kronologis, serta pembuatan fitur `Daily_Volatility = High - Low`.
2. **Feature Selection & Scaling:** Seleksi fitur utama `Close` dan `Daily_Volatility` untuk mengurangi multikolinearitas antar indikator harga, *split* data 80% *training* (3.424 baris) dan 20% *testing* (856 baris), lalu distandardisasi menggunakan `StandardScaler`.
3. **Penentuan Klaster (`K = 3`):** Dipilih berdasarkan titik siku *Elbow Method* (`K = 1` s.d. `10`).
4. **Segmentasi Klaster & Evaluasi:**
   - **Klaster 0 (Risiko Rendah):** 2.313 data *training* | 576 data *testing*
   - **Klaster 1 (Risiko Sedang):** 890 data *training* | 228 data *testing*
   - **Klaster 2 (Risiko Tinggi/Ekstrem):** 221 data *training* | 52 data *testing*
   - **Silhouette Score:** `0.6340`

## Batasan Proyek
Analisis ini bersifat deskriptif pada data historis untuk memetakan tingkat volatilitas/risiko masa lalu, bukan untuk peramalan (*forecasting*) harga Bitcoin di masa depan.

## Cara Menjalankan
1. Buka `LAPORAN_DATA_MINING_EDA.ipynb` di **Google Colab** atau **Jupyter Notebook/VS Code**.
2. Pastikan `bitcoin_dataset.csv` berada di direktori kerja yang sama (atau di-upload ke sesi Colab).
3. Jalankan sel kode secara berurutan dari atas ke bawah.
