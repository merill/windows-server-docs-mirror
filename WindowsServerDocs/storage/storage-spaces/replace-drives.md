---
layout: Conceptual
title: Replace failed drives on Azure Local | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/replace-drives
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: How to replace failed drives on Azure Local.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.reviewer: jgerend
ms.date: 2025-02-10T00:00:00.0000000Z
locale: en-us
document_id: 0134f1e5-4c1f-ac65-83c5-d546c15122e1
document_version_independent_id: 0134f1e5-4c1f-ac65-83c5-d546c15122e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/replace-drives.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/replace-drives
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/replace-drives.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 031eecb1-5f85-f429-852f-0b8282330862
---

# Replace failed drives on Azure Local | Microsoft Learn

Azure Local works with direct-attached SATA, SAS, NVMe, and persistent memory drives that are physically attached to a single server. Storage Spaces Direct automatically retires and evacuates failed drives. As a result, the drive status is marked as **Retired**, and its storage capacity bar is empty.

If a drive fails, you need access to the physical server hardware to replace it.

## Find the alert

When a drive fails, an alert appears in the upper **Alerts** area of the Windows Admin Center Dashboard.

1. In Windows Admin Center, select the alert to see details, like the drive's physical location.
2. To see more details, select **Drives** under **Tools** in the left pane to browse drives and see their status. On the **Inventory** tab, you can sort, group, and search across drives.
3. If your hardware supports it, you can select **Light On** or **Light Off** to control the drive's indicator light.
4. Physically remove the failed drive and insert its replacement.

## Wait for the alert to clear

In Windows Admin Center, under the **Drives &gt; Inventory** tab, the new drive appears. In time, the alert clears, volumes repair back to OK status, and storage rebalances onto the new drive automatically.

## Troubleshooting

If the new drive isn't added to the pool, it may be because AutoPool is disabled. To determine, run the following PowerShell command as administrator:

```powershell
Get-StorageSubsystem Cluster* | Get-StorageHealthSetting | select "System.Storage.PhysicalDisk.AutoPool.Enabled"
```

If the value is **True**, AutoPool is enabled. If the value is **False**, AutoPool is disabled. You have two options to resolve the issue:

### Option A

This option leaves AutoPool disabled and manually adds the disks to the storage pool. Run the following series of PowerShell commands as administrator:

Run the following and verify the new physical disk is listed with `OperationalStatus` is **OK**, and `HealthStatus` is **Healthy**.

```powershell
Get-PhysicalDisk -CanPool $true
```

Next, run the following command and make a note of the **FriendlyName** of the storage pool that you want to add the disk to. If it's a stretched cluster, you should see more than one pool name:

```powershell
Get-StoragePool -IsPrimordial $False
```

Next, run the following command:

```powershell
$disks = Get-PhysicalDisk -CanPool $true
```

Lastly, run the following command:

```powershell
Add-PhysicalDisk -StoragePoolFriendlyName "FriendlyName_from_step2" -PhysicalDisks $disks
```

### Option B

This option enables AutoPool and lets the Health service add the disk to the pool. Run the following PowerShell command as administrator:

```powershell
Get-StorageSubsystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.PhysicalDisk.AutoPool.Enabled" -Value True
```