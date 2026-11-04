---
layout: Conceptual
title: AD FS Federation Server Farm Using WID and Proxies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/federation-server-farm-using-wid-and-proxies-2012
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Federation Server Farm Using WID and Proxies'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
ms.custom: sfi-image-nochange
locale: en-us
document_id: 505aa190-50dc-5e78-8edf-230c96e02428
document_version_independent_id: 751e2eed-e523-f4fa-2e1d-925258f81042
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID-and-Proxies-2012.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/federation-server-farm-using-wid-and-proxies-2012
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID-and-Proxies-2012.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a04824ec-0bf5-e855-39de-7dc83887eb03
---

# AD FS Federation Server Farm Using WID and Proxies | Microsoft Learn

This deployment topology for Active Directory Federation Services (AD FS) is identical to the federation server farm with Windows Internal Database (WID) topology, but it adds federation server proxies to the perimeter network to support external users. The federation server proxies redirect client authentication requests that come from outside your corporate network to the federation server farm.

## Deployment considerations

This section describes various considerations about the intended audience, benefits, and limitations that are associated with this deployment topology.

### Who should use this topology?

- Organizations with 100 or fewer configured trust relationships that need to provide both their internal users and external users (who are logged on to computers that are physically located outside the corporate network) with single sign-on (SSO) access to federated applications or services
- Organizations that need to provide both their internal users and external users with SSO access to Microsoft Office 365
- Smaller organizations that have external users and require redundant, scalable services

### What are the benefits of using this topology?

- The same benefits as listed for the [Federation Server Farm Using WID](federation-server-farm-using-wid-2012) topology, plus the benefit of providing additional access for external users

### What are the limitations of using this topology?

- The same limitations as listed for the [Federation Server Farm Using WID](federation-server-farm-using-wid-2012) topology

## Server placement and network layout recommendations

To deploy this topology, in addition to adding two federation server proxies, you must make sure that your perimeter network can also provide access to a Domain Name System (DNS) server and to a second Network Load Balancing (NLB) host. The second NLB host must be configured with an NLB cluster that uses an Internet-accessible cluster IP address, and it must use the same cluster DNS name setting as the previous NLB cluster that you configured on the corporate network (fs.fabrikam.com). The federation server proxies should also be configured with Internet-accessible IP addresses.

The following illustration shows the existing federation server farm with WID topology that was described previously and how the fictional Fabrikam, Inc., company provides access to a perimeter DNS server, adds a second NLB host with the same cluster DNS name (fs.fabrikam.com), and adds two federation server proxies (fsp1 and fsp2) to the perimeter network.

![server farm using WID](media/farmwidproxies.gif)

For more information about how to configure your networking environment for use with federation servers or federation server proxies, see either [Name Resolution Requirements for Federation Servers](name-resolution-requirements-for-federation-servers) or [Name Resolution Requirements for Federation Server Proxies](name-resolution-requirements-for-federation-server-proxies).