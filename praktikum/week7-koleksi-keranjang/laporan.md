# Laporan Praktikum Minggu 7
Topik: Koleksi Keranjang

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

---

## Tujuan
Tujuan dari praktikum ini adalah agar mahasiswa memahami konsep dasar Object Oriented Programming (OOP) khususnya class dan object, serta mampu mengimplementasikannya dalam program Java secara sederhana dan terstruktur.
---

## Dasar Teori
1. Class merupakan cetak biru (blueprint) yang mendefinisikan atribut dan metode dari suatu objek.
2. Object adalah hasil instansiasi dari sebuah class yang dapat digunakan secara nyata dalam program.
3. Atribut adalah variabel yang dimiliki oleh class.
4. Method adalah fungsi yang mendefinisikan perilaku objek.
5. Konsep class dan object membantu program menjadi lebih terstruktur dan mudah dikembangkan.
---

## Langkah Praktikum
1. Menyiapkan lingkungan pemrograman Java (JDK dan IDE).
2. Membuat file Produk.java sebagai class utama.
3. Menambahkan atribut dan method pada class Produk.
4. Membuat file MainProduk.java untuk menjalankan program.
5. Menjalankan program dan mengamati hasil output di console.

Commit ke repository dengan pesan:
---

## Kode Program
package com.upb.agripos;

public class MainCart {
    public static void main(String[] args) {
        System.out.println("Hello, I am Hari Cahyono-240202900 (Week7)");

        Product p1 = new Product("P01", "Beras", 50000);
        Product p2 = new Product("P02", "Pupuk", 30000);

        ShoppingCart cart = new ShoppingCart();
        cart.addProduct(p1);
        cart.addProduct(p2);
        cart.printCart();

        cart.removeProduct(p1);
        cart.printCart();
    }
}
---

## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2025-12-18 100048" src="https://github.com/user-attachments/assets/e9b80b31-f0ad-4339-95dd-57b0ceaf0c32" />

---

## Analisis
1. Program berjalan dengan membuat objek Produk dari class Produk.
2. Data produk diakses menggunakan method getter, sehingga atribut tetap terlindungi (enkapsulasi).
3. Dibandingkan minggu sebelumnya yang masih bersifat prosedural, pendekatan OOP membuat kode lebih rapi dan terstruktur.
4. Kendala yang dihadapi adalah kesalahan penulisan constructor, namun dapat diatasi dengan menyesuaikan parameter dengan atribut class.
---

## Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa penggunaan class dan object mempermudah pengelolaan data dan membuat program lebih modular, terstruktur, serta mudah dikembangkan untuk skala yang lebih besar.
---

## Quiz
1. Apa yang dimaksud dengan class?
Jawaban: Class adalah blueprint atau cetak biru untuk membuat objek yang berisi atribut dan method.

2. Apa perbedaan class dan object?
Jawaban: Class adalah rancangan, sedangkan object adalah wujud nyata dari class.

3. Apa fungsi enkapsulasi?
Jawaban: Untuk melindungi data agar tidak diakses langsung dari luar class.
