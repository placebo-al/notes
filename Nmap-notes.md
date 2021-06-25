# Nmap Target Selection

Scan a single IP:  nmap 192.168.1.1
Scan a host:   nmap www.testhostname.com
Scan a range of IPs:   nmap 192.168.1.1-20
Scan a subnet: nmap 192.168.1.0/24
Scan targets from a text file: nmap -iL list-of-ips.txt

These are all default scans, which will scan 1000 TCP ports. Host discovery will take place.

# Nmap Port Selection

Scan a single Port: nmap -p 22 192.168.1.1
Scan a range of ports:  nmap -p 1-100 192.168.1.1
Scan 100 most common ports (Fast):  nmap -F 192.168.1.1
Scan all 65535 ports:   nmap -p- 192.168.1.1

# Nmap Port Scan types

Scan using TCP connect: nmap -sT 192.168.1.1
Scan using TCP SYN scan (default:   	nmap -sS 192.168.1.1
Scan UDP ports: nmap -sU -p 123,161,162 192.168.1.1
Scan selected ports - ignore discovery: nmap -Pn -F 192.168.1.1

Service and OS Detection

Detect OS and Services: nmap -A 192.168.1.1
Standard service detection: nmap -sV 192.168.1.1
More aggressive Service Detection:  nmap -sV --version-intensity 5 192.168.1.1
Lighter banner grabbing detection:  nmap -sV --version-intensity 0 192.168.1.1


Nmap Output Formats

Save default output to file:    nmap -oN outputfile.txt 192.168.1.1
Save results as XML:    nmap -oX outputfile.xml 192.168.1.1
Save results in a format for grep:  nmap -oG outputfile.txt 192.168.1.1
Save in all formats:    nmap -oA outputfile 192.168.1.1


A scan to search for DDOS reflection UDP services

Scan for UDP DDOS reflectors:   nmap –sU –A –PN –n –pU:19,53,123,161 –script=ntp-monlist,dns-recursion,snmp-sysdescr 192.168.1.0/24

HTTP Service Information

Gather page titles from HTTP services:  nmap --script=http-title 192.168.1.0/24
Get HTTP headers of web services:   nmap --script=http-headers 192.168.1.0/24
Find web apps from known paths: nmap --script=http-enum 192.168.1.0/24

Detect Heartbleed SSL Vulnerability

Heartbleed Testin:  nmap -sV -p 443 --script=ssl-heartbleed 192.168.1.0/24

IP Address information

Find Information about IP address:  	nmap --script=asn-query,whois,ip-geolocation-maxmind 192.168.1.0/24


#1: Scan a single host or an IP address (IPv4)

### Scan a single ip address ###
nmap 192.168.1.1
 
## Scan a host name ###
nmap server1.cyberciti.biz
 
## Scan a host name with more info###
nmap -v server1.cyberciti.biz

#2: Scan multiple IP address or subnet (IPv4)

nmap 192.168.1.1 192.168.1.2 192.168.1.3
## works with same subnet i.e. 192.168.1.0/24 
nmap 192.168.1.1,2,3
You can scan a range of IP address too:

nmap 192.168.1.1-20
You can scan a range of IP address using a wildcard:

nmap 192.168.1.*
Finally, you scan an entire subnet:

nmap 192.168.1.0/24

#3: Read list of hosts/networks from a file (IPv4)

The -iL option allows you to read the list of target systems using a text file. This is useful to scan a large number of hosts/networks. Create a text file as follows:
cat > /tmp/test.txt

Sample outputs:

server1.cyberciti.biz
192.168.1.0/24
192.168.1.1/24
10.1.2.3
localhost
The syntax is:

nmap -iL /tmp/test.txt

#4: Excluding hosts/networks (IPv4)

When scanning a large number of hosts/networks you can exclude hosts from a scan:

nmap 192.168.1.0/24 --exclude 192.168.1.5
nmap 192.168.1.0/24 --exclude 192.168.1.5,192.168.1.254
OR exclude list from a file called /tmp/exclude.txt

nmap -iL /tmp/scanlist.txt --excludefile /tmp/exclude.txt

#5: Turn on OS and version detection scanning script (IPv4)

nmap -A 192.168.1.254
nmap -v -A 192.168.1.1
nmap -A -iL /tmp/scanlist.txt 

#6: Find out if a host/network is protected by a firewall

nmap -sA 192.168.1.254
nmap -sA server1.cyberciti.biz

#7: Scan a host when protected by the firewall

nmap -PN 192.168.1.1
nmap -PN server1.cyberciti.biz

#8: Scan an IPv6 host/address

The -6 option enable IPv6 scanning. The syntax is:

nmap -6 IPv6-Address-Here
nmap -6 server1.cyberciti.biz
nmap -6 2607:f0d0:1002:51::4
nmap -v A -6 2607:f0d0:1002:51::4

#9: Scan a network and find out which servers and devices are up and running

This is known as host discovery or ping scan:

nmap -sP 192.168.1.0/24
Sample outputs:

Host 192.168.1.1 is up (0.00035s latency).
MAC Address: BC:AE:C5:C3:16:93 (Unknown)
Host 192.168.1.2 is up (0.0038s latency).
MAC Address: 74:44:01:40:57:FB (Unknown)
Host 192.168.1.5 is up.
Host nas03 (192.168.1.12) is up (0.0091s latency).
MAC Address: 00:11:32:11:15:FC (Synology Incorporated)
Nmap done: 256 IP addresses (4 hosts up) scanned in 2.80 second

#10: How do I perform a fast scan?

nmap -F 192.168.1.1

#11: Display the reason a port is in a particular state

nmap --reason 192.168.1.1
nmap --reason server1.cyberciti.biz

#12: Only show open (or possibly open) ports

nmap --open 192.168.1.1
nmap --open server1.cyberciti.biz

#13: Show all packets sent and received

nmap --packet-trace 192.168.1.1
nmap --packet-trace server1.cyberciti.biz

#14: Show host interfaces and routes

This is useful for debugging (ip command or route command or netstat command like output using nmap)

nmap --iflist
Sample outputs:

Starting Nmap 5.00 ( http://nmap.org ) at 2012-11-27 02:01 IST
************************INTERFACES************************
DEV    (SHORT)  IP/MASK          TYPE        UP MAC
lo     (lo)     127.0.0.1/8      loopback    up
eth0   (eth0)   192.168.1.5/24   ethernet    up B8:AC:6F:65:31:E5
vmnet1 (vmnet1) 192.168.121.1/24 ethernet    up 00:50:56:C0:00:01
vmnet8 (vmnet8) 192.168.179.1/24 ethernet    up 00:50:56:C0:00:08
ppp0   (ppp0)   10.1.19.69/32    point2point up
 
**************************ROUTES**************************
DST/MASK         DEV    GATEWAY
10.0.31.178/32   ppp0
209.133.67.35/32 eth0   192.168.1.2
192.168.1.0/0    eth0
192.168.121.0/0  vmnet1
192.168.179.0/0  vmnet8
169.254.0.0/0    eth0
10.0.0.0/0       ppp0
0.0.0.0/0        eth0   192.168.1.2

#15: How do I scan specific ports?

nmap -p [port] hostName
## Scan port 80
nmap -p 80 192.168.1.1
 
## Scan TCP port 80
nmap -p T:80 192.168.1.1
 
## Scan UDP port 53
nmap -p U:53 192.168.1.1
 
## Scan two ports ##
nmap -p 80,443 192.168.1.1
 
## Scan port ranges ##
nmap -p 80-200 192.168.1.1
 
## Combine all options ##
nmap -p U:53,111,137,T:21-25,80,139,8080 192.168.1.1
nmap -p U:53,111,137,T:21-25,80,139,8080 server1.cyberciti.biz
nmap -v -sU -sT -p U:53,111,137,T:21-25,80,139,8080 192.168.1.254
 
## Scan all ports with * wildcard ##
nmap -p "*" 192.168.1.1
 
## Scan top ports i.e. scan $number most common ports ##
nmap --top-ports 5 192.168.1.1
nmap --top-ports 10 192.168.1.1
Sample outputs:

Starting Nmap 5.00 ( http://nmap.org ) at 2012-11-27 01:23 IST
Interesting ports on 192.168.1.1:
PORT     STATE  SERVICE
21/tcp   closed ftp
22/tcp   open   ssh
23/tcp   closed telnet
25/tcp   closed smtp
80/tcp   open   http
110/tcp  closed pop3
139/tcp  closed netbios-ssn
443/tcp  closed https
445/tcp  closed microsoft-ds
3389/tcp closed ms-term-serv
MAC Address: BC:AE:C5:C3:16:93 (Unknown)
 
Nmap done: 1 IP address (1 host up) scanned in 0.51 seconds

#16: The fastest way to scan all your devices/computers for open ports ever

nmap -T5 192.168.1.0/24

#17: How do I detect remote operating system?

You can identify a remote host apps and OS using the -O option:

nmap -O 192.168.1.1
nmap -O  --osscan-guess 192.168.1.1
nmap -v -O --osscan-guess 192.168.1.1
Sample outputs:

Starting Nmap 5.00 ( http://nmap.org ) at 2012-11-27 01:29 IST
NSE: Loaded 0 scripts for scanning.
Initiating ARP Ping Scan at 01:29
Scanning 192.168.1.1 [1 port]
Completed ARP Ping Scan at 01:29, 0.01s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 01:29
Completed Parallel DNS resolution of 1 host. at 01:29, 0.22s elapsed
Initiating SYN Stealth Scan at 01:29
Scanning 192.168.1.1 [1000 ports]
Discovered open port 80/tcp on 192.168.1.1
Discovered open port 22/tcp on 192.168.1.1
Completed SYN Stealth Scan at 01:29, 0.16s elapsed (1000 total ports)
Initiating OS detection (try #1) against 192.168.1.1
Retrying OS detection (try #2) against 192.168.1.1
Retrying OS detection (try #3) against 192.168.1.1
Retrying OS detection (try #4) against 192.168.1.1
Retrying OS detection (try #5) against 192.168.1.1
Host 192.168.1.1 is up (0.00049s latency).
Interesting ports on 192.168.1.1:
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: BC:AE:C5:C3:16:93 (Unknown)
Device type: WAP|general purpose|router|printer|broadband router
Running (JUST GUESSING) : Linksys Linux 2.4.X (95%), Linux 2.4.X|2.6.X (94%), MikroTik RouterOS 3.X (92%), Lexmark embedded (90%), Enterasys embedded (89%), D-Link Linux 2.4.X (89%), Netgear Linux 2.4.X (89%)
Aggressive OS guesses: OpenWrt White Russian 0.9 (Linux 2.4.30) (95%), OpenWrt 0.9 - 7.09 (Linux 2.4.30 - 2.4.34) (94%), OpenWrt Kamikaze 7.09 (Linux 2.6.22) (94%), Linux 2.4.21 - 2.4.31 (likely embedded) (92%), Linux 2.6.15 - 2.6.23 (embedded) (92%), Linux 2.6.15 - 2.6.24 (92%), MikroTik RouterOS 3.0beta5 (92%), MikroTik RouterOS 3.17 (92%), Linux 2.6.24 (91%), Linux 2.6.22 (90%)
No exact OS matches for host (If you know what OS is running on it, see http://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=5.00%D=11/27%OT=22%CT=1%CU=30609%PV=Y%DS=1%G=Y%M=BCAEC5%TM=50B3CA
OS:4B%P=x86_64-unknown-linux-gnu)SEQ(SP=C8%GCD=1%ISR=CB%TI=Z%CI=Z%II=I%TS=7
OS:)OPS(O1=M2300ST11NW2%O2=M2300ST11NW2%O3=M2300NNT11NW2%O4=M2300ST11NW2%O5
OS:=M2300ST11NW2%O6=M2300ST11)WIN(W1=45E8%W2=45E8%W3=45E8%W4=45E8%W5=45E8%W
OS:6=45E8)ECN(R=Y%DF=Y%T=40%W=4600%O=M2300NNSNW2%CC=N%Q=)T1(R=Y%DF=Y%T=40%S
OS:=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%R
OS:D=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=
OS:0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID
OS:=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)
Uptime guess: 12.990 days (since Wed Nov 14 01:44:40 2012)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=200 (Good luck!)
IP ID Sequence Generation: All zeros
Read data files from: /usr/share/nmap
OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.38 seconds
           Raw packets sent: 1126 (53.832KB) | Rcvd: 1066 (46.100KB)
See also: Fingerprinting a web-server and a dns server command line tools for more information.

#18: How do I detect remote services (server / daemon) version numbers?

nmap -sV 192.168.1.1
Sample outputs:

Starting Nmap 5.00 ( http://nmap.org ) at 2012-11-27 01:34 IST
Interesting ports on 192.168.1.1:
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     Dropbear sshd 0.52 (protocol 2.0)
80/tcp open  http?
1 service unrecognized despite returning data.

#19: Scan a host using TCP ACK (PA) and TCP Syn (PS) ping

If firewall is blocking standard ICMP pings, try the following host discovery methods:

nmap -PS 192.168.1.1
nmap -PS 80,21,443 192.168.1.1
nmap -PA 192.168.1.1
nmap -PA 80,21,200-512 192.168.1.1

#20: Scan a host using IP protocol ping

nmap -PO 192.168.1.1

#21: Scan a host using UDP ping

This scan bypasses firewalls and filters that only screen TCP:

nmap -PU 192.168.1.1
nmap -PU 2000.2001 192.168.1.1

#22: Find out the most commonly used TCP ports using TCP SYN Scan

### Stealthy scan ###
nmap -sS 192.168.1.1
 
### Find out the most commonly used TCP ports using  TCP connect scan (warning: no stealth scan)
###  OS Fingerprinting ###
nmap -sT 192.168.1.1
 
### Find out the most commonly used TCP ports using TCP ACK scan
nmap -sA 192.168.1.1
 
### Find out the most commonly used TCP ports using TCP Window scan
nmap -sW 192.168.1.1
 
### Find out the most commonly used TCP ports using TCP Maimon scan
nmap -sM 192.168.1.1

#23: Scan a host for UDP services (UDP scan)

Most popular services on the Internet run over the TCP protocol. DNS, SNMP, and DHCP are three of the most common UDP services. Use the following syntax to find out UDP services:

nmap -sU nas03
nmap -sU 192.168.1.1
Sample outputs:

Starting Nmap 5.00 ( http://nmap.org ) at 2012-11-27 00:52 IST
Stats: 0:05:29 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 32.49% done; ETC: 01:09 (0:11:26 remaining)
Interesting ports on nas03 (192.168.1.12):
Not shown: 995 closed ports
PORT     STATE         SERVICE
111/udp  open|filtered rpcbind
123/udp  open|filtered ntp
161/udp  open|filtered snmp
2049/udp open|filtered nfs
5353/udp open|filtered zeroconf
MAC Address: 00:11:32:11:15:FC (Synology Incorporated)
 
Nmap done: 1 IP address (1 host up) scanned in 1099.55 seconds

#24: Scan for IP protocol

This type of scan allows you to determine which IP protocols (TCP, ICMP, IGMP, etc.) are supported by target machines:

nmap -sO 192.168.1.1

#25: Scan a firewall for security weakness

The following scan types exploit a subtle loophole in the TCP and good for testing security of common attacks:

## TCP Null Scan to fool a firewall to generate a response ##
## Does not set any bits (TCP flag header is 0) ##
nmap -sN 192.168.1.254
 
## TCP Fin scan to check firewall ##
## Sets just the TCP FIN bit ##
nmap -sF 192.168.1.254
 
## TCP Xmas scan to check firewall ##
## Sets the FIN, PSH, and URG flags, lighting the packet up like a Christmas tree ##
nmap -sX 192.168.1.254
See how to block Xmas packkets, syn-floods and other conman attacks with iptables.

#26: Scan a firewall for packets fragments

The -f option causes the requested scan (including ping scans) to use tiny fragmented IP packets. The idea is to split up the TCP header over
several packets to make it harder for packet filters, intrusion detection systems, and other annoyances to detect what you are doing.

nmap -f 192.168.1.1
nmap -f fw2.nixcraft.net.in
nmap -f 15 fw2.nixcraft.net.in

## Set your own offset size with the --mtu option ##
nmap --mtu 32 192.168.1.1

#27: Cloak a scan with decoys

The -D option it appear to the remote host that the host(s) you specify as decoys are scanning the target network too. Thus their IDS might report 5-10 port scans from unique IP addresses, but they won’t know which IP was scanning them and which were innocent decoys:

nmap -n -Ddecoy-ip1,decoy-ip2,your-own-ip,decoy-ip3,decoy-ip4 remote-host-ip
nmap -n -D192.168.1.5,10.5.1.2,172.1.2.4,3.4.2.1 192.168.1.5

#28: Scan a firewall for MAC address spoofing

### Spoof your MAC address ##
nmap --spoof-mac MAC-ADDRESS-HERE 192.168.1.1
 
### Add other options ###
nmap -v -sT -PN --spoof-mac MAC-ADDRESS-HERE 192.168.1.1
 
 
### Use a random MAC address ###
### The number 0, means nmap chooses a completely random MAC address ###
nmap -v -sT -PN --spoof-mac 0 192.168.1.1

#29: How do I save output to a text file?

The syntax is:

nmap 192.168.1.1 > output.txt
nmap -oN /path/to/filename 192.168.1.1
nmap -oN output.txt 192.168.1.1

#30 Scans for web servers and pipes into Nikto for scanning

nmap -p80 192.168.1.2/24 -oG - | /path/to/nikto.pl -h -
nmap -p80,443 192.168.1.2/24 -oG - | /path/to/nikto.pl -h -

#31 Speed up nmap

Pass the -T option:
nmap -v -sS -A -T4 192.168.2.5

Sample outputs:

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-15 01:52 IST
NSE: Loaded 143 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 01:52
Completed NSE at 01:52, 0.00s elapsed
Initiating NSE at 01:52
Completed NSE at 01:52, 0.00s elapsed
Initiating ARP Ping Scan at 01:52
Scanning 192.168.2.15 [1 port]
Completed ARP Ping Scan at 01:52, 0.01s elapsed (1 total hosts)
Initiating SYN Stealth Scan at 01:52
Scanning dellm6700 (192.168.2.15) [1000 ports]
Discovered open port 5900/tcp on 192.168.2.15
Discovered open port 80/tcp on 192.168.2.15
Discovered open port 22/tcp on 192.168.2.15
Completed SYN Stealth Scan at 01:53, 4.62s elapsed (1000 total ports)
Initiating Service scan at 01:53
Scanning 3 services on dellm6700 (192.168.2.15)
Completed Service scan at 01:53, 6.01s elapsed (3 services on 1 host)
Initiating OS detection (try #1) against dellm6700 (192.168.2.15)
Retrying OS detection (try #2) against dellm6700 (192.168.2.15)
NSE: Script scanning 192.168.2.15.
Initiating NSE at 01:53
Completed NSE at 01:53, 30.02s elapsed
Initiating NSE at 01:53
Completed NSE at 01:53, 0.00s elapsed
Nmap scan report for dellm6700 (192.168.2.15)
Host is up (0.00044s latency).
Not shown: 996 filtered ports
PORT     STATE  SERVICE VERSION
22/tcp   open   ssh     (protocol 2.0)
| fingerprint-strings: 
|   NULL: 
|_    SSH-2.0-OpenSSH_7.4p1 Ubuntu-10
| ssh-hostkey: 
|   2048 1d:14:84:f0:c7:21:10:0e:30:d9:f9:59:6b:c3:95:97 (RSA)
|_  256 dc:59:c6:6e:33:33:f2:d2:5d:9b:fd:b4:9c:52:c1:0a (ECDSA)
80/tcp   open   http    nginx 1.10.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: nginx/1.10.0 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
443/tcp  closed https
5900/tcp open   vnc     VNC (protocol 3.7)
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port22-TCP:V=7.40%I=7%D=5/15%Time=5918BCAA%P=x86_64-apple-darwin16.3.0%
SF:r(NULL,20,"SSH-2\.0-OpenSSH_7\.4p1\x20Ubuntu-10\n");
MAC Address: F0:1F:AF:1F:2C:60 (Dell)
Device type: general purpose
Running (JUST GUESSING): Linux 3.X|4.X|2.6.X (95%), OpenBSD 4.X (85%)
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:2.6.32 cpe:/o:openbsd:openbsd:4.0
Aggressive OS guesses: Linux 3.11 - 4.1 (95%), Linux 4.4 (95%), Linux 3.13 (92%), Linux 4.0 (90%), Linux 2.6.32 (89%), Linux 2.6.32 or 3.10 (89%), Linux 3.2 - 3.8 (89%), Linux 3.10 - 3.12 (88%), Linux 2.6.32 - 2.6.33 (87%), Linux 2.6.32 - 2.6.35 (87%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.000 days (since Mon May 15 01:53:08 2017)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=252 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.44 ms dellm6700 (192.168.2.15)

NSE: Script Post-scanning.
Initiating NSE at 01:53
Completed NSE at 01:53, 0.00s elapsed
Initiating NSE at 01:53
Completed NSE at 01:53, 0.00s elapsed
Read data files from: /usr/local/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 46.02 seconds
           Raw packets sent: 2075 (95.016KB) | Rcvd: 50 (3.084KB)

#32: Not a fan of command line tools?

Try zenmap the official network mapper front end:

Zenmap is the official Nmap Security Scanner GUI. It is a multi-platform (Linux, Windows, Mac OS X, BSD, etc.) free and open source application which aims to make Nmap easy for beginners to use while providing advanced features for experienced Nmap users. Frequently used scans can be saved as profiles to make them easy to run repeatedly. A command creator allows interactive creation of Nmap command lines. Scan results can be saved and viewed later. Saved scan results can be compared with one another to see how they differ. The results of recent scans are stored in a searchable database.
You can install zenmap using the following apt-get command:
$ sudo apt-get install zenmap



