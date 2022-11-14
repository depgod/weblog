---
layout: post
title: How permissions work on files and directories
---

# List set and change standard permissions

__chgrp__ - change group  
Change group ownerships  

__chmod__ - change mode  
Change modification permissions  

__chown__ - change ownership  
Change ownerships of users  




When we do `ls -l` we get this:
```bash
drwxr-xr-x user family 4.0 KB Thu Nov 10 07:31:07 2022 Downloads
```

__Interpretation__:
Here we see the folder "Downloads" is owned by user _"user"_ which has the read / write permissions to it and the super user _"sudo"_ too which has the admin privelages not to mention.
Other than the user their is also a family attribiute next to it which is a group which as can be seen has two permissions of reading it and executing it.

### Changing the group of the file it belongs to we can use the command `chgrp`:
```bash
$ chgrp wheel file
```

__Output__:
```bash
drwxr-xr-x user wheel 4.0 KB Thu Nov 10 07:31:07 2022 Downloads
```

### To see which a current user belongs to we can use:
```bash
groups
```
__Output__:
```bash
jetskar adm cdrom sudo dip plugdev lpadmin lxd sambashare
```

### Changing owenership of file/directory we use `chown`:

```bash
$ sudo chown user filename
```



