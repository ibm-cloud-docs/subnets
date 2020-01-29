---

copyright:
  years: 1994, 2017-2020
lastupdated: "2020-01-29"

keywords: IP addresses, IPs subnets, types of subnets

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}


# Getting started with subnets and IPs
{: #getting-started}

Subnets are an important part of how you use the internet, and that's also true when you use {{site.data.keyword.cloud}}. IBM has specific terminology for the types, and use, of subnets found on our platform. Each subnet provides IP addresses to resources in different ways. You come across the following types of subnets, and by knowing more about each type of subnet, you can understand how best to use them in your cloud infrastructure.
{:shortdesc}

  * Primary subnets - Assigned to meet the IP addressing needs of other products, such as bare metal server and virtual server instances. These subnets are automatically assigned and removed. Review the limitations of [primary subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#primary-subnets) for information on their proper use.
  * Secondary subnets - Purchased and routed by you, and cancelled when no longer needed. There are two subtypes:
    * Portable - IP addresses are available to all resources on a VLAN.
    * Static - IP addresses are available to the resource identified as the routing endpoint.
  * Global IP addresses - Unique routing behavior that uses {{site.data.keyword.cloud}}'s backbone, which provides IP addresses to the resource identified as the routing endpoint.

Review each type in detail at [About subnets and IPs](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) to review aspects such as IPv4 versus IPv6 and public versus private network availability.

To understand subnets and subnetting more generally, review [Subnetwork](https://en.wikipedia.org/wiki/Subnetwork){:external}.
Additionally, subnets are referred in [CIDR notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing){:external}.


## Ordering subnets
{:#ordering-subnets}

Follow these steps to order subnets, which provide more IP addresses:

  1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
  1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure** to get to the Classic Infrastructure landing page.
  1. In the Classic Infrastructure navigation, select **Network > IP Management > Subnets**.
  1. Click **Order IP addresses**.
  1. To start the ordering process, select either the Public or Private type of subnet.
  1. Choose between IPv4 or IPv6 options.
  1. To choose static or global IPs, click the corresponding box. For IPv4, use the menu list available in the static or portable options to choose how many addresses that you want.
  1. Select the VLAN to establish where the new IP addresses are routed.
  1. Complete the required information, and click **Create**.


After a subnet is purchased, you cannot change the type and routing destination. You must order a new subnet to acquire a different type or routing endpoint.

### What happens next?
{:#ordering-subnets-next}

Barring any necessary approval processes for your account status, a new subnet with your configuration appears on your account within a few moments.
