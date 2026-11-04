---
layout: Conceptual
title: Enable volume encryption and deduplication - Azure Local and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/volume-encryption-deduplication
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: This topic covers how to use volume encryption and deduplication in Azure Local and Windows Server using Windows Admin Center.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-08-17T00:00:00.0000000Z
locale: en-us
document_id: 0f74f23d-155e-5b99-b071-063f70b68216
document_version_independent_id: 0f74f23d-155e-5b99-b071-063f70b68216
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/volume-encryption-deduplication.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/volume-encryption-deduplication
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/volume-encryption-deduplication.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 69fe08b9-1110-a758-f950-eafb5a51fe1e
---

# Enable volume encryption and deduplication - Azure Local and Windows Server | Microsoft Learn

This topic covers how to enable encryption with BitLocker on volumes in Azure Local or Windows Server using Windows Admin Center. It also covers how to enable deduplication on volumes. To learn how to create volumes, see [Create volumes](create-volumes).

## Encrypt volumes with BitLocker

To turn on BitLocker in Windows Admin Center:

1. Connect to an Azure Local system or Storage Spaces Direct cluster running Windows Server, and then on the **Tools** pane, select **Volumes**.

    Note

    To use a new feature that provides an additional locally held BitLocker key without relying on Active Directory, you must use Windows PowerShell. The new feature is only available in Windows Server 2022 and Azure Local, version 21H2 and newer. For more information, see [Use BitLocker with Cluster Shared Volumes (CSV)](/en-us/windows-server/failover-clustering/bitlocker-on-csv-in-ws-2022).
2. On the **Volumes** page, select the **Inventory** tab, select the appropriate volume, and then select **Settings**.
3. Under **More features**, select **Use encryption**.
4. Select any optional settings, such as backing up the recovery password to Active Directory Domain Services, and then select **Save**.

    If the **Install BitLocker feature first** pop-up displays, follow its instructions to install the feature on each server in the cluster, and then restart your servers.

## Turn on deduplication

Deduplication uses a post-processing model, which means that you won't see savings until it runs. When it does, it deduplicates all existing files.

To turn on deduplication on a volume in Windows Admin Center:

1. Connect to an Azure Local system or Storage Spaces Direct cluster running Windows Server, and then on the **Tools** pane, select **Volumes**.
2. On the **Volumes** page, select the **Inventory** tab, select the appropriate volume, and then select **Settings**.
3. Under **More features**, select **Use deduplication**, and then select the deduplication mode. If you're not sure, use the default setting.
4. Select **Save**.