# Systemd Timers for Cron

Systemd timers are just the regular files with the extension `.timer`
encodes information about a timer controlled and supervised by systemd, for timer-based activation.
Systemd timers are little cumbersome to setup but are little more powerful imo
and have extra granularities as you will show below (with 30 seconds granularity example)

From `SYSTEMD.TIME(7)`:

The special expressions "minutely", "hourly", "daily", "monthly", "weekly", "yearly", "quarterly", "semiannually"
may be used as calendar events which refer to "*-*-* *:*:00", "*-*-* *:00:00", "*-*-* 00:00:00",
"*-*-01 00:00:00", "Mon *-*-* 00:00:00", "*-01-01 00:00:00", "*-01,04,07,10-01 00:00:00" and "*-01,07-01 00:00:00", respectively.

Steps to follow:

- create a script to run as cron

```shell
# $HOME/.bin/status-check.sh
#!/bin/bash

if curl -sS https://api.brighterlink.io >& /dev/null; then
  echo "Status check passed"
else
  echo "Status check failed. API Down :("
fi
```
- create a timer file

```ini
# $HOME/.config/systemd/user/status-check.timer

[Unit]
Description=Status Check

[Timer]
OnCalendar=*:*:0/30

[Install]
WantedBy=timers.target
```

- create a service file

```ini
# $HOME/.config/systemd/user/status-check.service

[Unit]
Description=Status Check Service

[Service]
ExecStart=/home/techgaun/.bin/status-check.sh
```

- enable and start the timer

```shell
# remove --user for system level timers (typically those saved in /etc/systemd/)

systemctl --user enable status-check.timer
systemctl --user start status-check.timer
```

- list timers

```shell
systemctl --user --all list-timers
```

- check status of particular timer

```shell
systemctl --user status status-check.timer
```
