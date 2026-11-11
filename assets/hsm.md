# Hardware Security Module (HSM)

## Simulasi HSM dan penerapan pada aplikasi FOSS Linux

### 3 Perbedaan HSM Token

- *Smart Card* = Kartu pintar fisik yang dipegang oleh Key Custodian dan dibuat saat Key Ceremony (digunakan untuk pembuatan Local Master Key)
- *Logic Partition PKCS#11* = Partisi(slot) logis pada HSM untuk menyimpan LMK, Asymmetric Key dan ZMK pada slot tertentu
- *USB Dongle HSM* = Digunakan untuk Multi-Factor Authentication

Pada alur yang terjadi di Hardware Security Module :

```text
1. Node A kirim pesan
2. Masuk ke slot PKCS#11 menggunakan User PIN
3. Memanggil Asymmetric Key untuk tanda tangan dan ZMK untuk enkripsi (proses ini dilindungi oleh LMK)
```

### Simulasi singkat pada Linux

- `sofths2 & opensc` = Menggunakan tools FOSS untuk mensimulasi perintah HSM
- `sudo softhsm2-util --show-slots` = Untuk melihat slot/token yang terdaftar
- `sudo softhsm2-util --init-token --slot 0 --label "LEARNING_TOKEN" --so-pin 123456 --pin 654321` = Membuat slot/token baru bernama LEARNING_TOKEN dengan PIN Security Officer (Administrator untuk konfigurasi) dan PIN User (Aplikasi yang menggunakan)
- `sudo pkcs11-tool --module /usr/lib/softhsm/libsofthsm2.so -l --pin 654321 --keypairgen --key-type rsa:2048 --label "LEARNING_KEY"` = Membuat Asymmetric Key yang akan digunakan oleh User dengan PIN User

Pada simulasi ini, kita tidak menggunakan LMK (karena membutuhkan Smart Card), Zone Master Key (karena digunakan untuk untuk enkripsi data transaksi) dan USB Dongle (karena digunakan untuk MFA login)
