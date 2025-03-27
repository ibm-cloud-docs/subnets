---

copyright:
  years: 1994, 2025
lastupdated: "2025-03-27"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Viewing subnet details
{: #view-subnet-details}
{: help}
{: support}

The **Subnet Details** page displays all IP addresses associated with the subnet. Take the following steps to display subnet details.
{: shortdesc}

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) and select **Infrastructure > Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click the subnet link to view the subnet's details.

## Finding IP addresses
{: #filter-subnet-details}

The **Subnet Details** page displays all IP addresses associated with the subnet, along with their status, description, and any notes. If a link to a device is listed as the description, click the link to the view the **Device Details** page for the device associated with the IP address.

You can use the **Search all columns** box to narrow the IP addresses displayed. You can also use the overflow menu ![overflow menu](images/overflow.png) to [edit notes](/docs/subnets?topic=subnets-edit-notes-subnet-ip) on the IP address. 

## Status and Description - What to expect
{: #status-description}

Depending on the type of subnet, the **Status** and **Description** columns present different values for IP addresses.

For [Primary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#primary-subnets), the status and description columns give contextual usage information, but are not intended to inform customer behavior, because primary IP addresses are assigned automatically and managed by {{site.data.keyword.cloud_notm}}. For primary IP addresses, the status column shows either **Reserved** or **In use**, dependent upon whether a resource is assigned to the IP address and whether or not you have access to that resource.

For [Secondary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets), only the IP addresses necessary for the subnet to function are marked **Reserved**. All IP addresses on routed subnets that are not marked with **Reserved** are available for use. [Static subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#static-subnets) do not require any reservations to function, so all IP addresses show a status of **In use**, and have a description of "Routed to `<IP address>` `<resource>`". Here, `<resource>` can represent the targeted IP address subnet or compute hostname. [Portable subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#portable-subnet) do require some IP addresses in order to function. These IP addresses are shown with a status of **Reserved**, and are not available for use. The description column indicates why the IP address is reserved in these cases. [Unrouted subnets](/docs/subnets?topic=subnets-re-routing-secondary-subnets) do not require any reservations to function, because these subnets are not routed on the {site.data.keyword.cloud_notm} network. These IP addresses are shown with a status of **Unrouted** and are not available for use until the subnet is routed again.

## Tagging subnets
{: #tagging-subnets}

You can tag all subnets on your account with one or more alphanumeric identifiers to make it easier to search and select for specific subnets. Use custom tags to locate subnets on your account rather than information such as subnet network identifier, VLAN, or location. Follow these steps to create or update subnet tags.

1. Click the **Add tags** button at the top of the **Subnet Details** page. If one or more tags are already present on the subnet, click the pencil icon to update them.
1. In the **Update tags** window that appears, enter one or more tags to be created or remove existing tags by clicking the `x` on the tag.
1. Click **Save** to update the tags.

## Editing reverse DNS
{: #edit-reverse-dns}

For any IP address on a public subnet, you can adjust the DNS settings from the overflow menu.  


1. Select **Edit reverse DNS** from the overflow menu ![overflow menu](images/overflow.png).
1. Enter the Reverse DNS in the field provided.
1. Select a Reverse TTL from the list.
1. Click **Update** to save your changes.
