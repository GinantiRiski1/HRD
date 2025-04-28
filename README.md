# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Jaya Jaya Maju

## Business Understanding

Jaya Jaya Maju adalah sebuah perusahaan multinasional yang telah berdiri sejak tahun 2000 dan memiliki lebih dari 1000 karyawan yang tersebar di seluruh penjuru negeri. 

Meskipun telah menjadi perusahaan besar, Jaya Jaya Maju menghadapi tantangan dalam pengelolaan karyawan, yang berdampak pada tingginya tingkat attrition (rasio jumlah karyawan yang keluar dibandingkan dengan total karyawan) hingga lebih dari 10%. 

Tingginya attrition rate ini menimbulkan kekhawatiran bagi perusahaan karena dapat berdampak negatif terhadap stabilitas operasional, beban biaya rekrutmen, dan produktivitas tim. 

Untuk mengatasi masalah ini, manajer departemen HR meminta bantuan untuk:
- Mengidentifikasi faktor-faktor utama yang mempengaruhi tingkat attrition di perusahaan.
- Membangun dashboard bisnis yang dapat memonitor faktor-faktor penting tersebut secara berkala, sehingga perusahaan dapat mengambil langkah preventif untuk mengurangi tingkat turnover karyawan.

### Permasalahan Bisnis

Berdasarkan latar belakang yang telah dijelaskan, permasalahan bisnis yang dihadapi oleh Jaya Jaya Maju adalah sebagai berikut:

1. **Tingginya Tingkat Attrition Karyawan**  
   - Rasio karyawan yang keluar dari perusahaan melebihi 10%, yang dapat berdampak pada stabilitas operasional dan meningkatkan biaya rekrutmen serta pelatihan karyawan baru.

2. **Kurangnya Pemahaman terhadap Faktor Penyebab Attrition**  
   - Perusahaan belum memiliki informasi yang jelas mengenai faktor-faktor apa saja yang paling berkontribusi terhadap keputusan karyawan untuk keluar, seperti lembur, gaji, usia, kepuasan kerja, keseimbangan hidup, dan faktor lainnya.

3. **Keterbatasan Alat Monitoring Faktor Risiko**  
   - Tidak adanya dashboard bisnis yang mampu memantau dan menganalisis faktor-faktor risiko attrition secara real-time, sehingga pengambilan keputusan menjadi kurang berbasis data.

4. **Kebutuhan untuk Mengurangi Turnover dan Meningkatkan Retensi Karyawan**  
   - Perusahaan perlu strategi berbasis data untuk mengidentifikasi kelompok karyawan yang berisiko tinggi keluar, agar dapat dilakukan intervensi lebih awal dan meningkatkan tingkat retensi.

### Cakupan Proyek

Cakupan proyek ini mencakup analisis dan visualisasi faktor-faktor yang mempengaruhi tingkat attrition karyawan di perusahaan Jaya Jaya Maju. Fokus analisis akan mencakup:

1. **Analisis Overtime**  
   - Mengkaji apakah karyawan yang melakukan lembur (OverTime) memiliki kecenderungan lebih tinggi untuk keluar dari perusahaan.

2. **Analisis Usia Karyawan**  
   - Menilai bagaimana usia karyawan berpengaruh terhadap keputusan untuk bertahan atau keluar dari perusahaan.

3. **Analisis Pengaruh Gaji Bulanan (Monthly Income)**  
   - Menganalisis keterkaitan antara tingkat gaji bulanan dengan tingkat attrition.

4. **Analisis Pengalaman dan Lama Bekerja**  
   - Menilai apakah karyawan dengan pengalaman kerja lebih lama atau total tahun bekerja lebih banyak cenderung lebih loyal atau justru lebih sering keluar.

5. **Analisis Kepuasan Kerja (Job Satisfaction)**  
   - Menilai seberapa besar pengaruh kepuasan kerja terhadap kecenderungan attrition.

6. **Analisis Keseimbangan Kerja dan Kehidupan (Work-Life Balance)**  
   - Menilai hubungan antara keseimbangan kehidupan kerja dengan tingkat attrition.

7. **Analisis Kepuasan Lingkungan Kerja (Environment Satisfaction)**  
   - Mengkaji pengaruh lingkungan kerja terhadap keputusan karyawan untuk keluar.

8. **Analisis Level Stock Option**  
   - Menganalisis apakah karyawan dengan level stock option yang lebih tinggi cenderung lebih loyal terhadap perusahaan.

9. **Analisis Kenaikan Gaji (Percent Salary Hike)**  
   - Menilai apakah kenaikan gaji memiliki efek dalam mengurangi tingkat turnover karyawan.

10. **Analisis Posisi Pekerjaan (Job Role)**  
    - Mengkaji posisi atau peran pekerjaan mana yang memiliki tingkat keluar tertinggi.

11. **Analisis Level Jabatan (Job Level)**  
    - Menganalisis apakah karyawan pada tingkat jabatan tertentu lebih rentan terhadap attrition.

12. **Analisis Jarak Rumah ke Kantor (Distance From Home)**  
    - Menilai apakah jarak tempat tinggal karyawan dari kantor berpengaruh terhadap keputusan mereka untuk keluar dari perusahaan.

Seluruh analisis ini akan divisualisasikan dalam sebuah dashboard interaktif untuk memudahkan manajemen HR dalam memahami kondisi karyawan dan mengambil langkah-langkah strategis.


### Persiapan

Sumber data: [Klik Link Disini](https://github.com/dicodingacademy/dicoding_dataset/blob/main/employee/employee_data.csv)

1. Setup environment:
```
pip install pandas sqlalchemy
```
2. Menyiapkan Dataset : ini adalah dataset yang sudah dibersihkan dari missing values
```
df = pd.read_csv("df_cleaned.csv", encoding='windows-1252')
df.head()
```
3. Menyiapkan Database di Supabase
   - pertama perlu lakukan registrasi terlebih dahulu di [Supabase](https://supabase.com/dashboard/sign-in) jika belum memiliki akun
   - jika sudah, maka klik `new project`, lalu isi informasi project yang ingin kamu buat
   - Tunggu sampai proses build selesai. Jika telah selesai, Anda bisa masuk ke Project setting.
   - Pada halaman Project setting, klik Database.
   - Pada halaman Database, Anda akan menemukan informasi yang dibutuhkan untuk menyambungkan Postgres database dengan metabase ataupun sqlalchemy.
   - Disana kita akan menemukan link connection URI dan password yang akan kita gunakan, lalu copy link tersebut
  
4. Mengirim dataset ke dalam database
   sebelumnya telah kita unduh ke dalam database menggunakan library sqlalchemy. Untuk melakukannya, Anda membutuhkan DATABASE_URL yang disediakan oleh supabase.
   berikut konfigurasi sesuai dengan link URI conncetion projectku :
   ```
   from sqlalchemy import create_engine
   URL = "postgresql://postgres.asngwxkmricdoeejrsqz:Ginanti10&25@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres"
   engine = create_engine(URL)
   df.to_sql('karyawan', engine)
   ```
5. Setelah berhasil maka dataset `karyawan.csv` akan ada ditable editor Supabase
6. Menghubungkan Metabase dengan Database
   Untuk melakukannya, kita perlu menjalankan docker image dari metabase dengan perintah berikut:
   ```
   docker run -p 3000:3000 --name metabase metabase/metabase
   ```
7. Setelah berhasil pull metabase kedalam docker, maka kita tinggal jalankan `http://localhost:3000/setup` pada web browser kita, dan sudah bisa melakukan pembuatan model, question dan dashboard.
   
## Business Dashboard

Jelaskan tentang business dashboard yang telah dibuat. Jika ada, sertakan juga link untuk mengakses dashboard tersebut.

## Conclusion

Jelaskan konklusi dari proyek yang dikerjakan.

### Rekomendasi Action Items (Optional)

Berikan beberapa rekomendasi action items yang harus dilakukan perusahaan guna menyelesaikan permasalahan atau mencapai target mereka.

- action item 1
- action item 2
