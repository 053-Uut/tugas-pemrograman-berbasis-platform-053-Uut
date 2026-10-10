# TM3 — Matriks Hak Akses dan Role

## 1. Tujuan

Tugas ini bertujuan untuk memahami penerapan autentikasi (*authentication*) dan otorisasi (*authorization*) berdasarkan peran pengguna pada proyek Sistem Informasi Absensi Siswa. Melalui matriks hak akses, setiap pengguna hanya dapat mengakses fitur yang sesuai dengan tugas dan kewenangannya.

## 2. Pengertian Autentikasi dan Otorisasi

**Autentikasi** adalah proses untuk memverifikasi identitas pengguna yang ingin masuk ke dalam sistem. Pada Sistem Informasi Absensi Siswa, proses ini dilakukan melalui halaman login dengan memasukkan data akun yang sesuai. Setelah berhasil login, pengguna dapat memperoleh token JWT untuk digunakan ketika mengakses endpoint yang dilindungi.

**Otorisasi** adalah proses untuk menentukan apakah pengguna yang identitasnya sudah terverifikasi memiliki izin untuk mengakses fitur tertentu. Pada sistem absensi siswa, hak akses dibedakan berdasarkan peran admin, guru, dan kepala sekolah.

## 3. Peran Pengguna

1. **Admin:** bertugas mengelola data guru, data siswa, dan data kelas.
2. **Guru:** bertugas melihat data siswa serta mencatat dan mengelola absensi siswa.
3. **Kepala Sekolah:** bertugas melihat rekap dan laporan absensi siswa untuk memantau kehadiran.

Matriks berikut merupakan rancangan hak akses yang disesuaikan dengan kebutuhan sistem. Endpoint perlu disesuaikan kembali jika implementasi proyek menggunakan nama route yang berbeda.

## 4. Matriks Hak Akses

| Fitur | Admin | Guru | Kepala Sekolah | Endpoint |
|---|---|---|---|---|
| Melihat data siswa | ✅ | ✅ | ✅ | `GET /siswa` |
| Menambah data siswa | ✅ | ❌ | ❌ | `POST /siswa` |
| Mengubah data siswa | ✅ | ❌ | ❌ | `PUT /siswa/:id` |
| Melihat data kelas | ✅ | ✅ | ✅ | `GET /kelas` |
| Mencatat absensi siswa | ✅ | ✅ | ❌ | `POST /absensi` |
| Melihat data absensi | ✅ | ✅ | ✅ | `GET /absensi` |
| Mengubah data absensi | ✅ | ✅ | ❌ | `PUT /absensi/:id` |
| Melihat rekap absensi | ✅ | ❌ | ✅ | `GET /absensi/rekap` |

Keterangan:

- ✅ berarti peran tersebut diizinkan mengakses fitur.
- ❌ berarti peran tersebut tidak diizinkan mengakses fitur dan harus ditolak dengan HTTP `403` apabila identitasnya sudah terverifikasi.
- `:id` merupakan parameter yang mewakili ID data yang dipilih.

Pembagian hak akses di atas merupakan rancangan. Hak akses final harus mengikuti aturan yang disepakati dalam proyek kelompok.

## 5. Perbedaan HTTP 401 dan HTTP 403

HTTP `401 Unauthorized` digunakan ketika pengguna belum berhasil diautentikasi, misalnya saat mengakses `GET /siswa` tanpa menyertakan token JWT atau menggunakan token yang tidak valid.

HTTP `403 Forbidden` digunakan ketika pengguna sudah terautentikasi dengan token yang valid, tetapi tidak mempunyai hak akses terhadap fitur yang diminta. Contohnya, guru mencoba menambah data siswa melalui `POST /siswa`, padahal fitur tersebut hanya diperuntukkan bagi admin.

Dengan demikian, HTTP `401` berkaitan dengan kegagalan autentikasi, sedangkan HTTP `403` berkaitan dengan penolakan hak akses.

## 6. Risiko Jika Hanya Menggunakan `requireAuth`

Jika endpoint `POST /siswa` hanya menggunakan middleware `requireAuth`, sistem hanya memeriksa apakah pengguna sudah terautentikasi, tanpa memastikan bahwa pengguna memiliki peran admin. Akibatnya, guru atau kepala sekolah yang sudah login berpotensi menambah data siswa meskipun tidak memiliki izin. Oleh karena itu, endpoint tersebut perlu menggunakan pemeriksaan role, misalnya `requireRole('admin')`, setelah autentikasi berhasil.

## 7. Kesimpulan

Autentikasi dan otorisasi merupakan bagian penting dalam menjaga keamanan Sistem Informasi Absensi Siswa. Autentikasi memastikan identitas pengguna, sedangkan otorisasi membatasi tindakan berdasarkan peran pengguna. Penerapan matriks hak akses, pemeriksaan token JWT, dan middleware pemeriksaan role membantu mencegah akses yang tidak sesuai dengan kewenangan pengguna.