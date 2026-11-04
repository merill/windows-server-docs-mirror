---
layout: Conceptual
title: Unregister an NPS from an Active Directory Domain | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-manage-unregister
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to unregister an NPS from an Active Directory Domain so you can move an NPS to another domain, replace an NPS, or retire an NPS.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 222a55e3-1b84-8f0e-2f26-8039c86a6925
document_version_independent_id: fa9843be-d359-23f9-2a77-32455769066e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-manage-unregister.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-manage-unregister
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-manage-unregister.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7a05e8d4-f225-130b-cef8-e540f86e4f76
---

# Unregister an NPS from an Active Directory Domain | Microsoft Learn

In the process of managing your NPS deployment, you might find it useful to move an NPS to another domain, to replace an NPS, or to retire an NPS.

When you move or decommission an NPS, you can unregister the NPS in the Active Directory domains where the NPS has permission to read the properties of user accounts in Active Directory.

Membership in **Administrators**, or equivalent, is the minimum required to perform these procedures.

## To unregister an NPS

1. On the domain controller, in Server Manager, click **Tools**, and then click **Active Directory Users and Computers**. The Active Directory Users and Computers console opens.
2. Click **Users**, and then double-click **RAS and IAS servers**.
3. Click the **Members** tab, and then select the NPS that you want to unregister.
4. Click **Remove**, click **Yes**, and then click **OK**.