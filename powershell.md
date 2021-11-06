# Powershell Cheatsheet
### Common Verbs (aliases)
```powershell
GET (g)
Start (sa)
Stop (sp)
Read (rd)
Write (wr)
New (n)
Out (o)
```
### Help
```powershell
# get command examples
Get-Help Get-Command -Examples
# list all installed GET cmdlets, allows for pattern matching
Get-Command Get-*
# list all installed Job cmdlets, allows for patter matching
Get-Command *-Job
```
### Object Manipulation with `|`: instead of passing around text or strings like other shells, powershell uses Objects
```powershell
# view member methods for Get-Command
Get-Command | Get-Member -MemberType Method
# view member properties for Get-Command
Get-Command | Get-Member -MemberType Properties
# create new object from properties with Select-Object
Get-ChildItem | Select-Object -Property Mode, Name
```
### Filter Objects with `Where-Object`
```powershell
# list stopped processes
Get-Service | Where-Object -Property Status -eq Stopped
```
### Enumeration
```powershell
# get list of local users
Get-WmiObject -Class Win32_UserAccount -Filter  "LocalAccount='True'" | select name, fullname, sid, passwordrequired
# get count of local groups / Measure-Object is similar to unix wc 
Get-LocalGroup | Measure-Object
# list members of "Advministrators" group
Get-LocalGroupMember -Group "Administrators" 
# ip info
Get-NetIpAddress
# open/listening ports
Get-NetTCPConnection -State Listen
netstat -a | Select-String listening | Measure-Object
# list installed updates/patches
Get-HotFix
# list running processes
Get-Process
# show file/directory permissions
Get-ACL C:\
# recursive grep
Get-ChildItem c:\ -Recurse | Select-String -Pattern "pattern" -CaseSensitive
```

### Get-WinEvent
```powershell
# Get WLMS events with System time of '2020-12-15T01:09:08.940277500Z'
Get-WinEvent -LogName "Application" -FilterXPath '*/System/Provider[@Name="WLMS"] and */System/TimeCreated[@SystemTime="2020-12-15T01:09:08.940277500Z"]'
# Get security events for username Sam with an event id of 4720
Get-WinEvent -LogName "Security" -FilterXPath '*/EventData/Data[@Name="TargetUserName"]="Sam" and */System/EventID=4720'
```

### Useful Misc Commands
```powershell
# print working directory
Get-Location
# grep for windows
Select-String 
# download file from http server
Invoke-WebRequest -Uri <URL> -OutFile <output-location> 
# alias for `Invoke-WebRequest`
iwr 
# list all event logs on the system
Get-EventLog -List 
# start a process
Start-Process <process name> 
# stop a"process" 
Stop-Process <process name> 
# create new user with 'username' & 'password'
New-LocalUser "username" -Password "password" 
```
