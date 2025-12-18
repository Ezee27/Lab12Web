# 🔐 Praktikum 12 Autentikasi dan Session

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
---
<img width="243" height="506" alt="image" src="https://github.com/user-attachments/assets/ebc81fd8-9bf1-4546-a593-5fa194a79404" />

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
---
<img width="1072" height="351" alt="image" src="https://github.com/user-attachments/assets/59958c50-a405-48ef-8de4-4bcfa20e12ea" />

---

## 🚪 **4. Modul Logout**

Logout digunakan untuk:

* Menghapus session
* Mengarahkan user kembali ke halaman login

```php
session_destroy();
```

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
---
<img width="912" height="426" alt="image" src="https://github.com/user-attachments/assets/f6f4a7a3-cfde-4b9a-b8df-3c81b2ddf53c" />

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

---

## 🧪 **7. Pengujian Sistem**

Pengujian yang dilakukan:

1. Akses halaman artikel tanpa login → diarahkan ke login
2. Login menggunakan akun admin
3. Mengakses CRUD artikel
4. Mengubah password melalui menu profil
5. Logout dan login kembali dengan password baru

### Akses halaman artikel tanpa login → diarahkan ke login
---
<img width="1919" height="368" alt="image" src="https://github.com/user-attachments/assets/bac8d99e-9d97-4052-8190-c90e3dc1cc80" />

---

### Mengakses CRUD artikel
---
<img width="1919" height="266" alt="image" src="https://github.com/user-attachments/assets/54679e53-a050-40b0-a82e-c8b74b42b1ca" />

---

### Mengakses CRUD artikel
---
### Halaman Artikel
---
<img width="1919" height="247" alt="image" src="https://github.com/user-attachments/assets/fd1a16c6-2c4e-4958-8818-99c6f55ac8d7" />

---
### Halaman Tambah Artikel
---
<img width="1919" height="336" alt="image" src="https://github.com/user-attachments/assets/7f7c8fa2-e5bf-4aa9-b026-5f18e8e9cd38" />

---

### Halaman Profile
---
<img width="1919" height="437" alt="image" src="https://github.com/user-attachments/assets/d902e5a0-9e8b-4351-8404-2618232f7148" />

---
### Mengubah password melalui menu profil
---
password baru:
zaenal27
---
<img width="1919" height="491" alt="image" src="https://github.com/user-attachments/assets/19e49c2c-890c-41dd-bb01-62ecfc32715d" />

---
### Logout dan login kembali dengan password baru
---
Username: admin Password Baru: zaenal27
---
<img width="1919" height="342" alt="image" src="https://github.com/user-attachments/assets/7ea8bf30-089b-4c8c-9429-fc5923edbe61" />

---
### Login Berhasil
---
<img width="1919" height="278" alt="image" src="https://github.com/user-attachments/assets/09293e60-67ba-4bd1-834f-dabe7d8102b0" />

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
