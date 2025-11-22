---
description: >-
  Captures raw 802.11 frames — used to collect WEP IVs and WPA/WPA2 handshakes
  for use with aircrack-ng. Produces several output files (APs, clients,
  packets) containing detailed network info — useful
---

# Airodump-ng

{% code title="To use Airodump-ng" %}
```shellscript
sudo airmon-ng start wlan0s
```
{% endcode %}

{% code title="Scan APs & Clients" %}
```shellscript
sudo airodump-ng -c 11 wlan0mon --band abg -w WriteToFile...
```
{% endcode %}

