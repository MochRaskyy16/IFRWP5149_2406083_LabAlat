# P05_2406083_LAB_skenario_v01 — Lembar Telaah Skenario Studi Kasus Laboratorium

**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek  
**Pertemuan:** 05 — Skenario Use Case: Dari Diagram ke Langkah Kegiatan  
**Kasus:** Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus (LAB)  
**Diagram Acuan:** `04_mode_analisis/P04/LAB/P04_2406083_LAB_usecase_v01.drawio` (5 Aktor, 12 Use Case, 2 Collaboration, 17 Hubungan)  
**Deliverable:** Lembar telaah 12 tabel skenario studi kasus terhadap diagram acuan kumulatif Pertemuan 4.

---

## 1. Pendahuluan dan Acuan Model

Studi kasus ini memakai diagram kumulatif Pertemuan 4 sebagai acuan. Kebutuhan `LAB-R01` sampai `LAB-R11` dan spesifikasi 17 hubungan pada diagram dirujuk dari Jobsheet Pertemuan 4 (Tabel 4.5); tidak ada kebutuhan baru dan tidak ada use case baru pada pertemuan ini. Diagram acuan tidak diubah.

Pekerjaan praktikum pada studi kasus ini adalah **menelaah ke-12 tabel skenario laboratorium** terhadap diagram acuan, memastikan:
1. Aktor pada baris *Aktor* sama persis dengan aktor pada diagram.
2. Setiap langkah kunci menelusur ke satu relasi pada diagram (*asosiasi*, *include*, *extend*, *generalization*, atau *realization*).
3. ID, nama use case, condition, dan extension point tertulis sama persis dengan diagram.
4. Catatan khusus use case Kepala Laboratorium (`LAB-UC07`) berdiri sendiri tanpa relasi ke use case lain.

---

## 2. Matriks Penelusuran 12 Tabel Skenario LAB terhadap Diagram P04

| No | ID Use Case | Nama Use Case | Aktor Terkait | Relasi Diagram yang Ditelusur | Hasil Pencocokan terhadap Diagram P04 |
|---|---|---|---|---|---|
| 1 | `LAB-UC01` | Lihat Ketersediaan Peralatan | Peminjam (berlaku untuk Mahasiswa dan Dosen) | Asosiasi dari aktor umum `Peminjam` | **Cocok.** Ditulis satu kali atas nama aktor umum Peminjam; diwarisi oleh Mahasiswa dan Dosen tanpa menggambar ulang asosiasi. |
| 2 | `LAB-UC02` | Kelola Data Peralatan | Petugas Laboratorium | Asosiasi Petugas Laboratorium; Generalization use case umum bagi `UC08`, `UC09`, `UC10` | **Cocok.** Bertindak sebagai use case umum pengelolaan bersama. Langkah bersama dirujuk oleh tabel khusus. |
| 3 | `LAB-UC03` | Ajukan Peminjaman | Peminjam (berlaku untuk Mahasiswa dan Dosen) | Asosiasi `Peminjam`; «include» ke `LAB-UC04`; «extend» dari `LAB-UC05`; Realization dari `LAB-CO01` | **Cocok.** Include `LAB-UC04` menjadi langkah rujukan 2 pada Skenario Normal; extend `LAB-UC05` menjadi langkah cabang 11–12 pada Skenario Alternative lengkap dengan condition `[mahasiswa memilih cetak]` dan extension point `Bukti pengajuan tersedia`. Collaboration `LAB-CO01` disebut pada keterangan. |
| 4 | `LAB-UC04` | Periksa Ketersediaan | Sistem / Peminjam (berjalan di dalam `LAB-UC03`) | «include» dari `LAB-UC03` | **Cocok.** Dipanggil di dalam alur pengajuan langkah 2. Tidak memiliki interaksi langsung dari luar dengan aktor. |
| 5 | `LAB-UC05` | Cetak Bukti Pengajuan | Mahasiswa (asosiasi khusus) | «extend» ke `LAB-UC03`; Asosiasi khusus dari `Mahasiswa` | **Cocok.** Memiliki extension point `Bukti pengajuan tersedia` dan condition `[mahasiswa memilih cetak]`. Asosiasi hanya dimiliki Mahasiswa (tidak diwariskan ke Dosen). Pengajuan tetap berhasil tanpa pencetakan bukti. |
| 6 | `LAB-UC06` | Proses Keputusan Peminjaman | Petugas Laboratorium | Asosiasi Petugas Laboratorium | **Cocok.** Berdiri sendiri menghubungkan Petugas dengan pemrosesan status Disetujui atau Ditolak. |
| 7 | `LAB-UC07` | Lihat Laporan Peminjaman | Kepala Laboratorium | Asosiasi Kepala Laboratorium | **Cocok.** Berdiri sendiri. Satu-satunya use case untuk Kepala Laboratorium; tidak memiliki relasi include, extend, generalization, maupun realization. |
| 8 | `LAB-UC08` | Tambah Data Peralatan | Petugas Laboratorium | Generalization ke `LAB-UC02` | **Cocok.** Use case khusus dari `LAB-UC02`. Perilaku pembeda: data peralatan baru tersimpan. Merujuk ke langkah bersama `LAB-UC02`. |
| 9 | `LAB-UC09` | Ubah Data Peralatan | Petugas Laboratorium | Generalization ke `LAB-UC02` | **Cocok.** Use case khusus dari `LAB-UC02`. Perilaku pembeda: data peralatan berubah. Merujuk ke langkah bersama `LAB-UC02`. |
| 10 | `LAB-UC10` | Hapus Data Peralatan | Petugas Laboratorium | Generalization ke `LAB-UC02` | **Cocok.** Use case khusus dari `LAB-UC02`. Perilaku pembeda: data peralatan terhapus, dengan syarat tidak sedang dipinjam dan tidak memiliki pengajuan aktif. |
| 11 | `LAB-UC11` | Catat Pengembalian Peralatan | Petugas Laboratorium | Asosiasi Petugas Laboratorium; «include» ke `LAB-UC12`; Realization dari `LAB-CO02` | **Cocok.** Include `LAB-UC12` menjadi langkah rujukan 6 pada Skenario Normal; alur alternatif mencakup penolakan jika status bukan Dipinjam. Collaboration `LAB-CO02` disebut pada keterangan. |
| 12 | `LAB-UC12` | Periksa Kondisi Peralatan | Petugas Laboratorium (berjalan di dalam `LAB-UC11`) | «include» dari `LAB-UC11` | **Cocok.** Dipanggil di dalam alur pengembalian langkah 6 untuk mencatat kondisi Baik, Rusak Ringan, atau Rusak Berat. |

---

## 3. Catatan Khusus Pemeriksaan Aktor Kepala Laboratorium

Sesuai instruksi Langkah 4 Jobsheet Pertemuan 5:
- Aktor **Kepala Laboratorium** hanya mempunyai tepat satu use case, yaitu `LAB-UC07 Lihat Laporan Peminjaman`.
- Use case `LAB-UC07` terhubung melalui tepat satu garis asosiasi lurus tanpa panah dari Kepala Laboratorium.
- `LAB-UC07` berdiri sendiri dan **tidak memiliki relasi lain**: tidak ada «include», «extend», generalization, maupun realization yang melibatkannya.
- Tabel skenario `LAB-UC07` pada Tabel 5.11 jobsheet telah ditelaah dan diverifikasi **bebas dari langkah rujukan include/extend/collaboration**, sehingga konsisten 100% dengan diagram P04.

---

## 4. Checklist Penilaian Studi Kasus LAB (Sesuai Bagian C.4)

| No | Butir Checklist Penilaian | Status Evaluasi | Keterangan & Bukti Penelusuran |
|---|---|---|---|
| 1 | Seluruh field tabel terisi lengkap (Nama, Aktor, Tujuan, Deskripsi, Kegiatan/Respon, Normal, Alternative, Akhir) | ✅ Terpenuhi | Ke-12 tabel memiliki seluruh field lengkap tanpa field kosong. |
| 2 | Satu aksi per langkah; penomoran berlanjut dari Normal ke Alternative tanpa reset ke nomor 1 | ✅ Terpenuhi | Penomoran langkah pada Skenario Alternative melanjutkan nomor terakhir Skenario Normal (contoh: UC03 langkah 1–6 normal, 7–12 alternative). |
| 3 | Pemisahan kolom Kegiatan (aksi aktor) dan Respon sistem (tanggapan sistem) tepat | ✅ Terpenuhi | Tidak ada aksi aktor di kolom sistem dan tidak ada respon sistem di kolom kegiatan. |
| 4 | Data yang dimasukkan dan ditampilkan disebut eksplisit (field, nilai, status) | ✅ Terpenuhi | Menyebut spesifik: tanggal pinjam, rencana kembali, status Menunggu Keputusan, nomor pengajuan, kondisi Baik/Rusak. |
| 5 | Relasi include ditulis sebagai langkah rujukan pada Skenario Normal | ✅ Terpenuhi | Terverifikasi pada `LAB-UC03` langkah 2 merujuk `LAB-UC04` dan `LAB-UC11` langkah 6 merujuk `LAB-UC12`. |
| 6 | Relasi extend ditulis sebagai cabang bersyarat di Alternative lengkap dengan condition & extension point | ✅ Terpenuhi | Terverifikasi pada `LAB-UC03` langkah 11–12 merujuk `LAB-UC05` dengan condition `[mahasiswa memilih cetak]` dan extension point `Bukti pengajuan tersedia`. |
| 7 | Generalization aktor diterapkan (tabel aktor umum + catatan aktor khusus) | ✅ Terpenuhi | `LAB-UC01` dan `LAB-UC03` ditulis atas nama `Peminjam (berlaku untuk Mahasiswa dan Dosen)`. |
| 8 | Generalization use case diterapkan (tabel umum bersama, tabel khusus perilaku pembeda) | ✅ Terpenuhi | `LAB-UC02` memuat alur bersama; `LAB-UC08`, `UC09`, `UC10` hanya memuat perilaku pembeda dan merujuk ke `UC02`. |
| 9 | Collaboration disebut pada keterangan tabel use case yang direalisasikan, tanpa langkah mandiri | ✅ Terpenuhi | `LAB-CO01` pada keterangan `LAB-UC03`; `LAB-CO02` pada keterangan `LAB-UC11`. Tidak ada tabel tersendiri untuk collaboration. |
| 10 | Setiap tabel memiliki Skenario Alternative dan Skenario Akhir | ✅ Terpenuhi | Ke-12 tabel skenario memiliki alur alternatif kegagalan/penyimpangan dan baris skenario akhir. |
| 11 | Nama, ID, aktor, condition, dan extension point sama persis dengan diagram P04 | ✅ Terpenuhi | Tidak ada perbedaan penamaan (100% konsisten). |
| 12 | Berkas diagram P04 tidak diubah; dokumen telaah disimpan pada folder `01_skenario/` | ✅ Terpenuhi | File tersimpan sebagai `01_skenario/P05_2406083_LAB_skenario_v01.md`. |
