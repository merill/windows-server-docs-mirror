---
layout: Conceptual
title: Performance Tuning Software Defined Networks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/subsystem/software-defined-networking/
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Software Defined Network (SDN) performance tuning guidelines
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 53fd9bf9-ddf6-a5db-c5bf-47fbec2e5e69
document_version_independent_id: 25e92d0f-46dc-1110-ea78-2dbdeecbc12c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/subsystem/software-defined-networking/index.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/subsystem/software-defined-networking/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/subsystem/software-defined-networking/index.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b4b400a4-69f8-ece8-1ad9-4482c77310b9
---

# Performance Tuning Software Defined Networks | Microsoft Learn

Software Defined Networking (SDN) in Windows Server 2016 is made up of a combination of a Network Controller, Hyper-V Hosts, Software Load Balancer Gateways and HNV Gateways. For tuning of each of these components refer to the following sections:

## Network Controller

The network controller is a Windows Server role which must be enabled on Virtual Machines running on hosts that are configured to use SDN and are controlled by the network controller.

Three Network Controller enabled VMs are sufficient for high availability and maximum performance. Each VM must be sized according to the guidelines provided in the SDN infrastructure virtual machine role requirements section of the [Plan a Software Defined Network Infrastructure](/en-us/azure/azure-local/concepts/plan-software-defined-networking-infrastructure?context=/windows-server/context/windows-server-edge-networking) topic.

### SDN Quality of Service (QoS)

To ensure virtual machine traffic is prioritized effectively and fairly, it is recommended that you configure SDN QoS on the workload virtual machines. For more information on configuring SDN QoS, refer to the [Configure QoS for a Tenant VM Network Adapter](../../../../networking/sdn/manage/configure-qos-for-tenant-vm-network-adapter) topic.

## Hyper-V Host Networking

The guidance provided in the Hyper-V network I/O performance section of the [Performance Tuning for Hyper-V Servers](../../role/remote-desktop/session-hosts) guide is applicable when SDN is used, however this section covers additional guidelines that must be followed to ensure the best performance when using SDN.

### Physical Network Adapter (NIC) Teaming

For best performance and fail-over capabilities, it is recommended that you configure the physical network adapters to be teamed. When using SDN you must create the team with Switch Embedded Teaming (SET).

The optimal number of team members is two as virtualized traffic will be spread across both of the team members for both inbound and outbound directions. You can have more than two team members; however inbound traffic will be spread over at most two of the adapters. Outbound traffic will always be spread across all adapters if the default of dynamic load balancing remains configured on the virtual switch.

### Encapsulation Offloads

SDN relies on encapsulation of packets to virtualize the network. For optimal performance, it is important that the network adapter supports hardware offload for the encapsulation format that is used. There is no significant performance benefit of one encapsulation format over another. The default encapsulation format when the network controller is used is VXLAN.

You can determine which encapsulation format is being used through the network controller with the following PowerShell cmdlet:

```syntax
    (Get-NetworkControllerVirtualNetworkConfiguration -connectionuri $uri).properties.networkvirtualizationprotocol
```

For best performance, if VXLAN is returned then you must make sure your physical network adapters support VXLAN task offload. If NVGRE is returned, then your physical network adapters must support NVGRE task offload.

### MTU

Encapsulation results in extra bytes being added to each packet. In order to avoid fragmentation of these packets, the physical network must be configured to use jumbo frames. An MTU value of 9234 is the recommended size for either VXLAN or NVGRE and must be configured on the physical switch for the physical interfaces of the host ports (L2) and the router interfaces (L3) of the VLANs over which encapsulated packets will be sent. This includes the Transit, HNV Provider and Management networks.

MTU on the Hyper-V host is configured through the network adapter, and the Network Controller Host Agent running on the Hyper-V host will adjust for the encapsulation overhead automatically if supported by the network adapter driver.

Once traffic egresses from the virtual network via a Gateway, the encapsulation is removed and the original MTU as sent from the VM is used.

### Single Root IO Virtualization (SR-IOV)

SDN is implemented on the Hyper-V host using a forwarding switch extension in the virtual switch. For this switch extension to process packets, SR-IOV must not be used on virtual network interfaces that are configured for use with the network controller as it causes VM traffic to bypass the virtual switch.

SR-IOV can still be enabled on the virtual switch if desired and can be used by VM network adapters that are not controlled by the network controller. These SR-IOV VMs can coexist on the same virtual switch as network controller controlled VMs which do not use SR-IOV.

If you are using 40Gbit network adapters it is recommended that you enable SR-IOV on the virtual switch for the Software Load Balancing (SLB) Gateways to achieve maximum throughput. This is covered in more detail in the [Software Load Balancer Gateways](slb-gateway-performance) section.

## HNV Gateways

You can find information on tuning HNV Gateways for use with SDN in the [HVN Gateways](hnv-gateway-performance) section.

## Software Load Balancer (SLB)

SLB Gateways can only be used with the Network Controller and SDN. You can find more information on tuning SDN for use with SLB Gateways in the [Software Load Balancer Gateways](slb-gateway-performance) section.