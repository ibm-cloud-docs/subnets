---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Einführung in Teilnetze und IPs

IBM Cloud-Kunden können jederzeit statische Teilnetze, öffentliche und private portierbare Teilnetze oder globale Teilnetze bestellen, die aus IPv4- und IPv6-Adressen bestehen. 

Gehen Sie wie folgt vor, um Teilnetze und IPs zu bestellen:

1. Öffnen Sie in Ihrem Browser das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com/){: new_window} und melden Sie sich bei Ihrem Konto an.
2. Wählen Sie in der Navigation des Kundenportals die Optionen für **Netz > IP-Verwaltung > Teilnetze** aus.
3. Wählen Sie den entsprechenden Teilnetztyp im Dropdown-Menü aus, um den Bestellablauf zu starten. 

**Beachten Sie, dass Teilnetze für Kunden auf individueller Basis erstellt werden. Dabei findet ein Überprüfungsprozess statt, bei dem das Verhältnis von IPs zu Servern berücksichtigt wird.**

## Erläuterungen zu statischen und portierbaren IP-Blöcken
Mit {{site.data.keyword.BluSoftlayer_notm}} werden zurzeit zwei verschiedene Typen von IP-Blöcken angeboten: statische und portierbare IP-Blöcke. Diese sind für eine unterschiedliche Verwendung konzipiert. Im Folgenden finden Sie eine Kurzbeschreibung zu jedem Blocktyp sowie einen Abschnitt zur Verwendung dieser IP-Adressen innerhalb einer virtuellen Maschine.
 
### Statischer IP-Block
Der gängigste Typ des IP-Blocks innerhalb des {{site.data.keyword.BluSoftlayer_notm}}-Netzes ist der statische IP-Block. Ein statischer IP-Block wird direkt an eine bestimmte IP in unserem Netz weitergeleitet. Jede IP-Adresse in einem statischen Block ist auf dem Server verwendbar. Ein Hauptvorteil der Verwendung eines statischen IP-Blocks ist, dass die ersten beiden IP-Adressen und die letzte IP-Adresse nicht verloren gehen - alle Adressen im Block sind verwendbar. 

Das folgende Beispiel eines kleinen statischen IP-Blocks (192.168.0.4/30) zeigt, dass alle 4 IPs in diesem Block für den Server verfügbar wären:
```
·192.168.0.4 – Verwendbare Adresse
·192.168.0.5 – Verwendbare Adresse
·192.168.0.6 – Verwendbare Adresse
·192.168.0.7 – Verwendbare Adresse
```
Bei einem portierbaren Block wäre nur eine einzige IP aus diesem Block auf dem Server verwendbar, weil die IP-Adressen für das Netz, für das Gateway und für Broadcast direkt an das VLAN gebunden werden. 

Anmerkung: Mit einem speziellen Verfahren können Sie alle IPs nutzen. Bei Verwendung der zugeordneten Teilnetzmaske können Sie hingegen eine der IPs (die Broadcast-IP) nicht nutzen. Um alle IPs nutzen zu können, verwenden Sie die Teilnetzmaske 255.255.255.255, anstatt auf die Broadcast-IP zu verzichten.

### Portierbarer IP-Block
Ein portierbarer IP-Block kann innerhalb eines einzelnen VLANs auf mehreren Servern gleichzeitig genutzt werden. Wir bieten zwei verschiedene Typen portierbarer IP-Blöcke an:

 * Der erste Typ des portierbaren IP-Blocks ist der Typ “An VLAN weitergeleitet”. Dabei handelt es sich um einen statischen IP-Block, der an ein gesamtes VLAN und nicht an eine bestimmte IP-Adresse weitergeleitet wird.
 * Der zweite Typ des portierbaren IP-Blocks ist der Typ “Sekundär in VLAN”, der für die Verwendung innerhalb einer virtuellen Umgebung vorgesehen ist.
 
Der wichtigste Unterschied zwischen den beiden Typen ist die Anzahl der IPs, die für die Verwendung verfügbar sind. 

Ein Block des Typs **An VLAN weitergeleitet** bietet Ihnen wie ein statischer Block Zugriff auf alle IPs innerhalb des Blocks. Bei einem Block des Typs **Sekundär in VLAN** müssen hingegen die IPs für Netz, Gateway und Broadcast direkt an das VLAN gebunden werden, sodass sie nicht verwendbar sind. Ein Block des Typs **An VLAN weitergeleitet** wird verwendet, wenn der Benutzer jede IP innerhalb dieses Blocks jederzeit auf jedem Server innerhalb des VLANs benutzen möchte. Der Block des Typs **Sekundär in VLAN** wird mit einer virtuellen Maschine verwendet. Weitere Informationen zu Blöcken des Typs **Sekundär in VLAN** finden Sie im Abschnitt _IPs für virtuelle Maschinen_.

Bei der Bestellung eines portierbaren IP-Blocks stellt {{site.data.keyword.BluSoftlayer_notm}} Ihnen standardmäßig einen Block des Typs **Sekundär in VLAN** bereit. Wenn dieser Block für die Verwendung auf Ihren Servern innerhalb eines einzigen VLANs in einen Block des Typs **An VLAN weitergeleitet** konvertiert werden soll, öffnen Sie ein Support-Ticket, um die Konvertierung in einen Block des Typs **An VLAN weitergeleitet** anzufordern.

### PODs mit Unterstützung für HSRP (Hot Standby Router Protocol)

Ein wichtiger Punkt ist, dass PODs, die das HSRP (Hot Standby Router Protocol) nutzen, zwei weitere IPv4-Adressen verwenden: eine für die VLAN-Schnittstelle jedes teilnehmenden Routers in jedem Block des Typs **Sekundär in VLAN**, der im VLAN konfiguriert ist. Die meisten unserer PODs unterstützen HSRP.

Es folgt ein Beispiel für einen Block des Typs **Sekundär in VLAN** (192.168.0.4/28), der für mehrere virtuelle Maschinen in einem HRSP-POD verwendet wird.
```
192.168.0.0 –  Netzadresse
192.168.0.1 –  Gateway-Adresse
192.168.0.2 –  VLAN-Schnittstelle für Router A
192.168.0.3 –  VLAN-Schnittstelle für Router B
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
192.168.0.15 – Broadcastadresse
```
 
### IPs für virtuelle Maschinen
Virtuelle Maschinen (VMs) werden häufig in Cloud-Workloads verwendet. Sie werden auch als "Instanzen" oder "Computes" bezeichnet. Dieser Abschnitt enthält Informationen zum Typ der IP-Blöcke, die für die Verwendung in einer VM erforderlich sind. Die hier bereitgestellten Informationen basieren auf Microsoft Hyper-V.

Für jede VM, die in einer virtuellen Umgebung mit dem {{site.data.keyword.BluSoftlayer_notm}}-Netz verbunden ist, wird eine primäre IP-Adresse aus einem portierbaren IP-Block benötigt, da Hyper-V erfordert, dass jede VM eine Netz-, Gateway- und Broadcastadresse in demselben Teilnetz bereitstellt wie die primäre IP-Adresse, die dieser VM zugeordnet ist. Einer der Vorteile unserer Netzkonfiguration ist, dass ein einziger Block des Typs **Sekundär in VLAN** für mehrere virtuelle Maschinen verwendet werden kann.  

Es folgt ein Beispiel für einen Block des Typs **Sekundär in VLAN** (192.168.0.4/29), der für mehrere virtuelle Maschinen verwendet wird:
```
·192.168.0.0 – Netzadresse
·192.168.0.1 – Gateway-Adresse
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Broadcastadresse
```
Wie das Beispiel zeigt, stellt dieser Block des Typs **Sekundär in VLAN** 5 verwendbare IP-Adressen von den 8 IP-Adressen in dem Block zur Verfügung, die an 3 verschiedene virtuelle Maschinen gebunden sind. Diese Konfiguration wirft die folgende Frage auf: “Wie füge ich einer virtuellen Maschine weitere IPs hinzu, wenn alle IPs in dem portierbaren Block belegt sind?”. Dieses Problem kann mithilfe eines statischen Blocks oder eines portierbaren Blocks des Typs **An VLAN weitergeleitet** gelöst werden.

Zur Verwendung eines statischen Blocks innerhalb einer VM bestellen Sie zuerst einen neuen statischen IP-Block über das Kundenportal. Bei der Bestellung dieses Blocks können Sie die IP-Adresse auswählen, an die dieser Block weitergeleitet werden soll. Wenn Sie die IP-Adresse auswählen, die der VM zugeordnet ist, wird der neue Block genau an diese VM weitergeleitet. Anschließend können Sie den neuen IP-Block direkt an diese VM binden und sofort mit der Verwendung der IPs beginnen.

Wünschen Sie jedoch, dass mehrere virtuelle Maschinen den neuen Block nutzen, verwenden Sie einen Block des Typs **An VLAN weitergeleitet**. Sie erhalten einen Block des Typs **An VLAN weitergeleitet**, indem Sie über das Portal einen portierbaren IP-Block kaufen und das VLAN auswählen, in dem sich die IP-Adresse der VM befindet. Nachdem der IP-Block erstellt wurde, ist er für die Verwendung auf jedem Server oder jeder VM in diesem VLAN verfügbar. 
