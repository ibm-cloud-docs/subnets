---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Getting Started with Subnets and IPs

IBM Cloud customers can order static subnets, public and private portable subnets, or global subnets that consist of IPv4 and IPv6 addresses at any time. 

To order Subnets and IPs:

1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){: new_window} and log into your account.
2. In the Customer Portal navigation, select **Network > IP Management > Subnets**.
3. To start the ordering process, select the appropriate type of subnet from the dropdown menu. 

**Note that Subnets are created for customers on a case-by-case basis, which involves a vetting process that looks at an IP-to-server ratio.**

## Understanding static and portable IP blocks
{{site.data.keyword.BluSoftlayer_notm}} currently offers 2 different types of IP blocks: static or portable. These are designed to be used in different ways. A brief description follows of each type of block, also including a section on using these IP addresses within a Virtual Machine.
 
### Static IP block
The most commonly used type of IP block within the {{site.data.keyword.BluSoftlayer_notm}} network is the Static IP block. A Static IP block is routed directly to a specific IP on our network. Every IP address in a Static block is usable on the server. One primary benefit of using a static IP block is that you do not lose the first two and last IP addresses--all addresses in the block are usable. 

Here is an example of a small Static IP block (192.168.0.4/30), showing that all 4 IP’s in this block would be available to the server:
```
·192.168.0.4 – Usable Address
·192.168.0.5 – Usable Address
·192.168.0.6 – Usable Address
·192.168.0.7 – Usable Address
```
With a portable block, only a single IP from this block would actually be useable on the server, because the network, gateway and broadcast IP addresses are bound directly to the VLAN.  

Note: A special technique lets you use all of the IPs, because using the assigned subnet mask will only let you use all but one (the broadcast IP). To use all of the IPs, use the subnet mask of 255.255.255.255 instead, rather than missing out on the broadcast IP.

### Portable IP block
A portable IP block can be used on multiple servers within a single VLAN concurrently. We offer two different types of portable IP blocks:

 * The first type of portable IP block is a “Routed to VLAN” block. This is a static IP block that is routed to an entire VLAN rather than a specific IP address.
 * The other type of portable IP Block is a “Secondary on VLAN” block, which is designed to be used within a Virtual Environment.
 
The primary difference between the two is the number of IPs that are available for use. 

A **Routed to VLAN block**,like a static block, provides you access to all IPs within the block. However, a **Secondary on VLAN** block requires that the Network, Gateway and Broadcast IPs be bound directly to the VLAN, which renders them unusable. A **Routed to VLAN** block would be used when the user wanted to use any IP within that block on any server within the VLAN at any time. The **Secondary on VLAN** block is used in conjunction with a Virtual Machine. More information on **Secondary on VLAN** blocks is provided under the _IPs for Virtual Machines_ section.

When ordering a portable IP block, by default {{site.data.keyword.BluSoftlayer_notm}} will provide you with a **Secondary on VLAN** block. If you wish to have this block converted to a **Routed to VLAN** block for use on your servers within a single VLAN, please open a support ticket requesting that this block be converted to a **Routed to VLAN** block

### PODs that support Hot Standby Router Protocol (HSRP)

It is important to note that PODs that take advantage of the Hot Standby Router Protocol (HSRP) utilize 2 additional IPv4 addresses: one for the VLAN interface of each participating router, out of every **Secondary on VLAN** block configured on the VLAN. Most of our PODs support HSRP.

What follows is an example of a **Secondary on VLAN** block (192.168.0.4/28) being used for multiple Virtual Machines in an HRSP POD.
```
192.168.0.0 –  Network Address
192.168.0.1 –  Gateway Address
192.168.0.2 –  Router A Vlan Interface
192.168.0.3 –  Router B Vlan Interface
192.168.0.4 –  VPS1
192.168.0.5 –  VPS2
192.168.0.6 –  VPS3
192.168.0.8 –  VPS4
192.168.0.9 –  VPS5
192.168.0.10 – VPS6
192.168.0.11 – VPS7
192.168.0.12 – VPS8
192.168.0.13 – VPS9
192.168.0.14 – VPS10
192.168.0.15 – Broadcast Address
```
 
### IPs for Virtual Machines
Virtual Machines (VMs) are commmonly used in cloud workloads, sometimes called "instances" or "computes". This section provides information on what type of IP blocks are required to be used in a VM. The information provided here is based on Microsoft Hyper-V.

Every VM connected to the {{site.data.keyword.BluSoftlayer_notm}} network in a virtual environment requires a primary IP address from a portable block of IPs, because Hyper-V requires each VM to provide a Network, Gateway and Broadcast address on the same subnet as the primary IP assigned to that VM. One advantage to our network configuration is that a single **Secondary on VLAN** block can be used for multiple Virtual Machines. 

What follows is an example of a **Secondary on VLAN** block (192.168.0.4/29) being used for multiple Virtual Machines:
```
·192.168.0.0 – Network Address
·192.168.0.1 – Gateway Address
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Broadcast Address
```
As the example shows, this **Secondary on VLAN** block provides 5 usable IP addresses out of the 8 IP addresses in the block, bound across 3 different Virtual Machines. This configuration brings up the question: “How do I add more IPs to a Virtual Machine if all the IPs on the Portable block are used?”. This problem can be solved through the use of a static block, or a **Routed to VLAN** portable block.

To use a static block within a VM, first order a new static IP block from the Customer Portal. As you order this block, you can select the IP address to which you wish to have this block routed. By selecting the IP address that is assigned to the VM, the new block will be routed specifically to that VM. Then you can bind the new block of IPs directly to that VM and begin using them immediately.

Alternately, if you wish for the new block to be usable by more than one Virtual Machine, use a **Routed to VLAN** block. A **Routed to VLAN** block is available by purchasing a Portable IP block from the portal and selecting the VLAN within which the IP address of the VM resides. Once the IP block is created, it is available for use on any server or VM on that VLAN.
