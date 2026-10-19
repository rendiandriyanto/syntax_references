# Windows

![Windows](../images/windows.png)

Image by [Magnific](https://www.magnific.com/icon/windows_232411)

***Credits*** :
> [Gemini](https://gemini.google.com/app) -
> [ChatGPT](https://chatgpt.com/)

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

### Service

```bash
# Melihat semua Service
Get-Service
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
