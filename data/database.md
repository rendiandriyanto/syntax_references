# Database

![Database](../images/database.png)

Image by [juicy_fish](https://www.freepik.com/icon/database_17069564#fromView=keyword&page=1&position=22&uuid=bf4fe23c-c479-4fed-a23f-9671003456ab)

Credit :
> [Programmer Zaman Now](https://www.youtube.com/watch?v=S4igMZFCvh8)

## Basis Data

- Basis = Tempat/Gudang/Penyimpanan
- Data = Representasi fakta dari dunia nyata (Manusia, Barang, Peristiwa dll)

## Bahasa Basis Data & DBMS

Operasi Basis Data = *CRUD* (Create, Read, Update, Delete)

*DBMS* (DataBase Management System) = Sistem yang mengelola Database dan menjadi perantara antara User dengan Database

- *DDL* (Data Definition Language) = Bahasa yang digunakan untuk mengelola struktur pada Database
- *DML* (Data Manipulation Language) = Bahasa yang digunakan untuk memanipulasi data pada Database

## ER Model

Model Data yang paling sering digunakan adalah *ERD* (Entity Relationship Diagram)

- Entity (Rectangle) -> Tabel = Suatu entitas yang mewakili individu sesuai ruang lingkup
- Attribute (Oval) -> Kolom = Karakteristik yang mendeskripsikan suatu entitas
- Relationship (Rhombus) = Merupakan hubungan antar entitas
- Link (Line) = Hubungan untuk mengetahui relasi antar entitas

Kardinalitas / Derajat Relasi :

1. One to One = Hanya berelasi 1-1 = Foreign Key berada pada Weak Entity
2. One to Many / Many to One = Berelasi 1-N / N-1 = Foreign Key pada Many (Dibuat tabel baru jika ada tambahan atribut)
3. Many to Many = Dapat berelasi N-N = Harus dibuat tabel baru untuk Foreign Key

***Entity -> Attribute -> Primary Key -> Relationship -> Kardinalitas -> Foreign Key***

## Model lainnya

- **Weak Entity** (Double Rectangle) = Entitas lemah yang tidak dapat ada jika entitas kuat nya belum ada
- **Sub Entity** (Flip Triangle/ISA) = Entitas yang sama tetapi masing-masing memiliki atribut spesifik
- **Unary Relationship** = Entitas yang berelasi dengan dirinya sendiri (Referral)
- **Multi Entity Relationship** = Entias yang berelasi lebih dari 2 entitas
- **Redundant Relationship** = Entitas yang dapat berelasi lebih dari 1 relasi

## Atribut

- Attribute Key / Primary Key = Atribut kunci yang khas untuk suatu entitas
- Superkey -> Candidate Key -> Primary Key
- Foreign Key = Attribute Key milik entitas lain yang digunakan sebagai Lookup
- Simple Attribute = Atribut yang sudah tidak dapat diuraikan lagi
- Composite Attribute = Atribut yang dapat diurai misalnya seperti alamat
- Single-Value Attribute = Atribut yang hanya memiliki 1 nilai dalam 1 kolom
- Multi-Value Attribute = Atribut yang memiliki banyak nilai dalam 1 kolom misalnya kode produk
- Mandatory Attribute = Atribut yang wajib memiliki nilai atau tidak NULL
- Derived Attribute = Atribut turunan hasil dari atribut lain

## Normalisasi Data

1. First Normal Form = Tidak boleh ada kolom yang berulang seperti produk 1, produk 2 dst dan tidak boleh ada Derived Attribute
2. Second Normal Form = Buat tabel baru pada baris yang berulang dan tentukan PK FK nya
3. Third Normal Form = Membuat tabel jika ada atribut yang tidak bergantung pada Attribute Key (A->B)

Denormalisasi data = Melanggar aturan normalisasi data untuk tujuan Read dengan lebih cepat

## Partitioning Data & ETL-ELT

Partitioning Data dapat dibagi menjadi 2 yaitu :

- Vertical Partitioning = Records dapat di partisi berdasarkan banyaknya kolom
- Horizontal Partitioning = Recods dapat di partisi berdasarkan records itu sendiri seperti waktu atau teks (jika diproses pada lokasi proses yang berbeda maka disebut dengan Sharding)

> ETL & ELT terkadang diperlukan untuk menjaga agar data tetap konsisten
