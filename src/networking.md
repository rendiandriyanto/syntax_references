# Networking

![Networking](../images/networking.png)

Image by [Eucalyp](https://www.magnific.com/icon/computer_3598209)

***Credits*** :
> [Gemini](https://gemini.google.com/app) -
> [Hostinger Indonesia](https://www.youtube.com/watch?v=Wz4GVpb0Tns)

## IP Address (Internet Protocol Address)

***Internet Protocol Address*** adalah sebuah alamat yang ditujukan untuk sebuah perangkat agar dapat berkomunikasi baik melalui jaringan publik maupun jaringan lokal. Terdapat jenis-jenis dari IP Address yakni versi dan aksesibilitas.

**Versi** :

- *IPv4* = Menggunakan format 32-bit (contoh 35.74.126.45), 4 blok dari rentang angka 0 - 255.
- *IPv6* = Menggunakan format 128-bit (contoh 2001:db8:86a7::37:7469), 8 blok dari rentang 0000 - ffff.

**Aksesibilitas** :

- *IP Public* = Jenis yang digunakan untuk berkomunikasi dengan jaringan Internet.
- *IP Private* = Jenis yang digunakan untuk berkomunikasi dengan jaringan lokal.

## Subnetting

***Subnetting*** adalah teknik untuk memecah jaringan yang besar menjadi jaringan yang lebih kecil (Subnet). Terdapat beberapa istilah penting dalam materi Subnetting, yaitu :

- *IP Address* = Angka 32-bit (IPv4) yang menjadi alamat unik pada setiap perangkat dalam sebuah jaringan.
- *Subnet Mask* = Penentu jarak batas tiap blok, yang membedakan bagian jaringan dan bagian perangkat.
- *Network Address* = Alamat awal pada tiap Subnet, digunakan untuk mewakili identitas sebuah jaringan.
- *Broadcast Address* = Alamat akhir pada tiap Subnet, digunakan untuk mengirim pesan/data ke seluruh perangkat pada sebuah jaringan.
- *Host ID* = Porsi alamat IP yang digunakan untuk mengenali setiap perangkat pada sebuah jaringan Subnet.
- *CIDR (Classless Inter-Domain Routing)* = Cara penulisan notasi ringkas jumlah bit (Subnet Mask), seperti contoh /8, /16 dan /24.
- *VLSM (Variable Length Subnet Mask)* = Teknik untuk membagi jaringan sesuai kebutuhan Host ID pada sebuah Subnet.

Berikut adalah penjelasan tentang cara Subnetting untuk `192.168.10.69/27` kelas C, untuk kelas B dan A metodenya tetap sama, namun hanya digeser ke oktet sebelumnya saja :

1. **Cari Subnet Mask** = Notasi /27 berarti ada 27-bit angka 1 dalam total 32-bit, sisanya adalah angka 0. Maka dalam biner berarti `11111111.11111111.11111111.11100000` atau dalam desimal oktet ke-1, ke-2 dan ke-3 adalah `255.255.255` dan oktet ke-4 adalah `224`, didapat dari perhitungan angka biner 1 pada oktet ke-4 menjadi `2^7 + 2^6 + 2^5 = 128+64+32 = 224`. Maka hasil Subnet Mask desimal-nya adalah `255.255.255.224`.
2. **Mendapatkan nilai x dan y** = Menggunakan x dan y, `x adalah biner 1 dan y adalah biner 0`. Didapatkan dari oktet ke-4 dengan biner `11100000`, yang berarti **x** adalah `3` dan **y** adalah `5`.
3. **Menghitung jumlah Subnet** = Menggunakan rumus `2^x`, untuk menghitung berapa blok Subnet/jaringan kecil yang dapat terbentuk. Karena tadi hasil x adalah 3, maka didapatkan hasil `2^3 = 2*2*2 = 8` jaringan yang dapat terbentuk.
4. **Menghitung jumlah Host per Subnet** = Menggunakan rumus `2^y-2` untuk menghitung berapa banyak Host yang dapat ditampung oleh sebuah Subnet. Sebelumnya y adalah 5, berarti perhitungannya adalah `2^5-2 = 32-2 = 30` Host/perangkat yang bisa terhubung dalam Subnet, `-2` dialokasikan untuk **Network Address** dan **Broadcast Address**.
5. **Mencari batas blok Subnet** = Menggunakan hapalan seperti `/24=256, /25=128, /26=64, /27=32, /28=16 dan seterusnya` atau rumus `256 - nilai desimal oktet terakhir Subnet Mask` yang berarti `256-224 = 32`. Kelompok Subnet akan meloncat setiap 32 angka, dimulai dari 0 seperti `0, 32, 64, 96 dan seterusnya`.
6. **Network Address** selalu mengambil alamat IP pertama disetiap Subnet. Karena alamat IP diatas adalah `.69`, maka alamat tersebut berada direntang loncatan antara 64 sampai 96, yang artinya Network Address nya adalah `192.168.10.64`.
7. **Broadcast Address** selalu mengambil alamat IP terakhir disetiap Subnet. Karena alamat IP diatas adalah `.69`, maka alamat tersebut berada direntang loncatan antara 64 sampai 96, yang artinya Broadcast Address nya adalah `192.168.10.95`.
