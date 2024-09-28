```apt install proxychains```

### Configuring Proxychains
The Proxychains configuration file is located at /etc/proxychains.conf. Edit this file to specify your desired proxy setup:

```nano /etc/proxychains.conf```

  Uncomment the dynamic_chain line:
  
  comment out the strict_chain line:
  
  Add some SOCKS proxies to the list. For example:
  
  ```
    socks5 127.0.0.1 1080
    socks4 1.2.3.4 1080  
    socks5 4.3.2.1 8080
  ```
    
Save the file after adding proxies.

### Testing Proxychains
Before pairing with Nmap, test that proxychains is working correctly:
>proxychains firefox
>Browse to a site like https://www.iplocation.net/ to check your origin IP address.
>The IP should match one of your proxy servers rather than your local system‘s real IP.

### Using Nmap with Proxychains
```proxychains nmap [target] [options]```
However, there are some limitations to be aware of:
    >ICMP/UDP scans do not work. Stick to TCP connect scans.
    >DNS resolution may not work properly. Specify targets by IP rather than name.
    >Banner grabbing and OS detection do not work with proxychains.

With those limitations in mind, let‘s walk through some examples.

***First, a basic TCP port scan:***
  ```proxychains nmap -Pn -sT 192.168.1.105```
    The -Pn skips ping discovery, and -sT specifies a TCP connect scan.

***Scanning specific ports:***
  ```proxychains nmap -Pn -sT -p22,80,443 192.168.1.105 ```

***More comprehensive TCP scan:***
  ```proxychains nmap -Pn -sT --top-ports 100 192.168.1.105```
    This scans the top 100 most common TCP ports.

Adjust the port list and target IP address as desired. Always use IP addresses rather than hostnames for best results with proxychains.

#More Advanced Scanning with Nmap and Proxychains
Many other Nmap scan types work through proxychains, though performance may be slower than normal.
For example, version detection:
```proxychains nmap -Pn -sV -p 22,80 192.168.1.105```
Or a full TCP port scan:
```proxychains nmap -Pn -p- 192.168.1.105```


