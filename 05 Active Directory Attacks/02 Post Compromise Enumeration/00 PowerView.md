Download or save powerview script in victim machine 

https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1

Run powerview in cmd or powershell

```sh
# bypass execution policy
> powershell -ep bypass

# cd to script folder and run powerview
> . .\PowerView.ps1
# dont worry, ther wont be much response. lol !!
# Carry on with other commands
> Get-NetDomain

> Get-NetDomainController

> Get-DomainPolicy
# To check password policy
> (Get-DomainPolicy)."system access"
> Get-NetUser

```


PowerView Cheatsheet 
https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993