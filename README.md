[Uploading README_Praktikum6_Authbook.md…]()
# 📚 Authbook — Sistem Pengelolaan Data Buku

<p align="center">
  <strong>Aplikasi Pengelolaan Buku Berbasis Laravel dan Filament</strong><br>
  Praktikum Pemrograman Berbasis Web — Pertemuan 6
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PHP-8.2%2B-777BB4?logo=php&logoColor=white" alt="PHP 8.2+">
  <img src="https://img.shields.io/badge/Laravel-12-FF2D20?logo=laravel" alt="Laravel">
  <img src="https://img.shields.io/badge/Filament-3-FDAE4B?logo=filament" alt="Filament">
  <img src="https://img.shields.io/badge/Database-SQLite-003B57?logo=sqlite" alt="SQLite">
  <img src="https://img.shields.io/badge/Project-Praktikum-blue" alt="Project Praktikum">
</p>

---

## 📋 Identitas Mahasiswa

| Keterangan | Informasi |
|---|---|
| Nama | Ridwan Odi Nugroho |
| NPM | 4524210089 |
| Program Studi | Teknik Informatika |
| Universitas | Universitas Pancasila |
| Mata Kuliah | Pemrograman Berbasis Web |
| Praktikum | Pertemuan 6 |

## 📖 Deskripsi Proyek

**Authbook** merupakan proyek aplikasi pengelolaan data buku yang dikembangkan menggunakan framework Laravel dan Filament. Proyek ini dibuat sebagai bagian dari Praktikum Pemrograman Berbasis Web Pertemuan 6 untuk mempelajari proses pembuatan proyek Laravel, konfigurasi database, instalasi panel admin, serta pengelolaan data menggunakan model dan migration.

Pada praktikum ini, aplikasi menggunakan dua model utama, yaitu `Author` dan `Book`. Model Author digunakan untuk menyimpan data penulis, sedangkan model Book digunakan untuk menyimpan informasi buku yang berhubungan dengan penulisnya.

Database dirancang menggunakan SQLite agar pengelolaan basis data dapat dilakukan tanpa memerlukan server database terpisah. Filament digunakan untuk menyiapkan panel administrasi yang menjadi dasar pengembangan antarmuka pengelolaan data.

## 🎯 Tujuan Praktikum

Tujuan pelaksanaan Praktikum Pertemuan 6 adalah:

1. Memahami proses pembuatan proyek Laravel baru menggunakan Composer.
2. Memahami konfigurasi database menggunakan SQLite.
3. Menginstal dan menyiapkan Filament sebagai panel administrasi.
4. Membuat model Laravel menggunakan perintah Artisan.
5. Membuat migration untuk menentukan struktur tabel database.
6. Memahami penggunaan `$fillable` pada model.
7. Memahami relasi one-to-many antara Author dan Book.
8. Memahami relasi many-to-one antara Book dan Author.
9. Memahami penggunaan foreign key dalam database.
10. Menjalankan migration dan memeriksa struktur database.

## ✨ Fitur dan Komponen Utama

### 1. 🚀 Setup Project Laravel

Proyek dibuat menggunakan Composer dengan perintah:

```bash
composer create-project laravel/laravel authbook
```

Perintah tersebut digunakan untuk membuat proyek Laravel baru beserta dependensi awal yang diperlukan.

### 2. 🗄️ Konfigurasi Database SQLite

SQLite digunakan sebagai database aplikasi. Database disimpan dalam file lokal sehingga tidak membutuhkan server database terpisah.

File database yang digunakan adalah:

```text
database/database.sqlite
```

Konfigurasi koneksi database dilakukan melalui file `.env` dengan pengaturan:

```env
DB_CONNECTION=sqlite
```

### 3. ⚙️ Instalasi Filament

Filament digunakan untuk menyiapkan panel administrasi aplikasi.

Instalasi dilakukan menggunakan Composer:

```bash
composer require filament/filament:"^3.0"
```

Setelah instalasi, panel administrasi disiapkan melalui perintah:

```bash
php artisan filament:install --panels
```

Salah satu file konfigurasi panel yang perlu diperiksa adalah:

```text
app/Providers/Filament/AdminPanelProvider.php
```
<img width="544" height="517" alt="image" src="https://github.com/user-attachments/assets/3e325979-d648-46ae-b2e0-e9d1e5e4640c" />


### 4. ✍️ Model Author

Model `Author` digunakan untuk merepresentasikan data penulis buku.

Model ini memiliki atribut utama:

- `id`: Identitas unik penulis.
- `name`: Nama penulis.
- `created_at`: Waktu data dibuat.
- `updated_at`: Waktu data diperbarui.

Model Author juga memiliki relasi `hasMany` dengan model Book, yang berarti satu penulis dapat memiliki banyak buku.

### 5. 📚 Model Book

Model `Book` digunakan untuk merepresentasikan data buku.

Atribut yang dirancang meliputi:

| Atribut | Keterangan |
|---|---|
| `id` | Identitas unik buku |
| `isbn` | Nomor identifikasi buku yang unik |
| `title` | Judul buku |
| `author_id` | ID penulis yang berhubungan dengan buku |
| `publisher` | Nama penerbit, boleh kosong |
| `year` | Tahun terbit, boleh kosong |
| `cover` | Informasi cover buku, boleh kosong |
| `status` | Status buku, yaitu available atau borrowed |
| `created_at` | Waktu data dibuat |
| `updated_at` | Waktu data diperbarui |

Atribut `author_id` digunakan sebagai foreign key yang menghubungkan buku dengan penulisnya.

### 6. 🔗 Relasi Author dan Book

Aplikasi menggunakan relasi antarmodel Laravel Eloquent.

**Relasi Author ke Book**

```php
public function books(): HasMany
{
    return $this->hasMany(Book::class);
}
```

Relasi tersebut menunjukkan bahwa satu penulis dapat mempunyai banyak buku.

**Relasi Book ke Author**

```php
public function author(): BelongsTo
{
    return $this->belongsTo(Author::class);
}
```

Relasi tersebut menunjukkan bahwa satu buku berhubungan dengan satu penulis melalui atribut `author_id`.

### 7. 🔄 Migration Database

Migration digunakan untuk membuat struktur tabel database melalui kode PHP.

Tabel yang dirancang dalam praktikum ini adalah:

- `authors`: Menyimpan data penulis.
- `books`: Menyimpan data buku dan relasinya dengan penulis.

Migration dijalankan menggunakan:

```bash
php artisan migrate
```

## 🛠️ Teknologi yang Digunakan

| Teknologi | Fungsi |
|---|---|
| PHP | Bahasa pemrograman backend |
| Laravel | Framework pengembangan aplikasi web |
| Composer | Mengelola dependensi PHP |
| Filament 3 | Menyiapkan panel administrasi |
| SQLite | Basis data berbasis file |
| Laravel Eloquent ORM | Mengelola interaksi model dengan database |
| Laravel Artisan | Menjalankan perintah pengembangan Laravel |
| Git dan GitHub | Mengelola versi dan menyimpan kode proyek |

## 🧠 Konsep Pemrograman yang Diterapkan

### 1. Model

Model merupakan bagian Laravel yang digunakan untuk merepresentasikan data dan berinteraksi dengan database melalui Eloquent ORM.

Dalam proyek Authbook, model yang digunakan adalah `Author` dan `Book`.

### 2. Migration

Migration digunakan untuk mendefinisikan struktur tabel database melalui kode PHP.

Migration membantu pengembang membuat dan mengelola struktur database secara terorganisasi.

### 3. Mass Assignment

Properti `$fillable` digunakan untuk menentukan atribut yang diperbolehkan diisi melalui mass assignment.

Contoh pada model Author:

```php
protected $fillable = [
    'name',
];
```

Contoh pada model Book:

```php
protected $fillable = [
    'isbn',
    'title',
    'author_id',
    'publisher',
    'year',
    'cover',
    'status',
];
```

### 4. Relasi One-to-Many

Relasi one-to-many menunjukkan hubungan satu data dengan banyak data lainnya.

Dalam proyek ini, satu Author dapat memiliki banyak Book. Relasi tersebut didefinisikan menggunakan `hasMany()`.

### 5. Relasi Many-to-One

Relasi many-to-one menunjukkan bahwa banyak data dapat berhubungan dengan satu data yang sama.

Dalam proyek ini, beberapa Book dapat dimiliki oleh satu Author. Relasi tersebut didefinisikan menggunakan `belongsTo()`.

### 6. Foreign Key

Foreign key merupakan kolom yang menghubungkan suatu tabel dengan tabel lainnya.

Pada tabel `books`, kolom `author_id` menghubungkan data buku dengan tabel `authors`.

Pengaturan `onDelete('cascade')` pada migration dirancang agar penghapusan data penulis juga menghapus buku yang terkait.

### 7. Type Casting

Properti `$casts` digunakan untuk mengonversi tipe atribut model secara otomatis.

Pada model Book, atribut `year` dikonversi menjadi integer:

```php
protected $casts = [
    'year' => 'integer',
];
```

### 8. Filament Panel

Filament menyediakan fondasi panel administrasi Laravel. Instalasi panel merupakan langkah awal sebelum menambahkan resource untuk pengelolaan model Author dan Book.

## 🔄 Alur Kerja Pengembangan

Alur pengerjaan proyek Authbook pada Pertemuan 6 adalah sebagai berikut:

```text
Mulai
  |
  v
Membuat Project Laravel
  |
  v
Konfigurasi Database SQLite
  |
  v
Instalasi Filament
  |
  v
Membuat Model Author
  |
  v
Membuat Migration Author
  |
  v
Membuat Model Book
  |
  v
Membuat Migration Book
  |
  v
Mengatur Relasi Antarmodel
  |
  v
Menjalankan Migration
  |
  v
Memeriksa Struktur Database
  |
  v
Selesai
```

## 📂 Struktur Proyek

Berikut gambaran struktur direktori proyek Authbook setelah komponen utama praktikum dibuat:

```text
Praktikum 6/
└── authbook/
    ├── app/
    │   ├── Models/
    │   │   ├── Author.php
    │   │   └── Book.php
    │   └── Providers/
    │       └── Filament/
    │           └── AdminPanelProvider.php
    ├── bootstrap/
    ├── database/
    │   ├── database.sqlite
    │   └── migrations/
    │       ├── xxxx_create_authors_table.php
    │       └── xxxx_create_books_table.php
    ├── public/
    ├── resources/
    ├── routes/
    ├── storage/
    ├── .env
    ├── .env.example
    ├── artisan
    ├── composer.json
    └── package.json
```

**Catatan:** Struktur di atas merupakan gambaran direktori yang diharapkan. Nama file migration mengikuti timestamp yang dibuat oleh Laravel, sedangkan file dan folder Filament bergantung pada proses instalasi.

### Penjelasan Direktori Penting

| Direktori atau Berkas | Fungsi |
|---|---|
| `app/Models/` | Menyimpan model Author dan Book |
| `app/Providers/Filament/` | Menyimpan konfigurasi panel Filament |
| `database/migrations/` | Menyimpan definisi struktur tabel |
| `database/database.sqlite` | Menyimpan database SQLite |
| `routes/` | Menyimpan definisi route aplikasi |
| `.env` | Menyimpan konfigurasi lingkungan lokal |
| `composer.json` | Mendefinisikan dependensi PHP |
| `artisan` | Menjalankan perintah CLI Laravel |

## 💻 Persyaratan Sistem

Sebelum menjalankan proyek, siapkan:

- PHP dengan ekstensi yang dibutuhkan Laravel dan SQLite.
- Composer.
- Node.js dan npm jika diperlukan untuk pengelolaan aset frontend.
- Browser modern.
- Git apabila ingin mengelola repository menggunakan Git.

Versi PHP yang digunakan harus sesuai dengan persyaratan versi Laravel yang terpasang.

## 🚀 Instalasi dan Konfigurasi

### 1. Membuat Project

Jalankan:

```bash
composer create-project laravel/laravel authbook
```

Masuk ke direktori proyek:

```bash
cd authbook
```

### 2. Menyiapkan Database SQLite

Buat file database SQLite jika belum tersedia.

Pada PowerShell:

```powershell
New-Item database/database.sqlite -ItemType File
```

Jika file sudah tersedia, jangan membuat file duplikat.

Atur konfigurasi `.env`:

```env
DB_CONNECTION=sqlite
```

### 3. Menginstal Filament

Jalankan:

```bash
composer require filament/filament:"^3.0"
```

Kemudian:

```bash
php artisan filament:install --panels
```

Ikuti instruksi instalasi yang ditampilkan di terminal.

### 4. Membuat Model Author

Jalankan:

```bash
php artisan make:model Author -m
```

Edit file migration Author dan model `app/Models/Author.php` sesuai struktur dan relasi yang ditentukan dalam materi praktikum.

### 5. Membuat Model Book

Jalankan:

```bash
php artisan make:model Book -m
```

Edit file migration Book dan model `app/Models/Book.php`, termasuk atribut, foreign key, status buku, serta relasinya dengan Author.

### 6. Menjalankan Migration

Setelah struktur migration selesai disiapkan, jalankan:

```bash
php artisan migrate
```

Perintah ini membuat tabel berdasarkan migration yang tersedia dan belum dijalankan.

### 7. Memeriksa Database

Untuk melihat status migration:

```bash
php artisan migrate:status
```

Untuk melihat informasi database:

```bash
php artisan db:show
```

### 8. Menjalankan Development Server

Jalankan:

```bash
php artisan serve
```

Buka browser pada alamat:

```text
http://localhost:8000
```

Panel Filament biasanya diakses melalui route `/admin` jika panel menggunakan ID `admin` dan konfigurasi route default.

## 🧪 Pemeriksaan Hasil Praktikum

Berikut daftar pemeriksaan untuk memastikan langkah-langkah praktikum telah dikerjakan.

| No. | Pemeriksaan | Hasil yang Diharapkan |
|---|---|---|
| 1 | Project Laravel dibuat | Direktori `authbook` tersedia |
| 2 | Database SQLite disiapkan | File `database.sqlite` tersedia |
| 3 | Filament diinstal | Dependensi Filament terpasang |
| 4 | Panel Filament disiapkan | File provider panel tersedia |
| 5 | Model Author dibuat | File `Author.php` tersedia |
| 6 | Model Book dibuat | File `Book.php` tersedia |
| 7 | Migration Author dibuat | Migration tabel `authors` tersedia |
| 8 | Migration Book dibuat | Migration tabel `books` tersedia |
| 9 | Relasi antarmodel ditambahkan | `hasMany` dan `belongsTo` didefinisikan |
| 10 | Migration dijalankan | Tabel berhasil dibuat |
| 11 | Status migration diperiksa | Status migration dapat ditampilkan |
| 12 | Server Laravel dijalankan | Halaman aplikasi dapat diakses |

Tabel tersebut merupakan daftar pemeriksaan praktikum. Status keberhasilan setiap langkah ditentukan berdasarkan hasil pengerjaan dan pemeriksaan langsung pada proyek.

## 🛡️ Keamanan dan Pengelolaan Proyek

Beberapa hal yang perlu diperhatikan:

- Jangan mengunggah `.env` yang berisi konfigurasi rahasia.
- Pastikan `.env.example` tersedia sebagai referensi konfigurasi tanpa menyertakan rahasia.
- Jangan menghapus database SQLite jika berisi data yang masih dibutuhkan.
- Pastikan kolom `isbn` memiliki batasan unik sesuai migration.
- Gunakan foreign key untuk menjaga hubungan antara buku dan penulis.
- Periksa kembali konfigurasi database sebelum menjalankan migration.
- Jangan mengunggah folder `vendor/` atau `node_modules/` jika sudah dikecualikan oleh `.gitignore`.

## 🔧 Penanganan Masalah

### Composer tidak dikenali

Periksa instalasi Composer:

```bash
composer --version
```

### PHP tidak dikenali

Periksa instalasi PHP:

```bash
php --version
```

### Database SQLite tidak ditemukan

Pastikan file database tersedia:

```text
database/database.sqlite
```

Pastikan juga `.env` menggunakan `DB_CONNECTION=sqlite`.

### Migration gagal

Periksa pesan error, konfigurasi database, urutan migration, dan definisi foreign key. Pastikan migration Author tersedia sebelum migration Book dijalankan.

### Filament tidak dapat diakses

Periksa apakah instalasi Filament selesai dan file provider panel tersedia. Pastikan panel terdaftar serta route `/admin` sesuai konfigurasi aplikasi.

### Git tidak mengunggah folder Authbook

Dari direktori repository Praktikum 6, jalankan:

```bash
git status
git add authbook/
git commit -m "Add Praktikum 6 Authbook"
git push origin main
```

Jika tidak ada perubahan untuk di-commit, periksa kembali status Git dan isi repository sebelum mencoba push ulang.

## 🚀 Pengembangan Selanjutnya

Setelah tahap setup, model, dan migration selesai, proyek Authbook dapat dikembangkan lebih lanjut melalui:

1. Membuat Filament Resource untuk Author.
2. Membuat Filament Resource untuk Book.
3. Menambahkan formulir pengelolaan penulis dan buku.
4. Menampilkan relasi Author pada data Book.
5. Menambahkan fitur pencarian dan penyaringan buku.
6. Menambahkan validasi ISBN dan input data buku.
7. Mengelola status buku tersedia atau dipinjam.
8. Menambahkan pengujian terhadap relasi model dan operasi database.

Daftar tersebut merupakan rencana pengembangan berikutnya, bukan pernyataan bahwa seluruh fitur telah dibuat dalam Pertemuan 6.

## 📌 Kesimpulan

Praktikum Pemrograman Berbasis Web Pertemuan 6 membahas pembuatan proyek Laravel, konfigurasi database SQLite, instalasi Filament, serta pengembangan model dan migration untuk data penulis dan buku.

Melalui proyek Authbook, mahasiswa mempelajari struktur dasar aplikasi Laravel, penggunaan Eloquent ORM, pengaturan atribut model, relasi one-to-many dan many-to-one, serta penggunaan foreign key dalam database.

Tahapan tersebut menjadi dasar untuk pengembangan panel administrasi dan fitur pengelolaan data buku menggunakan Filament pada tahap selanjutnya.

---

<p align="center">
  <strong>Ridwan Odi Nugroho</strong><br>
  4524210089<br>
  Teknik Informatika — Universitas Pancasila<br><br>
  <em>Praktikum Pemrograman Berbasis Web — Pertemuan 6</em>
</p>


---

## 🧪 Dokumentasi Langkah Praktikum — Bagian 1 sampai 7

Bagian ini merangkum tahapan praktikum pembuatan aplikasi Authbook berdasarkan modul Laravel dan Filament.

### BAGIAN 1 — Setup Project Laravel

- Membuat project Laravel bernama `authbook` menggunakan Composer.
- Menyiapkan konfigurasi database SQLite pada file `.env`.
- Menginstal Filament dan menyiapkan panel admin.
- Memastikan aplikasi dapat dijalankan melalui development server.

Perintah utama:

```bash
composer create-project laravel/laravel authbook
cd authbook
php artisan serve
composer require filament/filament:"^3.0"
php artisan filament:install --panels
```

### BAGIAN 2 — Membuat Model dan Database

- Membuat model `Author` beserta migration.
- Membuat model `Book` beserta migration.
- Menambahkan atribut yang diperlukan pada tabel `authors` dan `books`.
- Mengatur relasi `Author hasMany Book` dan `Book belongsTo Author`.
- Menjalankan serta memeriksa migration.

Perintah utama:

```bash
php artisan make:model Author -m
php artisan make:model Book -m
php artisan migrate
php artisan migrate:status
php artisan db:show
```

### BAGIAN 3 — Membuat Factory dan Seeder

- Membuat `AuthorFactory` dan `BookFactory` untuk data contoh.
- Mengatur `DatabaseSeeder` untuk membuat akun admin dan data buku.
- Membuat symbolic link storage untuk mendukung file cover.
- Menjalankan seeder dan memeriksa jumlah data yang dibuat.

Perintah utama:

```bash
php artisan make:factory AuthorFactory
php artisan make:factory BookFactory
php artisan storage:link
php artisan migrate:fresh --seed
php artisan tinker
```

> **Perhatian:** `php artisan migrate:fresh --seed` menghapus seluruh tabel yang ada lalu membuatnya kembali. Gunakan hanya jika data lama memang boleh dihapus.

### BAGIAN 4 — Membuat Filament Resources

- Membuat `AuthorResource` untuk mengelola data penulis.
- Membuat `BookResource` untuk mengelola data buku.
- Menyiapkan form, tabel, relasi penulis, status buku, dan upload cover.
- Menambahkan pencarian, sorting, filter, serta aksi lihat, edit, dan hapus.
- Menyiapkan halaman detail buku jika resource dibuat dengan opsi `--view`.

Perintah utama:

```bash
php artisan make:filament-resource Author --generate
php artisan make:filament-resource Book --generate --view
```

### BAGIAN 5 — Authorization dengan Policies

- Membuat `BookPolicy` untuk mengatur izin akses data buku.
- Membuat `AuthorPolicy` untuk mengatur izin akses data penulis.
- Menyesuaikan aturan izin sesuai kebutuhan aplikasi.

Perintah utama:

```bash
php artisan make:policy BookPolicy --model=Book
php artisan make:policy AuthorPolicy --model=Author
```

### BAGIAN 6 — Membuat Admin User dan Testing

- Membuat akun untuk masuk ke panel admin.
- Membuka halaman login Filament melalui `/admin/login`.
- Menguji operasi CRUD pada data buku.
- Menguji pencarian, filter status/tahun, edit, delete, bulk delete, dan halaman detail.

Perintah utama:

```bash
php artisan make:filament-user
php artisan serve
```

Contoh data untuk pengujian buku:

| Field | Contoh |
|---|---|
| ISBN | `978-0-545-01022-1` |
| Title | `Harry Potter and the Deathly Hallows` |
| Publisher | `Scholastic` |
| Year | `2007` |
| Status | `Available` |

### BAGIAN 7 — Verifikasi dan Optimasi

- Memeriksa route yang terdaftar untuk panel admin.
- Memeriksa informasi database dan status migration.
- Memeriksa jumlah data penulis dan buku.
- Memastikan relasi antara buku dan penulis dapat diakses.

Perintah utama:

```bash
php artisan route:list --path=admin
php artisan db:show
php artisan tinker
```

Di dalam Tinker, pemeriksaan dapat dilakukan dengan:

```php
use App\Models\Author;
use App\Models\Book;

Author::count();
Book::count();

$author = Author::first();
$author->books;

$book = Book::first();
$book->author;
```

---

## 📝 Tugas dan Evaluasi

### Tugas 1: Implementasi Dasar

Implementasikan langkah-langkah praktikum Bagian 1 sampai Bagian 7 dan lampirkan screenshot sebagai bukti pengerjaan berikut.

**Petunjuk menambahkan gambar ke GitHub:**

1. Buat folder `screenshots` di repository.
2. Simpan screenshot sesuai nama file yang tertera di bawah.
3. Upload folder/gambar tersebut ke GitHub.
4. Jika nama file berbeda, sesuaikan alamat gambar pada Markdown.

> **Catatan:** Area di bawah merupakan placeholder. Gambar akan tampil setelah file screenshot diunggah ke repository pada lokasi yang sesuai.

#### 1. Screenshot Admin Panel Berhasil Login

Bukti: halaman panel admin Filament setelah berhasil login.

<img width="1553" height="627" alt="image" src="https://github.com/user-attachments/assets/eb0565be-07d8-4786-893b-d7d740358ef9" />

`Tempat gambar: screenshots/tugas-1-admin-panel.png`

#### 2. Screenshot List Books dengan Data yang Ter-seed

Bukti: halaman daftar buku yang menampilkan data hasil seeder.

<img width="1018" height="725" alt="image" src="https://github.com/user-attachments/assets/f6711caf-fbd5-4491-8ab1-03e04ec3c2e2" />

`Tempat gambar: screenshots/tugas-1-list-books-seeded.png`

#### 3. Screenshot Form Create Book

Bukti: halaman form untuk menambahkan buku baru.

<img width="1018" height="745" alt="image" src="https://github.com/user-attachments/assets/c52e6d68-0b60-4698-a308-8113e2962dc0" />

`Tempat gambar: screenshots/tugas-1-create-book.png`

#### 4. Screenshot Hasil Pencarian

Bukti: halaman daftar buku setelah kata kunci pencarian dimasukkan dan hasilnya ditampilkan.

<img width="1025" height="749" alt="image" src="https://github.com/user-attachments/assets/e272e02f-1567-46e6-8d83-732d47626246" />

`Tempat gambar: screenshots/tugas-1-search-results.png`

#### 5. Screenshot Filter Aktif

Bukti: halaman daftar buku saat filter, misalnya status `Available` atau tahun `2007`, sedang diterapkan.



`Tempat gambar: screenshots/tugas-1-active-filter.png`


