---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-05"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Router une adresse IP globale vers un dispositif

Les adresses IP globales sont routées manuellement par l'utilisateur vers n'importe quel dispositif offert par {{site.data.keyword.BluSoftlayer_notm}}. Pour router une adresse IP globale vers un dispositif, celui-ci doit être associé au compte propriétaire de l'adresse IP globale. Suivez les étapes décrites ci-dessous pour router une adresse IP globale vers un dispositif.

1. Accédez à l'écran IP Globale sur le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/). Voir [Afficher l'écran IP Globale](display-global-ip-screen.html){:new_window}.
* Sélectionnez le sous-réseau de l'adresse IP globale que vous souhaitez router.
* Commencez par entrer l'adresse IP du dispositif vers lequel l'adresse IP sera routée dans la zone **Route vers**. Cette zone sera remplie automatiquement sur la base de votre entrée. Elle affiche tous les dispositifs associés à votre compte.
* Entrez toute remarque pertinente à propos de l'adresse IP globale, du dispositif ou de tout autre sujet dans la zone **Notes**.
* Sélectionnez le bouton **Mettre à jour** pour procéder au routage ou **Annuler** pour annuler l'action et retourner à l'écran **Sous-réseaux**.

## Etapes suivantes

Lorsque vous initiez le routage du sous-réseau d'adresse IP globale, le processus commence. Les routages prennent généralement moins d'une minute à s'exécuter. L'adresse IP globale peut être [déroutée](unroute-global-ip.html) du dispositif à tout moment.
