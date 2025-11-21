# Hidden SSIDs

\# Set interface to Monitor

Copy

```
sudo airmon-ng start wlan0
```

[Airodump-ng](tools/airodump-ng.md) will show hidden SSIDs; `<length: x>` indicates the SSID length.

To reveal hidden SSIDs:

* If clients are connected, use [**aireplay-ng**](tools/aireplay-ng.md) to deauth them. When they reconnect, **airodump-ng** captures (will show) the SSID.
* WPA3 networks resist deauth attacks due to 802.11w (PMF); brute-force attacks may be needed instead.

[**Direct link to heading**](hidden-ssids.md#detecting-hidden-ssid-using-deauth) **Detecting Hidden SSID using Deauth**

Copy

```
sudo aireplay-ng -0 10 -a F5:D2:00:AF:69:67 -c D5:00:B2:AF:23:24 wlan0mon
```

[**Direct link to heading**](hidden-ssids.md#bruteforcing-hidden-ssid) **Bruteforcing Hidden SSID**

Copy

```
sudo mdk3 wlan0mon p -b u -c 1 -t A2:FF:31:2C:B1:C4
```

[**Direct link to heading**](hidden-ssids.md#bruteforcing-using-a-wordlist) **Bruteforcing using a Wordlist**

Copy

```
sudo mdk3 wlan0mon p -f passwords.txt -t A2:FF:31:2C:B1:C4
```

[Previous802.11 & Auth](802.11-and-auth.md) [NextInterfaces](interfaces.md)

Last updated 12 days ago
