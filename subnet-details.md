---

copyright:
  years: 1994, 2020
lastupdated: "2020-05-13"

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Viewing subnet details
{:#view-subnet-details}
{: help}
{: support}

The **Subnet Details** screen displays all IP addresses associated with a subnet. Take the following steps to display subnet details.
{:shortdesc}

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click the **Subnet** link to view the subnet's details.


## IP addresses
{: #filter-subnet-details}

On the **Subnet Details** screen, all IP addresses associated with the subnet are displayed, along with their status, description, and any notes. The list of IP addresses can be filtered by IP address to narrow the IP addresses displayed. Follow these steps to filter IP addresses on the Subnet Details screen.

* Go to the **Subnet Details** screen within the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}. Refer to [Viewing subnet details](/docs/subnets?topic=subnets-view-subnet-details).
* Click the subnet that you want to view details for in the **Subnet** column.
* In the search input box, enter a complete IP address or a number present in one or more of the IP addresses desired, and click **Filter**.
* Return to the full list of all IP addresses by clearing the search input, and clicking **Filter**.


## What happens next
{:#view-subnet-details-next}

All IP addresses associated with the subnet are shown, along with their status, description, and any notes. You can edit the notes for any IP addresses associated with the subnet at any time. If a link to a device is listed as the description, click the link to the view the **Device Details** screen for the device associated with the IP address.


## Status and Description - What to expect
{: #status-description}

Depending on the type of subnet, the **Status** and **Description** columns present different values for IP addresses.

For [Primary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#primary-subnets), the status column shows either **Reserved** or **In Use**. Primary subnets are managed by {{site.data.keyword.cloud_notm}} and their IP addresses are not for general customer use. All addresses have a status of **Reserved** until assigned by {{site.data.keyword.cloud_notm}} to a resource, at which point the status becomes **In Use**. Along with the **Reserved** status, the description shows "Primary IP for future server only"; which reiterates that the IP address is reserved for assignment by {{site.data.keyword.cloud_notm}} for resources you provision. A **Reserved** status that has no description means that the IP address is still reserved for use by {{site.data.keyword.cloud_notm}}, and cannot be assigned to resources you provision.

For [Secondary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets), only the IP addresses necessary for the subnet to function are marked **Reserved**. All addresses that are not marked with **Reserved** are available for customer use. [Static subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#static-subnets) do not require any reservations to function, so all IP addresses show a status of **In Use**, and have a description of "Routed to `<IP address>` `<resource>`". Here, `<resource>` can represent the targeted IP address subnet or compute hostname. [Portable subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#portable-subnet) require three IP addresses to function, and in some locations, five. These IP addresses are shown with a status of **Reserved**, and should not be used. The description column indicates why the IP address is reserved in these cases.
