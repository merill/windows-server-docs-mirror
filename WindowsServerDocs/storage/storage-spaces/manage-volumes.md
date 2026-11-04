---
layout: Conceptual
title: Manage volumes in Azure Local and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/manage-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: How to manage volumes in Azure Local and Windows Server by using Windows Admin Center or PowerShell.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.reviewer: jgerend
ms.date: 2025-02-11T00:00:00.0000000Z
locale: en-us
document_id: 9a9ce6e5-4ab4-0744-bc0c-9845f4f617dd
document_version_independent_id: 9a9ce6e5-4ab4-0744-bc0c-9845f4f617dd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/manage-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/manage-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/manage-volumes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 123f39b0-becf-39b2-3970-43e869a36521
---

# Manage volumes in Azure Local and Windows Server | Microsoft Learn

This article describes how to expand, move, or delete volumes in Azure Local and Windows Server by using either Windows Admin Center or PowerShell.

## Prerequisites

Before you begin to manage volumes, make sure that:

- You have administrator privileges to access the cluster.
- You have access to a management computer that is in the same domain as your cluster.

Here are a few other prerequisites for moving volumes:

- Make sure the volume is in a healthy state before you move it. To find out about the health state of a volume, see [Monitor volumes](/en-us/azure/azure-local/manage/monitor-cluster#monitor-volumes) for Windows Admin Center and [Virtual disk state](/en-us/windows-server/storage/storage-spaces/storage-spaces-states#virtual-disk-states) for PowerShell.
- If using PowerShell to move volumes, make sure you have the Remote Server Administration Tools (RSAT) cmdlets and PowerShell modules for Hyper-V and Failover Clustering. If these aren't already available in your PowerShell session on your management computer, add them using the following command: `Add-WindowsFeature RSAT-Clustering-PowerShell`.

## Expand volumes

This section describes how to expand volumes using Windows Admin Center or PowerShell.

Warning

**Not supported: resizing the underlying storage used by Storage Spaces Direct.** If you are running Storage Spaces Direct in a virtualized storage environment, including in Azure, resizing or changing the characteristics of the storage devices used by the virtual machines isn't supported and will cause data to become inaccessible. Instead, follow the instructions in the Add servers or drives section to add additional capacity before expanding volumes.

# [Windows Admin Center](#tab/windows-admin-center)
Follow these steps to expand volumes in Windows Admin Center:

1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane.
2. On the **Volumes** page, select the **Inventory** tab, and then select the volume that you want to expand. On the volume detail page, the storage capacity for the volume is indicated.

    You can also open the volumes detail page directly from **Dashboard**. On the Dashboard, in the **Alerts** section, select the alert, which notifies you if a volume is running low on storage capacity, and then select **Go To Volume**.
3. At the top of the volumes detail page, select **Settings**.
4. Enter a new larger size in the right pane, and then select **Save**.

    On the volumes detail page, the larger storage capacity for the volume is indicated, and the alert on the Dashboard is cleared.

# [PowerShell](#tab/powershell)
### Capacity in the storage pool

Before you expand a volume, make sure you have enough capacity in the storage pool to accommodate its new, larger footprint. For example, when expanding a three-way mirror volume from 1 TB to 2 TB, its footprint would grow from 3 TB to 6 TB. For the expansion to succeed, you would need at least (6 - 3) = 3 TB of available capacity in the storage pool.

### Familiarity with volumes in Storage Spaces

In Storage Spaces Direct, every volume is composed of several stacked objects: the cluster shared volume (CSV), which is a volume; the partition; the disk, which is a virtual disk; and one or more storage tiers (if applicable). To resize a volume, you need to resize several of these objects.

![Diagram shows the layers of a volume, including cluster shard volume, volume, partition, disk, virtual disk, and storage tiers.](media/manage-volumes/volumes-in-smapi.png)

To familiarize yourself with them, try running the `Get-` cmdlet with the corresponding noun in PowerShell.

For example:

```PowerShell
Get-VirtualDisk
```

To follow associations between objects in the stack, pipe one `Get-` cmdlet into the next.

For example, here's how to get from a virtual disk up to its associated volume:

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-Disk | Get-Partition | Get-Volume
```

### Step 1 – Expand the virtual disk

The virtual disk may use storage tiers, or not, depending on how it was created.

To check, run the following cmdlet:

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-StorageTier
```

If the cmdlet returns nothing, the virtual disk doesn't use storage tiers.

#### No storage tiers

If the virtual disk has no storage tiers, you can expand it directly using the `Resize-VirtualDisk` cmdlet.

Provide the new size in the `-Size` parameter.

```PowerShell
Get-VirtualDisk <FriendlyName> | Resize-VirtualDisk -Size <Size>
```

When you expand the **VirtualDisk**, the associated **Disk** follows automatically and is resized too.

![Animated diagram shows the virtual disk of a volume becoming larger while the disk layer immediately above it automatically becomes larger as a result.](media/manage-volumes/resize-virtualdisk.gif)

#### With storage tiers

If the virtual disk uses storage tiers, you can expand each tier separately using the `Resize-StorageTier` cmdlet.

Get the names of the storage tiers by following the associations from the virtual disk:

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-StorageTier | Select FriendlyName
```

Then, for each tier, provide the new size in the `-Size` parameter:

```PowerShell
Get-StorageTier <FriendlyName> | Resize-StorageTier -Size <Size>
```

Tip

If your tiers are different physical media types (such as **MediaType = SSD** and **MediaType = HDD**) you need to ensure you have enough capacity of each media type in the storage pool to accommodate the new, larger footprint of each tier.

When you expand the **StorageTier**(s), the associated **VirtualDisk** and **Disk** follow automatically and are resized too.

![Animated diagram shows first one then another storage tier becoming large while the virtual disk layer and disk layer above become larger as well.](media/manage-volumes/resize-storagetier.gif)

### Step 2 – Expand the partition

Next, expand the partition using the `Resize-Partition` cmdlet. The virtual disk is expected to have two partitions: the first is `Reserved` and shouldn't be modified; the one you need to resize has **PartitionNumber = 2** and **Type = Basic**.

Provide the new size in the `-Size` parameter. We recommend using the maximum supported size, as follows:

```PowerShell
# Choose virtual disk
$VirtualDisk = Get-VirtualDisk <FriendlyName>

# Get its partition
$Partition = $VirtualDisk | Get-Disk | Get-Partition | Where PartitionNumber -Eq 2

# Resize to its maximum supported size
$Partition | Resize-Partition -Size ($Partition | Get-PartitionSupportedSize).SizeMax
```

When you expand the **Partition**, the associated **Volume** and **ClusterSharedVolume** follow automatically and are resized too.

![Animated diagram shows the virtual disk layer, at the bottom of the volume, growing larger with each of the layers above it growing larger as well.](media/manage-volumes/resize-partition.gif)

That's it!

Tip

You can verify the volume has the new size by running the `Get-Volume` cmdlet.

---

## Move volumes

This section describes how to move Cluster Shared Volumes (CSV) from one cluster node to another by using Windows Admin Center or PowerShell.

You may require to move volumes in several scenarios, including:

- To balance out the storage capacity among different nodes in the cluster.
- To troubleshoot an issue on an unhealthy cluster node.
- To conform to system configuration rules, such as to have certain volumes on a specific cluster node.

    Note

    For stretched clusters, you can move a volume only to another server in the same site.

# [Windows Admin Center](#tab/windows-admin-center)
Follow these steps to move volumes using Windows Admin Center:

1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane on the left.
2. On the **Volumes** page, select the **Inventory** tab, and then select the volume that you want to move.
3. At the top of the **Volumes** page, select **Move**.
4. In the right pane, select the **Destination server** where you want to move the volume to and then select **Move**.

# [PowerShell](#tab/powershell)
You can either run PowerShell locally using the Remote Desktop Protocol (RDP) on a host server, or you can run PowerShell remotely from a management computer.

Follow these steps to move volumes using PowerShell:

1. Launch PowerShell as Administrator on your management computer.
2. To remotely connect to the cluster, run the following command:

    ```powershell
    Enter-PSSession -ComputerName <ClusterName>
    ```

    where:

    - `ClusterName` is the name of your cluster.
3. To list all the CSVs in your cluster, run the following cmdlet:

    ```powershell
    Get-ClusterSharedVolume
    ```

    Here's an example output that lists all the CSVs in the `cluster.contoso.corp.com` cluster:

    ```output
    [cluster.contoso.corp.com]: PS C:\WINDOWS\system32> Get-ClusterSharedVolume
    
    Name                           State  Node
    ----                           -----  ----
    Cluster Virtual Disk (test)    Online azuredoc-srv2
    Cluster Virtual Disk (VMs1)    Online azuredoc-srv1
    Cluster Virtual Disk (VMs2)    Online azuredoc-srv1
    Cluster Virtual Disk (Volume1) Online azuredoc-srv2
    ```
4. To move a CSV from one node to another in your cluster, run the following cmdlet:

    ```powershell
    Move-ClusterSharedVolume -Name "<CSV-Name>" -Node <NodeName>
    ```

    where:

    - `CSV-Name` is the name of the CSV that you want to move. Make sure to type the entire string of the CSV name, and not just the FriendlyName. For example, `Cluster Virtual Disk (Volume1)`.
    - `NodeName` is the name of the cluster node where you want to move the CSV to.

    Here's an example output that moves `Cluster Virtual Disk (Volume1)` to the `azuredoc-srv1` node:

    ```output
       [cluster.contoso.corp.com]: PS C:\WINDOWS\system32> Move-ClusterSharedVolume -Name "Cluster Virtual Disk (Volume1)" -Node azuredoc-srv1
    
       Name                           State  Node
       ----                           -----  ----
       Cluster Virtual Disk (Volume1) Online azuredoc-srv1
    ```

---

## Delete volumes

This section describes how to delete volumes by using Windows Admin Center or PowerShell.

Before you delete a volume, consider the following requirements:

- Ensure the volume you're deleting isn't actively used by Arc Kubernetes clusters or VMs to prevent data loss or system issues.
- Remove the associated workload and then delete the storage paths. For more information, see [Delete a storage path](/en-us/azure/azure-local/manage/create-storage-path?tabs=azurecli#delete-a-storage-path).

# [Windows Admin Center](#tab/windows-admin-center)
1. In Windows Admin Center, connect to a cluster, and then select **Volumes** from the **Tools** pane on the left.
2. On the **Volumes** page, select the **Inventory** tab, and then select the volume that you want to delete.
3. At the top of the volumes detail page, select **Delete**.
4. In the confirmations dialog, confirm that you want to delete the volume, and select **Delete**.

# [PowerShell](#tab/powershell)
Use the **Remove-VirtualDisk** cmdlet to delete the **VirtualDisk** object and return the space it used to the storage pool that exposes the **VirtualDisk** object.

First, launch PowerShell on your management PC and run the **Get-VirtualDisk** cmdlet with the **CimSession** parameter, which is the name of a cluster or server node, for example *clustername.contoso.com*:

```PowerShell
Get-VirtualDisk -CimSession clustername.contoso.com
```

This returns a list of possible values for the **-FriendlyName** parameter, which correspond to volume names on your cluster.

### Example

To delete a mirrored volume called *Volume1,* run the following command in PowerShell:

```PowerShell
Remove-VirtualDisk -FriendlyName "Volume1"
```

You're asked to confirm that you want to perform the action and erase all the data that the volume contains. Choose Y or N.

Warning

This is not a recoverable action. This permanently deletes a **VirtualDisk** Volume object.

---