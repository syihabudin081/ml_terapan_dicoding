# Sistem Rekomendasi Anime Menggunakan Content-Based Filtering

## Deskripsi Proyek

![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/1c3081c5-0b81-4203-b2f6-069c13810770)

Proyek ini bertujuan untuk mengembangkan sebuah sistem rekomendasi anime menggunakan metode content-based filtering. Sistem ini akan merekomendasikan anime kepada pengguna berdasarkan kesamaan konten atau fitur antara anime yang disukai oleh pengguna dengan anime lainnya. Dengan menggunakan teknik ini, sistem dapat merekomendasikan anime yang memiliki karakteristik atau elemen serupa dengan anime favorit pengguna.

## Urgensi Permasalahan

Urgensinya proyek ini terletak pada pentingnya memberikan rekomendasi yang relevan dan sesuai dengan minat pengguna. Dalam dunia hiburan seperti anime, di mana terdapat ribuan judul yang berbeda dengan berbagai genre dan tema, memiliki sistem rekomendasi yang efektif dapat membantu pengguna menemukan konten yang sesuai dengan preferensi mereka tanpa harus menghabiskan waktu untuk mencari secara manual.

## Latar Belakang

Anime merupakan bentuk hiburan yang sangat populer di kalangan berbagai kelompok usia dan budaya. Dengan jumlah judul yang terus bertambah setiap tahunnya, pengguna sering kali mengalami kesulitan dalam menemukan anime yang sesuai dengan minat dan preferensi mereka. Oleh karena itu, pengembangan sistem rekomendasi anime dapat memberikan solusi untuk masalah tersebut dengan memberikan rekomendasi yang personal dan relevan kepada pengguna.

## Problem Statement

Dengan pertumbuhan yang pesat dalam jumlah judul anime yang tersedia, pengguna sering kali menghadapi kesulitan dalam menemukan anime yang sesuai dengan preferensi dan minat mereka. Masalah utama yang dihadapi adalah kurangnya rekomendasi yang personal dan relevan, yang dapat menyebabkan pengguna menghabiskan waktu berharga untuk mencari anime baru yang sesuai dengan selera mereka.

Selain itu, kebanyakan sistem rekomendasi yang tersedia cenderung mengandalkan data demografis pengguna atau perilaku interaksi sebelumnya, tanpa memperhitungkan karakteristik atau fitur konten dari anime yang disukai. Hal ini dapat menyebabkan rekomendasi yang kurang akurat dan kurang memuaskan bagi pengguna.

Oleh karena itu, diperlukan sebuah sistem rekomendasi anime yang dapat memberikan rekomendasi yang personal dan relevan kepada pengguna berdasarkan karakteristik atau fitur konten dari anime yang disukai oleh pengguna. Dengan demikian, pengguna akan lebih mudah menemukan anime baru yang sesuai dengan minat dan preferensi mereka, meningkatkan pengalaman hiburan mereka secara keseluruhan.

## Goals

1. Mengembangkan sistem rekomendasi anime yang menggunakan content-based filtering.
2. Menganalisis dan mengekstrak fitur atau karakteristik dari anime, seperti genre, tema, dan rating.
3. Membangun model yang dapat merekomendasikan anime berdasarkan kesamaan fitur dengan anime favorit pengguna.

## Solusi

Untuk mencapai tujuan proyek, langkah-langkah berikut akan dilakukan:

1. Pengumpulan Data: Mengumpulkan data tentang anime, termasuk informasi tentang genre, tema, rating, dan fitur lainnya.
2. Eksplorasi Data (EDA): Menganalisis dan memahami data anime untuk mengidentifikasi pola, tren, dan karakteristik yang relevan.
3. Pemrosesan Data: Membersihkan, mengubah, dan menormalkan data untuk persiapan pemodelan.
4. Ekstraksi Fitur: Mengekstrak fitur-fitur penting dari data anime, seperti genre, tema, dan rating.
5. Pembangunan Model: Menggunakan teknik content-based filtering untuk membangun model yang dapat merekomendasikan anime berdasarkan kesamaan fitur.
6. Evaluasi Model: Menguji kinerja model menggunakan metrik evaluasi yang sesuai, seperti precision, recall, dan F1-score.
7. Implementasi: Mengimplementasikan sistem rekomendasi dalam bentuk aplikasi atau platform yang dapat diakses oleh pengguna.

## Referensi

1. [MyAnimeList](https://myanimelist.net/)
2. [Content-Based Filtering for Recommendation Systems - Towards Data Science](https://towardsdatascience.com/content-based-recommender-systems-28a1dbd858f5)
3. [Building a Content-Based Movie Recommendation Engine - Real Python](https://realpython.com/build-recommendation-engine-collaborative-filtering/)
4. [Introduction to Recommender Systems - Analytics Vidhya](https://www.analyticsvidhya.com/blog/2018/06/comprehensive-guide-recommendation-engine-python/)
5. [An Introduction to Anime and Why It's Worth Your Time - Collider](https://collider.com/what-is-anime-explained/)
6. [Based Filtering Methods in Anime Recommendation Systems](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwihxPeZv_6EAxXy9zgGHZcZCMgQFnoECDUQAQ&url=https%3A%2F%2Fjournal.unimma.ac.id%2Findex.php%2Fkomtika%2Farticle%2Fdownload%2F9219%2F4657%2F&usg=AOvVaw2RL_6RvwrksuYvLzPw_Lb5&opi=89978449)

## Data Understanding
Data yang digunakan adalah dataset  dengan judul [Anime Recommendations Database](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fwww.kaggle.com%2Fdatasets%2FCooperUnion%2Fanime-recommendations-database) yang diambil dari kaggle 

### Dataset

Dataset ini berisi informasi tentang preferensi pengguna dari 73.516 pengguna pada 12.294 anime. Setiap pengguna dapat menambahkan anime ke daftar yang telah mereka tonton dan memberikan peringkat, dan dataset ini adalah kumpulan dari peringkat tersebut.

###  Anime

- Format: CSV
- Jumlah Sample: 12,294
- Jumlah Fitur: 7
- Tipe Data Fitur: 
    - 1 fitur float64
    - 2 fitur int64
    - 4 fitur object
- Terdapat nilai yang hilang (missing value) pada dataset.

### Anime Rating

- Format: CSV
- Jumlah Sample: 7,813,737
- Jumlah Fitur: 3
- Tipe Data Fitur: 
    - 1 fitur int64
- Tidak terdapat nilai yang hilang (missing value) pada dataset.

**Anime.csv**

|index|anime\_id|name|genre|type|episodes|rating|members|
|---|---|---|---|---|---|---|---|
|0|32281|Kimi no Na wa\.|Drama, Romance, School, Supernatural|Movie|1|9\.37|200630|
|1|5114|Fullmetal Alchemist: Brotherhood|Action, Adventure, Drama, Fantasy, Magic, Military, Shounen|TV|64|9\.26|793665|
|2|28977|Gintama°|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|TV|51|9\.25|114262|
|3|9253|Steins;Gate|Sci-Fi, Thriller|TV|24|9\.17|673572|
|4|9969|Gintama&\#039;|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|TV|51|9\.16|151266|

- `anime_id`: id unik dari myanimelist.net yang mengidentifikasi sebuah anime.
- `name`: nama lengkap dari anime.
- `genre`: daftar genre yang dipisahkan oleh koma untuk anime ini.
- `type`: film, TV, OVA, dll.
- `episodes`: jumlah episode dalam acara ini. (1 jika film).
- `rating`: peringkat rata-rata dari 10 untuk anime ini.
- `members`: jumlah anggota komunitas yang ada dalam "kelompok" anime ini.

**Rating.csv**
|index|user\_id|anime\_id|rating|
|---|---|---|---|
|0|1|20|-1|
|1|1|24|-1|
|2|1|79|-1|
|3|1|226|-1|
|4|1|241|-1|

- `user_id`: id pengguna yang dihasilkan secara acak dan tidak dapat diidentifikasi.
- `anime_id`: anime yang dinilai oleh pengguna ini.
- `rating`: peringkat dari 10 yang diberikan pengguna ini (-1 jika pengguna menontonnya tetapi tidak memberikan peringkat).
  
## Exploratory Data Analysis (EDA)

Tahap exploratory data analysis dilakukan untuk memahami data yang digunakan dalam proyek. Beberapa tahapan yang dilakukan antara lain:

- **Jumlah Data Judul Anime**: Terdapat 12.294 judul anime yang berbeda dalam dataset.
- **Jumlah Data Genre Anime**: Terdapat 3.265 genre anime yang berbeda dalam dataset.
- **Jumlah Data Pengguna**: Terdapat 73.515 pengguna yang berbeda dalam dataset.

### Deskripsi Variabel

**Anime.csv**

- `anime_id`: id unik dari myanimelist.net yang mengidentifikasi sebuah anime.
- `name`: nama lengkap dari anime.
- `genre`: daftar genre yang dipisahkan oleh koma untuk anime ini.
- `type`: film, TV, OVA, dll.
- `episodes`: jumlah episode dalam acara ini. (1 jika film).
- `rating`: peringkat rata-rata dari 10 untuk anime ini.
- `members`: jumlah anggota komunitas yang ada dalam "kelompok" anime ini.

**Rating.csv**

- `user_id`: id pengguna yang dihasilkan secara acak dan tidak dapat diidentifikasi.
- `anime_id`: anime yang dinilai oleh pengguna ini.
- `rating`: peringkat dari 10 yang diberikan pengguna ini (-1 jika pengguna menontonnya tetapi tidak memberikan peringkat).

### Distribusi Data 

**Anime.csv**

|index|anime\_id|rating|members|
|---|---|---|---|
|count|12294\.0|12064\.0|12294\.0|
|mean|14058\.221652838783|6\.473901690981432|18071\.33886448674|
|std|11455\.294700988183|1\.0267463068980571|54820\.67692490696|
|min|1\.0|1\.67|5\.0|
|25%|3484\.25|5\.88|225\.0|
|50%|10260\.5|6\.57|1550\.0|
|75%|24794\.5|7\.18|9437\.0|
|max|34527\.0|10\.0|1013917\.0|

**Keterangan:**

- **anime_id**: Terdapat 12.294 entri unik dalam kolom `anime_id`.
- **rating**: Rata-rata rating anime adalah sekitar 6.47, dengan standar deviasi sekitar 1.03. Rating berkisar dari 1.67 hingga 10.00.
- **members**: Rata-rata jumlah anggota komunitas dalam "kelompok" anime adalah sekitar 18.071, dengan standar deviasi sekitar 54.820. Jumlah anggota berkisar dari 5 hingga 1.013.917.
  
**Rating.csv**

|index|user\_id|anime\_id|rating|
|---|---|---|---|
|count|7813737\.0|7813737\.0|7813737\.0|
|mean|36727\.956744640884|8909\.072104295294|6\.144029546937656|
|std|20997\.946118974734|8883\.949635880968|3\.7278004201098787|
|min|1\.0|1\.0|-1\.0|
|25%|18974\.0|1240\.0|6\.0|
|50%|36791\.0|6213\.0|7\.0|
|75%|54757\.0|14093\.0|9\.0|
|max|73516\.0|34519\.0|10\.0|

**Keterangan:**

- **user\_id**: Terdapat sekitar 7.813.737 entri pada kolom `user\_id`.
- **anime\_id**: Terdapat sekitar 7.813.737 entri pada kolom `anime\_id`.
- **rating**: Rata-rata rating yang diberikan oleh pengguna adalah sekitar 6.14, dengan standar deviasi sekitar 3.73. Rating berkisar dari -1.0 hingga 10.0.

**Top 10 Anime Genre**

![Top 10 Anime Genre](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/80bb2943-33dd-45d9-9cab-860825fb72c3)

Grafik tersebut menampilkan 10 genre anime yang paling banyak ditemui.

**Top 10 Anime berdasarkan Rata-Rata Rating**

![Top 10 Anime berdasarkan Rata-Rata Rating](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/1181e5f7-bc09-4a3e-92e1-0aa0aab4b2c4)

Menampilkan Top 10 Anime dengan rata-rata rating tertinggi, di mana "Taka no Tsume" memiliki rata-rata rating tertinggi.

**Distribusi Rating Anime**

![Distribusi Rating Anime](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/72dcbe14-e152-4644-b7c5-f8de7e82b080)

Grafik tersebut menunjukkan distribusi rating dari anime.

**Distribusi Jenis Anime**

![Distribusi Jenis Anime](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/4e2dce44-3443-4523-907f-b89ffdca4c74)

Grafik tersebut menampilkan distribusi jenis anime, di mana jenis TV paling banyak ditemui.

### Data Preprocessing

# Count anime rating contribution

|anime\_id|user\_id|rating|
|---|---|---|
|1|15509|15509|
|5|6927|6927|
|6|11077|11077|

# Menggabungkan table anime rating contribution dengan dataframe anime berdasarkan anime_id

|index|anime\_id|user\_id|rating|name|genre|
|---|---|---|---|---|---|
|0|1|15509|15509|Cowboy Bebop|Action, Adventure, Comedy, Drama, Sci-Fi, Space|
|1|5|6927|6927|Cowboy Bebop: Tengoku no Tobira|Action, Drama, Mystery, Sci-Fi, Space|
|2|6|11077|11077|Trigun|Action, Comedy, Sci-Fi|
|3|7|2629|2629|Witch Hunter Robin|Action, Drama, Magic, Mystery, Police, Supernatural|
|4|8|413|413|Beet the Vandel Buster|Adventure, Fantasy, Shounen, Supernatural|
|5|15|2424|2424|Eyeshield 21|Action, Comedy, Shounen, Sports|
|6|16|3890|3890|Hachimitsu to Clover|Comedy, Drama, Josei, Romance|
|7|17|650|650|Hungry Heart: Wild Striker|Comedy, Shounen, Slice of Life, Sports|
|8|18|1911|1911|Initial D Fourth Stage|Action, Cars, Drama, Seinen, Sports|
|9|19|4594|4594|Monster|Drama, Horror, Mystery, Police, Psychological, Seinen, Thriller|

### Data Preparation

Pada tahap ini, dilakukan proses pembersihan data (data cleaning) dengan menggunakan fungsi `dropna()` untuk menghapus baris yang mengandung nilai yang hilang (missing value) dari dataset. Tujuan dari langkah ini adalah untuk memastikan bahwa dataset yang digunakan dalam analisis selanjutnya bebas dari nilai yang hilang, sehingga tidak mempengaruhi hasil analisis.

![Missing Value Handling](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/7cbf2998-25a0-4d43-ac84-9043171e4be4)

Proses pembersihan ini diperlukan untuk memastikan keakuratan dan konsistensi data sebelum dilakukan analisis lebih lanjut. Dengan menghapus baris yang mengandung nilai yang hilang, dataset menjadi lebih bersih dan siap untuk digunakan dalam proses analisis dan pemodelan.

### Content Based Filtering Modelling & Result 

![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/b6abcff9-a457-47ca-8cd4-15bbf851dd2d)

Content-based filtering adalah salah satu metode dalam sistem rekomendasi yang menghasilkan rekomendasi berdasarkan kesamaan fitur atau konten antara item yang telah disukai oleh pengguna dengan item lainnya. Pendekatan ini menggunakan informasi terperinci tentang item itu sendiri untuk membuat rekomendasi yang sesuai dengan preferensi pengguna.

### Pemilihan Content-Based Filtering untuk Sistem Rekomendasi Anime

Pemilihan pendekatan content-based filtering untuk sistem rekomendasi anime didasarkan pada beberapa pertimbangan yang meliputi:

#### Alasan Pemilihan Content-Based Filtering:

1. **Ketersediaan Data Rating yang Terbatas**: Dataset anime terkadang memiliki keterbatasan dalam hal data rating dari pengguna. Dalam kasus seperti ini, menggunakan metode content-based filtering lebih tepat karena tidak memerlukan data peringkat dari pengguna lain.

2. **Karakteristik Anime yang Jelas**: Anime memiliki beragam fitur dan karakteristik yang dapat dijadikan dasar untuk membuat rekomendasi, seperti genre, tema, studio pembuat, dan sebagainya. Dengan menggunakan content-based filtering, sistem dapat mengeksplorasi karakteristik ini untuk membuat rekomendasi yang lebih relevan.

3. **Personalisasi yang Tinggi**: Penggemar anime sering memiliki preferensi yang sangat spesifik, seperti genre atau tema favorit. Content-based filtering memungkinkan sistem untuk membuat rekomendasi yang lebih sesuai dengan preferensi unik dari setiap pengguna berdasarkan pada karakteristik anime yang mereka sukai.

#### Kelebihan Content-Based Filtering:

- **Personalisasi yang Tinggi**: Memungkinkan personalisasi yang tinggi dalam rekomendasi karena berfokus pada preferensi pengguna berdasarkan fitur-fitur yang mereka sukai dari anime sebelumnya.

- **Tidak Bergantung pada Data Eksternal**: Tidak memerlukan data eksternal seperti peringkat atau ulasan pengguna lainnya, membuatnya lebih mandiri dan dapat diterapkan dalam skenario di mana data eksternal tidak tersedia.

- **Rekomendasi yang Jelas dan Interpretabel**: Menghasilkan rekomendasi yang lebih jelas dan mudah diinterpretasikan oleh pengguna karena berdasarkan pada fitur-fitur yang dapat dijelaskan seperti genre, tema, dan karakteristik lainnya.

#### Kekurangan Content-Based Filtering:

- **Keterbatasan Dalam Variasi Rekomendasi**: Cenderung membatasi variasi rekomendasi karena hanya merekomendasikan anime dengan fitur serupa dengan yang telah disukai oleh pengguna sebelumnya.

- **Keterbatasan dalam Menemukan Item Baru**: Kurang efektif dalam menemukan item baru atau yang tidak sering dilihat oleh pengguna karena fokus pada fitur-fitur yang sudah dikenal oleh sistem.

- **Over-Spesialisasi**: Kadang-kadang menghasilkan rekomendasi yang terlalu spesifik atau tidak mencukupi karena terlalu berfokus pada fitur-fitur tertentu dari anime yang telah disukai pengguna.

Dengan mempertimbangkan kelebihan personalisasi, ketersediaan data, dan karakteristik anime, content-based filtering menjadi pilihan yang tepat untuk sistem rekomendasi anime dalam kasus-kasus di mana data rating pengguna terbatas atau tidak tersedia dalam jumlah yang cukup besar.

### TF-IDF Vectorizer

Pada tahap ini, TF-IDF (Term Frequency-Inverse Document Frequency) Vectorizer digunakan untuk membangun sistem rekomendasi sederhana berdasarkan genre anime. Teknik ini digunakan untuk menemukan representasi fitur penting dari setiap kategori anime. Berikut adalah langkah-langkah yang dilakukan:

1. **Melakukan Fit dan Transformasi**: Dilakukan fitting TF-IDF Vectorizer pada data genre anime untuk menghasilkan representasi vektor TF-IDF dari setiap genre. Proses ini mengubah teks genre menjadi vektor numerik berdasarkan frekuensi kata dalam setiap genre dan frekuensi invers dokumen di seluruh dataset.

2. **Mengubah Vektor ke Bentuk Matriks**: Hasil dari fitting dan transformasi adalah vektor TF-IDF untuk setiap genre anime. Kemudian, vektor tersebut diubah ke dalam bentuk matriks menggunakan fungsi `todense()` agar dapat dianalisis lebih lanjut.

3. **Membuat DataFrame**: Dibuatlah DataFrame untuk melihat matriks TF-IDF. Kolom DataFrame diisi dengan genre anime, sedangkan barisnya diisi dengan nama anime. Ini membantu untuk memvisualisasikan representasi TF-IDF untuk setiap anime.

![TF-IDF Matrix](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/24a99da8-93c1-47e0-ac79-16e8b8544e74)

### Cosine Similarity

Pada tahap ini, dilakukan perhitungan derajat kesamaan (similarity degree) antar anime menggunakan teknik cosine similarity. Proses ini memungkinkan untuk merekomendasikan daftar anime yang mirip dengan anime yang telah disukai oleh pengguna. Berikut adalah langkah-langkahnya:

1. **Perhitungan Cosine Similarity**: Menggunakan fungsi `cosine_similarity` dari library sklearn untuk menghitung cosine similarity antara vektor representasi TF-IDF dari setiap pasang anime. Cosine similarity mengukur seberapa mirip dua vektor berdasarkan sudut kosinus di antara keduanya.

2. **Rekomendasi Anime yang Mirip**: Dengan menggunakan data similarity yang diperoleh, direkomendasikan daftar anime yang memiliki kesamaan tertinggi dengan anime yang telah disukai oleh pengguna. Semakin tinggi nilai cosine similarity antara dua anime, semakin mirip kedua anime tersebut.

![Cosine Similarity](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/50cfd6b5-56b3-4b8d-a13d-c912d9371b16)

Dengan menggunakan TF-IDF Vectorizer dan Cosine Similarity, sistem rekomendasi anime yang sederhana namun efektif dapat dibangun berdasarkan genre anime yang disukai oleh pengguna. Metode ini memungkinkan untuk merekomendasikan anime yang memiliki kesamaan fitur dengan anime favorit pengguna, sehingga meningkatkan pengalaman pengguna dalam menemukan konten yang sesuai dengan preferensi mereka.

### Result

#### Mendapatkan Rekomendasi

Setelah melakukan perhitungan similarity antar anime menggunakan cosine similarity, langkah selanjutnya adalah menghasilkan rekomendasi anime kepada pengguna. Rekomendasi ini didasarkan pada tingkat kesamaan antar anime yang telah dihitung sebelumnya. Dengan menggunakan data kesamaan ini, sistem dapat merekomendasikan daftar anime yang mirip dengan anime yang telah disukai oleh pengguna sebelumnya. Proses ini memungkinkan pengguna untuk menemukan anime baru yang mungkin sesuai dengan preferensi mereka berdasarkan pada anime yang telah mereka sukai sebelumnya.

Sebagai contoh, kita ingin mendapatkan rekomendasi terkait dengan anime yang mirip dengan Gintama:

| Index | ID   | Anime Name                              | Genre                                            |
|-------|------|-----------------------------------------|--------------------------------------------------|
| 9832  | 28977| Gintama°                                | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |

Maka sistem akan merekomendasikan 5 anime yang mirip dengan Gintama:

| Index | Anime Name                                     | Genre                                            |
|-------|------------------------------------------------|--------------------------------------------------|
| 0     | Gintama Movie: Kanketsu-hen - Yorozuya yo Eien Nare | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 1     | Gintama Movie: Shinyaku Benizakura-hen        | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 2     | Gintama: Jump Festa 2014 Special              | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 3     | Gintama: Yorinuki Gintama-san on Theater 2D   | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 4     | Gintama'                                       | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |

### Evaluasi

Untuk evaluasi, menggunakan metrik precision yang dirumuskan sebagai berikut:

![Presisi (P) = Jumlah rekomendasi yang relevan / Jumlah item yang direkomendasikan](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/664195d3-3a82-42a7-bc8a-ef2f36ac1f03)

Keterangan:

- Jumlah rekomendasi yang relevan: Jumlah item yang direkomendasikan oleh sistem yang benar-benar disukai atau dibutuhkan oleh pengguna.
- Jumlah item yang direkomendasikan: Jumlah total item yang direkomendasikan oleh sistem kepada pengguna.

Berdasarkan hasil rekomendasi anime Gintama di atas, dapat dihitung nilai precision (P) sebagai berikut:

 **P = 5/5 = 1** 

Ini berarti bahwa dari 5 item yang direkomendasikan, semua di antaranya relevan, sehingga presisi adalah 100%.

Dengan demikian, tujuan dari pengembangan sistem rekomendasi anime menggunakan content-based filtering telah berhasil tercapai dengan baik.
