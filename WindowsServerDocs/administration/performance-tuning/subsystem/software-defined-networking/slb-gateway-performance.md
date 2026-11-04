---
layout: Conceptual
title: SLB Gateway Performance Tuning in Software Defined Networks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/subsystem/software-defined-networking/slb-gateway-performance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: SLB Gateway performance tuning guidelines on SDN networks
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: a4c850ed-503f-de4c-2f2a-17f3030e1fe1
document_version_independent_id: c0c29340-8e0b-86fd-aff2-f10ecf672013
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/subsystem/software-defined-networking/slb-gateway-performance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/subsystem/software-defined-networking/slb-gateway-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/subsystem/software-defined-networking/slb-gateway-performance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/f98c9a19-e481-4f15-8047-76b641e6ed57
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/f5685781-a4fd-40f1-8126-59abde4643bf
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 3dcfce63-653f-3251-bc89-8efbf4b58236
---

# SLB Gateway Performance Tuning in Software Defined Networks | Microsoft Learn

Applies to: Windows Server (All supported versions)

Software load balancing is provided by a set of Load Balancer Multiplexor (Mux) VMs, with the load balancer manager in the Network Controller VMs and the Hyper-V Virtual Switch.

No other performance tuning is required to configure the Network Controller or the Hyper-V host for load balancing beyond what is described in the [Software Defined Networking](./) section. If you're using SR-IOV for the Muxes, make sure to review the SLB Mux VM Configuration section.

## SLB Mux VM Configuration

SLB Mux virtual machines are deployed in an active-active configuration, meaning that every Mux VM that's deployed and added to the Network Controller can process incoming requests. In an active-active configuration, the total aggregate throughput of all of the connections is limited only by the number of Mux VMs that you deployed.

An individual connection to a Virtual IP (VIP) will always be sent to the same Mux, assuming the number of muxes remains constant and its throughput is limited to the throughput of a single Mux VM. Muxes only process the inbound traffic that's going to a VIP. Response packets go directly from the VM that's sending the response to the physical switch that forwards it on to the client.

In some cases, when the source of the request originates from an SDN host that's added to the same Network Controller that manages the VIP, further optimization of the inbound path for the request is also performed. With the SDN host and the VIP managed by the same controller, most packets are able to travel directly from the client to the server, bypassing the Mux VM entirely. No other configuration is required for this optimization to happen.

Each SLB Mux VM must be sized according to the guidelines provided in the SDN infrastructure virtual machine role requirements section. Learn more in the [Plan a Software Defined Network Infrastructure](/en-us/azure/azure-local/concepts/plan-software-defined-networking-infrastructure?context=/windows-server/context/windows-server-edge-networking) article.

## Single Root IO virtualization (SR-IOV)

When you're using 40 Gigabit Ethernet, the ability for the virtual switch to process packets for the Mux VM becomes the limiting factor for Mux VM throughput. SR-IOV should be enabled on the SLB VM's VM Network Adapter to ensure that the virtual switch isn't the bottleneck.

To enable SR-IOV, you must enable it on the virtual switch when the virtual switch is created. In this example, we're creating a virtual switch with switch embedded teaming (SET) and SR-IOV:

```syntax
    new-vmswitch -Name SDNSwitch -EnableEmbeddedTeaming $true -NetAdapterName @("NIC1", "NIC2") -EnableIOV $true
```

It must also be enabled on the virtual network adapter(s) of the SLB Mux VM that process the data traffic. In this example, SR-IOV is being enabled on all adapters:

```syntax
    get-vmnetworkadapter -VMName SLBMUX1 | set-vmnetworkadapter -IovWeight 50
```