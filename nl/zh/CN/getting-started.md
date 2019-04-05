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

# 子网和 IP 入门
{:#getting-started-subnets-ips}

子网是因特网使用方式的重要部分，在使用 {{site.data.keyword.cloud}} 时也是如此。我们具有针对在平台上找到的子网的类型和用途的特定术语。每个子网以不同方式向资源提供 IP 地址。您将遇到以下类型的子网，通过了解有关每种子网类型的更多信息，您可以掌握如何最好地在云基础架构中使用子网。

  * 主子网 - 为满足其他产品（例如，裸机服务器和虚拟服务器实例）的 IP 寻址需求而分配的子网。将自动分配和除去这些子网。
  * 辅助子网 - 您购买和路由的子网；在不再需要时取消。有两种子类型：
    * 可移植 - IP 地址可用于 VLAN 上的所有资源。
    * 静态 - IP 地址可用于路由端点所标识的资源。
  * 全局 IP 地址 - 利用 {{site.data.keyword.cloud}} 主干的独特路由行为，该主干向路由端点所标识的资源提供 IP 地址。

请在[关于子网和 IP](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) 中详细查看每种类型以了解各个方面，例如，IPv4 与 IPv6 以及公用/专用网络可用性。

要更普遍地了解子网和子网划分，请查看[子网 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://en.wikipedia.org/wiki/Subnetwork)。
此外，您将看到我们使用 [CIDR 表示法 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) 来指示子网。


## 订购子网
{:#ordering-subnets}

遵循以下步骤以订购提供额外 IP 地址的子网：

  1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/){: new_window} 并登录到您的帐户。
  1. 在客户门户网站导航中，选择**经典基础架构**。 
  1. 在“经典基础架构”导航中，选择**网络 > IP 管理 > 子网**。
  1. 选择列表右上角中的链接“新 IP 地址”。
  1. 要开始订购过程，请从单选按钮中选择“公用”或“专用”类型的子网。
  1. 选择 IPv4 或 IPv6 选项。
  1. 要选择“静态 IP”或“全局 IP”，请单击对应的框。 
    1. 对于 IPv4，使用“静态”或“可移植”选项中提供的下拉列表以选择想要的地址数量。 
  1. 选择 VLAN 以确定新 IP 地址路由到的位置。
  1. 填写请求的其余信息，然后单击**创建**。


在购买子网后，无法更改类型和路由目标。您必须订购新子网以获取不同类型或路由端点。

### 后续操作
{:#ordering-subnets-next}

除非帐户状态有任何必需的核准过程，否则很快将在帐户上显示使用所需配置的新子网。
