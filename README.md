# Laporan Praktikum 6: Relasi Tabel dan Query Builder

Repositori ini berisi hasil praktikum mata kuliah Pemrograman Web 2 yang fokus pada implementasi relasi antar tabel (One-to-Many) dan penggunaan Query Builder di CodeIgniter 4.

## Informasi Mahasiswa
- **Nama:** Fajar Fawwaz Atallah
- **NIM:** 312410357
- **Kelas:** TI.24.A4
- **Dosen:** Agung Nugroho, S.Kom., M.Kom.

---

## Ringkasan Praktikum
Pada praktikum ini, dilakukan pengembangan sistem artikel dengan menambahkan fitur kategori. Fokus utama meliputi:
1. **Relasi Database**: Menghubungkan tabel `artikel` dengan tabel `kategori` menggunakan `id_kategori` sebagai Foreign Key.
2. **Query Builder & Join**: Menggunakan metode `join()` pada Model/Controller untuk mengambil data gabungan dari dua tabel.
3. **Manajemen CRUD**: Memperbarui fungsi tambah dan edit artikel agar mendukung pemilihan kategori melalui dropdown.

---

## Langkah-langkah Implementasi

### 1. Persiapan Database
Menambahkan kolom `id_kategori` pada tabel `artikel` dan membuat tabel baru bernama `kategori`.


### 2. Konfigurasi Model
Memperbarui `ArtikelModel.php` untuk mengizinkan kolom `id_kategori` masuk ke database melalui properti `$allowedFields`.

### 3. Implementasi Controller
Memperbarui `Artikel.php` dengan menambahkan `left join` pada query data, sehingga setiap artikel yang ditarik membawa informasi `nama_kategori`.

```php
$this->artikelModel->select('artikel.*, kategori.nama_kategori')
    ->join('kategori', 'kategori.id_kategori = artikel.id_kategori', 'left')
    ->paginate(10);
```

4. Pembaruan View
- Halaman Depan: Menambahkan badge kategori di atas judul artikel.
- Halaman Admin: Menambahkan kolom kategori pada tabel daftar artikel.
- Form Add/Edit: Menambahkan elemen <select> yang berisi daftar kategori dari database.

<img width="1888" height="941" alt="image" src="https://github.com/user-attachments/assets/0ae72545-571a-4966-b2be-82da025085f8" />

## A. Daftar Artikel (User)
Menampilkan daftar artikel yang sudah dilengkapi dengan label kategori (contoh: Edukasi, Hiburan, Berita).

<img width="1915" height="949" alt="image" src="https://github.com/user-attachments/assets/c168263e-ed2d-45c9-be2a-97513016115f" />

## B. Form Edit Artikel (Admin)
Menampilkan dropdown pemilihan kategori yang berfungsi menyimpan perubahan ke database.

<img width="1910" height="905" alt="image" src="https://github.com/user-attachments/assets/262d9298-fb4d-46d7-abbe-65a9c8d6de72" />

## C. Halaman Detail Artikel
Menampilkan informasi kategori pada saat artikel dibaca secara penuh.

<img width="1919" height="958" alt="image" src="https://github.com/user-attachments/assets/597a1f3f-eeba-49a0-840a-e6cea841d280" />

## D. Form Tambah Artikel (Admin)
Menampilkan Dropdown untuk memilih kategori yang berfungsi Menyimpan Kedalam Database

## E. DATABASE TABEL ARTIKEL TERHUBUNG KE TABEL KATEGORI MENGGUNAKAN ID_KATEGORI

<img width="1872" height="387" alt="image" src="https://github.com/user-attachments/assets/e47c2aa3-6c57-411a-aed4-964daccc7f3e" />

<img width="1092" height="320" alt="image" src="https://github.com/user-attachments/assets/7738966e-5083-4213-8eaf-f02f5989af0d" />
