

# Kali setup
### Share with host machine
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

## flameshot (screenshot)
### Install

    apt get flameshot
### Configuration

 - Open flameshot from the menu
	 - This should open the flameshot trail icon (a flame - top right of the screen)
 - Right-click on it and select "Configuration"
 - Go to the "General" tab
 - Set "Save Path" to `/kali-share/screenshots`
 - Check "Use fixed path for screenshots to save
 - Prerred save file extension `jpeg`


### Keyboard shortcuts
In kali

 - Open the menu
 - Type "keyboard"
 - Open the "Keyboard" application
 - Select the "Application Shortcuts" tab

Shortcut "Print": `flameshot gui -s`
Shortcut "Shift+Print": `flameshot gui`


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
 - nmap -`Dradis::Plugins::Nmap`, see nmap / export below
 - nikto -`Dradis::Plugins::Nikto`, see nikto / export below
 - metasploit-framework - `Dradis::Plugins::Metasploit`, see metasploit
   framework / export database below

### Reset
https://dradisframework.com/ce/documentation/reset.html
#### Instance reset

    cd ~/dradis-ce/
    bundle exec thor dradis:reset
    


# Information gathering
## Scan
> Jackpot if these ports are open: 21, 80, 139, 445

Command: nmap
### Export

    nmap -sV -oX - <ip> >> /kali-share/nmap-<ip>.xml

## Ports
### FTP - 21

    nc <ip> 21

### HTTP - 80
#### Export

    nikto -h http://<ip>:<port> -o '/kali-share/nikto-<ip>-<port>.xml' -Format xml
    dirb http://<ip>:<port> >> /kali-share/dirb-<ip>-<port>.txt

Check if you find the following

 - phpinfo
 - system requirements
 - software (i.e. twiki)

### NETBIOS-SSN / SMB - 139, 445

    enum4linux -a <ip> >> /kali-share/enum4linux-<ip>.txt

### MiniServ (Webmin) - 10000, 20000
Go to `https://<ip>:10000/`


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

# Training
## Machines
https://www.vulnhub.com/

# Lexical
## Samba
Search also: smb