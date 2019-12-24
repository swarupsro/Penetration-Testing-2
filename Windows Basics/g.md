   ## WMIC commands
   
   #### Get System Roles, User Name, and Manufacturer
```Bash
 > wmic computersystem get Name, domain, Manufacturer, Model, Username, Roles /format:list
  ```
   #### Get the SIDs
```Bash
 > wmic group get Caption, InstallDate, LocalAccount, Domain, SID, Status
  ```
   #### Create a process
```Bash
 > wmic process call create "taskmgr.exe"
  ```
   #### Change Priority of a Process
```Bash
 > wmic process where name="explorer.exe" call setpriority 64
  ```
   #### Terminate a process 
```Bash
 > wmic process where name="explorer.exe" call terminate
  ```
   #### Get a list of Executable Files
```Bash
 > wmic PROCESS WHERE "NOT ExecutablePath LIKE ‘%Windows%’" GET ExecutablePath
  ```
   #### Get Folder Properties
```Bash
 > wmic FSDIR where "drive='c:' and filename='test" get /format:list
  ```
   #### Get File Properties
```Bash
 > wmic datafile where name='c:\\windows\\system32\\demo\\demo.txt' get /format:list
  ```
   #### Locate System Files
```Bash
 > wmic environment get Description, VariableValue
  ```
   #### Get a list of Installed Applications 
```Bash
 > wmic product get name
  ```
   #### Get a list of Running Services
```Bash
 > wmic service where (state="running") get caption, name, startmode, state
  ```
   #### Get Startup Services
```Bash
 > wmic startup get Caption, Command
  ```
   #### Get System Driver Details
```Bash
 > wmic sysdriver get Caption, Name, PathName, ServiceType, State, Status /format:list
  ```
   #### Get OS Details
```Bash
 > wmic os get CurrentTimeZone, FreePhysicalMemory, FreeVirtualMemory, LastBootUpdate, NumberofProcesses, NumberofUsers,
  ```
   #### Organization, Registereduser, Status /format:listGet the Motherboard Details
```Bash
 > wmic baseboard get Manufacturer, Product, SerialNumber, Version
  ```
   #### Get BIOS Serial Number
```Bash
 > wmic bios, get serialNumber
  ```
   #### Get Hard Disk Details
```Bash
 > wmic diskdrive get Name, Manufacturer, Model, InterfaceType, MediaLoaded, MediaType /format:list
  ```
   #### Get Hard Disk Partitions Details
```Bash
 > wmic logicaldisk where drivetype=3 get Name, Compressed, Description, FileSystem, FreeSpace, SupportsDiskQuotas, VolumeDirty
  ```
   #### Get Memory Cache Details
```Bash
 > wmic memcache get Name, BlockSize, Purpose, MaxCacheSize, Status
  ```
   #### Get Memory Chip Details
```Bash
 > wmic MEMORYCHIP get PartNumber, SerialNumber
  ```
   #### Detect If victim system is a host OS or installed via VMware
```Bash
 > wmic onboarddevice get Desciption, DeviceType, Enabled, Status /format:list
  ```
   #### Lock a User Account
```Bash
 > wmic useraccount where name='demo' set disabled=false
  ```
   #### Remove Password requirement for logging
```Bash
 > wmic useraccount where name='demo' set PasswordRequired=false
  ```
   #### Rename a user account
```Bash
 > wmic useraccount where name='demo' rename hacker
  ```
   #### Restrict user from changing a password
```Bash
 > wmic useraccount where name='hacker' set passwordchangeable=false
  ```
   #### Get Antivirus Details
```Bash
 > wmic /namespace:\\root\securitycenter2 path antivirusproduct GET displayName, productState, pathToSignedProductExe
  ```
   #### Clear System Logs
```Bash
 > wmic nteventlog where filename='system' call cleareventlog
  ```
  ## File commands
  
   #### Show contents
```Bash
 > dir
  ```
   #### Dir creation
```Bash
 > mkdir c:\temp
  ```
   #### Fie creation
```Bash
 > echo hey > cmd.exe
  ```
   #### Delete a file
```Bash
 > del cmd.exe
  ```
   #### Open text file
```Bash
 > notepad file.txt
  ```
   #### Clear the screen
```Bash
 > cls
  ```
   #### Change directory
```Bash
 > cd 
  ```
   #### Find particular string in output
```Bash
 > sc query | find "Event"
  ```
   #### Show contents of a file
```Bash
 > type c:\windows\win.ini
  ```
   #### Command history
```Bash
 > Alt+F7
  ```
   #### How many files are in system32
```Bash
 > dir /b c:\windows\system32 | find /c /v ""
  ```
   #### What is the length of ini file
```Bash
 > type c:\windows\win.ini | find /c /v ""
  ```
   #### Find hidden directory
```Bash
 > dir /aHD
  ```
   #### Searching file
```Bash
 > dir /b /s c:\ | find /i "wmic.exe"
 > dir /b /s wmic.exe
 > dir /b /s *wmic*
 > dir /b /s c:\wmic.exe
  ```
   #### Searching file conents
```Bash
 > findstr /d:c:\windows/system32 "Admin" *
 > findstr "Admin" *.ini
  ```
  
  ## User account commands
  
   #### To view a list of user accounts on the system
```Bash
 > net user
  ```
   #### Create a user account with a specific privilege
```Bash
 > net user Username Password /add
  ```
   #### Add the user to a particular group such as Administrator, Power User or Limited User
```Bash
 > net localgroup GroupPrivilege UserName /add
  ```
   #### To enable the built-in Administrator account, which you can use to manage all the resources of your computer.
```Bash
 > net user administrator /active:yes
 > net user administrator /active:no
  ```
   #### Account details
```Bash
 > net user UserName
  ```
   #### Account deletion
```Bash
 > net user UserName /del
  ```
  ## Proccess/Service commands
   #### Show running process
```Bash
 > tasklist
 > tasklist /src
 > tasklist /fi "imagename eq cms.exe" /m
 > tasklist /m ntdll.dll
  ```
   #### Kill process
```Bash
 > taskkill /PID [pid]
 > taskkill /PID [pid] /PID [pid2]
 > taskkill /IM cmd.exe
  ```
   #### Stop services
```Bash
 > sc query dhcp
 > sc stop dhcp
  ```
  ## Run Commands
   #### Computer management
```Bash
 > compmgmt.msc
  ```
   #### Device manager
```Bash
 > devmgmt.msc
  ```
   #### Disk management
```Bash
 > diskmgmt.msc
  ```
   #### Disk defrag
```Bash
 > dfrg.msc
  ```
   #### Event viewer
```Bash
 > eventvwr.msc
  ```
   #### Shared folders
```Bash
 > fsmgmt.msc
  ```
   #### Group policies
```Bash
 > gpedit.msc
  ```
   #### Local users and groups
```Bash
 > lusrmgr.msc
  ```
   #### Performance monitor
```Bash
 > perfmon.msc
  ```
   #### Resultant set of policies
```Bash
 > rsop.msc
  ```
   #### Local security settings
```Bash
 > secpol.msc
  ```
   #### System Configuration Utility
```Bash
 > msconfig
  ```
   #### Registry Editor
```Bash
 > regedit
  ```
   #### System Information
```Bash
 > msinfo32
  ```
   #### System Edit
```Bash
 > sysedit
  ```
   #### windows loading information(also system.ini)
```Bash
 > win.ini
  ```
   #### Shows current version of windows
```Bash
 > winver
  ```
   #### Opens default email client
```Bash
 > mailto:
  ```
   #### Opens command prompt
```Bash
 > command
  ```
  ## Run Commands to access the control panel
   #### Add/Remove Programs control
```Bash
 > appwiz.cplrc
  ```
   #### Date/Time Properties control
```Bash
 > timedate.cpl
  ```
   #### Display Properties control
```Bash
 > desk.cpl
  ```
   #### FindFast control
```Bash
 > findfast.cpl
  ```
   #### Internet Properties control
```Bash
 > inetcpl.cpl
  ```
   #### Keyboard Properties control
```Bash
 > main.cpl
  ```
   #### Mouse Properties control
```Bash
 > main.cpl
  ```
   #### Network Properties control
```Bash
 > netcpl.cpl
  ```
   #### Password Properties control
```Bash
 > password.cpl
  ```
   #### Sound Properties control
```Bash
 > mmsys.cpl
  ```
   #### System Properties control
```Bash
 > sysdm.cpl
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
     #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
   #### 
```Bash
 > 
  ```
