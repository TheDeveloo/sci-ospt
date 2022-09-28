# Table of Content

- [Pentest](#pentest)
  - [Frameworks](#frameworks)
  - [Phases](#phases)
  - [Pre-engagment](pre-engagement)
  - [Intelligence gathering](#intelligence-gathering)
      - [Tools](#tools)
      - [Google Hacks / dorks](#google-hacks--dorks)
      - [Knowledge databases](#knowledge-databases)
      - [Network scanning](#network-scanning)
      - [Port scanning](#port-scanning)
      - [Ports](#ports)
  - [Reporting](#reporting)
- [Training](#training)
- [Attacks](#attacks)
  - [Xmas attack](#xmas-attack)
  - [Null attack](#null-attack)
  - [XSS](#xss)
  - [SQL Injection](#sql-injection)
  - [Buffer overflow](#buffer-overflow)
- [Data exfiltration](#data-exfiltration)
  - [ICMP - Internet Control Message Protocol](#icmp---internet-control-message-protocol)
- [Privilege Escalation](#privilege-escalation)
  - [Windows](#windows)
  - [Linux](#linux)
- [Lexical](#lexical)
- [Learning](#learning)

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

#### VirtualBox network

![VirtualBox network manager](./assets/virtualbox-network-manager.jpg)



#### MiniServ (Webmin) - 10000, 20000
Go to `https://<ip>:10000/`

#### NETBIOS-SSN / SMB - 139, 445

    enum4linux -a <ip> >> /kali-share/enum4linux-<ip>.txt


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

# Lexical
## Samba
Search also: smb

# Learning

  - [Offensive Security - Penetrations Testing Bootcamp](https://github.com/phr85/swiss-cyber-defence/tree/main/Courses/Offensive%20Security%20-%20Penetrations%20Testing%20Bootcamp)
