## Laporan Proyek Machine Learning - Syihabudin Rahmat R

### Domain Proyek

Proyek ini berada dalam bidang keuangan dan perdagangan mata uang. Masalah yang dihadapi adalah fluktuasi harga tukar USD/IDR yang sulit diprediksi secara akurat menggunakan metode konvensional. Fluktuasi harga tukar mata uang dapat dipengaruhi oleh berbagai faktor seperti kondisi ekonomi, kebijakan moneter, geopolitik, dan lain sebagainya. Prediksi yang akurat mengenai perubahan harga tukar mata uang dapat memberikan keuntungan bagi para pelaku pasar, termasuk investor, eksportir, dan importir.

### Urgensi Permasalahan

Urgensinya permasalahan ini terletak pada pentingnya informasi yang akurat mengenai perubahan harga tukar mata uang bagi para pemangku kepentingan. Kenaikan atau penurunan harga tukar dapat memiliki dampak yang signifikan pada keputusan investasi, perencanaan bisnis, dan strategi perdagangan. Oleh karena itu, pengembangan model machine learning yang dapat memprediksi perubahan harga tukar dengan tingkat akurasi yang tinggi dapat membantu para pemangku kepentingan untuk mengambil keputusan yang lebih baik dan lebih informatif.

### Latar Belakang

Nilai tukar USD/IDR merupakan aspek penting dalam ekonomi Indonesia. Fluktuasi nilai tukar ini dapat berdampak signifikan pada berbagai sektor, seperti perdagangan internasional, investasi, dan stabilitas ekonomi secara keseluruhan. Kemampuan untuk memprediksi pergerakan nilai tukar USD/IDR dengan tingkat akurasi yang tinggi akan memberikan manfaat strategis bagi berbagai pihak, termasuk:

- **Pelaku Pasar**: Investor, eksportir, importir, dan perusahaan multinasional dapat menggunakan prediksi nilai tukar untuk meminimalkan risiko dan memaksimalkan keuntungan dalam transaksi keuangan mereka.
- **Pemerintah**: Bank Indonesia dan lembaga pemerintah lainnya dapat menggunakan prediksi nilai tukar untuk merumuskan kebijakan moneter dan fiskal yang tepat guna menjaga stabilitas ekonomi.
- **Masyarakat Luas**: Prediksi nilai tukar dapat membantu masyarakat dalam membuat keputusan yang lebih tepat terkait dengan investasi, remitansi, dan kegiatan ekonomi lainnya yang melibatkan mata uang asing.

### Contoh Penerapan Prediksi

- Investor dapat menggunakan prediksi nilai tukar untuk menentukan waktu yang tepat untuk membeli atau menjual aset dalam mata uang asing.
- Eksportir dapat menggunakan prediksi nilai tukar untuk menetapkan harga yang kompetitif dan meminimalkan risiko kerugian akibat fluktuasi nilai tukar.
- Importir dapat menggunakan prediksi nilai tukar untuk mengoptimalkan biaya impor dan meminimalkan risiko fluktuasi nilai tukar.
- Bank Indonesia dapat menggunakan prediksi nilai tukar untuk melakukan intervensi di pasar valuta asing dan menjaga stabilitas nilai tukar rupiah.

### Problem Statement

1. Model machine learning yang dapat memprediksi fluktuasi harga tukar USD/IDR, mengatasi kendala fluktuasi yang sulit diprediksi menggunakan metode konvensional?
2. Seberapa akurat prediksi perubahan harga tukar USD/IDR yang dihasilkan oleh model machine learning yang dikembangkan?
3. Bagaimana penerapan model machine learning dalam memprediksi perubahan harga tukar USD/IDR dapat memberikan manfaat strategis bagi berbagai pemangku kepentingan, seperti investor, eksportir, importir, pemerintah, dan masyarakat luas?

### Goals

1. Mengembangkan model machine learning yang mampu memprediksi fluktuasi harga tukar USD/IDR dengan hasil evaluasi yang baik, memanfaatkan data historis yang mempengaruhi pergerakan nilai tukar.
2. Menyediakan prediksi perubahan harga tukar USD/IDR kepada para pemangku kepentingan, sehingga membantu mereka dalam pengambilan keputusan yang lebih baik terkait dengan investasi, perdagangan, dan kegiatan ekonomi lainnya.

### Solusi

Untuk mencapai tujuan proyek, akan dilakukan hal-hal berikut:

1. **Eksplorasi Data (EDA)**:
   - Analisis data historis harga tukar USD/IDR untuk memahami pola dan tren yang terkandung di dalamnya.
   - Identifikasi faktor-faktor ekonomi, kebijakan moneter, dan geopolitik yang mempengaruhi fluktuasi harga tukar.

2. **Pemilihan Model Machine Learning**:
   - Memilih model Long Short-Term Memory (LSTM) untuk memodelkan hubungan temporal dalam data deret waktu harga tukar USD/IDR.
   - LSTM dipilih karena kemampuannya dalam menangani ketergantungan jarak jauh dan memahami pola kompleks dalam data deret waktu.

3. **Pelatihan Model**:
   - Melatih model LSTM menggunakan data historis yang telah dipersiapkan, termasuk variabel tanggal, harga pembukaan, harga tertinggi, harga terendah, harga penutupan, dan volume perdagangan.
   - Model akan diperbarui secara iteratif untuk mempelajari pola dan hubungan dalam data.

4. **Evaluasi Model**:
   - Model akan dievaluasi menggunakan metrik Mean Absolute Error (MAE) untuk mengukur seberapa dekat prediksi model dengan nilai sebenarnya dari harga tukar USD/IDR.
   - Evaluasi akan dilakukan pada set data validasi untuk memastikan kinerja model secara objektif.

5. **Optimisasi Model**:
   - Jika hasil evaluasi menunjukkan kinerja yang kurang memuaskan, model akan dioptimalkan dengan menyesuaikan parameter, menambahkan fitur tambahan, atau mencoba arsitektur model yang lebih kompleks.

Dengan demikian, proyek ini bertujuan untuk mengembangkan solusi yang dapat memberikan prediksi yang akurat dan bermanfaat terkait dengan perubahan harga tukar USD/IDR untuk berbagai pemangku kepentingan di bidang keuangan dan perdagangan mata uang.

### Data Understanding
Data yang digunakan adalah dataset historis harga tukar USD/IDR dari Yahoo Finance. Dataset ini berisi informasi tanggal dan harga penutupan (close) dari perdagangan mata uang USD/IDR. Berikut adalah variabel atau fitur pada data tersebut:

|index|Date|Open|High|Low|Close|Adj Close|Volume|
|---|---|---|---|---|---|---|---|
|0|2019-03-18|14251\.0|14283\.0|14204\.0|14251\.0|14251\.0|0\.0|
|1|2019-03-19|14246\.0|14252\.0|14163\.0|14251\.0|14251\.0|0\.0|
|2|2019-03-20|14224\.0|14233\.299805|14159\.0|14223\.0|14223\.0|0\.0|
|3|2019-03-21|14115\.5|14159\.0|14055\.0|14055\.0|14055\.0|0\.0|
|4|2019-03-22|14152\.5|14279\.0|14120\.0|14133\.0|14133\.0|0\.0|

- Date: Tanggal pencatatan data.
- Open: Harga pembukaan perdagangan USD/IDR.
- High: Harga tertinggi yang dicapai dalam perdagangan USD/IDR pada tanggal tersebut.
- Low: Harga terendah yang dicapai dalam perdagangan USD/IDR pada tanggal tersebut.
- Close: Harga penutupan perdagangan USD/IDR pada tanggal tersebut.
- Volume: Volume perdagangan total USD/IDR pada tanggal tersebut.

Sumber dataset : https://finance.yahoo.com/quote/IDR%3DX/history

### Exploratory Data Analysis (EDA)
Tahap exploratory data analysis dilakukan untuk memahami data yang digunakan dalam proyek. Beberapa tahapan yang dilakukan antara lain:

- Deskripsi variabel: Memahami karakteristik data pada setiap variabel, seperti mean, median, dan distribusi.
  ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/f35fdfc9-02ef-4621-ba48-4e135c8e2506)
- Penanganan nilai yang hilang: Mengidentifikasi dan menangani nilai yang hilang dalam dataset.
- 
  ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/e37c6fa0-1e4a-4dd6-ba44-3bae4d1a2dd7)
- Analisis univariat pada fitur numerik: Menganalisis distribusi dan statistik deskriptif dari setiap fitur numerik.
  ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/f0456a18-a04e-4e58-8783-6ef56f5e0657)
   - Terlihat pada histogram distribusi data itu bahwa kurs idr/usd ini memiliki jumlah data yang banyak pada harga 14000 - 15000
- Analisis multivariat pada fitur numerik: Mengeksplorasi hubungan antara beberapa fitur numerik.
  ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/f6b73b91-d21e-4517-b6ca-f0ec8346ef19)
   - Pola Persebaran data tersebut memiliki korelasi positif. Hal ini ditandai dengan meningkatnya variabel pada sumbu y saat terjadi peningkatan variabel pada sumbu x
     
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/44234801-3b65-468d-bcb6-5c2d051d0975)
    - grafik korelasi tersebut menunjukan bahwa semua fitur memiliki korelasi yang besar dengan fitur price, dimana menunjukan nilai diatas 0.97

- Menangani Outliers
- ![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/71264bce-c736-408f-8f3a-e14978386347)
  - Dari gambar tersebut dapat dilihat bahwa ada outlier pada feature 'Close', IQR Akan digunakan untuk mengatasi masalah ini 

- Visualisasi data: memvisualisasikan distribusi dan tren dalam data, termasuk close average dari harga tukar USD/IDR.

![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/c95b2838-9e44-4879-bfca-66dc57f6a82d)
  - Rata-rata harga pada kurs idr/usd terlihat cenderung meningkat naik
    
Dengan melakukan tahap-tahap ini, kita dapat memperoleh pemahaman yang mendalam tentang data dan persiapan yang tepat untuk membangun model prediksi.

### Data Preparation

Dalam tahap persiapan data, langkah-langkah yang lebih rinci dilakukan sebagai berikut:

#### Handling Missing Values dan Outlier Menggunakan IQR

Langkah pertama adalah menangani nilai-nilai yang hilang dari dataset. Dalam kasus ini, nilai yang hilang atau NA dihapus dari dataset. Selain itu, untuk mengatasi outlier, teknik IQR (Interquartile Range) digunakan. Nilai yang dianggap sebagai outlier diidentifikasi menggunakan IQR, dan baris yang mengandung outlier dihapus dari dataset.

#### Scaling Data

Setelah nilai-nilai yang hilang dan outlier telah ditangani, data dinormalisasi atau diskalakan untuk memastikan bahwa semua fitur memiliki skala yang seragam. Normalisasi data dilakukan untuk membuatnya berada dalam rentang antara 0 dan 1. Dengan melakukan normalisasi, perbedaan skala antar fitur tidak akan memengaruhi kinerja model.

#### Split Data

Data kemudian dibagi menjadi dua subset: data pelatihan dan data validasi. Data pelatihan digunakan untuk melatih model, sedangkan data validasi digunakan untuk menguji kinerja model yang telah dilatih. Pembagian ini umumnya dilakukan dengan proporsi tertentu, misalnya 80% data untuk pelatihan dan 20% untuk validasi.

#### Membuat Dataset untuk Model LSTM

Terakhir, data disiapkan dalam format yang sesuai untuk digunakan dalam model LSTM. Model LSTM memerlukan data dalam format deret waktu. Oleh karena itu, data harus diubah menjadi urutan waktu yang sesuai dengan konfigurasi model LSTM. Hal ini mungkin melibatkan mengonversi data menjadi urutan waktu yang tepat sesuai dengan jendela waktu yang dipilih untuk pengamatan.

Dengan melakukan langkah-langkah di atas, data siap untuk digunakan dalam pelatihan model LSTM untuk memprediksi fluktuasi harga tukar USD/IDR. Proses persiapan data yang cermat sangat penting untuk memastikan keberhasilan model dalam mempelajari pola dari data dan membuat prediksi yang akurat.

### Modeling
Model yang digunakan dalam kode ini adalah model jaringan saraf tiruan (neural network) berbasis LSTM (Long Short-Term Memory). LSTM adalah tipe khusus dari jaringan saraf rekuren (RNN) yang dirancang untuk menangani masalah serial, seperti data time series, dengan mengatasi masalah pelatihan jaringan RNN biasa yang rentan terhadap vanishing gradient.

#### Mengapa menggunakan LSTM?
1. **Kemampuan Memahami Data Sequential**: LSTM memiliki kemampuan untuk memahami dan mengingat informasi yang berurutan dari data time series dalam jangka waktu yang lebih panjang.
2. **Mengatasi Masalah Vanishing Gradient**: LSTM memiliki mekanisme gerbang (gate) yang memungkinkannya untuk mengontrol aliran informasi, sehingga mengatasi masalah vanishing gradient yang sering terjadi pada jaringan rekuren tradisional.
3. **Penanganan Data Time Series**: LSTM secara alami cocok untuk menangani data time series karena strukturnya yang mempertahankan memori jangka panjang.

#### Sequential Model vs. LSTM Layer
- Model yang digunakan dalam kode adalah model Sequential, yang merupakan tumpukan linear dari lapisan-lapisan yang dapat disusun secara berurutan. LSTM digunakan sebagai lapisan dalam model Sequential tersebut.
- LSTM yang digunakan dalam model Sequential adalah jenis lapisan khusus yang dirancang untuk menangani data serial dan memiliki kemampuan untuk mempertahankan informasi dari masa lalu dalam jangka waktu yang lama.

#### Parameter yang Digunakan:
1. **Jumlah Unit LSTM**: Dalam kode, setiap lapisan LSTM memiliki 60 unit. Ini menentukan jumlah unit dalam lapisan LSTM, yang merupakan dimensi ruang output untuk lapisan tersebut.
2. **Jumlah Neuron pada Dense Layers**: Ada tiga lapisan Dense yang digunakan setelah LSTM. Masing-masing memiliki jumlah neuron berturut-turut 30, 10, dan 1.
3. **Optimizer**: Stochastic Gradient Descent (SGD) digunakan sebagai optimizer dengan learning rate sebesar 1.0000e-04 dan momentum 0.9.
4. **Loss Function**: Huber loss digunakan sebagai fungsi kerugian (loss function) dalam pelatihan model. Huber loss adalah kombinasi dari MSE (Mean Squared Error) dan MAE (Mean Absolute Error), yang memberikan bobot yang lebih rendah untuk outlier.
5. **Metrik**: MAE (Mean Absolute Error) dipilih sebagai metrik untuk mengukur kinerja model selama pelatihan.

#### Hyperparameter Tuning:
- `epochs`: Jumlah epoch yang digunakan untuk pelatihan model.
- `batch_size`: Jumlah sampel yang akan digunakan dalam satu iterasi pelatihan.
- `patience` (pada callback EarlyStopping): Jumlah epoch yang akan ditunggu sebelum pelatihan dihentikan jika tidak ada peningkatan dalam metrik validasi.
- Lainnya: Parameter lain seperti jumlah unit dalam lapisan LSTM, jumlah neuron dalam lapisan Dense, dll.

Secara keseluruhan, model LSTM dipilih karena kemampuannya untuk menangani data time series dan mengatasi masalah yang sering terjadi pada jaringan rekuren tradisional, sementara parameter dan hyperparameter dipilih berdasarkan eksperimen untuk mencapai kinerja yang baik pada dataset yang diberikan

### Evaluation

**Metrik Evaluasi MAE (Mean Absolute Error):** 
Metrik Evaluasi MAE digunakan untuk mengevaluasi seberapa dekat prediksi model dengan nilai sebenarnya dari harga tukar USD/IDR. MAE mengukur rata-rata dari selisih absolut antara nilai prediksi dan nilai sebenarnya. Dengan demikian, hasil MAE yang lebih rendah menunjukkan kinerja model yang lebih baik dalam memprediksi perubahan harga tukar.

Formula untuk MAE adalah:

MAE = (1/n) Σ(i=1 to n) |y_i – ŷ_i|

**Hasil Proyek Berdasarkan Metrik Evaluasi:**
Setelah melakukan evaluasi menggunakan metrik MAE, kami memperoleh hasil sebagai berikut:
- Mean Absolute Error: 0.0277
- Threshold MAE: 0.1

Dalam konteks hasil nilai MAE sebesar 0.0277, hal ini menunjukkan bahwa rata-rata kesalahan prediksi model adalah sekitar 0.0277. Artinya, rata-rata selisih antara harga tukar yang diprediksi oleh model dengan harga tukar yang sebenarnya adalah sekitar 0.0277. Ini adalah ukuran yang relatif rendah, menunjukkan bahwa model telah mampu memprediksi fluktuasi harga tukar USD/IDR dengan tingkat akurasi yang baik.

Threshold MAE yang dipakai (0.1) adalah batas yang telah ditetapkan untuk menentukan seberapa baik kinerja model. Jika MAE melebihi threshold ini, dapat dianggap bahwa model tidak cukup akurat. Dalam konteks ini, dengan threshold sebesar 0.1, nilai MAE sebesar 0.0277 jelas jauh di bawah batas tersebut, menunjukkan bahwa model telah memberikan prediksi yang memuaskan dan dapat diandalkan.

**Plot Loss dan Akurasi:**
- ![Plot Loss dan Akurasi](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/cdaa0699-2cf8-4228-9fa6-a8d3c637ee94)
  - Plot Loss dan akurasi juga menunjukan hasil yang baik atau bisa dibilang well fitting

**Plot Harga Aktual dan Harga Prediksi:**
- ![Plot Harga Aktual dan Harga Prediksi](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/05237876-d8f9-4b70-846a-89e3613c300b) 
  - Hasil prediksi juga menunjukan hasil yang baik dan memiliki selisih yang sangat sedikit dibandingkan dengan harga aktual

Secara praktis, hasil metrik evaluasi tersebut menunjukkan bahwa model yang dikembangkan telah memberikan prediksi harga tukar USD/IDR yang cukup akurat. Hal ini memiliki dampak positif bagi berbagai pemangku kepentingan seperti investor, eksportir, importir, pemerintah, dan masyarakat luas. Mereka dapat menggunakan prediksi ini untuk mengambil keputusan yang lebih baik terkait dengan investasi, perdagangan, dan kegiatan ekonomi lainnya.

Dalam konteks goals dan solusi proyek, hasil evaluasi ini menunjukkan bahwa model LSTM yang dikembangkan berhasil mencapai tujuan proyek. Model ini dapat memprediksi fluktuasi harga tukar USD/IDR dengan hasil evaluasi yang baik, sesuai dengan yang diharapkan. Oleh karena itu, proyek ini dapat dianggap berhasil karena mampu memberikan solusi yang bermanfaat sesuai dengan problem statement yang diajukan.

