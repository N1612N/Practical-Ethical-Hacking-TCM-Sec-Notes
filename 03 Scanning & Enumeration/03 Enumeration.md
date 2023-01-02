### SMB Enumeration

```sh
# In Metasploit
use auxiliary/scanner/smb/smb_version

# Using smbclient in terminal (anonymous login)
$ smbclient -L ////<Target IP>\\
# Press enter for password
# Success if anonymous login possible
# If shares could be listed, Try
$ smbclient ////<Target IP>\\<SHARENAME>
# less chance to work without password
```

```
**Question**: My enum4linux and/or smbclient are not working. I am receiving "Protocol negotiation failed: NT_STATUS_IO_TIMEOUT". How do I resolve?

**Resolution**:

On Kali, edit /etc/samba/smb.conf

Add the following under global:

client min protocol = CORE

client max protocol = SMB3
```

### SSH Enumeration

```sh
$ ssh <Target IP>
# Will Have to negotiate with key exchange with their offered algorithm
$ ssh <Target IP> -oKexAlgorithms=+<offered algorithm by target, such as: diffie-hellman-group1-sha1>
# Will have to negotiate with matching cipher offered by target.
$ ssh <Target IP> -oKexAlgorithms=+<offered algorithm by target, such as: diffie-hellman-group1-sha1> -c <offered matching cipher, such as: aes128-cbc>
# sometimes a banner will be displayed which discloses version information, etc
```