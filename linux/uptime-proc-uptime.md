## Understanding uptime

- uptime reads uptime info from `/proc/uptime`.
- uptime reads user info from `/var/run/utmp`
- `/proc/uptime` has single line with two values. First represents total number of seconds the system has been up and
second represents time spent by machine being idle. Second value may be larger than first for multi-core systems.
- `uptime -s` provides datetime since the system has been up
- `uptime -p` gives prettified info (eg. `up 10 hours, 1 minute`)
