## Laporan Proyek Machine Learning - Syihabudin Rahmat R

### Domain Proyek
Proyek ini berfokus pada prediksi harga tukar USD/IDR menggunakan pendekatan machine learning dengan model LSTM (Long Short-Term Memory).

### Business Understanding

**Latar Belakang:**
Pergerakan nilai tukar USD/IDR adalah aspek penting dalam ekonomi Indonesia. Prediksi pergerakan nilai tukar ini memiliki nilai strategis dalam pengambilan keputusan investasi dan manajemen risiko. Dengan menggunakan pendekatan machine learning, kita dapat mengembangkan model yang dapat memprediksi pergerakan harga tukar USD/IDR di masa depan dengan tingkat akurasi yang tinggi. Hal ini akan membantu para pelaku pasar dalam mengantisipasi perubahan pasar dan mengambil keputusan yang tepat secara finansial.

**Problem Statements:**
1. Bagaimana memprediksi pergerakan harga tukar USD/IDR di masa depan dengan tingkat akurasi yang tinggi?
2. Apakah terdapat pola atau faktor tertentu yang secara signifikan mempengaruhi perubahan nilai tukar USD/IDR?

**Goals:**
1. Mengembangkan model machine learning yang dapat memprediksi pergerakan harga tukar USD/IDR dengan tingkat akurasi yang tinggi.
2. Mengidentifikasi faktor-faktor utama yang mempengaruhi perubahan nilai tukar USD/IDR.

**Solution Statement:**
Untuk mencapai tujuan proyek, akan dikembangkan model machine learning menggunakan algoritma LSTM (Long Short-Term Memory) untuk memprediksi pergerakan harga tukar USD/IDR. Model akan dilatih dengan data historis dan dievaluasi menggunakan metrik Mean Absolute Error (MAE) untuk mengukur tingkat akurasi.

### Data Understanding
Data yang digunakan adalah dataset historis harga tukar USD/IDR. Dataset ini berisi informasi tanggal dan harga penutupan (close) dari perdagangan mata uang USD/IDR. Berikut adalah variabel atau fitur pada data tersebut:

- Date: Tanggal pencatatan data.
- Open: Harga pembukaan perdagangan USD/IDR.
- High: Harga tertinggi yang dicapai dalam perdagangan USD/IDR pada tanggal tersebut.
- Low: Harga terendah yang dicapai dalam perdagangan USD/IDR pada tanggal tersebut.
- Close: Harga penutupan perdagangan USD/IDR pada tanggal tersebut.
- Volume: Volume perdagangan total USD/IDR pada tanggal tersebut.

### Exploratory Data Analysis (EDA)
Tahap exploratory data analysis dilakukan untuk memahami data yang digunakan dalam proyek. Beberapa tahapan yang dilakukan antara lain:

- Deskripsi variabel: Memahami karakteristik data pada setiap variabel, seperti mean, median, dan distribusi.
- Penanganan nilai yang hilang: Mengidentifikasi dan menangani nilai yang hilang dalam dataset.
- Analisis univariat pada fitur numerik: Menganalisis distribusi dan statistik deskriptif dari setiap fitur numerik.
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/f0456a18-a04e-4e58-8783-6ef56f5e0657)
- Analisis multivariat pada fitur numerik: Mengeksplorasi hubungan antara beberapa fitur numerik.
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/f6b73b91-d21e-4517-b6ca-f0ec8346ef19)
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/44234801-3b65-468d-bcb6-5c2d051d0975)
- Visualisasi data: Menggunakan boxplot dan grafik lainnya untuk memvisualisasikan distribusi dan tren dalam data, termasuk close average dari harga tukar USD/IDR.
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/71264bce-c736-408f-8f3a-e14978386347)

![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/c95b2838-9e44-4879-bfca-66dc57f6a82d)

Dengan melakukan tahap-tahap ini, kita dapat memperoleh pemahaman yang mendalam tentang data dan persiapan yang tepat untuk membangun model prediksi.

### Data Preparation
- Data dibersihkan dari nilai yang hilang.
- Dilakukan penskalaan data menggunakan MinMaxScaler.

### Modeling
Model LSTM (Long Short-Term Memory) digunakan untuk melakukan prediksi. Arsitektur model terdiri dari dua lapisan LSTM dan beberapa lapisan Dense.

**Kelebihan dan Kekurangan Algoritma LSTM:**
**Kelebihan:**
- LSTM (Long Short-Term Memory) cocok untuk memodelkan data time series yang kompleks karena dapat mengingat informasi jangka panjang.
- Dapat menangani masalah vanishing gradient dengan baik, sehingga cocok untuk data dengan jarak waktu yang panjang.
- Memiliki arsitektur yang dapat mempertahankan informasi dari waktu sebelumnya, sehingga efektif untuk memprediksi pergerakan harga tukar yang berkaitan dengan pola dan tren masa lalu.

**Kekurangan:**
- Memiliki kompleksitas komputasi yang tinggi, sehingga memerlukan sumber daya komputasi yang cukup besar.
- Rentan terhadap overfitting, terutama pada dataset kecil atau ketika model memiliki banyak parameter.

**Improvement dengan Hyperparameter Tuning:**
Pada tahap improvement, dilakukan tuning terhadap hyperparameter model LSTM untuk meningkatkan performa dan akurasi prediksi. Beberapa hyperparameter yang dioptimalkan meliputi:
- Jumlah unit LSTM: Menentukan jumlah unit atau neuron dalam lapisan LSTM.
- Jumlah lapisan LSTM: Menentukan jumlah lapisan LSTM yang digunakan dalam arsitektur model.
- Learning rate: Menentukan tingkat pembelajaran yang optimal untuk proses training model.
- Batch size: Menentukan jumlah sampel yang digunakan dalam satu iterasi training.

Proses hyperparameter tuning dilakukan dengan mencoba berbagai kombinasi nilai hyperparameter dan memilih kombinasi yang memberikan hasil terbaik berdasarkan metrik evaluasi yang ditetapkan.

**Plot Loss dan Akurasi**
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/cdaa0699-2cf8-4228-9fa6-a8d3c637ee94)

### Evaluation
**Metrik Evaluasi yang Digunakan:**
Dalam proyek ini, kami menggunakan metrik evaluasi Mean Absolute Error (MAE) untuk mengevaluasi kinerja model dalam memprediksi harga tukar USD/IDR. MAE mengukur rata-rata dari selisih absolut antara nilai prediksi dan nilai sebenarnya.

Formula untuk MAE adalah:

MAE = (1/n) Σ(i=1 to n) |y_i – ŷ_i|


**Hasil Proyek Berdasarkan Metrik Evaluasi:**
Setelah melakukan evaluasi menggunakan metrik MAE, kami memperoleh hasil sebagai berikut:
- Mean Absolute Error: 0.0277
- Threshold MAE: 0.1

**Plot harga aktual dan harga prediksi**
![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/05237876-d8f9-4b70-846a-89e3613c300b)

Dari hasil tersebut, dapat disimpulkan bahwa model kami mampu memprediksi pergerakan harga tukar USD/IDR
