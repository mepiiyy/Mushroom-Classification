# 🍄 Mushroom Classification — Take-Home Challenge

## Identitas

| Field | Value |
|-------|-------|
| Nama | Rizky Ahmad Arief |
| NIM | 09020182529006 |
| Jurusan | Komputerisasi Akuntansi |
| Tanggal | 13 September 2026 |

---

## Ringkasan Proyek

Tugas ini membangun model klasifikasi untuk membedakan jamur **edible** (aman dimakan) dan **poisonous** (beracun) menggunakan dataset mushrooms.csv. Dataset terdiri dari 8124 jamur dengan 23 fitur kategorikal, dan distribusi kelasnya cukup seimbang (51.8% edible, 48.2% poisonous).

Pipeline yang dilakukan: pemahaman data → EDA → preprocessing (penghapusan kolom `stalk-root` dan `veil-type`, One-Hot Encoding) → pelatihan empat model (Logistic Regression, Decision Tree, Random Forest, Neural Network) → evaluasi dan perbandingan → tuning hyperparameter → interpretasi model.

---

## Struktur Dataset

- **8124 baris** × **23 kolom**
- **Target:** `class` (`e` = Edible, `p` = Poisonous)
- **Fitur:** 22 fitur kategorikal (dari 23, `stalk-root` dihapus karena 30.5% missing value, `veil-type` dihapus karena konstan)
- **Missing value:** Tidak ada NaN, tapi ada 2480 nilai `?` di `stalk-root`

---

## Model yang Diuji

| Model | Accuracy | Keterangan |
|-------|----------|------------|
| Logistic Regression | ~0.99 | Baseline — sederhana tapi interpretable |
| Decision Tree | ~1.00 | Fleksibel, berisiko overfitting |
| Random Forest | ~1.00 | **Terbaik** — ensemble, stabil, interpretable |
| Neural Network | ~0.99 | Kompetitif, butuh lebih banyak tuning |

**Random Forest** jadi pilihan utama: menggabungkan akurasi tinggi dengan stabilitas ensemble.

---

## Fitur Paling Berpengaruh

1. **Odor (Aroma)** — hampir bisa menentukan class sendirian
2. **Gill-size (Ukuran insang)** — membedakan edible vs poisonous
3. **Gill-color (Warna insang)** — informasi tambahan signifikan
4. **Ring-type (Jenis cincin)** — pola yang konsisten
5. **Spore-print-color (Warna cetakan spora)** — kontribusi kuat

---

## Bonus Challenge

| Bonus | Deskripsi |
|-------|-----------|
| PCA Visualization | Pemisahan edible vs poisonous di ruang 2D |
| SHAP Explainability | Interpretasi prediksi di level individu |
| Advanced Models | XGBoost, SVM, KNN |
| Prediction Function | Pipeline end-to-end dari input mentah sampai label |

---

## Cara Menjalankan

```bash
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow shap xgboost
```

Buka Jupyter Notebook:
```bash
cd notebook
jupyter notebook Rizky_Ahmad_Arief_09020182529006_TakeHomeML.ipynb
```

Jalankan semua cell dari atas ke bawah (Cell → Run All).

---

## File

```
Mushroom-Classification/
├── data/
│   └── mushrooms.csv
├── notebook/
│   └── Rizky_Ahmad_Arief_09020182529006_TakeHomeML.ipynb
└── README.md
```
