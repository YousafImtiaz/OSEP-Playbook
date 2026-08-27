> With password:

```
netexec <module> <ip_subnet> -u <user> -p '<pass>' <--local-auth> --continue-on-success
```

> With hash:

```
netexec <module> <ip_subnet> -u <user> -H <hash> --local-auth --continue-on-success 
```

> Specify Domain (Make sure to try with different domain trusts):

```
netexec <module> <ip_subnet> -u <user> -p <pass> -d <domain> --continue-on-success
```

> Protocols that you could try spraying across:

```
smb
ssh
ftp
winrm
rdp
mssql
```