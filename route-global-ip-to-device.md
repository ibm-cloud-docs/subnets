---

copyright:
  years: 1994, 2020
lastupdated: "2020-11-12"

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

# Routing and unrouting a global IP address to a device
{:#route-global-ip-address-device}

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.cloud_notm}} offers. To route a global IP to a device, the device must be associated with the account that owns the global IP.
{:shortdesc}

Follow these steps to route a global IP address to a device, such as a bare metal server, portable subnet address, gateway virtual IP, or virtual server instance.

1. Go to the Subnets page on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. From the **Classic Infrastructure** menu, select **Network > IP Management > Subnets**.
1. Select the global IP subnet you want to route.
1. Use the overflow menu ![overflow menu](images/overflow.png) to select **Route global IP**.
1. In the Global IP Routing side panel, begin typing the IP address of the device that you want the global IP to route to in the **Search for IP address** field. This field auto-completes based on your input. It displays any device that is associated with your account.

   The menu is not an exhaustive list of available IP addresses. Manually enter the IP address that you want if it is not available in the list.
   {:note}

1. Select a target IP address from the list menu.
1. Click **Update** to complete the route, or select **Cancel** to cancel the action and return to the **Subnets** page.

When you initiate the global IP subnet route, the process begins. Routes generally take less than one minute to complete. 

## Unrouting a global IP address from a device
{:#unroute-global-ip-address}

Global IP addresses can be manually unrouted by the user at any time. Follow these steps to unroute a global IP address from a device.

1. Go to the Subnets page in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. From the **Classic Infrastructure** menu, select **Network > IP Management > Subnets**.
1. Select the global IP address you want to unroute.
1. Use the overflow menu ![overflow menu](images/overflow.png) to select **Unroute global IP**.
1. In the Unroute Global Subnet modal that appears, click **Confirm** to unroute the global IP, or click **Cancel** to return to the Subnets page.

After you unroute a global IP from a device, the global IP is no longer associated with that device. After the global IP unroute process is complete, that global IP address can be rerouted to any other device on the account.

## How often can I update?
{:#how-often-can-i-update}

A single route update is allowed to be in progress at any time. If you attempt to update a global IP address's route while a previous update is in progress, you receive an error. Wait until the previous update is complete before you try again.
