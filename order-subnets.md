---

copyright:
  years: 1994, 2020
lastupdated: "2022-05-26"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}


# Ordering secondary subnets and global IP addresses
{: #order-subnets}

Secondary subnets provide additional, independent IP addresses for your compute resources and are available until canceled.
{: shortdesc}

## Before you begin
{: #before-you-order}

1. Ensure you have the "Add/Upgrade Services" permission, which is set through the [IBM Cloud IAM users permissions panel](/docs/account?topic=account-mngclassicinfra).
1. Determine what [type of secondary subnet](/docs/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets) you need.

## Ordering secondary subnets
{: #ordering-secondary-subnets}

Follow these steps to order a secondary subnet, which provides more IP addresses:

Not all option combinations form orderable secondary subnets. Selecting some options might change available options in different sections.
{: note}

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. Click **Create subnet**. The Secondary subnets page appears. 
1. In the Details section:
   * Select a data center to order a secondary subnet. Select **Global** to order a global IP address.
   * Select either the **Public** or **Private** network for the subnet. Global IP addresses are only available on the public network.
   * Select between IPv4 or IPv6. IPv6 is only available on the public network.
   * Select the **Size**, which refers to a CIDR notation prefix.
   * Select a **Routing** type.
1. In the Endpoint section (only valid for portable and static routing types):
   * Select the destination for the subnet routing. Selections made in the previous sections determine what IP addresses or VLANs are available for your secondary subnet. Use the table's search bar to search within these results.
      * For static subnets, the endpoint table is populated with subnets. Expand the subnet row to see a list of IP addresses that are available to route your new subnet to. 
      * For portable subnets, a table of selectable VLANs appears.
1. Review the summary, read and agree to the Master Service Agreement, and click **Create**.

## Next steps
{: #order-next}

A new subnet with your configuration appears on your account within a few minutes. For information on how to manage global IP addresses, see [Working with global IP addresses](/docs/subnets?topic=subnets-work-with-global-ip-addresses). For information on how to route and unroute secondary subnets, see [Re-routing secondary subnets](/docs/subnets?topic=subnets-re-routing-secondary-subnets).
