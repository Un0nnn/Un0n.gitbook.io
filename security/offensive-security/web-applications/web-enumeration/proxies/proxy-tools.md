---
description: >-
  To route a tool’s traffic through a web proxy, set the tool’s proxy to
  something like http://127.0.0.1:8080, just as you would with a browser. Each
  tool handles proxy configuration differently.
---

# Proxy Tools

#### **Proxychains**

Proxychains forces ANY command-line program to route its traffic through a specified proxy.

{% code title="/etc/proxychains.conf" %}
```bash
#socks4         127.0.0.1 8080
http 127.0.0.1 8080 # Add this lines
```
{% endcode %}

```shellscript
proxychains -q curl http://SERVER_IP:PORT # Will be intercepted in Burp
```

#### **Metasploit**

```shellscript
msf6 auxiliary() > set PROXIES HTTP:127.0.0.1:8080 # Will be intercepted in Burp
```

