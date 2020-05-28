# LinuxCommands
A place to store helpful, occasionally used Linux/Unix commands.

Markup Guide: https://guides.github.com/features/mastering-markdown/

## Copying files between machines ##

Syntax:
```bash
scp <source> <destination>
```
To copy a file from **B** to **A** while logged into **B**:
```bash
scp /path/to/file username@a:/path/to/destination
```
To copy a file from **B** to **A** while logged into **A**:
````bash
scp username@b:/path/to/file /path/to/destination
````

source: https://unix.stackexchange.com/questions/106480/how-to-copy-files-from-one-machine-to-another-using-ssh
