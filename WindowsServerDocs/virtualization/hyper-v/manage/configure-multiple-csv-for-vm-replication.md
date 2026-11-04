---
layout: Conceptual
title: Configure multiple CSV for VM replication in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/configure-multiple-csv-for-vm-replication
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Configure multiple CSV for VM replication using Hyper-V Replica to increase scalability and fault tolerance in Windows Server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-15T00:00:00.0000000Z
locale: en-us
document_id: 25c08c01-d35c-9e7f-6e6e-0f85ddf9283f
document_version_independent_id: 25c08c01-d35c-9e7f-6e6e-0f85ddf9283f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/configure-multiple-csv-for-vm-replication.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/configure-multiple-csv-for-vm-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/configure-multiple-csv-for-vm-replication.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f00b583c-9434-382a-7fd8-22a7f632108b
---

# Configure multiple CSV for VM replication in Windows Server | Microsoft Learn

When setting up Virtual Machine (VM) replication, you might encounter a limitation where only a single path for Cluster Shared Volumes (CSV) can be specified. This guide outlines how to overcome this limitation to configure multiple CSV for VM replication. This approach provides greater control over your VM by improving flexibility and storage efficiency of your resources.

## Prerequisites

The following are required on your device before proceeding:

- The **Hyper-V** role must be installed. To learn more, see [Install the Hyper-V role on Windows Server](/en-us/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server).
- VM replication is enabled and inbound firewall rules are configured. To learn more, see [Set up Hyper-V Replica](/en-us/windows-server/virtualization/hyper-v/manage/set-up-hyper-v-replica).
- Sufficient disk space for successful storage migration.

Note

During the replication process, the hardware and network you use affects the services that rely on them. Depending on the amount of data replicated between the source and target systems, this process consumes a large amount of system resources. Your device performance is impacted until this process completes.

## Configure multiple CSV locations

When copying VMs through a replication process, it's possible to use multiple storage volumes to store the replicated data. There are two methods to configure new replication locations, through the Hyper-V Manager UI or via PowerShell.

# [Hyper-V](#tab/hyperv)
1. Open the **Hyper-V Manager**, under **Actions**, select **Hyper-V Settings**.
2. Under **Authorization and storage**, select either **Allow replication from any authenticated server** or **Allow replication from the specified servers**, then select **Browse**.
3. In the **Select Folder** window, choose a new default location, then select **Select Folder**.

When changes are made to the "default location" where replication is enabled for a VM, the new target volume is used for any new subsequent replication enablement. However, VMs that were already being replicated continues to use the original target volume that was set up when replication was first enabled.

# [PowerShell](#tab/powershell)
Open an elevated PowerShell window and run the following command:

```powershell
$VM = "MyVM"
$Destination = "E:\MyVM_NewPath"
Move-VMStorage $VM -DestinationStoragePath $Destination
```

This command moves the VM storage to the specified destination path, allowing for configuration of multiple CSV for VM replication.

This approach is effective in different situations, including prereplication, post-replication, and during delta transfers of a replicated VM. During a VM storage move operation, delta replication is temporarily paused and automatically resumes once the move is complete. However, in some situations, such as when there's low disk space or storage movement latency, it might be necessary to manually resume the replication process.

---