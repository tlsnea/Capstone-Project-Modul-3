<hr>

# **A. Business Problem Understanding**

## **1. Background**

- Perusahaan asuransi kendaraan ini berfokus pada memberikan solusi perlindungan yang komprehensif untuk berbagai segmen pasar, sehingga penting bagi mereka untuk memahami nilai jangka panjang setiap pelanggan.
- Tantangan dan Tugas: Untuk menentukan profit dari pelanggan dan biaya yang diperlukan untuk mempertahankan atau mendapatkan pelanggan baru, perusahaan meminta seorang Data Scientist untuk membuat model prediksi Customer Lifetime Value (CLV) yang akurat.
- Pentingnya CLV: CLV adalah metrik penting yang membantu perusahaan dalam membuat keputusan strategis terkait marketing, penjualan, dan retensi pelanggan, yang semuanya berkontribusi langsung pada profitabilitas perusahaan.

## **2. Problem Statement**
- Pendapatan dan Strategi Perusahaan: Perusahaan asuransi kendaraan mendapatkan profit dari premi yang dibayarkan oleh nasabah, sehingga penting untuk mempertahankan pelanggan yang sudah ada dan memberikan penawaran khusus bagi pelanggan loyal.
- Peran CLV dalam Marketing: CLV digunakan sebagai parameter untuk mengalokasikan usaha marketing dengan lebih efektif, membantu perusahaan menghindari pengeluaran berlebihan untuk mendapatkan pelanggan baru dan memastikan investasi yang tepat dalam mempertahankan pelanggan yang berharga.
- Pentingnya Akurasi CLV: Menentukan CLV setiap pelanggan dengan tepat, berdasarkan faktor seperti kelas kendaraan, cakupan asuransi, dan pendapatan pelanggan, sangat penting untuk mencapai tujuan perusahaan dalam meningkatkan profitabilitas dan efisiensi operasional.

## **3. Goals**
Tujuan dari pemodelan ini:
1. **Menentukan _Customer lifetime value_ dari setaiap _customer_ asuransi kendaraan**.
Dengan mempertimbangkan berbagai aspek yang melekat pada pelanggan, seperti kelas kendaraan, _coverage_, tipe tawaran perpanjangan, status pekerjaan, status pernikahan, pendidikan, jumlah polis, biaya premi per bulan, total klaim, pendapatan. .
2. **Menentukan aspek penting dalam perhitungan _Customer lifetime value_**.
Perlu diketahui aspek penting yang berhubungan secara signifikan dengan _Customer lifetime value_.

Output ini bisa digunakan sebagai **Marketing Strategy** untuk meminimalkan terjadinya **over budget** dalam anggaran pemasaran, dengan fokus pada alokasi sumber daya yang lebih efektif berdasarkan nilai pelanggan yang diproyeksikan, sehingga dapat meningkatkan profitabilitas dan efisiensi kampanye pemasaran.

## **4. Analytic Approach**
Kita perlu membuat **model machine learning** untuk menganalisis data dan menemukan pola dari fitur-fitur yang membedakan pemegang polis berdasarkan CLV. Hal ini penting untuk membantu Marketing Team mengembangkan strategi pemasaran yang lebih efektif, menargetkan pelanggan dengan nilai tertinggi, dan mengalokasikan anggaran dengan lebih efisien.

## **5. Modelling**
Pada kasus ini, label yang akan diprediksi adalah numerik, sehingga model machine learning yang digunakan adalah model regresi terawasi (supervised regression model).
Model yang akan diuji coba adalah
- Linear regression
- Lasso
- Ridge
- KNN Regressor
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor
- AdaBoost Regressor
- GradientBoostig Regressor

## **6. Evaluation Metric**
_Metric evaluation_ yang digunakan dalam pengambilan keputusan adalah `MAE` dan `MAPE` karena dalam hal ini MAE diperlukan untuk memberikan gambaran yang mudah dipahami tentang rata-rata kesalahan dalam satuan yang sama dengan target, memberikan gambaran mengenai selisih error yang mungkin terjadi pada prediksi. MAPE digunakan untuk menilai kesalahan relatif dalam bentuk persentase. [MAPE](https://www.researchgate.net/figure/nterpretation-of-typical-MAPE-values_tbl1_257812432#:~:text=A%20MAPE%20under%2010%25%20shows,shows%20incorrect%20results%20%5B36%5D%20.) digunakan agar dapat memberikan gambaran yang mudah dipahami dalam konteks bisnis.

<hr>

# **B. Data Understanding**

**Attribute Information**

|No|Attribute|Data Type|Deskripsi|Keterangan|
|--|-------|-------|---------|----------|
|1|Vehicle Class|Object| Tipe kendaraan pemengang polis|Kelas kendaraan dapat mempengaruhi jenis asuransi karena perbedaan setiap kendaraan memiliki level risiko yang berbeda|
|2|Coverage|Object| Tipe asuransi yang dipilih pemegang polis | Tipe covarage mempengaruhi lingkup proteksi dan biaya asuransi|
|3|Renew Offer Type|Object|Jenis perpanjangan penawaran yang diberikan kepada pemegang polis. | Dapat melingkupi perbedaan insentif, dikon, atau ketentuan kebijakan baru untuk mempertahankan pelanggan|
|4|Employment Status|Object|Status kepekerjaan pemegang polis | Dapat mempengaruhi profil risiko pemegang polis dan, selanjutnya, premi asuransi. Misalnya, pensiunan mungkin memiliki pola mengemudi yang berbeda dibandingkan dengan mereka yang bekerja.|
|5|Marital Status|Object|Status Perkawinan pemegang polis|Individu yang sudah menikah mungkin dianggap memiliki risiko lebih rendah|
|6|Education|Object|Level pendidikan tertinggi pemegang polis|Pendidikan dapat berkaitan dengan pendapatan dan status pekerjaan|
|7|Number of Policies|Float|Jumlah polis asuransi yang dimiliki pemegang polis pada perusahaan.|Pelanggan dengan berbagai kebijakan mungkin menerima diskon atau dianggap lebih setia, yang dapat memengaruhi harga dan penawaran perpanjangan.|
|8|Monthly Premium Auto|Float|Jumlah yang dibayarkan oleh pemegang polis setiap bulannya|Ini adalah metrik keuangan utama bagi pelanggan dan perusahaan asuransi, yang mencerminkan biaya pemeliharaan polis.|
|9|Total Claim Amount|Float|Total biaya yang sudah diklaim oleh pemengang polis selama umur polis|Jumlah total klaim tinggi menunjukkan profil risiko yang lebih tinggi, yang dapat menyebabkan premi lebih tinggi atau mempengaruhi penawaran perpanjangan.|
|10|Income|Float|Pendapatan tahunan pemegang polis|Tingkat pendapatan dapat mempengaruhi keterjangkauan premi dan jenis perlindungan yang mungkin dipilih oleh pemegang polis.|

<hr>

# **C. Data Preprocessing**
- Duplicated data: 10.90%
- No Missing Values
- Outlier: Terdapat outlier pada kolom numerikal dengan persentase sekitar 0% - 8.89%. Dalam kasus ini, outlier dapat memberikan informasi lebih dari setiap karakter _customer_ yang beragam sehingga akan dipertahankan terlebih dahulu.

<hr>

# **D. Feature Engineering**
1. **Handling Outliers**: Outliers pada kolom *Total Claim Amount* dan *Monthly Premium Auto* akan ditangani menggunakan metode *winsorizing*. Namun, pengujian juga akan dilakukan tanpa penanganan outliers untuk melihat perbandingannya.

2. **Encoding**: 
   - Fitur kategorikal seperti `Vehicle Class`, `Renew Offer Type`, `Employment Status`, dan `Marital Status` akan diencode menggunakan *One Hot Encoding* karena fitur-fitur ini tidak ordinal dan memiliki jumlah unique data yang sedikit.
   - Fitur `Coverage` dan `Education` akan diencode menggunakan *Ordinal Encoding* karena memiliki urutan (ordinal).

3. **Scaling**: 
   - *Robust Scaler* akan digunakan untuk scaling karena efektif dalam menghadapi outliers dengan menggunakan median dan *interquartile range (IQR)*. 
   - Selain itu, *PowerTransformer* dengan metode Yeo-Johnson akan digunakan sebagai alternatif scaling untuk mengatasi distribusi data yang skewed dan tidak normal.

<hr>

# **E. Machine Learning and Tuning**
Model-model akan diuji tanpa menggunakan TransformedTargetRegressor dan yang kedua menggunakan TransformedTargetRegressor. Tujuan penggunaan TransformedTargetRegressor adalah untuk mengubah distribusi target agar lebih sesuai dengan asumsi model dengan mengatasi skewness, distribusi tidak normal, dan menstabilkan varians, menggunakan teknik Yeo-Johnson yang dapat memproses data negatif maupun positif.

  ## **1. Splitting Scheme (80:20)**
* X: features -> columns other than `Customer Lifetime Value`
* y: target -> `Customer Lifetime Value`

  ## **2. Data Scaling**
  **Transformer**
  
| Technique | Action|
|----------------------------- | ----------- |
|One Hot Encoding | Transformasi kolom  `Vehicle Class`, `Renew Offer Type`,`EmploymentStatus`, dan `Marital Status` yang jumlah nilai uniknya <= 10 |
| Ordinal Encoding | Transformasi kolom  `Coverage` dan `Education` yang memiliki urutan |
  
  ## **3. Tuning**
Model|MAE Sebelum Tuning|MAE After Tuning|
|---|---|---|
|Gradient Boost| 1522.189114 |-1472.727|
|Random Forest| 1547.680836 |-1561.191|
|XGBoost| 1670.944095 |-1684.497|

<hr>

# **F. Conclusion & Recommendation**

## **1. Conclusion**
Berdasarkan hasil pemodelan terbaik (Gradient Boosting):
- Score MAE Gradient Boosting Model ini adalah 1396.65 dan score MAPE Gradient Boosting Model ini adalah 8.1%. Artinya, **rata-rata kesalahan prediksi model tersebut adalah sekitar 1396.65 dalam skala data asli (dollar), dan kesalahan tersebut merupakan 8.1% dari nilai target yang sebenarnya.**
- Waktu yang dibutuhkan untuk melatih model: 7 detik
- `Number of Policies` dan `Monthly Premium Auto` merupakan fitur dengan korelasi tinggi dengan CLV dan paling penting dalam pemodelan ini, sehingga mempengaruhi nilai `Customer Lifetime Value`
- Model ini memiliki limitasi yaitu hanya dapat memprediksi nilai `CLV` yang berkisaran `CLV` <**=$2596 sampai dengan $10000** dan kisaran nilai fitur sebagai berikut.
    - `Number of Policies` antara 1 sampai dengan 9.
    - `Monthly Premium Auto` antara 61 sampai dengan 297.
    - `Total Claim Amount` antara 0.423310 sampai dengan 2759.794354.
    - `Income` antara  0 sampai dengan 99934.
    - `Vehicle Class` diencoding dengan nilai 0 atau 1 berdasarkan onehot encoding.
    - `Coverage` diencoding dengan nilai antara 1 sampai 3.
    - `Renew Offer Type` diencoding dengan nilai 0 atau 1 berdasarkan onehot encoding.	
    - `EmploymentStatus` diencoding dengan nilai 0 atau 1 berdasarkan onehot encoding.	
    - `Marital Status` diencoding dengan nilai 0 atau 1 berdasarkan onehot encoding.	
    - `Education` diencoding dengan nilai antara 1 sampai 5.


## **2. Recommendation**
- Bagi perusahaan
  - Dalam meningkatkan pendapatan perusahaan, dapat dilakukan strategi pemasaran yang berfokus dalam meningkatkan `Number of Policies` dan `Monthly Premium Auto`. Namun, perlu mempertimbangkan agar `Monthly Premium Auto` tetaap sesuai dengan faktor seperti, pendapatan, pekerjaan, pendidikan karena premi per bulan dapat menjadi faktor yang paling sensitif dan berdampak besar dalam keputusan pelanggan.

- Bagian pengembangan Model Machine Learning
  - Dapat dilakukan optimasi menggunakan `GridSearch` agar lebih banyak kombinasi yang dilakukan dalam mencari parameter terbaik.
  - Dapat dilakukan pemodelan lain yang berfokus pada menggunakan Lasso maupun Ridge untuk `mencegah overfitting` dan `mengontrol kompleksitas model` dengan menambahkan penalti pada ukuran koefisien. Dan menjadi **pembanding model Gradient Boosting yang kompleks**. Kedua metode ini adalah bagian dari teknik yang disebut Regularisasi, sehingga dapat sekaligus dilakukan feature selection dan model menjadi lebih sederhana.
 
- Untuk Dataset
  - `Income` memiliki **nilai 0 di kuartil 25%**, yang menunjukkan ada banyak entri dengan pendapatan nol. Ini bisa menjadi masalah untuk model yang memerlukan informasi pendapatan untuk memprediksi CLV. 
  - **Penambahan fitur yang relevan**, seperti Tenure, Discounts Used, atau Customer Engagement Metrics, bisa memperkaya dataset untuk memberi informasi lebih berkaitan dengan kondisi setiap pelanggan. 

- 



































































