# Sistem Rekomendasi Anime Menggunakan Content-Based Filtering

## Ptoject Overview

![image](https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/1c3081c5-0b81-4203-b2f6-069c13810770)

Proyek ini bertujuan untuk mengembangkan sebuah sistem rekomendasi anime menggunakan metode content-based filtering. Sistem ini akan merekomendasikan anime kepada pengguna berdasarkan kesamaan konten atau fitur antara anime yang disukai oleh pengguna dengan anime lainnya. Dengan menggunakan teknik ini, sistem dapat merekomendasikan anime yang memiliki karakteristik atau elemen serupa dengan anime favorit pengguna.

### Urgensi Permasalahan

Urgensinya proyek ini terletak pada pentingnya memberikan rekomendasi yang relevan dan sesuai dengan minat pengguna. Dalam dunia hiburan seperti anime, di mana terdapat ribuan judul yang berbeda dengan berbagai genre dan tema, memiliki sistem rekomendasi yang efektif dapat membantu pengguna menemukan konten yang sesuai dengan preferensi mereka tanpa harus menghabiskan waktu untuk mencari secara manual.

### Latar Belakang

Anime merupakan bentuk hiburan yang sangat populer di kalangan berbagai kelompok usia dan budaya. Dengan jumlah judul yang terus bertambah setiap tahunnya, pengguna sering kali mengalami kesulitan dalam menemukan anime yang sesuai dengan minat dan preferensi mereka. Oleh karena itu, pengembangan sistem rekomendasi anime dapat memberikan solusi untuk masalah tersebut dengan memberikan rekomendasi yang personal dan relevan kepada pengguna.

### Business Understanding

#### Problem Statement

1. Bagaimana menganalisis data anime dengan lebih mendalam?
2. Bagaimana caranya untuk memberikan rekomendasi anime yang lebih personal dan relevan kepada pengguna, sehingga mereka dapat dengan mudah menemukan anime yang sesuai dengan minat dan preferensi mereka?
3. Apakah sistem rekomendasi anime ini dapat memberikan hasil dan presisi yang baik?

#### Goals

1. Menganalisis dan mengekstrak fitur atau karakteristik dari anime, seperti genre, tema, dan rating.
2. Membangun model yang dapat merekomendasikan anime berdasarkan kesamaan fitur dengan anime favorit pengguna.
3. Menguji model yang dibangun dengan menggunakan metrik precision.

### Solusi

Untuk mencapai tujuan proyek, langkah-langkah berikut akan dilakukan:

1. **Analisis dan Ekstraksi Fitur Anime**:
   - Melakukan analisis data anime untuk mengidentifikasi fitur-fitur penting seperti genre, tema, dan rating.
   - Fitur-fitur tersebut akan diekstrak dari data anime untuk digunakan dalam pembangunan model.

2. **Pembangunan Model Rekomendasi**:
   - Teknik content-based filtering akan digunakan untuk membangun model rekomendasi.
   - Model akan mempertimbangkan kesamaan fitur antara anime yang disukai pengguna dan anime lainnya untuk memberikan rekomendasi yang relevan.

3. **Evaluasi Model dengan Metrik Precision**:
   - Kinerja model yang dibangun akan diuji menggunakan metrik precision.
   - Metrik ini akan mengukur seberapa akurat model dalam memberikan rekomendasi anime yang sesuai dengan preferensi pengguna.


# Data Understanding
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

<div align="center">
Tabel 1. Overview dataset anime.csv
</div>

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

<div align="center">
Tabel 2. Overview dataset rating csv
</div>

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

<div align="center">
Tabel 3. Distribusi data anime.csv
</div>  

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

<div align="center">
Tabel 4. Distribusi data rating.csv
</div>  

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

<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/80bb2943-33dd-45d9-9cab-860825fb72c3" alt="Top 10 Anime Genre">
  <p>Gambar 1. Top 10 Genre Anime</p>
</div>


Grafik tersebut menampilkan 10 genre anime yang paling banyak ditemui.

**Top 10 Anime berdasarkan Rata-Rata Rating**

<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/1181e5f7-bc09-4a3e-92e1-0aa0aab4b2c4" alt="Top 10 Anime Berdasarkan Rata-Rata Rating">
  <p>Gambar 2. Top 10 Anime Berdasarkan rata-rata rating</p>
</div>

Menampilkan Top 10 Anime dengan rata-rata rating tertinggi, di mana "Taka no Tsume" memiliki rata-rata rating tertinggi.

**Distribusi Rating Anime**
<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/72dcbe14-e152-4644-b7c5-f8de7e82b080" alt="Distribusi Rating Anime">
  <p>Gambar 3. Distribusi Rating anime</p>
</div>

Grafik tersebut menunjukkan distribusi rating dari anime.

**Distribusi Jenis Anime**

<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/4e2dce44-3443-4523-907f-b89ffdca4c74" alt="Distribusi Rating Anime">
  <p>Gambar 4. Distribusi Jenis anime</p>
</div>


Grafik tersebut menampilkan distribusi jenis anime, di mana jenis TV paling banyak ditemui.

# Data Preparation

### Count anime rating contribution

<div align="center">
Tabel 5. kontribusi rating anime
</div>

|anime\_id|user\_id|rating|
|---|---|---|
|1|15509|15509|
|5|6927|6927|
|6|11077|11077|

### Menggabungkan table anime rating contribution dengan dataframe anime berdasarkan anime_id

<div align="center">
Tabel 6. tabel hasil merge antara rating.csv dan anime.csv
</div>  

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

Pada tahap ini, dilakukan proses pembersihan data (data cleaning) dengan menggunakan fungsi `dropna()` untuk menghapus baris yang mengandung nilai yang hilang (missing value) dari dataset. Tujuan dari langkah ini adalah untuk memastikan bahwa dataset yang digunakan dalam analisis selanjutnya bebas dari nilai yang hilang, sehingga tidak mempengaruhi hasil analisis.

<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/7cbf2998-25a0-4d43-ac84-9043171e4be4" alt="Missing Value Handling">
  <p>Gambar 5. Missing Value Handling</p>
</div>


Proses pembersihan ini diperlukan untuk memastikan keakuratan dan konsistensi data sebelum dilakukan analisis lebih lanjut. Dengan menghapus baris yang mengandung nilai yang hilang, dataset menjadi lebih bersih dan siap untuk digunakan dalam proses analisis dan pemodelan.

### Content Based Filtering Modelling & Result 

<div align="center">
  <img src="https://github.com/syihabudin081/ml_terapan_dicoding/assets/99803288/e302bc8f-419f-4dc9-8a56-b4049dfec1b9">
  <p>Gambar 6. Content Based Filtering</p>
</div>


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

<div align="center">
  <p>Tabel 7. Dataframe TF-IDF</p>
</div>

|anime\_name|adventure|ai|magic|shounen|cars|horror|drama|comedy|hentai|yaoi|fantasy|of|action|ecchi|supernatural|life|space|samurai|super|mystery|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Sheep in the Island|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|1\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Saikin, Imouto no Yousu ga Chotto Okashiinda ga\.|0\.0|0\.0|0\.0|0\.4139244457223737|0\.0|0\.0|0\.0|0\.28138674229986865|0\.0|0\.0|0\.0|0\.0|0\.0|0\.5582069951833066|0\.49479345484711246|0\.0|0\.0|0\.0|0\.0|0\.0|
|Uju Heukgisa|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.38161910123227727|0\.0|0\.0|0\.0|0\.6968149223554001|0\.0|0\.0|0\.0|
|Cookin&\#039; Idol Ai\! Mai\! Main\!|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.5289984351838201|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Toki-iro Kaima|0\.0|0\.0|0\.0|0\.5425262312642511|0\.0|0\.8400388612381027|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Beluga|0\.0|0\.0|0\.0|0\.0|0\.0|0\.6648388791469788|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Macross F Movie 1: Itsuwari no Utahime|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.24991864763907218|0\.0|0\.0|0\.0|0\.4563373334496427|0\.0|0\.0|0\.0|
|Hitsugi no Chaika OVA|0\.46373730053581397|0\.0|0\.0|0\.5095198294817932|0\.0|0\.0|0\.0|0\.3463726929798887|0\.0|0\.0|0\.47112015170502103|0\.0|0\.4282627927708617|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Ooi\! Hanimaru|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Ranma ½: Totteoki Talk Best of Memories|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.21536562651365765|0\.0|0\.0|0\.0|0\.3628453338600582|0\.0|0\.0|0\.0|0\.3628453338600582|0\.0|0\.0|0\.0|0\.0|

### Cosine Similarity

Pada tahap ini, dilakukan perhitungan derajat kesamaan (similarity degree) antar anime menggunakan teknik cosine similarity. Proses ini memungkinkan untuk merekomendasikan daftar anime yang mirip dengan anime yang telah disukai oleh pengguna. Berikut adalah langkah-langkahnya:

1. **Perhitungan Cosine Similarity**: Menggunakan fungsi `cosine_similarity` dari library sklearn untuk menghitung cosine similarity antara vektor representasi TF-IDF dari setiap pasang anime. Cosine similarity mengukur seberapa mirip dua vektor berdasarkan sudut kosinus di antara keduanya.

2. **Rekomendasi Anime yang Mirip**: Dengan menggunakan data similarity yang diperoleh, direkomendasikan daftar anime yang memiliki kesamaan tertinggi dengan anime yang telah disukai oleh pengguna. Semakin tinggi nilai cosine similarity antara dua anime, semakin mirip kedua anime tersebut.
   
<div align="center">
  <p>Tabel 8. Similiarity Matrix pada anime</p>
</div>

|anime\_name|Shuukan Shimakou: Sono Toki, Shimakou ga Ugoita\!|Issunboushi \(OVA\)|Ginga Tetsudou 999: Hoshizora wa Time Machine|Hajimari no Boukensha-tachi: Legend of Crystania|Kikoushi Enma|
|---|---|---|---|---|---|
|Uchuu no Kishi Tekkaman Blade II|0\.0|0\.0|0\.5140333729917009|0\.20352848053240138|0\.0|
|Inferno Cop: Fact Files|0\.3277258060281538|0\.0|0\.0|0\.1450885315667765|0\.0|
|Nazo no Kanojo X|0\.0|0\.0|0\.0|0\.0|0\.42663091401515024|
|Mobile Suit Gundam: The 08th MS Team - A Battle with the Third Dimension|0\.0|0\.0|0\.0|0\.14332081592418536|0\.0|
|Heroman Specials|0\.0|0\.0|0\.5794932587668898|0\.16096895670502798|0\.0|
|Momon&\#039;s Sand Witch Episode 0|0\.5289984351838202|0\.0|0\.0|0\.0|0\.0|
|Wamono|0\.0|0\.0|0\.0|0\.0|0\.0|
|Tobacco to Hai|0\.0|0\.0|0\.0|0\.38771931004185134|0\.0|
|Juugo Shounen Hyouryuuki|0\.0|0\.0|0\.30577955907704507|0\.19001019200531571|0\.0|
|Daikyouryuu Jidai|0\.0|0\.0|0\.8100043211350902|0\.0|0\.0|

Dengan menggunakan TF-IDF Vectorizer dan Cosine Similarity, sistem rekomendasi anime yang sederhana namun efektif dapat dibangun berdasarkan genre anime yang disukai oleh pengguna. Metode ini memungkinkan untuk merekomendasikan anime yang memiliki kesamaan fitur dengan anime favorit pengguna, sehingga meningkatkan pengalaman pengguna dalam menemukan konten yang sesuai dengan preferensi mereka.

### Result

#### Mendapatkan Rekomendasi

Setelah melakukan perhitungan similarity antar anime menggunakan cosine similarity, langkah selanjutnya adalah menghasilkan rekomendasi anime kepada pengguna. Rekomendasi ini didasarkan pada tingkat kesamaan antar anime yang telah dihitung sebelumnya. Dengan menggunakan data kesamaan ini, sistem dapat merekomendasikan daftar anime yang mirip dengan anime yang telah disukai oleh pengguna sebelumnya. Proses ini memungkinkan pengguna untuk menemukan anime baru yang mungkin sesuai dengan preferensi mereka berdasarkan pada anime yang telah mereka sukai sebelumnya.

Sebagai contoh, kita ingin mendapatkan rekomendasi terkait dengan anime yang mirip dengan Gintama:

<div align="center">
  <p>Tabel 9. Lihat Fitur anime Gintama</p>
</div>

| Index | ID   | Anime Name                              | Genre                                            |
|-------|------|-----------------------------------------|--------------------------------------------------|
| 9832  | 28977| Gintama°                                | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |

Maka sistem akan merekomendasikan 5 anime yang mirip dengan Gintama:

<div align="center">
  <p>Tabel 10. Hasil Sistem Rekomendasi Gintama</p>
</div>

| Index | Anime Name                                     | Genre                                            |
|-------|------------------------------------------------|--------------------------------------------------|
| 0     | Gintama Movie: Kanketsu-hen - Yorozuya yo Eien Nare | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 1     | Gintama Movie: Shinyaku Benizakura-hen        | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 2     | Gintama: Jump Festa 2014 Special              | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 3     | Gintama: Yorinuki Gintama-san on Theater 2D   | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| 4     | Gintama'                                       | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |

# Evaluasi

Untuk evaluasi, menggunakan metrik precision yang dirumuskan sebagai berikut:

### Precision = (Jumlah Rekomendasi Relevan) / (Jumlah Item yang Direkomendasikan) 

Keterangan:

- Jumlah rekomendasi yang relevan: Jumlah item yang direkomendasikan oleh sistem yang benar-benar disukai atau dibutuhkan oleh pengguna.
- Jumlah item yang direkomendasikan: Jumlah total item yang direkomendasikan oleh sistem kepada pengguna.

Berdasarkan hasil rekomendasi anime Gintama di atas, dapat dihitung nilai precision (P) sebagai berikut:

 **P = 5/5 = 1** 

Ini berarti bahwa dari 5 item yang direkomendasikan, semua di antaranya relevan, sehingga presisi adalah 100%.

Dengan demikian, tujuan dari pengembangan sistem rekomendasi anime menggunakan content-based filtering telah berhasil tercapai dengan baik.


## Referensi

1. MyAnimeList. [Online]. Available: https://myanimelist.net/
2. Vaughan, F. L. (2020, September 29). Content-Based Filtering for Recommendation Systems. Towards Data Science. https://towardsdatascience.com/content-based-recommender-systems-28a1dbd858f5
3. Nakano, J., & Takahashi, K. (2023, February 20). Building a Content-Based Movie Recommendation Engine. Real Python. https://realpython.com/build-recommendation-engine-collaborative-filtering/
4. Mehta, P. G., Agrawal, R., & Venkatasubramanian, S. (2018, June 12). Introduction to Recommender Systems. Analytics Vidhya. 5. https://www.analyticsvidhya.com/blog/2018/06/comprehensive-guide-recommendation-engine-python/
6. Bradley, T. (2020, October 28). An Introduction to Anime and Why It’s Worth Your Time. Collider. https://collider.com/what-is-anime-explained/
Ashfiya, L., & Yuniarti, E. (2020). Based Filtering Methods in Anime Recommendation Systems. Jurnal Komtika, 5(2), 131-140. [invalid URL removed]

