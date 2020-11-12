---

copyright:
  years: 1994, 2020
lastupdated: "2020-10-28"

keywords: 

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}
{:screen: .screen}

# About subnets and IPs
{:#about-subnets-and-ips}

{{site.data.keyword.cloud}} has specific terminology for the types, and uses, of subnets. Knowing their intended use helps you understand how best to use them in your cloud infrastructure.
{:shortdesc}

To understand subnets and subnetting in general, review [Subnetwork](https://en.wikipedia.org/wiki/Subnetwork){:external}.
Additionally, subnets are referred to in [CIDR notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing){:external}.

## Primary subnets
{:#primary-subnets}

Primary subnets are assigned automatically and managed by {{site.data.keyword.cloud_notm}}. IBM assigns and removes primary subnets as required to fulfill other services. IBM provides IP addresses to resources from primary subnets as needed. All servers are provisioned with at least one IP address from a primary subnet, commonly referred to as a primary IP address. Some services and options result in more than one primary IP addresses being assigned.

IP addresses within primary subnets which are not yet assigned to resources are not available for use. Attempting to use unassigned IP addresses from primary subnets can lead to IP conflicts on the network and general service disruption. IBM reserves the right to block, or otherwise make unusable, any IP address on a primary subnet which is not assigned during fulfillment of other services. Use secondary subnets as your external facing service/application IP addresses.

IP addresses in primary subnets cannot be reserved.
{:note}

## Secondary subnets
{:#secondary-subnets}

Secondary subnets provide additional, independent IP addresses for your compute resources, and are well suited for use as external application or service addresses. Secondary subnet IP addresses are managed independently of other resources and are yours until canceled.

Secondary subnets can be provisioned local to the data center or global. 

### Features and use cases

Secondary subnets have the following features:

-   Data center and globally routable public IPv4 and IPv6 IP addresses
-   Data center routable private IPv4 IP addresses
-   IPv4 /32 to /24 and IPv6 /64 blocks available
-   Provide unique IP addresses to virtual machines capable of portability across hosts
-   Address your services individually, maintaining a stable IP address when migrating to new compute resources
-   High availability configurations, which use virtual/floating IP address protocols
-   Route to a disaster recovery site in any data center that uses a global IP

Secondary subnets provide you with multiple IP addresses for many needs. Unlike primary subnets, these subnets are owned by you during your use, and are not removed unless you cancel them. Use secondary subnets when you need a stable IP address that does not depend on any specific compute device. Example uses include:

- IP addresses that you can assign to your own, local, virtual machines
- Multiple, distinct service IP addresses hosted by a single server allowing you to easily identify traffic (commonly used with web servers and TLS)
- A service IP address that is tied to DNS, so you can avoid DNS caching delays when shifting workloads to new servers; in other words, the service IP won't change simply because a server's primary IP address does
- High availability configurations, which use floating IP address protocols

IBM offers different routing options for secondary subnets. To help illustrate the differences between the secondary subnets offered, the following example is referenced in further explanations.

Available IP addresses provided by the subnet `10.0.0.0/29`:

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
{:screen}

### Static subnets
{:#static-subnets}

A secondary static subnet provides a single destination with access to all IP addresses defined by that subnet. One benefit of using a static subnet is that the destination device is able to use all IP addresses defined; not suffering the usual network, gateway, and broadcast address usage penalty. So, using the example subnet `10.0.0.0/29`, all addresses are usable:

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
{:screen}

As a result, if a server has the IP address `10.0.0.13`, and you routed `10.0.0.0/30` statically to `10.0.0.13`, that server can now bind four more IP addresses, receiving traffic on each individually. Note that Network Address Translation (NAT) is not done for any of the addresses provided. Each address can be used natively on servers, and so can be used for discrete purposes.

The following IP addresses are eligible as route targets for static subnets within the same data center:

  * Any primary IP address that is assigned to a bare metal server or virtual server instance
  * Any virtual (floating) IP address that is assigned to a gateway or Virtual Router Appliance (VRA)
  * Any portable subnet IP address, excluding network, gateway, and broadcast addresses

The following IP addresses are _not_ eligible as route targets for static subnets:

  * Any static subnet IP address
  * Any IPv6 address, as an IPv4 Static subnet route target
  * Any IPv4 address, as an IPv6 Static subnet route target

| Availability | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |  No  | No   |

### Portable subnet
{:#portable-subnet}

A secondary portable subnet provides its IP addresses to all resources on a VLAN. Therefore, any compute resource on the same VLAN can use any address that is provided by the subnet. This behavior is useful for floating addresses across multiple resources, and decouples the subnet from any particular resource. In a portable subnet, not all IP addresses defined by the subnet are usable by devices. Networking mechanics require some of the IP addresses to be consumed. These consumed addresses are referred to as the broadcast, network, and gateway IP addresses. Notice the addresses, which are available in the example:

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
{:screen}

| Availability | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  | Yes  | No   |


### Global IP addresses
{:#global-ip-addresses}

A global IP address is a specialized secondary static subnet that can be routed to any data center, on demand.

Global IP addresses are available as either an IPv4 /32 subnet (a single IP address), or an IPv6 /64 subnet. Each version can be routed only to a destination IP address of matching version (no address translation is performed). Acceptable routing targets include public primary IP addresses in use by your servers and any public secondary portable subnet IP addresses. The unique capabilities of a global IP address are:

  * Global, on-demand routing to IP addresses on an account
  * Global IP address internet announcement by all {{site.data.keyword.cloud}} edge routers
  
As result, your data takes the shortest path to the {{site.data.keyword.cloud}} network, and from there your traffic traverses the IBM Cloud dedicated, global backbone to reach the destination you configured.

Global IP addresses provide the flexibility to shift workloads between servers, even across geographically disparate data centers. Global IP addresses also provide IP persistence by allowing for transitions without a need to adapt (for example, to avoid DNS caches). The global routing capability is well suited for transitioning workloads across disaster recovery sites, or seamlessly migrating to a new deployment in a geographic area that can serve your audience better.

| Availability | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  | No   | No   |


## Product-specific considerations when ordering subnets
{:#product-specific-considerations-subnets}

The following considerations are product-specific, and should be noted when ordering your subnets.

### Hardware Firewall
{:#hardware-firewall-subnets}

By default, portable subnets are not protected by firewalls. If you need this feature, discuss it with your IBM Sales representative. Secondary subnets larger than `/29` cannot be routed through this firewall offering.

### Transferring portable subnet IP addresses between servers
{:#transferring-portable-subnet-ip-between-servers}

When transferring an IP address from one server to another, make sure that a gratuitous ARP packet is sent. This action allows IBM's routers to update their ARP entry and forward traffic to the correct server. Not doing so might result in up to a 4-hour delay in the new server receiving traffic for the transferred address.

### Virtual Router Appliance
{:#virtual-router-appliances-subnets}

When ordering subnets for a VLAN behind a High Availability (HA) Virtual Router Appliance (VRA), ensure that the subnet is configured correctly to allow for fail-over between the two appliances. For more information, see [Working with High Availability (HA) and VRRP](/docs/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
