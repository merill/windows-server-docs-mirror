---
layout: Conceptual
title: Learn about upgrading your domain and forest functional levels in Active Directory Domain Services. | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/identifying-your-functional-level-upgrade
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Upgrade your domain and forest functional level in Active Director Domain Services for Windows Server
author: robinharwood
ms.author: roharwoo
ms.date: 2024-10-25T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e5ca7573-9035-1ef9-dabc-d5ca083c513c
document_version_independent_id: dbf61e9d-9c48-2b85-f915-3877a6d3fa9e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Identifying-Your-Functional-Level-Upgrade.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/identifying-your-functional-level-upgrade
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Identifying-Your-Functional-Level-Upgrade.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 6ff2ee7f-7dcc-676e-34dc-d982811f5655
---

# Learn about upgrading your domain and forest functional levels in Active Directory Domain Services. | Microsoft Learn

In this article learn about the process for upgrading your domain and forest functional levels in Active Directory Domain Services.

Before you can raise domain and forest functional levels, evaluate your current environment and identify your target functional level. Assess your current environment by identifying:

- The domains in your forest
- The domain controllers that are located in each domain
- The operating system and updates that each domain controller is running
- When you plan to upgrade the domain controllers.

If you plan to retire a domain controller, make sure that you understand the full impact that doing so will have on your environment.

Consider the following items when assessing your current environment:

- Your domain controllers meet or exceed the hardware requirements for the operating system that you plan to upgrade to. To learn more about hardware requirements, see [Perform a Feature Update of Windows Server](../../../get-started/upgrade-in-place).
- Your Active Directory domain is operational and free from replication errors. To learn more about replication errors, see [Diagnose Active Directory replication failures](/en-us/troubleshoot/windows-server/active-directory/diagnose-replication-failures).
- Identify all your domain controllers hosting the Global Catalog (GC) and Flexible Single Master Operation (FSMO) roles. Create and verify backups of these Active Directory Domain Services domain controllers before making changes.
- Check for any incompatible software or applications that might prevent you from upgrading to a newer version of Windows Server.
- Check for removed features to make sure that none are being used. To learn more about removed features, see [Features removed or no longer developed in Windows Server](../../../get-started/removed-deprecated-features-windows-server).

Documenting this information can help you identify the steps to take to ensure that you have a fully functional Windows Server environment.

After you assess your current environment, identify the target functional level upgrade. To learn more about the functional levels, see [Forest and Domain Functional Levels](../active-directory-functional-levels).

This article discusses the following upgrade options:

- Upgrade to a Windows Server 2025 forest
- Upgrade to a Windows Server 2016 forest

## Upgrade functional levels to Windows Server 2025

In an environment consisting of only Windows Server 2025-based domain controllers, the functional levels default to Windows Server 2025. If your Active Directory Domain Services environment contains a mix of Windows Server releases, your functional levels might be set to a lower level.

To use all the forest-level and domain-level features in Windows Server 2025, you have to upgrade to the Windows Server 2025 forest and domain functional levels. To upgrade your domain controllers to Windows Server 2025, you must meet the following prerequisites:

- For new Active Directory forests, the minimum domain and forest functional level that can be set is Windows Server 2016.
- Existing domains must be at the Windows Server 2016 domain and forest functional levels to promote a Windows Server 2025 domain controller.

You can upgrade the functional levels by using the following options:

- Set up a new Active Directory domain with the new domain and forest functional levels when promoting the first Domain Controller for the new domain
- Introduce new Windows Server 2025 domain controllers into the forest, then retire or upgrade all domain controllers running an older version of Windows Server. After you've upgraded or retired all domain controllers running an older version of Windows Server, you can raise the domain and forest functional levels to Windows Server 2025.
- Perform a Feature Update of all existing domain controllers running an older version of Windows Server. To learn more about performing a Feature Update, see [Perform a Feature Update of Windows Server](../../../get-started/upgrade-in-place). Then raise the domain and forest functional levels to Windows Server 2025.

A Windows Server 2025 domain controller can only be added to an existing domain that is running Windows Server 2016 Domain Functional Level or newer version. You must also ensure that all hardware and software requirements for Windows Server 2025 are met.

## Upgrade functional levels in a Windows Server 2016 Active Directory forest

In an environment that consisting of Windows Server 2016, 2019 and 2022-based domain controllers, the functional levels are set by default to the Windows Server 2016 domain and forest functional level. The Windows Server 2016 domain and forest functional level is the most recent functional level for Windows Server 2019 and 2022. The functional level remains at these levels until you raise them manually after an upgrade to Windows Server 2025 or later.

To use all the forest-level and domain-level features in Windows Server 2016, you have to upgrade to the Windows Server 2016 forest and domain functional levels. To upgrade your domain controllers to Windows Server 2016, you must meet the following prerequisites:

- All domain controllers must be running Windows Server 2016, Windows Server 2019, or Windows Server 2022.
- The Active Directory forest functional level must be at least Windows Server 2012.

There are two upgrade options to choose from, as follows:

- Set up a new Active Directory domain with the new domain and forest functional levels when promoting the first Domain Controller for the new domain
- Introduce new Windows Server 2016, 2019 or 2022 domain controllers into the forest, then retire or upgrade all domain controllers running an older version of Windows Server. After you've upgraded or retired all domain controllers running an older version of Windows Server, you can raise the domain and forest functional levels to Windows Server 2016.
- Perform a feature update of all existing domain controllers running an older version of Windows Server. To learn more about performing a feature update, see [Perform a Feature Update of Windows Server](../../../get-started/upgrade-in-place). Then raise the domain and forest functional levels to Windows Server 2016.

## Upgrade functional levels in a previous version of Windows Server

If you're looking to identify functional levels for a previous version of Windows Server, see [Identifying your functional level upgrade](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc754209%28v=ws.10%29).