---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Addresses, Global IP address, single IP address

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# A propos des adresses IP globales
{:#about-global-ip-address}

Une adresse IP globale est un sous-réseau secondaire statique spécialisé. Il vous est distribué en tant que sous-réseau /32 (en d'autres termes, une seule adresse IP) qui peut être routé vers n'importe quelle autre adresse IP sur votre compte. Les adresses IPv4 et IPv6 sont disponibles, et chaque type doit être routé vers une adresse IP de la même version IP. Les cibles de routage admises sont les adresses IP principales utilisées par vos serveurs ainsi que toutes les adresses IP de sous-réseau secondaire portable. Les fonctionnalités d'une adresse IP globale sont les suivantes :

  * Le routage est effectué à la demande vers des adresses IP sur un compte, de manière globale.
  * L'adresse est annoncée sur Internet par tous les routeurs périphériques {{site.data.keyword.cloud}}. Par conséquent, vos données empruntent le chemin le plus court vers le réseau {{site.data.keyword.cloud}}, et vous pouvez utiliser le réseau principal global {{site.data.keyword.cloud}} dédié, pour atteindre la destination que vous avez configurée.

Les adresses IP globales offrent une certaine souplesse. En effet, elles vous permettent de transférer des charges de travail entre les serveurs, même dans des centres de données éloignés géographiquement. En outre, les adresses IP globales assurent la persistance IP en autorisant les transitions sans avoir besoin d'adaptation (par exemple, pour éviter les caches DNS). La fonctionnalité de routage globale est idéale pour répartir les charges de travail sur plusieurs sites de reprise après incident, ou pour effectuer en douceur un nouveau déploiement dans une zone géographique qui répond mieux aux besoins de votre audience.

| **Disponibilité** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Réseau public   | Oui  | Oui  |
| Réseau privé  |      |      |


## Gestion des adresses IP globales
{:#manage-global-ip-address}

Pour gérer des adresses IP globales, procédez comme suit :

 1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/){: new_window} et connectez-vous à votre compte.
 1. Dans la navigation du portail client, sélectionnez **Infrastructure classique**.
 1. Dans le menu de navigation Infrastructure classique, sélectionnez **Réseau > Gestion IP > IP globale**.
 1. La liste de vos adresses IP globales s'affiche. Utilisez les filtres pour affiner votre recherche si besoin. 
 
Certaines entrées peuvent ne pas avoir de valeur dans la zone **Cible**. Cela signifie que l'adresse IP globale n'est pas actuellement routée et que par conséquent elle n'est pas en service.

### Activation et désactivation du routage d'adresses
{:#route-unroute-address}

Une fois que vous avez localisé l'adresse IP globale de votre choix, cliquez sur son identificateur de sous-réseau. Un écran s'affiche dans lequel vous verrez sa cible de routage actuel, le cas échéant. Pour router, à savoir acheminer le trafic vers une nouvelle destination, deux options s'offrent à vous :

 * Entrer une adresse IP complète, ou
 * Commencer à saisir un nom d'hôte.
 
Lorsque vous saisissez un nom d'hôte, vous pouvez rechercher le nom d'hôte d'un serveur et par conséquent son adresse IP. Après avoir entré l'adresse IP, sélectionnez **Mise à jour**. Pour désactiver le routage d'une adresse IP globale, sélectionnez **Effacer**. Lorsque le statut change en 'Non routé', sélectionnez **Mise à jour**.

La liste du menu déroulant des adresses IP disponibles n'est pas exhaustive. Vous avez la possibilité de saisir l'adresse IP de votre choix si celle-ci n'apparaît pas dans la liste de sélection.
{:note}

### A quelle fréquence puis-je faire des mises à jour ?
{:#how-often-can-i-update}

Une seule mise à jour de routage à la fois est autorisée. Si vous tentez de mettre à jour un routage d'adresse IP globale alors qu'une mise à jour est déjà en cours d'exécution, un message d'erreur apparaît. Attendez que la mise à jour soit complètement terminée avant d'effectuer une nouvelle tentative.


## Comment puis-je commander des adresses IP globales ?  
{:#how-to-order-global-ip-address}

Effectuez les étapes ci-dessous pour commander des adresses IP globales :

  1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/){: new_window} et connectez-vous à votre compte.
  1. Dans la navigation du portail client, sélectionnez **Infrastructure classique**.
  1. Dans le menu de navigation Infrastructure classique, sélectionnez **Réseau > Gestion IP > IP globale**.
  3. Cliquez sur le lien **Nouvelles adresses IP**.
  4. Dans le menu déroulant, sélectionnez **IPv4 Global** ou **IPv6 Global** en fonction de vos besoins puis cliquez sur **Continuer** pour initier le processus de commande.

![Figure 1](images/1_2.png)

### Etapes suivantes
{:#global-ip-address-next}

A moins qu'un processus d'approbation du statut de votre compte ne soit nécessaire, le nouveau sous-réseau d'adresse IP globale apparaît sur votre compte au bout de quelques instants.

### Limite de ressource
{:#global-ip-resource-limit}

Un compte ne peut avoir que cinq (5) adresses IP globales par version d'IP. Par exemple, cinq (5) adresses IP globales IPv4, et cinq (5) adresses IP globales IPv6.

## Comment annuler des adresses IP globales ?
{:#how-to-cancel-global-ip-address}

Si vous n'avez plus besoin d'une adresse IP globale, procédez comme suit pour la supprimer :

  1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/){: new_window} et connectez-vous à votre compte.
  1. Dans la navigation du portail client, sélectionnez **Infrastructure classique**.
  1. Dans le menu de navigation Infrastructure classique, sélectionnez **Réseau > Gestion IP > IP globale**.
  1. Filtrez si besoin les résultats pour localiser l'adresse concernée.
  1. Un cercle avec un X apparaît en regard de l'entrée dans la liste d'adresses. Cliquez sur l'icône pour lancer le processus d'annulation.
