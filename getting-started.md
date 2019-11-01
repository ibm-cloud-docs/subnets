---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-08-05"

keywords: IP addresses, IPs Subnets, types of subnets

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:generic: data-hd-programlang="generic"}

# Getting started with Subnets and IPs
{: #getting-started}

Subnets are an important part of how you use the internet, and that's also true when using {{site.data.keyword.cloud}}. We have specific terminology for the types, and uses, of subnets found on our platform. Each subnet provides IP addresses to resources in different ways. You will encounter the following types of subnets, and by knowing more about each type of subnet, you can understand how best to use them in your cloud infrastructure.

  * Primary Subnets - Subnets assigned to meet the IP addressing needs of other products such as Bare Metal Server and Virtual Server Instances. These subnets are automatically assigned and removed. Review the limitations of [primary subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#primary-subnets) for information on their proper use.
  * Secondary Subnets - Subnets which are purchased and routed by you; cancelled when no longer needed. There are two sub-types:
    * Portable - IP addresses are available to all resources on a VLAN.
    * Static - IP addresses are available to the resource identified as the routing endpoint.
  * Global IP Addresses - Unique routing behavior utilizing {{site.data.keyword.cloud}}'s backbone which provides IP addresses to the resource identified as the routing endpoint.

Review each type in detail at [About Subnets and IPs](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) in order to review aspects such as IPv4 vs. IPv6 and public/private network availability.

To understand subnets and subnetting more generally, review [Subnetwork](https://en.wikipedia.org/wiki/Subnetwork){:external}.
Additionally, you'll see we refer to subnets using [CIDR notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing){:external}.


## Ordering Subnets
{:#ordering-subnets}

Follow these steps to order Subnets which provide additional IP addresses:

  1. From your browser, open the [customer portal](https://{DomainName}/){:external} and log into your account.
  1. In the Customer Portal navigation, select **Classic Infrastructure**. 
  1. In the Classic Infrastructure navigation, select **Network > IP Management > Subnets**.
  1. Select the link, "New IP Addresses", in the top right of the listing.
  1. To start the ordering process, select Public or Private type of subnet from the radio buttons.
  1. Choose between IPv4 or IPv6 options.
  1. To choose Static or Global IPs, click the corresponding box. 
    1. For IPv4, use the dropdown list available in the Static or Portable options to choose how many addresses you want. 
  1. Select the VLAN to establish where the new IP addresses are routed.
  1. Fill out the remaining information requested, and click **Create**.


After a subnet has been purchased, the type and routing destination cannot be changed. You must order a new subnet to acquire a different type or routing endpoint.

### What Happens Next?
{:#ordering-subnets-next}

Barring any necessary approval processes for your account status, a new subnet with your desired configuration appears on your account within a few moments.
