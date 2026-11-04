---
layout: Conceptual
title: Live Migration Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/live-migration-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Gives overview of live migration functionality in Windows Server 2016.
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2017-06-27T00:00:00.0000000Z
locale: en-us
document_id: 6ca8148b-52ed-2aae-3458-7661a6575bd3
document_version_independent_id: 8a7b57da-bcde-fa61-cf0c-157e032f1501
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/live-migration-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/live-migration-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/live-migration-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 23f24510-6556-99f5-ef76-18a06edf1c91
---

# Live Migration Overview | Microsoft Learn

Live migration is a Hyper-V feature in Windows Server. It allows you to transparently move running Virtual Machines from one Hyper-V host to another without perceived downtime. The primary benefit of live migration is flexibility; running Virtual Machines are not tied to a single host machine. This allows actions like draining a specific host of Virtual Machines before decommissioning or upgrading it. When paired with Windows Failover Clustering, live migration allows the creation of highly available and fault tolerant systems.

## Related Technologies and Documentation

Live migration is often used in conjunction with a few related technologies like Failover Clustering and System Center Virtual Machine Manager. If you're using Live Migration via these technologies, here are pointers to their latest documentation:

- [Failover Clustering](../../../failover-clustering/failover-clustering-overview) (Windows Server 2016)
- [System Center Virtual Machine Manager](/en-us/system-center/vmm/) (System Center 2016)

If you're using older versions of Windows Server, or need details on features introduced in older versions of Windows Server, here are pointers to historical documentation:

- [Live Migration](/en-us/previous-versions/windows/it-pro/microsoft-hyper-v-server-2008-R2/ee815293%28v=ws.10%29) (Windows Server 2008 R2)
- [Live Migration](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831435%28v=ws.11%29) (Windows Server 2012 R2)
- [Failover Clustering](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831579%28v=ws.11%29) (Windows Server 2012 R2)
- [Failover Clustering](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff182338%28v=ws.10%29) (Windows Server 2008 R2)
- [System Center Virtual Machine Manager](/en-us/previous-versions/system-center/system-center-2012-R2/gg610610%28v=sc.12%29) (System Center 2012 R2)
- [System Center Virtual Machine Manager](https://technet.microsoft.com/library/cc917964.aspx) (System Center 2008 R2)

## Live Migration in Windows Server 2016

In Windows Server 2016, there are fewer restrictions on live migration deployment. It now works without Failover Clustering. Other functionality remains unchanged from previous releases of Live Migration. For more details on configuring and using live migration without Failover Clustering:

- [Set up hosts for live migration without Failover Clustering](../deploy/set-up-hosts-for-live-migration-without-failover-clustering)
- [Use live migration without Failover Clustering to move a virtual machine](use-live-migration-without-failover-clustering-to-move-a-virtual-machine)