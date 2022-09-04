# Misc

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

# Export

    dirb http://<ip>:<port> > /kali-share/dirb-<ip>-<port>.txt

# dirbuster
https://www.kali.org/tools/dirbuster/

DirBuster is a multi threaded java application designed to brute force directories and files names on web/application servers. Often is the case now of what looks like a web server in a state of default installation is actually not, and has pages and applications hidden within. DirBuster attempts to find these.

However tools of this nature are often as only good as the directory and file list they come with. A different approach was taken to generating this. The list was generated from scratch, by crawling the Internet and collecting the directory and files that are actually used by developers! DirBuster comes a total of 9 different lists, this makes DirBuster extremely effective at finding those hidden files and directories. And if that was not enough DirBuster also has the option to perform a pure brute force, which leaves the hidden directories and files nowhere to hide.

# hydra

a very fast network logon cracker which support many different services

## Brute force - HTTP-FORM-POST
> **HINT**  
> Brute force HTTP-FORM-POST can also be achieved with burpsuite but the free version has limitations

Use burpsuite or the browser to get the request payload

![Get payload for hydra with firefox](../assets/hydra-http-form-post-payload-firefox.jpeg)
![Get payload for hydra with burpsuite](../assets/hydra-http-form-post-payload-burpsuite.jpeg)


    hydra -l <username> -P <pwd-list> <ip|dns> http-form-post "<login-page>:<post-content>:Invalid username"

Example:

    hydra -l Elliot -P /kali-share/downloads/fsocity.dic 192.168.56.105 http-form-post "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F192.168.56.105%2Fwp-admin%2F&testcookie=1:Invalid username"

Options:
  - `-l` username
  - `-L` username list
  - `-p` password
  - `-P` password list

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

### Troubleshooting
#### Database not connected
    msf6 > workspace
    [-] Database not connected
1. Check if running `sudo msfconsole` (or without sudo) changes the status
2. Run `sudo msfdb init && msfconsole` (that the command run by the kali menu)
3. Ensure the database is running 

Ensure the postgresql service is running

    ┌──(kali㉿kali)-[~]
    └─$ sudo service postgresql status    
    [sudo] password for kali:
    ○ postgresql.service - PostgreSQL RDBMS
    Loaded: loaded (/lib/systemd/system/postgresql.service; disabled; vendor preset: disabled)
    Active: inactive (dead)

Start it

    ┌──(kali㉿kali)-[~]
    └─$ sudo service postgresql start

    ┌──(kali㉿kali)-[~]
    └─$ sudo service postgresql status
    ● postgresql.service - PostgreSQL RDBMS
    Loaded: loaded (/lib/systemd/system/postgresql.service; disabled; vendor preset: disabled)
    Active: active (exited) since Sun 2022-09-04 04:49:20 EDT; 2min 12s ago
    Process: 37180 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
    Main PID: 37180 (code=exited, status=0/SUCCESS)
    CPU: 3ms
    
    Sep 04 04:49:20 kali systemd[1]: Starting PostgreSQL RDBMS...
    Sep 04 04:49:20 kali systemd[1]: Finished PostgreSQL RDBMS.

Check the status on metasploit

    msf6 > db_status
    [*] Connected to msf. Connection type: postgresql.
    msf6 > sudo msfdb init
    [*] exec: sudo msfdb init
    
    [sudo] password for kali:
    [i] Database already started
    [i] The database appears to be already configured, skipping initialization



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

Check if you find the following

- phpinfo
- system requirements
- software (i.e. twiki)