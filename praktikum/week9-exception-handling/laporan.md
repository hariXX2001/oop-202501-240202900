# Laporan Praktikum Minggu 9 (week 9)
Topik: ["Exception-Handling"]

## Identitas
- Nama  : [HARI CAHYONO]
- NIM   : [240202900]
- Kelas : [3 IKKA]

---

## Tujuan
Tujuan dari praktikum minggu sembilan ini adalah agar mahasiswa memahami konsep dasar Exception Handling dalam Java, mampu membedakan antara checked dan unchecked exception, serta mampu mengimplementasikan try-catch, throw, dan throws untuk menangani kesalahan runtime dalam program.
---

## Dasar Teori
1. Exception adalah kejadian yang mengganggu aliran normal program.
2. Checked Exception harus ditangani dengan try-catch atau dideklarasikan dengan throws (contoh: IOException).
3. Unchecked Exception biasanya berasal dari Runtime (contoh: ArithmeticException, NullPointerException).
4. try-catch digunakan untuk menangkap dan menangani exception.
5. throw digunakan untuk melemparkan exception secara manual.
6. throws digunakan dalam deklarasi method untuk menunjukkan bahwa method dapat melemparkan exception.
7. finally blok akan selalu dieksekusi, baik ada exception maupun tidak.
---

## Langkah Praktikum
1. Setup: Membuat project Java baru di IntelliJ IDEA dengan package com.upb.agripos.week9.
Coding:
 - Membuat class Product dengan atribut: code, name, harga, stok.
 - Membuat class ShoppingCart dengan method addProduct yang dapat melemparkan custom exception.
 - Membuat custom exception class: InvalidQuantityException.
 - Membuat class MainExceptionDemo untuk menguji exception handling.
2. Run: Menjalankan program dan memverifikasi output sesuai dengan yang diharapkan.
3. Commit Message: "Week9: Implementasi Exception Handling dengan Custom Exception"
---

## Kode Program
// File: Product.java
package com.upb.agripos.week9;

public class Product {
    private String code;
    private String name;
    private double harga;
    private int stok;

    public Product(String code, String name, double harga, int stok) {
        this.code = code;
        this.name = name;
        this.harga = harga;
        this.stok = stok;
    }

    // getter dan setter
    public String getCode() { return code; }
    public String getName() { return name; }
    public double getHarga() { return harga; }
    public int getStok() { return stok; }
    public void setStok(int stok) { this.stok = stok; }
}

// File: InvalidQuantityException.java
package com.upb.agripos.week9;

public class InvalidQuantityException extends Exception {
    public InvalidQuantityException(String message) {
        super(message);
    }
}

// File: ShoppingCart.java
package com.upb.agripos.week9;

import java.util.HashMap;
import java.util.Map;

public class ShoppingCart {
    private Map<Product, Integer> items = new HashMap<>();

    public void addProduct(Product product, int qty) throws InvalidQuantityException {
        if (qty <= 0) {
            throw new InvalidQuantityException("Quantity harus lebih dari 0.");
        }
        if (qty > product.getStok()) {
            throw new InvalidQuantityException("Stok tidak cukup untuk: " + product.getName());
        }
        items.put(product, qty);
        product.setStok(product.getStok() - qty);
    }

    public void removeProduct(Product product) throws InvalidQuantityException {
        if (!items.containsKey(product)) {
            throw new InvalidQuantityException("Produk tidak ada dalam keranjang.");
        }
        items.remove(product);
    }
}

// File: MainExceptionDemo.java
package com.upb.agripos.week9;

public class MainExceptionDemo {
    public static void main(String[] args) {
        System.out.println("Hello, I am Hari Cahyono-240202900 (Week9)");

        ShoppingCart cart = new ShoppingCart();
        Product p1 = new Product("P01", "Pupuk Organik", 25000, 3);

        try {
            cart.addProduct(p1, -1);
        } catch (InvalidQuantityException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.removeProduct(p1);
        } catch (InvalidQuantityException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.addProduct(p1, 5);
        } catch (InvalidQuantityException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }
    }
}
---

## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2026-01-14 170109" src="https://github.com/user-attachments/assets/e21f9902-a1d8-4a90-8be1-f9f92e3a422b" />

---

## Analisis
1. Bagaimana kode berjalan:
  - Program membuat objek Product dan ShoppingCart.
  - Pada percobaan pertama, mencoba menambahkan produk dengan quantity -1, yang memicu exception "Quantity harus lebih dari 0."
  - Pada percobaan kedua, mencoba menghapus produk yang belum ada di keranjang, memicu exception "Produk tidak ada dalam keranjang."
  - Pada percobaan ketiga, mencoba menambahkan produk dengan quantity 5 padahal stok hanya 3, memicu exception "Stok tidak cukup."

2. Perbedaan dengan minggu sebelumnya:
  - Minggu ini fokus pada penanganan error dengan exception, bukan hanya validasi biasa.
  - Menggunakan custom exception untuk kontrol yang lebih spesifik.
  - Program lebih robust karena error ditangani secara terstruktur.

3. Kendala dan solusi:
  - Kendala: Awalnya exception tidak ditampilkan karena hanya ditangkap tanpa print.
  - Solusi: Menambahkan System.out.println("Kesalahan: " + e.getMessage()); dalam blok catch.
  - Kendala: Penggunaan named parameter (seperti qty: -1) yang tidak valid di Java.
  - Solusi: Menghapus named parameter dan menggunakan argumen langsung.
---

## Kesimpulan
Dengan menggunakan Exception Handling, program menjadi lebih tangguh dan mudah dalam mengelola kondisi error. Custom exception memungkinkan kita memberikan pesan yang lebih jelas dan spesifik sesuai dengan bisnis logic. Try-catch memastikan program tidak berhenti tiba-tiba saat terjadi exception, sehingga user experience tetap terjaga.
---

## Quiz
1. Apa perbedaan antara checked dan unchecked exception?
Jawaban: Checked exception harus ditangani pada waktu compile (dengan try-catch atau throws), sedangkan unchecked exception (RuntimeException dan turunannya) tidak wajib ditangani.

2. Kapan kita menggunakan throw dan throws?
Jawaban: throw digunakan di dalam body method untuk melemparkan exception secara manual. throws digunakan dalam deklarasi method untuk menunjukkan bahwa method tersebut dapat menghasilkan exception.

3. Apa kegunaan blok finally?
Jawaban: Blok finally digunakan untuk menempatkan kode yang harus dieksekusi terlepas dari apakah exception terjadi atau tidak, biasanya untuk cleanup resource seperti menutup file atau koneksi database.
