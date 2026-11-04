---
layout: Conceptual
title: Planning Domain Controller Placement | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/planning-domain-controller-placement
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Planning Domain Controller Placement'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 4f5782e1-2456-caed-e9ac-7bfb1e56e964
document_version_independent_id: 0580972d-8cf5-3b55-a247-080d2cbe9a85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Planning-Domain-Controller-Placement.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/planning-domain-controller-placement
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Planning-Domain-Controller-Placement.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 8789f006-c9d5-2d39-b543-37eaa8ae0b8f
---

# Planning Domain Controller Placement | Microsoft Learn

After you have gathered all of the network information that will be used to design your site topology, plan where you want to place domain controllers, including forest root domain controllers, regional domain controllers, operations master role holders, and global catalog servers.

In Windows Server 2008 , you can also take advantage of read-only domain controllers (RODCs). An RODC is a new type of domain controller that hosts read-only partitions of the Active Directory database. Except for account passwords, an RODC holds all the Active Directory objects and attributes that a writable domain controller holds. However, changes can't be made to the database that is stored on the RODC. Changes must be made on a writable domain controller and then replicated back to the RODC.

An RODC is designed primarily to be deployed in remote or branch office environments, which typically have relatively few users, poor physical security, relatively poor network bandwidth to a hub site, and personnel with limited knowledge of information technology (IT). Deploying RODCs results in improved security and more efficient access to network resources. For more information about RODC features, see [AD DS: Read-Only Domain Controllers](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732801%28v=ws.10%29). For information about how to deploy an RODC, see the [Read-Only Domain Controllers Step-by-Step Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772234%28v=ws.10%29)

Note

This guide does not explain how you determine the proper number of domain controllers and the domain controller hardware requirements for each domain that is represented in each site.