---
description: >-
  Offline cracking tool that uses captured packets to crack WEP and WPA/WPA2
  (PSK and PMKID); no live interaction with the Wi-Fi device required.
---

# Aircrack-ng

{% code title="Benchmark to assess CPU performance for cracking" %}
```shellscript
aircrack-ng -S
```
{% endcode %}

{% code title="Cracking WEP" %}
```shellscript
aircrack-ng -K OUTPUT.ivs
```
{% endcode %}

Above command recovers WEP keys once enough IVs are captured. Use `airodump-ng --ivs` to save only IVs, then run `aircrack-ng -K` to apply the Korek WEP-cracking method.

{% code title="Cracking WPA" %}
```shellscript
aircrack-ng OUTPUT.pcap -w passwords.txt
```
{% endcode %}

Cracks WPA/WPA2-PSK from a captured four-way handshake (capture with airodump-ng).

* Cracking uses a dictionary/wordlist (offline).
* A full handshake is 4 EAPOL packets, but Aircrack-ng can work with just packets 2+3 or 3+4.

