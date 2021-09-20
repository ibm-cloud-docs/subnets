---

copyright:
  years: 2021
lastupdated: "2021-08-12"

subcollection: subnets

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}


# Setting up Terraform for subnets
{: #terraform-setup-subnets}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multi-tier cloud environments following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the provisioning, update, and deletion of your subnet resources by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with, but you don't have to worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for subnets
{: #install-terraform-subnets}

To install Terraform and configure resources for subnets:

1. Follow the [Terraform on {{site.data.keyword.cloud}} getting started tutorial](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) to install the Terraform CLI and configure the {{site.data.keyword.cloud}} Provider plug-in for Terraform. The plug-in abstracts the {{site.data.keyword.cloud}} APIs that are used to provision, update, or delete subnet resources.

1. Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create a subnet resource. For more information, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The following example creates an `ibm_subnet` resource with a type of `Portable` and the `private` property set to `true`. This subnet has an IP version of `4`, a capacity of `4`, and is associated with a `vlan_id` of `1234567`.

      For more information, see the [ibm_subnet](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/subnet){: external} usage example.
      {: note}

   ```terraform
      resource "ibm_subnet" "portable_subnet" {
        type       = "Portable"
        private    = true
        ip_version = 4
        capacity   = 4
        vlan_id    = 1234567
        notes      = "portable_subnet"

        //User can increase timeouts
        timeouts {
          create = "45m"
        }
      }
   ```
   {: codeblock}

3. Initialize the Terraform CLI.

   ```
   terraform init
   ```
   {: pre}

4. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the subnet resource in your account.

   ```
   terraform plan
   ```
   {: pre}

5. Create the subnet resource in {{site.data.keyword.cloud_notm}}.

   ```
   terraform apply
   ```
   {: pre}

6. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, select the subnet resource that you created and note the resource ID.

