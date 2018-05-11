---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Informazioni sulle sottoreti e gli IP

IBM Cloud fornisce varie opzioni per l'ordine delle sottoreti e degli indirizzi IP, per cui puoi progettare un'infrastruttura che soddisfa i tuoi bisogni. Comprendere come funzionano le sottoreti e sapere i loro scopi di utilizzo previsti, ti aiuterà a raggiungere esattamente quello di cui hai bisogno.

## Tipi di sottoreti

Avendo ulteriori informazioni su ogni tipo di sottorete, puoi comprendere come utilizzarle al meglio nella tua infrastruttura cloud.

### Sottoreti primarie

Le sottoreti primarie vengono assegnate automaticamente da {{site.data.keyword.BluSoftlayer_notm}} nelle VLAN, allo scopo di fornire i servizi e il provisioning automatizzato alle tue VLAN. Queste sottoreti non sono disponibili per i servizi o gli indirizzi IP secondari, perché vengono utilizzate dai nostri sistemi automatizzati. Le sottoreti primarie vengono assegnate ai nuovi server automaticamente. Se tenti di utilizzarle sui tuoi server, potresti causare un conflitto con l'indirizzo IP, nel qual caso ti verrà richiesto di rimuovere l'indirizzo IP.

**Nota: non possiamo riservare gli indirizzi IP nelle sottoreti primarie per il tuo utilizzo.**

### Sottoreti portatili

Le sottoreti portatili possono essere ordinate tramite il [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com/) Queste sottoreti normalmente forniscono gli indirizzi della macchina virtuale (VM) o gli indirizzi IP secondari per i server o le interfacce secondarie. Queste sottoreti possono anche essere utilizzate per il cluster o gli indirizzi IP HA, perché vengono tracciate dai nostri router tramite ARP. Possono essere spostate facilmente. Il formato standard di queste sottoreti include i propri rete, gateway e indirizzo di broadcast--pertanto, tre dei suoi indirizzi IP saranno immediatamente utilizzati.

### Sottoreti statiche

Le sottoreti statiche sono un altro tipo di sottorete che può essere ordinato tramite il [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com/network/subnets/order). Le sottoreti statiche sono normalmente utilizzate per i server web, l'email o per altri servizi ospitati su un server, che richiedono diversi indirizzi IP aggiuntivi per consentire le connessioni. Le sottoreti statiche sono univoche, perché devono specificare un altro indirizzo IP esistente che è già assegnato a un server al quale vene instradata direttamente la sottorete. Hai la flessibilità di instradare la sottorete come desideri e puoi spostarla in server differenti--ma per far ciò, devi modificare l'ubicazione di instradamento.

### Indirizzi IP globali

Per informazioni sull'offerta dell'IP globale, fai riferimento alla [Documentazione dell'IP globale](about-global-ip.html).

## Considerazioni da fare per l'account con sottoreti differenti

### Firewall hardware

Le sottoreti portatili non sono protette dai firewall per impostazione predefinita. Se hai bisogno di questa funzione, discutine con il tuo rappresentante delle vendite. Le sottoreti che devono essere protette non possono superare una sottorete /29.

### Trasferimento degli IP portatili tra i server

Quando trasferisci un IP portatile da un server a un altro, assicurati che venga inviato un pacchetto ARP gratuito in modo che i nostri router possano aggiornare la propria voce ARP e inoltrino l'indirizzo IP aggiornato al server corretto. Se non invii il pacchetto ARP, sono necessarie 4 ore o più perché l'indirizzo IP inizi a rispondere correttamente.

### Gateway Vyatta

Quando ordini le sottoreti per una VLAN dietro a un gateway Vyatta, assicurati che venga aggiunta correttamente alla configurazione di Vyatta. Se utilizzi VRRP per HA, assicurati che la sottorete sia configurata correttamente per consentire il failover tra i due dispositivi gateway. Se hai bisogno di ulteriore assistenza con queste attività, fai riferimento a questi due articoli sulla configurazione del gateway Vyatta:

 * [Network Gateway Devices Vyatta](../network-gateways/network-gateway-devices-vyatta.html)

 * [Vyatta High Availability Configuration](../vyatta/vyatta-high-availability-configuration.html)
 
 ### Annullamento delle sottoreti
 
Le sottoreti che vengono assegnate automaticamente a un account per l'adempimento degli ordini del dispositivo sono soggette al ritiro automatico quando non viene più fatto loro riferimento. Le sottoreti che vengono ordinate separatamente possono essere annullate in qualsiasi momento.
