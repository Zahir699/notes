```
whoami
id
hostname
ip a ; ifconfig ---> Am i part of another network?

sudo -l --- What are my permissions

cat /etc/os-release ---> check for vulnerable OS version

echo $PATH ---> Check if path hijacking is possible

env ---> check for passwords in environment variables

uname -a ---> check for vulnerable kernel version

sudo -V ---> Check for vulnerable version

find / -type f -name ".*" -exec ls -l {} \; 2>/dev/null | grep htb-student ---> search for hidden files

cat /etc/hosts 

lastlog ---> show last logged in users

find / -type f \( -name *_hist -o -name *_history \) -exec ls -l {} \; 2>/dev/null ---> Find history files


ls -la /etc/cron.* ; cat /etc/crontab ; ls -lart /var/spool/cron ---> List cronjobs

apt list --installed | tr "/" " " | cut -d" " -f1,3 | sed 's/[0-9]://g' ---> Show installed packages

find / -type f \( -name *.conf -o -name *.config \) -exec ls -l {} \; 2>/dev/null ---> Find conffiguration files

find / -type f -name "*.sh" 2>/dev/null | grep -v "src\|snap\|share" ---> Find scripts

```

# Credential Hunting
```
Look for config files in /var/www/*
cat wp-config.php | grep 'DB_USER\|DB_PASSWORD'

find /var/www/ -type f 2>/dev/null -exec grep 'DB_USER\|DB_PASSWORD' {} \;

```