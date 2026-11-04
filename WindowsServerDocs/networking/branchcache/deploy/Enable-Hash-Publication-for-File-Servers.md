---
layout: Conceptual
title: Enable Hash Publication for File Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/enable-hash-publication-for-file-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to enable BranchCache hash publication on one file server or on multiple file servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 356fc50d-f39d-f826-ba7f-ba3fae9d9d78
document_version_independent_id: ee41a525-3111-d57a-08b3-cdaad546a70d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-File-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/enable-hash-publication-for-file-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-File-Servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e950a82f-f112-495d-400c-9499bbabd0b9
---

# Enable Hash Publication for File Servers | Microsoft Learn

You can enable BranchCache hash publication on one file server or on multiple file servers.

- To enable hash publication on one file server using local computer Group Policy, see [Enable Hash Publication for Non-Domain Member File Servers](enable-hash-publication-for-non-domain-member-file-servers).
- To enable hash publication on multiple file servers using domain Group Policy, see [Enable Hash Publication for Domain Member File Servers](enable-hash-publication-for-domain-member-file-servers).

Note

If you have multiple file servers and you want to enable hash publication per share, rather than enabling hash publication for all shares, you can use the instructions in the topic [Enable Hash Publication for Non-Domain Member File Servers](enable-hash-publication-for-non-domain-member-file-servers).