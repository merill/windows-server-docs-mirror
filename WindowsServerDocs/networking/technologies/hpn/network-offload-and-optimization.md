---
layout: Conceptual
title: Network offload and optimization technologies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/hpn/network-offload-and-optimization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about the different network offload and optimization features available in Windows Server 2016 and discuss how they help make networking more efficient.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-26T00:00:00.0000000Z
locale: en-us
document_id: e035a443-af2b-9071-ed99-34606cdd8071
document_version_independent_id: 00a082bd-88fb-78ff-491f-be17ffc9be35
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/hpn/network-offload-and-optimization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/hpn/network-offload-and-optimization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/hpn/network-offload-and-optimization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f9cf537e-3e5a-4f31-a8e2-d06c28985eda
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b0200c40-0bea-4a73-a79b-8c68e19d3d16
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e568c0ee-9c3d-e097-d788-227a0265e960
---

# Network offload and optimization technologies | Microsoft Learn

In this topic, we give you an overview of the different network offload and optimization features available in Windows Server 2016 and discuss how they help make networking more efficient. These technologies include Software Only (SO) features and technologies, Software and Hardware (SH) integrated features and technologies, and Hardware Only (HO) features and technologies. To learn more, see [Host network requirements for Azure Local](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

The three categories of networking features available in Windows Server 2016 are:

1. [Software only (SO) features and technologies](hpn-software-only-features): These features are implemented as part of the OS and are independent of the underlying NIC(s). Sometimes these features will require some tuning of the NIC for optimal operation. Examples of these include Hyper-V features such as vmQoS, ACLs, and non-Hyper-V features like NIC Teaming.
2. [Software and Hardware (SH) integrated features and technologies](hpn-software-hardware-features): These features have both software and hardware components. The software is intimately tied to hardware capabilities that are required for the feature to work. Examples of these include VMMQ, VMQ, Send-side IPv4 Checksum Offload, and RSS.
3. [Hardware Only (HO) features and technologies](hpn-hardware-only-features): These hardware accelerations improve networking performance in conjunction with the software but are not intimately part of any software feature. Examples of these include Interrupt Moderation, Flow Control, and Receive-side IPv4 Checksum Offload.
4. [NIC advanced properties](hpn-nic-advanced-properties): You can manage NICs and all the features via Windows PowerShell using the NetAdapter cmdlet. You can also manage NICs and all the features using Network Control Panel (ncpa.cpl).

Tip

- SO features and technologies are available in all hardware architectures, regardless of NIC speed or NIC capabilities.
- SH and HO features are available only when your network adapter supports the features or technologies.