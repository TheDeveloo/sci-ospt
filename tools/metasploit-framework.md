# Metasploit framework

Open metasploitable framework
## Getting started
https://www.section.io/engineering-education/getting-started-with-metasploit-framework/  
https://www.offensive-security.com/metasploit-unleashed/using-databases/  
https://docs.rapid7.com/metasploit/exporting-and-importing-data/
## Start

    sudo msfdb init && msfconsole

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

### set options globally

    setg <option> <value>

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

## msfvenom

### Payloads

    msfvenom -p

### Payload options

    msfvenom -p <payload> --list-options

### Set option

set LHOST

    msfvenom -p <payload> LHOST=<host_ip>

### Write payload into a file

    msfvenom -p <payload> LHOST=<host_ip> > <outputfile>