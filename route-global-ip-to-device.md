---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, Global IP addresses, Update button

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

# Route a Global IP Address to a Device
{:#route-global-ip-address-device}

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.BluSoftlayer_notm}} offers. To route a Global IP to a device, the device must be associated with the account that owns the Global IP. Follow the steps below to route a Global IP address to a device.

1. Navigate to the Global IP screen on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. Refer to [Display the Global IP Screen](/docs/infrastructure/subnets?topic=subnets-display-global-ip-screen).

* Select the Global IP subnet to be routed.
* Begin typing the IP address of the device that the Global IP will route to in the **Routes to** field. This field will auto complete based on your input. It displays any device associated with your account.
* Enter any pertinent notes regarding the Global IP, device, or other items, in the **Notes** field.
* Select the **Update** button to complete the route, or select **Cancel** to cancel the action and return to the **Subnets** screen.

## What Happens Next
{:#route-global-ip-address-device-next}

When you initiate the Global IP subnet route, the process begins. Routes generally take less than one minute to complete. At any time, the Global IP may be [unrouted](/docs/infrastructure/subnets?topic=subnets-unroute-global-ip-address) from the device.
