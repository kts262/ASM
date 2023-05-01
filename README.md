# ASM - Attack Surface Management
Content for the Attack Surface Management workshop at Educause CPPC 2023

##Submit your findings here: https://forms.gle/RSEorumSMFMBno8i9


## Sample nmap searches

`nmap target`

`nmap -p22 *target*`

`nmap -p22 -sV *target*`

`nmap –p 443 --script ssl-enum-ciphers *target*`

`nmap –p 22 --script “ssh*” *target*`

`nmap –p 135-139,445 --script smb-os-discovery *target*`

`nmap –p 80,443 --script “ssl-*,http-*” *target*`

`nmap --script smb-os-discovery *target*`

`nmap -p443 --script ssl-enum-ciphers *target*`


Output: in "grepable" format `-oG *results*`

### Manipulating nmap -oG output

`grep 445/open *results*`

`grep 445/open *results* | awk ‘{ print $2}’`


## Shodan

Open a web browser and navigate to https://shodan.io 

Start searching for anything you can think of, some examples below (and you can combine multiple search terms into one search

Domain names (`umd.edu`)

IP addresses

Services (`ssh`, `telnet`)

Banners (`“OpenSSH”`, `“SSH-1.99”`)

`net:XX.XX.XX.XX/YY`

`port:443`

`http.status:200`

`org:Stanford`

`country:US`

`title:cyberspacekittens`

`apache city:“College Park”` (Find Apache servers in College Park)

`cisco country:”JP”` (Find cisco equipment in Japan)

`"default password"` (Find devices with the default login credentials still set.)

`ssh -port:22` (Find SSH on non-standard ports)

`vuln:CVE-2023-27350` (Search for a specific vulnerability - Paid/Academic accounts only)


## BloodHound

`sudo apt-get install bloodhound`

`sudo neo4j console`

http://localhost:7474/ (user `neo4j`, password `neo4j` - you will be asked to change the password, don't forget it!)

`bloodhound`

`wget https://github.com/kts262/ASM/raw/main/20230422184725_BloodHound.zip`

## AWS CLI queries

`aws s3api get-bucket-policy-status --bucket "*bucket*"`

`aws s3api get-bucket-policy-status --bucket "*bucket*" --query "PolicyStatus.IsPublic"`



`aws ec2 describe-instances --filters "Name=instance-state-name,Values=running" --query 'Reservations[*].Instances[*].[PublicIpAddress]' --region *region*`
