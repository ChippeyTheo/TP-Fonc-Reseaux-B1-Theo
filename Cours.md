**en0 :** ma carte reseaux

* ether : adresse mac
* inet : mon adresse IP 

**adresse mac :**

* grave sur la carte reseaux 
* hexadecimal : caractere de 0-9 et de "a,b,c,d,e,f"
* 4 premier caractere son acheter par le constructeur pour creer des cartes reseaux uniques
* 16^12 adresse possible 
* sert a communiquer dans un LAN

**adresse IP :**
 
 * que si on est co a une LAN
 * forme X.X.X.X --> X de 0 a 255
 * netmask : masque (de sous reseaux) (peut etre note /XX apres adresse IP)
 * masque equivaut au nom de la rue d'une adresse et IP le numero dans la rue 

 **binaire :**
 * 1 --> 0
 * 2 --> 0
 * 4 --> 0
 * 8 --> 0
 * 16 --> 0
 * 32 --> 1
 * 64 --> 1
 * 128 --> 0

 01100000 == 96 en binaire


netmask en binaire = 
11111111.11111111.11111100.00000000

adresse IP en binaire = 
00001010.00100001.00110000.10000101

adresse reseaux = 
00001010.00100001.00110000.00000000

sipcalc pour trouver adresse reseaux mais pas encore installer 

IP, DNS, paserelles = internet

192 168 17 221 / 18
11000000 10101000 00010001 11011101 

255 255 192 0
11111111 11111111 11000000 00000000

192 168 0 0
11000000 10101000 00000000 00000000

192 168 63 255
11000000 10101000 00111111 11111111

192 168 0 1
192 168 63 254

255 * 2 + 62 * 256
510 + 15872
16382
ou 2^14 -2 ( max: 32 - 18 :le mask)

172 18 31 102 / 30
1O101100 00010010 00011111 011OO11O

255 255 255 252
11111111 11111111 11111111 11111100

172 18 31 100
10101100 00010010 00011111 01100100

172 18 31 103
10101100 00010010 00011111
01100111

2^2 -2 = 2
