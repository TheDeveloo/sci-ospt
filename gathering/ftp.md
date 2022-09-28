https://www.howtoforge.com/tutorial/how-to-use-ftp-on-the-linux-shell/

# Anonymous login

Can be checked with nmap

    nmap -T4 -A -p- 192.168.56.109
Credentials

- User:  anonymous
- Password:  anonymous@domain.com or no password

# Upload

    put /kali-share/downloads/test.md ~/test.md

> Use fullpath

# Download
Before downloading a file, we should set the local FTP file download directory by using 'lcd' command:

    lcd /home/user/yourdirectoryname
If you dont specify the download directory, the file will be downloaded to the current directory where you were at the time you started the FTP session.

Now, we can use the command 'get' command to download a file, the usage is:

    get file