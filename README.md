# Final Project kelompok Beta Tech
# Banking Dataset - Marketing Targets

## Prerequisites :
1. Download Dataset [here](https://www.kaggle.com/datasets/prakharrathi25/banking-dataset-marketing-targets)

## Detailed Column Descriptions
#### bank client data:

###### 1 - age (numeric)
###### 2 - job : type of job (categorical: "admin.","unknown","unemployed","management","housemaid","entrepreneur","student","blue-collar","self-employed","retired","technician","services")
###### 3 - marital : marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
###### 4 - education (categorical: "unknown","secondary","primary","tertiary")
###### 5 - default: has credit in default? (binary: "yes","no")
###### 6 - balance: average yearly balance, in euros (numeric)
###### 7 - housing: has housing loan? (binary: "yes","no")
###### 8 - loan: has personal loan? (binary: "yes","no")
related with the last contact of the current campaign:
###### 9 - contact: contact communication type (categorical: "unknown","telephone","cellular")
###### 10 - day: last contact day of the month (numeric)
###### 11 - month: last contact month of year (categorical: "jan", "feb", "mar", …, "nov", "dec")
###### 12 - duration: last contact duration, in seconds (numeric)
other attributes:
###### 13 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
###### 14 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric, -1 means client was not previously contacted)
###### 15 - previous: number of contacts performed before this campaign and for this client (numeric)
###### 16 - poutcome: outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")
Output variable (desired target):
###### 17 - y - has the client subscribed a term deposit? (binary: "yes","no")
Missing Attribute Values: None


# Stage 0
## Problem Statement : <br>
Biaya marketing yang cukup mahal, membuat kita harus selektif untuk memberikan marketing hanya kepada user yang berpeluang tinggi untuk membuka deposito berjangka.
## Business Metric
- Tingkat konversi pembukaan deposito berjangka (berapa banyak user yang membuka deposito setelah ditarget marketing)
- Jumlah customer yang dihubungi saat campaign marketing
## Goals
- Meningkatkan efisiensi direct campaign marketing untuk mendapatkan nasabah deposito berjangka yang potensial dengan meminimalisir nilai False Positive.
- Meningkatkan tingkat konversi pembukaan deposito berjangka.
## Objective
- Membangun model Machine Learning yang dapat memprediksi nasabah yang potensial untuk menerima campaign
- Menemukan faktor utama dari nasabah yang menerima campaign dan menyetujui produk deposito yang ditawarkan
- Memberikan rekomendasi bagi tim marketing yang akan meningkatkan efektivitas perusahaan dalam memberikan campaign kepada nasabah terpilih
- Meminimalkan nilai False Positive pada model Machine Learning dengan nilai akurasi yang baik

# Stage 1
## Summary Insight: 
1. Nasabah yang mengambil deposito kurang lebih memiliki karakteristik sama, yaitu condong ke tidak punya riwayat gagal bayar cicilan dan tidak punya pinjaman pribadi, dengan conversion rate 10-11%. <br>
   *Business Recommendation:*<br>Menargetkan nasabah yang tidak punya riwayat gagal bayar cicilan dan tidak punya pinjaman pribadi.

2. ● Nasabah yang tidak punya cicilan rumah adalah yang paling banyak mengambil deposito dengan conversion rate 7.4%. <br>
   ● Nasabah dengan kategori balance 0-5000 adalah yang paling banyak mengambil deposito dengan conversion rate 10.2%.

3. ● Kebanyakan nasabah mengambil deposito pada Bulan Mei (late spring) untuk persiapan sebelum masuk tahun ajaran baru (September) atau persiapan sebelum libur akhir tahun (Desember). <br>
   ● Desember dan Januari merupakan bulan awal dan pertengahan musim dingin sehingga nasabah kemungkinan besar memilih menggunakan uangnya untuk memenuhi kebutuhan di musim dingin yang lebih tinggi dibanding musim lainnya. <br>
   *Business Recommendation:*<br>
   Memberikan loyalty poin yang bisa ditukarkan dengan benefit tertentu, dengan nilai loyalty poin lebih besar diawal dan pertengahan winter.

4. Pekerjaan di bidang management paling tinggi conversion ratenya (2,9%) <br>
   *Business Recommendation:*<br> Mengutamakan nasabah yang berprofesi di bidang management, technician, blue-collar, admin, serta yang sudah pensiun sebagai target marketing.

5. ● Nasabah dengan status sudah menikah paling tinggi conversion ratenya (6%) dibanding single dan divorced. <br>
   ● Nasabah dengan pendidikan secondary paling tinggi conversion ratenya (6%) dibanding tingkat pendidikan yang lain. <br>
   ● Nasabah dengan kategori prime working (usia 25-54) tahun adalah yang paling banyak mengambil deposito dengan conversion rate 9%.
   *Business Recommendation:*<br>
    Mengutamakan nasabah dengan status menikah/single, berpendidikan secondary, berusia 25-54 tahun untuk menerima campaign.

6. ● Nasabah dengan durasi telepon terakhir 3-6 menit memiliki conversion rate tertinggi, yaitu 3.4%.<br>
   ● Nasabah dengan kategori 1-2 kali kontak selama campaign berlangsung adalah yang paling banyak mengambil deposito dengan conversion rate 8.7%. <br>
   *Business Recommendation:*<br>
   Memperbaiki kualitas telemarketer, sebisa mungkin mempertahankan pembicaraan berbobot selama 3-6 menit   dengan jumlah kontak dengan nasabah selama campaign berlangsung sebanyak 1-2 kali.

7. ● Nasabah paling banyak mengambil deposito saat dihubungi ke nomor ponselnya dengan conversion rate 9.7%. <br>
   ● Nasabah yang sama sekali belum pernah dikontak sebelumnya dan memilih untuk mengambil deposito memiliki conversion rate 7.5%. <br>
   *Business Recommendation:* <br> 
   Menghubungi nasabah ke nomor ponselnya (jika ada).

8. ● Setiap kelompok umur memiliki puncak optimal di durasi telpon 3-6 menit. <br>
   ● Kurva total konversi naik sampai menit ke 3-6, kemudian turun di menit setelahnya.<br>
   ● Kelompok umur prime working memiliki total konversi terbanyak dengan puncak optimal di bulan Mei.<br>
   ● Kelompok umur mature working memiliki puncak optimal di bulan Agustus.<br>
   *Business Recommendation:*<br>
   ● Mengutamakan nasabah prime working, terutama di Bulan Mei dengan durasi telepon 3-6 menit.<br>
   ● Meningkatkan kualitas telemarketer

9. Pelanggan “ya” dihubungi lebih sedikit dan memiliki durasi panggilan yang lebih lama. Lebih penting lagi, setelah lima panggilan kampanye, klien cenderung menolak deposito kecuali durasinya tinggi. Sebagian besar klien “ya” didekati kurang dari 10 kali. Hal ini menunjukkan bahwa bank jangan menelepon klien lebih dari lima kali, yang dapat mengganggu dan meningkatkan ketidakpuasan. <br>
   *Business Recommendation:* <br>
   Pihak marketing bank bisa melakukan campaign khusus di bulan Mei kepada Nasabah yang memiliki Balance/Tabungan tahunan dibawah 5000 euro dengan ketentuan :<br>
   -Nasabah tidak memiliki riwayat kredit macet dan tidak punya kredit<br>
   -Nasabah telah menikah dengan range umur 25-54 tahun <br>
   -Melakukan panggilan ke nomor ponsel nasabah dengan cara 1-2 kali kontak selama campaign 

10. Pelanggan 'ya' untuk kelompok usia yang berbeda: keinginan untuk berlangganan sangat tinggi untuk orang berusia di antara 25-54 tahun dan orang yang lebih muda berusia di bawah 25 tahun juga memiliki tingkat berlangganan yang lebih tinggi daripada kelompok usia lainnya.<br>
    *Business Recommendation:* <br> Bank harus memprioritaskan telemarketingnya kepada klien yang berusia di di antara 25-54 yang memiliki saldo di antara 5001-25000, karena mereka memiliki tingkat penerimaan tertinggi sekitar 13.9%. Kelompok berikutnya yang harus menjadi fokus bank adalah kelompok early working dengan saldo 0-5000, yang menunjukkan tingkat berlangganan yang tinggi yaitu 5%.
