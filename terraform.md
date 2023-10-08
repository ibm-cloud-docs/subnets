---

copyright:
  years: 2021, 2023
lastupdated: "2023-04-07"

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for subnets
{: #terraform-setup-subnets}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multi-tier cloud environments following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the provisioning, update, and deletion of your subnet resources by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with, but you don't have to worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for subnets
{: #install-terraform-subnets}

Before you can create an authorization by using Terraform, make sure that you have completed the following:

* Make sure that you have the [required access](/docs/account?topic=account-mngclassicinfra) to create and work with subnet resources.
* Install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in for Terraform. For more information, see the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started). The plug-in abstracts the {{site.data.keyword.cloud_notm}} APIs that are used to complete this task.
* Create a Terraform configuration file that is named `main.tf`. In this file, you define resources by using HashiCorp Configuration Language. For more information, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

1. Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create a subnet resource and to assign a user an access policy in Identity and Access Management (IAM) for that instance by using HashiCorp Configuration Language (HCL). For more information, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

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

1. After you finish building your configuration file, initialize the Terraform CLI. For more information, see [Initializing Working Directories](https://www.terraform.io/cli/init){: external}.

   ```terraform
   terraform init
   ```
   {: pre}

1. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the subnet resource in your account.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Create the subnet resource in {{site.data.keyword.cloud_notm}}.

   ```terraform
   terraform apply
   ```
   {: pre}

1. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, select the subnet resource that you created and note the resource ID.

## What's next?
{: #terraform-setup-next}

Now that you successfully created your subnet instance with Terraform on {{site.data.keyword.cloud_notm}}, you can visit the [Subnet Terraform registry](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/subnet){: external} to perform additional tasks using Terraform.
