> Search for keytab files:

```
find / -type f \( -iname "*.keytab" -o -iname "krb5.keytab" -o -iname "*.kt" \) 2>/dev/null
```

> View the file:

```
klist -k -t <filename>
```

> We can also check in /tmp for krb5cc files which may allow us to pivot and login as a user without a password:

```
find / -name "krb5cc_*" -type f 2>/dev/null
```

> Krb5cc files have a string of numbers in the middle of the file name which we can use to get information about the user:

```
id <id>
```
