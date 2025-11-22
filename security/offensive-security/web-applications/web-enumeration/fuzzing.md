# Fuzzing

```shellscript
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://IP:PORT/FUZZ
```

{% code title="Fuzz for files within a directory" %}
```shellscript
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u http://IP:PORT/directory/FUZZ -e .php,.bak -v -fc 404,403
```
{% endcode %}
