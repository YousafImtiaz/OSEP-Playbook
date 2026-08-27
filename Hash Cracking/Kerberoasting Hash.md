> Place the hash in a file and make sure to tab everything over to line it up then clean up the file to be one string:

```
cat hash.txt | tr -d '\n\r' | tr -d ' ' > hash_clean.txt 
```

> Now we can crack it:

```
sudo hashcat -m 13100 -a 0 hash_clean.txt /usr/share/wordlists/rockyou.txt --force
```
