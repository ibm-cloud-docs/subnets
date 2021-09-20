---

copyright:
  years: 1994, 2020
lastupdated: "2020-11-12"

keywords: subnets

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

IBM has three types of subnets, with each subnet providing IP addresses to resources in different ways. The following topic describes the capabilities and best practices for each subnet type.
{: shortdesc}

* Primary subnets - Automatically assigned to meet the IP addressing needs of other services, such as bare metaservers and virtual server instances. These subnets are automatically assigned and removed by IBM.
* Secondary subnets - Purchased and routed by you, and cancelled when no longer needed. There are two subtypes:
    * Portable - IP addresses are available to all resources on a VLAN.
    * Static - IP addresses are available to the resource identified as the routing endpoint.
* Global IP addresses - Unique routing behavior that uses {{site.data.keyword.cloud}}'s backbone, which provides IP addresses to the resource identified as the routing endpoint.

Review each type in detail at [About subnets and IPs](/docs/subnets?topic=subnets-about-subnets-and-ips) to learn about aspects such as IPv4 versus IPv6 and public versus private network availability.

## Before you begin
{: #before-you-begin}

1. Ensure you have the "Add/Upgrade Services" permission, which is set through the [IBM Cloud IAM users permissions panel](/docs/account?topic=account-mngclassicinfra).
1. Determine what [type of secondary subnet](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets) you need.

## Ordering secondary subnets
{: #getting-started-order-secondary-subnets}

Follow these steps to order a secondary subnet which provides more IP addresses:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click **Create subnet**. The Secondary subnets page appears.
1. Select the location, network, protocol, size, and routing options to meet your needs. 
1. Review the summary, read and agree to the Master Service Agreement. 
1. Click **Create**.

See [Ordering secondary subnets and IPs](/docs/subnets?topic=subnets-order-subnets) for details about ordering different types of subnets.

## Next steps
{: #getting-started-next}

A new subnet with your configuration appears on your account within a few minutes and is viewable in the [subnets list page](https://{DomainName}/networking/subnets). For information on how to manage global IP addresses, see [Working with global IP addresses](/docs/subnets?topic=subnets-work-with-global-ip-addresses).

After ordering a secondary subnet, you cannot change the type or routing destination; you must order a new subnet to acquire a different type or routing endpoint. Global IP addresses _are_ routable after ordering. 

