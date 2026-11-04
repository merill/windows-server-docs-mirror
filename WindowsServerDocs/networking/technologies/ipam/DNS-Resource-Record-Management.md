---
layout: Conceptual
title: DNS Resource Record Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/dns-resource-record-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to manage DNS resource records by using IPAM.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: b97de1a7-9e81-ddee-a1eb-8c7c7d48371e
document_version_independent_id: bc2a0894-6b2a-fddc-46e2-4289ddac3321
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/DNS-Resource-Record-Management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/dns-resource-record-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/DNS-Resource-Record-Management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 84f2a4af-e5b1-c129-2c01-a53de73ed236
---

# DNS Resource Record Management | Microsoft Learn

This topic provides information about managing DNS resource records by using IPAM.

Note

In addition to this topic, the following DNS resource record management topics are available in this section.

- [Add a DNS Resource Record](add-a-dns-resource-record)
- [Delete DNS Resource Records](delete-dns-resource-records)
- [Filter the View of DNS Resource Records](filter-the-view-of-dns-resource-records)
- [View DNS Resource Records for a Specific IP Address](view-dns-resource-records-for-a-specific-ip-address)

## Resource record management overview

When you deploy IPAM in Windows Server 2016, you can perform server discovery to add DHCP and DNS servers to the IPAM server management console. The IPAM server then dynamically collects DNS data every six hours from the DNS servers that it is configured to manage. IPAM maintains a local database where it stores this DNS data. IPAM provides you with notification of the day and time that the server data was collected, as well as telling you the next day and time when data collection from DNS servers will occur.

The yellow status bar in the following illustration shows the user interface location of IPAM notifications.

![IPAM notifications](../../media/dns-resource-record-management/ipam_datacollection_01.jpg)

The DNS data that is collected includes DNS zone and resource record information. You can configure IPAM to collect zone information from your preferred DNS server. IPAM collects both file-based and Active Directory zones.

Note

IPAM collects data solely from domain-joined Microsoft DNS servers. Third party DNS servers and non-domain joined servers are not supported by IPAM.

Following is a list of DNS resource record types that are collected by IPAM.

- AFS database
- ATM Address
- CNAME
- DHCID
- DNAME
- Host A or AAAA
- Host Information
- ISDN
- MX
- Name Servers
- Pointer (PTR)
- Responsible person
- Route Through
- Service Location
- SOA
- SRV
- Text
- Well Known Services
- WINS
- WINS-R
- X.25

In Windows Server 2016, IPAM provides integration between IP address inventory, DNS Zones, and DNS resource records:

- You can use IPAM to automatically build an IP address inventory from DNS resource records.
- You can manually create an IP address inventory from DNS A and AAAA resource records.
- You can view DNS resource records for a specific DNS zone, and filter the records based on type, IP address, resource record data, and other filtering options.
- IPAM automatically creates a mapping between IP address ranges and DNS Reverse Look-up Zones.
- IPAM creates IP addresses for the PTR records that are present in the reverse look-up zone and which are included in that IP address range. You can also manually modify this mapping if needed.

IPAM allows you to perform the following operations on resource records from the IPAM console.

- Create DNS resource records
- Edit DNS resource records
- Delete DNS resource records
- Create associated resource records

IPAM automatically logs all DNS configuration changes that you make using the IPAM console.