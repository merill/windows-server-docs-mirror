---
layout: Conceptual
title: Network HUD Overview for Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/network-hud-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Network HUD detects networking issues in physical Windows Server 2025 Datacenter clusters. Learn about requirements, health faults, and detection scenarios.
author: robinharwood
ms.author: roharwoo
ms.reviewer: baselkablawi
ms.date: 2026-11-17T00:00:00.0000000Z
ms.topic: concept-article
ai-usage: ai-assisted
locale: en-us
document_id: 6ec93b68-9ef9-67d0-c8cb-1da79ca1271e
document_version_independent_id: 6ec93b68-9ef9-67d0-c8cb-1da79ca1271e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/network-hud-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/network-hud-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/network-hud-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://authoring-docs-microsoft.poolparty.biz/devrel/beac614b-f66d-40ed-a947-3996de709333
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://authoring-docs-microsoft.poolparty.biz/devrel/9da05372-4706-43ec-a899-f436adab380d
platformId: 1aaf063e-8e59-45cb-8b54-e987886de026
---

# Network HUD Overview for Windows Server 2025 | Microsoft Learn

Network HUD is a host networking diagnostics tool for physical Windows Server 2025 Datacenter failover clusters. It uses Network ATC intent data and signals from cluster nodes, network adapters, and physical switches to detect configuration and operational conditions and report them as cluster health faults.

Network HUD helps cluster administrators correlate host and physical network information without gathering it separately. Its detections identify conditions for administrators to investigate; Network HUD doesn't automatically remediate the reported conditions or guarantee that workloads avoid performance or connectivity problems.

Network HUD helps you:

- Identify physical network misconfigurations, such as missing VLANs or Priority Flow Control (PFC) priorities.
- Detect adapter instability and Peripheral Component Interconnect Express (PCIe) bandwidth limitations.
- Validate host networking configuration consistency and identify driver maintenance needs.
- Review health faults and recommended actions in Windows Admin Center or PowerShell.

After reading this article, you'll understand when Network HUD applies and how to use its detections and health faults to investigate host networking conditions.

## Network HUD availability and requirements

Network HUD is available as a benefit of Windows Server Management enabled by Azure Arc. For benefit availability and enrollment information, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview).

A supported Network HUD deployment has the following requirements:

- A physical Windows Server failover cluster with at least two servers. This deployment doesn't support virtual machines or offline deployments.
- Windows Server 2025 Datacenter on every cluster node.
- The Hyper-V role and its management tools on every cluster node.
- Configure Network ATC with host networking intents.
- Enable Storage Spaces Direct (S2D), which provides the Health Service that Network HUD uses to report faults. For cluster hardware requirements, see [Storage Spaces Direct hardware requirements](../storage/storage-spaces/storage-spaces-direct-hardware-requirements).
- Install the Data Center Bridging and Link Layer Discovery Protocol (LLDP) tools on every cluster node.
- Connect every cluster node to Azure Arc and enroll it in the Windows Server Management benefit.

## Network HUD terminology

The following terms describe the configuration and detection model that Network HUD uses:

| Term | Definition |
| --- | --- |
| Network HUD | A Windows Server Management enabled by Azure Arc benefit that detects host networking configuration and operational issues. |
| Content | Logic that Network HUD uses to evaluate host and network signals. |
| Detection | An individual check that identifies a configuration or operational condition. |
| Network ATC intent | A definition that specifies how to use one or more physical network adapters. Each physical adapter can belong to only one intent. |
| Network ATC intent type | A role assigned within an intent. The supported types are Management, Compute, Storage, and Stretch. Stretch is similar to Storage but doesn't use remote direct memory access (RDMA). |

## How Network HUD works

Network HUD interprets host and physical network signals in the context of Network ATC intents and cluster state. For example, it can associate an unstable adapter with the storage, compute, or management traffic that its intent assigns to it. Each node evaluates its local configuration and signals, and Network HUD publishes detected conditions to the cluster Health Service.

Network HUD uses the following sources to evaluate conditions:

- Network ATC intent metadata, which identifies the traffic roles for physical adapters.
- LLDP information from physical switches, including virtual local area networks (VLANs) and Priority Flow Control (PFC) priorities that the switches advertise.
- Adapter and driver properties, link-state events, performance counters, and hardware properties.

Network HUD reports detected conditions through health faults and diagnostic events. Health faults appear through the cluster Health Service in Windows Admin Center and PowerShell, with recommended actions to help you investigate and resolve issues. Network HUD runs locally on each node and requires Azure Arc connectivity.

## Network HUD health detection scenarios

Network HUD reports configuration and operational conditions through the cluster Health Service. The following table describes its detection inventory:

| Network HUD detection | Condition detected |
| --- | --- |
| Failed Network ATC intents | Identifies intents that didn't provision completely, including missing virtual adapters, quality-of-service settings, or storage settings. |
| Missing Network ATC intent types | Identifies missing traffic roles so administrators can determine whether the intended management, compute, storage, or stretch configuration is present. |
| Peripheral Component Interconnect Express (PCIe) bandwidth oversubscription | Compares aggregate network adapter link rates with the reported PCIe slot and lane capacity to identify potential oversubscription. |
| Unstable (flapping) adapters | Identifies repeated adapter link-state changes or resets. |
| Inbox drivers in production | Identifies adapters that use inbox drivers instead of validated vendor drivers. |
| Aging drivers | Identifies drivers whose reported driver date is more than 12 months old by default. The detection doesn't use the driver installation date or determine whether a newer driver is available. |
| Driver version inconsistency | Compares the major and minor driver versions that equivalent adapters report and identifies differences. |
| LLDP operational status | Identifies missing LLDP packets or LLDP parsing failures that can limit physical switch and fabric validation. |
| Misconfigured or inconsistent VLANs | Compares VLANs that switches advertise in three scopes: adapters in the same intent on one host, the same intent across cluster hosts, and VLAN availability for compute workload virtual machine (VM) network adapters on every adapter in that intent across the cluster. |
| Inconsistent PFC | For storage intent adapters, compares the PFC priorities that the physical switch advertises through LLDP with the priorities that Network ATC enables on the host. |

## Network HUD health faults and events

Network HUD diagnostic events and cluster health faults serve different purposes. Events in the Operational and Diagnostic channels provide node-local diagnostic information. Active cluster health faults report detected conditions and recommended actions through the cluster health service.

Run the following command locally on a cluster node to query active cluster health faults for Network HUD:

```powershell
Get-HealthFault | Where-Object Reason -like '*HUD*'
```

The `NetworkHUD` service can be running even when a Network HUD detection scenario didn't initialize. Similarly, an empty health-fault result means that the query returned no active matching faults; it doesn't prove that every detection initialized successfully.

You can also view Network HUD faults and recommended actions in Windows Admin Center cluster alerts. The following screenshot shows an example:

[!\[Screenshot of Windows Admin Center showing two Network HUD driver fault alerts for a cluster.\](media/network-hud/windows-admin-center-alerts.png)
 The Windows Admin Center dashboard for cluster CONTOSOSRV01 shows two identical server alerts. Each alert reports that an inbox driver was detected on the adapter in slot 3 for the intent named convergedintent and that inbox drivers aren't supported.](media/network-hud/windows-admin-center-alerts.png#lightbox)

An alert clears after Network HUD no longer detects the condition that caused it. The alert might not clear immediately, and clearing doesn't indicate that Network HUD automatically repaired the condition.