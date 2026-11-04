---
layout: Conceptual
title: AD FS Federation Server Farm Using SQL Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/federation-server-farm-using-sql-server-2012
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Federation Server Farm Using SQL Server'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
ms.custom: sfi-image-nochange
locale: en-us
document_id: 75dee1df-2ed4-0d9f-f132-bb2d2bab2dec
document_version_independent_id: d0668f2e-d62a-9415-5c1d-0e468249e73f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-SQL-Server-2012.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/federation-server-farm-using-sql-server-2012
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-SQL-Server-2012.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 36ced966-dd86-f5cd-2888-77ccff704938
---

# AD FS Federation Server Farm Using SQL Server | Microsoft Learn

This topology for Active Directory Federation Services (AD FS) differs from the federation server farm using Windows Internal Database (WID) deployment topology in that it does not replicate the data to each federation server in the farm. Instead, all federation servers in the farm can read and write data into a common database that is stored on a server running Microsoft SQL Server that is located in the corporate network.

## Deployment considerations

This section describes various considerations about the intended audience, benefits, and limitations that are associated with this deployment topology.

### Who should use this topology?

- Large organizations with more than 100 trust relationships that need to provide both their internal users and external users with single sign-on (SSO) access to federated application or services
- Organizations that already use SQL Server and want to take advantage of their existing tools and expertise

### What are the benefits of using this topology?

- Support for larger numbers of trust relationships (more than 100)
- Support for token replay detection (a security feature) and artifact resolution (part of the Security Assertion Markup Language (SAML) 2.0 protocol)
- Support for the full benefits of SQL Server, such as database mirroring, failover clustering, reporting, and management tools

### What are the limitations of using this topology?

- This topology does not provide database redundancy by default. Although a federation server farm with WID topology automatically replicates the WID database on each federation server in the farm, the federation server farm with SQL Server topology contains only one copy of the database

Note

SQL Server supports many different data and application redundancy options including failover clustering, database mirroring, and several different types of SQL Server replication.

The Microsoft Information Technology (IT) department uses SQL Server database mirroring in high-safety (synchronous) mode and failover clustering to provide high-availability support for the SQL Server instance. SQL Server transactional (peer-to-peer) and merge replication have not been tested by the AD FS product team at Microsoft. For more information about SQL Server, see [High Availability Solutions Overview](/en-us/sql/database-engine/sql-server-business-continuity-dr) or [Selecting the Appropriate Type of Replication](/en-us/previous-versions/sql/sql-server-2008-r2/ms152565%28v=sql.105%29).

### Supported SQL Server Versions

The following SQL server versions are supported with AD FS installed with Windows Server 2012:

- SQL Server 2008 / R2
- SQL Server 2012

## Server placement and network layout recommendations

Similar to the federation server farm with WID topology, all of the federation servers in the farm are configured to use one cluster Domain Name System (DNS) name (which represents the Federation Service name) and one cluster IP address as part of the Network Load Balancing (NLB) cluster configuration. This helps the NLB host allocate client requests to the individual federation servers. Federation server proxies can be used to proxy client requests to the federation server farm.

The following illustration shows how the fictional Contoso Pharmaceuticals company deployed its federation server farm with SQL Server topology in the corporate network. It also shows how that company configured the perimeter network with access to a DNS server, an additional NLB host that uses the same cluster DNS name (fs.contoso.com) that is used on the corporate network NLB cluster, and with two federation server proxies (fsp1 and fsp2).

![server farm using SQL](media/farmsqlproxies.gif)

For more information about how to configure your networking environment for use with federation servers or federation server proxies, see either [Name Resolution Requirements for Federation Servers](name-resolution-requirements-for-federation-servers) or [Name Resolution Requirements for Federation Server Proxies](name-resolution-requirements-for-federation-server-proxies).