# DockerCommands
A place to store helpful Docker commands

# DockerCommands for Windows Command Prompt

## Running a container with an attached volume ##

Description: Link a directory between your base OS and your container, allowing changes inside the container to be reflected
in the files outside the container, and vice versa.

Syntax:
```bash
docker run -it --volume /c/path/to/dir/on/Windows/directory:/path/to/where/dir/goes/in/containter repository/image shell
```
Note the conversion from Windows file structure to the file structure of the container OS.
C:\ on Windows is changed to /c/ (lowercase)
\ is changed to /
These changes are required. The following code is an example of going from a Windows machine to a linux based OS (Ubunutu) using the bash shell.

Example:
```bash
docker run -it --volume /c/Users/Jason/Desktop/CSE3341/Project1:/home/cse3341/project1 weible/osu_cse bash
```

source: https://medium.com/@kale.miller96/how-to-mount-your-current-working-directory-to-your-docker-container-in-windows-74e47fa104d7




