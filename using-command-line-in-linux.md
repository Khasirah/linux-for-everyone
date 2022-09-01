# Command Line In Linux
## Tips Study Command Line In Linux 
- shell command in linux placed in:
```
/bin/
/sbin/ 
/usr/bin/ 
/usr/sbin/ 
```
- to see shell command you can use:
```
$ ls /bin 
$ ls /sbin 
$ ls /usr/bin 
$ ls /usr/sbin 
```
> this command will return the contents of folder
- if you want to know how to use the command:
```
$ {command} -h 
$ {command} --help
$ man {command}
$ info {command}
```
> - man : open manual of {command}
> - info : open information of {command} (in my opinion resume of {command})

## Base Command Linux 

### Directory Navigation
| Command | Description |
| ---- | ---- |
| `pwd` | get full path of the current working directory |
| `cd` | navigate to the current user's home directory |
| `cd {destination}` | navigate to destination that you enter |
> example: `$ cd Documents/folder/folderfolder` this will navigate working directory to `Documents/folder/folderfolder`

### Listing files insed a directory 
| Command | Description |
| ---- | ---- |
| `ls -l` | list the files and directory / folder in the current directory in table format (**recommended to use for better readability**) |
| `ls -a` | list all the files including the hidden files (file names starting with a "." are hidden file in linux) |
| `ls -F` | appenda a symbol at the end of file name to indicate its type ("\*" means executable, "/" means directory, "@" means symbolic link, "=" means socket, "|" means named pipe, ">" means door) |
| `ls -lt` | list the files sorted by last modified time |
| `ls -lh` | list the file size in human readable format |
| `ls -lR` | show all the subdirectories recursively |
| `ls -l {directory}` | list the file and directory in {directory} that you pass in
> example : `ls -l Documents/folder`
> this command will list all files and directory in `Documents/folder`

### File/directory create, copy, and remove
| Command | Description |
| ---- | ---- |
| `cp -p {source} {destination}` | will copy the **file** from source to destination. |
| `cp -R {source} {destination}` | will copy source **directory** to destination recursively |
| `mv {file1} {file2}` | in linux there is no **rename** command as such. *mv* will move/rename the file1 to file2 |
| `rm -i {filename} {filename2}` | will remove {**filename**} and **ask** before every file removal for confirmation. you can remove multiple file |
| `rm -R {dir-name}` | will remove the **folder** recursively |
| `rmdir {dir-name}` | will remove **folder if empty** |
| `mkdir {folderName}` | create folder with {folderName} |
| `mkdir -p dir-name/{folderName}` | create folder inside *dir-name* with {folderName} |
| `touch {fileName}` | create file if it doesn't exist. otherwise change timestamp of the file to current time |
> example:
> - `cp -R Documents Pictures` 
> will copy folder "Documents" to folder "Pictures" 
> - `cp -R Documents/ Pictures` 
> will copy contents of "Documents" include subfolder to "Pictures" the "/" means that we command to pc copy contents of the folder
### File/directory permission and groups
| Command | Description |
| ---- | ---- |
| `chmod {spesification} {fileName}` | change the file permission. spesification, u = user, g = group, o = other, + add permission, - remove permission, r = read, w = write, x = execute |
| `chmod -R {spesification} {folderName}` | change the folder permission recursively, to change everything within the folder |
| `chmod go=+r {fileName}` | add read permission to group and other to {fileName} |
| `chmod a +rwx {fileName}` | add read, write, execute {fileName} to all user |
| `chmod go -r {fileName}` | remove read permission from group and other |
| `chown {user1} {fileName}` | change ownership of a file to user: user1 |
| `chgrp {grpOwner} {fileName}` | change primary group ownership of file: {fileName} to {grpOwner} |
| `chgrp -R {grpOwner} {folderName}` | change primary group ownership of {folderName} recursively to group: {grpOwner}, this will change **everything** within the folder |
| `chown {user}:{group} {fileName}` | change ownership and primary group at the same time |

#### chmod with number
we can use `chmod` with number instead of character that make use confuse
- use `ls -lh` to know detail of contents 
- at left side we see code like:
```
-rw-r--r-- 1 user users 70 Jul 22 13:36 someFile.txt
drwxrw-r-x 2 user users 4096 Jul 21 07:18 test
```
- let me explain left side
    - "-" or "d" at beginning means type the contents "-" = file, "d" = directory
    - "rwx" for user permission
    - "rw-" for group permission
    - "r-x" for other permission
- now we give "1" under character
```
d rwx rw- r-x 2 user users 4096 Jul 21 07:18 test 
  111 110 101
```
- and then change every 3 digit to 1 digit use this table:

| binary | decimal |
| ---- | ---- |
| 000 | 0 |
| 001 | 1 |
| 010 | 2 |
| 011 | 3 |
| 100 | 4 |
| 101 | 5 |
| 110 | 6 |
| 111 | 7 |

from table above we can convert, "111 110 101" to 765
- now use thu number to command 
`chmod 765 {fileName}` this will change the {fileName} to `rwxrw-r-x` or give user all permission, group add read and write, other read and execute.

### File Manipulation
these file manipulation command allow you to perform the same task that a graphical file explorer would perform.

**create** an empty text file called fileName:
```bash
touch fileName
```
**rename** fileName to fileName2:
```bash
mv fileName fileName1
```
**view** the contents of a file:
```bash
cat fileName2
```
> note: this will print all contents of file, so **becarefull** to use it if size of the file very large

**view** the contents of a file with **pager**:
```bash
less fileName2
```
**view** the **first several line** of a file:
```bash
head fileName2 
```
**view** the **last several line** of a file:
```bash
tail fileName2
```
**edit** the file:

linux have variety of file editor like **nano**, **vi**, **neovim**, etc
```bash
vi fileName2
or 
nano fileName2 
or 
nvim fileName2
``` 
for detail how to use, maybe i will create in another file.

### user identification and who is who in linux world
| Command | Description |
| ---- | ----- |
| `hostname` | display hostname of the system |
| `passwd {user}` | change password of {user} |
| `whoami` | username of the users logged in at the terminal |
| `who` | list of all users currently logged in as a user |
| `w` | display current system status, time, duration, list of users currently logged in on system and other |
| `last` | who recently used the system | 
| `lastb` | shows all bad login attempts into the system |

#### Process related information 
| Command | Description |
| ---- | ----- |
| `top` | list all process like task manager (windows) and continually updated display, to **quit** press "q" |
| `ps` | list process currently running on current shell session |
| `ps -u root` | list all process and command root is running |
| `ps aux` | list all process by all users |

#### shutdown restart using command line
| Command | Description |
| ---- | ----- |
| `shotdown -h now` | shutdown device now |
| `shutdown -r now` | restart device now |
| `halt {options}` | halt, poweroff, reboot options: --halth, -p, --reboot |

#### system identification
| Command | Description |
| ---- | ----- |
| `uname -a` | show information of system kernel |
| `lsb_release -a` | show what version of os you are running |
| `lsblk` | list all information about all available or the specified block device (HDD and RAM will show) |

> example:
>
> `uname -a`
>
> will print information like this:
> 
> Linux brian 5.15.0-46-generic #49-Ubuntu SMP Thu Aug 4 18:03:25 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

let me explain:
- brian : the name of pc 
- 5.15.0-46-generic : the kernel and architecture
- Ubuntu : tells me i am running ubuntu 
- x86_64 : 64-Bit
- if you cant find x86_64 and see i3xx : means 32-Bit

### organize disk/device 
i will show most commonly used command-line based disk manipulation that i use too.

1. fdisk

- fdisk is an most commonly used command-line based disk manipulation utility 

command that commonly use:
- `fdisk -l`
    - show all disk partition
    - 
      ```
      Disk /dev/sda: 465,76 GiB, 500107862016 bytes, 976773168 sectors
      Disk model: TOSHIBA DT01ACA0
      Units: sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 4096 bytes
      I/O size (minimum/optimal): 4096 bytes / 4096 bytes
      Disklabel type: gpt
      Disk identifier: 63645B40-E240-47BF-8B3B-09047FD4AA37

      Device       Start       End   Sectors   Size Type
      /dev/sda1     2048   1050623   1048576   512M EFI System
      /dev/sda2  1050624   1052671      2048     1M BIOS boot
      /dev/sda3  1052672 976771071 975718400 465,3G Linux filesystem
      ```
    - that the example ouput of my pc
    - "**/dev/sda**" means the name of the device 
    - "/dev/sda1" means the partition in the device
    - detail about fdisk maybe i create in another show 

2. mkfs
the mkfs command stands for "make file system" or commonly used for format usb like (FAT, FAT32, NTFS, EXT4)

### mounting disk/device 
if you want mount usb, external hdd, network folder, to your pc you can use **mount** and **umount** to unmount the device 
