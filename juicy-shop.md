# OWASP - Juicy Shop

# OSINT
## Application
Language: Angular
### Source code
`npm install` tells

    added 2047 packages, and audited 2048 packages in 7m

    149 packages are looking for funding
      run `npm fund` for details

    27 vulnerabilities (13 moderate, 6 high, 8 critical)

Can't run `npm audit`, run first `npm i --package-lock-only`

    ┌──(kali㉿kali)-[~/juice-shop]
    └─$ npm i --package-lock-only
Run `npm audit`

    ┌──(kali㉿kali)-[~/juice-shop]
    └─$ npm audit                
    # npm audit report

    base64url  <3.0.0
    Severity: moderate
    Out-of-bounds Read in base64url - https://github.com/advisories/GHSA-rvg8-pwq2-xj7q
    fix available via `npm audit fix --force`
    Will install jsonwebtoken@8.5.1, which is a breaking change
    node_modules/base64url
      jwa  <=1.1.5
      Depends on vulnerable versions of base64url
      node_modules/jwa
    jws  <=3.1.4
    Depends on vulnerable versions of base64url
    Depends on vulnerable versions of jwa
    node_modules/jws
      jsonwebtoken  <=4.2.2
      Depends on vulnerable versions of jws
      Depends on vulnerable versions of moment
      node_modules/express-jwt/node_modules/jsonwebtoken
      node_modules/jsonwebtoken
        express-jwt  <=5.3.3
        Depends on vulnerable versions of jsonwebtoken
        node_modules/express-jwt

    dicer  *
    Severity: high
    Crash in HeaderParser in dicer - https://github.com/advisories/GHSA-wm7h-9275-    46v2
    No fix available
    node_modules/dicer
      busboy  <=0.3.1
      Depends on vulnerable versions of dicer
      node_modules/busboy
    multer  <=2.0.0-rc.3
    Depends on vulnerable versions of busboy
    node_modules/multer

    ecstatic  <4.1.3
    Severity: moderate
    Denial of Service in ecstatic - https://github.com/advisories/GHSA-jc84-3g44-wf2q
    fix available via `npm audit fix --force`
    Will install http-server@14.1.1, which is a breaking change
    node_modules/ecstatic
      http-server  0.4.0 - 0.12.3
      Depends on vulnerable versions of ecstatic
      node_modules/http-server


    got  <11.8.5
    Severity: moderate
    Got allows a redirect to a UNIX socket - https://github.com/advisories/GHSA-    pfrx-2q88-qq97
    fix available via `npm audit fix --force`
    Will install download@3.3.0, which is a breaking change
    node_modules/got
      download  >=4.0.0
      Depends on vulnerable versions of got
      node_modules/download



    lodash  <=4.17.20
    Severity: critical
    Prototype Pollution in lodash - https://github.com/advisories/GHSA-jf85-cpcp-j695
    Regular Expression Denial of Service (ReDoS) in lodash - https://github.com/advisories/GHSA-x5rq-j2xg-h7qm
    Prototype Pollution in lodash - https://github.com/advisories/GHSA-p6mc-m468-83gw
    Command Injection in lodash - https://github.com/advisories/GHSA-35jh-r3h4-6jhm
    Regular Expression Denial of Service (ReDoS) in lodash - https://github.com/advisories/GHSA-29mw-wpgm-hmr9
    Prototype Pollution in lodash - https://github.com/advisories/GHSA-4xc9-xhrj-v574
    Prototype Pollution in lodash - https://github.com/advisories/GHSA-fvqr-27wr-82fm
    fix available via `npm audit fix --force`
    Will install sanitize-html@1.27.5, which is outside the stated dependency range
    node_modules/sanitize-html/node_modules/lodash
      sanitize-html  <=2.3.1
      Depends on vulnerable versions of lodash
      node_modules/sanitize-html

    marsdb  *
    Severity: critical
    Command Injection in marsdb - https://github.com/advisories/GHSA-5mrr-rgp6-x4gr
    No fix available
    node_modules/marsdb

    minimist  <1.2.6
    Severity: critical
    Prototype Pollution in minimist - https://github.com/advisories/GHSA-xvch-5gv4-984h
    fix available via `npm audit fix`
    node_modules/bower-config/node_modules/minimist
      bower-config  *
      Depends on vulnerable versions of minimist
      Depends on vulnerable versions of mout
      node_modules/bower-config

    moment  <=2.29.1
    Severity: high
    Regular Expression Denial of Service in moment - https://github.com/advisories/GHSA-446m-mv8f-q348
    Regular Expression Denial of Service in moment - https://github.com/advisories/GHSA-87vv-r9j6-g5qv
    Path Traversal: 'dir/../../filename' in moment.locale - https://github.com/advisories/GHSA-8hfj-j24r-96c4
    fix available via `npm audit fix --force`
    Will install jsonwebtoken@8.5.1, which is a breaking change
    node_modules/express-jwt/node_modules/moment

    mout  <=1.2.3
    Severity: high
    Prototype Pollution in mout - https://github.com/advisories/GHSA-vvv8-xw5f-3f88
    fix available via `npm audit fix`
    node_modules/mout

    nanoid  3.0.0 - 3.1.30
    Severity: moderate
    Exposure of Sensitive Information to an Unauthorized Actor in nanoid - https://github.com/advisories/GHSA-qrpm-p2h7-hrv2
    fix available via `npm audit fix`
    node_modules/nanoid
      mocha  8.2.0 - 9.1.4
      Depends on vulnerable versions of nanoid
      node_modules/mocha

    notevil  *
    Severity: moderate
    Sandbox escape in notevil and argencoders-notevil - https://github.com/advisories/GHSA-8g4m-cjm2-96wq
    No fix available
    node_modules/notevil


    vm2  <=3.9.5
    Severity: critical
    Sandbox bypass in vm2 - https://github.com/advisories/GHSA-6pw2-5hjv-9pf7
    Prototype Pollution in vm2 - https://github.com/advisories/GHSA-rjf2-j2r6-q8gr
    fix available via `npm audit fix --force`
    Will install juicy-chat-bot@0.6.4, which is a breaking change
    node_modules/vm2
      juicy-chat-bot  >=0.6.5
      Depends on vulnerable versions of vm2
      node_modules/juicy-chat-bot

    yargs-parser  6.0.0 - 13.1.1
    Severity: moderate
    yargs-parser Vulnerable to Prototype Pollution - https://github.com/advisories/GHSA-p9pc-299p-vxgp
    fix available via `npm audit fix --force`
    Will install webdriver-manager@12.1.8, which is a breaking change
    node_modules/webdriver-manager/node_modules/yargs-parser
      yargs  8.0.0-candidate.0 - 12.0.5
      Depends on vulnerable versions of yargs-parser
      node_modules/webdriver-manager/node_modules/yargs
    webdriver-manager  >=13.0.0-beta
    Depends on vulnerable versions of yargs
    node_modules/webdriver-manager

    27 vulnerabilities (13 moderate, 6 high, 8 critical)

    To address issues that do not require attention, run:
      npm audit fix

    To address all issues possible (including breaking changes), run:
      npm audit fix --force

    Some issues need review, and may require choosing
    a different dependency.

### Routes
Open main.js and find lines with `path:`

    	Line 16800:         path: 'administration',
	Line 16807:         path: 'accounting',
	Line 16814:         path: 'about',
	Line 16818:         path: 'address/select',
	Line 16825:         path: 'address/saved',
	Line 16832:         path: 'address/create',
	Line 16839:         path: 'address/edit/:addressId',
	Line 16846:         path: 'delivery-method',
	Line 16850:         path: 'deluxe-membership',
	Line 17105:         path: 'saved-payment-methods',
	Line 17109:         path: 'basket',
	Line 17113:         path: 'order-completion/:id',
	Line 17117:         path: 'contact',
	Line 17121:         path: 'photo-wall',
	Line 17125:         path: 'complain',
	Line 17129:         path: 'chatbot',
	Line 17133:         path: 'order-summary',
	Line 17137:         path: 'order-history',
	Line 17141:         path: 'payment/:entity',
	Line 17145:         path: 'wallet',
	Line 17149:         path: 'login',
	Line 17153:         path: 'forgot-password',
	Line 17157:         path: 'recycle',
	Line 17161:         path: 'register',
	Line 17165:         path: 'search',
	Line 17169:         path: 'hacking-instructor',
	Line 17173:         path: 'score-board',
	Line 17177:         path: 'track-result',
	Line 17181:         path: 'track-result/new',
	Line 17188:         path: '2fa/enter',
	Line 17192:         path: 'privacy-security',
	Line 17196:             path: 'privacy-policy',
	Line 17200:             path: 'change-password',
	Line 17204:             path: 'two-factor-authentication',
	Line 17208:             path: 'data-export',
	Line 17212:             path: 'last-login-ip',
	Line 17251:         path: '403',
	Line 17255:         path: '**',

### Redirects path
Open main.js and search `redirect`

	Line  4999:           this.windowRefService.nativeWindow.location.replace(`https://accounts.google.com/o/oauth2/v2/auth?client_id=${ this.clientId }&response_type=token&scope=email&redirect_uri=${ this.redirectUri }`)
	Line 13404:               url: './redirect?to=https://blockchain.info/address/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm',
	Line 13414:               url: './redirect?to=https://explorer.dash.org/address/Xr556RzuwX6hg5EGpkybbv5RanJoZN17kW',
	Line 13424:               url: './redirect?to=https://etherscan.io/address/0x0f933ab9fcaaa782d0279c300d73750e1311eae6',
	Line 13773:             './redirect?to=http://shop.spreadshirt.com/juiceshop'
	Line 13783:             './redirect?to=http://shop.spreadshirt.de/juiceshop'
	Line 13787:             './redirect?to=https://www.stickeryou.com/products/owasp-juice-shop/794'
	Line 13797:             './redirect?to=http://leanpub.com/juice-shop'
	Line 19758:             './redirect?to=https://github.com/bkimminich/juice-shop',
	Line 20189:             './redirect?to=https://github.com/bkimminich/juice-shop',

## dirb 


        └─$ dirb http://localhost:1000/                          
        
        -----------------
        DIRB v2.22    
        By The Dark Raver
        -----------------
        
        START_TIME: Mon Aug 29 13:16:06 2022
        URL_BASE: http://localhost:1000/
        WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt
        
        -----------------
        
        GENERATED WORDS: 4612                                                          
        
        ---- Scanning URL: http://localhost:1000/ ----
        + http://localhost:1000/assets (CODE:301|SIZE:179)                                                                                           
        + http://localhost:1000/ftp (CODE:200|SIZE:11062)                                                                                            
        + http://localhost:1000/profile (CODE:500|SIZE:1243)                                                                                         
        + http://localhost:1000/promotion (CODE:200|SIZE:6586)                                                                                       
        + http://localhost:1000/redirect (CODE:500|SIZE:3126)                                                                                        
        + http://localhost:1000/robots.txt (CODE:200|SIZE:28)                                                                                        
                                                                                                                                                     
        (!) FATAL: Too many errors connecting to host
            (Possible cause: RECV ERROR)
                                                                                       
        -----------------
        END_TIME: Mon Aug 29 13:17:07 2022
        DOWNLOADED: 3720 - FOUND: 6
# Files

## http://localhost:3000/ftp/
### List of files
HINT: kdbx files are keypass for windows files

        name: quarantine (folder)
        date: 8/29/2022 2:34:04 PM
        
        name: acquisitions.md
        size: 909
        date: 8/29/2022 2:34:04 PM
        
        name: announcement_encrypted.md
        size: 369237
        date: 8/29/2022 2:34:04 PM
        
        name: coupons_2013.md.bak
        size: 131
        date: 8/29/2022 2:34:04 PM
        
        name: eastere.gg
        size: 324
        date: 8/29/2022 2:34:04 PM
        
        name: encrypt.pyc
        size: 573
        date: 8/29/2022 2:34:04 PM
        
        name: incident-support.kdbx
        size: 3246
        date: 8/29/2022 2:34:04 PM
        
        name: legal.md
        size: 3047
        date: 8/29/2022 2:56:29 PM
        
        name: package.json.bak
        size: 4291
        date: 8/29/2022 2:34:04 PM
        
        name: suspicious_errors.yml
        size: 723
        date: 8/29/2022 2:34:04 PM

# Broken Access Control
## Admin Section
Login as admin and go to http://localhost:3000/#/administration
Got list of users

 - admin@juice-sh.op
 - jim@juice-sh.op
 - bender@juice-sh.op
 - bjoern.kimminich@gmail.com
 - ciso@juice-sh.op
 - support@juice-sh.op
 - morty@juice-sh.op
 - mc.safesearch@juice-sh.op
 - J12934@juice-sh.op
 - wurstbrot@juice-sh.op
 - amy@juice-sh.op
 - bjoern@juice-sh.op
 - bjoern@owasp.org
 - accountant@juice-sh.op
 - uvogin@juice-sh.op
 - demojohn@juice-sh.op
 - emma@juice-sh.op
 - stan@juice-sh.op

## Five-Star Feedback
Login as admin, go to http://localhost:3000/#/administration and delete review

# Improper Input Validation
## Missing Encoding
http://localhost:3000/#/photo-wall
\# is interpeted use %23 instead
## Repetitive Registration
http://127.0.0.1:3000/#/register

 1. Fill email
 2. Fill password
 3. Fill repeat password
 4. Add a char to password
 5. Fill Security Question
 6. Fill answer
 7. Register
## Zero Stars
http://127.0.0.1:3000/#/contact

 1. Open dev tools (F12)
 2. Open network tab
 3. Submit rating
 4. Right-click the request, select "Edit and resend"
 5. Request body example: `{"captchaId":1,"captcha":"17","comment":"test (anonymous)","rating":0}`
 6. Click send

# Injection
## Login Admin
Go to login page
Email: `' or 1=1;`  
Password: `test`

Logged in found email address
    

 - admin@juice-sh.op

# Miscellaneous
## Score board
http://localhost:3000/#/score-board
## Bully Chatbot
http://127.0.0.1:3000/#/chatbot

 1. Hi Juicy
 2. code
 3. coupons

Got this coupon

    k#*Agga+jm
## Privacy Policy
Log in and go to
http://localhost:3000/#/privacy-security/privacy-policy


# Sensitive Data Exposure
## Confidential Document
Download files from ftp folder
## Visual Geo Stalking
[IN PROGRESS]

 - emma@juice-sh.op
 - Downloaded IMG_4253.png from Gallery
 - Search image with Google Lens
   - https://www.google.com/maps/place/Kenaupark+23/@52.3868727,4.6345079,3a,75y,122.75h,90t/data=!3m4!1e1!3m2!1sit5fyfWvAhub305bDLCP9A!2e0!4m2!3m1!1s0x47c5ef6d6a305d03:0x9190d48aff770ba1?sa=X&ved=2ahUKEwic_Y7k6u35AhVHh_0HHccpDVYQxB16BAgMEAI

# Unvalidated Redirects
## Outdated Allowlist
http://localhost:3000/redirect?to=https://explorer.dash.org/address/Xr556RzuwX6hg5EGpkybbv5RanJoZN17kW
# XSS
Send HTML in the search field 
## DOM XSS
    <iframe src="javascript:alert(`xss`)">
## Bonus Payload
    <iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe> 
