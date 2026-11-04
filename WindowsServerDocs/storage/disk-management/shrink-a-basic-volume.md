---
layout: Conceptual
title: Shrink a Basic Volume | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/shrink-a-basic-volume
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: See how to decrease the space used by primary partitions and logical drives by shrinking them into adjacent, contiguous space on the same disk.
ms.date: 2025-04-22T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: f91258c0-7929-4d60-3f88-e67c957584c6
document_version_independent_id: d952a74b-1f86-de68-df1e-1956ac045fc7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/shrink-a-basic-volume.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/shrink-a-basic-volume
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/shrink-a-basic-volume.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: dfeede01-f491-ab0b-a838-f6224091ed1c
---

# Shrink a Basic Volume | Microsoft Learn

You can decrease the space used by primary partitions and logical drives by shrinking them into adjacent, contiguous space on the same disk. For example, you might discover that you need another partition but don't have more disks. To create new unallocated space, you can shrink the existing partition from the end of the volume. That space can then be used for a new partition. Certain file types can block the shrink operation. For more information, see Other considerations.

When you shrink a partition, any ordinary files are automatically relocated on the disk to create the new unallocated space. There's no need to reformat the disk to shrink the partition.

You can shrink primary partitions and logical drives on raw partitions, which are partitions without a file system, or on partitions that use New Technology File System (NTFS).

Caution

If the partition is a raw partition that contains data, such as a database file, shrinking the partition might destroy the data.

## Ways to shrink a basic volume

Note

You must be a member of the Backup Operators or Administrators group, at minimum, to complete these steps.

### Shrink a basic volume by using Disk Management

1. In Disk Management, right-click the basic volume you want to shrink.
2. Select **Shrink Volume**.
3. Follow the on-screen instructions.

Note

You can only shrink basic volumes that have no file system or that use NTFS.

### Shrink a basic volume by using the command line

1. Open Command Prompt and enter `diskpart`.
2. At the `DISKPART` prompt, enter `list volume`. The output lists information about the volumes on all disks. Note the number of the simple volume that you want to shrink.
3. To select the volume that you want to shrink, at the `DISKPART` prompt, enter `select volume <volume-number>`. For the *volume-number* value, use the number you noted in the previous step.
4. To shrink the volume that you selected, at the `DISKPART` prompt, enter `shrink [desired=<desired-size>] [minimum=<minimum-size>]`. If possible, this command shrinks the volume by the amount specified in megabytes (MB) in *desired-size*. If *desired-size* is too large, the command shrinks the volume by the amount specified in *minimum-size*.

The following table lists the `diskpart` commands, parameters, and arguments that you use to shrink a volume.

| Value | Description |
| --- | --- |
| `list volume` | Displays a list of basic and dynamic volumes on all disks. |
| `select volume <volume-number>` | Selects the specified volume, where *volume-number* is the volume number, and gives it focus. If no volume is specified, the `select` command lists the current volume with focus. You can specify the volume by number, drive letter, or mount point path. On a basic disk, selecting a volume also gives the corresponding partition focus. |
| `shrink` | Shrinks the volume that has the focus, to create unallocated space. No data loss occurs. If the partition includes unmovable files, such as the page file or the shadow copy storage area, the volume shrinks to the point where the unmovable files are located. |
| `desired=<desired-size>` | Specifies the amount of space, in megabytes, to recover to the current partition. If you don't specify a desired size, the command reduces the volume by the minimum amount. If you don't specify a desired or minimum size, the command reclaims the maximum amount of space possible. |
| `minimum=<minimum-size>` | Specifies the minimum amount of space, in megabytes, to recover to the current partition. If you don't specify a minimum size, the command reduces the volume by the desired amount. If you don't specify a desired or minimum size, the command reclaims the maximum amount of space possible. |

## Other considerations

- When you shrink a partition, certain files like the paging file or the shadow copy storage area can't be automatically relocated. Also, you can't decrease the allocated space beyond the point where the unmovable files are located.
- If the shrink operation fails, use one of the following methods to identify the unmovable file that's blocking the shrink operation:

    - Check the application log for an event with ID 259. This type of event provides information about the unmovable file.
    - If you know which clusters are associated with the unmovable file, use the `fsutil` command with the `querycluster` parameter at a command prompt. When you provide the `querycluster` parameter, this command displays the unmovable file that's preventing the shrink operation from succeeding. For information about how to use this command, enter `fsutil volume querycluster /?`.

    In some cases, you can relocate the file temporarily. For example, if you need to shrink the partition further, you can use Control Panel to move the paging file or stored shadow copies to another disk. Then you can delete the stored shadow copies, shrink the volume, and move the paging file back to the disk.
- If the number of bad clusters detected by dynamic bad-cluster remapping is too high, you can't shrink the partition. If this situation occurs, consider moving the data and replacing the disk. Don't use a block-level copy operation to transfer the data, because this method also copies the bad sector table. As a result, the sectors on the new disk that contain data from the bad sectors are treated as bad, even though they're healthy.