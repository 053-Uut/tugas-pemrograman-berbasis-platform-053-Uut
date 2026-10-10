# Perbandingan Component CSS dan Utility Classes

## 1. Perbandingan Implementasi

Pada tugas ini saya membuat dua kartu profil mahasiswa dengan isi yang sama, yaitu foto, nama lengkap, NIM, dan tombol "Lihat Profil". Versi pertama menggunakan pendekatan component CSS dengan CSS yang ditulis di dalam tag `<style>`, sedangkan versi kedua menggunakan Tailwind CSS dengan utility classes.

### Versi Component CSS

Pada versi component, styling dibuat menggunakan selector CSS seperti `.card`, `.photo`, `.name`, `.nim`, dan `.btn`.

Jumlah baris CSS yang digunakan adalah **64 baris CSS tidak kosong**. Jika baris kosong juga dihitung, blok CSS terdiri dari **76 baris**.

### Versi Utility Classes

Pada versi utility, styling dilakukan langsung menggunakan class Tailwind pada elemen HTML dan tidak menggunakan tag `<style>` maupun atribut `style`.

Pada kode yang dibuat, terdapat **38 utility class** yang digunakan untuk mengatur layout, ukuran, warna, jarak, teks, bentuk, dan efek hover.

## 2. Perbandingan Waktu Pengerjaan

Menurut pengalaman saya saat membuat kedua versi, pendekatan utility classes terasa lebih cepat karena saya tidak perlu membuat selector CSS dan menuliskan aturan CSS satu per satu. Saya cukup menambahkan class Tailwind sesuai kebutuhan pada elemen HTML.

Pada versi component CSS, prosesnya membutuhkan lebih banyak penulisan karena setiap bagian harus dibuatkan aturan CSS sendiri. Namun, struktur CSS lebih mudah dipisahkan dari HTML sehingga lebih nyaman jika styling yang sama akan digunakan pada beberapa komponen.

## 3. Kemudahan Mengubah Tema

Pada versi component CSS, perubahan tema seperti warna tombol, ukuran kartu, atau bentuk kartu dapat dilakukan dengan mengubah aturan CSS pada selector tertentu. Hal ini cukup mudah jika beberapa halaman menggunakan komponen dan aturan CSS yang sama.

Pada versi utility classes, perubahan tema dapat dilakukan langsung dengan mengganti class Tailwind pada elemen. Cara ini cepat untuk perubahan sederhana, tetapi jika class yang digunakan sudah sangat panjang, kode HTML dapat menjadi lebih sulit dibaca.

## 4. Pendekatan yang Saya Pilih

Untuk halaman yang memiliki banyak komponen dengan desain yang konsisten, saya lebih memilih pendekatan component CSS karena aturan tampilannya dapat dikelompokkan dan digunakan kembali dengan selector seperti `.card` dan `.btn`.

Untuk halaman sederhana atau pembuatan tampilan dengan cepat, saya lebih memilih utility classes karena styling dapat dilakukan langsung pada elemen tanpa membuat banyak aturan CSS tambahan.

## 5. Kesimpulan

Kedua pendekatan dapat digunakan untuk membuat tampilan kartu yang sama. Component CSS lebih terstruktur untuk pengelolaan style yang berulang, sedangkan utility classes lebih cepat dan praktis untuk membuat atau mengubah tampilan secara langsung pada HTML.

## 6. Bukti Pengerjaan

Screenshot hasil pengujian kedua versi disimpan di folder `screenshots/` pada folder `frontend/web/`.

- `screenshots/tm1-component-laptop.png`
- `screenshots/tm1-component-360.png`
- `screenshots/tm1-utility-laptop.png`
- `screenshots/tm1-utility-360.png`

Screenshot tersebut menunjukkan hasil tampilan kartu profil menggunakan component CSS dan utility classes pada layar laptop serta ukuran layar 360 piksel.