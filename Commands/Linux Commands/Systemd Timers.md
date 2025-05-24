```
1. Create a timer (schedules when your `mytimer.service` should run)

sudo mkdir /etc/systemd/system/mytimer.timer.d
sudo vim /etc/systemd/system/mytimer.timer

In mytimer.timer (it will run every 5 minutes):

[Unit]
Description=My Timer

[Timer]
OnBootSec=3min
OnUnitActiveSec=1hour
OnCalendar=*:0/5

[Install]
WantedBy=timers.target

2. Create script with reverse shell or task to be ran in
/etc/systemd/system/mytimer.timer.d, give it execute permissions and add the #!/bin/bash variable if its a bash script.

3. Create a service (executes the commands or script)

sudo vim /etc/systemd/system/mytimer.service

It should have these contents:

[Unit]
Description=My Service

[Service]
ExecStart=/etc/systemd/system/mytimer.timer.d/script.sh

[Install]
WantedBy=multi-user.target

4. Activate the timer

sudo systemctl daemon-reload
sudo systemctl start mytimer.timer
sudo systemctl enable mytimer.timer
```