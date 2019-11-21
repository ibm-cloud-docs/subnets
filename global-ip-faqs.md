---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: global IP FAQ, new global IP, global IP address

subcollection: subnets

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Global IP FAQs
{: #global-ip-faq}


## How long does it take for my new global IP to appear on my account after it is ordered?
{: #faq-global-ip-new-appear} 


It takes approximately five minutes for a global IP to appear after it was ordered.


## Can I convert one of my pre-existing static IPs to a global IP?
{: #faq-global-ip-convert-static-global} 


Not at this time. {{site.data.keyword.BluSoftlayer_notm}} requires all global IP addresses to be newly provisioned IPs, so we don’t allow pre-existing IP addresses to be converted into global IPs.


## How long does it take for my global IP to associate to an instance?
{: #faq-global-ip-associate-instance} 


The amount of time it takes for your global IP to associate depends on if you are associating a global IP for the first time or if you are transferring the Global IP to a new instance. For new global IPs, it takes approximately five minutes before the address can be linked to an instance. When transferring an existing global IP between instances, it takes less than one minute.


## What types of subnets are available with global IPs?
{: #faq-global-ip-subnet-types} 


We currently offer global IP addresses as both IPv4 addresses and IPv6 addresses. Our global IPv4 addresses are available as single /32 addresses, while our global IPv6 addresses are available as single /64 addresses.


## Can IPv4 and IPv6 global IPs be used interchangeably?
{: #faq-global-ip-ipv4-ipv6-interchangeably} 


Because of incompatibility between IP address styles, you cannot use IPv4 and IPv6 global IPs interchangeably.


## What is a global IP?
{: #faq-what-is-global-ip} 


A global IP is a static IP address that can be transferred between bare metal servers or virtual servers that are associated with the account that owns the subnet. Global IPs can be moved to any compatible device or instance on the {{site.data.keyword.BluSoftlayer_notm}} network.


## How many global IP addresses may I order?
{: #faq-global-ip-how-many} 


Each account can have up to five global IP addresses. Global IPs can be either IPv4, IPv6, or both.


## How much does it cost to add a global IP to my account?
{: #faq-global-ip-how-much} 


For global IP pricing, refer to the product breakdowns on our main site. Scroll down to IPv4 addresses and IPv6 addresses for global IP pricing for each type of address.
