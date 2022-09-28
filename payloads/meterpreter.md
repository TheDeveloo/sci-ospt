# Meterpreter

    meterpreter > shell
<!-- Launch shell -->
    python -c 'import pty;pty.spawn("/bin/bash")'
<!-- Vuln software -->
    find / -perm -u=s -type f 2>/dev/null

- `/` denotes that we will start from the top (root) of the file system and find every directory
- `perm` denotes that we will search for the permissions that follow:
- `u=s` denotes that we will look for files which are owned by the root user
- `type` states the type of file we are looking for
- `f` denotes a regular file, excluding directories and special files
- `2>/dev/null` means we will redirect all errors to /dev/null.  
  In other words, we will ignore all errors.