# Metadata Artefak Pertemuan 6 — Activity Diagram: Dari Skenario ke Alur Aktivitas

## 1. Metadata Studi Kasus LAB (Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium)

ID artefak              : LAB-P06-ACT
Judul                   : Activity Diagram: Dari Skenario ke Alur Aktivitas (Studi Kasus Laboratorium)
Pertemuan               : 06
Kakas                   : draw.io
Pembuat                 : Moch Rasky Putra Softiawan_2406083
Versi dan tanggal       : v01 / 11 November 2026
Jenis/status            : Activity Diagram UML 2.5.1 / Final v01
Dokumen skenario acuan  : 01_skenario/P05_2406083_LAB_skenario_v01.md & Jobsheet Pertemuan 5
Diagram use case acuan  : 04_mode_analisis/P04/LAB/P04_2406083_LAB_usecase_v01.drawio

### Rincian 7 Activity Diagram LAB:
1. **Activity Lihat Ketersediaan Peralatan**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_lihat_ketersediaan_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC01 (Tabel 5.2 Jobsheet P05)
   - Swimlane             : Peminjam, Sistem
   - Unsur activity       : Initial node, Action, Decision (`[tersedia]`, `[tidak tersedia]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada

2. **Activity Kelola Data Peralatan**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_kelola_data_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC02 (umum bersama), LAB-UC08 (tambah), LAB-UC09 (ubah), LAB-UC10 (hapus) (Tabel 5.3, 5.7, 5.8, 5.9 Jobsheet P05)
   - Swimlane             : Petugas Laboratorium, Sistem
   - Unsur activity       : Initial node, Action, Decision (Bentuk pengelolaan `[tambah]`, `[ubah]`, `[hapus]`; Data ditemukan `[ditemukan]`, `[tidak ditemukan]`; Syarat hapus `[terpenuhi]`, `[tidak terpenuhi]`; Data sah `[lengkap dan sah]`, `[tidak lengkap atau tidak sah]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada

3. **Activity Peminjaman**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_peminjaman_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC03 (induk), include LAB-UC04 (Tabel 5.4 & 5.5), extend LAB-UC05 (Tabel 5.6)
   - Swimlane             : Mahasiswa, Sistem, Petugas Laboratorium
   - Unsur activity       : Initial node, Action, Decision (`[tersedia]`, `[tidak tersedia]`; `[ya, memilih cetak]`, `[tidak]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada

4. **Activity Cetak Bukti Pengajuan**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_cetak_bukti_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC05 (Tabel 5.6 Jobsheet P05, extension point Bukti pengajuan tersedia)
   - Swimlane             : Mahasiswa, Sistem
   - Unsur activity       : Initial node, Action, Decision (`[ya, memilih cetak]`, `[tidak]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada

5. **Activity Proses Keputusan Peminjaman (Tugas Mandiri)**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_keputusan_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC06 (Tabel 5.10 Jobsheet P05)
   - Swimlane             : Petugas Laboratorium, Sistem
   - Unsur activity       : Initial node, Action, Decision (`[dapat diproses]`, `[tidak dapat diproses]`; `[disetujui]`, `[ditolak]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada
   - Catatan perbandingan : Dikerjakan mandiri tanpa melihat pembanding, diverifikasi dengan checklist C.4, kemudian diselaraskan dengan pembanding lampiran.

6. **Activity Pengembalian**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_pengembalian_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC11 (induk), include LAB-UC12 kondisi fisik (Tabel 5.12 & 5.13 Jobsheet P05)
   - Swimlane             : Mahasiswa, Sistem, Petugas Laboratorium
   - Unsur activity       : Initial node, Action, Fork, Join, Decision (`[baik dan lengkap]`, `[rusak atau tidak lengkap]`), Merge, Activity final node
   - Unsur proses baru    : **Periksa kelengkapan aksesori peralatan** (Kebutuhan proses baru dari Jobsheet P06 untuk melatih fork & join, bukan dari P03-P05).

7. **Activity Lihat Laporan Peminjaman**
   - Berkas sumber        : 04_mode_analisis/P06/LAB/P06_2406083_LAB_activity_laporan_v01.drawio & .png
   - Tabel skenario sumber: LAB-UC07 (Tabel 5.11 Jobsheet P05)
   - Swimlane             : Kepala Laboratorium, Sistem
   - Unsur activity       : Initial node, Action, Decision (`[ada]`, `[tidak ada]`), Merge, Activity final node
   - Unsur proses baru    : Tidak ada

---

## 2. Metadata Tugas Praktik SIA (Sistem Informasi Akademik — Layanan Hasil Studi)

ID artefak              : SIA-P06-ACT
Judul                   : Activity Diagram Input Nilai Mata Kuliah sampai Lihat KHS
Pertemuan               : 06
Kakas                   : draw.io
Pembuat                 : Moch Rasky Putra Softiawan_2406083
Versi dan tanggal       : v01 / 11 November 2026
Jenis/status            : Activity Diagram UML 2.5.1 / Tugas Mandiri v01
Dokumen skenario acuan  : 01_skenario/P05_2406083_SIA_skenario_v01.md (SIA-UC08 & SIA-UC09)
Diagram use case acuan  : 04_mode_analisis/P04/SIA/P04_2406083_SIA_usecase_v01.drawio
Berkas sumber           : 04_mode_analisis/P06/SIA/P06_2406083_SIA_activity_v01.drawio & .png
Tabel skenario sumber   : SIA-UC08 Input Nilai Mata Kuliah & SIA-UC09 Lihat KHS
Swimlane                : 4 Partisi (Dosen, Sistem, Admin Akademik, Mahasiswa)
Unsur activity          : 
  - Tepat 1 Initial node dan tepat 1 Activity final node
  - Decision kelengkapan nilai dengan guard `[lengkap]` dan `[belum lengkap]` (loop kembali ke Dosen untuk melengkapi nilai)
  - Pasangan Fork dan Join untuk publikasi paralel hasil studi (Menerbitkan KHS pada portal akademik & Mengirim pemberitahuan hasil studi kepada mahasiswa) sebelum Mahasiswa melihat KHS
  - Merge untuk menyatukan cabang pengisian nilai kembali sebelum pengesahan oleh Admin Akademik
Unsur proses baru       : Tidak ada (seluruh alur tertelusur ke skenario SIA P05)

---

## 3. Catatan Pemeriksaan & Riwayat Revisi

Asumsi                  : Diagram acuan kumulatif P04 tetap utuh dan valid; dokumen skenario P05 menjadi acuan murni teks dan urutan action; collaboration tidak dimodelkan pada activity diagram.
Pemeriksaan             : Memenuhi 100% checklist penilaian Bagian C.4 Jobsheet Pertemuan 6 Revisi.
Riwayat revisi          : 
  - v01 (11/11/2026): Pemisahan berkas mandiri 7 activity LAB dari master multi-tab, sinkronisasi identitas NIM berkas sumber dan ekspor SIA (2406083), standardisasi nama file sesuai format resmi jobsheet, pembersihan artefak duplikat tidak baku.
