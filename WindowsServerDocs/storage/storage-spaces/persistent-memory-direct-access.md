---
layout: Conceptual
title: Understand Direct Access (DAX) and create DAX volumes with persistent memory devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/persistent-memory-direct-access
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: This article provides information on DAX and how to configure it with persistent memory modules.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2021-05-14T00:00:00.0000000Z
locale: en-us
document_id: 3b807e0a-b239-6d79-7c9a-3b8d67c863a6
document_version_independent_id: 88e18190-dcbd-56d9-3bc3-68e307977238
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/persistent-memory-direct-access.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/persistent-memory-direct-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/persistent-memory-direct-access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f8708e49-5293-6ad4-bcae-8831d7ea09c5
---

# Understand Direct Access (DAX) and create DAX volumes with persistent memory devices | Microsoft Learn

**Direct access (DAX)** treats persistent memory devices as byte-addressable memory to get the lowest latency, providing direct access to byte-addressable memory rather than following normal file system block I/O conventions. The app directly modifies the persistent memory, bypassing the software overhead of the I/O stack. When used properly by DAX-aware code (that is, by memory mapping data), this can provide significant performance benefits. However, DAX has a number of issues, and it won’t provide significant benefits without DAX-aware code.

In Windows Server 2019 and later, you can only create a DAX volume on a Storage Spaces or Storage Spaces Direct configuration that uses a single persistent memory disk, with no parity and no redundancy. You can't use DAX across more than one persistent memory disk, and you can only use DAX with NTFS.

Note

DAX isn't supported on Azure Local environments.

## DAX and block translation table (BTT)

**If you don't use DAX correctly, there is potential for data loss.** We strongly recommend that you use DAX in conjunction with the block translation table (BTT) to protect against "torn writes" that can occur in the case of a power failure or system outage. BTT mitigates this risk by providing atomic sector update semantics for persistent memory devices, essentially enabling block-like sector writes so that apps can avoid mixing old and new data in a failure scenario.

Although we recommend enabling BTT on most DAX volumes to avoid subjecting the NTFS metadata to torn write issues, the downside of BTT is that it can impact the usage of "large" and "huge" memory pages on a DAX volume because remappings will occur for metadata operations. If you want to use large and huge memory pages for your memory mapped sections, do not turn on BTT.

## Create a DAX volume by using Windows PowerShell

Because DAX is a property of the file system, it must be specified when [formatting an NTFS volume](/en-us/powershell/module/storage/Format-Volume).

After creating a volume, use the **-IsDax** switch with the `Format-Volume` cmdlet to format the volume to be DAX-enabled.

```PowerShell
Format-Volume -IsDax:$true
```

The following code snippet creates a DAX volume on a persistent memory disk.

```PowerShell
# Here we use the first pmem disk to create the volume as an example
$disk = (Get-PmemDisk)[0] | Get-PhysicalDisk | Get-Disk
# Initialize the disk to GPT if it is not initialized
If ($disk.partitionstyle -eq "RAW") {$disk | Initialize-Disk -PartitionStyle GPT}
# Create a partition with drive letter 'S' (can use any available drive letter)
$disk | New-Partition -DriveLetter S -UseMaximumSize

   DiskPath: \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{53f56307-b6
bf-11d0-94f2-00a0c91efb8b}

PartitionNumber  DriveLetter Offset                                               Size Type
---------------  ----------- ------                                               ---- ----
2                S           16777216                                        251.98 GB Basic

# Format the volume with drive letter 'S' to DAX Volume
Format-Volume -FileSystem NTFS -IsDax:$true -DriveLetter S

DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------ -------------- --------- ------------ ----------------- -------------      ----
S                        NTFS           Fixed     Healthy      OK                    251.91 GB 251.98 GB

# Verify the volume is DAX enabled
Get-Partition -DriveLetter S | fl

UniqueId             : {00000000-0000-0000-0000-000100000000}SCMLD\VEN_8980&DEV_097A&SUBSYS_89804151&REV_0018\3&1B1819F6&0&03018089F
                       B63494DB728D8418B3CBBF549997891:WIN-8KGI228ULGA
AccessPaths          : {S:\, \\?\Volume{cf468ffa-ae17-4139-a575-717547d4df09}\}
DiskNumber           : 2
DiskPath             : \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{5
                       3f56307-b6bf-11d0-94f2-00a0c91efb8b}
DriveLetter          : S
Guid                 : {cf468ffa-ae17-4139-a575-717547d4df09}
IsActive             : False
IsBoot               : False
IsHidden             : False
IsOffline            : False
IsReadOnly           : False
IsShadowCopy         : False
IsDAX                : True                   # <- True: DAX enabled
IsSystem             : False
NoDefaultDriveLetter : False
Offset               : 16777216
OperationalStatus    : Online
PartitionNumber      : 2
Size                 : 251.98 GB
Type                 : Basic
```