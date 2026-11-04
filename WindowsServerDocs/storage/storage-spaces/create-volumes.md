---
layout: Conceptual
title: Create volumes on Azure Local and Windows Server clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/create-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: How to create volumes on Azure Local and Windows Server clusters by using Windows Admin Center and PowerShell.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2025-07-22T00:00:00.0000000Z
locale: en-us
document_id: 6fafd7e1-ee37-dfb1-7018-3a2b6cdbfbc6
document_version_independent_id: 7e68238e-76a0-f92f-ac98-26656b22b3c5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/create-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/create-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/create-volumes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/5cf46315-b33f-4e99-8224-a1592697eff9
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/715d24c3-3683-4219-82c5-1e3c813fb7fc
platformId: 93333c70-6e26-ab1a-c261-fd42c9d777e7
---

# Create volumes on Azure Local and Windows Server clusters | Microsoft Learn

This article describes how to create volumes on a cluster by using Windows Admin Center and Windows PowerShell, how to work with files on the volumes, and how to enable deduplication, integrity checksums, or BitLocker encryption on volumes. To learn how to create volumes and set up replication for stretched clusters, see [Create stretched volumes](/en-us/azure/azure-local/manage/create-stretched-volumes).

Tip

If you haven't already, check out [Plan volumes](plan-volumes) first.

When creating volumes on a single-node cluster, you must use PowerShell. See [Create volumes using PowerShell](create-volumes#create-volumes-using-windows-powershell).

## Create a two-way or three-way mirror volume

To create a two-way or three-way mirror volume using Windows Admin Center:

1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane.
2. On the **Volumes** page, select the **Inventory** tab, and then select **Create**.
3. In the **Create volume** pane, enter a name for the volume.
4. In **Resiliency**, select **Two-way mirror** or **Three-way mirror** depending on the number of servers in your cluster.
5. In **Size on HDD**, specify the size of the volume. For example, 5 TB (terabytes).
6. Under **More options,** you can use the checkboxes to turn on deduplication, integrity checksums, or encryption.
7. Select **Create**.

Depending on the size, creating the volume can take a few minutes. Notifications in the upper-right let you know when the volume is created. The new volume appears in the Inventory list.

## Create a mirror-accelerated parity volume

Mirror-accelerated parity (MAP) reduces the footprint of the volume on the HDD. For example, a three-way mirror volume would mean that for every 10 terabytes of size, you need 30 terabytes as a footprint. To reduce the overhead in footprint, create a volume with mirror-accelerated parity. This reduces the footprint from 30 terabytes to just 22 terabytes, even with only 4 servers, by mirroring the most active 20 percent of data and using parity, which is more space efficient, to store the rest. You can adjust this ratio of parity and mirror to make the performance versus capacity tradeoff that's right for your workload. For example, 90 percent parity and 10 percent mirror yields less performance but streamlines the footprint even further.

Note

Mirror-accelerated parity volumes require Resilient File System (ReFS).

To create a volume with mirror-accelerated parity in Windows Admin Center:

1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane.
2. On the Volumes page, select the **Inventory** tab, and then select **Create**.
3. In the **Create volume** pane, enter a name for the volume.
4. In **Resiliency**, select **Mirror-accelerated parity**.
5. In **Parity percentage**, select the percentage of parity.
6. Under **More options,** you can use the checkboxes to turn on deduplication, integrity checksums, or BitLocker encryption.
7. Select **Create**.

## Open volume and add files

To open a volume and add files to the volume in Windows Admin Center:

1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane.
2. On the **Volumes** page, select the **Inventory** tab.
3. In the list of volumes, select the name of the volume that you want to open.

    On the volume details page, you can see the path to the volume.
4. At the top of the page, select **Open**. This launches the **Files** tool in Windows Admin Center.
5. Navigate to the path of the volume. Here you can browse the files in the volume.
6. Select **Upload**, and then select a file to upload.
7. Use the browser **Back** button to go back to the **Tools** pane in Windows Admin Center.

## Use ReFS deduplication

Deduplication is managed per volume. Deduplication uses a post-processing model, which means that you won't see savings until it runs. When it does, it works over all files, even files that were there from before.

To learn more, see [Enable volume encryption and deduplication](volume-encryption-deduplication).

## Create volumes using Windows PowerShell

First, launch Windows PowerShell from the Windows start menu. We recommend using the **New-Volume** cmdlet to create volumes for Azure Local. It provides the fastest and most straightforward experience. This single cmdlet automatically creates the virtual disk, partitions and formats it, creates the volume with matching name, and adds it to cluster shared volumes – all in one easy step.

The **New-Volume** cmdlet has four parameters you need to provide:

- **FriendlyName:** Any string you want, for example *"Volume1"*

    Note

    Don't use the format "UserStorage\_&lt;#&gt;", such as "UserStorage\_1". This format is a deployment-managed naming pattern.
- **FileSystem:** Either **CSVFS\_ReFS** (recommended for all volumes; required for mirror-accelerated parity volumes) or **CSVFS\_NTFS**
- **StoragePoolFriendlyName:** The name of your storage pool, for example *"S2D on ClusterName"*
- **Size:** The size of the volume, for example *"10TB"*

    Note

    Windows, including PowerShell, counts using binary (base-2) numbers, whereas drives are often labeled using decimal (base-10) numbers. This explains why a "one terabyte" drive, defined as 1,000,000,000,000 bytes, appears in Windows as about "909 GB". This is expected. When creating volumes using **New-Volume**, you should specify the **Size** parameter in binary (base-2) numbers. For example, specifying "909GB" or "0.909495TB" creates a volume of approximately 1,000,000,000,000 bytes.

### Example: With 1 to 3 servers

To make things easier, if your deployment has only one or two servers, Storage Spaces Direct automatically uses two-way mirroring for resiliency. If your deployment has only three servers, it automatically uses three-way mirroring.

```PowerShell
New-Volume -FriendlyName "Volume1" -FileSystem CSVFS_ReFS -StoragePoolFriendlyName S2D* -Size 1TB
```

### Example: With 4+ servers

If you have four or more servers, you can use the optional **ResiliencySettingName** parameter to choose your resiliency type. The **ResiliencySettingName** is either **Mirror** or **Parity**.

In the following example, *"Volume2"* uses three-way mirroring and *"Volume3"* uses dual parity (often called "erasure coding").

```PowerShell
New-Volume -FriendlyName "Volume2" -FileSystem CSVFS_ReFS -StoragePoolFriendlyName S2D* -Size 1TB -ResiliencySettingName Mirror
New-Volume -FriendlyName "Volume3" -FileSystem CSVFS_ReFS -StoragePoolFriendlyName S2D* -Size 1TB -ResiliencySettingName Parity
```

## Use storage tiers

In deployments with three types of drives, one volume can span the SSD and HDD tiers to reside partially on each. Likewise, in deployments with four or more servers, one volume can mix mirroring and dual parity to reside partially on each.

To help you create such volumes, Azure Local provides default tier templates called **MirrorOn*MediaType*** and **NestedMirrorOn*MediaType*** (for performance), and **ParityOn*MediaType*** and **NestedParityOn*MediaType*** (for capacity), where *MediaType* is HDD or SSD. The templates represent storage tiers based on media types and encapsulate definitions for three-way mirroring on the faster capacity drives (if applicable), and dual parity on the slower capacity drives (if applicable).

- Storage Bus Layer (SBL) cache isn't supported in single server configuration. All flat single storage type configurations (for example all-NVMe or all-SSD) are the only supported storage type for single server.
- On Storage Spaces Direct clusters running on earlier versions of Windows Server 2016, the default tier templates are called **Performance** and **Capacity**.

You can see the storage tiers by running the **Get-StorageTier** cmdlet on any server in the cluster.

```PowerShell
Get-StorageTier | Select FriendlyName, ResiliencySettingName, PhysicalDiskRedundancy
```

For example, if you have a two-node cluster with only HDD, your output might look something like this:

```PowerShell
FriendlyName      ResiliencySettingName PhysicalDiskRedundancy
------------      --------------------- ----------------------
NestedParityOnHDD Parity                                     1
Capacity          Mirror                                     1
NestedMirrorOnHDD Mirror                                     3
MirrorOnHDD       Mirror                                     1
```

To create tiered volumes, reference these tier templates using the **StorageTierFriendlyNames** and **StorageTierSizes** parameters of the **New-Volume** cmdlet. For example, the following cmdlet creates one volume that mixes three-way mirroring and dual parity in 30:70 proportions.

```PowerShell
New-Volume -FriendlyName "Volume1" -FileSystem CSVFS_ReFS -StoragePoolFriendlyName S2D* -StorageTierFriendlyNames MirrorOnHDD, Capacity -StorageTierSizes 300GB, 700GB
```

Repeat as needed to create more than one volume.

### Storage tier summary table

The following tables summarize the storage tiers that are created in Azure Local and Windows Server.

#### NumberOfNodes: 1

| FriendlyName | MediaType | ResiliencySettingName | NumberOfDataCopies | PhysicalDiskRedundancy | NumberOfGroups | FaultDomainAwareness | ColumnIsolation | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MirrorOnHDD | HDD | Mirror | 2 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |
| MirrorOnSSD | SSD | Mirror | 2 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |
| MirrorOnSCM | SCM | Mirror | 2 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |
| ParityOnHDD | HDD | Parity | 1 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |
| ParityOnSSD | SSD | Parity | 1 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |
| ParityOnSCM | SCM | Parity | 1 | 1 | 1 | PhysicalDisk | PhysicalDisk | auto created |

#### NumberOfNodes: 2

| FriendlyName | MediaType | ResiliencySettingName | NumberOfDataCopies | PhysicalDiskRedundancy | NumberOfGroups | FaultDomainAwareness | ColumnIsolation | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MirrorOnHDD | HDD | Mirror | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSSD | SSD | Mirror | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSCM | SCM | Mirror | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| NestedMirrorOnHDD | HDD | Mirror | 4 | 3 | 1 | StorageScaleUnit | PhysicalDisk | manual |
| NestedMirrorOnSSD | SSD | Mirror | 4 | 3 | 1 | StorageScaleUnit | PhysicalDisk | manual |
| NestedMirrorOnSCM | SCM | Mirror | 4 | 3 | 1 | StorageScaleUnit | PhysicalDisk | manual |
| NestedParityOnHDD | HDD | Parity | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | manual |
| NestedParityOnSSD | SSD | Parity | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | manual |
| NestedParityOnSCM | SCM | Parity | 2 | 1 | 1 | StorageScaleUnit | PhysicalDisk | manual |

#### NumberOfNodes: 3

| FriendlyName | MediaType | ResiliencySettingName | NumberOfDataCopies | PhysicalDiskRedundancy | NumberOfGroups | FaultDomainAwareness | ColumnIsolation | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MirrorOnHDD | HDD | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSSD | SSD | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSCM | SCM | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |

#### NumberOfNodes: 4+

| FriendlyName | MediaType | ResiliencySettingName | NumberOfDataCopies | PhysicalDiskRedundancy | NumberOfGroups | FaultDomainAwareness | ColumnIsolation | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MirrorOnHDD | HDD | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSSD | SSD | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| MirrorOnSCM | SCM | Mirror | 3 | 2 | 1 | StorageScaleUnit | PhysicalDisk | auto created |
| ParityOnHDD | HDD | Parity | 1 | 2 | Auto | StorageScaleUnit | StorageScaleUnit | auto created |
| ParityOnSSD | SSD | Parity | 1 | 2 | Auto | StorageScaleUnit | StorageScaleUnit | auto created |
| ParityOnSCM | SCM | Parity | 1 | 2 | Auto | StorageScaleUnit | StorageScaleUnit | auto created |

## Nested resiliency volumes

Nested resiliency only applies to two-server clusters running Azure Local or Windows Server 2022 or Windows Server 2019; you can't use nested resiliency if your cluster has three or more servers, or if your cluster runs Windows Server 2016. Nested resiliency enables a two-server cluster to withstand multiple hardware failures at the same time without loss of storage availability, allowing users, apps, and virtual machines to continue to run without disruption. For more information, see [Nested Resiliency for Storage Spaces Direct](nested-resiliency) and [Plan volumes: choosing the resiliency type](plan-volumes#choosing-the-resiliency-type).

You can use familiar storage cmdlets in PowerShell to create volumes with nested resiliency, as described in the following section.

### Step 1: Create storage tier templates (Windows Server 2019 only)

Windows Server 2019 requires you to create new storage tier templates using the `New-StorageTier` cmdlet before creating volumes. You only need to do this once, and then every new volume you create can reference these templates.

Note

If you're running Windows Server 2022, Azure Stack HCI, version 21H2, or Azure Stack HCI, version 20H2, you can skip this step.

Specify the `-MediaType` of your capacity drives and, optionally, the `-FriendlyName` of your choice. Don't modify other parameters.

For example, if your capacity drives are hard disk drives (HDD), launch PowerShell as Administrator and run the following cmdlets.

To create a NestedMirror tier:

```powershell
New-StorageTier -StoragePoolFriendlyName S2D* -FriendlyName NestedMirrorOnHDD -ResiliencySettingName Mirror -MediaType HDD -NumberOfDataCopies 4
```

To create a NestedParity tier:

```powershell
New-StorageTier -StoragePoolFriendlyName S2D* -FriendlyName NestedParityOnHDD -ResiliencySettingName Parity -MediaType HDD -NumberOfDataCopies 2 -PhysicalDiskRedundancy 1 -NumberOfGroups 1 -FaultDomainAwareness StorageScaleUnit -ColumnIsolation PhysicalDisk
```

If your capacity drives are solid-state drives (SSD), set the `-MediaType` to `SSD` instead and change the `-FriendlyName` to `*OnSSD`. Don't modify other parameters.

Tip

Verify that `Get-StorageTier` created the tiers successfully.

### Step 2: Create nested volumes

Create new volumes using the `New-Volume` cmdlet.

- Nested two-way mirror

    To use nested two-way mirror, reference the `NestedMirror` tier template and specify the size. For example:

    ```PowerShell
    New-Volume -StoragePoolFriendlyName S2D* -FriendlyName Volume01 -StorageTierFriendlyNames NestedMirrorOnHDD -StorageTierSizes 500GB
    ```

    If your capacity drives are solid-state drives (SSD), change `-StorageTierFriendlyNames` to `*OnSSD`.
- Nested mirror-accelerated parity

    To use nested mirror-accelerated parity, reference both the `NestedMirror` and `NestedParity` tier templates and specify two sizes, one for each part of the volume (mirror first, parity second). For example, to create one 500-GB volume that's 20% nested two-way mirror and 80% nested parity, run:

    ```PowerShell
    New-Volume -StoragePoolFriendlyName S2D* -FriendlyName Volume02 -StorageTierFriendlyNames NestedMirrorOnHDD, NestedParityOnHDD -StorageTierSizes 100GB, 400GB
    ```

    If your capacity drives are solid-state drives (SSD), change `-StorageTierFriendlyNames` to `*OnSSD`.

### Step 3: Continue in Windows Admin Center

Volumes that use nested resiliency appear in [Windows Admin Center](/en-us/windows-server/manage/windows-admin-center/overview) with clear labeling, as in the following screenshot. Once they're created, you can manage and monitor them using Windows Admin Center just like any other volume in Storage Spaces Direct.

![Volume management in Windows Admin Center.](media/create-volumes-with-nested-resiliency/windows-admin-center.png)

### Optional: Extend to cache drives

With its default settings, nested resiliency protects against the loss of multiple capacity drives at the same time, or one server and one capacity drive at the same time. To extend this protection to [cache drives](cache), there's another consideration: because cache drives often provide read and write caching for multiple capacity drives, the only way to ensure you can tolerate the loss of a cache drive when the other server is down is to not cache writes, but that impacts performance.

To address this scenario, Storage Spaces Direct offers the option to automatically disable write caching when one server in a two-server cluster is down, and then re-enable write caching once the server is back up. To allow routine restarts without performance impact, write caching isn't disabled until the server has been down for 30 minutes. Once write caching is disabled, the contents of the write cache is written to capacity devices. After this, the server can tolerate a failed cache device in the online server, though reads from the cache might be delayed or fail if a cache device fails.

Note

For an all cache (single media type) physical system, you don't need to consider automatic disabling of write caching when one server in a two-server cluster is down. You need to consider this only with the storage bus layer (SBL) cache, which is required only if you are using HDDs.

(Optional) To automatically disable write caching when one server in a two-server cluster is down, launch PowerShell as Administrator and run:

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.NestedResiliency.DisableWriteCacheOnNodeDown.Enabled" -Value "True"
```

Once set to **True**, the cache behavior is:

| Situation | Cache behavior | Can tolerate cache drive loss? |
| --- | --- | --- |
| Both servers up | Cache reads and writes, full performance | Yes |
| Server down, first 30 minutes | Cache reads and writes, full performance | No (temporarily) |
| After first 30 minutes | Cache reads only, performance impacted | Yes (after the cache is written to capacity drives) |