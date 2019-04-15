---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-04"

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

# About Subnets and IPs
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} has specific terminology for the types, and uses, of subnets found on our platform. Knowing their intended use will help you know how best to use them in your cloud infrastructure.


## Types of Subnets
{:#subnet-types}

### Primary Subnets
{:#primary-subnets}

Primary Subnets are assigned automatically by {{site.data.keyword.BluSoftlayer_notm}}, and are what provide IP addresses to
resources as needed. We assign and remove Primary Subnets as required to fulfill other products. All servers will be provisioned with at least one IP address from a Primary Subnet, commonly referred to as a primary IP address. Some products and options result in more primary IP addresses being assigned.

It is important to understand that IP addresses within Primary Subnets, which are not yet assigned to resources, are not available for your use. If you attempt to use unassigned IP addresses from Primary Subnets we will inevitably assign them to another resource at some point. This leads to IP conflicts on the network and general service disruption. We reserve the right to block or otherwise make unusable any IP address on a Primary Subnet which is not specifically assigned during fulfillment of other products.

We **highly recommend** using **Secondary Subnets** as your external facing service/application IP addresses; especially when designing multi-server applications. Using the primary IP addresses assigned to your servers is perfectly fine. However, doing so lacks the flexibility of maintaining known addresses to your services which are agnostic of server cancellation and ordering. There are no guarantees made with regard to the order primary IP addresses are assigned in, such as ascending, descending, skipping gaps, etc.

Under no circumstances are we able to reserve IP addresses in Primary Subnets for your use.
{:note}

### Secondary Subnets
{:#secondary-subnets}

Secondary Subnets provide you with additional IP addresses for many needs. Unlike Primary Subnets, these subnets are owned by you for the duration of your use, and will not be removed unless you cancel them. Secondary subnets should be used when you need a stable IP address that should not be dependent of any specific compute device. Example uses include:

  * IP addresses you can assign to your own, local, virtual machines.
  * Multiple, distinct service IP addresses hosted by a single server allowing you to easily identify traffic. Commonly used with web servers and TLS.
  * A service IP address tied to DNS. Avoid DNS caching delays when shifting workloads to new servers (ie. the service IP won't change simply because a server's primary IP address does!).
  * High availability configurations which utilize "floating" IP address protocols.

To achieve such uses, and many more, we offer different routing options for Secondary Subnets. In order to help illustrate the differences between the Secondary Subnets we offer, we'll refer to the below example subnet in further explanations.

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

#### Static Subnets
{:#static-subnets}

A Static subnet provides a single destination with access to all IP addresses defined by that subnet. One benefit of using a Static subnet is that the destination device is able to utilize all IP addresses defined; not suffering the usual network, gateway, and broadcast address usage penalty. So using our example subnet, all addresses are usable:

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

Thus, if a server has IP address 10.0.0.13, and you routed 10.0.0.0/30 statically to 10.0.0.13, that server can now bind four additional IP addresses; receiving traffic on each individually. It is important to understand there is no Network Address Translation (NAT) being performed for any of the addresses provided. Each address can be used natively on servers, and thus each can be used for discrete purposes.

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |      |      |

#### Portable Subnet
{:#portable-subnet}

A Portable subnet provides its IP addresses to all resources on a VLAN. This means that any compute resource on the same VLAN can utilize any address provided by the subnet. This behavior is very useful for "floating" addresses across multiple resources, and decouples the subnet from any particular resource. A necessity of portable subnets is that not all IP addresses defined by the subnet are usable by devices. Networking mechanics require some of the IP addresses to be consumed. These consumed addresses are referred to as the broadcast, network, and gateway IP addresses. Notice the addresses which are
available in our example:

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
| Private Network  | Yes  |      |


### Global IP Addresses
{:#global-ip-addresses}

For information regarding the Global IP offering, please refer to the [Global IP documentation](/docs/infrastructure/subnets?topic=subnets-about-global-ip-address#about-global-ip-address).

| **Availability** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Public Network   | Yes  | Yes  |
| Private Network  |      |      |


## Canceling Subnets
{:#canceling-subnets}

If you no longer require a Secondary Subnet, follow these steps to cancel it:

  1. From your browser, open the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/){: new_window} and log into your account.
  1. In the Customer Portal navigation, select **Classic Infrastructure**. 
  1. From the Classic Infrastructure navigation menu, select **Network > IP Management > Subnets**.
  1. Choose any desired filters to locate the desired subnet.
  1. On the right hand side of the subnet's entry in the subnet list, a red circled with an X will be shown. Click on this icon to initiate the cancellation process.


## Product Specific Considerations when Ordering Subnets
{:#product-specific-considerations-subnets}

### Hardware Firewall (Shared)
{:#hardware-firewall-subnets}

Portable Subnets are not protected by firewalls by default. If you need this feature, please discuss it with your Sales representative. Secondary Subnets larger than /29 cannot be routed through this firewall offering.

### Transferring Portable Subnet IP Addresses Between Servers
{:#transferring-portable-subnet-ip-between-servers}

When transferring an IP address from one server to another, make sure a gratuitous ARP packet is sent. This allows our routers to update their ARP entry and forward traffic to the correct server. Not doing so could result in up to a 4 hour delay in the new server receiving traffic for the transferred address.

### Virtual Router Appliances
{:#virtual-router-appliances-subnets}

When ordering subnets for a VLAN behind a High Availability Virtual Router Appliance, ensure the subnet is configured correctly to allow for fail-over between the two appliances. Detailed assistance is described in the [VRA High Availability Configuration](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp) documentation.
