---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: IP addresses, IPs Subnets, types of subnets

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Initiation aux sous-réseaux et aux adresses IP
{:#getting-started-subnets-ips}

Les sous-réseaux constituent un élément important de la façon dont vous utilisez Internet, et cela vaut également avec {{site.data.keyword.cloud}}. Nous utilisons une terminologie spécifique pour décrire les types et les utilisations des sous-réseaux accessibles sur notre plateforme. Chaque sous-réseau fournit des adresses IP aux ressources de différentes manières. Vous serez amené à utiliser les types de sous-réseaux ci-dessous et en connaissant mieux chaque type de sous-réseau, vous serez en mesure de les utiliser au mieux dans votre infrastructure de Cloud.

  * Sous-réseaux principaux : Sous-réseaux attribués pour répondre aux besoins d'adressage IP d'autres produits, tels que des instances de serveurs virtuels ou Bare Metal. Ces sous-réseaux sont automatiquement attribués et supprimés.
  * Sous-réseaux secondaires : Sous-réseaux achetés et routés par vos soins. Vous pouvez également les annuler si besoin. Il existe deux sous-types :
    * Portable : Les adresses IP sont mises à la disposition de toutes les ressources d'un réseau local virtuel (VLAN).
    * Statique : Les adresses IP sont mises à la disposition de la ressource identifiée comme noeud final de routage.
  * Adresses IP globales : Il s'agit d'un comportement de routage unique basé sur le réseau principal d'{{site.data.keyword.cloud}}, qui fournit des adresses IP à la ressource identifiée comme noeud final de routage.

Examinez en détail chaque type dans la section [Présentation des sous-réseaux et des adresses IP](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) afin d'obtenir des précisions supplémentaires, notamment sur les différences entre IPv4 et IPv6 et la disponibilité des réseaux public/privé.

Afin de comprendre plus généralement les sous-réseaux et le mécanisme sous-jacent, consultez la rubrique [Sous-réseau ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Subnetwork).
De plus, vous verrez la façon dont nous faisons référence aux sous-réseaux à l'aide de la [notation CIDR ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


## Commander des sous-réseaux
{:#ordering-subnets}

Suivez la procédure de commande de sous-réseaux ci-dessous afin de bénéficier d'adresses IP supplémentaires :

  1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/){: new_window} et connectez-vous à votre compte.
  1. Dans la navigation du portail client, sélectionnez **Infrastructure classique**. 
  1. Dans la navigation Infrastructure classique, sélectionnez **Réseau > Gestion IP > Sous-réseaux**.
  1. Cliquez sur le lien "Nouvelles adresses IP" en haut à droite de la liste.
  1. Pour commencer le processus de commande, sélectionnez un type de sous-réseau à l'aide des boutons radio Public ou Privé.
  1. Choisissez l'option IPv4 ou IPv6.
  1. Pour sélectionnez des IP statiques ou globales, cliquez sur la case correspondante. 
    1. Pour IPv4, utilisez la liste déroulante disponible dans les options Statique ou Portable pour choisir le nombre d'adresses que vous souhaitez avoir. 
  1. Sélectionnez le VLAN vers lequel acheminer les nouvelles adresses IP.
  1. Renseignez les informations demandées et cliquez sur **Créer**.


Après avoir acheté un sous-réseau, vous ne pouvez plus modifier le type ni la destination du routage. Vous devez commander un nouveau sous-réseau pour utiliser un type ou un noeud final de routage différent.

### Etapes suivantes
{:#ordering-subnets-next}

A moins qu'un processus d'approbation du statut de votre compte ne soit nécessaire, le nouveau réseau configuré selon vos besoins apparaît sur votre compte au bout de quelques instants.
