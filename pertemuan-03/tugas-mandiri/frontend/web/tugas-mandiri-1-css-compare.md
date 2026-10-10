
# Tugas Mandiri 1
## Perbandingan Component-Based dan Utility-First

### 1. Tujuan

Tugas ini bertujuan membandingkan pendekatan component-based dan utility-first dalam membuat kartu profil mahasiswa, terutama dari segi penulisan kode, waktu pengerjaan, kemudahan perubahan tema, dan responsivitas.

### 2. Hasil Implementasi

Kedua versi menggunakan konten yang sama, yaitu foto profil, nama Sri Maulani, NIM 2024520016, dan tombol "Lihat Profil". Keduanya menggunakan tema pastel pink dan dapat menyesuaikan tampilan pada layar laptop maupun layar selebar 360 px.

Pada versi component-based, tampilan diatur menggunakan CSS di dalam tag `<style>` dengan class seperti `.card`, `.card-photo`, dan `.btn`.

Pada versi utility-first, tampilan diatur menggunakan class utility dari Tailwind CSS melalui CDN tanpa menambahkan CSS sendiri.

### 3. Perbandingan

| Aspek | Component-Based | Utility-First |
|---|---|---|
| Penulisan CSS | Menggunakan aturan CSS dalam tag `<style>` | Menggunakan class utility Tailwind CSS |
| Jumlah baris CSS | Sekitar 83 baris, termasuk baris kosong | 0 baris CSS tambahan |
| Jumlah class utility | 0 class utility Tailwind | Sekitar 42 pemakaian class utility |
| Waktu pengerjaan | Disesuaikan dengan waktu pengerjaan aktual | Disesuaikan dengan waktu pengerjaan aktual |
| Perubahan tema | Mengubah aturan CSS pada class komponen | Mengubah class utility pada elemen |
| Penggunaan ulang | Class komponen dapat digunakan kembali pada beberapa elemen | Kombinasi class utility dapat digunakan kembali |
| Responsivitas | Menggunakan media query CSS | Menggunakan breakpoint utility Tailwind CSS |


### 4. Analisis

Pendekatan component-based memisahkan aturan tampilan ke dalam class CSS. Jika beberapa elemen menggunakan class yang sama, perubahan pada satu aturan dapat diterapkan ke seluruh elemen yang menggunakan class tersebut. Pendekatan ini membuat pengelolaan tema lebih terpusat.

Pendekatan utility-first mengatur tampilan langsung melalui class pada elemen HTML. Pendekatan ini memudahkan pengaturan jarak, warna, ukuran, dan responsivitas tanpa harus menulis aturan CSS sendiri. Namun, atribut class dapat menjadi panjang karena memuat banyak utility.

### 5. Pilihan Pendekatan untuk Proyek Akhir

Untuk halaman yang memiliki banyak komponen dengan tampilan konsisten, seperti dashboard admin, saya memilih [component-based/utility-first].

Untuk halaman yang membutuhkan pembuatan antarmuka secara cepat dan variasi tata letak, seperti halaman profil atau landing page, saya memilih [component-based/utility-first].

### 6. Kesimpulan

Kedua pendekatan dapat digunakan untuk membuat kartu profil yang responsif. Component-based memusatkan aturan tampilan pada CSS, sedangkan utility-first mengatur tampilan melalui class utility. Pilihan terbaik bergantung pada kebutuhan pemeliharaan, konsistensi desain, dan kecepatan pengembangan proyek.

### 7. Dokumentasi Screenshot

- Versi component-based pada layar laptop
- Versi component-based pada layar 360 px
- Versi utility-first pada layar laptop
- Versi utility-first pada layar 360 px
