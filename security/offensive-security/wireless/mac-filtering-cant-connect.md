# MAC Filtering (Can't Connect)

Using the same MAC can cause collisions, as two devices with identical MACs can’t coexist on one network. Better approaches is to **Deauth the legitimate client** to free the MAC, or wait for it to disconnect. Works well in BYOD networks with frequent connections/disconnections.

MAC collisions can sometimes be exploited for **DoS attacks**. In dual-band or multi-AP setups, using a client’s MAC on a different AP or switching to **5 GHz** (if available) can avoid collisions, as most clients use 2.4 GHz.

\# Stop monitor mode

Copy

```
sudo airmon-ng stop wlan0mon
```

\# Check current MAC

Copy

```
sudo macchanger wlan0
```

\# Disable interface

Copy

```
sudo ifconfig wlan0 down
```

\# Change MAC Address

Copy

```
sudo macchanger wlan0 -m 3E:48:72:B7:62:2A
```

\# Enable interface

Copy

```
sudo ifconfig wlan0 up
```

[PreviousInterfaces](interfaces.md) [NextWifi CLI](wifi-cli.md)

Last updated 12 days ago
