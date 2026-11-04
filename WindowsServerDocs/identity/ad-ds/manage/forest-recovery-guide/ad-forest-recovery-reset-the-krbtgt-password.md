---
layout: Conceptual
title: AD Forest Recovery - Reset the krbtgt password | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-the-krbtgt-password
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: How to reset the krbtgt password for the domain.
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-21T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 8af07e29-cc98-8f81-6fa4-063605ffe385
document_version_independent_id: 8af07e29-cc98-8f81-6fa4-063605ffe385
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-the-krbtgt-password.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-the-krbtgt-password
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-the-krbtgt-password.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b68327aa-2e22-6fc5-3e9e-ce153182acfa
---

# AD Forest Recovery - Reset the krbtgt password | Microsoft Learn

Use the following procedure to reset the krbtgt password for the domain. The following procedure applies to writeable DCs, but not read-only domain controllers (RODC).

Important

If you plan to recover RODC during the forest recovery, don't delete the krbtgt accounts for the RODC. The krbtgt account for an RODC is listed in the format krbtgt\_*number*.

If you use a customized password filter (such as passfilt.dll) on a DC, then you might receive an error when you try to reset the krbtgt password. For more information, including a workaround, see Microsoft Knowledge Base [article 2549833](https://support.microsoft.com/kb/2549833).

## Reset the krbtgt password

1. Select **Start**, point to **Control Panel**, point to **Administrative Tools**, and then select **Active Directory Users and Computers**.
2. Select **View**, and then select **Advanced Features**.
3. In the console tree, double-click the domain container, and then select **Users**.
4. In the details pane, right-click the **krbtgt** user account, and then select **Reset Password**. ![Reset password](media/resetpass1.png)
5. In **New password**, type a new password, retype the password in **Confirm password**, and then select **OK**. The password that you specify isn't significant because the system generates a strong password automatically independent of the password that you specify.

Important

You should perform this operation twice. You must wait 10 hours between password resets. 10 hours are the default **Maximum lifetime for user ticket** and **Maximum lifetime for service ticket** policy settings, hence in a case where the Maximum lifetime period changes, the minimum waiting period between resets should be greater than the configured value.

Note

The password history value for the krbtgt account is 2, meaning it includes the two most recent passwords. By resetting the password twice you effectively clear any old passwords from the history, so there's no way another DC replicates with this DC by using an old password.