# JetExpress — JeteXpress_123 (Aktor Admin, Petugas Konter & Petugas Kurir)

Proyek kuliah pengiriman paket **JetExpress Samarinda** — Java Swing
(NetBeans GUI Builder) + Maven + MySQL, arsitektur **MVC + pola DAO**.

## Isi Proyek

```
JeteXpress_123/
├── pom.xml                  ← Java 17, MySQL Connector/J 9.3, JXMapViewer 2.8
└── src/main/java/
    ├── main/Main.java       ← titik masuk aplikasi
    ├── config/              ← KoneksiDatabase (JDBC, singleton)
    ├── model/               ← 10 POJO + interface BarisTabel
    ├── dao/                 ← BaseDAO (abstract) + 10 DAO (PreparedStatement)
    ├── controller/          ← 9 controller (logika bisnis + validasi)
    ├── util/                ← InputHelper, FilterNomorHp (awalan 08),
    │                          HakAkses (abstract) + 3 subclass role,
    │                          NavigasiHalaman (interface), Sesi,
    │                          TemaJetExpress, DatePickerKalender,
    │                          ValidasiKoordinat, KonversiWaktu, TeksPetunjuk
    ├── image/               ← ImageManager: foto bukti pengantaran kurir
    └── view/                ← 30 JPanel + MainFrame + PanelPeta (JXMapViewer)
```

## Cara Menjalankan (NetBeans)

1. **Import database**: buat database `jetexpress` lalu import
   `db_jetexpress.sql`.
2. **Cek kredensial** MySQL pada `config/KoneksiDatabase.java`
   (bawaan: `root` / password kosong, port 3306).
3. Buka folder proyek di NetBeans (**File → Open Project**), tunggu Maven
   mengunduh dependensi, lalu **Run** `main.Main`.
4. **Peta OpenStreetMap butuh koneksi internet** (tile dari
   tile.openstreetmap.org). Foto bukti tersimpan di folder `bukti/`
   di samping folder proyek (dibuat otomatis).

## Akun Uji (role diambil otomatis dari database)

| Role | Email | Password | Beranda setelah login |
|---|---|---|---|
| Admin | `siti.mahendra@jetexpress.co.id` | `adminkeren47` | MenuAdmin |
| Petugas Konter | `nia.rahman@jetexpress.co.id` | `petugasterbaik83` | MenuKelolaPengiriman |
| Kurir | `linda.noor@jetexpress.co.id` | `kurirjago38` | LihatPengantaran |

## Fitur Utama

| Fitur | Keterangan |
|---|---|
| **Login berbasis role** | Role dibaca dari tabel `user` (bukan ComboBox). Admin → MenuAdmin, Petugas Konter → MenuKelolaPengiriman, Kurir → LihatPengantaran. Hak akses tiap pindah halaman diperiksa objek `HakAkses` (abstract class + 3 subclass); halaman di luar wewenang ditolak dengan pesan dan dialihkan ke beranda role. |
| **Nomor HP otomatis 08** | Kolom No. HP pengirim & penerima pada 4 form pengiriman memakai `FilterNomorHp`: terisi `08` saat form dibuka, hanya menerima angka, awalan 08 tidak bisa dihapus, maksimal 13 digit; validasi lengkap dijalankan lagi sebelum simpan. |
| **Form Ubah menampilkan data lama** | Semua form ubah (pengiriman admin & konter, pengantaran admin, status pengantaran kurir, kurir & petugas konter) mengambil ulang data terbaru dari database berdasarkan ID/resi yang dipilih — termasuk pilihan ComboBox, tanggal, dan foto bukti. |
| **Reset form** | Form Tambah selalu kosong (HP kembali `08`) saat dibuka; tombol Batal mengosongkan isian setelah konfirmasi; refresh-on-show di MainFrame memuat ulang data setiap halaman ditampilkan. |
| **Scroll bar semua halaman** | Setiap halaman dibungkus `JScrollPane` di MainFrame — scrollbar muncul hanya bila diperlukan; desain panel tidak diubah. |
| **Foto bukti pengantaran** | Package `image` (`ImageManager`): JFileChooser JPG/JPEG/PNG, maks 2 MB, validasi isi berkas, disalin ke `bukti/` dengan nama unik, pratinjau lewat dialog, path relatif disimpan ke kolom `pengantaran.bukti_foto`. Di form Ubah Status: klik dua kali kolom bukti foto = pilih foto baru / lihat pratinjau foto tersimpan. |
| **InputHelper** | Validasi kosong, angka, desimal, HP (08), email, resi (JE+8), koordinat, berat 0–50 kg, tanggal/waktu, password min 6, konter/ongkir dipilih; semua dijalankan sebelum CRUD. |
| **MVC + DAO + OOP** | View → Controller → DAO → MySQL. Semua SQL `PreparedStatement`. OOP: encapsulation (model), inheritance & abstraction (`BaseDAO<T>` abstract, `HakAkses` abstract), interface (`NavigasiHalaman`, `BarisTabel`) yang benar-benar dipakai, polymorphism & overloading (`isiDataUser(Object[])`/`isiDataUser(int)`, `ambilAngka`), association antar model (Pengiriman↔Paket↔Konter↔Ongkir↔Pengantaran↔RiwayatPelacakan). |
| **Tombol semuanya berfungsi** | Tambah/Simpan/Ubah/Hapus (dengan konfirmasi)/Cari/Refresh (ambil ulang dari DB, tanpa duplikasi)/Batal/Kembali/Login/Logout + seluruh navigasi sidebar admin, konter, dan kurir. Tidak ada handler kosong. |
| **Peta JXMapViewer** | Tambah/Ubah Data Pengantaran: klik peta mengisi koordinat; koordinat lama tampil kembali saat form ubah dibuka. |
| **Kalender** | Semua field tanggal memakai DatePickerKalender berbahasa Indonesia sesuai tipe kolom (DATE/DATETIME). |
