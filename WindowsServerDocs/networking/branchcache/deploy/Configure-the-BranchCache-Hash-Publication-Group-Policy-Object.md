---
layout: Conceptual
title: Configure the BranchCache Hash Publication Group Policy Object | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/configure-the-branchcache-hash-publication-group-policy-object
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure the BranchCache hash publication Group Policy Object (GPO) so that all file servers that you added to your OU have the same hash publication policy setting applied to them.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 6e711ca8-53dd-b0a3-8c11-49623fd42ab3
document_version_independent_id: 48fe102f-57b4-f5a4-f0ca-c7782637825b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Configure-the-BranchCache-Hash-Publication-Group-Policy-Object.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/configure-the-branchcache-hash-publication-group-policy-object
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Configure-the-BranchCache-Hash-Publication-Group-Policy-Object.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 622459fd-2aa3-ca46-aa1e-0b550a5771ed
---

# Configure the BranchCache Hash Publication Group Policy Object | Microsoft Learn

You can use this procedure to configure the BranchCache hash publication Group Policy Object (GPO) so that all file servers that you added to your OU have the same hash publication policy setting applied to them.

Membership in **Domain Admins**, or equivalent is the minimum required to perform this procedure.

Note

Before performing this procedure, you must create the BranchCache file servers organizational unit, move file servers into the OU, and create the BranchCache hash publication GPO. For more information, see [Enable Hash Publication for Domain Member File Servers](enable-hash-publication-for-domain-member-file-servers).

### To configure the BranchCache hash publication Group Policy Object

1. Run Windows PowerShell as an Administrator, type **mmc**, and then press ENTER. The Microsoft Management Console (MMC) opens.
2. In the MMC, on the **File** menu, click **Add/Remove Snap-in**. The **Add or Remove Snap-ins** dialog box opens.
3. In **Add or Remove Snap-ins**, in **Available snap-ins**, double-click **Group Policy Management**, and then click **OK**.
4. In the Group Policy Management MMC, expand the path to the BranchCache hash publication GPO that you previously created. For example, if your forest is named example.com, your domain is named example1.com, and your GPO is named **BranchCache Hash Publication**, expand the following path: **Group Policy Management**, **Forest: example.com**, **Domains**, **example1.com**, **Group Policy Objects**, **BranchCache Hash Publication**.
5. Right-click the **BranchCache Hash Publication** GPO and click **Edit**. The Group Policy Management Editor console opens.
6. In the Group Policy Management Editor console, expand the following path: **Computer Configuration**, **Policies**, **Administrative Templates**, **Network**, **Lanman Server**.
7. In the Group Policy Management Editor console, click **Lanman Server**. In the details pane, double-click **Hash Publication for BranchCache**. The **Hash Publication for BranchCache** dialog box opens.
8. In the **Hash Publication for BranchCache** dialog box, click **Enabled**.
9. In **Options**, click **Allow hash publication for all shared folders**, and then click one of the following:

    1. To enable hash publication for all shared folders for all file servers that you added to the OU, click **Allow hash publication for all shared folders**.
    2. To enable hash publication only for shared folders for which BranchCache is enabled, click **Allow hash publication only for shared folders on which BranchCache is enabled**.
    3. To disallow hash publication for all shared folders on the computer even if BranchCache is enabled on the file shares, click **Disallow hash publication on all shared folders**.
10. Click **OK**.

Note

In most cases, you must save the MMC console and refresh the view to display the configuration changes you have made.