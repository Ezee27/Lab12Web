---

# 🔐 Praktikum 12 PHP OOP – Autentikasi & Session

**Mata Kuliah:** Pemrograman Web 1
**Dosen:** Agung Nugroho
**Nama:** Zaenal Maulana Rizki
**NIM:** 312410332

---

## 📌 Pendahuluan

Praktikum 12 ini merupakan **lanjutan dari Praktikum 11 (Lab11Web)**.
Pada praktikum ini ditambahkan fitur **Autentikasi dan Session** tanpa menghilangkan
fitur routing dan CRUD artikel yang telah dibuat sebelumnya.

Fokus utama pada praktikum ini adalah:

* Login dan Logout user
* Session management
* Proteksi halaman
* Fitur Profil user
* Enkripsi password menggunakan `password_hash()`

---

## 📁 **1. Struktur Folder Lab12Web**

Struktur folder pada Praktikum 12 adalah pengembangan dari Praktikum 11 dengan
penambahan modul `user`.

```
Lab12Web/
├── .htaccess
├── config.php
├── index.php
├── class/
│   ├── Database.php
│   └── Form.php
├── module/
│   ├── artikel/
│   │   ├── index.php
│   │   ├── tambah.php
│   │   └── ubah.php
│   └── user/
│       ├── login.php
│       ├── logout.php
│       └── profile.php
└── template/
    ├── header.php
    └── footer.php
```

### 📸 Screenshot Struktur Folder (VS Code)

> *(isi screenshot struktur project di VS Code)*

---

## ⚙️ **2. Proteksi Routing & Session (index.php)**

File `index.php` dimodifikasi untuk:

* Mengaktifkan session
* Membatasi akses halaman tertentu jika belum login
* Mengarahkan user ke halaman login jika belum memiliki session

```php
session_start();
```

Dan dilakukan pengecekan:

```php
if (!isset($_SESSION['is_login'])) {
    header("Location: /Lab12Web/user/login");
    exit;
}
```

### 📸 Screenshot Kode index.php (VS Code)

> *(isi screenshot kode index.php)*

---

## 🔑 **3. Modul Login User**

Modul login digunakan untuk memverifikasi user berdasarkan:

* Username
* Password (menggunakan `password_verify()`)

Jika login berhasil, session akan dibuat:

```php
$_SESSION['is_login'] = true;
$_SESSION['username'] = $data['username'];
$_SESSION['nama'] = $data['nama'];
```

### 📸 Screenshot Halaman Login (Browser)

> *(isi screenshot halaman login)*

### 📸 Screenshot Kode login.php (VS Code)

> *(isi screenshot kode login.php)*

---

## 🚪 **4. Modul Logout**

Logout digunakan untuk:

* Menghapus session
* Mengarahkan user kembali ke halaman login

```php
session_destroy();
```

### 📸 Screenshot Kode logout.php (VS Code)

> *(isi screenshot kode logout.php)*

---

## 👤 **5. Modul Profil User**

Halaman profil menampilkan:

* Nama user
* Username

Serta menyediakan form untuk:

* Mengubah password user

Password baru akan disimpan dengan enkripsi:

```php
password_hash($password_baru, PASSWORD_DEFAULT);
```

### 📸 Screenshot Halaman Profil (Browser)

> *(isi screenshot halaman profil user)*

### 📸 Screenshot Kode profile.php (VS Code)

> *(isi screenshot kode profile.php)*

---

## 🔐 **6. Enkripsi Password**

Untuk keamanan data user, password disimpan menggunakan:

```php
password_hash()
```

Dan diverifikasi menggunakan:

```php
password_verify()
```

Dengan metode ini, password tidak disimpan dalam bentuk teks biasa di database.

### 📸 Screenshot Tabel users di phpMyAdmin

> *(isi screenshot struktur & data tabel users)*

---

## 🧪 **7. Pengujian Sistem**

Pengujian yang dilakukan:

1. Akses halaman artikel tanpa login → diarahkan ke login
2. Login menggunakan akun admin
3. Mengakses CRUD artikel
4. Mengubah password melalui menu profil
5. Logout dan login kembali dengan password baru

### 📸 Screenshot Pengujian Akses Tanpa Login

> *(isi screenshot redirect ke login)*

### 📸 Screenshot CRUD Artikel Setelah Login

> *(isi screenshot halaman artikel)*

---

## 🔑 **8. Akun Login Default**

```
Username : admin
Password : admin123
```

---

## 🎯 **9. Kesimpulan Praktikum**

Pada Praktikum 12 ini, saya berhasil:

✔ Mengimplementasikan autentikasi login dan logout
✔ Menggunakan session untuk manajemen user
✔ Melindungi halaman dari akses tanpa login
✔ Menambahkan fitur profil user
✔ Mengamankan password dengan `password_hash()`
✔ Mengembangkan project dari Praktikum 11 tanpa merusak fitur sebelumnya

Praktikum ini memberikan pemahaman dasar tentang bagaimana sistem autentikasi
dan session bekerja pada aplikasi web berbasis PHP OOP.

---
