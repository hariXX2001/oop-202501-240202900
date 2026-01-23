# Laporan Praktikum Minggu 10
Topik: pattern-testing

## Identitas
- Nama  : Hari cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

---

## Tujuan
Mahasiswa mampu mengimplementasikan pola arsitektur MVC (Model-View-Controller) sederhana, memahami fungsi masing-masing komponen, serta menerapkan prinsip enkapsulasi menggunakan getter dan kata kunci this pada Java.
---

## Dasar Teori
1. MVC Pattern: Memisahkan logika data (Model), tampilan (View), dan penghubung keduanya (Controller) agar kode lebih terorganisir.
2. Enkapsulasi: Melindungi data dengan akses private dan menyediakan akses melalui metode public (getter).
3. Keyword this: Digunakan untuk merujuk pada variabel instance saat terjadi shadowing (nama parameter sama dengan nama variabel class).
4. Instansiasi: Proses pembuatan objek dari blueprint (class) agar bisa digunakan di memori.
---

## Langkah Praktikum
1. Membuat struktur package yang rapi: model, view, dan controller.
2. Menyusun class Product sebagai Model untuk menyimpan data kode dan nama produk.
3. Membuat class ConsoleView untuk menangani logika output ke layar.
4. Menghubungkan Model dan View melalui class ProductController.
5. Mengeksekusi seluruh logika melalui AppMVC.java sebagai entry point.
6. Melakukan debugging pada kesalahan inisialisasi variabel dan getter.
---

## Kode Program
// File: Product.java (Model)
public class Product {
    private String code;
    private String name;

    public Product(String code, String name) {
        this.code = code; // Menggunakan 'this' agar data tersimpan
        this.name = name;
    }

    public String getCode() { return code; }
    public String getName() { return name; }
}

// File: AppMVC.java (Main)
public static void main(String[] args) {
    Product product = new Product("P01", "Pupuk Organik");
    ConsoleView view = new ConsoleView();
    ProductController controller = new ProductController(product, view);
    controller.showProduct();
}
---

## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2026-01-23 170047" src="https://github.com/user-attachments/assets/139be8d8-11e3-4f07-8b79-3436786315e7" />

---

## Analisis
1. Cara Kerja Kode: AppMVC membuat objek data (Product) dan tampilan (View). Keduanya dimasukkan ke Controller. Saat showProduct() dipanggil, Controller mengambil data dari Product lewat getter lalu mengirimnya ke View untuk dicetak.
2. Perbedaan: Minggu ini kode jauh lebih modular. Data tidak langsung dicetak di kelas utama, melainkan dipisah sesuai fungsinya (MVC), mempermudah pengembangan ke depan.
3. Kendala & Solusi:
   3.1 NullPointerException: Terjadi karena lupa menginisialisasi variabel di constructor Controller. Solusi: Menambahkan this.variable = parameter.
   3.2 Output Null: Terjadi karena shadowing di class Product dan getter yang mengembalikan null. Solusi: Menggunakan kata kunci this di constructor dan memperbaiki return value pada getter.
---

## Kesimpulan
Penerapan pola MVC membuat kode lebih bersih dan profesional. Penggunaan kata kunci this sangat krusial dalam Java untuk memastikan data dari parameter constructor benar-benar masuk ke dalam variabel objek, sehingga data tidak bernilai null saat diakses.
---

## Quiz
1. Apa fungsi Controller dalam MVC?
   Jawaban: Controller bertindak sebagai jembatan yang mengatur aliran data dari Model ke View dan sebaliknya.

2. Mengapa variabel di Model diset private?
   Jawaban: Untuk keamanan data (enkapsulasi), sehingga data hanya bisa diubah atau dibaca melalui metode yang diizinkan (getter/setter).
