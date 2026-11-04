---
layout: Conceptual
title: Active Directory LDAP client performance counters in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/ldap-client-performance-counters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about Active Directory LDAP client performance counters in Windows Server.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2024-10-25T00:00:00.0000000Z
locale: en-us
document_id: b5bf376d-1918-7ccc-f385-10d0c6d8c2c6
document_version_independent_id: b5bf376d-1918-7ccc-f385-10d0c6d8c2c6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/ldap-client-performance-counters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/ldap-client-performance-counters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/ldap-client-performance-counters.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: d526fd53-3925-e845-d190-f4eb90b9ee82
---

# Active Directory LDAP client performance counters in Windows Server | Microsoft Learn

Beginning with Windows Server 2025, you can use Active Directory Lightweight Directory Access Protocol (LDAP) client performance counters to monitor the performance of LDAP clients. These counters provide valuable insights into the performance of LDAP clients, including the number of binds, connections, and operations that are being processed.

LDAP is an integral part of Windows Server that enables querying and modification of directories. LDAP interacts with Active Directory to manage all network resources, including users, groups, permissions, and other data stored within the directory.

You can access these performance counters using Performance Monitor (`perfmon.exe`).

## LDAP client performance counters

LDAP client performance counters can be monitored per process running on the local client machine. Multiple processes can be assessed simultaneously. Examples of available counters include binds, connections, and operations.

The following table shows the counters that can be monitored when using a process that performs LDAP queries. The table shows the counter name, and type.

| Counter name | Type | Description |
| --- | --- | --- |
| `Digest Binds/sec` | Binds | The number of binds per second performed using digest authentication with LDAP and SASL. |
| `Negotiate Binds/sec` | Binds | The number of binds per second performed using negotiated authentication with LDAP and SASL. |
| `NTLM Binds/sec` | Binds | The number of binds per second performed using NTLM authentication with LDAP and SASL. |
| `Simple Binds/sec` | Binds | The number of binds per second performed using simple authentication with LDAP and SASL. |
| `Total Binds/sec` | Binds | The total number of binds per second performed with LDAP and SASL. |
| `New Connections/sec` | Connections | The number of new connections per second to the LDAP server. |
| `New TCP Connections/sec` | Connections | The number of new TCP connections per second to the LDAP server. |
| `New TLS Connections/sec` | Connections | The number of new TLS connections per second to the LDAP server. |
| `New LDP Connections/sec` | Connections | The number of new LDP connections per second to the LDAP server. |
| `Open Connections` | Connections | The total number of open connections to the LDAP server. |
| `Abandons/sec` | Operations | The number of abandoned operations per second. |
| `Adds/sec` | Operations | The number of add operations per second. |
| `Deletes/sec` | Operations | The number of LDAP delete operations per second. |
| `Modify/sec` | Operations | The number of LDAP modify operations per second. |
| `New Requests/sec` | Requests | The number of new LDAP requests per second. |
| `Request Count` | Requests | The total number of LDAP requests since monitoring began. |
| `Average Response Time` | Responses | The average response time for LDAP requests since monitoring began. |
| `Failure Polling Responses/sec` | Responses | The number of failed polling responses per second. |
| `Failure Responses/sec` | Responses | The number of failed LDAP responses per second. |
| `Pending Responses` | Responses | The number of LDAP responses pending a response. |
| `Successful Polling Responses/sec` | Responses | The number of successful LDAP polling responses per second. |
| `Successful Responses/sec` | Responses | The number of successful LDAP responses per second. |
| `Base Searches/sec` | Searches | The number of LDAP base searches per second. |
| `Subtree Searches/sec` | Searches | The number of LDAP subtree searches per second. |