---
copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, unroute process, Device Global IP addresses

subcollection: subnets

---{:shortdesc: .shortdesc}
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

# Unroute a Global IP Address from a Device
{:#unroute-global-ip-address}

Global IP addresses may be manually unrouted by the user at any time. Follow the steps below to unroute a Global IP address from a device.

1. Navigate to the Global IP screen on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. Refer to [Display the Global IP Screen](/docs/infrastructure/subnets?topic=subnets-display-global-ip-screen#display-global-ip-screen).
* Select the Global IP Address to be unrouted.
* Select the **Clear** button.
* Select the **Update** button to complete the unroute process, or select **Cancel** to cancel the action and return to the **Subnets** screen.

## What Happens Next
{:#unroute-global-ip-next}

After you unroute a Global IP from a device, the Global IP is no longer associated with that device. After the Global IP unroute process is complete, that Global IP address may be [rerouted](/docs/infrastructure/subnets?topic=subnets-route-global-ip-address-device#route-global-ip-address-device) to any other device on the account.
