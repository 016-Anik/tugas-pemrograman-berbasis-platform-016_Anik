# Tugas Mandiri 4 — JSON Web Token (JWT)

**Nama:** Sri Maulani
**NIM:** 2024520016
**Program Studi:** Informatika
**Mata Kuliah:** Pemrograman Berbasis Platform

## 1. Tujuan

Tujuan tugas ini adalah memahami struktur JSON Web Token (JWT), mengenali fungsi header, payload, dan signature, serta menguji bagaimana perubahan payload memengaruhi proses verifikasi signature.

## 2. Alat yang Digunakan

1. Website [jwt.io](https://jwt.io/) untuk membaca dan menguji token JWT.
2. Browser Google Chrome untuk menjalankan pengujian.
3. JWT latihan yang dibuat menggunakan data mahasiswa.

## 3. Data Pengujian

Token JWT dibuat menggunakan algoritma HS256 dengan payload berikut:

```json
{
  "sub": "2024520016",
  "nama": "Sri Maulani",
  "role": "mahasiswa"
}
```

Keterangan:

* `sub`: identitas subjek atau pengguna dalam token.
* `nama`: nama pengguna.
* `role`: peran pengguna, yaitu mahasiswa.

## 4. Struktur JWT

JSON Web Token terdiri dari tiga bagian yang dipisahkan oleh tanda titik (`.`), yaitu:

1. **Header** — berisi informasi mengenai tipe token dan algoritma yang digunakan. Pada pengujian ini, algoritma yang digunakan adalah HS256.
2. **Payload** — berisi data atau claims, seperti identitas dan peran pengguna.
3. **Signature** — digunakan untuk memverifikasi integritas token dan memastikan bahwa data yang ditandatangani tidak diubah tanpa menghasilkan signature yang sesuai.

Payload JWT dapat dibaca tanpa secret key. Oleh karena itu, informasi rahasia tidak boleh disimpan di dalam payload.

## 5. Langkah-Langkah Pengujian

### 5.1 Pengujian Token Asli

1. Membuka website jwt.io.
2. Memasukkan token JWT latihan ke bagian Encoded.
3. Memeriksa header dan payload pada bagian Decoded.
4. Memastikan payload berisi `sub`, `nama`, dan `role` sesuai data yang dibuat.
5. Memeriksa hasil verifikasi signature menggunakan secret yang sesuai.

**Hasil pengujian:** Payload token asli dapat dibaca dan menampilkan data mahasiswa sesuai dengan data yang digunakan saat pembuatan token.

**Bukti screenshot:** `tm4-token-asli.png`

### 5.2 Pengujian Payload yang Diubah

1. Mengubah nilai `role` dari `mahasiswa` menjadi `admin`.
2. Mempertahankan signature asli tanpa melakukan penandatanganan ulang.
3. Memasukkan token hasil perubahan ke jwt.io.
4. Memeriksa kembali payload dan hasil verifikasi signature.

**Hasil pengujian:** jwt.io menampilkan pesan `Signature Verification Failed`. Hasil tersebut menunjukkan bahwa signature tidak cocok dengan data token yang telah diubah.

**Bukti screenshot:** `tm4-token-diubah.png`

### 5.3 Pengamatan Struktur JWT

Pada pengujian ini, header menunjukkan algoritma HS256 dan tipe JWT, sedangkan payload berisi identitas dan peran mahasiswa. Ketiga bagian token dipisahkan oleh tanda titik.

**Bukti screenshot:** `tm4-struktur-jwt.png`

## 6. Analisis Hasil

Berdasarkan pengujian, payload JWT dapat dibaca selama format token dan encoding-nya benar. Namun, perubahan payload tanpa menghasilkan signature yang sesuai menyebabkan proses verifikasi signature gagal.

Hal ini menunjukkan bahwa signature berperan dalam memverifikasi integritas data yang ditandatangani. Status payload yang valid sebagai JSON tidak otomatis berarti signature token juga valid.

## 7. Kesimpulan

JWT merupakan format token yang terdiri dari header, payload, dan signature. Header menjelaskan tipe token dan algoritma yang digunakan, payload menyimpan claims pengguna, sedangkan signature digunakan untuk memverifikasi integritas token.

Berdasarkan pengujian menggunakan jwt.io, perubahan nilai `role` dari `mahasiswa` menjadi `admin` dengan mempertahankan signature lama menghasilkan pesan `Signature Verification Failed`. Dengan demikian, pengujian menunjukkan bahwa perubahan data dapat terdeteksi melalui verifikasi signature, selama token diverifikasi dengan algoritma dan secret yang benar.

## 8. Dokumentasi

Screenshot hasil pengujian disimpan dengan nama:

* `jwt-payload.png`
* `jwt-token-asli-200.png`
* `jwt-token-diubah-401.png`