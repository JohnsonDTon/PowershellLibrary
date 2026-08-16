## Deep Clean uninstall printer and the printer drivers
## You usually want to do this when there is a printer/scanner issue and its acting up, and you have trouble reinstalling it.
## Ideally, remove printer, clear print spooler and stuck print jobs, remove printer driver, remove windows driver store via pnputil

```powershell
Get-Printer | Format-List Name, DriverName, PortName
Remove-Printer -Name "Copy/Paste exact name here"

Stop-Service Spooler 
Remove-Item "$env:SystemRoot\System32\spool\PRINTERS\*" -Force
Start-Service Spooler

Get-PrinterDriver | Format-List Name, Manufacturer, DriverVersion, InfPath
Remove-PrinterDriver -Name "Copy/Paste exact name here"

pnputil /enum-drivers
pnputil /delete-driver oemXX.inf /uninstall
```
