   ## Networking Commands
   
   #### Displays IP address
```Bash
 > ipconfig
  ```
  #### Change ip address
```Bash
 > netsh int ip set address "Local area connection" static 192.168.10.10 255.255.255.0 192.168.10.1
  ```
   #### Displays the system's local DNS cache
```Bash
 > ipconfig /displaydns
  ```
   #### Displays the full information about the system's network interface cards (NICs).
```Bash
 > ipconfig /all
  ```
 #### Lists all the systems currently in the machine's ARP table.
```Bash
 > arp -a
  ```
   #### Show firewall settings
```Bash
 > netsh firewall show config
  ```
   #### Retrieve information about Domain and Domain Controller
```Bash
 > wmic ntdomain list
  ```
   #### Prints the password policy for the local system. Pass it the /domain option to query the domain for the domain password policy
```Bash
 > net accounts [/domain | /domain:OTHERDOMAINNAME]
  ```
   #### Prints the members of the Administrators local group. The /domain switch can show you the list of current domain admins
```Bash
 > net group "GROUPNAME" /domain
  ```
   #### Prints the members of the local group "GROUPNAME". The /domain switch can show you members of domain groups
```Bash
 > net localgroup "GROUPNAME" [/domain]
  ```
   #### Queries NBNS/SMB (SAMBA) and tries to find all hosts in the system's current workgroup. Add the /domain option if the current system is joined to a domain. To query a different domain, use the /domain:OTHERDOMAINNAME option
```Bash
 > net view [/domain | /domain:OTHERDOMAINNAME]
  ```
   #### Displays the system's currently shared SMB entries, and what path(s) they point to
```Bash
 > net share
  ```
   #### Lists the local users or, if the /domain option is passed, users on the computer's domain
```Bash
 > net user [/domain]
  ```
   #### Lists detailed information about the current local user or, if the /domain option is passed, the account on the computer's domain. If it is a local user then drop the /domain. Important things to note are login times, last time changed password, logon scripts, and group membership. You may wish to run this twice, once with and once without the /domain switch to find both local and domain accounts
```Bash
 > net user %USERNAME% [/domain]
  ```
   #### Shows information on network services and adapters
```Bash
 > netsh diag show all
  ```
   #### Shows all saved wireless profiles. You may then export the info for those profiles with the other netsh commands listed here
```Bash
 > netsh wlan show profiles
  ```
   #### Shows saved wireless profile with password
```Bash
 > netsh wlan show profile name="SSID" key=clear
  ```
   #### Find Information about a specific Service
```Bash
 > netstat -nabo | findstr /I (SERVICE|PROCESS|PORT)
  ```
   #### Find all listening ports and connections on port 80 (replace 80 with your target such as 445 or 3389)
```Bash
 > netstat -na | findstr :80
  ```
   #### Find all listening ports and their associated PIDs (Process IDs). The findstr /I switch makes the search case insensitive. This could be important if you are looking for a buMPy service (example: svchost vs. SVChost) or don't know the case of it
```Bash
 > netstat -nao | findstr /I listening
  ```
   #### List Ports and Connections
```Bash
 > netstat -nabo
  ```
   #### Displays the system's routing table
```Bash
 > netstat -r
  ```
   #### Another handy thing you can do with ipconfig is flush the DNS resolver cache. This can be helpful when a system is resolving DNS addresses incorrectly. You can flush the DNS cache by using this command:
```Bash
 > ipconfig /flushdns
  ```
   #### Assuming that the system has acquired its IP address from a DHCP server, you can use the ipconfig command to release and then renew the IP address. Doing so involves using the following commands:
```Bash
 > ipconfig /release
 > ipconfig /renew
  ```
   #### Traces the route it takes for a packet to reach a destination.
```Bash
 > tracert google.com
  ```
   #### Type ping google.com and Windows will send packets to Google.com
```Bash
 > ping google.com
  ```
  
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
 or
 > hdwwiz.cpl
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
