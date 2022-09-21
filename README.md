# SistemRekomendasiWisata

# Laporan Proyek Machine Learning - Putra Dwi Wira Gardha Yuniahans

## Project Overview

Covid-19 atau Coronavirus 2019 merupakan sebuah virus yang menyerang manusia serta penularannya begitu cepat. Pandemi tersebut juga mengakibatkan dampak pada seluruh dunia serta seluruh kegiatan masyarakat. Salah satu kegiatan yang terkena dampak tersebut yaitu kegiatan perekonomian serta pariwisata [1]. Selama dua tahun sektor pariwisata tidak bisa berjalan dengan semestinya dikarenakan pandemi yang memaksa pemerintahan untuk membuat peraturan agar masyarakat tidak berkeliaran atau berkegiatan diluar rumah. Maka dari itu pariwisata pada dua tahun lalu yaitu pada tahun 2020 dan 2021 mengalami penurunan pengunjung. tetapi berbeda dengan tahun ini pandemi covid-19 sudah semakin melandai. Semua negara sudah mulai memperbaiki perekonomian negara masing-masing. Begitu pun Indonesia juga mulai memperbaiki perekonomian serta pariwisata yang terkena dampak pandemi kemarin, dengan membuka pariwisata serta merenggangkan peraturannya. Rekomendasi wisata sekarang juga sangat berguna untuk pengunjung wisata diluar kota tersebut, karena rekomendasi wisata bisa merekomendasikan wisata dengan rating wisata yang tinggi. Maka dari itu terdapat proyek mechine learning Sistem Rekomendasi Wisata Surabaya. 

## Business Understanding

Berdasarkan uraian diatas maka saya mengembangkan sebua proyek mechine learning yaitu Sistem Rekomendasi Wisata Surabaya untuk menjawa pertanyaan-pertanyaan berikut:

### Problem Statements

- Berdasarkan data mengenai pengguna, bagaimana membuat suatu sistem rekomendasi wisata yang dipersonalisasi dengan teknik content-based filtering?
- Dengan dataset rating yang tersedia, Bagaimana cara mendapatkan rekomendasi wisata yang mungkin disukai pengguna serta pengguna belum pernah mengunjungi wisata tersebut?

### Goals

- Menghasilkan sejumlah rekomendasi wisata yang dipersonalisasi untuk pengguna
- Menghasilkan sejumlah rekomendasi wisata berdasarkan preferensi pengguna serta pengguna belum pernah mengunjungi wisata tersebut.

### Solution statements
- Agar menghasilkan rekomendasi wisata yang dipersonalisasi untuk pengguna dengan menggunakan teknik content-based filtering.
- Teknik kedua terdapat colaborative filtering agar menghasilkan rekomendasi wisata berdasarkan preferensi pengguna serta pengguna belum pernah mengunjungi wisata tersebut.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://drive.google.com/uc?export=download&id=1pm9x4P1MQ-5y_u2U_zecdifI8fY_tpyh).
Proyek mechine learning Sistem Rekomendasi Wisata membutuhkan dataset untuk bisa merekomendasikan wisata kepada pengguna. Dataset tersebut tersedia pada platform kaggle, berikut merupakan link [dataset](https://drive.google.com/uc?export=download&id=1pm9x4P1MQ-5y_u2U_zecdifI8fY_tpyh) yang digunakan. Pada dataset tersebut terdapat empat file yang berextensi .csv. Pada proyek ini hanya menggunakan tiga file yang penting yaitu data wisata, data pengguna, serta data rating wisata. Jumlah masing-masing data dari ketiga file tersebut yaitu pada file data wisata terdapat 437 data yang terdiri dari 5 kota terbesar yaitu Bandung, Jakarta, Yogyakarta, Semarang, serta Surabaya, untuk proyek ini yang akan digunakan hanya data wisata yang terdapat pada kota surabaya. Selanjutnya pada file pengguna terdapat 300 data, dan file terakhir rating wisata terdapat 10.000 data. berikut merupakan bukti jumlah data tersebut:<br>
![Capture](https://user-images.githubusercontent.com/108270264/191395556-0f98e165-92fc-4558-9e89-fbebee9e840e.PNG)
<br>Gambar 1. Jumlah Data Wisata
<br>
Variabel-variabel pada Dataset yang digunakan adalah sebagai berikut:
- package_tourism : merupakan file yang berisi paket untuk liburan.
- tourism_with_id : merupakan file yang berisi tentang berbagai macam wisata dari lima kota terbesar yaitu Bandung, Jakarta, Yogyakarta, Semarang dan Surabaya.
- user : merupakan file yang berisi tentang pengguna.
- tourism_rating : merupakan file yang berisi tentang kumpulan rating dari berbagai macam wisata yang terdapat di file tourism_with_id.

Pada file tourism_with_id terdapat 437 data dari macam-macam wisata yang tersebar di lima kota besar yang sudah dijelaskan, berikut merupakan visualisasi sebaran data tersebut dari masing-masing kota:
![visualisasi](https://user-images.githubusercontent.com/108270264/191396155-75b534bf-be69-40e8-98d9-41518f5a6405.PNG)
<br>Gambar 2. Visualisasi Data Wisata
<br>Pada file tersebut juga terdapat fiel kategory, berikut merupakan visualisasi sebaran data berdasarkan kategory dan data tersebut sudah hanya data wisata yang berada di kota Surabaya: <br>
![kategori](https://user-images.githubusercontent.com/108270264/191396369-58d93e35-ad1e-4780-a2c5-689827c28162.PNG)
<br>Gambar 3. Visualisasi Data Wisata Berdasarkan Kategori
## Data Preparation

Tahap selanjutnya yaitu data preparation atau persiapan data, berikut merupakan tahap-tahap pada data preparation:

### Menampilkan Hanya Data Wisata di Surabaya
Seperti yang diketahui pada dataset file tourism_with_id yang berisikan data wisata dari lima kota besar, serta tujuan dari proyek ini yaitu hanya merekomendasikan wisata yang berada pada kota Surabaya saja, maka langkah yang tepat yaitu hanya membaca data file tersebut yang berisikan wisata di Surabaya. tahap tersebut akan disimpan divariable yang berbeda agar data yang disimpan sama seperti tujuan dari proyek ini, berikut merupakan Tabel data wisata yang terdapat di Surabaya:<br>
<br>
| Place_Id | Place_Name | Description | Category | City | Price | Rating | Time_Minutes | Coordinate | Lat | Long |
|---|---|---|---|---|---|---|---|---|---|---|
| 392 | Ekowisata Mangrove Wonorejo | Hutan Wisata Mangrove Surabaya merupakan wisat...	| Cagar Alam | Surabaya | 0 | 4.3 | 60.0 | {'lat': -7.308648199999999, 'lng': 112.8216622} | -7.308648 | 112.821662 |
| 393 | Taman Harmoni Keputih	| Tempat tersebut ialah Taman Hatmoni Keputih Su... | Cagar Alam | Surabaya | 0	| 4.4	| 60.0 | {'lat': -7.2952211, 'lng': 112.8035603} | -7.295221 | 112.803560 |
| 394 | Air Mancur Menari | Jembatan Kenjeran dengan air mancur menarinya ...	| Taman Hiburan	| Surabaya | 35000 | 4.4 | 45.0 | {'lat': -7.2356933, 'lng': 112.7955234} | -7.235693 | 112.795523 |

<br>Tabel 1. Data Wisata di Surabaya
<br>Pada Tabel 1 terdapat 'Place_Id' yang berarti kode dari wisata tersebut, lalu terdapat 'Place_Name' atau nama wisata, 'Description' yaitu deskripsi hingga terdapat harga dan lain sebagainya. Tidak hanya pada tabel data wisata saja yang di tampilkan hanya wisata di Surabaya melainkan kedua tabel lainnya juga diperlakukan seperti terebut.

### Menggabungkan Data
Setelah data telah bersih atau sudah berisi tentang data wisata yang berada si Surabaya, maka selanjutnya yaitu menggabungkan data rating dengan nama wisata serta kategorinya. yang bertujuan agar mengetahui rating dari setiap wisata di Surabaya serta kategori dari wisata di Surabaya. Data tersebutlah yang nantinya akan digunakan untuk sistem rekomendasi wisata. berikut merupakan tabel data setelah digabung:<br>
| User_Id | Place_Id | Place_Ratings | Place_Name | Category | 
|---|---|---|---|---|
| 25 | 392 | 4 | Ekowisata Mangrove Wonorejo | Cagar Alam |
| 298 | 392 | 3 | Ekowisata Mangrove Wonorejo | Cagar Alam |
| 297 | 392 |	3	| Ekowisata Mangrove Wonorejo | Cagar Alam |

<br>Tabel 2. Penggabungan Data

### Mencari Data Missing Value
Setelah dataset digabung maka sebelum dataset digunakan untuk pemodelan alangkah baiknya dataset tersebut dicari data yang missing value, pada pencarian data missing value di proyek ini menggunakan fungsi isnull() yang berfungsi apakah terdapat data yang kosong, serta fungsi sum() yang berfungsi untuk menjumlahkan data yang ksong tersebut. Ternyata pada dataset yang digunakan kali ini tidak terdapat data yang missing value. Karena tidak terlihat data yang kosong pada dataset tersebut, berikut merupakan bukti tidak adanya data yang missing value:<br>
| Variable | Jumlah Data Missing Value |
|---|---|
| User_Id | 0 |
| Place_Id | 0 |
| Place_Ratings | 0 |
| Place_Name | 0 |
| Category | 0 |

<br>Tabel 3. Hasil Cek Data Missing Value

### Menghapus Data Duplikat
Langkah selanjutnya setelah dipastikan dataset bersih atau tidak terdapat missing value yaitu langkah menghapus data yang duplikat. Tujuan dari tahap ini yaitu agar dataset yang akan digunakan untuk pemodelan hanya berupa data yang uni saja. Sebelum melakukan penghapusan data yang duplikat, jumlah dataset tersebut terdapat 1050 data, dan setelah  dilakukan penghapusan terdapat hanya 46 data. berikut merupakan Tabel data setalah melakukan tahapan penghapusan data yang duplikat:<br>

| User_Id | Place_Id | Place_Ratings | Place_Name | Category | 
|---|---|---|---|---|
| 25 | 392 | 4 | Ekowisata Mangrove Wonorejo | Cagar Alam |
| 1 | 393 | 5 | Taman Harmoni Keputih | Cagar Alam |
| 43 | 394 | 2 | Air Mancur Menari | Taman Hiburan |

<br>Tabel 4. Data Tidak Duplikat Wisata Surabaya 
### Membagi Dataset
Langkah ini hanya digunakan untuk pendekatan colaborative filtering karena pendekatan tersebut menggunakan model untuk dilatih. Pembagian dataset untuk proyek ini yaitu membagi data trai dan validasi dengan komposisi 80:20.

## Modeling
Setelah melakukan berbai tahapan seperti Bussines Understanding, Data Understanding, serta Data Preparation maka tahap selanjutnya yaitu pemodelan. Pada proyek kali ini terdapat dua pendekatan untuk mengembangkan sistem rekomendasi, yaitu pendekatan menggunakan content-based filtering data colaborative filtering. Berikut penjelasan masing-masing pendekatan:

### Content-Based Filtering
Content-Based Filtering merupakan sebuah pendekatan sistem rekomendasi yang memiliki konsep kerja mencocokan item yang disukai oleh pengguna dengan item lainya serta memiliki kemiripan berdasarkan atributnya [2]. Sebelum mengembangkan sistem rekomendasi dengan pendekatan langkah pertama yang dijalankan yaitu menemukan representasi fitur penting dari setiap kategori wisata. untuk menemukan hal tersebut proyek ini menggunakan CountVektorizer dari library scikit learn dan melakukan fit serta transormasi daam bentuk matriks, berikut merupakan hasil matriks dari CountVektorize():<br>
![matriks](https://user-images.githubusercontent.com/108270264/191401580-694f784c-9cec-4360-be8d-2ec12b89f2d8.PNG)
<br>Gambar 4. Matriks CountVektorize
<br>Selanjutnya memvisualisasikan data wisata dan kategori berdasarkan matriks diatas :
| Nama Wisata | Pusat | Hiburan | Bahari | Budaya | Tempat | Alam | Perbelanjaan | Taman | Ibadah | Cagar |
|---|---|---|---|---|---|---|---|---|---|---|
| Surabaya Museum (Gedung Siola) | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| Taman Prestasi | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| Surabaya North Quay | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |

<br>Tabel 5. Data Wisata dan Kategori Berdasarkan Matriks
<br>Terlihat pada Tabel 5. diatas yaitu Surabaya Museum (Gedung Siola) merupakan kategori wisata Budaya yang dibuktikan dari nilai matriks pada kategori Budaya bernilai 1.0. Setelah menemukan representasi fitur yang penting, maka terdapat langkah mengidentifikasi korelasi wisata dan kategori dengan menggunakan teknik consine similarity dari library scikit learn untuk menghitung drajat kesamaan antar wisata dan kategorinya. Selanjutnya memvisualisasikan matriks kesamaan setiap wisata :<br>
![kesamaan](https://user-images.githubusercontent.com/108270264/191402834-f6a5bd89-e34e-4c57-9880-d7cdf7a7f9e7.PNG)
<br>Gambar 5. Matriks Kesamaan Setiap Wisata
<br>Pada Gambar 5 diatas dengan nilai matriks 1.0 berarti terdapat kesamaan wisata pada sumbu x dan sumbu y, seperti Taman Kunang-Kunang teridentifikasi sama dengan Taman Barunawati. Langkah terakhir yaitu membuat rekmendasi yang akan memberi output Top-N Recomendation wisata, dan dengan mengetest apakah fungsi tersebut berjalan secara akurat atau tidak dengan menghapus salah satau data wisata yang akan kita gunakan untuk mengetest fungsi tersebut. Maka hasil dari pendekatan content-based filtering sebagai berikut:<br>
| Nama Wisata | Kategori Wisata |
|---|---|
| Ekowisata Mangrove Wonorejo | Cagar Alam |
| Kebun Binatang Surabaya	| Cagar Alam |
| Hutan Bambu Keputih	| Cagar Alam |
| Kebun Bibit Wonorejo | Cagar Alam |
| Taman Buah Surabaya | Taman Hiburan |

<br>Tabel 6. Hasil Rekomendasi dengan Pendekatan <i>Content-Based Filtering</i>
<br>Pada test kali ini menggunakan data Taman Harmoni Keputih yang berkategori Cagar Alam, maka seharusnya rekomendasi wisata adalah wisata yang memiliki kemiripan kategori dari Taman Harmoni Keputih tersebut. Dan hasilnya benar mendapatkan Top-N rekomendasi dengan kategori Cagar Alam yang sama dengan Taman Harmoni Keputih. Pada pendekatan ini memiliki kekurangan dan kelebihan yaitu untuk mendapatkan akurasi yang baik atau rekomendasi yang baik pendekatan ini memerlukan fitur atau deskripsi item yang baik juga.

### Colaborative Filtering
Selain pendekatan content-based filtering, pada proyek ini juga menggunakan pendekatan colaborative filtering dengan tujuan menghasilkan rekomendasi wisata berdasarkan preferensi pengguna dan rating yang telah diberikan sebelumnya. Dari rating tersebut akan digunakan untuk merekomendasikan wisata yang mirip dan belum pernah dikunjung oleh pengguna. Setelah pada tahap Data Preparation pada proses pembagian dataset menjadi data training dan data validasi maka langkah selanjutnya yaitu melakukan mapping data user dan wisata menjadi satu value terlebih dahulu. Berikut merupakan hasil mapping dari data user dan wisata:<br>
![mapping](https://user-images.githubusercontent.com/108270264/191405117-09a8dcad-7173-40d2-8689-88bdf0d8e164.PNG)
<br>Gambar 6. Hasil Mapping
<br>dari Gambar 6. mapping tersebut digunakan untuk menyatukan dari berbagai data serta menjembatani perbedaan dari data tersebut. Setelah melakukan mapping maka selanjutnya yaitu membuat kelas RecommenderNet yang digunakan untuk menghitung nilai kecocokan antara user dan wisata. skor kecocokan ditetapkan dalam skala 0 hingga 1 dengan fungsi aktivasi sigmoid. Setelah membuat class tersebut maka model akan dicompile terlebih dahulu sebelum melakukan proses training. Model ini menggunakan Binarry Crossentropy untuk menghitung los function, optimizer menggunakan Adam (Adaptive Moment Estimation), dan RMSE sebagai metriks evaluation, setelah melakukan compile pada model maka model akan ditraining atau dilataih, berikut merupakan hasil erorr setelah model dilatih: <br>
![plot](https://user-images.githubusercontent.com/108270264/191405878-ac76b934-7dfc-4652-8c9d-15dd57a66e74.PNG)
<br>Gambar 7. Plot Error Model
<br>Langkah terakhir yaitu mengetest model apakah memiliki prediksi rekomendasi yang akurat. Dengan membat variable wisata not visited dengan tujuan atau goal yang sudah dijelaskan agar rekomendasi pengguna yaitu wisata yang belum pernah dikunjungi tetapi mempunyai kemiripan. berikut merupakan output dari pendekatan colaborative filtering :<br>
| Nama Wisata | Kategori Wisata |
|---|---|
| Taman Prestasi | Taman Hiburan |
| Monumen Kapal Selam |  Budaya |
| Taman Pelangi | Taman Hiburan |
| Taman Keputran | Taman Hiburan |
| Taman Ekspresi Dan Perpustakaan | Taman Hiburan |
| Masjid Nasional Al-Akbar |  Tempat Ibadah |
| Keraton Surabaya |  Budaya |
| Waterpark Kenjeran Surabaya | Taman Hiburan |
| Monumen Bambu Runcing Surabaya | Budaya |
| House of Sampoerna | Budaya |

<br>Tabel 7. Hasil Rekomendasi dengan Pendekatan <i>Colaborative Filtering</i>
<br>Sample user yang diambil secara acak pernah memberi rating pada wisata Taman Kunang-Kunang, Taman Buah Surabaya dsb. maka hasil Top 10 rekomendasi untuk user tersebut yaitu yang berkategori sama seperti wisata yang diberi rating tinggi oleh user. Pendekatan ini juga memiliki kelemahan serta kelebihan yaitu agar sistem berfungsi dengan baik, maka sistem memerlukan banyak data feedback dari pengguna agara sistem tersebut berfungsi dengan baik.


## Evaluation
Proyek mechine learning Sistem Rekomendasi Wisata Surabaya ini menggunakan matriks evaluasi RMSE atau singkatan dari Root Mean Squared Error. RMSE merupakan metode pengukuran perbedaan dari nilai prediksi sebuah model untuk estimasi nilai yang diboservasi. RMSE merupakan hasil akar kuadrat dari MSE (Mean Square Error). untuk mengetahui keakuratan dari model bisa dilihat dari nilai RMSE, yaitu semakin kecil nilai RMSE semakin akurat model begitu sebaliknya semaik besar nilai RMSE semakin menjahui kata akurat model. untuk menghitung RMSE yaitu dengan cara mengurangkan nilai aktal dan nilai dari peramalan serta hasil tersebut dikuadratkan dan dijumlahkan, kemudian dibagi dengan n atau banyak data. hasil tersebut akan dihitung kembali untuk mencari nilai dari akar kuadrat. berikut merupakan gambaran rumus dari RMSE:<br>
![rumus](https://user-images.githubusercontent.com/108270264/191408231-3ebf5f21-f610-4df5-86f1-11fdb6d5f9ba.PNG)
<br>Gambar 8. Rumus RMSE
<br>Berdasarkan Gambar 7 yang berada pada Modeling terlihat nilai RMSE 0,2594 untuk train dan 0,3771 untuk error validasi. angka tersebut tergolong bagus untuk rekomendasi karena error yang dihasilkan nilainya cukup kecil.

<br>Selain menggunakan RMSE untuk matriks evaluasi, pada proyek ini juga menggunakan Precision Content-Based Learning, terlihat pada Tabel 6 diatas, yang merupakan hasil dari rekomendasi dengan pendekatan content-based learning. Dengan menggunakan sample test Taman Harmoni Keputih yang berkategorikan cagar alam, maka hasil yang didapatkan yaitu 4 dari 5 item memiliki similar atau kesamaan kategori yaitu cagar alam, tetapi 1 item tidak mempunyai similar yang sama. Jadi artinya precisio sistem tersebut sebesar 4/5 atau 80%. berikut merupakan formula dari precision sistem tersebut :<br>
![formula](https://user-images.githubusercontent.com/108270264/191466244-0c0ef12d-08b1-448b-ac8a-06e3ac7cc067.PNG)
<br>Gambar 9. Formula Precision Sistem


## Refrensi
[1] Virgiant, R. B., & Rochmawati, N. (2022). Implementasi Metode MOORA Untuk Penentuan Wisata Surabaya Terbaik Di Masa Pandemi COVID-19. Journal of Informatics and Computer Science (JINACS), 3(03), 267-277.<br>
[2] Aprianto, A. (2022). TA: Penerapan Algoritma Content-Based Filtering untuk Rekomendasi Destinasi Wisata pada Aplikasi Picnicker (Doctoral dissertation, Universitas Dinamika).

**---Ini adalah bagian akhir laporan---**
