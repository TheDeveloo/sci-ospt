# General

> Jackpot if these ports are open: 21, 80, 139, 445

## Commands
- [nmap](#nmap)
- hping3 - nmap with traceroute
  - DDoS with `--flood`

# nmap

    nmap -T4 -A -p- 192.168.56.109


## Network scanning

https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#IPv4_CIDR_blocks

    nmap -sP 19
    sudo netdiscover -i eth1 -r 192.168.56.0/24
<!---->
    ┌──(kali㉿kali)-[~]
    └─$ nmap -sP 192.168.56.0/24
    Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-04 05:44 EDT
    Nmap scan report for 192.168.56.101
    Host is up (0.0026s latency).
    Nmap scan report for 192.168.56.105
    Host is up (0.012s latency).
    Nmap done: 256 IP addresses (2 hosts up) scanned in 15.36 seconds


## Export (for dradis)

    nmap -sV -oX - <ip> > /kali-share/nmap.xml

## Vulnerability scan

    sudo nmap -v --script vuln <ip>
    sudo nmap -v --script vuln -oX - <ip> > /kali-share/nmap-vuln.xml

## Auth scan

    sudo nmap -v --script auth <ip>

## Noisy scan

    nmap -p- -sV -T4 <ip>
    nmap -v -T4 -p- -sC -sV 192.168.56.112

- `-p-` all ports
- `-T4` set timing template
    - paranoid (0)
    - sneaky (1)
    - polite (2)
    - normal (3)
    - aggressive (4)
    - insane (5)
- `-sV` (Version detection)  
  Enables version detection, as discussed above. Alternatively, you can use -A, which enables version
  detection among other things.
- `-v` verbose
- `-sC`
  Performs a script scan using the default set of scripts. It is equivalent to --script=default. Some
  of the scripts in this category are considered intrusive and should not be run against a target
  network without permission.

## Sneaky

    nmap -v -T1 -p- -sC -sV -Pn 192.168.56.112

- `-Pn` (No ping)
  This option skips the host discovery stage altogether. Normally, Nmap uses this stage to determine active machines for heavier scanning and to gauge the speed of the network. By default, Nmap only performs heavy probing such as port scans, version detection, or OS detection against hosts that are found to be up. Disabling host discovery with -Pn causes Nmap to attempt the requested scanning functions against every target IP address specified. So if a /16 sized network is specified on the command line, all 65,536 IP addresses are scanned. Proper host discovery is skipped as with the list scan, but instead of stopping and printing the target list, Nmap continues to perform requested functions as if each target IP is active. Default timing parameters are used, which may result in slower scans. To skip host discovery and port scan, while still allowing NSE to run, use the two options -Pn -sn together.
  For machines on a local ethernet network, ARP scanning will still be performed (unless --disable-arp-ping or --send-ip is specified) because Nmap needs MAC addresses to further scan target hosts. In previous versions of Nmap, -Pn was -P0 and -PN.

## SSH scan

    nmap -p22 <ip> -sC # Send default nmap scripts for SSH
    nmap -p22 <ip> -sV # Retrieve version
    nmap -p22 <ip> --script ssh2-enum-algos # Retrieve supported algorythms
    nmap -p22 <ip> --script ssh-hostkey --script-args ssh_hostkey=full # Retrieve weak keys
    nmap -p22 <ip> --script ssh-auth-methods --script-args="ssh.user=root" # Check authentication methods