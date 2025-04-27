# Laporan Proyek Machine Learning - Mu'azah Al'Adawiyah

## Project Overview

Kanker merupakan salah satu penyakit paling mematikan di dunia, dengan angka kematian yang terus meningkat setiap tahunnya. Menurut Organisasi Kesehatan Dunia (WHO), sekitar 10 juta kematian terjadi akibat kanker pada tahun 2020, dan jumlah ini diperkirakan akan terus meningkat seiring bertambahnya populasi dan berbagai faktor risiko seperti gaya hidup tidak sehat dan polusi (World Health Organization, 2023). Salah satu tantangan besar dalam penanganan kanker adalah banyaknya kasus yang terdiagnosis pada tahap lanjut, ketika pengobatan menjadi kurang efektif dan peluang bertahan hidup menurun secara signifikan (Bray et al., 2021).

Data pasien kanker global dari tahun 2015 hingga 2024 menunjukkan tren penting dalam pemahaman serta penanganan penyakit ini. Dataset tersebut disusun untuk mensimulasikan berbagai faktor yang memengaruhi diagnosis, pengobatan, dan kelangsungan hidup pasien kanker. Melihat tren peningkatan kasus secara global, dibutuhkan sistem yang efektif untuk mengumpulkan, menganalisis, dan melaporkan data secara akurat. Deteksi sel kanker secara dini menjadi sangat penting untuk menurunkan angka kematian. Diagnosis yang dilakukan tepat waktu memungkinkan pasien menerima perawatan lebih awal, yang dapat meningkatkan kemungkinan bertahan hidup (Bo Zhang et al., 2023).

Salah satu pendekatan yang umum digunakan dalam studi data medis adalah teknik klasifikasi, yang memungkinkan pengelompokan data berdasarkan karakteristik tertentu. Dalam konteks ini, Machine Learning (ML) menawarkan potensi besar untuk meningkatkan akurasi diagnosis kanker, sekaligus mempercepat dan mempermudah prosesnya (Cahyo Prianto et al., 2023). Proyek ini bertujuan mengembangkan sistem analisis data pasien kanker dengan menerapkan teknik ML seperti Support Vector Machine (SVM), Logistic Regression, Random Forest, dan Decision Tree. Metode ini mempertimbangkan faktor risiko seperti genetik, polusi udara, alkohol, merokok, dan obesitas. dengan harapan dapat membantu dalam deteksi dini, pengelolaan kanker yang lebih baik, serta memberikan informasi akurat dan relevan bagi peneliti, dokter, dan pembuat kebijakan.

## Business Understanding

Dari latar belakang yang telah dipaparkan di atas, berikut ini merupakan masalah dan tujuan yang dihasilkan di atas:

### Problem Statements

1. Banyak kasus kanker yang terlambat terdiagnosis, sehingga pengobatan menjadi tidak efektif dan menurunkan tingkat kelangsungan hidup pasien. <br>
2. Belum adanya sistem analisis data pasien kanker yang terintegrasi, yang dapat memberikan wawasan mendalam tentang tren dan pola diagnosis, pengobatan, dan kelangsungan hidup pasien secara global. <br>
3. Kurangnya prediksi berbasis data terhadap faktor risiko utama kanker seperti genetik, merokok, obesitas, alkohol, dan polusi, yang dapat membantu dalam deteksi dini.<br>

### Goals

1. Mengembangkan model prediksi untuk mendeteksi potensi kanker sejak dini berdasarkan fitur pasien dan faktor risiko yang tersedia dalam dataset. <br>
2. Membangun sistem analisis data untuk memahami tren dan pola pasien kanker secara global antara tahun 2015–2024. <br>
3. Memberikan insight berbasis data yang dapat dimanfaatkan oleh tenaga medis, peneliti, dan pembuat kebijakan dalam mendukung pengambilan keputusan dan strategi pencegahan. <br>

### Solution statements
1. Membangun beberapa model klasifikasi seperti Logistic Regression, Random Forest, Decision Tree, dan XGBoost untuk memprediksi apakah pasien memiliki risiko kanker. <br>
2. Melakukan evaluasi model menggunakan metrik seperti F1-score, Recall, dan Confusion Matrix, guna memilih model terbaik yang memiliki performa paling akurat dalam mendeteksi pasien berisiko. <br>
3. Melakukan analisis eksploratif (EDA) terhadap tren tahunan, distribusi jenis kanker, demografi, dan keberhasilan pengobatan dari dataset agar bisa dihubungkan dengan hasil klasifikasi. <br>

## Data Understanding
Kumpulan data ini berisi data pasien kanker global yang dilaporkan dari tahun 2015 hingga 2024, yang dirancang untuk mensimulasikan faktor-faktor utama yang memengaruhi diagnosis, pengobatan, dan kelangsungan hidup kanker.

Dataset digunakan dari Kaggle: [global_cancer_patients_2015_2024](https://www.kaggle.com/datasets/zahidmughal2343/global-cancer-patients-2015-2024/data)

Berikut ini merupakan informasi data untuk menunjang proyek pada tabel di bawah ini :

Informasi Dataset:
RangeIndex: 50000 entries, 0 to 49999
Data columns (total 15 columns):
|  #  | Column                | Non-Null Count |   Dtype |
|:---:|-----------------------|---------------:|--------:|
|  0  | Patient_ID            | 50000 non-null |  object |
|  1  | Age                   | 50000 non-null |   int64 |
|  2  | Gender                | 50000 non-null |  object |
|  3  | Country_Region        | 50000 non-null |  object |
|  4  | Year                  | 50000 non-null |   int64 |
|  5  | Genetic_Risk          | 50000 non-null | float64 |
|  6  | Air_Pollution         | 50000 non-null | float64 |
|  7  | Alcohol_Use           | 50000 non-null | float64 |
|  8  | Smoking               | 50000 non-null | float64 |
|  9  | Obesity_Level         | 50000 non-null | float64 |
|  10 | Cancer_Type           | 50000 non-null | object  |
|  11 | Cancer_Stage          | 50000 non-null | object  |
|  12 | Treatment_Cost_USD    | 50000 non-null | float64 |
|  13 | Survival_Years        | 50000 non-null | float64 |
|  14 | Target_Severity_Score | 50000 non-null | float64 |
dtypes: float64(8), int64(2), object(5)

Melihat hasil informasi dataset terdapat 14 kolom di dalam dataset namun saya menghapus kolom id untuk memudahkan saya dalam melakukan proses analisis. Jumlah dari data disetiap kolom sebanyak 50000 data/baris. Tidak ada missing value maupun data duplikat.

Tabel yang diambil pada Global Cancer Patients Dataset adalah sebagai berikut:
- Age             : Usia pasien saat di diagnosis kanker. <br>
- Gender          : Jenis kelamin pasien (Male atau Female). <br>
- Country Region  : Negara tempat pasien berasal atau dirawat. <br>
- Tahun           : Tahun pasien saat di diagnosis kanker. <br>
- Faktor Resiko   : <br>
  - Genetic Risk  : Adanya faktor risiko genetik pada pasien (Yes/No). <br>
  - Air Pollution : Tingkat polusi udara di lingkungan tempat tinggal pasien (Low, Medium, High). <br>
  - Alcohol Use   : Riwayat konsumsi alkohol pasien (Yes/No). <br>
  - Smoking       : Riwayat merokok pasien (Yes/No). <br>
  - Obesity Level : Status obesitas pasien berdasarkan diagnosis medis (Yes/No). <br>
- Cancer Type     : Jenis kanker yang diderita pasien (contoh: Breast Cancer, Lung Cancer, Leukemia, dll). <br>
- Cancer Stage    : Stadium kanker saat pasien terdiagnosis (Stage I, II, III, IV). <br>
- Treatment Cost  : Biaya pengobatan yang dikeluarkan pasien (dalam satuan dolar). <br>
- Survival Years  : tahun kelangsungan hidup pasien bertahan lama. <br>
- Target Severity Score : Skor tingkat keparahan kondisi pasien kanker. <br>

Selanjutnya statistik data dari data yang numerik ditampilkan pada tabel di bawah ini!
Statistik Deskriptif:
|       |          Age |         Year | Genetic_Risk | Air_Pollution |  Alcohol_Use |      Smoking | Obesity_Level | Treatment_Cost_USD | Survival_Years | Target_Severity_Score |
|------:|-------------:|-------------:|-------------:|--------------:|-------------:|-------------:|--------------:|-------------------:|---------------:|----------------------:|
| count | 50000.000000 | 50000.000000 | 50000.000000 |  50000.000000 | 50000.000000 | 50000.000000 |  50000.000000 |       50000.000000 |   50000.000000 |          50000.000000 |
|  mean |    54.421540 |  2019.480520 |     5.001698 |      5.010126 |     5.010880 |     4.989826 |      4.991176 |       52467.298239 |       5.006462 |              4.951207 |
|  std  |    20.224451 |     2.871485 |     2.885773 |      2.888399 |     2.888769 |     2.881579 |      2.894504 |       27363.229379 |       2.883335 |              1.199677 |
|  min  |    20.000000 |  2015.000000 |     0.000000 |      0.000000 |     0.000000 |     0.000000 |      0.000000 |        5000.050000 |       0.000000 |              0.900000 |
|  25%  |    37.000000 |  2017.000000 |     2.500000 |      2.500000 |     2.500000 |     2.500000 |      2.500000 |       28686.225000 |       2.500000 |              4.120000 |
|  50%  |    54.000000 |  2019.000000 |     5.000000 |      5.000000 |     5.000000 |     5.000000 |      5.000000 |       52474.310000 |       5.000000 |              4.950000 |
|  75%  |    72.000000 |  2022.000000 |     7.500000 |      7.500000 |     7.500000 |     7.500000 |      7.500000 |       76232.720000 |       7.500000 |              5.780000 |
|  max  |    89.000000 |  2024.000000 |    10.000000 |     10.000000 |    10.000000 |    10.000000 |     10.000000 |       99999.840000 |      10.000000 |              9.160000 |

## Exploratory Data Analysis.
Beberapa tahapan EDA juga dilakukan:
- Menampilkan distribusi kelas target <br>
  1. Distribusi Kelas Kategori <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/kategori.png) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  2. Distribusi Kelas Numerik <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/numerik.png) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari age, year, genetic_risk, air_pollution, alcohol_use, smoking, obesity_level, treatment_cost, Survival_years, Target_severity_sscore. <br>
  3. proporsi jenis kanker <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/jeniskanker.png) <br>
     
     Pada gambar diatas menunjukkan beberapa jumlah persentase beberapa type kanker yang di diagnosis pasien terdapat type kanker yang terdiri dari lung, breast, cervical, skin, liver, leukemia, prostate, colon. Persentase yang ditampilkan jumlahnya sama rata yaitu 12% tetapi yang paling tinggi persentase komanya yaitu jenis kanker colon. <br>
  4. Jumlah Kasus Kanker tiap tahun <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/kasuskanker.png) <br>

     Pada gambar diatas menunjukkan hasil perkembangan kasus penyakit kanker tiap tahun. Dari  kita liat grafiknya menunjukkan bahwa kasus penyakit kanker secara global tiap tahunnya berubah-ubah dari waktu ke waktu. Dari mulai tahun 2015 sebanyak >= 5000 naik di tahun 2016 sebanyak >= 5050an kasus dan pada tahun 2024 mengalami sedikit penurunan sebanyak 5000 kasus. <br>
  5. Kasus kanker perwilayah <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/wilayah%20kanker.png) <br>

     Pada gambar diatas menunjukkan beberapa jumlah persentase beberapa kasus kanker perwilayah yang di diagnosis pasien terdapat negara china, pakistan, brazil, rusia, jerman, india, usa, uk, australia, dan canada. Dari hasil diagram lingkaran tersebut persentase yang ditampilkan jumlahnya sama rata yaitu 10% kecuali untuk negara canada, china, dan pakistan yang menampilkan persentase sebanyak 9%. <br>
  6. Top 10 Negara jumlah penderita kanker tertinggi <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/top10negara.png) <br>
   
     Pada gambar diatas menunjukkan bahwa ada 10 negara yang memiliki jumlah penderita kanker tertinggi yaitu australia, uk, usa, india, jerman, rusia, brazil, pakistan, china dan canada. Kasus tertinggi di peroleh dari negara australia dan negara yang sedikit kasusnya yaitu canada. <br>
  7. Jenis kanker di 5 negara penderita terbanyak <br>
     ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/tipekanker.png) <br>
     
     Pada gambar diatas menunjukkan bahwa ada 5 negara yang memiliki tipe kanker yang memiliki pasien terbanyak yaitu urutan pertama ada UK, dimana tipe kanker paling tinggi yaitu kanker prostate, yang kedua negara jerman tipe kanker yang paling tinggi yaitu kanker leukemia, dan untuk urutan terakhir negara australia yang memiliki tipe kanker dengan pasien terbanyak yaitu kanker liver. <br>
     

- korelasi antar fitur <br>
  ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/heatmap.png) <br>
     
  Pada gambar diatas menunjukkan hubungan atau korelasi antar fitur dalam dataset. Korelasi diukur dalam rentang -1 hingga 1. Terdapat beberapa warna area yaitu :
  - Area merah menunjukkan korelasi yang sangat kuat (mendekati nilai 1.0) pada area ini memiliki fitur korelasi antar dirinya sendiri sehingga wajar selalu memiliki korelasi sempurna. <br>
  - Area biru menunjukkan korelasi negatif moderat sekitar -0.4 yang artinya salah satu fitur naik, maka fitur lain turun seperti korelasi antara target_severity_score dan treatment_cost. <br>
  - Area Coklat menunjukkan korelasi positif lemah sampai sedang (antara 0.3 sampai 0.7). Misalnya, hubungan target_severity_score dengan generic, pollution, dan alcohol berada di rentang ini, yang berarti ada kecenderungan naik bersama, tetapi tidak terlalu kuat. <br>
  - Area abu-abu biru langit mewakili korelasi sangat lemah (sekitar 0.2 atau lebih kecil), menunjukkan hubungan yang hampir tidak signifikan antara fitur-fitur tersebut <br>

- Visualisasi outlier <br>
  ![Kategori](https://github.com/muazahalwyh/Submission_LaskarAI/blob/submission4_1/image/outlier.png) <br>
   
  Pada gambar diatas menunjukkan titik data yang berada jauh dari distribusi normal data lainnya. Mereka bisa mempengaruhi analisis statistik atau model.  <br> 

## Data Preparation
Tahapan yang dilakukan:
1. Menghapus data duplikat dan missing value. Namun, pada dataset ini setelah di cek kedua nya tidak memilikinya sehingga tidak perlu melakukan nya berulang lagi. <br>
2. Menyalin data asli ke dataframe baru (`new_df`).<br>
3. Konversi `Target_Severity_Score` menjadi Kelas (Menggunakan Fungsi `convert_to_class`), dimana target sebelumnya berbentuk numerik diubah menjadi kategori dengan fungsi `convert_to_class`. <br>
4. Menambahkan Kolom Kelas pada DataFrame, Kolom baru `Severity_Class` ditambahkan ke `new_df`. <br>
5. Memisahkan fitur ke dalam dua kategori: numerik (features) dan kategorikal (categorical_features). <br>
6. Pemisahan data menjadi fitur x berisi (input data) dan fitur y berisi target (output data yang ingin diprediksi, yaitu Severity_Class). <br>
7. Penerapan label encoding pada kelas target (y) bersifat kategorikal (`Rendah, sedang, tinggi`) menjadi (`0,1,2`) <br>
8. Melakukan Train-test split dengan proporsi 80% untuk training dan 20% untuk testing, menggunakan train_test_split dari sklearn. <br>
9. Penggunaan ColumnTransformer untuk Preprocessing. Pada fitur numerik di biarkan tidak ada perubahan. Sedangkan fitur kategorikal diubah dengan `One-Hot Encoding` menggunakan `OneHotEncoder`. <br>
10. Transformasi Data (Encoding untuk fitur kategorikal dan Scaling dilakukan pada seluruh data numerik menggunakan StandardScaler). <br>
11. Mengubah Data ke Format yang Dapat Digunakan untuk Model yaitu menjadi menjadi data pelatihan (X_train_encoded_scaled) dan data pengujian (X_test_encoded_scaled). <br>


Alasan dilakukan:
1. Duplikasi dan missing value bisa mengganggu pelatihan model. <br>
2. Menyalin dataframe dilakukan agar tidak mengubah data asli (`df`), dan untuk memudahkan modifikasi atau preprocessing lebih lanjut tanpa merusak dataset yang digunakan di tahap lain. <br>
3. Menyederhanakan masalah yang akan diselesaikan oleh model (klasifikasi biner atau multi-kelas). <br>
4. Kolom baru ini berfungsi sebagai target variabel untuk klasifikasi. Memisahkan antara fitur dan target di tahap awal memungkinkan proses training model menjadi lebih jelas dan terstruktur. <br>
5. Fitur numerik yang diproses langsung atau di-scale, sedangkan fitur kategorikal harus diubah menjadi format yang dapat dimengerti oleh algoritma machine learning (misalnya melalui encoding).<br>
6. Pemisahan fitur dan target diperlukan untuk memisahkan data yang akan digunakan untuk training model dan data yang digunakan sebagai output prediksi.<br>
7. Sebagian besar model machine learning memerlukan target yang berupa angka, bukan string. Label Encoding mengonversi kategori menjadi format numerik sehingga model dapat memprosesnya.<br>
8. Train-test split dilakukan untuk menghindari `overfitting` atau untuk menghindari bias dan memastikan model diuji pada data yang berbeda dari data yang dilatih.<br>
9. Fitur kategorikal perlu diubah menjadi format yang dapat diterima oleh model machine learning. One-Hot Encoding memungkinkan model untuk mengerti informasi kategorikal dalam bentuk numerik.<br>
10. Standardization dilakukan Untuk menghindari model bias terhadap fitur dengan skala lebih besar. dan One-Hot Encoding diperlukan untuk fitur kategorikal agar dapat diproses oleh algoritma yang hanya menerima data numerik.<br>
11. Data perlu dalam format yang tepat (numerik dan terstandarisasi) untuk dapat digunakan oleh model machine learning seperti SVM, Decision Tree, dll.<br>

## Modeling
Model yang digunakan:
- Logistic Regression sederhana dan cepat, tetapi mungkin tidak cocok untuk data yang sangat non-linier.<br>
- Decision Tree mudah dipahami, namun bisa overfit.<br>
- Random Forest lebih stabil dan robust dibandingkan Decision Tree.<br>
- Naive Bayes cepat, namun kurang akurat jika asumsi independensinya tidak valid.<br>
- XGBoost menawarkan performa terbaik, tetapi membutuhkan tuning yang lebih rumit.<br>

Proses:
- Training dan Evaluasi Model. Model dilatih pada data pelatihan menggunkan `fit()`, yang kemudian hasil evaluasi dilakukan pada data pelatihan dan pengujian. Evaluasi Model sendiri digunakan untuk menghitung metrik evaluasi sebagai berikut : 
   - Confusion Matrix: Matriks yang menunjukkan jumlah prediksi benar dan salah untuk setiap kelas.<br>
   - Accuracy: Persentase prediksi yang benar.<br>
   - Precision: Proporsi prediksi positif yang benar. <br>
   - Recall: Proporsi aktual positif yang benar.<br>
   - F1-Score: Harmonisasi mean dari precision dan recall, memberikan ukuran keseimbangan antara keduanya.<br>
- Untuk setiap model, Confusion Matrix divisualisasikan menggunakan heatmap untuk memudahkan analisis lebih lanjut terhadap kesalahan prediksi.<br>


## Evaluation
Metrik evaluasi:
- **Accuracy**: proporsi prediksi benar secara keseluruhan <br>
- **Precision**: dari semua prediksi positif, berapa yang benar<br>
- **Recall**: dari semua kasus sebenarnya positif, berapa yang berhasil diprediksi<br>
- **F1 Score**: Harmonisasi mean dari precision dan recall, memberikan ukuran keseimbangan antara keduanya.<br>

Hasil Evaluasi Berdasarkan Metrik:
- Train Results (Hasil pada data pelatihan):
   - Logistic Regression: Akurasi, precision, recall, dan F1-score semuanya sangat tinggi, mendekati nilai 1 (0.9984), menunjukkan bahwa model ini sangat baik dalam mempelajari data pelatihan.<br>
   - Decision Tree: 100% pada semua metrik, artinya model ini mampu mengingat seluruh data pelatihan dengan sangat baik. Meskipun ini terlihat sangat baik, bisa jadi model ini overfitting, yang berarti sangat spesifik terhadap data pelatihan dan bisa gagal ketika diuji pada data baru.<br>
   - Random Forest: Juga mendapatkan nilai sempurna (1.0000) pada semua metrik, mirip dengan Decision Tree, namun Random Forest lebih tahan terhadap overfitting karena menggunakan metode ensemble yang menggabungkan banyak pohon keputusan.<br>
   - Naive Bayes: Hasilnya cukup rendah, dengan akurasi 86.54% dan F1-score 84.59%. Ini menunjukkan bahwa model ini tidak terlalu kuat dalam mempelajari pola dari data pelatihan.<br>
   - XGBoost: Mendapatkan nilai sempurna pada semua metrik, mirip dengan Random Forest, namun XGBoost cenderung lebih baik pada dataset yang lebih kompleks berkat teknik boosting yang digunakan untuk meningkatkan performa.<br>

Test Results (Hasil pada data uji):
   - Logistic Regression: Akurasi 99.66%, precision, recall, dan F1-score yang sangat tinggi (di atas 99%) menunjukkan model ini masih generalisasi dengan sangat baik pada data yang belum pernah dilihat sebelumnya, meskipun sedikit menurun dibandingkan data pelatihan.<br>
   - Decision Tree: Akurasi yang lebih rendah (89.58%) dibandingkan dengan data pelatihan menunjukkan bahwa model ini overfitting, di mana model terlalu menyesuaikan diri dengan data pelatihan dan gagal untuk generalisasi dengan baik pada data uji.<br>
   - Random Forest: Akurasi 91.58% dengan precision dan recall yang baik (92.27% dan 91.58%, F1 score 90.66%) menunjukkan bahwa model ini cukup baik dalam menggeneraliskan data, namun sedikit lebih rendah dibandingkan dengan Logistic Regression dan XGBoost.<br>
   - Naive Bayes: Akurasi (86.27%) dan F1-score (84.20%) yang lebih rendah menunjukkan bahwa model ini gagal memberikan performa yang baik pada data uji, kemungkinan karena asumsi independensi yang tidak sesuai dengan dataset.<br>
   - XGBoost: Akurasi 97.33%, precision dan recall hampir sempurna (mendekati 97%), menunjukkan bahwa XGBoost menggeneralisasi dengan baik, meskipun tidak sebaik Logistic Regression dalam hal akurasi.<br>

Hasil terbaik diperoleh dari model: **Logistic Regression** dan **XGBoost**
- **Logistic Regression** dipilih karena memberikan performanya yang sangat stabil pada data uji, dengan nilai akurasi, precision, recall, dan F1-score yang sangat tinggi, yaitu sekitar 99.6%. Model ini mudah diinterpretasi, tidak terlalu kompleks, dan bekerja dengan baik pada dataset ini.
- Accuracy: `99.66%`
- Precision: `99.66%`
- Recall: `99.66%`
- F1 Score: `99.66%`

**XGBoost** adalah model yang lebih kompleks dan memberikan hasil seimbang dengan logistic regression, tetapi sedikit lebih rendah di beberapa metrik. Namun, XGBoost tetap memberikan recall yang sangat baik (97.33%), yang sangat penting untuk masalah deteksi penyakit, di mana kita ingin meminimalkan false negative (mislabeling data positif).
- Accuracy: `97.33%`
- Precision: `97.33%`
- Recall: `97.33%`
- F1 Score: `97.30%`

Model ini dipilih karena : 
1. Logistic Regression memiliki keseimbangan yang sangat baik antara performanya dan interpretabilitas yang tinggi, cocok untuk aplikasi yang membutuhkan pemahaman model yang sederhana dan efisien.<br>
2. XGBoost adalah pilihan kedua yang baik karena performa recall yang lebih tinggi dan kemampuannya dalam menangani data yang lebih kompleks, tetapi dengan sedikit kehilangan dalam hal interpretabilitas dibandingkan Logistic Regression.<br>

Jadi, berdasarkan kebutuhan untuk deteksi penyakit, kedua model ini adalah pilihan yang baik, namun Logistic Regression mungkin lebih diutamakan karena kemudahan interpretasinya dan hasil yang setara dalam hal akurasi dan recall.<br>

## Referensi
- [Cancer](https://www.who.int/news-room/fact-sheets/detail/cancer)
- [Global Cancer Statistics 2020: GLOBOCAN Estimates of Incidence and Mortality Worldwide for 36 Cancers in 185 Countries](https://pubmed.ncbi.nlm.nih.gov/33538338/)
- [RANCANG BANGUN APLIKASI PREDIKSI KANKER PAYUDARA DENGAN PENDEKATAN MACHINE LEARNING](https://journal.eng.unila.ac.id/index.php/jitet/article/view/3351/1488)
- [Machine Learning and AI in Cancer Prognosis, Prediction, and Treatment Selection: A Critical Approach](https://pmc.ncbi.nlm.nih.gov/articles/PMC10312208/)
---