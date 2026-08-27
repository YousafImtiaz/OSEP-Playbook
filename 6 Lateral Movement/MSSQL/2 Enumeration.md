> **Enumerate linked servers:**

```
enum_links;
```

> **Show all databases:**

```
SELECT name FROM sys.databases;
```

> **View tables in a database:**

```
USE <database>;
```

```
SELECT * FROM <table name>.information_schema.tables;
```

> **View entries in a table:**

```
select * from <catalog>.<schema>.<name>;
```

> Query linked servers:

```
SELECT name FROM sys.servers;
```

> Check for possible impersonation:

```
SELECT distinct b.name FROM sys.server_permissions a INNER JOIN sys.server_principals b ON a.grantor_principal_id = b.principal_id WHERE a.permission_name = 'IMPERSONATE'
```

> If we have impersonation then we can impersonate and then repeat the enumeration steps:

```
exec_as_login <user>
```
