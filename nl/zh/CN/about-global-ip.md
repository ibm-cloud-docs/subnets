---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Addresses, Global IP address, single IP address

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# 关于全局 IP 地址
{:#about-global-ip-address}

全局 IP 地址是专门的静态辅助子网。全局 IP 地址作为 /32 子网（即，单个 IP 地址）交付给您，可以路由到您帐户上的其他任何 IP 地址。IPv4 和 IPv6 地址均可用，并且必须将每种类型路由到相同 IP 版本的 IP 地址。可接受的路由目标包括服务器使用的主 IP 地址以及任何可移植辅助子网 IP 地址。全局 IP 地址的特有功能为：

  * 全局随需路由至帐户上的 IP 地址。
  * 该地址由所有 {{site.data.keyword.cloud}} 边缘路由器向因特网宣布。因此，数据采用到 {{site.data.keyword.cloud}} 网络的最短路径，您可以从其中利用 {{site.data.keyword.cloud}} 专用、全局主干来访问已配置的目标。

全局 IP 地址提供了灵活性。这些 IP 地址支持您在服务器之间转移工作负载，甚至可以在地理位置不同的数据中心之间转移工作负载。另外，全局 IP 地址通过允许无需调整（例如，避免 DNS 高速缓存）的转移，提供 IP 持久性。全局路由功能非常适合在不同灾难恢复站点之间转移工作负载，或者无缝地转移到可更好地服务受众的地理区域中的新部署。

|**可用性**|IPv4|IPv6|
| ---------------- | :--: | :--: |
|公用网络|是|是|
|专用网络|      |      |


## 管理全局 IP 地址
{:#manage-global-ip-address}

要管理全局 IP 地址，请执行以下步骤：

 1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/){: new_window} 并登录到您的帐户。
 1. 在客户门户网站导航中，选择**经典基础架构**。
 1. 在“经典基础架构”导航菜单中，选择**网络 > IP 管理 > 全局 IP**。
 1. 您将看到列出了全局 IP 地址。利用过滤器以根据需要缩小搜索范围。 
 
您可能注意到，某些条目没有**目标**值，这指示全局 IP 地址当前未路由，因此未在使用中。

### 路由和取消路由地址
{:#route-unroute-address}

在找到所需的全局 IP 地址后，单击其子网标识。接下来，您将看到一个屏幕，显示其当前路由目标（如果适用）。要路由（发送流量）到新目标，您有两个选项：

 * 输入完整的 IP 地址，或者
 * 开始输入主机名。
 
输入主机名即可搜索服务器的主机名，从而可查找其 IP 地址。在输入 IP 地址后，选择**更新**。要取消路由全局 IP 地址，请选择**清除**。如果输入状态更改为“已取消路由”等，请选择**更新**。

下拉菜单不是可用 IP 地址的穷举列表。如果所需的 IP 地址在选择列表中不可用，请手动进行输入。
{:note}

### 更新频率可以是多少？
{:#how-often-can-i-update}

在任何时间只允许进行单个路由更新。如果在已有更新正在进行时尝试更新全局 IP 地址的路由，那么将收到错误。等待先前更新完成，然后再重试。


## 如何订购全局 IP 地址
{:#how-to-order-global-ip-address}

遵循以下指示信息以订购全局 IP 地址：

  1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/){: new_window} 并登录到您的帐户。
  1. 在客户门户网站导航中，选择**经典基础架构**。
  1. 在“经典基础架构”导航菜单中，选择**网络 > IP 管理 > 全局 IP**。
  3. 单击**新 IP 地址**链接。
  4. 从下拉菜单中，根据需要选择**全局 IPv4** 或**全局 IPv6**，然后单击**继续**以开始订购流程。

![图 1](images/1_2.png)

### 后续操作
{:#global-ip-address-next}

除非帐户状态有任何必需的核准过程，否则很快将在帐户上显示新的全局 IP 地址子网。

### 资源限制
{:#global-ip-resource-limit}

一个帐户对于每个 IP 版本只能有五 (5) 个全局 IP 地址。例如，五 (5) 个 IPv4 全局 IP 地址和五 (5) 个 IPv6 全局 IP 地址。

## 如何取消全局 IP 地址
{:#how-to-cancel-global-ip-address}

如果不再需要某个全局 IP 地址，请执行以下步骤以将其取消：

  1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/){: new_window} 并登录到您的帐户。
  1. 在客户门户网站导航中，选择**经典基础架构**。
  1. 在“经典基础架构”导航菜单中，选择**网络 > IP 管理 > 全局 IP**。
  1. 完成任何必需的过滤器以查找所需的地址。
  1. 在地址列表中地址条目的右侧，显示一个包含 X 的圆圈。单击此图标可启动取消过程。
