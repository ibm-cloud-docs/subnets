---

copyright:
  years: 1994,2020
lastupdated: "2020-01-29"

keywords: global IP addresses, global IP Address, single IP address

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

# About global IP addresses
{:#about-global-ip-address}

A global IP address is a specialized secondary static subnet that can be routed to any data center, on demand. Global IP addresses are available as either a IPv4 /32 subnet (a single IP address), or a IPv6 /64 subnet. Each version can be routed only to a destination IP address of matching version (no address translation is performed). Acceptable routing targets include primary IP addresses in use by your servers and any secondary portable subnet IP addresses. The unique capabilities of a global IP address are these:

  * Global, on-demand routing to IP addresses on an account.
  * Global IP addresses are announced to the internet by all {{site.data.keyword.cloud}} edge routers. Therefore, your data takes the shortest path to the {{site.data.keyword.cloud}} network, and from there your traffic traverses {{site.data.keyword.cloud}}'s dedicated, global backbone to reach the destination you've configured.

Global IP addresses provide flexibility. They enable you to shift workloads between servers, even across geographically disparate data centers. Also, global IP addresses provide IP persistence by allowing for transitions without a need to adapt (for example, to avoid DNS caches). The global routing capability is perfect for transitioning workloads across disaster recovery sites, or to seamlessly transition to a new deployment in a geographic area that can serve your audience better.2

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  | No   | No   |


## Managing global IP addresses
{:#manage-global-ip-address}

To manage global IP addresses, follow these steps:

 1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
 1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure** to get to the classic infrastructure landing page.
 1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
 1. Your global IP addresses are listed. Use filters to narrow your search as needed.

You might notice that some entries do not have a value for **Target**, which indicates that the global IP address is not currently routed, and thus is not in service.

### Routing and unrouting addresses
{:#route-unroute-address}

After you locate the global IP address, click its subnet identifier. You'll next see a screen that shows its current route target, if applicable. To route (send traffic) to a new destination, you have two options:

 * Enter a complete IP address, or
 * Begin typing a hostname.

Typing a hostname enables you to search for a server's hostname, so you can look up its IP address. After you enter an IP address, select **Update**. To unroute the global IP address, select **Clear**. When the input status changes to say 'Unrouted', select **Update**. Acceptable routing targets include primary IP addresses in use by your servers and any secondary portable subnet IP addresses.

The menu is not an exhaustive list of available IP addresses. Manually enter the IP address that you want if it is not available in the list.
{:note}

### How often can I update?
{:#how-often-can-i-update}

A single route update is allowed to be in progress at any time. If you attempt to update a global IP address's route while a previous update is in progress, you receive an error. Wait until the previous update is complete before trying again.


## Ordering global IP addresses
{:#how-to-order-global-ip-address}

Follow these instructions to order global IP addresses:

  1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
  1. From the Dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure** to get to the Classic Infrastructure landing page.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  1. Click **Order IP addresses**.
  1. In the **New IP addresses** screen, select **Public** or **Private**.
  1. Choose **Global IPv4** or **Global IPv6** as needed.
  1. Choose your options on **Static**, **Portable**, or **Global** addresses, and then click **Create** to start the ordering process.

![Figure 1](images/1_2.png)

### What happens next?
{:#global-ip-address-next}

Barring any necessary approval processes for your account status, a new global IP address subnet appears on your account within a few moments.

### Resource limit
{:#global-ip-resource-limit}

An account can have only five global IP addresses per IP version. For instance, five IPv4 global IP addresses, and five IPv6 global IP addresses.

## Canceling global IP addresses
{:#how-to-cancel-global-ip-address}

If you no longer require a global IP address, follow these steps to cancel it:

  1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
  1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > **Classic Infrastructure** to get to the Classic Infrastructure landing page.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  1. Complete any necessary filters to locate the address that you want.
  1. At the end of the entry in the address list, click the ![close icon](../../icons/close-tagging.svg) to initiate the cancellation process.
