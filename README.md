# PCD17
# Klasifikasi Jenis Warna/Tingkat Pemanggangan Biji Kopi Berdasarkan Tekstur dan Intensitas Warna

## Nama Anggota
### 1. MUZAYYAN ROZAAN : F1D02310018
### 2. FADILA RAHMANIA : F1D02310048
### 3. NAUFAL IHSANUL ISLAM : F1D02310084
### 4. NAUFAL PRAMUDYA ANANDA : F1D02310085


# Project Overview

<p align = justify>Mengetahui tingkat kematangan sangrai (roast level) biji kopi adalah fundamental bagi seorang barista karena berdampak langsung pada setiap aspek persiapan dan hasil akhir minuman kopi. .
Tujuan dari klasifikasi tingkat pemanggangan biji kopi berdasarkan tekstur dan intensitas warna adalah untuk memastikan konsistensi kualitas dan rasa kopi, mempermudah proses identifikasi secara visual maupun otomatis, serta mendukung efisiensi dalam produksi, pengemasan, dan pengembangan produk kopi sesuai preferensi konsumen.</p>

### Dataset
Dataset yang digunakan dalam proyek ini terdiri dari citra biji kopi 4 macam yaitu:
1. *Dark* :  Menunjukkan Biji kopi disangrai paling lama dan pada suhu tertinggi, biasanya hingga melewati second crack atau bahkan lebih lama lagi.
2. *Medium* :  Menunjukkan Biji kopi disangrai sedikit lebih lama dan/atau pada suhu yang sedikit lebih tinggi dibandingkan light roast.
3. *Light* : Menunjukkan Biji kopi disangrai dalam waktu yang lebih singkat dan pada suhu yang relatif lebih rendah.
4. *Green* : Menunjukkan adalah biji kopi dalam keadaan mentah.

Dataset diperoleh dari https://www.kaggle.com/datasets/gpiosenka/coffee-bean-dataset-resized-224-x-224 dan telah melalui proses preprocessing sebelum digunakan dalam pelatihan model.

# Metodologi
Proyek ini dilakukan melalui beberapa tahapan utama sebagai berikut:

## 1. Load Data
Membaca citra dari folder dataset, mengubah ke grayscale, dan resize ke ukuran seragam (128x128 piksel).

## 2. Preprocessing
Terdapat beberapa metode yang di terapkan dalam preprocessing proyek ini, yaitu:
- Greyscale: Membuat citra menjadi greyscale.
- Resize: Mengubah ukuran gambar agar sesuai dengan kebutuhan proses.
- Mean Filter: Mereduksi noise dan menghaluskan gambar.
- Spesifikasi: Menyesuaikan distribusi intensitas warna citra agar menyerupai citra referensi.
- Smoothing: Mengurangi fluktuasi intensitas piksel kecil (noise) agar citra terlihat lebih halus.
- Ekualisasi: Meningkatkan kontras citra dengan menyebarkan intensitas piksel.
#### Berdasarkan Metode yang sudah di sebutkan, terdapat 4 percobaan berbeda yang telah di lakukan untuk tahap preprocessing;
- Percobaan pertama : greyscale --> resize --> normalisasi
- Percobaan kedua : greyscale --> resize --> normalisasi --> smoothing
- Percobaan ketiga : ekualisasi --> spesifikasi
- Percobaan keempat : mean_filter --> ekualisasi --> spesifikasi

## 3. Ekstraksi Fitur
- Menggunakan metode GLCM (Gray-Level Co-occurrence Matrix) pada 4 sudut (0°, 45°, 90°, 135°).
- Fitur yang diekstrak: contrast, correlation, energy, homogeneity, ASM, entropy, dan dissimilarity.

## 4. Penyimpanan Fitur
- Hasil ekstraksi fitur disimpan dalam file CSV untuk memudahkan analisis dan pelatihan model.

## 5. Seleksi Fitur
- Menggunakan analisis korelasi untuk mengurangi fitur yang redundant (korelasi tinggi).

## 6. Split Dataset
- Membagi data menjadi data latih dan data uji (misal 80% training, 20% testing).

## 7. Normalisasi Fitur
- Menggunakan standardisasi (Z-score) agar fitur memiliki skala yang seragam.

## 8. Model Training
- Melatih tiga model klasifikasi: Random Forest, SVM, dan KNN.

## 9. Evaluasi Model
- Menggunakan metrik akurasi, precision, recall, classification report, dan confusion matrix untuk mengukur performa model.
