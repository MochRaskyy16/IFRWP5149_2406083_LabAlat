# DESKRIPSI SKENARIO

Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

# TABEL KEBUTUHAN

| ID      | Kebutuhan                                                                |
| :------ | :----------------------------------------------------------------------- |
| SIA-R03 | Mahasiswa dapat mengajukan KRS                                           |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan                          |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS                |

# BATASAN SISTEM DAN ATURAN

- Pengguna telah terautentikasi.
- Data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
- Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
- KRS tersimpan belum berarti disetujui.
- Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas.

# TABEL IDENTIFIKASI AKTOR

| Aktor      | Tujuan terhadap sistem                                                    |
| :--------- | :------------------------------------------------------------------------ |
| Mahasiswa  | Mengajukan KRS, memilih mata kuliah, memilih mengunduh bukti pengajuan    |
| Dosen wali | Menyetujui atau menolak pengajuan KRS dan memberikan catatan keputusan    |

# TABEL KATALOG USE CASE

| ID       | Nama use case              | Aktor terkait | Sumber kebutuhan |
| :------- | :------------------------- | :------------ | :--------------- |
| SIA-UC03 | Ajukan KRS                 | Mahasiswa     | SIA-R03          |
| SIA-UC04 | Validasi KRS               | Sistem        | SIA-R04          |
| SIA-UC05 | Unduh bukti pengajuan KRS  | Mahasiswa     | SIA-R05          |
| SIA-UC06 | Proses keputusan KRS       | Dosen wali    | SIA-R06          |

# RELASI INCLUDE

SIA-UC03 «include» SIA-UC04
Alasan: validasi KRS (kelengkapan, prasyarat, benturan jadwal) merupakan bagian yang selalu dijalankan dalam proses pengajuan KRS.

# RELASI EXTEND

SIA-UC05 «extend» SIA-UC03
Extension point: Konfirmasi penyimpanan / bukti pengajuan tersedia.
Kondisi: [mahasiswa memilih mengunduh bukti].
Alasan: pengajuan tetap berhasil tersimpan tanpa pengunduhan bukti.

# TABEL HUBUNGAN

| Sumber     | Hubungan  | Tujuan   |
| :--------- | :-------- | :------- |
| Mahasiswa  | Asosiasi  | SIA-UC03 |
| Mahasiswa  | Asosiasi  | SIA-UC05 |
| Dosen wali | Asosiasi  | SIA-UC06 |
| SIA-UC03   | «include» | SIA-UC04 |
| SIA-UC05   | «extend»  | SIA-UC03 |
