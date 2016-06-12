# Zip and Rar files cracking with John The Ripper

John The Ripper comes with `rar2john` and `zip2john` executables which can be used to generate hashes that can be then used to be bruteforced (or other attacks) with john the ripper.

```shell
./rar2john pwd_protected.rar > out.hash
./john out.hash
```
