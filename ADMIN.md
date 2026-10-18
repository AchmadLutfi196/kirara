# Admin KIRARA

Area pengelolaan lokal pada aplikasi Next.js. Buka `/admin` atau tautan **Ruang Pengelola** di footer. Tidak ada login atau pembatasan peran server: siapa pun yang memakai browser ini dapat membuka rute admin.

| Bagian | Rute | Cakupan |
|---|---|---|
| Ringkasan | `/admin` | Ringkasan konten dan karya serta pintasan pengelolaan |
| Konten Belajar | `/admin/konten` | CRUD cerita/materi, draf, publikasi, arsip, pulihkan |
| Bank Kuis | `/admin/kuis` | Soal lokal, empat pilihan, kunci, pembahasan, draf/publikasi |
| Mini Game | `/admin/mini-game` | Lima pasangan budaya yang memakai id sumber tetap |
| Moderasi Karya | `/admin/karya` | Persetujuan, revisi dengan masukan, antrean unggahan lokal |
| Progres Siswa | `/admin/siswa` | Satu profil browser, poin, aktivitas, refleksi |
| Pengaturan | `/admin/pengaturan` | Nama pengelola/sekolah dan peninjauan karya baru |

## Konten belajar

Pada **Konten Belajar**, pilih Cerita atau Materi. **Tambah Cerita/Materi** membuat entri lokal baru; **Edit** mengubah entri. **Simpan Draf** menyimpan pekerjaan untuk dilanjutkan tanpa mengubah siswa, sedangkan **Terbitkan** membuat konten tersedia pada halaman siswa. Entri buatan pengelola dapat **Hapus** setelah konfirmasi. Referensi bawaan tidak dihapus; gunakan **Arsipkan/Pulihkan** untuk mengatur tampilnya. Tampilan siswa dapat dibuka pada browser/origin yang sama melalui **Lihat Tampilan Siswa**.

Naskah lengkap harus berasal dari sumber yang benar-benar tersedia dan telah ditinjau pengelola. Cuplikan Jokotole awal bukan cerita lengkap; Potre Koneng dan Ke’ Lesap belum memiliki naskah. Aplikasi tidak menyusun naskah atau audio palsu. Publikasi naskah dapat ditandai selesai oleh siswa dan memberi 50 poin satu kali per cerita.

**Arsipkan** menyembunyikan konten dari daftar siswa; **Pulihkan** mengembalikannya. Tiga identitas cerita dan lima id budaya sumber dipertahankan. Materi sumber yang diterbitkan dipakai pada halaman Materi dan Mini Game; materi tambahan tampil pada halaman Materi. Istilah budaya sumber harus unik agar pasangan permainan tidak ambigu.

## Sampul cerita

Gunakan JPG, PNG, atau WebP maksimal 2 MB yang benar-benar dapat dibaca sebagai gambar. Tunggu proses baca/pratinjau selesai sebelum menyimpan. Gambar konten ditampilkan utuh; berkas asli tidak ditimpa.

**Simpan Draf** mempertahankan sampul untuk nanti. **Terbitkan Sampul** hanya menerapkan gambar, sehingga draf judul, metadata, dan naskah tidak ikut terbit. **Pulihkan Sampul Asli** langsung memulihkan gambar bawaan tanpa menerbitkan draf teks. Penerbitan seluruh konten tetap memakai tombol **Terbitkan** dan validasi naskah.

Sampul disimpan sebagai data gambar lokal. Ukuran unggahan yang lolos validasi tidak menjamin kuota localStorage cukup; kegagalan simpan harus diperhatikan sebelum menutup tab.

## Bank kuis

**Tambah Soal** menyediakan pertanyaan, empat pilihan berbeda, satu kunci benar, dan pembahasan. Simpan draf untuk meninjau atau terbitkan agar soal tersedia pada kuis siswa. Soal sumber Jokotole dilindungi dari penghapusan; soal tambahan dapat dihapus setelah konfirmasi. **Tarik Publikasi** mengeluarkan soal dari sesi kuis baru tanpa menghapus draf.

Sesi kuis memakai salinan soal terbit saat sesi dimulai. Siswa memilih jawaban, menandai ragu-ragu bila perlu, meninjau, lalu menyelesaikan kuis. Hasil memperlihatkan jawaban dan pembahasan. **Main Lagi** memulai sesi baru dengan bank soal terbaru. Hasil sempurna memberi 20 poin satu kali; hasil bukan penilaian semua cerita.

## Moderasi karya

Unggahan dari Ruang Karya browser ini masuk antrean secara default. **Setujui Karya** menampilkannya pada galeri siswa. **Minta Revisi** memerlukan masukan minimal lima karakter; masukan terlihat pada status karya siswa. Karya dapat dikembalikan ke antrean atau dihapus dari perangkat setelah konfirmasi.

Enam karya bawaan beserta nama/apresiasinya adalah contoh referensi desain, bukan data siswa terverifikasi. Contoh tidak masuk antrean moderasi. Pengaturan peninjauan hanya mengubah status awal unggahan baru; status lama tetap dipertahankan.

## Penyimpanan dan batas

Aplikasi memakai `kirara.next.v2`, dengan import sumber historis `kirara.v1` dan `kirara.admin.v1` pada origin yang sama. Membuka domain/port berbeda atau pindah dari file lokal tidak otomatis memindahkan data. Detail import dan hasil browser aktual: [laporan migrasi/QA](docs/migration-qa.md).

Jika storage penuh atau ditolak, perubahan sesi dapat tetap digunakan tetapi hilang ketika dimuat ulang. Belum ada penyimpanan gambar server, cadangan lintas perangkat, pengiriman karya ke sekolah, autentikasi/otorisasi, atau data seluruh kelas. Activity log server, kebijakan akses sekolah, dan audit keamanan berada di luar cakupan.

`admin.js`/`admin.css` di root adalah sumber prototipe historis. Jalankan aplikasi kanonis melalui perintah [README.md](README.md); tidak ada deployment yang dilakukan dalam migrasi ini.
