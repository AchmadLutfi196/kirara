# KIRARA Design System

Versi 2.0 · `kirara-design-spec-2.0-storybook`.

UI Kit interaktif: **`index.html#/ui-kit`**. Token mesin: `design-tokens.json`. Token CSS aktif: `:root` pada `styles.css`. Sumber tetap HTML/CSS/JavaScript lokal dengan entry `index.html`.

## Arah visual dan cakupan

Seluruh KIRARA memakai satu dunia **petualangan budaya Madura**: lanskap desa, cream hangat, bingkai kayu, terracotta, aksen emas dan hijau, judul sans-serif membulat, serta karakter asli. Permintaan terbaru pengguna memperluas gaya yang semula terbatas pada Menu Utama dan onboarding ke seluruh aplikasi. Arah ini melanjutkan referensi ilustratif yang dipilih pengguna; cream, bentuk papan kayu, dan kedalaman kontrol merupakan pilihan berdasarkan referensi tersebut.

Cakupan: onboarding, Menu Utama, Pilih Cerita, seluruh Story Reader, Mini Game, Kuis Budaya, Hasil Akhir, Ruang Karya, Profil Siswa, Materi, UI Kit, navbar, footer, dialog, dan notifikasi. Struktur konten serta logika belajar tetap dipertahankan.

Screenshot modern awal tetap menjadi rujukan konten dan alur. Referensi serif tidak menjadi sistem tipografi. Tidak ada campuran navbar alternatif, kontrol presenter, atau navigasi desainer di menu siswa. UI Kit diakses melalui rutenya sendiri.

## Prinsip komposisi

- Satu halaman memiliki satu tujuan utama. Pembelajaran mendahului gamifikasi.
- Bingkai kayu menyatukan komponen; ketebalan dan elevasi mengikuti peran, bukan ditumpuk pada setiap elemen.
- Menu dan onboarding menampilkan lanskap serta karakter lebih kuat. Pada pembaca dan kuis, lanskap lebih ringan dan area tugas memakai panel putih opak.
- Isi bacaan, jawaban, input, serta informasi penting berada di permukaan opak. Teks tidak dipanggang ke gambar.
- Konten utama menggunakan flex/grid normal flow dan layout primitives. Dialog, toast, dan dekorasi latar memiliki lapisan tersendiri.
- Tampilan desktop, tablet, dan mobile mengatur ulang komposisi, bukan mengecilkan seluruh halaman.

## Palette

| Token CSS | Nilai | Penggunaan |
|---|---|---|
| `--background` | `#FFF9F2` | Ground utama |
| `--surface` | `#FFF4DD` | Panel cream dan papan |
| `--reading-surface` | `#FFFFFF` | Bacaan, kuis, input, frame gambar |
| `--surface-secondary` | `#F6EADF` | Area sekunder dan disabled |
| `--primary` | `#A83D24` | Aksi dan lokasi aktif |
| `--primary-hover` | `#852D19` | Hover dan kedalaman aksi |
| `--primary-soft` | `#FBE9E1` | Pilihan aktif dan penekanan ringan |
| `--text` | `#382B24` | Teks utama |
| `--muted` | `#69584A` | Helper dan caption |
| `--world-wood` | `#8A5038` | Bingkai utama |
| `--world-wood-dark` | `#613A2B` | Teks papan dan kedalaman |
| `--world-wood-light` | `#C28A62` | Bingkai komponen |
| `--world-plaque-line` | `#E4BD95` | Detail panel dan separator |
| `--world-sky` | `#A7D1D7` | Acuan langit dan cadangan latar |
| `--world-meadow` | `#AFC797` | Acuan lanskap |
| `--gold` / `--gold-text` | `#F2BF45` / `#604600` | Reward dengan teks terbaca |
| `--reward-surface` | `#FFF2CA` | Background lencana dan poin |
| `--success` / `--success-soft` | `#2D6845` / `#E8F2E8` | Benar dan sukses |
| `--error` / `--error-soft` | `#AE2634` / `#FCECEF` | Salah dan error |
| `--focus` | `#214F75` | Fokus keyboard |

Teks isi memakai foreground gelap pada panel terang, dengan sasaran kontras minimal 4.5:1. Teks putih dipakai pada aksi terracotta yang gelap. Status memiliki teks atau ikon selain warna. Tidak ada dark mode pada cakupan ini.

## Tipografi

Maksimal dua keluarga font: **Trebuchet MS** untuk heading dan **Segoe UI** untuk body, keduanya dengan fallback sans-serif. Ini pilihan implementasi dari spesifikasi, bukan identifikasi pasti font pada screenshot. Tidak ada unduhan font eksternal.

| Hierarki | Ukuran | Weight / line-height |
|---|---|---|
| Display | `clamp(32px,4vw,56px)` | 700 / 1.2 |
| Page title | `clamp(28px,2.4vw,40px)` | 700 / 1.2–1.3 |
| Section | 24px | 700 / 1.2–1.4 |
| Card | 20px | 700 / 1.3 |
| Body | 18px | 400 / 1.6 |
| Reader | 18px, dapat diperbesar 22px | 400 / 1.7 |
| Label/caption | 16px | 400 atau 600 / 1.5–1.6 |

Outline cream terbatas pada judul besar di atas lanskap. Paragraf reader maksimal 65ch. Judul dan copy utama membungkus utuh; label aksi, waktu, jumlah, dan status tetap terbaca tanpa pemotongan. Data panjang di detail membungkus; nama profil menggunakan wrapping agar tidak keluar panel.

## Token, bentuk, dan elevasi

- Spacing: 4, 8, 12, 16, 24, 32, 48, 64, 96px.
- Radius: kontrol 12px, kartu 16px, panel/papan 24px.
- Border: 2px pada komponen umum; maksimal 4px pada bingkai papan utama. Detail dekoratif tipis boleh 1px.
- `--world-panel-shadow`: kedalaman bawah ringan 4px dan shadow lembut.
- `--world-control-shadow`: kedalaman bawah 4px untuk kontrol utama.
- `--world-board-shadow` dan `--world-board-inset`: kedalaman 8px serta bingkai dalam untuk papan menu.
- Semua `--entry-*` menjadi alias token `--world-*` atau token global. Tema entry bukan palette kedua.
- Ikon SVG outline yang ada: viewBox 24, stroke 2, rounded caps/joins. Tidak memakai emoji fungsional.
- Tombol minimal 48px, input minimal 52px, target sentuh minimal 44px, pin Mini Game 44px.
- Fokus keyboard outline biru 3px, offset 4px; papan menu dapat memakai outline 4px.

## Komponen dan state

| Komponen | Sumber/kait | Aturan |
|---|---|---|
| App shell | `renderHeader()`, `.site-header`, `.footer` | Chrome cream dengan detail kayu pada semua rute |
| Navigation | `.nav-item`, `#main-nav` | Lima label yang sama, active terracotta, menu mobile eksplisit |
| Primary button | `.btn-primary` | Terracotta, teks putih, kedalaman terbatas |
| Secondary button | `.btn-secondary` | Cream, bingkai kayu, teks gelap |
| Ghost button | `.btn-ghost` | Ringan untuk kembali atau aksi sekunder |
| Card/panel | `.card`, `.panel` | Bingkai dan radius konsisten; isi mengikuti peran |
| Story card | `storyCard()` | Gambar utuh, metadata, judul, deskripsi, reward, progress, CTA |
| Reader | `reader()`, `.reader-copy` | Putih opak, lebar paragraf dibatasi, toolbar dan navigasi jelas |
| Audio | `audioPlayer()` | Status belum tersedia tetap nyata; kontrol disabled |
| Matching | `miniGame()`, `bindMatchConnections()` | Papan putih, kartu cream, pin/tali aktif; state warna dan teks |
| Quiz option | `.quiz-option` | Padding dan ukuran stabil pada selected/correct/wrong |
| Progress | `progress()` | Label dan nilai terpisah; nilai tidak terpotong |
| Points/badge/chip | `.points`, `.badge`, `.chip` | Poin aktual; reward menjadi pendukung belajar |
| Character dialogue | `guide()` | Satu pesan, karakter asli, ukuran sesuai halaman |
| Artwork card | `galleryCards()` | Gambar utuh, kategori, judul, pembuat, apresiasi |
| Gallery tools | `.gallery-toolbar`, `.filters` | Label persisten, pencarian, sortir, filter aktif |
| Profile | `profile()` | Identitas, progress dan lencana tanpa struktur sosial |
| Input/search | `.input`, `.field` | Label, fokus, validasi blur/submit, pesan error dekat field |
| Notification | `notice()`, `toast()` | Informasi/sukses/error memakai teks dan ikon |
| Modal | native `dialog` | Label judul, close, Escape, fokus kembali |
| UI Kit | `kit()` | Contoh komponen nyata, state, matching, aset, dan aturan responsif |

Default, hover, focus, pressed, disabled, loading, empty, success, dan failure digunakan sesuai kebutuhan alur. Loading hanya untuk proses nyata seperti FileReader, atau contoh UI Kit yang jelas diberi konteks. Tidak ada loading palsu untuk perpindahan lokal yang langsung selesai.

## Interaksi yang dipertahankan

- Nama onboarding, validasi, edit profil, dan localStorage.
- Lima menu navbar, enam fitur Menu Utama, navigasi compact, posisi scroll per rute.
- Tiga cerita: Jokotole & Kuda Si Giga, Putri Potre Koneng, Ke' Lesap Sang Pemberani.
- Cuplikan Jokotole, glosarium, refleksi, ukuran teks, dan penanda naskah/audio belum tersedia.
- Mini Game: lima pasangan, drag dari pin ke kartu kanan, preview tali, drop target, pembatalan, scroll tepi, klik/keyboard, pemeriksaan, penguncian benar, perbaikan salah, reset, timer, skor, dan hasil.
- Kuis: satu soal referensi, pilihan, ragu-ragu, review, penyelesaian, timer, hasil, dan ulangi.
- Galeri: pencarian, filter, sortir, detail, apresiasi, unggah gambar lokal, validasi dan feedback quota.
- Profil: progress, lencana, aktivitas tersedia, dan skor terbaik.

## Responsive

| Lebar | Perilaku |
|---|---|
| 375–767px | Navbar compact, grid utama satu kolom, reader vertikal, navigasi reader bertumpuk, kuis satu kolom, matching dua kolom sentuh |
| 768–1023px | Grid dua kolom bila muat, sidebar masuk alur utama, karakter ringkas |
| 1024–1279px | Navbar penuh, reader dua kolom, grid sesuai ruang, detail chrome ringkas |
| 1280px | Gutter 32px dan komposisi desktop |
| 1440px ke atas | Gutter 48px, konten maksimal 1344px |

Breakpoints mengatur ulang konten. Pada mobile, tombol reader dan hasil mendapat ruang satu baris penuh agar label tidak bertabrakan. Form dan dialog tetap muat layar; matching menjaga pin yang mudah disentuh. Pembesaran teks tidak dinonaktifkan.

Motion: enter 180ms ease-out, exit 120ms ease-in. Hover/pressed memberi feedback kontrol, tanpa animasi lanskap atau karakter terus-menerus. Reduced-motion menonaktifkan transisi dan pergeseran yang tidak diperlukan.

## Aset dan geometri

`assets/kirara-village-background.png` berukuran 1556 × 1011px, hasil edit bawaan dari referensi ilustratif pengguna. Sumber, prompt, serta batas rekonstruksinya tercatat pada README. Satu gambar tersebut dipakai ulang, tanpa gambar baru atau library tambahan.

Logo, Sakera, Marlena, ilustrasi cerita, dan karya tetap memakai aset lokal asli. Gambar konten mempertahankan width/height intrinsik dan `height:auto`, tampil full-frame. Lanskap merupakan dekorasi yang boleh memakai cover-crop. Contoh lanskap di UI Kit tampil utuh karena berperan sebagai konten dokumentasi.

`body.world-theme` mengaktifkan tema. `data-surface` membedakan entry, reader, quiz, game, kit, dan learning untuk pengaturan intensitas. Pseudo-element latar dekoratif tidak menutup kontrol. Entry masih memakai `.storybook-surface` dengan sumber lanskap yang sama; browser menggunakan ulang file yang sama.

## Konten dan progress

- Asal, estimasi baca 7/6/8 menit, serta reward 50 poin mengikuti screenshot sumber.
- Naskah lengkap belum tersedia. Membuka cuplikan tidak menyelesaikan cerita dan tidak memberi reward cerita.
- Audio asli belum tersedia; tidak ada playback atau waktu narasi palsu.
- Mini Game memberi skor 100 per pasangan benar dan hadiah total 500 hanya sekali.
- Kuis menggunakan satu soal referensi. Nilai aktual 0 atau 100; 20 poin hanya sekali bila benar.
- Progress profil mengacu pada dua aktivitas tersedia, bukan penguasaan semua materi.
- Karya awal, nama, dan angka apresiasi merupakan contoh referensi yang tetap dilabeli. Unggahan baru hanya lokal.

## Handoff Next.js dan Tailwind CSS

Komponen bersama: `AppShell`, `MainNavigation`, `PointIndicator`, `Button`, `Panel`, `Badge`, `Chip`, `ProgressBar`, `CharacterDialogue`, `Field`, `Notification`, dan `Dialog`.

Komponen permukaan: `EntryLandscape`, `EntryBrand`, `LearningCompanion`, `WoodenMenuLink`, `OnboardingForm`, `LearningSteps`, `StoryCard`, `StoryReader`, `AudioPlayer`, `MatchingBoard`, `CultureCard`, `QuizScreen`, `QuizOption`, `ResultSummary`, `ArtworkCard`, `GalleryToolbar`, dan `StudentProfile`.

Letakkan token global pada globals.css dan konsumsi dengan Tailwind custom properties, misalnya `bg-[var(--surface)]`, `text-[var(--text)]`, dan `rounded-[var(--r-card)]`. Satu provider/theme membungkus semua rute. Alias entry hanya mendukung komponen yang sudah ada; jangan membuat ulang palette yang berbeda.

Data cerita, soal, pasangan, dan karya tetap terpisah dari komponen presentasi. State browser, localStorage, pointer events, FileReader, timer, dan dialog membutuhkan komponen client. Pada SSR, jangan mengakses window/localStorage saat render server. Jangan menyalin innerHTML ke React; ubah ke JSX dan props.

## Deployment dan status

`.vercelignore` dan `vercel.json` tetap dipertahankan. Semua aset tetap lokal dan tidak menambah gambar besar. Aturan daftar berkas deploy serta batas integrasi Redeploy dijelaskan pada README. Tidak ada deployment yang dilakukan.

Sumber ditulis mengikuti kontrak desain. Tidak ada klaim preview, render, screenshot, pengujian, atau validasi browser pascagenerasi.
## Perluasan admin 1.0

Design Spec: kirara-admin-design-spec-1.0. Area pengelola mewarisi palet dan dua font KIRARA dengan panel putih opak, border hangat 1px, radius 12/16/24px, dan shadow halus. Lanskap serta dekorasi kayu yang tebal tidak memenuhi area kerja. Ilustrasi buku menu yang sudah ada dipakai pada sapaan dashboard.

Sidebar 248px pada desktop, 232px pada laptop; di bawah 1024px navigasi menjadi menu details dalam normal flow. Pada 375px daftar reflow, editor satu kolom, kontrol minimal 44px, label 16px, judul 28–40px, dan paragraf dibatasi sekitar 72ch. Ikon admin meneruskan SVG outline 24px stroke 2. Status selalu berteks dan berikon.

Token area pengelola berada di root admin.css. Tujuh bagian admin berbagi shell, pencarian/filter, daftar, editor, status, dialog konfirmasi, dan feedback penyimpanan. Student navbar, karakter, ilustrasi, serta enam ikon Menu Utama tetap dipertahankan. Panduan kontrak data: ADMIN.md.
