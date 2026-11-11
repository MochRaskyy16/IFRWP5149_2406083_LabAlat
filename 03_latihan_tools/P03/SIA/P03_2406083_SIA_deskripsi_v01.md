# Use Case Description — SIA-UC03 Ajukan KRS

| Elemen                | SIA-UC03 — Ajukan KRS                                            |
| :-------------------- | :--------------------------------------------------------------- |
| Tujuan                | Menghasilkan pengajuan KRS yang tersimpan                        |
| Aktor utama           | Mahasiswa                                                        |
| Sumber kebutuhan      | SIA-R03 dan SIA-R04                                              |
| Pemicu                | Mahasiswa memilih fungsi pengajuan KRS                           |
| Prasyarat             | Mahasiswa telah terautentikasi; data mata kuliah dan jadwal tersedia |
| Pascakondisi berhasil | Pengajuan KRS tersimpan berstatus menunggu persetujuan dosen wali |
| Pascakondisi gagal    | Tidak ada pengajuan KRS yang berhasil tersimpan                  |
| Include               | SIA-UC04 — Validasi KRS                                          |
| Extension point       | Konfirmasi penyimpanan / bukti pengajuan tersedia, pada langkah 6 |
| Extend                | SIA-UC05 jika [mahasiswa memilih mengunduh bukti]                |

## Alur Utama

| Langkah | Tindakan mahasiswa       | Respons sistem                                                            |
| :------ | :----------------------- | :------------------------------------------------------------------------ |
| 1       | Membuka pengajuan KRS    | Menampilkan formulir pemilihan mata kuliah                                |
| 2       | Memilih mata kuliah      | Menampung pilihan                                                         |
| 3       | Mengirim pengajuan       | Memeriksa kelengkapan data                                                |
| 4       | —                        | Menjalankan SIA-UC04 (Validasi KRS)                                       |
| 5       | —                        | Jika valid, menyimpan pengajuan dan memberikan status menunggu persetujuan |
| 6       | Melihat konfirmasi       | Menampilkan status pengajuan; mencapai extension point                    |
| 7       | Mengakhiri pengajuan     | Menutup proses pengajuan                                                  |

## Alur Alternatif / Pengecualian

| Langkah | Kondisi                           | Penanganan                                                    |
| :------ | :-------------------------------- | :------------------------------------------------------------ |
| 3a      | Data tidak lengkap                | Sistem menampilkan pesan kesalahan; kembali ke langkah 2      |
| 4a      | Validasi gagal (prasyarat/jadwal) | Sistem menampilkan alasan kegagalan; pengajuan tidak disimpan |

---

# Use Case Description — SIA-UC04 Validasi KRS

| Elemen                | SIA-UC04 — Validasi KRS                                                                         |
| :-------------------- | :----------------------------------------------------------------------------------------------- |
| Tujuan                | Memastikan pengajuan KRS memenuhi ketentuan                                                      |
| Aktor utama           | Sistem (dipanggil dari SIA-UC03)                                                                 |
| Sumber kebutuhan      | SIA-R04                                                                                          |
| Pemicu                | SIA-UC03 menjalankan validasi pada langkah 4                                                     |
| Prasyarat             | Mahasiswa telah memilih mata kuliah                                                              |
| Pascakondisi berhasil | KRS dinyatakan valid dan dapat disimpan                                                          |
| Pascakondisi gagal    | Pengajuan ditolak karena tidak lengkap, prasyarat tidak terpenuhi, atau jadwal bentrok           |
| Include               | —                                                                                                |
| Extension point       | —                                                                                                |
| Extend                | —                                                                                                |

## Alur Utama

| Langkah | Respons sistem                                          |
| :------ | :------------------------------------------------------ |
| 1       | Memeriksa kelengkapan data mata kuliah yang dipilih      |
| 2       | Memeriksa prasyarat mata kuliah                          |
| 3       | Memeriksa benturan jadwal                                |
| 4       | Mengembalikan hasil validasi ke SIA-UC03                 |

## Alur Alternatif / Pengecualian

| Langkah | Kondisi                              | Penanganan                                    |
| :------ | :----------------------------------- | :-------------------------------------------- |
| 1a      | Data mata kuliah tidak lengkap       | Mengembalikan hasil gagal: data tidak lengkap  |
| 2a      | Prasyarat mata kuliah tidak terpenuhi | Mengembalikan hasil gagal: prasyarat belum lulus |
| 3a      | Jadwal bentrok                       | Mengembalikan hasil gagal: benturan jadwal     |

---

# Use Case Description — SIA-UC05 Unduh Bukti Pengajuan KRS

| Elemen                | SIA-UC05 — Unduh bukti pengajuan KRS                             |
| :-------------------- | :--------------------------------------------------------------- |
| Tujuan                | Menyediakan bukti pengajuan KRS yang dapat diunduh               |
| Aktor utama           | Mahasiswa                                                        |
| Sumber kebutuhan      | SIA-R05                                                          |
| Pemicu                | Mahasiswa memilih mengunduh bukti pada konfirmasi penyimpanan    |
| Prasyarat             | Pengajuan KRS telah berhasil tersimpan; konfirmasi ditampilkan   |
| Pascakondisi berhasil | Bukti pengajuan berhasil diunduh                                 |
| Pascakondisi gagal    | Bukti tidak berhasil diunduh; pengajuan tetap tersimpan          |
| Include               | —                                                                |
| Extension point       | —                                                                |
| Extend                | —                                                                |

## Alur Utama

| Langkah | Tindakan mahasiswa  | Respons sistem                     |
| :------ | :------------------ | :--------------------------------- |
| 1       | Memilih unduh bukti | Menyiapkan dokumen bukti pengajuan |
| 2       | —                   | Menyajikan bukti untuk diunduh     |
| 3       | Mengunduh bukti     | Mengonfirmasi unduhan berhasil     |

---

# Use Case Description — SIA-UC06 Proses Keputusan KRS

| Elemen                | SIA-UC06 — Proses keputusan KRS                                                      |
| :-------------------- | :------------------------------------------------------------------------------------ |
| Tujuan                | Menentukan persetujuan atau penolakan pengajuan KRS                                   |
| Aktor utama           | Dosen wali                                                                            |
| Sumber kebutuhan      | SIA-R06                                                                               |
| Pemicu                | Dosen wali membuka pengajuan KRS yang menunggu persetujuan                            |
| Prasyarat             | Pengajuan KRS telah tersimpan dan berstatus menunggu persetujuan                      |
| Pascakondisi berhasil | Status KRS berubah menjadi disetujui atau ditolak, disertai catatan keputusan         |
| Pascakondisi gagal    | Keputusan gagal disimpan dan status KRS tidak berubah                                 |
| Include               | —                                                                                     |
| Extension point       | —                                                                                     |
| Extend                | —                                                                                     |

## Alur Utama

| Langkah | Tindakan dosen wali                            | Respons sistem                                      |
| :------ | :--------------------------------------------- | :-------------------------------------------------- |
| 1       | Membuka daftar pengajuan KRS                   | Menampilkan pengajuan yang menunggu persetujuan      |
| 2       | Memilih pengajuan                              | Menampilkan detail pengajuan KRS                     |
| 3       | Menyetujui atau menolak dan memberikan catatan | Menyimpan keputusan dan catatan                      |
| 4       | —                                              | Mengubah status KRS sesuai keputusan                 |

## Alur Alternatif / Pengecualian

| Langkah | Kondisi                    | Penanganan                                                    |
| :------ | :------------------------- | :------------------------------------------------------------ |
| 3a      | Dosen wali memilih menolak | Sistem menyimpan status ditolak beserta catatan penolakan     |
