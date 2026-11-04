---
layout: Conceptual
title: Prehashing and Preloading Content on Hosted Cache Servers (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/prehashing-and-preloading
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to force the creation of content information - also called hashes - on BranchCache-enabled Web and file servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: d83d6b81-37a9-ef91-3e60-a89bd3e1ec6e
document_version_independent_id: 42fbc97c-fedc-5ed2-6527-41d01582df70
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/prehashing-and-preloading.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/prehashing-and-preloading
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/prehashing-and-preloading.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae7680c8-04fe-a7d6-1bb3-7a260940783c
---

# Prehashing and Preloading Content on Hosted Cache Servers (Optional) | Microsoft Learn

You can use this procedure to force the creation of content information - also called hashes - on BranchCache-enabled Web and file servers. You can also gather the data on file and web servers into packages that can be transferred to remote hosted cache servers. This provides you with the ability to preload content on remote hosted cache servers so that data is available for the first client access.

You must be a member of **Administrators**, or equivalent to perform this procedure.

### To prehash content and preload the content on hosted cache servers

1. Log on to the file or Web server that contains the data that you wish to preload, and identify the folders and files that you wish to load on one or more remote hosted cache servers.
2. Run Windows PowerShell as an Administrator. For each folder and file, run either the `Publish-BCFileContent` command or the `Publish-BCWebContent` command, depending on the type of content server, to trigger hash generation and to add data to a data package.
3. After all the data has been added to the data package, export it by using the `Export-BCCachePackage` command to produce a data package file.
4. Move the data package file to the remote hosted cache servers by using your choice of file transfer technology. FTP, SMB, HTTP, DVD and portable hard disks are all viable transports.
5. Import the data package file on the remote hosted cache servers by using the `Import-BCCachePackage` command.