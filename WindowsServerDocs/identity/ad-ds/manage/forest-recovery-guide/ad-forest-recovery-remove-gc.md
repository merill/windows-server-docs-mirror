---
layout: Conceptual
title: AD Forest Recovery - Remove the global catalog | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-remove-gc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Removing the global catalog'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 2be2fd29-3375-21b5-08c8-e809129fc0cd
document_version_independent_id: 2be2fd29-3375-21b5-08c8-e809129fc0cd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-remove-gc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-remove-gc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-remove-gc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 9979b1b9-b20a-a786-3017-2b926a2e8ae1
---

# AD Forest Recovery - Remove the global catalog | Microsoft Learn

Use the following procedure to remove the global catalog from a DC.

Restoring a global catalog server from backup could result in the global catalog holding newer data for one of its partial replicas than the corresponding domain that is authoritative for that partial replica. In such a case, the newer data won't be removed from the global catalog and might even replicate to other global catalog servers. As a result, even if you did restore a DC that was a global catalog server, either inadvertently or because that was the solitary backup you trusted, you should remove the global catalog soon after the restore operation is complete. When the global catalog is removed, the computer removes all its partial replicas.

## Remove the global catalog using Active Directory Sites and Services

1. Open Server Manager, select **Tools** and select **Active Directory Sites and Services**.
2. In the console tree, expand the **Sites** container, and then select the appropriate site that contains the target server.
3. Expand the **Servers** container, and then expand the *server* object for the DC from which you want to remove the global catalog.
4. Right-click **NTDS Settings**, and then select **Properties**.
5. Clear the **Global Catalog** check box. ![Remove GC](media/removegc1.png)
6. Select **Apply**.

## Remove the global catalog using Repadmin

Open an elevated command prompt, type the following command, and press ENTER:

```cli
repadmin.exe /options DC_NAME –IS_GC
```