# Coding stuff
## Compiling a x86 DLL, CS/C#, with csc.exe and signing with a strong name key
```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /out:DLLNAME.dll /target:library /keyfile:C:\Users\User1\Desktop\YOURKEY.snk C:\Users\User1\Desktop\DLLNAME-source.cs /unsafe
```
