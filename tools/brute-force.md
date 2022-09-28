# HTTP

See in gathering/http  
- ffuf (best speed)
- hydra
- wfuzz (needs a lot of resources)

# ZIP

zip2john

    ┌──(kali㉿kali)-[/kali-share/downloads]
    └─$ zip2john war-is-over > war-is-over-hash

# John The Ripper

    ┌──(kali㉿kali)-[/kali-share/downloads]
    └─$ john respect-hash --wordlist=/usr/share/wordlists/rockyou.txt
    Using default input encoding: UTF-8
    Loaded 1 password hash (PKZIP [32/64])
    Will run 2 OpenMP threads
    Press 'q' or Ctrl-C to abort, almost any other key for status
    072528035        (respectmydrip.zip/respectmydrip.txt)     
    1g 0:00:00:01 DONE (2022-09-24 14:02) 0.7633g/s 10627Kp/s 10627Kc/s 10627KC/s 072551..072046870
    Use the "--show" option to display all of the cracked passwords reliably
    Session completed.

## MD5

    ┌──(kali㉿kali)-[~]
    └─$ john --format=raw-md5 mr-robot-hash --wordlist=/kali-share/downloads/fsocity.dic               
    Using default input encoding: UTF-8
    Loaded 1 password hash (Raw-MD5 [MD5 128/128 SSE2 4x3])
    Warning: no OpenMP support for this hash type, consider --fork=2
    Press 'q' or Ctrl-C to abort, almost any other key for status
    0g 0:00:00:00 DONE (2022-09-09 17:36) 0g/s 2258Kp/s 2258Kc/s 2258KC/s 2Fwiki..ABCDEFGHIJKLMNOPQRSTUVWXYZ

## No password hashes left to crack (see FAQ)

https://www.openwall.com/john/doc/FAQ.shtml

    ┌──(kali㉿kali)-[/kali-share/downloads]
    └─$ john war-is-over-hash --wordlist=/usr/share/wordlists/rockyou.txt
    Using default input encoding: UTF-8
    Loaded 1 password hash (ZIP, WinZip [PBKDF2-SHA1 128/128 SSE2 4x])
    No password hashes left to crack (see FAQ)
    
    ┌──(kali㉿kali)-[/kali-share/downloads]
    └─$ john --show war-is-over-hash                                     
    war-is-over/king:ragnarok123:king:war-is-over:war-is-over
    
    1 password hash cracked, 0 left

