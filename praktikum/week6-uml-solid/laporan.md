# Laporan Praktikum Minggu 6
Topik: "uml-solid"

## Identitas
- Nama  : Hari Cahyono
- NIM   : 240202900
- Kelas : 3 IKKA

---

## Tujuan
Mahasiswa mampu memahami dan menerapkan desain arsitektur sistem menggunakan UML serta prinsip SOLID pada studi kasus sistem Agri-POS, sehingga dapat menghasilkan rancangan sistem yang modular, mudah dikembangkan, dan mudah dipelihara.
---

## Dasar Teori
1. UML (Unified Modeling Language) adalah bahasa standar untuk memodelkan dan mendokumentasikan sistem perangkat lunak.
2. Use Case Diagram digunakan untuk menggambarkan fungsionalitas sistem dan interaksi aktor dengan sistem.
3. Class Diagram merepresentasikan struktur kelas, atribut, method, serta relasi antar kelas.
4. SOLID merupakan prinsip desain OOP untuk meningkatkan maintainability dan extensibility sistem.
5. Open/Closed Principle memungkinkan sistem dikembangkan tanpa mengubah kode yang sudah ada.
---

## Langkah Praktikum
1. Menganalisis kebutuhan sistem Agri-POS berdasarkan deskripsi tugas.
2. Mengidentifikasi aktor dan fungsionalitas utama sistem.
3. Membuat desain Use Case Diagram menggunakan Graphviz.
4. Menyusun relasi antar use case (include).
5. Mengekspor diagram ke format gambar.
6. Melakukan commit dengan pesan: week6-uml-solid: iterasi-1 use case diagram.
---

## Kode Program
digraph UseCaseAgriPOS {
    rankdir=LR;
    node [shape=box, style=rounded];
    
    // Actors
    node [shape=plaintext];
    Admin [label="Admin"];
    Kasir [label="Kasir"];
    
    // System boundary
    subgraph cluster_0 {
        label="AgriPOS";
        style=dashed;
        
        // Use Cases
        node [shape=ellipse, style=filled, fillcolor=lightblue];
        UC1 [label="Kelola Produk"];
        UC2 [label="Lihat Laporan"];
        UC3 [label="Checkout"];
        UC4 [label="Pembayaran Tunai"];
        UC5 [label="Pembayaran E-Wallet"];
        UC6 [label="Cetak Struk"];
        UC7 [label="Scan Produk"];
        UC8 [label="Hitung Total"];
        UC9 [label="Validasi Pembayaran"];
        UC10 [label="Update Stok"];
    }
    
    // Associations
    Admin -> UC1 [label="uses"];
    Admin -> UC2 [label="uses"];
    
    Kasir -> UC3 [label="uses"];
    Kasir -> UC6 [label="uses"];
    
    // Include relationships
    UC3 -> UC4 [label="<<include>>", style=dashed];
    UC3 -> UC5 [label="<<include>>", style=dashed];
}
---

## Hasil Eksekusi
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f0a6896b-6437-48f2-928e-f9187469c63b" />

---

## Analisis
1. Kode Graphviz bekerja dengan mendefinisikan aktor, batas sistem, serta use case yang terdapat pada sistem Agri-POS.
2. Pendekatan minggu ini berbeda dengan minggu sebelumnya karena fokus pada desain dan arsitektur sistem, bukan implementasi kode program.
3. Kendala yang dihadapi adalah menentukan relasi use case yang tepat, yang diatasi dengan mempelajari kembali konsep include dan extend pada UML.
---

## Kesimpulan
Dengan menggunakan UML dan prinsip SOLID, desain sistem Agri-POS menjadi lebih terstruktur, mudah dipahami, serta siap dikembangkan di masa depan tanpa mengubah desain inti sistem.
---

## Quiz
1. Jelaskan perbedaan aggregation dan composition serta berikan contoh penerapannya pada desain Anda.
Jawaban: Aggregation adalah relasi lemah antar objek, sedangkan composition adalah relasi kuat. Contoh composition pada Agri-POS adalah relasi antara transaksi dan item transaksi.

2. Bagaimana prinsip Open/Closed dapat memastikan sistem mudah dikembangkan?
Jawaban: Dengan membuat sistem terbuka untuk penambahan fitur baru melalui ekstensi tanpa mengubah kode lama.

3. Mengapa Dependency Inversion Principle (DIP) meningkatkan testability?
Jawaban: Karena dependency berbasis interface dapat di-mock sehingga pengujian dapat dilakukan tanpa bergantung pada implementasi nyata.
