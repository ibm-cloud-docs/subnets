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

# Introduzione alle sottoreti e agli IP
{:#getting-started-subnets-ips}

Le sottoreti sono una parte importante di come utilizziamo Internet e lo stesso vale anche quando utilizziamo {{site.data.keyword.cloud}}. Abbiamo una terminologia specifica per i tipi, e gli utilizzi, di sottoreti rilevati sulla nostra piattaforma. Ogni sottorete fornisce gli indirizzi IP alle risorse in modi diversi. Riscontrerai i seguenti tipi di sottoreti e, sapendone di più su ciascun tipo di sottorete, puoi comprendere come utilizzarli al meglio nella tua infrastruttura cloud.

  * Sottoreti primari - le sottoreti assegnate per soddisfare le esigenze di indirizzi IP di altri prodotti quali i server Bare Metal e le istanze del server virtuale. Queste sottoreti vengono assegnate e rimosse automaticamente.
  * Sottoreti secondarie - le sottoreti acquistate e instradate da te; vengono annullate quando non sono più necessarie. Ci sono due sottotipi:
    * Portatile - gli indirizzi IP sono disponibili per tutte le risorse su una VLAN.
    * Statica - gli indirizzi IP sono disponibili per la risorsa identificata come endpoint di instradamento.
  * Indirizzi IP globali - una modalità di funzionamento dell'instradamento peculiare che utilizza la backbone di {{site.data.keyword.cloud}} che fornisce gli indirizzi IP alla risorsa identificata come endpoint di instradamento.

Controlla ciascun tipo nel dettaglio in [Informazioni sulle sottoreti e sugli IP](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) per esaminare aspetti quali una messa a confronto tra IPv4 e IPv6 e la disponibilità di rete pubblica/privata.

Per comprendere le sottoreti e i collegamenti in sottorete in modo più generale, consulta la pagina relativa alla [sottorete ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://en.wikipedia.org/wiki/Subnetwork).
Vedrai inoltre che facciamo riferimento alle sottoreti utilizzando la [notazione CIDR ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


## Ordinazione di sottoreti
{:#ordering-subnets}

Per ordinare delle sottoreti che forniscono degli indirizzi IP aggiuntivi, attieniti alla seguente procedura:

  1. Dal tuo browser, apri il [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/){: new_window} e accedi al tuo account.
  1. Nella navigazione del Portale del Cliente, seleziona **Classic Infrastructure**. 
  1. Nella navigazione Classic Infrastructure, seleziona **Network > IP Management > Subnets**.
  1. Seleziona il link "New IP Addresses", nella parte superiore destra dell'elenco.
  1. Per iniziare il processo di ordinazione, seleziona il tipo di sottorete pubblica (Public) o privata (Private) dai pulsanti di opzione
  1. Scegli tra le opzioni IPv4 o IPv6.
  1. Per scegliere statica (Static) o IP globali (Global IP), fai clic sulla casella corrispondente. 
    1. Per IPv4, utilizza l'elenco a discesa disponibile nelle opzioni Static (Statica) o Portable (Portatile) per scegliere quanti indirizzi desideri. 
  1. Seleziona la VLAN per stabilire dove vengono instradati i nuovi indirizzi IP.
  1. Compila le restanti informazioni richieste e fai clic su **Create**.


Dopo che una sottorete è stata acquistata, il tipo e la destinazione di instradamento non possono essere modificati. Devi ordinare una nuova sottorete per acquisire un tipo o un endpoint di instradamento differenti.

### Operazioni successive 
{:#ordering-subnets-next}

Come consentito dagli eventuali processi di approvazione necessari per lo stato del tuo account, entro pochi minuti nel tuo account comparirà una nuova sottorete con la configurazione desiderata.
