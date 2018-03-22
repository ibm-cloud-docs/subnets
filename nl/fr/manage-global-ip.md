---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Gérer les adresses IP globales

Vous pouvez gérer vos adresses IP globales dans l'écran **Sous-réseaux**. 

1. Dans votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/){: new_window} et connectez-vous à votre compte.
2. Dans la structure de navigation du portail client, sélectionnez **Réseau > Gestion IP > Sous-réseaux**.
3. Dans le menu déroulant, sélectionnez **IPv4 Global** (ou IPv6) pour filtrer la liste des sous-réseaux afin d'afficher uniquement les adresses IP globales.
4. Cliquez sur l'adresse IP globale que vous souhaitez gérer.
 
  **Remarque : une adresse IP globale est une adresse IP statique qui peut être routée vers n'importe quel serveur à l'intérieur du réseau IBM Cloud. L'offre actuelle d'adresse IP statique peut uniquement être routée à une adresse IP au sein du même centre de données, mais les adresses IP globales ne sont pas soumises à cette restriction.**

5. Sur la page de gestion des adresses IP, entrez l'adresse IP du serveur vers lequel vous souhaitez router l'adresse IP globale et saisissez une remarque, si applicable, puis sélectionnez **Mettre à jour**.

![Figure 2](images/2_1.png)

## Ajouter une adresse IP globale à votre serveur 

Avant que votre serveur accepte le trafic de l'adresse IP globale, cette adresse IP doit être ajoutée correctement au système. Chaque système requiert des commandes légèrement différentes, qui sont présentées dans les sections qui suivent.

### Pour les serveurs Linux :

**Red Hat/CentOS**

1. Editez (vim ou nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* Ajoutez les lignes suivantes :
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. Editez `/etc/network/interfaces`

* Ajoutez les lignes suivantes :

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

Si votre système ne fonctionne pas correctement, ajoutez les lignes suivantes à la place, en remplaçant le signe # par le prochain numéro disponible :

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### Pour les serveurs Windows

1. Accédez à **Démarrer -> Panneau de configuration -> Connexions réseau -> Connexion au réseau local (Public) (propriétés)**.
* Sélectionnez **Protocole Internet (TCP/IP)** et cliquez sur **Propriétés -> Avancées**.
* Sélectionnez **Ajouter** dans la section Adresses IP et entrez l'adresse IP et le masque de sous-réseau.
* Une fois cette tâche terminée, sélectionnez simplement "OK" pour retourner au bureau.

Pour vérifier que vos paramètres ont été appliqués, ouvrez une invite DOS en sélectionnant **Démarrer -> Exécuter -> "cmd"** et exécutez la commande

```
        > ipconfig /all
```

**Remarques :**

* Si vous avez déjà un fichier `eth1:1` sur votre serveur comme dans l'exemple ci-dessus, incrémentez le dernier chiffre au prochain nombre entier disponible.
* La modification d'une adresse IP globale vers un nouveau serveur ou VSI peut prendre jusqu'à cinq minutes avant d'entrer en vigueur. 
* Au sein du réseau IBM Cloud, le changement de route prend moins d'une minute à être mis à jour.
* Les adresses IP globales ne fonctionnent pas avec les équilibreurs de charge locaux.
* Les adresses IP globales sont distribuées depuis un sous-réseau unique ; les adresses IP existantes des clients ne peuvent pas être converties ni utilisées en tant qu'adresses IP globales.
* En soi, les adresses IP globales ne sont pas une solution de basculement automatique, car elles ne font pas l'objet de contrôles de santé ; cependant, une adresse IP globale peut être utilisée comme composant d'un environnement de basculement, si vous voulez contourner la propagation du DNS.
