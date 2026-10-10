# Tugas Mandiri 5: Hashing, bcrypt, dan Keamanan Secret

## 1. Percobaan Hashing dengan bcrypt

Pada percobaan ini, saya menggunakan library `bcryptjs` untuk melakukan hashing terhadap teks `sama` dengan cost factor `10`.

Perintah yang digunakan:

```bash
node -e "console.log(require('bcryptjs').hashSync('sama', 10))"
```

**Hasil hash pertama:**

```text
$2b$10$HWEPGasWmmS8KnfXSNWlt.HFDbADPu4lekeB.tyVgq08oG0rzgKgm
```

**Hasil hash kedua:**

```text
$2b$10$0MGrEZsdqeC9JM71QXs7aO9bGx4z/Z97xUADgiMyPiiwW0IKLsyeC
```

**Analisis:**

Kedua hasil hash berbeda meskipun menggunakan teks input yang sama, yaitu `sama`. Hal ini terjadi karena bcrypt menggunakan salt acak pada setiap proses hashing. Angka `10` menunjukkan cost factor yang digunakan. Semakin tinggi cost factor, semakin besar komputasi yang dibutuhkan untuk menghasilkan hash.

## 2. Jawaban Pertanyaan

### 1. Apa perbedaan hashing dan enkripsi?

Hashing merupakan proses satu arah yang mengubah data menjadi nilai hash. Nilai hash tidak dirancang untuk dikembalikan langsung menjadi teks aslinya. Sementara itu, enkripsi mengubah data menjadi bentuk yang tidak dapat dibaca dan dapat dikembalikan melalui proses dekripsi menggunakan kunci yang sesuai.

### 2. Mengapa password disimpan dalam bentuk hash?

Password sebaiknya disimpan dalam bentuk hash agar password asli tidak langsung terbaca jika database bocor. Dengan menggunakan algoritma khusus password seperti bcrypt, penyerang juga perlu melakukan komputasi untuk menebak password yang sesuai.

### 3. Bagaimana cara kerja `bcrypt.compare()`?

Fungsi `bcrypt.compare()` digunakan untuk memeriksa apakah password yang dimasukkan pengguna sesuai dengan hash yang tersimpan. Fungsi ini menggunakan informasi salt dan cost factor dari hash untuk melakukan verifikasi, kemudian menghasilkan nilai `true` jika cocok dan `false` jika tidak cocok.

### 4. Apa fungsi salt dan bagaimana salt membantu menghadapi rainbow table?

Salt adalah nilai acak yang ditambahkan dalam proses hashing. Salt membuat password yang sama dapat menghasilkan hash berbeda. Hal ini mengurangi efektivitas rainbow table, yaitu kumpulan hasil hash yang telah dihitung sebelumnya, karena penyerang tidak dapat langsung menggunakan satu hasil hash untuk semua password yang sama.

### 5. Mengapa `JWT_SECRET` harus dirahasiakan dan tidak boleh masuk ke Git?

`JWT_SECRET` digunakan untuk menandatangani atau memverifikasi token JWT pada algoritma yang menggunakan secret bersama. Jika secret diketahui orang lain, mereka dapat mencoba membuat token dengan tanda tangan yang valid. Oleh karena itu, secret perlu disimpan di file konfigurasi lokal seperti `.env`, dikecualikan dari Git, dan tidak boleh dibagikan secara publik. Jika secret terlanjur masuk ke riwayat Git, menghapusnya dari file terbaru saja tidak cukup. Secret tersebut perlu diganti atau dirotasi.

## 3. Pemeriksaan Keamanan Git

### A. Pemeriksaan file `.env`

Perintah yang digunakan untuk memeriksa path file `.env` pada lokasi tugas:

```powershell
git ls-files --error-unmatch pertemuan-03/tugas-mandiri/backend/.env 2>$null; if ($LASTEXITCODE -eq 0) { "BAHAYA: .env terlacak" } else { "AMAN: .env tidak terlacak" }
```

**Hasil:**

```text
AMAN: .env tidak terlacak
```

**Analisis:**

Git tidak melacak file `.env` pada path yang diperiksa. Hal ini merupakan praktik yang baik karena file tersebut dapat berisi secret atau konfigurasi sensitif. Pemeriksaan ini hanya memastikan status pelacakan pada path tersebut, bukan memastikan bahwa file tidak pernah masuk ke riwayat Git.

### B. Pemeriksaan pola token JWT

Perintah yang digunakan:

```powershell
git grep -nE 'eyJ[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+' -- pertemuan-03
```

**Hasil:**

```text
AMAN: tidak ada pola JWT pada file terlacak di pertemuan-03
```

**Analisis:**

Pemeriksaan tidak menemukan pola token JWT yang dicari pada file yang dilacak Git di folder `pertemuan-03`. Hasil ini membantu mengurangi risiko token tersimpan di dokumentasi atau kode yang dilacak Git, tetapi tidak menjamin bahwa tidak ada token di luar cakupan pemeriksaan atau di riwayat Git.

## 4. Kesimpulan

Berdasarkan percobaan, bcrypt menghasilkan hash yang berbeda untuk teks input yang sama karena menggunakan salt acak. Hashing cocok untuk penyimpanan password karena tidak dirancang untuk dibalik menjadi teks asli. Selain itu, file `.env` perlu dijaga agar tidak terlacak Git dan token JWT harus dihindari dari dokumentasi maupun kode yang dipublikasikan. Pemeriksaan keamanan Git membantu menemukan potensi kebocoran, tetapi tetap perlu dilakukan dengan cakupan yang tepat.