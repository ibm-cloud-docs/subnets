---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Initiation aux sous-réseaux et aux adresses IP

Les clients IBM Cloud peuvent commander à tout moment des sous-réseaux statiques, des sous-réseaux portables publics et privés ou des sous-réseaux globaux qui se composent d'adresses IPv4 et IPv6. 

Pour commander des sous-réseaux et des adresses IP :

1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/){: new_window} et connectez-vous à votre compte.
2. Dans la structure de navigation du portail client, sélectionnez **Réseau > Gestion IP > Sous-réseaux**.
3. Pour commencer le processus de commande, sélectionnez le type de sous-réseau approprié dans la liste déroulante. 

**Notez que les sous-réseaux sont créés pour les clients au cas par cas, ce qui implique un processus de filtrage qui tient compte d'un rapport IP/serveur.**

## Connaissance des blocs IP statiques et portables
{{site.data.keyword.BluSoftlayer_notm}} offre actuellement 2 types de blocs IP différents : les blocs statiques et les blocs portables. Ces blocs sont conçus pour être utilisés de différentes manières. Vous trouverez ci-dessous une brève description de chaque type de bloc ainsi qu'une section sur l'utilisation de ces adresses IP sur une machine virtuelle.
 
### Bloc IP statique
Le bloc IP le plus communément utilisé au sein du réseau {{site.data.keyword.BluSoftlayer_notm}} est le bloc IP statique. Un bloc IP statique est routé directement à une adresse IP spécifique sur notre réseau. Chaque adresse IP d'un bloc statique est utilisable sur le serveur. Le principal avantage à utiliser un bloc IP statique est que vous ne perdez pas les deux premières ni les deux dernières adresses IP. Toutes les adresses du bloc sont utilisables. 

L'exemple suivant montre un petit bloc IP statique (192.168.0.4/30). Ici les 4 adresses IP de ce bloc sont disponibles sur le serveur :
```
·192.168.0.4 – Usable Address
·192.168.0.5 – Usable Address
·192.168.0.6 – Usable Address
·192.168.0.7 – Usable Address
```
Dans le cas d'un bloc portable, une seule adresse IP de ce bloc serait utilisable sur le serveur car le réseau, la passerelle et les adresses IP de diffusion sont directement liés au réseau local virtuel. 

Remarque : il existe une technique spéciale qui permet d'utiliser toutes les adresses IP car l'utilisation du masque de sous-réseau affecté vous permet seulement d'utiliser toutes les adresses sauf une (l'adresse IP de diffusion). Pour utiliser toutes les adresses IP, utilisez le masque de sous-réseau 255.255.255.255 pour éviter de manquer l'adresse IP de diffusion.

### Bloc IP portable 
Un bloc IP portable peut être utilisé sur plusieurs serveurs d'un même réseau local virtuel simultanément. Nous offrons deux types de blocs IP portables différents :

 * Le premier type de bloc IP portable est le bloc “routé vers le réseau local virtuel”. Il s'agit d'un bloc IP statique qui est routé vers un réseau local virtuel entier plutôt que vers une adresse IP spécifique.
 * L'autre type de bloc IP portable est le bloc “secondaire sur le réseau local virtuel” qui est conçu pour être utilisé dans un environnement virtuel.
 
La principale différence entre les deux est le nombre d'adresses IP pouvant être utilisées. 

Un bloc **routé vers le réseau local virtuel**, comme un bloc statique, vous donne accès à toutes les adresses IP du bloc. En revanche, un bloc **secondaire sur le réseau local virtuel** nécessite que le réseau, la passerelle et les adresses IP de diffusion soit directement liés au réseau local virtuel, ce qui les rend inutilisables. Un bloc **routé vers le réseau local virtuel** est utilisé lorsque l'utilisateur souhaite utiliser n'importe quelle adresse IP de ce bloc sur n'importe quel serveur du réseau local virtuel à tout moment. Le bloc **secondaire sur le réseau local virtuel** est utilisé conjointement avec une machine virtuelle. Vous trouverez des informations supplémentaires sur les blocs **secondaires sur le réseau local virtuel** dans la section _Adresses IP pour machines virtuelles_.

Lorsque vous commandez un bloc IP portable, {{site.data.keyword.BluSoftlayer_notm}} vous fournit par défaut un bloc **secondaire sur le réseau local virtuel**. Si vous souhaitez convertir ce bloc en un bloc **routé vers le réseau local virtuel** pour une utilisation sur vos serveurs au sein d'un réseau local virtuel unique, ouvrez un ticket de demande de service et demandez la conversion de ce bloc en un bloc **routé vers le réseau local virtuel** 

### POD prenant en charge le protocole HSRP (Hot Standby Router Protocol)

Il est important de noter que les POD qui profitent du protocole HSRP (Hot Standby Router Protocol) utilisent 2 adresses IPv4 additionnelles : une pour l'interface du réseau local virtuel de chaque routeur participant, et une pour chaque bloc **secondaire sur le réseau local virtuel** configuré sur le réseau local virtuel. La plupart de nos POD prennent en charge le protocole HSRP.

L'exemple suivant montre un bloc **secondaire sur le réseau local virtuel** (192.168.0.4/28) utilisé pour plusieurs machines virtuelles dans un POD HSRP.
```
192.168.0.0 –  Network Address
192.168.0.1 –  Gateway Address
192.168.0.2 –  Router A Vlan Interface
192.168.0.3 –  Router B Vlan Interface
192.168.0.4 –  VPS1
192.168.0.5 –  VPS2
192.168.0.6 –  VPS3
192.168.0.8 –  VPS4
192.168.0.9 –  VPS5
192.168.0.10 – VPS6
192.168.0.11 – VPS7
192.168.0.12 – VPS8
192.168.0.13 – VPS9
192.168.0.14 – VPS10
192.168.0.15 – Broadcast Address
```
 
### Adresses IP pour machines virtuelles
Les machines virtuelles sont communément utilisées dans les charges de travail sur le cloud, ou "instances". Cette section indique quels types de blocs IP doivent être utilisés dans une machine virtuelle. Les informations fournies ici sont basées sur Microsoft Hyper-V.

Chaque machine virtuelle connectée au réseau {{site.data.keyword.BluSoftlayer_notm}} dans un environnement virtuel nécessite une adresse IP principale d'un bloc d'IP portable car Hyper-V nécessite que chaque machine virtuelle fournisse un réseau, une passerelle et une adresse de diffusion sur le même sous-réseau que l'adresse IP principale affectée à cette machine virtuelle. L'un des avantages de notre configuration réseau est qu'un seul bloc **secondaire sur le réseau local virtuel** peut être utilisé pour plusieurs machines virtuelles. 

L'exemple suivant montre un bloc **secondaire sur le réseau local virtuel** (192.168.0.4/29) utilisé pour plusieurs machines virtuelles :
```
·192.168.0.0 – Network Address
·192.168.0.1 – Gateway Address
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Broadcast Address
```
Comme le montre l'exemple, ce bloc **secondaire sur le réseau local virtuel** fournit 5 adresses IP utilisables sur les 8 adresses IP contenues dans le bloc, reliées entre 3 machines virtuelles différentes. Cette configuration soulève une question : “Comment faire pour ajouter d'autres adresses IP à une machine virtuelle si toutes les adresses IP sont utilisées sur le bloc portable ?". Ce problème peut être résolu en utilisant un bloc statique ou un bloc portable **routé vers le réseau local virtuel**.

Pour utiliser un bloc statique dans une machine virtuelle, commandez d'abord un nouveau bloc IP statique sur le portail client. Durant le processus de commande, vous pouvez sélectionner l'adresse IP vers laquelle vous souhaitez que ce bloc soit routé. En sélectionnant l'adresse IP affectée à la machine virtuelle, le nouveau bloc sera spécifiquement routé à cette machine virtuelle. Vous pouvez ensuite lier le nouveau bloc d'adresses IP directement à cette machine virtuelle et commencer à les utiliser immédiatement.

Si vous souhaitez que le nouveau bloc puisse être utilisé par plusieurs machines virtuelles, utilisez un bloc **routé vers le réseau local virtuel**. Pour obtenir un bloc **routé vers le réseau local virtuel**, achetez un bloc IP portable sur le portail et sélectionnez le réseau local virtuel sur lequel réside l'adresse IP de la machine virtuelle. Une fois que le bloc IP est créé, il peut être utilisé sur n'importe quel serveur ou n'importe quelle machine virtuelle sur ce réseau local virtuel.
