# Bookshelf API
Bookshelf API adalah proyek backend sederhana yang dibangun menggunakan Hapi.js berfungsi untuk mengelola data buku. API ini memungkinkan pengguna untuk menambahkan, membaca, mengubah, dan menghapus (CRUD) data buku,serta melakukan pencarian berdasarkan status membaca (reading), status selesai (finished), dan nama buku (name).

## Cara Menjalankan Proyek
### 1. Clone atau salin proyek

    git clone <url-repo-anda>
    cd submission

### 2. Install dependencies

    npm install

### 3. Jalankan Server

    npm run start
    
Server akan berjalan di: http://localhost:9000

## Endpoint API
### 1. Menambahkan Buku (POST ```/books```)
    Body (JSON):
    {
        "name": "Buku Dicoding",
        "year": 2024,
        "author": "Dicoding Indonesia",
        "summary": "Belajar membuat REST API",
        "publisher": "Dicoding",
        "pageCount": 100,
        "readPage": 50,
        "reading": true
    }
    
### 2. Menampilkan Semua Buku (GET ```/books```)
Optional query:
- ?reading=1 → Menampilkan buku yang sedang dibaca
- ?finished=0 → Menampilkan buku yang belum selesai
- ?name=Dicoding → Mencari berdasarkan nama

### 3. Menampilkan Detail Buku (GET ```/books/{id}```)

### 4. Mengubah Data Buku (PUT ```/books/{id}```)
Body (JSON): sama seperti POST

### 5. Menghapus Buku (DELETE ```/books/{id}```)

## Validasi
- Jika ```name``` kosong → status 400
- Jika ```readPage > pageCount``` → status 400
- Jika ```id``` tidak ditemukan → status 404

## Testing
Pengujian dilakukan menggunakan Newman, yaitu Command Line Runner untuk Postman Collection. File koleksi dan environment sudah disediakan pada folder ```/test```.

Gunakan Newman untuk menjalankan Postman Collection:

    npx newman run test/"Bookshelf API Test.postman_collection.json" -e test/"Bookshelf API Test.postman_environment.json"

Hasil pengujian:

✔ 104 assertions passed

✔ Semua endpoint berfungsi dengan benar

✔ Tidak ada error

## Struktur Folder
    submission/
    │
    ├── package.json
    ├── src/
    │   ├── server.js      ← konfigurasi Hapi server
    │   ├── routes.js      ← daftar route API
    │   ├── handler.js     ← fungsi-fungsi handler untuk tiap endpoint
    │   └── books.js       ← data penyimpanan (array buku)
    │
    └── test/
        ├── Bookshelf API Test.postman_collection.json
        └── Bookshelf API Test.postman_environment.json


© 13 November 2025 Firda Humaira
