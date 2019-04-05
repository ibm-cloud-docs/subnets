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

# Häufig gestellte Fragen
{:#subnets-faq}

## Was bedeutet `Primäre IP-Adresse nur für zukünftigen Server` beim Anzeigen der IP-Adressen eines Teilnetzes?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

Primäre Teilnetze werden von {{site.data.keyword.BluSoftlayer_notm}} zu anderen von Ihnen bestellte Ressourcen zugeordnet oder von diesen entfernt, zum Beispiel Bare-Metal-Server oder virtuelle Serverinstanzen. Somit wird nicht einfach eine IP-Adresse gleichzeitig zugeordnet, sondern ein Teilnetz. Das bedeutet, dass es manchmal zusätzlichen Spielraum für zukünftige Ressourcen gibt. Diese Bezeichnung gibt an, dass diese Adressen von zukünftigen Ressourcen verwendet werden. Erläuterungen dazu, warum diese IP-Adressen nicht verwendbar sind, finden Sie unter der Frage **Kann ich die anderen IP-Adressen verwenden, die von den angezeigten primären Teilnezten definiert werden?**.


## Kann ich die anderen IP-Adressen verwenden, die in den angezeigten primären Teilnezten definiert sind?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

Nein. Uns ist bewusst, dass Ihnen die primären Teilnetze angezeigt werden, die von {{site.data.keyword.BluSoftlayer_notm}} als weiteres Teilnetz zugeordnet werden, aber wie in [Informationen zu Teilnetzen](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) beschrieben, werden den Ressourcen von primären Teilnetzen bei Bedarf IP-Adressen bereitgestellt. Wir ordnen primäre Teilnetze so zu und entfernen diese auch so wieder, dass die Anforderungen anderer Produkte erfüllt sind. Wenn Sie versuchen, nicht zugeordnete IP-Adressen aus primären Teilnetzen zu verwenden, werden sie an einem bestimmten Punkt zwangsläufig einer anderen Ressource zugeordnet. Dies führt zu IP-Konflikten im Netz und allgemeinen Serviceunterbrechungen. Wir behalten uns das Recht vor, jede beliebige IP-Adresse in einem primären Teilnetz zu blockieren und unbrauchbar zu machen, die während der Auftragserfüllung für weitere Produkte nicht ausdrücklich zugewiesen wurde. Sie sollten **sekundäre Teilnetze** für alle zusätzlichen Anforderungen an IP-Adressen verwenden; es wird dringend empfohlen, sie für Anforderungen der Anwendungen und Serviceadressen zu verwenden. Sekundäre Teilnetze sind sehr viel flexibler und werden auf Ihrem Konto verwaltet, solange Sie Eigner der Teilnetze sind. 


## Kann ich beim Bestellen angeben, welches Teilnetz ich für mein Gerät verwenden möchte?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

Ja, während des Bestellablaufs kann ein bestimmtes Teilnetz angegeben werden. Beim Bestellen eines Geräts ist diese Option am Ende des Bestellformulars verfügbar. Nach der Auswahl eines privaten VLANs wird eine Liste der primären Teilnetze angezeigt, die an dieses VLAN weitergeleitet werden. Sie können das gewünschte Teilnetz auswählen. Derselbe Prozess kann für das öffentliche VLAN und und das Teilnetz wiederholt werden.

Es ist wichtig, darauf hinzuweisen, dass durch die Übermittlung der Bestellung **nicht garantiert werden kann**, dass eine IP-Adresse im angeforderten Teilnetz verfügbar ist. Wenn keine Adressen verfügbar sind, werden Sie kontaktiert, um das weitere Vorgehen festzulegen. Damit Sie mit {{site.data.keyword.BluSoftlayer_notm}} nur die besten Erfahrungen machen, sollten Sie auf die Auswahl eines Teilnetzes für typische Verwendungen verzichten.


## Wie gehe ich vor, wenn ich über keine weiteren IP-Adressen verfüge?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

Dieser Fall wird nicht eintreten. Wir ordnen primäre Teilnetze automatisch zu, damit Ihnen mehr IP-Adressen zur Verfügung stehen und Sie ausreichend Rechenleistung kaufen können. Sie müssen sich um nichts kümmern. Wenn Sie jedoch der Meinung sind, dass Sie mehr IP-Adressen für lokale virtuelle Maschinen oder für die Trennung von Anwendungen benötigen, lesen Sie die Informationen im Abschnitt **Sekundäre Teilnetze** in [Informationen zu Teilnetzen](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).


## Wie weise ich einer Rechenressource mehr IP-Adressen zu?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

Zunächst ist der Kauf eines **sekundären Teilnetzes** sinnvoll; Informationen zu den unterschiedlichen Typen eines solchen Teilnetzes finden Sie in [Informationen zu Teilnetzen](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips). Wenn Sie ein Teilnetz an die gewünschte IP-Adresse oder das gewünschte VLAN weiterleiten, ist es sinnvoll, sich in der konkreten Dokumentation für die Datenverarbeitung darüber zu informieren, wie die neuen IP-Adressen konfiguriert werden:

  * [Zuweisung von IP-Adressen für Bare-Metal-Server](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Zuweisung von IP-Adressen für virtuele Serverinstanzen](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## Was bedeutet `Reserviert für HSRP` beim Anzeigen der IP-Adressen eines Teilnetzes?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

An einer abnehmenden Anzahl von Standorten werden von {{site.data.keyword.BluSoftlayer_notm}} Router mit einer Technik verwendet, die als 'Hot Router Standby Protocol' oder 'HSRP' bezeichnet wird. Die Art und Weise, wie sie verwendet wird, wirkt sich besonders auf die IP-Adressen aus, die für ***portierbare sekundäre Teilnetze*** verfügbar sind; dies bedeutet, dass Sie den Zugriff auf zwei zusätzliche Adressen an diesen Standorten verlieren werden. Wie aus der Formulierung 'Reserved for HSRP' (Für HSRP reserviert) hervorgeht, sind diese IP-Adressen für die Verwendung durch die HSRP-Technik reserviert. Derselbe Router kann sogar über Teilnetze mit Reservierung und Teilnetze ohne Reservierungen verfügen. Versuchen Sie wie bei jedem IP-Konflikt, diese Adressen nicht zu verwenden, da sonst das Risiko besteht, dass der Datenverkehr im gesamten Teilnetz beeinträchtigt wird.

