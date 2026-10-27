SSD
```powershell
Get-PhysicalDisk | Format-Table FriendlyName, MediaType, HealthStatus, OperationalStatus, Size
```
```text
1. Open Settings.
2. Go to System → Storage → Advanced storage settings → Disks & volumes.
3. Select your SSD and open Properties.
4. Look for drive health warnings, estimated remaining life, or reliability issues.
If you see a critical warning, back up your data immediately.
```
```powershell
chkdsk C: /scan
```

RAM
```text
Run memtest86
```

Temperature
```text
Run HWMonitor
```

