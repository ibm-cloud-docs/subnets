---

copyright:
  years: 1994, 2022
lastupdated: "2022-09-07"

keywords: 

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Re-routing secondary subnets
{: #re-routing-secondary-subnets}

You can re-route the secondary subnets that are assigned to your account on the **Subnets** page. For instance, you can:
{: shortdesc}

* Route an unrouted secondary subnet as a static secondary or portable secondary when needed
* Re-route a portable secondary subnet as a static secondary subnet
* Re-route a portable secondary subnet to another VLAN in the same data center
* Re-route a static secondary subnet as a portable secondary subnet
* Re-route a static secondary subnet to another IP address within the same VLAN
* Unroute a static or portable secondary subnet _without_ canceling it

Re-routing secondary subnets has no effect on billing. Unrouted secondary subnets remain billed and assigned to your account.

Secondary subnets in the unrouted state may be subject to automatic reclaim. Refer to the [FAQs](/docs/subnets?topic=subnets-faq#faq-unrouted-subnet-automatic-reclaim) for more details on this policy.
{: note}

## Limitations when re-routing secondary subnets
{: #routing-secondary-subnets-limitations}

The following limitations exist when re-routing your secondary subnets: 

### Scoped to a single data center
{: #single-data-center-limitation}

Secondary subnets are scoped to a single data center. If you order a secondary subnet in `dal10` and wish to re-route it, your available routing endpoints will consist of `dal10` IP addresses for static secondary routing and `dal10` VLANs for portable secondary routing. If you are interested in subnets that are not scoped to a single data center, read more about [global IP addresses](/docs/subnets?topic=subnets-work-with-global-ip-addresses).

### Minimum size requirements for IPv4
{: #minimum-size-requirement-limitation}

Portable secondary subnets have a minimum size requirement of 8 addresses, or `/29`. Any static secondary subnets on your account that are `/30` or smaller can be unrouted, but cannot be re-routed as portable secondary subnets. Any unrouted secondary subnets on your account that are `/30` or smaller can be routed as static secondary subnets, but cannot be routed as portable secondary subnets. Any secondary subnets on your account that are `/29` or larger can be routed as both static and portable secondary subnets.

### Losing dependent routes
{: #dependent-routes-lost-limitation}

Re-routing portable secondary subnets with dependent routes causes those dependent routes to be lost. For example, if you have a static secondary subnet routed to a portable secondary subnet on your account and re-route the portable secondary subnet, the static secondary subnet will be unrouted as part of the portable secondary subnet re-route. Dependent routes that might be lost as a result of portable secondary subnet re-routing are displayed on the re-route confirmation page before any changes are made.

## Re-routing secondary subnets using the UI
{: #ui-re-routing-secondary-subnets}
{: ui}

You can route and unroute secondary subnets assigned to your account using the UI. To do so, take the following steps:

1. From your browser, open the [IBM Cloud console](https://{DomainName}/) and log in to your account.
1. From the console, click the Menu icon ![menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click the overflow menu ![overflow menu](images/overflow.png) for the subnet you want to re-route and select **Change route**.
1. Select a **Routing** option. 
1. Select a routing endpoint.
    * For **Unrouted** secondary subnets, no routing endpoint is needed.
    * For **Static** secondary subnets, a table of subnets is shown. Expand the subnet row(s) to see a list of IP addresses that are available to route your subnet to.
    * For **Portable** secondary subnets, a table of VLANs is shown. Select the VLAN you want to route your subnet to.
1. Click **Change route**. A confirmation window will appear.
1. Review the route change details and click **Confirm** to proceed with the route change.

## Re-routing secondary subnets using the API
{: #api-re-routing-secondary-subnets}
{: api}

You can route and unroute secondary subnets assigned to your account using the API. 

### Routing secondary subnets using the API
{: #api-routing-secondary-subnets}

For more information on routing secondary subnets using the API, see [route](https://sldn.softlayer.com/reference/services/SoftLayer_Network_Subnet/route/){: external}

### Unrouting secondary subnets using the API
{: #api-unrouting-secondary-subnets}

For more information on unrouting secondary subnets using the API, see [clearRoute](https://sldn.softlayer.com/reference/services/SoftLayer_Network_Subnet/clearRoute/){: external}
