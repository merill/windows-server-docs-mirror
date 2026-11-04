---
layout: Conceptual
title: Creating a Forest Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-a-forest-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating a Forest Design'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 7c99990b-6344-1ea5-a056-49b2743204f1
document_version_independent_id: e0b4e097-6b27-5824-3a99-8b967320b9f2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-a-Forest-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-a-forest-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-a-Forest-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 38eb14e4-ebe3-a584-8eb1-46346c9bb113
---

# Creating a Forest Design | Microsoft Learn

Creating a forest design involves first identifying the groups within your organization that have the resources available to host an Active Directory forest and then defining your forest design requirements. Finally, you need to determine the number of forests that you require to meet the needs of your organization.

After you map all your design requirements to forest models and select the forest model that meets the needs of your organization, document the proposed forest design. Include in your documentation the name of the group for which the forest is designed, the contact information for the forest owner, the type of forest for each forest that you include, and the requirements that each forest is designed to meet. This documentation will help the design team both to ensure that all the appropriate people are involved in the design process and to clarify the scope of the deployment project.

For a worksheet to assist you in documenting the proposed forest design, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Forest Design" (DSSLOGI\_3.doc).