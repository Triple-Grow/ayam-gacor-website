# Ayam Gacor Indonesia — Website

Website company profile + landing page kemitraan (franchise) **Ayam Gacor Indonesia**, ayam goreng sambel cabe ijo.
Static site: HTML, CSS, dan JavaScript tanpa framework atau proses build.

## Halaman

Satu file `index.html` dengan 6 tampilan (pindah tampilan lewat hash URL):

| Tampilan | URL | Isi |
|---|---|---|
| Beranda | `#beranda` | Hero, video reel, keunggulan, menu andalan, teaser kemitraan & outlet |
| Tentang Kami | `#tentang` | Filosofi, arti nama & warna brand, visi-misi, The Journey 2026–2030 |
| Menu | `#menu` | Menu utama, paket + nasi, ala carte, add on, Gacor Kids |
| Kemitraan | `#kemitraan` | Paket Basic (Rp65 jt) & Prime (Rp390 jt), tahapan, simulasi BEP, FAQ, form calon mitra |
| Outlet | `#outlet` | 4 outlet aktif dengan pencarian, filter wilayah, tombol rute Google Maps & WhatsApp |
| Galeri | `#galeri` | Video, foto outlet & menu, slot testimoni |

## Struktur folder

```
index.html            Source website (HTML + CSS + JS dalam satu file)
assets/img/           Logo, maskot, foto menu & outlet (WebP)
assets/video/         Video reel brand (MP4, 17 detik, tanpa suara)
dist/                 Versi final 1-file (semua foto, video & font ditanam), bisa dibuka offline
```

## Menjalankan di komputer

Buka `index.html` langsung di browser, atau jalankan server lokal:

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

Font (Anton & Plus Jakarta Sans) dimuat dari Google Fonts, jadi butuh internet. Untuk presentasi tanpa internet, pakai file di `dist/`.

## Yang sering diubah

- **Data outlet**: di `index.html`, cari `const OUTLETS = [`. Tiap outlet punya `nama`, `area`, `alamat`, `jam`, `status` (`"buka"` / `"segera"`), `lat`, `lng` (titik koordinat), dan `foto`. Tombol "Rute ke sini" membuka Google Maps ke titik koordinat itu.
- **Harga menu & paket**: langsung di HTML bagian `id="v-menu"` dan `id="v-kemitraan"`.
- **Simulasi BEP**: konstanta di script (`OPEX`, `MARGIN`, `DAYS`, `INVEST`) mengikuti proposal kemitraan: biaya operasional Rp12 jt/bulan, marjin 55%, 30 hari, investasi Rp65 jt.
- **Kontak**: hotline franchise `6282319727767` dan WhatsApp order `628139631093` (cari `WA_FRANCHISE`, `WA_ORDER`, dan link `wa.me`).
- **Warna brand**: variabel CSS di `:root` (`--merah`, `--kuning`, `--hijau-tua`, dst.) sesuai Logo Guideline 2026.

## Catatan sebelum go-live

- `index.html` masih memakai `<meta name="robots" content="noindex, nofollow">` supaya versi preview tidak masuk Google. Hapus baris itu saat website resmi tayang di domain sendiri.
- Form calon mitra saat ini meneruskan data ke WhatsApp hotline. Integrasi ke email + Google Sheets belum dipasang.
- Masih perlu materi asli: video produksi (pengganti reel sementara), foto menu Yakitori Gacor, Telur Gacor, dan Telur, serta testimoni mitra/pelanggan.
- Belum ada tracking Google Analytics 4 / Meta Pixel.

## Deploy

Karena static, bisa di-host di mana saja: GitHub Pages, Netlify, Vercel, atau hosting biasa. Cukup upload isi repo ini; `index.html` adalah halaman utamanya.
