---
layout: Conceptual
title: Adjust storage repair speed in Azure Local and Windows Server clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-repair-speed
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: How to adjust storage repair speed in Azure Local and Windows Server clusters by using Windows Admin Center or PowerShell.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.reviewer: tinawu
ms.date: 2023-06-05T00:00:00.0000000Z
locale: en-us
document_id: 8615dcef-9620-2f60-5438-0489d5d407e3
document_version_independent_id: 8615dcef-9620-2f60-5438-0489d5d407e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/storage-repair-speed.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/storage-repair-speed
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/storage-repair-speed.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 8cd774dd-fe37-5782-54a1-fb795675323d
---

# Adjust storage repair speed in Azure Local and Windows Server clusters | Microsoft Learn

User-adjustable storage repair speed offers more control over the data resync process by allocating resources to either repair data copies (resiliency) or run active workloads (performance). This feature helps improve availability and enables you to service your clusters more flexibly and efficiently.

## Storage repair speed settings

The storage speed repair settings are:

| **Setting** | **Queue depth** | **Resource allocation** |
| --- | --- | --- |
| Very low | 1 | Most resources to active workloads |
| Low | 2 | More resources to active workloads |
| Medium (default) | 4 | Balances workloads and repairs |
| High | 8 | More resources to resync and repairs |
| Very high | 16 | Most resources to resync and repairs |

**Very low** to **Low** settings allocates more resources to active workloads, allowing the server to complete mission-critical tasks. Take caution when changing the setting to **Very low**, as it may impact the time for storage to regain full resiliency. **High** to **Very high** settings prioritize storage resync and repairs, allowing a patch and update cycle to complete faster. The default setting is **Medium**, which ensures a balance of workload and repair prioritization. It's recommended to keep the repair speed set to **Medium** in most cases, unless you have a good reason for prioritizing either resiliency or performance.

Important

When storage repair speed is set to **Very high**, active workloads and cluster performance can be impacted. Likewise, when repair speed is set to **Very low**, it will take more time for storage to regain full resiliency.

## Change storage repair speed using Windows Admin Center

To change the storage repair speed for a cluster by using Windows Admin Center, do the following:

[![You can change storage repair speeds in Cluster Manager &gt; Settings &gt; Storage Spaces and pools](media/storage-repair-speed/change-storage-repair-speed.png)](media/storage-repair-speed/change-storage-repair-speed.png#lightbox)

1. In Windows Admin Center, connect to a cluster, and then select **Settings** from the **Tools** pane.
2. In the **Settings** pane, select **Storage Spaces and pools**.
3. Use the **Storage repair speed** dropdown to select the desired speed.
4. Review the caution text if selecting **Very low** or **Very high**.
5. Select **Save**.

## Change storage repair speed using PowerShell

To check the current repair speed setting:

```PowerShell
Get-StorageSubSystem -FriendlyName <name of cluster subsystem> | ft FriendlyName,VirtualDiskRepairQueueDepth
```

To set the repair speed:

```PowerShell
Set-StorageSubSystem -FriendlyName <name of cluster subsystem> -VirtualDiskRepairQueueDepth <value>
```