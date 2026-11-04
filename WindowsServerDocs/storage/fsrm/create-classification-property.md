---
layout: Conceptual
title: Create a Classification Property | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/create-classification-property
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes classification properties used to assign values to files within a specified folder or volume.
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 76a504e5-3a98-59e2-bb92-d5e57e8e0c01
document_version_independent_id: ac363aff-5629-bdd1-97d1-7798e8e17f62
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/create-classification-property.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/create-classification-property
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/create-classification-property.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 370ae1a4-3b0f-6267-3e0a-da891f5ec259
---

# Create a Classification Property | Microsoft Learn

Classification properties are used to assign values to files within a specified folder or volume. There are many property types that you can choose from, depending on your needs. The following table defines the available property types.

| Property | Description |
| --- | --- |
| Yes/No | A Boolean property that can be **Yes** or **No**. When combining multiple values during classification or from file content, a **No** value is overridden by a **Yes** value. |
| Date-time | A simple date/time property. When combining multiple values during classification or from file content, conflicting values prevent reclassification. |
| Number | A simple number property. When combining multiple values during classification or from file content, conflicting values prevent reclassification. |
| Ordered List | A list of fixed values. Only one value can be assigned to a property at a time. When combining multiple values during classification or from file content, the value highest in the list is used. |
| String | A simple string property. When combining multiple values during classification or from file content conflicting values prevent reclassification. |
| Multi-choice | A list of values that can be assigned to a property. More than one value can be assigned to a property at a time. When combining multiple values during classification or from file content, each value in the list is used. |
| Multi-string | A list of strings that can be assigned to a property. More than one value can be assigned to a property at a time. When combining multiple values during classification or from file content, each value in the list is used. |

## To create a Classification property

The following procedure guides you through the process of creating a classification property.

1. In **Classification Management**, select the **Classification Properties** node.
2. Right-select **Classification Properties**, and then select **Create property** (or select **Create property** in the **Actions** pane). This opens the **Classification Property Definitions** dialog box.
3. In the **Property Name** text box, type a name for the property.
4. In the **Description** text box, add an optional description for the property.
5. In the **Property Type** drop-down menu, select a property type from the list.
6. Select **OK**.

## Related links

- [Create an Automatic Classification Rule](create-automatic-classification-rule)
- [Classification Management](classification-management)