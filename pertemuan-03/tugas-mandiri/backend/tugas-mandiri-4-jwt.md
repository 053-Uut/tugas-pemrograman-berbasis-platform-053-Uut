# TUGAS MANDIRI 4 — JSON WEB TOKEN (JWT)

**Nama:** Barrotut Taqiyah  
**NIM:** 2024520053  
**Program Studi:** Informatika  
**Mata Kuliah:** Pemrograman Berbasis Platform

## 1. Tujuan

Tujuan tugas ini adalah memahami struktur JSON Web Token (JWT), mengenali fungsi header, payload, dan signature, serta menguji bagaimana perubahan payload memengaruhi proses verifikasi signature.

## 2. Alat yang Digunakan

1. Website [jwt.io](https://jwt.io/) untuk membaca dan menguji token JWT.
2. Browser Google Chrome untuk menjalankan pengujian.
3. Token JWT latihan untuk mengamati struktur dan proses verifikasi token.

## 3. Data Pengujian

Data payload yang digunakan sebagai contoh dalam pengujian adalah sebagai berikut:

```json
{
  "sub": "2024520053",
  "name": "Barrotut Taqiyah",
  "role": "mahasiswa"
}
```

Keterangan:

- `sub`: identitas subjek atau pengguna dalam token, yaitu NIM mahasiswa.
- `name`: nama pengguna yang tercantum dalam token.
- `role`: peran pengguna, yaitu mahasiswa.

## 4. Struktur JWT

JSON Web Token (JWT) terdiri dari tiga bagian yang dipisahkan oleh tanda titik (`.`), yaitu:

1. **Header**, berisi informasi tentang tipe token dan algoritma yang digunakan untuk menghasilkan signature.
2. **Payload**, berisi data atau claims pengguna, seperti NIM, nama, dan peran pengguna.
3. **Signature**, digunakan untuk memverifikasi integritas token dan mendeteksi perubahan pada bagian yang ditandatangani.

Payload JWT dapat dibaca tanpa secret key karena isinya hanya di-*encode*, bukan otomatis dienkripsi. Oleh karena itu, informasi rahasia seperti kata sandi tidak boleh disimpan di dalam payload.

## 5. Langkah-Langkah Pengujian

### 5.1 Pengujian Token Asli

Langkah-langkah pengujian:

1. Membuka website [jwt.io](https://jwt.io/).
2. Memasukkan token JWT latihan ke bagian **Encoded**, jika token sudah tersedia.
3. Memeriksa bagian header dan payload pada tampilan **Decoded**.
4. Memastikan data payload sesuai dengan data yang digunakan untuk membuat token.
5. Memeriksa hasil verifikasi signature menggunakan secret yang sesuai, jika tersedia.

**Hasil pengujian:** Bagian ini diisi berdasarkan hasil yang benar-benar muncul pada jwt.io. Jika token asli berhasil diverifikasi, catat hasil verifikasi yang ditampilkan.

**Bukti screenshot:** `tm4-token-asli-200.png`

### 5.2 Pengujian Payload jwt
Langkah-langkah pengujian:

1. Mengubah nilai `role` dari `mahasiswa` menjadi `admin` pada token latihan.
2. Mempertahankan signature asli tanpa melakukan penandatanganan ulang.
3. Memeriksa kembali token dan payload hasil perubahan.
4. Mengamati hasil verifikasi signature yang ditampilkan oleh jwt.io.

**Hasil pengujian:** Jika payload diubah tanpa menghasilkan signature yang sesuai, verifikasi signature seharusnya gagal. Catat pesan yang benar-benar ditampilkan oleh jwt.io.

**Bukti screenshot:** `tm4-jwt-payload.png`

### 5.3 Pengujian Token yang Diubah

Pada tahap ini, token JWT yang telah diubah diuji untuk mengetahui apakah server dapat mendeteksi perubahan data pada token. Nilai `role` diubah dari `mahasiswa` menjadi `admin` tanpa menghasilkan signature baru yang valid. Token kemudian dikirim ke endpoint autentikasi untuk melihat respons dari server.

**Hasil pengujian:** Server memberikan respons HTTP 401 yang menunjukkan bahwa token ditolak karena tidak lolos proses autentikasi.

**Bukti screenshot:** `tm4-jwt-token-diubah-401.png`

## 6. Analisis Hasil

JWT memiliki tiga bagian utama, yaitu header, payload, dan signature. Payload dapat dibaca karena data di dalamnya di-*encode*, tetapi perubahan pada payload akan memengaruhi hasil perhitungan signature.

Jika nilai `role` diubah dari `mahasiswa` menjadi `admin` tanpa menghasilkan signature baru yang valid, signature lama tidak lagi sesuai dengan isi token. Akibatnya, proses verifikasi signature seharusnya gagal.

Pengujian ini menunjukkan bahwa perubahan data pada token dapat dideteksi melalui verifikasi signature. Namun, hasil pengujian di jwt.io perlu dibedakan dari pengujian autentikasi pada server, karena keberhasilan verifikasi signature di jwt.io saja tidak membuktikan bahwa server menerima atau menolak token tersebut.

## 7. Kesimpulan

JSON Web Token (JWT) merupakan format token yang terdiri dari header, payload, dan signature. Header menjelaskan tipe token dan algoritma yang digunakan, payload menyimpan claims pengguna, sedangkan signature berfungsi untuk memverifikasi integritas token.

Melalui pengujian perubahan nilai `role` dari `mahasiswa` menjadi `admin` tanpa membuat signature baru yang valid, dapat dipahami bahwa perubahan payload memengaruhi kecocokan signature. Dengan demikian, token harus diverifikasi dengan benar sebelum digunakan untuk memberikan akses kepada pengguna.

## 8. Dokumentasi

Screenshot hasil pengujian disimpan dengan nama berikut:

1. `tm4-jwt-token-asli-200.png`
2. `tm4-jwt-payload.png`
3. `tm4-jwt-token-diubah-401.png`
