Laporan Proyek Machine Learning - Syihabudin Rahmat R

Domain Proyek

Proyek ini berfokus pada prediksi harga tukar USD/IDR menggunakan pendekatan machine learning dengan model LSTM (Long Short-Term Memory).

Business Understanding

Latar Belakang:

Pergerakan nilai tukar USD/IDR mempengaruhi banyak aspek kehidupan ekonomi di Indonesia, termasuk daya beli masyarakat, ekspor-impor, dan investasi asing. Memprediksi pergerakan nilai tukar ini dapat membantu para pelaku pasar dalam pengambilan keputusan investasi dan manajemen risiko.

Problem Statements:

Bagaimana memprediksi pergerakan harga tukar USD/IDR di masa depan dengan tingkat akurasi yang tinggi?
Apakah terdapat pola atau faktor tertentu yang secara signifikan mempengaruhi perubahan nilai tukar USD/IDR?

Goals:

Mengembangkan model machine learning yang dapat memprediksi pergerakan harga tukar USD/IDR dengan tingkat akurasi yang tinggi.
Mengidentifikasi faktor-faktor utama yang mempengaruhi perubahan nilai tukar USD/IDR.
Data Understanding
Data yang digunakan adalah dataset historis harga tukar USD/IDR. Dataset ini berisi informasi tanggal dan harga penutupan (close) dari perdagangan mata uang USD/IDR.

Data Preparation

Data dibersihkan dari nilai yang hilang.
Dilakukan penskalaan data menggunakan MinMaxScaler.

Modeling

Model LSTM (Long Short-Term Memory) digunakan untuk melakukan prediksi.
Arsitektur model terdiri dari dua lapisan LSTM dan beberapa lapisan Dense.

Evaluation

Metrik evaluasi yang digunakan adalah Mean Absolute Error (MAE).
Hasil model dinilai berdasarkan MAE dan threshold MAE yang ditetapkan.
