---

copyright:
  years: 2020
lastupdated: "2022-05-04"

keywords:

subcollection: subnets

---

{{site.data.keyword.attribute-definition-list}}

# Registering with the Regional Internet Registry
{: #rir}

The Regional Internet Registry (RIR) registration process associates personal or business identifiable information with an assigned subnet resource. By registering subnets, you affirm your presence on the internet, making data publicly available to a respective registrar and accessible through `whois` and `rwhois` services in association with your individual, or ranges of, assigned public IP addresses. The {{site.data.keyword.cloud_notm}} RIR Registration pages enable management of subnet registrations and the person records associated with them.
{: shortdesc}

## Registering a subnet with a RIR
{: #register-subnet-rir}
{: help}
{: support}

Any public subnet owned by {{site.data.keyword.cloud_notm}} which has been assigned to your account can be registered with its respective registrar. Navigate to the **RIR Registration** page and take the following steps to register a subnet.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > RIR Registration**.
1. Select **Create Registration** from the **Actions** list for a particular subnet. A **Register Subnet** window appears.
1. Select the Person Record you want to use for the registration. For more information, see [Creating an RIR registration with person details](#creating-rir-registration-person-details).
1. Click **Register** to create the RIR registration. The status of the registration is **Pending** until the registration is complete, at which point the status changes to **Complete**.

Registration times are not controlled internally, and they can vary based on the region in which the subnet is located.
{: note}

## Updating the registration information for a registered subnet
{: #update-registration-information-registered-subnet}
{: help}
{: support}

After a subnet completes its initial RIR registration, you can update the registration information for the subnet. Follow these steps to update the RIR registration for a subnet.

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/) and log in to your account.
1. From the dashboard, click the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) and select **Classic Infrastructure**.
1. Select **Network > IP Management > RIR Registration**.
1. Select **Edit Registration** from the **Actions** list for a registered subnet. An **Update Subnet** window appears, displaying the current registration information.
1. Select the Person Record you would like to use for the registration. For more information, see [Creating an RIR registration with person details](#creating-rir-registration-person-details).
1. Click **Register** to update the RIR registration. The status of the registration is **Pending** until the registration update is complete, at which point the status changes to **Complete**.

Registration update times are not controlled internally, and they can vary based on the region in which the subnet is located.
{: note}

## Creating an RIR registration with person details
{: #creating-rir-registration-person-details}
{: help}
{: support}

Several person records can be maintained on your account for use across multiple subnet registrations. A subnet registration must be associated to a single person record before attempting to inform the registrar of the associated network assignment. If invalid or poorly formatted data is present in the chosen person record, according to the targeted registrar, the registration request is rejected.

Registrar entities maintain different rules for formatting personal data, so it is possible for a person record to be successfully registered with one registrar and to be rejected by another.
{: note}

### Person record validation rules
{: #validations}

The following sections outline the various validation measures applied to person detail records and their properties when attempting to create or modify subnet registrations.

#### First Name
{: #first-name}

* First name is required.
* It can contain a maximum of five words.
* First name must not exceed 75 characters.
* The first word must begin with a letter.
* Only the following are valid for this field: a-z A-Z 0-9 `'` `-` and space.

#### Last Name
{: #last-name}

* Last name is required.
* It can contain a maximum of five words.
* Last name must not exceed 75 characters.
* The first word must begin with a letter.
* Only the following are valid for this field: a-z A-Z 0-9 `'` `-` and space.

#### Address
{: #address}

* Address is required.
* Address must be 2 - 200 characters.
* Only the following are valid for this field: a-z A-Z 0-9 `'` `#` `/` `&` `,` `.` `-` `:` and space.

#### City
{: #city}

* City name is required.
* City must be 2 - 50 characters.
* Only the following are valid for this field: a-z A-Z 0-9 `.` `'` `-` and space.

#### Postal code
{: #postal-code}

* Postal code is required for certain locales.
* Postal code cannot exceed 15 characters.
* Only the following are valid for this field: a-z A-Z 0-9 `-` and space.

#### Country
{: #country}

* Country is required.
* Country code must equal 2 characters, in compliance with [ISO 3166-1](https://www.nro.net/list-of-country-codes-and-rirs-ordered-by-country-code){: external}.

#### State
{: #state}

* State is required for certain locales.

#### Phone
{: #phone}

* Phone is required.
* Only the following are valid for this field: a-z A-Z 0-9 `(` `)` `+` `.` `-` and space.
* Contact telephone number. Can take one of the forms:
    * `+<integer-list>`
        * Examples - `+012-3456`, `+12345689457920`
    * `+<integer-list> (<integer-list> )<integer-list>`
        * Example - `+01 (234)567-8901`
    * `+<integer-list> ext.<integer-list>`
        * Example - `+012-345-6789 ext.123`
    * `+<integer-list> ( integer-list ) <integer-list> ext. <integer-list>`
        * Example - `+012 (345) 678-9012 ext. 123`

#### Email
{: #email}

* A valid email address is required.
