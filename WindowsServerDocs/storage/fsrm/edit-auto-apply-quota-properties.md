---
layout: Conceptual
title: Edit Auto Apply Quota Properties | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/edit-auto-apply-quota-properties
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to edit auto apply quota properties
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: fe7c290b-bb87-9988-90b1-2d797838380f
document_version_independent_id: b801bc7c-c3f5-3776-8fab-9d3cea134909
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/edit-auto-apply-quota-properties.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/edit-auto-apply-quota-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/edit-auto-apply-quota-properties.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 81e67f80-583a-cf44-ae1f-a896f4bfb5d4
---

# Edit Auto Apply Quota Properties | Microsoft Learn

When you make changes to an auto apply quota, you have the option of extending those changes to existing quotas in the auto apply quota path. You can choose to modify only those quotas that still match the original auto apply quota or all quotas in the auto apply quota path, regardless of any modifications that were made to the quotas since they were created. This feature simplifies the process of updating the properties of quotas that were derived from an auto apply quota by providing one central point where you can make all the changes.

Note

If you choose to apply the changes to all quotas in the auto apply quota path, you will overwrite any custom quota properties that you have created.

## To edit an Auto Apply Quota

1. In **Quotas**, select the auto apply quota that you want to modify. You can filter the quotas to show only auto apply quotas.
2. Right-click the quota entry, and then click **Edit Quota Properties** (or in the **Actions** pane, under **Selected Quotas,** select **Edit Quota Properties**). This opens the **Edit Auto Apply Quota** dialog box.
3. Under **Derive properties from this quota template**, select the quota template that you want to apply. You can review the properties of each quota template in the summary list box.
4. Click **OK**. This will open the **Update Quotas Derived from Auto Apply Quota** dialog box.
5. Select the type of update that you want to apply:

    - If you have quotas that have been modified since they were automatically generated, and you do not want to change them, select **Apply auto apply quota only to derived quotas that match the original auto apply quota**. This option will update only those quotas in the auto apply quota path that have not been edited since they were automatically generated.
    - If you want to modify all existing quotas in the auto apply quota path, select **Apply auto apply quota to all derived quotas**.
    - If you want to keep the existing quotas unchanged but make the modified auto apply quota effective for new subfolders in the auto apply quota path, select **Do not apply auto apply quota to derived quotas**.
6. Click **OK**.

## Additional References

- [Quota Management](quota-management)
- [Create an Auto Apply Quota](create-auto-apply-quota)