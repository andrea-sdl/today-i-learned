# Free Space locked by files still in use #


It might happen that space isn't freed because some file that you deleted are still "considered" by the system.
To find them first do a lsof of the deleted files

```bash
 sudo /usr/sbin/lsof | grep deleted
```

This will give you the file list and the list of inodes used.

To zeroe them find the process id and find the right entry (/proc/<pid>/fd/) by 
```bash
 sudo cat /dev/null > /proc/0123/fd/456
```
