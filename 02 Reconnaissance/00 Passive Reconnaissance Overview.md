
# Physical / Social Recon

Get all the information about a target which will be usefull for the engagement.
+ Location Information
	+ Satelite Images
	+ Drone Visuals
	+ Building Layout
		+ Badge Readers
		+ Fencing
		+ Security
		+ Break Areas,etc..

+ Job Information
	+ Employee Information
		+ Name
		+ ID Card
		+ Job Title
		+ Phone Number
		+ Email Address
		+ Manager
		+ Department
	+ Pictures
		+ Desk Photos
		+ ID Card
		+ Computer Photos

# Web / Host

+ Target Validation
+ whois
```sh
# Domain lookup
> whois <Target Domain>

# Reverse Domain Lookup
> whois <Target IP Address
```

+ nslookup
```sh
# Domain Lookup
> nslookup <Target Domain>

# Reverse Domain Lookup
> nslookup <Target IP Address>

# Specific Domain Lookup
> nslookup <Specific domain: irl.fp.vip.mud.yahoo.com>

# Mail Exchange(MX) Record Query
> nslookup -query=mx <domain: www.yahoo.com>

# Name Server(NS) Record Query
> nslookup -query=ns <domain: www.yahoo.com>

#  All Available DNS Query
> nslookup -query=any <domain: www.yahoo.com>

# Start of Authority(SOA) Record Query
> nslookup -type=soa <domain: www.yahoo.com>
```

+ dnsrecon
```sh
> dnsrecon -d <domain.com> -D <dictionaryLIst: /usr/share/wordlists/dnsmap.txt> -t std

# Zone Transfer using dnsracon
> dnsrecon -d <domain.com> -t axfr
```

Validate the target before initiating the engagement to avoid unneccasery mistakes like scope mishandling, etc.

+ Finding Subdomains
	+ google Fu
https://www.google.com/advanced_search?hl=en-IN&fg=1

	+ dig
```sh
# Get IP Address of target domain
> dig <domain.com>

# Show only IP
>dig <domain.com> +short

# Get IP Address of target domain from specific DNS Server
> dig -server <dns server: 8.8.8.8> <domain.com>

# Check MX Records
> dig <domain.com> MX

# Check NS Records
> dig <domain.com NS>

# Check TXT Records
> dig <domain.com> TXT

# Get all available records
> dig <domain.com> ANY

# Zone Transfer
> dig @<Target IP Address> <domain.com> -t AXFR +nocookie

# dig and trace the name resolution request
> dig +trace <domain.com> <Target IP Address>
```
+ nmap
```sh
> nmap -A -T4 <domain.com> -p- -sV -v -oN <outputFileName>
```

+ sublist3r
https://github.com/aboul3la/Sublist3r
+ bluto
https://github.com/darryllane/Bluto
+ crt.sh
https://crt.sh/
Use other tools as well to enumerate subdomains

+ Fingerprinting
	+ nmap
	+ nikto
	+ wappalyzer
	+ whatweb
	+ builtwith
	+ netcat
	+ telnet
	+ curl, etc..
+ Data Breaches
	+ haveibeenpwned
	+ breachparse
	+ weleakinfo

Resource: 
https://pentester.land/categories/cheatsheets/