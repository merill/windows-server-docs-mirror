---
layout: Conceptual
title: Enable Hash Publication for Non-Domain Member File Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/enable-hash-publication-for-non-domain-member-file-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure hash publication for BranchCache using local computer Group Policy on a file server with the BranchCache for Network Files role service of the File Services server role installed.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: a632dbe0-3577-4322-05f9-c3a8be1457af
document_version_independent_id: cca7ff7c-6318-f7b2-3b9c-20b170255fdb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-Non-Domain-Member-File-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/enable-hash-publication-for-non-domain-member-file-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Enable-Hash-Publication-for-Non-Domain-Member-File-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ab2aaab0-fc63-77de-978a-764927e17c53
---

# Enable Hash Publication for Non-Domain Member File Servers | Microsoft Learn

You can use this procedure to configure hash publication for BranchCache using local computer Group Policy on a file server that is running Windows Server 2016 with the **BranchCache for Network Files** role service of the File Services server role installed.

This procedure is intended for use on a non-domain member file server. If you perform this procedure on a domain member file server and you also configure BranchCache using domain Group Policy, domain Group Policy settings override local Group Policy settings.

Membership in **Administrators**, or equivalent is the minimum required to perform this procedure.

Note

If you have one or more domain member file servers, you can add them to an organizational unit (OU) in Active Directory Domain Services and then use Group Policy to configure hash publication for all of the file servers at one time, rather than individually configuring each file server. For more information, see [Enable Hash Publication for Domain Member File Servers](enable-hash-publication-for-domain-member-file-servers).

### To enable hash publication for one file server

1. Open Windows PowerShell, type **mmc**, and then press ENTER. The Microsoft Management Console (MMC) opens.
2. In the MMC, on the **File** menu, click **Add/Remove Snap-in**. The **Add or Remove Snap-ins** dialog box opens.
3. In **Add or Remove Snap-ins**, in **Available snap-ins**, double-click **Group Policy Object Editor**. The Group Policy Wizard opens with the Local Computer object selected. Click **Finish**, and then click **OK**.
4. In the Local Group Policy Editor MMC, expand the following path: **Local Computer Policy**, **Computer Configuration**, **Administrative Templates**, **Network**, **Lanman Server**. Click **Lanman Server**.
5. In the details pane, double-click **Hash Publication for BranchCache**. The **Hash Publication for BranchCache** dialog box opens.
6. In the **Hash Publication for BranchCache** dialog box, click **Enabled**.
7. In **Options**, click **Allow hash publication for all shared folders**, and then click one of the following:

    1. To enable hash publication for all shared folders on this computer, click **Allow hash publication for all shared folders**.
    2. To enable hash publication only for shared folders for which BranchCache is enabled, click **Allow hash publication only for shared folders on which BranchCache is enabled**.
    3. To disallow hash publication for all shared folders on the computer even if BranchCache is enabled on the file shares, click **Disallow hash publication on all shared folders**.
8. Click **OK**.