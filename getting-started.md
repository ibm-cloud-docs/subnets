---

copyright:
  years: 1994, 2020
lastupdated: "2022-09-01"

keywords: subnets

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with subnets and IPs
{: #getting-started}

{{site.data.keyword.cloud}} offers three types of subnets, with each type providing IP addresses to resources in different ways. A brief description of their capabilities and distinct lifecycles follows.
{: shortdesc}

* Primary subnets - Automatically assigned to meet the IP addressing needs of other services, such as bare metal servers and virtual server instances. These subnets are automatically assigned and removed by {{site.data.keyword.cloud_notm}}.
* Secondary subnets - Purchased and routed by you, and canceled when no longer needed. There are two routing options:
    * Portable - IP addresses are available to all resources on a VLAN.
    * Static - IP addresses are available to the resource identified as the routing endpoint.
* Global IP addresses - Unique routing behavior that uses {{site.data.keyword.cloud_notm}}'s backbone, which provides IP addresses to the resource identified as the routing endpoint.

Review each type in detail at [About subnets and IPs](/docs/subnets?topic=subnets-about-subnets-and-ips) to learn about aspects such as IPv4 versus IPv6 and public versus private network availability.

## Before you begin
{: #before-you-begin}

Ensure you have the "Add/Upgrade Services" permission, which is set through the [IBM Cloud IAM users permissions panel](/docs/account?topic=account-mngclassicinfra).

## Ordering secondary subnets
{: #intro-ordering-secondary-subnets}

Take the following steps to order a secondary subnet.

1. Determine what [type of secondary subnet](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets) you need.
1. [Order](https://{DomainName}/networking/subnets/provision) a secondary subnet. See [Ordering secondary subnets and IPs](/docs/subnets?topic=subnets-order-subnets) for details about ordering secondary subnets with different types and routing options.

## Next steps
{: #getting-started-next}

A new subnet with your configuration appears on your account within a few minutes and is viewable in the [subnets list page](https://{DomainName}/networking/subnets). For information on how to manage global IP addresses, see [Working with global IP addresses](/docs/subnets?topic=subnets-work-with-global-ip-addresses). For information on how to route and unroute secondary subnets, see [Re-routing secondary subnets](/docs/subnets?topic=subnets-re-routing-secondary-subnets).
