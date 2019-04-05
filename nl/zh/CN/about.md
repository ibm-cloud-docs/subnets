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

# 关于子网和 IP
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} 具有针对在平台上找到的子网的类型和用途的特定术语。了解其目标用途将帮助您了解如何最好地在云基础架构中加以使用。


## 子网类型
{:#subnet-types}

### 主子网
{:#primary-subnets}

主子网由 {{site.data.keyword.BluSoftlayer_notm}} 自动分配，并且根据需要向资源提供 IP 地址。我们根据满足其他产品需要时的需求来分配和除去主子网。将从主子网为所有服务器至少供应一个 IP 地址，通常被称为主 IP 地址。某些产品和选件导致分配多个主 IP 地址。

请务必了解，主子网中的 IP 地址尚未分配给资源，不可供您使用。如果尝试使用主子网中未分配的 IP 地址，那么不可避免地，我们需要在某个时刻将它们分配给其他资源。这将导致网络上的 IP 冲突和一般服务中断。我们保留权利以阻止在满足其他产品需求期间未专门分配的主子网上任何 IP 地址或者以其他方式使其不可用。

我们**强烈建议**使用**辅助子网**作为面向外部的服务/应用程序 IP 地址；尤其是在设计多服务器应用程序时。使用分配给服务器的主 IP 地址完全没问题。但是，这样做缺乏维护服务已知地址的灵活性，这些地址与服务器的取消和排序无关。无法保证分配主 IP 地址的顺序，例如，升序、降序或跳过间隔等。

在任何情况下，我们都无法保留主子网中的 IP 地址供您使用。
{:note}

### 辅助子网
{:#secondary-subnets}

辅助子网为您提供满足众多需求的额外 IP 地址。与主子网不同，这些子网在您进行使用的持续时间内归您所有，并且只有在您取消的情况下才会除去。在需要不应依赖于任何特定计算设备的稳定 IP 地址时，应使用辅助子网。示例用法包括：

  * 可分配给自己的本地虚拟机的 IP 地址。
  * 由单个服务器托管的多个不同的服务 IP 地址，允许轻松识别流量。通常与 Web 服务器和 TLS 一起使用。
  * 绑定到 DNS 的服务 IP 地址。在将工作负载转移到新服务器时避免 DNS 高速缓存延迟（即，服务 IP 不会仅仅因为服务器的主 IP 地址更改而更改！）。
  * 利用“浮动”IP 地址协议的高可用性配置。

为了实现此类用途以及其他更多用途，我们针对辅助子网提供不同的路由选项。为帮助阐述所提供的辅助子网之间的差别，我们将在下面的示例子网中进一步说明。

以下是子网 10.0.0.0/29 提供的 IP 地址的示例：
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

#### 静态子网
{:#static-subnets}

静态子网提供可访问该子网定义的所有 IP 地址的单个目标。使用静态子网的一个优点是，目标设备能够利用定义的所有 IP 地址；而不会遭受通常的网络、网关和广播地址使用惩罚。因此在使用示例子网时，所有地址均可用：

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

因此，如果服务器具有 IP 地址 10.0.0.13，并且您已将 10.0.0.0/30 静态路由到 10.0.0.13，那么该服务器现在可绑定 4 个额外的 IP 地址；在每个地址上单独接收流量。请务必了解对于任何提供的地址，将不执行网络地址转换 (NAT)。可在服务器上本机使用每个地址，因此每个地址都可用于不同的目的。

|**可用性**|IPv4|IPv6|
| ---------------- | :--: | :--: |
|公用网络|是|是|
|专用网络|      |      |

#### 可移植子网
{:#portable-subnet}

可移植子网向 VLAN 上的所有资源提供其 IP 地址。这意味着，相同 VLAN 上的任何计算资源都可利用子网提供的任何地址。此行为对于多个资源上的“浮动”地址非常有用，并可使子网与任何特定资源相分离。可移植子网的必要性是并非子网定义的所有 IP 地址均可供设备使用。联网机制要求消耗某些 IP 地址。这些消耗的地址被称为广播、网络和网关 IP 地址。请注意在示例中可用的地址：

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

|**可用性**|IPv4|IPv6|
| ---------------- | :--: | :--: |
|公用网络|是|是|
|专用网络|是|      |


### 全局 IP 地址
{:#global-ip-addresses}

有关全局 IP 产品的信息，请参阅[全局 IP 文档](/docs/infrastructure/subnets?topic=subnets-about-global-ip-addresses)。

|**可用性**|IPv4|IPv6|
| ---------------- | :--: | :--: |
|公用网络|是|是|
|专用网络|      |      |


## 取消子网
{:#canceling-subnets}

如果不再需要某个辅助子网，请执行以下步骤以将其取消：

  1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/){: new_window} 并登录到您的帐户。
  1. 在客户门户网站导航中，选择**经典基础架构**。 
  1. 从“经典基础架构”导航菜单中，选择**网络 > IP 管理 > 子网**。
  1. 选择任何期望的过滤器以查找所需的子网。
  1. 在子网列表中子网条目的右侧，将显示一个红色的带圆圈 X。单击此图标可启动取消过程。


## 订购子网时特定于产品的注意事项
{:#product-specific-considerations-subnets}

### 硬件防火墙（共享）
{:#hardware-firewall-subnets}

缺省情况下，可移植子网不受防火墙保护。如果您需要此功能，请与销售代表商量。无法通过此防火墙产品路由大于 /29 的辅助子网。

### 在服务器之间传输可移植子网 IP 地址
{:#transferring-portable-subnet-ip-between-servers}

在服务器之间传输 IP 地址时，确保发送免费 ARP 包。这将允许路由器更新其 ARP 条目并将流量转发到正确的服务器。不执行此操作可能导致新服务器延迟最多 4 小时才能接收到所传输地址的流量。

### 虚拟路由器设备
{:#virtual-router-appliances-subnets}

在高可用性虚拟路由器设备之后为 VLAN 订购子网时，确保正确配置子网以允许在两个设备之间进行故障转移。[VRA 高可用性配置](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp)文档中描述了详细的帮助。
