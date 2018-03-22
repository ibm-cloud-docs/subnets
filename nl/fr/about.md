---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Présentation des sous-réseaux et des adresses IP

IBM Cloud vous propose plusieurs options pour commander des sous-réseaux et des adresses IP vous permettant de concevoir une infrastructure qui répond à vos besoins. Comprendre le fonctionnement des sous-réseaux et connaître leurs domaines d'application vous aidera à obtenir exactement ce dont vous avez besoin.
.

## Types de sous-réseaux

En connaissant mieux chaque type de sous-réseau, vous pouvez comprendre comment les utiliser au mieux dans votre infrastructure de Cloud.


### Sous-réseaux principaux

Les sous-réseaux principaux sont attribués automatiquement par {{site.data.keyword.BluSoftlayer_notm}} sur les réseaux locaux virtuels dans le but de fournir un approvisionnement et des services automatisés sur vos réseaux locaux virtuels. Ces sous-réseaux ne sont pas disponibles pour vos services ou adresses IP secondaires car ils sont utilisés par nos systèmes automatisés. Les sous-réseaux principaux sont affectés aux nouveaux serveurs de façon automatique. Si vous essayez de les utiliser sur vos serveurs, un conflit peut se produire au niveau de l'adresse IP, et vous devrez alors supprimer l'adresse IP. 

**Remarque : nous ne pouvons pas réserver des adresses IP dans les sous-réseaux principaux pour votre utilisation.**

### Sous-réseaux portables

Les sous-réseaux portables peuvent être commandés sur le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/) Ces sous-réseaux fournissent généralement des adresses de machines virtuelles ou des adresses IP secondaires sur des serveurs ou sur des interfaces secondaires. Ces sous-réseaux sont également utilisés pour les adresses IP de cluster ou HA car ils sont suivis par nos routeurs via l'ARP. Ils peuvent être déplacés facilement. Le format standard de ces sous-réseaux comprend son propre réseau, sa propre passerelle et son adresse de diffusion, par conséquent trois adresses IP seront utilisées immédiatement.

### Sous-réseaux statiques

Les sous-réseaux statiques sont un autre type de sous-réseau que vous pouvez commander à travers le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/network/subnets/order). Les sous-réseaux statiques sont généralement utilisés pour les serveurs Web, les courriers électroniques ou les autres services hébergés sur un serveur qui nécessitent plusieurs adresses IP additionnelles pour permettre les connexions. Les sous-réseaux statiques sont uniques car vous devez spécifier une autre adresse IP existante déjà affectée à un serveur vers lequel le sous-réseau est routé directement. Vous avez la flexibilité de router le sous-réseau comme vous le souhaitez, et vous pouvez le déplacer vers différents serveurs, mais pour ce faire, vous devez changer l'emplacement routé.
.

### Adresses IP globales

Pour obtenir des informations sur l'offre des adresses IP globales, veuillez vous reporter à la [documentation sur les adresses IP globales](about-global-ip.html).

## Eléments à prendre en compte en présence de sous-réseaux différents

### Pare-feu matériels

Par défaut, les sous-réseaux portables ne sont pas protégés par les pare-feu. Si vous avez besoin de cette fonctionnalité, veuillez en discuter avec votre représentant commercial. Les sous-réseaux qui ont besoin d'être protégés ne peuvent pas dépasser un sous-réseau /29.

### Transfert d'adresses IP portables entre serveurs

Lorsque vous transférez une adresse IP portable d'un serveur à un autre, assurez-vous qu'un paquet ARP gratuit est envoyé afin que nos routeurs puissent mettre à jour leur entrée ARP et transmettre l'adresse IP mise à jour au bon serveur. Si vous n'envoyez pas le paquet ARP, il faudra compter 4 heures ou plus pour que l'adresse IP commence à répondre correctement.

### Passerelles Vyatta

Lorsque vous commandez des sous-réseaux pour un réseau local virtuel derrière une passerelle Vyatta, vérifiez que le sous-réseau est ajouté correctement à la configuration de la passerelle Vyatta. Si vous utilisez VRRP for HA, assurez-vous que le sous-réseau est configuré correctement et permet le basculement entre les deux dispositifs de passerelle. Si vous avez besoin d'aide pour effectuer ces tâches, veuillez consulter ces deux articles sur la configuration de la passerelle Vyatta : 

 * [Dispositifs de passerelle réseau Vyatta](../network-gateways/network-gateway-devices-vyatta.html)

 * [Configuration de la haute disponibilité Vyatta](../vyatta/vyatta-high-availability-configuration.html)
 
 ### Annulation des sous-réseaux
 
Les sous-réseaux qui sont automatiquement affectés à un compte dans le cadre des commandes de dispositifs font l'objet de réclamations automatiques lorsque ces sous-réseaux ne sont plus référencés. Les sous-réseaux commandés séparément peuvent être annulés à tout moment. 
