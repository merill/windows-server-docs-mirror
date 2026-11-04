---
layout: Conceptual
title: Configure virtual local area networks for Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/configure-virtual-local-area-networks-for-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to configure a virtual local area network (VLAN) for use by virtual machines on a Hyper-V host.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-18T00:00:00.0000000Z
locale: en-us
document_id: 96354f2e-e4eb-5efb-84e1-c1328e891ef6
document_version_independent_id: 2d8b614b-868a-4462-4815-213e7d84a5c5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/deploy/configure-virtual-local-area-networks-for-hyper-v.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/deploy/configure-virtual-local-area-networks-for-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/deploy/configure-virtual-local-area-networks-for-hyper-v.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 63c1dec7-8765-d8c5-ab48-06120cc6224a
---

# Configure virtual local area networks for Hyper-V | Microsoft Learn

Virtual local area networks (VLANs) offer one way to isolate network traffic. VLANs are configured in switches and routers that support 802.1q. If you configure multiple VLANs and want communication to occur between them, you need to configure the network devices to allow that.

To set up VLANs, make sure you have:

- A physical network adapter and driver that supports 802.1q VLAN tagging.
- A physical network switch that supports 802.1q VLAN tagging.

On the host, set up the virtual switch to let network traffic on the physical switch port for the VLAN IDs you use with virtual machines. Then, set up the virtual machine to specify the VLAN it uses for all network communications.

## Allow a virtual switch to use a VLAN

1. In Hyper-V Manager, select **Virtual Switch Manager** from the **Actions** pane on the right.
2. In **Virtual Switch Manager**, under **Virtual Switches** on the left, select a virtual switch connected to a physical network adapter that supports VLANs.
3. Under **VLAN ID** in the right pane, select **Enable virtual LAN identification for management operating system** and then type a number for the VLAN ID.
4. Select **OK**.

All traffic that goes through the physical network adapter connected to the virtual switch is tagged with the VLAN ID you set on the virtual switch and virtual machines.

## Allow a virtual machine to use a VLAN

1. In Hyper-V Manager, under **Virtual Machines**, right-click the appropriate virtual machine and select **Settings**. Or, select the machine and then select **Settings** under the machine name in the right pane.
2. On the **Settings** screen, under **Hardware** in the left pane, select a **Network Adapter** that has a virtual switch that's set up with a VLAN.
3. Under **VLAN ID** in the right pane, select **Enable virtual LAN identification**, and then type the same VLAN ID as the one you specified for the virtual switch.
4. Select **OK**.

If the virtual machine needs to use more VLANs, do one of the following:

- Connect more virtual network adapters to appropriate virtual switches and assign the VLAN IDs. Make sure to configure the IP addresses correctly, and that the traffic you want to route through the VLAN also uses the correct IP address.
- Configure the virtual network adapter in trunk mode by using the [Set-VMNetworkAdapterVlan](/en-us/powershell/module/hyper-v/set-vmnetworkadaptervlan) cmdlet.