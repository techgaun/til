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

### strace bash builtins

Sometimes you may want to know what syscalls are made when you execute bash builtins such as `cd`. I got two ways around
this:

```shell
$ cat | strace bash > /dev/null
# strace outputs will appear but you can run commands here although it might not look like shell
cd /tmp
```

Other way is to create simple scripts to forward to builtin:

- Create a file named `mycd` with following content and `chmod +x mycd`:

```shell
#!/bin/bash
builtin cd "$@"
```

- Now run strace on `mycd` by doing: `strace ./mycd /tmp`
