---
layout: Conceptual
title: Classification Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/classification-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to categorize files based on classification properties
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 2c4f52c7-137e-a505-d1f7-ece6cea17ce2
document_version_independent_id: a92a84a0-c672-fe11-f421-7e7bd9dd3d5f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/classification-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/classification-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/classification-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 4db35d8a-af32-ae7c-8519-b80a27bdcc23
---

# Classification Management | Microsoft Learn

Classification properties are used to categorize files and can be used to select files for scheduled file management tasks.

There are many ways to classify a file. One way is to create a classification property that assigns a value to all files within a specified directory. Another way is to create rules to decide what value to set for a given property.

This section includes the following topics:

- [Create a Classification Property](create-classification-property)
- [Create an Automatic Classification Rule](create-automatic-classification-rule)

Note

To set e-mail notifications and certain reporting capabilities, you must first configure the general File Server Resource Manager options.

## Additional References

[Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)