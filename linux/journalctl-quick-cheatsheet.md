## Journalctl Quick Cheatsheet

- systemd-journald system service is responsible for collecting and storing log data. It creates and maintains
structured, indexed journals based on logging information that is received from a variety of sources.
- One of the main changes in journald was to replace simple plain text log files with a special file format optimized for log messages. This file format allows system administrators to access relevant messages more efficiently. It also brings some of the power of database-driven centralized logging implementations to individual systems.
- You are supposed to use the `journalctl` command to query log files.

### Cheatsheets

- sshd logs : `journalctl _COMM=sshd`
- sshd logs in json format : `journalctl _COMM=sshd -o json-pretty`
- filter by date range : `journalctl --since "2015-01-10" --until "2015-01-11 03:00"`
- another filter by date range example : `journalctl --since 09:00 --until "1 hour ago"`
- logs since boot : `journalctl -b`
- follow logs : `journalctl -f`
- disk usage of all journal files : `journalctl --disk-usage`
- Reduce disk usage below specified size : `journalctl --vacuum-size=1G`

Source : [htop explained](https://peteris.rocks/blog/htop/)
