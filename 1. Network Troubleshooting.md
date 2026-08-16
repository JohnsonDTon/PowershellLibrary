Show network configuration <br>
Includes IP address, subnet mask, default gateway, DHCP, DNS servers, MAC address, and network adapter information
```powershell
ipconfig /all
```
<br>

Test connectivity via ping.<br>
Ctrl + C to stop <br>
```powershell
ping 8.8.8.8 -t
```
<br>

Test TCP port connectivity.  <br>
Can gain intel if a port is blocked. Port 9100 is typically used for network printing
```powershell
Test-NetConnection 192.168.0.50 -Port 9100
```
<br>

Check routing table, use when you can connect on LAN, but not the internet
```powershell
route print
```
<br>

Show network hops of your traffic to destination. <br>
See where traffic stops/fails or troubleshoot latency or connectivity across networks
```powershell
tracert www.google.com
```
<br>

Flush DNS Cache <br>
Useful when DNS resolves a hostname to incorrect/outdated IP address
```powershell
ipconfig /flushdns
```
<br>

Test DNS resolution, see if DNS resolves a hostname to an IP address
```powershell
nslookup www.google.com
```
<br>

Release/Request DHCP address
```powershell
ipconfig /release
ipconfig /renew
```
<br>

Network Adapter information <br>
See what interface is active, whether PC is using wi-fi or Ethernet
```powershell
Get-NetAdapter
```
<br>

See more specific detail of the active interface only. <br>
Note: The adapter might be named differently on another computer. Get Name from Get-NetAdapter
```powershell
Get-NetIPConfiguration -Detailed | Where-Object {$_.InterfaceAlias -eq "Ethernet"}
Get-NetIPConfiguration -Detailed | Where-Object {$_.InterfaceAlias -eq "Wi-Fi"}
```
<br>

Network Discovery <br>
Scan a network for devices <br>
Note: nmap is an external tool, must be installed seperately <br>
https://nmap.org/download.html
```powershell
nmap -sn 192.168.0.0/24
```
<br>

Check Arp Cache, a list mapping local IP addresses to MAC addresses <br>
Useful to see what devices your PC talked to on LAN <br>
Great to find the ip address of that pesky printer with unknown IP
```powershell
arp -a
```
<br>

Shows network connections and listening ports on your own computer. <br>
```powershell
netstat -ano
```
<br>

After using netstat, use this to see what process using that port <br>
```powershell
Get-Process -Id 1234
```
