## WHOIS
https://whois.icann.org/en

## WAY BACK MACHINE
https://archive.org/

## GOOGLEDORKS
Usage
searchString options $url
Example
Search for a PDF containing the string "Resume" on a website
"Resume" filetype:pdf site:$url
Options
site: Returns files located on a specified website or domain
Filetype: Returns files of a specific type

* DOC
* PDF
* XLS
* TXT

Inurl: Returns results with the specified characters in the URL
Intext: Returns files with the string anywhere in the text

## SHODAN
shodan.io

## DNSDUMPSTER
https://dnsdumpster.com

----

# Recon (CLI Publicly available information)


## THE HARVESTER

usage
theharvester -d target -b searchEngine -f $out
Example
theharvester -d $url -b linkedin
options
-d: Domain to search or company name
-b: Data source (google,bing, bingapi,pgp,linkedin, google-profiles,people123,jigsaw, all)
-s: Start in result number X (default 0)
-v: verify host name via dns resolution and virtual hosts
-f: save the results into an HTML and XML file
-n: Perform a DNS reverse query on all ranges discovered
-c: Perform a DNS brute force for the domain name
-t: Perform a DNS TLD expansion discovery
-l: Limit the number of results to work with(bing goes from 50 to 50 results,
-h: use SHODAN database to query discovered hosts google
100 to 100, and pgp doesn't use this option)

## DMITRY
Usage
dmitry options target
Example
Basic Usage:
dmitry -winseo $out $url
options
-o: save output to %host.txt or to file specified by -o file
-i: Perform a whois lookup on the IP address of a host
-w: Perform a whois lookup on the domain name of a host
-n: Retrieve Netcraft.com information on a host
-s: Perform a search for possible subdomains
-e: Perform a search for possible email addresses


-----
# Recon (DNS)


## DIG

usage
dig options target
Examples
dig ($url or $ip)
Zone Transfer
dig -t axfr ($url or $ip)
Display only the ANSWER SECTION
dig ($url or $ip) +noall answer
Query the A record:
dig -t A $url
Query the MX record:
dig -t MX $url
Query the Ns record
dig -t NS $url
Query all of the available records;
dig -t ANY $url

options
-t: query type

* AXFR: Zone tranfer
* IXFR: Incremental zone tranfer
* MX: Mx records
* A: A record
* NS: NS record
* ANY: Query all records
-noall: set or clear all display flags
-answer: Control display of answer section

## DNSENUM

Usage
dnsenum options target
Examples
Basic Scan:
dnsenum $url
Full Scan:
dnsenum -enum $url
Find subdomains:
dnsenum -s 5 -p 5 $url
Brute force subdomains
dnsenum -enum -r $url

Options
-s: max number of subdomains that will be scraped from Google
-p: number of google search pages processed when scraping names
-enum: Shortcut option equivalent to --threads 5 -s 15 -w
-r: brute force all discovered subdomains

----

## NSLOOKUP

usage
nslookup options target
Example
Basic Usage:
nslookup ($url or $ip)
Checking for an A record:
nslookup -type=A ($url or $ip)
Checking for MX record:
nslookup -type=Mx $url
Checking for TXT record:
nslookup -type=TXT $url
Query the authoritative server:
nslookup -type=SOA $url
Check the length of time a record is cached
nslookup -type=(desired record type) -debug ($url or $ip)

options
-type: specifies desired record to be queried
-debug: Query the length of time a record is cached


## DNSRECON
usage
dnsrecon target options
Example
DNS bruteforce:
dnsrecon -d $ip -D wordlist.txt -t std --xml ouput.xml

Options
-d: Specifies a domain to target
-D: Sets the dictionary file to be used
-t: Sets the enumeration type
\*std: Record types such as SOA, NS, A, AAAA, and MX
--xml: Specifies an XML file to save the output to

----

# Scanning and Enumeration (General)


## NMAP

Usage
nmap options target
Examples
Use a list of targets for a scan:
nmap -iL targetlist.txt
Exclude an ip from a scan
nmap options target --exclude $ip
Scan a specified port:
nmap -p $port $ip
TCP SYN Scan
nmap -sS $ip
TCP connect scan:
nmap -sT $ip
UDP-scans
nmap -sU $ip
Os Scan:
nmap -o $ip
Service version scan:
nmap -sV $ip
Firewall detection scan:
nmap -sA $ip
Firewall protection detection scan:
nmap -PN $ip
Perform a fast scan
nmap -F $ip
NSE scan
Nmap --script-ScriptName $ip
ICMP Sweep:
Nmap -sn $ip -oG ping-sweep.txt
Identify what is responding:
grep up ping-sweep. txt | cut -d " " -f2
output scan results to file:
nmap options target -oA fileName

----

options
-iL: Input from list of hosts/networks
-p: Only scan specified ports
-sS: TCP SYN Scan
-sT: Connect scan
-sU: UDP Scan
-o: Enable os detection
-sV: Probe open ports to determine service/version info
-sA: ACK
-Pn: Treat all hosts as online
-F: Fast mode scan fewer ports than the defa
-oG: output scan in normal, XML, scrIpt kiddi3
-sn: Ping Scan - disable port scan

Notes
NSE scripts can be found at /usr/share/nmap/scripts


## NPING

Usage
nping options target
Examples
Basic scan:
nping $ip
TCP connect scan
nping -tcp-connect $ip
TCP connect scan with a port range:
nping tcp-connect $ip -p1-1000
UDP scan
nping -udp $ip
ARP Scan
nping --arp $ip
Send random data of desired size
nping $ip --data-length 100

options
-tcp-connect: Unprivileged TCP connect probe mode
-p: Set destination port(s).
-udp: UDP probe mode.
-arp: ARP/RARP probe mode
-data-length: Include random bytes as payload


----

## METASPLOIT NMAP
step 1 Database Setup
1. start postgres server
service postgresql start
2. Initialize the database:
msfdb init
3. connect to the database:
msfdb start
4. Check database connection status:
    1. msfconsole
    2. msf> db_status
5. reinitialize the database (If needed):
msfdb reinit

#### Database setup notes
If the database is successfully connected you will
get the following message "[\*] postgresql connected to
msf" If you do not receive this message you will need to
reinitialize the database.
Once the database is reinitialized you will need
to run msfdb start to reconnect to the database.
Step 2 Workspace setup
1. Check workspace being used
msfworkspace
2. Create a workspace:
msf workspace -a workspaceName
3. Change workspaces:
msfworkspace workspaceName
4. Delete a workspace (If desired):
msf workspace -d workspaceName

Workspace options
-a Create a database
-d Delete a database

----

METASPLOIT NMAP (CONTINUED)
step 3 Performing the scan
Scanning:
msf> dbnmap options $ip


Performing the scan notes 
Scan results will be saved in the user current database. 
This command works the same way as the command line version of Nmap. See the Nmap portion
of this book for scan examples.

step 4 viewing the data
View hosts (Basic)
msf > hosts
View hosts (Display the address and OS columns);
msf > hosts -c address,os flavor,os_name
View hosts (Search for a string):
msf > hosts -s linux
View services (Basic):
msf > services
view services (Display the name and info columns of a host)
msf > services -c name, info $ip
view services (search for a specific port)
msf services -p $port
View vulnerabilities:
msf > vulns

Viewing the data options
-c used to filter columns
-s used to search for a string
-p used to specify a port

Step 5 Backing up the data
Export msf database
msf > db_export -f xml /desired/location/Export.xml

backing up the data options
-f specify the output format. Either 'xml' or 'pwdump'

----

## UNICORNSCAN

usage
unicornscan options target
Examples
Basic scan:
unicornscan $ip/$sn
TCP scanning:
unicornscan -r200 -mT $ip:80,443
UDP Scanning:
unicornscan -r300 -mu $ip
Output to a PCAP file and spoof an IP:
unicornscan $ip/$sn -r500 -w $out.pcap -w1 -s $ip

options
-r: packets per second
-mT: TCP scan mode
-mU: UDP scan mode
-w: write PCAP file of received packets
-W: Perform an os fingerprint
0=cisco(def) 1=openbsd 2=WindowsXP 3=pOfsendsyn
4=FreeBSD 5=nmap 6=linux 7:strangetcp
-s: set the source address


## NETCAT
Usage
netcat options target port
Examples
Port scan:
netcat -z -v $ip $port-$port
Banner grab:
nc -nv $ip $port
SMTP:
1 connection
nc -nv $ip 25
2 verify user
VRFY UserName
Options
-z zero-I/O mode [used for scanning]
-v verbose [use twice to be more verbose]
-n numeric-only IP addresses, no DNS

----

## NETDISCOVER

Usage
netdiscover options host
Examples
Basic scan:
netdiscover -r $ip/$sn
Fast Scan:
netdiscover -fr $ip/$sn
Passive Scan:
netdiscover -p
Scan a list of mac address and host names
netdiscover -m fileName.txt
Scan a list of ranges:
netdiscover -l fileName. txt
options
-r Scan a given range instead of auto scan
-l scan the list of ranges contained in the given file
-p Do not send anything, only sniff
-m Scan the list of known MACS and host names
-f enable fastmode scan


## DMITRY

Usage
dmitry options host
Example
Basic port scan
dmitry -pfbo $out.txt $url
Domain lookup:
dmitry -winsep $url

Options
-o save output to %host.txt or to file specified
-p Perform a TCP port scan on a host
-f Perform a TCP port scan on a host showing output reporting filtered ports
-b Read in the banner received from the scanned port
-w domain whois lookup
-i IP whois
-e subdomain address lookup
-n netcraft info

----

## HPING3

Usage
hping3 options target
Examples
Testing ICMP:
hping3 -1 $url
Traceroute using ICMP
hping3 --traceroute -v -1 $url
Checking port
hping3 -v -s -p $port -s 5050 $url
Traceroute to a determined port:
hping3 --traceroute -V -s -p $port -s 5050 $url
Xmas Scan:
hping3 -c 1 -v -p $port -s 5050 -M 0 -UPF $url
Smurf Attack:
hping3 -1 --flood -a $ip BROADCAST_ADDRESS
DOS Land Attack
hping3 -v -c 1000000 -d 120 -s -w 64 -p $port -s $port flood --rand-source $ip

Options
-1 --icmp ICMP mode
-V --verbose verbose mode
-s --syn set SYN flag
-p destination port(default 0)
-s --baseport base source port (default random)
-c --count packet count
-M --setseq set TCP sequence number
-w --win winsize (default 64)
-d --data data size (default is 0)
--flood sent packets as fast as possible. Don't show replies
--rand-source random source address mode. see the man
-T --traceroute traceroute mode (implies --bind and --ttl)


----

## MASSCAN

usage
masscan options target
Examples
Scan a network for web ports
masscan $ip -p80,443,8080
Scan a network for all ports:
masscan $ip -p0-65535

options
-p: port or port range


## ENUM4LINUX

Usage
enum4linux options target
Example
Simple enumeration
enum4linux -a $ip
Enumerate a list of users:
enum4linux -U $ip
Enumerate a list of groups and users
enum4linux -G $ip
Enumerate shares:
enum4linux -s $ip
Enumerate password policy info:
enum4linux -P $ip
Utilise credentials for the scan:
enum4linux -u $user -p $pass -a $ip
options
-U: Get list of users
-s: Get list of shares
-P: Get password policy information
-G: Get group and member list
-u: Specify username to use
-p: Specify password to use
-a: Enumerate all
-v: specify verbose output


# Scanning and Enumeration (SNMP)

## ONESIXTYONE

Usage
onesixtyone options target
Examples
Single target:
onesixtyone -c communityfile.txt $ip
Multiple targets:
onesixtyone -c communityfile.txt -i iplist.txt
Scan with output:
onesixtyone -c communityfile.txt $ip -o $out.log
Adding a delay to the scan
onesixtyone -c communityfile.txt $ip -w 100

Options
-c file with community names to try
-i file with target hosts
-o output log
-w wait in milliseconds 1/1000 of a second

Notes
The community file is a self generated file with a
list of communities to search for. Examples are public,
private, and manager. The -i option can be used with an IP list file.


## NMAP (SNMP SCRIPTS)

SNMP scans
snmp brute:
nmap $ip -Pn -sU -p 161 -script=snmp-brute

snmp interfaces
nmap $ip -Pn -sU -p 161 -script=snmp-interfaces
options
-sU: UDP Scan
-Pn: Treat all hosts as online
-p: only scan specified ports

Notes
See "Scanning and Enumeration (General)" for more
NMAP options and usage details.


----

## SNMPWALK

Syntax
snmpwalk -c community -vSNMPVersion target mibValue
Example
Basic Scan
snmpwalk -c public -v1 $ip
Specifying a mib value:
snmpwalk -c public -v1 $ip 1.3.6.1.2.1.25.4.2.1.2
Options
-c Set the community string
-v Specifies the SNMP version to use
\* 1
\* 2c
\* 3
-mib values
Value| Resulting info
1.3.6.1.2.1.25.1.6.0| System Processes
1.3.6.1.2.1.25.4.2.1.2| Running Programs
1.3.6.1.2.1.25.4.2.1.4| Processes Path
1.3.6.1.2.1.25.2.3.1.4| Storage Units
1.3.6.1.2.1.25.6.3.1.2| software Name
1.3.6.1.2.1.77.1.2.25| User Accounts
1.3.6.1.2.1.6.13.1.3| TCP Local ports 


----

## RPCCLIENT

step 1 Login
Logging in using a null session:
1.1 rpcclient -U "" $ip
1.2 when prompted for a password hit enter

Login options
-u used to set username

step 2 Enumeration
OS information:
rpcclient $> srvinfo
Users:
Rpcclient $> enumdomusers
Password policy information:
rpcclient $> getdompwinfo


## NMAP

Null session scans
nmap -p 139,445 -script smb-enum-users $ip

Options
-p: Only scan specified ports

Notes
see the Nmap portion of "scanning and Enumeration
(General)" for more options and usage details.


## NET USE

Step 1 Connect to share
net use \\$ip\shareName "" /user:""
Step 2 Access share
net view \\$ip
Step 3 Enumerate info from the share
Administrator enumeration
local administrators \\$ip
Domain admin enumeration:
global "domain admins" \\$ip
