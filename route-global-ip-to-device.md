---

copyright:
  years: 1994, 2025
lastupdated: "2025-02-13"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Routing and unrouting a global IP address to a device
{: #route-global-ip-address-device}
{: #unroute-global-ip-address}

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.cloud}} offers. To route a global IP to a device, the device must be associated with the account that owns the global IP.
{: shortdesc}

## Re-routing global IP addresses using the UI
{: #ui-re-routing-global-ip-addresses}
{: ui}

Follow these steps to route a global IP address to a device, such as a bare metal server, portable subnet address, gateway virtual IP, or virtual server instance.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the console, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Infrastructure > Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Find the global IP address you want to route. If necessary, use the **Filter subnets** section, selecting **Global** as **Type** to show only the global IP addresses.
1. Click the Overflow Menu ![Overflow Menu](images/overflow.png) for the global IP address you want to re-route and select **Change route**.
1. Select a **Routing** option.
1. Select a routing endpoint.
    * For **Unrouted** global IP addresses, no routing endpoint is needed.
    * For **Static** global IP addresses, a table of subnets is shown. Expand the subnet row(s) to see a list of IP addresses that are available to route your global IP address to.
1. Click **Change route**. A confirmation window will appear.
1. Review the route change details and click **Confirm**.

When you initiate the global IP address route, the process begins. Routes generally take less than one minute to complete. 
{: note}

## Re-routing global IP addresses using the API
{: #api-re-routing-global-ip-addresses}
{: api}

You can route and unroute global IP addresses assigned to your account using the API.

### Routing global IP addresses using the API
{: #api-routing-global-ip-addresses}

For more information on routing global IP addresses using the API, see [route](https://sldn.softlayer.com/reference/services/SoftLayer_Network_Subnet/route/){: external}

### Unrouting global IP addresses using the API
{: #api-unrouting-global-ip-addresses}

For more information on unrouting global IP addresses using the API, see [clearRoute](https://sldn.softlayer.com/reference/services/SoftLayer_Network_Subnet/clearRoute/){: external}

## How often can I update?
{: #how-often-can-i-update}

A single route update is allowed to be in progress at any time. If you attempt to update a global IP address's route while a previous update is in progress, you will receive an error. Wait until the previous update is complete before you try again.
