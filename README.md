# Sistem Rekomendasi Film - Aldy Muardi
## Domain Proyek
### Latar Belakang

Dalam era digital yang semakin maju, _platform_ hiburan seperti layanan _streaming_ film dan serial TV telah menjadi sangat populer. Pengguna sekarang memiliki akses ke ribuan film dari berbagai genre, tahun rilis, dan negara. Namun, dengan keberagaman konten yang luas, muncul masalah kelebihan pilihan yang dapat membuat pengguna bingung atau bahkan mengabaikan beberapa film yang mungkin sesuai dengan preferensi mereka. Dalam menghadapi tantangan ini, pengembang _platform_ hiburan telah mengadopsi sistem rekomendasi film yang canggih. 

Sistem rekomendasi film adalah teknologi cerdas yang digunakan oleh platform hiburan untuk memberikan rekomendasi film yang relevan dan menarik kepada pengguna. Tujuannya adalah untuk membantu pengguna menemukan film-film yang sesuai dengan preferensi dan minat mereka, mengatasi masalah kelebihan pilihan, dan meningkatkan pengalaman pengguna secara keseluruhan. Sebuah sistem rekomendasi film biasanya didasarkan pada teknik-teknik pengolahan data dan kecerdasan buatan yang kompleks. Data merupakan komponen kunci dalam sistem ini, dan platform hiburan mengumpulkan beragam informasi, termasuk riwayat penonton, peringkat film, preferensi, ulasan, dan interaksi pengguna sebelumnya dengan konten. Informasi ini dianalisis secara mendalam untuk memahami pola perilaku pengguna dan memprediksi film-film yang mungkin diminati.

![WhatsApp Image 2023-07-30 at 12 45 01](https://github.com/aldymuardi/Sistem-Rekomendasi-Film/assets/79571450/8f694a33-ccf7-45f3-a689-b6bb31d5c1f4)

Gambar 1. Ilustrasi Sistem Rekomendasi Film


Ada beberapa pendekatan yang dapat digunakan dalam mengembangkan sistem rekomendasi film. Salah satunya adalah pendekatan berbasis konten, di mana film-film dianalisis berdasarkan atribut-atribut mereka, seperti genre, aktor, sutradara, plot, dan bahasa. Jika seorang pengguna menyukai film-film dengan genre petualangan dan aktor tertentu, sistem akan merekomendasikan film-film dengan ciri-ciri serupa. Selain itu, ada juga pendekatan berbasis kolaboratif, yang memanfaatkan pola kesamaan antara pengguna. Dalam pendekatan ini, sistem mencari pengguna dengan preferensi serupa dan menggunakan data mereka untuk merekomendasikan film kepada pengguna lain dengan minat yang mirip. Misalnya, jika dua pengguna dengan minat film yang hampir sama memberikan peringkat yang tinggi pada film tertentu, sistem dapat merekomendasikan film tersebut kepada pengguna lain yang memiliki minat yang serupa. Sistem rekomendasi film juga dapat memanfaatkan teknik pembelajaran mesin dan algoritma terbaru. Algoritma ini terus ditingkatkan melalui pembelajaran dari data baru, sehingga sistem dapat menyediakan rekomendasi yang semakin akurat seiring berjalannya waktu.

Kegunaan sistem rekomendasi film tidak hanya menguntungkan bagi pengguna, tetapi juga bagi _platform_ hiburan itu sendiri. Dengan memberikan rekomendasi yang relevan, _platform_ dapat meningkatkan retensi pengguna, meningkatkan waktu tayang, dan mendorong interaksi lebih lanjut dengan konten mereka. Selain itu, data yang dikumpulkan dari interaksi pengguna dengan sistem rekomendasi dapat membantu _platform_ dalam memahami tren dan preferensi pengguna yang sedang berlangsung, sehingga mereka dapat menghadirkan konten baru yang sesuai dengan permintaan pasar.

## _Business Understanding_
Dalam era modern, di mana _platform_ hiburan berbasis streaming telah mengambil alih preferensi penonton, sistem rekomendasi film menjadi kunci untuk mengatasi tantangan kelebihan pilihan dan meningkatkan pengalaman pengguna.

Dengan beragamnya film yang tersedia, pengguna seringkali merasa kewalahan dan bingung dalam memilih konten yang sesuai dengan selera mereka. Sistem rekomendasi film hadir untuk menyelesaikan masalah ini dengan memberikan rekomendasi yang dipersonalisasi berdasarkan pola perilaku dan preferensi pengguna. Pengguna akan merasa diarahkan dengan tepat ke film-film yang paling mungkin mereka nikmati, sehingga meningkatkan kepuasan dan loyalitas pelanggan terhadap _platform_ hiburan tersebut.

Selain meningkatkan pengalaman pengguna, implementasi sistem rekomendasi film memberikan manfaat bisnis yang signifikan. Dengan menarik pengguna untuk terus menggunakan _platform_, retensi pelanggan meningkat, yang pada gilirannya berdampak positif pada pendapatan dan laba. Informasi yang dikumpulkan dari interaksi pengguna dengan sistem rekomendasi juga memberikan wawasan berharga tentang preferensi dan tren pasar yang dapat digunakan untuk mengoptimalkan strategi konten dan menghadirkan film-film yang diantisipasi oleh pengguna.

### _Problem Statment_
1. Bagaimana meningkatkan akurasi dan efektivitas sistem rekomendasi film untuk memberikan rekomendasi yang lebih personal dan relevan bagi setiap pengguna dengan _content-based filtering_?
2. Bagaimana meningkatkan pengalaman pengguna di platform hiburan dengan menyediakan rekomendasi film yang relevan dan sesuai dengan preferensi masing-masing pengguna dengan _collaborative filtering_?

### _Goals_
1. Menghasilkan rekomendasi film yang dipersonalisasi dan relevan untuk pengguna dengan teknik _content-based filtering_.
2. Menghasilkan rekomendasi film yang sesuai dengan preferensi pengguna dan belum pernah ditonton sebelumnya dengan _collaborative filtering_.

### _Solution Statement_
Untuk mencapai goals yang telah ditetapkan, langkah-langkah yang dilakukan oleh penulis adalah sebagai berikut:

1. Data Understanding

Tahap ini melibatkan pemahaman mendalam tentang data yang ada. Data yang relevan untuk sistem rekomendasi film termasuk informasi tentang film-film yang tersedia, preferensi dan riwayat penonton, peringkat film, ulasan, dan interaksi pengguna sebelumnya dengan konten. Penulis menganalisis dan memahami struktur data ini untuk mempersiapkan langkah-langkah selanjutnya.

2. _Univariate Exploratory Data Analysis_

Tahap ini melibatkan analisis data secara individual untuk memahami distribusi, statistik, dan karakteristik dari setiap atribut data. Dengan melakukan analisis ini, penulis dapat mengidentifikasi potensi _outliers_, _missing_ _values_, atau kesalahan data lainnya yang perlu ditangani selama tahap _preprocessing_.

3. _Data_ _Preprocessing_

Langkah ini melibatkan pembersihan dan transformasi data agar dapat diolah dengan tepat oleh sistem rekomendasi. Hal ini mencakup penanganan _missing values_, normalisasi data, penghapusan duplikat, dan penyusunan ulang data agar sesuai dengan kebutuhan model.

4. _Data_ _Preparation_

Setelah data diproses, tahap ini melibatkan persiapan data yang akan digunakan untuk mengembangkan model rekomendasi. Data yang relevan dipisahkan menjadi data latih dan data uji untuk menguji dan mengevaluasi performa model.

5. _Model_ _Development_ dengan _Content-Based Filtering_

Dalam langkah ini, penulis mengembangkan model content-based filtering. Model ini menganalisis atribut-atribut film seperti genre, aktor, sutradara, dan plot untuk memberikan rekomendasi film yang mirip dengan film-film yang telah disukai oleh pengguna sebelumnya.

6. _Model_ _Development_ dengan _Collaborative Filtering_

Selain _content-based filtering_, penulis juga mengembangkan model _collaborative filtering_. Model ini menganalisis pola kesamaan antara pengguna untuk merekomendasikan film-film yang disukai oleh pengguna dengan preferensi serupa.

7. Evaluasi dan Peningkatan Model

Setelah mengembangkan kedua model, penulis melakukan evaluasi untuk mengukur kinerja mereka. Model tersebut diperbaiki dan dioptimalkan dengan mengadaptasi feedback dan rekomendasi dari pengguna untuk meningkatkan akurasi dan relevansi rekomendasi.

## _Data Understanding_
Dataset yang digunakan dalam proyek ini merupakan data rekomendasi film. Dataset ini dapat diunduh di [Film Recomendation](https://www.kaggle.com/datasets/uttam94/recommendation). Pada dataset tersebut terdapat 2 file dengan format .csv yang terdiri dari movies.csv dan ratings.csv.

### Variabel-variabel Dataset
1. movies.csv

```
RangeIndex: 9742 entries, 0 to 9741
Data columns (total 3 columns):
 #   Column   Non-Null Count  Dtype 
---  ------   --------------  ----- 
 0   movieId  9742 non-null   int64 
 1   title    9742 non-null   object
 2   genres   9742 non-null   object
dtypes: int64(1), object(2)
```
* moviesId = ID film
* title = Judul film
* genres = genre atau kategori film

2. ratings.csv
```
RangeIndex: 100836 entries, 0 to 100835
Data columns (total 4 columns):
 #   Column     Non-Null Count   Dtype  
---  ------     --------------   -----  
 0   userId     100836 non-null  int64  
 1   movieId    100836 non-null  int64  
 2   rating     100836 non-null  float64
 3   timestamp  100836 non-null  int64  
dtypes: float64(1), int64(3)
```
* userId = ID user
* moviesId = ID film yang telah ditonton
* rating = Rating film
* timestamp = Waktu ketika _user_ melakukan penilaian

### Memahami Isi Dataset
1. Mengetahui jumlah dan tipe dari dataset

Untuk mengentahui informasi dari suatu _data frame_ dapat menggunakan fungsi pandas, yakni `df.info()`

2. Mengetahui nilai unik dataset

Berikut nilai unik yang didapatkan

```
Banyak movie dalam ratings : 9724
Banyak user dalam ratings : 610
```
3. mengetahui jumlah rating

Berikut total rating pada setiap film

Tabel 1. Jumlah Rating Setiap Film
**movieId**|**userId**|**rating**|**timestamp**
:-----:|:-----:|:-----:|:-----:	
1|65904|843.0|242914455479
2|36251|377.5|124938583322
3|14747|169.5|52265734386
4|1539|16.5|6290052048
5|14679|150.5|48640552594
...|...|...|...
193581|184|4.0|1537109082
193583|184|3.5|1537109545
193585|184|3.5|1537109805
193587|184|3.5|1537110021
193609|331|4.0|1537157606

## _Data Preparation_
### Menghapus _Missing Value_

_Missing value_ atau nilai yang hilang pada dataset adalah kondisi di mana suatu observasi atau entri dalam dataset tidak memiliki nilai atau informasi yang valid atau lengkap untuk atribut tertentu. Dalam bahasa lain, missing value adalah bagian dari data yang kosong atau tidak diisi.

Berikut jumlah nilai kosong pada setiap variabel:
```
userId       0
movieId      0
rating       0
timestamp    0
title        0
genres       0
dtype: int64
```

### Menghapus Fitur Yang Tidak Diperlukan

Dari fitur yang terdapat pada file ratings.csv, terdapat fitur yang tidak diperlukan, yakni fitur timestap, untuk menghilangkan fitur tersebut dapat menggunakan fungsi `drop()`. Berikut rating setelah fitur timestap dihapus.

Berikut total rating pada setiap film

Tabel 2. Jumlah Rating Pada Film (Setelah Timestamp Di-_Drop_)
**#**|**userId**|**movieId**|**rating**
:-----:|:-----:|:-----:|:-----:
0|1|1|4.0
1|1|3|4.0
2|1|6|4.0
3|1|47|5.0
4|1|50|5.0
...|...|...|...
100831|610|166534|4.0
100832|610|168248|5.0
100833|610|168250|5.0
100834|610|168252|5.0
100835|610|170875|3.0
     
### Menghapus Film Yang Tidak Ada Genre
Berikut nama-nama film yang tidak memiliki data genre.


Tabel 3. Daftar Film Yang Tidak Mempunyai Genre
**#**|**movieId**|**title**|**genres**
:-----:|:-----:|:-----:|:-----:
8517|114335|La cravate (1957)|(no genres listed)
8684|122888|Ben-hur (2016)|(no genres listed)
8687|122896|Pirates of the Caribbean: Dead Men Tell No Tal...|(no genres listed)
8782|129250|Superfast! (2015)|(no genres listed)
8836|132084|Let It Be Me (1995)|(no genres listed)
8902|134861|Trevor Noah: African American (2013)|(no genres listed)
9033|141131|Guardians (2016)|(no genres listed)
9053|141866|Green Room (2015)|(no genres listed)
9070|142456|The Brand New Testament (2015)|(no genres listed)
9091|143410|Hyena Road|(no genres listed)
...|...|...|...
9573|174403|The Putin Interviews (2017)|(no genres listed)
9611|176601|Black Mirror|(no genres listed)
9661|181413|Too Funny to Fail: The Life and Death of The D...|(no genres listed)
9663|181719|Serving in Silence: The Margarethe Cammermeyer...|(no genres listed)
9669|182727|A Christmas Story Live! (2017)|(no genres listed)

Kemudian melakukan drop yang tidak memiliki genre dan hasilnya sebagai berikut:
`jumlah movie tidak ada genre :  0`

## _Modelling_
Pada proyek ini, menggunakan penerapan 2 tipe model, yakni _Content Based Filtering_ dan _Collaborative Based Filtering_.

![WhatsApp Image 2023-07-30 at 12 41 41](https://github.com/aldymuardi/Sistem-Rekomendasi-Film/assets/79571450/f49f2919-c76a-454a-973b-6e8875d023fb)

Gambar 2. Sistem Rekomendasi _Content Based Filtering_ dan _Collaborative Filtering_

### _Content Based Filtering_
Content-Based Filtering adalah metode dalam sistem rekomendasi yang menggunakan informasi konten atau fitur dari item (produk, film, lagu, dll.) dan preferensi pengguna untuk memberikan rekomendasi yang sesuai. Pendekatan ini mencocokkan preferensi pengguna dengan fitur-fitur item yang relevan.

Kelebihan dari _Content Based Filtering_ adalah

* Tidak memerlukan data pengguna lain atau kolaboratif.
* Dapat memberikan rekomendasi personal yang disesuaikan dengan preferensi pengguna.
* Dapat memanfaatkan fitur-fitur detail dari item untuk memberikan rekomendasi yang lebih spesifik.
* Mampu menangani keadaan baru, di mana item baru dapat direkomendasikan berdasarkan fitur-fitur yang relevan.

Namun terdapat beberapa kelemahannya, yaitu

* Rentan terhadap _overfitting_, di mana rekomendasi dapat menjadi terlalu spesifik dan kurang variasi.
* Terbatas pada informasi konten yang tersedia untuk menggambarkan item.
* Tidak dapat menangkap preferensi pengguna yang kompleks atau berubah seiring waktu.
* Tidak mampu merekomendasikan item baru yang tidak ada dalam data pelatihan.

Pada proyek ini, _Content Based Filtering_ diawali dengan TF-IDF _Vectorizer_.

1. TF-IDF _Vectorizer_

_Term Frequency-Inverse Document Frequency_ (TF-IDF) _Vectorizer_ adalah sebuah metode yang digunakan untuk mengubah teks menjadi representasi vektor numerik. Metode ini digunakan dalam pemrosesan bahasa alami dan analisis teks untuk mengekstrak fitur-fitur penting dari teks.

Pada dasarnya, TF-IDF _Vectorizer_ mengukur pentingnya suatu kata dalam suatu dokumen berdasarkan frekuensi kemunculan kata dokumen tersebut (TF) dan keberulangan kata di seluruh dokumen dalam korpus (IDF).

Rumus umum untuk menghitung nilai TF-IDF adalah sebagai berikut:

$$TF-IDF(d, t) = TF(d, t) * IDF(t)$$

Di mana:

* TF(d, t) adalah frekuensi kemunculan kata (_term_) t dalam dokumen d. Frekuensi ini dapat dihitung dengan berbagai metode, misalnya menggunakan skema biner (jika kata ada dalam dokumen, nilai TF = 1) atau menggunakan frekuensi relatif (jumlah kemunculan kata dibagi dengan total kata dalam dokumen).
* IDF(t) adalah _inverse document frequency_ (kebalikan frekuensi dokumen) dari kata t. IDF mengukur sejauh mana kata t umum atau langka di seluruh dokumen dalam korpus. IDF dihitung sebagai logaritma dari jumlah total dokumen dalam korpus dibagi dengan jumlah dokumen yang mengandung kata t.

Untuk rumus TF adalah sebagai berikut
$$TF(d, t) = \dfrac{f_d(t)}{maxf_d(w)}$$

- $f_d(t)$ merupakan frekuensi kemunculan kata $t$ dalam dokumen $d$
- $maxf_d(w)$ merupakan jumlah kata dalam dokumen $d$


Pada bagian ini, _TF-IDF_ akan diterapkan untuk kolom genre. Langkah yang dilakukan untuk menerapkan Pada tahapan ini, _tokenizer_ yang akan digunakan adalah dengan _split_ pada data kolom tersebut. Hal ini digunakan agar data genre akan diproses dalam keadaan utuh, seperti pada suatu film dengan Genre _"Action, Sci-Fi, Drama"_, maka setelah dilakukan _vectonizer_ menjadi `['action', 'sci-fi', 'drama']`. Setelah itu lakukan perhitungan _IDF_ pada data genre. Kemudian jika di-_mapping_, maka hasilnya akan sebagai berikut.

`['action', 'adventure', 'animation', 'children', 'comedy', 'crime',
       'documentary', 'drama', 'fantasy', 'film-noir', 'horror', 'imax',
       'musical', 'mystery', 'romance', 'sci-fi', 'thriller', 'war',
       'western']`

Setelah itu, lakukan proses _fit_ dan transformasikan ke dalam bentuk matriks. Sehingga hasil ukuran matriks yang terbentuk adalah **9708 x 19** dengan 10 sampel hasil nya adalah sebagai berikut.

Tabel 4. Hasil Proses _Fit_ dan Transformasi ke Dalma Matriks
**title**|**musical**|**sci-fi**|**crime**|**war**|**adventure**|**comedy**|**mystery**|**horror**|**imax**|**western**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
Kissing Jessica Stein(2001)|0|0|0|0|0|0.570705|0|0|0|0
Black Sheep (1996)|0|0|0|0|0|1|0|0|0|0
Gothika (2003)|0|0.0|0|0|0|0|0|0.781052|0|0
Tie Me Up! Tie Me Down! (¡Átame!) (1990)|0|0|0.679969|0|0|0|0|0|0|0
Matewan (1987)|0|0.|0|0|0|0|0|0|0|0
House of Flying Daggers (Shi mian mai fu) (2004)|0|0|0|0|0|0|0|0|0|0
Bill Burr: I'm Sorry You Feel That Way (2014)|0|0|0|0|0|1|0|0|0|0
The Danish Girl (2015)|0|0|0|0|0|0|0|0|0|0
Sweeney Todd: The Demon Barber of Fleet Street (2007)|0.689591|0|0|0|0|0|0|0.520236|0|0
Evening with Kevin Smith 2: Evening Harder, An (2006)|0.000000|0|0|0|0|0.430109|0|0|0|0

2. _Consine Similarity_
   
_Cosine Similarity_ adalah sebuah metode yang digunakan untuk mengukur kemiripan antara dua vektor dalam ruang berdimensi banyak. Metode ini sering digunakan dalam pemrosesan bahasa alami, analisis teks, dan pengelompokan data.

Dalam _cosine similarity_, kemiripan antara dua vektor diukur berdasarkan sudut antara vektor-vektor tersebut. Nilai _cosine similarity_ berkisar antara -1 hingga 1, di mana nilai 1 menunjukkan kedua vektor memiliki arah yang sama atau sangat mirip, nilai 0 menunjukkan tidak ada kemiripan, dan nilai -1 menunjukkan arah yang berlawanan atau sangat berbeda.

Rumus untuk _Cosine Similarity_ adalah

$$Cosine Similarity_{(A,B)} = \dfrac{(A.B)}{(||A|| * ||B||)}$$

Di mana:

-   A dan B adalah dua vektor yang akan dibandingkan.
-   A . B adalah hasil perkalian dot (inner product) antara vektor A dan B.
-   ||A|| dan ||B|| adalah panjang (magnitude) dari vektor A dan B.

 <p align="center">
 <img src="https://images.deepai.org/glossary-terms/cosine-similarity-1007790.jpg" alt="Cosine Similarity Concept">
 </p>

Gambar 3. _Consine Similarity_

Untuk penerapan pada proyek ini, dapat menggunakan fungsi `cosine_similarity` dari _library sklearn_. Pada tahapan ini, akan dihitung menggunakan _cosine similarity_ pada data hasil _tf-idf_ sebelumnya. Sehingga hasil dari proses ini dapat dilihat di tabel sampel berikut ini.

Tabel 5. Menghitung Hasil TF-IDF Menggunakan Funsi _Consine Similarity_

**title**|**Duck, You Sucker (1971)**|**Every Secret Thing (2014)**|**Two Women (Ciociara, La) (1960)**|**Happy Feet Two (2011)**|**Liberal Arts (2012)**|**Two Brothers (Deux frères) (2004)**|**Great Ziegfeld, The (1936)**|**War and Peace (2016)**|**Stuck on You (2003)**|**Iron Man 3 (2013)**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:										
Game 6 (2005)|0|0.208262|0.265503|0.188629|1|0.239389|0.258560|0.366418|0.734682|0
Another Cinderella Story (2008)|0|0|0|0.343378|0.215217|0.399129|0.606649|0.354725|0.292939|0
Con Air (1997)|0.258163|0.245103|0|0|0|0.375026|0|0|0|0.407835
Killer Joe (2011)|0|0.692502|0|0|0||0|0|0|0|0.239137
Fistful of Dollars, A (Per un pugno di dollari) (1964)|1|0|0|0|0|0|0|0|0|0.174427
In the blue sea, in the white foam. (1984)|0|0|0|0.576353|0|0.419343|0|0|0|0
Duets (2000)|0|0.208262|0.265503|0.188629|1|0.239389|0.258560|0.366418|0.734682|0
Grizzly Man (2005)|0|0|0|0|0|0|0|0|0|0
Nanny McPhee (2005)|0|0|0|0.418940|0.262576|0.486959|0|0|0.357401|0
Candyman: Farewell to the Flesh (1995)|0|0|0|0|0|0|0|0|0|0

3. Mendapatkan Rekomendasi

Berikut _sample_ film yang dijadikan sebagai rujukan rekomendasi:

Tabel 6. Sampel Rujukan Rekmomendasi Film

**movieId**|**title**|**genres**
:-----:|:-----:|:-----:
127096|Project Almanac (2015)|Sci-Fi/Thrille

Hasil rekomendasi menggunakan teknik _Content Based Filtering_.

 Tabel 7. Hasil Rekomendasi Film Menggunakan Teknik _Content Based Filtering_

**movieId**|**title**|**genres**
:-----:|:-----:|:-----:
Signal, The (2014)|112868|Sci-Fi/Thriller
Seven Sisters (2017)|173925|Sci-Fi/Thriller
Push (2009)|66171|Sci-Fi/Thriller
Saturn 3 (1980)|2851|Adventure/Sci-Fi/Thriller
Saturn 3 (1980)|168358|Sci-Fi/Thriller
Limitless (2011)|84152|Sci-Fi/Thriller
Futureworld (1976)|26365|Sci-Fi/Thriller

### _Collaborative Based Filtering_

_Collaborative Based Filtering_ adalah metode dalam sistem rekomendasi yang mengandalkan informasi dari pengguna lain untuk memberikan rekomendasi. Pendekatan ini mencocokkan preferensi pengguna dengan preferensi pengguna lain yang memiliki profil atau perilaku serupa.

Kelebihan dari metode ini adalah

1.  Mampu menangani kompleksitas preferensi pengguna yang tidak dapat dilihat dari informasi konten item.
2.  Dapat merekomendasikan item baru yang tidak ada dalam data pelatihan berdasarkan perilaku pengguna lain.
3.  Tidak terbatas pada fitur-fitur item, sehingga dapat merekomendasikan item yang berbeda tetapi relevan.

Namun terdapat beberapa kekurangan, yaitu

1.  Bergantung pada ketersediaan data pengguna yang cukup untuk membuat rekomendasi yang akurat.
2.  Membutuhkan pemrosesan yang lebih intensif dan kompleks, terutama dalam skala besar.
3.  Rentan terhadap _cold start_ di mana rekomendasi sulit untuk pengguna baru yang memiliki sedikit atau tanpa data perilaku.

Berikut adalah tahapan dari _Collaborative Filtering_:

1. _Spliting_ Dataset

Data yang akan dibagi merupakan data yang sudah diproses di tahap Data Preperation. Sebelum membagi data training dan validasi, acak datanya terlebih dahulu agar distribusinya random.

Karena data berjumlah banyak, maka penulis bagi data dengan rasio 90:10. Namun sebelumnya, penulis perlu memetakan data user dan movie menjadi satu value terlebih dahulu. Lalu, buatlah rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.
  
2. Proses _Training_

Pada tahap ini, model menghitung skor kecocokan antara pengguna dan movie dengan teknik embedding. Pertama, penulis melakukan proses embedding terhadap data user dan movie. Selanjutnya, lakukan operasi perkalian dot product antara embedding user dan movie. Selain itu, penulis juga dapat menambahkan bias untuk setiap user dan movie. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid.

Di sini, penulis membuat _class RecommenderNet_ dengan keras Model class. Kode class RecommenderNet ini terinspirasi dari tutorial dalam situs Keras dengan beberapa adaptasi.

Selanjutnya, lakukan proses compile terhadap model.

Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation.

Langkah berikutnya, mulailah proses training dengan _batch_size_ = 64 dan epochs = 5.

Setelah melakukan fit model, maka model siap digunakan untuk menghasilkan rekomendasi.

3. Mendapatkan Rekomendasi Film

Untuk mendapatkan rekomendasi movie, pertama penulis ambil sampel user secara acak dan definisikan variabel movie_not_watched yang merupakan daftar movie yang belum pernah ditonton oleh pengguna. daftar movie_not_watched ini yang akan menjadi movie yang penulis rekomendasikan.

Sebelumnya, pengguna telah memberi rating pada beberapa movie yang telah mereka tonton. penulis menggunakan rating ini untuk membuat rekomendasi movie yang mungkin cocok untuk pengguna. Nah, movie yang akan direkomendasikan tentulah movie yang belum pernah ditonton oleh pengguna. Oleh karena itu, penulis perlu membuat variabel movie_not_watched sebagai daftar movie untuk direkomendasikan pada pengguna.

Variabel movie_not_watched diperoleh dengan menggunakan operator bitwise (~) pada variabel movie_watched_by_user.

Selanjutnya, untuk memperoleh rekomendasi restoran, gunakan fungsi model.predict() dari library Keras.

Berikut rekomendasi yang dihasilkan dari model.

```
Showing recommendations for users: 77
===========================
film with high ratings from user
--------------------------------
1. Title: Star Wars: Episode IV - A New Hope (1977)
   Genres: Action|Adventure|Sci-Fi

2. Title: Star Wars: Episode V - The Empire Strikes Back (1980)
   Genres: Action|Adventure|Sci-Fi

3. Title: Harry Potter and the Chamber of Secrets (2002)
   Genres: Adventure|Fantasy

4. Title: Lord of the Rings: The Two Towers, The (2002)
   Genres: Adventure|Fantasy

5. Title: Spider-Man 2 (2004)
   Genres: Action|Adventure|Sci-Fi|IMAX

--------------------------------
Top 10 film recommendation
--------------------------------
1. Title: Silence of the Lambs, The (1991)
   Genres: Crime|Horror|Thriller

2. Title: Fargo (1996)
   Genres: Comedy|Crime|Drama|Thriller

3. Title: Third Man, The (1949)
   Genres: Film-Noir|Mystery|Thriller

4. Title: Goodfellas (1990)
   Genres: Crime|Drama

5. Title: Godfather: Part II, The (1974)
   Genres: Crime|Drama

6. Title: Full Metal Jacket (1987)
   Genres: Drama|War

7. Title: Amadeus (1984)
   Genres: Drama

8. Title: Boot, Das (Boat, The) (1981)
   Genres: Action|Drama|War

9. Title: Glory (1989)
   Genres: Drama|War

10. Title: Cool Hand Luke (1967)
   Genres: Drama
```

Hasil di atas adalah rekomendasi untuk user dengan id 77. Dari _output_ tersebut, dapat dibandingkan antara _Film with high ratings from user_ dan Top 10 _film recommendation_ untuk _user_.

Beberapa movie rekomendasi menyediakan genre yang sesuai dengan rating _user_. Sistem merekomendasikan movie dengan genre dominan Drama, sesuai dengan rating _user_ yang lebih dominan movie bergenre Drama. Begitu pula dengan genre lainnya. Prediksi yang cukup sesuai.

## _Evaluation_
Dalam proyek ini, kedua solusi rekomendasi mempunyai masing-masing cara evaluasi. Berikut evaluasi dari solusi-solusi rekomendasi.

### Evaluasi _Content Based Filtering_
Untuk mengevaluasi hasil rekomendasi _Content Based Filtering_, penulis menggunakan _Precision_. Metrik ini mengukur sejauh mana rekomendasi yang diberikan relevan dengan preferensi pengguna. Presisi dihitung dengan membagi jumlah rekomendasi yang relevan dengan jumlah total rekomendasi yang diberikan.

`Presisi = ((Jumlah Rekomendasi yang Relevan) / (Jumlah Total Rekomendasi)) * 100%`

```
Jumlah rekomendasi yang relevan = 7;
Jumlah total rekomendasi = 7;
```

```
Presisi = ((Jumlah Rekomendasi yang Relevan) / (Jumlah Total Rekomendasi)) * 100%

Presisi = (7 / 7) * 100%

Presisi = 100%
```
Maka dapat diketahui bahwa nilai evaluasi _Content Based Filtering_ menggunakan metrik _Precision_ adalah 100%.

### Evaluasi _Collaborative Based Filtering_

Untuk mengevaluasi model yang telah dilatih, proyek ini menggunakan metrik _root mean squared error_ (RMSE). _Root Mean Squared Error_ (RMSE) adalah metrik evaluasi yang digunakan untuk mengukur tingkat kesalahan atau deviasi dari prediksi model dalam perbandingan dengan nilai sebenarnya pada masalah regresi pada machine learning. RMSE merupakan akar kuadrat dari _Mean Squared Error_ (MSE).

* Metrik Root Mean Squared Error (RMSE)

_Root Mean Squared Error_ (RMSE) adalah metrik evaluasi yang umum digunakan dalam sistem rekomendasi untuk mengukur sejauh mana prediksi rekomendasi yang dibuat oleh sistem mendekati nilai yang sebenarnya atau preferensi pengguna. RMSE menghitung perbedaan antara nilai prediksi dan nilai sebenarnya dari set data pengujian.

Rumus RMSE adalah sebagai berikut:

`RMSE = sqrt((1/n) * Σ(yi - ŷi)^2)`

Di sini:

- n adalah jumlah data pengujian.
- yi adalah nilai sebenarnya.
- ŷi adalah nilai prediksi.

* Visualisasi Metrik

![image](https://github.com/aldymuardi/Sistem-Rekomendasi-Film/assets/79571450/b1a18d9a-930d-4248-abdf-6181303f834e)

Gambar 4. Hasil Visualisasi Metrik


Dari hasil RMSE tersebut, dapat dilihat bahwa baik pada data pelatihan maupun data validasi, RMSE mengalami penurunan setiap epoch. Hal ini menunjukkan bahwa model semakin mempelajari pola dalam data dan semakin baik dalam memprediksi nilai target.

Selain itu, RMSE pada data validasi juga memberikan gambaran tentang performa model pada data yang tidak digunakan dalam proses pelatihan. Jika RMSE pada data validasi tetap rendah dan mendekati RMSE pada data pelatihan, maka model memiliki kemampuan umum dalam memprediksi rating tanpa overfitting pada data pelatihan.

## Kesimpulan

Pada solusi _Content Based Filtering_, solusi ini menghasilkan rekomendasi yang sangat sesuai dengan sampel movie yang diberikan berdasarkan fitur genre movie. Metrik yang digunakan untuk mengukur evaluasi _Content Based Filtering_ adalah _Precision_. nilai precision didapat dari jumlah item yang relevan dibagi dengan jumlah item yang direkomendasikan. Nilai precision dari solusi rekomendasi ini sebesar 100%. Dalam hal ini, sistem rekomendasi memiliki presisi yang tinggi, menunjukkan bahwa sistem tersebut dapat menghasilkan rekomendasi yang sesuai dengan preferensi genre pengguna.

Pada solusi _Collaborative Filtering_, solusi ini menghasilkan rekomendasi yang relevan terhadap rating user dan genre. Rekomendasi movie yang diberikan memiliki genre yang sama paling tidak satu genre yang sama. Berdasarkan hasil visualisasi metrik, proses training model cukup smooth dan model konvergen pada epochs sekitar 4. Dari proses ini, penulis memperoleh nilai error (RSME) akhir sebesar sekitar 0.20 dan error pada data validasi sebesar 0.20. Nilai tersebut cukup bagus untuk sistem rekomendasi.

## Referensi
[1] Kristianto, W., Herwindiati, D. E., &amp; Hendryli, J. (2021). Sistem Rekomendasi drama Korea menggunakan metode user-based collaborative filtering. Jurnal Ilmu Komputer Dan Sistem Informasi, 9(1), 252. https://doi.org/10.24912/jiksi.v9i1.12668 

[2] Ritdrix, A. H., &amp; Wirawan, P. W. (2018). Sistem Rekomendasi Buku Menggunakan metode item-based collaborative filtering. JURNAL MASYARAKAT INFORMATIKA, 9(2), 24–32. https://doi.org/10.14710/jmasif.9.2.31482 
