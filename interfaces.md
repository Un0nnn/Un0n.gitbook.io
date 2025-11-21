# Interfaces

\# Check interface strength

Copy

```
iwconfig
iw reg get
```

\# Change interface region (Abide by pertinent rules and laws when changing)

Copy

```
sudo iw reg set US
```

\# Change interface power settings

Copy

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 txpower 40
sudo ifconfig wlan0 up
```

\# Check interface capabilities

Copy

```
iw list
```

\# Change interface channel

Copy

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 channel 64
sudo ifconfig wlan0 up
iwlist wlan0 channel
```

\# Change interface frequency

Copy

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 freq "5.52G"
sudo ifconfig wlan0 up
```

\# Check frequency

Copy

```
iwlist wlan0 frequency | grep Current
```

\# Change mode to managed

Copy

```
sudo iwconfig wlan0 mode managed
```

\# Broadcast a network on master mode

Copy

```
interface=wlan0
driver=65782yn
ssid=APName
channel=7
hw_mode=g

sudo hostapd open.conf
```

\# Change interface to mesh mode

Copy

```
sudo iw dev wlan0 set type mesh
```

\# Change interface to monitor mode (First disable interface)

Copy

```
sudo iw wlan0 set monitor control
```

[**Direct link to heading**](interfaces.md#wi-fi-attack-modes-and-interface-requirements) **Wi-Fi Attack Modes and Interface Requirements**

1. **Rogue AP / Evil-Twin Attack**

* Requires **master/AP mode** support.
* Tools/daemons: `hostapd`, `hostapd-mana`, `hostapd-wpe`, `airbase-ng`.
* Purpose: Set up a fake access point to trick clients into connecting.

2. **Backhaul / Mesh Exploitation**

* Requires **ad-hoc or mesh mode** support.
* Basic monitoring: **monitor mode + packet injection** is often enough.
* Advanced: Allows **node impersonation** and other mesh/network-level attacks.

[PreviousHidden SSIDs](hidden-ssids.md) [NextMAC Filtering (Can't Connect)](security/offensive-security/wireless/mac-filtering-cant-connect.md)

Last updated 12 days ago
