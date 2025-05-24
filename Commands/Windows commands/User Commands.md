
# CMD

```
whoami ---> Displays the username of the currently logged-on user.

whoami /priv ---> Displays the security privileges of the current user.

whoami /groups ---> Displays the user groups that the current user belongs to.

whoami /all v Displays all information about the current user, including username, security identifiers (SID), privileges, and groups.

net user ---> Displays a list of the user accounts on the computer

net localgroup ---> Displays the name of the server and the names of local groups on the computer.

net group --->Displays the name of a server and the names of groups on the server. Only able to be used if the machine is joined to the domain.
```

# Powershell
```
Get-LocalGroup ---> View all groups specific to the host only.

Get-LocalUser ---> View all local users. Similar to net user.

New-LocalUser -Name "username" -NoPassword ---> Create a new Local user.

Set-LocalUser -Name "username" -Password $Password -Description "users 
description" ---> Modify a local user's settings.

Get-LocalGroupMember -Name "Group Name" ---> Check Group membership.

Add-LocalGroupMember -Group "Group Name" -Member "User-To-Add" ---> Add a user to a local group.

Get-WindowsCapability -Name RSAT* -Online | Add-WindowsCapability -Online ---> Install Remote System Administration Tools.

Get-Module -Name ActiveDirectory -ListAvailable---> Locate the Active Directory module.

Get-ADUser -FIlter * ---> List all domain users.

Get-ADUser -Identity <name> ---> Show a specific domain user and its properties.

Get-ADUser -Filter {EmailAddress -like '*greenhorn.corp'} ---> Filter domain users based on the EmailAddress property.

New-ADUser -Name "UserName" -Surname "Last Name" -GivenName "First Name" -Office "Security" -OtherAttributes @{'title'="Sensei";'mail'="UserName@greenhorn.corp"} -Accountpassword (Read-Host -AsSecureString "AccountPassword") -Enabled $true ---> Create a New Domain user and set its properties such as name, password, and other attributes.

Set-ADUser -Identity <UserName> -Description " Information we want in the description field" ---> Modify the property settings of a domain user.
```
