Once you land on a webpage or an endpoint make sure to view the page source to see the framework in place and find other useful information that may be present. 

> We can also do some light directory enumeration to find endpoints:

```
gobuster dir -u http://<ip>/ -w /usr/share/wordlists/dirb/common.txt -x pdf,text,html,php -t 5  
```