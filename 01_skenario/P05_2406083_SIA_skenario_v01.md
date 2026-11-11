# P05_2406083_SIA_skenario_v01 — Skenario Tugas Sistem Informasi Akademik, Layanan Hasil Studi

**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek  
**Pertemuan:** 05 — Skenario Use Case: Dari Diagram ke Langkah Kegiatan  
**Kasus:** Sistem Informasi Akademik (SIA) — Layanan Hasil Studi  
**Diagram Acuan:** `04_mode_analisis/P04/SIA/P04_2406083_SIA_usecase_v01.drawio`  
**Format Dokumen:** Tabel Skenario Dua Kolom (Kegiatan dan Respon Sistem)

---

## 1. Ringkasan Kasus & Struktur 9 Use Case Utama SIA

Sesuai arahan dosen dan kebutuhan sistem, Sistem Informasi Akademik (SIA) secara konseptual memiliki **9 Use Case Utama**:

| No | ID Use Case Utama | Nama Use Case | Aktor Utama | Ruang Lingkup Pertemuan | Catatan Struktur & Relasi |
|:--:|:---|:---|:---|:---:|:---|
| 1 | `SIA-UC01` | Lihat Jadwal Kuliah | Mahasiswa | Pertemuan 2 | Fungsi dasar informasi perkuliahan |
| 2 | `SIA-UC02` | Kelola Jadwal Kuliah | Admin Akademik | Pertemuan 2 | Pengelolaan data jadwal |
| 3 | `SIA-UC03` | Ajukan KRS | Mahasiswa | Pertemuan 3 | Menyertakan validasi KRS (`UC04`) |
| 4 | `SIA-UC05` | Unduh Bukti Pengajuan KRS | Mahasiswa | Pertemuan 3 | Fitur tambahan bersyarat pengajuan KRS |
| 5 | `SIA-UC06` | Proses Keputusan KRS | Dosen Wali | Pertemuan 3 | Keputusan persetujuan/penolakan KRS |
| 6 | **`SIA-UC07`** | **Lihat Kalender Akademik** | **Civitas Akademika** | **Pertemuan 4 & 5** | Diwarisi oleh Mahasiswa dan Dosen |
| 7 | **`SIA-UC08`** | **Input Nilai Mata Kuliah** | **Dosen** | **Pertemuan 4 & 5** | Direalisasikan oleh `SIA-CO01` |
| 8 | **`SIA-UC09`** | **Lihat KHS** | **Mahasiswa** | **Pertemuan 4 & 5** | Direalisasikan oleh `SIA-CO02` |
| 9 | **`SIA-UC10`** | **Kelola Data Mahasiswa** | **Admin Akademik** | **Pertemuan 4 & 5** | Use case umum yang mencakup bentuk khusus tambah (`UC11`), ubah (`UC12`), dan hapus (`UC13`) |

Tugas Pertemuan 5 memfokuskan penyusunan tabel skenario pada **4 use case utama baru** (`SIA-UC07` s.d. `SIA-UC10`) beserta rincian bentuk khusus pengelolaan datanya (`SIA-UC11` s.d. `SIA-UC13`), dengan mengacu pada kebutuhan `SIA-R07` sampai `SIA-R12`.

---

## 2. Tabel Kebutuhan Acuan (SIA-R07 s.d. SIA-R12)

| ID | Kebutuhan Tugas |
|:---|:---|
| **SIA-R07** | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| **SIA-R08** | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| **SIA-R09** | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| **SIA-R10** | Admin Akademik dapat mengelola data mahasiswa. |
| **SIA-R11** | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| **SIA-R12** | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah (`SIA-CO01`) dan Lihat KHS (`SIA-CO02`). |

---

## 3. Indeks Tabel Skenario Tugas (Sesuai Tabel 5.14 Jobsheet)

| ID | Nama Use Case | Aktor | Catatan Pemetaan Skenario |
|:---|:---|:---|:---|
| **SIA-UC07** | Lihat Kalender Akademik | Civitas Akademika | Ditulis satu kali atas nama Civitas Akademika; diwarisi oleh Mahasiswa dan Dosen. |
| **SIA-UC08** | Input Nilai Mata Kuliah | Dosen | Prasyarat: dosen pengampu mata kuliah; alur alternatif: nilai di luar rentang sah ditolak; direalisasikan `SIA-CO01`. |
| **SIA-UC09** | Lihat KHS | Mahasiswa | Hanya menampilkan nilai yang sudah dipublikasikan; direalisasikan `SIA-CO02`. |
| **SIA-UC10** | Kelola Data Mahasiswa | Admin Akademik | Skenario umum pengelolaan bersama yang dirujuk oleh UC11, UC12, dan UC13. |
| **SIA-UC11** | Tambah Data Mahasiswa | Admin Akademik | Bentuk khusus dari UC10; perilaku pembeda: data mahasiswa baru tersimpan. |
| **SIA-UC12** | Ubah Data Mahasiswa | Admin Akademik | Bentuk khusus dari UC10; perilaku pembeda: data mahasiswa berubah. |
| **SIA-UC13** | Hapus Data Mahasiswa | Admin Akademik | Bentuk khusus dari UC10; perilaku pembeda: data mahasiswa terhapus; syarat: tidak ada data akademik aktif. |

---

## 4. Tabel Skenario Use Case Tugas Akademik

### Tabel Skenario SIA-UC07: Lihat Kalender Akademik

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC07 Lihat Kalender Akademik |
| **Aktor** | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen) |
| **Tujuan** | Civitas Akademika mengetahui agenda resmi institusi pada semester aktif |
| **Deskripsi** | Aktor umum Civitas Akademika membuka kalender akademik, memilih agenda, lalu sistem menampilkan rincian agenda. Perilaku ini diwarisi oleh Mahasiswa dan Dosen |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Civitas Akademika membuka fungsi Lihat Kalender Akademik | 2. Sistem menampilkan kalender akademik semester aktif: awal semester, batas KRS, masa ujian, dan agenda resmi lain |
| 3. Civitas Akademika memilih satu agenda | 4. Sistem menampilkan rincian agenda: nama agenda, tanggal mulai, tanggal selesai, dan keterangan |
| **Skenario Alternative** | |
| 5. Kalender semester aktif belum tersedia (cabang dari langkah 2) | 6. Sistem menampilkan pesan “Kalender akademik belum tersedia” |
| 7. Agenda yang dipilih sudah berakhir (cabang dari langkah 4) | 8. Sistem menampilkan rincian agenda beserta status “Selesai” |
| **Skenario Akhir** | Use case selesai jika kalender atau rincian agenda ditampilkan; jika data belum tersedia, use case selesai dengan pesan informasi |

*Keterangan tabel:* Ditulis satu kali atas nama aktor umum Civitas Akademika dan diwarisi oleh Mahasiswa dan Dosen.

---

### Tabel Skenario SIA-UC08: Input Nilai Mata Kuliah

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC08 Input Nilai Mata Kuliah |
| **Aktor** | Dosen |
| **Tujuan** | Nilai mata kuliah yang diampu tersimpan dan siap dipublikasikan |
| **Deskripsi** | Dosen memilih mata kuliah dan kelas yang diampu, mengisi nilai mahasiswa, lalu sistem memvalidasi rentang nilai sebelum menyimpan |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Dosen membuka fungsi Input Nilai Mata Kuliah | 2. Sistem menampilkan daftar mata kuliah yang diampu dosen tersebut |
| 3. Dosen memilih mata kuliah dan kelas | 4. Sistem menampilkan daftar mahasiswa peserta kelas beserta kolom nilai |
| 5. Dosen mengisi nilai mahasiswa | 6. Dosen menyimpan isian nilai |
| 7. Dosen mengonfirmasi penyimpanan nilai | 8. Sistem memvalidasi kelengkapan dan rentang nilai yang sah, menyimpan nilai berstatus Belum Dipublikasikan, dan menampilkan pesan berhasil |
| **Skenario Alternative** | |
| 9. Dosen memilih mata kuliah yang bukan ampuannya (cabang dari langkah 3) | 10. Sistem menolak akses dan menampilkan pesan bahwa dosen bukan pengampu mata kuliah tersebut |
| 11. Nilai di luar rentang yang sah (cabang dari langkah 8) | 12. Sistem menolak penyimpanan, menandai isian yang tidak sah, dan meminta dosen mengoreksi nilai |
| 13. Sebagian nilai mahasiswa belum diisi (cabang dari langkah 8) | 14. Sistem menyimpan data sebagai draf sementara dan memberi tanda mahasiswa yang nilainya belum terisi |
| **Skenario Akhir** | Use case selesai jika nilai tersimpan dengan status Belum Dipublikasikan; jika validasi gagal, tidak ada perubahan data nilai |

*Keterangan tabel:* Use case ini direalisasikan oleh collaboration `SIA-CO01: Input Nilai Mata Kuliah`. Collaboration tidak memiliki langkah kegiatan mandiri.

---

### Tabel Skenario SIA-UC09: Lihat KHS

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC09 Lihat KHS |
| **Aktor** | Mahasiswa |
| **Tujuan** | Mahasiswa memperoleh Kartu Hasil Studi semester yang nilainya sudah dipublikasikan |
| **Deskripsi** | Mahasiswa memilih semester, sistem memeriksa status publikasi nilai, lalu menampilkan KHS beserta Indeks Prestasi |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Mahasiswa membuka fungsi Lihat KHS | 2. Sistem menampilkan pilihan semester |
| 3. Mahasiswa memilih semester yang ingin dilihat | 4. Sistem memeriksa status publikasi nilai pada semester terpilih |
| 5. Mahasiswa mengonfirmasi tampilan KHS | 6. Sistem menampilkan KHS berisi daftar mata kuliah, SKS, nilai huruf/angka, dan Indeks Prestasi semester yang nilainya sudah resmi dipublikasikan |
| **Skenario Alternative** | |
| 7. Nilai semester terpilih belum dipublikasikan (cabang dari langkah 4) | 8. Sistem menampilkan pesan bahwa nilai semester tersebut belum dipublikasikan dan KHS tidak ditampilkan |
| 9. Mahasiswa memilih semester yang belum pernah ditempuh (cabang dari langkah 4) | 10. Sistem menampilkan pesan bahwa tidak ditemukan data akademik pada semester tersebut |
| **Skenario Akhir** | Use case selesai jika KHS semester terpilih dengan nilai terpublikasi ditampilkan; jika nilai belum dipublikasikan, use case selesai dengan pesan informasi |

*Keterangan tabel:* Use case ini direalisasikan oleh collaboration `SIA-CO02: Lihat KHS`. Sesuai aturan tugas, hanya nilai yang sudah dipublikasikan yang ditampilkan pada KHS.

---

### Tabel Skenario SIA-UC10: Kelola Data Mahasiswa (Use Case Umum)

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC10 Kelola Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa terpelihara melalui satu fungsi pengelolaan bersama (tambah, ubah, dan hapus) |
| **Deskripsi** | Admin Akademik membuka fungsi pengelolaan data mahasiswa dan memilih bentuk pengelolaan; alur khusus pembeda ditangani oleh SIA-UC11, SIA-UC12, dan SIA-UC13 |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Kelola Data Mahasiswa | 2. Sistem menampilkan daftar mahasiswa beserta pilihan aksi Tambah, Ubah, dan Hapus |
| 3. Admin Akademik memilih aksi pengelolaan yang diinginkan | 4. Sistem menjalankan use case khusus terpilih: SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data Mahasiswa, atau SIA-UC13 Hapus Data Mahasiswa |
| 5. Admin Akademik menyelesaikan aksi | 6. Sistem memperbarui dan menampilkan kembali daftar data mahasiswa terbaru |
| **Skenario Alternative** | |
| 7. Admin Akademik membatalkan pilihan aksi pengelolaan (cabang dari langkah 3) | 8. Sistem menutup pilihan dan kembali ke tampilan daftar data mahasiswa tanpa ada perubahan |
| 9. Data mahasiswa yang dicari tidak ditemukan pada daftar (cabang dari langkah 2) | 10. Sistem menampilkan pesan “Data mahasiswa tidak ditemukan” |
| **Skenario Akhir** | Use case selesai setelah aksi pengelolaan khusus selesai dijalankan dan data mahasiswa terbarui |

*Keterangan tabel:* Use case umum bagi `SIA-UC11`, `SIA-UC12`, dan `SIA-UC13`. Admin Akademik hanya dihubungkan ke use case umum ini pada diagram P04.

---

### Tabel Skenario SIA-UC11: Tambah Data Mahasiswa (Use Case Khusus)

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC11 Tambah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa baru tersimpan pada sistem |
| **Deskripsi** | Use case khusus dari Kelola Data Mahasiswa. Admin Akademik mengisi formulir data mahasiswa baru dan sistem memvalidasi keunikan NIM sebelum menyimpan |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih aksi Tambah Data Mahasiswa | 2. Sistem menampilkan formulir isian data mahasiswa baru |
| 3. Admin Akademik mengisi NIM, nama, program studi, angkatan, dan status | 4. Admin Akademik menyimpan data formulir |
| 5. Admin Akademik mengonfirmasi penyimpanan | 6. Sistem memvalidasi kelengkapan data dan keunikan NIM, menyimpan data mahasiswa baru, dan menampilkan konfirmasi berhasil |
| **Skenario Alternative** | |
| 7. NIM mahasiswa sudah terdaftar pada sistem (cabang dari langkah 6) | 8. Sistem menolak penyimpanan dan menampilkan pesan bahwa NIM sudah digunakan |
| 9. Field data wajib belum lengkap (cabang dari langkah 6) | 10. Sistem menampilkan penanda field yang belum diisi dan data tidak disimpan |
| **Skenario Akhir** | Use case selesai jika data mahasiswa baru berhasil tersimpan; jika validasi gagal, tidak ada data baru yang tersimpan |

*Keterangan tabel:* Use case khusus dari `SIA-UC10`. Perilaku pembeda: data mahasiswa baru tersimpan. Langkah umum mengikuti Tabel skenario `SIA-UC10`.

---

### Tabel Skenario SIA-UC12: Ubah Data Mahasiswa (Use Case Khusus)

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC12 Ubah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Perubahan data mahasiswa tersimpan pada sistem |
| **Deskripsi** | Use case khusus dari Kelola Data Mahasiswa. Admin Akademik memilih data mahasiswa, memperbarui data yang diperlukan, dan sistem menyimpan perubahan |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih satu data mahasiswa pada daftar | 2. Sistem menampilkan formulir dengan data mahasiswa terpilih saat ini |
| 3. Admin Akademik mengubah field data yang diperlukan | 4. Admin Akademik menekan tombol simpan perubahan |
| 5. Admin Akademik mengonfirmasi perubahan | 6. Sistem memeriksa keabsahan data, menyimpan perubahan data mahasiswa, dan menampilkan konfirmasi berhasil |
| **Skenario Alternative** | |
| 7. Tidak ada perubahan yang dilakukan pada data (cabang dari langkah 4) | 8. Sistem menutup formulir tanpa melakukan proses penyimpanan |
| 9. NIM diubah menjadi NIM lain yang sudah terdaftar (cabang dari langkah 6) | 10. Sistem menolak penyimpanan dan menampilkan pesan konflik NIM |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa berhasil tersimpan; jika validasi gagal, data mahasiswa tidak berubah |

*Keterangan tabel:* Use case khusus dari `SIA-UC10`. Perilaku pembeda: data mahasiswa berubah. Langkah umum mengikuti Tabel skenario `SIA-UC10`.

---

### Tabel Skenario SIA-UC13: Hapus Data Mahasiswa (Use Case Khusus)

| Elemen | Keterangan |
|:---|:---|
| **Nama use case** | SIA-UC13 Hapus Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa yang tidak memiliki data akademik aktif terhapus dari sistem |
| **Deskripsi** | Use case khusus dari Kelola Data Mahasiswa. Admin Akademik mengonfirmasi penghapusan, sistem memverifikasi syarat tidak adanya data akademik aktif, lalu menghapus data |

| Kegiatan | Respon sistem |
|:---|:---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih aksi Hapus pada data mahasiswa terpilih | 2. Sistem menampilkan kotak dialog konfirmasi penghapusan beserta rincian data mahasiswa |
| 3. Admin Akademik mengonfirmasi penghapusan | 4. Sistem memeriksa apakah mahasiswa yang bersangkutan memiliki data akademik aktif |
| 5. Admin Akademik menyetujui peringatan final | 6. Sistem memverifikasi syarat terpenuhi, menghapus data mahasiswa dari sistem, dan menampilkan pesan berhasil |
| **Skenario Alternative** | |
| 7. Admin Akademik membatalkan penghapusan data (cabang dari langkah 3) | 8. Sistem menutup kotak konfirmasi dan data mahasiswa tetap tersimpan |
| 9. Mahasiswa memiliki data akademik aktif (cabang dari langkah 4) | 10. Sistem menolak penghapusan dan menampilkan pesan bahwa data mahasiswa masih memiliki catatan akademik aktif |
| **Skenario Akhir** | Use case selesai jika data mahasiswa berhasil terhapus; jika mahasiswa memiliki data akademik aktif atau dibatalkan, data tidak terhapus |

*Keterangan tabel:* Use case khusus dari `SIA-UC10`. Perilaku pembeda: data mahasiswa terhapus, dengan syarat tidak memiliki data akademik aktif (sesuai aturan tugas).

---

## 5. Checklist Evaluasi Mandiri Tugas SIA (Checklist Bagian C.4)

| No | Kriteria Evaluasi | Status | Bukti pada Dokumen Ini |
|:--:|:---|:---:|:---|
| 1 | Seluruh field tabel skenario terisi lengkap | ✅ Terpenuhi | Nama use case, Aktor, Tujuan, Deskripsi, Kegiatan, Respon sistem, Skenario Normal, Alternative, dan Akhir terisi 100%. |
| 2 | Satu aksi per langkah; penomoran berlanjut | ✅ Terpenuhi | Penomoran langkah pada Skenario Alternative melanjutkan nomor terakhir Skenario Normal pada seluruh tabel. |
| 3 | Pemisahan kolom Kegiatan vs Respon sistem | ✅ Terpenuhi | Kolom Kegiatan murni aksi aktor; kolom Respon sistem murni reaksi sistem. |
| 4 | Data disebut secara eksplisit | ✅ Terpenuhi | Menyebutkan NIM, nama, angkatan, nilai huruf/angka, IP, status Belum Dipublikasikan, status Selesai. |
| 5 | Generalization aktor diterapkan | ✅ Terpenuhi | `SIA-UC07` ditulis satu kali atas nama `Civitas Akademika (berlaku untuk Mahasiswa dan Dosen)`. |
| 6 | Generalization use case diterapkan | ✅ Terpenuhi | `SIA-UC10` memuat skenario umum; `SIA-UC11`, `UC12`, `UC13` hanya memuat langkah pembeda dan merujuk ke `UC10`. |
| 7 | Collaboration disebutkan pada keterangan | ✅ Terpenuhi | `SIA-CO01` pada keterangan `SIA-UC08`; `SIA-CO02` pada keterangan `SIA-UC09`. |
| 8 | Setiap tabel memiliki Alternative & Akhir | ✅ Terpenuhi | Semua 7 tabel memiliki jalur cabang alternatif dan kalimat kondisi selesai pada Skenario Akhir. |
| 9 | Nama, ID, aktor konsisten dengan diagram P04 | ✅ Terpenuhi | 100% konsisten dengan `P04_2406083_SIA_usecase_v01.drawio`. |
| 10 | Diagram acuan P04 tidak diubah | ✅ Terpenuhi | Diagram kumulatif P04 tetap utuh dan dijadikan acuan murni. |
