---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Utilizza le sottoreti secondarie sulle macchine virtuali (VM, Virtual Machine) ospitate in modo autonomo
{:#use-secondary-subnets-self-hosted-vms}

Quando ospiti delle tue macchine virtuali, e desideri che abbiano una posizione di rilievo nella rete {{site.data.keyword.BluSoftlayer_notm}},
è necessario utilizzare le **sottoreti secondarie**. Discuteremo di un modo flessibile per fornire alle tue macchine virtuali degli indirizzi IP utilizzando uno o più host di macchina virtuale, che partecipino a configurazioni organizzate in cluster o meno. 

Nel corso di questo scenario, fai riferimento a [Informazioni sulle sottoreti](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) per maggiori dettagli sui tipi di sottoreti descritti.

Poniamo allora che hai due server Bare Metal e chiamiamoli `aunt` e `uncle`. Entrambi saranno host per la tua macchina virtuale e ciascuno già ha dei suoi indirizzi IP assegnati da una **sottorete primaria**. Hai bisogno di indirizzi IP aggiuntivi per le tue macchine virtuali. Potresti utilizzare qualsiasi tipo di sottorete secondaria per raggiungere tale obiettivo, ma noi consigliamo di utilizzare una **sottorete secondaria portatile** come origine degli indirizzi utilizzati dalle tue macchine virtuali. Una sottorete portatile fornisce sia a `aunt` che ha `uncle` l'accesso agli indirizzi IP definiti dalla sottorete. In questo modo, puoi condividere questi indirizzi IP tra entrambi i server e, se utilizzi le tecniche di migrazione per le tue macchine virtuali, puoi trasferire le macchine virtuali tra questi server senza soluzione di continuità.

Poniamo ora che hai creato due macchine virtuali, `VPS1` e `VPS2`, hai acquistato la sottorete portatile 129.42.0.0/29 e hai assegnato due indirizzi da essa alle tue macchine virtuali. L'utilizzo degli indirizzi IP sarebbe qualcosa di simile a quanto segue:

129.42.0.0/29 - Sottorete secondaria portatile
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

Poniamo ora che desideri che VPS1 abbia più indirizzi IP per separare i servizi che sta fornendo. Puoi assolutamente assegnare più indirizzi dalla sottorete 129.42.0.0/29, ma sarebbe opportuno che utilizzassi tale sottorete solo per portare online le macchine virtuali, non per i loro servizi. Hai due opzioni: 1) acquistare un'altra sottorete portatile 2) acquistare una sottorete statica. Se ricordi quanto indicato nella descrizione delle sottoreti portatili e in quella delle sottoreti statiche in [Informazioni sulle sottoreti](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) saprai che, se da una parte le sottoreti portatili forniscono flessibilità, dall'altra non ti danno accesso a tutti gli indirizzi IP. Se hai bisogno solo, poniamo, di quattro indirizzi IP aggiuntivi, l'acquisto di una sottorete statica è un'opzione efficiente. Proviamo con questo.

Acquisti una sottorete statica e ricevi 129.42.0.100/30. Durante l'acquisto, ne esegui l'instradamento a 129.42.0.3 o VPS1 in questo scenario. Tale operazione ti fornisce tutti e quattro gli indirizzi IP da utilizzare su qualsiasi server stia rispondendo a 129.42.0.3, (ricorda che attualmente è VPS1) ma puoi trasferire 129.42.0.3 a VPS2 in qualsiasi momento e questi quattro nuovi indirizzi IP da 129.42.0.100/30 si trasferiranno con esso. Guardiamo quindi di nuovi l'utilizzo degli indirizzi IP:

129.42.0.0/29 - Sottorete secondaria portatile
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

129.42.0.100/30 - Sottorete secondaria statica
```
129.42.0.100 – 129.42.0.3 (aka VPS1)
129.42.0.101 – 129.42.0.3 (aka VPS1)
129.42.0.102 – 129.42.0.3 (aka VPS1)
129.42.0.103 – 129.42.0.3 (aka VPS1)
```

Ricapitolando, abbiamo utilizzato una sottorete portatile per rendere disponibili degli indirizzi IP a tutti gli host di macchina virtuale e abbiamo quindi reso disponibili degli indirizzi IP aggiuntivi a una macchina virtuale utilizzando una sottorete statica.Potresti tranquillamente avere utilizzato indirizzi dalla sottorete portatile originale o semplicemente aggiunto un'altra rete portatile. Speriamo che questo scenario illustri che non solo è possibile instradare le sottoreti statiche agli indirizzi IP sulle sottoreti portatili ma che farlo è in effetti efficiente e utile.
