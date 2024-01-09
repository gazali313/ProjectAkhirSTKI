# Sistem Rekomendasi Film
### _Problem Statment_
1. Bagaimana meningkatkan akurasi dan efektivitas sistem rekomendasi film untuk memberikan rekomendasi yang lebih personal dan relevan bagi setiap pengguna dengan _content-based filtering_?
2. Bagaimana meningkatkan pengalaman pengguna di platform hiburan dengan menyediakan rekomendasi film yang relevan dan sesuai dengan preferensi masing-masing pengguna dengan _collaborative filtering_?

### _Goals_
1. Menghasilkan rekomendasi film yang dipersonalisasi dan relevan untuk pengguna dengan teknik _content-based filtering_.
2. Menghasilkan rekomendasi film yang sesuai dengan preferensi pengguna dan belum pernah ditonton sebelumnya dengan _collaborative filtering_.

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

* TF(d, t) adalah frekuensi kemunculan kata (_term_) t dalam dokumen d. Frekuensi ini dapat dihitung dengan berbagai metode, misalnya menggunakan skema biner (jika kata ada dalam dokumen, nilai TF = 1) atau menggunakan frekuensi relatif (jumlah kemunculan kata dibagi dengan total kata dalam dokumen).
* IDF(t) adalah _inverse document frequency_ (kebalikan frekuensi dokumen) dari kata t. IDF mengukur sejauh mana kata t umum atau langka di seluruh dokumen dalam korpus. IDF dihitung sebagai logaritma dari jumlah total dokumen dalam korpus dibagi dengan jumlah dokumen yang mengandung kata t.

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
