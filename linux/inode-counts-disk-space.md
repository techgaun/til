# inodes unavailability

Inode is a data structure that defines metadata of the files in the linux (& other Unix-like) file system. On Linux, you need both physical storage and unused inodes available to save a file and you can hit the issues like `No space left on device` even if your `df -h` output shows that you have enough physical space available.

The reason it happens is you have too many files or directories that are empty or very small in size. Also, once you have created the file system, you can not increase (or decrease) the number of inodes unless you perform the formatting and recreating of file system.

To view available storage (in human readable format)

```shell
$ df -h
```

To view available inodes (in human readable format)

```shell
$ df -ih
```

Just remove `h` flag if you want to see raw precise details.

Sometimes, you have cases where you have too many files each of very small size (eg. time series data sent by energy monitoring devices sent per minute can be very small in size). In such case, you can create the file system by specifying the bytes-per-inode of your need. By default, `mkfs.ext4` creates one inode for every 16Kb. You can specify to create one inode for every 4096 bytes.

```shell
$ mkfs.ext4 -i 4096 /dev/sdb
```

Also, you can use `-T` arg to specify the usage type so that you can create file system which is optimized for your use case.

From `MKE2FS(8)`:

```
-T usage-type[,...]
              Specify  how  the filesystem is going to be used, so that mke2fs can choose optimal filesystem parameters for that use.  The usage types that are supported are defined in the configuration
              file /etc/mke2fs.conf.  The user may specify one or more usage types using a comma separated list.

              If this option is is not specified, mke2fs will pick a single default usage type based on the size of the filesystem to be created.  If the filesystem size is  less  than  or  equal  to  3
              megabytes,  mke2fs will use the filesystem type floppy.  If the filesystem size is greater than 3 but less than or equal to 512 megabytes, mke2fs(8) will use the filesystem type small.  If
              the filesystem size is greater than or equal to 4 terabytes but less than 16 terabytes, mke2fs(8) will use the filesystem type big.  If the filesystem size is greater than or equal  to  16
              terabytes, mke2fs(8) will use the filesystem type huge.  Otherwise, mke2fs(8) will use the default filesystem type default.
```
