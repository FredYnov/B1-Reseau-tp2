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

**En Graphique (GUI):**

Trouver l'IP, la MAC et la Gateway pour l'interface Wifi de votre MAC:

Je suis allé dans le menu "Pomme" et j'ai cliqué sur "Préférences Système". Ensuite, je suis allé dans la section "Réseau", j'ai cliqué sur "Avancé" et dans la partie TCP/IP pour afficher l'ensemble des informations.

![](https://i.imgur.com/sB88blq.png)

La Gateway sert à faire le lien entre notre réseau local et le réseau Internet. Il sert à faire une passerelle entre ces deux réseaux informatique.
###### 
###### IP = 00001010.00100001.00000010.00010010
###### Masque = 11111111.11111111.11111100.00000000
###### Réseau = 00001010.00100001.00000000.00000000

1ère adresse IP dispo: 10.33.0.1
Dernière adresse IP dispo: 10.33.3.254

*J'ai du installer un package pour pouvoir utiliser nmap*

**nmap -sn -PE 10.33.0.0/22**

**Résultat:**

![](https://i.imgur.com/ZtiU0iu.png)

Au Campus Ynov, il y a 1024 adresses IP dispos au total

# **Partie 2 - Exploration locale en duo**

En ce qui concerne la partie en Duo, nous avons rencontrés le problème des ports Ethernet. Nous sommes trois et seul 1 des participants possèdent un adaptateur pour port Ethernet. Nous nous sommes mis d'accord pour en acheter un second et faire les tests dans les jours à venir pour mettre en pratique l'exercice demandé.

Pour ma part, j'ai essayé de réaliser l'exercice avec une machine virtuelle mais sans succès. Là aussi, je n'ai pas dit mon dernier mot.
