---

copyright:
  years: 1994, 2020
lastupdated: "2020-10-28"

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

The **Subnet Details** page displays all IP addresses associated with the subnet. Take the following steps to display subnet details.
{:shortdesc}

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click the subnet link to view the subnet's details.

## Finding IP addresses
{: #filter-subnet-details}

The **Subnet Details** page displays all IP addresses associated with the subnet, along with their status, description, and any notes. If a link to a device is listed as the description, click the link to the view the **Device Details** page for the device associated with the IP address.

You can use the **Search all columns** box to narrow the IP addresses displayed. You can also use the overflow menu ![overflow menu](images/overflow.png) to [edit notes](/docs/subnets?topic=subnets-edit-notes-subnet-ip) on the IP address. 

### Editing reverse DNS
{:#edit-reverse-dns}

For any IP address on a public subnet, you can adjust the DNS settings from the overflow menu.  

1. Select **Edit Reverse DNS** from the overflow menu ![overflow menu](images/overflow.png).
1. Enter the Reverse DNS in the field provided.
1. Select a Reverse TTL from the list.
1. Click **Update** to save your changes.

## Status and Description - What to expect
{: #status-description}

Depending on the type of subnet, the **Status** and **Description** columns present different values for IP addresses.

For [Primary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#primary-subnets), the status column shows either **Reserved** or **In Use**. Primary subnets are managed by {{site.data.keyword.cloud_notm}} and their IP addresses are not for general customer use. All addresses have a status of **Reserved** until assigned by {{site.data.keyword.cloud_notm}} to a resource, at which point the status becomes **In Use**. Along with the **Reserved** status, the description shows "Primary IP for future server only"; which reiterates that the IP address is reserved for assignment by {{site.data.keyword.cloud_notm}} for resources you provision. A **Reserved** status that has no description means that the IP address is still reserved for use by {{site.data.keyword.cloud_notm}}, and cannot be assigned to resources you provision.

For [Secondary subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets), only the IP addresses necessary for the subnet to function are marked **Reserved**. All addresses that are not marked with **Reserved** are available for use. [Static subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#static-subnets) do not require any reservations to function, so all IP addresses show a status of **In Use**, and have a description of "Routed to `<IP address>` `<resource>`". Here, `<resource>` can represent the targeted IP address subnet or compute hostname. [Portable subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#portable-subnet) require three IP addresses to function, and in some locations, five. These IP addresses are shown with a status of **Reserved**, and should not be used. The description column indicates why the IP address is reserved in these cases.
