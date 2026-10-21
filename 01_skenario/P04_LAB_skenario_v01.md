Batas sistem dan aturan 
•	Sistem mencatat dan menyediakan informasi; perpindahan fisik alat tidak terjadi di dalam perangkat lunak (tetap dari Pertemuan 3). 
•	Pengguna telah terautentikasi dan memiliki hak akses sesuai peran (tetap dari Pertemuan 3). 
•	Pengembalian hanya dapat dicatat untuk peminjaman berstatus Dipinjam. Peminjaman yang masih Menunggu Keputusan atau Ditolak tidak dapat dicatat pengembaliannya. 
•	Kondisi peralatan pada pengembalian dicatat dengan salah satu nilai: Baik, Rusak Ringan, atau Rusak Berat. 
•	Hapus Data Peralatan hanya untuk peralatan yang tidak sedang dipinjam dan tidak memiliki pengajuan aktif. 
•	Keterlambatan dan denda belum dimodelkan pada pertemuan ini. Tuliskan sebagai pertanyaan terbuka pada berkas kebutuhan, jangan mengarang aturan denda. 
•	Kriteria penerimaan model: semua kebutuhan LAB-R01 sampai LAB-R11 mempunyai representasi pada diagram kumulatif, arah generalization dan realization benar, dan diagram konsisten dengan deskripsinya. 

 

|  Aktor  | Kedudukan  |  Tujuan  terhadap                                                                                 sistem                                                                                |
|---------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Peminjam |    Umum    (general),  baru   |                                pada Pertemuan 4 Peran umum bagi peminjam peralatan. Mewariskan fungsinya kepada Mahasiswa dan Dosen.                                 |
|Mahasiswa|   Khusus   |   dari   Peminjam,|tetap dari Pertemuan 3 Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri. |
|  Dosen  |   Khusus   |   dari   Peminjam,|                                    baru pada Pertemuan 4 Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam).                                    |
| Petugas aboratorium|  Tetap     dari   |                              Pertemuan 3 Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan.                              |
| Kepala  Laboratorium|  Tetap     dari   |                                                               Pertemuan 3 Melihat laporan peminjaman.                                                                |


| ID       | Nama                         | use case Peran dalam model       | Sumber kebutuhan |
| :------- | :--------------------------- | :------------------------------- | ---------------- |
| LAB-UC01 | Lihat ketersediaan peralatan | Fungsi utama mahasiswa           | LAB-R01, LABR07  |
| LAB-UC02 | Kelola data peralatan        | Fungsi utama petugas             | LAB-R02, LABR08  |
| LAB-UC03 | Ajukan peminjaman            | Fungsi utama mahasiswa           | LAB-R03, LABR07  |
| LAB-UC04 | Periksa ketersediaan         | Perilaku yang disertakan UC03    | LAB-R03          |
| LAB-UC05 | Cetak bukti pengajuan        | Tambahan bersyarat pada UC03     | LAB-R04          |
| LAB-UC06 | Proses keputusan peminjaman  | Fungsi utama petugas             | LAB-R05          |
| LAB-UC07 | Lihat laporan peminjaman     | Fungsi utama kepala laboratorium | LAB-R06          |
| LAB-UC08 | Tambah Data Peralatan       |  Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02  | LAB-R08          |
| LAB-UC09 | Ubah Data Peralatan         | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02        | LAB-R08          |
| LAB-UC010 |  Hapus Data Peralatan       |  Baru pada Pertemuan 4;           | LAB-R09          |
| LAB-UC11 | Catat Pengembalian Peralatan   | Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-CO02     | LAB-R09         |
| LAB-UC12 | Periksa Kondisi Peralatan     |Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC1                        |LAB-R010
|          |                              |                                  |                  |

# Tetapkan generalization aktor 
•	Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah bentuk khusus dari Peminjam. Alasan: keduanya berbagi fungsi yang sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman. 
•	Asosiasi ke LAB-UC01 dan LAB-UC03 digambar satu kali, yaitu dari Peminjam. Jangan menggambar garis yang sama dari Mahasiswa dan dari Dosen. 
•	Asosiasi Mahasiswa ke LAB-UC05 Cetak Bukti Pengajuan tidak ikut dipindahkan dan tidak dihapus, karena fungsi itu khusus mahasiswa. Asosiasi ini menjadi contoh asosiasi tambahan milik aktor khusus. 
•	Periksa arah panah pada gambar: ujung segitiga kosong harus menempel pada Peminjam, bukan pada Mahasiswa dan bukan pada Dosen. Karena Peminjam digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas; keduanya berakhir pada Peminjam. 

# Tetapkan generalization use case 
•	LAB-UC08, LAB-UC09, dan LAB-UC10 adalah bentuk khusus dari LABUC02 Kelola Data Peralatan. Alasan: ketiganya adalah bentuk khusus pengelolaan data peralatan. 
•	Tuliskan untuk setiap use case khusus satu kalimat perilaku pembedanya. Tambah menghasilkan data peralatan baru. Ubah menghasilkan data peralatan yang berubah. Hapus menghasilkan data peralatan yang terhapus dengan syarat pada aturan studi kasus. 

|ID |	Nama collaboration (sama|dengan nama use case) 	Use case yang direalisasikan|
|-------|---------------------|---------------------------------------------------|
|LAB-CO01 |	Ajukan Peminjaman |            LAB-UC03: Ajukan Peminjaman            |
|LAB-CO02 |	Catat Pengembalian|      Peralatan 	LAB-UC11: Catat Pengembalian    Peralatan    |


