---
layout: Conceptual
title: Create a Quota | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/create-quota
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create a quota based on a template
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 89479a27-79a0-3f3f-55d0-2b675dd94445
document_version_independent_id: d042ffaa-0026-99f5-f214-4200eac2560d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/create-quota.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/create-quota
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/create-quota.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c678845e-c9bd-deab-1658-505739f09180
---

# Create a Quota | Microsoft Learn

Quotas can be created from a template or with custom properties. The following procedure describes how to create a quota that is based on a template (recommended). If you need to create a quota with custom properties, you can save these properties as a template to re-use at a later date.

When you create a quota, you choose a quota path, which is a volume or folder that the storage limit applies to. On a given quota path, you can use a template to create one of the following types of quota:

- A single quota that limits the space for an entire volume or folder.
- An auto apply quota, which assigns the quota template to a folder or volume. Quotas based on this template are automatically generated and applied to all subfolders. For more information about creating auto apply quotas, see [Create an Auto Apply Quota](create-auto-apply-quota).

Note

By creating quotas exclusively from templates, you can centrally manage your quotas by updating the templates instead of the individual quotas. Then, you can apply changes to all quotas based on the modified template. This feature simplifies the implementation of storage policy changes by providing one central point where all updates can be made.

## To create a quota that is based on a template

1. In **Quota Management**, click the **Quota Templates** node.
2. In the Results pane, select the template on which you will base your new quota.
3. Right-click the template and click **Create Quota from Template** (or select **Create Quota from Template** from the **Actions** pane). This opens the **Create Quota** dialog box with the summary properties of the quota template displayed.
4. Under **Quota path**, type or browse to the folder that the quota will apply to.
5. Click the **Create quota on path** option. Note that the quota properties will apply to the entire folder.

    Note

    To create an auto apply quota, click the **Auto apply template and create quotas on existing and new subfolders** option. For more information about auto apply quotas, see [Create an Auto Apply Quota](create-auto-apply-quota)
6. Under **Derive properties from this quota template**, the template you used in step 2 to create your new quota is pre-selected (or you can select another template from the list). Note that the template's properties are displayed under **Summary of quota properties**.
7. Click **Create**.

## Additional References

- [Quota Management](quota-management)
- [Create an Auto Apply Quota](create-auto-apply-quota)
- [Create a Quota Template](create-quota-template)