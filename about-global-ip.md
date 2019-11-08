---

copyright:
  years: 1994,2019
lastupdated: "2019-11-06"

keywords: Global IP Addresses, Global IP Address, single IP address

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

# About Global IP Addresses
{:#about-global-ip-address}

A Global IP Address is a specialized Secondary Static Subnet that can be routed to any data center, on demand. Global IP Addresses are available as either a IPv4 /32 subnet (ie. a single IP address), or a IPv6 /64 subnet. Each version may only be routed to a destination IP address of matching version (no address translation is performed). Acceptable routing targets include Primary IP addresses in use by your servers and any Secondary Portable Subnet IP addresses. The unique capabilities of a Global IP Address are these:

  * Global, on-demand routing to IP addresses on an account.
  * Global IP Addresses are announced to the internet by all {{site.data.keyword.cloud}} edge routers. Therefore, your data takes the shortest path to the {{site.data.keyword.cloud}} network, and from there your traffic traverses {{site.data.keyword.cloud}}'s dedicated, global backbone to reach the destination you've configured.

Global IP Addresses provide flexibility. They enable you to shift workloads between servers, even across geographically disparate datacenters. Also, Global IP Addresses provide IP persistence by allowing for transitions without a need to adapt (for example, to avoid DNS caches). The global routing capability is perfect for transitioning workloads across disaster recovery sites, or to seamlessly transition to a new deployment in a geographic area that can serve your audience better.

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |  -   |  -   |


## Managing Global IP Addresses
{:#manage-global-ip-address}

To manage Global IP Addresses, follow these steps:

 1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log into your account.
  1. From the Dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure** to get to the Classic Infrastructure landing page.
 1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
 1. You'll see your Global IP Addresses listed. Utilize filters to narrow your search as needed. 

You may notice that some entries do not have a value for **Target**, which indicates that the Global IP Address is not currently routed, and thus is not in service.

### Routing and unrouting addresses
{:#route-unroute-address}

Once you locate the desired Global IP Address, click on its subnet identifier. You'll next see a screen that shows its current route target, if applicable. To route (send traffic) to a new destination, you have two options:

 * enter a complete IP address, or
 * begin typing a hostname.

Typing a hostname enables you to search for a server's hostname, so you can look up its IP address. After you enter an IP address, select **Update**. To unroute the Global IP Address, select **Clear**. When the input status changes to say 'Unrouted', select **Update**. Acceptable routing targets include Primary IP addresses in use by your servers and any Secondary Portable Subnet IP addresses.

The dropdown menu is not an exhaustive list of available IP addresses. Manually enter the desired IP address if it is not available in the selection list.
{:note}

### How often can I update?
{:#how-often-can-i-update}

A single route update is allowed to be in progress at any time. If you attempt to update a Global IP Address's route while a previous update is in progress, you'll receive an error. Wait until the previous update is complete before trying again.


## How to order Global IP Addresses
{:#how-to-order-global-ip-address}

Follow these instructions to order Global IP Addresses:

  1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log into your account.
  1. From the Dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure** to get to the Classic Infrastructure landing page.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  1. Click on the **Order IP Addresses** button.
  1. In the **New IP Addresses** screen, select Public or Private.
  1. Choose **Global IPv4** or **Global IPv6** as needed.
  1. Choose your options on **Static**, **Portable**, or **Global** addresses, and then click **Create** to start the ordering process.

![Figure 1](images/1_2.png)

### What Happens Next?
{:#global-ip-address-next}

Barring any necessary approval processes for your account status, a new Global IP Address subnet appears on your account within a few moments.

### Resource Limit
{:#global-ip-resource-limit}

An account may only have five (5) Global IP Addresses per IP version. For instance, five (5) IPv4 Global IP Addresses, and five (5) IPv6 Global IP Addresses.

## How to cancel Global IP Addresses
{:#how-to-cancel-global-ip-address}

If you no longer require a Global IP Address, follow these steps to cancel it:

  1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log into your account.
  1. From the Dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > **Classic Infrastructure** to get to the Classic Infrastructure landing page.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  1. Complete any necessary filters to locate the desired address.
  1. At the end the of the address's entry in the address list, click on the ![close icon](../../icons/close-tagging.svg)  to initiate the cancellation process.
