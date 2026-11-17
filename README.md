# Catatan Keuangan

Aplikasi web untuk mencatat pemasukan dan pengeluaran pribadi, mengatur anggaran bulanan, dan melihat grafiknya. Bisa dipasang di HP atau laptop sebagai aplikasi (PWA) dan tetap bisa dibuka tanpa internet.

**Demo:** https://NAMAMU.github.io/NAMA-REPO/ *(ganti dengan alamat Pages-mu)*

<!-- Tambahkan screenshot di sini, misalnya:
![Tampilan utama](screenshots/utama.png)
-->

## Fitur

- **Catat transaksi**: pemasukan dan pengeluaran dengan tanggal, kategori, jumlah (titik ribuan otomatis dan mendukung desimal, misalnya 12.500,75), dan catatan
- **Edit dan hapus** transaksi kapan saja
- **Ringkasan**: total pemasukan, pengeluaran, dan saldo
- **Grafik**: pengeluaran per bulan (batang) dan per kategori (donat)
- **Filter bulan** untuk riwayat, ringkasan, dan grafik kategori
- **Anggaran bulanan per kategori** dengan batang progres dan peringatan saat mencapai 80% dan saat terlampaui
- **Transaksi berulang**: tagihan atau gaji bulanan dibuat otomatis begitu tanggalnya tiba
- **Ekspor dan impor CSV**, dengan pencegahan data ganda saat impor
- **Cadangan JSON**: simpan dan pulihkan semua data (transaksi, anggaran, aturan berulang)
- **PWA**: bisa dipasang, berjalan offline, dan mengikuti mode terang atau gelap

## Teknologi

- HTML, CSS, dan JavaScript murni, tanpa framework dan tanpa proses build
- [Chart.js](https://www.chartjs.org) 4.4.1 untuk grafik (disimpan lokal di `chart.umd.js`, lisensi MIT)
- `localStorage` untuk penyimpanan data
- Service worker dan Web App Manifest untuk fitur PWA

## Menjalankan di komputer

PWA hanya berfungsi lewat `https://` atau `localhost`, jadi jalankan server lokal:

```bash
python3 -m http.server 8000
```

Lalu buka <http://localhost:8000>.

Membuka `index.html` langsung dengan klik dua kali tetap menampilkan aplikasinya, tetapi pemasangan dan mode offline tidak aktif.

## Memasang sebagai aplikasi

- **Android (Chrome):** tekan tombol *Pasang aplikasi* di pojok kanan atas, atau menu ⋮ lalu *Instal aplikasi*
- **iPhone (Safari):** tombol *Bagikan* lalu *Tambah ke Layar Utama*
- **Laptop (Chrome atau Edge):** ikon pasang di kanan bilah alamat

## Struktur proyek

```
.
├── index.html               # aplikasi (HTML, CSS, dan JavaScript)
├── manifest.webmanifest     # identitas aplikasi untuk PWA
├── sw.js                    # service worker (cache dan mode offline)
├── chart.umd.js             # Chart.js
└── icons/                   # ikon aplikasi
```

## Data dan privasi

Semua data disimpan di browser perangkatmu (`localStorage`) dan tidak dikirim ke server mana pun. Konsekuensinya:

- Data tidak otomatis tersinkron antarperangkat. Gunakan **Cadangkan semua data** lalu **Pulihkan cadangan** untuk memindahkannya.
- Menghapus data situs di pengaturan browser juga menghapus catatanmu. Buat cadangan secara berkala.
- Jangan mengunggah file CSV atau cadangan JSON berisi data pribadi ke repositori publik.

## Catatan pengembangan

Setelah mengubah file yang di-cache (daftar `DAFTAR_FILE` di `sw.js`), naikkan nilai `VERSI` di `sw.js` (misalnya `keuangan-v2`) agar pengguna menerima versi baru.

## Ide pengembangan

- Sinkronisasi antarperangkat dengan backend (Firebase atau Supabase) dan login
- Beberapa dompet atau rekening
- Kategori yang bisa diubah sendiri
- Pencarian transaksi
- Pemisahan kode menjadi `style.css` dan `script.js`, serta pengujian otomatis

## Lisensi

Pilih lisensi untuk proyekmu, misalnya [MIT](https://choosealicense.com/licenses/mit/). Chart.js berlisensi MIT.
