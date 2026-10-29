# PM-Turi4-clustering

# TuRi 4: Clustering dengan K-Means (Segmentasi Pelanggan)

Praktikum **Pertemuan 9** mata kuliah **Pembelajaran Mesin** (INF62325, 3 SKS), Sub-CPMK SCPMK0401-003.

**Nama:** Kurniawan Aji Saputra Romadhon
**NIM:** 2488010027
**Kelas:** INFORMATIKA 5B

## Deskripsi

Proyek ini menerapkan **K-Means clustering** (unsupervised learning) untuk mengelompokkan pelanggan berdasarkan tiga fitur: `usia`, `pendapatan` (Rp/bulan), dan `skor_belanja` (1–100). Dataset berupa data sintetis 200 pelanggan yang dibuat di dalam notebook (seed 42), sehingga hasilnya dapat direproduksi.

## Tujuan

- Menyiapkan data tanpa label untuk clustering, termasuk scaling.
- Menentukan jumlah cluster optimal dengan metode Elbow.
- Menerapkan K-Means dan memvisualisasikan hasilnya.
- Mengevaluasi clustering dengan silhouette score.
- Menafsirkan makna tiap cluster sebagai segmen pelanggan.

## Struktur Repositori

```
pm-turi4-clustering/
├── Praktikum9_Clustering_KMeans.ipynb   # notebook utama
└── README.md
```

## Cara Menjalankan

1. Buka notebook di Google Colab (atau Jupyter Notebook).
2. Pilih **Runtime → Run all**. Seluruh sel berjalan tanpa error dan semua grafik tampil.

Pustaka yang digunakan: `numpy`, `pandas`, `matplotlib`, `scikit-learn`.

## Alur Pengerjaan

1. **Scaling:** fitur distandarkan dengan `StandardScaler` karena K-Means berbasis jarak.
2. **Metode Elbow:** inertia dihitung untuk K = 1–10.
3. **K-Means (K=3):** `KMeans(n_clusters=3, random_state=42, n_init=10)`.
4. **Evaluasi:** silhouette score.
5. **Interpretasi:** profil rata-rata tiap cluster, lalu penamaan segmen.

## Hasil Utama

**Metode Elbow:** siku terlihat jelas di **K = 3**.

| K | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Inertia | 600,0 | 266,8 | 73,3 | 62,4 | 52,6 |

**Silhouette score (K=3, dengan scaling): 0,702**

**Profil dan nama cluster:**

| Segmen | Usia | Pendapatan (Rp/bln) | Skor belanja | Jumlah |
|---|---|---|---|---|
| Muda Konsumtif | 24,2 | 5.358.571 | 77,5 | 70 |
| Premium / Sultan | 37,9 | 16.296.667 | 80,4 | 60 |
| Hemat / Pasif | 49,8 | 6.530.000 | 23,5 | 70 |

**Saran strategi:**
- **Muda Konsumtif:** cicilan/paylater, bundling, promosi media sosial.
- **Premium / Sultan:** program loyalitas VIP, produk premium.
- **Hemat / Pasif:** voucher dan promo reaktivasi.

## Latihan Mandiri

| Percobaan | Silhouette | Kesimpulan |
|---|---|---|
| K=3 dengan scaling | 0,702 | Terbaik, sesuai 3 kelompok alami |
| K=5 dengan scaling | 0,452 | Kelompok utuh terpecah, separasi menurun |
| K=3 tanpa scaling | 0,606 | Pendapatan mendominasi jarak, segmen berbeda tercampur |

Scatter plot usia vs skor belanja (lengkap dengan centroid) tersedia di notebook.

## Kesimpulan

- Scaling wajib untuk algoritma berbasis jarak seperti K-Means.
- Elbow dan silhouette sama-sama mendukung **K = 3**.
- Tiga segmen yang terbentuk memiliki karakter berbeda dan dapat ditindaklanjuti dengan strategi pemasaran yang berbeda.
- Tanpa scaling, cluster didominasi pendapatan dan menjadi kurang bermakna secara bisnis.
