---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-08-07"

keywords: Primary IP, IP address, Frequently Asked Questions

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:new_window: target="_blank"}

# FAQs
{: #faq}

## What does "Primary IP for future server only" when I look at a subnet's IP addresses mean?
{: #subnets-faq-primary-ip-future-server-only}
{: faq}

Primary Subnets are assigned and removed as needed by {{site.data.keyword.BluSoftlayer_notm}} for other resources you've ordered, such as Bare Metal Servers or Virtual Server Instances. We don't simply assign one IP address at a time, we assign a subnet. This means there is sometimes additional room for future resources. This designation is stating that these addresses will be used by future resources. Please see the question, **Can I use the other IP addresses defined by the Primary Subnets I see?** for why you should not consider these IP addresses as usable.


## Can I use the other IP addresses defined by the Primary Subnets I see?
{: #subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

No! We realize you see the Primary Subnets assigned by {{site.data.keyword.BluSoftlayer_notm}} as any other subnet, but as described in [About Subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips), Primary Subnets are what provide IP addresses to resources on demand. We assign and remove Primary Subnets as we require to fulfill other products. If you attempt to use unassigned IP addresses from Primary Subnets, we will inevitably assign them to another resource at some point. This leads to IP conflicts on the network and general service disruption. We reserve the right to block or otherwise make unusable any IP address on a Primary Subnet which is not specifically assigned during fulfillment of other products. You should use **Secondary Subnets** for all additional IP address needs, and we strongly encourage you to use them for your application/service address needs. Secondary Subnets are much more flexible and are maintained on your account for as long as you own them.


## Is there a way to specify which subnet I want to use for my device when I order it?
{: #subnets-faq-specify-which-subnet-on-order}
{: faq}

Yes, a specific subnet may be specified during the ordering process. When ordering a device, this option is available at the end of the order form. After selection of a private VLAN, a list of Primary Subnets routed to that VLAN is presented. You may select a desired subnet. The same process can be repeated for the public VLAN and subnet.

It is important to note that submission of the order **does not guarantee** that an IP address is available in the requested subnet. If no addresses are available, you will be contacted in order to determine a course of action. For the best {{site.data.keyword.BluSoftlayer_notm}} experience, selection of a subnet is discouraged for typical uses.


## I ran out of IP addresses, now what?
{: #subnets-faq-ran-out-of-addresses}
{: faq}

This won't happen! We automatically assign Primary Subnets to make more IP addresses available to fulfill your compute purchases. You don't need to manage a thing. However, if you mean that you need more IP addresses for say local virtual machines or segregating applications, then read up on **Secondary Subnets** in [About Subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips).


## How do I assign more IP addresses to a compute resource?
{: #subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

First, you'll want to purchase a **Secondary Subnet**, there are multiple types, so review [About Subnets](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips). Once you have a subnet routed to the IP address or VLAN desired, you'll want to refer to the specific compute documentation for how to setup your new IP addresses:
  * [Bare Metal Server IP address assignment](/docs/bare-metal?topic=bare-metal-assigning-and-binding-ip-addresses#bm-assign-ip-address)
  * [Virtual Server Instance IP address assignment](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses#assigning-server-ip-addresses)


## What does "Reserved for HSRP" when I look at a subnet's IP addresses mean?
{: #subnets-faq-reserved-hsrp-meaning}
{: faq}

In a decreasing number of locations, {{site.data.keyword.BluSoftlayer_notm}} has routers utilizing a technique known as Hot Router Standby Protocol or HSRP. Specifically, the way it is used impacts the IP addresses available to ***Secondary Portable Subnets***; meaning you will lose access to two additional addresses in these locations. As the designation, "Reserved for HSRP", indicates, these IP addresses are reserved to fulfill the needs of HSRP. You may even have subnets on the same router, some with and some without, such reservations. As with any IP conflict, please do not attempt to use these addresses or you risk affecting traffic on the entire subnet.

## Global IP FAQ
{: #global-ip-faq}
{: faq}

The following section covers frequently asked questions about Global IP.

### How long does it take for my new Global IP to appear on my account after it has been ordered?
{: #faq-global-ip-new-appear}
{: faq}

It takes approximately five (5) minutes for a Global IP to appear after it has been ordered.


### Can I convert one of my pre-existing static IPs to a Global IP?
{: #faq-global-ip-convert-static-global}
{: faq}

Not at this time. {{site.data.keyword.BluSoftlayer_notm}} requires all Global IP addresses to be newly provisioned IPs, so we don’t allow pre-existing IP addresses to be converted into Global IPs.


### How long does it take for my Global IP to associate to an instance?
{: #faq-global-ip-associate-instance}
{: faq}

The amount of time it takes for your Global IP to associate depends on if you are associating a Global IP for the first time or if you are transferring the Global IP to a new instance. For new Global IPs, it takes approximately five (5) minutes before the address may be linked to an instance. When transferring an existing Global IP between instances, it takes less than one (1) minute.


### What types of subnets are available with Global IPs?
{: #faq-global-ip-subnet-types}
{: faq}

We currently offer Global IP addresses as both IPv4 addresses and IPv6 addresses. Our Global IPv4 addresses are available as single /32 addresses, while our Global IPv6 addresses are available as single /64 addresses.


### Can IPv4 and IPv6 Global IPs be used interchangeably?
{: #faq-global-ip-ipv4-ipv6-interchangeably}
{: faq}

Because of incompatibility between IP address styles, using IPv4 and IPv6 Global IPs interchangeably is not an option.


### What is a Global IP?
{: #faq-what-is-global-ip}
{: faq}

A Global IP is a static IP address that can be transferred between Bare Metal Servers or Virtual Servers associated with the account that owns the subnet. Global IPs can be moved to any compatible device or instance on the {{site.data.keyword.BluSoftlayer_notm}} network.


### How many Global IP addresses may I order?
{: #faq-global-ip-how-many}
{: faq}

Each account may have up to five (5) single Global IP addresses. Global IPs may be either IPv4 or IPv6, or a combination of the two.


### How much will it cost to add a Global IP to my account?
{: #faq-global-ip-how-much}
{: faq}

For Global IP pricing, please refer to the product breakdowns on our main site. Scroll down to IPv4 addresses and IPv6 addresses for Global IP pricing for each type of address.
