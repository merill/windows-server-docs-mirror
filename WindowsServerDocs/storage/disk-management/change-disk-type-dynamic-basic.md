---
layout: Conceptual
title: Convert a disk to Dynamic or Basic | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-disk-type-dynamic-basic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to convert a disk type to Dynamic or Basic using Disk Management and the command line in Windows.
ms.date: 2025-06-17T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 722fedef-d6a4-5ed6-526b-d6dd1a4d0642
document_version_independent_id: 10f9b44a-5a88-cb84-293f-1baf62359299
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/change-disk-type-dynamic-basic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/change-disk-type-dynamic-basic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/change-disk-type-dynamic-basic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be127171-156d-685b-1c61-7efc1311ed4c
---

# Convert a disk to Dynamic or Basic | Microsoft Learn

Converting a disk between dynamic and basic types allows you to change how storage is managed on your Windows system. Basic disks use primary partitions, extended partitions, and logical drives, making them suitable for most standard configurations. Dynamic disks offer advanced features like spanning, striping, and mirroring volumes, but are now deprecated and not recommended for new deployments. Instead, use basic disks or the newer [Storage Spaces](../storage-spaces/overview) technology when you want to pool disks together into larger volumes. If you want to mirror the volume from which Windows boots, you might want to use a hardware RAID controller, such as the one included on many motherboards.

## Prerequisites

You must be a member of the **Administrators** group (or have equivalent privileges) to convert a disk.

Important

Before you convert a disk, back up any data on the disk, and close any programs that access the disk.

## Convert a disk

You can convert your disk using either the Disk Management tool or the command line. Follow these steps for your method of choice.

# [Disk Management](#tab/disk-management)
Before you convert your disk type, back up or move the data off the disk.

1. Select **Start**, type **diskmgmt.msc**, then hit **Enter**.
2. Right-click on the volume pertaining to your disk.
3. Select **Delete Volume**, then select **Yes**. Repeat this step for all volumes on the disk.
4. Right-click on the disk and select either:

    1. **Convert to Dynamic Disk**, select the correct disk that you want to convert, then select **OK**.
    2. **Convert to Basic Disk**.

Once conversion is complete, you'll see either **Basic** or **Dynamic** under your disk. If a new volume is created, you can see the disk type under the **Type** column.

# [Diskpart](#tab/diskpart)
Before you convert partition styles, back up or move the data off the disk.

1. Open an elevated command prompt window, type **diskpart**, then hit **Enter**.
2. Prepare your disk for conversion by cleaning (deleting) any partitions or volumes.

    Note

    If your disk doesn't have any partitions or volumes, skip to step **3** to convert your disk.

    1. Type `list disk` and press **Enter**. Note the disk number that you want to convert.
    2. Type `select disk <disk number>`, replace `<disk number>` with the number you noted in the previous step, and then press **Enter**.
    3. To verify the details of the currently selected disk, type `detail disk` and press **Enter**. The `detail disk` command displays information about the currently selected disk and doesn't accept a disk number as an argument.
    4. Type `clean` and press **Enter** to delete all partitions and volumes on the disk.

Caution

The `clean` command permanently destroys all data on the selected disk. Ensure you back up or move all important data before running this command.
3. Type `convert basic` or `convert dynamic`, and then press **Enter**.

Once conversion is complete, you're notified of the process.

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
3. To convert the disk type to **basic**, run the following command and replace `Disk Number` with your actual disk number:

    ```powershell
    $diskNumber = Disk Number
    $convert = @(
      "select disk $diskNumber",
      "convert basic"
    )
    $convert | ForEach-Object { $_ } | diskpart
    ```

    To convert the disk type to **dynamic**, run the following command and replace `Disk Number` with your actual disk number:

    ```powershell
    $diskNumber = Disk Number
    $convert = @(
      "select disk $diskNumber",
      "convert dynamic"
    )
    $convert | ForEach-Object { $_ } | diskpart
    ```

Once conversion is complete, you're notified of the process.

---

## Related links

- [Convert a disk to GPT or MBR partition scheme](change-disk-partition-scheme)