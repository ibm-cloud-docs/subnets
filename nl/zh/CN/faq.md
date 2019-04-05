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

# 常见问题
{:#subnets-faq}

## 在查看子网的 IP 地址时，`仅用于未来服务器的主 IP` 是什么意思？
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

将根据 {{site.data.keyword.BluSoftlayer_notm}} 的需要针对您订购的其他资源（例如，裸机服务器或虚拟服务器实例）分配和除去主子网。我们并不是简单地一次分配一个 IP 地址，而是分配一个子网。这意味着有时存在额外空间供未来资源使用。该指定表明这些地址将由未来资源使用。请查看问题“**我能否使用所看到的主子网定义的其他 IP 地址？**”以了解为何不应将这些 IP 地址视为可用的原因。


## 我能否使用所看到的主子网定义的其他 IP 地址？
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

不能！我们认识到您看到 {{site.data.keyword.BluSoftlayer_notm}} 分配为任何其他子网的主子网，但是如[关于子网](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)中所述，主子网随需向资源提供 IP 地址。我们根据满足其他产品需要时的需求来分配和除去主子网。如果尝试使用主子网中未分配的 IP 地址，那么不可避免地，我们需要在某个时刻将它们分配给其他资源。这将导致网络上的 IP 冲突和一般服务中断。我们保留权利以阻止在满足其他产品需求期间未专门分配的主子网上任何 IP 地址或者以其他方式使其不可用。您应该使用**辅助子网**来满足所有其他 IP 地址需求，我们强烈鼓励您使用它们来满足应用程序/服务地址需求。辅助子网灵活得多，并且只要您拥有这些子网，就会在您的帐户上维护这些子网。


## 在订购子网时是否有方法可指定想要用于设备的子网？
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

有，在订购过程期间可指定特定子网。订购设备时，此选项在订购表单的末尾提供。在选择专用 VLAN 后，将显示路由到该 VLAN 的主子网的列表。您可以选择所需的子网。可针对公共 VLAN 和子网重复相同过程。

请务必注意，提交订单**并不保证**有 IP 地址在请求的子网中可用。如果无地址可用，那么将与您联系以确定行动方案。要获取最佳 {{site.data.keyword.BluSoftlayer_notm}} 体验，建议不要针对典型用途选择子网。


## 我已用尽 IP 地址，现在该怎么办？
{:#subnets-faq-ran-out-of-addresses}
{: faq}

不会发生此情况！我们自动分配主子网，从而提供更多 IP 地址以满足您的计算购买需求。您完全无需操心。但是，如果您的意思是需要更多 IP 地址用于本地虚拟机或隔离应用程序等，那么请仔细研究[关于子网](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)中的**辅助子网**。


## 如何向一个计算资源分配更多 IP 地址？
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

首先，您将需要购买一个**辅助子网**，有多种类型，因此请查看[关于子网](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)。在将子网路由到所需的 IP 地址或 VLAN 后，您将需要参阅特定计算文档以了解如何设置新的 IP 地址：

  * [裸机服务器 IP 地址分配](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [虚拟服务器实例 IP 地址分配](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## 在查看子网的 IP 地址时，`针对 HSRP 保留`是什么意思？
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

在越来越少的位置中，{{site.data.keyword.BluSoftlayer_notm}} 包含的路由器利用了称为“热备用路由器协议”或 HSRP 的技术。尤其是，其使用方式会影响可用于***可移植辅助子网***的 IP 地址；这意味着您将无法访问这些位置中的两个额外地址。正如“针对 HSRP 保留”名称所述，这些 IP 地址保留用于满足 HSRP 的需求。您甚至可能在相同路由器上有一些子网包含此类预留，有一些子网不包含此类预留。与任何 IP 冲突一样，请勿尝试使用这些地址，否则可能会影响整个子网上的流量。

