# Information gathering & Scanning

To collect as much information as possible. Collecting information and knowing deeply about the target system is known as **“Reconnaissance”**. This data is the main street for the hackers to hack the target system. It involves Footprinting, Enumeration, and Scanning.

> **Passive vs. Active reconnaissance**

|                      Passive reconnaissance                      |                      Active reconnaissance                      |
|:----------------------------------------------------------------:|:---------------------------------------------------------------:|
|1. Gathering information without actually connecting to the target.|1. Gathering information about the target while initiating connections.|
|2. Passive reconnaissance generally involves Open Source Intelligence (OSINT) investigation.|2. Active reconnaissance typically involves using of varity of tools like port and vulnerability scanners.|
|3. This allow not being detected while gathering information.|3. This allow you to gather more information but allow you to be detected.|

## Google Dorking


> **Google dork cheatsheet**


**Search filters**
| Filter          | Description                                        | Example                              |
| :-------------- |:---------------------------------------------------| :------------------------------------|
| allintext      | Searches for occurrences of all the keywords given. | `allintext:"keyword"` |
| intext      | Searches for the occurrences of keywords all at once or one at a time. | `intext:"keyword"` |
| inurl      | Searches for a URL matching one of the keywords. | `inurl:"keyword"` |
| allinurl      | Searches for a URL matching all the keywords in the query. | `allinurl:"keyword"` |
| intitle      | Searches for occurrences of keywords in title all or one. | `intitle:"keyword"` |
| allintitle      | Searches for occurrences of keywords all at a time. | `allintitle:"keyword"` |
| site      | Specifically searches that particular site and lists all the results for that site. | `site:"www.google.com"` |
| filetype      | Searches for a particular filetype mentioned in the query. | `filetype:"pdf"` |
| link      | Searches for external links to pages. | `link:"keyword"` |
| numrange      | Used to locate specific numbers in your searches. | `numrange:321-325` |
| before/after      | Used to search within a particular date range. | `filetype:pdf & (before:2000-01-01 after:2001-01-01)` |
| allinanchor (and also inanchor)      | This shows sites which have the keyterms in links pointing to them, in order of the most links. | `inanchor:rat` |
| allinpostauthor (and also inpostauthor)      | Exclusive to blog search, this one picks out blog posts that are written by specific individuals. | `allinpostauthor:"keyword"` |
| related      | List web pages that are “similar” to a specified web page. | `related:www.google.com` |
| cache      | Shows the version of the web page that Google has in its cache. | `cache:www.google.com` |


**Source : [sundowndev](https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06)**


> **GOOGLE HACKING DATABASE**

[![GHDB](https://gitlab.com/uploads/-/system/project/avatar/11903608/kali-exploitdb.png)](https://www.exploit-db.com/google-hacking-database)

## Recon Techniques

**ARP-SCAN**
```sh
┌──(root💀kali)-[/home/kali]
└─# arp-scan -l
Interface: eth0, type: EN10MB, MAC: 00:0c:29:3d:e7:e0, IPv4: 192.168.171.130
Starting arp-scan 1.9.7 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.171.1	00:50:56:c0:00:08	VMware, Inc.
192.168.171.2	00:50:56:f6:56:73	VMware, Inc.
192.168.171.254	00:50:56:e1:3b:6d	VMware, Inc.

3 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.9.7: 256 hosts scanned in 1.991 seconds (128.58 hosts/sec). 3 responded
```

**WHATWEB**
```sh
┌──(root💀kali)-[/home/kali]
└─# whatweb youtube.com
http://youtube.com [301 Moved Permanently] Country[UNITED STATES][US], HTTPServer[ESF], IP[142.250.182.110], RedirectLocation[https://youtube.com/], UncommonHeaders[x-content-type-options], X-Frame-Options[SAMEORIGIN], X-XSS-Protection[0]
https://youtube.com/ [301 Moved Permanently] Country[UNITED STATES][US], HTTPServer[ESF], IP[142.250.182.110], RedirectLocation[https://www.youtube.com/], Strict-Transport-Security[max-age=31536000; includeSubDomains; preload], UncommonHeaders[x-content-type-options,accept-ch,accept-ch-lifetime,permissions-policy,alt-svc], X-Frame-Options[SAMEORIGIN], X-XSS-Protection[0]
https://www.youtube.com/ [200 OK] Cookies[GPS,VISITOR_INFO1_LIVE,YSC], Country[UNITED STATES][US], Frame, HTML5, HTTPServer[ESF], HttpOnly[GPS,VISITOR_INFO1_LIVE,YSC], IP[142.251.42.46], Open-Graph-Protocol[87741124305], OpenSearch[https://www.youtube.com/opensearch?locale=en_GB], Script, Strict-Transport-Security[max-age=31536000], Title[YouTube], UncommonHeaders[x-content-type-options,accept-ch,accept-ch-lifetime,permissions-policy,alt-svc], X-Frame-Options[SAMEORIGIN], X-UA-Compatible[IE=edge], X-XSS-Protection[0]
```

**SubLister**
```sh
 _______________
< !!SuB-ListeR!! >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/
                ||----w |
                ||     ||
Usage: Enter the domain name without <http> or <https>
Example: google.com
Enter the domain name : hackerearth.com

[+] Discovered subdomain: https://www.hackerearth.com
[+] Discovered subdomain: https://blog.hackerearth.com
[+] Discovered subdomain: https://support.hackerearth.com
[+] Discovered subdomain: https://static.hackerearth.com
[+] Discovered subdomain: https://api.hackerearth.com
[+] Discovered subdomain: https://files.hackerearth.com
[+] Discovered subdomain: https://app.hackerearth.com
[+] Discovered subdomain: https://help.hackerearth.com
[+] Discovered subdomain: https://gmail.hackerearth.com
[+] Discovered subdomain: https://s.hackerearth.com
```

### NMAP

- Nmap is probably one of the most important tools in the pentesting tool kit.
- It is a versatile port scanner that can be used to scan entire networks to discover what ports are open.
- Information that nmap can gather includes:
    - Operating system
    - Services running on device
    - Open/closed ports
    - Vulnerabilities on that device

**Usage Nmap**
```md
# TCP syn-awk scan

> nmap -sS [Network]

----------------------------------------------------
# All port scan

> nmap -p- [IP_Adderss]

----------------------------------------------------
# Enumerate versions

> nmap -sV [IP_Adderss]

----------------------------------------------------
# Aggressive OS enumeration

> nmap -A -O [IP_Adderss]

----------------------------------------------------
# Recommended 

> nmap -sC -sV [IP_Adderss]

----------------------------------------------------
# Nmap Scripting Engine(NSE)

> nmap --script=vuln [IP_Adderss]
```

### Vuln_Scanners:

1. Nikto
2. NessusNetsparker
3. Acunetix
