---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Introduzione alle sottoreti e agli IP

I clienti IBM Cloud possono ordinare sottoreti statiche, portatili private e pubbliche o globali composte da indirizzi IPv4 e IPv6 in qualsiasi momento. 

Per ordinare le sottoreti e gli IP:

1. Dal tuo browser, apri [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com/){: new_window} e accedi al tuo account.
2. Nella navigazione del portale del cliente, seleziona **Network > IP Management > Subnets**.
3. Per avviare il processo di ordine, seleziona il tipo appropriato di sottorete dal menu a discesa. 

**Nota che le sottoreti sono create per i clienti caso per caso, che implica un processo accurato che cerca un rapporto da IP a server.**

## Informazioni sui blocchi IP portatile e statico
{{site.data.keyword.BluSoftlayer_notm}} al momento offre 2 tipi differenti di blocchi IP: statico e portatile. Sono progettati per essere utilizzati in modi differenti. Viene fornita una breve descrizione con ogni tipo di blocco, che include inoltre una sezione sull'utilizzo di questi indirizzi IP in una macchina virtuale.
 
### Blocco IP statico
Il tipo di blocco IP più comunemente utilizzato nella rete {{site.data.keyword.BluSoftlayer_notm}} è il blocco IP statico. Un blocco IP statico viene instradato a un IP specifico nella nostra rete. Ogni indirizzo IP in un blocco statico è utilizzabile sul server. Un vantaggio principale di utilizzare un blocco IP statico è che non perdi i primi due e ultimi indirizzi IP--tutti gli indirizzi nel blocco sono utilizzabili. 

Questo è un esempio di un piccolo blocco IP statico (192.168.0.4/30), che indica che tutti e 4 gli IP in questo blocco saranno disponibili nel server:
```
·192.168.0.4 – Usable Address
·192.168.0.5 – Usable Address
·192.168.0.6 – Usable Address
·192.168.0.7 – Usable Address
```
Con un blocco portatile, solo un singolo IP da questo blocco sarà effettivamente utilizzabile sul server, perché la rete, il gateway e gli indirizzi IP di broadcast sono stati associati direttamente alla VLAN.

Nota: una tecnica speciale ti permette di utilizzare tutti gli IP, perché l'utilizzo della maschera della sottorete assegnata ti permetterà soltanto di utilizzarli tutti tranne uno (l'IP di broadcast). Per utilizzare tutti gli IP, utilizza una maschera della sottorete di 255.255.255.255, invece di perdere l'IP di broadcast.

### Blocco IP portatile
Un blocco IP portatile può essere utilizzato su più server all'interno di una sola VLAN contemporaneamente. Offriamo due tipi differenti di blocchi IP:

 * Il primo tipo di blocco IP portatile è un blocco “Instradato alla VLAN”. Questo è un blocco IP statico che viene instradato a una VLAN completa anziché a un indirizzo IP specifico.
 * L'altro tipo di blocco IP portatile è un blocco “Secondario sulla VLAN”, che è progettato per essere utilizzato in un ambiente virtuale.
 
La differenza principale tra i due è il numero di IP disponibili per l'utilizzo. 

Un **blocco Instradato alla VLAN**, come un blocco statico, ti fornisce l'accesso a tutti gli IP all'interno del blocco. Tuttavia, un blocco **Secondario sulla VLAN** richiede che la rete, il gateway e gli IP di broadcast vengano associati direttamente alla VLAN, che li rende inutilizzabili. Un blocco **Instradato alla VLAN** dovrebbe venire utilizzato quando l'utente vuole utilizzare un IP all'interno di tale blocco su un qualsiasi server nella VLAN in qualsiasi momento. Il blocco **Secondario sulla VLAN** viene utilizzato insieme alla macchina virtuale. Ulteriori informazioni sui blocchi **Secondari sulla VLAN** vengono fornite nella sezione _IP per le macchine virtuali_.

Quando ordini un blocco IP portatile, per impostazione predefinita {{site.data.keyword.BluSoftlayer_notm}} ti fornirà un blocco **Secondario sulla VLAN**. Se desideri che questo blocco venga convertito in un blocco **Instradato alla VLAN** da utilizzare nei tuoi server in una sola VLAN, apri un ticket di supporto con la richiesta che questo blocco venga convertito in un blocco **Instradato alla VLAN** 

### POD che supportano HSRP (Hot Standby Router Protocol)

È importante notare che i POD che usufruiscono del HSRP (Hot Standby Router Protocol) utilizzano due ulteriori indirizzi IPv4: uno per l'interfaccia della VLAN di ogni router interessato e uno per ogni blocco **Secondario sulla VLAN** configurato per la VLAN. Molti dei nostri POD supportano HSRP.

Il seguente è un esempio di un blocco **Secondario sulla VLAN** (192.168.0.4/28) che viene utilizzato per più macchine virtuali in un POD HRSP.
```
192.168.0.0 –  Network Address
192.168.0.1 –  Gateway Address
192.168.0.2 –  Router A Vlan Interface
192.168.0.3 –  Router B Vlan Interface
192.168.0.4 –  VPS1
192.168.0.5 –  VPS2
192.168.0.6 –  VPS3
192.168.0.8 –  VPS4
192.168.0.9 –  VPS5
192.168.0.10 – VPS6
192.168.0.11 – VPS7
192.168.0.12 – VPS8
192.168.0.13 – VPS9
192.168.0.14 – VPS10
192.168.0.15 – Broadcast Address
```
 
### IP per le macchine virtuali
Le macchine virtuali (VM) vengono comunemente utilizzate nei carichi di lavoro cloud, alcune volte denominate "istanze" o "calcoli". Questa sezione fornisce le informazioni su quale tipo di blocchi IP deve essere utilizzato in una VM. Le informazioni qui fornite si basano su Microsoft Hyper-V.

Ogni VM collegata alla rete {{site.data.keyword.BluSoftlayer_notm}} in un ambiente virtuale richiede un indirizzo IP primario da un blocco di IP portatili, perché Hyper-V richiede che ogni VM fornisca una rete, un gateway e un indirizzo di broadcast nella stessa sottorete dell'IP primario assegnato a tale VM. Un vantaggio della nostra configurazione di rete è che può essere utilizzato un solo blocco **Secondario sulla VLAN** per più macchine virtuali. 

Il seguente è un esempio di un blocco **Secondario sulla VLAN** (192.168.0.4/29) che viene utilizzato per più macchine virtuali: 
```
·192.168.0.0 – Network Address
·192.168.0.1 – Gateway Address
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Broadcast Address
```
Come mostrato dall'esempio, questo blocco **Secondario sulla VLAN** fornisce 5 indirizzi IP utilizzabili degli 8 indirizzi IP nel blocco, associati con 3 differenti macchine virtuali. Questa configurazione pone una domanda: “Come aggiungo più IP a una macchina virtuale se vengono utilizzati tutti gli IP nel blocco portatile?”. Questo problema può essere risolto tramite l'utilizzo di un blocco statico o un blocco portatile **Instradato alla VLAN**.

Per utilizzare un blocco statico in una VM, devi prima ordinare un nuovo blocco IP statico dal portale del cliente. Come hai ordinato questo blocco, puoi selezionare l'indirizzo IP a cui desideri venga instradato. Selezionando l'indirizzo IP assegnato alla VM, il nuovo blocco sarà instradato specificatamente a tale VM. Dopo puoi associare il nuovo blocco di IP direttamente a tale VM e iniziare ad utilizzarli immediatamente.

In alternativa, se desideri che il nuovo blocco sia utilizzabile da più di una macchina virtuale, utilizza un blocco **Instradato alla VLAN**. Un blocco **Instradato alla VLAN** è disponibile acquistando un blocco IP portatile dal portale e selezionando la VLAN nell'indirizzo IP in cui risiede la VM. Dopo aver creato il blocco IP, diventa disponibile per l'utilizzo su qualsiasi server o VM su tale VLAN.
