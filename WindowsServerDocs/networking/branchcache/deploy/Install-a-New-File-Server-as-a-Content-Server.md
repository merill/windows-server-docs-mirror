---
layout: Conceptual
title: Install a New File Server as a Content Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/install-a-new-file-server-as-a-content-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install the File Services server role and the BranchCache for Network Files role service on a computer running  Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 88e624d0-9c60-5397-4399-3fed3e1e2cef
document_version_independent_id: e472552f-c6e9-6fdc-aaf4-d4cbb867ae9c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Install-a-New-File-Server-as-a-Content-Server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/install-a-new-file-server-as-a-content-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Install-a-New-File-Server-as-a-Content-Server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3b61a463-fcc9-fd39-927a-7be5b32265c0
---

# Install a New File Server as a Content Server | Microsoft Learn

You can use this procedure to install the File Services server role and the **BranchCache for Network Files** role service on a computer running Windows Server 2016.

Membership in **Administrators**, or equivalent is the minimum required to perform this procedure.

Note

To perform this procedure by using Windows PowerShell, run Windows PowerShell as an Administrator, type the following commands at the Windows PowerShell prompt, and then press ENTER.

`Install-WindowsFeature FS-BranchCache -IncludeManagementTools`

`Restart-Computer`

To install the Data Deduplication role service, type the following command, and then press ENTER.

`Install-WindowsFeature FS-Data-Deduplication -IncludeManagementTools`

### To install File Services and the BranchCache for network files role service

1. In Server Manager, click **Manage**, and then click **Add Roles and Features**. The Add Roles and Features Wizard opens. In **Before you begin**, click **Next**.
2. In **Select installation type**, ensure that **Role-based or feature-based installation** is selected, and then click **Next**.
3. In **Select destination server**, ensure that the correct server is selected, and then click **Next**.
4. In **Select server roles**, in **Roles**, note that the **File And Storage Services** role is already installed; click the arrow to the left of the role name to expand the selection of role services, and then click the arrow to the left of **File and iSCSI Services**.
5. Select the check boxes for **File Server** and **BranchCache for Network Files**.

    Tip

    It is recommended that you also select the check box for **Data Deduplication**.

    Click **Next**.
6. In **Select features**, click **Next**.
7. In **Confirm installation selections**, review your selections, and then click **Install**. The **Installation progress** pane is displayed during installation. When installation is complete, click **Close**.