> Proof files are always in /root or the Administrator desktop but sometimes local can be hard to find so these commands will find it for you and show the path:

**WIndows:**

```
Get-ChildItem -Path C:\ -Filter local.txt -Recurse -ErrorAction SilentlyContinue -Force
```

**Linux:**

```
find / -name local.txt 2>/dev/null
```
