---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-04"

keywords: IP addresses , IP address, duration of your use

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Présentation des sous-réseaux et des adresses IP
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} utilise une terminologie spécifique pour décrire les types et utilisations des sous-réseaux accessibles sur notre plateforme. Le fait de connaître le vocabulaire associé à ce produit vous permettra d'optimiser son utilisation dans votre infrastructure de cloud.


## Types de sous-réseaux
{:#subnet-types}

### Sous-réseaux principaux
{:#primary-subnets}

Les sous-réseaux principaux sont attribués automatiquement par {{site.data.keyword.BluSoftlayer_notm}}, et permettent d'acheminer les ressources appropriées via les adresses IP. Il est possible d'affecter et de supprimer des sous-réseaux afin de répondre, si nécessaire, aux exigences d'autres produits. Tous les serveurs seront mis à disposition avec au moins une adresse IP à partir d'un sous-réseau principal, communément appelée adresse IP principale. Certains produits et options peuvent par conséquent nécessiter un plus grand nombre d'adresses IP principales.

Notez que vous ne devez en aucun cas utiliser les adresses IP des sous-réseaux principaux qui ne sont pas encore affectées aux ressources. En effet, si vous utilisez des adresses IP qui ne sont pas encore affectées à partir des sous-réseaux principaux, il est fort probable que nous affections ces adresses à une autre ressource à un moment ou un autre. Des conflits d'adresses IP risquent alors de se produire sur le réseau, entraînant ainsi une interruption de service générale. Nous nous réservons le droit de bloquer ou rendre inutilisable toute adresse IP sur un réseau principal qui n'est pas spécifiquement affectée à l'exécution d'autres produits. 

Nous vous **recommandons vivement** d'utiliser des **sous-réseaux secondaires** pour vos adresses IP d'application/de service externes, en particulier lorsque vous concevez des applications multiserveurs. Il est parfaitement possible d'utiliser les adresses IP principales affectées à vos serveurs. Toutefois, cette solution n'offre pas la flexibilité nécessaire pour assurer la maintenance des adresses connues de vos services indépendamment de l'annulation ou du classement des serveurs. Aucune garantie ne peut ainsi être donnée quant à l'ordre dans lequel les adresses IP principales sont affectées, à savoir de manière ascendante, descendante, en ignorant les écarts, etc.

Nous ne pouvons en aucun cas réserver des adresses IP de sous-réseaux principaux pour votre utilisation personnelle.
{:note}

### Sous-réseaux secondaires
{:#secondary-subnets}

Les sous-réseaux secondaires vous fournissent les adresses IP supplémentaires dont vous avez besoin. Contrairement aux sous-réseaux principaux, les sous-réseaux secondaires vous appartiennent et ne peuvent être supprimés que si vous les annulez expressément. Vous pouvez les utiliser lorsque vous avez besoin d'une adresse IP qui ne devrait pas être dépendante d'un dispositif spécifique. Parmi les exemples possibles, citons :

  * Les adresses IP que vous pouvez affecter à vos propres machines virtuelles en local.
  * Les adresses IP de plusieurs services distincts, hébergées par un seul serveur pour vous permettre d'identifier plus facilement le trafic. Généralement utilisées avec les serveurs Web et le protocole TLS.
  * Une adresse IP de service liée à un DNS. Evitez tout délai de mise en cache DNS lorsque vous basculez des charges de travail vers de nouveaux serveurs (l'adresse IP du service ne changera pas simplement parce que l'adresse IP principale du serveur change !).
  * Des configurations à haute disponibilité qui utilisent des protocoles d'adresses IP flottantes.

Pour mettre en places ces utilisations, entre autres, nous offrons diverses options de routage pour les sous-réseaux secondaires. Afin d'illustrer les différences entre les sous-réseaux secondaires que nous proposons, examinons l'exemple ci-dessous.

Voici un exemple d'adresses IP fournies par le sous-réseau 10.0.0.0/29 :
```
10.0.0.0
10.0.0.1
10.0.0.2
10.0.0.3
10.0.0.4
10.0.0.5
10.0.0.6
10.0.0.7
```

#### Sous-réseaux statiques
{:#static-subnets}

Un sous-réseau statique fournit une seule destination avec accès à toutes les adresses IP définies par ce sous-réseau. L'un des avantages de l'utilisation d'un sous-réseau statique est que l'appareil cible peut utiliser toutes les adresses IP définies, sans pour autant subir les habituelles pénalités d'utilisation de réseau, de passerelle et d'adresse de diffusion. Dans notre exemple ci-dessous, toutes les adresses peuvent être utilisées :

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

Si un serveur possède une adresse IP 10.0.0.13, et que vous routez le trafic 10.0.0.0/30 vers 10.0.0.13 de manière statique, ce serveur peut lier quatre adresses IP supplémentaires, chacune de ces adresses recevant le trafic de manière individuelle. Il convient de comprendre qu'aucune conversion d'adresses réseau (NAT) n'est effectuée sur les adresses fournies. Chaque adresse peut être utilisée en mode natif sur les serveurs, et peut donc être utilisée à des fins distinctes.

| **Disponibilité** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Réseau public   | Oui  | Oui  |
| Réseau privé  |      |      |

#### Sou-réseau portable
{:#portable-subnet}

Un sous-réseau portable fournit ses adresses IP à toutes les ressources d'un réseau local virtuel (VLAN). Autrement dit, toutes les ressources informatiques qui partagent le même VLAN peuvent utiliser n'importe quelle adresse fournie par le sous-réseau. Ce comportement est très utile pour les adresses "flottantes" dans plusieurs ressources, et découple le sous-réseau d'une ressource spécifique. L'une des exigences de la portabilité des sous-réseaux est que toutes les adresses IP définies par le sous-réseau ne doivent pas être utilisables par les appareils. Le mécanisme de mise en réseau requiert, en effet, la consommation de certaines adresses IP. Ces adresses consommées sont appelées adresses IP de passerelle, adresses réseau et adresses de diffusion. Remarquez les adresses qui sont disponibles dans notre exemple :

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

| **Disponibilité** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Réseau public   | Oui  | Oui  |
| Réseau privé  | Oui  |      |


### Adresses IP globales
{:#global-ip-addresses}

Pour en savoir plus sur l'offre IP Globale, veuillez consulter la [documentation sur les adresses IP globales](/docs/infrastructure/subnets?topic=subnets-about-global-ip-addresses).

| **Disponibilité** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Réseau public   | Oui  | Oui  |
| Réseau privé  |      |      |


## Annulation des sous-réseaux
{:#canceling-subnets}

Si vous n'avez plus besoin d'un sous-réseau secondaire, procédez comme suit pour le supprimer :

  1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/){: new_window} et connectez-vous à votre compte.
  1. Dans la navigation du portail client, sélectionnez **Infrastructure classique**. 
  1. Dans le menu de navigation Infrastructure classique, sélectionnez **Réseau > Gestion IP > Sous-réseaux**.
  1. Choisissez les filtres appropriés pour localiser le sous-réseau concerné.
  1. Dans la liste des sous-réseaux, un cercle rouge avec un X à l'intérieur apparaît en regard de l'entrée du sous-réseau. Cliquez sur l'icône pour lancer le processus d'annulation.


## Remarques spécifiques au produit lors de la commande de sous-réseaux
{:#product-specific-considerations-subnets}

### Pare-feu matériel (partagé)
{:#hardware-firewall-subnets}

Par défaut, les sous-réseaux portables ne sont pas protégés par les pare-feu. Si vous avez besoin de cette fonctionnalité, veuillez en discuter avec votre représentant commercial. Les sous-réseaux secondaires au-delà de /29 ne peuvent pas être routés via cette offre de pare-feu.

### Transfert d'adresses IP de sous-réseaux portables entre serveurs
{:#transferring-portable-subnet-ip-between-servers}

Lorsque vous transférez une adresse IP d'un serveur à un autre, assurez-vous qu'un paquet ARP gratuit est envoyé. Ceci permet aux routeurs de mettre à jour leur entrée ARP et de transmettre l'adresse IP mise à jour au bon serveur. Dans le cas contraire, un délai de 4 heures maximum peut être constaté lors de la réception du trafic de l'adresse envoyée sur le nouveau serveur.

### Dispositifs de routeur virtuel
{:#virtual-router-appliances-subnets}

Lorsque vous commandez des sous-réseaux pour un réseau local virtuel (VLAN) derrière un dispositif de routeur virtuel à haute disponibilité, vérifiez que le sous-réseau est configuré correctement pour permettre la reprise en ligne entre les deux dispositifs. Pour toute aide supplémentaire, veuillez consulter la documentation [VRA High Availability Configuration](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
