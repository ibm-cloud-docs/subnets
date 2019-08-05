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

# Static to VLAN Routed Subnets functionality is being deprecated
{: #deprecating-static-to-vlan-routed-subnets}

Over the years, some solutions utilized an off-menu Secondary Portable Subnet routing option which is referred to as "Routed to VLAN" or "Static to VLAN". The Static to VLAN routing option provides the behavior of Secondary Portable Subnets in terms of allowing multiple IP addresses to be used across multiple servers without the loss of network, gateway, or broadcast IP addresses. This routing method is not generally supported by all operating systems or applications, and poses unique challenges that inhibit flexibility.

The deprecation of the Static to VLAN functionality is retroactive, and in most cases, will require that you take actions to adjust. If you are affected by this change, you will be contacted directly in a Support Case. All relevant subnets and VLANs that require review will be provided. After determining your desired course of action for each item, maintenance windows will be coordinated with you for performing the adjustment activities.
{: important}

## Action required
{: #action-required}

You have 45 days from receipt of the Support Case to coordinate a transition plan, and 90 days to complete the transition plan. If you fail to communicate after 45 days, all Static to VLAN subnets will be disabled as indicated by the notice. 

Failure to respond in 45 days will cause traffic to stop on your VLANs. You will have 90 days from the date of the initial notice to coordinate completion of transition activities. At the end of 90 days, all Static to VLAN subnets will be reclaimed.
{: important} 

## Establish your transition plan
{: #establish-transition-plan}

For each of the subnets affected, you must identify the best course of action to take. This may require changing IP addresses used by your servers. The following scenarios provide some recommended courses of action. This is by no means an exhaustive list of scenarios or available options. We ask that you provide detailed descriptions of your usage of IP addresses and your environment so we can help you minimize the disruption. 

You can review the [Secondary Subnet summary](#secondary-subnets-summary) about the relevant Static to VLAN, Secondary Portable, and Secondary Static Subnet behaviors to help you determine a plan.

All actions require a few moments of service interruption, resulting in packet loss and the dropping of existing connections. These interruptions can be scheduled at your convenience, and can be done for each subnet individually, if necessary.
{: note}


### Scenario 1: Subnet is not needed
{: #subnet-not-needed}

If the subnet is not being used, cancel it.

### Scenario 2: All IP addresses are in-use by a single server
{: #all-ip-addresses-on-single-server}

You can have the subnet routed as a Secondary Static to the primary IP address of the server currently using the Static to VLAN IP addresses.


### Scenario 3: The Static to VLAN subnet is too small to convert to a Secondary Portable
{: #static-to-vlan-too-small-to-convert}

If a subnet is under a certain size (for instance, /30-/32), it cannot be converted to a Secondary Portable. If you want to use these addresses across multiple servers in a dynamic fashion (portability), it's recommended that you migrate to a new Secondary Portable Subnet which meets your needs. If portability is not necessary, then have the subnet routed as a Secondary Static to the desired server.

### Scenario 4: IP addresses in-use are not the network, gateway, or broadcast addresses
{: #ip-addresses-are-not-network-gateway-or-broadcast}

Route the subnet as a Secondary Portable, and all existing servers making use of the IP addresses should continue to function.

### Scenario 5: IP addresses in-use conflict with the network, gateway, or broadcast addresses
{: #ip-addresses-conflict-with-network-gateway-or-broadcast}

Discontinue use of the conflicting addresses and have the subnet routed as a Secondary Portable. If you require additional addresses due to the loss of the conflicting addresses, it may be best to order a new Secondary Portable Subnet and migrate to using it instead.

## Secondary Subnets summary
{: #secondary-subnets-summary}

In order to decide how best to proceed with changes, first take a look at the differences between the Static to VLAN option and the routing options that are available to transition to: Secondary Portable and Secondary Static.

A Static to VLAN subnet allows for all defined IP addresses to be usable by servers, referred to as "host addressable" later in this topic. Additionally, these IP addresses are usable by any server on the VLAN the subnet is routed to; referred to as  "portable". Any server that responds to an ARP for an address in this subnet will receive traffic for the address. For example, `10.54.28.80/29` would look like the following:

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

A Secondary Portable Subnet also provides IP addresses that are usable by any server on the VLAN, but it does so in a traditional way, where the gateway must consume an address on the subnet, and an address is defined for broadcast traffic. The IP address availability for a Secondary Portable Subnet looks like this:

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

Secondary Static Subnets are the most straightforward. Subnets routed in this way provide all of their IP addresses to a single server by directing all traffic to an existing IP address. This means the addresses are not portable, and multiple servers cannot use different IP addresses from a Secondary Static Subnet at the same time. However, the host can utilize all IP addresses from the subnet, making IP utilization more efficient. This means the IP address availability looks like the following, where `ABC` represents the same server with the primary IP address `10.0.0.29`:

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

It is possible to combine the portability of addresses afforded by Secondary Portable Subnets with the address efficiency of Secondary Static subnets. This can be done by addressing servers from a Secondary Portable Subnet, and then routing one or more Secondary Static Subnets to the portable IP address. For example:


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

If you then decide that host EFG is going to take over the portable IP address `10.54.28.84` by reconfiguring the operating system and sending a gratuitous ARP, the situation would change to this:


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

For further information about available subnets and their uses, refer to the [Secondary Subnet documentation](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#secondary-subnets).
