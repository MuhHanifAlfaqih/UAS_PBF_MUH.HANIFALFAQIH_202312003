# 📋 Aplikasi Aktivitas Harian

Aplikasi web sederhana berbasis **Node.js + Express + EJS + Prisma** untuk mencatat aktivitas harian beserta detailnya (master–detail).  
Dilengkapi dengan fitur **login**, **CRUD aktivitas**, dan **CRUD detail aktivitas**.

---

## 👤 Identitas Mahasiswa
- **Nama**: Muh. Hanif Alfaqih  
- **NIM**: (202312003)

---

## 🚀 Fitur Utama
- Login & Logout
- Dashboard
- Master Aktivitas
  - Tambah, lihat, edit, hapus aktivitas
- Detail Aktivitas (Relasi Master–Detail)
  - Tambah, edit, hapus detail aktivitas
- Konfirmasi hapus menggunakan SweetAlert2

---

## 🛠️ Teknologi yang Digunakan
- Node.js
- Express.js
- EJS (Template Engine)
- Prisma ORM
- MySQL / SQLite
- Bootstrap 5
- SweetAlert2

---

## 📂 Struktur Folder
# UAS_PBF_MUH.HANIFALFAQIH_202312003

---

## 🔗 Routing Express (Singkat)
- `/login` → halaman login
- `/dashboard` → dashboard utama
- `/aktivitas` → master aktivitas
- `/aktivitas/:id/detail` → detail aktivitas (relasi)
- `/aktivitas/tambah` → tambah aktivitas
- `/detail/edit/:id` → edit detail aktivitas

---

## 🔗 Relasi Master–Detail
- **Aktivitas** → Master
- **DetailAktivitas** → Detail
- Satu aktivitas bisa memiliki **banyak detail**
- Relasi menggunakan `aktivitasId` sebagai foreign key

---

## 🗄️ Database Schema (Prisma)
```prisma
model User {
  id        Int         @id @default(autoincrement())
  username  String
  password  String
  aktivitas Aktivitas[]
}

model Aktivitas {
  id        Int              @id @default(autoincrement())
  judul     String
  kategori  String
  tanggal   DateTime
  userId    Int
  user      User             @relation(fields: [userId], references: [id])
  detail    DetailAktivitas[]
}

model DetailAktivitas {
  id           Int        @id @default(autoincrement())
  deskripsi    String
  durasi       Int
  status       String
  aktivitasId  Int
  aktivitas    Aktivitas @relation(fields: [aktivitasId], references: [id])
}

---

⚙️ Cara Install & Menjalankan Aplikasi
1️⃣ Pastikan Node.js & npm Terpasang
Cek versi Node.js dan npm:
node -v
npm -v

2️⃣ Inisialisasi Project
Masuk ke folder project lalu jalankan:
npm init -y

3️⃣ Install Dependency Utama
npm install express ejs mysql2 express-session body-parser

4️⃣ Install dotenv
npm install dotenv

5️⃣ Install Prisma
npm install prisma --save-dev
npm install prisma@5 @prisma/client@5

6️⃣ Inisialisasi Prisma
npx prisma init
Cek versi Prisma:
npx prisma -v

7️⃣ Konfigurasi Database
Atur koneksi database di file .env
Sesuaikan dengan MySQL lokal
Contoh:
DATABASE_URL="mysql://root:@localhost:3306/db_aktivitas"

8️⃣ Migrasi Database
npx prisma migrate dev --name init

9️⃣ Jalankan Aplikasi
node app.js
Akses aplikasi melalui browser:
http://localhost:3000

---
