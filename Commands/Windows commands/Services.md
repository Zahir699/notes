# CMD
```
sc query ---> Lists all running services and provides additional information for each service.

sc query <Name> ---> Lists details about a specific service by name.

sc start <Name> ---> Start a service by name.

sc stop <Name> ---> Stop a service by name.

sc config <Name> start= disabled --->Change settings of the service specified.

tasklist /svc ---> Provide a list of services running under each process on the system.

net start ---> List all running services.

wmic service list brief ---> List all services on the system using WMIC. Includes information such as: ExitCode, Name, ProcessID, StartMode, State, and Status.
```

# Powershell
```
Get-service ---> List all services

Get-Service <PIPE> ft DisplayName,Status ---> List all services and format their information by DisplayName and Status.

Get-Service <PIPE> where DisplayName -like '*Name*' <PIPE> ft DisplayName,ServiceName,Status ---> Query for a specific service whose name matches 'name'.

Start-Service <Name> ---> Start a service by name.

Stop-Service <Name> ---> Stop a service by name.

Set-Service -Name <Name> -StartType Disabled ---> Change settings of the service specified.

Get-service -ComputerName ACADEMY-ICL-DC ---> Remote query of a hosts services.

Get-Service -ComputerName ACADEMY-ICL-DC | Where-Object {$_.Status -eq "Running"} ---> Remote query of services filtered to only show those that are Running.

Invoke-command -ComputerName ACADEMY-ICL-DC,LOCALHOST -ScriptBlock {Get-Service -Name 'windefend'} ---> Issue the Get-Service command on a list of hosts.
```