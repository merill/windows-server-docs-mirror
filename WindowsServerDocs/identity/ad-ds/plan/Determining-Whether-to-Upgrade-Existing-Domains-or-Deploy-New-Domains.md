---
layout: Conceptual
title: Determining Whether to Upgrade Existing Domains or Deploy New Domains | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/determining-whether-to-upgrade-existing-domains-or-deploy-new-domains
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Determining Whether to Upgrade Existing Domains or Deploy New Domains'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e96b17b9-d7e6-0128-0ff6-0b8574318789
document_version_independent_id: 7dd2d4c7-3755-42aa-ebe1-0e81426a6642
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Determining-Whether-to-Upgrade-Existing-Domains-or-Deploy-New-Domains.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/determining-whether-to-upgrade-existing-domains-or-deploy-new-domains
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Determining-Whether-to-Upgrade-Existing-Domains-or-Deploy-New-Domains.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: efec957f-f1ba-f987-99d4-e43e53c80d18
---

# Determining Whether to Upgrade Existing Domains or Deploy New Domains | Microsoft Learn

Each domain in your design will either be a new domain or an existing upgraded domain. Users from existing domains that you do not upgrade must be moved into new domains.

Moving accounts between domains can impact end users. Before deciding whether to move users into a new domain or to upgrade existing domains, evaluate the long-term administrative benefits of a new AD DS domain against the cost of moving users into the domain.

For more information about upgrading Active Directory domains to Windows Server 2008, see [Upgrading Active Directory Domains to Windows Server 2008 and Windows Server 2008 R2 AD DS Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731188%28v=ws.10%29).

For more information about restructuring AD DS domains within and between forests, see [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29).

For a worksheet to assist you in documenting your plans for new and upgraded domains, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Domain Planning" (DSSLOGI\_5.doc).