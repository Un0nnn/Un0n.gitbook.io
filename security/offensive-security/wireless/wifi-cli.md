---
description: Covers interacting with wireless connections in the CLI.
---

# Wifi CLI

Use `wpa_supplicant` with a config file (network SSID/passphrase) to authenticate and join.

Normally switch the interface to **monitor** for scanning; if monitor isn't available, use **managed** mode and `iwlist` (with `grep`) to list useful info: Cell, Signal, ESSID, and IEEE.

{% code title="" %}
```shellscript
sudo iwlist wlan0 s | grep 'Cell\|Quality\|ESSID\|IEEE'
```
{% endcode %}

#### **Connecting to WEP**

Provide SSID, WEP hex key, and key index (`wep_tx_keyidx`) in a config file (e.g., `wep.conf`). Set `key_mgmt=NONE` for WEP or open networks.

```shellscript
network={
	ssid="APName"
    key_mgmt=NONE
    wep_key0=8759JC84C9
    wep_tx_keyidx=0
}
```

```shellscript
sudo wpa_supplicant -c wep.conf -i wlan0
```

Run `dhclient` to get an IP from the network’s DHCP server, completing the setup.

```shellscript
sudo dhclient wlan0
```

#### **Connecting to WPA Personal Networks**

```shellscript
network={
	ssid="APName"
    psk="password"
}
```

```shellscript
sudo wpa_supplicant -c wpa.conf -i wlan0
```

Use `dhclient` to get an IP from the network’s DHCP server. If a previous DHCP IP exists, release it first using:

```shellscript
sudo dhclient wlan0 -r
sudo dhclient wlan0
```

For WPA3 networks, add `key_mgmt=SAE` in the wpa\_supplicant config to use the SAE protocol required by WPA3.

#### **Connecting to WPA Enterprise**

```shellscript
network={
  ssid="APName"
  key_mgmt=WPA-EAP
  identity="DOMAIN\Administrator"
  password="password"
}
```

```shellscript
sudo wpa_supplicant -c wpa_enterprsie.conf -i wlan0
sudo dhclient wlan0 -r
sudo dhclient wlan0
```

Another way to connect all protocols via CLI is:

```shellscript
sudo nmtui
```
