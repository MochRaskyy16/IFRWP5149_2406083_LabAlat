# 2. Hasil Review

No.
Aspek yang Direview
Kriteria Kesesuaian

1

Kebutuhan dan batas sistem

Skenario, kebutuhan SIA-R03 sampai SIA-R06, asumsi, dan aturan batasan telah dicatat.

2

Identifikasi aktor

Aktor yang digunakan adalah Mahasiswa dan Dosen Wali. Admin akademik tidak ditambahkan karena pengelolaan jadwal berada di luar cakupan tugas ini.

3

Katalog use case

Setiap fungsi memiliki ID, nama, aktor terkait, dan sumber kebutuhan yang sesuai.

4

Relasi include

Use case Ajukan KRS memiliki relasi <<include>> dengan Validasi KRS karena validasi merupakan bagian wajib dari proses pengajuan.

5

Relasi extend

Use case Unduh Bukti Pengajuan KRS memiliki relasi <<extend>> dengan Ajukan KRS karena pengunduhan bersifat opsional.

6

Deskripsi Ajukan KRS

Menjelaskan pemilihan mata kuliah, proses validasi, penyimpanan pengajuan, serta alternatif ketika validasi gagal.

7

Deskripsi Validasi KRS

Menjelaskan pemeriksaan kelengkapan, prasyarat mata kuliah, dan benturan jadwal.

8

Deskripsi Unduh Bukti

Menjelaskan kondisi pengunduhan berdasarkan pilihan mahasiswa pada konfirmasi penyimpanan.

9

Deskripsi Proses Keputusan KRS

Menjelaskan proses persetujuan atau penolakan oleh dosen wali beserta catatan keputusan.

10

Konsistensi kebutuhan

Hasil analisis tidak menambahkan aturan batas SKS, pembayaran, pengisian nilai, atau kewenangan lain yang tidak disebutkan dalam skenario.