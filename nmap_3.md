#                                                                 Scanning Type


** nmap 172.217.31.206 -sS  --> Tcp SYN port scan(Default)
** nmap 172.217.31.206 -sT  --> Tcp connected port
** nmap 172.217.31.206 -sA  --> Tcp ACK port
** nmap 172.217.31.206 -sU  --> Udp port scan
** nmap 172.217.31.206 -sX  --> Xmas scan
** nmap 172.217.31.206 -sP  --> Ping scan



#                                                                Version Detection


** nmap 172.217.31.206 -sV  --> Basic CM for finding the version of the service

** nmap 172.217.31.206 -sV --version-intensity 6  --> intensity level 0-9

** nmap 172.217.31.206 -A  --> A means aggressive.It's find os detection, version detection, script scanning, and traceroute. But it creates much noise for that your sending request may be caught by the firewall if they have

** nmap 172.217.31.206 -O  --> Remote os detection

 #                                                               Port Specification 


** nmap 172.217.31.206 -p 23   --> For specific port

** nmap 172.217.31.206 -p 23-100  --> For specific port to specefic port range

** nmap 172.217.31.206 -pU:110,T:23-25 --> U(UDP),T(TCP) Scan together different types of ports

** nmap 172.217.31.206 -p-   --> Scan all ports means 65535 ports(default scan 1000 ports).This thinks also makes much noise. But the interesting thing is sometimes some clever admin hide important info on some odd port

** nmap 172.217.31.206 -smtp,https  --> Scan for specific protocols



#                                                                    Time Options

** nmap 172.217.31.206 -T0  --> Slow scan
** nmap 172.217.31.206 -T1  --> little fast 
** nmap 172.217.31.206 -T2  --> Timely scan
** nmap 172.217.31.206 -T3  --> Aggressive scan
** nmap 172.217.31.206 -T4  --> Very aggressive scan


#                                                              Scripts (Best part on Nmap)

 
** nmap 172.217.31.206 --scripts vulners    --> vulners script name find on github https://github.com/vulnersCom/nmap-vulners

** nmap 172.217.31.206 --script vulners,ftp-anon  --> Comma for  multiple scripting adding

** nmap 172.217.31.206 -p 21 --script "ftp-*"  --> For using all ftp script.On ftp you can add http/smb ect

** nmap 172.217.31.206 -sV -sC  --> Scan using default scripts

** nmap --script-help http-waf-detect.nse  --> Get help for any script 
                                                                         
## Type this ls -al /usr/share/nmap/scripts/ on your terminal to see nmap defult scripts.
## Also many scripts are available on github
## For better performance you should update your nmap scripts DB for this CM is  nmap --script-updatedb 


#                                                                     Firewall Bypass


** nmap 172.217.31.206 -f   --> To send your request by fragment packets. It sends your request as a very small packets that's why the Firewall/IDS(institution detection system) can't detect it.
# Note: This method doesn't work every time because nowadays many Fire/IDS are capable to detect them.

** nmap 172.217.31.206 -A -T1  --> Use T1 for tricky scan to avoid IDS/Firewall

** nmap 172.217.31.206 -sS -sV -D RND:3  --> D(decoys), RND:3(random) 3 ip which is auto selected by nmap
  


#                                                                     Some Other Command

** nmap 172.217.31.206 -A -T4  --> T4 for make aggressive scan faster
** nmap 172.217.31.206 -sV -sS -vv  --> vv for verbose output/in details
** nmap 172.217.31.206 -A -F   --> F is also use for fast scan but it only scan most common 100 ports
** nmap 172.217.31.206 -A | tee /root/Desktop/nmaptestresult.txt  --> Use tee for easy output

=============================================================================================

# Nmap-Cheat-Sheet

- Nmap Target Selection

```bash
Scan a single IP	               nmap 192.168.1.1
Scan a host	                     nmap www.testhostname.com
Scan a range of IPs	             nmap 192.168.1.1-20
Scan a subnet	                   nmap 192.168.1.0/24
Scan targets from a text file	   nmap -iL list-of-ips.txt
```

- Nmap Port Selection

```bash
Scan a single Port	                    nmap -p 22 192.168.1.1
Scan a range of ports                   nmap -p 1-100 192.168.1.1
Scan 100 most common ports (Fast)	      nmap -F 192.168.1.1
Scan all 65535 ports	                  nmap -p- 192.168.1.1
```
- Nmap Port Scan types

```bash
Scan using TCP connect	                  nmap -sT 192.168.1.1
Scan using TCP SYN scan (default)	        nmap -sS 192.168.1.1
Scan UDP ports	                          nmap -sU -p 123,161,162 192.168.1.1
Scan selected ports - ignore discovery	  nmap -Pn -F 192.168.1.1
```

- Service and OS Detection

```bash
Detect OS and Services	           nmap -A 192.168.1.1
Standard service detection	       nmap -sV 192.168.1.1
More aggressive Service Detection	 nmap -sV --version-intensity 5 192.168.1.1
Lighter banner grabbing detection	 nmap -sV --version-intensity 0 192.168.1.1
```

- Nmap Output Formats

```bash
Save default output to file	       nmap -oN outputfile.txt 192.168.1.1
Save results as XML	               nmap -oX outputfile.xml 192.168.1.1
Save results in a format for grep	 nmap -oG outputfile.txt 192.168.1.1
Save in all formats	               nmap -oA outputfile 192.168.1.1
```

- Digging deeper with NSE Scripts

```bash
Scan using default safe scripts	   nmap -sV -sC 192.168.1.1
Get help for a script	             nmap --script-help=ssl-heartbleed
Scan using a specific NSE script	 nmap -sV -p 443 –script=ssl-heartbleed.nse 192.168.1.1
Scan with a set of scripts	       nmap -sV --script=smb* 192.168.1.1
```

- A scan to search for DDOS reflection UDP services

```bash
Scan for UDP DDOS reflectors	    nmap –sU –A –PN –n –pU:19,53,123,161 –script=ntp-monlist,dns-recursion,snmp-sysdescr 192.168.1.0/24
```


- HTTP Service Information

```bash
Gather page titles from HTTP services	   nmap --script=http-title 192.168.1.0/24
Get HTTP headers of web services	       nmap --script=http-headers 192.168.1.0/24
Find web apps from known paths	         nmap --script=http-enum 192.168.1.0/24
```

- Detect Heartbleed SSL Vulnerability

```bash
Heartbleed Testing	      nmap -sV -p 443 --script=ssl-heartbleed 192.168.1.0/24
```

- IP Address information

```bash
Find Information about IP address	nmap --script=asn-query,whois,ip-geolocation-maxmind 192.168.1.0/24
```

- Scan port services from 1 to 65535

```bash
nmap -sV -p 1-65535 192.168.1.1/24
```

- All ports, all service versions, simple scripts = just the open

```bash
nmap -p- -sV -sC $IP --open
```
