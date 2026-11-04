---
layout: Conceptual
title: Evaluating AD DS Deployment Strategy Examples | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/evaluating-ad-ds-deployment-strategy-examples
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Evaluating AD DS Deployment Strategy Examples'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 1953f7d5-0fb4-e986-7f99-44e0b4ec796e
document_version_independent_id: 20d60d64-0cf0-6b2d-e70b-861109fd21d6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Evaluating-AD-DS-Deployment-Strategy-Examples.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/evaluating-ad-ds-deployment-strategy-examples
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Evaluating-AD-DS-Deployment-Strategy-Examples.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e32a8a56-5dd1-4714-d4d2-6d33e4508630
---

# Evaluating AD DS Deployment Strategy Examples | Microsoft Learn

Consider the following example of a fictitious company, Contoso Pharmaceuticals, which is deploying Active Directory Domain Services (AD DS) in its environment. The Contoso environment consists of four domains. The forest functional level is Windows Server 2003. The following illustration shows the current domain structure for the Contoso organization.

![Illustration that shows the current domain structure for the Contoso organization.](media/evaluating-ad-ds-deployment-strategy-examples/3dd79e00-48f8-4927-989c-c55a79caf1be.gif)

After reviewing its existing environment and identifying its deployment goals, Contoso established the following AD DS deployment strategy:

- Upgrade Windows Server 2003 domains to Windows Server 2008 domains.
- Enable advanced AD DS features by raising the domain and forest functional levels to Windows Server 2008 .
- Restructure the africa.concorp.contoso.com domain within the forest to consolidate that domain with the emea.concorp.contoso.com domain.

Raising the forest functional level to Windows Server 2008 will enable Contoso to take full advantage of the new AD DS features. Restructuring the domains within the forest, as shown in the following illustration, will reduce the amount of administration that is necessary for managing the domains.

![AD DS deployment strategy](media/evaluating-ad-ds-deployment-strategy-examples/1c061755-413d-452d-b121-6910f8555327.gif)