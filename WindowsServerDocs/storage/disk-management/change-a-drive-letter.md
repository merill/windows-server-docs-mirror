---
layout: Conceptual
title: Change a Drive Letter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-drive-letter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Change or assign a Windows drive letter to a drive by using the Change Drive Letter and Paths feature with the Disk Management utility in Windows.
ms.date: 2025-06-24T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 35f8441a-d145-c5ce-36ee-49058d0c09b4
document_version_independent_id: 49a7f4be-4d96-8b7b-537d-3a758d0a4beb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/change-a-drive-letter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/change-a-drive-letter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/change-a-drive-letter.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 436c5be1-eba1-0648-bd01-872751f6468f
---

# Change a Drive Letter | Microsoft Learn

This article describes how to manage the drive letter assigned to a drive in Windows by using the Disk Management utility. Use this procedure to complete the following tasks:

- Change the assigned drive letter for an existing drive
- Assign a drive letter to a new drive

An alternate approach is to mount the drive in an empty folder so the drive appears as a folder. For more information, see [Mount a drive in a folder](assign-a-mount-point-folder-path-to-a-drive).

## Prerequisites

To complete the procedure in this article, the following prerequisites must be met:

- The user account must be a member of the **Backup Operators** or **Administrators** group.
- A new drive or an existing drive that doesn't store the Windows operating system or any applications.

    Important

    If you change the drive letter of a drive that contains Windows or apps, the apps might have trouble running or finding the drive. The recommended approach is to not change the drive letter of a drive that contains Windows or apps.

## Change or assign a drive letter

The following steps show how to change the drive letter:

1. From the Windows **Start** menu, search for and open Disk Management with Administrator permissions.
2. Expand the **Storage** node and select **Disk Management**.
3. Locate the volume for which you want to manage the assigned drive letter. Right-click the volume and select **Change Drive Letter and Paths**.

    ![Screenshot showing the Disk Management window with the Change Drive Letter and Paths feature selected.](media/change-drive-letter.png)

    If the **Change Drive Letter and Paths** option is missing or not available, see Troubleshoot volume and drive.
4. Update the drive letter assignment:

    - To change the existing drive letter assignment, select **Change**.
    - To add a drive letter for a new drive, select **Add**.

    ![Screenshot of the Change Drive Letter and Paths dialog that shows how to select Change or Add for a drive letter assignment.](media/change-drive-letter2.png)
5. Select the **Assign the following drive letter** option. Expand the dropdown list, select the drive letter to apply, and select **OK**.

    ![Screenshot of the Change Drive Letter or Path dialog that shows how to assign a new drive letter.](media/change-drive-letter3.png)
6. In the confirmation dialog, select **Yes** and complete the assignment.

### Troubleshoot volume and drive

Here are some troubleshooting tips to help you manage the drive letter assignment process:

- If the **Change Drive Letter and Paths** option is missing for the volume you want to manage, or the option isn't available (grayed), then the volume isn't ready to receive an assigned drive letter.

    Some possible issues include:

    - The selected drive is unallocated and needs to be [initialized](initialize-new-disks).
    - The selected drive isn't accessible, which is the case for **EFI System** partitions and **Recovery** partitions. For more information, see [View drives and partitions](overview-of-disk-management#view-drives-and-partitions).
    - You have insufficient permissions to change the assignment.

    Ensure the volume you want to manage is initialized and accessible, and confirm your Administrator permissions.
- If the volume is formatted with a drive letter, and you have access to the volume but you're unable to change the assignment, the issue resolution requires assistance beyond the scope of this article. You can contact [Microsoft Support](https://support.microsoft.com/contactus/) or the manufacturer of your computer.