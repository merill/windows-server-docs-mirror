---
layout: Conceptual
title: Enable BranchCache on a File Share (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/enable-bc-on-file-share
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to enable BranchCache on a file share.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 886d58c5-fb46-c716-0208-b82e4d7a73a3
document_version_independent_id: 7dd74748-0c93-9cbe-a710-009d263a74b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/enable-bc-on-file-share.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/enable-bc-on-file-share
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/enable-bc-on-file-share.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ec0b6a0c-4636-cf9e-98cc-bab291a17bfb
---

# Enable BranchCache on a File Share (Optional) | Microsoft Learn

You can use this procedure to enable BranchCache on a file share.

Important

You do not need to perform this procedure if you configure the hash publication setting with the value **Allow hash publication for all shared folders**.

Membership in **Administrators**, or equivalent is the minimum required to perform this procedure.

### To enable BranchCache on a file share

1. Open Windows PowerShell, type **mmc**, and then press ENTER. The Microsoft Management Console (MMC) opens.
2. In the MMC, on the **File** menu, click **Add/Remove Snap-in**. The **Add or Remove Snap-ins** dialog box opens.
3. In **Add or Remove Snap-ins**, in **Available snap-ins**, double-click **Shared Folders**. The Shared Folders Wizard opens with the Local Computer object selected. Configure the View that you prefer, click **Finish**, and then click **OK**.
4. Double-click **Shared Folders (Local)**, and then click **Shares**.
5. In the details pane, right-click a share, and then click **Properties**. The share's **Properties** dialog box opens.
6. In the **Properties** dialog box, on the **General** tab, click **Offline Settings**. The **Offline Settings** dialog box opens.
7. Ensure that **Only the files and programs that users specify are available offline** is selected, and then click **Enable BranchCache**.
8. Click **OK** twice.