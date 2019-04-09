---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, Global IP addresses, Update button

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# 将全局 IP 地址路由到设备
{:#route-global-ip-address-device}

全局 IP 地址由用户手动路由到 {{site.data.keyword.BluSoftlayer_notm}} 提供的任何设备。要将全局 IP 路由到设备，设备必须与拥有全局 IP 的帐户相关联。执行以下步骤将全局 IP 地址路由到设备。

1. 浏览至[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/) 上的“全局 IP”屏幕。请参阅[显示全局 IP 屏幕](/docs/infrastructure/subnets?topic=subnets-display-global-ip-screen){:new_window}。
* 选择要路由的全局 IP 子网。
* 在**路由目标**字段中，开始输入全局 IP 将路由到的设备的 IP 地址。此字段将根据您的输入自动填写。它会显示与您的帐户关联的任何设备。
* 在**注释**字段中，输入有关全局 IP、设备或其他项的任何相关注释。
* 选择**更新**按钮以完成路由，或选择**取消**以取消该操作并返回到**子网**屏幕。

## 后续操作
{:#route-global-ip-address-device-next}

启动全局 IP 子网路由时，路由过程即会开始。路由通常不到一分钟即可完成。可以随时从设备[取消路由](/docs/infrastructure/subnets?topic=subnets-unroute-global-ip-address)全局 IP。
