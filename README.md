**B1 Réseau 2018 - TP2**
===

### **Partie 1 - Exploration locale en solo**

Nom, adresse MAC et adresse IP de l'interface Wifi:

Sous Mac Os:
######
###### IFCONFIG

Pour afficher les informations, on ouvre un Terminal MacOs et on tape **IFCONFIG**

| NOM         | Carte Réseau Sans Fil           | Binaire|
| ------------- |-------------|----------------|
| Masque de sous-réseau      | 0xfffffc00 ou 255.255.252.0 | 11111111.11111111.11111100.00000000|
| Adresse MAC      | 88:e9:fe:7e:4d:2a ||
| Adresse IP (IPv4) | 10.33.2.18/22|00001010.00100001.00000010.00010010/22|

######
###### Nom, adresse MAC et adresse IP de l'interface Ethernet:

###### Pas de carte Ethernet

**Pour le réseau WIFI:**

**Adresse Réseau:** Adresse IP = 10.33.2.18/22 en binaire = **00001010.00100001.00000010.00010010**

**Masque:** 255.255.252.0 en binaire = **11111111.11111111.11111100.00000000**

L'adresse de réseau est donc **00001010.00100001.00000000.00000000**

**Adresse Broadcast:** 10.33.3.255, en binaire = 00001010.00100001.00000011.11111111

**Affichez votre Gateway:**

Pour déterminer la Gateway, j'ai fait un **traceroute 12.34.56.78**, ce qui m'a retourné ces informations:

![](https://i.imgur.com/SZDT8Y9.png)

L'adresse IP de la passerelle est: **10.33.3.253**.

**En Graphique (GUI):**

Trouver l'IP, la MAC et la Gateway pour l'interface Wifi de votre MAC:

Je suis allé dans le menu **"Pomme"** et j'ai cliqué sur **"Préférences Système"**. Ensuite, je suis allé dans la section **"Réseau"**, j'ai cliqué sur **"Avancé"** et dans la partie **"TCP/IP"** pour afficher l'ensemble des informations.

On peut également passer par la touche **'Option'** du clavier et cliquer en haut à droite sur l'icône du Wifi pour aller dans **'Ouvrir les préférences Réseau'**

![](https://i.imgur.com/sB88blq.png)

La Gateway sert à faire le lien entre notre réseau local et le réseau Internet. Il sert à faire une passerelle entre ces deux réseaux informatique.
###### 
###### IP = 00001010.00100001.00000010.00010010
###### Masque = 11111111.11111111.11111100.00000000
###### Réseau = 00001010.00100001.00000000.00000000

1ère adresse IP dispo: **10.33.3.1**
Dernière adresse IP dispo: **10.33.3.255**

**nmap**

Après l'installation de nmap, j'ai tapé la commande `nmap -sn -PE 10.33.0.0/22`

```
>Nmap scan report for 10.33.3.254
Host is up (0.0093s latency).
MAC Address: 88:e9:fe:7e:4d:2a (Tp-link Technologies)
Nmap scan report for 10.33.2.18
Host is up.
Nmap done: 1024 IP addresses (207 hosts up) scanned in 34.91 seconds
MacBook-Pro-de-Fred:~ fredcharruyer$ 

**nmap -sn -PE 10.33.0.0/22**

**Résultat:**

![](https://i.imgur.com/ZtiU0iu.png)

Au Campus Ynov, il y a **1024 adresses IP** au total

### **Partie 2 - Exploration locale en duo**

## II. Exploration locale en duo

Une fois les firewall désactivés on s'est connectés en RJ45.

### Cablâge

On s'est branché via un câble RJ45 à nos adaptateurs

---
### 3. Modification d'adresse IP


Nous avons tout deux modifié l'adresse IP de notre carte Ethernet

**Adresse IP de Sascha :** `10.0.0.2`

**Adresse IP de Mathis :** `10.0.0.3`

**Masque de sous-réseau :** `255.255.255.0`

**Test avec le ping :**
Statistiques Ping pour 10.0.0.3 :
```
--- 10.0.0.3 ping statistics ---
19 packets transmitted, 19 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.663/0.901/1.218/0.132 ms
MacBook-Pro-de-Sascha:~ saschasalles$ 
```

### 4. Utilisation d'un des deux comme gateway

Mathis à désactiver sa carte Wifi.

J'ai activé le partage internet. Mais helas sous nous ne pouvons pas acceder à la gateway de l'adaptateur RJ45.

### 5.Petit chat privé
Après 2h passé à essayer de faire la commande nc -l -p 8888, sur le mac de mathis,ainsi que celui de fred, nous n'avons réussi à faire le chat. Nous ne pouvons pas configurer l'ip 182.168.1.12 sur l'adaptateur réseau Nous ne pouvons qu'écouter mais pas envoyer de message. Nous avons essayé sur une VM Linux, évidemment cela n'a pas marché. 

### 6. WireShark
On a pas forcement tout compris de ce truc, mais je te joins un screen des connexions que j'ai filtrer, meme si je vois pas l'interet.

![alt text](https://github.com/Sascha40/TP2-Reseau/blob/master/images/Capture%20d’écran%202019-01-21%20à%2017.16.59.png)

### 7. Firewall

Non fait

---
## III. Exploration locale en duo
### DHCP

Pour savoir ça il faut aller dans le **Terminal** et taper **`system_profiler SPNetworkDataType | grep "Server Identifier"**`

Il nous reponds :
**`Server Identifier: 10.33.3.254`**

Pour ce qui est de la durée du bail nous ne parvenons pas à trouver la durée du bail dhcp sur mac. Mais il y a un onglet duration sur la commande `system_profiler SPNetworkDataType`

![alt text](https://github.com/Sascha40/TP2-Reseau/blob/master/images/Capture%20d’écran%202019-01-21%20à%2017.47.47.png)

---

**A propos du DHCP**


**DHCP** signifie Dynamic Host Configuration Protocol (protocole de configuration automatiques des hôtes.)

Il est chargé de la configuration automatique des adresses IP d'un réseau. 
Cela évite à l'utilisateur paramétrer les IP manuellement.

---
Toujours dans notre dans le terminal, on tape la commande **`sudo ipconfig set en0 DHCP`**

### DNS


Avec la commande **`system_profiler SPNetworkDataType`**

**`Serveur DNS : 10.33.10.20`**

Bien que notre commande nous fourni aussi une deuxieme adresse IP du serveur DNS: la **`10.33.10.7`**

![alt text](https://github.com/Sascha40/TP2-Reseau/blob/master/images/Capture%20d’écran%202019-01-21%20à%2018.00.46.png)

---
---

**Nslookup**
 
**lookup de google.com :**

on tape **'dig google.com'** et on obtient **`ANSWER SECTION: google.com. 172.217.22.142`**.

**lookup de ynov.com :**

on tape **'dig ynov.com'** et on obtient **`ANSWER SECTION: ynov.com. 217.70.184.38`**.

Reverse:

Pour **78.78.21.21**

Sous mac nous tapons la commande suivante **`dig -x 78.78.21.21 +short`**

Et on obtient **`host-78-78-21-21.mobileonline.telia.com.`**

Pour **92.16.54.88**

Sous mac nous tapons la commande suivante **`dig -x 92.16.54.88 +short`**

Et on obtient **`host-92-16-54-88.as13285.net.`**

**Intrepretation:**

C'est la même chose que pour le lookup mais dans l'autre sens. 

C'est-à-dire que **`78.78.21.21`** est lié au nom de domaine **host-78-78-21-21.mobileonline.telia.com**

### 3. Bonus

**Se renseigner sur les différences entre WiFi et câble**

Le câble a un meilleur débit que la Wifi car les pertes sont restreintes et que le signal ne peut etre altéré par les murs par exemple.

---

**explorer l'interface d'administration de votre box (chez vous) avec tout ça en tête**

Fournisseur FREE

L'interface est accessible avec l'adresse **http://mafreebox.freebox.fr** sur n'importe quel navigateur WEB, 

Sur le site il y a toutes les infos concernant la Freebox. L'IP, Wifi, paramètres de la Freebox, accès aux téléchargements,  etc.

![](https://i.imgur.com/vipVCKl.jpg)

---

**sinon, elle sert à quoi la MAC si on a des IP ? => Se renseigner sur ARP**

Une adresse IP est attribuée en fonction du réseau et elle change en fonction de l'endroit où on se connecte.

L'adresse MAC est physique, déterminée en fonction de la carte réseau et ne change pas.

---

Nous ne possèdons pas de switch.

---

---
