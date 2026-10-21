# P04_SIA_kebutuhan_v01 — Kebutuhan Tugas Pertemuan 4: Sistem Informasi Akademik, Layanan Hasil Studi

Status: LATIHAN USE CASE DIAGRAM LANJUTAN (diagram kumulatif)  
Kasus: SIA | Versi: v01

## 1. Skenario

Skenario tugas berikut fiktif untuk praktikum dan berbeda dari tugas Pertemuan 2 (jadwal kuliah) dan Pertemuan 3 (pengajuan KRS).

Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

## 2. Kebutuhan baru (Tabel 4.6)

| ID | Kebutuhan tugas |
|---|---|
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa. |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS. |

Kebutuhan SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap berlaku dan tidak berubah arti; tidak disalin ulang sebagai kebutuhan baru (rujuk jobsheet Pertemuan 2 dan Pertemuan 3).

## 3. Batas dan asumsi

- Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap mempunyai identitas berbeda.
- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); tidak sama dengan jadwal kuliah pada Pertemuan 2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini fiktif untuk latihan.
- Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3. Pembayaran dan perancangan basis data berada di luar tugas ini.

## 4. Pertanyaan terbuka (belum dimodelkan, bukan dianggap selesai)

1. **Mekanisme publikasi nilai.** Tugas menyatakan nilai belum terpublikasi sampai "dinyatakan resmi oleh ketentuan tugas ini", tetapi tugas tidak menyebut siapa yang mempublikasikan, kapan, atau melalui fungsi apa. Tidak dibuat use case publikasi karena tidak ada kebutuhan SIA-R yang menyebutnya.
2. **Rentang nilai yang sah.** Alur alternatif "nilai di luar rentang yang sah ditolak" memerlukan rentang, tetapi tugas tidak menetapkannya. Rentang tidak dikarang; perlu ditetapkan oleh pemangku kepentingan.
3. **Penentuan dosen pengampu dan berakhirnya masa perkuliahan.** Sumber data penugasan pengampu dan penanda berakhirnya masa perkuliahan tidak dijelaskan di tugas (kemungkinan terkait data jadwal/perkuliahan Pertemuan 2).
4. **Pemetaan kebutuhan lama ke use case lama.** Pemetaan tepat SIA-R01 sampai SIA-R06 ke SIA-UC01 sampai SIA-UC06 (termasuk aktor yang terhubung, condition dan extension point pada extend SIA-UC05 ke SIA-UC03) harus dicocokkan dengan berkas SIA Pertemuan 2 dan Pertemuan 3 milik sendiri (lihat catatan asumsi pada `P04_SIA_skenario_v01.md`).

## 5. Hasil uji konsistensi (Langkah 8)

**Situasi A — Mahasiswa melihat kalender akademik tanpa garis asosiasi langsung dari Mahasiswa.**  
Tetap benar menurut diagram. Satu-satunya asosiasi ke SIA-UC07 Lihat Kalender Akademik digambar dari aktor umum Civitas Akademika. Mahasiswa adalah aktor khusus dari Civitas Akademika (panah generalization Mahasiswa → Civitas Akademika, segitiga kosong menunjuk Civitas Akademika), sehingga Mahasiswa mewarisi seluruh asosiasi aktor umum. Aktor khusus dapat dipakai di setiap tempat aktor umum dapat dipakai. Dosen mewarisi asosiasi yang sama dengan cara yang sama. Menggambar ulang garis dari Mahasiswa atau Dosen justru salah, karena asosiasi warisan digambar satu kali dari aktor umum.

**Situasi B — Dosen yang bukan pengampu mencoba menginput nilai.**  
Menurut deskripsi SIA-UC08 Input Nilai Mata Kuliah, prasyarat "dosen adalah pengampu mata kuliah" tidak terpenuhi (alur alternatif A1). Sistem menolak input nilai dan menampilkan pemberitahuan bahwa dosen bukan pengampu. Pascakondisi gagal berlaku: tidak ada nilai baru yang tersimpan dan tidak ada nilai yang berubah.

**Situasi C — Admin Akademik menghapus data mahasiswa yang masih memiliki data akademik aktif.**  
Menurut aturan tugas, SIA-UC13 Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Maka penghapusan harus ditolak: data mahasiswa tetap tersimpan dan tidak ada perubahan data. Aturan ini adalah pembeda perilaku khusus SIA-UC13 terhadap use case umum SIA-UC10.

## 6. Catatan review

- Pemeriksaan oleh rekan atau asisten (arah panah generalization dan realization, nama collaboration, pascakondisi): **belum dilakukan pada v01**. Temuan review dicatat pada `P04_SIA_logbook_v01.md`; bila ada perubahan isi, simpan sebagai v02 dan pertahankan v01.
