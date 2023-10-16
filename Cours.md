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