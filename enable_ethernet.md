Ubuntu Server - enable ethernet

1) Determine which logical name your eth port is called
```
ifconfig -a
```
2) Determine factory info about Ethernet Hardware
```
lspci -nnk | grep -iA2 eth

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
Subsystem: Giga-byte Technology Device [1458:e000]
Kernel driver in use: atl1c
```
3) Determine hardware information
```
sudo lshw -C network

*-network DISABLED
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@000:02:00.0
logical name: eth0
version: c0
serial: 50:e5:49:d0:9e:9e
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:18 memory:fddc000-fddfffff ioport:df00(size=128)
```

4) If Ethernet is disabled: enable Ethernet
```
sudo ifconfig eth0 up
```

5) Restart networking
```
sudo service networking restart
```
6) Check if hardware included in interfaces file
```
cat /etc/network/interfaces

# The loopback network interface
# auto lo
# iface lo inet loopback
```

7) If not there: add it
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

https://ubuntuforums.org/showthread.php?t=2034067
