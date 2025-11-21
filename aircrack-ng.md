# Aircrack-ng

\# Benchmark to assess CPU performance for cracking

Copy

```
aircrack-ng -S
```

\# Cracking WEP

Copy

```
aircrack-ng -K OUTPUT.ivs
```

Above command recovers WEP keys once enough IVs are captured. Use `airodump-ng --ivs` to save only IVs, then run `aircrack-ng -K` to apply the Korek WEP-cracking method.

\# Cracking WPA

Copy

```
aircrack-ng OUTPUT.pcap -w passwords.txt
```

Cracks WPA/WPA2-PSK from a captured four-way handshake (capture with airodump-ng).

* Cracking uses a dictionary/wordlist (offline).
* A full handshake is 4 EAPOL packets, but Aircrack-ng can work with just packets 2+3 or 3+4.

[PreviousTools](security/offensive-security/wireless/tools/) [NextAirdecap-ng](airdecap-ng.md)

Last updated 12 days ago
