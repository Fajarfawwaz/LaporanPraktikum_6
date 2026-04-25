# Laporan Praktikum 6: Relasi Tabel dan Query Builder

Repositori ini berisi hasil praktikum mata kuliah Pemrograman Web 2 yang fokus pada implementasi relasi antar tabel (One-to-Many) dan penggunaan Query Builder di CodeIgniter 4.

## Informasi Mahasiswa
* **Nama:** Fajar Fawwaz Atallah
* **NIM:** 312410357
* **Kelas:** TI.24.A4
* **Dosen:** Agung Nugroho, S.Kom., M.Kom.

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

### 4. Pembaruan View

- Halaman Depan : Menambahkan Badge Kategoori di atas judul artikel
- Halaman Admin : Menambahkan Dropdown Kategori Pada Tabel Daftar Artikel ( ADD ARTIKEL DAN EDIT ARTIKEL )
- Form Add Atau Edit :  Menambahkan Element ``` <sellect> ``` yang berisi daftar kategori dari database 

--- 

### Hasil Praktikum

### A. Dashboard Admin (Daftar Artikel)

## Menampilkan tabel manajemen artikel pada sisi admin.

<img width="1919" height="945" alt="image" src="https://github.com/user-attachments/assets/ac9bceb2-aa69-49cd-a127-fa881e4c981e" />

### B. Daftar Artikel (User Interface)

## Menampilkan daftar artikel yang sudah dilengkapi dengan label kategori.

<img width="1917" height="936" alt="image" src="https://github.com/user-attachments/assets/01c34485-dae8-47ab-bcb0-6d490318ca14" />

### C. Form Tambah & Edit Artikel

## Implementasi dropdown pemilihan kategori untuk proses simpan dan perbarui data ke database.

# Tampilan Dropdown DI Tambah Artikel : 

<img width="1707" height="942" alt="image" src="https://github.com/user-attachments/assets/619ea05e-a336-45cb-8153-6e13e33ec722" />

# Tampilan Dropdown Di Edit Artikel : 

<img width="1919" height="940" alt="image" src="https://github.com/user-attachments/assets/f7353d12-8d52-41cb-a5b8-9e8a1cf2f1d9" />

### D. Halaman Detail Artikel

## Menampilkan informasi kategori secara spesifik pada saat artikel dibaca secara penuh.

<img width="1919" height="950" alt="image" src="https://github.com/user-attachments/assets/e15ec1f9-bac0-45a0-ad9a-603879661e31" />

### E. Struktur Database (Relasi Tabel)

## Tabel artikel telah terhubung ke tabel kategori menggunakan id_kategori.

# Tabel Database Kategori : 

<img width="1191" height="355" alt="image" src="https://github.com/user-attachments/assets/f3522a75-2f15-4e6e-9b8d-b6ed3b3f43e0" />

# Tabel Database Artikel : 

<img width="1898" height="339" alt="image" src="https://github.com/user-attachments/assets/1523c235-b6e2-4528-a794-f3e6a24df356" />

---

© 2026 Fajar Fawwaz Atallah - 312410357 - I241D - Universitas Pelita Bangsa
