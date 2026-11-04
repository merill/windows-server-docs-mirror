---
layout: Conceptual
title: Deploy a Software Defined Network Infrastructure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: This topic provides links to topics on how to deploy a Microsoft Software Defined Network (SDN) infrastructure using scripts in Windows Server 2019 and 2016.
ms.topic: how-to
ms.date: 2021-10-28T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: 407ad9e1-1178-d454-7aa4-749bd2e1d48f
document_version_independent_id: c6a6b7a5-bc24-8fff-9a7c-8d9bd7259398
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/deploy/Deploy-a-Software-Defined-Network-Infrastructure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/deploy/deploy-a-software-defined-network-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/deploy/Deploy-a-Software-Defined-Network-Infrastructure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/c89972e1-0a93-4ce3-b588-9c24d08ca424
- https://authoring-docs-microsoft.poolparty.biz/devrel/f98c9a19-e481-4f15-8047-76b641e6ed57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b2144970-2aee-47fb-9df2-af491ca710ec
- https://authoring-docs-microsoft.poolparty.biz/devrel/f5685781-a4fd-40f1-8126-59abde4643bf
platformId: 15cd1632-d7da-cd33-43a0-73999bb7519b
---

# Deploy a Software Defined Network Infrastructure | Microsoft Learn

Deploy Microsoft's Software Defined Networking (SDN) infrastructure.

These deployments include all the technologies you need for a fully functional infrastructure, including Hyper-V Network Virtualization (HNV), network controllers, software load balancers (SLB/MUX), and gateways.

## Set up SDN infrastructure in the VMM fabric

- [Set up a Software Defined Network (SDN) infrastructure in the VMM fabric](/en-us/system-center/vmm/deploy-sdn)

    Use this method if you want to incorporate System Center Virtual Machine Manger (VMM) to manage your SDN infrastructure.

## Deploy SDN infrastructure using scripts

- [Deploy a Software Defined Network infrastructure using scripts](deploy-a-software-defined-network-infrastructure-using-scripts)

    Use this method if you do not want to use VMM to manage your SDN infrastructure, or if you have another management method.

## Deploy individual SDN technologies instead of an entire infrastructure

If you want to deploy individual SDN technologies instead of an entire infrastructure, see: [Deploy Software Defined Network Technologies using Windows PowerShell](deploy-software-defined-network-technologies-using-windows-powershell).