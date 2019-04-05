---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Primary IP, IP address, subnet's IP

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}
{:faq: data-hd-content-type='faq'}

# Foire aux questions
{:#subnets-faq}

## Que signifie `IP Principale pour futur serveur uniquement` en ce qui concerne les adresses IP d'un sous-réseau ?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

Les sous-réseaux principaux sont attribués et supprimés par {{site.data.keyword.BluSoftlayer_notm}} en fonction des besoins des autres ressources que vous avez commandées, notamment les instances de serveur virtuel ou Bare Metal. Nous ne faisons pas qu'attribuer une adresse IP à la fois, nous affectons un sous-réseau complet. Cela signifie qu'il reste parfois de la place pour des ressources futures. Par conséquent, cette expression indique que ces adresses seront utilisées par des ressources futures. Veuillez vous reporter à la question "**Puis-je utiliser les autres adresses IP définies par les sous-réseaux principaux que je vois ?**" pour savoir pourquoi vous ne devez pas considérer ces adresses IP comme étant utilisables. 


## Puis-je utiliser les autres adresses IP définies par les sous-réseaux principaux que je vois ?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

Certainement pas ! Nous sommes conscients que vous voyez les sous-réseaux principaux attribués par {{site.data.keyword.BluSoftlayer_notm}} à l'instar des autres sous-réseaux, mais comme il est indiqué dans la section [A propos des sous-réseaux](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), les sous-réseaux principaux servent à acheminer, à la demande, les adresses IP vers les ressources. Nous affectons et retirons des sous-réseaux principaux en fonction des exigences d'autres produits. Si vous utilisez des adresses IP qui ne sont pas affectées à partir de sous-réseaux principaux, nous les attribuerons inévitablement à une autre ressource à un moment donné. Des conflits d'adresses IP risquent alors de se produire sur le réseau, entraînant ainsi une interruption de service générale. Nous nous réservons le droit de bloquer ou rendre inutilisable toute adresse IP sur un réseau principal qui n'est pas spécifiquement affectée à l'exécution d'autres produits. Utilisez des **sous-réseaux secondaires** pour répondre à vos besoins additionnels d'adresses IP, et privilégiez cette solution pour vos besoins en matière d'adresses de service/d'application. Les sous-réseaux secondaires sont bien plus flexibles et restent sur votre compte aussi longtemps que vous le voulez.


## Est-il possible de spécifier le sous-réseau que je souhaite utiliser avec mon unité au moment de la commande ?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

Oui, vous pouvez indiquer un sous-réseau spécifique lors du processus de commande. Lorsque vous commandez une unité, cette option est disponible à la fin du formulaire de commande. Après avoir choisi un VLAN privé, la liste des sous-réseaux principaux acheminés vers ce réseau s'affiche. Vous pouvez sélectionner le sous-réseau de votre choix. La même procédure est disponible pour un VLAN public. 

Il est important de noter que la soumission de la commande **ne garantit pas** qu'une adresse IP soit disponible dans le sous-réseau demandé. Si aucune adresse n'est disponible, notre service vous contactera pour vous indiquer la marche à suivre. Pour bénéficier de la meilleure expérience {{site.data.keyword.BluSoftlayer_notm}} possible, nous vous déconseillons de sélectionner un sous-réseau dans le cadre d'une utilisation normale.


## Je manque d'adresses IP, que faire ?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

Ceci ne peut pas se produire ! Nous attribuons automatiquement des sous-réseaux principaux afin de fournir les adresses IP dont vous avez besoin pour vos nouvelles ressources. Aucune action n'est requise de votre part. Toutefois, si vous avez besoin de nouvelles adresses IP, par exemple pour des machines virtuelles locales ou pour séparer des applications, lisez la section **Sous-réseaux secondaires** de la rubrique [A propos des sous-réseaux](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).


## Comment puis-je affecter de nouvelles adresses IP à une ressource informatique ?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

Tout d'abord, vous aurez besoin d'acheter un **sous-réseau secondaire**. Il en existe plusieurs types, alors n'hésitez pas à consultez la rubrique [A propos des sous-réseaux](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips). Une fois que votre sous-réseau est routé vers l'adresse IP ou le VLAN de votre choix, consultez la documentation relative à la configuration de vos nouvelles adresses IP :

  * [Affectation d'adresses IP de serveur bare metal](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Affectation d'adresse IP d'instance de serveur virtuel](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## Que signifie `Réservé pour HSRP` en ce qui concerne les adresses IP d'un sous-réseau ?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

En raison du nombre décroissant d'emplacements, {{site.data.keyword.BluSoftlayer_notm}} possède des routeurs qui font appel à la technique HSRP (Hot Router Standby Protocol). Plus précisément, la façon dont celui-ci est utilisé a une influence sur les adresses IP disponibles pour les ***Sous-réseaux secondaires portables*** ; ce qui signifie que vous perdrez l'accès à deux adresses supplémentaires dans ces emplacements. Au niveau de la terminologie, "Réservé pour HSRP", indique que ces adresses IP sont réservées exclusivement aux besoins du protocole HSRP. Vous pouvez avoir des sous-réseaux sur le même routeur, certains avec réservations, et d'autres sans. N'essayez pas d'utiliser ces adresses, faute de quoi le trafic risque d'être affecté sur l'ensemble du sous-réseau.

