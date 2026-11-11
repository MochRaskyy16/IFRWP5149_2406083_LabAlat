# KEBUTUHAN — Sistem Informasi Akademik (SIA)

## Skenario

Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

## Tabel Kebutuhan

| ID      | Kebutuhan                                                                |
| :------ | :----------------------------------------------------------------------- |
| SIA-R03 | Mahasiswa dapat mengajukan KRS                                           |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan                          |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS                |

> Kode dimulai dari R03 agar kebutuhan jadwal SIA-R01 dan SIA-R02 dari Pertemuan 2 tetap mempunyai identitas berbeda.

## Batas dan Asumsi

- Pengguna telah terautentikasi.
- Data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
- Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
- KRS tersimpan belum berarti disetujui.
- Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas.
