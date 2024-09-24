# Struktur API Pengelolaan Sistem

API ini mengelola beberapa modul penting dalam sistem seperti pengelolaan token JWT, admin, genre, novel, dan chapter. Setiap modul memiliki endpoint spesifik untuk mengelola berbagai entitas.

## 1. Struktur API Pengelolaan Token JWT

| Method | Path               | Body              | Keterangan                                              |
|--------|--------------------|-------------------|---------------------------------------------------------|
| POST   | `/authentications`  | Username, password | Mendapatkan akses token, refresh token, dan id_admin     |
| PUT    | `/authentications`  | Refresh token      | Memperbarui akses token                                 |
| DELETE | `/authentications`  | Refresh token      | Menghapus akses token, refresh token, dan id_admin       |

Setelah mendapatkan akses token, token harus dimasukkan dalam header saat melakukan request API lainnya:

- **Key**: `Authorization`
- **Value**: `Bearer [akses token]`

## 2. Struktur API Pengelolaan Admin

| Method | Path               | Body                        | Keterangan                                      |
|--------|--------------------|-----------------------------|-------------------------------------------------|
| GET    | `/admin/{id}`       | -                           | Menampilkan data admin berdasarkan id admin     |
| POST   | `/admin`            | Username, password, name_admin | Menambahkan data admin baru                     |
| PUT    | `/admin/{id}`       | Username, password, name_admin | Memperbarui data admin berdasarkan id admin     |
| DELETE | `/admin/{id}`       | -                           | Menghapus data admin berdasarkan id admin       |

## 3. Struktur API Pengelolaan Genre

| Method | Path                   | Body              | Keterangan                                      |
|--------|------------------------|-------------------|-------------------------------------------------|
| GET    | `/genre`               | -                 | Menampilkan semua data genre                    |
| GET    | `/genre/{id}`          | -                 | Menampilkan data genre berdasarkan id genre     |
| GET    | `/genre/{id}/novel`    | -                 | Menampilkan data novel berdasarkan id genre     |
| POST   | `/genre`               | nama_genre, id_admin | Menambahkan data genre                          |
| PUT    | `/genre/{id}`          | nama_genre, id_admin | Memperbarui data genre berdasarkan id genre     |

## 4. Struktur API Pengelolaan Novel

| Method | Path                   | Body                                    | Keterangan                                      |
|--------|------------------------|-----------------------------------------|-------------------------------------------------|
| GET    | `/novel`               | -                                       | Menampilkan semua data novel                    |
| GET    | `/novel/{id}`          | -                                       | Menampilkan data novel berdasarkan id novel     |
| POST   | `/novel`               | judul_novel, deskripsi, pengarang, penerbit, tgl_rilis, img, id_admin, id_genre | Menambahkan data novel |
| PUT    | `/novel/{id}`          | judul_novel, deskripsi, pengarang, penerbit, tgl_rilis, img, id_admin, id_genre | Memperbarui data novel berdasarkan id novel |
| DELETE | `/novel/{id}`          | -                                       | Menghapus data novel berdasarkan id novel       |

## 5. Struktur API Pengelolaan Chapter

| Method | Path                          | Body                                  | Keterangan                                      |
|--------|-------------------------------|---------------------------------------|-------------------------------------------------|
| GET    | `/chapterlist/{id_novel}`      | -                                     | Menampilkan semua chapter berdasarkan id novel  |
| GET    | `/chapter/{no_chapter}/{id_novel}` | -                                   | Menampilkan isi chapter berdasarkan no chapter dan id novel |
| POST   | `/chapter`                    | no_chapter, tgl_chapter, isi_chapter, id_admin, id_novel | Menambahkan data chapter |
| PUT    | `/chapter/{id}`               | no_chapter, tgl_chapter, isi_chapter, id_admin, id_novel | Memperbarui data chapter berdasarkan id chapter |
| DELETE | `/chapter/{id}`               | -                                     | Menghapus data chapter berdasarkan id chapter   |
