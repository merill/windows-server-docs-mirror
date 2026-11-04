---
layout: Conceptual
title: Move and Resize the Hosted Cache (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/6-bc-move-resize-cache
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to move the hosted cache to the drive and folder that you prefer, and to specify the amount of disk space that the hosted cache server can use for the hosted cache.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: b96d6aa6-72d2-a884-c28f-09046b5c4b0c
document_version_independent_id: 659df2e7-5764-736b-9e4c-83f1be530a37
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/6-Bc-Move-Resize-Cache.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/6-bc-move-resize-cache
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/6-Bc-Move-Resize-Cache.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 786ebb03-fcec-c52c-ea3d-c4b4503f4bdd
---

# Move and Resize the Hosted Cache (Optional) | Microsoft Learn

You can use this procedure to move the hosted cache to the drive and folder that you prefer, and to specify the amount of disk space that the hosted cache server can use for the hosted cache.

This procedure is optional. If the default cache location (%windir%\ServiceProfiles\NetworkService\AppData\Local\PeerDistPub) and size – which is 5% of the total hard disk space – are appropriate for your deployment, you do not need to change them.

You must be a member of the Administrators group to perform this procedure.

### To move and resize the hosted cache

1. Open Windows PowerShell with Administrator privileges.
2. Type the following command to move the hosted cache to another location on the local computer, and then press ENTER.

    Important

    Before running the following command, replace parameter values, such as –Path and –MoveTo, with values that are appropriate for your deployment.

    ```
    Set-BCCache -Path C:\datacache –MoveTo D:\datacache
    ```
3. Type the following command to resize the hosted cache –specifically the data cache - on the local computer. Press ENTER.

    Important

    Before running the following command, replace parameter values, such as -Percentage, with values that are appropriate for your deployment.

    ```
    Set-BCCache -Percentage 20
    ```
4. To verify the hosted cache server configuration, type the following command and press ENTER.

    ```
    Get-BCStatus
    ```

    The results of the command display status for all aspects of your BranchCache installation. Following are a few of the BranchCache settings and the correct value for each item:

    - DataCache | CacheFileDirectoryPath: Displays the hard disk location that matches the value you provided with the –MoveTo parameter of the SetBCCache command. For example, if you provided the value D:\datacache, that value is displayed in the command output.
    - DataCache | MaxCacheSizeAsPercentageOfDiskVolume: Displays the number that matches the value you provided with the –Percentage parameter of the SetBCCache command. For example, if you provided the value 20, that value is displayed in the command output.

To continue with this guide, see [Prehash and Preload Content on the Hosted Cache Server (Optional)](7-bc-prehash-preload).