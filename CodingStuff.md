# Coding stuff
## Compiling a x86 DLL, CS/C#, with csc.exe and signing with a strong name key
```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /out:DLLNAME.dll /target:library /keyfile:C:\Users\User1\Desktop\YOURKEY.snk C:\Users\User1\Desktop\DLLNAME-source.cs /unsafe
```
## Retreive the PublicToken, Version and Culture of your DLL via Powershell
```
([system.reflection.assembly]::loadfile("C:\Full_Path\MyDLL.dll")).FullName
```
