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





































































