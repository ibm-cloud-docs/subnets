---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-03"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQ

## How are server IP addresses assigned on the {{site.data.keyword.BluSoftlayer_notm}} Network?

We provision servers with a single private Primary IPv4 Address that is associated to the device.  Each server may optionally have a single public Primary IPv4 Address and a single public Primary IPv6 Address.  All other IP addresses associated with a server must be assigned from a secondary subnet, which may be purchased through the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/).

Subnets are created for customers on a case-by-case basis, which involves a vetting process that looks at an IP-to-server ratio.
