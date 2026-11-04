---
layout: Conceptual
title: AD Forest Recovery - Resetting the computer account on the recovered DC | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-computer-account-dc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Resetting the computer account on the recovered DC'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 238a6337-e463-9506-e2da-8a4036e09601
document_version_independent_id: 238a6337-e463-9506-e2da-8a4036e09601
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-computer-account-dc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-computer-account-dc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-computer-account-dc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 6cf4a505-e19f-0642-4fe0-bbd7bd22a14d
---

# AD Forest Recovery - Resetting the computer account on the recovered DC | Microsoft Learn

Use the following procedure to reset the computer account password of the Domain Controller (DC).

## Reset the computer account password of the domain controller

1. Open PowerShell as an Administrator, type the following command, and then press ENTER:

    ```cli
    Reset-ComputerMachinePassword
    ```
2. Run the same command again to ensure other Domain Controllers from before the Forest Recovery can't replicate from it.

Warning

This should only be carried out on the sole recovered DC during a forest recovery exercise. Using this command *will* break replication with other DCs.