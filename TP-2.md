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

🦈 [ping-pong](https://github.com/ChippeyTheo/TP-Fonc-Reseaux-B1-Theo/blob/main/pong-ping.pcapng)

## II. ARP my bro

**🌞 Check the ARP table**

```
theo@MacBook-Pro-de-chippey ~ % arp -a
? (10.33.51.254) at 7c:5a:1c:cb:fd:a4 on en0 ifscope [ethernet]
? (169.254.78.45) at b0:68:e6:bc:ef:e3 on en0 [ethernet]
? (192.168.123.2) at 8:0:27:ae:a5:3e    XXX on bridge100 ifscope [bridge]
mdns.mcast.net (224.0.0.251) at 1:0:5e:0:0:fb on en0 ifscope permanent [ethernet]

```

manque la gateway

**🌞 Manipuler la table ARP**

* vider votre table ARP

```
theo@MacBook-Pro-de-chippey ~ % sudo arp -a -d
Password:
10.33.51.254 (10.33.51.254) deleted
169.254.78.45 (169.254.78.45) deleted
224.0.0.251 (224.0.0.251) deleted
theo@MacBook-Pro-de-chippey ~ % arp -a
? (10.33.51.254) at 7c:5a:1c:cb:fd:a4 on en0 ifscope [ethernet]
```
* ré-apparition des données dans la table ARP

```
theo@MacBook-Pro-de-chippey ~ % arp -a
? (10.33.51.254) at 7c:5a:1c:cb:fd:a4 on en0 ifscope [ethernet]
? (192.168.123.2) at 8:0:27:ae:a5:3e on bridge100 ifscope [bridge]
```

**🌞 Wireshark it**

🦈 [ARP](https://github.com/ChippeyTheo/TP-Fonc-Reseaux-B1-Theo/blob/main/arp.pcapng)

1. Ligne 1 : requete de mon Terminal à ma VM. 
* `source : 8a:e9:fe:57:59:64`, c'est l'adresse MAC de mon Terminal.
* `destination : broadcast`, il ne connait pas encore l'adresse MAC de ma VM, le switch envoie des requetes pour savoir à qui appartient l'IP 192.168.123.2 et renvoyer l'adresse MAC associer. 

2. Ligne 2 : réponse de ma VM.
* `source : PcsCompu_ae:a5:3e`, adresse MAC de ma VM(PcsCompu = nom du constructeur)
* `destination : 8a:e9:fe:57:59:64`, renvoie l'adresse MAC de ma VM à mon Terminal

## III. DHCP

**🌞 Wireshark it**
