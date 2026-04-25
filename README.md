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

<img width="1919" height="958" alt="Screenshot 2026-04-25 115844" src="https://github.com/user-attachments/assets/9ae284cf-cfe9-4fdd-8461-00655bd88610" />
