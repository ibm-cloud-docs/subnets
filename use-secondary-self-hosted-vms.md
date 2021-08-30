---
copyright:
  years: 1994, 2020
lastupdated: "2020-10-27"

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
{: #use-secondary-subnets-self-hosted-vms}

If you host your own virtual machines on the {{site.data.keyword.cloud}} network, you'll need secondary subnets to provide the instances with IP addresses. The following scenario shows a flexible way to provide your VMs IP addresses by using one or more virtual machine hosts, whether participating in clustered configurations or not.
{: shortdesc}

Suppose you have two bare metal servers, named **`baremetal1`** and **`baremetal2`**. Both are host to your own virtual machines, and each already has their own IP addresses assigned from a primary subnet. You need additional IP addresses for your virtual machines. You can use any type of secondary subnet to achieve that, but it is recommended to use a secondary portable subnet as the source of addresses used by your VMs. A portable subnet provides both bare metals access to the IP addresses defined by the subnet. This way, you can share those IP addresses across both servers, and if you use migration techniques for your VMs, can transfer VMs across those servers seamlessly.

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
{: screen}

If you want **`VPS1`** to have more IP addresses to segregate services that it is providing, you can assign more addresses out of the `129.42.0.0/29` subnet, but you may want to use that subnet only to bring VMs online, not for their services. You have two options: 1) purchase another portable subnet, or 2) purchase a static subnet. Portable subnets provide flexibility but they don't give you access to all of the IP addresses. If you only needed four additional IP addresses, for example, purchasing a static subnet is an efficient option. 

You can purchase a static subnet and receive `129.42.0.100/30`. You can route the subnet to `129.42.0.3` or **`VPS1`** in this scenario. Doing so provides you with all four IP addresses to use on whatever server is responding to `129.42.0.3`, and if you transfer `129.42.0.3` to **`VPS2`**, those four new IP addresses from `129.42.0.100/30` will follow. Let's look at the IP address usage again:

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
{: screen}

`129.42.0.100/30` - Secondary static subnet

```
129.42.0.100 – 129.42.0.3 (VPS1)
129.42.0.101 – 129.42.0.3 (VPS1)
129.42.0.102 – 129.42.0.3 (VPS1)
129.42.0.103 – 129.42.0.3 (VPS1)
```
{: screen}

In summary, this scenario used a portable subnet to make IP addresses available to all virtual machine hosts, and then made additional IP addresses available to a virtual machine by using a static subnet. You can use addresses out of the original portable subnet, or add another portable subnet. This scenario illustrates that not only is it OK to route static subnets to IP addresses on portable subnets, but it is efficient and useful to do so.
