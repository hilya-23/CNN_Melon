# CNN_Melon
Deteksi Kekurangan Makronutrien Melon Menggunakan ResNet50

Di Susun Oleh
1. reva pramaulidia (240441100131)
2. hilyatul abidah (240441100132)
3. rizqita martha amalia (240441100027)


Pendahuluan
Notebook ini mendemonstrasikan implementasi model deep learning (ResNet50) untuk mendeteksi kekurangan makronutrien pada tanaman melon. Proyek ini mengeksplorasi tiga skenario berbeda: Transfer Learning dasar, Transfer Learning dengan Augmentasi Data, dan Transfer Learning dengan Augmentasi Data dan Fine-tuning.

Dataset
Dataset yang digunakan terdiri dari gambar-gambar daun melon yang dikategorikan berdasarkan kekurangan makronutrien dan kondisi sehat. Kelas-kelas yang ada meliputi:

calcium (kekurangan kalsium)
health (sehat)
nitrogen (kekurangan nitrogen)
potasium (kekurangan kalium)
Jumlah total gambar dalam dataset adalah 200 gambar, dengan 50 gambar untuk setiap kelas.

Pra-pemrosesan Data
Split Data: Dataset dibagi menjadi subset pelatihan (training), validasi (validation), dan pengujian (testing) dengan rasio berikut:
Training: 80% (160 gambar)
Validation: 10% (20 gambar)
Testing: 10% (20 gambar)
Transformasi Gambar: Gambar diubah ukurannya menjadi 224x224 piksel dan dinormalisasi menggunakan mean dan standard deviation ImageNet.
Augmentasi Data (untuk Skenario 2 & 3): Untuk data pelatihan, augmentasi diterapkan termasuk RandomResizedCrop, RandomHorizontalFlip, RandomRotation, dan ColorJitter untuk meningkatkan variasi data dan membantu mencegah overfitting.
Model dan Skenario Eksperimen
Semua skenario menggunakan arsitektur model ResNet50 yang telah dilatih sebelumnya (pre-trained) pada dataset ImageNet. Lapisan klasifikasi terakhir (Fully Connected layer) disesuaikan untuk empat kelas keluaran spesifik pada dataset melon.

Skenario 1: Transfer Learning (Dasar)
Strategi: Membekukan semua lapisan ResNet50 kecuali lapisan Fully Connected (FC) terakhir, yang dilatih dari awal.
Augmentasi: Tidak ada augmentasi data yang digunakan.
Optimizer: Adam dengan learning rate 0.001.
Epochs: 10
Hasil Evaluasi pada Data Uji:
Accuracy : 1.0000
Precision : 1.0000
Recall : 1.0000
F1-Score : 1.0000

Skenario 2: Transfer Learning + Augmentasi Data
Strategi: Sama seperti Skenario 1 (membekukan semua lapisan kecuali FC terakhir).
Augmentasi: Augmentasi data diterapkan pada data pelatihan.
Optimizer: Adam dengan learning rate 0.001.
Epochs: 10
Hasil Evaluasi pada Data Uji:
Accuracy : 1.0000
Precision : 1.0000
Recall : 1.0000
F1-Score : 1.0000

Skenario 3: Transfer Learning + Augmentasi Data + Fine-tuning
Strategi: Membekukan sebagian besar lapisan ResNet50, tetapi melepas pembekuan (unfreeze) lapisan konvolusional terakhir (layer4) dan lapisan FC terakhir. Kedua lapisan ini dilatih kembali (fine-tuned).
Augmentasi: Augmentasi data diterapkan pada data pelatihan.
Optimizer: Adam dengan learning rate 0.001 untuk lapisan FC dan 0.0001 (lebih rendah) untuk lapisan konvolusional (layer4).
Epochs: 10
Hasil Evaluasi pada Data Uji:
Accuracy : 1.0000
Precision : 1.0000
Recall : 1.0000
F1-Score : 1.0000

Kesimpulan
Semua skenario menunjukkan performa yang sangat baik pada dataset pengujian, mencapai akurasi 100%. Hal ini mungkin disebabkan oleh ukuran dataset yang relatif kecil dan perbedaan visual yang jelas antar kelas. Implementasi augmentasi data dan fine-tuning pada Skenario 2 dan 3 adalah praktik terbaik untuk generalisasi model yang lebih baik pada dataset yang lebih besar atau lebih kompleks di masa mendatang.
