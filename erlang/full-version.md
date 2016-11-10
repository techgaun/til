# Finding Erlang Full Version

Erlang full version with minor and patch does not seem to be listed on erl or anywhere. The best way I could get the full version info was by checking the `OTP_VERSION` file.

```shell
$ cat <INSERT_ERLANG_ROOT_DIR>/releases/<INSERT_MAJOR_VERSION_HERE>/OTP_VERSION
$ cat /usr/lib/erlang/releases/19/OTP_VERSION
```
