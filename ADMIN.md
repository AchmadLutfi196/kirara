# Admin KIRARA

Dashboard interaktif lokal untuk guru atau pengelola konten. Entry tetap `index.html`; tidak ada halaman HTML admin terpisah.

## Membuka dashboard

Buka `index.html#/admin`, atau pilih **Area Admin** pada footer aplikasi siswa. Di admin, **Lihat Tampilan Siswa** kembali ke Menu Utama.

| Bagian | Rute | Fungsi |
|---|---|---|
| Ringkasan | `#/admin` | Jumlah konten aktif, soal terbit, karya menunggu, dan aktivitas pengelolaan aktual |
| Konten Belajar | `#/admin/konten` | Cerita dan materi; cari, edit, simpan draf, terbitkan, arsipkan, pulihkan |
| Bank Kuis | `#/admin/kuis` | Tambah/edit soal, empat pilihan, satu jawaban benar, penjelasan, draf dan publikasi |
| Mini Game | `#/admin/mini-game` | Edit lima pasangan budaya dengan id dan gambar tetap |
| Moderasi Karya | `#/admin/karya` | Detail gambar utuh, persetujuan, permintaan revisi dengan alasan, hapus unggahan lokal |
| Progres Siswa | `#/admin/siswa` | Satu profil perangkat, poin, cerita selesai, hasil kuis, status Mini Game dan refleksi |
| Pengaturan | `#/admin/pengaturan` | Nama pengelola/sekolah serta kewajiban meninjau unggahan baru |

## Mengelola konten

1. Pilih **Konten Belajar**, lalu tab Cerita atau Materi.
2. Tekan **Edit** dan isi bagian yang diperlukan. Sumber awal tetap tersedia; naskah cerita lengkap yang belum disediakan tidak direka.
3. **Simpan Draf** menyimpan pekerjaan tanpa mengubah publikasi siswa.
4. **Terbitkan** memeriksa isian. Cerita memerlukan judul, asal, waktu baca 1–120 menit, kategori, deskripsi, dan naskah. Gunakan naskah resmi yang telah ditinjau, bukan cuplikan yang dianggap lengkap.
5. Buka tampilan siswa pada browser yang sama untuk menggunakan publikasi. Naskah terbit tampil sebagai teks aman dengan paragraf; tidak menerima HTML aktif.

Cerita terbit memiliki tindakan **Tandai Selesai**, dengan 50 Poin Budaya satu kali per cerita. Audio tetap ditandai belum tersedia karena tidak ada rekaman sumber.

Tiga cerita sumber tidak bisa dihapus. Arsip menyembunyikan konten dari daftar siswa; **Pulihkan** mengembalikannya. Materi yang diarsipkan disembunyikan dari halaman Materi, sementara lima pasangan Mini Game tetap dipertahankan agar permainan selalu lengkap.

Pada **Mini Game**, istilah dan deskripsi menggunakan publikasi materi yang sama. Istilah pasangan harus unik. Menyimpan draf tidak mengubah kartu siswa; penerbitan menerapkan perubahan tanpa mengganti id pasangan atau tali drag-and-drop.

## Mengunggah sampul cerita

1. Buka **Konten Belajar → Cerita → Edit**.
2. Pada **Sampul cerita**, pilih **Unggah atau ganti sampul**. Gunakan JPG, PNG, atau WebP maksimal 2 MB dan 24 megapiksel. Berkas harus dapat dibaca sebagai gambar; SVG tidak diterima.
3. Tunggu sampai pratinjau selesai disiapkan. Ukuran asli gambar dibaca untuk menjaga rasio; gambar tidak dipotong.
4. **Simpan Draf** menyimpan pilihan untuk dikerjakan nanti tanpa mengubah sampul siswa.
5. **Terbitkan Sampul** memperbarui gambar saja, tanpa mengharuskan naskah lengkap dan tanpa menerbitkan perubahan teks/metadata yang belum disimpan. Tombol **Terbitkan** di bawah editor tetap menerbitkan konten lengkap dengan validasi sebelumnya.
6. Untuk mengembalikan gambar bawaan, tekan **Gunakan Sampul Asli**, lalu **Terbitkan Sampul**, atau simpan sebagai draf jika belum ingin mengubah tampilan siswa.

Sampul terbit tampil pada kartu Pilih Cerita, pembaca cerita, profil siswa, serta daftar cerita admin. Gambar karya dan ilustrasi halaman lain tidak diganti. Arsip cerita tetap berlaku meskipun sampul diperbarui.

Sampul tersimpan sebagai data gambar dalam namespace admin lokal; berkas aset asli tetap utuh. Browser yang sama diperlukan untuk melihat publikasi. Gambar besar dapat memenuhi kuota localStorage: bila penyimpanan gagal, pemberitahuan menjelaskan bahwa perubahan hanya berlaku pada sesi ini. Gunakan berkas yang lebih kecil sebelum menyimpan ulang. Ukuran maksimum unggahan tidak menjamin ruang penyimpanan masih tersedia.

## Bank kuis

Tambahkan pertanyaan, empat pilihan berbeda, satu jawaban benar, dan penjelasan. Draf baru belum muncul pada kuis siswa. Soal sumber Jokotole tidak dapat dihapus; soal pengelola dapat dihapus setelah konfirmasi.

Kuis siswa mengambil salinan soal terbit ketika sesi kuis dimulai, menampilkan satu pertanyaan setiap langkah, memberikan feedback benar/salah, lalu menghitung skor dari seluruh jawaban. Publikasi saat sesi sedang berlangsung tidak mengubah pertanyaan di tengah pengerjaan. Gunakan **Main Lagi** setelah menyelesaikan kuis untuk memulai sesi dengan bank soal terbaru. Poin kuis dan lencana mengikuti aturan awal: hasil sempurna memberikan reward satu kali.

## Moderasi karya

Unggahan berasal dari fitur Ruang Karya siswa pada browser ini. Secara default, unggahan baru menunggu persetujuan. Pengelola dapat:

- **Setujui** agar karya terlihat pada galeri siswa.
- **Minta Revisi** dengan masukan minimal 5 karakter; masukan tampil pada bagian Status karya di perangkat ini.
- **Hapus** setelah konfirmasi; gambar dan record unggahan dihapus dari data lokal.

Enam karya bawaan beserta nama pembuatnya merupakan referensi desain, bukan daftar siswa nyata. Karya tersebut tidak dihitung sebagai unggahan baru dan tidak dapat dimoderasi/dihapus.

Menonaktifkan peninjauan pada Pengaturan hanya memengaruhi unggahan baru. Status karya lama tetap dipertahankan.

## Penyimpanan dan batas penggunaan

- `kirara.v1`: profil, unggahan, poin, refleksi, progres, dan hasil siswa.
- `kirara.admin.v1`: draf, publikasi, soal, status moderasi, preferensi, serta maksimal 30 catatan aktivitas aktual.
- Semua data hanya berlaku pada origin dan browser ini. File lokal atau deployment dengan alamat berbeda dapat memakai penyimpanan yang berbeda.
- Bila localStorage penuh atau tidak tersedia, perubahan tetap dapat digunakan dalam sesi yang sedang terbuka dan ditandai dengan pemberitahuan. Muat ulang dapat menghilangkan perubahan yang gagal disimpan.
- Dashboard tidak menyediakan autentikasi, pembatasan peran server, sinkronisasi, atau data seluruh sekolah. Rute admin adalah area prototipe yang dapat dibuka langsung.
- Untuk pemakaian sekolah, diperlukan layanan autentikasi/otorisasi server, basis data, penyimpanan gambar, kebijakan akses siswa/guru, dan audit log server.

## Sumber dan implementasi

`admin.js` menyediakan `window.KiraraAdmin`, dimuat sebelum `app.js`. Inisialisasi terjadi setelah sumber siswa tersedia. Modul menghubungkan publikasi ke cerita/materi, kuis, dan galeri; draf memakai namespace terpisah. `admin.css` memusatkan token serta layout area admin tanpa mengganti navigasi atau ikon Menu Utama siswa.

Untuk Next.js, pecah shell, daftar konten, editor, bank soal, moderasi, dan profil menjadi komponen. Ganti adapter localStorage dengan API terotorisasi; pertahankan pemisahan draft/published, id konten stabil, dan validasi server. Kontrak tampilan ini tidak mengimplementasikan backend tersebut.

Entry `index.html`, `admin.js`, `admin.css`, dan panduan ini disertakan pada daftar `.vercelignore`. Konfigurasi statis yang ada tetap digunakan. Deploy belum dijalankan. Tidak ada preview, render, atau pengujian browser setelah finalisasi entry.
