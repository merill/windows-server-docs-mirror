---
layout: Conceptual
title: Install the BranchCache Feature | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/install-the-branchcache-feature
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install the BranchCache feature and start the BranchCache service on a computer running Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 3e94268e-a5ec-5a5e-a4b0-f6f219f98a97
document_version_independent_id: 4074a136-191b-17d6-2f09-6467f55f96e0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Install-the-BranchCache-Feature.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/install-the-branchcache-feature
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Install-the-BranchCache-Feature.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 60689536-e105-23f5-cc57-09c2e3e17ad2
---

# Install the BranchCache Feature | Microsoft Learn

You can use this procedure to install the BranchCache feature and start the BranchCache service on a computer running Windows Server® 2016, Windows Server 2012 R2, or Windows Server 2012.

Membership in **Administrators** or equivalent is the minimum required to perform this procedure.

Before you perform this procedure, it is recommended that you install and configure your BITS-based application or Web server.

Note

To perform this procedure by using Windows PowerShell, run Windows PowerShell as an Administrator, type the following commands at the Windows PowerShell prompt, and then press ENTER.

`Install-WindowsFeature BranchCache`

`Restart-Computer`

### To install and enable the BranchCache feature

1. In Server Manager, click **Manage**, and then click **Add Roles and Features**. The Add Roles and Features wizard opens. Click **Next**.
2. In **Select installation type**, ensure that **Role-based or feature-based installation** is selected, and then click **Next**.
3. In **Select destination server**, ensure that the correct server is selected, and then click **Next**.
4. In **Select server roles**, click **Next**.
5. In **Select features**, click **BranchCache**, and then click **Next**.
6. In **Confirm installation selections**, click **Install**. In **Installation progress**, the BranchCache feature installation proceeds. When installation is complete, click **Close**.

After you install the BranchCache feature, the BranchCache service - also called the PeerDistSvc - is enabled, and the start type is Automatic.