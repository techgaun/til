# Count number of files in a directory better way

You have probably encountered an error `-bash: /bin/ls: Argument list too long` because you try to find the number of files in a directory by doing something like

```shell
$ ls * | wc -l
```

This is because you can not exceed your argument list more than `ARG_MAX` (`getconf ARG_MAX` gives you the number).

The alternative and much safer way is to use `FIND(1)` and pipe the result to `WC(1)`. Examples follow:

***Search only the current level of directory without considering files in sub-directories (`maxdepth` arg is the key):***

```shell
$ find . -maxdepth 1 -type f -exec printf %.sX {} + | wc -c
```

***Search the whole directory tree for number of files:***

```shell
$ find . -type f -exec printf %.sX {} + | wc -c
```
