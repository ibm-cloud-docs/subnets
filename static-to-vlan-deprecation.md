---
copyright:
  years: 2019
lastupdated: "2019-07-24"

keywords: routed to vlan, static to vlan, deprecate, deprecation

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:DomainName: data-hd-keyref="DomainName"} 
{:note: .note}
{:tip: .tip}
{:important: .important}

# Static to VLAN-routed subnets functionality is being deprecated
{: #deprecating-static-to-vlan-routed-subnets}

Over the years, some solutions used an off-menu secondary portable subnet routing option, which is referred to as "Routed to VLAN" or "Static to VLAN". The static-to-VLAN routing option provides the behavior of secondary portable subnets in terms of allowing multiple IP addresses to be used across multiple servers without the loss of network, gateway, or broadcast IP addresses. This routing method is not generally supported by all operating systems or applications, and poses unique challenges that inhibit flexibility.

The deprecation of the static-to-VLAN functionality is retroactive, and in most cases, requires that you take actions to adjust. If you are affected by this change, you are contacted directly in an IBM Support case. All relevant subnets and VLANs that require review are provided. After determining your course of action for each item, maintenance windows are coordinated with you for performing the adjustment activities.
{: important}

## Action required
{: #action-required}

You have 45 days from receipt of the IBM Support case to coordinate a transition plan, and 90 days to complete the transition plan. If you fail to communicate after 45 days, all static-to-VLAN subnets are disabled as indicated by the notice. 

Failure to respond in 45 days causes traffic to stop on your VLANs. You have 90 days from the date of the initial notice to coordinate completion of transition activities. At the end of 90 days, all static-to-VLAN subnets are reclaimed.
{: important} 

## Establishing your transition plan
{: #establish-transition-plan}

For each of the subnets affected, you must identify the best course of action to take. This might require changing IP addresses that are used by your servers. The following scenarios provide some recommended courses of action. This is by no means an exhaustive list of scenarios or available options. We ask that you provide detailed descriptions of your usage of IP addresses and your environment so that we can help you minimize the disruption. 

You can review the [secondary subnet summary](#secondary-subnets-summary) about the relevant static-to-VLAN, secondary portable, and secondary static subnet behaviors to help you determine a plan.

All actions require a few moments of service interruption, resulting in packet loss and the dropping of existing connections. These interruptions can be scheduled at your convenience, and can be done for each subnet individually, if necessary.
{: note}


### Scenario 1: Subnet is not needed
{: #subnet-not-needed}

If the subnet is not being used, cancel it.

### Scenario 2: All IP addresses are in-use by a single server
{: #all-ip-addresses-on-single-server}

You can have the subnet that is routed as a secondary static to the primary IP address of the server currently using the static-to-VLAN IP addresses.


### Scenario 3: The Static to VLAN subnet is too small to convert to a Secondary Portable
{: #static-to-vlan-too-small-to-convert}

If a subnet is under a certain size (for instance, /30-/32), it cannot be converted to a secondary portable. If you want to use these addresses across multiple servers in a dynamic fashion (portability), it's recommended that you migrate to a new secondary portable subnet, which meets your needs. If portability is not necessary, then have the subnet routed as a secondary static to the server.

### Scenario 4: IP addresses in-use are not the network, gateway, or broadcast addresses
{: #ip-addresses-are-not-network-gateway-or-broadcast}

Route the subnet as a secondary portable, and all existing servers making use of the IP addresses should continue to function.

### Scenario 5: IP addresses in-use conflict with the network, gateway, or broadcast addresses
{: #ip-addresses-conflict-with-network-gateway-or-broadcast}

Discontinue use of the conflicting addresses and have the subnet that is routed as a secondary portable. If you require additional addresses due to the loss of the conflicting addresses, it may be best to order a new secondary portable subnet and migrate to using it instead.

## Secondary subnets summary
{: #secondary-subnets-summary}

To decide how best to proceed with changes, first look at the differences between the static-to-VLAN option and the routing options that are available to transition to: secondary portable and secondary static.

A static-to-VLAN subnet allows for all defined IP addresses to be usable by servers, referred to as "host addressable" later in this topic. Additionally, these IP addresses are usable by any server on the VLAN the subnet is routed to; referred to as "portable". Any server that responds to an ARP for an address in this subnet receives traffic for the address. For example, `10.54.28.80/29` would look like the following:

```
10.54.28.80/29
10.54.28.80 - host addressable
10.54.28.81 - host addressable
10.54.28.82 - host addressable
10.54.28.83 - host addressable
10.54.28.84 - host addressable
10.54.28.85 - host addressable
10.54.28.86 - host addressable
10.54.28.87 - host addressable
```

A secondary portable subnet also provides IP addresses that are usable by any server on the VLAN, but it does so in a traditional way, where the gateway must consume an address on the subnet, and an address is defined for broadcast traffic. The IP address availability for a secondary portable subnet looks like this:

```
10.54.28.80/29
10.54.28.80 - network
10.54.28.81 - gateway
10.54.28.82 - host addressable
10.54.28.83 - host addressable
10.54.28.84 - host addressable
10.54.28.85 - host addressable
10.54.28.86 - host addressable
10.54.28.87 - broadcast
```

Notice that three addresses of the possible eight are no longer available to servers on the VLAN.

Secondary static subnets are the most straightforward. Subnets that are routed in this way provide all of their IP addresses to a single server by directing all traffic to an existing IP address. This means that the addresses are not portable, and multiple servers cannot use different IP addresses from a secondary static subnet at the same time. However, the host can use all IP addresses from the subnet, making IP use more efficient. This means that the IP address availability looks like the following, where `ABC` represents the same server with the primary IP address `10.0.0.29`:

Server `ABC`with IP address `10.0.0.29`, and `10.54.28.80/29` is routed to `10.0.0.29`:


```
10.54.28.80/29
10.54.28.80 - host ABC
10.54.28.81 - host ABC
10.54.28.82 - host ABC
10.54.28.83 - host ABC
10.54.28.84 - host ABC
10.54.28.85 - host ABC
10.54.28.86 - host ABC
10.54.28.87 - host ABC
```

### Secondary Static to Secondary Portable Subnets
{: #secondary-static-to-secondary-portable-subnets}

It is possible to combine the portability of addresses afforded by secondary portable subnets with the address efficiency of secondary static subnets. This can be done by addressing servers from a secondary portable subnet, and then routing one or more secondary static subnets to the portable IP address. For example:


```
10.54.28.80/29 - Secondary Portable
10.54.28.80 - network
10.54.28.81 - gateway
10.54.28.82 - host addressable
10.54.28.83 - host addressable
10.54.28.84 - host XYZ
10.54.28.85 - host addressable
10.54.28.86 - host addressable
10.54.28.87 - broadcast
```


```
10.100.134.204/30 - Secondary Static routed to 10.54.28.84 (ie. host XYZ)
10.100.134.204 - host XYZ
10.100.134.205 - host XYZ
10.100.134.206 - host XYZ
10.100.134.207 - host XYZ
```

If you then decide that host EFG is going to take over the portable IP address `10.54.28.84` by reconfiguring the operating system and sending a gratuitous ARP, the situation changes to this:


```
10.54.28.80/29 - Secondary Portable
10.54.28.80 - network
10.54.28.81 - gateway
10.54.28.82 - host addressable
10.54.28.83 - host addressable
10.54.28.84 - host EFG
10.54.28.85 - host addressable
10.54.28.86 - host addressable
10.54.28.87 - broadcast
```


```
10.100.134.204/30 - Secondary Static routed to 10.54.28.84 (ie. now host EFG)
10.100.134.204 - host EFG
10.100.134.205 - host EFG
10.100.134.206 - host EFG
10.100.134.207 - host EFG
```

For more information about available subnets and their uses, see [secondary subnet documentation](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets).
