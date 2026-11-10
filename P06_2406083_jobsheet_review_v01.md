
| NO | Temuan                                                                          | Perbaikan yang di perlukan                                                                                                                           |
| -- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | Action respon sistem diletakkan di swimlane aktor manusia.                      | Pindahkan seluruh action respon sistem ke dalam swimlane Sistem.                                                                                     |
| 2  | Percabangan keputusan (decision) tidak memiliki label guard pada alur keluar.   | Tambahkan label guard berformat kurung siku [guard] pada setiap alur keluar dari decision.                                                           |
| 3  | Dua proses yang berjalan paralel disatukan menggunakan simbol merge.            | Ganti simbol merge dengan simbol join untuk menyatukan kembali alur dari fork.                                                                       |
| 4  | Collaboration dari diagram P04 digambar sebagai swimlane atau action.           | Hapus elemen collaboration dari activity diagram karena activity diagram memodelkan alur aktivitas, bukan perwujudan kelas.                          |
| 5  | Aktor Kepala Laboratorium dimasukkan ke dalam swimlane Activity Peminjaman LAB. | Hapus Kepala Laboratorium dari Activity Peminjaman, karena aktor tersebut hanya bertanggung jawab pada use case Lihat Laporan Peminjaman (LAB-UC07). |
| 6  | Nama action menggunakan istilah yang berbeda dari tabel skenario P05.           | Sesuaikan nama action menggunakan kata kerja dan objek yang sama persis dengan bunyi langkah pada skenario Pertemuan 5.                              |

---

| NO | Alasan                                                                                                                                                              |
| -- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | Swimlane (partisi aktivitas) berfungsi membagi tanggung jawab; respon sistem adalah kewenangan partisi Sistem secara eksplisit.                                     |
| 2  | Berdasarkan aturan UML 2.5.1, setiap alur keluar dari decision wajib memiliki guard yang saling lepas untuk memastikan kejelasan kondisi alur.                      |
| 3  | Simbol merge tidak menunggu alur lain selesai, sedangkan proses paralel memerlukan join agar alur berikutnya berjalan hanya setelah seluruh proses paralel selesai. |
| 4  | Collaboration merupakan konseptual perwujudan use case oleh elemen struktur dan tidak memiliki urutan kegiatan atau swimlane.                                       |
| 5  | Menambahkan aktor yang tidak relevan dengan skenario use case induk akan melanggar prinsip keterlacakan (traceability) dari skenario P05.                           |
| 6  | Konsistensi penamaan kata kerja dan objek antara skenario P05 dan action P06 wajib dijaga untuk memudahkan verifikasi dan pemeriksaan keterlacakan.                 |