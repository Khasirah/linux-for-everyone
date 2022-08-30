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
> example: `$ cd Documents/folder/folderfolder` <br/>
> this will navigate working directory to `Documents/folder/folderfolder`

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
> example : `ls -l Documents/folder` <br/>
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
