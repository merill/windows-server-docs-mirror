---
layout: Conceptual
title: Use Enhanced Log in Storage Replica | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-replica/storage-replica-enhanced-log
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to use Enhanced Log in Storage Replica and about the performance improvements it delivers to your replication groups.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-05-13T00:00:00.0000000Z
locale: en-us
document_id: 679607c9-3e7c-bcd2-f2bc-52254f5d1f6e
document_version_independent_id: 679607c9-3e7c-bcd2-f2bc-52254f5d1f6e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-replica/storage-replica-enhanced-log.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-replica/storage-replica-enhanced-log
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-replica/storage-replica-enhanced-log.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: deef69ac-59fc-eaa8-865a-00ab161af5fb
---

# Use Enhanced Log in Storage Replica | Microsoft Learn

Storage Replica in Windows Server uses a general-purpose logging service to replicate I/O to the secondary volume in any replication group. Beginning in Windows Server 2025, users can opt in to a higher performance logging service called *Enhanced Log*. To differentiate this redesigned logging service, we refer to the original logging service as *Traditional Log*.

## Enhanced Log vs. Traditional Log

Traditional Log is based on the [Common Log File System (CLFS)](/en-us/windows-hardware/drivers/kernel/introduction-to-the-common-log-file-system).

Enhanced Log avoids file system abstractions and their performance costs by using a raw format for logging I/O that needs to be replicated. Enhanced Log introduces an architecture that allows multiple I/O data records to be concurrently written to the secondary volume in a replication group, improving overall workload performance.

Important

There's no migration path from Storage Replica Traditional Log to Enhanced Log or vice versa. You must declare the log format when you create the Storage Replica partnership.

## Enhanced Log deployment steps

To deploy a Storage Replica partnership that uses Enhanced Log:

1. Create standard new CSV\_ReFS formatted volumes for Storage Replica data/data replication on each site's storage pool:

    ```powershell
    New-Volume -FriendlyName south-data -StoragePoolFriendlyName "Pool for Site South" -Size 1tb -FileSystem CSVFS_ReFS
    ```

    ```powershell
    New-Volume -FriendlyName north-data -StoragePoolFriendlyName "Pool for Site North" -Size 1tb -FileSystem CSVFS_ReFS
    ```
2. Create a new virtual disk for Storage Replica logs and initialize the partition for each site:

    ```powershell
    New-VirtualDisk -FriendlyName south-log -StoragePoolFriendlyName "Pool for Site South" -Size 16gb
    ```

    ```powershell
    New-VirtualDisk -FriendlyName north-log -StoragePoolFriendlyName "Pool for Site North" -Size 16gb
    ```
3. Identify the disk number of the partitions you initialized in Step 2 so you can assign a drive letter:

    ```powershell
    Get-Disk
    ```

    On site 1:

    ```powershell
    New-Partition -DiskNumber <Disk Number> -DriveLetter 'e' -UseMaximumSize
    ```

    On site 2:

    ```powershell
    New-Partition -DiskNumber <Disk Number> -DriveLetter 'f' -UseMaximumSize
    ```
4. Create the new Storage Replica partnership by using the `-LogType Raw` parameter to access Enhanced Log functionality:

    ```powershell
    New-SRPartnership -SourceComputerName <Source Computer Hostname> -SourceRGName <Source Replication Group Name> -SourceVolumeName 'C:\ClusterStorage\south-data\' -SourceLogVolumeName e: -DestinationComputerName <Destination Computer Name> -DestinationRGName <Destination Replication Group Name> -DestinationVolumeName 'C:\ClusterStorage\north-data\' -DestinationLogVolumeName f: -LogType Raw -EnableCompression
    ```

    Note

    The `-EnableCompression` parameter is needed only if you intend to use Server Message Block (SMB) compression for Storage Replica traffic.

You can use `-LogType FileBased` to deploy the Storage Replica partnership by using the Traditional Log format.