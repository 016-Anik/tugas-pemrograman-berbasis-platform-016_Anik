# Tugas Mandiri 3 — Analisis Authentication dan Authorization

Proyek Kelompok: Sistem Repository Skripsi dan Pemetaan Peminatan Mahasiswa (Studi Kasus: Fakultas Teknik UNIRA)

---

## 1. Peran Pengguna (Roles)
Proyek kelompok ini menggunakan tiga peran utama yang terlibat dalam sistem:
1. **Mahasiswa**: Pengguna yang memilih peminatan, mengajukan judul skripsi, dan mengunggah dokumen skripsi.
2. **Kaprodi**: Pengguna yang memvalidasi judul/skripsi, memantau statistik peminatan, dan mengelola repository.
3. **Tendik**: Pengguna tenaga kependidikan yang mengelola data master mahasiswa, rekapitulasi, dan laporan akademik.

---

## 2. Fitur Spesifik Sistem (Minimal 6 Fitur)
1. Memilih peminatan (BI / SA)
2. Mengajukan judul skripsi
3. Mengunggah dokumen skripsi
4. Validasi judul skripsi oleh Kaprodi
5. Menambah data mahasiswa baru
6. Melihat statistik peminatan mahasiswa

---

## 3. Tabel Matriks Hak Akses (Access Matrix)

| Fitur | Mahasiswa | Kaprodi | Tendik | Endpoint & Method |
| :--- | :---: | :---: | :---: | :--- |
| **Memilih peminatan** | ✅ | ❌ | ❌ | `POST /api/v1/peminatan/pilih` |
| **Mengajukan judul skripsi** | ✅ | ❌ | ❌ | `POST /api/v1/theses/pengajuan` |
| **Mengunggah dokumen skripsi** | ✅ | ❌ | ❌ | `POST /api/v1/theses/upload` |
| **Validasi judul skripsi** | ❌ | ✅ | ❌ | `PUT /api/v1/theses/validate/:id` |
| **Menambah data mahasiswa** | ❌ | ❌ | ✅ | `POST /api/v1/mahasiswa` |
| **Melihat statistik peminatan** | ❌ | ✅ | ✅ | `GET /api/v1/peminatan/statistik` |

---

## 4. Analisis Skenario Pemeriksaan (Authentication vs Authorization)

Pada aplikasi repository skripsi dan peminatan ini, skenario akses dapat diilustrasikan melalui contoh berikut: Mahasiswa bernama Sri Maulani berhasil login menggunakan NIM dan kata sandinya sehingga identitasnya terverifikasi. Ketika Sri Maulani mencoba mengakses endpoint penambahan data mahasiswa (`POST /api/v1/mahasiswa`), sistem akan menolak permintaan tersebut karena fitur itu khusus milik Tendik.

| Keadaan Pengguna | Pemeriksaan Identitas | Hasil yang Diharapkan pada Endpoint Terlindungi |
| :--- | :--- | :--- |
| **Sri Maulani tidak menyertakan token** | Identitas belum terverifikasi | **401 Unauthorized** |
| **Sri Maulani menyertakan token valid dan meminta akses ke fitur mahasiswa (memilih peminatan)** | Identitas dan hak akses memenuhi aturan | **200 OK / 201 Created** (Permintaan diizinkan) |
| **Sri Maulani menyertakan token valid dan meminta akses ke fitur Tendik (menambah data mahasiswa)** | Identitas valid, tetapi hak akses tidak memenuhi aturan | **403 Forbidden** |

### Penjelasan Penggunaan Kode 401 dan 403
- **Kode 401 Unauthorized** diberikan kepada permintaan yang sama sekali tidak menyertakan token autentikasi atau tokennya sudah tidak valid/kadaluwarsa. Hal ini berarti sistem belum mengenali siapa yang mengirimkan permintaan tersebut (identitas belum terverifikasi).
- **Kode 403 Forbidden** diberikan kepada permintaan yang menyertakan token valid, sehingga identitas pengguna sudah dikenali oleh sistem, namun pengguna tersebut tidak memiliki hak akses (*role*) yang diperlukan untuk mengakses endpoint tertentu (misalnya Mahasiswa memaksa mengakses endpoint khusus Tendik).

---

## 5. Analisis Risiko Tanpa Pemeriksaan Peran (`requireRole`)

Jika endpoint penambahan data mahasiswa hanya memeriksa identitas melalui `requireAuth` tanpa memeriksa peran melalui `requireRole`, sistem hanya memastikan bahwa pengguna tersebut sudah login. Akibatnya, mahasiswa yang sudah login dapat mengakses fitur penambahan data mahasiswa karena tidak adanya lapis pemeriksaan hak akses peran yang membatasi endpoint tersebut.