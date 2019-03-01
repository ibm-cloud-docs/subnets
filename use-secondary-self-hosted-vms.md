---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Use Secondary Subnets on Self-Hosted VMs
{:#use-secondary-subnets-self-hosted-vms}

When hosting your own virtual machines, and wanting to those virtual machines to
be first class citizens on the {{site.data.keyword.BluSoftlayer_notm}} network,
it is necessary to utilize **Secondary Subnets**. We'll discuss a flexible way
to provide your VMs IP addresses using one or more virtual machine hosts, whether
participating in clustered configurations or not.

Throughout the course of this scenario, refer to [About Subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) for more details regarding the types of subnets described.

So let's say you have two Bare Metal Servers, let's call them `aunt` and `uncle`. Both will be host to your own virtual machines, and each already has their own IP addresses assigned from a **Primary Subnet**. You need additional IP addresses for your virtual machines. You could use any type of Secondary Subnet to achieve that, but we'd recommend using a **Portable Secondary Subnet** as the source of addresses used by your VMs. A portable subnet provides both `aunt` and `uncle` access to the IP addresses defined by the subnet. This way, you can share those IP addresses across both servers, and if you utilize
migration techniques for your VMs, can transfer VMs across those servers seamlessly.

Now let's say you've created two virtual machines, `VPS1` and `VPS2`, purchased portable subnet 129.42.0.0/29, and assigned two addresses from it to your virtual machines. The IP address utilization would look something like this:

129.42.0.0/29 - Portable Secondary Subnet
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

Now let's say you want VPS1 to have more IP addresses to segregate services it is providing. You can absolutely assign more addresses out of the 129.42.0.0/29 subnet, but you may want to only use that subnet to bring VMs online, not for their services. You have two options: 1) purchase another portable subnet 2) purchase a static subnet. If you recall from the descriptions of portable versus static subnets in [About Subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), you'll know that while portable subnets provide flexibility, they also don't give you access to all of the IP
addresses. If you only needed say four additional IP addresses, purchasing a static subnet is an efficient option. Let's try that out.

You purchase a static subnet and receive 129.42.0.100/30. During the purchase you route it to 129.42.0.3 or VPS1 in this scenario. Doing so provides you with all four IP addresses to use on whatever server is responding to 129.42.0.3, again, that's currently VPS1, but you could transfer 129.42.0.3 to VPS2 at any time and those four new IP addresses from 129.42.0.100/30 would follow! So let's look at the IP address utilization again:

129.42.0.0/29 - Portable Secondary Subnet
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

129.42.0.100/30 - Static Secondary Subnet
```
129.42.0.100 – 129.42.0.3 (aka VPS1)
129.42.0.101 – 129.42.0.3 (aka VPS1)
129.42.0.102 – 129.42.0.3 (aka VPS1)
129.42.0.103 – 129.42.0.3 (aka VPS1)
```

To recap, we used a portable subnet to make IP addresses available to all virtual machine hosts, and then made additional IP addresses available to a virtual machine by using a static subnet. You could definitely have used addresses out of the original portable subnet, or simply added another portable subnet. We hope this scenario illustrates that not only is it OK to route static subnets to IP addresses on portable subnets, but it is actually efficient and useful to do so.
