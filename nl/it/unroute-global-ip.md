---
copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, unroute process, Device Global IP addresses

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Annulla l'instradamento a un indirizzo IP globale da un dispositivo
{:#unroute-global-ip-address}

L'instradamento degli indirizzi IP globali può essere manualmente annullato dall'utente in qualsiasi momento. Utilizza le seguenti istruzioni per annullare l'instradamento di un indirizzo IP globale da un dispositivo.

1. Passa alla schermata dell'IP globale nel [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/). Fai riferimento a [Visualizza la schermata dell'IP globale](/docs/infrastructure/subnets?topic=subnets-display-the-global-ip-screen){:new_window}.
* Seleziona l'indirizzo IP globale di cui annullare l'instradamento.
* Seleziona il pulsante **Clear**.
* Seleziona il pulsante **Update** per completare l'annullamento dell'instradamento o seleziona **Cancel** per annullare l'azione e ritornare alla schermata **Subnets**.

## Operazioni successive
{:#unroute-global-ip-next}

Dopo aver annullato l'instradamento di un IP globale da un dispositivo, l'IP globale non è più associato a tale dispositivo. Dopo il completamento del processo di annullamento dell'instradamento, tale indirizzo IP globale può essere [reinstradato](/docs/infrastructure/subnets?topic=subnets-route-a-global-ip-address-to-a-device) a qualsiasi altro dispositivo nell'account.
