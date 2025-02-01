# PostgreSQL

![PostgreSQL](images/postgresql.png)

Image by [Freepik](https://www.freepik.com/icon/postgre_5968342#fromView=keyword&page=1&position=1&uuid=f5d152b7-d1d4-42ce-b9ee-71147a1c9ad1)

Credits :
> [Programmer Zaman Now](https://www.youtube.com/watch?v=iEeveYoD0SA&t=529s) -
> [ProgrammingKnowledge](https://www.youtube.com/watch?v=tducLYZzElo) -
> [Buttle Butkus](https://stackoverflow.com/questions/61523447/skipping-acquire-of-configured-file-main-binary-i386-packages)

## Alur Kerja

***Database Client -> DBMS -> Database File***

*Command* :

- `\l` = Untuk melihat List Database
- `\c [database]` = Pindah ke Database lain
- `\conninfo` = Untuk melihat detail koneksi
- `\dt` = Melihat seluruh tabel
- `\ds` = Melihat seluruh Sequence
- `\d` = Melihat seluruh struktur yang telah dibuat pada Database
- `\d [table]` = Untuk melihat struktur data tabel

*Syntax* :

- `SELECT datname FROM pg_database;` = \l
- `CREATE DATABASE [database];` = Membuat Database baru
- `DROP DATABASE [database];` = Menghapus Database
- `SELECT * FROM pg_tables WHERE schemaname = 'public';` = \dt

## Tipe Data

**Number** :

- smallint = 2 bytes - 32k
- int = 4 bytes - 2b
- bigint = 8 bytes - 9quin
- numeric = Precision, Scale
- real = 4 bytes - 6 digits precision
- double precision = 8 bytes - 15 digits precision
- smallserial = 2 bytes - 32k
- serial = 4 bytes - 2b
- bigserial = 8 bytes - 9quin

**TEXT** :

- char = Digunakan untuk panjang teks yang pasti - 65k
- varchar = Digunakan untuk panjang teks yang fleksibel - 65k
- text = Digunakan untuk teks panjang seperti deskripsi

**DATETIME** :

- timestamp with time zone = Untuk tanggal dan waktu - 8 bytes
- date = Hanya untuk tanggal - 4 bytes
- time with time zone = Hanya untuk waktu - 12 bytes

**BOOLEAN** :

- TRUE = Jika benar
- FALSE = Jika salah

**ENUMERATE** :

- `CREATE TYPE [enum] AS ENUM ('VALUE1', 'VALUE2', 'VALUE3');` = Membuat enum

## DDL

- `CREATE TABLE [table] (column);` = Membuat tabel
- `TRUNCATE [table];` = Untuk menghapus seluruh data pada suatu tabel
- `DROP TABLE [table];` = Untuh menghapus tabel
- `ALTER TABLE [table]` = Mengubah struktur tabel / DDL
- `ADD COLUMN [column] [datatype];` = Menambahkan kolom baru
- `DROP COLUMN [column];` = Menghapus kolom
- `RENAME COLUMN [column] TO [column];` = Mengubah nama kolom
- `ADD PRIMARY KEY ([column]);` = Menambahkan Primary Key pada column yang sudah dibuat
- `NOT NULL;` = Digunakan untuk Mandatory Attribute
- `DEFAULT [value];` = Digunakan untuk menambahkan nilai pada Value secara Default

## DML

- `INSERT INTO [table] (column) VALUES (data);` = Memasukkan data ke tabel
- `SELECT [column] FROM [table];` = Melihat data pada tabel
- `WHERE [column] [value];` = Mencari data spesifik
- `UPDATE [table] SET [column] WHERE [column];` = Mengubah data
- `DELETE FROM [table] WHERE [column];` = Menghapus data
- `SELECT [column] AS [alias] FROM [table];` = Melakukan alias agar memperbuat Read
- `= != < > <= >= OR AND ()` = Operator perbandingan dan logika
