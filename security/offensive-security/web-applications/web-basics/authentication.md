# Authentication

{% code title="Basic Auth (GET)" %}
```shellscript
curl -u user:password http://<SERVER_IP>:<PORT>/
curl http://user:password@<SERVER_IP>:<PORT>/ # Alternative to above
curl -H 'Authorization: Basic uWiue76NhysNBgsid...=' http://<SERVER_IP>:<PORT>/ # Without credentials
```
{% endcode %}

{% code title="Basic Auth (POST)" %}
```shellscript
curl -X POST -L -d 'username=user&password=password' http://<SERVER_IP>:<PORT>/ -i
curl -d '{"data":"new-data"} '-b 'PHPSESSID=al8r3kppr0...' -H 'Content-Type: application/json' http://<SERVER_IP>:<PORT>/ # Without credentials
```
{% endcode %}
