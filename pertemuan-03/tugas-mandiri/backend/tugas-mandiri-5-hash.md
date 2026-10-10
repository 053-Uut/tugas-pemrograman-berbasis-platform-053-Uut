# Tugas Mandiri 5 — Hashing, Enkripsi, dan Keamanan Kunci Rahasia

**Nama:** Barrotut Taqiyah  
**NIM:** 2024520053  
**Program Studi:** Informatika  
**Mata Kuliah:** Pemrograman Berbasis Platform

## 1. Tujuan

Tujuan tugas ini adalah memahami perbedaan hashing dan enkripsi, mengetahui cara kerja bcrypt dalam melindungi kata sandi, serta memahami pentingnya menjaga kerahasiaan kunci JWT dan memeriksa keamanan repository.

## 2. Alat yang Digunakan

1. Node.js untuk menjalankan perintah JavaScript.
2. npm untuk memasang pustaka yang diperlukan.
3. Pustaka `bcryptjs` untuk melakukan hashing kata sandi.
4. Git Bash untuk menjalankan perintah pemeriksaan keamanan repository.
5. Visual Studio Code untuk membuat dan mengedit laporan.

## 3. Data Pengujian

Pada pengujian ini, kata sandi contoh yang digunakan adalah `sama`. Proses hashing dilakukan menggunakan bcrypt dengan cost factor 10.

### 3.1 Hash Pertama

```text
$2b$10$d/GC87Wzp6rhnCAqiWG3Yu.kMII8X6b7u3.zcp28.FfzZbMmMq5Pq
```

### 3.2 Hash Kedua

```text
$2b$10$nS/V/MCct2QIl4819gtn/efi1GhZCWJqT1OLKbCK.LTrrWzgT0MV6
```

**Hasil pengujian:** Kedua hash memiliki nilai berbeda meskipun dibuat dari kata sandi yang sama. Hal ini terjadi karena bcrypt menggunakan salt acak pada setiap proses hashing.

## 4. Analisis Hashing dengan bcrypt

### 4.1 Perbedaan Hashing dan Enkripsi

Hashing merupakan proses satu arah yang mengubah data menjadi nilai hash dan tidak dirancang untuk mengembalikan data asli secara langsung. Sementara itu, enkripsi mengubah data menggunakan kunci agar data dapat dikembalikan melalui proses dekripsi dengan kunci yang sesuai.

### 4.2 Alasan Aplikasi Menyimpan Hash Kata Sandi

Aplikasi menyimpan hash kata sandi agar kata sandi asli tidak tersimpan dalam bentuk teks biasa di dalam basis data. Dengan cara ini, risiko terbukanya kata sandi asli dapat dikurangi apabila basis data mengalami kebocoran.

### 4.3 Cara Kerja `bcrypt.compare`

Fungsi `bcrypt.compare` digunakan untuk memeriksa apakah kata sandi yang dimasukkan pengguna cocok dengan hash yang tersimpan. Fungsi ini menggunakan informasi salt dan parameter yang terdapat dalam hash untuk melakukan verifikasi tanpa perlu menyimpan kata sandi asli.

### 4.4 Rainbow Table dan Fungsi Salt

Rainbow table merupakan kumpulan hasil perhitungan hash yang dapat digunakan untuk membantu menebak data asli. Salt yang unik membuat kata sandi yang sama menghasilkan hash berbeda, sehingga penggunaan rainbow table menjadi kurang efektif.

### 4.5 Pengaruh Cost Factor 10

Cost factor menentukan tingkat biaya komputasi yang diperlukan dalam proses hashing bcrypt. Pada pengujian ini, cost factor 10 digunakan untuk menentukan tingkat kerja hashing; semakin tinggi nilainya, semakin besar waktu dan sumber daya komputasi yang diperlukan.

## 5. Pentingnya Menjaga Kerahasiaan JWT_SECRET

`JWT_SECRET` merupakan kunci rahasia yang digunakan untuk menandatangani atau memverifikasi token JWT pada algoritma yang menggunakan secret bersama, seperti HS256. Jika kunci tersebut bocor, pihak lain berpotensi membuat token dengan signature yang valid. Oleh karena itu, kunci rahasia tidak boleh dimasukkan ke repository Git atau dibiarkan tersimpan dalam riwayat commit.

## 6. Pemeriksaan Keamanan Repository

### 6.1 Pemeriksaan File `.env`

Pemeriksaan dilakukan menggunakan perintah berikut:

```bash
git ls-files --error-unmatch backend/.env 2>/dev/null && echo "BAHAYA: .env terlacak" || echo "AMAN: .env tidak terlacak"
```

**Hasil pemeriksaan:**

```text
AMAN: .env tidak terlacak
```

Hasil tersebut menunjukkan bahwa Git tidak menemukan file `backend/.env` pada lokasi yang diperiksa sebagai file yang sedang dilacak. Karena struktur repository ini tidak memiliki folder `backend` pada direktori utama, pemeriksaan ini terbatas pada lokasi tersebut.

### 6.2 Pemeriksaan Token JWT

Pemeriksaan token JWT dilakukan menggunakan perintah berikut:

```bash
git grep -nE 'eyJ[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+' -- pertemuan-03 || echo "AMAN: tidak ada JWT yang cocok di pertemuan-03"
```

**Hasil pemeriksaan:**

```text
AMAN: tidak ada JWT yang cocok di pertemuan-03
```

Hasil tersebut menunjukkan bahwa tidak ditemukan teks yang cocok dengan pola token JWT pada folder `pertemuan-03`. Pemeriksaan ini terbatas pada folder dan pola yang digunakan serta tidak mencakup seluruh kemungkinan lokasi atau riwayat Git.

## 7. Analisis Hasil

Berdasarkan percobaan, dua proses hashing terhadap kata sandi yang sama menghasilkan nilai hash yang berbeda karena bcrypt menggunakan salt acak. Penggunaan salt membantu mengurangi efektivitas rainbow table, sedangkan cost factor menentukan besarnya biaya komputasi hashing.

Hashing berbeda dengan enkripsi karena hashing tidak dirancang untuk mengembalikan data asli melalui proses dekripsi. Dalam aplikasi, hash kata sandi dapat diverifikasi menggunakan `bcrypt.compare` tanpa harus menyimpan kata sandi asli.

Pemeriksaan repository menunjukkan bahwa file `backend/.env` tidak terlacak pada lokasi yang diperiksa dan tidak ditemukan teks yang cocok dengan pola token JWT pada folder `pertemuan-03`. Namun, hasil ini bukan jaminan bahwa seluruh file dan riwayat Git bebas dari informasi rahasia.

## 8. Kesimpulan

Hashing dan enkripsi memiliki fungsi yang berbeda. Hashing digunakan untuk menghasilkan representasi satu arah dari data, sedangkan enkripsi memungkinkan data asli dikembalikan melalui dekripsi dengan kunci yang sesuai. Bcrypt dapat digunakan untuk melindungi kata sandi dengan salt dan cost factor, serta memverifikasi kata sandi melalui `bcrypt.compare`.

Selain itu, `JWT_SECRET` harus dijaga kerahasiaannya agar tidak disalahgunakan untuk membuat token yang dianggap valid. Pemeriksaan keamanan repository merupakan langkah penting untuk mengurangi risiko kebocoran file konfigurasi dan token autentikasi.

