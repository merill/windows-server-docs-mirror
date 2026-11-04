---
layout: Conceptual
title: Move File Servers to the BranchCache File Servers Organizational Unit | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/move-file-servers-to-the-branchcache-file-servers-organizational-unit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to add BranchCache file servers to an organizational unit (OU) in Active Directory Domain Services (AD DS).
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 811097b5-35cf-a6b5-f1ba-7fad8fbc3f05
document_version_independent_id: c11823c3-8682-adc0-47ef-4faa7b37464b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Move-File-Servers-to-the-BranchCache-File-Servers-Organizational-Unit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/move-file-servers-to-the-branchcache-file-servers-organizational-unit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Move-File-Servers-to-the-BranchCache-File-Servers-Organizational-Unit.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 0058568f-7e0e-8d9f-64ac-e31c18a19638
---

# Move File Servers to the BranchCache File Servers Organizational Unit | Microsoft Learn

You can use this procedure to add BranchCache file servers to an organizational unit (OU) in Active Directory Domain Services (AD DS).

Membership in **Domain Admins**, or equivalent is the minimum required to perform this procedure.

Note

You must create a BranchCache file servers OU in the Active Directory Users and Computers console before you add computer accounts to the OU with this procedure. For more information, see [Create the BranchCache File Servers Organizational Unit](create-the-branchcache-file-servers-organizational-unit).

### To move file servers to the BranchCache file servers organizational unit

1. On a computer where AD DS is installed, in Server Manager, click **Tools**, and then click **Active Directory Users and Computers**. The Active Directory Users and Computers console opens.
2. In the Active Directory Users and Computers console, locate the computer account for a BranchCache file server, left-click to select the account, and then drag and drop the computer account on the BranchCache file servers OU that you previously created. For example, if you previously created an OU named **BranchCache file servers**, drag and drop the computer account on the **BranchCache file servers** OU.
3. Repeat the previous step for each BranchCache file server in the domain that you want to move to the OU.