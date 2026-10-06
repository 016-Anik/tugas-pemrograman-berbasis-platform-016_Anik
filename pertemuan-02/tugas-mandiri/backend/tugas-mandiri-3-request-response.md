# Tugas Mandiri 3 — Memahami Request dan Response

## 1. Tujuan

Tugas ini bertujuan untuk memahami konsep **request** dan **response** dalam komunikasi antara client dan server menggunakan protokol HTTP. Pengujian dilakukan menggunakan **Postman** dengan layanan publik **HTTPBin**.

Pada pengujian ini digunakan dua endpoint:

```text
GET https://httpbin.org/get

dan

GET https://httpbin.org/headers
```

Endpoint `/get` digunakan untuk melihat informasi request yang dikirim, termasuk query parameter. Sedangkan endpoint `/headers` digunakan untuk melihat HTTP header yang diterima oleh server.

---

## 2. Hasil Pengujian

| Endpoint | Method | Parameter | Hasil |
|---|---|---|---|
| `/get` | GET | `nama=Anik`, `kelas=PBP` | Server mengembalikan query parameter pada bagian `args` serta informasi header request. |
| `/headers` | GET | Tidak ada | Server menampilkan HTTP header yang diterima dari client. |

---

## 3. Detail Pengujian

### 3.1 Pengujian GET `/get`

**Request:**

```text
GET https://httpbin.org/get
```

**Query Parameter:**

| Key | Value |
|---|---|
| nama | Anik |
| kelas | PBP |

Sehingga request yang dikirim menjadi:

```text
GET https://httpbin.org/get?nama=Anik&kelas=PBP
```

Data tersebut dikirim sebagai **query parameter**, bukan melalui request body.

**Status:**

```text
200 OK
```

**Hasil Response:**

Server mengembalikan informasi request dalam format JSON. Pada bagian `args`, query parameter yang dikirim dapat dilihat sebagai berikut:

```json
{
  "args": {
    "kelas": "PBP",
    "nama": "Anik"
  },
  "headers": {
    "Accept": "*/*",
    "Accept-Encoding": "gzip, deflate, br",
    "Host": "httpbin.org",
    "Postman-Token": "...",
    "User-Agent": "PostmanRuntime/2.10.1",
    "X-Amzn-Trace-Id": "..."
  }
}
```

**Hasil Pengamatan:**

Berdasarkan hasil pengujian, query parameter `nama` dan `kelas` yang dikirim melalui URL berhasil diterima oleh server. Data tersebut ditampilkan pada bagian `args` pada response.

Pada response juga terdapat informasi `headers`. Beberapa header yang terlihat adalah `Accept`, `Accept-Encoding`, `Host`, `Postman-Token`, `User-Agent`, dan `X-Amzn-Trace-Id`.

Hal ini menunjukkan bahwa HTTPBin dapat menampilkan informasi request yang diterima oleh server.

---

### 3.2 Pengujian GET `/headers`

**Request:**

```text
GET https://httpbin.org/headers
```

Request ini tidak menggunakan query parameter maupun request body.

**Status:**

```text
200 OK
```

**Hasil Response:**

Server menampilkan HTTP header yang diterima dari client:

```json
{
  "headers": {
    "Accept": "*/*",
    "Accept-Encoding": "gzip, deflate, br",
    "Host": "httpbin.org",
    "Postman-Token": "...",
    "User-Agent": "PostmanRuntime/2.10.1",
    "X-Amzn-Trace-Id": "..."
  }
}
```

**Hasil Pengamatan:**

Berdasarkan hasil pengujian, server menampilkan beberapa HTTP header yang diterima dari client. Beberapa header yang terlihat adalah `Accept`, `Accept-Encoding`, `Host`, `Postman-Token`, `User-Agent`, dan `X-Amzn-Trace-Id`.

Header `User-Agent` menunjukkan bahwa request dikirim menggunakan Postman dengan:

```text
PostmanRuntime/2.10.1
```

---

## 4. Alur Request dan Response

Proses komunikasi antara client dan server dapat digambarkan sebagai berikut:

```text
Client / Postman
       |
       | HTTP Request
       | Method + URL + Header + Body
       v
     Server
    (HTTPBin)
       |
       | HTTP Response
       | Status Code + Header + Body
       v
Client / Postman
```

Pada pengujian ini, Postman bertindak sebagai client yang mengirimkan request kepada server HTTPBin. Server kemudian memproses request dan memberikan response kembali kepada Postman.

---

## 5. Jawaban Pertanyaan

### 1. Apa yang dimaksud request?

Request adalah permintaan yang dikirimkan oleh client kepada server untuk meminta data atau melakukan suatu proses. Request HTTP dapat terdiri dari method, URL, query parameter, HTTP header, dan request body.

Pada pengujian ini, Postman bertindak sebagai client yang mengirimkan request dengan method GET kepada server HTTPBin.

### 2. Apa yang dimaksud response?

Response adalah balasan yang diberikan oleh server setelah menerima dan memproses request dari client. Response dapat berisi status code, HTTP header, dan response body.

Pada pengujian ini, HTTPBin memberikan response dengan status `200 OK` yang berisi informasi mengenai request yang telah diterima oleh server.

### 3. Apa fungsi query parameter?

Query parameter berfungsi untuk mengirimkan data atau informasi tambahan melalui URL. Query parameter ditulis setelah tanda `?` dan apabila terdapat lebih dari satu parameter, setiap parameter dipisahkan menggunakan tanda `&`.

Contohnya:

```text
https://httpbin.org/get?nama=Anik&kelas=PBP
```

Pada contoh tersebut terdapat dua query parameter:

```text
nama = Anik
kelas = PBP
```

HTTPBin kemudian menampilkan data tersebut pada bagian `args` dalam response.

### 4. Apa fungsi HTTP header?

HTTP header berfungsi untuk membawa informasi tambahan dalam komunikasi antara client dan server. Header dapat memberikan informasi mengenai jenis data yang diterima, jenis client yang digunakan, host tujuan, dan informasi lainnya.

Pada pengujian `/headers`, HTTPBin menampilkan beberapa header yang dikirim oleh Postman, seperti:

```text
Accept
Accept-Encoding
Host
Postman-Token
User-Agent
X-Amzn-Trace-Id
```

### 5. Apa perbedaan data pada URL dengan data pada request body?

Data pada URL biasanya dikirim menggunakan query parameter dan dapat terlihat langsung pada URL.

Contohnya:

```text
GET https://httpbin.org/get?nama=Anik&kelas=PBP
```

Sedangkan data pada request body dikirim pada bagian isi request dan tidak ditampilkan sebagai bagian dari URL. Request body biasanya digunakan pada method seperti POST, PUT, dan PATCH.

Contoh data pada request body:

```json
{
  "nama": "Anik",
  "nim": "2024520016"
}
```

Jadi, perbedaannya adalah data pada URL dikirim melalui query parameter, sedangkan data pada request body dikirim melalui isi request.

---

## 6. Screenshot Pengujian

### Screenshot GET `/get`

Masukkan screenshot hasil pengujian:

```text
GET https://httpbin.org/get?nama=Anik&kelas=PBP
```

Screenshot menunjukkan query parameter:

```text
nama = Anik
kelas = PBP
```

Response menghasilkan status:

```text
200 OK
```

Gambar 1. Pengujian GET `/get` dengan query parameter.

### Screenshot GET `/headers`

Masukkan screenshot hasil pengujian:

```text
GET https://httpbin.org/headers
```

Response menghasilkan status:

```text
200 OK
```

Screenshot menunjukkan HTTP header yang diterima oleh server HTTPBin.

Gambar 2. Pengujian GET `/headers` untuk melihat HTTP header.

---

## 7. Kesimpulan

Berdasarkan pengujian yang telah dilakukan menggunakan Postman dan HTTPBin, dapat dipahami bahwa request merupakan permintaan yang dikirim oleh client kepada server, sedangkan response merupakan balasan yang diberikan oleh server kepada client.

Pengujian endpoint `/get` menunjukkan bahwa query parameter dapat digunakan untuk mengirimkan data melalui URL dan data tersebut dapat diterima serta ditampilkan oleh server pada bagian `args`. Pada pengujian ini, query parameter yang digunakan adalah `nama=Anik` dan `kelas=PBP`.

Sementara itu, pengujian endpoint `/headers` menunjukkan informasi HTTP header yang diterima oleh server dari client. Beberapa informasi yang ditampilkan antara lain `Accept`, `Accept-Encoding`, `Host`, `Postman-Token`, `User-Agent`, dan `X-Amzn-Trace-Id`.

Dengan demikian, request dan response merupakan bagian penting dalam komunikasi antara client dan server pada aplikasi berbasis HTTP. Pemahaman terhadap query parameter, HTTP header, URL, dan request body juga diperlukan dalam pengembangan aplikasi web dan API.