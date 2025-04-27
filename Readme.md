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

Beberapa hasil visualisasi juga dilakukan:
- Menampilkan distribusi kelas target <br>
  1. Distribusi Kelas Kategori <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1wTRZxcFCWGOq42-8YA2jbwTLQgTMzlBa) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari gender, country_region, cancer_type, cancer_stage. <br>
  2. Distribusi Kelas Numerik <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1j_ug4WyhszgkOs4Qc6eXnIkAJDD-EiW6) <br>
     
     Pada gambar diatas menunjukkan visualisasi distribusi kelas kategori yang terdiri dari age, year, genetic_risk, air_pollution, alcohol_use, smoking, obesity_level, treatment_cost, Survival_years, Target_severity_sscore. <br>
  3. proporsi jenis kanker <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1XOyBHsIxZ1X18qKSv8HU7v1Yt_W1LibT) <br>
     
     Pada gambar diatas menunjukkan beberapa jumlah persentase beberapa type kanker yang di diagnosis pasien terdapat type kanker yang terdiri dari lung, breast, cervical, skin, liver, leukemia, prostate, colon. Persentase yang ditampilkan jumlahnya sama rata yaitu 12% tetapi yang paling tinggi persentase komanya yaitu jenis kanker colon. <br>
  4. Jumlah Kasus Kanker tiap tahun <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=15v17MoRId6Q95IHq72NJldApQTXdVAr9) <br>

     Pada gambar diatas menunjukkan hasil perkembangan kasus penyakit kanker tiap tahun. Dari  kita liat grafiknya menunjukkan bahwa kasus penyakit kanker secara global tiap tahunnya berubah-ubah dari waktu ke waktu. Dari mulai tahun 2015 sebanyak >= 5000 naik di tahun 2016 sebanyak >= 5050an kasus dan pada tahun 2024 mengalami sedikit penurunan sebanyak 5000 kasus. <br>
  5. Kasus kanker perwilayah <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1jRlZ_q0A_zZFxIWwcyskVJNJxfSaUdfP) <br>

     Pada gambar diatas menunjukkan beberapa jumlah persentase beberapa kasus kanker perwilayah yang di diagnosis pasien terdapat negara china, pakistan, brazil, rusia, jerman, india, usa, uk, australia, dan canada. Dari hasil diagram lingkaran tersebut persentase yang ditampilkan jumlahnya sama rata yaitu 10% kecuali untuk negara canada, china, dan pakistan yang menampilkan persentase sebanyak 9%. <br>
  6. Top 10 Negara jumlah penderita kanker tertinggi <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1-KYVMDwyWBqLtSHMiGTQ_Nu3wJ8rg5qF) <br>
   
     Pada gambar diatas menunjukkan bahwa ada 10 negara yang memiliki jumlah penderita kanker tertinggi yaitu australia, uk, usa, india, jerman, rusia, brazil, pakistan, china dan canada. Kasus tertinggi di peroleh dari negara australia dan negara yang sedikit kasusnya yaitu canada. <br>
  7. Jenis kanker di 5 negara penderita terbanyak <br>
     ![Kategori](https://drive.google.com/uc?export=view&id=1NasEqPRrTOUcRJC10FQbIpBPtSN3WyMS) <br>
     
     Pada gambar diatas menunjukkan bahwa ada 5 negara yang memiliki tipe kanker yang memiliki pasien terbanyak yaitu urutan pertama ada UK, dimana tipe kanker paling tinggi yaitu kanker prostate, yang kedua negara jerman tipe kanker yang paling tinggi yaitu kanker leukemia, dan untuk urutan terakhir negara australia yang memiliki tipe kanker dengan pasien terbanyak yaitu kanker liver. <br>

- korelasi antar fitur <br>
  ![Kategori](https://drive.google.com/uc?export=view&id=12fQEUSaEZ35AYBFFWLcPcoTA_c8-o-xw) <br>
     
  Pada gambar diatas menunjukkan hubungan atau korelasi antar fitur dalam dataset. Korelasi diukur dalam rentang -1 hingga 1. Terdapat beberapa warna area yaitu :
  - Area merah menunjukkan korelasi yang sangat kuat (mendekati nilai 1.0) pada area ini memiliki fitur korelasi antar dirinya sendiri sehingga wajar selalu memiliki korelasi sempurna. <br>
  - Area biru menunjukkan korelasi negatif moderat sekitar -0.4 yang artinya salah satu fitur naik, maka fitur lain turun seperti korelasi antara target_severity_score dan treatment_cost. <br>
  - Area Coklat menunjukkan korelasi positif lemah sampai sedang (antara 0.3 sampai 0.7). Misalnya, hubungan target_severity_score dengan generic, pollution, dan alcohol berada di rentang ini, yang berarti ada kecenderungan naik bersama, tetapi tidak terlalu kuat. <br>
  - Area abu-abu biru langit mewakili korelasi sangat lemah (sekitar 0.2 atau lebih kecil), menunjukkan hubungan yang hampir tidak signifikan antara fitur-fitur tersebut <br>

- Visualisasi outlier <br>
  ![Kategori](https://drive.google.com/uc?export=view&id=1bRrqQi4mTOqWcSgqLtByOMXjCPNksWDa) <br>
   
  Pada gambar diatas menunjukkan titik data yang berada jauh dari distribusi normal data lainnya. Mereka bisa mempengaruhi analisis statistik atau model.  <br> 

## Referensi
- [Cancer](https://www.who.int/news-room/fact-sheets/detail/cancer)
- [Global Cancer Statistics 2020: GLOBOCAN Estimates of Incidence and Mortality Worldwide for 36 Cancers in 185 Countries](https://pubmed.ncbi.nlm.nih.gov/33538338/)
- [RANCANG BANGUN APLIKASI PREDIKSI KANKER PAYUDARA DENGAN PENDEKATAN MACHINE LEARNING](https://journal.eng.unila.ac.id/index.php/jitet/article/view/3351/1488)
- [Machine Learning and AI in Cancer Prognosis, Prediction, and Treatment Selection: A Critical Approach](https://pmc.ncbi.nlm.nih.gov/articles/PMC10312208/)