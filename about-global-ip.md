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

# About Global IP Addresses
{:#about-global-ip-address}

A Global IP address is a specialized Static Secondary Subnet. It is delivered to you as a /32 subnet (in other words, a single IP address) that can be routed to any other IP address on your account. Both IPv4 and IPv6 addresses are available, and each type must be routed to an IP address of the same IP version. Acceptable routing targets include Primary IP addresses in use by your servers and any Portable Secondary Subnet IP addresses. The unique capabilities of a Global IP address are these:

  * On-demand routing to IP addresses on an account, globally.
  * The address is announced to the internet by all {{site.data.keyword.cloud}} edge routers. Therefore, your data takes the shortest path to the {{site.data.keyword.cloud}} network, and from there you can utilize the {{site.data.keyword.cloud}} dedicated, global backbone to reach the destination you've configured.

Global IP addresses provide flexibility. They enable you to shift workloads between servers, even across geographically disparate datacenters. Also, Global IP addresses provide IP persistence by allowing for transitions without a need to adapt (for example, to avoid DNS caches). The global routing capability is perfect for transitioning workloads across disaster recovery sites, or to seamlessly transition to a new deployment in an geographic area that can serve your audience better.

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |      |      |


## Managing Global IP addresses
{:#manage-global-ip-address}

To manage Global IP addresses, follow these steps:

 1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
 1. In the Customer Portal navigation, select **Classic Infrastructure**.
 1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
 1. You'll see your Global IP addresses listed. Utilize filters to narrow your search as needed. 
 
You may notice that some entries do not have a value for **Target**, which indicates that the Global IP address is not currently routed, so is not in service.

### Routing and unrouting addresses
{:#route-unroute-address}

Once you locate the desired Global IP address, click on its subnet identifier. You'll next see a screen that shows its current route target, if applicable. To route (send traffic) to a new destination, you have two options:

 * enter a complete IP address, or
 * begin typing a hostname.
 
Typing a hostname enables you to search for a server's hostname, so you can look up its IP address. After you enter an IP address, select **Update**. To unroute the Global IP address, select **Clear**. When the input status changes to say 'Unrouted', select **Update**.

The dropdown menu is not an exhaustive list of available IP addresses. Manually enter the desired IP address if it is not available in the selection list.
{:note}

### How often can I update?
{:#how-often-can-i-update}

Only one, single route update is allowed to be in progress at any time. If you attempt to update a Global IP address's route while another update is in progress, you'll receive an error. Wait until the previous update is complete before trying again.


## How to order Global IP addresses
{:#how-to-order-global-ip-address}

Follow these instructions to order Global IP addresses:

  1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
  1. In the Customer Portal navigation, select **Classic Infrastructure**.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  3. Click on the **New IP Addresses** link.
  4. From the dropdown menu, choose **Global IPv4** or **Global IPv6** as needed, and click **Continue** to start the ordering process.

![Figure 1](images/1_2.png)

### What Happens Next?
{:#global-ip-address-next}

Barring any necessary approval processes for your account status, a new Global IP address subnet appears on your account within a few moments.

### Resource Limit
{:#global-ip-resource-limit}

An account may only have five (5) Global IP addresses per IP version. For instance, five (5) IPv4 Global IP addresses, and five (5) IPv6 Global IP addresses.

## How to cancel Global IP addresses
{:#how-to-cancel-global-ip-address}

If you no longer require a Global IP address, follow these steps to cancel it:

  1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
  1. In the Customer Portal navigation, select **Classic Infrastructure**.
  1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Global IP**.
  1. Complete any necessary filters to locate the desired address.
  1. On the right-hand side of the address's entry in the address list, a circle with an X is shown. Click on this icon to initiate the cancellation process.
