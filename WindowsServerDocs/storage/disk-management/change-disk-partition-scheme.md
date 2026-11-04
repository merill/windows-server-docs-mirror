---
layout: Conceptual
title: Convert a disk to GPT or MBR | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-disk-partition-scheme
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to convert a disk to GPT or MBR partition scheme (style) using Disk Management and the command line in Windows.
ms.date: 2025-06-17T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 28e747b1-411e-7f53-69d5-69c3730bf223
document_version_independent_id: d8da91d3-7b35-5a49-e484-e16fc31011ef
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/change-disk-partition-scheme.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/change-disk-partition-scheme
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/change-disk-partition-scheme.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f4a638c1-10d8-b09b-03db-fed1a3b9090a
---

# Convert a disk to GPT or MBR | Microsoft Learn

Master Boot Record (MBR) disks use the legacy BIOS partitioning scheme (also known as partition style) and supports up to four primary partitions per disk. MBR is limited to disks of 2 TB or smaller and isn't recommended for larger drives. GUID Partition Table (GPT) disks use the modern Unified Extensible Firmware Interface (UEFI), supports more than four partitions, and can manage disks larger than 2 TB.

You can convert a disk's partition style only if it doesn't contain any partitions or volumes. Make sure to delete all existing partitions or volumes before attempting to change the disk's format.

## Prerequisites

You must be a member of the **Administrators** group (or have equivalent privileges) to convert a disk.

Important

Before you convert a disk, back up any data on the disk, and close any programs that access the disk.

## Convert a disk

You can convert your disk using either the Disk Management tool or the command line. Follow these steps for your method of choice.

# [Disk Management](#tab/disk-management)
Before you convert partition styles, back up or move the data off the disk.

1. Select **Start**, type **diskmgmt.msc**, then select **Enter**.
2. Right-click on the volume pertaining to your disk.
3. Select **Delete Volume**, then select **Yes**. Repeat this step for all volumes on the disk.
4. Right-click on the disk, then select **Convert to MBR Disk** or **Convert to GPT Disk**.
5. To verify the conversion process, right-click on your disk, select **Properties**, select the **Volumes** tab, and check the partition style information.

# [Diskpart](#tab/diskpart)
Before you convert partition styles, back up or move the data off the disk.

1. Open an elevated command prompt window, type **diskpart**, then hit **Enter**.
2. Prepare your disk for conversion by cleaning (deleting) any partitions or volumes.

    Note

    If your disk doesn't have any partitions or volumes, skip to step **3** to convert your disk.

    1. Type **list disk** and hit **Enter**. Make a note of the disk number that you want to convert.
    2. Type **select disk**, provide the disk number you want to convert, then hit **Enter**.
    3. Type **clean** to delete all partitions and volumes on the disk.
3. To convert GPT to MBR, type **convert mbr**, then hit **Enter**.

    To convert MBR to GPT, type **convert gpt**, then hit **Enter**.

You're notified when the conversion process completes. To learn more, see the [diskpart](/en-us/windows-server/administration/windows-commands/diskpart) commands reference.

# [PowerShell](#tab/powershell)
Before you convert partition styles, back up or move the data off the disk.

1. Open an elevated PowerShell window.
2. Prepare your disk for conversion by cleaning (deleting) any partitions or volumes.

    Note

    If your disk doesn't have any partitions or volumes, skip to step **3** to convert your disk.

    1. To list all disks, run the following command:

        ```powershell
        Get-Disk
        ```

        Note the disk number you want to convert.
    2. To remove all partitions and volumes from the disk, run the following command. Replace `<Disk Number>` with the disk number you noted earlier:

        ```powershell
        Clear-Disk -Number <Disk Number> -RemoveData -Confirm:$false
        ```
3. To convert the partitioning style, run the following command:

    For MBR to GPT conversion:

    ```powershell
    Initialize-Disk -Number <Disk Number> -PartitionStyle GPT
    ```

    For GPT to MBR conversion:

    ```powershell
    Initialize-Disk -Number <Disk Number> -PartitionStyle MBR
    ```

    Note

    Once a disk is initialized, you can't convert it to another partition style without first running the `Clear-Disk` cmdlet again.
4. To verify the conversion process, run the following command and check the *Partition Style* column:

    ```powershell
    Get-Disk
    ```

---