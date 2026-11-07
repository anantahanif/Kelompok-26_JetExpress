<img width="1920" height="1080" alt="Slide Deck Kelompok 26 Jet" src="https://github.com/user-attachments/assets/078e9425-f3e0-4ca7-8d01-cb51bfcc25d7" />

# JetExpress 
## 📦 Sistem Informasi Manajemen Pengiriman & Pelacakan Paket Dengan Aplikasi JetExpress

## SDGs : 8. Decent Work and Economic Growth & 9. Industry, Innovation and Infrastructure

<img width="1285" height="1176" alt="image" src="https://github.com/user-attachments/assets/6a49bfbb-8ed8-41f9-9292-13edf08615b5" />

---


### Kontributor
* Alya Hauranisa Nugroho (25019116005)
* Annisa Nayzhua Febriyani (25019116013)
* Ananta Hanif Fidzya Pratama (25019116023)
* Muhammad Risky Alpianur (25019116101)

## Deskripsi Singkat

JetExpress adalah Sistem Informasi Manajemen Pengiriman dan Pelacakan Paket berbasis desktop. Aplikasi ini dirancang untuk memfasilitasi proses bisnis ekspedisi, mulai dari pencatatan paket, pengelolaan tarif ongkos kirim, penugasan kurir, hingga pelacakan riwayat rute secara *real-time*. Dikembangkan menggunakan Java Swing dengan pola arsitektur MVC (Model-View-Controller) dan metode DAO (Data Access Object) Pattern untuk memastikan struktur kode yang *scalable* dan terorganisasi dengan baik, serta mengimplementasikan desain tata letak UI menggunakan FlatLaf.

## Fitur Utama Program

1. **Multi-Role Authentication**: Akses login berbeda untuk Admin, Petugas Konter, dan Kurir.

<img width="1354" height="761" alt="image" src="https://github.com/user-attachments/assets/1b70a70f-2caf-4a98-b600-153d94e2a84f" />

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


## Tech Stack

* **Bahasa Pemrograman**: Java 

* **Database**: MySQL

* **Arsitektur**: MVC (Model-View-Controller) & DAO (Data Access Object)
* **Framework/Library**:
* **GUI Library**: Java Swing
* **UI Library**: FlatLaf 
* **Map Library**: JXMapViewer2 v2.8


* JUnit 5 v5.10.3 (Unit Testing)




* **Build Tool & IDE**: Maven, Apache NetBeans



## Perancangan Sistem

*Silakan sesuaikan direktori path gambar Flowchart dan Use Case jika Anda menaruhnya di dalam folder khusus (misal: `assets/`)*.

* **Use Case Diagram**: 
* **Flowchart**: 
* **ERD Logical**: ![ERD Logical](ERD Logical_PA_Jet.jpg)
* **ERD Relational**: ![ERD Relational](ERD Relational_PA_Jet.jpg)

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
