# Laporan Praktikum Minggu 3
Topik: Inheritance

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

## Tujuan
Mahasiswa mampu menjelaskan konsep inheritance (pewarisan class) dalam OOP, membuat superclass dan subclass untuk produk pertanian, mendemonstrasikan hierarki class melalui contoh kode, menggunakan super untuk memanggil konstruktor dan method parent class, serta membuat laporan yang menjelaskan perbedaan penggunaan inheritance dibanding class tunggal.

## Dasar Teori
1. Inheritance adalah mekanisme dalam OOP yang memungkinkan suatu class mewarisi atribut dan method dari class lain.
2. Superclass (class induk) mendefinisikan atribut dan method umum yang dapat digunakan oleh subclass.
3. Subclass (class turunan) mewarisi dari superclass dan dapat menambahkan atribut/method khusus.
4. Keyword super digunakan untuk memanggil konstruktor atau method dari superclass.
5. Hierarki class membantu mengorganisir kode dengan hubungan "is-a" yang jelas (contoh: Benih adalah Produk).

## Langkah Praktikum
Langkah 1: Setup Environment
Membuat struktur folder sesuai petunjuk
Membuat package com.upb.agripos.model dan com.upb.agripos.util

Langkah 2: Membuat Superclass Produk
Membuat file Produk.java di package model
Mendefinisikan atribut dasar: kode, nama, harga, stok
Membuat konstruktor, getter, setter, dan method tampilkanInfo()

Langkah 3: Membuat Subclass
Benih.java: menambahkan atribut varietas dan musimTanam
Pupuk.java: menambahkan atribut jenis dan kandungan
AlatPertanian.java: menambahkan atribut material dan garansi
Menggunakan super() untuk memanggil konstruktor parent class

Langkah 4: Membuat Main Class
Membuat MainInheritance.java di package utama
Menginstansiasi objek dari setiap subclass
Menampilkan informasi menggunakan method yang diwarisi

Langkah 5: Membuat CreditBy Utility
Membuat class CreditBy.java dengan method static print()

Langkah 6: Testing dan Dokumentasi
Menjalankan program dan memastikan berjalan dengan benar
Mengambil screenshot hasil eksekusi
Membuat laporan praktikum

Commit Message

git add .
git commit -m "week3-inheritance"
git push origin main

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

    // Getter dan Setter
    public String getKode() { return kode; }
    public void setKode(String kode) { this.kode = kode; }
    
    public String getNama() { return nama; }
    public void setNama(String nama) { this.nama = nama; }
    
    public double getHarga() { return harga; }
    public void setHarga(double harga) { this.harga = harga; }
    
    public int getStok() { return stok; }
    public void setStok(int stok) { this.stok = stok; }
    
    public void tampilkanInfo() {
        System.out.println("Kode: " + kode);
        System.out.println("Nama: " + nama);
        System.out.println("Harga: Rp" + harga);
        System.out.println("Stok: " + stok);
    }
}

## Hasil Eksekusi
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0c0bc9d8-4080-4b60-9c08-281d4440b66e" />


## Analisis
Bagaimana Kode Berjalan:
Superclass Produk menyediakan atribut dan method dasar yang umum untuk semua produk.
Subclass Benih, Pupuk, AlatPertanian mewarisi dari Produk dan menambahkan atribut khusus.
Keyword super digunakan untuk:
super(kode, nama, harga, stok): Memanggil konstruktor superclass
super.tampilkanInfo(): Memanggil method dari superclass dalam override
Polymorphism: Objek subclass dapat menggunakan method dari superclass dan override method jika diperlukan.

## Kesimpulan
Dengan menggunakan inheritance dalam OOP, program Agri-POS menjadi lebih terstruktur dan efisien. Inheritance memungkinkan:
1. Code Reusability: Atribut dan method umum di Produk dapat digunakan ulang oleh subclass
2. Maintainability: Perubahan di superclass otomatis berlaku ke semua subclass
3. Extensibility: Mudah menambahkan jenis produk baru tanpa mengubah kode existing
4. Structured Hierarchy: Representasi hubungan produk yang jelas dalam sistem
Pendekatan inheritance lebih baik daripada class tunggal karena mengurangi duplikasi kode, meningkatkan konsistensi, dan memudahkan pengembangan fitur baru di masa depan.

Quiz

## Quiz
1. Apa keuntungan menggunakan inheritance dibanding membuat class terpisah tanpa hubungan?
Jawaban:
Keuntungan utama inheritance adalah:
1. Code Reusability: Menghindari duplikasi kode dengan mewarisi atribut dan method yang sama
2. Code Maintenance: Perubahan di superclass otomatis berlaku untuk semua subclass
3. Struktur yang Lebih Baik: Representasi hubungan hierarkis yang jelas
4. Polymorphism: Memungkinkan fleksibilitas dalam penggunaan objek
5. Ekstensibilitas: Mudah menambahkan class baru tanpa mengubah kode yang sudah ada

2. Bagaimana cara subclass memanggil konstruktor superclass?
Jawaban:
Subclass memanggil konstruktor superclass menggunakan keyword super() pada baris pertama konstruktor subclass. Contoh:
java
public class Benih extends Produk {
    public Benih(String kode, String nama, double harga, int stok, String varietas) {
        super(kode, nama, harga, stok); // Memanggil konstruktor Produk
        this.varietas = varietas;
    }
}

3. Berikan contoh kasus di POS pertanian selain Benih, Pupuk, dan Alat Pertanian yang bisa dijadikan subclass.
Jawaban:
1. ObatPestisida → extends Produk
  Atribut tambahan: jenisPestisida (insekisida, fungisida, herbisida), targetHama
  Method: petunjukPenggunaan()
2. PeralatanIrigasi → extends Produk
  Atribut tambahan: tipeIrigasi (sprinkler, drip, manual), kapasitas
  Method: hitungKebutuhanAir()
3. PakaianPelindung → extends Produk
  Atribut tambahan: ukuran, tingkatPerlindungan, material
  Method: cekKesesuaianCuaca()
4. MediaTanam → extends Produk
  Atribut tambahan: komposisi (tanah, sekam, kompos), pH
  Method: rekomendasiTanaman()
