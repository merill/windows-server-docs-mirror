---
layout: Conceptual
title: Create the BranchCache Hash Publication Group Policy Object | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/create-the-branchcache-hash-publication-group-policy-object
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to create the BranchCache hash publication Group Policy Object (GPO).
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 8a51cb3e-ea74-f054-7ee8-eb85da081ff3
document_version_independent_id: 6775b939-8a38-3769-a5f8-d06c05516b77
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Create-the-BranchCache-Hash-Publication-Group-Policy-Object.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/create-the-branchcache-hash-publication-group-policy-object
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Create-the-BranchCache-Hash-Publication-Group-Policy-Object.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d4b3928d-9e04-05f0-8a9d-83968817000b
---

# Create the BranchCache Hash Publication Group Policy Object | Microsoft Learn

You can use this procedure to create the BranchCache hash publication Group Policy Object (GPO).

Membership in **Domain Admins**, or equivalent is the minimum required to perform this procedure.

Note

Before performing this procedure, you must create the BranchCache file servers organizational unit and move file servers into the OU. For more information, see [Enable Hash Publication for Domain Member File Servers](enable-hash-publication-for-domain-member-file-servers).

### To create the BranchCache hash publication Group Policy Object

1. Open Windows PowerShell, type **mmc**, and then press ENTER. The Microsoft Management Console (MMC) opens.
2. In the MMC, on the **File** menu, click **Add/Remove Snap-in**. The **Add or Remove Snap-ins** dialog box opens.
3. In **Add or Remove Snap-ins**, in **Available snap-ins**, double-click **Group Policy Management**, and then click **OK**.
4. In the Group Policy Management MMC, expand the path to the BranchCache file servers OU that you previously created. For example, if your forest is named example.com, your domain is named example1.com, and your OU is named BranchCache file servers, expand the following path: **Group Policy Management**, **Forest: example.com**, **Domains**, **example1.com**, **BranchCache file servers**.
5. Right-click **BranchCache file servers**, and then click **Create a GPO in this domain, and Link it here**. The **New GPO** dialog box opens. In **Name**, type a name for the new GPO. For example, if you want to name the object BranchCache Hash Publication, type **BranchCache Hash Publication**. Click **OK**.