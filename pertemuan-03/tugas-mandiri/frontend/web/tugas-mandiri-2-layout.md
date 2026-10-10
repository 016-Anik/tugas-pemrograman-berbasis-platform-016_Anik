
# Tugas Mandiri 2
## Menyusun Tata Letak dengan Class Utility

### 1. Tujuan

Tugas ini bertujuan mempelajari penggunaan class utility Tailwind CSS untuk menyusun tata letak halaman web yang responsif. Halaman dibuat menggunakan Tailwind CSS CDN tanpa menambahkan CSS buatan sendiri.

### 2. Hasil Implementasi

Halaman yang dibuat adalah Profil Mahasiswa dengan tema pastel pink. Halaman terdiri dari navbar, hero, tiga kartu informasi, dan footer.

Bagian navbar memuat tautan Beranda, Profil, dan Kontak. Bagian hero berisi judul sambutan, deskripsi singkat, tombol Jelajahi Profil, dan foto mahasiswa. Tiga kartu konten berisi Biodata, Jadwal Kuliah, dan Kegiatan. Bagian footer menampilkan nama mahasiswa, tahun, dan mata praktikum.

### 3. Class Utility dan Fungsinya

| Bagian | Class Utility | Fungsi |
|---|---|---|
| Navbar | `flex`, `flex-col`, `sm:flex-row`, `gap-3`, `sm:justify-between` | Mengatur susunan navigasi menjadi vertikal pada layar kecil dan horizontal pada layar yang lebih lebar. |
| Hero | `grid`, `grid-cols-1`, `md:grid-cols-2`, `items-center`, `gap-8` | Mengatur hero menjadi satu kolom pada layar kecil dan dua kolom mulai breakpoint `md`. |
| Judul hero | `text-3xl`, `md:text-5xl`, `font-bold`, `leading-tight` | Mengatur ukuran, ketebalan, dan jarak baris judul sesuai ukuran layar. |
| Foto profil | `h-56`, `w-56`, `rounded-full`, `object-cover`, `md:h-72`, `md:w-72` | Mengatur ukuran foto, membuat bentuk lingkaran, dan menyesuaikan ukuran foto pada layar lebih lebar. |
| Kumpulan kartu | `grid`, `grid-cols-1`, `md:grid-cols-3`, `gap-6` | Menyusun kartu menjadi satu kolom pada layar kecil dan tiga kolom mulai breakpoint `md`, dengan jarak antarkartu. |
| Kartu konten | `rounded-2xl`, `border`, `bg-white`, `p-6`, `shadow-sm` | Mengatur sudut, garis tepi, warna latar, padding, dan bayangan kartu. |
| Efek hover | `transition-transform`, `hover:-translate-y-1`, `hover:shadow-lg` | Mengangkat kartu sedikit dan memperbesar bayangannya saat kursor diarahkan ke kartu. |
| Tombol | `bg-[#c65d91]`, `hover:bg-[#a94778]`, `px-6`, `py-3`, `rounded-xl` | Mengatur warna, ukuran, sudut tombol, dan perubahan warna saat kursor berada di atas tombol. |
| Footer | `bg-white`, `px-4`, `py-6`, `text-center` | Memberikan latar putih, jarak bagian dalam, dan membuat teks berada di tengah. |

### 4. Hubungan Class Utility dengan Tampilan

Class utility menentukan tampilan elemen secara langsung melalui atribut `class`. Contohnya, `grid-cols-1` membuat kumpulan kartu tersusun dalam satu kolom, sedangkan `md:grid-cols-3` mengubahnya menjadi tiga kolom mulai breakpoint `md` Tailwind CSS, yaitu 768 piksel pada konfigurasi standar. Class `gap-6` memberikan jarak antarkartu, sementara `hover:shadow-lg` menambahkan bayangan ketika kursor berada di atas kartu.

### 5. Analisis Penggunaan Class Utility

Bagian yang paling mudah disusun menggunakan class utility adalah kumpulan kartu karena kombinasi `grid`, `grid-cols-1`, `md:grid-cols-3`, dan `gap-6` dapat mengatur kolom dan jarak tanpa menulis CSS sendiri. Sementara itu, bagian yang class-nya lebih sulit dibaca adalah kartu konten karena banyak class untuk mengatur warna, padding, border, bayangan, dan efek hover ditulis dalam satu atribut `class`. Meskipun demikian, penggunaan utility memudahkan perubahan tampilan secara langsung pada elemen HTML.

### 6. Kesimpulan

Tailwind CSS membantu menyusun halaman Profil Mahasiswa yang responsif dengan memanfaatkan class utility. Penggunaan `flex`, `grid`, `gap`, breakpoint `md:`, dan efek `hover:` membuat tata letak lebih mudah diatur untuk berbagai ukuran layar. Namun, atribut `class` yang panjang perlu ditulis dengan rapi agar kode tetap mudah dibaca dan dipelihara.

### 7. Dokumentasi Screenshot

- Screenshot tampilan laptop.
- Screenshot tampilan pada lebar layar 360 px.
