Check all services on PC <br>
```powershell
Get-Service
```
<br>

Get a specific service <br>
```powershell
Get-Service *WSearch*  | Select-Object Name, DisplayName, Status, StartType
```
<br>

Stop a specific service, make sure to run Powershell as admin <br>
Stopping SysMain and/or WSearch helps with Task Manager Disk Performance <br>
```powershell
Stop-Service -Name SysMain
Stop-Service -Name WSearch
```
<br>

Start a specific service, , make sure to run Powershell as admin <br>
```powershell
Start-Service -Name WSearch
```
<br>

Restart a specific service, , make sure to run Powershell as admin <br>
Rarely, but sometimes a service isn't running properly. You can also restart computer. <br>
```powershell
Restart-Service -Name Spooler
```
<br>



Set a specific service to Automatic, make sure to run Powershell as admin <br>
Run Get-Service on specific Service again to confirm it went through <br>
```powershell
Set-Service WSearch -StartupType Automatic
```
<br>
