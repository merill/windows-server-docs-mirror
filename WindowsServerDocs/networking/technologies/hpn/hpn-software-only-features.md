---
layout: Conceptual
title: Software only (SO) features and technologies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/hpn/hpn-software-only-features
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: These features are implemented as part of the OS and are independent of the underlying NIC(s). Sometimes these features require some tuning of the NIC for optimal operation. Examples of these include Hyper-V features such as Virtual Machine Quality of Service (vmQoS), Access Control Lists (ACLs), and non-Hyper-V features like NIC Teaming.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-26T00:00:00.0000000Z
locale: en-us
document_id: acd97240-7de5-0932-3dae-af9dd9947e5e
document_version_independent_id: 4b18d6eb-14d2-c7c6-8a60-bfbbf9ba56fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/hpn/hpn-software-only-features.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/hpn/hpn-software-only-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/hpn/hpn-software-only-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 6fa0874a-84a5-9912-a28c-8c66a651f48d
---

# Software only (SO) features and technologies | Microsoft Learn

Software only features are implemented as part of the OS and are independent of the underlying NIC(s). Sometimes these features require some tuning of the NIC for optimal operation. Examples of these include Hyper-V features such as Virtual Machine Quality of Service (vmQoS), Access Control Lists (ACLs), and non-Hyper-V features like NIC Teaming. To learn more, see [Host network requirements for Azure Local](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

## Access Control Lists (ACLs)

A Hyper-V and SDNv1 feature for managing security for a VM. This feature applies to the non-virtualized Hyper-V stack and the HVNv1 stack. You can manage Hyper-V switch ACLs through [Add-VMNetworkAdapterAcl](/en-us/powershell/module/hyper-v/add-vmnetworkadapteracl) and [Remove-VMNetworkAdapterAcl](/en-us/powershell/module/hyper-v/remove-vmnetworkadapteracl) PowerShell cmdlets.

## Extended ACLs

Hyper-V Virtual Switch extended ACLs enable you to configure the Hyper-V Virtual Switch Extended Port ACLs to provide firewall protection and enforce security policies for the tenant VMs in datacenters. Because the port ACLs are configured on the Hyper-V Virtual Switch rather than within the VMs, the administrator can manage security policies for all tenants in a multitenant environment.

You can manage Hyper-V switch extended ACLs through the [Add-VMNetworkAdapterExtendedAcl](/en-us/powershell/module/hyper-v/add-vmnetworkadapterextendedacl) and [Remove-VMNetworkAdapterExtendedAcl](/en-us/powershell/module/hyper-v/remove-vmnetworkadapteracl) PowerShell cmdlets.

Tip

This feature applies to the HNVv1 stack. For ACLs in the SDN stack, refer to Software Defined Networking SDN) ACLs below.

For more information about Extended Port Access Control Lists in this library, see [Create Security Policies with Extended Port Access Control Lists](../../../virtualization/hyper-v-virtual-switch/create-security-policies-with-extended-port-access-control-lists).

## NIC Teaming

NIC Teaming, also called NIC bonding, is the aggregation of multiple NIC ports into an entity the host perceives as a single NIC port. NIC Teaming protects against the failure of a single NIC port (or the cable connected to it). It also aggregates network traffic for faster throughput.

With Windows Server 2016 you have two ways to do teaming:

1. Windows Server 2012 teaming solution
2. Windows Server 2016 Switch Embedded Teaming (SET)

## RSC in the vSwitch

Receive Segment Coalescing (RSC) in the vSwitch is a feature that takes packets that are part of the same stream and arrive between network interrupts, and coalesces them into a single packet before delivering them to the operating system. The virtual switch in Windows Server 2019 has this feature. For more details about this feature, see [Receive Segment Coalescing in the vSwitch](rsc-in-the-vswitch).

## Software Defined Networking (SDN) ACLs

The SDN-extension in Windows Server 2016 improved ways to support ACLs. In the Windows Server 2016 SDN v2 stack, SDN ACLs are used instead of ACLs and Extended ACLs. You can use Network Controller to manage SDN ACLs.

## SDN Quality of Service (QoS)

The SDN extension in Windows Server 2016 improved ways to provide bandwidth control (egress reservations, egress limits, and ingress limits) on a 5-tuple basis. Typically, these policies get applied at the vNIC or vmNIC level, but you can make them much more specific. In the Windows Server 2016 SDN v2 stack, SDN QoS is used instead of vmQoS. You can use Network Controller to manage SDN QoS.

## Switch Embedded Teaming (SET)

SET is an alternative NIC Teaming solution that you can use in environments that include Hyper-V and the Software Defined Networking (SDN) stack in Windows Server 2016. SET integrates some NIC Teaming functionality into the Hyper-V Virtual Switch. For information about Switch Embedded Teaming in this library, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

## Virtual Receive Side Scaling (vRSS)

Software vRSS is used to spread incoming traffic destined for a VM across multiple logical processors (LPs) of the VM. Software vRSS gives the VM the ability to handle more networking traffic than a single LP would be able to handle.

## Virtual Machine Quality of Service (vmQoS)

Virtual Machine Quality of Service is a Hyper-V feature that allows the switch to set limits on traffic generated by each VM. It also enables a VM to reserve an amount of bandwidth on the external network connection so that one VM can't starve another VM for bandwidth. In the Windows Server 2016 SDN v2 stack, SDN QoS replaces vmQoS.

vmQoS can set egress limits and egress reservations. You must determine the egress reservation mode (relative weight or absolute bandwidth) before creating the Hyper-V switch.

- Determine the egress reservation mode with the –MinimumBandwidthMode parameter of the New-VMSwitch PowerShell cmdlet.
- Set the value of the egress limit with the –MaximumBandwidth parameter on the Set-VMNetworkAdapter PowerShell cmdlet.
- Set the value for the egress reservation with either of the following parameters of the Set VMNetworkAdapter PowerShell cmdlet:

    - If the –MinimumBandwidthMode parameter on the New-VMSwitch cmdlet is Absolute, then set the –MinimumBandwidthAbsolute parameter on the Set VMNetworkAdapter cmdlet.
    - If the –MinimumBandwidthMode parameter on the New-VMSwitch cmdlet is Weight, then set the –MinimumBandwidthWeight parameter on the Set VMNetworkAdapter cmdlet.

Because of the limitations in the algorithm used for this feature, we recommend that the highest weight or absolute bandwidth not be more than 20 times the lowest weight or absolute bandwidth. If more control is needed, consider using the SDN stack and the SDN-QoS feature.