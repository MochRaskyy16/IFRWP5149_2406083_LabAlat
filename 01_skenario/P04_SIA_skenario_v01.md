# P04_SIA_skenario_v01 — Model Tugas Pertemuan 4: Sistem Informasi Akademik, Layanan Hasil Studi

Diagram: `04_model_analisis/P04/SIA/P04_NIM_SIA_usecase_v01.drawio` (ekspor `.png` dengan versi yang sama).  
Diagram bersifat kumulatif: memuat fungsi jadwal (Pertemuan 2), fungsi KRS (Pertemuan 3), dan fungsi hasil studi (Pertemuan 4) dalam satu diagram.

## 1. Aktor

| Aktor | Kedudukan | Tujuan terhadap sistem |
|---|---|---|
| Civitas Akademika | Umum (general), baru pada Pertemuan 4 | Peran umum bagi warga akademik. Mewariskan fungsinya (melihat kalender akademik) kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Civitas Akademika, tetap dari pertemuan sebelumnya | Melihat kalender akademik (diwarisi dari Civitas Akademika), ditambah asosiasi khususnya sendiri: Lihat Jadwal Kuliah, Ajukan KRS, Unduh Bukti Pengajuan KRS, dan Lihat KHS. |
| Dosen | Khusus dari Civitas Akademika, baru pada Pertemuan 4 | Melihat kalender akademik (diwarisi dari Civitas Akademika), ditambah asosiasi khususnya sendiri: Input Nilai Mata Kuliah. |
| Admin Akademik | Tetap dari pertemuan sebelumnya | Mengelola jadwal kuliah dan mengelola data mahasiswa. |
| Dosen Wali | Tetap dari pertemuan sebelumnya | Memproses keputusan KRS. |

Kelima aktor digambar di luar batas sistem. Dosen Wali tidak digabung dengan Dosen: keduanya aktor berbeda.

## 2. Keputusan generalization aktor

Hierarki satu tingkat: Mahasiswa → Civitas Akademika dan Dosen → Civitas Akademika.

- **Keputusan 1:** Mahasiswa adalah bentuk khusus dari Civitas Akademika, dan Dosen adalah bentuk khusus dari Civitas Akademika. **Alasan:** keduanya berbagi fungsi yang sama, yaitu melihat kalender akademik (SIA-R07).
- **Keputusan 2:** Asosiasi ke SIA-UC07 Lihat Kalender Akademik digambar satu kali, dari Civitas Akademika. Tidak ada garis yang sama dari Mahasiswa maupun dari Dosen.
- **Fungsi yang diwarisi:** SIA-UC07 Lihat Kalender Akademik.
- **Asosiasi milik aktor khusus (tidak diwariskan):** Input Nilai Mata Kuliah hanya milik Dosen (SIA-R08); Lihat KHS hanya milik Mahasiswa (SIA-R09). Keduanya digambar langsung dari aktor khusus masing-masing, bukan dari Civitas Akademika.
- **Arah panah:** segitiga kosong menempel pada Civitas Akademika. Karena Civitas Akademika digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas; keduanya berakhir pada Civitas Akademika.
- **Uji tiga pertanyaan:** (1) peran menggunakan fungsi yang sama persis — ya (kalender akademik); (2) kesamaan tetap berlaku selama sistem berkembang — ya (agenda resmi institusi berlaku untuk seluruh civitas); (3) nama peran umum membuat diagram lebih jelas — ya. Ketiganya ya, maka generalization aktor layak digunakan.

## 3. Katalog use case gabungan

ID use case lama tidak diganti nomornya. SIA-UC01 sampai SIA-UC06 tetap; use case baru dimulai dari SIA-UC07.

| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Tanda | Peran dalam model |
|---|---|---|---|---|---|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01 s.d. SIA-R02 (Pertemuan 2)* | Tetap | Fungsi lama (Pertemuan 2) |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R01 s.d. SIA-R02 (Pertemuan 2)* | Tetap | Fungsi lama (Pertemuan 2) |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 s.d. SIA-R06 (Pertemuan 3)* | Tetap | Menyertakan SIA-UC04; diperluas SIA-UC05 |
| SIA-UC04 | Validasi KRS | — (use case yang disertakan; tidak ada aktor langsung) | SIA-R03 s.d. SIA-R06 (Pertemuan 3)* | Tetap | Perilaku yang disertakan SIA-UC03 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R03 s.d. SIA-R06 (Pertemuan 3)* | Tetap | Tambahan bersyarat pada SIA-UC03 melalui «extend» |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R03 s.d. SIA-R06 (Pertemuan 3)* | Tetap | Fungsi lama (Pertemuan 3) |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika (diwarisi Mahasiswa dan Dosen) | SIA-R07 | Baru | Fungsi aktor umum Civitas Akademika |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08, SIA-R12 | Baru | Use case utama; direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09, SIA-R12 | Baru | Use case utama; direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10, SIA-R11 | Baru | Use case UMUM bagi SIA-UC11, SIA-UC12, SIA-UC13 |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R10, SIA-R11 | Baru | Use case KHUSUS dari SIA-UC10 |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R10, SIA-R11 | Baru | Use case KHUSUS dari SIA-UC10 |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R10, SIA-R11 | Baru | Use case KHUSUS dari SIA-UC10 |

\* Kebutuhan lama tidak berubah arti; pemetaan rinci per use case merujuk jobsheet Pertemuan 2 dan Pertemuan 3.

## 4. Keputusan generalization use case

Use case umum: **SIA-UC10 Kelola Data Mahasiswa**. Tiga use case khusus (masing-masing satu panah generalization, segitiga kosong menunjuk SIA-UC10):

| Use case khusus | Perilaku pembeda (satu kalimat) |
|---|---|
| SIA-UC11 Tambah Data Mahasiswa | Menghasilkan data mahasiswa baru yang tersimpan. |
| SIA-UC12 Ubah Data Mahasiswa | Menghasilkan data mahasiswa yang berubah. |
| SIA-UC13 Hapus Data Mahasiswa | Menghasilkan data mahasiswa yang terhapus, dengan syarat mahasiswa tidak memiliki data akademik aktif. |

- **Perilaku umum (diwarisi):** ketiganya sama-sama mengelola data mahasiswa.
- **Alasan:** ketiganya menghasilkan data mahasiswa yang terkelola, sehingga sah sebagai bentuk khusus pengelolaan data mahasiswa.
- Admin Akademik hanya dihubungkan ke SIA-UC10 (use case umum); tidak dihubungkan ke SIA-UC11, SIA-UC12, SIA-UC13.
- Antara SIA-UC10 dan ketiga use case khusus hanya dipakai generalization (tidak ada include/extend).

## 5. Collaboration dan realization

| ID | Nama collaboration (sama persis dengan nama use case) | Use case yang direalisasikan |
|---|---|---|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08: Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09: Lihat KHS |

**Alasan:** kedua use case tersebut adalah use case utama pada potongan model ini, sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini. Collaboration digambar sebagai elips garis putus-putus, tidak diberi ID use case (memakai ID SIA-CO), tidak dihubungkan ke aktor, dan relasi realization (garis putus-putus, segitiga kosong) mengarah dari collaboration menuju use case.

## 6. Spesifikasi hubungan diagram kumulatif SIA (18 hubungan)

| No | Sumber | Hubungan | Tujuan | Asal |
|---|---|---|---|---|
| 1 | Mahasiswa | Association | SIA-UC01 Lihat Jadwal Kuliah | Tetap* |
| 2 | Admin Akademik | Association | SIA-UC02 Kelola Jadwal Kuliah | Tetap* |
| 3 | Mahasiswa | Association | SIA-UC03 Ajukan KRS | Tetap* |
| 4 | Mahasiswa | Association | SIA-UC05 Unduh Bukti Pengajuan KRS | Tetap* |
| 5 | Dosen Wali | Association | SIA-UC06 Proses Keputusan KRS | Tetap* |
| 6 | SIA-UC03 Ajukan KRS | «include» | SIA-UC04 Validasi KRS | Tetap* |
| 7 | SIA-UC05 Unduh Bukti Pengajuan KRS | «extend» (condition + extension point) | SIA-UC03 Ajukan KRS | Tetap* |
| 8 | Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik | Baru |
| 9 | Mahasiswa | Generalization → | Civitas Akademika | Baru |
| 10 | Dosen | Generalization → | Civitas Akademika | Baru |
| 11 | Dosen | Association (khusus) | SIA-UC08 Input Nilai Mata Kuliah | Baru |
| 12 | Mahasiswa | Association (khusus) | SIA-UC09 Lihat KHS | Baru |
| 13 | Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa | Baru |
| 14 | SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru |
| 15 | SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru |
| 16 | SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru |
| 17 | SIA-CO01 (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah | Baru |
| 18 | SIA-CO02 (collaboration) | Realization → | SIA-UC09 Lihat KHS | Baru |

\* Mengikuti asumsi pada catatan di awal berkas ini; cocokkan dengan P02/P03 asli.

Tidak ada asosiasi warisan yang digambar ulang dari Mahasiswa atau Dosen ke SIA-UC07, dan tidak ada garis dari aktor ke collaboration.

## 7. Keterlacakan elemen baru ke kebutuhan

| Elemen baru | Jenis | Kebutuhan |
|---|---|---|
| Civitas Akademika | Aktor umum | SIA-R07 |
| Dosen | Aktor khusus | SIA-R07, SIA-R08 |
| Generalization Mahasiswa → Civitas Akademika | Relasi | SIA-R07 |
| Generalization Dosen → Civitas Akademika | Relasi | SIA-R07 |
| SIA-UC07 Lihat Kalender Akademik | Use case | SIA-R07 |
| SIA-UC08 Input Nilai Mata Kuliah | Use case | SIA-R08 |
| SIA-UC09 Lihat KHS | Use case | SIA-R09 |
| SIA-UC10 Kelola Data Mahasiswa | Use case umum | SIA-R10, SIA-R11 |
| SIA-UC11, SIA-UC12, SIA-UC13 + tiga generalization | Use case khusus | SIA-R10, SIA-R11 |
| SIA-CO01 + realization ke SIA-UC08 | Collaboration | SIA-R12 (SIA-R08) |
| SIA-CO02 + realization ke SIA-UC09 | Collaboration | SIA-R12 (SIA-R09) |

## 8. Use case description: SIA-UC08 Input Nilai Mata Kuliah

| Elemen | SIA-UC08: Input Nilai Mata Kuliah |
|---|---|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah yang diampu dosen tersimpan di sistem |
| Aktor utama | Dosen |
| Aktor pendukung | Tidak ada |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah yang diampunya |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah yang dipilih; masa perkuliahan mata kuliah tersebut telah berakhir |
| Pascakondisi berhasil | Nilai mata kuliah tersimpan untuk setiap mahasiswa yang diinput; nilai berstatus belum terpublikasi (belum tampil pada KHS) |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan; nilai yang sudah ada tidak berubah |
| Generalization | Tidak ada (bukan bagian hierarki use case) |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |
| Aturan bisnis atau asumsi | Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. KHS hanya menampilkan nilai yang sudah dipublikasikan. Rentang nilai yang sah belum ditetapkan pada tugas (pertanyaan terbuka). |

**Alur utama**

| Langkah | Tindakan dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang diampunya | Memeriksa bahwa dosen adalah pengampu mata kuliah tersebut; menampilkan daftar mahasiswa dan isian nilai |
| 2 | Mengisi nilai setiap mahasiswa | Menampung isian nilai |
| 3 | Menyimpan nilai | Memeriksa bahwa setiap nilai berada dalam rentang yang sah |
| 4 | Tidak ada | Menyimpan nilai dengan status belum terpublikasi |
| 5 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

**Alur alternatif atau pengecualian**

- **A1: Dosen bukan pengampu mata kuliah (pada langkah 1):** sistem menolak input nilai dan menampilkan pemberitahuan bahwa dosen bukan pengampu. Pascakondisi gagal berlaku; tidak ada data yang disimpan.
- **A2: Nilai di luar rentang yang sah (pada langkah 3):** sistem menolak penyimpanan, menandai isian yang tidak sah, dan meminta dosen mengoreksinya. Nilai tidak disimpan sampai semua isian berada dalam rentang yang sah; bila dosen membatalkan, pascakondisi gagal berlaku.

## 9. Use case description ringkas: SIA-UC09 Lihat KHS

| Elemen | SIA-UC09: Lihat KHS |
|---|---|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 dan SIA-R12 |
| Tujuan | Mahasiswa mengetahui hasil studinya pada semester yang nilainya sudah dipublikasikan |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi lihat KHS dan menentukan semester |
| Prasyarat | Mahasiswa telah terautentikasi |
| Ringkasan alur | Mahasiswa memilih semester; sistem menampilkan KHS yang **hanya memuat nilai yang sudah dipublikasikan**. Nilai yang belum terpublikasi tidak ditampilkan; bila semester belum memiliki nilai terpublikasi, sistem memberi tahu bahwa KHS semester tersebut belum tersedia. |
| Pascakondisi berhasil | KHS semester terpilih tampil dengan nilai terpublikasi saja |
| Pascakondisi gagal | Tidak ada KHS yang ditampilkan; data nilai tidak berubah |
| Generalization | Tidak ada (bukan bagian hierarki use case) |
| Collaboration | SIA-CO02: Lihat KHS |

## 10. Pemeriksaan terhadap checklist jobsheet

| Butir checklist | Status |
|---|---|
| Elemen Pertemuan 3 tetap ada dan tidak berubah nama (SIA-UC01 s.d. SIA-UC06, include, extend) | Ada, dengan catatan asumsi bagian aktor/condition dicocokkan dengan P03 asli |
| Asosiasi bersama digambar satu kali dari aktor umum | Ya (Civitas Akademika → SIA-UC07) |
| Setiap aktor khusus punya satu panah generalization, segitiga kosong di aktor umum | Ya (2 panah) |
| Tidak ada asosiasi warisan digambar ulang dari aktor khusus | Ya |
| Setiap use case khusus punya satu panah generalization, segitiga kosong di use case umum | Ya (3 panah) |
| Collaboration elips putus-putus, nama sama persis, tidak terhubung ke aktor | Ya |
| Realization dari collaboration menuju use case (putus-putus, segitiga kosong) | Ya (2 relasi) |
| «include» mengarah ke perilaku yang disertakan | Ya (SIA-UC03 → SIA-UC04) |
| Aktor di luar batas sistem; use case dan collaboration di dalam | Ya |
| Nama dan ID sama persis di diagram, katalog, dan deskripsi | Ya |
| Elemen baru tertelusur ke SIA-R07 s.d. SIA-R12 | Ya (bagian 7) |
| Kebutuhan yang belum dimodelkan ditandai pertanyaan terbuka | Ya (lihat `P04_SIA_kebutuhan_v01.md`, bagian 4) |
