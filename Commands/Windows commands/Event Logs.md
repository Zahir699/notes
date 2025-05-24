```
wevtutil el ---> Uses the Windows Events Commandline utility to enumerate all log sources.

wevtutil gl "name" ---> Will gather config information about the log specified.

wevtutil qe <Name> /c:5 /rd:true /f:text ---> Query a log for events.

wevtutil epl <Name> C:\system_export.evtx ---> Export a Log.

Get-WinEvent -ListLog * ---> List all logging facilities using PowerShell cmdlets.

Get-WinEvent -LogName 'Name' -MaxEvents 5 <PIPE> Select-Object -ExpandProperty Message ---> View the messages of a specific log.

Get-WinEvent -FilterHashTable @{LogName='Security';ID='4625 '} ---> Query for a specific log by eventID.
```