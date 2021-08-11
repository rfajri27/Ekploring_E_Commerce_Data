# Exploring E-Commerce Data

Project ini merupakan salah satu modul project-based yang telah saya selesaikan di DQLab Academy. Project ini menggunakan dataset DQLab Store yang berisi transaksi bulan Januari 2019 hingga Mei 2020, dataset yang digunakan terdiri dari:
1.  user dataset, berisi detail data pengguna yang terdiri dari:
	* user_id : ID pengguna
	* nama_user : nama pengguna
	* kodepos : kodepos alamat utama dari pengguna
	* email : email dari pengguna
2. products dataset, berisi detail data dari produk yang dijual yang terdiri dari:
	* product_id : ID produk
	* desc_product : nama produk
	* category : kategori produk
	* base_price : harga asli dari produk
3. orders dataset, berisi transaksi pembelian dari pembeli ke penjual yang terdiri dari:
	* order_id : ID transaksi
	* seller_id : ID dari pengguna yang menjual
	* buyer_id : ID dari pengguna yang membeli
	* kodepos : kodepos alamat pengirimian transaksi (bisa beda dengan alamat utama)
	* subtotal : total harga barang sebelum diskon
	* discount : diskon dari transaksi
	* total : total harga barang setelah dikurangi diskon, yang dibayarkan pembeli
	* created_at : tanggal transaksi
	* paid_at : tanggal dibayar
	* delivery_at : tanggal pengiriman
4. order_details dataset, berisi detail barang yang dibeli saat transaksi yang terdiri dari:
	* order_detail_id : ID table ini
	* order_id : ID dari transaksi
	* product_id : ID dari masing-masing produk transaksi
	* price : harga barang masing-masing produk
	* quantity : jumlah barang yang dibeli dari masing-masing produk
---
## Berikut Merupakan Hasil Eksplorasi
### Jumlah Produk per Kategori 
Untuk mendapatkan jumlah produk per kategori, dilakukan **grouping** berdasarkan *category* lalu dihitung jumlah produk tiap kategori
| category | jumlah |
| ----------- | ----------- |
|Kebersihan Diri|          434
|Fresh Food|               134
|Makanan Instan|           133
|Pakaian Pria|              98
|Bahan Makanan|             98
|Minuman Ringan|            97
|Vitamin|                   49
|Pakaian Wanita|            49
|Makanan Kaleng|            22
|Aksesoris Wanita|          18
|Pakaian Muslim Wanita|      7
|Pakaian Tidur Wanita|       6

### Jumlah Transaksi per Bulan
Untuk memperoleh jumlah transaksi per bulan, dilakukan perubahan frekuensi data dari frekuensi harian (daily) menjadi frekuensi bulanan (monthly) dan menghitung jumlah order tiap bulan.
 | create_at | jumlah_transaksi |
 | ----------- | ----------- |
|2019-01|      117
|2019-02|      354
|2019-03|      668
|2019-04|      984
|2019-05|     1462
|2019-06|     1913
|2019-07|     2667
|2019-08|     3274
|2019-09|     4327
|2019-10|     5577
|2019-11|     7162
|2019-12|    10131
|2020-01|     5062
|2020-02|     5872
|2020-03|     7323
|2020-04|    7955
|2020-05|    10026

### Status Transaksi
* Jumlah transaksi yang tidak dibayar : 5046
* Jumlah transaksi yang tidak dikirim, baik yang sudah dibayar maupun belum dibayar : 9790
* Jumlah transaksi yang dikirim pada hari yang sama dengan tanggal bayar : 4588
* Jumlah transaksi yang sudah dibayar tapi tidak dikirim : 4744

### Status User
* Jumlah seluruh user : 17936
* Jumlah user yang pernah bertransaksi sebagai buyer:  17877
* Jumlah user yang pernah bertransaksi sebagai seller:  69
* Jumlah user yang pernah bertransaksi sebagai seller & buyyer:  69
* Jumlah user yang belum pernah bertransaksi:  59

#### Sepuluh Produk Terlaris
Untuk memperoleh 10 produk terlalris, dilakukan **grouping** berdasarkan *product_id* lalu dihitung jumlah *quantity* order.

|product_id|	quantity|	desc_product|	category|
| ----------- | ----------- | ----------- | ----------- |
|983|	6270|	Vaseline Lotion Healthy White Uv Lightening 20...|	Kebersihan Diri
|166|	6119|	RIDER CELANA ACTIVE WEAR 3IN1 R315B|	Pakaian Pria
|805|	5867|	Big Soft Drink Strawberry 3.1L|	Minuman Ringan
|532|	5849|	Formula Pasta Gigi + Sikat Gigi Sparkling Whit...|	Kebersihan Diri
|41|	5775|	LEGGING WORLD JEGGING LW 11|	Pakaian Wanita
|162|	5715|	RIDER CELANA SUPER RIDER R321B|	Pakaian Pria
|529|	5689|	Fit-U-Mask Masker Anak 5'S|	Kebersihan Diri
|594|	5674|	Blackmores Odourless Fish Oil 1000 200's|	Vitamin
|868|	5662|	Ultra Hand Sanitizer Spray 100Ml|	Kebersihan Diri
|253|	5541|	Ajinomoto Bumbu Nasi Goreng Sajiku Ayam 20G|	Bahan Makanan
