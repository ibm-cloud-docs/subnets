---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-04"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# About Global IP Addresses

A Global IP is a static IP address that can be transferred between {{site.data.keyword.baremetal_short}} or {{site.data.keyword.virtualmachinesshort}} associated with the account that owns the subnet. Global IPs can be moved to any compatible device on the {{site.data.keyword.BluSoftlayer_notm}} network.

Global IP addresses provide IP flexibility. They allow users to shift workloads between servers, even in different datacenters. Global IPs also provide IP persistence by allowing for transitions between servers and Virtual Server Instances (VSIs). For example, you can upgrade from a VSI to a dedicated system without having your IP tied to a particular server or VLAN.

## How to order Global IP addresses 

To order Global IPs, please follow these steps:

1. Through the customer portal [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/) navigate to **Network ->IP Management-> Subnets**, and then select [**Order IP Addresses**](https://control.softlayer.com/network/subnets/order).
* From the dropdown menu, choose **Global IPv4** or **Global IPv6** as needed, and select **Continue**
* Confirm the order, and the IP(s) will be added within a few minutes.

![Figure 1](images/1_2.png)
