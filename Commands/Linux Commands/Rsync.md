```
Create backups:
rsync -av /path/to/mydirectory user@backup_server:/path/to/backup/directory
sync -avz --backup --backup-dir=/path/to/backup/folder --delete /path/to/mydirectory user@backup_server:/path/to/backup/directory

Restore backups:
rsync -av user@remote_host:/path/to/backup/directory /path/to/mydirectory

Encrypted rsync:
rsync -avz -e ssh /path/to/mydirectory user@backup_server:/path/to/backup/directory
```