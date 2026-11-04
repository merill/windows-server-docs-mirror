---
layout: Conceptual
title: Manage Cluster Shared Volumes | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/failover-cluster-manage-cluster-shared-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: Learn how to manage Cluster Shared Volumes (CSVs) in a failover cluster in Windows Server.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-07-08T00:00:00.0000000Z
locale: en-us
document_id: 0dc76fdb-e714-2f10-1f47-351bc9ec3d5b
document_version_independent_id: 0dc76fdb-e714-2f10-1f47-351bc9ec3d5b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/failover-cluster-manage-cluster-shared-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/failover-cluster-manage-cluster-shared-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/failover-cluster-manage-cluster-shared-volumes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e159faa7-36ae-0a10-e6c6-9b2ea3ba333c
---

# Manage Cluster Shared Volumes | Microsoft Learn

Cluster Shared Volumes (CSVs) are a Windows Server and Azure Local feature that enables multiple nodes in a failover cluster to concurrently access the same NTFS or ReFS volume. This shared access is essential for high-availability workloads such as Hyper-V and Scale-Out File Server, allowing virtual machines and applications to move seamlessly between cluster nodes without requiring changes to drive letters or mount points. CSVs streamline storage management, enhance flexibility, and support continuous availability. You can manage CSVs using tools like Failover Cluster Manager and Windows PowerShell, which provide capabilities for adding disks, configuring caching, and performing backups.

## Prerequisites

To manage CSVs, ensure the following prerequisites are met:

- Your device must be running Windows Server 2012 or later and the **Failover Clustering** feature is installed on all nodes (servers) in the cluster. To learn more, see [Add or remove roles and features in Windows Server](/en-us/windows-server/administration/server-manager/add-remove-roles-features).
- You must be a member of the **Administrators**, **Domain Admins**, or **Cluster Administrators** group.
- Your cluster configuration must have at least two nodes configured in a failover cluster. All nodes must be joined to the same Active Directory (AD) domain.
- At least one shared disk (LUN) must be accessible by all cluster nodes and configured as a cluster disk using NTFS or ReFS. Format SAN volumes with NTFS and Storage Spaces Direct (S2D) volumes with ReFS for optimal performance. If you're using iSCSI or Fibre Channel for shared storage, ensure that multipath I/O (MPIO) is properly configured to provide redundancy and optimal performance.
- At least two network interfaces per node are recommended, one for cluster communication and one for client access. Ensure that the network settings allow for proper communication between nodes, including correct IP addresses and subnet configurations. Make sure firewalls are configured to permit necessary cluster traffic.

## Add a CSV to a failover cluster

The CSV feature is enabled by default in Failover Clustering. To add a disk to a CSV, you must add a disk to the **Available Storage** group of the cluster (if it isn't already added), and then add the CSV on the cluster. When you add disks to a Windows Failover Cluster, they're typically placed in the **Available Storage** group if they aren't immediately assigned to any specific cluster roles or configurations. This placement acts as a holding area for disks that are recognized by the cluster but not yet designated for a specific use within the cluster.

You can use the Failover Cluster Manager or PowerShell to perform these procedures.

# [Failover Cluster Manager](#tab/fcm)
1. In **Server Manager**, select **Tools**, then select **Failover Cluster Manager**.

    Alternatively, select **Start**, type **cluadmin.msc**, and press **Enter**.
2. In the left pane under **Failover Cluster Manager**, expand your cluster, and then expand **Storage**.
3. Select **Disks**, then in the right pane, select **Add Disk**.
4. The wizard lists the available disks that can be added to the cluster. Select the disk you want to add and select **OK**.
5. The newly added disk is assigned to **Available Storage** under the **Assigned To** column. Right-click on the disk and select **Add to Cluster Shared Volumes**.

# [PowerShell](#tab/powershell)
1. Open PowerShell in an elevated window.
2. To view all available disks that can be added to your cluster, run the following command:

    ```powershell
    Get-ClusterAvailableDisk
    ```
3. To add all available disks to the **Available Storage** group, run the following command:

    ```powershell
    Add-ClusterDisk
    ```

    To add a specific disk, you can run the following command and filter based on properties like `Number`, `Name`, or `UniqueId`. This example uses the `Number` associated to `DiskNumber`:

    ```powershell
    $addClusterDisk = Get-ClusterAvailableDisk | Where-Object { $_.Number -eq <DiskNumber> }
    $addClusterDisk | Add-ClusterDisk
    ```
4. Once the disk is added to the cluster, run the following command to add the disk as a CSV:

    ```powershell
    Add-ClusterSharedVolume -Name "Cluster Disk Name"
    ```
5. To verify all available disks added as a CSV, run the following command:

    ```powershell
    Get-ClusterSharedVolume
    ```

---

Tip

You can rename the CSV volumes in the `%SystemDrive%\ClusterStorage` folder.

## Enable the CSV cache for read-intensive workloads (optional)

The CSV cache enhances performance by using system memory (RAM) to cache block-level, read-only, unbuffered I/O operations. Since unbuffered I/O bypasses the standard cache manager, enabling the CSV cache is beneficial for workloads like Hyper-V, where virtual hard disks (VHDs) are accessed using unbuffered I/O. The CSV cache accelerates read operations but doesn't cache write operations. This feature is also valuable in Scale-Out File Server environments to improve read performance. It's recommended that you enable CSV cache for all clustered Hyper-V and Scale-Out File Server deployments.

Note

In Windows Server 2016 and later versions, the CSV cache is enabled by default with 1 gibibyte (GiB) of memory allocated. In Windows Server 2012 R2, the cache is enabled by default, but you must manually specify the amount of memory to reserve for the block cache as it isn't preallocated. In Windows Server 2012, administrators must manually enable and configure the CSV cache as it's disabled by default.

The following table describes the two configuration settings that control the CSV cache.

| Windows Server 2012 R2 and later | Windows Server 2012 | Description |
| --- | --- | --- |
| BlockCacheSize | SharedVolumeBlockCacheSizeInMB | This is a cluster common property that allows you to define how much memory (in megabytes) to reserve for the CSV cache on each node in the cluster. For example, if a value of 512 is defined, then 512 MB of system memory is reserved on each node. In many clusters, 512 MB is a recommended value. The default setting is 0 (disabled). |
| EnableBlockCache | CsvEnableBlockCache | This is a private property of the cluster Physical Disk resource. It allows you to enable CSV cache on an individual disk that is added as a CSV. In Windows Server 2012, the default setting is 0 (disabled). To enable CSV cache on a disk, configure a value of 1. By default, in Windows Server 2012 R2, this setting is enabled. |

To enable the CSV cache on your CSV, open PowerShell in an elevated window and perform the following steps:

1. To view the current CSV cache setting, run the following command:

    ```powershell
    Get-ClusterSharedVolume | Select Name, BlockCacheSize
    ```
2. To set the amount of memory for the CSV cache to `512 MB` for Windows Server 2012 R2 and later, run the following command:

    ```powershell
    (Get-Cluster).BlockCacheSize = 512
    ```

    For Windows Server 2012, run the following command:

    ```powershell
    (Get-Cluster).SharedVolumeBlockCacheSizeInMB = 512
    ```
3. To enable the CSV cache in Windows Server 2012, run the following command replacing `Cluster Disk #` with your value:

    ```PowerShell
    Get-ClusterSharedVolume "Cluster Disk #" | Set-ClusterParameter CsvEnableBlockCache 1
    ```

## Monitor CSV cache

You can monitor the CSV cache using Performance Monitor. This tool helps administrators track cache usage, identify potential bottlenecks, and analyze cache efficiency. Monitoring metrics such as cache hits, misses, and memory usage enables proactive performance tuning and helps maintain optimal cluster reliability. To add this counter, follow these steps:

1. Select **Start**, type **perfmon**, then select **Performance Monitor**.
2. In the left pane, select **Performance Monitor**, then in the right pane, select the green **+** (plus sign) button.
3. In the **Add Counters** window, under **Select counters from computer**, choose from the list **Cluster CSV Volume Cache**.
4. Select **Add &gt;&gt;** then select **OK**.

Note

- In Windows Server 2012, you can allocate only 20% of the total physical RAM to the CSV cache. In Windows Server 2012 R2 and later, you can allocate up to 80%. Because Scale-Out File Servers aren't typically memory constrained, you can accomplish large performance gains by using the extra memory for the CSV cache.
- To avoid resource contention, you should restart each node in the cluster after you modify the memory that is allocated to the CSV cache. In Windows Server 2012 R2 and later, a restart isn't required.
- After you enable or disable CSV cache on an individual disk, for the setting to take effect, you must take the physical disk resource offline and bring it back online.

## Backing up CSVs

There are multiple methods to back up data stored on CSVs in a failover cluster. You can use a Microsoft backup application or a non-Microsoft application. In general, backing up CSVs follows the same procedures and requirements as backing up other clustered storage volumes formatted with NTFS or ReFS. No extra or unique backup steps are required specifically for CSVs. CSV backups also don't disrupt other CSV storage operations.

Be sure to carefully review what data your backup application backs up and restores, which CSV features it supports, and the resource requirements for the application on each cluster node. You should consider the following factors when you select a backup application and backup schedule for your CSVs:

- You might need to provide administrative credentials when backing up a failover cluster.
- Volume-level backup of a CSV volume can be run from any node that connects to the CSV volume.
- Your backup application can use software snapshots or hardware snapshots. Depending on the ability of your backup application to support them, backups can use application-consistent and crash-consistent Volume Shadow Copy Service (VSS) snapshots.
- If you're backing up CSV that have multiple running virtual machines (VM), you should generally choose a management operating system-based backup method. If your backup application supports it, multiple virtual machines can be backed up simultaneously.
- CSVs support backup operations using Windows Server Backup. However, Windows Server Backup is a basic solution and may not meet the needs of larger clusters. It doesn't support application-consistent backups for VMs on CSVs, providing only crash-consistent volume-level backups. When you restore a crash-consistent backup, the VM is in the same state as if it had crashed at the time of backup. Although backing up a VM on a CSV volume completes successfully, an error event is logged to indicate that application-consistent backup isn't supported.

Warning

If you need to restore the backup data onto a CSV volume, be aware of the capabilities and limitations of the backup application to maintain and restore application-consistent data across the cluster nodes. For example, with some applications, if the CSV is restored on a node that is different from the node where the CSV volume was backed up, you might inadvertently overwrite important data about the application state on the node where the restore is taking place.