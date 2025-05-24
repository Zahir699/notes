# CMD
```
ipconfig ---> View basic networking configurations.

ipconfig /all ---> View detailed networking configuration information.

net share ---> Displays info about all of the resources that are shared on the local computer.

net view ---> Displays a list of domains, computers, or resources being shared by the specified computer.

arp /a ---> Displays the contents and entries contained within the Address Resolution Protocol (ARP) cache.

netstat -an ---> Display current network connections.

nslookup <query> ---> Query DNS for a name or address.
```

# Powershell
```
Get-NetIPInterface -ifIndex <#> ---> Retrieve network adapter properties of the interface listed as ifIndex #.

Get-NetNeighbor ---> Retrieves the neighbor entries from the cache. Similar to arp -a.

Get-Netroute ---> Will print the current route table. Similar to IPRoute.

Set-NetAdapter ---> Set basic adapter properties at the Layer-2 level, such as VLAN id, description, and MAC-Address.

Set-NetIPInterface ---> Modifies the settings of an interface to include DHCP status, MTU, and other metrics.

Set-NetIPAddress ---> Modifies the configuration of a network adapter.

Disable-NetAdapter ---> Used to disable network adapter interfaces.

Enable-NetAdapter ---> Used to turn network adapters back on and allow network connections.

Restart-NetAdapter ---> Used to restart an adapter. It can be useful to help push changes made to adapter settings.

test-NetConnection ---> Allows for diagnostic checks to be run on a connection. It supports ping, tcp, route tracing, and more.

Get-WindowsCapability -Online <PIPE> Where-Object Name -like 'OpenSSH*' ---> List Windows packages for OpenSSH.

Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0 ---> Install the SSH package to the host.

ssh-keygen ---> Generate SSH keys for the user you run the command as. This enables the use of the user for remote login.

winrm quickconfig ---> Enable WinRM.

Test-WSMan -ComputerName "10.129.224.248" ---> Test if the host specified has WinRM running.

Enter-PSSession -ComputerName 10.129.224.248 -Credential htb-student -Authentication Negotiate ---> Start a remote PowerShell session with the host specified.

```



