# 🍄 Mushroom Classification — Take-Home Challenge

## Identitas

| Field | Value |
|-------|-------|
| Nama | Rizky Ahmad Arief |
| NIM | 09020182529006 |
| Jurusan | Komputerisasi Akuntansi |
| Tanggal | 13 September 2026 |

---

## Tentang Proyek Ini

Jamur liar itu beragam sekali bentuk, warna, dan baunya — tapi tidak semuanya aman untuk dimakan. Tugas ini membangun model machine learning yang bisa membedakan jamur **edible** (aman) dari yang **poisonous** (beracun) berdasarkan ciri-ciri fisiknya.

Datanya terdiri dari 8124 sampel jamur, masing-masing punya 23 fitur kategorikal — dari aroma, bentuk tudung, warna insang, sampai habitat. Distribusinya cukup merata: 51.8% edible, 48.2% poisonous. Tidak perlu teknik khusus untuk menangani ketidakseimbangan kelas.

Alur kerjanya sendiri berjalan dari pemahaman data, eksplorasi visual (EDA), preprocessing, pelatihan model, evaluasi, sampai interpretasi hasil. Empat model diuji: Logistic Regression, Decision Tree, Random Forest, dan Neural Network. Selain itu, ada empat bonus challenge — PCA, SHAP, model lanjutan (XGBoost, SVM, KNN), dan pipeline prediksi end-to-end.

---

## Sekilas Soal Dataset

- **8124 baris** × **23 kolom** — seluruhnya kategorikal
- **Target:** `class` (`e` = Edible, `p` = Poisonous)
- **Fitur yang dibuang:**
  - `stalk-root` — 30.5% isinya `?` (missing value tersamar), terlalu besar untuk diimputasi
  - `veil-type` — nilainya cuma `p` di semua baris, tidak ada variasi
- **Sisa fitur:** 22 kolom kategorikal yang informatif

---

## Hasil Modeling

| Model | Accuracy | Catatan |
|-------|----------|---------|
| Logistic Regression | ~0.99 | Baseline — simpel, mudah diinterpretasi |
| Decision Tree | ~1.00 | Fleksibel, tapi rawan overfitting |
| Random Forest | ~1.00 | **Pilihan utama** — akurat, stabil, bisa dijelaskan |
| Neural Network | ~0.99 | Kompetitif, tapi butuh lebih banyak tuning |

**Random Forest** jadi model utama karena menggabungkan akurasi tinggi dengan kestabilan ensemble. Untuk data tabular seperti ini, Random Forest sering kali sebagus atau lebih baik dari deep learning.

---

## Apa yang Paling Mempengaruhi Prediksi

Berdasarkan analisis Feature Importance dan SHAP:

1. **Aroma (odor)** — fitur paling kuat. Jamur tanpa bau hampir pasti edible; bau foul/fishy/spicy hampir pasti poisonous.
2. **Ukuran insang (gill-size)** — insang lebar cenderung edible, sempit cenderung poisonous.
3. **Warna insang (gill-color)** — pola warnanya cukup konsisten untuk membedakan kelas.
4. **Jenis cincin (ring-type)** — perbedaan bentuk cincin mengikut pola tertentu.
5. **Warna cetakan spora (spore-print-color)** — kontribusinya signifikan juga.

---

## Bonus Challenge

| Bonus | Isi |
|-------|-----|
| **PCA Visualization** | Pemisahan edible vs poisonous divisualisasikan di ruang 2D |
| **SHAP Explainability** | Interpretasi prediksi di level individu — kenapa model bilang jamur ini edible/poisonous |
| **Advanced Models** | XGBoost, SVM, KNN — model tambahan untuk perbandingan |
| **Prediction Function** | Pipeline end-to-end: input ciri-ciri jamur mentah, langsung keluar label dan probabilitas |

---

## Cara Pakai

1. Install dependencies-nya dulu:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow shap xgboost
```

2. Buka folder `notebook/`, lalu jalankan notebook-nya:

```bash
cd notebook
jupyter notebook Rizky_Ahmad_Arief_09020182529006_TakeHomeML.ipynb
```

3. Jalankan semua cell dari atas ke bawah (Cell → Run All).

---

## Struktur Repo

```
Mushroom-Classification/
├── data/
│   └── mushrooms.csv
├── notebook/
│   └── Rizky_Ahmad_Arief_09020182529006_TakeHomeML.ipynb
└── README.md
```
