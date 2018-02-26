---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# About Subnets and IPs

IBM Cloud provides a number of options for ordering Subnets and IP addresses, so our clients can design infrastructures that meet their needs. Understanding how subnets work and knowing their intended use cases will help you achieve exactly what you need.

One thing common to all types of subnets that is you can attach notes to specific IPs in the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/) so that you can keep track of how they are being used. You can edit these notes by following the directions in this article: [Edit Notes for a Subnet](edit-notes.html)

## Descriptions of Each Type of Subnet 

By knowing more about each type of subnet, you can understand how best to use them in your cloud infrastructure.

### Primary Subnets

Primary Subnets are automatically assigned by {{site.data.keyword.BluSoftlayer_notm}} on VLANs, for the purpose of supplying automated provisioning and services on your VLANs. These subnets are not available for your secondary IPs or services, because they are used by our automated systems. Primary subnets are assigned to new servers automatically. If you try to use them on your servers, you may cause an IP conflict, in which case you will be required to remove the IP.

**Note: We are not able to reserve IP addresses in Primary Subnets for your use.**

### Portable Subnets

Portable Subnets can be ordered through the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/) These subnets usually provide Virtual Machine (VM) addresses, or secondary IP addresses on servers or secondary interfaces. These subnets also would be used for cluster or HA IP addresses, because they are tracked by our routers by means of ARP. They can be moved around easily. The standard format of these subnets includes its own Network, Gateway, and Broadcast address--therefore, three of its IP addresses will be in use right away.

As a second option, Portable Subnets can be implemented by opening a support ticket and requesting that the subnet be converted to a “Routed on VLAN” subnet. (The standard offering is known as “Secondary on VLAN.”). This option enables you to use all the IPs in the subnet, because it no longer has its own Network, Gateway, or Broadcast IPs. It also allows you to have secondary alias IP addresses on a server, which are used for things such as webserver IPs or for HA. By using this type of subnet, you have more IPs available, and they can be moved around without using the manual steps in the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/) or through a ticket, because they are tracked by our routers using ARP.

### Static Subnets

Static subnets are another type of subnet that you can order through the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/). Static subnets typically are used for webservers, email, or other services hosted on a server, which require several additional IP addresses to allow connections. Static Subnets are unique, because you must specify another existing IP address that is already assigned to a server to which the subnet is directly routed. You have the flexibility to route the subnet as you desire, and you can move it around to different servers--but to do so, you must change the routed location in the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/).

### Global IPs

For information regarding the Global IP Offering, please refer to the [Global IP documentation](about-global-ip.html).

## Considerations to Take into Account with Different Subnets:

### Hardware Firewalls

Portable Subnets are not protected by firewalls by default. If you need this feature, please discuss it with your Sales representative. The subnets that need to be protected cannot exceed a /29 subnet.

### Requesting New Primary IPs on Your Server

In certain circumstances, you may need to have certain servers on the same subnet (for HA, clustering, and so forth). We can accommodate changes to the primary IP address on a server, including moving it to a Secondary Subnet if needed. However, you must provide adequate justification for the change in a support ticket. These requests are handled on a case-by-case basis, and we will not be able to track it for you within our portal.

### Transferring Portable IPs Between Servers

When transferring a Portable IP from one server to another, make sure a gratuitous ARP packet is sent out so that our routers can update their ARP entry and forward the updated IP address to the correct server. If you don't send the ARP packet, it may take 4 hours or more for the IP address to begin responding correctly.

### Virtual Router Appliance (Vyatta) Gateways

When ordering subnets for a VLAN behind a Virtual Router Appliance Gateway, ensure that the subnet is added correctly to the configuration of the Virtual Router Appliance. If using VRRP for HA, ensure that the subnet is configured correctly to allow failover between the two gateway devices. If you need further assistance with these tasks, please refer to these two articles about configuring the Virtual Router Appliance Gateway:

 * [Virtual Router Appliance Network Gateway](../virtual-router-appliance/manage-vlans.html)

 * [Virtual Router Appliance High Availability Configuration](../virtual-router-appliance/vrrp.html)
 
 
 ### Canceling Subnets
 
Subnets that are automatically assigned to an account for the fulfillment of device orders are subject to automatic reclaims when those subnets are no longer referenced. Subnets that are ordered separately may be canceled, subject to a minimum 24-hour wait.
