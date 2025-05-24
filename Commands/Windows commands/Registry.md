```
Get-Item -Path Registry::<HIVE>\Path-to-key\ <PIPE> Select-Object -ExpandProperty Property ---> See the sub-keys and properties of a registry key.

Get-ChildItem -Path <HIVE>:\Path-to-key -Recurse ---> Recursively search through a Key and all subkeys.

Get-ItemProperty -Path Registry::<HIVE>\Path-to-key\key ---> View the properties and values of a specific key.

REG QUERY <HIVE>\PATH\KEY ---> Use reg.exe to query the registry.

REG QUERY <HIVE> /F "Password" /t REG_SZ /S /K ---> Search for specific strings within the Registry hive.

New-Item -Path <HIVE>:\PATH\ -Name KeyName ---> Create a new Registry Key.

New-ItemProperty -Path <HIVE>:\PATH\KEY -Name "ValueName" -PropertyType String -Value "C:\Users\htb-student\Downloads\payload.exe" ---> Set a new Value pair within a registry Key.

REG add "<HIVE>\PATH\KEY" /v access /t REG_SZ /d "C:\Users\htb-student\Downloads\payload.exe" ---> Use Reg.exe to create a new key/value pair.

Remove-ItemProperty -Path <HIVE>:\PATH\KEY -Name "name" ---> Delete a key/value from the registry.
```