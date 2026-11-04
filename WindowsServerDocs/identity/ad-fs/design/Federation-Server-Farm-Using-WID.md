---
layout: Conceptual
title: Federation Server Farm Using WID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/federation-server-farm-using-wid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Legacy AD FS Federation Server Farm Using WID'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 598bc8bd-33ec-d805-98aa-e94f7146f5c3
document_version_independent_id: 3dc3754e-5df3-1cd1-6c8b-5f0e7294d71c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/federation-server-farm-using-wid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 3b3eb52d-eea6-fb49-6e4a-5c2c4ef0dad3
---

# Federation Server Farm Using WID | Microsoft Learn

The default topology for Active Directory Federation Services (AD FS) is a federation server farm, using the Windows Internal Database (WID). In this topology, AD FS uses WID as the store for the AD FS configuration database for all federation servers that are joined to that farm. The farm replicates and maintains the Federation Service data in the configuration database across each server in the farm. AD FS in Windows Server 2012 R2 enables organizations with 100 or fewer relying party trusts to configure federation server farms using WID with up to 30 servers.

The act of creating the first federation server in a farm also creates a new Federation Service. When you use WID for the AD FS configuration database, the first federation server that you create in the farm is referred to as the *primary federation server*. This means that this computer is configured with a read/write copy of the AD FS configuration database.

All other federation servers that you configure for this farm are referred to as *secondary federation servers* because they must replicate any changes that are made on the primary federation server to the read-only copies of the AD FS configuration database that they store locally.

Important

We recommend the use of at least two federation servers in a load-balanced configuration.

## Deployment considerations

This section describes various considerations about the intended audience, benefits, and limitations that are associated with this deployment topology.

### Who should use this topology?

- Organizations with 100 or fewer configured trust relationships that need to provide their internal users (logged on to computers that are physically connected to the corporate network) with single sign-on (SSO) access to federated applications or services
- Organizations that want to provide their internal users with SSO access to Microsoft Online Services or Microsoft Office 365
- Smaller organizations that require redundant, scalable services

Note

Organizations with larger databases should consider using the [Federation Server Farm Using SQL Server](federation-server-farm-using-sql-server) deployment topology. Organizations with users who log in from outside the network should consider using either the [Federation Server Farm Using WID and Proxies](federation-server-farm-using-wid-and-proxies) topology or the [Federation Server Farm Using SQL Server](federation-server-farm-using-sql-server) topology.

### What are the benefits of using this topology?

- Provides SSO access to internal users
- Data and Federation Service redundancy (each federation server replicates changes to other federation servers in the same farm)
- WID is included with Windows; therefore, no need to purchase SQL Server

### What are the limitations of using this topology?

- A WID farm has a limit of 30 federation servers if you have 100 or fewer relying party trusts.
- A WID farm does not support token replay detection or artifact resolution (part of the Security Assertion Markup Language (SAML) protocol).

The following table provides a summary for using a WID farm. Use it to plan your implementation.

| 1-100 RP Trusts | More than 100 RP Trusts |
| --- | --- |
| **1-30 AD FS Nodes:** WID supported | **1-30 AD FS Nodes:** Not supported using WID - SQL Required |
| **More than 30 AD FS Nodes:** Not supported using WID - SQL Required | **More than 30 AD FS Nodes:** Not supported using WID - SQL Required |

## Server placement and network layout recommendations

When you are ready to start deploying this topology in your network, you should plan on placing all of the federation servers in your corporate network behind a Network Load Balancing (NLB) host that can be configured for an NLB cluster with a dedicated cluster Domain Name System (DNS) name and cluster IP address.

Note

This cluster DNS name must match the Federation Service name, for example, fs.fabrikam.com.

The NLB host can use the settings that are defined in this NLB cluster to allocate client requests to the individual federation servers. The following illustration shows how the fictional Fabrikam, Inc., company sets up the first phase of its deployment using a two-computer federation server farm (fs1 and fs2) with WID and the positioning of a DNS server and a single NLB host that is wired to the corporate network.

![server farm using WID](media/farmwid.gif)

Note

If there is a failure on this single NLB host, users will not be able to access federated applications or services. Add additional NLB hosts if your business requirements do not allow having a single point of failure.

For more information about how to configure your networking environment for use with federation servers, see the Name Resolution Requirements section in [AD FS Requirements](ad-fs-requirements).