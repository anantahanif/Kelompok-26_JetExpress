# JetExpress 
<img width="1920" height="1080" alt="Slide Deck Kelompok 26 Jet" src="https://github.com/user-attachments/assets/078e9425-f3e0-4ca7-8d01-cb51bfcc25d7" />

## 📦 Sistem Informasi Manajemen Pengiriman & Pelacakan Paket Dengan Aplikasi JetExpress

![Java](https://img.shields.io/badge/Java-17-orange?logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/GUI-Java%20Swing-blue)
![MySQL](https://img.shields.io/badge/Database-MySQL%208-4479A1?logo=mysql&logoColor=white)
![Maven](https://img.shields.io/badge/Build-Maven-C71A36?logo=apachemaven&logoColor=white)
![Arsitektur](https://img.shields.io/badge/Arsitektur-MVC%20%2B%20DAO-green)

Proyek Akhir Mata Kuliah **Pemrograman Berorientasi Objek (PBO)** dan **Sistem Basis Data (SBD)**
Program Studi Sistem Informasi, Fakultas Teknik, Universitas Mulawarman.

## SDGs : 8. Decent Work and Economic Growth & 9. Industry, Innovation and Infrastructure

<img width="1285" height="1176" alt="image" src="https://github.com/user-attachments/assets/6a49bfbb-8ed8-41f9-9292-13edf08615b5" />

---

## Daftar Isi
 
1. [Deskripsi Singkat](#1-deskripsi-singkat)
2. [Fitur Utama Program](#2-fitur-utama-program)
3. [Tech Stack](#3-tech-stack)
4. [Perancangan Sistem](#4-perancangan-sistem)
5. [Struktur Folder / Package](#5-struktur-folder--package)
6. [Penerapan 4 Pilar OOP](#6-penerapan-4-pilar-oop)
7. [Cara Penggunaan Program](#7-cara-penggunaan-program)
8. [Kontributor](#8-kontributor)
---

## 1. Deskripsi Singkat
 
**JetExpress** adalah aplikasi desktop berbasis **Java Swing** untuk mengelola operasional perusahaan
ekspedisi **Jet** di Kota Samarinda, mulai dari penerimaan paket di konter, pencatatan pengiriman,
penugasan kurir, sampai pelacakan status paket oleh pelanggan.
 
**Latar belakang.** Banyak usaha ekspedisi masih mencatat pengiriman secara manual (misalnya dengan
spreadsheet). Akibatnya pencarian data lambat, pencatatan rawan salah, dan status pengiriman sulit dipantau.
Di sisi lain, pelanggan juga kesulitan mengetahui tarif dan posisi paketnya.
 
**Solusi.** JetExpress menyimpan seluruh data (user, konter, paket, pengiriman, ongkir, pengantaran, dan
riwayat pelacakan) di database MySQL yang saling berelasi, dengan pembagian hak akses untuk **Admin**,
**Petugas Konter**, **Kurir**, dan **Pengguna Umum**. Pengguna umum dapat mengecek tarif dan melacak paket
dengan nomor resi **tanpa login**.
 
**Relevansi SDGs.**
 
| SDG | Keterkaitan |
|---|---|
| **SDG 8** — Decent Work and Economic Growth | Meningkatkan efisiensi dan produktivitas kerja petugas lewat pencatatan terstruktur dan pembagian tugas yang jelas. |
| **SDG 9** — Industry, Innovation, and Infrastructure | Mendukung digitalisasi proses bisnis ekspedisi melalui sistem informasi terintegrasi. |
 
---

## 2. Fitur Utama Program

### 🌐 Pengguna Umum (tanpa login)
- **Lacak Paket** — telusuri status dan riwayat pengiriman memakai nomor resi.
- **Cek Tarif** — hitung estimasi ongkos kirim berdasarkan jarak dan berat paket.
- **Konter Kami** — lihat daftar konter Jet beserta alamat dan kontaknya.
### 🛠️ Admin
- **Dashboard** laporan sederhana.
- **CRUD** untuk seluruh data: User, Konter, Pengiriman, Paket, Ongkir, Riwayat Pelacakan, dan Pengantaran.
- Penugasan kurir pada pengantaran, dengan pemilihan titik tujuan di **peta** (latitude dan longitude).
- Peringatan yang ramah saat data tidak bisa dihapus karena masih dipakai data lain.
### 🧾 Petugas Konter
- Kelola data **Pengiriman**, **Paket**, dan **Riwayat Pelacakan**.
- Melihat informasi **Ongkir**, **Pengantaran**, dan **Konter**.
### 🛵 Kurir
- Melihat tugas pengantaran yang diberikan.
- Memperbarui status pengantaran: `Ditugaskan` → `Dalam Perjalanan` → `Berhasil` / `Gagal`.
- Melampirkan **foto bukti** pengantaran dan catatan kurir.
### ⚙️ Fitur Teknis
- Seluruh data dari database MySQL (tidak ada data yang di-hardcode).
- Validasi input (nomor HP, koordinat, tanggal) dan pembatasan menu berdasarkan peran.
- Peta OpenStreetMap untuk memilih koordinat tujuan pengantaran.
---

<details>
<summary>Fitur Utama Program</summary>
  
1. **Multi-Role Authentication**: Akses login berbeda untuk Admin, Petugas Konter, dan Kurir.

<img width="1356" height="764" alt="image" src="https://github.com/user-attachments/assets/fa050a97-b9b4-4ef8-a586-bdc87d98c28b" />

2. **Dashboard & Laporan Operasional**: Rekapitulasi jumlah pengiriman dan pengelolaan data sistem (khusus Admin).

<img width="1359" height="762" alt="image" src="https://github.com/user-attachments/assets/0291e38f-f6c4-4c21-838b-33ce817b2545" />

3. **Manajemen Master Data (CRUD)**: Pengelolaan penuh data Konter, User, Tarif Ongkir, dan Kendaraan Kurir.

<img width="1355" height="759" alt="image" src="https://github.com/user-attachments/assets/4602aaa0-a8c7-460c-8cba-5cfd406b5083" />

4. **Transaksi Pengiriman & Paket**: Pembuatan resi pengiriman, pencatatan data pengirim/penerima, kalkulasi biaya, dan manajemen metode pembayaran (Cash, Cashless, COD).

<img width="1349" height="761" alt="image" src="https://github.com/user-attachments/assets/239d23ba-3a0d-436e-8e2a-4fe032b5214b" />

5. **Pelacakan (Tracking)**: Pembaruan dan monitoring *Riwayat Pelacakan* berdasarkan nomor resi yang dapat diakses publik.

<img width="1354" height="762" alt="image" src="https://github.com/user-attachments/assets/4966aaf7-9d8e-492b-b837-92db9c68f224" />

6. **Manajemen Pengantaran**: Pembaruan status penugasan oleh kurir di lapangan beserta unggah bukti foto pengiriman.

<img width="1357" height="759" alt="image" src="https://github.com/user-attachments/assets/1c5d0434-7dff-4ef5-99b7-777760ff4fcc" />

7. **Peta Interaktif**: Integrasi rute dan visualisasi titik koordinat latitude/longitude menggunakan library JXMapViewer2.

<img width="700" height="557" alt="image" src="https://github.com/user-attachments/assets/68dab32c-4a9f-4251-b004-39dfd54c2a62" />

</details>

---

## 3. Tech Stack
 
| Kategori | Teknologi |
|---|---|
| Bahasa | Java 17 |
| GUI | Java Swing (desktop) |
| Database | MySQL 8.0 |
| Build tool | Apache Maven |
| Driver database | MySQL Connector/J 9.3.0 (JDBC) |
| Library peta | JXMapViewer2 2.8 (OpenStreetMap) |
| Testing | JUnit Jupiter 5.10.3 |
| Arsitektur | MVC + DAO Pattern |
| IDE | Apache NetBeans |
| Tools perancangan | Oracle SQL Developer Data Modeler (ERD), draw.io (Use Case dan Flowchart), Figma (desain antarmuka), phpMyAdmin |
 
---

## Perancangan Sistem

*Silakan sesuaikan direktori path gambar Flowchart dan Use Case jika Anda menaruhnya di dalam folder khusus (misal: `assets/`)*.


<details>
<summary><b>📌 Use Case Diagram</b> (klik untuk menampilkan)</summary>

<br>

<img width="1548" height="2752" alt="JetExpress-USE CASE DIAGRAM drawio" src="https://github.com/user-attachments/assets/34d21f67-d226-4196-a4ff-d9f53f10630e" />

</details>

<details>
<summary><b>🔄 Flowchart</b> (klik untuk menampilkan)</summary>

<br>

**Menu Utama**
<img width="1652" height="1332" alt="JetExpress-JetExpress MENU UTAMA drawio" src="https://github.com/user-attachments/assets/651d883c-48e8-4f42-a613-55369805f905" />

**Menu Login**
<img width="992" height="772" alt="JetExpress- JetExpress MENU LOGIN drawio" src="https://github.com/user-attachments/assets/1a51f2a9-2104-42ed-8332-d65a8c0a5886" />

**Menu Kurir**
<img width="1142" height="1852" alt="JetExpress-JetExpress MENU KURIR drawio" src="https://github.com/user-attachments/assets/6f3ea31e-59f0-464b-83ac-503d6566407b" />

**Menu Admin**
<img width="1762" height="862" alt="JetExpress-JetExpress MENU ADMIN drawio (1)" src="https://github.com/user-attachments/assets/75be6c70-c23a-4133-bed6-9852d163e57c" />

**Menu Petugas Konter**
<img width="1472" height="842" alt="JetExpress-JetExpress MENU PETUGAS KONTER drawio" src="https://github.com/user-attachments/assets/6a73c34c-4ebe-424b-8339-083f7ba63c93" />


**Link Flowchart**: <https://app.diagrams.net/#G1ZnnL7I5e6o7-vNZJKJbzveKaD8YHyKVH>
</details>


<details>
<summary><b>🗂️ ERD Logical</b> (klik untuk menampilkan)</summary>

<br>

<img width="6203" height="4044" alt="ERD Logical_PA_Jet" src="https://github.com/user-attachments/assets/16be3d07-0545-4ff0-8025-02e04560eb79" />

</details>
  
<details>
<summary><b>🗃️ ERD Relational</b> (klik untuk menampilkan)</summary>

<br>

<img width="12295" height="5924" alt="ERD Relational_PA_Jet" src="https://github.com/user-attachments/assets/b3349a2d-7e9a-473e-858f-e3036d30f7bc" />

</details>


## Struktur Folder/Package

```text
JeteXpress_123
├── pom.xml
├── db_jetexpress_4.sql
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── mycompany
│   │   │           └── jetexpress
│   │   │               ├── main (Main class entry point)
│   │   │               ├── config (Manajemen Singleton untuk Database Connection Pooling)
│   │   │               ├── model (POJO/Entitas database: User, Admin, Kurir, Paket, dll.)
│   │   │               ├── dao (Interface DAO untuk standarisasi query)
│   │   │               ├── daoimpl (Implementasi kongkret operasi CRUD JDBC)
│   │   │               ├── controller (Logika bisnis MVC & validasi event)
│   │   │               └── view (Desain antarmuka/GUI berbasis Java Swing)
│   │   └── resources (Aset gambar, ikon, dan resi)
│   └── test (File JUnit testing)

```

## Penjelasan Penerapan 4 Pilar OOP

1. **Encapsulation (Enkapsulasi)**:
Artinya Membungkus data supaya tidak bisa diubah sembarangan dari luar. Seluruh atribut pada class `Model` (seperti `id_user`, `nama`, `no_resi`, `total_biaya`) dideklarasikan dengan *access modifier* `private`. Akses dan modifikasi data dijembatani secara aman dari luar *class* menggunakan metode *getter* dan *setter*, dengan ini data akan lebih aman, dan jika aturan berubah cukup mengubah satu tempat(geter/setter) tanpa merusak bagian lain.

3. **Inheritance (Pewarisan)**:
Artinya Class anak mewarisi sifat class induk(class lain).olehkarna itu untuk menerapkan hierarki *Supertype-Subtype* pada rancangan basis data ke dalam kelas Java. Terdapat parent class `User` yang menampung atribut umum, lalu diwariskan (`extends`) ke child class seperti `Admin`, `PetugasKonter`, dan `Kurir` yang memiliki atribut lebih spesifik (contoh: `shift_kerja` pada class Petugas Konter, `nomor_kendaraan` pada class Kurir), tidak perlu menulis ulang nama, email, dan password di tiga class cukup ditulis sekali di user.

4. **Polymorphism (Polimorfisme)**:
Artinya banyak bentuk satu perintah yang sama bisa dijalankan dengan cara berbeda tergantung siapa pelaksananya. Oleh karna itu diterapkan melalui penggunaan antarmuka (interface) pada lapisan DAO dan *Method Overriding*. Sebuah antarmuka seperti `UserDAO` mendefinisikan kontrak operasi (contoh: `insert()`, `update()`), yang kemudian diimplementasikan dan di- *override* secara spesifik oleh `UserDAOImpl`, menyesuaikan query SQL yang dibutuhkan. Semua DAO punya bentuk yang seragam jika suatu saat database diganti cukup memuat implementasi baru tanpa menggubah controller.

6. **Abstraction (Abstraksi)**:
Artinya menyembunyikan hal rumit dan hanya menampilkan yang perlu, Proses akses dan komunikasi ke basis data MySQL disembunyikan menggunakan *Interface* (lapisan DAO). Lapisan Controller (maupun View) hanya memanggil metode dari interface DAO dan tidak perlu mengetahui detail kompleksitas query, koneksi `ResultSet`, atau penanganan `SQLException` yang terjadi di balik layar.

## Cara Penggunaan Program

1. **Persiapan Database**:
* Buka XAMPP/Laragon dan jalankan layanan MySQL.
* Buat database baru dengan nama `jetexpress`.
* Lakukan proses *import* lalu pilih file `db_jetexpress_4.sql` yang telah disediakan.


2. **Menjalankan Program**:
* Buka *source code* (folder `JeteXpress_123`) di Apache NetBeans.


* Tunggu hingga proses *Resolve Dependencies* Maven selesai untuk mengunduh driver MySQL dan JXMapViewer2.


* Jalankan program melalui file utama (`main.Main`).




3. **Autentikasi**:
* Gunakan email dan password yang terdaftar di dalam tabel `user` untuk login.


* Pastikan Anda memilih Role (*Admin / Petugas Konter / Kurir*) yang tepat sesuai dengan data akun Anda.





### Tampilan Antarmuka (GUI)

![Tampilan 1](Screenshot 2026-11-06 234352.png)
![Tampilan 2](Screenshot 2026-11-06 234338.png)
![Tampilan 3](Screenshot 2026-11-06 234320.png)
