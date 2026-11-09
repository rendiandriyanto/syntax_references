# Windows

![Windows](../images/windows.png)

Image by [Magnific](https://www.magnific.com/icon/windows_232411)

***Credits*** :
> [Gemini](https://gemini.google.com/app)

## PowerShell

Penggunaan perintah pada *PowerShell* menggunakan *Verb-Noun* (kata kerja-kata benda) yang terstruktur dan mudah dibaca. Seperti contoh beberapa *Command* dibawah ini yang ***Equivalent***/setidaknya hampir mirip dengan **Linux** :

### Computer

```bash
# Memulai ulang komputer
Restart-Computer
# Linux
sudo reboot
```

### Process ID

```bash
# Menghentikan proses
Stop-Process -Id [PID]
# Linux
kill [PID]
```

```bash
# menggunakan netstat yang Equivalent dengan ss
netstat -ano | findstr "LISTENING"
# atau membuka + resmon.exe agar dapat mencocokan PID dan tampilan seperti HTOP
# Linux
ss -tuln | grep "LISTEN"
# sudo ss -tulpn untuk hasil yang setara + htop
```

### Service

```bash
# Melihat semua Service
Get-Service
# atau membuka services.msc untuk GUI
# Linux
systemctl list-units --type=service --all
```

```bash
# Melihat status Service
Get-Service [service]
# Linux
systemctl status [service]
```

```bash
# Memulai Service
Start-Service [service]
# Linux
sudo systemctl start [service]
```

```bash
# Menghentikan Service
Stop-Service [service]
# Linux
sudo systemctl stop [service]
```

```bash
# Memulai ulang Service
Restart-Service [service]
# Linux
sudo systemctl restart [service]
```

### Log

```bash
# Membuka Event Viewer GUI
eventvwr.msc
# Linux
journalctl
```

### Networking

```bash
# PING—Internet Control Message Protocol
ping -n [number] [ip/domain]
# Linux
ping -c [number] [ip/domain]
```

```bash
# Telnet yang Equivalent
telnet [ip/domain] [port]
# Linux
telnet [ip/domain] [port]
```

```bash
# Melihat apakah Port terbuka atau tidak
Test-NetConnection -ComputerName [ip/domain] -Port [port]
tnc [ip/domain] -Port [port]
# Linux
nc -zv [ip/domain] [port]
```

```bash
# Traceroute dengan hasil numerik tanpa Reverse DNS Lookup
tracert -d [ip/domain]
# Linux
traceroute -n [ip/domain]
```

```bash
# Path yang mirip
pathping [ip/domain]
# Linux
tracepath [ip/domain]
```
