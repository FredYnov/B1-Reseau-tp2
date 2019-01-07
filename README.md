**B1 Réseau 2018 - TP2**
===

# **Partie 1 - Exploration locale en solo**

Nom, adresse MAC et adresse IP de l'interface Wifi:

**IFCONFIG** sous Mac Os:

![](https://i.imgur.com/wqEmFeD.png)

Nom: en0
Adresse MAC: 88:e9:fe:7e:4d:2a
Adresse IP: 10.33.2.18/22

Nom, adresse MAC et adresse IP de l'interface Ethernet:

Pas de Port Ethernet

**Pour le réseau WIFI:**

**Adresse Réseau:** Adresse IP = 10.33.2.18/22 en binaire = 00001010.00100001.00000010.00010010

**Masque:** 255.255.252.0 en binaire = 11111111.11111111.11111100.00000000

L'adresse de réseau est donc **00001010.00100001.00000000.00000000**

**Adresse Broadcast:** 10.33.3.255

**Affichez votre Gateway:**

Pour déterminer la Gateway, j'ai fait un **traceroute 12.34.56.78**, ce qui m'a retourné ces informations:

![](https://i.imgur.com/SZDT8Y9.png)

Selon moi, l'adresse IP de la passerelle est: **10.33.3.253**.
