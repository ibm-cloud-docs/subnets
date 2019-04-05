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

# Informationen zu Teilnetzen und IPs
{:#about-subnets-and-ips}

Für {{site.data.keyword.BluSoftlayer_notm}} wird eine spezielle Terminologie für die Typen und Verwendungen der Teilnetze auf den Plattformen verwendet. Wenn Sie mit dem bestimmungsgemäßen Gebrauch vertraut sind, verstehen Sie am besten, wie Sie diese in Ihrer Cloudinfrastruktur verwenden.


## Typen von Teilnetzen
{:#subnet-types}

### Primäre Teilnetze
{:#primary-subnets}

Primäre Teilnetze werden von {{site.data.keyword.BluSoftlayer_notm}} automatisch zugeordnet und stellen die IP-Adressen bereit, die bei Bedarf zum Erfüllen der Anforderungen der Ressourcen erforderlich sind. Primäre Teilnetze werden abhängig von der Nutzung durch andere Produkte zugeordnet und entfernt. Alle Server werden mit mindestens einer IP-Adresse von einem primären Teilnetz bereitgestellt; sie wird im Allgemeinen als primäre IP-Adresse bezeichnet. Bei einigen Produkten und Optionen werden auch mehrere primäre IP-Adressen zugeordnet.

Es ist wichtig zu verstehen, dass IP-Adressen in primären Teilnetzen, die noch nicht Ressourcen zugeordnet sind, nicht zur Verwendung verfügbar sind. Wenn Sie versuchen, nicht zugeordnete IP-Adressen aus primären Teilnetzen zu verwenden, werden diese an einem bestimmten Punkt zwangsläufig einer anderen Ressource zugeordnet. Dies führt zu IP-Konflikten im Netz und allgemeinen Serviceunterbrechungen. Wir behalten uns das Recht vor, jede beliebige IP-Adresse in einem primären Teilnetz zu blockieren und unbrauchbar zu machen, die während der Auftragserfüllung für weitere Produkte nicht ausdrücklich zugewiesen wurde.

Es wird **dringend empfohlen**, die **sekundären Teilnetze** als IP-Adressen für externe zugängliche Services bzw. Anwendungen zu verwenden; dies gilt insbesondere für das Entwickeln von Anwendungen mit mehreren Servern. Die Verwendung primärer IP-Adressen, die Ihren Servern zugeordnet sind, ist völlig in Ordnung. Darunter leidet jedoch die Flexibilität bei der Verwaltung der bekannten Adressen für die Services, die von Serverstornierungen und -bestellungen unabhängig sind. Es wird keine Gewähr für die Reihenfolge der Zuweisung von primären IP-Adressen übernommen, zum Beispiel für eine aufsteigende oder absteigende Reihenfolge oder das Überspringen von Lücken.

Wir können unter keinen Umständen IP-Adressen in primären Teilnetzen für Ihre Verwendung reservieren.{:note}

### Sekundäre Teilnetze
{:#secondary-subnets}

Sekundäre Teilnetze bieten zusätzliche IP-Adressen für viele Anforderungen. Im Gegensatz zu primären Teilnetzen sind Sie für die Dauer der Verwendung dieser Teilnetze ihr Eigner; die Teilnetze werden erst entfernt, wenn Sie diese stornieren. Sekundäre Teilnetze sollten verwendet werden, wenn Sie eine stabile IP-Adresse benötigen, die nicht von einer bestimmten Recheneinheit abhängig sein darf. Hierzu gehören unter anderem die folgenden Beispiele:

  * IP-Adressen, die Sie Ihren eigenen, lokalen, virtuellen Maschinen zuordnen können.
  * Mehrere unterschiedliche Service-IP-Adressen, die auf einem einzigen Server gehostet werden und Ihnen die einfache Identifizierung des Datenverkehrs ermöglichen. Sie werden häufig für Web-Server und TLS verwendet.
  * Eine Service-IP-Adresse, die an das Domain Name System (DNS) gebunden ist. Vermeiden Sie Verzögerungen beim DNS-Caching, wenn Sie Workloads auf neue Server verschieben (die Service-IP-Adresse ändert sich nicht automatisch, wenn sich die primäre IP-Adresse eines Servers ändert)..
  * Hochverfügbarkeitskonfigurationen, von denen Protokolle für variable IP-Adressen verwendet werden.

Für solche und viele weitere Verwendungen bieten wir verschiedene Routing-Optionen für sekundäre Teilnetze an. Zur Verdeutlichung der Unterschiede zwischen den angebotenen sekundären Teilnetzen verweisen wir in späteren Erklärungen auf das nachfolgende Beispielteilnetz.

Beispiel für IP-Adressen, die im Teilnetz 10.0.0.0/29 bereitgestellt werden:
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

#### Statische Teilnetze
{:#static-subnets}

In einem statischen Teilnetz wird ein einzelnes Ziel mit Zugriff auf alle IP-Adressen bereitgestellt, die in diesem Teilnetz definiert werden. Einer der Vorteile eines statischen Teilnetzes besteht darin, dass vom Zielgerät alle definierten IP-Adressen verwendet werden können; die üblichen Einbußen bei der Nutzung der Netze, Gateways und Broadcastadresse müssen nicht in Kauf genommen werden. Bei Verwendung des Beispielteilnetzes können alle Adressen verwendet werden:

```
10.0.0.0 - Verwendbar durch Geräte
10.0.0.1 - Verwendbar durch Geräte
10.0.0.2 - Verwendbar durch Geräte
10.0.0.3 - Verwendbar durch Geräte
10.0.0.4 - Verwendbar durch Geräte
10.0.0.5 - Verwendbar durch Geräte
10.0.0.6 - Verwendbar durch Geräte
10.0.0.7 - Verwendbar durch Geräte
```

Wenn somit ein Server über die IP-Adresse 10.0.0.13 verfügt und Sie eine statische Weiterleitung von 10.0.0.0/30 zu 10.0.0.13 festgelegt haben, können von diesem Server jetzt vier zusätzliche IP-Adressen gebunden werden; der Datenverkehr wird auf jeder Seite einzeln empfangen. Es ist wichtig zu verstehen, dass für die angegebenen Adressen keine Netzadressumsetzung (Network Address Translation, NAT) durchgeführt wird. Jede Adresse kann nativ auf Servern verwendet werden und somit jeweils für separate Zwecke genutzt werden.

| **Verfügbarkeit** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Öffentlliches Netz | Ja | Ja |
| Privates Netz      |      |      |

#### Portierbares Teilnetz
{:#portable-subnet}

Von einem portierbaren Teilnetz werden IP-Adressen für alle Ressourcen in einem VLAN bereitgestellt. Dies bedeutet, dass von der Rechenressource in demselben VLAN alle vom Teilnetz bereitgestellten Adressen verwendet werden können. Dieses Verhalten ist für variable Adressen für mehrere Ressourcen sehr nützlich, da das Teilnetz von einer bestimmten Ressource entkoppelt wird. In portierbaren Teilnetzen ist es dafür erforderlich, dass nicht alle im Teilnetz definierten IP-Adressen von Geräten verwendet werden können. Für das technische Funktionieren des Netzbetriebs ist es erforderlich, dass einige IP-Adressen gelesen werden können. Diese gelesenen Adressen werden als Broadcast-, Netz- und Gateway-IP-Adressen bezeichnet. Beachten Sie die Adressen, die in unserem Beispiel verfügbar sind:

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Verwendbar durch Geräte
10.0.0.3 - Verwendbar durch Geräte
10.0.0.4 - Verwendbar durch Geräte
10.0.0.5 - Verwendbar durch Geräte
10.0.0.6 - Verwendbar durch Geräte
10.0.0.7 - Broadcast
```

| **Verfügbarkeit** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Öffentlliches Netz | Ja | Ja |
| Privates Netz      | Ja |      |


### Globale IP-Adressen
{:#global-ip-addresses}

Informationen zum Angebot für globale IPs finden Sie in der [Dokumentation zu globalen IPs](/docs/infrastructure/subnets?topic=subnets-about-global-ip-addresses).

| **Verfügbarkeit** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Öffentlliches Netz | Ja | Ja |
| Privates Netz      |      |      |


## Teilnetze stornieren
{:#canceling-subnets}

Wenn Sie ein sekundäres Teilnetz nicht mehr benötigen, führen Sie die folgenden Schritte aus, um es zu stornieren: 

  1. Öffnen Sie in Ihrem Browser das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/){: new_window} und melden Sie sich bei Ihrem Konto an.
  1. Wählen Sie in der Navigation im Kundenportal **Klassische Infrastruktur** aus. 
  1. Wählen Sie im Navigationsmenü 'Klassische Infrastruktur' **Netz > IP-Verwaltung > Teilnetze** aus.
  1. Wählen Sie die gewünschten Filter aus, um das gewünschte Teilnetz zu lokalisieren.
  1. Rechts neben dem Eintrag des Teilnetzes in der Teilnetzliste wird ein roter Kreis mit einem X angezeigt. Klicken Sie auf dieses Symbol, um den Stornierungsprozess einzuleiten.


## Produktspezifische Hinweise zum Bestellverfahren bei Teilnetzen
{:#product-specific-considerations-subnets}

### Hardware-Firewall (gemeinsam genutzt)
{:#hardware-firewall-subnets}

Portierbare Teilnetze sind nicht standardmäßig durch Firewalls geschützt. Wenn Sie dieses Feature benötigen, besprechen Sie dies bitte mit Ihrem Vertriebsbeauftragten. Sekundäre Teilnetze, die größer als /29 sind, können durch dieses Firewallangebot nicht weitergeleitet werden.

### Portierbare IP-Teilnetzadressen von einem Server an einen anderen übertragen
{:#transferring-portable-subnet-ip-between-servers}

Stellen Sie beim Übertragen einer IP-Adresse von einem Server an einen anderen Server sicher, dass ein Gratuitous ARP-Paket gesendet wird. Dies ermöglicht es unseren Routern, den ARP-Eintrag zu aktualisieren und den Datenverkehr an den richtigen Server weiterzuleiten. Ist dies nicht der Fall, kann dies dazu führen, dass der neue Server den Datenverkehr für die übertragene Adresse mit einer Verzögerung von bis zu vier Stunden empfängt.

### Virtual Router Appliances
{:#virtual-router-appliances-subnets}

Wenn Sie Teilnetze für ein VLAN hinter einer Virtual Router Appliance bestellen, müssen Sie sicherstellen, dass das Teilnetz so konfiguriert ist, dass ein Failover zwischen zwei Appliances möglich ist. Detaillierte Unterstützung finden Sie in der Dokumentation zur [Hochverfügbarkeitskonfiguration für Virtual Router Appliances](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
