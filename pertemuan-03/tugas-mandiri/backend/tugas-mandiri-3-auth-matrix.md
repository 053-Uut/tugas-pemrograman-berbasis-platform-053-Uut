# TM3 — Matriks Hak Akses dan Role

## 1. Tujuan

Tugas ini bertujuan untuk memahami penerapan autentikasi (*authentication*) dan otorisasi (*authorization*) berdasarkan peran pengguna pada proyek **Sistem Repository Skripsi dan Pemetaan Peminatan Mahasiswa (Studi Kasus: Fakultas Teknik UNIRA)**. Melalui matriks hak akses, setiap pengguna hanya dapat mengakses fitur yang sesuai dengan tugas dan kewenangannya.

## 2. Pengertian Autentikasi dan Otorisasi

**Autentikasi** adalah proses untuk memverifikasi identitas pengguna yang ingin masuk ke dalam sistem. Pada sistem repository skripsi, proses ini dilakukan melalui halaman login dengan memasukkan kredensial akun yang sesuai. Setelah berhasil login, pengguna dapat memperoleh token JWT untuk digunakan ketika mengakses endpoint yang dilindungi.

**Otorisasi** adalah proses untuk menentukan apakah pengguna yang identitasnya sudah terverifikasi memiliki izin untuk mengakses fitur tertentu. Pada sistem repository skripsi dan pemetaan peminatan mahasiswa, hak akses dibedakan berdasarkan peran Kaprodi, Mahasiswa, dan Tendik.

## 3. Peran Pengguna

1. **Kaprodi:** bertugas memantau data repository skripsi dan informasi pemetaan peminatan mahasiswa sesuai kewenangannya.
2. **Mahasiswa:** bertugas melihat informasi repository skripsi dan pemetaan peminatan yang tersedia, serta mengunggah dokumen skripsi apabila fitur tersebut disediakan oleh sistem.
3. **Tendik:** bertugas membantu pengelolaan data administrasi mahasiswa, dokumen skripsi, dan informasi pendukung sesuai kewenangannya.

Matriks berikut merupakan rancangan hak akses awal. Nama endpoint dan kewenangan perlu disesuaikan dengan fitur serta implementasi API yang benar-benar digunakan oleh proyek kelompok.

## 4. Matriks Hak Akses

| Fitur | Kaprodi | Mahasiswa | Tendik | Contoh Endpoint |
|---|---|---|---|---|
| Melihat repository skripsi | ✅ | ✅ | ✅ | `GET /skripsi` |
| Melihat detail skripsi | ✅ | ✅ | ✅ | `GET /skripsi/:id` |
| Mengunggah skripsi | Sesuai kebijakan | Sesuai kebijakan | Sesuai kebijakan | `POST /skripsi` |
| Mengubah data skripsi | Sesuai kewenangan | ❌ | ✅ | `PUT /skripsi/:id` |
| Menghapus data skripsi | Sesuai kewenangan | ❌ | Sesuai kewenangan | `DELETE /skripsi/:id` |
| Melihat pemetaan peminatan | ✅ | Melihat data yang diizinkan | ✅ | `GET /peminatan` |
| Mengelola data peminatan | Sesuai kewenangan | ❌ | Sesuai kewenangan | `POST /peminatan` |
| Melihat data mahasiswa | ✅ | Data yang diizinkan | ✅ | `GET /mahasiswa` |
| Mengelola data administrasi mahasiswa | Sesuai kewenangan | ❌ | ✅ | `PUT /mahasiswa/:id` |

**Keterangan:**

- ✅ berarti peran diizinkan mengakses fitur berdasarkan rancangan.
- ❌ berarti peran tidak diizinkan mengakses fitur.
- *Sesuai kewenangan* berarti izin perlu ditetapkan berdasarkan kebijakan dan kebutuhan proyek kelompok.
- `:id` merupakan parameter yang mewakili ID data yang dipilih.

Matriks ini merupakan rancangan awal, bukan bukti bahwa semua endpoint tersebut sudah tersedia. Hak akses final harus mengikuti kesepakatan kelompok dan implementasi sistem.

## 5. Perbedaan HTTP 401 dan HTTP 403

HTTP `401 Unauthorized` digunakan ketika pengguna belum berhasil diautentikasi, misalnya saat mengakses `GET /skripsi` tanpa menyertakan token JWT atau menggunakan token yang tidak valid.

HTTP `403 Forbidden` digunakan ketika pengguna sudah terautentikasi dengan token yang valid, tetapi tidak memiliki hak akses terhadap fitur yang diminta. Contohnya, mahasiswa mencoba mengubah data administrasi mahasiswa melalui `PUT /mahasiswa/:id`, padahal fitur tersebut hanya diizinkan bagi petugas yang berwenang.

Dengan demikian, HTTP `401` berkaitan dengan kegagalan autentikasi, sedangkan HTTP `403` berkaitan dengan penolakan hak akses.

## 6. Risiko Jika Hanya Menggunakan `requireAuth`

Jika suatu endpoint hanya menggunakan middleware `requireAuth`, sistem hanya memeriksa apakah pengguna sudah terautentikasi tanpa memastikan bahwa pengguna memiliki peran yang sesuai. Akibatnya, mahasiswa yang sudah login berpotensi mencoba mengakses fitur pengelolaan data skripsi atau administrasi yang bukan kewenangannya.

Oleh karena itu, endpoint yang dilindungi perlu menerapkan pemeriksaan role, misalnya `requireRole('tendik')`, setelah autentikasi berhasil. Nama role dalam kode harus mengikuti nilai yang benar-benar digunakan oleh backend proyek kelompok.

## 7. Kesimpulan

Autentikasi dan otorisasi merupakan bagian penting dalam menjaga keamanan Sistem Repository Skripsi dan Pemetaan Peminatan Mahasiswa. Autentikasi memastikan identitas pengguna, sedangkan otorisasi membatasi tindakan berdasarkan peran Kaprodi, Mahasiswa, dan Tendik. Penerapan matriks hak akses, pemeriksaan token JWT, dan middleware pemeriksaan role dapat membantu mencegah akses yang tidak sesuai dengan kewenangan pengguna. Penerapan akhirnya perlu disesuaikan dengan fitur dan aturan akses yang disepakati dalam proyek kelompok.