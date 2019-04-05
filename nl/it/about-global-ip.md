---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Addresses, Global IP address, single IP address

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Informazioni sugli indirizzi IP globali
{:#about-global-ip-address}

Un indirizzo IP globale è una sottorete secondaria statica specializzata. Ti viene fornito come una sottorete /32 (in altre parole, un singolo indirizzo IP) che può essere instradato a qualsiasi altro indirizzo IP sul tuo account. Sono disponibili sia gli indirizzi IPv4 che quelli IPv6 e ciascun tipo deve essere instradato a un indirizzo IP della stessa versione IP. LE destinazioni di instradamento accettabili includono gli indirizzi IP primari utilizzati dai tuoi server e gli eventuali indirizzi IP di sottorete secondaria portatile. Le funzionalità peculiari di un indirizzo IP globale sono le seguenti:

  * Un instradamento su richiesta agli indirizzi IP su un account, globalmente.
  * L'indirizzo viene annunciato a internet da tutti i router edge {{site.data.keyword.cloud}}. Pertanto, i tuoi dati prendono il percorso più breve alla rete {{site.data.keyword.cloud}} e, da lì, puoi utilizzare {{site.data.keyword.cloud}} dedicato, la backbone globale per raggiungere la destinazione che hai configurato.

Gli indirizzi IP globali forniscono flessibilità. Ti consentono di spostare i carichi di lavoro tra i server, anche su data center geograficamente eterogenei. Inoltre, gli indirizzi IP globali forniscono la persistenza IP consentendo le transizioni senza la necessità di un adattamento (ad esempio, per evitare le cache DNS). La funzionalità di instradamento globale è perfetta per la transizione dei carichi di lavoro sui siti di ripristino di emergenza o per la transizione senza soluzione di continuità a una nuova distribuzione in un'area geografica che può servire meglio i tuoi destinatari.

| **Disponibilità** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rete pubblica | Sì  | Sì  |
| Rete privata  |      |      |


## Gestione degli indirizzi IP globali
{:#manage-global-ip-address}

Per gestire gli indirizzi IP globali, attieniti alla seguente procedura:

 1. Dal tuo browser, apri il [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/){: new_window} e accedi al tuo account.
 1. Nella navigazione del Portale del Cliente, seleziona **Classic Infrastructure**.
 1. Nel menu di navigazione Classic Infrastructure, seleziona **Network > IP Management > Global IP**.
 1. Vedrai elencati i tuoi indirizzi IP globali. Utilizza i filtri per restringere la tua ricerca come necessario. 
 
Potresti notare che alcune voci non hanno un valore per **Target**; questo indica che l'indirizzo IP globale non è attualmente instradato e, pertanto, non è in servizio.

### Instradamento e annullamento dell'instradamento degli indirizzi
{:#route-unroute-address}

Dopo che hai individuato il tuo indirizzo IP globale desiderato, fai clic sul suo identificativo di sottorete. Vedrai quindi una schermata che ne mostra l'instradamento corrente, se applicabile. Per instradare (inviare il traffico) a una nuova destinazione, disponi di due opzioni:

 * immettere un indirizzo IP completo oppure
 * iniziare a digitare un nome host.
 
Digitare un nome host ti consente di cercare il nome host di un server, così puoi cercarne l'indirizzo IP. Dopo che hai immesso un indirizzo IP, seleziona **Update**. Per annullare l'instradamento dell'indirizzo IP globale, seleziona **Clear**. Quando lo stato dell'input cambia e indica 'Unrouted', seleziona **Update**.

Il menu a discesa non è un elenco completo degli indirizzi IP disponibili. Immetti manualmente l'indirizzo IP desiderato, se non è disponibile nell'elenco di selezione.
{:note}

### Con che frequenza posso aggiornare?
{:#how-often-can-i-update}

È consentito solo un singolo aggiornamento dell'instradamento in corso per volta. Se provi ad aggiornare l'instradamento di un indirizzo IP globale mentre è in corso un altro aggiornamento, riceverai un errore. Aspetta che l'aggiornamento precedente venga completato, prima di riprovare.


## Come ordinare gli indirizzi IP globali
{:#how-to-order-global-ip-address}

Per ordinare degli indirizzi IP globali, attieniti alle seguenti istruzioni:

  1. Dal tuo browser, apri il [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/){: new_window} e accedi al tuo account.
  1. Nella navigazione del Portale del Cliente, seleziona **Classic Infrastructure**.
  1. Nel menu di navigazione Classic Infrastructure, seleziona **Network > IP Management > Global IP**.
  3. Fai clic sul link **New IP Addresses**.
  4. Dal menu a discesa, scegli **Global IPv4** o **Global IPv6** come necessario e fai clic su **Continue** per avviare il processo di ordine.

![Figura 1](images/1_2.png)

### Operazioni successive 
{:#global-ip-address-next}

Come consentito dagli eventuali processi di approvazione necessari per lo stato del tuo account, entro pochi minuti nel tuo account comparirà una nuova sottorete di indirizzo IP globale.

### Limite delle risorse
{:#global-ip-resource-limit}

Un account può avere cinque (5) indirizzi IP globali per ogni versione IP. Un esempio sarebbe cinque (5) indirizzi IP globali IPv4 e cinque (5) indirizzi IP globali IPv6.

## Come annullo gli indirizzi IP globali
{:#how-to-cancel-global-ip-address}

Se non hai più bisogno di un indirizzo IP globale, attieniti alla seguente procedura per annullarlo:

  1. Dal tuo browser, apri il [Portale del Cliente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/){: new_window} e accedi al tuo account.
  1. Nella navigazione del Portale del Cliente, seleziona **Classic Infrastructure**.
  1. Nel menu di navigazione Classic Infrastructure, seleziona **Network > IP Management > Global IP**.
  1. Completa gli eventuali filtri necessari per individuare l'indirizzo desiderato.
  1. Sul lato destro della voce dell'indirizzo nell'elenco degli indirizzi, viene visualizzato un cerchio con una X. Fai clic su questa icona per avviare il processo di annullamento.
