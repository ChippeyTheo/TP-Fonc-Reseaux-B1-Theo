# TP-2 : Ethernet, IP, et ARP

## I. Setup IP

**🌞 Mettez en place une configuration réseau fonctionnelle entre les deux machines**

```
theo@MacBook-Pro-de-chippey ~ % ifconfig
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	options=400<CHANNEL_IO>
	ether 88:e9:fe:75:94:10 
	inet6 fe80::4e:6f62:f43f:d284%en0 prefixlen 64 secured scopeid 0x4 
	inet 10.33.48.133   XXX netmask 0xfffffc00    XXX broadcast 10.33.51.255    XXX
	nd6 options=201<PERFORMNUD,DAD>
	media: autoselect
	status: active
```

* CALCUL

```
adresse IP de la VM = 192.168.123.2
adresse réseaux = 192.168.123.0

0xffffff00
11111111.11111111.11111111.00000000

192.168.123.1
11000000.10101000.01111011.00000001

192.168.123.0
11000000.10101000.01111011.00000000
```

**🌞 Prouvez que la connexion est fonctionnelle entre les deux machines**

```
theo@MacBook-Pro-de-chippey ~ % ping 192.168.123.2
PING 192.168.123.2 (192.168.123.2): 56 data bytes
64 bytes from 192.168.123.2: icmp_seq=0 ttl=64 time=0.980 ms
64 bytes from 192.168.123.2: icmp_seq=1 ttl=64 time=0.762 ms
64 bytes from 192.168.123.2: icmp_seq=2 ttl=64 time=0.728 ms
^C
--- 192.168.123.2 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.728/0.823/0.980/0.112 ms
```

**🌞 Wireshark it**

* [ping-pong](https://github.com/ChippeyTheo/TP-Fonc-Reseaux-B1-Theo/blob/main/ping-pong.pcapng)