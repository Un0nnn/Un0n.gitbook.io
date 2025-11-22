---
description: >-
  Enables wireless interface to capture all 802.11 frames within range, not just
  those addressed to it (unlike managed mode). Provides full visibility of
  wireless traffic & supporting packet analysis.
---

# Airmon-ng

{% code title="Monitor Mode" %}
```shellscript
sudo airmon-ng start wlan0 11 # Specific Channel
```
{% endcode %}

{% code title="Check Interfering Processes" %}
```shellscript
sudo airmon-ng check
```
{% endcode %}

{% code title="Kill Interfering Processes (If encountering problems)" %}
```shellscript
sudo airmon-ng check kill
```
{% endcode %}
