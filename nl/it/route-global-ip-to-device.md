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

# Instrada un indirizzo IP globale a un dispositivo
{:#route-global-ip-address-device}

Gli indirizzi IP globali vengono manualmente instradati dall'utente a qualsiasi dispositivo offerto da {{site.data.keyword.BluSoftlayer_notm}}. Per instradare un IP globale a un dispositivo, questo deve essere associato all'account che gestisce l'IP globale. Utilizza le seguenti istruzioni per instradare un indirizzo IP globale a un dispositivo.

1. Passa alla schermata dell'IP globale nel [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/). Fai riferimento a [Visualizza la schermata dell'IP globale](/docs/infrastructure/subnets?topic=subnets-display-the-global-ip-screen){:new_window}.
* Seleziona la sottorete dell'IP globale da instradare.
* Inizia immettendo l'indirizzo IP del dispositivo a cui sarà instradato l'IP globale nel campo **Routes to**. Questo campo verrà completato automaticamente in base al tuo input. Visualizza tutti i dispositivi associati al tuo account.
* Immetti tutte le note pertinenti che riguardano l'IP globale, il dispositivo o altri elementi, nel campo **Notes**.
* Seleziona il pulsante **Update** per completare l'instradamento o seleziona **Cancel** per annullare l'azione e ritornare alla schermata **Subnets**.

## Operazioni successive
{:#route-global-ip-address-device-next}

Quando avvii la rotta della sottorete dell'IP globale, si avvia il processo. Le rotte generalmente impiegano meno di un minuto per il completamento. In qualsiasi momento può essere [annullato l'instradamento](/docs/infrastructure/subnets?topic=subnets-unroute-a-global-ip-address-from-a-device) al dispositivo.
