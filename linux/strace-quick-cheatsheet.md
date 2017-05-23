## Strace Quick Cheatsheet

I'm using more and more sysdig but sometimes I can't use it for various reasons (such as on someone else's system or
    some server).
This is a quick strace cheatsheet:

- strace running process : `strace -p <pid>`
- strace running process and threads : `strace -fp <pid>`
- strace a program : `strace /usr/bin/uptime`
- strace particular syscalls : `strace -e open <program>` or `strace -e trace=open,close <program>`
- exclude particular syscall : `strace -e 'trace=!open'` (use single quotes as `!` has special meaning to shell)
- strace set of syscalls : `strace -e trace=file`. Other sets include `process`, `network`, `signal`, `ipc`, `desc`,
  `memory`
- syscalls statistics : `strace -c <program>`
- print time of day at the start of each line : `strace -t <program>`
