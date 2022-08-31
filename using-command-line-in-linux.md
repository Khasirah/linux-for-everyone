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
