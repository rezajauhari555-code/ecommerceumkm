# 🛍️ UMKM Mart — Mobile E-Commerce UMKM Indonesia

**UMKM Mart** adalah aplikasi mobile e-commerce yang dirancang untuk membantu pelaku Usaha Mikro, Kecil, dan Menengah (UMKM) memasarkan produk mereka secara digital.

Aplikasi ini memungkinkan pelanggan melihat produk, mencari barang, memasukkan produk ke keranjang, dan membuat pesanan. Backend menyediakan REST API untuk autentikasi, pengelolaan produk, dan pemrosesan pesanan.

Proyek ini dikembangkan menggunakan React Native untuk frontend mobile, Node.js dan Express.js untuk backend, serta MySQL dari XAMPP sebagai database.

## 📌 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Tujuan](#-tujuan)
- [Fitur](#-fitur)
- [Teknologi](#-teknologi)
- [Arsitektur Sistem](#-arsitektur-sistem)
- [Struktur Folder](#-struktur-folder)
- [Persyaratan Sistem](#-persyaratan-sistem)
- [Instalasi Database](#-instalasi-database)
- [Menjalankan Backend](#-menjalankan-backend)
- [Pengujian API dengan Postman](#-pengujian-api-dengan-postman)
- [Menjalankan Frontend](#-menjalankan-frontend)
- [Endpoint API](#-endpoint-api)
- [Keamanan](#-keamanan)
- [Pengembangan Selanjutnya](#-pengembangan-selanjutnya)
- [Kontribusi](#-kontribusi)
- [Lisensi](#-lisensi)

## 📖 Tentang Proyek

UMKM Mart merupakan proyek pengembangan sistem informasi e-commerce berbasis mobile yang berfokus pada digitalisasi penjualan produk UMKM Indonesia.

Aplikasi ini dirancang dengan memisahkan frontend dan backend agar pengembangan, pengujian, serta pemeliharaan sistem menjadi lebih terstruktur.

Frontend berfungsi sebagai antarmuka pengguna, sedangkan backend menangani autentikasi, logika bisnis, validasi, dan komunikasi dengan database.

## 🎯 Tujuan

1. Membantu UMKM memperluas jangkauan pemasaran produk.
2. Menyediakan pengalaman belanja yang praktis melalui perangkat mobile.
3. Memudahkan pelanggan mencari dan memilih produk.
4. Mengimplementasikan autentikasi pengguna yang aman.
5. Mengelola data produk dan pesanan menggunakan MySQL.
6. Memisahkan frontend dan backend untuk mempermudah pengembangan.
7. Menguji REST API menggunakan Postman sebelum integrasi dengan frontend.

## ✨ Fitur

### 👤 Fitur Pelanggan

- Registrasi akun.
- Login dan autentikasi JWT.
- Melihat daftar produk UMKM.
- Melihat detail produk.
- Mencari produk.
- Memilih kategori produk.
- Menambahkan produk ke keranjang.
- Mengatur jumlah produk.
- Membuat pesanan.
- Melihat riwayat pesanan.
- Melihat profil pengguna.

### 🛠️ Fitur Admin

- Mengelola data produk.
- Menambahkan produk baru.
- Memperbarui informasi produk.
- Menghapus produk.
- Mengelola stok produk.
- Mengakses fungsi administrasi sesuai hak akses.

### 🔐 Fitur Keamanan

- Password di-hash menggunakan bcrypt.
- Autentikasi menggunakan JSON Web Token (JWT).
- Middleware untuk memverifikasi token.
- Pembatasan akses berdasarkan peran pengguna.
- Validasi input pada backend.
- Query database menggunakan parameter untuk mengurangi risiko SQL injection.
- Validasi harga dan stok pada proses pemesanan.

> **Catatan:** Fitur di atas merupakan target pengembangan proyek. Status implementasi setiap fitur perlu disesuaikan dengan kode yang benar-benar tersedia di repository.

## 🧰 Teknologi

| Teknologi | Fungsi |
|---|---|
| React Native | Pengembangan antarmuka aplikasi mobile |
| Expo | Menjalankan dan mengembangkan aplikasi React Native |
| TypeScript | Penulisan kode frontend dengan tipe data |
| Node.js | Runtime JavaScript untuk backend |
| Express.js | Framework REST API |
| MySQL | Database relasional |
| XAMPP | Lingkungan pengembangan database lokal |
| phpMyAdmin | Pengelolaan database melalui browser |
| MySQL2 | Koneksi backend ke MySQL |
| bcryptjs | Hashing dan verifikasi password |
| JSON Web Token | Autentikasi berbasis token |
| dotenv | Pengelolaan konfigurasi environment |
| Postman | Pengujian endpoint API |
| Git | Version control |
| GitHub | Penyimpanan repository dan kolaborasi |

## 🏗️ Arsitektur Sistem

```text
+--------------------------------+
|       MOBILE FRONTEND          |
|     React Native + Expo        |
+--------------------------------+
                |
                | HTTP Request
                | JSON Response
                v
+--------------------------------+
|          BACKEND API           |
|       Node.js + Express        |
|                                |
| - Authentication               |
| - Product Management           |
| - Order Management             |
| - JWT Middleware               |
| - Role Authorization           |
+--------------------------------+
                |
                | SQL Queries
                v
+--------------------------------+
|          MYSQL DATABASE        |
|          XAMPP MySQL           |
|                                |
| - users                        |
| - categories                   |
| - products                     |
| - orders                       |
| - order_items                  |
+--------------------------------+

+--------------------------------+
|            POSTMAN             |
|       REST API Testing         |
+--------------------------------+
                |
                v
         BACKEND API
```

Frontend dan backend dikembangkan secara terpisah. Postman digunakan untuk menguji backend sebelum API diintegrasikan dengan aplikasi mobile.

## 📂 Struktur Folder

Struktur proyek yang direncanakan:

```text
UMKM-Mart/
│
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── database.js
│   │   │
│   │   ├── controllers/
│   │   │   ├── authController.js
│   │   │   ├── productController.js
│   │   │   └── orderController.js
│   │   │
│   │   ├── middleware/
│   │   │   ├── authMiddleware.js
│   │   │   └── roleMiddleware.js
│   │   │
│   │   ├── routes/
│   │   │   ├── authRoutes.js
│   │   │   ├── productRoutes.js
│   │   │   └── orderRoutes.js
│   │   │
│   │   ├── app.js
│   │   └── server.js
│   │
│   ├── database/
│   │   └── umkm_mart.sql
│   │
│   ├── .env.example
│   └── package.json
│
├── frontend/
│   ├── app/
│   ├── components/
│   ├── services/
│   ├── types/
│   ├── assets/
│   └── package.json
│
├── .gitignore
└── README.md
```

Struktur aktual dapat berbeda sesuai implementasi dan konfigurasi Expo yang digunakan.

## 💻 Persyaratan Sistem

Sebelum menjalankan proyek, siapkan:

- [Node.js](https://nodejs.org/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [XAMPP](https://www.apachefriends.org/)
- [Postman](https://www.postman.com/)
- [Git](https://git-scm.com/)
- [Expo](https://docs.expo.dev/)

Disarankan menggunakan versi Node.js LTS yang kompatibel dengan dependensi proyek.

## 🗄️ Instalasi Database

### 1. Jalankan XAMPP

Buka XAMPP Control Panel.

Aktifkan:

- MySQL
- Apache, jika diperlukan untuk mengakses phpMyAdmin melalui instalasi XAMPP.

### 2. Buka phpMyAdmin

Akses:

```text
http://localhost/phpmyadmin
```

### 3. Buat database

Buat database dengan nama:

```sql
CREATE DATABASE umkm_mart;
```

Pilih database `umkm_mart`, kemudian impor file SQL:

```text
backend/database/umkm_mart.sql
```

File SQL harus berisi definisi tabel, foreign key, dan data contoh yang sesuai dengan implementasi backend.

## ⚙️ Menjalankan Backend

### 1. Masuk ke folder backend

Buka terminal di Visual Studio Code:

```bash
cd backend
```

### 2. Instal dependensi

```bash
npm install
```

Pastikan `package.json` sudah mendefinisikan script untuk menjalankan server.

Contoh:

```json
{
  "scripts": {
    "start": "node src/server.js",
    "dev": "nodemon src/server.js"
  }
}
```

Jika `nodemon` belum tersedia, instal sebagai dependensi pengembangan:

```bash
npm install --save-dev nodemon
```

### 3. Konfigurasi environment

Buat file `.env` di dalam folder `backend`.

Contoh konfigurasi lokal:

```env
PORT=5000

DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=
DB_NAME=umkm_mart

JWT_SECRET=GANTI_DENGAN_SECRET_ACAK_YANG_KUAT
JWT_EXPIRES_IN=1h
```

Sesuaikan konfigurasi dengan instalasi MySQL di komputer masing-masing.

Jangan mengunggah file `.env` yang berisi password database atau secret ke GitHub.

### 4. Jalankan server

```bash
npm run dev
```

Jika server berjalan dengan benar, API dapat diakses melalui:

```text
http://localhost:5000
```

Contoh endpoint pemeriksaan server:

```text
GET http://localhost:5000/api/health
```

Endpoint tersebut harus dibuat di backend agar dapat digunakan.

## 🧪 Pengujian API dengan Postman

Backend diuji menggunakan Postman sebelum diintegrasikan dengan frontend.

### 1. Registrasi pengguna

**Method:** `POST`

```text
http://localhost:5000/api/auth/register
```

Body → raw → JSON:

```json
{
  "name": "Pengguna UMKM",
  "email": "pengguna@example.com",
  "password": "ContohPasswordAman123!"
}
```

### 2. Login pengguna

**Method:** `POST`

```text
http://localhost:5000/api/auth/login
```

Body → raw → JSON:

```json
{
  "email": "pengguna@example.com",
  "password": "ContohPasswordAman123!"
}
```

Jika berhasil, backend mengembalikan token JWT sesuai format respons yang diterapkan.

### 3. Memeriksa identitas pengguna

**Method:** `GET`

```text
http://localhost:5000/api/auth/me
```

Header:

```http
Authorization: Bearer TOKEN_JWT
```

Ganti `TOKEN_JWT` dengan token yang diperoleh dari proses login.

### 4. Melihat produk

**Method:** `GET`

```text
http://localhost:5000/api/products
```

Endpoint ini digunakan untuk mengambil daftar produk.

### 5. Melihat detail produk

**Method:** `GET`

```text
http://localhost:5000/api/products/1
```

Angka `1` merupakan contoh ID produk.

### 6. Membuat pesanan

**Method:** `POST`

```text
http://localhost:5000/api/orders
```

Header:

```http
Authorization: Bearer TOKEN_JWT
Content-Type: application/json
```

Contoh body, jika format tersebut didukung backend:

```json
{
  "shipping_address": "Alamat pengiriman contoh",
  "items": [
    {
      "product_id": 1,
      "quantity": 2
    }
  ]
}
```

Backend harus menghitung harga berdasarkan data database, memvalidasi stok, dan menggunakan transaksi database untuk membuat pesanan.

### 7. Melihat riwayat pesanan

**Method:** `GET`

```text
http://localhost:5000/api/orders/my
```

Header:

```http
Authorization: Bearer TOKEN_JWT
```

Pastikan endpoint pesanan hanya mengembalikan pesanan milik pengguna yang sedang login.

> Format request dan response di atas merupakan contoh kontrak API. Sesuaikan dengan implementasi backend yang sebenarnya.

## 📱 Menjalankan Frontend

### 1. Masuk ke folder frontend

Buka terminal baru:

```bash
cd frontend
```

### 2. Instal dependensi

```bash
npm install
```

### 3. Jalankan Expo

```bash
npx expo start
```

Ikuti petunjuk Expo untuk membuka aplikasi melalui perangkat yang kompatibel atau emulator Android.

### 4. Konfigurasi alamat API

Frontend harus menggunakan alamat backend yang dapat dijangkau dari perangkat.

Contoh untuk Android Emulator standar:

```text
http://10.0.2.2:5000
```

Contoh untuk perangkat fisik dalam jaringan lokal:

```text
http://192.168.1.10:5000
```

Ganti alamat IP tersebut dengan alamat komputer yang menjalankan backend.

`localhost` pada HP menunjuk ke HP itu sendiri, bukan otomatis ke komputer.

Pastikan backend mendengarkan pada alamat jaringan yang sesuai dan firewall mengizinkan koneksi yang diperlukan.

Untuk deployment, gunakan HTTPS dan konfigurasi jaringan yang aman.

## 🔌 Endpoint API

Daftar endpoint yang direncanakan:

| Method | Endpoint | Fungsi | Akses |
|---|---|---|---|
| GET | `/api/health` | Memeriksa status server | Publik |
| POST | `/api/auth/register` | Registrasi pengguna | Publik |
| POST | `/api/auth/login` | Login pengguna | Publik |
| GET | `/api/auth/me` | Informasi pengguna aktif | Pengguna login |
| GET | `/api/products` | Daftar produk | Publik |
| GET | `/api/products/:id` | Detail produk | Publik |
| POST | `/api/products` | Menambah produk | Admin |
| PUT | `/api/products/:id` | Mengubah produk | Admin |
| DELETE | `/api/products/:id` | Menghapus produk | Admin |
| POST | `/api/orders` | Membuat pesanan | Pelanggan login |
| GET | `/api/orders/my` | Riwayat pesanan sendiri | Pelanggan login |
| GET | `/api/orders/:id` | Detail pesanan dengan pemeriksaan kepemilikan | Pengguna berwenang |

Akses aktual harus ditentukan oleh middleware backend, bukan hanya oleh tampilan frontend.

## 🔐 Keamanan

Beberapa prinsip keamanan yang diterapkan dalam pengembangan:

1. Password tidak disimpan dalam bentuk teks biasa.
2. Password di-hash menggunakan bcryptjs.
3. JWT diverifikasi oleh middleware backend.
4. Endpoint administratif hanya dapat digunakan oleh admin yang terautentikasi.
5. Input pengguna divalidasi di backend.
6. Query database menggunakan parameterized queries.
7. Harga produk dihitung dari database, bukan dipercaya dari frontend.
8. Stok divalidasi sebelum pesanan diproses.
9. Proses pembuatan pesanan dan pengurangan stok menggunakan transaksi database.
10. Secret dan kredensial tidak disimpan di repository publik.
11. Endpoint autentikasi perlu dilengkapi pembatasan percobaan login dan perlindungan yang sesuai.
12. Token disimpan menggunakan penyimpanan aman pada perangkat mobile.

Untuk penggunaan produksi, gunakan konfigurasi database dengan hak akses terbatas, HTTPS, pengelolaan secret yang benar, serta kebijakan akses database yang sesuai.

## 🚀 Pengembangan Selanjutnya

Fitur yang dapat dikembangkan:

- Integrasi pembayaran melalui payment gateway.
- Upload gambar produk.
- Dashboard admin berbasis web.
- Notifikasi pesanan.
- Pencarian dan filter produk yang lebih lengkap.
- Pengelolaan alamat pengiriman.
- Pengelolaan status pesanan.
- Laporan penjualan untuk UMKM.
- Pengujian otomatis backend.
- Deployment backend dan database ke server produksi.

Pembayaran online tidak dianggap aktif sampai integrasi, konfigurasi, dan pengujian payment gateway selesai.

## 🤝 Kontribusi

Kontribusi untuk pengembangan proyek ini dapat dilakukan melalui:

1. Fork repository.
2. Buat branch baru.
3. Lakukan perubahan kode.
4. Jalankan pengujian.
5. Buat Pull Request.

Pastikan perubahan tidak memasukkan kredensial atau data pribadi ke repository.

## 📄 Lisensi

Lisensi proyek belum ditentukan.

Tambahkan file `LICENSE` jika proyek akan dibagikan atau digunakan oleh pihak lain. Pilih lisensi yang sesuai dengan tujuan distribusi dan penggunaan proyek.

---

**UMKM Mart**   
Digitalisasi UMKM Indonesia melalui teknologi mobile dan web.
