**Make sure to use nslookup if you want the IP Address for a machine** 

> View terminal history in Powershell:

```
history
```

> Also look the environmental variables in powershell to see if there may be a password there:

```
dir env:
```

> In CMD you can check for stored credentials using:

```
cmdkey /list
```


**Directories to check for interesting files:** (Use `icacls` to check permissions you have on the file):

```
C:\ Drive
C:\inetpub\wwwroot
C:\inetpub\logs
C:\inetpub (serach for web.config file)
C:\Tasks
C:\users\<user>\<folders> (check for .ssh keys) (check for known hosts)
C:\TEMP
```

> **Check Scheduled tasks:**

```
Get-ScheduledTask | where {$_.TaskPath -notlike "\Microsoft*"} -Verbose
```

Query task information if you find an unusual task running:

```
schtasks /query /tn "<task_name>" /fo LIST /v
```

> Check for domain trusts:

```
nltest /trusted_domains
```
