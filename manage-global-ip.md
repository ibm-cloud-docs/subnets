---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP addresses, Global IPs, IP Management

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Manage Global IP addresses
{:#manage-global-ip-addresses}

You can manage your Global IP addresses in the **Subnets** screen. 

1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
1. In the Customer Portal navigation, select **Classic Infrastructure**. 
1. In the Classic Infrastructure navigation menu, select **Network > IP Management > Subnets**.
1. In the dropdown menu, choose **Global IPv4** (or IPv6) to filter the Subnet list to show only the Global IPs.
1. Click on the Global IP you want to manage.
 
  **Note: A Global IP is a static IP address that can be routed to any server within the IBM Cloud network. The current static 
  IP address offering can be routed only to an IP address within the same datacenter, but Global IP addresses do not share 
  this restriction.**
  
1. On the IP address management page, enter the IP address of the server to which you wish to route the Global IP address, and enter any applicable notes, then select **Update**.

![Figure 2](images/2_1.png)

## Add a Global IP to your server 
{:#add-global-ip-server}

Before your server will accept traffic for the Global IP, that IP must be properly added to the system. Each system requires slightly different commands, so they are shown in the next few sections.

### For Linux servers:
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

**Debian/Ubuntu**

1. Edit `/etc/network/interfaces`

* Add the following lines:

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

If your system does not work properly, add the following lines instead, replacing the # with the next number available:

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### For Windows servers
{:#add-global-ip-server-windows}

1. Browse to: **Start -> Control Panel -> Network Connections -> Local Area Connection (Public) (properties)**.
* Select: **Internet Protocol (TCP/IP)** and click **Properties -> Advanced**.
* Select **Add** in the IP addresses section and enter the IP address and Subnet mask.
* Once this task is complete, simply "OK" back to the desktop.

To verify that your settings have taken effect, open a DOS prompt by browsing to **Start -> Run -> "cmd"** and run the command

```
        > ipconfig /all
```

**Notes:**

* If you already have an `eth1:1` file on your server as in the example above, increment the last digit to the next available integer.
* Modification of a global IP address to a new server or VSI requires up to five minutes to take effect. 
* Within the IBM Cloud network, the route change takes less than 1 minute to update.
* Global IPs do not work for local load balancers.
* Global IPs are distributed from a unique subnet; existing customer IPs cannot be converted or used as Global IPs.
* By itself, Global IPs are not an automatic failover solution, because they lack health checks; however, a Global IP address may be used as a component for a failover environment, if you want to circumvent DNS propagation.
