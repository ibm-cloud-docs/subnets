---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-11-20"

keywords: IP addresses , IP address, duration of your use

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# About subnets and IPs
{:#about-subnets-and-ips}

{{site.data.keyword.cloud_notm}} has specific terminology for the types, and uses, of subnets found on the {{site.data.keyword.cloud_notm}} platform. Knowing their intended use helps you understand how best to use them in your cloud infrastructure.


## Types of subnets
{:#subnet-types}

### Primary subnets
{:#primary-subnets}

Primary subnets are assigned automatically by {{site.data.keyword.cloud_notm}}, and are what provide IP addresses to
resources as needed. IBM assigns and removes primary subnets as required to fulfill other products. All servers are provisioned with at least one IP address from a primary subnet, commonly referred to as a primary IP address. Some products and options result in more primary IP addresses being assigned.

It is important to understand that IP addresses within primary subnets, which are not yet assigned to resources, are not available for your use. If you attempt to use unassigned IP addresses from primary subnets, these subnets are inevitably assigned to another resource at some point. This leads to IP conflicts on the network and general service disruption. We reserve the right to block or otherwise make unusable any IP address on a primary subnet, which is not assigned during fulfillment of other products.

The use of secondary subnets as your external facing service/application IP addresses is highly recommended, especially when designing multi-server applications. Using the primary IP addresses assigned to your servers is perfectly fine. However, doing so lacks the flexibility of maintaining known addresses to your services, which are agnostic of server cancellation and ordering. No guarantees are made regarding the order primary IP addresses are assigned in, such as ascending, descending, and skipping gaps.

Under no circumstances are we able to reserve IP addresses in primary subnets for your use.
{:note}

### Secondary subnets
{:#secondary-subnets}

Secondary subnets provide additional, independent IP addresses for your compute resources. Perfect for use as external application or service addresses. Secondary subnet IP addresses are managed independently of other resources and are yours until canceled.

Secondary subnets come in "data center" and "global" flavors, the latter referred to as global IP. For more information, see [Getting started with Subnets and IPs](/docs/infrastructure/subnets?topic=subnets-getting-started).

Features:

-   Data center and globally routable public IPv4 and IPv6 IP addresses
-   Data center routable private IPv4 IP addresses
-   IPv4 /32 to /24 and IPv6 /64 blocks available
-   Provide unique IP addresses to virtual machines capable of portability across hosts
-   Address your services individual, maintaining a stable IP address when migrating to new compute resources
-   High availability configurations, which use virtual/floating IP address protocols
-   Route to a disaster recovery site in any data center that uses a global IP.

Secondary subnets provide you with multiple IP addresses for many needs. Unlike primary subnets, these subnets are owned by you for the duration of your use, and are not removed unless you cancel them. Use secondary subnets when you need a stable IP address that does not depend on any specific compute device. Example uses include:

  * IP addresses that you can assign to your own, local, virtual machines
  * Multiple, distinct service IP addresses hosted by a single server allowing you to easily identify traffic. Commonly used with web servers and TLS
  * A service IP address that is tied to DNS. Avoid DNS caching delays when shifting workloads to new servers; in other words, the service IP won't change simply because a server's primary IP address does.
  * High availability configurations, which use "floating" IP address protocols.

To achieve such uses, and many more, we offer different routing options for secondary subnets. To help illustrate the differences between the secondary subnets we offer, the following example is referenced in further explanations.

Here is an example of the IP addresses provided by the subnet 10.0.0.0/29:
```
10.0.0.0
10.0.0.1
10.0.0.2
10.0.0.3
10.0.0.4
10.0.0.5
10.0.0.6
10.0.0.7
```

#### Static subnets
{:#static-subnets}

A secondary static subnet provides a single destination with access to all IP addresses defined by that subnet. One benefit of using a static subnet is that the destination device is able to use all IP addresses defined; not suffering the usual network, gateway, and broadcast address usage penalty. So using our example subnet, all addresses are usable:

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

Thus, if a server has IP address 10.0.0.13, and you routed 10.0.0.0/30 statically to 10.0.0.13, that server can now bind four additional IP addresses, receiving traffic on each individually. It is important to understand that Network Address Translation (NAT) is not performed for any of the addresses provided. Each address can be used natively on servers, and thus each can be used for discrete purposes.

The following IP addresses are eligible as route targets for static subnets within the same data center:

  * Any primary IP address that is assigned to a bare metal server or virtual server instance.
  * Any virtual (floating) IP address that is assigned to a gateway or Virtual Router Appliance (VRA).
  * Any portable subnet IP address, excluding network, gateway, and broadcast addresses.

The following IP addresses are NOT eligible as route targets for static subnets:

  * Any static subnet IP address
  * Any IPv6 address, as an IPv4 Static subnet route target
  * Any IPv4 address, as an IPv6 Static subnet route target.

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |  No  | No   |

#### Portable subnet
{:#portable-subnet}

A secondary "portable" subnet provides its IP addresses to all resources on a VLAN. Therefore, any compute resource on the same VLAN can use any address that is provided by the subnet. This behavior is useful for "floating" addresses across multiple resources, and decouples the subnet from any particular resource. A necessity of portable subnets is that not all IP addresses defined by the subnet are usable by devices. Networking mechanics require some of the IP addresses to be consumed. These consumed addresses are referred to as the broadcast, network, and gateway IP addresses. Notice the addresses, which are available in our example:

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  | Yes  | No   |


### Global IP addresses
{:#global-ip-addresses}

For information regarding the global IP offering, see [Global IP documentation](/docs/infrastructure/subnets?topic=subnets-about-global-ip-address#about-global-ip-address).

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  | No   | No   |


## Canceling subnets
{:#canceling-subnets}

If you no longer require a secondary subnet, follow these steps to cancel it:

  1. From your browser, open the [customer portal](https://{DomainName}/){: new_window} and log in to your account.
  1. In the customer portal navigation, select **Classic Infrastructure**.
  1. From the Classic Infrastructure navigation menu, select **Network > IP Management > Subnets**.
  1. Choose filters to locate the subnet that you want.
  1. Click the Cancel icon next to the subnet's entry in the subnet list to initiate the cancellation process.

## Product-specific considerations when ordering subnets
{:#product-specific-considerations-subnets}

### Hardware Firewall (Shared)
{:#hardware-firewall-subnets}

By default, portable subnets are not protected by firewalls. If you need this feature, discuss it with your IBM Sales representative. Secondary subnets larger than /29 cannot be routed through this firewall offering.

### Transferring portable subnet IP addresses between servers
{:#transferring-portable-subnet-ip-between-servers}

When transferring an IP address from one server to another, make sure that a gratuitous ARP packet is sent. This allows our routers to update their ARP entry and forward traffic to the correct server. Not doing so might result in up to a 4-hour delay in the new server receiving traffic for the transferred address.

### Virtual Router Appliances
{:#virtual-router-appliances-subnets}

When ordering subnets for a VLAN behind a High Availability (HA) Virtual Router Appliance (VRA), ensure that the subnet is configured correctly to allow for fail-over between the two appliances. For more information, see [VRA High Availability Configuration](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
