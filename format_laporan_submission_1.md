# Laporan Proyek Machine Learning - Mu'azah Al'Adawiyah

## Project Overview

Kanker merupakan salah satu penyakit paling mematikan di dunia, dengan angka kematian yang terus meningkat setiap tahunnya. Menurut Organisasi Kesehatan Dunia (WHO), sekitar 10 juta kematian terjadi akibat kanker pada tahun 2020, dan jumlah ini diperkirakan akan terus meningkat seiring bertambahnya populasi dan berbagai faktor risiko seperti gaya hidup tidak sehat dan polusi (World Health Organization, 2023). Salah satu tantangan besar dalam penanganan kanker adalah banyaknya kasus yang terdiagnosis pada tahap lanjut, ketika pengobatan menjadi kurang efektif dan peluang bertahan hidup menurun secara signifikan (Bray et al., 2021).

Data pasien kanker global dari tahun 2015 hingga 2024 menunjukkan tren penting dalam pemahaman serta penanganan penyakit ini. Dataset tersebut disusun untuk mensimulasikan berbagai faktor yang memengaruhi diagnosis, pengobatan, dan kelangsungan hidup pasien kanker. Melihat tren peningkatan kasus secara global, dibutuhkan sistem yang efektif untuk mengumpulkan, menganalisis, dan melaporkan data secara akurat. Deteksi sel kanker secara dini menjadi sangat penting untuk menurunkan angka kematian. Diagnosis yang dilakukan tepat waktu memungkinkan pasien menerima perawatan lebih awal, yang dapat meningkatkan kemungkinan bertahan hidup (Bo Zhang et al., 2023).

Salah satu pendekatan yang umum digunakan dalam studi data medis adalah teknik klasifikasi, yang memungkinkan pengelompokan data berdasarkan karakteristik tertentu. Dalam konteks ini, Machine Learning (ML) menawarkan potensi besar untuk meningkatkan akurasi diagnosis kanker, sekaligus mempercepat dan mempermudah prosesnya (Cahyo Prianto et al., 2023). Proyek ini bertujuan mengembangkan sistem analisis data pasien kanker dengan menerapkan teknik ML seperti Support Vector Machine (SVM), Logistic Regression, Random Forest, dan Decision Tree. Metode ini mempertimbangkan faktor risiko seperti genetik, polusi udara, alkohol, merokok, dan obesitas. dengan harapan dapat membantu dalam deteksi dini, pengelolaan kanker yang lebih baik, serta memberikan informasi akurat dan relevan bagi peneliti, dokter, dan pembuat kebijakan.

Referensi:
- [Cancer](https://www.who.int/news-room/fact-sheets/detail/cancer)
- [Global Cancer Statistics 2020: GLOBOCAN Estimates of Incidence and Mortality Worldwide for 36 Cancers in 185 Countries](https://pubmed.ncbi.nlm.nih.gov/33538338/)
- [RANCANG BANGUN APLIKASI PREDIKSI KANKER PAYUDARA DENGAN PENDEKATAN MACHINE LEARNING](https://journal.eng.unila.ac.id/index.php/jitet/article/view/3351/1488)
- [Machine Learning and AI in Cancer Prognosis, Prediction, and Treatment Selection: A Critical Approach](https://pmc.ncbi.nlm.nih.gov/articles/PMC10312208/)


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
     ![Kategori](https://drive.google.com/uc?export=view&id=1wTRZxcFCWGOq42-8YA2jbwTLQgTMzlBa) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  2. Distribusi Kelas Numerik <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1j_ug4WyhszgkOs4Qc6eXnIkAJDD-EiW6) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari age, year, genetic_risk, air_pollution, alcohol_use, smoking, obesity_level, treatment_cost, Survival_years, Target_severity_sscore. <br>
  3. proporsi jenis kanker <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1XOyBHsIxZ1X18qKSv8HU7v1Yt_W1LibT) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  4. Jumlah Kasus Kanker tiap tahun <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=15v17MoRId6Q95IHq72NJldApQTXdVAr9) <br>

     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  5. Kasus kanker perwilayah <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1jRlZ_q0A_zZFxIWwcyskVJNJxfSaUdfP) <br>

     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  6. Top 10 Negara jumlah penderita kanker tertinggi <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1-KYVMDwyWBqLtSHMiGTQ_Nu3wJ8rg5qF) <br>
   
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  7. Jenis kanker di 5 negara penderita terbanyak <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1NasEqPRrTOUcRJC10FQbIpBPtSN3WyMS) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
     

- korelasi antar fitur <br>
  ![Kategori](https://drive.google.com/uc?export=view&id=12fQEUSaEZ35AYBFFWLcPcoTA_c8-o-xw) <br>
     
  Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>

- Visualisasi outlier <br>
  ![Kategori](https://drive.google.com/uc?export=view&id=1bRrqQi4mTOqWcSgqLtByOMXjCPNksWDa) <br>
   
  Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br> 

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

Tahapan yang dilakukan:
- Menghapus data duplikat
- Memastikan tidak ada nilai kosong/missing value
- Melakukan encoding untuk fitur kategorik (`cp`, `thal`, `slope`)
- Standarisasi fitur numerik seperti `age`, `chol`, `trestbps`, dll.

Alasan dilakukan:
- Duplikasi dan missing value bisa mengganggu pelatihan model
- Klasifikasi membutuhkan semua data numerik atau sudah terenkode
- Standarisasi membantu model seperti Logistic Regression bekerja lebih optimal


## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

Model yang digunakan:
- Logistic Regression (baseline)
- Random Forest Classifier
- XGBoost Classifier

Proses:
- Membagi data menjadi data latih dan data uji
- Melatih model dan membandingkan hasil dengan metrik klasifikasi
- Melakukan hyperparameter tuning (GridSearchCV) pada model terbaik


## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

Metrik evaluasi:
- **Accuracy**: proporsi prediksi benar secara keseluruhan
- **Precision**: dari semua prediksi positif, berapa yang benar
- **Recall**: dari semua kasus sebenarnya positif, berapa yang berhasil diprediksi
- **F1 Score**: harmonisasi precision dan recall

Hasil terbaik diperoleh dari model: **Random Forest**
- Accuracy: `X.XX`
- Recall: `X.XX`
- F1 Score: `X.XX`

Model ini dipilih karena keseimbangan antara performa dan interpretabilitas, serta performa recall yang penting untuk deteksi penyakit.

---

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

