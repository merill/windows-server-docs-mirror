---
layout: Conceptual
title: Understanding AD DS Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/understanding-ad-ds-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Understanding AD DS Design'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 41df3e75-5445-86e2-a5bd-280e38b8abc0
document_version_independent_id: 71cc9feb-024a-6d3e-080e-e29dcdc3730b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Understanding-AD-DS-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/understanding-ad-ds-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Understanding-AD-DS-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: be70529f-6741-0d6d-f1bc-b844a27da414
---

# Understanding AD DS Design | Microsoft Learn

Organizations can use Active Directory Domain Services (AD DS) in Windows Server to simplify user and resource management while creating scalable, secure, and manageable infrastructures. You can use AD DS to manage your network infrastructure, including branch office, Microsoft Exchange Server, and multiple forest environments.

An AD DS deployment project involves three phases: a design phase, a deployment phase, and an operations phase. During the design phase, the design team creates a design for the AD DS logical structure that best meets the needs of each division in the organization that will use the directory service. After the design is approved, the deployment team tests the design in a lab environment and then implements the design in the production environment. Because testing is performed by the deployment team and it potentially affects the design phase, it is an interim activity that overlaps both design and deployment. When the deployment is complete, the operations team is responsible for maintaining the directory service.

Although the Windows Server AD DS design and deployment strategies that are presented in this guide are based on extensive lab and pilot-program testing and successful implementation in customer environments, you might have to customize your AD DS design and deployment to better suit specific, complex environments.

- For more information about deploying AD DS in a branch office environment, see the [Read-Only Domain Controller (RODC) Branch Office Planning Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd734758%28v=ws.10%29).
- For more information about deploying AD DS in an Exchange environment, see the article [Active Directory in Exchange Server organizations](/en-us/exchange/plan-and-deploy/active-directory/active-directory).
- For more information about deploying AD DS in a multiple forest environment, see the article [Multiple Forest Considerations in Windows 2000 and Windows Server 2003](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc739395%28v=ws.10%29).