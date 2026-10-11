# Linux

![Linux](../images/linux.png)

Image by [Magnific](https://www.flaticon.com/free-icon/linux_518713)

***Credits*** :
> [Gemini](https://gemini.google.com/app) -
> [ID-Networkers (IDN.ID)](https://www.youtube.com/playlist?list=PLbLqbqNn7VYpZjf4i02hzlId7314OuM1Y)

## Explanation

- `/` (Root Directory) = Akar dari segala Directory pada sistem Linux
- `/home/[user]` (Home Directory) = Directory spesifik milik User biasa
- `.` (Current Directory) = Mewakili Directory yang sedang digunakan saat ini
- `..` (Parent Directory) = Mewakili Directory diatasnya
- Flag / Opsi = Digunakan untuk memberikan detail dari suatu Command
- `sudo` = SuperUser DO memberikan sementara hak akses Administrator tertinggi di Linux
- `sudo su` = SuperUser DO Switch User memberikan hak akses Administrator tertinggi di Linux
- PID (Process ID) = Nomor identitas unik dari setiap proses yang berjalan di latar belakang

## Shell Command

### Print Working Directory

```bash
# Untuk mengecek posisi kita berada di Directory mana saat ini
pwd
```

### List

```bash
# Untuk menampilkan daftar dari seluruh isi Directory saat ini
ls
```

```bash
# Menggunakan Flag List untuk menampilkan rincian dari setiap File
ls -l
```

```bash
# Menggunakan Flag List juga namun terfokus pada satu atau lebih file
ls -l [file_1] [file_2]
```

```bash
# Menggunakan Flag All untuk menampilkan seluruh File saat ini (termasuk Hidden File)
ls -a
```

```bash
# Menggunakan Flag List dan All untuk menampilkan seluruh File sekaligus rincian dari setiap File
ls -la
```

### Change Directory

```bash
# Digunakan untuk berpindah Directory
cd [directory]
```

```bash
# Digunakan untuk berpindah ke Parent Directory
cd ..
```

```bash
# Digunakan untuk berpindah ke Home Directory
cd ~
# atau
cd
```

```bash
# Digunakan untuk berpindah ke Root Directory
cd /
```

### Make Directory

```bash
# Membuat Directory baru
mkdir [directory]
```

### Make File

```bash
# Membuat File / memperbarui Timestamp pada File yang sudah ada
touch [file]
```

```bash
# Membuat File dengan mengatur Timestamp ke waktu spesifik
touch -t YYYYMMDDhhmm.ss [file]
```

### Read File

```bash
# Melihat isi File tanpa harus membuka Text Editor
cat [file]
```

### Copy File or Directory

```bash
# Menyalin sebuah File
cp [file] [file_new]
```

```bash
# Menyalin sebuah File ke Directory tertentu
cp [file] [directory]
```

```bash
# Menyalin Directory menggunakan Flag Recursive agar folder dibawahnya juga ikut tersalin
cp -r [directory] [directory_new]
```

### Move or Rename into File or Directory

```bash
# Memindahkan File/Directory ke Directory lain
mv [file/directory] [directory]
```

```bash
# Mengubah nama File/Directory ke nama yang baru
mv [file/directory] [file_new/directory_new]
```

### Remove

```bash
# Menghapus sebuah File
rm [file]
```

```bash
# Menghapus sebuah File dengan menggunakan Flag Interactive agar system bertanya y/n terlebih dahulu
rm -i [file]
```

```bash
# Menghapus sebuah Directory dengan menggunakan Flag Recursive agar semua terhapus
rm -r [directory]
```

```bash
# Menghapus sebuah Directory dengan menggunakan Flag Recursive dan Force agar semua terhapus dengan paksa
rm -rf [directory]
```

### Echo / Output Redirection

```bash
# Menulis dengan menimpa/Overwrite seluruh isi File
echo [message] > [file]
```

```bash
# Menulis dengan menambahkan/Append tulisan dibaris paling bawah
echo [message] >> [file]
```
