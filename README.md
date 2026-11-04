# Ayam Gacor Indonesia — Website

Website company profile + landing page kemitraan (franchise) **Ayam Gacor Indonesia**, ayam goreng sambel cabe ijo.
Static site: HTML, CSS, dan JavaScript tanpa framework atau proses build.

**Website resmi:** https://ayamgacorindonesia.com/ (Netlify, auto-deploy dari branch `main` repo ini)
**Preview lama:** https://rezafauzii.github.io/ayam-gacor-website/ (GitHub Pages)

## Halaman

Satu file `index.html` dengan 6 tampilan (pindah tampilan lewat hash URL):

| Tampilan | URL | Isi |
|---|---|---|
| Beranda | `#beranda` | Hero, video reel, keunggulan, menu andalan, video food review, teaser kemitraan & outlet |
| Tentang Kami | `#tentang` | Filosofi, arti nama & warna brand, visi-misi, The Journey 2026–2030 |
| Menu | `#menu` | Menu utama, paket + nasi, ala carte, add on, Gacor Kids |
| Kemitraan | `#kemitraan` | Paket Basic (Rp65 jt) & Prime (Rp390 jt), tahapan, simulasi BEP, FAQ, form calon mitra |
| Outlet | `#outlet` | 4 outlet aktif dengan pencarian, filter wilayah, tombol rute Google Maps & WhatsApp |
| Galeri | `#galeri` | Video, foto outlet & menu, video food review (filter "Food Review"), slot testimoni |

## Animasi

Animasi dibuat ringan dan formal, tanpa library tambahan (CSS + IntersectionObserver):

- **Opening (sekali saat website pertama dibuka):** layar kuning dengan logo berputar dan hitungan 0–100, lalu tirai naik. Di Beranda, piring ayam berputar masuk, stiker "Pedasnya Nampol", label 19K, dan maskot muncul "pop". Piring ayam di hero bisa diklik: berputar, keluar partikel, dan muncul kata seperti "KRIUK!".
- Konten (judul section, kartu, foto, tabel, FAQ) muncul halus dari bawah saat di-scroll, berurutan per baris.
- Setiap kali halaman dibuka (Beranda, Menu, dst.), isi bagian atas muncul berurutan dan ilustrasi/maskot masuk pelan dari kanan; penanda menu aktif di header ikut bergeser ke menu yang diklik.
- Kartu menu, keunggulan, paket, dan outlet sedikit terangkat saat di-hover; foto galeri dan outlet zoom pelan.
- Bar target outlet di The Journey terisi saat terlihat; header mendapat bayangan tipis saat halaman di-scroll.
- Video reel autoplay tanpa suara (aturan browser); tombol "Nyalakan suara" di pojok video menyalakan audio. Musik dan sound effect di reel dibuat sendiri (sintesis), bebas lisensi.
- Jika perangkat memakai pengaturan "kurangi gerakan" (reduce motion), semua animasi otomatis mati dan konten tampil langsung.

Pengaturannya ada di `index.html`: CSS di bagian `/* ---------- Motion tipis ---------- */` dan script di bagian `Motion tipis: muncul halus saat di-scroll`.

## Video food review

Sumber: video review dari tim Ayam Gacor (Nov 2026). 6 cuplikan dipotong 12–15 detik dari video asli (bagian promo opening/giveaway yang sudah lewat tidak dipakai):

| File | Creator | Outlet | Potongan dari video asli |
|---|---|---|---|
| kol-ria-mayor-oking | Ria Apriliani | Mayor Oking | 0:12–0:26 |
| kol-putri-yasmin | Putri Permatasari | Yasmin | 0:06–0:21 |
| kol-gorila-telukjambe | Gorila Gembul | Telukjambe | 0:04–0:19 |
| kol-belva-sukahati | Belva (video tanpa suara) | Sukahati | 0:03–0:16 |
| kol-silaperz-sukahati | Silaperz | Sukahati | 0:17–0:31 |
| kol-sukakuliner-sukahati | Suka Kuliner | Sukahati | 0:16–0:30 |

Copy di website sengaja netral ("Food review", "Kata mereka yang udah nyobain"), tanpa menyebut KOL/food creator, sesuai permintaan owner.

Di Beranda video diputar otomatis tanpa suara saat terlihat di layar; klik kartu untuk membuka video dengan suara. Untuk mengganti/menambah, potong video jadi 540×960 (MP4 H.264), simpan di `assets/video/kol-<nama>.mp4` + poster `assets/img/kol-<nama>.webp`, lalu salin satu kartu `<button class="kol" ...>` di `index.html` (dan item `gi--video` di Galeri).

## Struktur folder

```
index.html            Source website (HTML + CSS + JS dalam satu file)
assets/img/           Logo, maskot, foto menu & outlet (WebP). Foto asli: paket-*, ala-*, addon-*, menu-*, outlet2-*
                      og-image.jpg (gambar preview saat link dibagikan di WhatsApp/IG/FB), favicon.png, apple-touch-icon.png
assets/video/         Video reel brand (MP4 1600×900, 21,6 detik, dengan musik & sound effect) + cuplikan food review (kol-*.mp4, 540×960, 12–15 detik)
dist/                 Versi final 1-file (semua foto, video & font ditanam), bisa dibuka offline
netlify.toml          Pengaturan Netlify (publish folder root, cache foto/video, dist/ tidak diindex Google)
robots.txt            Izin crawl Google + lokasi sitemap
sitemap.xml           Sitemap untuk Google Search Console
```

## Menjalankan di komputer

Buka `index.html` langsung di browser, atau jalankan server lokal:

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

Font (Anton & Plus Jakarta Sans) dimuat dari Google Fonts, jadi butuh internet. Untuk presentasi tanpa internet, pakai file di `dist/`.

## Data outlet aktif

Sumber: dokumen *LOKASI OUTLET 221026* dari tim Ayam Gacor.

| Outlet | Area | Jam buka | Koordinat |
|---|---|---|---|
| Ayam Gacor Mayor Oking — Jl. Raya Mayor Oking Jaya Atmaja No. 72, Cirimekar, Kec. Cibinong, Kab. Bogor 16917 | Cibinong | 10.00–22.00 | -6.4700076, 106.8607766 |
| Ayam Gacor Cibinong Sukahati — Jl. Raya Sukahati No. 84, Sukahati, Kec. Cibinong, Kab. Bogor 16913 | Cibinong | 10.00–24.00 | -6.484831, 106.8173936 |
| Ayam Gacor Yasmin — Auto 2000, Jl. Ring Road Taman Yasmin RT.05/RW.04, Cibadak, Tanah Sareal, Kota Bogor 16113 | Kota Bogor | 10.00–22.00 | -6.5561693, 106.7772751 |
| Ayam Gacor Telukjambe — Jl. HS. Ronggo Waluyo, Sirnabaya, Telukjambe Timur, Karawang 41360 (plus code M8G3+HGW) | Karawang | 10.00–22.00 | -6.323546, 107.3038235 |

## Sumber konten

- **Business Proposal Ayam Gacor:** paket kemitraan, tahapan, proyeksi keuangan, The Journey 2026–2030.
- **Pricelist Ayam Gacor Indonesia (biasa & Kids) + folder foto "01. Website" dari tim Ayam Gacor (Okt 2026):** harga menu, ala carte, add on, foto menu (paket + nasi, ala carte, add on) dan foto 4 outlet.
- **Logo Guideline Ayam Gacor 2026:** logo, maskot, palet warna (#EE2A24, #F68C1F, #F9ED23, #A1CD3A, #569D44, #026C44, #FFFFFF), filosofi brand.
- **Kontak:** Hotline Franchise 0823 1972 7767, WhatsApp order 0813-9631-093, Instagram @ayamgacor.indonesia, TikTok @ayamgacorindonesia.

## Yang sering diubah

- **Data outlet**: di `index.html`, cari `const OUTLETS = [`. Tiap outlet punya `nama`, `area`, `alamat`, `jam`, `status` (`"buka"` / `"segera"`), `lat`, `lng` (titik koordinat), dan `foto`. Tombol "Rute ke sini" membuka Google Maps ke titik koordinat itu.
- **Harga menu & paket**: langsung di HTML bagian `id="v-menu"` dan `id="v-kemitraan"`.
- **Simulasi BEP**: konstanta di script (`OPEX`, `MARGIN`, `DAYS`, `INVEST`) mengikuti proposal kemitraan: biaya operasional Rp12 jt/bulan, marjin 55%, 30 hari, investasi Rp65 jt.
- **Kontak**: hotline franchise `6282319727767` dan WhatsApp order `628139631093` (cari `WA_FRANCHISE`, `WA_ORDER`, dan link `wa.me`).
- **Warna brand**: variabel CSS di `:root` (`--merah`, `--kuning`, `--hijau-tua`, dst.) sesuai Logo Guideline 2026.

## Status go-live

- Sudah siap tayang di domain utama: `noindex` sudah dihapus, ada `canonical` + Open Graph ke https://ayamgacorindonesia.com/, `robots.txt`, dan `sitemap.xml`.
- Kalau nanti domain berubah, ganti `ayamgacorindonesia.com` di `index.html` (canonical, og:url, og:image), `robots.txt`, dan `sitemap.xml`.
- Form calon mitra saat ini meneruskan data ke WhatsApp hotline. Integrasi ke email + Google Sheets belum dipasang.
- Masih perlu materi asli: testimoni mitra/pelanggan. Reel di `assets/video/reel.mp4` dibuat dari foto resmi tim Ayam Gacor; ganti dengan video produksi kalau sudah ada.
- Belum ada tracking Google Analytics 4 / Meta Pixel. Setelah tayang, daftarkan domain di Google Search Console dan submit `sitemap.xml`.
- Semua tombol "Pesan via WA" di kartu outlet masih ke nomor order pusat (0813-9631-093). Kalau tiap cabang punya nomor sendiri, tambahkan field nomor WA di tiap outlet pada `OUTLETS`, lalu pakai field itu (bukan `WA_ORDER`) saat membuat link "Pesan via WA".
- Proyeksi BEP skenario rendah di proposal tertulis 14,5 bulan; hitungan website (Rp65 jt ÷ Rp4,5 jt) menampilkan 14,4 bulan. Samakan angka di proposal kalau perlu.

## Belum ditampilkan di website

Ada di pricelist terbaru tapi belum dibuat section-nya: Paket Komplit (Cumi 32K, Ayam 33K), Paket MBG (MBG 3 55K, MBG 4 79K, MBG 5 109K), Paket Duo (Ayam 54K, Daging 70K), dan minuman (Frestea 7K, Air Mineral 5K).

## Deploy

Website di-host di **Netlify** dan tersambung ke repo ini: setiap commit ke branch `main` otomatis tayang di https://ayamgacorindonesia.com/ dalam 1–2 menit. Tidak ada proses build (pengaturan di `netlify.toml`).

Cara update konten: edit/upload file di GitHub → **Commit changes** → tunggu deploy selesai di Netlify (tab *Deploys*).
