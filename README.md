# Sistem Rekomendasi Anime menggunakan Content-Based Filtering

## Deskripsi Proyek

Proyek ini bertujuan untuk mengembangkan sebuah sistem rekomendasi anime menggunakan metode content-based filtering. Sistem ini akan merekomendasikan anime kepada pengguna berdasarkan kesamaan konten atau fitur antara anime yang disukai oleh pengguna dengan anime lainnya. Dengan menggunakan teknik ini, sistem dapat merekomendasikan anime yang memiliki karakteristik atau elemen serupa dengan anime favorit pengguna.

## Urgensi Permasalahan

Urgensinya proyek ini terletak pada pentingnya memberikan rekomendasi yang relevan dan sesuai dengan minat pengguna. Dalam dunia hiburan seperti anime, di mana terdapat ribuan judul yang berbeda dengan berbagai genre dan tema, memiliki sistem rekomendasi yang efektif dapat membantu pengguna menemukan konten yang sesuai dengan preferensi mereka tanpa harus menghabiskan waktu untuk mencari secara manual.

## Latar Belakang

Anime merupakan bentuk hiburan yang sangat populer di kalangan berbagai kelompok usia dan budaya. Dengan jumlah judul yang terus bertambah setiap tahunnya, pengguna sering kali mengalami kesulitan dalam menemukan anime yang sesuai dengan minat dan preferensi mereka. Oleh karena itu, pengembangan sistem rekomendasi anime dapat memberikan solusi untuk masalah tersebut dengan memberikan rekomendasi yang personal dan relevan kepada pengguna.

## Goals

1. Mengembangkan sistem rekomendasi anime yang menggunakan content-based filtering.
2. Menganalisis dan mengekstrak fitur atau karakteristik dari anime, seperti genre, tema, dan rating.
3. Membangun model yang dapat merekomendasikan anime berdasarkan kesamaan fitur dengan anime favorit pengguna.
4. Mengimplementasikan sistem rekomendasi dalam bentuk aplikasi atau platform yang user-friendly dan dapat diakses oleh pengguna.

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

