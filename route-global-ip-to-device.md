---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-05"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Route a Global IP Address to a Device

Global IP addresses are manually routed by the user to any device that {{site.data.keyword.BluSoftlayer_notm}} offers. To route a Global IP to a device, the device must be associated with the account that owns the Global IP. Follow the steps below to route a Global IP address to a device.

1. Navigate to the Global IP screen on the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/). Refer to [Display the Global IP Screen](display-global-ip-screen.html){:new_window}.
* Select the Global IP subnet to be routed.
* Begin typing the IP address of the device that the Global IP will route to in the **Routes to** field. This field will auto complete based on your input. It displays any device associated with your account.
* Enter any pertinent notes regarding the Global IP, device, or other items, in the **Notes** field.
* Select the **Update** button to complete the route, or select **Cancel** to cancel the action and return to the **Subnets** screen.

## What Happens Next

When you initiate the Global IP subnet route, the process begins. Routes generally take less than one minute to complete. At any time, the Global IP may be [unrouted](unroute-global-ip.html) from the device.
