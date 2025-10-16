# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: class dan object

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 ikka

---

## Tujuan
1.Mahasiswa mampu menjelaskan konsep class, object, atribut, dan method dalam pemrograman berorientasi objek (OOP).
2.Mahasiswa mampu menerapkan enkapsulasi dan access modifier dalam pembuatan class.
3.Mahasiswa mampu membuat dan mengimplementasikan class Produk serta menampilkan hasil di console.
4.Mahasiswa mampu menyusun laporan hasil praktikum lengkap dengan kode, output, dan analisis.

## Dasar Teori
1.Class adalah blueprint atau cetak biru dari objek yang berisi atribut (data) dan method (perilaku).
2.Object adalah instansiasi dari class, yaitu bentuk nyata dari sebuah class.
3.Atribut digunakan untuk menyimpan data, sedangkan method digunakan untuk memberikan perilaku pada objek.
4.Enkapsulasi dilakukan dengan menjadikan atribut private dan mengaksesnya melalui getter dan setter untuk menjaga keamanan data.
5.Dalam sistem Agri-POS, produk pertanian dapat direpresentasikan sebagai objek yang dikelola secara terstruktur.

## Langkah Praktikum
1.Membuat struktur proyek Java sesuai instruksi:
oop-20251-<nim>/
 └─ praktikum/week2-class-object/
     ├─ src/main/java/com/upb/agripos/model/Produk.java
     ├─ src/main/java/com/upb/agripos/util/CreditBy.java
     ├─ src/main/java/com/upb/agripos/MainProduk.java
     ├─ screenshots/hasil.png
     └─ laporan_week2.md
2.Membuat class Produk di package model dengan atribut kode, nama, harga, dan stok.
3.Membuat class CreditBy di package util untuk menampilkan identitas mahasiswa.
4.Membuat class MainProduk untuk menjalankan program dan menampilkan hasil.
5.Melakukan commit dengan pesan week2-class-object.

## Kode Program
package com.upb.agripos.model;

public class Produk {
    private String kode;
    private String nama;
    private double harga;
    private int stok;

    public Produk(String kode, String nama, double harga, int stok) {
        this.kode = kode;
        this.nama = nama;
        this.harga = harga;
        this.stok = stok;
    }

    public String getKode() { return kode; }
    public void setKode(String kode) { this.kode = kode; }

    public String getNama() { return nama; }
    public void setNama(String nama) { this.nama = nama; }

    public double getHarga() { return harga; }
    public void setHarga(double harga) { this.harga = harga; }

    public int getStok() { return stok; }
    public void setStok(int stok) { this.stok = stok; }

    public void tambahStok(int jumlah) {
        this.stok += jumlah;
    }

    public void kurangiStok(int jumlah) {
        if (this.stok >= jumlah) {
            this.stok -= jumlah;
        } else {
            System.out.println("Stok tidak mencukupi!");
        }
    }
}

CreditByjava
package com.upb.agripos.util;

public class CreditBy {
    public static void print(String nim, String nama) {
        System.out.println("\ncredit by: " + nim + " - " + nama);
    }
}

MainProduk.java
package com.upb.agripos;

import com.upb.agripos.model.Produk;
import com.upb.agripos.util.CreditBy;

public class MainProduk {
    public static void main(String[] args) {
        Produk p1 = new Produk("BNH-001", "Benih Padi IR64", 25000, 100);
        Produk p2 = new Produk("PPK-101", "Pupuk Urea 50kg", 350000, 40);
        Produk p3 = new Produk("ALT-501", "Cangkul Baja", 90000, 15);

        System.out.println("Kode: " + p1.getKode() + ", Nama: " + p1.getNama() + ", Harga: " + p1.getHarga() + ", Stok: " + p1.getStok());
        System.out.println("Kode: " + p2.getKode() + ", Nama: " + p2.getNama() + ", Harga: " + p2.getHarga() + ", Stok: " + p2.getStok());
        System.out.println("Kode: " + p3.getKode() + ", Nama: " + p3.getNama() + ", Harga: " + p3.getHarga() + ", Stok: " + p3.getStok());

        CreditBy.print("2310112345", "Andi Pratama");
    }
}


## Hasil Eksekusi
<img width="1920" height="1080" alt="Main Produk" src="https://github.com/user-attachments/assets/07e98d21-870c-45f5-bbfe-380d69fd03ee" />


## Analisis
Cara kerja kode:
Setiap objek Produk dibuat melalui konstruktor dan disimpan di variabel (p1, p2, p3).
Nilai atribut diambil menggunakan method getter dan ditampilkan dengan System.out.println.
Di akhir program, CreditBy.print() dipanggil untuk menampilkan identitas mahasiswa.

Perbedaan dengan minggu sebelumnya:
Pada minggu ini, digunakan pendekatan OOP (Object-Oriented Programming), bukan hanya prosedural.
Semua data dan perilaku produk ditempatkan dalam class tersendiri, membuat kode lebih terstruktur dan mudah dikembangkan.

Kendala yang dihadapi:
Awalnya terjadi error karena nama file tidak sama dengan nama class (MainProduk harus di file MainProduk.java).
Masalah diakses class antar-package diatasi dengan menambahkan import com.upb.agripos.model.Produk;.

##kesimpulan
Dengan menerapkan class dan object, program menjadi lebih terstruktur, rapi, dan mudah dikembangkan.
Prinsip enkapsulasi menjaga agar data produk tidak diubah langsung dari luar class.
Konsep ini merupakan dasar penting dalam pengembangan aplikasi skala besar seperti sistem POS (Point of Sale). 


## Quiz
1.Mengapa atribut sebaiknya dideklarasikan sebagai private dalam class?
Jawaban: Karena dengan menjadikannya private, atribut tidak dapat diubah secara langsung dari luar class. Hal ini menjaga keamanan dan konsistensi data (enkapsulasi).

2.Apa fungsi getter dan setter dalam enkapsulasi?
Jawaban: Getter digunakan untuk mengambil nilai atribut, sedangkan setter digunakan untuk mengubah nilai atribut dengan cara yang terkontrol.

3.Bagaimana cara class Produk mendukung pengembangan aplikasi POS yang lebih kompleks?
Jawaban: Class Produk menjadi fondasi untuk fitur lain seperti pengelolaan stok, transaksi penjualan, laporan, dan integrasi database. Dengan struktur OOP, sistem dapat dikembangkan tanpa mengubah logika utama.
