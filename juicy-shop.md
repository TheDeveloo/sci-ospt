# OWASP - Juicy Shop

# OSINT
## Application
Language: Angular
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
# Injection
## XSS
Send HTML in the search field 

# Chatbot
Asked him "coupons"

    k#*Agga+jm
# Admin user
Go to login page
Email: `' or 1=1;`  
Password: `test`

Logged in found email address
    admin@juice-sh.op
