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

```bash
# Melihat isi File tanpa harus membuka Text Editor dengan Flag Number untuk melihat nomor baris
cat -n [file]
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

### Read Oldest, Newest and Global Regular Expression Print

```bash
# Melihat 10 baris pertama dari suatu File
head [file]
```

```bash
# Melihat 10 baris terakhir dari suatu File
tail [file]
```

```bash
# Melihat 10 baris terakhir dari suatu File dengan Real-Time menggunakan Flag Follow
tail -f [file]
```

```bash
# Melihat 50 baris pertama/terakhir dari suatu File menggunakan Flag Number
[head/tail] -n 50 [file]
```

```bash
# Contoh menyambungkan Command pertama ke Command kedua menggunakan Pipe
[cat/head/tail] [file] | grep [message]
```

```bash
# Mencari kata kunci tertentu dari suatu File
grep [message] [file]
```

```bash
# Mencari kata kunci tertentu dari suatu File menggunakan Flag Ignore Case atau Case Insensitive
grep -i [message] [file]
```

```bash
# Mencari kata kunci tertentu dari suatu File menggunakan Flag Number untuk melihat nomor baris yang dicari
grep -n [message] [file]
```

```bash
# Mencari kata kunci tertentu dari suatu File menggunakan Flag Regular Expression agar GREP dapat mengenali tanda dash/-
grep -e [-message] [file]
```

```bash
# Menggunakan kata kunci tertentu dari suatu File menggunakan Flag Ignore Case, Number dan Regular Expression sekaligus
grep -ine [message] [file]
```

```bash
# Contoh membuat File baru dengan hasil dari pencarian
grep [message] [file] > [file]
```

### Find File

```bash
# Mencari File dengan nama Case Sensitive
find [directory] -name "[file]"
```

```bash
# Mencari File dengan nama Case Insensitive
find [directory] -iname "[file]"
```

```bash
# Mencari File dengan nama Case Insensitive dan Wildcard
find [directory] -iname "[*.file]"
```

## User

```bash
# Melihat User (manusia) yang tersedia
cat /etc/passwd | grep -ie "/home/"
```

```bash
# Menambahkan User baru beserta Home Directory-nya
sudo useradd -m [user]
```

```bash
# Memberi Password pada User
sudo passwd [user]
```

```bash
# Menghapus User beserta Home Directory-nya
sudo deluser --remove-home [user]
```

```bash
# Pindah ke User lain
su - [user]
```

## File Permissions

- `-rwxrw-r--` = Contoh izin dari sebuah File
- `drwxrw-r--` = Contoh izin dari sebuah Directory

1. Karakter pertama dapat berupa `-` atau `d` yang menandakan bahwa itu adalah File atau Directory
2. Ketiga karakter selanjutnya atau `rwx` adalah milik User/Owner
3. Ketiga karakter selanjutnya atau `rw-` adalah milik Group
4. Ketiga karakter selanjutnya atau `r--` adalah milik Others

### Symbolic Mode and Octal Notation

| Subject           | Action    | Permissions   |
| -----             | -----     | -----         |
| `u` (user/owner)  | `+` (add) | `r` (read)    |
| `g` (group)       | `-` (sub) | `w` (write)   |
| `o` (others)      | `=` (set) | `x` (execute) |
| `a` (all)         |           | `` (clear)    |

| Permissions       | Symbol    | Value         |
| -----             | -----     | -----         |
| Read              | `r`       | 4             |
| Write             | `w`       | 2             |
| Execute           | `x`       | 1             |
| None              | `-`       | 0             |

### Change Mode

```bash
# Contoh penggunaan Symbolic Mode pada File dengan -rwxr-x--x (memberikan hak eksekusi pada semua pengguna)
chmod +x [file]
```

```bash
# Contoh penggunaan Symbolic Mode pada File dengan -rw----r--
chmod u=rw,g=,o=r [file]
```

```bash
# Contoh penggunaan Octal Notation pada File dengan -rw----r--
chmod 604 [file]
```

### Change Owner

```bash
# Mengubah kepemilikan suatu File ke Owner baru (wajib menggunakan SuperUser DO)
sudo chown [owner] [file]
```

```bash
# Mengubah kepemilikan suatu File ke Owner dan Group baru (wajib menggunakan SuperUser DO)
sudo chown [owner]:[group] [file]
```

## Process Management

### Background Process

```bash
# Menampilkan daftar seluruh proses yang sedang berjalan di sistem secara detail
ps aux
```

```bash
# Menampilkan daftar suatu proses yang sedang berjalan menggunakan GREP
ps aux | grep -ie [message]
```

### Force Stop

```bash
# Menghentikan suatu proses menggunakan Process ID
kill [pid]
```

```bash
# Menghentikan suatu proses secara paksa menggunakan Process ID dan Flag Force Kill
kill -9 [pid]
```

### Service / Daemon

```bash
# Mengecek layanan sedang berjalan
systemctl status
```

```bash
# Mengecek apakah suatu layanan sedang berjalan atau tidak
systemctl status [service]
```

```bash
# Menjalankan layanan secara manual
sudo systemctl start [service]
```

```bash
# Membuat layanan berjalan otomatis saat Server Reboot
sudo systemctl enable [service]
```

```bash
# Menghentikan layanan yang sedang berjalan
sudo systemctl stop [service]
```

```bash
# Membuat layanan tidak berjalan otomatis saat Server Reboot
sudo systemctl disable [service]
```

```bash
# Menghentikan total seluruh layanan lalu menjalankannya lagi dari awal (Less Downtime)
sudo systemctl restart [service]
```

```bash
# Membaca ulang berkas konfigurasi tanpa menghentikan layanan apapun (Zero Downtime)
sudo systemctl reload [service]
```
