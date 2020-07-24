---

copyright:
  years: 1994, 2019
lastupdated: "2019-02-28"

keywords: global IP addresses, global IPs, IP management

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Managing global IP addresses
{:#manage-global-ip-addresses}
{: help}
{: support}

You can manage your global IP addresses in the **Subnets** screen.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window} and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > Subnets**.
1. In the menu list, select **Global IPv4** (or IPv6) to filter the subnet list to show only the global IPs.
1. Click the global IP you want to manage.

   A global IP is a static IP address that can be routed to any server within the IBM Cloud network. The current static
  IP address offering can be routed only to an IP address within the same data center, but global IP addresses do not share
  this restriction.
  {: note}

1. On the IP address management page, enter the IP address of the server to which you want to route the global IP address, and enter any applicable notes, then select **Update**.

## Adding a global IP to your server
{:#add-global-ip-server}

Before your server accepts traffic for the global IP, that IP must be properly added to the system. Each system requires slightly different commands, as shown in the following sections.

### For Linux&reg; servers:
{:#add-global-ip-server-linux}

**Red Hat/CentOS**

1. Edit (vim or nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* Add the following lines:
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```
{:pre}

**Debian/Ubuntu**

1. Edit `/etc/network/interfaces`

* Add the following lines:

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```
{:pre}

If your system doesn't work properly, add the following lines instead, replacing the # with the next number available.

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```
{:pre}

### For Windows servers
{:#add-global-ip-server-windows}

1. Browse to **Start > Control Panel > Network Connections > Local Area Connection (Public) (properties)**.
* Select **Internet Protocol (TCP/IP)** and click **Properties > Advanced**.
* Select **Add** in the IP addresses section and enter the IP address and subnet mask.
* After this task is complete, click **OK** to return to the desktop.

To verify that your settings took effect, open a DOS prompt by browsing to **Start > Run > "cmd"** and run the command:

```
        > ipconfig /all
```
{:pre}

**Notes:**

* If you already have an `eth1:1` file on your server as in the example, increment the last digit to the next available integer.
* Modification of a global IP address to a new server or VSI requires up to five minutes to take effect.
* Within the IBM Cloud network, the route change takes less than one minute to update.
* Global IPs do not work for local load balancers.
* Global IPs are distributed from a unique subnet; existing customer IPs cannot be converted or used as global IPs.
* By itself, global IPs are not an automatic failover solution because they lack health checks. However, a global IP address can be used as a component for a failover environment, if you want to circumvent DNS propagation.
