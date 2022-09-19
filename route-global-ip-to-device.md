---

copyright:
  years: 1994, 2020
lastupdated: "2022-09-02"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Routing and unrouting a global IP address to a device
{: #route-global-ip-address-device}

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.cloud}} offers. To route a global IP to a device, the device must be associated with the account that owns the global IP.
{: shortdesc}

Follow these steps to route a global IP address to a device, such as a bare metal server, portable subnet address, gateway virtual IP, or virtual server instance.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Find the global IP address you want to route. If necessary, use the **Filter subnets** section, selecting **Global** as **Type** to show only the global IP addresses.
1. Use the overflow menu ![overflow menu](images/overflow.png) to select **Route global IP**.
1. In the Global IP Routing side panel, begin typing the IP address of the device that you want the global IP address to route to in the **Search for IP address** field. This field auto-completes based on your input. It displays any device that is associated with your account.

   The menu is not an exhaustive list of available IP addresses. Manually enter the IP address that you want if it is not available in the list.
   {: note}

1. Select a target IP address from the list menu.
1. Click **Update** to complete the route, or select **Cancel** to cancel the action and return to the **Subnets** page.

When you initiate the global IP subnet route, the process begins. Routes generally take less than one minute to complete. 

## Unrouting a global IP address from a device
{: #unroute-global-ip-address}

Global IP addresses can be manually unrouted by the user at any time. Follow these steps to unroute a global IP address from a device.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Select the global IP address you want to unroute. If necessary, use the **Filter subnets** section, selecting **Global** as **Type** to show only the global IP addresses.
1. Use the overflow menu ![overflow menu](images/overflow.png) to select **Unroute global IP**.
1. In the Unroute Global Subnet modal that appears, click **Confirm** to unroute the global IP address, or click **Cancel** to cancel the action and return to the **Subnets** page.

After you unroute a global IP address from a device, the global IP address is no longer associated with that device. After the global IP address unroute process is complete, that global IP address can be re-routed to any other device on the account.

## How often can I update?
{: #how-often-can-i-update}

A single route update is allowed to be in progress at any time. If you attempt to update a global IP address's route while a previous update is in progress, you will receive an error. Wait until the previous update is complete before you try again.
