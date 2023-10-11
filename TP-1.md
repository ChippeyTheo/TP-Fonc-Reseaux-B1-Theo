# TP1 - Premier pas réseau

## I. Exploration locale en solo

### 1. Affichage d'informations sur la pile TCP/IP locale

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

### 2. Modifications des informations

#### A. Modification d'adresse IP (part 1)

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

## II. Exploration locale en duo


## III. Manipulations d'autres outils/protocoles côté client

### 1. DHCP

**🌞Exploration du DHCP, depuis votre PC**

* Adresse IP du serveur DHCP du réseau WiFi YNOV

```
theo@MacBook-Pro-de-chippey ~ % ipconfig getpacket en0
op = BOOTREPLY
htype = 1
flags = 0
hlen = 6
hops = 0
xid = 0xd2a82548
secs = 2
ciaddr = 0.0.0.0
yiaddr = 10.33.48.133
siaddr = 0.0.0.0
giaddr = 0.0.0.0
chaddr = 88:e9:fe:75:94:10
sname = 
file = 
options:
Options count is 7
dhcp_message_type (uint8): ACK 0x5
server_identifier (ip): 10.33.51.254        XXX
lease_time (uint32): 0x15180
subnet_mask (ip): 255.255.252.0
router (ip_mult): {10.33.51.254}
domain_name_server (ip_mult): {10.33.10.2, 8.8.8.8}
end (none):
```

* Date d'expiration de votre bail DHCP(fait avec ma 4g refaire avec wifi ynov)

```
theo@MacBook-Pro-de-chippey ~ % sudo su 
sh-3.2# cat /var/db/dhcpclient/leases/*
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>IPAddress</key>
	<string>192.168.1.15</string>
	<key>LeaseLength</key>
	<integer>86400</integer>        XXX
	<key>LeaseStartDate</key>
	<date>2022-06-08T14:16:12Z</date>
	<key>PacketData</key>
	<data>
	AgEGAIQrZdMAAAAAwKgBD8CoAQ/AqAEBAAAAAIjp/nWUEAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABjglNjNQEFNgTAqAEBMwQAAVGA
	OgQAAKjAOwQAASdQAQT///8ABgTAqAEBDwRob21lAwTAqAEBfS0AAA3pKAQGMzA5M0JD
	BQ9MSzIwMDAyRFA5OTUwODkGDUxpdmVib3ggRmlicmX/
	</data>
	<key>RouterHardwareAddress</key>
	<data>
	MJO8nUiQ
	</data>
	<key>RouterIPAddress</key>
	<string>192.168.1.1</string>
	<key>SSID</key>
	<string>Livebox-4890</string>
</dict>
</plist>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>ClientIdentifier</key>
	<data>
	AYjp/nWUEA==
	</data>
	<key>IPAddress</key>
	<string>172.20.10.2</string>
	<key>LeaseLength</key>
	<integer>86400</integer>
	<key>LeaseStartDate</key>
	<date>2023-10-11T16:08:08Z</date>
	<key>PacketData</key>
	<data>
	AgEGANKoJUoAAAAAAAAAAKwUCgKsFAoBAAAAAIjp/nWUEAAAAAAAAAAAAABpUGhvbmUA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABjglNjNQEFNgSsFAoBMwQAAVGA
	AQT////wAwSsFAoBBgSsFAoB/wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
	</data>
	<key>RouterHardwareAddress</key>
	<data>
	CscpxIhk
	</data>
	<key>RouterIPAddress</key>
	<string>172.20.10.1</string>
	<key>SSID</key>
	<string>iPhone</string>
</dict>
</plist>
```