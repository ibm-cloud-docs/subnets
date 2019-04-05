---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Utilisation de sous-réseaux secondaires sur des machines virtuelles auto-hébergées
{:#use-secondary-subnets-self-hosted-vms}

Si vous hébergez vos propres machines virtuelles et que vous voulez qu'elles occupent la première place sur le réseau {{site.data.keyword.BluSoftlayer_notm}}, vous devez faire appel à des **sous-réseaux secondaires**. Nous allons examiner une manière souple de fournir des adresses IP à vos machines virtuelles, grâce à l'utilisation d'un ou de plusieurs hôtes de machine virtuelle, qu'ils fassent partie ou non d'une configuration en cluster.

Vous pouvez vous reporter à la rubrique [A propos des sous-réseaux](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) tout au long de ce scénario afin d'en savoir plus sur les types de sous-réseaux présentés.

Supposons que vous avez deux serveurs bare metal, que nous appellerons `tante` et `oncle`. Tous les deux seront hébergés sur vos propres machines virtuelles, et possèdent déjà des adresses IP attribuées à partir d'un **réseau principal**. Vous avez besoin d'adresses IP supplémentaires pour vos machines virtuelles. Pour cela, vous pouvez utiliser n'importe quel type de sous-réseau, mais nous vous conseillons d'utiliser un **sous-réseau secondaire portable** comme source des adresses utilisées par vos machines virtuelles. Un sous-réseau portable fournit à `tante` et à `oncle` l'accès aux adresses IP définies par le sous-réseau. De cette façon, vous pourrez partager ces adresses IP entre les deux serveurs, et si vous utilisez les techniques de migration pour vos machines virtuelles, vous pourrez transférer automatiquement ces machines virtuelles vers ces serveurs. 

Maintenant, supposons que vous avez créé deux machines virtuelles, `VPS1` et `VPS2`, que vous avez acheté le sous-réseau portable 129.42.0.0/29 et que vous avez affecté deux de ses adresses à vos machines virtuelles. L'utilisation des adresses IP peut ressembler à ce qui suit :

129.42.0.0/29 - Sous-réseau secondaire portable
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

Admettons maintenant que vous vouliez affecter plus d'adresses IP à VPS1 afin de séparer les services qu'elle fournit. Vous pouvez parfaitement affecter de nouvelles adresses à partir du sous-réseau 129.42.0.0/29, mais vous pouvez également vouloir que ce sous-réseau serve uniquement à connecter les machines virtuelles et non leurs services. Deux options s'offrent alors à vous : 1) acheter un autre sous-réseau portable ou 2) acheter un sous-réseau statique. Si vous vous souvenez ce que qui a été dit au sujet des sous-réseaux portables et statiques dans la rubrique [A propos des sous-réseaux](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), vous savez que les sous-réseaux portables sont plus flexibles, mais qu'ils ne vous permettent pas d'accéder à l'ensemble des adresses IP. Si vous n'avez besoin, par exemple, que de quatre adresses IP supplémentaires, l'achat d'un sous-réseau statique s'avère une option judicieuse. Voyons cela en détail.

Vous achetez un sous-réseau statique et vous recevez le réseau 129.42.0.100/30. Au moment de l'achat, vous le routez vers 129.42.0.3 ou la machine VPS1, dans ce scénario. Vous disposez ainsi de quatre adresses IP supplémentaires que vous pouvez utiliser sur n'importe quel serveur qui répond à 129.42.0.3, à savoir encore une fois, la machine VPS1 dans notre scénario, mais vous pourriez à tout moment acheminer le trafic de 129.42.0.3 vers VPS2, et les quatre nouvelles adresses IP de 129.42.0.100/30 en feraient de même ! Regardons à nouveau l'utilisation des adresses IP :

129.42.0.0/29 - Sous-réseau secondaire portable
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

129.42.0.100/30 - Sous-réseau secondaire statique
```
129.42.0.100 – 129.42.0.3 (aka VPS1)
129.42.0.101 – 129.42.0.3 (aka VPS1)
129.42.0.102 – 129.42.0.3 (aka VPS1)
129.42.0.103 – 129.42.0.3 (aka VPS1)
```

Pour résumer, nous avons tout d'abord utiliser un sous-réseau portable pour mettre les adresses IP à la disposition de tous les hôtes de machine virtuelle, puis nous avons utilisé un sous-réseau statique pour mettre les adresses IP supplémentaires à la disposition d'une machine virtuelle spécifique. Vous auriez parfaitement pu utiliser des adresses du sous-réseau portable d'origine, ou simplement ajouter un autre sous-réseau portable. Nous espérons que ce scénario aura su vous montrer qu'il est non seulement possible de router des sous-réseaux statiques vers des adresses IP sur des sous-réseaux portables, mais qu'en plus cette solution se révèle particulièrement efficace et utile.
