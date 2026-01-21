# Laporan Praktikum Minggu 4
Topik: Polymorphism

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

---

## Tujuan
1. Mahasiswa mampu menjelaskan konsep polymorphism dalam OOP.
2. Mahasiswa mampu membedakan method overloading dan overriding.
3. Mahasiswa mampu mengimplementasikan polymorphism (overloading, overriding, dynamic binding) dalam Java.
4. Mahasiswa mampu menganalisis penerapan polymorphism dalam sistem nyata, khususnya dalam konteks Agri-POS.

---

## Dasar Teori
1. Polymorphism adalah kemampuan objek berbeda menanggapi pemanggilan method yang sama dengan cara berbeda.
2. Overloading terjadi ketika ada method dengan nama yang sama tetapi parameter berbeda dalam suatu class (compile-time polymorphism).
3. Overriding terjadi ketika subclass mengganti implementasi method dari superclass (runtime polymorphism).
4. Dynamic Binding adalah mekanisme di mana method yang dipanggil ditentukan saat runtime sesuai tipe objek sebenarnya, bukan tipe referensinya.
5. Dalam konteks Agri-POS, polymorphism digunakan untuk menampilkan informasi produk yang berbeda (Benih, Pupuk, Alat Pertanian) melalui satu interface getInfo().
---

## Langkah Praktikum
1. Membuat class Produk dengan atribut dasar dan method overloading tambahStok(int) dan tambahStok(double).
2. Membuat subclass Benih, Pupuk, dan AlatPertanian yang override method getInfo().
3. Membuat class MainPolymorphism untuk:
    membuat array Produk[],
    menyimpan objek subclass,
4. menampilkan informasi menggunakan dynamic binding.
5. Menjalankan program dan mengambil screenshot output.

Melakukan commit dengan pesan:

week4-polymorphism

---

## Kode Program
package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainPolymorphism {
    public static void main(String[] args) {
        Produk[] daftarProduk = {
            new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64"),
            new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea"),
            new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja")
        };

        for (Produk p : daftarProduk) {
            System.out.println(p.getInfo());
        }

        CreditBy.print("<NIM>", "<Nama Mahasiswa>");
    }
}

---

## Hasil Eksekusi
<img width="1920" height="1080" alt="Screenshot 2026-01-21 120224" src="https://github.com/user-attachments/assets/f5e108d3-42f4-41eb-b3ee-630df3e8a66c" />

---

## Analisis
1. Pada class Produk, method tambahStok() menggunakan overloading, sehingga Java memilah method berdasarkan tipe parameter (int atau double).
2. Pada class Benih, Pupuk, dan AlatPertanian, method getInfo() di-override, sehingga tiap objek punya implementasi berbeda.
3. Pada class MainPolymorphism, ketika daftarProduk di-loop, method getInfo() yang dieksekusi adalah method milik objek sebenarnya (subclass), bukan milik Produk. Ini adalah contoh dynamic binding.
4. Pendekatan minggu ini lebih maju dari minggu sebelumnya karena melibatkan pewarisan dan polymorphism, bukan hanya enkapsulasi.
5. Kendala yang ditemui (misalnya method tidak ditemukan, paket salah, atau constructor belum benar) dapat diatasi dengan memastikan inheritence dan struktur folder benar.
---

## Kesimpulan
1. Polymorphism memungkinkan class berbeda memberikan implementasi berbeda terhadap method yang sama.
2. Overloading terjadi pada class yang sama, overriding terjadi pada superclass–subclass.
3. Java menentukan method yang dipanggil melalui dynamic binding, yaitu saat runtime.
4. Implementasi polymorphism membuat program lebih fleksibel, efisien, dan mudah dikembangkan.
---

## Quiz
1. Apa perbedaan overloading dan overriding?
Jawaban:
Overloading: method sama, parameter berbeda, terjadi di class yang sama.
Overriding: subclass mengganti method superclass, tanda @Override.

2. Bagaimana Java menentukan method mana yang dipanggil dalam dynamic binding?
Jawaban:
Java memilih method berdasarkan tipe objek sebenarnya (runtime type), bukan tipe referensi.

3. Berikan contoh polymorphism dalam sistem POS selain produk pertanian.
Jawaban:
Contoh: class Pembayaran dengan subclass PembayaranTunai, PembayaranQRIS, dan PembayaranDebit, masing-masing override method prosesPembayaran().
