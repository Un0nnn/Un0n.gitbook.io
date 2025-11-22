---
description: >-
  Decrypts & strips Wi-Fi headers to make packet contents readable (wireshark).
  Removes wireless headers from unencrypted captures, Decrypt WEP with hex WEP
  key. Decrypt WPA/WPA2 (PSK) using passphrase.
---

# Airdecap-ng

{% code title="Remove Wireless Headers from Unencrypted Captures" %}
```shellscript
sudo airdecap-ng -b 00:D3:F5:7C:34:46 capture.cap
```
{% endcode %}

{% code title="Decrypting WEP-encrypted captures" %}
```shellscript
sudo airdecap-ng -w 732483BC97393 OUTPUT-01.cap
```
{% endcode %}

{% code title="Decrypting WPA-encrypted captures" %}
```shellscript
sudo airdecap-ng -p 'password' OUTPUT-01.cap -e "APName"
```
{% endcode %}

These commands for specific protocols will decrypt and allow for easy data analysis from outputted `-dec.cap` files.
