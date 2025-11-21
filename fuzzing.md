# Fuzzing

Copy

```
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://IP:PORT/FUZZ
```

Fuzz for files within a directory

Copy

```
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u http://IP:PORT/directory/FUZZ -e .php,.bak -v -fc 404,403
```

[PreviousWeb Enumeration](security/offensive-security/web-applications/web-enumeration/) [NextProxies](security/offensive-security/web-applications/web-enumeration/proxies/)

Last updated 8 days ago
