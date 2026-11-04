---
layout: Conceptual
title: Enable Hash Publication for Domain Member File Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/enable-hash-publication-for-domain-member-file-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to enable BranchCache hash publication for multiple file servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: c73d25d6-e575-e9e5-28ff-9ed2d7365f5f
document_version_independent_id: 61b23783-03b1-cc3d-effe-2e92e959ba97
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/enable-hash-publication-for-domain-member-file-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 04035bb0-8cca-53c8-63d2-2a85f6ccf038
---

# Enable Hash Publication for Domain Member File Servers | Microsoft Learn

When you're using Active Directory Domain Services (AD DS), you can use domain Group Policy to enable BranchCache hash publication for multiple file servers. To do so, you must create an organizational unit (OU), add file servers to the OU, create a BranchCache hash publication Group Policy Object (GPO), and then configure the GPO.

See the following topics to enable hash publication for multiple file servers.

- [Create the BranchCache File Servers Organizational Unit](create-the-branchcache-file-servers-organizational-unit)
- [Move File Servers to the BranchCache File Servers Organizational Unit](move-file-servers-to-the-branchcache-file-servers-organizational-unit)
- [Create the BranchCache Hash Publication Group Policy Object](create-the-branchcache-hash-publication-group-policy-object)
- [Configure the BranchCache Hash Publication Group Policy Object](configure-the-branchcache-hash-publication-group-policy-object)