# Kegiatan Praktikum Pertemuan 02

## Judul

Pengujian HTTP Method, HTTP Status Code, serta Request & Response menggunakan Postman dan HTTPBin

## Tujuan

Melakukan pengujian HTTP Method, HTTP Status Code, serta Request & Response (termasuk Headers) menggunakan Postman untuk memahami proses komunikasi HTTP antara client dan server.

Pengujian dilakukan menggunakan HTTPBin sebagai layanan untuk melihat data request yang dikirim oleh client serta memahami status code dan response yang diberikan oleh server.

## Cara Menjalankan

Pengujian dilakukan menggunakan aplikasi Postman dengan langkah-langkah berikut:

1. Membuka aplikasi Postman.
2. Membuat request HTTP sesuai dengan pengujian yang dilakukan.
3. Memasukkan URL HTTPBin.
4. Mengatur method, headers, dan parameter sesuai kebutuhan pengujian.
5. Mengirim request menggunakan tombol **Send**.
6. Mengamati status code dan response yang diberikan oleh server.
7. Menyimpan screenshot hasil pengujian sebagai bukti pengerjaan.

## Hasil

### 1. Pengujian GET

Request GET berhasil dikirim ke HTTPBin dan menghasilkan response dari server.

**Bukti hasil pengujian GET:**

[![Hasil Pengujian GET](./tm1-fungsi-get.png)](./tm1-fungsi-get.png)

### 2. Pengujian PUT

Request PUT berhasil dikirim ke HTTPBin dan menghasilkan response dari server.

**Bukti hasil pengujian PUT:**

[![Hasil Pengujian PUT](./tm1-fungsi-put.png)](./tm1-fungsi-put.png)

### 3. Pengujian HTTP Status Code

Pengujian HTTP Status Code dilakukan menggunakan endpoint:

`https://httpbin.org/status/:code`

Method yang digunakan adalah **GET**.

Pengujian dilakukan dengan beberapa status code untuk melihat response yang diberikan oleh server.

#### Status Code 200

[![Hasil Pengujian Status Code 200](./tm2-200.png)](./tm2-200.png)

#### Status Code 201

[![Hasil Pengujian Status Code 201](./tm2-201.png)](./tm2-201.png)

#### Status Code 400

[![Hasil Pengujian Status Code 400](./tm2-400.png)](./tm2-400.png)

### 4. Pengujian Request & Response (TM-3)

Pengujian Request dan Response dilakukan menggunakan endpoint `/get` dan `/headers` pada HTTPBin.

Pengujian `/get` digunakan untuk melihat query parameter yang dikirim oleh client, sedangkan `/headers` digunakan untuk melihat HTTP header yang diterima oleh server.

#### Pengujian Fungsi GET TM-3

[![Hasil Pengujian TM-3 Fungsi GET](./tm3-get.png)](./tm3-get.png)

#### Pengujian Headers TM-3

[![Hasil Pengujian TM-3 Headers](./tm3-get-headers.png)](./tm3-get-headers.png)

## Lokasi Bukti

Bukti screenshot hasil pengujian disimpan pada folder:

`pertemuan-02/kegiatan-praktikum/`

### Bukti TM-1

- [tm1-fungsi-get.png](./tm1-fungsi-get.png)
- [tm1-fungsi-put.png](./tm1-fungsi-put.png)

### Bukti TM-2

- [tm2-200.png](./tm2-200.png)
- [tm2-201.png](./tm2-201.png)
- [tm2-400.png](./tm2-400.png)

### Bukti TM-3

- [tm3-fungsi-get.png](./tm3-get.png)
- [tm3-fungsi-headers.png](./tm3-get-headers.png)

## Laporan Tugas

### TM-1 — HTTP Method

[`tugas-mandiri-1-http-method.md`](../tugas-mandiri/backend/tugas-mandiri-1-http-method.md)

### TM-2 — HTTP Status Code

[`tugas-mandiri-2-status-kode.md`](../tugas-mandiri/backend/tugas-mandiri-2-status-kode.md)

### TM-3 — Request & Response

[`tugas-mandiri-3-request-response.md`](../tugas-mandiri/backend/tugas-mandiri-3-request-response.md)