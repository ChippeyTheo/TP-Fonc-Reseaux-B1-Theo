# TP1 - Premier pas réseau

## 1. Affichage d'informations sur la pile TCP/IP locale

**🌞 Affichez les infos des cartes réseau de votre PC**

```
theo@MacBook-Pro-de-chippey ~ % ifconfig

en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	options=400<CHANNEL_IO>
	ether 88:e9:fe:75:94:10     XXX
	inet6 fe80::4e:6f62:f43f:d284%en0 prefixlen 64 secured scopeid 0x4 
	inet 10.33.48.133   XXX netmask 0xfffffc00 broadcast 10.33.51.255
	nd6 options=201<PERFORMNUD,DAD>
	media: autoselect
	status: active
```

**🌞 Affichez votre gateway**

```
theo@MacBook-Pro-de-chippey ~ % route -n get default
   route to: default
destination: default
       mask: default
    gateway: 10.33.51.254       XXX
  interface: en0
      flags: <UP,GATEWAY,DONE,STATIC,PRCLONING,GLOBAL>
 recvpipe  sendpipe  ssthresh  rtt,msec    rttvar  hopcount      mtu     expire
       0         0         0         0         0         0      1500         0 
```

**🌞 Déterminer la MAC de la passerelle**

```
theo@MacBook-Pro-de-chippey ~ % ifconfig en1 | awk '/ether/{print $2}'
82:6d:86:62:50:01       XXX
```

## 2. Modifications des informations

### A. Modification d'adresse IP (part 1)

**🌞 Utilisez l'interface graphique de votre OS pour changer d'adresse IP :**

```
theo@MacBook-Pro-de-chippey ~ % ifconfig
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	options=400<CHANNEL_IO>
	ether 88:e9:fe:75:94:10 
	inet6 fe80::4e:6f62:f43f:d284%en0 prefixlen 64 secured scopeid 0x4 
	inet 10.33.48.100   XXX netmask 0xfffffc00 broadcast 10.33.51.255
	nd6 options=201<PERFORMNUD,DAD>
	media: autoselect
	status: active
```


