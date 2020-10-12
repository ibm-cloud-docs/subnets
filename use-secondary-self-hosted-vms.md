---
copyright:
  years: 1994, 2019
lastupdated: "2019-11-06"

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

# Using secondary subnets on self-hosted VMs
{:#use-secondary-subnets-self-hosted-vms}

When hosting your own virtual machines, and wanting those virtual machines to be first class citizens on the {{site.data.keyword.BluSoftlayer_notm}} network, it is necessary to use secondary subnets. The following scenario shows a flexible way to provide your VMs IP addresses by using one or more virtual machine hosts, whether participating in clustered configurations or not.
{:shortdesc}

For more information regarding the types of subnets described, see [About subnets](/docs/subnets?topic=subnets-about-subnets-and-ips).

So let's say you have two bare metal servers, named **`aunt`** and **`uncle`**. Both are host to your own virtual machines, and each already has their own IP addresses assigned from a primary subnet. You need additional IP addresses for your virtual machines. You can use any type of secondary subnet to achieve that, but it is recommended to use a secondary portable subnet as the source of addresses used by your VMs. A portable subnet provides both **`aunt`** and **`uncle`** access to the IP addresses defined by the subnet. This way, you can share those IP addresses across both servers, and if you use migration techniques for your VMs, can transfer VMs across those servers seamlessly.

Now let's say you've created two virtual machines, **`VPS1`** and **`VPS2`**, purchased portable subnet `129.42.0.0/29`, and assigned two addresses from it to your virtual machines. The IP address utilization looks something like this:

`129.42.0.0/29` - Secondary portable subnet

```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```
{:pre}

Now let's say you want VPS1 to have more IP addresses to segregate services it is providing. You can assign more addresses out of the `129.42.0.0/29` subnet, but you might want to use that subnet only to bring VMs online, not for their services. You have two options: 1) purchase another portable subnet, or 2) purchase a static subnet. If you recall from the descriptions of portable versus static subnets in [About subnets](/docs/subnets?topic=subnets-about-subnets-and-ips), you know that while portable subnets provide flexibility, they also don't give you access to all of the IP addresses. If you only needed four additional IP addresses, for example, purchasing a static subnet is an efficient option. Let's try that out.

You purchase a static subnet and receive `129.42.0.100/30`. During the purchase, you route it to `129.42.0.3` or VPS1 in this scenario. Doing so provides you with all four IP addresses to use on whatever server is responding to 129.42.0.3, again, that's currently VPS1, but you can transfer 129.42.0.3 to VPS2 at any time and those four new IP addresses from `129.42.0.100/30` would follow. Let's look at the IP address usage again:

`129.42.0.0/29` - Secondary portable subnet

```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```
{:pre}

`129.42.0.100/30` - Secondary static subnet

```
129.42.0.100 – 129.42.0.3 (aka VPS1)
129.42.0.101 – 129.42.0.3 (aka VPS1)
129.42.0.102 – 129.42.0.3 (aka VPS1)
129.42.0.103 – 129.42.0.3 (aka VPS1)
```
{:pre}

To recap, this scenario used a portable subnet to make IP addresses available to all virtual machine hosts, and then made additional IP addresses available to a virtual machine by using a static subnet. You can use addresses out of the original portable subnet, or add another portable subnet. This scenario illustrates that not only is it OK to route static subnets to IP addresses on portable subnets, but it is efficient and useful to do so.
