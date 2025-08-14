# PostgreSQL

![PostgreSQL](../images/postgresql.png)

Image by [Freepik](https://www.freepik.com/icon/postgre_5968342)

***Credits*** :
> [ProgrammingKnowledge](https://www.youtube.com/watch?v=tducLYZzElo) -
> [Buttle Butkus](https://stackoverflow.com/questions/61523447/skipping-acquire-of-configured-file-main-binary-i386-packages) -
> [DataCamp (Associate Data Engineer in SQL)](https://www.datacamp.com/tracks/associate-data-engineer-in-sql) -
> [Neon (Learning Path Guide)](https://neon.com/postgresql/tutorial)

## Table, Column and Row

Terdapat 3 struktur utama pada Database, yakni :

- Table = Berisi seluruh struktur untuk menyimpan data (nama tabel harus spesifik, Lower Case dan menggunakan Underscore daripada spasi)
- Columns/Fields = Berisi 1 kategori spesifik untuk data tertentu (sama seperti tabel yang harus spesifik, Lower Case dan Underscore)
- Rows/Records = Berisi seluruh data suatu individual tertentu

Dan ada juga yang namanya Result Set yang artinya adalah kumpulan hasil dari suatu Query

## Data Type

Tipe data terbagi menjadi banyak tipe, berikut adalah tipe data yang paling sering digunakan :

- VARCHAR (String) = Tipe data untuk karakter seperti huruf, angka, ataupun tanda baca
- CHAR (Character) = Sama seperti VARCHAR tetapi lebih diperuntukan untuk panjang yang tetap
- TEXT = Tipe data untuk String dengan panjang berapapun
- INT (Integer) = Tipe data untuk bilangan bulat
- NUMERIC (Float) = Tipe data untuk bilangan pecahan
- DATE = Tipe data untuk tanggal dengan format YYYY-MM-DD
- TIME = Tipe data untuk waktu dengan format HH:mm:ss
- TIMESTAMP = Tipe data untuk tanggal dan waktu (dapat ditambahkan TZ untuk Timezone)
- BOOLEAN = Tipe data untuk nilai TRUE atau FALSE dan 1 atau 0 (dan NULL)

## Query

### Order of Execution & Comparison Operator & Arithmetic Operator

| Write | Keyword       | Order     |
| ----- | ---------     | --------- |
| 1     | `SELECT`      | 7         |
| 2     | `FROM`        | 1         |
| 3     | `JOIN`        | 2         |
| 4     | `ON`          | 3         |
| 5     | `WHERE`       | 4         |
| 6     | `GROUP BY`    | 5         |
| 7     | `HAVING`      | 6         |
| 8     | `ORDER BY`    | 8         |
| 9     | `LIMIT`       | 9         |

Operator komparasi pada SQL adalah `> < >= <= = !=`

Operator aritmatika pada SQL adalah `+ - * /`

### SELECT FROM

```sql
-- mengambil data dari 1 Field
SELECT field
FROM table;
```

```sql
-- mengambil data dari beberapa Field
SELECT field_1, field_2
FROM table;
```

```sql
-- mengambil seluruh Field menggunakan Wildcard asterisk
SELECT *
FROM table;
```

### ALIAS

```sql
-- membuat alias untuk kemudahan penamaan Field
SELECT field AS alias
FROM table;
```

### ORDER BY ASC/DESC

```sql
-- mengurutkan hasil dari Result Set (Default nya adalah ASC)
SELECT *
FROM table
ORDER BY field DESC;
```

### DISTINCT

```sql
-- untuk mendapatkan Result Set yang unik
SELECT DISTINCT field
FROM table;
```

### WHERE

```sql
-- memfilter hasil dari Query
SELECT *
FROM table
WHERE field = value;
```

### AND

```sql
-- menghasilkan hasil logika AND
SELECT *
FROM table
WHERE field_1 = value_1 AND field_2 = value_2;
```

### OR

```sql
-- menghasilkan hasil logika OR
SELECT *
FROM table
WHERE field_1 = value_1 OR field_2 = value_2;
```

### LIMIT

```sql
-- membatasi hasil yang diberikan oleh Result Set (sering digunakan untuk menguji kode sebelum menjadi akhir Query)
SELECT *
FROM table
LIMIT limit;
```

### IN

```sql
-- untung memfilter beberapa nilai sekaligus
SELECT *
FROM table
WHERE field IN (value_1, value_2);
```

### BETWEEN

```sql
-- menghasilkan hasil logika BETWEEN (biasa digunakan untuk mencari nilai rentang tertentu)
SELECT *
FROM table
WHERE field BETWEEN value_1 AND value_2;
```

### LIKE - ILIKE - NOT LIKE

```sql
-- menggunakan LIKE untuk mencari teks tertentu (Case Sensitive) dan menggunakan Wildcard % dan _
SELECT *
FROM table
WHERE field LIKE 'x_%';
```

```sql
-- menggunakan ILIKE untuk mencari teks tertentu (Case Insensitive) dan menggunakan Wildcard % dan _
SELECT *
FROM table
WHERE field LIKE 'x_%';
```

```sql
-- menggunakan NOT LIKE untuk mencari teks tertentu (kebalikan dari LIKE) dan menggunakan Wildcard % dan _
SELECT *
FROM table
WHERE field NOT LIKE 'x_%';
```

### IS NULL - IS NOT NULL

```sql
-- mencari nilai NULL pada Records
SELECT *
FROM table
WHERE field IS NULL;
```

```sql
-- mencari nilai yang tidak NULL pada Records
SELECT *
FROM table
WHERE field IS NOT NULL;
```

### Relationship

Ada 3 relasi yang digunakan untuk menghubungkan antar tabel :

- One to One = Hanya berelasi 1-1
- One to Many / Many to One = Berelasi 1-N / N-1
- Many to Many = Dapat berelasi N-M

### INNER JOIN

```sql
-- merelasikan antar table
SELECT t1.field_1 AS alias_1, t2.field_2 AS alias_2, field_3
FROM table_1 AS t1
INNER JOIN table_2 AS t2
ON t1.field_4 = t2.field_5;
```

```sql
-- merelasikan antar table menggunakan USING (jika ada Field dengan nama yang sama)
SELECT t1.field_1 AS alias_1, t2.field_2 AS alias_2, field_3
FROM table_1 AS t1
INNER JOIN table_2 AS t2
USING(field_4);
```

```sql
-- menggabungkan lebih dari 2 tabel
SELECT t1.field_1 AS alias_1, t2.field_2 AS alias_2, field_3
FROM table_1 AS t1
INNER JOIN table_2 AS t2
ON t1.field_4 = t2.field_5
INNER JOIN table_3 AS t3
ON t1.field_6 = t3.field_7;
```

```sql
-- menggunakan 2 Field sebagai syarat untuk Result Set
SELECT t1.field_1 AS alias_1, t2.field_2 AS alias_2, field_3
FROM table_1 AS t1
INNER JOIN table_2 AS t2
ON t1.field_4 = t2.field_5
INNER JOIN table_3 AS t3
ON t1.field_6 = t3.field_7
    AND t2.field_8 = t3.field_9;
```

### LEFT JOIN

```sql
-- untuk menampilkan seluruh Records pada tabel di sebelah kiri (meskipun NULL)
SELECT *
FROM table_1 AS t1
LEFT JOIN table_2 AS t2
USING(field);
```

### RIGHT JOIN

```sql
-- untuk menampilkan seluruh Records pada tabel di sebelah kanan (meskipun NULL)
SELECT *
FROM table_1 AS t1
RIGHT JOIN table_2 AS t2
USING(field);
```

### SELF JOIN

```sql
-- merelasikan tabel dengan dirinya sendiri
SELECT t1.field_1 AS alias_1, t2.field_2 AS alias_2, field_3
FROM table AS t1
INNER JOIN table AS t2
ON t1.field_4 = t2.field_4;
```

### FULL JOIN

```sql
-- menampilkan seluruh Records pada tabel yang di relasikan (seperti gabungan antara LEFT JOIN dan RIGHT JOIN)
SELECT *
FROM table_1 AS t1
FULL JOIN table_2 AS t2
USING(field);
```

### CROSS JOIN

```sql
-- mengembalikan semua kemungkinan dari kedua tabel yang sedang direlasikan
SELECT *
FROM table_1 AS t1
CROSS JOIN table_2 AS t2;
```

### COUNT

```sql
-- memberikan hasil dari seluruh Records
SELECT COUNT(*) AS count
FROM table;
```

```sql
-- memberikan hasil dari seluruh Records (tanpa NULL)
SELECT COUNT(field) AS count
FROM table;
```

```sql
-- memberikan hasil dari seluruh Records (tanpa NULL dan unik)
SELECT COUNT(DISTINCT field) AS count
FROM table;
```

### AGGREGATE FUNCTION

```sql
-- MIN untuk mencari nilai terkecil
SELECT MIN(field) AS alias
FROM table;
```

```sql
-- MAX untuk mencari nilai terbesar
SELECT MAX(field) AS alias
FROM table;
```

```sql
-- SUM untuk menghitung total pada Field
SELECT SUM(field) AS alias
FROM table;
```

```sql
-- AVG untuk menghitung rata-rata pada Field
SELECT AVG(field) AS alias
FROM table;
```

```sql
-- ROUND untuk membuat hasil dari Result Set memiliki angka desimal yang pasti (Number, Scale)
SELECT ROUND(AVG(field), value) AS alias
FROM table;
```

### GROUP BY - HAVING

```sql
-- mengelompokan hasil dari Result Set berdasarkan Field yang dipilih (untuk Aggregate Function)
SELECT field_1, AVG(field_2) AS alias
FROM table
GROUP BY field_1;
```

```sql
-- memfilter hasil dari Result Set dengan kriteria yang diinginkan menggunakan HAVING
SELECT field_1, AVG(field_2) AS alias
FROM table
GROUP BY field_1
HAVING AVG(field_2) operator value;
```

### UNION - UNION ALL

```sql
-- menampilkan data dari 2 tabel terpisah (duplikat Records akan dihitung 1)
SELECT *
FROM table_1
UNION
SELECT *
FROM table_2;
```

```sql
-- menampilkan data dari 2 tabel terpisah (seluruh Records akan dihitung termasuk yang duplikat)
SELECT *
FROM table_1
UNION ALL
SELECT *
FROM table_2;
```

### INTERSECT

```sql
-- menampilkan data antara 2 tabel terpisah (data yang sama diantara 2 tabel hanya dihitung 1)
SELECT *
FROM table_1
INTERSECT
SELECT *
FROM table_2;
```

### EXCEPT

```sql
-- menampilkan data pada tabel kiri yang tidak ada pada tabel kanan
SELECT *
FROM table_1
EXCEPT
SELECT *
FROM table_2;
```

### SEMI-JOIN

```sql
-- menggunakan Sub Query IN pada WHERE Clause
SELECT field_1, field_2
FROM table_1
WHERE field_3 = value
    AND field_2 IN (
        SELECT field_2
        FROM table_2
    );
```

### ANTI-JOIN

```sql
-- menggunakan Sub Query NOT IN pada WHERE Clause
SELECT field_1, field_2
FROM table_1
WHERE field_3 = value
    AND field_2 NOT IN (
        SELECT field_2
        FROM table_2
    );
```

### INSERT DATA

```sql
-- menambahkan data secara manual
INSERT INTO table (field_1, field_2)
VALUES (value_1, value_2);
```

```sql
-- migrasi data dari tabel lama ke tabel baru (pilihan Field tergantung kondisi)
INSERT INTO new_table
SELECT DISTINCT field_1, field_2
FROM old_table;
```

### UPDATE DATA

```sql
-- mengupdate data yang yang ada pada sebuah Record
UPDATE table
SET field_1 = value_1
WHERE field_2 = value_2;

```

```sql
-- mengupdate data menggunakan Field yang sudah ada dan digabungkan menggunakan CONCAT
UPDATE table
SET field_1 = CONCAT(field_1, field_2);
```

### INFORMATION SCHEMA

```sql
-- mengambil informasi dari seluruh tabel yang ada pada Database, baik itu dari public, pg_catalog dan information_schema
SELECT table_schema, table_name
FROM information_schema.tables;
```

```sql
-- mengambil data dari seluruh Field yang ada pada tabel tersebut
SELECT table_name, column_name, data_type
FROM information_schema.columns
WHERE table_name = table;
```

```sql
-- mengambil data dari seluruh View yang ada (dengan mengecualikan tampilan dari sistem)
SELECT *
FROM information_schema.views
WHERE table_schema NOT IN ('information_schema', 'pg_catalog');
```

### CREATE TABLE

```sql
-- membuat tabel pada database
CREATE TABLE table (
    field type
);
```

### ALTER TABLE

```sql
-- menambahkan Field jika tabel sudah terlanjur dibuat
ALTER TABLE table
ADD COLUMN field type;
```

```sql
-- merubah nama Field
ALTER TABLE table
RENAME COLUMN old_field TO new_field;
```

```sql
-- menghapus sebuah Field
ALTER TABLE table
DROP COLUMN field;
```

```sql
-- mengubah tipe data suatu Field
ALTER TABLE table
ALTER COLUMN field
TYPE type;
```

```sql
-- menggunakan USING untuk data numerik
ALTER TABLE table
ALTER COLUMN field
TYPE type
USING ROUND(field, value);
```

```sql
-- menggunakan USING untuk data karakter yang diperpendek
ALTER TABLE table
ALTER COLUMN field
TYPE type
USING SUBSTRING(field FROM 1 FOR value);
```

```sql
-- menambahkan NOT NULL pada kolom
ALTER TABLE table
ALTER COLUMN field
SET NOT NULL;
```

```sql
-- menghapus NOT NULL pada kolom
ALTER TABLE table
ALTER COLUMN field
DROP NOT NULL;
```

```sql
-- menambahkan CONSTRAINT UNIQUE untuk membuat suatu Field menjadi unik
ALTER TABLE table
ADD CONSTRAINT constraint UNIQUE (field);
```

```sql
-- menambahkan PRIMARY KEY pada suatu Field tanpa nama eksplisit
ALTER TABLE table
ADD PRIMARY KEY (field);
```

```sql
-- menambahkan PRIMARY KEY pada suatu Field dengan menggunakan nama eksplisit
ALTER TABLE table
ADD CONSTRAINT constraint PRIMARY KEY (field);
```

```sql
-- menambahkan FOREIGN KEY pada tabel
ALTER TABLE table_1
ADD CONSTRAINT constraint FOREIGN KEY (field_1) REFERENCES table_2 (field_2);
```

```sql
-- membuat Behavior Delete/Update menjadi CASCADE (data yang dihapus/diubah pada tabel A, juga akan dihapus/diubah pada tabel B)
ALTER TABLE table_1
ADD CONSTRAINT constraint FOREIGN KEY (field_1) REFERENCES table_2 (field_2)
ON DELETE/UPDATE CASCADE;
```

### DROP TABLE

```sql
-- menghapus tabel yang sudah tidak diperlukan
DROP TABLE table;
```

### CASTING DATA

```sql
-- untuk mengubah tipe data (misalnya untuk kebutuhan operasi matematika)
SELECT field_1 * CAST(field_2 AS type) AS alias
FROM table;
```

### VIEW

```sql
-- membuat VIEW untuk keperluan SELECT agar lebih cepat (Result Set yang diberikan akan selalu Realtime)
CREATE VIEW view AS
SELECT field_1, field_2
FROM table;
```

```sql
-- memanggil VIEW yang telah dibuat
SELECT *
FROM view;
```

```sql
-- menimpa View yang ada dengan syarat kondisi View wajib sama seperti sebelumnya dan Field baru ditambahkan di akhir
CREATE OR REPLACE VIEW view_new AS
SELECT field_1, field_2
FROM view_old;
```

### MATERIALIZED VIEW

```sql
-- membuat Materialized View dengan tujuan View yang diperbarui secara berkala (misalnya karena Query dari View sangat lama)
CREATE MATERIALIZED VIEW view AS
SELECT field_1, field_2
FROM table;
```

```sql
-- memperbarui Materialized View
REFRESH MATERIALIZED VIEW view;
```

### USER CONTROLLER

Pada User Controller ini, ada cara untuk memeberi akses dan menghapus akses pada suatu Role :

```sql
-- memberi akses
GRANT privilege ON object TO role
```

```sql
-- menghapus akses
REVOKE privilege ON object FROM role
```

Contoh pada Privilege dapat berupa :

- `SELECT`
- `INSERT`
- `UPDATE`
- `DELETE`

Kemudian pada Object dapat berupa :

- Table
- View
- Schema
- etc

Terakhir pada `role` yaitu User/Group yang diberi mandat

### ROLE

```sql
-- membuat Role
CREATE ROLE role;
```

```sql
-- contoh memberi peran lebih pada Role
CREATE ROLE role WITH LOGIN PASSWORD 'password' CREATEDB CREATEROLE VALID UNTIL '1970-1-1';
```

```sql
-- mengubah peran Role jika telah dibuat
ALTER ROLE role WITH LOGIN;
```

```sql
-- menambahkan suatu Role ke Group Role
GRANT group_role TO role;
```

```sql
-- menghapus suatu Role dari Group Role
REVOKE group_role FROM role;
```

### PARTITIONING

Terdapat 2 cara pada partisi yaitu Vertical dan Horizontal :

- Vertical = Mempartisi secara kolom (jika ada kolom yang dapat membuat tabel menjadi lambat jika di Query)
- Horizontal = Biasanya dipartisi berdasarkan waktu (misalnya per-tahun atau per-kuartal), jika diproses ditempat lain untuk Parallel Processing maka disebut dengan Sharding

```sql
-- contoh cara membuat tabel yang dapat dipartisi menggunakan RANGE
CREATE TABLE table (
    field type
) PARTITION BY RANGE (field);
```

```sql
-- contoh cara membuat tabel yang dapat dipartisi menggunakan RANGE
CREATE TABLE table (
    field type
) PARTITION BY LIST (field);
```

```sql
-- contoh cara membuat tabel misalnya untuk kuartal 3 tahun 2025 menggunakan FROM TO
CREATE TABLE table_2025_q3 PARTITION OF table
    FOR VALUES FROM (value_1) TO (value_2);
```

```sql
-- contoh cara membuat tabel misalnya untuk kuartal 3 tahun 2025 menggunakan IN
CREATE TABLE table_2025_q3 PARTITION OF table
    FOR VALUES IN (value);
```

```sql
-- disarankan untuk menambahkan Index pada Field yang telah dipartisi
CREATE INDEX ON table ('field');
```
