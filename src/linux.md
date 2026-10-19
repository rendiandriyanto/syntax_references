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

### Resource Monitoring

```bash
# Menampilkan total penggunaan RAM dan Swap Memory yang terpakai dan tersisa Flag Human-Readable
free -h
```

```bash
# Menampilkan kapasitas ruang penyimpanan di seluruh partisi dengan Flag Human-Readable
df -h
```

```bash
# Menghitung total ukuran suatu Directory secara ringkas dengan Flag Human-Readable dan Flag Summary
du -sh [directory]
```

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
sudo kill [pid]
```

```bash
# Gunakan Kill All jika ingin menghentikan seluruh proses milik User tertentu
sudo killall -u [user]
```

```bash
# Menghentikan suatu proses secara paksa menggunakan Process ID dan Flag Force Kill
sudo kill -9 [pid]
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
# Menghentikan total suatu layanan lalu menjalankannya lagi dari awal (Less Downtime)
sudo systemctl restart [service]
```

```bash
# Membaca ulang berkas konfigurasi tanpa menghentikan layanan apapun (Zero Downtime)
sudo systemctl reload [service]
```

## Network

### Remote Server

```bash
# Digunakan untuk me-Remote menggunakan Secure SHell
ssh [username]@[ip]
```

```bash
# Digunakan untuk me-Remote menggunakan Secure SHell dan Flag Port jika Port SSH telah diubah
ssh [username]@[ip] -p [port]
```

### Socket Statistics

```bash
# Untuk melihat Port yang terbuka dan aplikasi apa yang sedang menggunakannya
sudo ss -tulpn
```

### Response Test

```bash
# Menguji dan melihat respon HTTP/HTTPS dari suatu alamat web
curl [web]
```

```bash
# Menguji dan melihat respon HTTP/HTTPS dari suatu alamat web dengan Flag Silent—seperti tanpa Verbose
curl -s [web]
```

```bash
# Menguji dan melihat respon HTTP/HTTPS dari suatu alamat web menggunakan Port
curl [web]:[port]
```

```bash
# Menguji dan melihat respon HTTP/HTTPS dari suatu alamat web dengan Header saja
curl -I [web]:[port]
```

```bash
# Melihat IP Address publik menggunakan Curl
curl -s ifconfig.me
```

```bash
# Melihat IP Address publik menggunakan Curl dengan lebih detail
curl -s ipinfo.io
```

### IP Address

```bash
# Digunakan untuk melihat IP Private dan Loopback
ip a
# atau
ip addr
```

```bash
# Digunakan untuk melihat kemana Default Gateway diarahkan
ip route
```

### PING

```bash
# Untuk mengetes koneksi menggunakan ICMP
ping [ip/domain]
```

```bash
# Untuk mengetes koneksi menggunakan ICMP dengan Flag Count
ping -c [number] [ip/domain]
```

### Telnet < Netcat

```bash
# Menggunakan Telnet untuk mengecek port apakah membalas atau tidak
telnet [ip/domain] [port]
```

```bash
# Menggunakan Netcat dengan Flag Zero-I/O (hanya mengetuk tanpa memberi paket) dan Flag Verbose (melihat detail)
nc -zv [ip/domain] [port]
```

```bash
# Menggunakan Netcat dengan Flag Zero-I/O (hanya mengetuk tanpa memberi paket), Flag Verbose (melihat detail) dan Timeout/Wait (tunggu)
nc -zvw [number] [ip/domain] [port]
```

```bash
# Menggunakan Netcat dengan Flag UDP, Flag Zero-I/O (hanya mengetuk tanpa memberi paket) dan Flag Verbose (melihat detail)
nc -uzv [ip/domain] [port]
```

```bash
# Menggunakan Netcat dengan Flag Listen (berperan sebagai penerima) dan Flag Verbose (melihat detail)
nc -lv [port]
```

### Traceroute & Tracepath (Time To Live (TTL) & RTT (Round Trip Time))

```bash
# Menggunakan Traceroute dengan paket default UDP (User Datagram Protocol) ke Port tinggi acak (biasanya di atas Port 33434)
traceroute [ip/domain]
```

```bash
# Menggunakan Traceroute dengan Flag Numeric agar mengembalikan hasil numerik IP saja dan tidak perlu Reverse DNS Lookup
traceroute -n [ip/domain]
```

```bash
# Menggunakan Traceroute dengan paket ICMP (Internet Control Message Protocol) ke Port tinggi acak (di atas Port 33434)
traceroute -I [ip/domain]
```

```bash
# Menggunakan Traceroute dengan paket TCP (Transmission Control Protocol) ke Port tinggi acak (di atas Port 33434)
sudo traceroute -T [ip/domain]
```

```bash
# Menggunakan Traceroute dengan paket default UDP (User Datagram Protocol) ke Port tertentu
traceroute -p [port] [ip/domain]
```

```bash
# Menggunakan Tracepath dengan UDP untuk melihat Path Maximum Transmission Unit (PMTU) dan melihat jalur pulang packet (Asymm)
tracepath [ip/domain]
```

### My TraceRoute (MTR)

```bash
# MTR menggunakan default ICMP untuk mengecek jalur secara Real-Time
mtr [ip/domain]
```

```bash
# Menggunakan TCP dan ICMP untuk mengecek jalur secara Real-Time
mtr --tcp [ip/domain]
```

```bash
# Menggunakan UDP dan ICMP untuk mengecek jalur secara Real-Time
mtr --udp [ip/domain]
```

### Network Mapping (NMAP)

```bash
# Default menggunakan Flag Scan dan Flag Stealth dengan Half-Open agar lebih cepat dan tidak tercatat di log tujuan
sudo nmap [ip/domain]
# atau
sudo nmap -sS [ip/domain]
```

```bash
# Menggunakan Flag Scan dan Flag TCP agar 3-Way Handshake SYN - SYN/ACK - ACK terjadi
sudo nmap -sT [ip/domain]
```

```bash
# Menggunakan Flag Scan dan Flag UDP
sudo nmap -sU [ip/domain]
```

```bash
# Menggunakan Flag Port agar menscan langsung Port tertentu
sudo nmap -p [port] [ip/domain]
```
