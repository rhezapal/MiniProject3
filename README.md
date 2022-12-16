# MiniProject3 - Predict Customer Personality to boost marketing campaign by using Machine Learning
Rakamin Academy

## Latar Belakang
“Sebuah perusahaan dapat berkembang dengan pesat saat mengetahui perilaku customer personality nya, sehingga dapat memberikan layanan serta manfaat lebih baik kepada customers yang berpotensi menjadi loyal customers. Dengan mengolah data historical marketing campaign guna menaikkan performa dan menyasar customers yang tepat agar dapat bertransaksi di platform perusahaan, dari insight data tersebut fokus kita adalah membuat sebuah model prediksi kluster sehingga memudahkan perusahaan dalam membuat keputusan ”

## Pertanyaan Riset
Target customer seperti apa yang memerlukan marketing campaign ?

## Tujuan
Mengetahui target customer, sehingga marketing campaign menjadi tepat sasaran.

## Exploratory Data Analysis
- Dataset : marketing_campaign_data.csv.
- Dataset terdiri dari 29 kolom, dan 2240 baris.

## Feature Engineering for Data Visualisation
- Num_Transaction = Dengan menambahkan kolom NumDealsPurchases, NumWebPurchases, NumCatalogPurchases, dan NumStorePurchases
- Conversion_Rate = Membagi Num_Transaction dengan NumWebVisitsMonth
- Umur = Mengurangi 2022 dengan Year_Birth
- Kategori Usia = Mengelompokkan Usia <= 11 tahun adalah Anak,<=25 adalah Remaja, <=35 adalah Dewasa Awal, <=45 adalah Dewasa Akhir, <=55 tahun adalah Lansia Awal, <=65 tahun adalah Lansia Akhir, >65 adalah Manula
- Jumlah_anak = Menambahkan Kidhome dan Teenhome
- Parent = Mengelompokkan berdasarkan Jumlah Anak, 0 : bukan parent, >0 adalah parent
- Accepted Campaign = Dengan menambahkan kolom AcceptedCmp1, AcceptedCmp2, AcceptedCmp3, AcceptedCmp4, dan AcceptedCmp5
- Income = Mengelompokkan Income, <=1.000.000 (Low Income), <=3.000.000 (Low-Middle), <=5.000.000 (Middle Income, <=7.000.000 (Middle-High), >7.000.000 High
- Transaction Amount = Menambahkan MntCoke, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, dan MntGoldProds
- Kategori Transaction = Mengelompokkan Income, <=500.000 (Low Transaction), <=1.000.000 (Middle Transaction), <=1.500.000 (High Transaction), dan >1.500.000 (Very High Transaction)

## Data Visualisation
- Hubungan Umur dan Conversion rate : Tidak ditemukan perbedaan Conversion rate yang siginifikan antar Kategori Usia.
<img width="450" alt="image" src="https://user-images.githubusercontent.com/114345988/208020065-6abaf091-2440-4659-a58b-3325863691b2.png">

- Hubungan Kategori Income dan Conversion rate : Untuk Kategori Middle High Income (3.000.001-5.000.000), memiliki Conversion Rate yang lebih tinggi diantara ketiga kategori lainnya.
<img width="450" alt="image" src="https://user-images.githubusercontent.com/114345988/208020258-8c045d7e-2eab-4e3f-ad2c-243702b5ed13.png">

- Hubungan  Kategori Jumlah Transaksi dan Conversion Rate
Untuk Kategori Middle Transaction, High Transaction, dan Very High Transaction (>1.000.000), memiliki Conversion Rate yang tidak berbeda signifikan. 
<img width="450" alt="image" src="https://user-images.githubusercontent.com/114345988/208020326-6371899c-0d73-4810-98b7-c09c2d94dc2c.png">

## Data Preprocessing
### Handle Null Value :
- Income dan Conversion Rate diisi dengan nilai Modus.
### Data Duplicated : 
- tidak ada
### Handle Outlier :
- Khusus untuk data numerikal
- Jumlah baris sebelum memfilter outlier: 2240
- Jumlah baris setelah memfilter outlier: 1907
### Label Encoding :
- Label Encoding : Education
- One Hot Encoding : Cat_Usia (Kategori Usia),Marital_Status, Cat_Income (Kategori Income), Cat_Transaction (Kategori Transaksi
### Dropping Value : 
- ada beberapa fitur yang didrop
- 'Unnamed: 0','ID','Education','Marital_Status','Kidhome','Teenhome','Dt_Customer','Recency',
- 'MntCoke','MntFruits','MntMeatProducts','MntFishProducts','MntSweetProducts','MntGoldProds',
- 'NumDealsPurchases','NumWebPurchases','NumCatalogPurchases','NumStorePurchases','NumWebVisitsMonth',
- 'AcceptedCmp3','AcceptedCmp4','AcceptedCmp5','AcceptedCmp1','AcceptedCmp2','Complain','Z_CostContact','Z_Revenue','Response',
- 'Cat_Usia','Cat_Transaction','Cat_Income'
### Log Tranformasion :
- Fitur Year Birth, Income, Umur, dan Transaction_tot perlu dilakukan log transformasi
### Standarisasi : 
- perlu dilakukan

## Data Modelling
- Visualisasi Elbow Method menggunakan K-Means Clustering
- Evaluasi KMeans

## Kesimpulan :
- Usia : dari data diatas, customer kebanyakan diusia dewasa akhir sampai lansia, sehingga tidak ada perbedaan yang bermakna.
Dari clustering, perbedaan yang jelas adalah pembagian segmentasi jumlah nominal transaksi.

- Rekomendasi Bisnis :
- Untuk Cluster 2 : Jumlah transaksi minimal dibandingkan dua jenis cluster lainnya,  dapat dipertimbangkan untuk menambah jenis promo, sehingga meningkatkan jumlah transaksi, perlu adanya peningkatan kunjungan ke Website. Promo kunjungan perlu dipertimbangkan ada. Perlu adanya Program Loyalty dengan indikator jumlah kunjungan, semakin sering customer datang, akan mendapatkan voucher diskon (contoh)
- Untuk Cluster 1 dan 3, Jumlah kunjungan sudah cukup tinggi, dan nominal transaksi juga tinggi, perlu adanya maintenance agar, tidak terjadi churn. Bisa menggunakan voucher tambahan diskon untuk minimal pembelanjaan tertentu. 

Noted : Jupyter Notebook dan Slide Presentasi, berbeda, dikarenakan adanya penambahan  handle outlier dan log transformation sebelum encoding pada jupyter notebook









