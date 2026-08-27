> After port forwarding we can login if we have credentials:

```
mysql -h 127.0.0.1 -P 3306 -u root -p
```

> Basic navigation commands:

```
show databases;
use <database>;
show tables;
describe <tablename>;
```

> Once we are in a table where we want to extract information:

```
select * from <table_name>;
```
