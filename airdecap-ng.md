# Airdecap-ng

\# Remove Wireless Headers from Unencrypted Captures

Copy

```
sudo airdecap-ng -b 00:D3:F5:7C:34:46 capture.cap
```

\# Decrypting WEP-encrypted captures

Copy

```
sudo airdecap-ng -w 732483BC97393 OUTPUT-01.cap
```

\# Decrypting WPA-encrypted captures

Copy

```
sudo airdecap-ng -p 'password' OUTPUT-01.cap -e "APName"
```

These commands for specific protocols will decrypt and allow for easy data analysis from outputted `-dec.cap` files.

[PreviousAircrack-ng](aircrack-ng.md) [NextAireplay-ng](security/offensive-security/wireless/tools/aireplay-ng.md)

Last updated 12 days ago
