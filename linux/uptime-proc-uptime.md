## Understanding uptime

- uptime reads uptime info from `/proc/uptime`.
- uptime reads user info from `/var/run/utmp`
- uptime reads load average from `/proc/loadavg`
- `/proc/uptime` has single line with two values. First represents total number of seconds the system has been up and
second represents time spent by machine being idle. Second value may be larger than first for multi-core systems.
- `uptime -s` provides datetime since the system has been up
- `uptime -p` gives prettified info (eg. `up 10 hours, 1 minute`)
- `strace -e open uptime` is how you can know how this happens :)

```shell
$ strace -e open uptime
# ...... other syscalls
open("/proc/filesystems", O_RDONLY)     = 3
open("/sys/devices/system/cpu/online", O_RDONLY|O_CLOEXEC) = 3
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
open("/etc/localtime", O_RDONLY|O_CLOEXEC) = 3
open("/proc/uptime", O_RDONLY)          = 3
open("/var/run/utmp", O_RDONLY|O_CLOEXEC) = 4
open("/proc/loadavg", O_RDONLY)         = 4
```
