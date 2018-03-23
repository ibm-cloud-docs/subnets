---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Informationen zu Teilnetzen und IPs

IBM Cloud bietet eine Reihe von Optionen für die Bestellung von Teilnetzen und IP-Adressen, damit Sie eine Infrastruktur entwerfen können, die Ihre Anforderungen erfüllt. Wenn Sie verstehen, wie Teilnetze funktionieren, und die vorgesehenen Anwendungsfälle für Teilnetze kennen, können Sie Ihre Ziele besser erreichen.

## Typen von Teilnetzen

Wenn Sie sich mit den verschiedenen Typen von Teilnetzen vertraut machen, verstehen Sie besser, wie Sie sie in Ihrer Cloudinfrastruktur optimal einsetzen können.

### Primäre Teilnetze

Primäre Teilnetze werden von {{site.data.keyword.BluSoftlayer_notm}} in VLANs automatisch zugeordnet, um in Ihren VLANs automatisierte Bereitstellung und Services zur Verfügung zu stellen. Diese Teilnetze sind nicht für Ihre sekundären IP-Adressen oder Services verfügbar, weil sie von unseren automatisierten Systemen verwendet werden. Primäre Teilnetze werden neuen Servern automatisch zugeordnet. Wenn Sie versuchen, sie auf Ihren Servern zu verwenden, verursachen Sie möglicherweise einen IP-Adressenkonflikt. In diesem Fall müssen Sie die IP-Adresse entfernen.

**Anmerkung: Wir können keine IP-Adressen in primären Teilnetzen für Ihre Verwendung reservieren.**

### Portierbare Teilnetze

Portierbare Teilnetze können über das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com/) bestellt werden. Diese Teilnetze stellen in der Regel VM-Adressen (VM - virtuelle Maschine) oder sekundäre IP-Adressen auf Servern oder sekundären Schnittstellen bereit. Diese Teilnetze werden auch für Cluster- oder HA-IP-Adressen verwendet, da sie von unseren Routern mithilfe von ARP verfolgt werden. Sie können problemlos übertragen werden. Das Standardformat dieser Teilnetze umfasst eine eigene Netz-, Gateway- und Broadcastadresse, daher sind drei ihrer IP-Adressen von Anfang an belegt.

### Statische Teilnetze

Statische Teilnetze sind ein anderer Typ von Teilnetzen, den Sie über das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com/network/subnets/order) bestellen können. Statische Teilnetze werden normalerweise für Web-Server, E-Mail oder andere Services verwendet, die auf einem Server gehostet werden und zusätzliche IP-Adressen für Verbindungen erfordern. Ein besonderes Merkmal von statischen Teilnetzen ist, dass Sie eine andere vorhandene, einem Server bereits zugeordnete IP-Adresse angeben müssen, an die das Teilnetz direkt weitergeleitet wird. Sie haben die Flexibilität, das Teilnetz nach Wunsch weiterzuleiten, und Sie können es an verschiedene Server übertragen. Dazu müssen Sie jedoch die Position für die Weiterleitung ändern.

### Globale IP-Adressen

Informationen zum Angebot für globale IPs finden Sie in der [Dokumentation zu globalen IPs](about-global-ip.html).

## Hinweise für verschiedene Teilnetze

### Hardware-Firewalls

Portierbare Teilnetze sind nicht standardmäßig durch Firewalls geschützt. Wenn Sie dieses Feature benötigen, besprechen Sie dies bitte mit Ihrem Vertriebsbeauftragten. Bei Teilnetzen, die geschützt werden müssen, kann es sich maximal um /29-Teilnetze handeln.

### Portierbare IPs von einem Server an einen anderen übertragen

Stellen Sie beim Übertragen einer portierbaren IP von einem Server an einen anderen Server sicher, dass ein Gratuitous ARP-Paket gesendet wird, damit unsere Router ihren ARP-Eintrag aktualisieren und die aktualisierte IP-Adresse an den richtigen Server weiterleiten können. Wenn Sie das ARP-Paket nicht senden, kann es 4 Stunden oder länger dauern, bis die IP-Adresse korrekt antwortet.

### Vyatta-Gateways

Wenn Sie Teilnetze für ein VLAN hinter einem Vyatta-Gateway bestellen, müssen Sie sicherstellen, dass das Teilnetz der Konfiguration des Vyatta-Geräts korrekt hinzugefügt wird. Stellen Sie bei der Verwendung von VRRP für HA sicher, dass das Teilnetz korrekt konfiguriert ist und die Funktionsübernahme zwischen den beiden Gateway-Geräten zulässt. Wenn Sie weitere Unterstützung für diese Aufgaben benötigen, lesen Sie die beiden folgenden Artikel zur Konfiguration des Vyatta-Gateways:

 * [Netzgateway-Geräte Vyatta](../network-gateways/network-gateway-devices-vyatta.html)

 * [Vyatta-Konfiguration für hohe Verfügbarkeit](../vyatta/vyatta-high-availability-configuration.html)
 
 ### Teilnetze stornieren
 
Die einem Konto im Rahmen von Gerätebestellungen automatisch zugeordneten Teilnetze werden automatisch freigegeben, wenn diese Teilnetze nicht mehr referenziert werden. Teilnetze, die separat bestellt werden, können jederzeit storniert werden.
