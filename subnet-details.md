---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: View Subnet Details, IP addresses, Subnet link

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# View Subnet details
{:#view-subnet-details}

The **Subnet Details** screen displays all IP addresses associated with a subnet, its status, its description, and any notes, if present. Follow the steps in this article to display subnet details.

1. From your browser, open the [{{site.data.keyword.cloud}} Console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
1. In the {{site.data.keyword.cloud_notm}} Console navigation, select **Classic Infrastructure**.
1. In the Classic Infrastructure menu, select **Network > IP Management > Subnets**.
1. Click on the **Subnet** link to view the subnet's details.

## Filter subnet details
{: #filter-subnet-details}

On the **Subnet Details** screen, all IP addresses associated with the subnet are displayed, along with their status, description and any notes present for the IP. The list of IPs may be filtered by IP address to narrow the IPs displayed at any time. Follow these steps to filter IP addresses on the Subnet Details screen.

* Navigate to the **Subnet Details** screen within the [{{site.data.keyword.cloud_notm}} Console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/)}. Refer to [Use the Subnet Details Screen](/docs/infrastructure/subnets?topic=subnets-view-subnet-details).
* Click the desired **IP address** in the **Subnet** column.
* Choose the **Filter** tab to display the filter options.
* Select the IP address from the dropdown list.
  Partial IP addresses may be selected to display a number of addresses. For example, if the last portion of the IP address selected is .1, the IP addresses listed may include those that end in .1 through .19.
  {:note}


After filtering the IP addresses, all IPs that correspond with the parameters set by the filter are displayed on the Subnet Details screen. To modify the filter options entered, click the **Modify** button and update the desired filter options. To clear all parameters set by the filter, click the **Clear All** button.
{:tip}


## What happens next
{:#view-subnet-details-next}

All IP addresses associated with the subnet are shown, along with their status, description, and any notes, if present. You may edit the notes for any IP addresses associated with the subnet at any time. If a link to a device is listed as the description, click the link to the view the **Device Details** screen for the device associated with the IP address.
