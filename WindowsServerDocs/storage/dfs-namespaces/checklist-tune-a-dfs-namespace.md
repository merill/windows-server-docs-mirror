---
layout: Conceptual
title: Checklist Tune a DFS Namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/checklist-tune-a-dfs-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to optimize how the DFS Namespace handles referrals and polls AD DS for updated namespace data
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: checklist
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 5145ce2c-ade1-a337-7b95-b7cf3f6c6a69
document_version_independent_id: c5449abc-5709-c314-628b-38b01b6c41b9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/checklist-tune-a-dfs-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/checklist-tune-a-dfs-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/checklist-tune-a-dfs-namespace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 72e4e9f7-ce0a-9ea6-9acd-75656afbee51
---

# Checklist Tune a DFS Namespace | Microsoft Learn

After creating a namespace and adding folders and targets, use the following checklist to tune or optimize the way the DFS namespace handles referrals and polls Active Directory Domain Services (AD DS) for updated namespace data.

- Prevent users from seeing folders in a namespace that they do not have permissions to access. [Enable Access-Based Enumeration on a Namespace](enable-access-based-enumeration-on-a-namespace)
- Enable or prevent users from being referred to a namespace or folder target when they access a folder in the namespace. [Enable or Disable Referrals and Client Failback](enable-or-disable-referrals-and-client-failback)
- Adjust how long clients cache a referral before requesting a new one. [Change the Amount of Time That Clients Cache Referrals](change-the-amount-of-time-that-clients-cache-referrals)
- Optimize how namespace servers poll AD DS to obtain the most current namespace data. [Optimize Namespace Polling](optimize-namespace-polling)
- Use inherited permissions to control which users can view folders in a namespace for which access-based enumeration is enabled. [Using Inherited Permissions with Access-Based Enumeration](using-inherited-permissions-with-access-based-enumeration)

In addition, by using a DFS Namespaces enhancement known as target priority, you can specify the priority of servers so that a specific server is always placed first or last in the list of servers (known as a referral) that the client receives when it accesses a folder with targets in the namespace.

- Specify in what order users should be referred to folder targets. [Set the Ordering Method for Targets in Referrals](set-the-ordering-method-for-targets-in-referrals)
- Override referral ordering for a specific namespace server or folder target. [Set Target Priority to Override Referral Ordering](set-target-priority-to-override-referral-ordering)

## Additional References

- [Namespaces](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771914%28v=ws.11%29)
- [Checklist: Deploy DFS Namespaces](checklist-deploy-dfs-namespaces)
- [Tuning DFS Namespaces](tuning-dfs-namespaces)