# Saudi-Arabia-Used-Cars-Prediction-Car-Price
Saudi Arabia Used Cars - Car Price Prediction

Dataset Source : https://www.kaggle.com/datasets/turkibintalib/saudi-arabia-used-cars-dataset

Contents Flowchart Program :
1. Business Problem Understanding
2. Data Understanding / EDA
3. Data Preprocessing
4. Modeling
5. Conclusion
6. Recommendation

1. Business Problem Understanding :
- Context
syarah company merupakan perusahaan yang bergerak dalam bidang jual beli mobil yang berlokasi Riyadh, Ar Riyad, Saudi Arabia dan merupakan bagian dari Taxi and Limousine Service Industry. syarah company menawarkan pengalaman yang berbeda dalam melakukan jual beli mobil melalui digital platform yaitu syarah.com. syarah.com sudah beroperasi sejak tahun 2015 dengan wilayah operasinya tersebar di saudi arabia dan telah melakukan penjualan senilai $835,725.

syarah.com menawarkan berbagai jenis mobil sesuai kebutuhan pelanggan. Pelanggan dapat memilih mobil sesuai keinginannya dengan mencocokkan spesifikasi yang diinginkan dan harga yang sesuai dengan yang dimiliki pelanggan. Pada web syarah.com telah disediakan banyak fitur dari setiap pilihan mobil seperti brand name, model, manufacturing year, origin, the color of the car, options, capacity of the engine, type of fuel, transmission type, the mileage that the car covered, region price, and negotiable. Tentu saja harga sebuah mobil akan ditentukan oleh berbagai fitur yang ada tersebut. Semakin tinggi spesifikasi seperti kondisi mobil sehat, usia mobil tergolong muda, fitur mobil sudah modern teknologi tentu saja akan semakin mahal. Penentuan harga mobil menjadi penting bagi perusahaan agar dapat menarik banyak perhatian pembeli, jangan sampai mobil dengan spesifikasi biasa saja dijual dengan harga yang mahal. Karena pada umumnya pelanggan dengan kategori kelas menengah hingga bawah yang dilihat pertama yaitu harganya baru spesifikasi menyesuaikan, berbeda dengan kelas atas yang melihat mobil dari spesifikasi dan subjektif kesukaan baru harga menyesuaikan. Penetapan harga ini menjadi sangat krusial bagi perusahaan karena akan berdampak langsung pada pendapatan perusahaan kedepannya.

- Problem Statement
Salah satu permasalahan yang dapat berdampak langsung pada pendapatan perusahaan yaitu pemecahan masalah untuk dapat memiliki model bisnis dapat memberikan dampak positif terhadap kinerja keuangan perusahaan serta memberikan pengalaman yang baik terhadap pelanggan yang ingin membeli mobil sesuai kebutuhannya.

Dengan banyaknya pilihan mobil dengan berbagai spesifikasi dan kondisi, diharapkan perusahaan mampu memiliki model bisnis yang dapat menentukan harga mobil yang kompetitif di pasaran agar banyak pelanggan yang tertarik untuk membeli mobil pada perusahaan ini. Selain itu pelanggan juga diberikan kemudahan dalam mencari pilihan mobil yang diinginkan sesuai spesifikasi dan harganya. Kemudahan dan harga yang kompetitif inilah yang dapat meningkatkan jumlah pelanggan dan tentu saja dapat meningkatkan pendapatan perusahaan.

- Goals
Berdasarkan permasalahan tersebut, syarah company harus memiliki tools yang dapat memprediksi harga mobil sesuai spesifikasi yang diinginkan pelanggan dan membantu pelanggan untuk dapat menemukan mobil impian mereka sesuai dengan spesifikasi dan harga yang sesuai dengan kebutuhan pelanggan. Variabel - variabel yang dapat berpengaruh pada harga mobil yaitu seperti merk mobil, tipe mobil, gear type, asal mobil, tahun mobil, jarak tempuh, hingga engine size diharapkan dapat memberikan akurasi yang baik dalam menentukan harga mobil, yang mana dapat memberikan harga yang kompetitif di pasaran yang terjangkau bagi pelanggan namun tetap menguntungkan bagi perusahaan.

- Analytic Approach
Yang perlu dilakukan yaitu membuat prediksi berdasarkan analisis dari data yang ada dengan menemukan pola dari fitur - fitur yang ada pada data, yang membedakan suatu mobil dengan mobil lainnya. Selanjutnya akan dibangun model regresi untk membantu perusahaan sebagai tools untuk memprediksi harga mobil sesuai spesifikasi yang ada, sehingga dapat menguntungkan perusahaan dalam menjual mobil dan pelanggan dalam mencari mobil sesuai kebutuhan.

- Metric Evaluation
Evaluasi metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana :
1. RMSE adalah nilai rataan akar kuadrat dari error,
2. MAE adalah rataan nilai absolut dari error,
3. MAPE adalah rataan persentase error yang dihasilkan oleh model regresi.

2. Data Understanding
![image](https://user-images.githubusercontent.com/81374865/171561454-3ebc73b2-80d0-4c76-9e8b-d89bca9a1535.png)

3. Data Preprocessing
Pada tahap ini, akan dilakukan cleaning pada data untuk kebutuhan proses analisis selanjutnya. Beberapa hal yang perlu dilakukan adalah:
- Melakukan pengecekan terhadap duplikat data, missing value, dan drop fitur yang tidak memiliki relevansi terhadap permasalahan yang sedang dihadapi.
- Melakukan treatment terhadap missing value jika ada. Bisa dengan cara men-drop fiturnya jika memang tidak dibutuhkan atau bisa juga dengan mengimputasi dengan nilai yang paling masuk akal berdasarkan kasusnya.

4. Modeling
- Encoding
Agar dapat menggunakan semua fitur yang dipilih, maka fitur-fitur kategorikal harus diubah menjadi fitur numerikal menggunakan encoding. Kali ini akan diggunakan ColumnTransformer untuk dapat mengubah tipe datanya karena terdapat 2 metode encoding yang digunakan yaitu onehot encoding dan binary encoding, yang mana nanti dapat output dari transformer akan diaplikasikan pada model menggunakan pipeline.

onehot encoding digunakan untuk fitur 'Options', 'Origin' dan 'Gear_Type'. onehot encoding digunakan karena data yang berisi data ketegorik harus dirubah kedalam data numerik agar dapat digunakan. Dengan onehot encodig data dalam suatu fitur akan dikonversi dengan menambahkan kolom dengan jumlah kolom sesuai dengan jumlah variasi nilai data, selanjutnya akan diisikan nilai dengan angka 0 dan 1 sesuai dengan nilai pada datanya. onehot encoding juga lebih baik digunakan untuk data yang berisi sedikit variasi nilai pada datanya sehingga tidak menambah jumlah kolom terlalu banyak dalam data.

binary encoding digunakan untuk fitur 'Type', 'Region' dan 'Make'. binary encoding digunakan karena dalam fitur tersebut berisikan banyak variasi nilai data sehingga akan sulit jika menggunakan onehot encoding. Dengan binary encoding, outputnya akan lebih ringkas karena akan dikonversi menjadi format angka biner.

- Model : Benchmark
Pada model benchmark kali ini akan dibandingkan hasil performa model dengan menggunakan RMSE, MAE dan MAPE. Penggunaan ketiga parameter tersebut dikarenakan label y memiliki nilai yang cukup beragam sehingga MAE dan MAPE lebih baik digunakan dibanding MSE. Selain itu MAE dan MAPE juga tidak sensitif terhadap outlier sehingga lebih cocok digunakan untuk dataset ini.

RMSE adalah metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. Keakuratan metode estimasi kesalahan pengukuran ditandai dengan adanya nilai RMSE yang kecil. Dengan didapatkannya RMSE dengan nilai yang kecil diharapkan model dapat melakukan prediksi harga mobil secara akurat dengan error antara nilai prediksi dengan nilai seharusnya yang sangat kecil.
MAE adalah rata-rata selisih mutlak nilai sebenarnya dengan nilai prediksi. MAE menunjukkan nilai kesalahan atau perbedaan nilai sebenarnya dengan nilai prediksi. Semakin kecil nilai MAE, semakin baik model tersebut dalam melakukan prediksi. Dengan didapatkannya MAE dengan nilai yang kecil diharapkan model dapat melakukan prediksi harga mobil dengan baik dengan nilai error mutlak antara nilai prediksi dengan nilai seharusnya yang sangat kecil.
MAPE adalah presentase atas nilai error mutlak / MAE. MAPE mengukur presentase error mutlak MAE dengan nilai rentang datanya. Dengan MAPE nilai error dapat terbaca dengan lebih mudah apakah besar atau kecil, karena besar kecilnya nilai error tergantung dari rentang datanya. Semakin kecil nilai presentasi kesalahan (percentage error) pada MAPE maka semakin akurat hasil prediksi tersebut. Dengan didapatkannya MAE dengan nilai yang kecil diharapkan model dapat melakukan prediksi harga mobil dengan baik dengan nilai presentase error mutlak antara nilai prediksi dengan nilai seharusnya yang sangat kecil.

Model yang akan dibandingkan yaitu terdapat 5 model yaitu:
1. Linear regression
2. KNN
3. Decision Tree
4. Random Forest
5. XGBoost

Dari kelima model tersebut akan dipilih 2 model terbaik yang memberikan nilai RMSE, MAE dan MAPE yang kecil dan standar deviasi dari RMSE, MAE dan MAPE yang kecil juga. Selain membandingkan model ML yang akan digunakan, akan dibandingkan juga metode dari scaling yang akan digunakan yang mampu memberikan kinerja yang paling baik pada RMSE, MAE dan MAPE. Metode scaling yang akan dibandingkan yaitu:
1. Standard Scaler
2. Min Max Scaler
3. Robust Scaler

Berdasarkan hasil prediksi pada test set, XGBoostdan Min Max Scaler memberikan performa masih yang paling baik dengan score RMSE, MAE dan MAPE yang lebih rendah dibanding model yang lain.

Boosting adalah salah satu algoritma pembentukan model prediktif dengan ide utamanya menggabungkan beberapa model sederhana (weak learner) agar menjadi suatu model yang kuat/bertenaga (strong learner) secara iteratif. XGBoost merupakan pengembangan algoritma Gradient Boosting Machine (GBM) dengan beberapa fitur tambahan yang berguna dalam mempercepat proses komputasi dan mencegah terjadinya overftting. Proses pemodelan dilakukan secara iteratif dan sequential. Kunci kecepatan komputasi XGBoost terletak pada optimasi penggunaan memori dan cache di komputer sehingga dapat bekerja secara efsien, meskipun berhadapan dengan data berukuran besar. Di dalam XGBoost juga terdapat pencegahan kejadian overftting yang ilakukan dengan teknik regularisasi dengan cara memberikan komponen penalti pada fungsi kerugian sehingga model akan terhindar dari model yang terlalu kompleks, tetapi berkinerja buruk dalam memprediksi kejadian dengan data baru.

- Hyperparameter Tuning
Karena model yang terpilih yaitu XGBoost yang memberikan performa paling baik, maka selanjutnya kita akan menggunakan model XGBoost ini sebagai model akhir. Pada tahap ini, kita akan melakukan hyperparameter tuning pada model XGBoost dengan harapan dapat meningkatkan performa model.

Pada XGBoost terdapat 3 kategori parameter yang bisa dituning untuk meningkatkan kinerja model, diantaranya yaitu :
1. General Parameter : booster, silent, nthread
2. Booster Parameter : eta, min_child_weight, max_depth, max_leaf_nodes, gamma, max_delta_step, subsample, colsample_bytree, colsample_bylevel, lambda, alpha, scale_pos_weight
3. Learning Task Parameter : objective, eval_metric_seed

Namun pada tahap ini akan dilakukan hyperparamater tuning untuk beberapa variabel dari ketiga parameter tersebut, yaitu:
1. learning rate
2. estimator of tuning tree (max_depth, min_child_weight, gamma, subsample, colsample_bytree, scale_pos_weight)
3. regularization parameters

5. Conclusion
Berdasarkan pemodelan yang sudah dilakukan, fitur 'Engine_Size' dan 'Year' menjadi fitur yang paling berpengaruh terhadap 'Price'.

Metrik evaluasi yang digunakan pada model adalah nilai RMSE, MAE & MAPE. Jika ditinjau dari nilai RMSE yang dihasilkan oleh model setelah dilakukan hyperparameter tuning, yaitu sebesar 16.730,79 dari rentang data 'Price' dengan nilai minimum 11.000, nilai maksimum 181.250, delta nilai price (nilai maksimum - nilai minimum) 170.250, maka presentase RMSE terhadap rentang data sebesar 9,8%. Sedangkan jika dilihat dari nilai MAPE didapatkan performa dengan nilai 22% dimana model dapat dikategorikan kedalam 'reasonable forecasting'.

Dapat disimpulkan bahwa bila nanti model yang ini digunakan untuk memperkirakan harga mobil pada rentang nilai seperti yang dilatih terhadap model (nilai limitasi model : min_price = 11.000 dan max_price = 170.250), maka perkiraan harga rata-rata akan meleset kurang lebih sebesar 16.730,79 atau sebesar 9,8% dari harga yang mungkin seharusnya. Tetapi tidak menutup kemungkinan juga prediksinya meleset lebih jauh karena bias yang dihasilkan model masih cukup tinggi bila dilihat dari visualisasi antara harga aktual dan prediksi. Bias yang dihasilkan oleh model ini dikarenakan oleh kurangnya fitur pada dataset yang bisa lebih merepresentasikan aspek kondisi mobil seperti apakah pernah terjadi kendala pada mesin (turun mesin), apakah pernah mengalami kecelakaan, jika iya seberapa parah pernah mengalami kecelakaan, garansi mobil, dll.

Dengan adanya limitasi rentang nilai dalam model yang dilatih maka model dapat dipercaya jika rentang nilai mobil yang akan diperdiksi masuk dalam range limitasi nilai tersebut dan terdapat nilai dari fitur yang digunakan dalam model yang telah dilatih (tidak ada data missing value) seperti fitur engine_size, mileage, year, merk mobil, dll sesuai clean dataset yang digunakan dalam model. Jika terdapat nilai rentang mobil diluar dari range limitasi nilai dan terdapat missing value pada beberapa fitur yang telah dilatih dalam model maka hasil prediksi model dapat dikatakan tidak dapat dipercaya.

6. Recommendation
Hal-hal yang dapat dilakukan untuk mengembangkan model agar lebih baik lagi, seperti:
1. Melakukan pengecekan dan pengelompokkan atas fitur - fitur mana saja yang memberikan error yang tinggi terhadap target 'Price' sehingga kita dapat melakukan feature engineering yang lebih baik terlebih dahulu terhadap fitur tersebut agar dapat meningkatkan performa model.
2. Melakukan penambahan data dari yang ada saat ini sejumlah 3.429 menjadi lebih banyak atau sekitar > 5.000 sesuai dataset awal yang terdapat missing value dan outlier. Sehingga model mendapatkan banyak refrensi data yang dipelajari. Penambahan data dapat dilakukan dengan melakukan update data terbaru atau memperbaiki data mentah yang terdapat missing value.
3. Jika memungkinkan, penambahan fitur yang lebih korelatif dengan target ('Price'), seperti kondisi mobil, garansi mobil dan after sales service.
4. Jika ada penambahan banyak data, dapat dicoba dengan menggunakan model yang lebih kompleks, seperti recursive neural networks (RNN).
5. Selanjutnya kedepan dari model ini dapat dijadikan sebagai dasar pengembangan untuk model lainnya seperti model untuk mengklasifikasikan jenis pelanggan terhadap spesifikasi dan harga mobil. Model tersebut bermanfaat sebagai dasar perencanaan biaya marketing strategy agar dapat optimal terhadap peningkatan pendapatan perusahaan dari jual - beli mobil.
