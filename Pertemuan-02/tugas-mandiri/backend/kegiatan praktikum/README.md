# Kegiatan Praktikum — Tugas Mandiri 3

Folder ini berisi dokumentasi hasil pengujian **HTTP Request dan Response** menggunakan **Postman** dengan layanan **HTTPBin**.

## Pengujian yang Dilakukan

Pada Tugas Mandiri 3 dilakukan pengujian terhadap dua endpoint HTTPBin, yaitu:

1. `GET /get`
2. `GET /headers`

---

## 1. Pengujian GET /get

Endpoint yang digunakan:

```text
GET https://httpbin.org/get
```

Pengujian menggunakan query parameter:

| Key | Value |
|---|---|
| `nama` | `Uut` |
| `kelas` | `PBP` |

Request yang dikirim:

```text
GET https://httpbin.org/get?nama=Uut&kelas=PBP
```

Hasil pengujian menunjukkan bahwa server berhasil menerima query parameter dan menampilkannya pada bagian `args` dalam response.

### Screenshot

![Hasil pengujian GET /get](tm3-get.png)

**Gambar 1. Pengujian GET /get dengan query parameter nama dan kelas.**

---

## 2. Pengujian GET /headers

Endpoint yang digunakan:

```text
GET https://httpbin.org/headers
```

Pengujian ini tidak menggunakan query parameter maupun request body.

Hasil pengujian menunjukkan bahwa server menampilkan HTTP header yang diterima dari client, seperti:

- `Accept`
- `Accept-Encoding`
- `Host`
- `User-Agent`

Header `User-Agent` menunjukkan bahwa request dikirim menggunakan Postman.

### Screenshot

![Hasil pengujian GET /headers](tm3-headers.png)

**Gambar 2. Pengujian GET /headers untuk melihat HTTP header.**

---

## Kesimpulan

Berdasarkan kegiatan praktikum, endpoint `/get` dapat digunakan untuk melihat query parameter yang dikirim melalui URL. Sementara itu, endpoint `/headers` dapat digunakan untuk melihat HTTP header yang diterima oleh server.

Pengujian ini membantu memahami bagaimana **request** dikirim dari client menggunakan Postman dan bagaimana **response** diberikan kembali oleh server HTTPBin.