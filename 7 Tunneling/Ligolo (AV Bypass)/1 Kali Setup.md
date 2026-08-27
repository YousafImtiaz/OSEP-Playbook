```
sudo ip tuntap add user kali mode tun ligolo 
```

```
sudo ip link set ligolo up
```

```
sudo ./proxy -selfcert
```

> If we ever need to delete the interface:

```
sudo ip tuntap del dev ligolo mode tun
```


