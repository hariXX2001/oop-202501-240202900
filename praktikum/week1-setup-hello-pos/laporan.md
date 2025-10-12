# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: [Tuliskan judul topik, misalnya "Class dan Object"]

## Identitas
- Nama  : [Hari Cahyono]
- NIM   : [240202900]
- Kelas : [3 IKKA]

---

## Tujuan
mampu memahami tiga paradigma utama pemrograman: prosedural, OOP, dan fungsional.
mampu membandingkan kelebihan dan kekurangan tiap paradigma.
mampu membuat contoh program sederhana menggunakan ketiga paradigma tersebut.
mampu melakukan setup awal proyek Java untuk sistem Agri-POS.

## Dasar Teori
Paradigma pemrograman adalah pendekatan atau cara berpikir dalam menyusun program.
Paradigma prosedural berfokus pada urutan langkah-langkah atau perintah yang dijalankan secara berurutan.
Paradigma OOP (Object-Oriented Programming) memandang program sebagai kumpulan objek yang memiliki atribut dan method.
Paradigma fungsional berfokus pada fungsi matematika dan transformasi data tanpa mengubah data asli (immutability).
Dalam konteks aplikasi POS (Point of Sale), OOP memudahkan pengembangan karena dapat memodelkan entitas nyata seperti Produk, Transaksi, dan Pembayaran.

## Langkah Praktikum
Melakukan setup lingkungan pengembangan:
Menginstall JDK, IDE (IntelliJ IDEA), Git, dan PostgreSQL.
Membuat folder proyek: oop-pos-2310112345.
Membuat struktur direktori src/main/java/com/upb/agripos/.
Membuat tiga program “Hello POS World” dengan paradigma berbeda:
HelloProcedural.java
HelloOOP.java
HelloFunctional.java
Menjalankan ketiga program untuk memastikan hasilnya sesuai.
Membuat commit Git dengan pesan:
week1-setup-hello-pos
Menyimpan hasil screenshot ke folder praktikum/week1-setup-hello-pos/screenshots/hasil.png.

## Kode Program
public class HelloProcedural {
   public static void main(String[] args) {
      String nim = "2310112345";
      String nama = "Budi Santoso";
      String[] produk = {"Beras", "Pupuk", "Benih"};
      int[] harga = {10000, 15000, 12000};
      int total = 0;

      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      for (int i = 0; i < produk.length; i++) {
         System.out.println("- " + produk[i] + ": " + harga[i]);
         total += harga[i];
      }
      System.out.println("Total harga semua produk: " + total);
   }
}
class Produk {
   String nama;
   int harga;

   Produk(String nama, int harga) {
      this.nama = nama;
      this.harga = harga;
   }
}

public class HelloOOP {
   public static void main(String[] args) {
      String nim = "2310112345";
      String namaMhs = "Budi Santoso";

      Produk[] daftar = {
         new Produk("Beras", 10000),
         new Produk("Pupuk", 15000),
         new Produk("Benih", 12000)
      };

      int total = 0;
      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + namaMhs);
      System.out.println("Daftar Produk:");
      for (Produk p : daftar) {
         System.out.println("- " + p.nama + ": " + p.harga);
         total += p.harga;
      }
      System.out.println("Total harga semua produk: " + total);
   }
}
import java.util.*;
import java.util.stream.*;

public class HelloFunctional {
   public static void main(String[] args) {
      String nim = "2310112345";
      String nama = "Budi Santoso";
      List<String> produk = Arrays.asList("Beras", "Pupuk", "Benih");
      List<Integer> harga = Arrays.asList(10000, 15000, 12000);

      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      IntStream.range(0, produk.size())
         .forEach(i -> System.out.println("- " + produk.get(i) + ": " + harga.get(i)));

      int total = harga.stream().mapToInt(Integer::intValue).sum();
      System.out.println("Total harga semua produk: " + total);
   }
}


## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2025-10-10 210057" src="https://github.com/user-attachments/assets/5af5cac8-ae26-4b6d-b306-10f4c6f90631" />

## Analisis
Ketiga program menghasilkan output yang sama, namun dengan pendekatan kode berbeda.
Prosedural: langsung menjalankan perintah secara berurutan, mudah dipahami namun sulit dikembangkan.
OOP: membagi kode menjadi class dan objek, lebih rapi dan mudah diperluas.
Fungsional: menggunakan ekspresi lambda dan stream untuk memproses data dengan cara yang singkat dan efisien.
Kendala: setup awal IDE dan struktur folder agak rumit, tapi bisa diatasi dengan mengikuti langkah panduan setup dengan teliti.

## Kesimpulan
Paradigma pemrograman menentukan cara berpikir dalam menulis program.
Untuk aplikasi besar seperti Agri-POS, OOP lebih unggul karena lebih mudah dipelihara dan dikembangkan.
Paradigma fungsional membantu menulis kode yang lebih ringkas dan bebas dari efek samping.
Dengan memahami tiga paradigma ini, mahasiswa dapat memilih pendekatan yang paling sesuai untuk setiap jenis proyek.

## Quiz
1.Apakah OOP selalu lebih baik dari prosedural?
Jawaban: Tidak selalu. Untuk program kecil, paradigma prosedural bisa lebih sederhana dan efisien. OOP lebih unggul jika proyek berskala besar atau kompleks.

2.Kapan functional programming lebih cocok digunakan dibanding OOP atau prosedural?
Jawaban: Ketika kita ingin memproses data besar secara paralel, menghindari efek samping, dan menulis kode singkat menggunakan fungsi murni atau lambda expression.

3.Bagaimana paradigma (prosedural, OOP, fungsional) memengaruhi maintainability dan scalability aplikasi?
Jawaban:
Prosedural: sulit di-maintain jika program membesar.
OOP: mudah dikembangkan karena modular.
Fungsional: mudah diuji dan minim bug karena tidak ada perubahan data langsung.

4.Mengapa OOP lebih cocok untuk mengembangkan aplikasi POS dibanding prosedural?
Jawaban: Karena OOP bisa memodelkan entitas nyata seperti Produk dan Transaksi sebagai objek, sehingga kode lebih mudah dipahami dan dikembangkan.

5.Bagaimana paradigma fungsional dapat membantu mengurangi kode berulang (boilerplate code)?
Jawaban: Dengan menggunakan fungsi lambda dan stream API, banyak operasi data dapat ditulis hanya dalam satu baris tanpa membuat loop atau variabel tambahan.
