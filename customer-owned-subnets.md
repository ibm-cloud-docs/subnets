---

copyright:
  years: 2024, 2024
lastupdated: "2024-08-28"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Customer-owned subnets for Classic
{: #customer-owned-subnets}

This topic explains how to use your own _public_ IP addresses on the IBM Cloud Classic platform. If you are looking for how to use your own _private_ IP addresses on the IBM Cloud Classic platform, see [Bring Your Own IP Address](/docs/solution-tutorials?topic=solution-tutorials-byoip).
{: shortdesc}

If you want to use your own public IP addresses, instead of the options provided by the IBM Cloud Classic platform, you can use your own public subnets. Using your public subnet gives you full control over the lifecycle and assignment of your public IP addresses and gives you the option to modify any Classic Regional Internet Registry (RIR) registration information that is announced for your subnet.

If you do not have your own public IP ranges, you must first purchase one. Due to the global exhaustion of public IPv4 subnet space, RIR organizations no longer directly offer IPv4 subnets. As a result, you must obtain the IP ranges from a third-party broker. IPv6 space is still readily available directly from RIR organizations.

With RADb's recent migration of their database from IRRDv3 to IRRDv4, any new or pre-existing BGP announcements whose RPKI status is flagged as "INVALID" may cause those announcements to be filtered. Please contact your Regional Internet Register (RIPE, ARIN, APNIC, etc) or third party broker and ensure that any new or pre-existing IP space has valid RPKI signatures. For more information, please visit https://www.radb.net/support/informational/irrdv4-migration-faq.html.
{: note}

The minimum subnet size that can be announced from IBM Cloud is `/24` for an IPv4 subnet, or `/48` for an IPv6 subnet.
{: note}

After you procure your subnet, [create an IBM Support case](/docs/get-support?topic=get-support-open-case&interface=ui) with the following information:

* List the specific IP ranges that you want to use.
* Provide a Letter of Authority (LoA) for the specific IP ranges to be used.
* Indicate whether this request is for existing servers or a new solution.
* Specify whether you want IBM Cloud to announce your IP ranges, or if you want to announce them yourself. If you prefer to announce your own IP ranges, you are charged a monthly recurring fee for each separate announcement.

   There is no charge if IBM Cloud announces on your behalf.
   {: note}

* Provide any additional questions or requirements.

## Next steps
{: #next-steps}

After you submit your IBM Support case, the following occurs:

1. The IBM Cloud Support team reviews and approves your request, or ask for any missing or unclear information.
1. After the support team approves your request:

   * If you request IBM Cloud to announce your IP ranges, the support team configures the announcement and confirms through the support case when completed.
   * If you request to announce your own IP ranges, the support team reviews your request, then works with you to set up the peering relationship between the device that you are announcing from and IBM Cloud front-end routers.
