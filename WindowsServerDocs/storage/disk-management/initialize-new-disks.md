---
layout: Conceptual
title: Initialize New Disks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Initialize new disks with the Disk Management utility in Windows and prepare them for use or get help with troubleshooting.
ms.date: 2025-06-24T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 34cb12dc-0216-e29d-bd60-32baa89eac39
document_version_independent_id: c1f66e26-0632-ba4c-c2d6-09251075ce98
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/initialize-new-disks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/initialize-new-disks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/initialize-new-disks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 01787ea2-080d-9983-8193-7d6beff649dd
---

# Initialize New Disks | Microsoft Learn

When you add a new disk to your computer, the disk isn't immediately available in Windows File Explorer. First, you need to initialize the disk so it's ready for use by Windows. You might also need to [assign a drive letter](change-a-drive-letter) to the disk. After you initialize the disk, you can format it and store files on the disk.

This article describes how to initialize a new disk that has no existing data. If you want to use a USB drive for this procedure, keep in mind that some types of USB drives can't be initialized. The USB drives are only formatted and then assigned a drive letter.

## Prerequisites

To complete the procedures in this article, the following prerequisites must be met:

- The user account must be a member of the **Backup Operators** or **Administrators** group.
- A new, uninitialized disk that has no existing data.

    Warning

    If you want to initialize a disk already in use, first save the existing files to a backup location. The initialization process erases all data on the disk.

    If the existing disk has errors, try troubleshooting the disk to see if you can read the files. For more information, see [Troubleshoot Disk Management &gt; Disks that are missing or not initialized](/en-us/troubleshoot/windows-server/backup-and-storage/troubleshoot-disk-management#disks-that-are-missing-or-not-initialized).

## Initialize a new disk

The following steps show how to initialize a new disk with Disk Management. If you prefer to use PowerShell, run the [Initialize-Disk](/en-us/powershell/module/storage/initialize-disk) cmdlet.

1. Open Disk Management with Administrator permissions. From the Windows **Start** menu, enter **Create and format hard disk partitions**.
2. In the results list, right-click **Create and format hard disk partitions** and select **Run as administrator** &gt; **Yes**.

    If you can't open Disk Management with Administrator permissions, follow these steps:

    1. In the **Search** box on the taskbar, enter **Computer Management**.
    2. In the results list, right-click **Computer Management** and select **Run as administrator** &gt; **Yes**.
    3. In the **Computer Management** dialog, go to the **Storage** &gt; **Disk Management** section.
3. In Disk Management, locate the disk to initialize. If the disk is **Offline**, right-click the disk and select **Online**.
4. Right-click the disk and select **Initialize Disk**:

    ![Screenshot that shows Disk Management and the right-click menu for an unformatted disk with the Initialize Disk option selected.](media/select-uninitialized-disk.png)
5. In the **Initialize Disk** dialog, confirm the correct disk is selected, check the partition style, and select **OK**.

    The default partition style is **GUID Partition Table (GPT)**. For more information, see Partition styles (GPT and MBR).

    ![Screenshot that shows the Initialize Disk dialog box with the GPT partition style selected.](media/initialize-disk.png)

    The disk status briefly changes to **Initializing**. After disk initialization completes, the disk status changes to **Online**.

    If disk initialization fails, see [Troubleshoot Disk Management &gt; Disks that are missing or not initialized](/en-us/troubleshoot/windows-server/backup-and-storage/troubleshoot-disk-management#disks-that-are-missing-or-not-initialized).
6. In Disk Management, locate the initialized disk and configure the disk:

    1. Right-click the **Unallocated space** on the drive, select **New Simple Volume**, and select **Next**.
    2. Specify the volume size, and select **Next**.

        The common approach is to accept the default size, which uses the entire drive. To learn more about supported drive capacities, see [Windows support for hard disks that are larger than 2 TB](/en-us/troubleshoot/windows-server/backup-and-storage/support-for-hard-disks-exceeding-2-tb).
    3. Specify the drive letter to assign to the volume, and select **Next**.
    4. Specify the file system to use (usually NTFS), and select **Next**.
7. Select **Finish** to prepare the new disk.

### Partition styles (GPT and MBR)

Disks can be divided into chunks called *partitions*. Each partition has a partition style, even when the disk has only one partition.

Windows uses two partition styles to understand how to access the data on the disk:

| Partition style | Usage |
| --- | --- |
| **GUID Partition Table (GPT)** | Most computers use the GPT disk type for hard drives and solid-state drives (SSDs). GPT is more robust and allows for volumes larger than 2 terabytes (TB). |
| **Master Boot Record (MBR)** | The MBR style is an older disk type. This style is used by 32-bit computers, older computers, and removable drives like memory cards. |

You don't usually have to worry about assigning the partition style. Windows automatically uses the appropriate disk type.