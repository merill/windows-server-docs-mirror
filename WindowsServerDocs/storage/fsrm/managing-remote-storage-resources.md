---
layout: Conceptual
title: Managing Remote Storage Resources | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/managing-remote-storage-resources
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to manage storage resources on a remote computer
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 6508bd3e-55ea-b0b1-b2d1-303a179a145f
document_version_independent_id: 6ca0eb73-9056-ca2a-970a-0a62dd286795
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/managing-remote-storage-resources.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/managing-remote-storage-resources
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/managing-remote-storage-resources.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: acb6e3ac-2703-cd33-0650-5f172ad919b0
---

# Managing Remote Storage Resources | Microsoft Learn

To manage storage resources on a remote computer, you have two options:

- Connect to the remote computer from the File Server Resource Manager Microsoft^®^ Management Console (MMC) snap-in (which you can then use to manage the remote resources).
- Use the command-line tools that are installed with File Server Resource Manager.

Either option allows you to work with quotas, screen files, manage classifications, schedule file management tasks, and generate reports with those remote resources.

Note

File Server Resource Manager can manage resources on either the local computer or a remote computer, but not both at the same time.

For example, you can:

- Connect to another computer in the domain using the File Server Resource Manager MMC snap-in and review storage utilization on a volume or folder located on the remote computer.
- Create quota and file screen templates on a local server and then use the command-line tools to import those templates into a file server located in a branch office.

This section includes the following topics:

- [Connect to a Remote Computer](connect-to-remote-computer)
- [Command-Line Tools](command-line-tools)