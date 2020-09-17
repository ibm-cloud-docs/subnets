---

copyright:
  years: 1994, 2019
lastupdated: "2019-02-28"

keywords: 

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

# Routing a global IP address to a device
{:#route-global-ip-address-device}

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.BluSoftlayer_notm}} offers. To route a global IP to a device, the device must be associated with the account that owns the global IP. 
{:shortdesc}

Follow these steps to route a global IP address to a device, such as a bare metal server, portable subnet address, gateway virtual IP, or virtual server instance.

1. Go to the Global IP screen on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. Refer to [Displaying the global IP screen](/docs/subnets?topic=subnets-display-global-ip-screen).
1. Select the global IP subnet to be routed.
1. Begin typing the IP address of the device that you want the global IP to route to in the **Routes to** field. This field auto completes based on your input. It displays any device that is associated with your account.
1. Enter any pertinent notes regarding the global IP, device, or other items, in the **Notes** field.
1. Select **Update** to complete the route, or select **Cancel** to cancel the action and return to the **Subnets** screen.

You cannot route global IP addresses to a primary subnet IP address.
{:important}

## What happens next
{:#route-global-ip-address-device-next}

When you initiate the global IP subnet route, the process begins. Routes generally take less than one minute to complete. At any time, the global IP may be [unrouted](/docs/subnets?topic=subnets-unroute-global-ip-address) from the device.
