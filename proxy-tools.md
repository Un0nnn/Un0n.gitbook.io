# Proxy Tools

[**Direct link to heading**](proxy-tools.md#proxychains) **Proxychains**

Proxychains forces ANY command-line program to route its traffic through a specified proxy.

/etc/proxychains.conf

Copy

```
#socks4         127.0.0.1 8080
http 127.0.0.1 8080 # Add this lines
```

Copy

```
proxychains -q curl http://SERVER_IP:PORT # Will be intercepted in Burp
```

[**Direct link to heading**](proxy-tools.md#metasploit) **Metasploit**

Copy

```
msf6 auxiliary() > set PROXIES HTTP:127.0.0.1:8080 # Will be intercepted in Burp
```

[PreviousBurp Suite](burp-suite.md) [NextZAP](security/offensive-security/web-applications/web-enumeration/proxies/zap.md)

Last updated 6 days ago
