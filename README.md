# KIRARA — prototipe interaktif

## Membuka hasil

Buka **`index.html`** di browser modern. Semua asset dan kode dirujuk secara relatif, tidak memakai CDN atau build step. Mulai dari onboarding dengan nama panggilan, lalu jelajahi Menu Utama.

UI Kit: buka **`index.html#/ui-kit`**. Dokumentasi visual: `DESIGN.md`. Token: `design-tokens.json`.

Tema **petualangan budaya versi 2.0** diterapkan pada seluruh halaman: onboarding, Menu Utama, Pilih Cerita, pembaca, Mini Game, kuis, hasil, Ruang Karya, profil, Materi, dan UI Kit. Semuanya memakai token bersama, latar desa lokal, panel cream/putih, serta detail kayu yang mengikuti referensi pengguna. Untuk melihat onboarding saat nama sudah tersimpan, buka `index.html#/masuk` langsung; tidak perlu menghapus progres.

Jika kebijakan browser membatasi penyimpanan saat membuka file lokal, gunakan server lokal pilihan Anda dari folder ini. Prototipe tetap memberi tahu saat penyimpanan tidak tersedia.

## Berkas

| Berkas | Isi |
|---|---|
| `index.html` | Entry kanonis dan layout primitives |
| `styles.css` | Design tokens aktif, komponen, responsive rules |
| `app.js` | Data referensi, rute, komponen dan interaksi lokal |
| `.vercelignore` | Daftar berkas yang dikirim saat deploy dengan Vercel CLI |
| `vercel.json` | Konfigurasi situs statis, tanpa install/build, output root |
| `assets/` | Hasil ekstraksi screenshot dan latar ilustratif hasil edit |
| `assets/kirara-village-background.png` | Satu latar dekoratif lokal 1556 × 1011px yang dipakai ulang pada seluruh aplikasi |
| `assets/provenance.json` | Sumber, nomor referensi, koordinat crop, dimensi, treatment |
| `DESIGN.md` | Design system dan panduan komponen |
| `design-tokens.json` | Token dalam format mesin |
| `PRODUCT.md` | Tujuan, audiens, batas produk |
| `prepare-assets.py` | Sumber pemrosesan crop dan penghapusan latar dari screenshot |

## Halaman

| Tujuan | Hash route |
|---|---|
| Entry / Onboarding | `#/masuk` |
| Menu Utama | `#/menu` |
| Pilih Cerita | `#/cerita` |
| Story Reader | `#/baca/jokotole`, `#/baca/potre-koneng`, `#/baca/ke-lesap` |
| Mini Game | `#/mini-game` |
| Kuis Budaya | `#/kuis` |
| Hasil Akhir | `#/hasil` |
| Ruang Karya | `#/karya` |
| Profil Siswa | `#/profil` |
| Materi pendukung | `#/materi` |
| UI Kit | `#/ui-kit` |

UI Kit terpisah dari menu siswa, supaya produk tidak menampilkan kontrol desainer.

## Interaksi yang disertakan

- Onboarding dengan validasi nama; edit nama dan kelas di profil.
- Navigasi desktop/mobile, tombol kembali, penyimpanan posisi scroll per rute.
- Tiga kartu cerita; cuplikan Jokotole, ukuran teks, glosarium, refleksi yang dapat disimpan.
- Mini Game lima pasangan dengan tali drag-and-drop dari pin kiri ke kartu kanan (mouse, pena, atau sentuhan). Ujung tali mengikuti pointer; kartu tujuan ditandai; tepi layar menggulir saat menyeret. Klik dua kartu atau Tab + Enter/Spasi tetap tersedia. Escape/drop di luar kartu membatalkan tanpa menghapus pasangan lama. Periksa Jawaban mengunci pasangan benar; pasangan salah dapat ditarik ulang. Reset, timer, skor, dan hasil tetap tersedia.
- Satu soal kuis dari referensi, selected/correct/incorrect states, tanda ragu-ragu, peninjauan sebelum submit, timer, hasil, ulangi.
- Poin dan lencana tidak bertambah tanpa batas saat mengulang. Mini Game memberi total 500 sekali; jawaban kuis benar memberi 20 sekali.
- Galeri enam contoh, filter, search, sort, detail karya, apresiasi toggle.
- Scan/upload memakai file picker dengan `capture=environment` sebagai petunjuk kamera pada perangkat yang mendukung. Ini pengambilan foto, bukan OCR atau pemindaian dokumen otomatis. Desktop dapat memilih file.
- Validasi gambar JPG/PNG/WebP maksimal 2 MB, pratinjau, judul, kategori, pembuat, penambahan galeri lokal, feedback error/quota.
- Modal native dialog dengan Escape, tombol tutup, dan fokus kembali; feedback melalui live region.

## Batas konten yang disetujui

Pengguna memilih penggunaan screenshot serta konten yang tampak di referensi, dengan penandaan bagian yang belum tersedia.

1. Hanya satu cuplikan Jokotole tersedia. Cerita lengkap tidak ditulis ulang atau direka. Potre Koneng dan Ke' Lesap memiliki ilustrasi dan metadata serta state naskah belum tersedia.
2. Tidak ada audio asli. Player menunjukkan state unavailable dengan kontrol nonaktif, tanpa timer atau suara narator palsu.
3. Bank soal lengkap belum tersedia. Kuis berisi satu pertanyaan Jokotole yang terlihat; hasil menyebut cakupan satu soal.
4. Materi menggunakan deskripsi kartu budaya dari screenshot. Tidak ada klaim akreditasi atau verifikasi guru yang dibuat.
5. Nama siswa, karya, dan hitungan apresiasi awal adalah contoh dari desain referensi, bukan rekaman siswa terverifikasi.
6. Prototipe ini bukan aplikasi backend; tidak ada autentikasi, pengiriman, publikasi, atau sinkronisasi lintas perangkat.

## Asal dan batas aset

Seluruh gambar diambil dari screenshot yang disediakan. Karakter tidak digambar ulang. Checkerboard luar logo dibersihkan menjadi alpha transparan melalui seleksi warna yang terhubung ke tepi. Area cream luar gambar Sakera/Marlena juga dibersihkan. Ekstraksi disimpan sebagai PNG; tidak dilakukan generasi karakter baru.

Daftar lengkap crop dan dimensi ada pada `assets/provenance.json`. Foto/screenshot asli tetap tersimpan utuh di root proyek. Karena sumber berupa screenshot, beberapa label yang menyatu dengan gambar tetap terlihat, dan ketajaman terbatas. Aset original terpisah diperlukan untuk menghilangkan semua label tanpa merekonstruksi ilustrasi. Bagian UI di luar gambar ditulis sebagai HTML interaktif, bukan screenshot halaman.

Referensi modern utama: 1, 2, 5, 6, 8, 11, 12. Referensi lama 3, 4, 7, 9, 10 digunakan untuk konten/layout saja. Sakera diekstrak dari referensi 10, Marlena dari 7, logo dari 4, dan ilustrasi utama dari 2/5/8.

Wrapper panduan media tambahan tidak mengembalikan isi dalam sesi ini. Ekstraksi memakai aset pengguna dan aturan sumber/fidelitas yang sudah disepakati.

## Penyimpanan dan data

`localStorage['kirara.v1']` menyimpan nama, kelas, cerita yang pernah dibuka, refleksi, skor terbaik, hadiah aktivitas, apresiasi, karya lokal, dan hasil terakhir. Jawaban/posisi permainan yang belum selesai bertahan selama sesi dan navigasi rute, tetapi tidak dilanjutkan setelah reload. Timer menghitung saat halaman aktivitas aktif.

Jika localStorage ditolak atau penuh, perubahan tetap berjalan dalam memori sesi dan notifikasi menjelaskan bahwa data belum disimpan secara permanen. Hindari mengunggah banyak gambar besar; implementasi produk nyata sebaiknya menggunakan penyimpanan file terpisah.

## Handoff Next.js + Tailwind CSS

| Prototipe | Komponen/rute yang disarankan |
|---|---|
| `renderHeader()` | `AppShell`, `MainNavigation`, `PointIndicator` |
| `entryLandscape()`, `entryBrand()`, `entryCompanion()` | `EntryLandscape`, `EntryBrand`, `LearningCompanion` |
| `onboarding()`, `menu()` | `OnboardingForm`, `WoodenMenuLink`, `LearningSteps` |
| `storyCard()` | `StoryCard` |
| `reader()` | `StoryReader`, `Glossary`, `ReflectionField`, `AudioPlayer` |
| `miniGame()` | `MatchingBoard`, `CultureCard`, `ActivityStats` |
| `quizPage()` | `QuizScreen`, `QuizOption`, `QuizProgress` |
| `gallery()` | `GalleryToolbar`, `ArtworkCard`, `ArtworkDialog`, `UploadForm` |
| `profile()` | `StudentProfile`, `ProgressSummary`, `AchievementBadge` |
| `modal()` | `Dialog` |
| `state`, `persist()` | `StudentProgressProvider`, storage adapter |

Migrasikan hash routes ke rute App Router yang setara. Gunakan data terstruktur untuk cerita lengkap dan status ketersediaannya. Mapping token dan aturan responsive ada di `DESIGN.md`. Jangan menyalin HTML via `innerHTML` ke React; pisahkan menjadi JSX dan props. Nilai input pengguna sudah di-escape pada prototipe ini, dan pada React gunakan rendering teks standar.

## Tema seluruh aplikasi: sumber dan batas

Permintaan terbaru, “lanjut revisi pada keseluruhan”, memperluas cakupan tema awal `entry-menu` menjadi seluruh prototipe. Enam fitur, sapaan siswa, CTA membaca, form nama, langkah belajar, lima label navbar, logo, dan karakter dipertahankan. Kartu cerita, reader, permainan, kuis, hasil, galeri, profil, Materi, dialog, notifikasi, dan UI Kit memakai tema bersama. Semua menu, tombol, dan input tetap berupa kontrol HTML.

Tema aktif melalui `body.world-theme` pada semua rute. `renderHeader()` memperbarui `data-surface` menjadi entry, reader, quiz, game, kit, atau learning; ini mengatur intensitas dekorasi dan jenis panel. Pembaca dan kuis menggunakan panel putih opak dengan lanskap lebih ringan. Token utama `--world-*` dipusatkan pada `:root`; `--entry-*` menjadi alias untuk komponen Menu Utama/onboarding yang sudah ada. `.entry-page` tetap mengatur layout dua halaman pembuka. Papan kayu, judul, state, dan aturan responsif ditulis dalam CSS; tidak ada screenshot UI yang menjadi tombol palsu.

Revisi ini menggunakan ulang aset yang sudah tersedia tanpa gambar baru, CDN, atau library tambahan. Logika aktivitas, pointer events tali, pemeriksaan jawaban, penguncian pasangan benar, kuis, timer, perhitungan poin, unggah galeri, serta localStorage dipertahankan. UI Kit memuat contoh warna, tombol, input, progress, notifikasi, dialog, navigasi, ikon, kartu, pilihan kuis, matching, dan aturan responsif dari sistem yang sama.

Handoff versi 2.0: gunakan satu `AppShell`/theme provider untuk seluruh rute. Pisahkan komponen bersama `Button`, `Panel`, `Badge`, `Chip`, `ProgressBar`, `CharacterDialogue`, `Field`, `Notification`, dan `Dialog` dari komponen halaman. Gunakan Tailwind custom properties yang mengacu pada token CSS; jangan menyalin palette terpisah ke setiap halaman. Rincian ada pada `DESIGN.md` dan `design-tokens.json`.

Latar lokal `assets/kirara-village-background.png` dibuat menggunakan **alat image generation bawaan dalam mode edit** dari lampiran `task-input:attachments/attachment-001.png`, SHA-256 sumber `7f5ad68f2060a889fa0bed3fcd58d61410a0013fe7c7e4eb7366569bab78b966`. Ukuran intrinsik hasil yang dipakai: 1556 × 1011px. Logo/karakter lama tidak ditimpa. Detail lanskap direkonstruksi dan dapat berbeda dari referensi. Gambar ini ilustrasi fiktif, bukan dokumentasi geografis.

Prompt edit yang digunakan:

```text
Use case: precise-object-edit. Asset type: decorative background for the KIRARA educational website. EDIT the attached reference image, preserving its illustrated landscape and warm hand-painted cartoon style. Remove ALL lettering, the KIRARA title, subtitles, every wooden menu button, all menu icons, the two large foreground human characters, and the settings/sound controls. Seamlessly reconstruct the sky, mountains, village buildings, palms, rice fields, water, paths and foreground grass where these elements were removed. Keep the existing landscape composition, soft blue sky, cream and peach clouds, green hills, warm sunlight, gentle outlines and rural Madurese cultural atmosphere. Keep the small existing cattle as part of the landscape. Output a clean continuous landscape background with calm open space across the upper-center and center for live HTML headings and buttons. No text, logos, UI, boards, icons, humans, watermark or transparency checkerboard. Landscape format approximately 1600:1040, opaque background. This is an edit of the user-supplied fictional illustration, not a photographic depiction of a real landmark.
```

Lookup panduan media tambahan melalui wrapper pada scope run mengembalikan hasil kosong. Pembuatan memakai instruksi imagegen yang tersedia dan aturan aset proyek; tidak memakai fallback CLI atau API key.

## Redeploy ke Vercel dan pesan batas 10 MB

Proyek ini adalah website statis dengan entry `index.html`. `vercel.json` memakai preset **Other** (`framework: null`), perintah install/build kosong, dan output directory `.`. Tidak diperlukan konversi ke Next.js untuk menerbitkan prototipe yang ada. Navigasi hash seperti `#/menu` tetap ditangani JavaScript di browser.

`.vercelignore` memakai allowlist: abaikan seluruh isi root terlebih dahulu, kemudian izinkan:

- `index.html`, `app.js`, dan `styles.css`;
- direktori `assets` beserta seluruh isinya, termasuk logo, karakter, cerita, galeri, dan latar desa;
- `DESIGN.md`, `README.md`, dan `design-tokens.json`, yang dipakai oleh dokumentasi/UI Kit;
- `vercel.json` dan `.vercelignore`.

Screenshot referensi di root (`image.png` dan `WhatsApp-Image-*.jpeg`), `.file-versions`, `.od-frames`, `.od-skills`, metadata artifact, `PRODUCT.md`, serta `prepare-assets.py` dikecualikan dari unggahan yang mengikuti daftar ini. Semua berkas tersebut tetap tersimpan di proyek; tidak ada aset yang dihapus atau dikompresi ulang. Daftar pengecualian ini didukung oleh [dokumentasi resmi .vercelignore](https://vercel.com/docs/deployments/vercel-ignore).

Pada tahap perencanaan perbaikan deploy sebelumnya, root dan aset berjumlah **8.207.696 byte**. Sumber website, aset, dan tiga berkas dokumentasi yang dipilih saat itu berjumlah **3.792.867 byte** (sekitar **3,79 MB**), atau sekitar **5.057.156 byte / 5,06 MB** dalam base64 sebelum overhead JSON. Konfigurasi, revisi UI versi 2.0, dan catatan baru menambah sumber teks; seluruh gambar memakai berkas sebelumnya. Angka historis ini adalah perhitungan berkas input, bukan ukuran paket terkini, pengukuran request redeploy, hasil validasi unggahan, atau bukti deploy berhasil.

### Mengirim melalui Vercel CLI

Jika Vercel CLI sudah terpasang dan Anda sudah masuk ke akun yang memiliki akses project, jalankan dari root proyek:

```powershell
vercel deploy
```

Perintah tersebut membuat deployment preview. Untuk menerbitkan ke production atas pilihan Anda:

```powershell
vercel deploy --prod
```

Pilih project Vercel yang memang dimaksud bila CLI meminta penautan. Tidak ada project ID, team ID, token, atau akun yang ditanam ke konfigurasi ini. Lihat [metode deployment Vercel](https://vercel.com/docs/deployments) dan [konfigurasi vercel.json](https://vercel.com/docs/project-configuration/vercel-json).

### Jika tombol Redeploy tetap menampilkan error yang sama

Belum diketahui klien atau endpoint yang menghasilkan pesan `Request body too large. Limit: 10mb`. Pengiriman seluruh proyek dalam base64 dapat melampaui 10 MB, tetapi penyebab persisnya memerlukan log request dari jalur deploy yang digunakan.

Pengirim REST atau integrasi pihak lain harus memilih berkasnya sebelum membentuk request. Menyertakan `.vercelignore` sebagai satu berkas dalam request tidak otomatis membuat pengirim tersebut menerapkan polanya. Bila jalur Redeploy mengabaikan allowlist, konfigurasi lokal ini belum mengurangi payload jalur tersebut; perbaikannya berada pada pemilihan berkas di integrasi pengirim.

Untuk integrasi REST, gunakan daftar berkas yang sama. Alur resmi Vercel memungkinkan pengunggahan berkas terlebih dahulu, lalu pembuatan deployment memakai referensi SHA berkas, sehingga tidak perlu menanam seluruh isi base64 dalam satu request pembuatan deployment. Sumber dan akses integrasi tersebut tidak tersedia dalam proyek ini, sehingga tidak diubah atau diklaim telah diperbaiki. Dokumentasi: [deployment melalui REST API](https://vercel.com/docs/deployments#vercel-rest-api).

## Status pemeriksaan

Berkas sumber dibuat dalam workflow ship-on-write yang diminta. Tidak dilakukan preview, render, screenshot, automated test, atau validasi pascagenerasi. Karena itu hasil tidak diklaim telah diuji di browser. Tidak ada deployment yang dilakukan.

## Dashboard admin

Buka **index.html#/admin** atau tautan **Area Admin** pada footer siswa. Tersedia Ringkasan, Konten Belajar, Bank Kuis, Mini Game, Moderasi Karya, Progres Siswa, dan Pengaturan. Panduan lengkap: [ADMIN.md](ADMIN.md).

Modul admin.js dan admin.css dimuat dari entry yang sama. Draf dan publikasi disimpan di kirara.admin.v1; profil dan progres siswa tetap di kirara.v1. Konten terbit, bank soal, dan moderasi dihubungkan ke aplikasi siswa pada browser yang sama. Admin belum memakai autentikasi atau backend sekolah. Angka ringkasan berasal dari data lokal, bukan data seluruh kelas.
