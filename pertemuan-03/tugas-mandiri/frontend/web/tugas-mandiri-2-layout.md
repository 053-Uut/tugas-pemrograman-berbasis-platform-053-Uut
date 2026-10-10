# Laporan Tugas Mandiri 2 — Layout Responsif dengan Tailwind CSS

## 1. Tujuan

Tujuan tugas ini adalah memahami penggunaan Tailwind CSS untuk membuat layout halaman web yang responsif. Halaman dibuat dengan navbar, hero, tiga kartu layanan, bagian tentang, dan footer. Tugas ini juga melatih penggunaan Flexbox, Grid, utility classes, breakpoint responsif, serta efek hover.

## 2. Implementasi

Pada tugas ini saya membuat halaman web bertema KampusKu menggunakan Tailwind CSS melalui CDN. Halaman terdiri dari beberapa bagian berikut:

1. **Navbar:** Menampilkan nama KampusKu dan menu navigasi Beranda, Layanan, serta Tentang.
2. **Hero:** Menampilkan judul sambutan, deskripsi singkat, dan tombol Jelajahi Layanan.
3. **Tiga kartu layanan:** Menampilkan Materi Kuliah, Jadwal Kuliah, dan Komunitas.
4. **Bagian Tentang:** Menampilkan deskripsi singkat mengenai KampusKu.
5. **Footer:** Menampilkan informasi hak cipta dan keterangan tugas.

Bagian navbar menggunakan utility classes Flexbox untuk mengatur susunan elemen. Class `flex-col` digunakan untuk susunan vertikal pada layar kecil, sedangkan `md:flex-row` digunakan untuk susunan horizontal pada layar yang lebih besar.

Bagian kartu menggunakan CSS Grid melalui utility classes `grid-cols-1`, `md:grid-cols-2`, dan `lg:grid-cols-3`. Class tersebut mengatur jumlah kolom berdasarkan ukuran layar. Class `gap-*` digunakan untuk mengatur jarak antar elemen, sedangkan `hover:*` digunakan untuk memberikan efek ketika kursor diarahkan ke tombol, tautan, dan kartu.

Seluruh styling dibuat menggunakan utility classes Tailwind CSS tanpa menambahkan CSS kustom.

## 3. Cara Menjalankan

1. Buka folder `pertemuan-03/tugas-mandiri/frontend/web/`.
2. Buka file `tugas-mandiri-2-layout.html` menggunakan browser atau ekstensi Live Server di VS Code.
3. Pastikan koneksi internet tersedia agar Tailwind CSS CDN dapat dimuat.
4. Periksa tampilan halaman pada ukuran laptop.
5. Gunakan DevTools browser untuk menguji tampilan pada ukuran layar 360 × 800 piksel.
6. Periksa susunan kartu, navigasi, dan kemungkinan scroll horizontal pada layar kecil.

## 4. Hasil Pengujian

Berdasarkan pengujian pada browser, halaman berhasil menampilkan navbar, hero, tiga kartu layanan, bagian Tentang KampusKu, dan footer.

Layout kartu dirancang menggunakan satu kolom pada layar kecil, dua kolom pada breakpoint `md`, dan tiga kolom pada breakpoint `lg`. Dengan demikian, susunan kartu menyesuaikan lebar layar.

Efek hover diterapkan pada tautan navigasi, tombol, dan kartu layanan. Pengujian dilakukan pada tampilan laptop dan ukuran layar 360 × 800 piksel untuk memeriksa responsivitas halaman.

## 5. Bukti Pengerjaan

Screenshot hasil pengujian disimpan di folder `screenshots/` pada folder `frontend/web/`.

- `screenshots/tm2-layout-laptop.png`
- `screenshots/tm2-layout-360.png`
- `screenshots/tm2-layout-360-bawah.png`

Screenshot digunakan untuk menunjukkan tampilan halaman pada laptop dan perangkat berukuran 360 piksel, termasuk bagian bawah halaman apabila diperlukan.

## 6. Kesimpulan

Melalui tugas ini, saya memahami bahwa Tailwind CSS dapat digunakan untuk membuat layout web responsif tanpa menulis CSS kustom. Utility classes untuk Flexbox, Grid, jarak, breakpoint, dan hover membantu menyusun halaman secara praktis. Penggunaan breakpoint memungkinkan tata letak menyesuaikan ukuran layar sehingga halaman lebih nyaman digunakan pada laptop maupun perangkat berukuran kecil.