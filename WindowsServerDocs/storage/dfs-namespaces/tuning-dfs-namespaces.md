---
layout: Conceptual
title: Tuning DFS Namespaces | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/tuning-dfs-namespaces
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to tune or optimize DFS namespaces
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: bdd1999e-df75-7da9-cc91-9b2c8fc2b448
document_version_independent_id: b444f681-6caa-71d8-a0e2-e978c4a99918
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/tuning-dfs-namespaces.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/tuning-dfs-namespaces
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/tuning-dfs-namespaces.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: b5754c16-88d4-9340-b153-d3bcc2bead02
---

# Tuning DFS Namespaces | Microsoft Learn

After creating a namespace and adding folders and targets, refer to the following sections to tune or optimize the way DFS Namespace handles referrals and polls Active Directory Domain Services (AD DS) for updated namespace data:

- [Enable Access-Based Enumeration on a Namespace](enable-access-based-enumeration-on-a-namespace)
- [Enable or Disable Referrals and Client Failback](enable-or-disable-referrals-and-client-failback)
- [Change the Amount of Time That Clients Cache Referrals](change-the-amount-of-time-that-clients-cache-referrals)
- [Set the Ordering Method for Targets in Referrals](set-the-ordering-method-for-targets-in-referrals)
- [Set Target Priority to Override Referral Ordering](set-target-priority-to-override-referral-ordering)
- [Optimize Namespace Polling](optimize-namespace-polling)
- [Using Inherited Permissions with Access-Based Enumeration](using-inherited-permissions-with-access-based-enumeration)

Note

To search for folders or folder targets, select a namespace, click the **Search** tab, type your search string in the text box, and then click **Search**.