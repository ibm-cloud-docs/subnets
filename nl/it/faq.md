---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Primary IP, IP address, subnet's IP

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}
{:faq: data-hd-content-type='faq'}

# Domande frequenti (FAQ, Frequently Asked Questions)
{:#subnets-faq}

## Cosa significa `Primary IP for future server only` quando guardo gli indirizzi IP di una sottorete?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

Le sottoreti primarie sono assegnate e rimosse come necessario da {{site.data.keyword.BluSoftlayer_notm}} per le altre risorse che hai ordinato, come server Bare Metal o istanze del server virtuale. Non assegniamo semplicemente un singolo indirizzo IP per volta, bensì una sottorete. Ciò significa che a volte c'è spazio aggiuntivo per future risorse. Questa designazione sta indicando che questi indirizzi verranno utilizzati da future risorse. Vedi la domanda "**Posso utilizzare gli altri indirizzi IP definiti dalle sottoreti primarie che vedo?**" per una spiegazione del motivo per cui non dovresti considerare tali indirizzi IP come utilizzabili.


## Possono utilizzare gli altri indirizzi IP definiti dalle sottoreti primarie che vedo?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

No. Ci rendiamo conto che vedi le sottoreti primarie assegnate da {{site.data.keyword.BluSoftlayer_notm}} come qualsiasi altra sottorete ma, come descritto in [Informazioni sulle sottoreti](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), le sottoreti primarie forniscono gli indirizzi IP alle risorse su richiesta. Assegniamo e rimuoviamo le sottoreti primarie come ci è necessario per soddisfare le esigenze di altri prodotti. Se provi a utilizzare degli indirizzi IP non assegnati dalle sottoreti primarie, prima o poi li assegneremo inevitabilmente a un'altra risorsa. Ciò produce dei conflitti IP sulla rete e una generale interruzione del servizio. Ci riserviamo il diritto di bloccare o rendere in altro modo inutilizzabile qualsiasi indirizzo IP su una rete primaria che non viene specificamente assegnato per soddisfare le esigenze di altri prodotti.Devi utilizzare le **sottoreti secondarie** per tutte le esigenze di indirizzi IP aggiuntivi e ti incoraggiamo vivamente a utilizzarle per le tue esigenze di indirizzo di servizio/applicazione. Le sottoreti secondarie sono molto più flessibili e sono mantenute sul tuo account per tutto il tempo che le possiedi.


## C' è un modo per specificare quale sottorete desidero utilizzare per il mio dispositivo quando lo ordino?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

Sì, durante il processo di ordinazione è possibile indicare una specifica sottorete. Quando ordini un dispositivo, questa opzione è disponibile alla fine del modulo d'ordine. Dopo la selezione di una VLAN privata, viene presentato un elenco delle sottoreti primarie instradate a tale VLAN. Puoi selezionare una sottorete desiderata. Lo stesso processo può essere ripetuto per la sottorete e la VLAN pubblica.

È importante notare che l'inoltro dell'ordine **non garantisce** che un indirizzo IP sia disponibile nella sottorete richiesta. Se non ci sono indirizzi disponibili, verrai contattato per determinare una linea di azione. Per un'esperienza {{site.data.keyword.BluSoftlayer_notm}} ottimale, si sconsiglia la selezione di una sottorete per gli usi tipici.


## Ho esaurito gli indirizzi IP; e ora?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

Questo non succederà. Assegniamo automaticamente le sottoreti primarie per rendere disponibili più indirizzi IP per soddisfare le esigenze dei tuoi acquisti di calcolo. Non hai bisogno di gestire nulla. Tuttavia, se ritieni che hai bisogno di più indirizzi IP ad esempio per le macchine virtuali locali o per separare le applicazioni, leggi **Sottoreti secondarie** in [Informazioni sulle sottoreti](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).


## Come assegno più indirizzi IP a una risorsa di calcolo?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

Per prima cosa, vorrai acquistare una **sottorete secondaria**; ci sono diversi tipi, quindi leggi con attenzione [Informazioni sulle sottoreti](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips). Una volta che disporrai di una sottorete instradata all'indirizzo IP o alla VLAN desiderati, vorrai fare riferimento alla specifica documentazione relativa al calcolo per la modalità di configurazione dei tuoi nuovi indirizzi IP:

  * [Assegnazione di un indirizzo IP a un server Bare Metal](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Assegnazione di un indirizzo IP a un'istanza del server virtuale](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## Cosa significa `Reserved for HSRP` quando guardo gli indirizzi IP di una sottorete?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

In un numero in via di diminuzione di ubicazioni, {{site.data.keyword.BluSoftlayer_notm}} ha dei router che utilizzano una tecnica nota come HSRP (Hot Router Standby Protocol). In modo specifico, il modo in cui se ne fa uso si ripercuote sugli indirizzi IP disponibili per le ***sottoreti secondarie portatili***, il che vuol dire che perderai l'accesso a due indirizzi aggiuntivi in queste ubicazioni. Come indicato dalla designazione "Reserved for HSRP", questi indirizzi sono riservati per soddisfare le esigenze di HSRP. Puoi anche avere delle sottoreti sullo stesso router, alcune con e altre senza tali condizioni di riservato. Come per qualsiasi conflitto di IP, non provare a utilizzare questi indirizzi altrimenti rischi delle ripercussioni sul traffico nell'intera sottorete.

