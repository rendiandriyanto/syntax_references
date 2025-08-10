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
- INT (Integer) = Tipe data untuk bilangan bulat
- NUMERIC (Float) = Tipe data untuk bilangan pecahan

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
