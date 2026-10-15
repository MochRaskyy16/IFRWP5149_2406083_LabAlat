# DESKRIPSI SKENARIO
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

#  TABEL KEBUTUHAN
|---------|--------------------------------------------------------------------------|
| ID      |Kebutuhan tugas                                                           |
| :-------|------------------------------------------------------------------------- |
| SIA-R01 |Mahasiswa dapat melihat jadwal kuliah                                     |
| SIA-R02 |Admin akademik dapat mengelola jadwal kuliah                              |
| SIA-R03 |Mahasiswa dapat mengajukan KRS                                            |
| SIA-R04 |Sistem memvalidasi KRS sebagai bagian pengajuan                           |
| SIA-R05 |Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 |Dosen wali dapat memproses persetujuan atau penolakan KRS                 |
|---------|--------------------------------------------------------------------------|


# BATASAN SISTEM DAN ATURAN 
Batas dan asumsi:
• Pengguna telah terautentikasi.
• Data mata kuliah, prasyarat, dan jadwal tersedia.
• Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
• Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
• KRS tersimpan belum berarti disetujui.
• Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas.

# TABEL IDENTIFIKASI AKTOR
|------------|------------------------------------------------------------------------------|
| Aktor      | Tujuan terhadap sistem                                                       |
| :----------| ---------------------------------------------------------------------------- |
| Admin      | Mengelola jadwal kuliah.
| Mahasiswa  | Mengajukan KRS, Memilih mata kuliah, memilih mengunduh bukti pengajuan.      |
| Dosen      | Memeriksa pengajuan KRS mahasiswa,Menyetujui atau menolak pengajuan KRS.     |
|            | Memberikan catatan keputusan persetujuan atau penolakan.                     |
|------------|------------------------------------------------------------------------------|

# TABEL KATALOG USECASE


| ID      | Kebutuhan Tugas                                                           |
|:--------|:--------------------------------------------------------------------------|
| SIA-R01 | Mahasiswa dapat melihat jadwal kuliah                                     |
| SIA-R02 | Admin akademik dapat mengelola jadwal kuliah                              |
| SIA-R03 | Mahasiswa dapat mengajukan KRS                                            |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan                           |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS                 |

# RELASI INCLUDE
SIA-R03 «include» SIA-R04
Alasan: validasi KRS (kelengkapan, prasyarat, benturan jadwal) merupakan bagian yang selalu dijalankan dalam proses pengajuan KRS.

SIA-R06 «include» SIA-R04
Alasan: validasi KRS menjadi bagian dari proses pemeriksaan sebelum dosen wali menyetujui atau menolak pengajuan.
# RELASI EXTEND
Extension point: Bukti pengajuan tersedia.
Kondisi: [mahasiswa memilih mengunduh bukti].
Alasan: pengajuan tetap berhasil tersimpan tanpa pengunduhan bukti.

Use case: SIA-R05 Mengunduh Bukti Pengajuan «extend» SIA-R03 Mengajukan KRS

# TABEL HUBUNGAN

| Sumber         | Hubungan   | Tujuan  |
|:---------------|:-----------|:--------|
| Mahasiswa      | Asosiasi   | SIA-R01 |
| Mahasiswa      | Asosiasi   | SIA-R03 |
| Mahasiswa      | Asosiasi   | SIA-R05 |
| Dosen Wali     | Asosiasi   | SIA-R06 |
| Admin Akademik | Asosiasi   | SIA-R02 |
| SIA-R03        | «include»  | SIA-R04 |
| SIA-R06        | «include»  | SIA-R04 |
| SIA-R05        | «extend»   | SIA-R03 |