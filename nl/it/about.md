---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-04"

keywords: IP addresses , IP address, duration of your use

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Informazioni sulle sottoreti e sugli IP
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} ha una terminologia specifica per i tipi, e gli utilizzi, di sottoreti rilevati sulla nostra piattaforma. Conoscerne l'uso previsto ti aiuterà a utilizzarli in modo ottimale nella tua infrastruttura cloud.


## Tipi di sottoreti
{:#subnet-types}

### Sottoreti primarie
{:#primary-subnets}

Le sottoreti primarie vengono assegnate automaticamente da {{site.data.keyword.BluSoftlayer_notm}} e forniscono gli indirizzi IP alle risorse come necessario. Assegniamo e rimuoviamo le sottoreti primarie come necessario per soddisfare le esigenze di altri prodotti. Per tutti i server verrà eseguito il provisioning di almeno un indirizzo IP da una sottorete primaria, comunemente indicato come indirizzo IP primario. Per alcuni prodotti e alcune opzioni vengono assegnati più indirizzi IP primari.

È importante comprendere che gli indirizzi IP all'interno delle sottoreti primarie, che non sono ancora assegnati alle risorse, non sono disponibili per il tuo utilizzo. Se provi a utilizzare degli indirizzi IP non assegnati dalle sottoreti primarie, prima o poi li assegneremo inevitabilmente a un'altra risorsa. Ciò produce dei conflitti IP sulla rete e una generale interruzione del servizio. Ci riserviamo il diritto di bloccare o rendere in altro modo inutilizzabile qualsiasi indirizzo IP su una rete primaria che non viene specificamente assegnato per soddisfare le esigenze di altri prodotti.

**Consigliamo vivamente** di utilizzare **sottoreti secondarie** come tuoi indirizzi IP di servizio/applicazione rivolti all'esterno, in particolare durante la progettazione di applicazioni a più server. L'utilizzo di indirizzi IP primari assegnati ai tuoi server non comporta alcun problema. Tuttavia, a tale utilizzo manca la flessibilità derivante dal mantenere degli indirizzi noti ai tuoi servizi che sono indipendenti dall'annullamento e dall'ordinazione di server. Non c'è alcuna garanzia per quanto riguarda l'ordine con il quale vengono assegnati gli indirizzi IP primari, come ad esempio crescente, decrescente, tralasciando eventuali numeri mancanti ecc.

In nessun caso possiamo riservare degli indirizzi IP nelle sottoreti primarie per il tuo utilizzo.
{:note}

### Sottoreti secondarie
{:#secondary-subnets}

Le sottoreti secondarie ti forniscono degli indirizzi IP aggiuntivi per molte esigenze. A differenza delle sottoreti primarie, queste sottoreti appartengono a te per il tempo che ne fai uso e non verranno rimosse a meno che tu non proceda ad annullarle. Le sottoreti secondarie devono essere utilizzate quando hai bisogno di un indirizzo IP stabile che non deve dipendere da nessun altro dispositivo di calcolo specifico. Degli utilizzi di esempio includono:

  * Indirizzi IP che puoi assegnare alle tue macchine virtuali locali.
  * Più indirizzi IP di servizio distinti ospitati da un singolo server che ti consentono di identificare facilmente il traffico. Sono comunemente utilizzi con TLS e server web.
  * Un indirizzo IP di servizio collegato a DNS. Evita dei ritardi della memorizzazione in cache DNS quando sposti i carichi di lavoro a dei nuovi server (ossia, l'IP di servizio non cambierà solo perché cambia l'indirizzo IP primario di un server).
  * Configurazioni ad elevata disponibilità che utilizzano dei protocolli di indirizzo IP "mobili".

Per pervenire a tali utilizzi, e molti altri ancora, offriamo diverse opzioni di instradamento per le sottoreti secondarie. Per illustrare meglio le differenze tra le sottoreti secondarie che offriamo, faremo riferimento alla sottorete di esempio qui di seguito in ulteriori spiegazioni.

Ecco un esempio degli indirizzi IP forniti dalla sottorete 10.0.0.0/29:
```
10.0.0.0
10.0.0.1
10.0.0.2
10.0.0.3
10.0.0.4
10.0.0.5
10.0.0.6
10.0.0.7
```

#### Sottoreti statiche
{:#static-subnets}

Una sottorete statica fornisce una singola destinazione con accesso a tutti gli indirizzi IP definiti da tale sottorete. Un vantaggio derivante dall'utilizzo di una sottorete statica è che il dispositivo di destinazione può utilizzare tutti gli indirizzi IP definiti, senza subire la penalità di utilizzo degli indirizzi di rete, gateway e broadcast. Pertanto, utilizzando la nostra sottorete di esempio, sono utilizzabili tutti gli indirizzi:

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

Pertanto, se un server ha l'indirizzo IP 10.0.0.13 e hai instradato 10.0.0.0/30 staticamente a 10.0.0.13, tale server può ora associare quattro indirizzi IP aggiuntivi, ricevendo traffico su ciascuno di essi singolarmente. È importante comprendere che non viene eseguita alcuna NAT (Network Address Translation) per gli indirizzi forniti. Ogni indirizzo può essere utilizzato in modo nativo sui server e, pertanto, ognuno può essere utilizzato per scopi distinti.

| **Disponibilità** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rete pubblica | Sì  | Sì  |
| Rete privata  |      |      |

#### Sottorete portatile
{:#portable-subnet}

Una sottorete portatile fornisce i suoi indirizzi IP a tutte le risorse su una VLAN. Ciò significa che qualsiasi risorsa di calcolo sulla stessa VLAN può utilizzare qualsiasi indirizzo fornito dalla sottorete. Questa modalità di funzionamento è molto utile per gli indirizzi "mobili" su più risorse e disgiunge la sottorete da qualsiasi specifica risorsa. Una necessità delle sottoreti portatili è che non tutti gli indirizzi IP definiti dalla sottorete siano utilizzabili dai dispositivi. La meccanica della rete ha bisogno di avere disponibili per l'utilizzo alcuni degli indirizzi IP. Questi indirizzi utilizzati sono indicati come indirizzi IP di broadcast, rete e gateway. Nota gli indirizzi che sono disponibili nel nostro esempio:

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

| **Disponibilità** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rete pubblica | Sì  | Sì  |
| Rete privata  | Sì  |      |


### Indirizzi IP globali
{:#global-ip-addresses}

Per informazioni sull'offerta dell'IP globale, fai riferimento alla [Documentazione dell'IP globale](/docs/infrastructure/subnets?topic=subnets-about-global-ip-address).

| **Disponibilità** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rete pubblica | Sì  | Sì  |
| Rete privata  |      |      |


## Annullamento delle sottoreti
{:#canceling-subnets}

Se non hai più bisogno di una sottorete secondaria, attieniti alla seguente procedura per annullarla:

  1. Dal tuo browser, apri il [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/){: new_window} e accedi al tuo account.
  1. Nella navigazione del Portale del Cliente, seleziona **Classic Infrastructure**. 
  1. Dal menu di navigazione Classic Infrastructure, seleziona **Network > IP Management > Subnets**.
  1. Scegli i filtri che vuoi per individuare la sottorete desiderata.
  1. Sul lato destro della voce della sottorete nell'elenco delle sottoreti, verrà visualizzato un cerchio rosso con una X. Fai clic su questa icona per avviare il processo di annullamento.


## Considerazioni specifiche per i prodotti quando si ordinano delle sottoreti
{:#product-specific-considerations-subnets}

### Hardware Firewall (Shared)
{:#hardware-firewall-subnets}

Le sottoreti portatili non sono protette dai firewall per impostazione predefinita. Se hai bisogno di questa funzione, discutine con il tuo rappresentante delle vendite. Le sottoreti secondarie più grande di /29 non possono essere instradate attraverso questa offerta firewall.

### Trasferimento degli indirizzi IP di sottorete portatile tra i server
{:#transferring-portable-subnet-ip-between-servers}

Quando trasferisci un indirizzo IP da un server a un altro, assicurati che venga inviato un pacchetto ARP gratuito. Ciò consente ai nostri router di aggiornare la loro voce ARP e inoltrare il traffico al server corretto. Non eseguire tale operazione potrebbe produrre un ritardo di fino a 4 ore nel nuovo server che riceve il traffico per l'indirizzo trasferito.

### VRA (Virtual Router Appliance)
{:#virtual-router-appliances-subnets}

Quando ordini le sottoreti per una VLAN dietro un VRA (Virtual Router Appliance) ad alta disponibilità, assicurati che la sottorete sia configurata correttamente per consentire il fail-over tra i due dispositivi. Un'assistenza dettagliata è descritta nella documentazione relativa alla [configurazione dell'alta disponibilità del VRA](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
