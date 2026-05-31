# Smart Parking System

Sistem manajemen parkir berbasis web menggunakan PHP dan CodeIgniter 4.

Project ini dibuat untuk membantu proses pengelolaan parkir menjadi lebih terstruktur, digital, dan mudah dimonitor oleh admin maupun pengguna.

---

# Features

## Authentication

* Login
* Register
* Logout
* Session Authentication
* Multi-role Access (Admin & User)

## Admin Features

* Dashboard statistik
* Manajemen slot parkir
* Manajemen user
* Approval booking
* Cancel booking
* Laporan transaksi
* Export laporan CSV
* Pengaturan tarif parkir

## User Features

* Booking slot parkir
* Melihat slot tersedia
* Membatalkan booking
* Riwayat booking
* Update profile

---

# Tech Stack

| Technology    | Description                  |
| ------------- | ---------------------------- |
| PHP           | Backend Programming Language |
| CodeIgniter 4 | PHP Framework                |
| MySQL         | Database                     |
| Bootstrap     | Frontend Styling             |
| HTML/CSS      | User Interface               |
| JavaScript    | Frontend Interaction         |
| Composer      | Dependency Management        |

---

# Project Structure

```bash
smartparking/
│
├── app/
│   ├── Config/
│   ├── Controllers/
│   │   ├── Admin/
│   │   └── User/
│   ├── Filters/
│   ├── Models/
│   └── Views/
│
├── public/
├── writable/
├── vendor/
├── .env
├── composer.json
└── spark
```

---

# Architecture

Project menggunakan konsep MVC (Model View Controller).

## Model

Mengelola database dan data aplikasi.

## View

Menampilkan antarmuka pengguna.

## Controller

Mengatur logika aplikasi dan komunikasi antara Model dan View.

Karena mencampur query database, HTML, dan logika bisnis dalam satu file adalah cara tercepat menciptakan penderitaan maintenance.

---

# Authentication & Authorization

Project menggunakan:

* Session Authentication
* Role-based Access Control
* Password Hashing
* Auth Filter

## Roles

| Role  | Access            |
| ----- | ----------------- |
| Admin | Full Access       |
| User  | Booking & History |

---

# Application Routes

## Auth Routes

```php
/login
/register
/logout
```

## Admin Routes

```php
/admin/dashboard
/admin/slots
/admin/users
/admin/bookings
/admin/reports
```

## User Routes

```php
/user/dashboard
/user/booking
/user/history
/user/profile
```

---

# Controllers

## Admin Controllers

| Controller    | Function              |
| ------------- | --------------------- |
| Dashboard.php | Dashboard admin       |
| Slots.php     | Manajemen slot parkir |
| Users.php     | Manajemen user        |
| Bookings.php  | Approval booking      |
| Reports.php   | Laporan & tarif       |

## User Controllers

| Controller    | Function       |
| ------------- | -------------- |
| Dashboard.php | Dashboard user |
| Booking.php   | Booking parkir |
| Profile.php   | Profile user   |

## Auth Controller

| Controller | Function         |
| ---------- | ---------------- |
| Auth.php   | Login & register |

---

# Database Design

## users

| Field    | Type    |
| -------- | ------- |
| id       | int     |
| name     | varchar |
| email    | varchar |
| password | varchar |
| role     | varchar |

---

## parking_slots

| Field       | Type    |
| ----------- | ------- |
| id          | int     |
| slot_number | varchar |
| status      | varchar |

---

## bookings

| Field          | Type     |
| -------------- | -------- |
| id             | int      |
| user_id        | int      |
| slot_id        | int      |
| vehicle_number | varchar  |
| start_time     | datetime |
| end_time       | datetime |
| total_price    | decimal  |
| status         | varchar  |

---

## tariff

| Field          | Type    |
| -------------- | ------- |
| id             | int     |
| price_per_hour | decimal |

---

# Installation

## 1. Clone Repository

```bash
git clone https://github.com/username/smartparking.git
```

---

## 2. Masuk ke Folder Project

```bash
cd smartparking
```

---

## 3. Install Dependency

```bash
composer install
```

---

## 4. Konfigurasi Environment

Copy file:

```bash
env .env
```

Lalu ubah konfigurasi database:

```env
CI_ENVIRONMENT = development

app.baseURL = 'http://localhost:8080/'

 database.default.hostname = localhost
 database.default.database = smartparking
 database.default.username = root
 database.default.password =
 database.default.DBDriver = MySQLi
```

---

## 5. Import Database

Import file database ke MySQL menggunakan:

* phpMyAdmin
* MySQL CLI
* HeidiSQL

Nama database:

```sql
smartparking
```

---

## 6. Jalankan Project

```bash
php spark serve
```

Akses browser:

```text
http://localhost:8080
```

---

# Booking Flow

```text
User Login
    ↓
Pilih Slot Parkir
    ↓
Input Kendaraan
    ↓
Pilih Durasi
    ↓
Booking Disimpan
    ↓
Admin Approval
    ↓
Slot Menjadi Occupied
```

---

# Reports

Admin dapat:

* Melihat laporan transaksi
* Melihat total pendapatan
* Export CSV
* Mengatur tarif parkir

Export laporan:

```text
parking_report_YYYY-MM-DD.csv
```

Karena spreadsheet adalah agama kedua dunia administrasi.

---

# Security

Fitur keamanan yang digunakan:

* Password Hashing
* Session Authentication
* Route Protection
* Role Validation
* Auth Filter

Password menggunakan:

```php
password_hash()
```

---

# Future Improvements

Pengembangan yang dapat dilakukan:

* QR Code Parking
* Payment Gateway
* Realtime Monitoring
* IoT Sensor Integration
* Mobile Application
* Notification System
* Realtime WebSocket
* CCTV Integration

---

---

# Default Accounts

## Admin

```text
Email    : admin@smarkparking.com
Password : admin123
```

## User

```text
Email    : user@gmail.com
Password : user123
```
---

# License

This project is for educational and learning purposes.

---

# Author

Developed by:

```
KELOMPOK 2
```

---

# Conclusion

Smart Parking System berhasil dibangun menggunakan CodeIgniter 4 dengan implementasi:

* Authentication system
* Multi-role management
* Parking booking system
* Report management
* CSV export
* Dashboard analytics

Karena project CRUD biasa sudah terlalu banyak. Minimal ini punya alur bisnis yang benar-benar dipakai dunia nyata.
