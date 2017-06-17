## How To Retrieve Kernel Boot Parameter

You can use one of the following techniques to retrieve kernel boot parameters
- `cat /proc/cmdline`
- `dmesg | grep 'BOOT_IMAGE'`
- `cat /var/log/kern.log | grep BOOT_IMAGE`
