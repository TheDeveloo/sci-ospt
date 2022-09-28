
https://delinea.com/blog/linux-privilege-escalation

| Enumeration Commands | Description                                 |
|----------------------|---------------------------------------------|
| `id`                 | print real and effective user and group IDs |
| `whoami`             | current user                                |
| `hostname`           | show or set the system's host name          |
| `uname -a`           | print system information                    |
| `ps -ef`             | report a snapshot of the current processes  |
| `echo $PATH`         | print environment PATH variable             |
| `ifconfig`           | configure a network interface               |
| `cat /etc/passwd`    | show passwd file contents                   |
| `sudo -l`            | list commands allowed using sudo            |
| See suidexec.md      | Find all files suid and sgid files          |

Ubuntu version
    
    lsb_release -a


# Tools

- [LinEnum.sh](./tools/tools.md#linenum---linux-enumeration-script)
- [LinPEAS](./tools/tools.md#linpeas---linux-privilege-escalation-awesome-script)

# Links

- https://delinea.com/blog/linux-privilege-escalation
- https://null-byte.wonderhowto.com/how-to/use-linenum-identify-potential-privilege-escalation-vectors-0197225/

# OS / Architecture / Kernel version

    uname -a
    cat /proc/version
    cat /etc/issue

Don't use kernel exploits if you can avoid it. If you use it it might crash the machine or put it in an unstable state.  
So kernel exploits should be the last resort. Always use a simpler priv-esc if you can. They can also produce a lot of stuff in the sys.log.  
So if you find anything good, put it up on your list and keep searching for other ways before exploiting it.

# Running Processes

    ps aux

# Installed softwares

    # Common locations for user installed software
    /usr/local/
    /usr/local/src
    /usr/local/bin
    /opt/
    /home
    /var/
    /usr/src/
    
    # Debian
    dpkg -l
    
    # CentOS, OpenSuse, Fedora, RHEL
    rpm -qa (CentOS / openSUSE )
    
    # OpenBSD, FreeBSD
    pkg_info

# Weak/reused/plaintext passwords
- Check file where webserver connect to database (config.php or similar)
- Check databases for admin passwords that might be reused
- Check weak passwords


    username:username
    username:username1
    username:root
    username:admin
    username:qwerty
    username:password

- Check plaintext password

# Anything interesting the the mail?
/var/spool/mail
./LinEnum.sh -t -k password