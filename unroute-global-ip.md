---
copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: global IP address, unroute process, device global IP addresses

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

# Unrouting a global IP address from a device
{:#unroute-global-ip-address}

Global IP addresses can be manually unrouted by the user at any time. Follow these steps to unroute a global IP address from a device.

1. Go to the Global IP screen on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. Refer to [Displaying the Global IP screen](/docs/subnets?topic=subnets-display-global-ip-screen#display-global-ip-screen).
* Select the global IP address to be unrouted.
* Select **Clear**.
* Select **Update** to complete the unroute process, or select **Cancel** to cancel the action and return to the **Subnets** screen.

## What happens next
{:#unroute-global-ip-next}

After you unroute a global IP from a device, the global IP is no longer associated with that device. After the global IP unroute process is complete, that global IP address may be [rerouted](/docs/subnets?topic=subnets-route-global-ip-address-device#route-global-ip-address-device) to any other device on the account.
