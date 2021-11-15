---

copyright:
  years: 1994, 2020
lastupdated: "2020-11-09"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Working with global IP addresses
{: #work-with-global-ip-addresses}

You can manage your global IP addresses in the **Subnets** page.
{: shortdesc}

## Prerequisites
{: #global-ip-prereqs}

You must have the following Classic infrastructure permissions to change the routing of global IP addresses:

- **Manage Network Subnet Routes** 
- **Allow Access To All Hardware**
- **Allow Access To All Virtual Servers**

## Managing global IP addresses
{: #manage-global-ip-addresses}
{: help}
{: support}

To manage global IP addresses, follow these steps:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the menu icon ![menu icon](../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Subnets**.
1. Expand the **Filter subnets** section, and use the **Type** menu list to select **Global** to filter the subnet list to show only the global IP addresses.
1. Click the overflow menu ![overflow menu](images/overflow.png) of the global IP you want to manage.

    A global IP is a static IP address that can be routed to any server within the IBM Cloud network. The current static IP address offering can be routed only to an IP address within the same data center, but global IP addresses do not share this restriction.
    {: note}

1. Select the operation you want to perform from the overflow menu. You can [edit notes](/docs/subnets?topic=subnets-edit-notes-subnet-ip), [route or unroute](/docs/subnets?topic=subnets-route-global-ip-address-device) the global IP address, or [cancel the subnet](/docs/subnets?topic=subnets-canceling-subnets).

You might notice that some entries do not have a value for **Target**, which indicates that the global IP address is not currently routed, and thus is not in service.

## Adding a global IP to your server
{: #add-global-ip-server}

Before your server accepts traffic for the global IP, that IP must be properly added to the system. Each system requires slightly different commands, as shown in the following sections.

### For Linux servers
{: #add-global-ip-server-linux}

The following instructions are for different versions of Linux servers.

#### Red Hat/CentOS
{: #redhat}

Edit (vim or nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

Add the following lines:

```sh
DEVICE=eth1
IPADDR=[Global IP address]
NETMASK=255.255.255.255
NETWORK=[Network of the Primary IP Block]
ONBOOT=yes
```
{: codeblock}

#### Debian/Ubuntu
{: #ubuntu}

Edit `/etc/network/interfaces`

Add the following lines:

```sh
post-up ip addr add [Global IP address]/32 dev eth1
post-down ip addr del [Global IP address]/32 dev eth1
```
{: codeblock}

If your system doesn't work properly, add the following lines instead, replacing the # with the next number available.

```sh
auto eth1:#
iface eth1:# inet static
address [Global IP address]
netmask 255.255.255.255
gateway [Server Primary Public Gateway]
```
{: codeblock}

### For Windows servers
{: #add-global-ip-server-windows}

1. Browse to **Start > Control Panel > Network Connections > Local Area Connection (Public) (properties)**.
1. Select **Internet Protocol (TCP/IP)** and click **Properties > Advanced**.
1. Select **Add** in the IP addresses section and enter the IP address and subnet mask.
1. After this task is complete, click **OK** to return to the desktop.

To verify that your settings took effect, open a DOS prompt by browsing to **Start > Run > "cmd"** and run the command:

```sh
ipconfig /all
```
{: codeblock}

**Notes:**

* If you already have an `eth1:1` file on your server as in the example, increment the last digit to the next available integer.
* Modification of a global IP address to a new server or VSI requires up to five minutes to take effect.
* Within the IBM Cloud network, the route change takes less than one minute to update.
* Global IP addresses do not work for local load balancers.
* Global IP addresses are distributed from a unique subnet; existing customer IP addresses cannot be converted or used as global IP addresses.
* By itself, global IP addresses are not an automatic failover solution because they lack health checks. However, a global IP address can be used as a component for a failover environment, if you want to circumvent DNS propagation.

### Resource limit
{: #global-ip-resource-limit}

An account can have only five global IP addresses per IP version. For instance, five IPv4 global IP addresses, and five IPv6 global IP addresses.
