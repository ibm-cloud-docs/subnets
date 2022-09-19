---

copyright:
  years: 2022
lastupdated: "2022-07-01"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Understanding network protection
{: #understanding-network-protect}

The network protection methods explained here are to protect IBM data centers, and are not to be regarded as a specific customer service. As such, network protection is not available for use as a DDoS mitigation protection service, and its enablement cannot be requested for personal use. For DDoS protection for your internet-facing workloads, consider [{{site.data.keyword.cis_full}}](/catalog/services/internet-services). 
{: note}

For more information about personal services available to you to further protect your infrastructure, contact your IBM Sales representative to discuss your options.

## About network protection
{: #about-network-protect}

IBM protects the data centers that support your cloud infrastructure from malicious attacks. However, the potential remains for a volumetric DDOS attack on any of your public IP addresses. The following mitigation processes are in place to help protect cloud infrastructure.

## Null route protection
{: #null-route-protect}

Null route protection is triggered when traffic that is routed to your public IP goes beyond a certain threshold. A static null route is applied to your public IP that effectively stops all traffic from the internet to that IP address at the edge of the IBM network. This static null route remains in place for 24 hours, after which traffic to your IP is reassessed. If traffic continues to exceed the threshold, your IP remains in a null route for another 24 hours. If the traffic is below the threshold, the static null route is then removed, allowing normal traffic flow to your IP again.

During periods of null route protection, a ticket is generated with the subject “DDOS: Automated System Alert – Null Route”. See the ticket for more details about why your traffic is being diverted.

Null route protection only applies to public IP addresses. If you suspect that your public IP address is blocked or restricted, access your customer portal and review the tickets.
{: note}

## Filtered protection
{: #filtered-protect}

Unlike null routing, filtered protection does not block or restrict your IP address from being reachable by the public internet. Protection devices analyze the traffic and use internal logic to determine if there is malicious traffic to filter. When triggered, filtered protection eliminates any suspicious traffic and allows legitimate traffic to flow to your host.

This protection remains in place until the traffic drops to appropriate levels within the threshold.

During periods of filtered protection, a ticket is generated with the subject “NETWORK ALERT: Automated Managed Network Alert”. See the ticket for more details about why your traffic is being diverted.

The internal logic used to filter malicious traffic might also filter legitimate traffic. If you find that legitimate traffic is filtered, contact IBM Support with the auto-generated ticket you received, and request further investigation.
{: note}

## Raising the threshold limit
{: #raise-threshold-limit}

Most customer traffic flow per IP address is less than 1 Gb/s. This includes customers that have ordered hosts with 10G and 25G interfaces. However, if you require inbound rates to be greater than this per IP address, and if your hosts on the account have 10G or 25G interfaces, you can reach out to IBM Support to discuss changing the network protection setting for an IP address to avoid triggering our network protection against your legitimate traffic.
