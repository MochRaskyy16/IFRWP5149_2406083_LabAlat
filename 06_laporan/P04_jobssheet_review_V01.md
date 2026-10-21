# P04_jobssheet_review_V01 — Review Jobsheet Pertemuan 4 dan Hasil Pengerjaan SIA

Sumber yang direview: Jobsheet Praktikum Pertemuan 4, *Use Case Diagram Lanjutan: Generalization dan Collaboration* (Institut Teknologi Garut, S1 Teknik Informatika, hlm. 45–68).  
Cakupan: (A) ringkasan isi, (B) temuan ketidakkonsistenan pada jobsheet, (C) review hasil pengerjaan tugas SIA terhadap jobsheet dan checklist, (D) tindak lanjut.

---

## A. Ringkasan isi jobsheet

**Tujuan (6):** hierarki aktor, hierarki use case, dua collaboration dengan realization, diagram kumulatif P4, satu use case description baru, dan keterlacakan ke kebutuhan dengan perbaikan ke v02.

**Prinsip utama**

| Topik | Aturan inti |
|---|---|
| Kumulatif | Diagram P4 = salinan diagram P3 + elemen baru. P03 asli tidak diubah; ID lama tidak diganti. |
| Generalization aktor | Segitiga kosong menempel pada aktor umum. Asosiasi bersama digambar satu kali dari aktor umum; asosiasi khusus tetap dari aktor khusus. Hanya satu tingkat. Tidak dipakai bila peran tidak berbagi fungsi. |
| Generalization use case | Segitiga kosong menempel pada use case umum. Aktor dihubungkan ke use case umum (atau khusus yang benar-benar dipakai). Use case khusus bukan sekadar ganti nama. Satu pasang use case hanya satu jenis relasi. |
| Collaboration | Elips garis putus-putus, nama sama persis dengan use case, ID sendiri (LAB-CO / SIA-CO), merealisasikan tepat satu use case, tidak pernah terhubung ke aktor, hanya untuk use case utama. |
| Realization | Garis putus-putus, segitiga kosong, dari collaboration menuju use case, tanpa label. |
| Perbandingan relasi | Include/extend: antar use case, garis putus-putus panah terbuka, berlabel. Generalization: garis utuh. Realization: garis putus-putus segitiga kosong. |
| Use case description | Template P3 + baris Generalization dan Collaboration. Ditulis untuk use case, bukan collaboration. |

**Studi kasus LAB:** 5 aktor, 12 use case (LAB-UC01–UC12), 2 collaboration, 17 hubungan (Tabel 4.5).  
**Tugas SIA:** layanan hasil studi, 5 aktor, 13 use case (SIA-UC01–UC13), 2 collaboration, tanpa contoh jawaban.  
**Deliverable:** berkas kebutuhan dan skenario, katalog, keputusan generalization/collaboration, use case description, sumber dan ekspor diagram, logbook.

---

## B. Temuan pada jobsheet (ketidakkonsistenan dan bagian yang belum jelas)

| No | Lokasi | Temuan | Dampak dan cara saya menanganinya |
|---|---|---|---|
| 1 | C.1 Simbol | Menyebut "sembilan unsur pada Tabel 4.1", tetapi Tabel 4.1 tidak ada pada berkas (penomoran dimulai dari 4.2). | Daftar sembilan unsur tidak dapat diverifikasi. Saya memakai notasi dari penjelasan di Bagian B dan Tabel 4.2. |
| 2 | C.3 Langkah 8 | Menyebut berkas draw.io pembanding (tahap1_basis_P03 … tahap5_final) "pada Lampiran", tetapi Lampiran tidak ada pada berkas. | Tidak bisa membandingkan dengan berkas tahap. Pembanding yang tersedia hanya gambar tahap 1–5 di halaman 59–61 (LAB). |
| 3 | C.3 Langkah 4 | Kalimat pembuka "dua keputusan pemodelan", tetapi tertulis empat butir. | Hanya penulisan; keempat butir saya perlakukan sebagai aturan yang berlaku. |
| 4 | B.6 vs C.4 Langkah 6 | B.6: dua baris ditambahkan (Generalization dan Collaboration). Contoh LAB-UC11 memuat baris Include dan Collaboration tanpa baris Generalization. Tugas SIA hanya menyebut tambahan baris Collaboration. | Tidak jelas apakah baris Generalization wajib. Pada SIA-UC08 dan SIA-UC09 saya mencantumkan baris Generalization dengan isi "Tidak ada" agar aman terhadap kedua pembacaan. |
| 5 | C.5 Checklist | "Relasi «include» pada pencatatan pengembalian / tugas mengarah ke perilaku yang disertakan": tugas SIA tidak memiliki include baru. | Include yang ada pada diagram SIA hanya yang lama (SIA-UC03 → SIA-UC04), dan saya periksa arahnya. Tidak saya buat include baru. |
| 6 | C.4 Langkah 2 | "relasi include dan extend di antara ketiganya" setelah menyebut empat use case (SIA-UC03 s.d. SIA-UC06). | Dibaca: relasi ada di antara SIA-UC03, SIA-UC04, SIA-UC05 (analog LAB). Aktor dan condition/extension point-nya tidak disebut; diasumsikan (lihat bagian C, butir risiko 1). |
| 7 | C.4 Batas dan asumsi | Nilai "belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini", tetapi tidak ada ketentuan publikasi pada tugas. Rentang nilai yang sah juga tidak ditetapkan. | Bersifat melingkar. Saya tidak membuat use case publikasi dan tidak mengarang rentang; keduanya dicatat sebagai pertanyaan terbuka. |
| 8 | C.3 Langkah 7 (LAB-UC11) | Status "Selesai" dipakai sebagai pascakondisi, padahal aturan hanya menyebut status Dipinjam, Menunggu Keputusan, dan Ditolak. Alur A3 merujuk langkah 2, padahal respons sistem di langkah 2 hanya "menampung konfirmasi". | Tidak memengaruhi tugas SIA; dicatat sebagai bahan perbaikan jobsheet. |
| 9 | C.3 Langkah 3 vs Tabel 4.4 | Katalog LAB-UC11 menyebut "fungsi utama petugas", sementara Tabel 4.4 menyebut asosiasi Petugas ke LAB-UC11; konsisten. Tabel 4.5 berjumlah 17 baris: sudah saya hitung dan cocok. | Tidak ada masalah. |
| 10 | Tabel 4.5 untuk SIA | Jobsheet tidak menetapkan jumlah hubungan untuk SIA. | Hasil saya: 18 hubungan (7 lama dengan asumsi + 11 baru). Angka ini bukan angka resmi jobsheet. |

---

## C. Review hasil pengerjaan SIA terhadap checklist jobsheet

| Butir checklist (C.5) | Hasil | Bukti |
|---|---|---|
| Elemen P3 tetap ada, tidak berubah nama | **Sebagian terverifikasi** | SIA-UC01–UC06, include, extend ada. Aktor terhubung, condition, dan extension point adalah asumsi (risiko 1). |
| Asosiasi bersama digambar satu kali dari aktor umum | Terpenuhi | Civitas Akademika → SIA-UC07, tidak ada garis dari Mahasiswa/Dosen. |
| Tiap aktor khusus satu panah generalization, segitiga kosong di aktor umum | Terpenuhi | Mahasiswa → Civitas, Dosen → Civitas. |
| Tidak ada asosiasi warisan digambar ulang | Terpenuhi | Daftar 18 hubungan, `P04_SIA_skenario_v01.md` bagian 6. |
| Tiap use case khusus satu panah generalization, segitiga kosong di use case umum | Terpenuhi | SIA-UC11, UC12, UC13 → SIA-UC10. |
| Collaboration elips putus-putus, nama sama persis, tidak terhubung ke aktor | Terpenuhi | SIA-CO01 dan SIA-CO02. |
| Realization dari collaboration ke use case | Terpenuhi | CO01 → SIA-UC08, CO02 → SIA-UC09. |
| «include» mengarah ke perilaku yang disertakan | Terpenuhi | SIA-UC03 → SIA-UC04 (lihat temuan B5). |
| Aktor di luar batas; use case dan collaboration di dalam | Terpenuhi | Aktor di x < 230 dan x > 1090, batas sistem 230–1090. |
| Nama dan ID sama persis di diagram, katalog, deskripsi | Terpenuhi | Diperiksa pada kebutuhan, skenario, dan diagram. |
| Elemen baru tertelusur ke SIA-R07–R12 | Terpenuhi | Tabel keterlacakan, bagian 7 skenario. |
| Kebutuhan P3 tidak diubah artinya; P03 tidak ditimpa | Terpenuhi | Berkas P04 dibuat baru; tidak ada berkas P03 yang disentuh. |
| Sumber dapat dibuka dan disunting; versi sumber = ekspor | **Sebagian** | XML .drawio valid dan versi sama (v01). Berkas **belum saya buka di aplikasi draw.io**; PNG dibuat dari data yang sama, bukan ekspor draw.io. |
| Kebutuhan belum dimodelkan ditandai pertanyaan terbuka | Terpenuhi | Tiga pertanyaan terbuka di `P04_SIA_kebutuhan_v01.md`. |

**Uji tiga situasi (Langkah 8):** Situasi A, B, dan C dijawab di `P04_SIA_kebutuhan_v01.md` bagian 5, dan konsisten dengan deskripsi SIA-UC08 (alur alternatif A1) serta aturan Hapus Data Mahasiswa.

### Risiko dan keputusan desain yang perlu diketahui

1. **Asumsi bagian lama (P02/P03).** Aktor-ke-use-case lama, condition `[mahasiswa memilih unduh]`, dan extension point `Bukti pengajuan KRS tersedia` meniru pola LAB. Bila berkas P03 SIA Anda berbeda, bagian lama harus diganti agar sama persis dengan P03 (jumlah hubungan juga akan ikut berubah).
2. **ID di dalam elips.** Ellips diberi dua baris: ID dan nama. Gambar contoh jobsheet hanya menampilkan nama. Nama pada baris kedua tetap sama persis dengan nama use case.
3. **Tata letak.** Ujung segitiga generalization Mahasiswa dan Dosen menyentuh ikon Civitas Akademika (kepala dan kaki) karena ketiganya ditumpuk vertikal; terbaca, tetapi bisa dirapikan di draw.io.
4. **Fungsi bersama hanya satu.** Generalization Civitas Akademika hanya mewariskan satu fungsi (SIA-UC07). Ini sesuai instruksi tugas dan lolos uji tiga pertanyaan, tetapi merupakan kasus minimum untuk generalization aktor.
5. **Review rekan/asisten belum dilakukan**, sehingga tidak ada versi v02.

---

## D. Tindak lanjut

| No | Tindakan | Penanggung jawab | Status |
|---|---|---|---|
| 1 | Cocokkan bagian lama diagram SIA dengan P02 dan P03 asli | Mahasiswa | Belum |
| 2 | Ganti `NIM` pada nama berkas dan folder | Mahasiswa | Belum |
| 3 | Buka .drawio di draw.io, rapikan tata letak, ekspor ulang PNG bila diwajibkan | Mahasiswa | Belum |
| 4 | Minta review rekan/asisten (arah panah, nama collaboration, pascakondisi) | Mahasiswa | Belum |
| 5 | Bila ada perubahan isi, simpan sebagai v02, pertahankan v01, catat di metadata dan logbook | Mahasiswa | Menunggu review |
| 6 | Tanyakan ke dosen: ketersediaan Tabel 4.1 dan Lampiran, serta apakah baris Generalization wajib | Mahasiswa | Opsional |

**Status dokumen:** V01, belum melalui review pihak lain.
