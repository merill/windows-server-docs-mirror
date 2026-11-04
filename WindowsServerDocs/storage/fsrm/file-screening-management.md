---
layout: Conceptual
title: File Screening Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/file-screening-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create file screens, generate notifications, define file screening templates, and create file screening exceptions
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 9d0e41f0-2245-fbbd-793e-2820deaef6d5
document_version_independent_id: 9692c2c6-d602-2b10-5ed2-693451521692
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/file-screening-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/file-screening-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/file-screening-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: 05634f32-fa85-5cf7-3818-4b7019d84728
---

# File Screening Management | Microsoft Learn

On the **File Screening Management** node of the File Server Resource Manager MMC snap-in, you can perform the following tasks:

- Create file screens to control the types of files that users can save, and generate notifications when users attempt to save unauthorized files.
- Define file screening templates that can be applied to new volumes or folders and that can be used across an organization.
- Create file screening exceptions that extend the flexibility of the file screening rules.

For example, you can:

- Ensure that no music files are stored on personal folders on a server, yet you could allow storage of specific types of media files that support legal rights management or comply with company policies. In the same scenario, you might want to give a vice president in the company special privileges to store any type of files in his personal folder.
- Implement a screening process to notify you by e-mail when an executable file is stored on a shared folder, including information about the user who stored the file and the file's exact location, so that you can take the appropriate precautionary steps.

This section includes the following topics:

- [Define File Groups for Screening](define-file-groups-for-screening)
- [Create a File Screen](create-file-screen)
- [Create a File Screen Exception](create-file-screen-exception)
- [Create a File Screen Template](create-file-screen-template)
- [Edit File Screen Template Properties](edit-file-screen-template-properties)

Note

To set e-mail notifications and certain reporting capabilities, you must first configure the general File Server Resource Manager options.

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)