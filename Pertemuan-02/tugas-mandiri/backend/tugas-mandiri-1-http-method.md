# Tugas Mandiri 1 — Mengenal HTTP Method dan Endpoint

## 1. Tujuan

Tugas ini bertujuan untuk memahami penggunaan HTTP method dan endpoint dalam komunikasi antara client dan server. Pengujian dilakukan menggunakan **Postman** dengan layanan publik **HTTPBin**.

HTTP method yang diuji meliputi:

* GET
* POST
* PUT
* PATCH
* DELETE

Base URL yang digunakan:

```text
https://httpbin.org
```

---

## 2. Hasil Pengujian

| No | Method | Endpoint  | Data yang Dikirim                            | Status | Hasil                                                                                    |
| -: | :----- | :-------- | :------------------------------------------- | :----: | :--------------------------------------------------------------------------------------- |
|  1 | GET    | `/get`    | Query parameter `nama=Uut`, `nim=2024520053` | 200 OK | Server mengembalikan query parameter, header, origin, dan URL request dalam format JSON. |
|  2 | POST   | `/post`   | JSON `nama`, `nim`, `prodi`                  | 200 OK | Server menerima dan mengembalikan data JSON yang dikirim melalui request body.           |
|  3 | PUT    | `/put`    | JSON `nama`, `nim`, `prodi`                  | 200 OK | Server menerima dan mengembalikan data JSON yang dikirim melalui request body.           |
|  4 | PATCH  | `/patch`  | JSON `status`, `semester`                    | 200 OK | Server menerima dan mengembalikan data JSON yang dikirim melalui request body.           |
|  5 | DELETE | `/delete` | Tidak ada data/body                          | 200 OK | Server menerima request DELETE dan mengembalikan informasi request tanpa data JSON/body. |

---

## 3. Detail Pengujian

### 3.1 GET `/get`

**Method:**

```text
GET
```

**URL:**

```text
https://httpbin.org/get?nama=Uut&nim=2024520053
```

**Tujuan endpoint:**

Endpoint `/get` digunakan untuk menguji request GET dan melihat bagaimana server menerima parameter yang dikirim melalui URL.

**Data yang dikirim:**

```text
nama = Uut
nim = 2024520053
```

Data dikirim sebagai **query parameter**, bukan melalui request body.

**Status code:**

```text
200 OK
```

**Response body:**

```json
{
  "args": {
    "nama": "Uut",
    "nim": "2024520053"
  },
  "headers": {
    "Host": "httpbin.org"
  },
  "origin": "182.8.68.12",
  "url": "https://httpbin.org/get?nama=Uut&nim=2024520053"
}
```

*Catatan: response di atas merupakan cuplikan informasi penting. Nilai header dapat berbeda sesuai request yang dikirim.*

**Informasi yang dikembalikan server:**

Server mengembalikan query parameter pada bagian `args`, informasi header request pada bagian `headers`, alamat asal request pada `origin`, serta URL yang digunakan pada bagian `url`.

**Kesimpulan:**

GET digunakan untuk mengambil informasi dari server. Pada pengujian ini, parameter `nama` dan `nim` berhasil diterima serta ditampilkan kembali dalam response JSON.

**Screenshot**
![Hasil pengujian GET](kegiatan%20praktikum/tm1-fungsi-get.png)
---

### 3.2 POST `/post`

**Method:**

```text
POST
```

**URL:**

```text
https://httpbin.org/post
```

**Tujuan endpoint:**

Endpoint `/post` digunakan untuk menguji pengiriman data melalui request body menggunakan method POST.

**Data yang dikirim:**

```json
{
  "nama": "Uut",
  "nim": "2024520053",
  "prodi": "Informatika"
}
```

Data dikirim melalui **request body** dengan format JSON.

**Status code:**

```text
200 OK
```

**Response body:**

```json
{
  "json": {
    "nama": "Uut",
    "nim": "2024520053",
    "prodi": "Informatika"
  },
  "url": "https://httpbin.org/post"
}
```

*Catatan: response di atas merupakan cuplikan data penting dari response asli.*

**Informasi yang dikembalikan server:**

Server mengembalikan data yang dikirim pada bagian `json`. Response juga berisi informasi request, seperti `headers`, `origin`, dan `url`. Header `Content-Type: application/json` menunjukkan bahwa data dikirim dalam format JSON.

**Kesimpulan:**

POST digunakan untuk mengirim data ke server. Pada pengujian ini, data nama, NIM, dan program studi berhasil diterima dan ditampilkan kembali oleh HTTPBin.

---

### 3.3 PUT `/put`

**Method:**

```text
PUT
```

**URL:**

```text
https://httpbin.org/put
```

**Tujuan endpoint:**

Endpoint `/put` digunakan untuk menguji pengiriman data menggunakan method PUT yang umumnya digunakan untuk mengganti atau memperbarui representasi suatu sumber daya.

**Data yang dikirim:**

```json
{
  "nama": "Uut",
  "nim": "2024520053",
  "prodi": "Mahasiswa Aktif"
}
```

Data dikirim melalui request body dalam format JSON.

**Status code:**

```text
200 OK
```

**Response body:**

```json
{
  "json": {
    "nama": "Uut",
    "nim": "2024520053",
    "prodi": "Mahasiswa Aktif"
  },
  "url": "https://httpbin.org/put"
}
```

*Catatan: response di atas merupakan cuplikan data penting dari response asli.*

**Informasi yang dikembalikan server:**

Server mengembalikan data JSON yang dikirim melalui request body. Response juga memuat informasi header, origin, dan URL request.

**Kesimpulan:**

PUT umumnya digunakan untuk mengganti atau memperbarui data suatu sumber daya. Dalam pengujian ini, HTTPBin menerima request dan mengembalikan data yang dikirim. Pengujian ini tidak memperbarui data mahasiswa sungguhan karena HTTPBin hanya digunakan untuk menguji request dan response.

**Screenshot**
![Hasil pengujian PUT](kegiatan%20praktikum/tm1-fungsi-put.png)
---

### 3.4 PATCH `/patch`

**Method:**

```text
PATCH
```

**URL:**

```text
https://httpbin.org/patch
```

**Tujuan endpoint:**

Endpoint `/patch` digunakan untuk menguji pengiriman data menggunakan method PATCH yang umumnya digunakan untuk memperbarui sebagian data suatu sumber daya.

**Data yang dikirim:**

```json
{
  "status": "Mahasiswa Aktif",
  "semester": 5
}
```

Data dikirim melalui request body dengan format JSON.

**Status code:**

```text
200 OK
```

**Response body:**

```json
{
  "json": {
    "semester": 5,
    "status": "Mahasiswa Aktif"
  },
  "url": "https://httpbin.org/patch"
}
```

*Catatan: urutan properti pada JSON response dapat berbeda, tetapi isi datanya tetap sama.*

**Informasi yang dikembalikan server:**

Server mengembalikan data `status` dan `semester` pada bagian `json`. Response juga berisi informasi request lainnya, seperti `headers`, `origin`, dan `url`.

**Kesimpulan:**

PATCH umumnya digunakan untuk memperbarui sebagian data. Pada pengujian ini, data status mahasiswa dan semester berhasil diterima serta ditampilkan kembali oleh HTTPBin.

---

### 3.5 DELETE `/delete`

**Method:**

```text
DELETE
```

**URL:**

```text
https://httpbin.org/delete
```

**Tujuan endpoint:**

Endpoint `/delete` digunakan untuk menguji request DELETE yang umumnya digunakan untuk meminta penghapusan suatu sumber daya.

**Data yang dikirim:**

Tidak ada request body.

**Status code:**

```text
200 OK
```

**Response body:**

```json
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "json": null,
  "url": "https://httpbin.org/delete"
}
```

*Catatan: response di atas merupakan cuplikan informasi penting dari response asli.*

**Informasi yang dikembalikan server:**

Server mengembalikan informasi request. Bagian `data` berisi string kosong dan bagian `json` bernilai `null` karena tidak ada data JSON yang dikirim melalui request body. Informasi lain, seperti `headers`, `origin`, dan `url`, juga dikembalikan oleh server.

**Kesimpulan:**

DELETE digunakan untuk meminta penghapusan suatu sumber daya. Pada pengujian ini, HTTPBin berhasil menerima request DELETE dan mengembalikan informasi request. Pengujian ini tidak menghapus data mahasiswa atau data sungguhan karena HTTPBin hanya berfungsi sebagai layanan pengujian HTTP.

---

## 4. Kesimpulan

Berdasarkan pengujian menggunakan Postman dan HTTPBin, kelima HTTP method, yaitu GET, POST, PUT, PATCH, dan DELETE, berhasil menghasilkan response dengan status **200 OK**.

GET digunakan untuk mengirim request dengan query parameter, sedangkan POST, PUT, dan PATCH digunakan untuk mengirim data melalui request body dalam format JSON. PUT umumnya digunakan untuk mengganti atau memperbarui representasi sumber daya, sedangkan PATCH digunakan untuk memperbarui sebagian data. DELETE digunakan untuk meminta penghapusan suatu sumber daya dan pada pengujian ini dikirim tanpa request body.

Hasil pengujian menunjukkan bahwa server mengembalikan informasi mengenai parameter, data JSON, header, origin, dan URL sesuai jenis request yang dikirim. Melalui tugas ini, hubungan antara HTTP method, endpoint, parameter, request, response body, dan status code dapat dipahami dengan lebih baik.
