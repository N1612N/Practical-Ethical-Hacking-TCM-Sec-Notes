```sh
# Install BloodHound
> sudo apt install bloodhound

> neo4j console
# Open the remove interface in browser
# Change default credetial from : neo4j // neo4j

# In new terminal tab
> bloodhound

# Login to bllodhound in browser using changed credential
```

## Invoke Bloodhound
Invoke Bloodhound is used in powershell
Can use sharphound written in C# or a script written in python.

Copy the invoke bloodhound file from git and save in victim windows machine.
script: https://github.com/BloodHoundAD/BloodHound/blob/master/Collectors/SharpHound.ps1

```sh

# Navigate to script folder in cmd of victim windows machine
> powershell -ep bypass
> . \sharpHound.ps1
# there wont be much response
> Invoke-BloodHound -CollectionMethod All -Domain <domainname: MARVEL.local> -ZipFileName <filename: file.zip>

# Move the zip file from victim machine to attacker machine.
```