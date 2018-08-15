---
copyright:
  years: 1994, 2018
lastupdated: "2018-08-06"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Getting Started with Subnets and IPs

Subnets are an important part of how you use the internet, and that's also true when using {{site.data.keyword.cloud}}. We have specific terminology for the types, and uses, of subnets found on our platform. Each subnet provides IP addresses to resources in different ways. You will encounter the following types of subnets, and by knowing more about each type of subnet, you can understand how best to use them in your cloud infrastructure.

  * Primary Subnets - Subnets assigned to meet the IP addressing needs of other products such as Bare Metal Server and Virtual Server Instances. These subnets are automatically assigned and removed.
  * Secondary Subnets - Subnets which are purchased and routed by you; cancelled when no longer needed. There are two sub-types:
    * Portable - IP addresses are available to all resources on a VLAN.
    * Static - IP addresses are available to the resource identified as the routing endpoint.
  * Global IP Addresses - Unique routing behavior utilizing {{site.data.keyword.cloud}}'s backbone which provides IP addresses to the resource identified as the routing endpoint.

Review each type in detail at [About Subnets and IPs](about.md) in order to review aspects such as IPv4 vs. IPv6 and public/private network availability.

To understand subnets and subnetting more generally, review [Subnetwork ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/Subnetwork).
Additionally, you'll see we refer to subnets using [CIDR notation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


## Ordering Subnets

Follow these steps to order Subnets which provide additional IP addresses:

  1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){: new_window} and log into your account.
  2. In the Customer Portal navigation, select **Network > IP Management > Subnets**.
  3. Select the link, "Order IP Addresses", in the top right of the listing.
  4. To start the ordering process, select the appropriate type of subnet from the dropdown menu.

After a subnet has been purchased, the type and routing destination cannot be changed. You must order a new subnet to acquire a different type or routing endpoint.

### What Happens Next?

Barring any necessary approval processes for your account status, a new subnet with your desired configuration appears on your account within a few moments.
