﻿# Misc

- https://gchq.github.io/CyberChef/ - The Cyber Swiss Army Knife - a web app for encryption, encoding, compression and data analysis
- https://beefproject.com/ - BeEF is short for The Browser Exploitation Framework. It is a penetration testing tool that focuses on the web browser.

# burpsuite
https://www.kali.org/tools/burpsuite/

Burp Suite is an integrated platform for performing security testing of web applications. Its various tools work seamlessly together to support the entire testing process, from initial mapping and analysis of an application’s attack surface, through to finding and exploiting security vulnerabilities.

Burp gives you full control, letting you combine advanced manual techniques with state-of-the-art automation, to make your work faster, more effective, and more fun.

# dirb
Scan available pages
https://www.hackingarticles.in/comprehensive-guide-on-dirb-tool/

    dirb http://<ip> <opt:wordlist>

options:
- `-z`: Add a milliseconds delay to not cause excessive Flood.

wordlists:
- /usr/share/dirb/wordlist/vulns/...
- /usr/share/dirb/wordlists/big.txt

# dirbuster
https://www.kali.org/tools/dirbuster/

DirBuster is a multi threaded java application designed to brute force directories and files names on web/application servers. Often is the case now of what looks like a web server in a state of default installation is actually not, and has pages and applications hidden within. DirBuster attempts to find these.

However tools of this nature are often as only good as the directory and file list they come with. A different approach was taken to generating this. The list was generated from scratch, by crawling the Internet and collecting the directory and files that are actually used by developers! DirBuster comes a total of 9 different lists, this makes DirBuster extremely effective at finding those hidden files and directories. And if that was not enough DirBuster also has the option to perform a pure brute force, which leaves the hidden directories and files nowhere to hide.

# Metasploit framework

Open metasploitable framework
## Getting started
https://www.section.io/engineering-education/getting-started-with-metasploit-framework/  
https://www.offensive-security.com/metasploit-unleashed/using-databases/  
https://docs.rapid7.com/metasploit/exporting-and-importing-data/
## Start

    msfconsole
## Workspace
### See workspaces

    workspace

### Add workspace

    workspace -a <workspace-name>

### Change workspace

    workspace <workspace-name>

## Scanning
This will add the remote machine to hosts

    db_nmap -A <ip>
Useful to set RHOSTS of exploits rapidly
## Search
    search <terms>

## Exploit
### set RHOSTS

    hosts -R

## Scanner
### set USER_FILE
#### rockyou
Use one of the path found with the following command

    locate rockyou
## Vulnerabilities
Displays the vulnerabilities exploited

    vulns
## Credentials

    creds
## Loot

    loot

## Import module
Copy file to ~/.msf4/modules/exploits

    sudo updatedb
Restart metasploit-framework

## Export database

    db_export -f xml -a /kali-share/metasploit-framework.xml


# nikto
Gives vulnerabilities

    nikto -h http://<ip>:<port>

## Export

    nikto -h http://<ip>:<port> -o '/kali-share/nikto-<ip>-<port>.xml' -Format xml
    dirb http://<ip>:<port> >> /kali-share/dirb-<ip>-<port>.txt

Check if you find the following

- phpinfo
- system requirements
- software (i.e. twiki)