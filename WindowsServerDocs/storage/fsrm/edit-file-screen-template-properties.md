---
layout: Conceptual
title: Edit File Screen Template Properties | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/edit-file-screen-template-properties
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to edit file screen template properties
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 0db7a075-700c-44c7-126f-b70bcff75aea
document_version_independent_id: 2b731ce0-31cb-1ff6-5da7-58116049dd08
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/edit-file-screen-template-properties.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/edit-file-screen-template-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/edit-file-screen-template-properties.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a2fb6eb4-337e-9494-c3c6-da2765a373e5
---

# Edit File Screen Template Properties | Microsoft Learn

When you make changes to a file screen template, you have the option of extending those changes to file screens that were created with the original file screen template. You can choose to modify only those file screens that match the original template or all file screens that derive from the original template, regardless of any modifications that you made to the file screens since they were created. This feature simplifies the process of updating the properties of file screens by providing one central point where you make all the changes.

Note

If you apply the changes to all file screens that derive from the original template, you will overwrite any custom file screen properties that you created.

## To edit File Screen Template Properties

1. In **File Screen Templates**, select the template that you want to modify.
2. Right-click the file screen template and click **Edit Template Properties** (or in the **Actions** pane, under **Selected File Screen Templates**, select **Edit Template Properties**.) This opens the **File Screen Template Properties** dialog box.
3. If you want to copy the properties of another template as a base for your modified template, select a template from the **Copy properties from template** drop-down list. Then click **Copy**.
4. Perform all necessary changes. The settings and notification options are identical to those that are available when you create a file screen template.
5. When you are finished editing the template properties, click **OK**. This will open the **Update File Screens Derived from Template** dialog box.
6. Select the type of update that you want to apply:

    - If you have file screens that have been modified since they were created using the original template, and you do not want to change them, click **Apply template only to derived file screens that match the original template**. This option will update only those file screens that have not been edited since they were created with the original template properties.
    - If you want to modify all existing file screens that were created using the original template, click **Apply template to all derived file screens**.
    - If you want to keep the existing file screens unchanged, click **Do not apply template to derived file screens**.
7. Click **OK**.

## Additional References

- [File Screening Management](file-screening-management)
- [Create a File Screen Template](create-file-screen-template)