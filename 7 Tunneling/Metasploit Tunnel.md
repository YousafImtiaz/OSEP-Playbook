> After we have a shell connection in meterpreter, we can send it to the background then configure the proxy:

```
background

use multi/manage/autoroute

set session 1

exploit
```

> Once the route is added we can setup the socks:

```
use auxiliary/server/socks_proxy

try this first: set srvhost 0.0.0.0
Alternative: set srvhost 127.0.0.1

show options
```

> Now we can edit our to our proxychains.conf file:

```
sudo nano /etc/proxychains.conf

socks5 127.0.0.1 1080
```

> Now we can start the tunnel:

```
run
```
