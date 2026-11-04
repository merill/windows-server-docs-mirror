---
layout: Conceptual
title: Enable Active Directory Recycle Bin in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/adac/active-directory-recycle-bin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to enable Active Directory Recycle Bin and restore deleted objects in Active Directory Domain Services on Windows Server.
ms.author: roharwoo
author: Orin-Thomas
ms.date: 2025-06-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: aeadb406-e1c9-c88d-d92e-f9d52d323f20
document_version_independent_id: aeadb406-e1c9-c88d-d92e-f9d52d323f20
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/get-started/adac/active-directory-recycle-bin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/get-started/adac/active-directory-recycle-bin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/get-started/adac/active-directory-recycle-bin.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 06b36aae-63b7-f0ec-9042-8a09d58b7a5f
---

# Enable Active Directory Recycle Bin in Windows Server | Microsoft Learn

Active Directory Recycle Bin allows you to preserve and recover accidentally deleted Active Directory objects. When you enable Active Directory Recycle Bin, all link-valued and non-link-valued attributes of the deleted Active Directory objects are preserved. Meaning objects can be restored in their entirety to the same consistent logical state that they were in immediately before deletion. For example, restored user accounts automatically regain all group memberships and corresponding access rights that they had immediately before deletion, within and across domains.

Important

Active Directory Recycle Bin isn't enabled by default. The process of enabling Active Directory Recycle Bin is irreversible. After you enable Active Directory Recycle Bin in your environment, you can't disable it.

## Prerequisites

Before you can enable Active Directory Recycle Bin, you need to complete the following prerequisites.

- The forest and domain functional level must be Windows Server 2008 R2 or higher.
- You must be a member of the Domain Admins group in the domain you want to enable Active Directory Recycle Bin.
- You must have either of the following Remote Server Administration Tools (RSAT) installed:

    - Active Directory Administrative Center (ADAC)
    - Active Directory module for Windows PowerShell.

## Enable Active Directory Recycle Bin

To enable Active Directory Recycle Bin, perform the following steps:

# [Active Directory Administrative Center](#tab/adac)
Here's how to enable Active Directory Recycle Bin using Active Directory Administrative Center (ADAC):

1. Sign into a computer that has the Active Directory module for Windows PowerShell installed.
2. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
3. If the appropriate target domain isn't selected, choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
4. In the **Tasks** pane, choose **Enable Recycle Bin** in the **Tasks** pane, choose **OK** on the warning message box, and then choose **OK** to the refresh ADAC message.
5. To refresh ADAC, press F5 or select the refresh icon.

# [PowerShell](#tab/powershell)
Here's how to enable Active Directory Recycle Bin using the [Enable-ADOptionalFeature](/en-us/powershell/module/activedirectory/enable-adoptionalfeature) cmdlet.

1. Open an elevated PowerShell session, right-click on the *Start* button, choose **Windows PowerShell (Admin)**.
2. Run the following command to enable the Active Directory Recycle Bin in the `contoso.com` domain:

    ```powershell
    Enable-ADOptionalFeature -Identity 'CN=Recycle Bin Feature,CN=Optional Features,CN=Directory Service,CN=Windows NT,CN=Services,CN=Configuration,DC=contoso,DC=com' -Scope ForestOrConfigurationSet -Target 'contoso.com'
    ```

---

If you encounter an error, you can try moving both the schema master and the domain naming master roles to the same domain controller in the root domain. Then run the cmdlet from that domain controller.

## Restore deleted objects

Perform perform the following steps to restore deleted objects using Active Directory Administrative Center.

Tip

You can only restore AD DS items that were deleted after Active Directory Recycle Bin is enabled. You can't use Active Directory Recycle Bin to recover items that were deleted before enabling this functionality.

# [Active Directory Administrative Center](#tab/adac)
Here's how to restore deleted objects using Active Directory Administrative Center:

1. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
2. choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
3. Navigate to the **Deleted Objects** container.
4. Select the users you wish to restore and then choose either **Restore** in the **Tasks** pane, or **Restore To** in the **Tasks** pane and specify the location to which you wish to restore the deleted objects.
5. To confirm the objects were restored to their original location, navigate to the target domain and verify the user accounts are listed.

# [PowerShell](#tab/powershell)
Here's how to restore deleted objects using the [Restore-ADObject](/en-us/powershell/module/activedirectory/Restore-ADObject) cmdlet.

1. Open an elevated PowerShell session, right-click on the *Start* button, choose **Windows PowerShell (Admin)**.
2. Restore all deleted objects that include the name "test" using the following command:

    ```powershell
    Get-ADObject -Filter 'Name -Like "*User*"' -IncludeDeletedObjects | Restore-ADObject
    ```
3. Restore deleted objects to a different location using the `Restore-ADObject` cmdlet with the `-TargetPath` parameter. For example, to restore all objects that include the name "User" to the `Corp` OU in the `contoso.com` domain, run the command:

    ```powershell
    Get-ADObject -Filter 'Name -Like "*User*"' -IncludeDeletedObjects | Restore-ADObject -TargetPath "OU=Corp,DC=contoso,DC=com"
    ```

---