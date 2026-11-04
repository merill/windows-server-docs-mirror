---
layout: Conceptual
title: AD Forest Recovery - Cleaning metadata of removed writable domain controllers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleaning-metadata-of-removed-dcs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Metadata cleanup removes Active Directory data that identifies a DC to the replication system. Note that outside of a Forest Recovery, metadata cleanup is part of the demotion process of domain controllers, however, when they aren't reachable anymore, this process also applies. Use the following procedure to delete the DC objects for DCs that you plan to add back to the network by reinstalling AD DS.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 04e4240a-5278-7029-f59a-1e82c8a70900
document_version_independent_id: 04e4240a-5278-7029-f59a-1e82c8a70900
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleaning-metadata-of-removed-dcs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleaning-metadata-of-removed-dcs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleaning-metadata-of-removed-dcs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 1da24492-5ca6-1b49-2de5-16a8ae6da934
---

# AD Forest Recovery - Cleaning metadata of removed writable domain controllers | Microsoft Learn

Metadata cleanup removes Active Directory data that identifies a DC to the replication system.

Note that outside of a Forest Recovery, metadata cleanup is part of the demotion process of domain controllers, however, when they aren't reachable anymore, this process also applies.

Use the following procedure to delete the DC objects for DCs that you plan to add back to the network by reinstalling AD DS.

## Delete a domain controller using Active Directory Users and Computers

When you use the version of Active Directory Users and Computers or Active Directory Administrative Center in Remote Server Administration Tools (RSAT), metadata cleanup is performed automatically when you delete the DC object. The server object and the computer object are also deleted automatically.

As an alternative, you can also use Active Directory Sites and Services in RSAT to delete a DC object. If you use Active Directory Sites and Services, you must delete the associated server object and NTDS Settings object before you can delete the DC object. Metadata cleanup can also be done through command line, via NTDSUtil or using PowerShell with Active Directory Module.

For information about installing RSAT, see the article [Remote Server Administration Tools](/en-us/windows-server/remote/remote-server-administration-tools).

**To delete a domain controller object using Active Directory Users and Computers in RSAT**

1. Select **Start**, select **Administrative Tools**, and then select **Active Directory Users and Computers**.
2. In the console tree, double-click the domain container, and then double-click the **Domain Controllers** organizational unit (OU).
3. In the details pane, right-click the DC that you want to delete, and then select **Delete**. ![Delete](media/86716786218562ce1d1abcdb4a22ce11.png)
4. Select **Yes** to confirm the deletion. Select the **This Domain Controller is permanently offline and can no longer be demoted using the Active Directory Domain Services Installation Wizard (DCPROMO)** check box and select **Delete**.
5. If the DC was a global catalog server, select **Yes** confirm that the deletion.