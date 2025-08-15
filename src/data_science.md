# Conceptual

![Data Science](../images/data_science.png)

Image by [Flowicon](https://www.freepik.com/icon/data-science_6097658)

***Credits*** :
> [DataCamp (Associate Data Engineer in SQL)](https://www.datacamp.com/tracks/associate-data-engineer-in-sql)

## Data Workflow

Data mengalir dari hulu ke hilir dengan 4 tahap :

1. Data Collection & Storage (Data Engineer)
2. Data Preparation (Data Engineer & Data Analyst & Data Scientist)
3. Exploration & Visualization (Data Analyst & Data Scientist)
4. Experimentation & Prediction (Data Scientist)

## The Five V's of Big Data

Terdapat 5 komponen V yang membuat sebuah data dapat dikatakan sebagai Big Data :

- Volume = Seberapa besar data tersebut?
- Variety = Seberapa beragam data tersebut?
- Velocity = Seberapa cepat data tersebut dihasilkan?
- Veracity = Seberapa besar data tersebut dapat dipercaya?
- Value = Seberapa bergunanya data tersebut?

## SQL - ETL - Database Schema

### SQL

**SQL** adalah singkatan dari *Structured Query Language* dan digunakan untuk berinteraksi dengan *RDBMS* (Relational DataBase Management System)

### ETL

**ETL** adalah Framework yang populer dalam Data Engineering dan singkatan dari *Extract, Transform, Load* yang artinya data diproses terlebih dahulu sebelum disimpan (tetapi tidak wajib)

### Database Schema

Database Schema dapat diibaratkan sebagai Blueprint dari Database

## Data Structures

Terdapat 3 macam varian pada struktur data :

- Structured Data = Data yang terstruktur oleh tabel dalam bentuk kolom dan baris (menggunakan SQL untuk mengelolanya)
- Semi-Structured Data = Data yang lebih fleksibel dari Structured Data (contohnya seperti JSON, XML dan YAML)
- Unstructured Data = Data yang tidak terstruktur tetapi memiliki Value yang besar jika dapat dikelola (seperti foto, video dan lain-lain)

## Data Lake vs Data Warehouse vs Database

Ada 3 tipe dari tempat dimana kita dapat menyimpan data :

- Data Lake = Tempat dimana seluruh data dikumpulkan (dibutuhkan Data Catalog untuk mengimbangi ketidak strukturan pada Data Lake agar tidak menjadi Data Swamp)
- Data Warehouse = Tempat dimana data yang telah diolah dikumpulkan dan biasanya digunakan untuk Ad-Hoc dan Read Only
- Database = Secara umum Database dapat diartikan dengan tempat berkumpulnya suatu data yang telah dikelola (Data Warehouse termasuk bagian dari Database)

## Processing

Terdapat 3 macam penjadwalan dalam model Processing :

- Manual = Dilakukan secara mandiri (misalnya ada data yang perlu diperbarui secara mandiri)
- Time = Diproses saat memasuki waktu yang telah ditentukan (seperti memperbarui data karyawan setiap jam 6 pagi)
- Condition/Sensor = Memproses data saat data tersebut memenuhi kondisi yang telah ditentukan

Selain itu, ada 2 macam proses yang dapat digunakan untuk mengirim data :

- Batch Processing = Mengirim beberapa data sekaligus dalam interval waktu tertentu
- Stream Processing = Mengirim data individu langsung ke Database (seperti proses Register pada sebuah Platform)

## Parallel Processing

Parallel Processing digunakan untuk membagi beban kerja dalam sebuah proses yang membutuhkan daya komputasi yang besar

## Cloud Computing

Provider Cloud menyediakan alternatif yang dapat digunakan untuk menghemat biaya dibandingkan dengan On-Premise Server

## OLTP & OLAP

- *OLTP* = Online Transaction Processing adalah Database yang biasa digunakan untuk keperluan operasional
- *OLAP* = Online Analytical Processing adalah Database digunakan untuk keperluan analisis Ad-Hoc

## ETL vs ELT

Pada *ETL*, data di Transform sebelum masuk ke Data Warehouse untuk di-analisa. Pada *ELT*, data di Load sebelum di Transform (misalnya untuk keperluan Big Data Analytics)

### Kelebihan dan Kekurangan ETL

- Biaya Data Storage menjadi rendah
- Dapat dengan mudah mematuhi privasi data (PII)
- Jika transformasi Error maka harus mengambil data ulang
- Tidak dapat menyimpan data asli karena sudah ditransformasi (dapat mengabaikan Transform jika beberapa data tidak ingin diubah)

### Kelebihan dan Kekurangan ELT

- Tidak butuh sistem yang berbeda pada pemrosesan data
- Transformasi dapat dilakukan tanpa harus mengambil datanya secara ulang
- Biaya/kapasitas menjadi besar karena langsung menyimpan data pada Data Warehouse tanpa diproses
- Sulit mematuhi privasi data (PII) karena data tersebut langsung di Load tanpa di Transform terlebih dahulu

## Data Mart

Data Mart adalah lokasi akhir setelah Data Warehouse jika diperlukan untuk tiap masing-masing Stakeholder agar memiliki data akhir yang spesifik

## Fact Table & Dimensional Table

Fact Table adalah tabel yang berisi data metrik didalamnya, dan Dimensional Table berisi data yang lebih spesifik

## Star Schema vs Snowflake Schema

Ada 2 skema yang populer pada Database Design :

- Star Schema = Biasa digunakan pada Data Warehouse untuk keperluan OLAP
- Snowflake Schema = Digunakan pada Database Transactional yang memerlukan presisi data yang tinggi

## 1NF > 2NF > 3NF

Pada normalisasi data berdasarkan [Edgar F. Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd), minimal ada 3 normalisasi yang setidaknya diketahui :

1. 1NF = Setiap Record tidak boleh ada yang memiliki 2 nilai atau lebih
2. 2NF = Setiap Field harus bergantung ke Field Key
3. 3NF = Setiap Field tidak boleh ada yang bergantung pada Field Non-Key lainnya

## Top-Down Architecture vs Bottom-Up Architecture

Terdapat 2 Approach pada arsitektur Data Warehouse, berikut masing-masing kelebihan dan kekurangannya :

### Inmon Approach (Top-Down)

- Data dikumpulkan dulu di Data Warehouse setelah proses *ETL* kemudian disebar ke Data Mart untuk di Consume oleh aplikasi atau User
- Data pada Data Warehouse dinormalisasi dengan tujuan integrasi kebenaran data mutlak
- Mudah dikelola jika memerlukan kebutuhan Data Mart

### Kimball Approach (Bottom-Up)

- Data langsung dimasukan kedalam Data Mart kemudian dikumpulkan kedalam Data Warehouse untuk di Consume
- Pada data Data Mart dan Data Warehouse, data didenormalisasi untuk keperluan Query yang cepat
- Lebih cepat beroperasi namun lebih sulit untuk dikelola (misalnya membutuhkan Data Mart baru)

## Data Modeling

Ada 4 proses pada Data Modeling yang disebut sebagai Kimball's Four Step Process, yaitu :

1. Tentukan bisnis proses apa yang dibutuhkan disetiap Data Mart
2. Tentukan Grain/data yang akan terkandung dalam setiap Row
3. Tentukan Dimentional Table nya
4. Tentukan Fact Table nya

Kemudian ada 4 macam SCD (Slowly Changing Dimensions) atau cara mengubah data lama pada Dimentional Table agar tetap selaras dengan data terbaru :

- Type I = Mengubah langsung data tersebut (tetapi memiliki resiko History data tidak konsisten dengan data terbaru)
- Type II = Menambahkan data pada Row (data baru merujuk pada Row terbaru)
- Type III = Menambahkan kolom/Field baru (data merujuk pada kapan data itu dibuat)
- Modern Approach = Seperti tipe I tetapi data di Snapshot terlebih dahulu sebelum diubah

## Data Warehouse Workflow

1. Tentukan apakah Inmon Approach atau Kimball Approach?
2. Gunakan Kimball's Four Step Process
3. On-Premise atau Cloud
4. ETL atau ELT
