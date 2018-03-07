---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# About Subnets and IPs

IBM Cloud provides a number of options for ordering Subnets and IP addresses, so you can design an infrastructure that meets your needs. Understanding how subnets work and knowing their intended use cases will help you achieve exactly what you need.

## Types of Subnets

By knowing more about each type of subnet, you can understand how best to use them in your cloud infrastructure.

### Primary Subnets

Primary Subnets are assigned automatically by {{site.data.keyword.BluSoftlayer_notm}} on VLANs, for the purpose of supplying automated provisioning and services on your VLANs. These subnets are not available for your secondary IP addresses or services, because they are used by our automated systems. Primary subnets are assigned to new servers automatically. If you try to use them on your servers, you may cause an IP address conflict, in which case you will be required to remove the IP address.

**Note: We are not able to reserve IP addresses in Primary Subnets for your use.**

### Portable Subnets

Portable Subnets can be ordered through the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/) These subnets usually provide Virtual Machine (VM) addresses, or secondary IP addresses on servers or secondary interfaces. These subnets also would be used for cluster or HA IP addresses, because they are tracked by our routers by means of ARP. They can be moved around easily. The standard format of these subnets includes its own Network, Gateway, and Broadcast address--therefore, three of its IP addresses will be in use right away.

### Static Subnets

Static subnets are another type of subnet that you can order through the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/network/subnets/order). Static subnets typically are used for webservers, email, or other services hosted on a server, which require several additional IP addresses to allow connections. Static Subnets are unique, because you must specify another existing IP address that is already assigned to a server to which the subnet is directly routed. You have the flexibility to route the subnet as you desire, and you can move it around to different servers--but to do so, you must change the routed location.

### Global IP Addresses

For information regarding the Global IP Offering, please refer to the [Global IP documentation](about-global-ip.html).

## Considerations to Take into Account with Different Subnets

### Hardware Firewalls

Portable Subnets are not protected by firewalls by default. If you need this feature, please discuss it with your Sales representative. The subnets that need to be protected cannot exceed a /29 subnet.

### Transferring Portable IPs Between Servers

When transferring a Portable IP from one server to another, make sure a gratuitous ARP packet is sent out so that our routers can update their ARP entry and forward the updated IP address to the correct server. If you don't send the ARP packet, it may take 4 hours or more for the IP address to begin responding correctly.

### Virtual Router Appliance (Vyatta) Gateways

When ordering subnets for a VLAN behind a Virtual Router Appliance Gateway, ensure that the subnet is added correctly to the configuration of the Virtual Router Appliance. If using VRRP for HA, ensure that the subnet is configured correctly to allow failover between the two gateway devices. If you need further assistance with these tasks, please refer to these two articles about configuring the Virtual Router Appliance Gateway:

 * [Virtual Router Appliance Network Gateway](../virtual-router-appliance/manage-vlans.html)

 * [Virtual Router Appliance High Availability Configuration](../virtual-router-appliance/vrrp.html)
 
 
 ### Canceling Subnets
 
Subnets that are automatically assigned to an account for the fulfillment of device orders are subject to automatic reclaims when those subnets are no longer referenced. Subnets that are ordered separately may be canceled, subject to a minimum 24-hour wait.
