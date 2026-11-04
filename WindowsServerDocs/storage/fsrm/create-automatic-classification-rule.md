---
layout: Conceptual
title: Create an Automatic Classification Rule | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/create-automatic-classification-rule
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create a classification rule for a property.
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: b9d52c01-7806-41c1-8745-63f24f95aa4c
document_version_independent_id: 4ed2b471-9171-e40a-73bd-a10be35b75e6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/create-automatic-classification-rule.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/create-automatic-classification-rule
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/create-automatic-classification-rule.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 489218ec-04db-0a34-37b4-f0ee5d4ae5aa
---

# Create an Automatic Classification Rule | Microsoft Learn

The following procedure guides you through the process of creating a classification rule. Each rule sets the value for a single property. By default, a rule is run only once and ignores files that already have a property value assigned. However, you can configure a rule to evaluate files regardless of whether a value is already assigned to the property.

## To create a Classification Rule

1. In **Classification Management**, click the **Classification Rules** node.
2. Right-click **Classification Rules**, and then click **Create a New Rule** (or click **Create a New Rule** in the **Actions** pane). This opens the **Classification Rule Definitions** dialog box.
3. On the **Rule Settings** tab, enter the following information:

    - **Rule name**. Type a name for the rule.
    - **Enabled**. This rule will only be applied if the Enabled check box is selected. To disable the rule, clear this box.
    - **Description**. Type an optional description for this rule.
    - **Scope**. Click **Add** to select a location where this rule will apply. You can add multiple locations, or remove a location by clicking **Remove**. The classification rule will apply to all folders and their subfolders in this list.
4. On the **Classification** tab, enter the following information:

    - **Classification mechanism**. Choose a method for assigning the property value.
    - **Property name**. Select the property that this rule will assign.
    - **Property value**. Select the property value that this rule will assign.
5. Optionally, click the **Advanced** button to select further options. On the **Evaluation Type** tab, the check box to **Re-evaluate files** is unchecked by default. The options that can be selected here are as follows:

    - **Re-evaluate files** unchecked: A rule is applied to a file if, and only if, the property specified by the rule has not been set to any value on the file.
    - **Re-evaluate files** checked and the **Overwrite the existing value** option selected: the rule will be applied to the files every time the automatic classification process runs. For example, if a file has a Boolean property that is set to **Yes**, a rule using the folder classifier to set all files to **No** with this option set will leave the property set to **No**.
    - **Re-evaluate files** checked and the **Aggregate the values** option selected: The rule will be applied to the files every time the automatic classification process runs. However, when the rule has decided what value to set the property file to, it aggregates that value with the one already in the file. For example, if a file has a Boolean property that is set to **Yes**, a rule using the folder classifier to set all files to **No** with this option set will leave the property set to **Yes**.

    On the **Additional Classification Parameters** tab, you can specify additional parameters that are recognized by the selected classification method by entering the name and value and clicking the **Insert** button.
6. Click **OK** or **Cancel** to close the **Advanced** dialog box.
7. Click **OK**.

## Additional References

- [Create a Classification Property](create-classification-property)
- [Classification Management](classification-management)