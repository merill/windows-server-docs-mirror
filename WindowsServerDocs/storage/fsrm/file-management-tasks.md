---
layout: Conceptual
title: File Management Tasks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/file-management-tasks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes the process of automating file management tasks
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 14b78a67-c7a0-baa8-b741-5dc2f2238535
document_version_independent_id: 91ccf285-1e27-f1a5-2d8d-2b0816c09cae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/file-management-tasks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/file-management-tasks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/file-management-tasks.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6cffafa8-6d44-9ab6-52e0-9e954512e458
---

# File Management Tasks | Microsoft Learn

File management tasks automate the process of finding subsets of files on a server and applying simple commands. These tasks can be scheduled to occur periodically to reduce repetitive costs. Files that will be processed by a file management task can be defined through any of the following properties:

- Location
- Classification properties
- Creation time
- Modification time
- Last accessed time

File management tasks can also be configured to notify file owners of any impending policy that will be applied to their files.

Note

Individual File Management tasks are run on independent schedules.
 This section includes the following topics: 
- [Create a File Expiration Task](create-file-expiration-task)
- [Create a Custom File Management Task](create-custom-file-management-task)

Note

To set e-mail notifications and certain reporting capabilities, you must first configure the general File Server Resource Manager options.

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)