---
layout: Conceptual
title: Lower AD DS Domain and Forest Functional Levels in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/lower-domain-forest-functional-levels
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to lower the domain or forest functional level in Active Directory Domain Services (AD DS) on Windows Server with PowerShell.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2026-07-03T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 41be3f2f-6a7e-7573-1e8d-1c1360e52c23
document_version_independent_id: 41be3f2f-6a7e-7573-1e8d-1c1360e52c23
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/lower-domain-forest-functional-levels.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/lower-domain-forest-functional-levels
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/lower-domain-forest-functional-levels.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 4c42a600-996e-2ce6-bdb8-d1fdc0d827df
---

# Lower AD DS Domain and Forest Functional Levels in Windows Server | Microsoft Learn

Functional levels determine the capabilities available in an Active Directory Domain Services (AD DS) domain or forest, and which Windows Server operating systems you can run on domain controllers. You raise a functional level to enable newer capabilities. Raising a level is no longer permanent, so you can lower a domain or forest back to a supported earlier level. You might need to lower the level if you raise it before your environment is ready, or if you need to add domain controllers that run an earlier version of Windows Server.

This article shows how to lower domain and forest functional levels by using PowerShell. After you complete the steps, the domain or forest operates at the level you specify, provided it meets the prerequisites described in this article.

## Prerequisites

Before you lower a functional level, make sure your environment meets the prerequisites in this section.

### Permissions and tools

- To lower the domain functional level, you're a member of the Domain Admins group or have equivalent permissions. To lower the forest functional level, you're a member of the Enterprise Admins group or have equivalent permissions.
- You have a computer with the AD DS Remote Server Administration Tools (RSAT) installed, including the Active Directory module for Windows PowerShell.

### Supported rollback levels

- If your forest or domain contains Windows Server 2022 or earlier domain controllers, the lowest level you can roll back to is Windows Server 2008.
- If your forest or domain contains Windows Server 2025 domain controllers, the lowest level you can roll back to is Windows Server 2016.

### Forest functional level prerequisites

- Your forest doesn't use any forest-level features exclusive to the current functional level. After you enable a feature tied to a specific forest functional level, you can't roll back to a lower level.
- You have access to the domain controller that holds the Schema Operations Master flexible single master operations (FSMO) role.

### Domain functional level prerequisites

- Your domain doesn't use any features exclusive to the current domain functional level. For details about the features each level supports, see [Active Directory Domain Services functional levels](../active-directory-functional-levels).
- The target domain functional level isn't lower than the current forest functional level.
- You have network connectivity to the domain controller that holds the Primary Domain Controller (PDC) emulator FSMO role.

## Lower the forest functional level

To lower the forest functional level by using PowerShell:

1. Sign in to a computer with RSAT installed.
2. Open PowerShell as an administrator.
3. Run the following command to lower the forest functional level. Replace *`<forest>`* with the forest name and *`<level>`* with the forest functional level you want. For example, use `Windows2016Forest` to roll back to the Windows Server 2016 level.

    ```powershell
    Set-ADForestMode -Identity <forest> -ForestMode <level>
    ```
4. When PowerShell prompts you to confirm, enter **Y**.
5. Run the following command to verify the change.

    ```powershell
    Get-ADForest | Select-Object ForestMode
    ```
6. Confirm that `ForestMode` shows the level you set.

## Lower the domain functional level

To lower the domain functional level by using PowerShell:

1. Sign in to a computer with RSAT installed.
2. Open PowerShell as an administrator.
3. Run the following command to lower the domain functional level. Replace *`<domain>`* with the domain name and *`<level>`* with the domain functional level you want. For example, use `Windows2016Domain` to roll back to the Windows Server 2016 level.

    ```powershell
    Set-ADDomainMode -Identity <domain> -DomainMode <level>
    ```
4. When PowerShell prompts you to confirm, enter **Y**.
5. Run the following command to verify the change.

    ```powershell
    Get-ADDomain | Select-Object DomainMode
    ```
6. Confirm that `DomainMode` shows the level you set.