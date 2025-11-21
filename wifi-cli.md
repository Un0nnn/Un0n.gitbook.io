# Wifi CLI

Use `wpa_supplicant` with a config file (network SSID/passphrase) to authenticate and join.

Normally switch the interface to **monitor** for scanning; if monitor isn't available, use **managed** mode and `iwlist` (with `grep`) to list useful info: Cell, Signal, ESSID, and IEEE.

\# Display network information around you

Copy

```
sudo iwlist wlan0 s | grep 'Cell\|Quality\|ESSID\|IEEE'
```

[**Direct link to heading**](wifi-cli.md#connecting-to-wep) **Connecting to WEP**

Provide SSID, WEP hex key, and key index (`wep_tx_keyidx`) in a config file (e.g., `wep.conf`). Set `key_mgmt=NONE` for WEP or open networks.

Copy

```
network={
	ssid="APName"
    key_mgmt=NONE
    wep_key0=8759JC84C9
    wep_tx_keyidx=0
}
```

Copy

```
sudo wpa_supplicant -c wep.conf -i wlan0
```

Run `dhclient` to get an IP from the network’s DHCP server, completing the setup.

Copy

```
sudo dhclient wlan0
```

[**Direct link to heading**](wifi-cli.md#connecting-to-wpa-personal-networks) **Connecting to WPA Personal Networks**

Copy

```
network={
	ssid="APName"
    psk="password"
}
```

Copy

```
sudo wpa_supplicant -c wpa.conf -i wlan0
```

Use `dhclient` to get an IP from the network’s DHCP server. If a previous DHCP IP exists, release it first using:

Copy

```
sudo dhclient wlan0 -r
sudo dhclient wlan0
```

For WPA3 networks, add `key_mgmt=SAE` in the wpa\_supplicant config to use the SAE protocol required by WPA3.

[**Direct link to heading**](wifi-cli.md#connecting-to-wpa-enterprise) **Connecting to WPA Enterprise**

Copy

```
network={
  ssid="APName"
  key_mgmt=WPA-EAP
  identity="DOMAIN\Administrator"
  password="password"
}
```

Copy

```
sudo wpa_supplicant -c wpa_enterprsie.conf -i wlan0
sudo dhclient wlan0 -r
sudo dhclient wlan0
```

Another way to connect all protocols via CLI is:

Copy

```
sudo nmtui
```

[PreviousMAC Filtering (Can't Connect)](security/offensive-security/wireless/mac-filtering-cant-connect.md) [NextTools](security/offensive-security/wireless/tools/)

Last updated 12 days ago
