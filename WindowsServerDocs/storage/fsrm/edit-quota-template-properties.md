---
layout: Conceptual
title: Edit Quota Template Properties | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/edit-quota-template-properties
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to edit quota template properties to extend changes to quotas created from the original quota template
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: a0dec1c9-7465-7b3f-b25f-579620ac12d1
document_version_independent_id: ae67d4c0-a294-0203-6453-4d98169822ac
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/edit-quota-template-properties.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/edit-quota-template-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/edit-quota-template-properties.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 542215d7-7a8f-e210-451f-7a86b0e67fdf
---

# Edit Quota Template Properties | Microsoft Learn

When you make changes to a quota template, you have the option of extending those changes to quotas that were created from the original quota template. You can choose to modify only those quotas that still match the original template or all quotas that were derived from the original template, regardless of any modifications that were made to the quotas since they were created. This feature simplifies the process of updating the properties of your quotas by providing one central point where you can make all the changes.

Note

If you choose to apply the changes to all quotas that were derived from the original template, you will overwrite any custom quota properties that you created.

## To edit Quota Template Properties

1. In **Quota Templates**, select the template that you want to modify.
2. Right-click the quota template, and then click **Edit Template Properties** (or in the **Actions** pane, under **Selected Quota Templates,** select **Edit Template Properties**). This opens the **Quota Template Properties** dialog box.
3. Perform all necessary changes. The settings and notification options are identical to those that you can set when you create a quota template. Optionally, you can copy the properties from a different template and modify them for this one.
4. When you are finished editing the template properties, click **OK**. This will open the **Update Quotas Derived from Template** dialog box.
5. Select the type of update that you want to apply:

    - If you have quotas that have been modified since they were created with the original template, and you do not want to change them, select **Apply template only to derived quotas that match the original template**. This option will update only those quotas that have not been edited since they were created with the original template.
    - If you want to modify all existing quotas that were created from the original template, select **Apply template to all derived quotas**.
    - If you want to keep the existing quotas unchanged, select **Do not apply template to derived quotas**.
6. Click **OK**.

## Additional References

- [Quota Management](quota-management)
- [Create a Quota Template](create-quota-template)