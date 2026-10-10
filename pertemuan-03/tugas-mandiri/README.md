# Tugas Mandiri Pertemuan 03

## Tujuan

Tugas mandiri ini bertujuan untuk memahami perbedaan penggunaan component CSS dan utility classes, membuat layout web responsif menggunakan Tailwind CSS, memahami autentikasi dan otorisasi JWT, serta mempelajari hash password menggunakan bcrypt.

## Daftar Tugas

1. TM1 — Perbandingan Component CSS dan Utility Classes
2. TM2 — Layout Responsif dengan Tailwind CSS
3. TM3 — Matriks Hak Akses dan Role
4. TM4 — Analisis JWT
5. TM5 — Analisis Hash Password dengan bcrypt

---

## TM1 — Perbandingan Component CSS dan Utility Classes

### Tujuan

Membandingkan pembuatan kartu profil mahasiswa menggunakan component CSS dan utility classes Tailwind CSS.

### File Pengerjaan

- `frontend/web/tugas-mandiri-1-component.html`
- `frontend/web/tugas-mandiri-1-utility.html`
- `frontend/web/tugas-mandiri-1-css-compare.md`

### Hasil

Berhasil membuat dua versi kartu profil mahasiswa yang berisi foto, nama lengkap, NIM, dan tombol "Lihat Profil". Versi pertama menggunakan CSS di dalam tag `<style>`, sedangkan versi kedua menggunakan utility classes Tailwind CSS.

Kedua versi diuji pada tampilan laptop dan layar berukuran 360 piksel.

### Bukti Pengerjaan

Screenshot disimpan di folder `frontend/web/screenshots/`.

- `tm1-component-laptop.png`
- `tm1-component-360.png`
- `tm1-utility-laptop.png`
- `tm1-utility-360.png`

Hasil perbandingan implementasi dijelaskan lebih lanjut dalam file laporan TM1.

---

## TM2 — Layout Responsif dengan Tailwind CSS

### Tujuan

Membuat halaman web responsif menggunakan Tailwind CSS dengan menerapkan Flexbox, Grid, breakpoint, utility classes, dan efek hover.

### File Pengerjaan

- `frontend/web/tugas-mandiri-2-layout.html`
- `frontend/web/tugas-mandiri-2-layout.md`

### Hasil

Berhasil membuat halaman KampusKu yang terdiri dari navbar, hero, tiga kartu layanan mahasiswa, bagian tentang, dan footer.

Layout kartu menggunakan satu kolom pada layar kecil, dua kolom pada breakpoint `md`, dan tiga kolom pada breakpoint `lg`. Halaman diuji pada tampilan laptop dan layar berukuran 360 piksel.

### Bukti Pengerjaan

Screenshot disimpan di folder `frontend/web/screenshots/`.

- `tm2-layout-laptop.png`
- `tm2-layout-360.png`
- `tm2-layout-360-bawah.png`

---

## TM3 — Matriks Hak Akses dan Role

- **Topik:** Authentication dan Authorization.
- **Proyek:** Sistem Repository Skripsi dan Pemetaan Peminatan Mahasiswa (Studi Kasus: Fakultas Teknik UNIRA).
- **File laporan:** `backend/tugas-mandiri-3-auth-matrix.md`
- **Isi pengerjaan:**
  - Menentukan tiga peran pengguna, yaitu Kaprodi, Mahasiswa, dan Tendik.
  - Menyusun matriks hak akses berdasarkan peran pengguna.
  - Merancang endpoint untuk fitur repository skripsi dan pemetaan peminatan mahasiswa.
  - Menjelaskan perbedaan HTTP `401` dan `403`.
  - Menganalisis risiko endpoint yang hanya menggunakan `requireAuth` tanpa pemeriksaan role.
- **Status:** Selesai.

---

## TM4 — Analisis JWT

**Status:** Belum dikerjakan.

File yang akan dibuat:

- `backend/tugas-mandiri-4-jwt.md`

---

## TM5 — Analisis Hash Password dengan bcrypt

**Status:** Belum dikerjakan.

File yang akan dibuat:

- `backend/tugas-mandiri-5-hash.md`

---

## Struktur Folder

```text
tugas-mandiri/
├── README.md
├── backend/
│   ├── tugas-mandiri-3-auth-matrix.md
│   ├── tugas-mandiri-4-jwt.md
│   └── tugas-mandiri-5-hash.md
└── frontend/
    └── web/
        ├── screenshots/
        ├── foto-barrotut.jpg
        ├── tugas-mandiri-1-component.html
        ├── tugas-mandiri-1-utility.html
        ├── tugas-mandiri-1-css-compare.md
        ├── tugas-mandiri-2-layout.html
        └── tugas-mandiri-2-layout.md
```

**Catatan:** Folder `screenshots/` berada di dalam `frontend/web/`, sesuai struktur repository. TM4 dan TM5 belum memiliki hasil pengerjaan karena masih belum dikerjakan.