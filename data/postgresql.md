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
- `\du` = Melihat seluruh Role
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
- `WHERE [column] LIKE/ILIKE/NOT LIKE '%value%';` = Mencari karakter yang cocok
- `WHERE [column] IS NULL/IS NOT NULL` = Mencari data NULL
- `WHERE [column] BETWEEN/NOT BETWEEN [value] AND [value];` = Mencari nilai di antaranya
- `WHERE [column] IN/NOT IN ('value', 'value');` = Mencari beberapa nilai sekaligus
- `ORDER BY [value] ASC/DESC;` = Pengurutan
- `LIMIT [value] OFFSET [value];` = Membatasi tampilan data dan men-skip data
- `SELECT DISTINCT [column] FROM [table];` = Menghasilkan Output unik yang tidak duplikat
- `+ - * / %` = Operasi matematika pada SQL
- `LOWER, UPPER, LENGTH` = Contoh String Function
- `EXTRACT([YEAR/MONTH/DATE] FROM [column])` = Contoh Datetime Function
- `COUNT, MAX, MIN, AVG` = Contoh Aggregate Function

## Sequence

- `CREATE SEQUENCE [seq];` = Membuat Sequence atau urutan
- `SELECT CURRVAL([seq]);` = Melihat urutan terkini
- `SELECT NEXTVAL([seq]);` = Menambahkan Sequence ke urutan selanjutnya
- `DROP SEQUENCE [seq];` = Menghapus Sequence

## If Else / CASE dalam SQL

- `SELECT CASE [column] WHEN [value] THEN [condition] ELSE [condition] END AS [column]` = Pengkondisian pada SQL
- `SELECT CASE WHEN [column] > [value] THEN [condition] ELSE [condition] END AS [column]` = Menggunakan operasi
- `SELECT CASE WHEN [column] IS NULL THEN [condition] ELSE [condition] END AS [column]` = Mengecek NULL

## GROUP BY

- `SELECT [column], [agg func] FROM [table] GROUP BY [column];` = Menampilkan kolom dengan agregat
- `SELECT [column], [agg func] FROM [table] GROUP BY [column] HAVING [agg func];` = Mensortir hasil GROUP BY

## CONSTRAINT

- `CONSTRAINT [constraint] UNIQUE ([column]);` = Membuat data suatu kolom menjadi unik
- `CONSTRAINT [constraint] CHECK ([column] [condition]);` = Membuat agar kolom tetap valid
- `DROP CONSTRAINT [constraint];` = Menghapus Constraint pada tabel tertentu

## INDEX & FULL TEXT SEARCH

- `CREATE INDEX [index] ON [table] (column);` = Membuat Index agar mempercepat Read
- `SELECT CFGNAME FROM pg_ts_config;` = Melihat bahasa yang tersedia untuk FTS
- `CREATE INDEX [index] ON [table] USING GIN (to_tsvector('[lang]', '[column]'));` = Membuat FTS
- `SELECT * FROM [table] WHERE [column] @@ to_tsquery ('|&!');` = Melakukan Read FTS
- `DROP INDEX [index];` = Menghapus Index dan FTS

## Relational - Join Table - Sub Query - Set Operator - Transaction

- `CONSTRAINT [constraint] FOREIGN KEY ([column]) REFERENCES [table] ([column]);` = Menambahkan Foreign Key
- `ON DELETE/UPDATE RESTRICT/CASCADE/NO ACTION/SET NULL/SET DEFAULT` = Behavior Constraint
- `JOIN [table] ON [table].[column] = [table].[column] JOIN ~;` = Menggabungkan 2 tabel atau lebih
- `INNER - LEFT - RIGHT - FULL` = Macam-macam Join
- `SELECT * FROM [table] WHERE [table] [condition] ([sub]);` = Sub Query dari Where Clause
- `SELECT * FROM ([sub]) AS [as];` = Sub Query dari From Clause
- `UNION - UNION ALL - INTERSECT - EXCEPT` = Macam-macam Set operator
- `START TRANSACTION - COMMIT - ROLLBACK` = Alur Database Transaction
- `SELECT * FROM [table] WHERE [coloum] [condition] [value] FOR UPDATE;` = Locking data secara manual

## Schema

- `SELECT CURRENT_SCHEMA();` = Melihat skema yang sedang digunakan
- `CREATE SCHEMA [schema];` = Membuat skema baru
- `SET SEARCH_PATH TO [schema];` = Pindah ke skema lain
- `DROP SCHEMA [schema];` = Menghapus skema

## User Role

- `CREATE ROLE [role];` = Membuat Role
- `DROP ROLE [role];` = Menghapus Role
- `ALTER ROLE [role] [option];` = Memberikan opsi seperti Login / Password
- `GRANT [access] ON ALL TABLES IN SCHEMA [schema] TO [role];` = Memberikan seluruh akses tabel
- `GRANT [access] ON [tables] TO [role];` = Memberikan akses ke suatu tabel
- `GRANT [access] ON [tables] FROM [role];` = Menghapus akses suatu Role

## Backup & Restore

- `pg_dump -h [host] -p [port] -d [db] --format=plain -f [loc] -U [user] -W` = Backup
- `psql -h [host] -p [port] -d [db] -f [loc] -U [user] -W` = Restore
