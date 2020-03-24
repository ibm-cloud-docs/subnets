---

copyright:
  years: 1994, 2020
lastupdated: "2020-02-12"

keywords: primary IP, IP address, frequently asked questions

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:new_window: target="_blank"}
{:support: data-reuse='support'}

# FAQs
{: #faq}

## What does "Primary IP for future server only" mean when I look at a subnet's IP addresses?
{: #subnets-faq-primary-ip-future-server-only}
{: faq}
{: support}

Primary subnets are assigned and removed as needed by {{site.data.keyword.BluSoftlayer_notm}} for other resources you ordered, such as bare metal servers or virtual server instances. We don't assign one IP address at a time. We assign a subnet, meaning that there is sometimes additional room for future resources. This designation is stating that these addresses will be used by future resources. See [Can I use the other IP addresses that are defined by the primary subnets I see?](#subnets-faq-use-other-ip-addresses-primary-subnets) for reasons why you should not consider these usable IP addresses.


## Can I use the other IP addresses that are defined by the primary subnets I see?
{: #subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}
{: support}

No! We realize you see the primary subnets that are assigned by {{site.data.keyword.BluSoftlayer_notm}} as any other subnet, but as described in [About subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips), primary subnets are what provide IP addresses to resources on demand. We assign and remove primary subnets as we require to fulfill other products. If you attempt to use unassigned IP addresses from primary subnets, we will inevitably assign them to another resource at some point. This leads to IP conflicts on the network and general service disruption. We reserve the right to block or otherwise make unusable any IP address on a primary subnet, which is not assigned during fulfillment of other products. It is recommended you use "secondary subnets" for all additional IP (application/service) address needs. Secondary subnets are much more flexible and are maintained on your account for as long as you own them.


## Is there a way to specify which subnet I want to use for my device when I order it?
{: #subnets-faq-specify-which-subnet-on-order}
{: faq}
{: support}

Yes, you can specify a certain subnet during the ordering process. When ordering a device, this option is available at the end of the order form. After selection of a private VLAN, a list of primary subnets that are routed to that VLAN is presented. You can select a subnet. The same process can be repeated for the public VLAN and subnet.

It is important to note that submission of the order **does not guarantee** that an IP address is available in the requested subnet. If no addresses are available, you are contacted to determine a course of action. For the best {{site.data.keyword.BluSoftlayer_notm}} experience, selection of a subnet is discouraged for typical uses.


## I ran out of IP addresses, now what?
{: #subnets-faq-ran-out-of-addresses}
{: faq}
{: support}

We automatically assign primary subnets to make more IP addresses available to fulfill your compute purchases. You don't need to manage a thing. However, if you mean that you need more IP addresses for say local virtual machines or segregating applications, then read up on "secondary subnets" in [About subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips).


## How do I assign more IP addresses to a compute resource?
{: #subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}
{: support}

Purchase a secondary subnet. Because there are multiple types of subnets, it is a good idea to review [About subnets](/docs/subnets?topic=subnets-about-subnets-and-ips#about-subnets-and-ips). After you have a subnet that is routed to the IP address or VLAN you want, you'll want to refer to the specific compute documentation for how to set up your new IP addresses:

  * [Bare Metal Server IP address assignment](/docs/bare-metal?topic=bare-metal-bm-assigning-and-binding-ip-addresses#bm-assign-ip-address)                            
  * [Virtual Server Instance IP address assignment](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses#assigning-server-ip-addresses)


## What does "Reserved for HSRP" when I look at a subnet's IP addresses mean?
{: #subnets-faq-reserved-hsrp-meaning}
{: faq}
{: support}

In a decreasing number of locations, {{site.data.keyword.BluSoftlayer_notm}} has routers using a technique that is known as Hot Router Standby Protocol (HSRP). Specifically, the way it's used impacts the IP addresses available to "secondary portable subnets," meaning that you lose access to two more addresses in these locations. As the designation, "Reserved for HSRP", indicates, these IP addresses are reserved to fulfill the needs of HSRP. You might even have subnets on the same router, some with and some without, such reservations. As with any IP conflict, do not attempt to use these addresses or you risk affecting traffic on the entire subnet.

## Global IP FAQs
{: #global-ip-faq}
{: support}

The following section covers frequently asked questions about global IP.

## How long does it take for my new global IP to appear on my account after it's ordered?
{: #faq-global-ip-new-appear}
{: faq}
{: support}

It takes approximately five minutes for a global IP to appear after it was ordered.


## Can I convert one of my pre-existing static IPs to a global IP?
{: #faq-global-ip-convert-static-global}
{: faq}

No. {{site.data.keyword.BluSoftlayer_notm}} requires all global IP addresses to be newly provisioned IPs, so we don’t allow pre-existing IP addresses to be converted into global IPs.

## How long does it take for my global IP to associate to an instance?
{: #faq-global-ip-associate-instance}
{: faq}

The time that it takes for your global IP to associate depends on if you are associating a global IP for the first time, or if you are transferring it to a new instance. For new global IPs, it takes approximately five minutes before the address can be linked to an instance. When transferring an existing global IP between instances, it takes less than one minute.

## What types of subnets are available with global IPs?
{: #faq-global-ip-subnet-types}
{: faq}

We currently offer global IP addresses as both IPv4 addresses and IPv6 addresses. Our global IPv4 addresses are available as single /32 addresses, while our global IPv6 addresses are available as single /64 addresses.

## Can IPv4 and IPv6 global IPs be used interchangeably?
{: #faq-global-ip-ipv4-ipv6-interchangeably}
{: faq}

Because of incompatibility between IP address styles, you cannot use IPv4 and IPv6 global IPs interchangeably.

## What is a global IP?
{: #faq-what-is-global-ip}
{: faq}

A global IP is a static IP address, which can be transferred between bare metal servers or virtual servers that are associated with the account that owns the subnet. Global IPs can be moved to any compatible device or instance on the {{site.data.keyword.BluSoftlayer_notm}} network.

## How many global IP addresses may I order?
{: #faq-global-ip-how-many}
{: faq}

Each account can have up to five global IP addresses. A global IP can be either IPv4, IPv6, or both.

## How much does it cost to add a global IP to my account?
{: #faq-global-ip-how-much}
{: faq}

For global IP pricing, see the product breakdowns on our main site. Scroll down to IPv4 addresses and IPv6 addresses for global IP pricing for each type of address.
