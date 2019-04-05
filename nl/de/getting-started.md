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

# Einführung in Teilnetze und IPs
{:#getting-started-subnets-ips}

Teilnetze sind ein wichtiger Teil der Internetnutzung, auch bei Verwendung von {{site.data.keyword.cloud}}. Für die Typen und Nutzungen von Teilnetzen auf einer Plattform wird eine bestimmte Terminologie verwendet. Von jedem Teilnetz werden den Ressourcen auf unterschiedliche Arten IP-Adressen bereitgestellt. Die folgenden Teilnetztypen stehen zur Verfügung; wenn Sie sich mit den verschiedenen Typen von Teilnetzen vertraut machen, verstehen Sie besser, wie Sie sie in Ihrer Cloudinfrastruktur optimal einsetzen können.

  * Primäre Teilnetze - Teilnetze, die zugeordnet werden, um die IP-Adressierungsanforderungen weiterer Produkte wie Bare-Metal-Server und virtuelle Serverinstanzen zu erfüllen. Diese Teilnetze werden automatisch zugeordnet und entfernt.
  * Sekundäre Teilnetze - Teilnetze, die von Ihnen gekauft und weitergeleitet werden; sie werden storniert, wenn sie nicht mehr benötigt werden. Zwei Untertypen stehen zur Verfügung:
    * Portierbar - Die IP-Adressen stehen allen Ressourcen in einem VLAN zur Verfügung.
    * Statisch - Die IP-Adressen stehen der Ressource zur Verfügung, die als Routing-Endpunkt angegeben ist.
  * Globale IP-Adressen - Ein eindeutiges Routing-Verhalten, von dem der Backbone von {{site.data.keyword.cloud}} verwendet wird, um IP-Adressen der Ressource bereitzustellen, die als Routing-Endpunkt angegeben ist.

Detaillierte Informationen zu jedem Typ sowie Hinweise zum Unterschied zwischen IPv4 und IPv6 und der Verfügbarkeit öffentlicher und privater Netze finden Sie im Abschnitt [Informationen zu Teilnetzen und IPs](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).

Allgemeine Erläuterungen zu Teilnetzen und zur Teilnetzadressierung finden Sie unter [Subnetwork ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://en.wikipedia.org/wiki/Subnetwork). Außerdem werden Sie feststellen, dass auf Teilnetze mit einer [CIDR-Notation ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) verwiesen wird.


## Teilnetze bestellen
{:#ordering-subnets}

Führen Sie die folgenden Schritte aus, um Teilnetze zu bestellen, von denen zusätzliche IP-Adressen bereitgestellt werden:

  1. Öffnen Sie in Ihrem Browser das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/){: new_window} und melden Sie sich bei Ihrem Konto an.
  1. Wählen Sie in der Navigation im Kundenportal **Klassische Infrastruktur** aus. 
  1. Wählen Sie in der Navigation 'Klassische Infrastruktur' **Netz > IP-Verwaltung > Teilnetze** aus.
  1. Wählen Sie den Link 'Neue IP-Adressen' in der rechten oberen Ecke der Liste aus.
  1. Wählen Sie zum Starten des Bestellablaufs in den Optionsfeldern den Teilnetztyp 'Öffentlich' oder 'Privat' aus.
  1. Wählen Sie die Option 'IPv4' oder 'IPv6' aus.
  1. Klicken Sie zum Auswählen statischer IPs oder globaler IPs auf das entsprechende Kästchen. 
    1. Wählen Sie bei Auswahl von 'IPv4' in der für die Optionen 'Statisch' bzw. 'Portierbar' verfügbaren Dropdown-Liste die Anzahl der gewünschten Adressen aus. 
  1. Wählen Sie das VLAN aus, das an der Position erstellt werden soll, an die die neuen IP-Adressen weitergeleitet werden.
  1. Geben Sie die restlichen erforderlichen Informationen an und klicken Sie auf **Erstellen**.


Nach dem Kauf eines Teilnetzes können der Typ und das Routing-Ziel nicht mehr geändert werden. Sie müssen ein neues Teilnetz bestellen, um einen anderen Typ oder Routing-Endpunkt zu erhalten.

### Nächste Schritte
{:#ordering-subnets-next}

Falls keine Freigabeprozesse für Ihren Kontostatus erforderlich sind, wird in wenigen Momenten ein neues Teilnetz mit der gewünschten Konfiguration für Ihr Konto angezeigt.
