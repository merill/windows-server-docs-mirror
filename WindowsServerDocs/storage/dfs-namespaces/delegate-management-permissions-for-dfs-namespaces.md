---
layout: Conceptual
title: Delegate Management Permissions for DFS Namespaces | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/delegate-management-permissions-for-dfs-namespaces
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to delegate management permissions for DFS namespaces, and which groups can execute namespace tasks by default
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 0aff1e99-89dc-9b39-c5e4-14c7b4ff694f
document_version_independent_id: 202bb8fd-880d-7f31-0513-f45ced734d43
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/delegate-management-permissions-for-dfs-namespaces.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/delegate-management-permissions-for-dfs-namespaces
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/delegate-management-permissions-for-dfs-namespaces.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 579704de-aa3c-2d43-3a2d-ba46cf365857
---

# Delegate Management Permissions for DFS Namespaces | Microsoft Learn

The following table describes the groups that can perform basic namespace tasks by default, and the method for delegating the ability to perform these tasks:

| Task | Groups that Can Perform this Task by Default | Delegation Method |
| --- | --- | --- |
| Create a domain-based namespace | Domain Admins group in the domain where the namespace is configured | Right-click the **Namespaces** node in the console tree, and then click **Delegate Management Permissions**. Or use the [Set-DfsnRoot GrantAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot) and [Set-DfsnRoot RevokeAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot). Windows PowerShell cmdlets (introduced in Windows Server 2012). You must also add the user to the local Administrators group on the namespace server. |
| Add a namespace server to a domain-based namespace | Domain Admins group in the domain where the namespace is configured | Right-click the domain-based namespace in the console tree, and then click **Delegate Management Permissions**. Or use the [Set-DfsnRoot GrantAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot) and [Set-DfsnRoot RevokeAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot). Windows PowerShell cmdlets (introduced in Windows Server 2012). You must also add the user to the local Administrators group on the namespace server to be added. |
| Manage a domain-based namespace | Local Administrators group on each namespace server | Right-click the domain-based namespace in the console tree, and then click **Delegate Management Permissions**. |
| Create a stand-alone namespace | Local Administrators group on the namespace server | Add the user to the local Administrators group on the namespace server. |
| Manage a stand-alone namespace\* | Local Administrators group on the namespace server | Right-click the stand-alone namespace in the console tree, and then click **Delegate Management Permissions**. Or use the [Set-DfsnRoot GrantAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot) and [Set-DfsnRoot RevokeAdminAccounts](/en-us/powershell/module/dfsn/set-dfsnroot). Windows PowerShell cmdlets (introduced in Windows Server 2012). |
| Create a replication group or enable DFS Replication on a folder | Domain Admins group in the domain where the namespace is configured | Right-click the Replication node in the console tree, and then click **Delegate Management Permissions**. |

\*Delegating management permissions to manage a stand-alone namespace does not grant the user the ability to view and manage security by using the **Delegation** tab unless the user is a member of the local Administrators group on the namespace server. This issue occurs because the DFS Management snap-in cannot retrieve the discretionary access control lists (DACLs) for the stand-alone namespace from the registry.