# P04_LAB_skenario_v01 — Model Studi Kasus Pertemuan 4: Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus

Diagram: `04_model_analisis/P04/LAB/P04_2406083_LAB_usecase_v01.drawio` (ekspor `.png` dengan versi yang sama).
Diagram bersifat kumulatif: memuat seluruh diagram Pertemuan 3 (LAB-UC01 s.d. LAB-UC07) ditambah elemen baru Pertemuan 4.

## 1. Aktor

| Aktor                | Kedudukan                                  | Tujuan terhadap sistem                                                                                                                                          |
| :------------------- | :----------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Peminjam             | Umum (general), baru pada Pertemuan 4      | Peran umum bagi peminjam peralatan. Mewariskan fungsinya (Lihat Ketersediaan Peralatan dan Ajukan Peminjaman) kepada Mahasiswa dan Dosen.                       |
| Mahasiswa            | Khusus dari Peminjam, tetap dari Pertemuan 3 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri.                  |
| Dosen                | Khusus dari Peminjam, baru pada Pertemuan 4 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam).                                                                                        |
| Petugas Laboratorium | Tetap dari Pertemuan 3                     | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan.                                                                  |
| Kepala Laboratorium  | Tetap dari Pertemuan 3                     | Melihat laporan peminjaman.                                                                                                                                     |

Kelima aktor digambar di luar batas sistem. Aktor baru: Peminjam dan Dosen. Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium tetap seperti Pertemuan 3.

## 2. Keputusan generalization aktor

Hierarki satu tingkat: Mahasiswa → Peminjam dan Dosen → Peminjam.

- **Keputusan 1:** Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah bentuk khusus dari Peminjam. **Alasan:** keduanya berbagi fungsi yang sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman (LAB-R07).
- **Keputusan 2:** Asosiasi ke LAB-UC01 Lihat Ketersediaan Peralatan dan LAB-UC03 Ajukan Peminjaman digambar satu kali, dari Peminjam. Tidak ada garis yang sama dari Mahasiswa maupun dari Dosen.
- **Asosiasi khusus Mahasiswa:** Mahasiswa → LAB-UC05 Cetak Bukti Pengajuan tetap digambar langsung dari Mahasiswa (fungsi khusus mahasiswa, tidak diwariskan ke Dosen).
- **Arah panah:** segitiga kosong menempel pada Peminjam. Panah dari Mahasiswa dan panah dari Dosen keduanya berakhir pada Peminjam.
- **Uji tiga pertanyaan:** (1) kedua peran menggunakan fungsi yang sama — ya; (2) kesamaan tetap berlaku — ya; (3) nama peran umum membuat diagram lebih jelas — ya. Ketiganya ya, maka generalization aktor layak digunakan.

## 3. Katalog use case gabungan

ID lama tidak diganti. LAB-UC01 s.d. LAB-UC07 tetap; use case baru dimulai dari LAB-UC08.

| ID       | Nama use case                | Peran dalam model                                                                     | Sumber kebutuhan |
| :------- | :--------------------------- | :------------------------------------------------------------------------------------ | :--------------- |
| LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap dari Pertemuan 3; fungsi aktor umum Peminjam                                    | LAB-R01, LAB-R07 |
| LAB-UC02 | Kelola Data Peralatan        | Tetap dari Pertemuan 3; use case UMUM bagi LAB-UC08, LAB-UC09, LAB-UC10               | LAB-R02, LAB-R08 |
| LAB-UC03 | Ajukan Peminjaman            | Tetap dari Pertemuan 3; fungsi aktor umum Peminjam; menyertakan LAB-UC04; direalisasikan LAB-CO01 | LAB-R03, LAB-R07 |
| LAB-UC04 | Periksa Ketersediaan         | Tetap dari Pertemuan 3; perilaku yang disertakan LAB-UC03                              | LAB-R03          |
| LAB-UC05 | Cetak Bukti Pengajuan        | Tetap dari Pertemuan 3; tambahan bersyarat pada LAB-UC03 melalui «extend»             | LAB-R04          |
| LAB-UC06 | Proses Keputusan Peminjaman  | Tetap dari Pertemuan 3; fungsi utama petugas                                           | LAB-R05          |
| LAB-UC07 | Lihat Laporan Peminjaman     | Tetap dari Pertemuan 3; fungsi utama kepala laboratorium                               | LAB-R06          |
| LAB-UC08 | Tambah Data Peralatan        | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02                                   | LAB-R08          |
| LAB-UC09 | Ubah Data Peralatan          | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02                                   | LAB-R08          |
| LAB-UC10 | Hapus Data Peralatan         | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02                                   | LAB-R08          |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-CO02                   | LAB-R09          |
| LAB-UC12 | Periksa Kondisi Peralatan    | Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC11                               | LAB-R10          |

## 4. Keputusan generalization use case

Use case umum: **LAB-UC02 Kelola Data Peralatan**. Tiga use case khusus (masing-masing satu panah generalization, segitiga kosong menunjuk LAB-UC02):

| Use case khusus                  | Perilaku pembeda (satu kalimat)                                                                  |
| :------------------------------- | :----------------------------------------------------------------------------------------------- |
| LAB-UC08 Tambah Data Peralatan   | Menghasilkan data peralatan baru yang tersimpan.                                                 |
| LAB-UC09 Ubah Data Peralatan    | Menghasilkan data peralatan yang berubah.                                                        |
| LAB-UC10 Hapus Data Peralatan   | Menghasilkan data peralatan yang terhapus, dengan syarat peralatan tidak sedang dipinjam dan tidak memiliki pengajuan aktif. |

- **Perilaku umum (diwarisi):** ketiganya sama-sama mengelola data peralatan.
- **Alasan:** ketiganya menghasilkan data peralatan yang terkelola, sehingga sah sebagai bentuk khusus pengelolaan data peralatan.
- Petugas Laboratorium dihubungkan ke LAB-UC02 (use case umum); tidak dihubungkan langsung ke LAB-UC08, LAB-UC09, LAB-UC10.

## 5. Collaboration dan realization

| ID       | Nama collaboration (sama persis dengan nama use case) | Use case yang direalisasikan              |
| :------- | :---------------------------------------------------- | :---------------------------------------- |
| LAB-CO01 | Ajukan Peminjaman                                     | LAB-UC03: Ajukan Peminjaman               |
| LAB-CO02 | Catat Pengembalian Peralatan                          | LAB-UC11: Catat Pengembalian Peralatan    |

**Alasan:** kedua use case tersebut adalah use case utama pada potongan model ini, sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini. Collaboration digambar sebagai elips garis putus-putus, tidak diberi ID use case (memakai ID LAB-CO), tidak dihubungkan ke aktor, dan relasi realization (garis putus-putus, segitiga kosong) mengarah dari collaboration menuju use case.

## 6. Perbandingan diagram Pertemuan 3 dan diagram Pertemuan 4

| Kelompok                              | Isi                                                                                                                                                                                                                                                                                                             |
| :------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tetap sama dari Pertemuan 3           | Aktor Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium; use case LAB-UC01 s.d. LAB-UC07; relasi «include» LAB-UC03 ke LAB-UC04; relasi «extend» LAB-UC05 ke LAB-UC03 lengkap dengan condition [mahasiswa memilih cetak] dan extension point Bukti pengajuan tersedia; asosiasi Petugas Laboratorium ke LAB-UC02 dan LAB-UC06; asosiasi Kepala Laboratorium ke LAB-UC07; asosiasi Mahasiswa ke LAB-UC05. |
| Berubah karena generalization aktor   | Asosiasi ke LAB-UC01 dan LAB-UC03 yang pada Pertemuan 3 digambar dari Mahasiswa kini digambar satu kali dari Peminjam. Fungsi mahasiswa tidak hilang: mahasiswa mewarisinya dari Peminjam. Inilah satu-satunya perubahan garis pada diagram lama, dan alasannya adalah aturan generalization, bukan penghapusan fungsi. |
| Ditambah pada Pertemuan 4             | Aktor Peminjam dan Dosen; dua generalization aktor; use case LAB-UC08, LAB-UC09, LAB-UC10 beserta tiga generalization use case ke LAB-UC02; use case LAB-UC11 dan LAB-UC12 beserta relasi «include» di antara keduanya dan asosiasi Petugas Laboratorium ke LAB-UC11; collaboration LAB-CO01 dan LAB-CO02 beserta dua relasi realization. |

## 7. Spesifikasi hubungan diagram kumulatif LAB (17 hubungan)

| No | Sumber                              | Hubungan                                           | Tujuan                                   |
| :- | :---------------------------------- | :------------------------------------------------- | :--------------------------------------- |
| 1  | Peminjam                            | Association                                        | LAB-UC01 Lihat Ketersediaan Peralatan    |
| 2  | Peminjam                            | Association                                        | LAB-UC03 Ajukan Peminjaman               |
| 3  | Mahasiswa                           | Association (khusus, tetap dari Pertemuan 3)        | LAB-UC05 Cetak Bukti Pengajuan           |
| 4  | Mahasiswa                           | Generalization →                                   | Peminjam                                 |
| 5  | Dosen                               | Generalization →                                   | Peminjam                                 |
| 6  | Petugas Laboratorium                | Association                                        | LAB-UC02 Kelola Data Peralatan           |
| 7  | Petugas Laboratorium                | Association                                        | LAB-UC06 Proses Keputusan Peminjaman     |
| 8  | Petugas Laboratorium                | Association                                        | LAB-UC11 Catat Pengembalian Peralatan    |
| 9  | Kepala Laboratorium                 | Association                                        | LAB-UC07 Lihat Laporan Peminjaman        |
| 10 | LAB-UC03 Ajukan Peminjaman          | «include» (tetap dari Pertemuan 3)                 | LAB-UC04 Periksa Ketersediaan            |
| 11 | LAB-UC05 Cetak Bukti Pengajuan      | «extend» (tetap dari Pertemuan 3)                  | LAB-UC03 Ajukan Peminjaman               |
| 12 | LAB-UC08 Tambah Data Peralatan      | Generalization →                                   | LAB-UC02 Kelola Data Peralatan           |
| 13 | LAB-UC09 Ubah Data Peralatan        | Generalization →                                   | LAB-UC02 Kelola Data Peralatan           |
| 14 | LAB-UC10 Hapus Data Peralatan       | Generalization →                                   | LAB-UC02 Kelola Data Peralatan           |
| 15 | LAB-UC11 Catat Pengembalian Peralatan | «include»                                         | LAB-UC12 Periksa Kondisi Peralatan       |
| 16 | LAB-CO01 (collaboration)            | Realization →                                      | LAB-UC03 Ajukan Peminjaman               |
| 17 | LAB-CO02 (collaboration)            | Realization →                                      | LAB-UC11 Catat Pengembalian Peralatan    |

Catatan: Kepala Laboratorium hanya terhubung dengan LAB-UC07. LAB-UC07 tidak mempunyai relasi lain (tidak ada include, extend, generalization, atau realization). Tidak ada asosiasi warisan yang digambar ulang dari Mahasiswa atau Dosen, dan tidak ada garis dari aktor ke collaboration.

## 8. Keterlacakan elemen baru ke kebutuhan

| Elemen baru                                               | Jenis              | Kebutuhan        |
| :-------------------------------------------------------- | :------------------ | :--------------- |
| Peminjam                                                  | Aktor umum          | LAB-R07          |
| Dosen                                                     | Aktor khusus        | LAB-R07          |
| Generalization Mahasiswa → Peminjam                       | Relasi              | LAB-R07          |
| Generalization Dosen → Peminjam                           | Relasi              | LAB-R07          |
| LAB-UC08 Tambah Data Peralatan                            | Use case khusus     | LAB-R08          |
| LAB-UC09 Ubah Data Peralatan                              | Use case khusus     | LAB-R08          |
| LAB-UC10 Hapus Data Peralatan                             | Use case khusus     | LAB-R08          |
| Generalization LAB-UC08, UC09, UC10 → LAB-UC02            | Relasi              | LAB-R08          |
| LAB-UC11 Catat Pengembalian Peralatan                     | Use case            | LAB-R09          |
| LAB-UC12 Periksa Kondisi Peralatan                        | Use case            | LAB-R10          |
| «include» LAB-UC11 → LAB-UC12                            | Relasi              | LAB-R10          |
| LAB-CO01 + realization ke LAB-UC03                        | Collaboration       | LAB-R11          |
| LAB-CO02 + realization ke LAB-UC11                        | Collaboration       | LAB-R11          |
