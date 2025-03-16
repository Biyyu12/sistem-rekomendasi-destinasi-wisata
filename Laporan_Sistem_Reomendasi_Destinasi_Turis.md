# Laporan Proyek Sistem Rekomendasi Destinasi Wisata - Abiyyu Rasyiq Muhadzzib

## Project Overview

Industri pariwisata telah menjadi sektor yang penting dalam mendorong pertumbuhan ekonomi Indonesia. Namun, menurut artikel yang diterbitkan oleh GoodStat, industri ini mengalami penurunan signifikan hingga mencapai 87,44% pada masa pandemi COVID-19 [1]. Meski demikian, menurut Kemenparekraf, industri pariwisata kini mulai mengalami pemulihan, dengan teknologi berperan penting dalam hal ini, memberikan kontribusi sebesar 43,59% dalam kemudahan akses berwisata [2].

Seiring dengan kemudahan dalam mengakses informasi destinasi, wisatawan kini dihadapkan dengan tantangan dalam memilih destinasi yang sesuai dengan preferensi pribadi mereka. Setiap individu memiliki minat yang berbeda, seperti pada budaya, alam, kuliner, atau hiburan, yang mempengaruhi keputusan mereka dalam memilih destinasi yang tepat [3]. Untuk menjawab tantangan ini, sistem rekomendasi destinasi berbasis *collaborative filtering* dapat menjadi solusi yang efektif dalam mempersonalisasi rekomendasi destinasi wisata yang relevan dengan preferensi dan kebutuhan pengguna [4].

Selain itu, pada proyek ini menngunakan 2 solusi pendekatan sistem rekomendasi yaitu *content based filtering* dan *collaborative filtering*. Untuk pendekatan *collaborative filtering* akan dibuat 2 algoritma berbeda. Lalu kedua model tersebut akan dibandingkan dengan *RMSE* dan *Data Ground Truth* untuk menguji kinerja model.

Dengan proyek ini, sistem rekomendasi diharapkan dapat memberikan top-n rekomendasi destinasi yang sesuai dengan data pengguna, dan rating dari tempat yang pernah dikunjungi sehingga dapat memudahkan wisatawan dalam memilih destinasi wisata yang tepat.

## Business Understanding

Industri pariwisata di Indonesia merupakan sektor penting yang mendukung pertumbuhan ekonomi. Namun, sektor ini mengalami penurunan drastis akibat pandemi COVID-19, meskipun saat ini sedang menuju pemulihan dengan peran teknologi sebagai pendukung utama. Dalam pemilihan destinasi, wisatawan sering merasa kesulitan menentukan pilihan yang sesuai dengan preferensi pribadi karena banyaknya pilihan yang tersedia.

Dengan menyediakan sistem rekomendasi yang relevan, wisatawan lebih mungkin melakukan pemesanan atau kunjungan, yang dapat meningkatkan pendapatan bagi pelaku industri pariwisata. Dengan teknologi canggih dalam personalisasi dapat meningkatkan citra positif pelaku industri pariwisata di mata pelanggan. Sistem rekomendasi juga dapat mengurangi kebutuhan intervensi manual dalam menyarankan destinasi kepada pelanggan.

### Problem Statements

1. **Bagaimana mengatasi masalah dalam pemilihan destinasi wisata?**
Wisatawan mengalami kesulitan dalam memilih destinasi wisata yang sesuai dengan preferensi pribadi mereka, karena adanya banyak pilihan dan perbedaan minat individu seperti budaya, alam, kuliner, atau hiburan.

2. **Bagaimana sistem rekomendasi yang efektif?**
Untuk memudahkan wisatawan dalam menentukan destinasi yang sesuai dengan preferensi mereka, dibutuhkan sistem rekomendasi yang dapat mempersonalisasi pilihan destinasi berdasarkan data pengguna.

3. **Apa algortima yang tepat untuk rekomendasi?**
Algortima yang tepat untuk memberikan rekomendasi yang akurat, sehingga dapat membantu dan memberikan kepuasan kepada pengguna yang diberikan rekomendasi destinasi wisata.

### Goals

1. **Meningkatkan Kemudahan dalam Pemilihan Destinasi Wisata**
Menyediakan solusi bagi wisatawan yang kesulitan dalam memilih destinasi wisata yang tepat dengan memberikan rekomendasi yang relevan berdasarkan data pengguna.

2. **Mengembangkan Sistem Rekomendasi Destinasi Wisata yang Personalisasi**
Mengembangkan sistem rekomendasi destinasi wisata berbasis collaborative filtering dan content based filtering yang dapat mempersonalisasi rekomendasi berdasarkan preferensi pengguna, seperti minat pada budaya, alam, kuliner, atau hiburan.

3. **Mencari algorimta sistem rekomendasi yang relevan.**
Membuat dan membandingkan algoritma-algoritma collaborative filtering menggunakan metrik RMSE dan Data Ground Truth untuk menilai akurasi rekomendasi yang dihasilkan, guna memilih algoritma yang paling efektif dalam memberikan top-n rekomendasi destinasi wisata.

### Solution statements

1. **Menggunakan data yang relevan**
Mengumpulkan dan menggunakan data pengguna seperti rating pada destinasi, aktifitas sebelumnya, tempat tinggal, hingga umur pengguna. Selain itu, mengumpulkan dan menggunakan data destinasi, seperti deskripsi, lokasi, kategori, dan popularitas.

2. **Mengembangkan 2 model solusi sistem rekomendasi**
Mengembangkan 2 model dengan pendekatan yang berbeda, yaitu *content based filtering* dan *model-based collaborative filtering*. Lalu menampilkan top-n rekomendasi.

3. **Evaluation and Comparison**
Menggunakan metrik Root Mean Square Error (RMSE) dan Data Ground Truth untuk mengevaluasi akurasi prediksi rating. Lalu, melakukan eksperimen pada kedua algoritma dengan dataset yang sama, dan bandingkan hasilnya berdasarkan metrik evaluasi.

## Data Understanding

Pada proyek ini menggunakan dataset [Indonesia Tourism Destination](https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination/data?select=tourism_with_id.csv) yang dibuat oleh A_Prabowo pada 3 tahun lalu dan dapat diakses melalui platform kaggle. Dataset ini merupakan bagian dari sebuah proyek yang dikembangkan pada program Bangkit Academy 2021. Dataset ini terdiri dari 4 file utama, akan tetapi akan digunakan 3 file pada proyek ini:

1. tourism_with_id.csv
Berisi data tentang tempat wisata di 5 kota besar Indonesia: Jakarta, Yogyakarta, Semarang, Bandung, dan Surabaya.
Jumlah data: 437 baris dan 13 kolom.
Informasi yang mungkin disediakan: ID tempat, nama tempat, kota, kategori (misalnya, pantai, museum), harga tiket masuk, dll.

2. user.csv
Berisi data pengguna dummy untuk fitur rekomendasi berbasis pengguna.
Jumlah data: 300 baris dan 3 kolom.
Informasi yang mungkin ada: ID pengguna, nama, preferensi wisata (misalnya, suka pantai atau museum).

3. tourism_rating.csv
Memuat data rating yang diberikan pengguna untuk tempat wisata dengan total 1000 data.
jumlah data : 10000 baris dan 3 kolom
Kolom yang tersedia:
User ID: Pengguna yang memberi rating.
Place ID: Tempat wisata yang dinilai.
Rating: Skor yang diberikan pengguna (misalnya, skala 1–5).
Digunakan untuk membangun sistem rekomendasi berbasis rating.

### Kondisi Dataset
Pada platform kaggel diberitau kondisi dataset tidak memiliki missing value. Akan tetapi saat diperikasa pada variabel `Time_Minutes` terdapat beberapa missing value, akan tetapi variabel tersebut tidak digunakan pada proyek ini. Dataset ini juga memiliki sedikit outlier pada variabel `rating`. Dataset juga tidak memiliki nilai duplikat.  

### Variabel-variabel pada dataset *Indonesia Tourism Destination* adalah sebagai berikut:
File tourism_with_id.csv
- Place_id : Identitas unik untuk setiap tempat
- Place_Name : Nama dari tempat wisata
- Description : Deskripsi tempat wisata
- Category : Kategori tempat wisata
- City : Nama lokasi/kota dari tempat wisata
- Price : Harga tiket masuk dari tempat wisata
- Rating : Rating dari setiap destinasi wisata
- Time_Minutes : Waktu/durasi dalam menit
- Coordinate : Koordinat dari tempat wisata
- Lat : Latitude (garis lintang) dari tempat wisata.
- Long : Longitude (garis bujur) dari lokasi tempat wisata.

user.csv
- User_Id : Identitas unik pada setiap pengguna
- Location : Lokasi pengguna tinggal
- Age : Umur pengguna

tourism_rating.csv
- User_Id : Data identitas unik user
- Place_Id : Data identitas unik destinasi wisata
- Place_Ratings : Rating yang diberikan oleh user terhadap destinasi wisata yang pernah dikunjung oleh user

### EDA Dataset

**City**

![EDA_Place_City](https://github.com/user-attachments/assets/b53f2079-72e1-45ba-9402-b84cd20a221e)

Pada variabel `City` ada beberapa insight, yaitu:
- Terdapat 5 kota dari setiap destinasi wisata yang berada di pulau Jawa, yaitu Jakarta, Bandung, Yogyakarta, Semarang, dan Surabaya
- Kota dengan destinasi terbanyak pada dataset adalah Yogyakarta dan Bandung
- Tempat wisata terendah pada dataset adalah Surabaya

**Category**

![EDA_Place_Category](https://github.com/user-attachments/assets/94e9fc96-fbf6-403c-8c7b-e9e02b9d1b2f)

Pada variabel `Category` ada insight menarik yaitu:
- Terdapat 6 kategori destrinasi wisata pada file place, yaitu taman huburan, budaya, cagar alam, wisata bahari, tempat ibadah, dan pusat perbelanjaan
- Distribusi data dominan taman hiburan, wisata budaya, dan wisata cagar alam
- Jumlah tempat wisata paling sedikit dengan kategori Pusat Belanja dan Tempat Ibada

**Price**
 Berikut analisis statistika
 
 |Index| Rating |
|--|--|
|Count| 437.0 |
|Mean| 24652.17 |
|Std| 66446.37 |
|min| 0.0 |
|25%| 0.0 |
|50%| 5000.0 |
|75%| 20000.0 |
|Max| 900000.0 |

Dari tabel deskripsi tersebut dapat disimpulkan bahwa harga destinasi wisata ada pada angka 0 sampai 900000. Berikut adalah distribusi harga

![EDA_Place_Price](https://github.com/user-attachments/assets/e8a5fdc8-9d58-43af-8c2f-51508a761c94) 

Dari visual diatas dpaatdisimpulkan bahwa banyak destinasi wisata yang gratis dibandingkan dengan yang berbayar

**Rating**
Berikut analsis statis

|Index| Rating |
|--|--|
|Count| 437.0 |
|Mean| 4.4 |
|Std| 0.2 |
|min| 3.4 |
|25%| 4.3 |
|50%| 4.5 |
|75%| 4.6 |
|Max| 5.0 |

Dari hasil kolom deskripsi dapat dilihat bahwa rata-rata rating pada destinasi tempat adalah 4.4. Rating terendah adalah 3.4 dan tertinggi 5.0. Dapat diketahui juga bahwa skala rating pada dataset adalah 1-5. Berikut distribusi rating

![EDA_Place_Rating](https://github.com/user-attachments/assets/8c87ea60-9f86-4433-8be5-c30f61bca771)

Dari visual diatas dapat diketahui bahwa distribusi rata-rata rating destinasi wisata pada dataset ada pada 4.3 - 4.6. Dan outlier pada rating 3.8 dan 3.4.

**Asal Kota User**
Berikut adalah distribusi asal kota para pengguna.

![EDA_User_AsalKota](https://github.com/user-attachments/assets/d419279a-57e8-4770-a5c7-10c7d26f1074)

Dari visual diatas ada insight yang didapat, yaitu
- Terdapat 28 kota yang terdapat di pulau jawa.
- Kota Bekasi menjadi kota dengan data terbanyak yaitu 40 data, kemudian diikuti oleh kota semarang, yogyakarta dan Lampung.
- Kota dengan jumlah data paling sedikit yaitu Madura dan Ngajuk

**Age**
Berikut adalah hasil dari analisis statistik

|Index| Rating |
|--|--|
|Count| 300 |
|Mean| 28 |
|Std| 6.3 |
|min| 18 |
|25%| 24 |
|50%| 29 |
|75%| 34 |
|Max| 40 |

Dari tabel deskripsi diatas dapat disimpulkan bahwa rata-rata umur pengguna 28, dengan umur paling muda 18 tahun dan paling tua 40 tahun. Berikut adalah distribusi umur pengguna dengan plotbox.

![EDA_User_Age](https://github.com/user-attachments/assets/94fdf44a-7e4d-4b0c-8e5d-58466bf0d0d2)

Dari visual tersebut rata-rata distribusi umur pengguna ada pada jangkauan 24 sampai 34 tahun.

**Rating dari Pengguna**
Berikut adalah tabel statistika dari rating pengguna

|index|User\_Id|Place\_Id|Place\_Ratings|
|---|---|---|---|
|count|10000\.0|10000\.0|10000\.0|
|mean|151\.2927|219\.4164|3\.0665|
|std|86\.137|126\.228|1\.379|
|min|1\.0|1\.0|1\.0|
|25%|77\.0|108\.75|2\.0|
|50%|151\.0|220\.0|3\.0|
|75%|226\.0|329\.0|4\.0|
|max|300\.0|437\.0|5\.0|

Dari tabel tersebut dapat disimpulkan bahwa rata-rata pengguna memberikan rating 3 pada tempat yang meraka pernah kunjungi. Dan berikut merupakan destinasi wisata dengan jumlah rating terbanyak

![EDA_Rating_Top10](https://github.com/user-attachments/assets/98def685-21cc-4add-9b0c-eed8cff1e9e0)

Visual diatas memberikan informasi top 10 wisata dengan rating terbanyak. Dengan Gereja Perawan Maria Tak Berdosa Surabaya, Food Junction Grand Pakuwon dan Grand Maerakaca sebagai destinasi dengan rating terbanyak.

## Data Preparation
Pada data preparation ada beberapa tahap yang akan dilakukan untuk mempersiapkan dataset. Dataset ini nantinya akan digunakan untuk melatih 2 model dengan pendekatan yang berbeda. Berikut tahapan-tahapan yang dilakukan.
**Content Based Filtering**
1. TF-IDF Vectorizer

**Collaborative Filtering**
1. Encode dataset yang dibutuhkan
2. Trasnformasi nilai rating
3. Membagi dataset

berikut penjelasan setiap tahapan yang dilakukan pada proyek ini.

### TF-IDF Vectorizer
Pada Tahap ini akan digunakan TF-IDF Vectorizer. Teknik ini digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap kategori tempat wisata. 

```
tfidf = TfidfVectorizer()

place['Category'] =  place['Category'].str.replace(' ', '_')
place_categoty = tfidf.fit(place['Category'])

tfidf.get_feature_names_out()
```

Code diatas digunakan tunuk melakukan eksraksi fitur pada kolom `Category` dan melakukan replace untuk label yang menggunakan space(' ') menjadi underscore('_'). Selanjutnya, transformasi ke dalam matriks.

```
tfidf_matrix = tfidf.fit_transform(place['Category'])
tfidf_matrix.shape
```
Berhasil mentransformasi ke dalam matriks dnegan tfidf. Matriks tersebut memiliki 437 baris dan 6 kolom. Selanjutnya memeriksa matriks tfidf pada beberapa tempat wisata.

|Place\_Name|taman\_hiburan|tempat\_ibadah|bahari|pusat\_perbelanjaan|budaya|cagar\_alam|
|---|---|---|---|---|---|---|
|Pasar Taman Puring|0\.0|0\.0|0\.0|1\.0|0\.0|0\.0|
|Museum Sepuluh Nopember Kota Surabaya|0\.0|0\.0|0\.0|0\.0|1\.0|0\.0|
|Kampung Wisata Kadipaten|0\.0|0\.0|0\.0|0\.0|1\.0|0\.0|
|Museum Sasmita Loka Ahmad Yani|0\.0|0\.0|0\.0|0\.0|1\.0|0\.0|
|Gumuk Pasir Parangkusumo|1\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Situ Cileunca|0\.0|0\.0|0\.0|0\.0|0\.0|1\.0|
|Pantai Patihan|0\.0|0\.0|1\.0|0\.0|0\.0|0\.0|
|Taman Badak|1\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Gua Pawon|0\.0|0\.0|0\.0|0\.0|0\.0|1\.0|
|Jalan Braga|0\.0|0\.0|0\.0|0\.0|1\.0|0\.0|

Dapat dilihat bahwa nilai matriks sesuai dengan tempat-tempat wisata. Jadi pada dataset ini siap untuk digunakan untuk model content based filtering

### Encode Dataset 
Pada tahap ini dilakukan encode pada variabel `User_Id` dan `Place_Id` menjadi Interger. Hal ini dilakukan karena model-model yang akan digunakan pada proyek ini bekerja secara optimal dengan tipe data numerik. berikut code yang dijalankan

```
df = rating.copy()
def encoding(col, data=df):
  unique_value = data[col].unique().tolist()
  col_to_value_encoded = {x: i for i, x in enumerate(unique_value)}
  value_encoded_to_col = {i: x for i, x in enumerate(unique_value)}
  return col_to_value_encoded, value_encoded_to_col

user_to_user_encoded, user_encoded_to_user = encoding('User_Id')
place_to_place_encoded, place_encoded_to_place = encoding('Place_Id')
df['User_Id'] = df['User_Id'].map(user_to_user_encoded)
df['Place_Id'] = df['Place_Id'].map(place_to_place_encoded)
```

Penjelasan code diatas sebagai berikut. pertama melakukan copy pada data rating. Kemudian membuat fungsi untuk encode variabel/colom yang ingin di encode, yaitu 'User_ID' dan 'Place_Id'. Setelah dilakukan encode pada variabel tersebut, Dilakukan mapping menggunakan dictionary hasil encoding (`user_to_user_encoded` dan `place_to_place_encoded`) untuk memetakan nilai asli pada kolom `User_Id` dan `Place_Id` menjadi nilai numerik.

### Trasformasi nilai rating
Pada tahap ini dilakukan trasformasi/mengganti tipe data integer ke float pada data rating. Hal ini berguna untuk meningkatkan efesiensi dan kinerja model dalam membaca skala rating pada dataset. Berikut adalah code yang jalankan.

```
df['Place_Ratings'] = df['Place_Ratings'].values.astype(np.float32)
```

### Membagi Dataset
Pada tahap ini melakukan pembagian dataset menjadi dua, yaitu data latih dan data uji. Pada proyek ini dilakukan pembagian dengan perbandingan 80:20. Penggunkan perbandingan demikian karena dataset memiliki jumlah data yang cukup banyak. Berikut code yang digunakan.

```
df = df.sample(frac=1, random_state=42)
x = df[['User_Id', 'Place_Id']].values
y = df['Place_Ratings'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values

train_indices = int(0.8 * df.shape[0])
x_train, x_val, y_train, y_val = (
    x[:train_indices],
    x[train_indices:],
    y[:train_indices],
    y[train_indices:]
)
```
Berikut penjelasan dari code tersebut, yaitu:
1. Mengacak data untuk menghilangkan pola urutan.
2. Memisahkan fitur (User_Id, Place_Id) dan target (Place_Ratings).
3. Menormalkan target (Place_Ratings) untuk berada dalam rentang [0, 1].
4. Membagi dataset menjadi data latih dan validasi dengan proporsi 80%-20%.

## Modeling
Pada tahap ini membuat dan mengembangkan dua model solusi dengan dua pendekatan yang berbeda, yaitu *content based filtering* dan *collaborative filtering*. Kemudian untuk *contetn based filtering* menggunakan metode *Cosine Similarity* Dan *collaborative filtering* menggunakan dua motode, yaitu  metode *matrix factorization* dan metode *neural collaborative filtering*. 

### Content Based Filtering
*contetn based filtering* menggunakan metode *Cosine Similarity*. Berikut kelebihan dan kekurangannya

**Kelebihan content based filtering**
- Personalisasi Tinggi
Sistem merekomendasikan item berdasarkan preferensi dan karakteristik pengguna, sehingga lebih relevan secara individual.

- Tidak Membutuhkan Data Pengguna Lain
Hanya memerlukan data pengguna yang aktif, sehingga efektif meskipun basis pengguna kecil.

- Skalabilitas terhadap Item Baru (New User Problem)
Dapat dengan mudah menangani item baru selama memiliki deskripsi yang relevan.

- Privasi Pengguna Terjaga
Karena hanya mengandalkan informasi dari pengguna individu, data yang dibutuhkan lebih sedikit dibandingkan metode lain seperti collaborative filtering.

- Fleksibilitas pada Domain
Dapat digunakan di berbagai domain atau skenario dengan mudah, selama fitur konten item didefinisikan dengan baik.

**Kekurangan content based filtering**
- Terbatasnya Eksplorasi Konten Baru
Sistem hanya merekomendasikan item serupa dengan yang sudah diminati pengguna, sehingga rentan terhadap masalah filter bubble (tidak ada keragaman rekomendasi).

- Kebutuhan Ekstraksi Fitur yang Baik
Sistem sangat bergantung pada kualitas dan representasi fitur konten. Jika fitur tidak relevan atau kurang deskriptif, performa rekomendasi akan menurun.

- Kurangnya Collaborative Insight
Tidak dapat memanfaatkan pola atau preferensi kolektif pengguna lain, sehingga peluang untuk memberikan rekomendasi yang "tak terduga" lebih rendah.

- Masalah pada New User Problem
Jika pengguna baru tidak memiliki riwayat interaksi yang cukup, sistem akan sulit memberikan rekomendasi yang akurat.

- Overfitting pada Preferensi Pengguna
Sistem dapat menjadi terlalu fokus pada preferensi spesifik pengguna dan gagal memperkenalkan variasi atau item baru.

#### Cosine Similarity
Cosine Similarity adalah sebuah metode untuk mengukur kesamaan antara dua vektor dalam ruang n-dimensi berdasarkan sudut kosinus antara keduanya. Nilainya berkisar dari -1 hingga 1. Pada proyek ini mengukur kesamaan antara kategori yang dimiliki oleh tempat wisata.

```
cosine_sim = cosine_similarity(tfidf_matrix)
cosine_sim_df = pd.DataFrame(cosine_sim, index=place['Place_Name'], columns=place['Place_Name'])
cosine_sim_df.sample(5, axis=1).sample(10, axis=0)
```

Penjelasan kode diatas, sebagai beriktu.
- `tfidf_matrix`: Matrix representasi fitur dari dokumen menggunakan TF-IDF (Term Frequency-Inverse Document Frequency). Fungsi `cosine_similarity` menghitung matriks kesamaan (similarity matrix) antar semua pasangan dokumen dalam `tfidf_matrix`.
- `cosine_sim_df`: DataFrame untuk mempermudah interpretasi hasil Cosine Similarity.
Baris (index) dan kolom diberi nama berdasarkan `Place_Name` dari dataset `place`.
Setiap sel menunjukkan nilai kesamaan kosinus antara dua tempat.
- `sample(5, axis=1)`: Mengambil 5 kolom secara acak (tempat).
- `sample(10, axis=0)`: Dari hasil sebelumnya, mengambil 10 baris secara acak.

Tujuannya adalah untuk melihat subset kecil dari DataFrame secara acak, sehingga lebih mudah untuk diamati. Berikut top-n rekomendasi yang diberikan oleh model ini berdasarkan kemiripan dengan tempat wisata monumen nasional.

![Top-n_Rekomendasi_by_CBF](https://github.com/user-attachments/assets/f4b85290-cd89-4ba5-8504-7b7eb4750806)

### Collaborative Filtering
*collaborative filtering* menggunakan dua motode, yaitu  metode *matrix factorization* dan metode *neural collaborative filtering*. Pada metode *matrix factorization* menggunakan *Singular Value Decomposition (SVD)*. Dan pada metode *neural collaborative filtering* menggunkanan *RecommanderNet*. Beriktu penjelasan dari masing-masing model.

**Kelebihan Pendekatan Collaborative Filtering**
- Tidak Memerlukan Metadata:
Collaborative Filtering (CF) hanya memerlukan data interaksi (seperti user-item rating atau klik). Tidak perlu informasi tambahan seperti deskripsi produk atau profil pengguna.

- Mampu Menangkap Preferensi Kompleks:
CF dapat menangkap pola tersembunyi dalam preferensi pengguna melalui hubungan tidak langsung, misalnya "pengguna yang mirip dengan Anda menyukai item ini."

- Adaptif Terhadap Preferensi Pengguna:
Karena fokusnya pada data interaksi, CF bisa menyesuaikan rekomendasi berdasarkan perilaku pengguna.

- Penerapan Umum:
CF dapat digunakan dalam berbagai domain, mulai dari rekomendasi film, musik, belanja, hingga pendidikan.

- Personalisasi:
Pendekatan ini memberikan rekomendasi spesifik untuk setiap pengguna berdasarkan data interaksinya, menghasilkan pengalaman personal yang lebih baik.

**Kekurangan Pendekatan Collaborative Filtering**
- Cold Start Problem:
Untuk Pengguna Baru: Tanpa data interaksi sebelumnya, sistem sulit memberikan rekomendasi.
Untuk Item Baru: Jika item baru tidak memiliki cukup ulasan atau rating, item tersebut sulit direkomendasikan.

- Data Sparsity:
Pada dataset besar dengan banyak pengguna dan item, matriks user-item sering kali sangat jarang terisi (sparse). Hal ini menyulitkan model untuk mempelajari hubungan yang bermakna.

- Scalability:
Untuk sistem dengan jutaan pengguna dan item, menghitung kesamaan atau dekomposisi matriks bisa sangat mahal secara komputasi.

- Bias pada Data Populer:
CF cenderung merekomendasikan item populer (sering dirating) dibandingkan item niche yang jarang dirating, meskipun item niche mungkin lebih relevan untuk pengguna tertentu.

- Keseragaman Rekomendasi:
Karena pendekatan ini bergantung pada pola interaksi yang ada, pengguna yang memiliki perilaku mirip mungkin menerima rekomendasi yang sangat mirip, sehingga kurang beragam.

- Kurangnya Penjelasan:
CF tidak memberikan penjelasan langsung tentang mengapa suatu item direkomendasikan. Ini bisa menjadi tantangan untuk transparansi sistem.

- Masalah Cold Start pada Grup Tertentu:
Pengguna atau item yang jarang berinteraksi (long-tail) sering kali kurang terwakili dalam rekomendasi.

#### RecommanderNet

Model RecommenderNet merupakan model rekomendasi berbasis Embedding Layer untuk sistem rekomendasi. Model ini menggunakan pendekatan Collaborative Filtering dengan cara mempelajari representasi (embedding) dari pengguna dan item untuk memprediksi hubungan di antara mereka.

**Arsitektur Model**
```
class RecommenderNet(tf.keras.Model):

  def __init__(self, num_users, num_place, embedding_size, **kwargs):
    super(RecommenderNet, self).__init__(**kwargs)
    self.num_users = num_users
    self.num_place = num_place
    self.embedding_size = embedding_size
    self.user_embedding = layers.Embedding(
        num_users,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.user_bias = layers.Embedding(num_users, 1) 
    self.place_embedding = layers.Embedding( 
        num_place,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.place_bias = layers.Embedding(num_place, 1) 

  def call(self, inputs):
    user_vector = self.user_embedding(inputs[:,0])
    user_bias = self.user_bias(inputs[:, 0])
    place_vector = self.place_embedding(inputs[:, 1]) 
    place_bias = self.place_bias(inputs[:, 1]) 

    dot_user_resto = tf.tensordot(user_vector, place_vector, 2)

    x = dot_user_resto + user_bias + place_bias

    return tf.nn.sigmoid(x) # activation sigmoid
```

Penjelasan pada Arsitektur Model :
- Embedding Layer:
user_embedding dan place_embedding: Digunakan untuk merepresentasikan pengguna dan item dalam ruang vektor laten berdimensi embedding_size. Setiap pengguna dan item akan memiliki vektor laten yang dioptimalkan selama training.
user_bias dan place_bias: Embedding tambahan untuk menangkap bias khusus pengguna dan item.
- Dot Product (tf.tensordot):
Dot product antara user_vector dan place_vector merepresentasikan interaksi laten antara pengguna dan item. Nilai ini digunakan untuk memprediksi skor relevansi (rating).

- Penjumlahan Bias:
Setelah dot product, bias dari pengguna dan item ditambahkan untuk menyesuaikan prediksi agar lebih akurat.

- Aktivasi Sigmoid:
Aktivasi sigmoid memastikan output berada di rentang 0 hingga 1, cocok untuk tugas klasifikasi biner seperti preferensi.

**Model Compile**
```
model_RN.compile(
    loss = tf.keras.losses.BinaryCrossentropy(),
    optimizer = keras.optimizers.Adam(learning_rate=0.001),
    metrics=[tf.keras.metrics.RootMeanSquaredError()]
)
```
Penjelasan pada model compile yang digunakan:
- Loss Function:
BinaryCrossentropy: Cocok untuk kasus prediksi biner (contohnya suka atau tidak suka).

- Optimizer:
Adam digunakan karena sifat adaptifnya dalam mengatur learning rate.

- Metric:
RootMeanSquaredError digunakan untuk mengevaluasi seberapa jauh prediksi model dari target aslinya.

**Callback**
Menggunakan callback Learning Rate Scheduler untuk menurunkan learning rate secara otomatis saat model stagnan (val_loss tidak membaik).

```
reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.002, patience=5, min_lr=0.001)
```

**Model Fit**
Melatih model dengan `batch_size` 24 dan `epochs` 20.

```
history = model_RN.fit(
    x = x_train,
    y = y_train,
    batch_size = 24,
    epochs = 20,
    validation_data = (x_val, y_val),
    callbacks = [reduce_lr]
)
```

Setelah model dibuat, selanjutnya menguji coba model untuk mendapatkan Top-N recommended. Berikut hasilnya:

![Top-n_Rekomendasi_by_RN](https://github.com/user-attachments/assets/5d1173f5-69ba-4271-b330-7ca4e2a42f38)

#### Singular Value Decomposition (SVD)

SVD adalah salah satu algoritma populer dalam sistem rekomendasi berbasis Collaborative Filtering. SVD digunakan untuk memfaktorkan matriks besar (misalnya matriks user-item) menjadi matriks dengan dimensi yang lebih kecil, yang disebut latent factors. Ini memungkinkan kita memahami hubungan antara pengguna dan item dengan lebih efisien.

**Kelebihan Model SVD** :

- Efisiensi Representasi:
Mengurangi dimensi data, membuat proses rekomendasi lebih efisien.

- Penanganan Noise:
Dengan merepresentasikan data dalam latent factors, SVD dapat mengurangi efek noise dari data yang tidak konsisten.

- Akurasi Tinggi:
SVD sering menunjukkan performa yang baik dalam berbagai dataset rekomendasi.

- Fleksibilitas:
Parameter seperti n_factors, n_epochs, dan reg_all dapat disesuaikan untuk dataset yang berbeda.

- Matematis Terbukti:
SVD memiliki dasar matematis yang kuat, memastikan model bekerja secara optimal pada data matriks yang terstruktur.

**Kekurangan Model SVD** :
- Cold Start Problem:
Sama seperti Collaborative Filtering lainnya, SVD kesulitan memberikan rekomendasi untuk pengguna atau item baru yang belum memiliki data interaksi.

- Kompleksitas untuk Dataset Besar:
Pada dataset dengan jumlah pengguna atau item yang sangat besar, proses pelatihan SVD dapat menjadi lambat dan memakan memori.

- Overfitting:
Jika regularisasi tidak diatur dengan baik, model dapat terlalu menyesuaikan data pelatihan dan gagal generalisasi pada data baru.

- Tidak Memanfaatkan Fitur Tambahan:
Model ini hanya memanfaatkan data interaksi user-item dan tidak bisa langsung memanfaatkan metadata pengguna atau item.

**Komponen Model SVD** :
```
trainset = train_dataset.build_full_trainset()
model_SVD = SVD(n_factors=10, n_epochs=5, lr_all=0.005, reg_all=0.02)
model_SVD.fit(trainset)
```

Berikut penjelasan komponen-komponen diatas:
- `n_factors`:
Jumlah latent factors yang digunakan untuk merepresentasikan pengguna dan item.
Semakin besar nilai n_factors, semakin kompleks representasi hubungan user-item. Pada proyek ini menggunakan `n_factors` = 10

- `n_epochs`:
Jumlah iterasi yang dilakukan model selama pelatihan.
Semakin banyak epoch, model lebih mampu mengkonvergensi, namun risiko overfitting bisa meningkat. Pada proyek ini menggunakan `n_epochs=5`

- lr_all (Learning Rate):
Kecepatan model dalam memperbarui parameter selama proses pelatihan. Nilai kecil seperti 0.005 memastikan pelatihan yang stabil. Pada proyek ini menggunakan `lr_all=0.005` 

- reg_all (Regularization):
Regularisasi digunakan untuk mencegah overfitting dengan memberikan penalti pada parameter yang terlalu besar. pada proyek ini menggunakan `reg_all=0.02`

- trainset.build_full_trainset():
Dataset dilatih dalam bentuk matriks lengkap (user-item matrix) di mana semua data yang tersedia digunakan untuk pelatihan.

- Fitting Model (fit):
Model mempelajari representasi laten dari pengguna dan item menggunakan data pelatihan.

Setelah model dibuat, selanjutnya menguji coba model untuk mendapatkan Top-N recommended. Berikut hasilnya:

![Top-n_Rekomendasi_by_SVD](https://github.com/user-attachments/assets/395a0641-2137-48d9-9368-30d8dd2ea958)

## Evaluation
Metrik evaluasi yang digunakan untuk mengevaluasi model-model yang telah dilatih adalah RMSE dan Precision. Root Mean Squared Error (RMSE) merupakan salah satu metrik evaluasi yang sering digunakan untuk mengukur seberapa baik model prediksi dibandingkan dengan nilai sebenarnya pada dataset yang diberikan. RMSE memberikan nilai dalam satuan yang sama dengan target, membuatnya intuitif untuk memahami seberapa jauh prediksi rata-rata meleset dari nilai sebenarnya.

### Precision
**Formula Precision**

$$Presicion = \frac{True \ Positives}{True \  Positives + False \ Positives}$$

**Cara Kerja**
Cara kerja dari presicion adalah precision menunjukkan berapa banyak dari prediksi kelas positif yang benar-benar positif. Jika precision tinggi, berarti model jarang salah mengklasifikasikan sampel negatif sebagai positif. 

Hasil evalusi Precision dari model pada proyek ini
|No|Model|Precision|
|--|--|--|
|1|Cosine Similarity|85%|
|2|RecommenderNet|100%|
|3|Singular Value Decomposition (SVD)|100%|

### RMSE
**Formula dari RMSE**

$$\sqrt{\dfrac{1}{n}\sum_{i=1}^{n} (y_i\ - \hat y_i)^2}$$

Keterangan
$$n$$ : Jumlah data (observasi) dalam dataset
$$y_i$$ : Nilai aktual dari data ke-$$i$$
$$\hat y_i$$ : Nilai prediksi dari data ke-$$i$$
$$(y_i\ - \hat y_i)^2$$ : Selisih kuadrat antara nilai aktual dan prediksi.

**Cara Kerja Metrik RMSE**

Hitung selisih (error) antara nilai prediksi ($$\hat y_i$$) dan nilai aktual ($$y_i$$) untuk setiap data. Kemudian tingkatkan semua error ke pangkat dua untuk memastikan bahwa nilai negatif tidak membatalkan nilai positif dan untuk memberi bobot lebih besar pada error yang lebih besar. lalu, mengambil rata-rata dari semua error kuadrat. Terakhir, Hitung akar kuadrat dari rata-rata error kuadrat untuk mengembalikan error ke skala aslinya.

Evalusi RMSE digunakan untuk evaluasi *collaborative filtering*, berikut adalah hasilnya.
|No|Model|RMSE|
|--|--|--|
|1|RecommenderNet|0.35040|
|2|Singular Value Decomposition (SVD)|0.35260|

### Dampak model pada Business Understanding.

Model sudah menjawab problem statemtn. Dengan 2 pendekatan solusi sistem rekomendasi dan mencari model yang efektif dan relevan dalam memberikan rekomendasi terhadapa preferensi pengguna. Model *content based filtering* memberikan tempat rekomendasi yang relevan dengan tempat wisata seperti monumen nasional. Pada model *collaborative filtering* juga baik dalam memberikan 10 tempat yang relevan dengan data pengguna, yang dimana data tersebut berisi tempat yang pernah dikunjungi oleh pengguna dan berdasarkan rating tertinggi dari pengguna.

Hasil evaluasi *content based filtering* memberikan precision 85% relevan dengan tempat wisata monumen nasional. Dan pada hasil evalusi *collaborative filtering* kedua model memberikan precision yang sempurna yaitu 100%. Model ini dapat menjadi model sistem rekomendasi yang efektif dan tepat dalam memberikan rekomendasi relevan.

Model juga berhasil mencapai kedua goals yang ditentukan.

1. Meningkatkan kemudahan dalam pemilihan destinasi wisata
Model ini membantu pengguna dalam memilih tempat wisata yang belum mereka kunjungi dan tempat wisata tersebut relevan dengan data pengguna. Dengan membantu pengguna memberikan 10 tempat rekomendasi.

2. Mengembangkan sistem rekomendasi destinasi wisata yang personal
Model collaborative filtering dapat memberikan destinasi wisata yang personal dengan memanfaatkan data rating tertinggi pengguna dari tempat yang pernah dikunjungi.

3. Mencari algorimta sistem rekomendasi yang relevan
Dengan hasil evalusi tersebut sistem dengan collaboratif filtefing, seperti RecommenderNet dan SVD dapat menjadi model yang memberikan tempat-tempat wisata yang relevan.

Solusi statement yang direncanakan juga memiliki dampak yang signifikan untuk mencapai goals. Berikut merupakan penjelasannya.
1. Penggunaan dataset Indonesia Tourism Destination Memberikan data yang relevan. Data tersebut berisi rating wisata, data pengguna, dan data lain yang dibutuhkan untuk mengembangkan sistem rekomendasi
2. Dengan mengembangakan 2 solsui sistem rekomendasi. Ini memudahkan dalam mencari model yang efektif dan relevan dalam memberikan rekomendasi. Dengan dua pendekatan ini dapat dimanfaatkan ataupun dikombinasikan untuk menghasilkan model yang lebih optimal lagi.
3. Evaluasi dan comparacon. Evaluasi dan perbandingan ini juga membantu menemukan model terbaik yaitu RecommenderNet karena memiliki precision 100% dan RMSE 0.350. Menjadikan model terbaik dalam proyek ini.

## Referensi 
[1] Rainer, Pierre. (2024) *Kunjungan Wisatawan Mancanegara Capai 1,16 Juta, Tembus Rekor Pascapandemi*. Diakses pada 16 November 2024 dari https://goodstats.id/article/kunjungan-wisatawan-mancanegara-1-16-juta-tembus-rekor-pascapandemi-WHAyT

[2] Kemenparekraf. (2021). *Pemulihan sektor pariwisata melalui teknologi. Kementerian Pariwisata dan Ekonomi Kreatif Indonesia*. Diakses pada 16 November 2024 dari https://kemenparekraf.go.id/ragam-pariwisata/expert-survey-sektor-pariwisata-dan-ekonomi-kreatif-tumbuh-pada-2024

[3] Drift. (2024). *What Factors to Consider When Choosing Your Next Travel Destination*. Diakses pada 17 November 2024 dari https://drifttravel.com/what-factors-to-consider-when-choosing-your-next-travel-destination/

[4] Ningrum, E. C. (2020). *Sistem rekomendasi pemilihan tempat wisata menggunakan Metode Item Based Collaborative Filtering dan Location Based Service (Kota Batu)* (Doctoral dissertation, Universitas Islam Negeri Maulana Malik Ibrahim).