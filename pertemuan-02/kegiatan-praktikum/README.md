# Praktikum 2 — HTTP Method dan Endpoint

## Identitas

| Keterangan | Detail |
|---|---|
| **Nama** | Sri Maulani |
| **NIM** | 2024520016 |
| **Program Studi** | Informatika |

---

## Deskripsi Kegiatan

Pada kegiatan praktikum ini dilakukan pengujian beberapa **HTTP method** menggunakan **Postman** dengan layanan publik **HTTPBin**.

Praktikum ini bertujuan untuk memahami bagaimana client mengirim **request** ke server melalui method dan endpoint tertentu, serta bagaimana server memberikan **response** berupa status code dan data JSON.

HTTP method yang digunakan:

- GET
- POST
- PUT
- PATCH
- DELETE

Base URL:

```text
https://httpbin.org
```

---

## Endpoint yang Diuji

| No | Method | Endpoint | Data |
|---:|:---:|:---|:---|
| 1 | GET | `/get` | Query parameter `nama`, `nim` |
| 2 | POST | `/post` | JSON `nama`, `nim`, `prodi` |
| 3 | PUT | `/put` | JSON `nama`, `nim`, `status` |
| 4 | PATCH | `/patch` | JSON `status`, `semester` |
| 5 | DELETE | `/delete` | Tidak ada body |

---

## Hasil Praktikum

Seluruh request yang diuji berhasil mendapatkan response dengan status **200 OK**.

### GET `/get`

URL yang digunakan:

```text
https://httpbin.org/get?nama=anik&nim=2024520016
```

Data yang dikirim:

```text
nama = anik
nim = 2024520016
```

Server mengembalikan query parameter pada bagian `args`:

```json
{
  "args": {
    "nama": "anik",
    "nim": "2024520016"
  }
}
```

Response juga berisi informasi header, origin, dan URL request.

### POST `/post`

URL:

```text
https://httpbin.org/post
```

Data yang dikirim:

```json
{
  "nama": "Anik",
  "nim": "2024520016",
  "prodi": "Informatika"
}
```

Data berhasil diterima server dan dikembalikan pada bagian `json` response.

### PUT `/put`

URL:

```text
https://httpbin.org/put
```

Data yang dikirim:

```json
{
  "nama": "Anik",
  "nim": "2024520016",
  "status": "Mahasiswa Aktif"
}
```

Server menerima request dan mengembalikan kembali data JSON yang dikirim.

### PATCH `/patch`

URL:

```text
https://httpbin.org/patch
```

Data yang dikirim:

```json
{
  "status": "Mahasiswa Aktif",
  "semester": 5
}
```

Server berhasil menerima data dan mengembalikannya pada response bagian `json`.

### DELETE `/delete`

URL:

```text
https://httpbin.org/delete
```

Pada request DELETE tidak terdapat data pada request body.

Response menunjukkan:

```json
{
  "data": "",
  "json": null
}
```

Request berhasil diproses oleh server dengan status **200 OK**.

---

## Dokumentasi Postman

### Screenshot GET

> Masukkan screenshot hasil request GET dari Postman di sini.

### Screenshot POST

> Masukkan screenshot hasil request POST dari Postman di sini.

---

## Kesimpulan

Dari kegiatan praktikum ini dapat dipahami bahwa setiap **HTTP method** memiliki penggunaan yang berbeda dalam komunikasi client dan server. GET menggunakan query parameter, sedangkan POST, PUT, dan PATCH dapat mengirim data melalui request body dalam format JSON. DELETE dapat digunakan tanpa request body.

Pengujian menggunakan Postman dan HTTPBin menunjukkan bahwa request berhasil diterima oleh server dan menghasilkan **response 200 OK**. Praktikum ini memberikan pemahaman dasar mengenai hubungan antara **method, endpoint, request, parameter, status code, dan response**.