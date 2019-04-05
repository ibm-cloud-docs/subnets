---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, Global IP addresses, Update button

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Router une adresse IP globale vers un dispositif
{:#route-global-ip-address-device}

Les adresses IP globales sont routées manuellement par l'utilisateur vers n'importe quel dispositif offert par {{site.data.keyword.BluSoftlayer_notm}}. Pour router une adresse IP globale vers un dispositif, celui-ci doit être associé au compte propriétaire de l'adresse IP globale. Suivez les étapes décrites ci-dessous pour router une adresse IP globale vers un dispositif.

1. Accédez à l'écran IP Globale sur le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/). Voir [Afficher l'écran IP Globale](/docs/infrastructure/subnets?topic=subnets-display-the-global-ip-screen){:new_window}.
* Sélectionnez le sous-réseau de l'adresse IP globale que vous souhaitez router.
* Commencez par entrer l'adresse IP du dispositif vers lequel l'adresse IP sera routée dans la zone **Route vers**. Cette zone sera remplie automatiquement sur la base de votre entrée. Elle affiche tous les dispositifs associés à votre compte.
* Entrez toute remarque pertinente à propos de l'adresse IP globale, du dispositif ou de tout autre sujet dans la zone **Notes**.
* Sélectionnez le bouton **Mettre à jour** pour procéder au routage ou **Annuler** pour annuler l'action et retourner à l'écran **Sous-réseaux**.

## Etapes suivantes
{:#route-global-ip-address-device-next}

Lorsque vous initiez le routage du sous-réseau d'adresse IP globale, le processus commence. Les routages prennent généralement moins d'une minute à s'exécuter. L'adresse IP globale peut être [déroutée](/docs/infrastructure/subnets?topic=subnets-unroute-a-global-ip-address-from-a-device) du dispositif à tout moment.
