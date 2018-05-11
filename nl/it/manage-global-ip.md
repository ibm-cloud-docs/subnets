---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Gestisci gli indirizzi IP globali 

Puoi gestire i tuoi indirizzi IP globali nella schermata **Subnets**. 

1. Dal tuo browser, apri [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com/){: new_window} e accedi al tuo account.
2. Nella navigazione del portale del cliente, seleziona **Network > IP Management > Subnets**.
3. Nel menu a discesa, scegli **Global IPv4** (o IPv6) per filtrare l'elenco di sottoreti in modo da visualizzare solo gli IP globali.
4. Fai clic sull'IP globale che vuoi gestire.
 
  **Nota: un IP globale è un indirizzo IP statico che può essere instradato a qualsiasi server all'interno di una rete IBM Cloud. L'offerta corrente di indirizzo IP statico
  può essere instradata solo a un indirizzo IP all'interno dello stesso data center, ma gli indirizzi IP globali non condividono
  questa limitazione.**

5. Nella pagina di gestione dell'indirizzo IP, immetti l'indirizzo IP del server a cui desideri instradare l'indirizzo IP globale e inserisci tutte le note applicabili e seleziona **Update**.

![Figura 2](images/2_1.png)

## Aggiungi un IP globale al tuo server 

Prima che il tuo server accetti il traffico di un IP globale, tale IP deve essere aggiunto correttamente al sistema. Ogni sistema richiede comandi leggermente differenti, per questo motivo vengono mostrati nelle successive poche sezioni.

### Per i server Linux:

**Red Hat/CentOS**

1. Modifica (vim o nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* Aggiungi le seguenti righe:
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. Modifica `/etc/network/interfaces`

* Aggiungi le seguenti righe:

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

Se il tuo sistema non funziona correttamente, aggiungi invece le seguenti righe, sostituendo il # con il numero successivo disponibile:

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### Per i server Windows

1. Passa a: **Start -> Control Panel -> Network Connections -> Local Area Connection (Public) (properties)**.
* Seleziona: **Internet Protocol (TCP/IP)** e fai clic su **Properties -> Advanced**.
* Seleziona **Add** nella sezione degli indirizzi IP e immetti l'indirizzo IP e la maschera della sottorete.
* Dopo aver completato questa attività, fai semplicemente clic su "OK" per tornare al desktop.

Per verificare che le tue impostazioni siano state applicate, apri un prompt DOS selezionando **Start -> Run -> "cmd"** ed esegui il comando

```
        > ipconfig /all
```

**Note:**

* Se già hai un file `eth1:1` nel tuo server come nel precedente esempio, incrementa l'ultimo numero al numero intero successivo disponibile.
* La modifica di un indirizzo IP globale a un nuovo server o VSI richiede fino a cinque minuti per essere effettiva. 
* Nella rete IBM Cloud, la modifica alla rotta necessità di meno di 1 minuto per l'aggiornamento.
* Gli IP globali non funzionano per i programmi di bilanciamento del carico locali.
* Gli IP globali sono distribuiti da una sottorete univoca, gli IP del cliente esistenti non possono essere convertiti o utilizzati come IP globali.
* Di per sé, gli IP globali non hanno una soluzione di failover automatica, per l'assenza dei controlli di integrità; tuttavia, un indirizzo IP globale può essere utilizzato come un componente di un ambiente di failover, se vuoi aggirare la propagazione DNS.
