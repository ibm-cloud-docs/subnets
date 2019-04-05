---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Sekundäre Teilnetze für selbst gehostete virtuelle Maschinen verwenden
{:#use-secondary-subnets-self-hosted-vms}

Wenn Sie eigene virtuelle Maschinen hosten und diese virtuellen Maschinen als Mitglieder ersten Grades im {{site.data.keyword.BluSoftlayer_notm}}-Netz verwendet werden sollen, müssen Sie **sekundäre Teilnetze** verwenden. Nachfolgend wird eine flexible Methode zur Bereitstellung der IP-Adressen von virtuellen Maschinen mit einem oder mehreren VM-Hosts besprochen, die von der Verwendung in einer Clusterkonfiguration unabhängig sind.

Weitere Details zu den im Verlauf dieses Szenarios beschriebenen Teilnetztypen finden Sie im Abschnitt [Informationen zu Teilnetzen](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).

Angenommen, Sie verfügen über zwei Bare-Metal-Server mit den Namen `Tante` und `Onkel`. Beide werden als Host für Ihre eigenen virtuellen Maschinen verwendet und jeder verfügt bereits über eigene IP-Adressen, die über ein **primäres Teilnetz** zugeordnet werden. Sie benötigen weitere IP-Adressen für Ihre virtuellen Maschinen. Sie können dafür jeden Typ eines sekundären Teilnetzes verwenden, es wird jedoch empfohlen, ein **portierbares sekundäres Teilnetz** als Quelle für Adressen zu verwenden, die von Ihren virtuellen Maschinen verwendet werden. Von einem portierbaren Teilnetz wird `Tante` und `Onkel` Zugriff auf die IP-Adressen bereitgestellt, die durch das Teilnetz definiert werden. Auf diese Weise können diese IP-Adressen von beiden Servern gemeinsam genutzt werden; wenn Sie für die virtuellen Maschinen (VMs) Migrationstechniken verwenden, können Sie die VMs nahtlos von einem Server auf den anderen übertragen.

Angenommen, Sie haben die beiden virtuellen Maschinen `VPS1` und `VPS2` erstellt, das portierbare Teilnetz 129.42.0.0/29 gekauft und zwei Adressen aus diesem Teilnetz den VMs zugeordnet. Die Nutzung der IP-Adressen ähnelt der folgenden Darstellung:

129.42.0.0/29 - Portierbares sekundäres Teilnetz
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

Angenommen, VPS1 soll über weitere IP-Adressen verfügen, mit denen die bereitgestellten Services getrennt werden sollen. Sie können ohne weiteres mehr Adressen aus dem Teilnetz 129.42.0.0/29 zuweisen, es kann aber sinnvoll sein, dieses Teilnetz nur für die Bereitstellung von VMs zu verwenden, nicht jedoch für Services. Sie haben zwei Möglichkeiten: 1) Kauf eines weiteren portierbaren Teilnetzes, 2) Kauf eines statischen Teilnetzes. Wie bereits im Abschnitt zu den Unterschieden zwischen portierbaren und statischen Teilnetzen in [Informationen zu Teilnetzen](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) beschrieben, bieten portierbare Teilnetze zwar Flexibilität, Sie verfügen aber nicht über Zugriff auf alle IP-Adressen. Wenn Sie nur vier zusätzliche IP-Adressen benötigen, ist der Kauf eines statischen Teilnetzes eine effiziente Lösung. Versuchen Sie es.

Sie kaufen ein statisches Teilnetz und erhalten 129.42.0.100/30. Während des Kaufs leiten Sie es in diesem Szenario an 129.42.0.3 oder VPS1 weiter. So können Sie alle vier IP-Adressen für einen beliebigen Server verwenden, von dem 129.42.0.3 geantwortet wird; das ist derzeit zwar VPS1, aber Sie könnten jederzeit 129.42.0.3 an VPS2 und somit auch diese vier neuen IP-Adressen von 129.42.0.100/30 weiterleiten. Daraus ergibt sich die folgende Nutzung der IP-Adressen:

129.42.0.0/29 - Portierbares sekundäres Teilnetz
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

129.42.0.100/30 - Statisches sekundäres Teilnetz
```
129.42.0.100 – 129.42.0.3 (bzw. VPS1)
129.42.0.101 – 129.42.0.3 (bzw. VPS1)
129.42.0.102 – 129.42.0.3 (bzw. VPS1)
129.42.0.103 – 129.42.0.3 (bzw. VPS1)
```

Zusammenfassung: Mithilfe eines portierbaren Teilnetzes wurden IP-Adressen allen Hosts der virtuellen Maschinen verfügbar gemacht, danach wurden weitere IP-Adressen einer virtuellen Maschine mithilfe eines statischen Teilnetzes verfügbar gemacht. Es konnten Adressen des ursprünglichen portierbaren Teilnetzes verwendet werden oder einfach ein weiteres portierbares Teilnetz hinzugefügt werden. Wir hoffen, dass dieses Szenario veranschaulicht hat, dass das Weiterleiten statischer Teilnetze an IP-Adressen in portierbaren Teilnetzen nicht nur ein ordnungsgemäßes Vorgehen darstellt, sondern sogar effizient und sinnvoll ist.
