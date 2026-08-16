Show network configuration <br>
Includes IP address, subnet mask, default gateway, DHCP, DNS servers, MAC address, and network adapter information <br>
```powershell
ipconfig /all
```

Ping to test connectivity. Either cmd works.<br>
```powershell
ping 8.8.8.8
Test-NetConnection 8.8.8.8
```

Network Adapter information <br>
See what interface is active, whether PC is using wi-fi or Ethernet <br>
```powershell
Get-NetAdapter
```

See more specific detail of the active interface only. <br>
Note: The adapter might be named differently on another computer. Get Name from Get-NetAdapter <br>
```powershell
Get-NetIPConfiguration -Detailed | Where-Object {$_.InterfaceAlias -eq "Ethernet"}
Get-NetIPConfiguration -Detailed | Where-Object {$_.InterfaceAlias -eq "Wi-Fi"}
```

