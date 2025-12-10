# Laporan Praktikum Minggu 5
Topik: Abstraction-Interface

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

---

## Tujuan
1. Memahami konsep abstraksi dalam pemrograman berorientasi objek
2. Menerapkan interface dalam desain sistem
3. Mengimplementasikan multiple inheritance melalui interface
4. Membedakan penggunaan abstract class dan interface
---

## Dasar Teori
1. Abstraksi adalah konsep menyembunyikan detail implementasi dan hanya menampilkan fungsionalitas esensial kepada pengguna.
2. Interface adalah kontrak yang berisi deklarasi method tanpa implementasi (sebelum Java 8). Semua method dalam interface bersifat abstract secara default.
3. Interface memungkinkan multiple inheritance di Java, dimana sebuah class dapat mengimplementasikan lebih dari satu interface.
4. Abstract class adalah class yang tidak dapat diinstansiasi langsung dan dapat memiliki method abstract dan konkret.
5. Polymorphism dapat dicapai melalui interface, dimana objek dari class yang berbeda dapat diperlakukan sama jika mengimplementasikan interface yang sama.
---

## Langkah Praktikum
Setup Environment: Membuka IDE (VS Code/IntelliJ) dan membuat project Java baru
Membuat Interface:
  Membuat file Pembayaran.java sebagai interface utama
  Membuat file Notifikasi.java sebagai interface tambahan
Membuat Abstract Class:
  Membuat file Transaksi.java sebagai abstract class
Implementasi Concrete Class:
  Membuat file PembayaranTunai.java
  Membuat file PembayaranKartu.java
Testing:
  Membuat file Main.java untuk menguji implementasi
  Menjalankan program dan memverifikasi output
Commit ke Git:
  git add .
  git commit -m "Implementasi abstraction dan interface"
  git push origin main
---

## Kode Program
public class MainAbstraction {
    public static void main(String[] args) {

        Payment cash = new Cash("INV-001", 100000, 120000);
        Payment ewallet = new EWallet("INV-002", 50000, "user@gmail.com", 100000);
        Payment transfer = new TransferBank("INV-003", 200000, 250000, "BRI");

        Payment[] list = { cash, ewallet, transfer };

        for (Payment p : list) {
            Receiptable r = (Receiptable) p;
            System.out.println(r.cetakStruk());
            System.out.println("Status: " + (p.prosesPembayaran() ? "BERHASIL" : "GAGAL"));
            System.out.println("--------------------------------");
        }
    }
}

---

## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2025-12-10 143410" src="https://github.com/user-attachments/assets/264f33f7-5a6a-420f-8008-9ef6644cc7b6" />

---

## Analisis
Bagaimana Kode Berjalan:
  Program dimulai dari class Main yang membuat objek dari PembayaranTunai dan PembayaranKartu
  Setiap objek meng-extend abstract class Transaksi dan meng-implement dua interface: Pembayaran dan Notifikasi
  Abstract class Transaksi menyediakan struktur dasar dan method abstract validasi() yang harus diimplementasikan subclass
  Interface Pembayaran dan Notifikasi mendefinisikan kontrak method yang harus diimplementasikan
  Polymorphism ditunjukkan dengan menyimpan objek berbeda dalam array interface yang sama

Perbedaan dengan Minggu Sebelumnya:
  Minggu 4 (Inheritance & Polymorphism): Fokus pada inheritance class tunggal dan polymorphism melalui overriding method
  Minggu 5 (Abstraction & Interface): Menggunakan multiple inheritance melalui interface dan abstraksi yang lebih ketat
  Interface memungkinkan desain yang lebih fleksibel karena class dapat mengimplementasikan banyak interface
  Abstract class cocok untuk berbagi kode antara class terkait, sedangkan interface untuk mendefinisikan kemampuan

Kendala dan Solusi:
  Kendala: Kesulitan memahami kapan menggunakan abstract class vs interface
  Solusi: Mempelajari bahwa abstract class untuk "is-a" relationship dengan shared code, interface untuk "can-do" capability

  Kendala: Error implementasi method interface
  Solusi: Memastikan semua method dari interface diimplementasikan dengan signature yang tepat

  Kendala: Desain hierarki yang kompleks
  Solusi: Membuat diagram class sebelum coding untuk memahami hubungan antar komponen
---

## Kesimpulan
1. Abstraction melalui interface dan abstract class memungkinkan desain sistem yang modular dan fleksibel
2. Interface di Java memungkinkan multiple inheritance dan mendefinisikan kontrak tanpa implementasi
3. Abstract class cocok untuk menyediakan implementasi dasar yang dapat di-extend oleh subclass
4. Penggunaan polymorphism melalui interface meningkatkan fleksibilitas dan maintainability kode
5. Kombinasi interface dan abstract class memungkinkan desain yang kuat dengan separation of concerns yang jelas
---

## Quiz
1. Apa perbedaan utama antara abstract class dan interface?
Jawaban:
  Abstract class dapat memiliki method konkret (berimplementasi) dan abstract, sedangkan interface (sebelum Java 8) hanya memiliki method abstract
  Sebuah class hanya bisa meng-extend satu abstract class, tetapi bisa meng-implement banyak interface
  Abstract class digunakan untuk "is-a" relationship dengan berbagi kode, interface untuk "can-do" capability
  Abstract class dapat memiliki constructor, sedangkan interface tidak
  Field dalam abstract class dapat berbagai access modifier, sedangkan dalam interface secara default public static final

2. Kapan sebaiknya menggunakan interface daripada abstract class?
Jawaban:
  Ketika perlu multiple inheritance
  Ketika mendefinisikan kontrak/tanpa peduli implementasi
  Ketika class tidak terkait secara hierarki tetapi memiliki kemampuan yang sama
  Ketika ingin memisahkan API dari implementasi
  Ketika ingin mencapai loose coupling dalam desain sistem

3. Apa keuntungan menggunakan polymorphism dengan interface?
Jawaban:
  Fleksibilitas: objek dari class berbeda dapat diperlakukan sama
  Extensibility: mudah menambah class baru tanpa mengubah kode yang ada
  Maintainability: kode menjadi lebih modular dan mudah di-maintain
  Testability: mudah melakukan mocking dan testing
  Loose coupling: mengurangi ketergantungan antara komponen sistem
