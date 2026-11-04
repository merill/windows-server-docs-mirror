---
layout: Conceptual
title: Container Networking Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/technologies/containers/container-networking-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: This topic is an overview of the networking stack for Windows Containers and includes links to additional guidance about creating, configuring, and managing container networks.
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-28T00:00:00.0000000Z
locale: en-us
document_id: 9447a867-a056-9e26-5ccc-5d2c68142226
document_version_independent_id: b7e3daa5-c6e3-6cff-1c3f-6256efa28bae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/technologies/Containers/Container-networking-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/technologies/containers/container-networking-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/technologies/Containers/Container-networking-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 1de6b559-7a53-3b13-68ab-47ef57dab064
---

# Container Networking Overview | Microsoft Learn

In this topic, we give you an overview of the networking stack for Windows containers and we include links to additional guidance about creating, configuring, and managing container networks.

Windows Server Containers are a lightweight operating system virtualization method separating applications or services from other services that run on the same container host. Windows containers function similarly to virtual machines. When enabled, each container has a separate view of the operating system, processes, file system, registry, and IP addresses, which you can connect to virtual networks.

A Windows container shares a kernel with the container host and all containers running on the host. Because of the shared kernel space, these containers require the same kernel version and configuration. Containers provide application isolation through process and namespace isolation technology.

Important

Windows containers do not provide a hostile security boundary and should not be used to isolate untrusted code.

With Windows containers, you can deploy a Hyper-V host, where you create one or more virtual machines on the VM hosts. Inside the VM hosts, containers get created, and the networking access is through a virtual switch running inside the virtual machine. You can use reusable images stored in a repository to deploy the operating system and services into containers. Each container has a virtual network adapter which connects to a virtual switch, forwarding inbound and outbound traffic. You can attach container endpoints to a local host network (such as NAT), the physical network or overlay virtual network created through the SDN stack.

For enforcing isolation between containers on the same host, you create a network compartment for each Windows Server and Hyper-V container. Windows Server containers use a Host vNIC to attach to the virtual switch. Hyper-V Containers use a Synthetic VM NIC (not exposed to the Utility VM) to attach to the virtual switch.