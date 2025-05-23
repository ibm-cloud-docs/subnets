---

copyright:
  years: 1994, 2024
lastupdated: "2024-10-30"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Viewing all subnets
{: #view-all-subnets}
{: help}
{: support}

The **Subnets** page lists each subnet that is associated with the account, along with specific information about the subnet, including its network, type, VLAN, location, target, and total number of IP addresses. Follow these steps to view the **Subnets** page.
{: shortdesc}

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Infrastructure > Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.


## Filtering the list of subnets
{: #filter-details}

The list of subnets can be filtered to narrow the subnets displayed at any time. Follow these steps to filter the information shown in the **Subnets** page.

1. Expand the **Filter subnets** section to display the filter options.
1. Specify values for one or more items in the menu list. Filter options include:
    * Subnet
    * Network
    * Type
    * VLAN
    * Location
    * Target
    * Note
1. Click **Filter** to apply the selected filters to the display.

After filtering, all subnets that correspond with the parameters set by the filter are displayed on the **Subnets** page. To clear all parameters set by the filter, click **Clear**.
{: tip}

The search bar acts on the filtered results. If you have no filters selected, it searches all subnets.

## Other actions available
{: #view-all-subnets-next}

On the **Subnets** page, each subnet that is associated with the account is displayed within the list of subnets. From this page, you can view a subnet or VLAN's details, edit notes for a subnet, or order more IP addresses. 

Click the download icon ![Download icon](../icons/download.svg) to download a comma-separated value file of your subnets.

If you have filters applied in the **Filter subnets** section, the CSV file contains only those filtered subnets. If no filters are applied, the CSV file contains all of your subnets. Any search bar filters in use have no effect on the contents of the CSV file.
{: note}
